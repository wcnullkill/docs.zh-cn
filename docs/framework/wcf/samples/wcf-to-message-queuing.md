---
title: "Windows Communication Foundation 到消息队列"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 78d0d0c9-648e-4d4a-8f0a-14d9cafeead9
caps.latest.revision: "32"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6d3a9dd8c17b39ae52fffb5995f4763b250a3551
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/02/2017
---
# <a name="windows-communication-foundation-to-message-queuing"></a>Windows Communication Foundation 到消息队列
本示例演示 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 应用程序如何向消息队列 (MSMQ) 应用程序发送消息。 此服务是自承载控制台应用程序，通过它可以观察服务接收排队消息。 服务和客户端不需要同时运行。  
  
 服务从队列接收消息并处理订单。 服务创建一个事务性队列，并为收到的消息设置消息处理程序，如下面的示例代码所示。  
  
```  
static void Main(string[] args)  
{  
    if (!MessageQueue.Exists(  
              ConfigurationManager.AppSettings["queueName"]))  
       MessageQueue.Create(  
           ConfigurationManager.AppSettings["queueName"], true);  
        //Connect to the queue  
        MessageQueue Queue = new   
    MessageQueue(ConfigurationManager.AppSettings["queueName"]);  
    Queue.ReceiveCompleted +=   
                 new ReceiveCompletedEventHandler(ProcessOrder);  
    Queue.BeginReceive();  
    Console.WriteLine("Order Service is running");  
    Console.ReadLine();  
}  
```  
  
 当消息到达队列中时，将调用消息处理程序 `ProcessOrder`。  
  
```  
public static void ProcessOrder(Object source,  
    ReceiveCompletedEventArgs asyncResult)  
{  
    try  
    {  
        // Connect to the queue.  
        MessageQueue Queue = (MessageQueue)source;  
        // End the asynchronous receive operation.  
        System.Messaging.Message msg =   
                     Queue.EndReceive(asyncResult.AsyncResult);  
        msg.Formatter = new System.Messaging.XmlMessageFormatter(  
                                new Type[] { typeof(PurchaseOrder) });  
        PurchaseOrder po = (PurchaseOrder) msg.Body;  
        Random statusIndexer = new Random();  
        po.Status = PurchaseOrder.OrderStates[statusIndexer.Next(3)];  
        Console.WriteLine("Processing {0} ", po);  
        Queue.BeginReceive();  
    }  
    catch (System.Exception ex)  
    {  
        Console.WriteLine(ex.Message);  
    }  
  
}  
```  
  
 服务从 MSMQ 消息正文中提取 `ProcessOrder` 并处理订单。  
  
 MSMQ 队列名称在配置文件的 appSettings 节中指定，如以下示例配置所示。  
  
```xml  
<appSettings>  
    <add key="orderQueueName" value=".\private$\Orders" />  
</appSettings>  
```  
  
> [!NOTE]
>  队列名称为本地计算机使用圆点 (.)，并在其路径中使用反斜杠分隔符。  
  
 客户端创建采购订单并在事务的范围内提交该采购订单，如下面的示例代码所示。  
  
```  
// Create the purchase order  
PurchaseOrder po = new PurchaseOrder();  
// Fill in the details  
...  
  
OrderProcessorClient client = new OrderProcessorClient("OrderResponseEndpoint");  
  
MsmqMessage<PurchaseOrder> ordermsg = new MsmqMessage<PurchaseOrder>(po);  
using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))  
{  
    client.SubmitPurchaseOrder(ordermsg);  
    scope.Complete();  
}  
Console.WriteLine("Order has been submitted:{0}", po);  
  
//Closing the client gracefully closes the connection and cleans up resources  
client.Close();  
```  
  
 客户端按顺序使用自定义客户端将 MSMQ 消息发送给队列。 由于接收和处理消息的应用程序是 MSMQ 应用程序，而不是 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 应用程序，因此这两个应用程序之间没有隐式服务协定。 所以在此方案中，我们不能使用 Svcutil.exe 工具创建代理。  
  
 对于使用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 绑定发送消息的所有 `MsmqIntegration` 应用程序而言，自定义客户端在本质上都是相同的。 与其他客户端不同，它不包含一系列服务操作。 它只是一个提交消息操作。  
  
```  
[System.ServiceModel.ServiceContractAttribute(Namespace = "http://Microsoft.ServiceModel.Samples")]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true, Action = "*")]  
    void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg);  
}  
  
public partial class OrderProcessorClient : System.ServiceModel.ClientBase<IOrderProcessor>, IOrderProcessor  
{  
    public OrderProcessorClient(){}  
  
    public OrderProcessorClient(string configurationName)  
        : base(configurationName)  
    { }  
  
    public OrderProcessorClient(System.ServiceModel.Channels.Binding binding, System.ServiceModel.EndpointAddress address)  
        : base(binding, address)  
    { }  
  
    public void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg)  
    {  
        base.Channel.SubmitPurchaseOrder(msg);  
    }  
}  
```  
  
 运行示例时，客户端和服务活动将显示在服务和客户端控制台窗口中。 您可以看到服务从客户端接收消息。 在每个控制台窗口中按 Enter 可以关闭服务和客户端。 请注意：由于正在使用队列，因此不必同时启动和运行客户端和服务。 例如，可以先运行客户端，再将其关闭，然后启动服务，这样服务仍然会收到客户端的消息。  
  
> [!NOTE]
>  此示例需要安装消息队列。 请参阅中的安装说明[消息队列](http://go.microsoft.com/fwlink/?LinkId=94968)。  
  
### <a name="to-setup-build-and-run-the-sample"></a>设置、生成和运行示例  
  
1.  确保已执行[的 Windows Communication Foundation 示例的一次性安装过程](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2.  如果先运行服务，则它将检查以确保队列存在。 如果队列不存在，则服务将创建一个队列。 可以先运行服务以创建队列或通过 MSMQ 队列管理器创建一个队列。 执行下面的步骤来在 Windows 2008 中创建队列。  
  
    1.  在 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 中打开服务器管理器。  
  
    2.  展开**功能**选项卡。  
  
    3.  右键单击**私有消息队列**，然后选择**新建**，**专用队列**。  
  
    4.  检查**事务**框。  
  
    5.  输入`ServiceModelSamplesTransacted`作为新队列的名称。  
  
3.  若要生成 C# 或 Visual Basic .NET 版本的解决方案，请按照 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的说明进行操作。  
  
4.  若要在单台计算机配置上运行示例，请按照中的说明[运行 Windows Communication Foundation 示例](../../../../docs/framework/wcf/samples/running-the-samples.md)。  
  
### <a name="to-run-the-sample-across-computers"></a>跨计算机运行示例  
  
1.  将 \service\bin\ 文件夹（在语言特定文件夹内）中的服务程序文件复制到服务计算机上。  
  
2.  将 \client\bin\ 文件夹（在语言特定文件夹内）中的客户端程序文件复制到客户端计算机上。  
  
3.  在 Client.exe.config 文件中，更改客户端终结点地址以指定服务计算机名称，而不是使用“.”。  
  
4.  在服务计算机上，在命令提示符下启动 Service.exe。  
  
5.  在客户端计算机上，在命令提示符下启动 Client.exe。  
  
> [!IMPORTANT]
>  您的计算机上可能已安装这些示例。 在继续操作之前，请先检查以下（默认）目录：  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目录不存在，请访问 [针对 .NET Framework 4 的 Windows Communication Foundation (WCF) 和 Windows Workflow Foundation (WF) 示例](http://go.microsoft.com/fwlink/?LinkId=150780) 以下载所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 示例。 此示例位于以下目录：  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\WcfToMsmq`  
  
## <a name="see-also"></a>另请参阅  
 [如何： 与 WCF 终结点交换消息和消息队列应用程序](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)  
 [消息队列](http://go.microsoft.com/fwlink/?LinkId=94968)
