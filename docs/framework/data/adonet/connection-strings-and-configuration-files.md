---
title: "连接字符串和配置文件"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 37df2641-661e-407a-a3fb-7bf9540f01e8
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: fe56dc279471f77a3f9ae014f65faaa99a113624
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/21/2017
---
# <a name="connection-strings-and-configuration-files"></a>连接字符串和配置文件
在应用程序代码中嵌入连接字符串可能导致安全漏洞和维护问题。 可以使用查看编译到应用程序源代码的加密的连接字符串[Ildasm.exe （IL 反汇编程序）](../../../../docs/framework/tools/ildasm-exe-il-disassembler.md)工具。 此外，如果连接字符串发生更改，则必须重新编译应用程序。 因此，我们建议您将连接字符串存储在应用程序配置文件中。  
  
## <a name="working-with-application-configuration-files"></a>使用应用程序配置文件  
 应用程序配置文件包含特定应用程序特有的设置。 例如，ASP.NET 应用程序可以包含一个或多个**web.config**文件和 Windows 应用程序可能包含一个可选**app.config**文件。 虽然配置文件的名称和位置会因应用程序宿主的不同而有所不同，但配置文件可以有相同的元素。  
  
### <a name="the-connectionstrings-section"></a>connectionStrings 节  
 连接字符串可以存储为键/值对中**connectionStrings**部分**配置**的应用程序配置文件的元素。 子元素包括**添加**，**清除**，和**删除**。  
  
 下面的配置文件片段演示用于存储连接字符串的架构和语法。 **名称**属性是您提供用来唯一标识的连接字符串，以便可以在运行时对其进行检索的名称。 **ProviderName**是在 machine.config 文件中注册的.NET Framework 数据提供程序固定名称。  
  
```xml  
<?xml version='1.0' encoding='utf-8'?>  
  <configuration>  
    <connectionStrings>  
      <clear />  
      <add name="Name"   
       providerName="System.Data.ProviderName"   
       connectionString="Valid Connection String;" />  
    </connectionStrings>  
  </configuration>  
```  
  
> [!NOTE]
>  您可以将连接字符串的一部分保存在配置文件中，并使用 <xref:System.Data.Common.DbConnectionStringBuilder> 类在运行时将该字符串补充完整。 如果您预先不知道连接字符串的元素，或者不希望将敏感信息保存到配置文件中，这一方法会很有用。 有关详细信息，请参阅[连接字符串生成器](../../../../docs/framework/data/adonet/connection-string-builders.md)。  
  
### <a name="using-external-configuration-files"></a>使用外部配置文件  
 外部配置文件是单独的文件，此类文件包含由一部分组成的配置文件的片段。 外部配置文件由主配置文件引用。 存储**connectionStrings**物理上独立的文件中的部分是在部署应用程序后编辑连接字符串可能的情况下有用。 例如，标准 ASP.NET 行为是在修改配置文件后重新启动应用程序域，这将导致状态信息丢失。 然而，修改外部配置文件不会导致重新启动应用程序。 外部配置文件并不局限于由 ASP.NET 使用，Windows 应用程序也可以使用。 此外，文件访问安全性和权限也可以用于限制对外部配置文件的访问。 运行时使用外部配置文件是透明的，且不需要特殊编码。  
  
 若要在外部配置文件中存储连接字符串，创建单独的文件只包含**connectionStrings**部分。 不要包含任何其他的元素、节或属性。 此示例演示外部配置文件的语法。  
  
```xml  
<connectionStrings>  
  <add name="Name"   
   providerName="System.Data.ProviderName"   
   connectionString="Valid Connection String;" />  
</connectionStrings>  
```  
  
 在主应用程序配置文件中，你使用**configSource**特性以指定的完全限定的名称和外部文件的位置。 此示例引用名为 `connections.config` 的外部配置文件。  
  
```xml  
<?xml version='1.0' encoding='utf-8'?>  
<configuration>  
    <connectionStrings configSource="connections.config"/>  
</configuration>  
```  
  
## <a name="retrieving-connection-strings-at-run-time"></a>运行时检索连接字符串  
 .NET Framework 2.0 在 <xref:System.Configuration> 命名空间中引入了新类，以简化在运行时从配置文件检索连接字符串的操作。 您可以以编程方式按名称或提供程序名称检索连接字符串。  
  
> [!NOTE]
>  **Machine.config**文件还包含**connectionStrings**部分中，其中包含由 Visual Studio 使用的连接字符串。 通过从提供程序名称检索连接字符串时**app.config** Windows 应用程序中的连接字符串中的文件**machine.config**加载第一个，然后条目获得**app.config**。添加**清除**后立即**connectionStrings**元素在内存中，数据结构中移除所有继承的引用，以便在本地中定义仅连接字符串**app.config**文件被视为。  
  
### <a name="working-with-the-configuration-classes"></a>使用配置类  
 从 .NET Framework 2.0 开始，当使用本地计算机上的配置文件时，将使用 <xref:System.Configuration.ConfigurationManager>，从而替换已不推荐使用的 <xref:System.Configuration.ConfigurationSettings>。 <xref:System.Web.Configuration.WebConfigurationManager> 与 ASP.NET 配置文件一起使用。 它设计用于在 Web 服务器上，配置文件，并允许以编程方式访问配置文件节如**system.web**。  
  
> [!NOTE]
>  在运行时访问配置文件需要对调用方授予权限，根据应用程序类型、配置文件和位置确定所需的权限。 有关详细信息，请参阅[使用配置类](http://msdn.microsoft.com/library/98d2b386-baf6-4a17-974b-76e3b4c87acc)和<xref:System.Web.Configuration.WebConfigurationManager>对于 ASP.NET 应用程序，和<xref:System.Configuration.ConfigurationManager>对 Windows 应用程序。  
  
 您可以使用 <xref:System.Configuration.ConnectionStringSettingsCollection> 从应用程序配置文件中检索连接字符串。 它包含一套<xref:System.Configuration.ConnectionStringSettings>对象，其中每个表示中的一项**connectionStrings**部分。 它的属性 (Property) 映射为连接字符串属性 (Attribute)，从而允许您通过指定名称或提供程序名称来检索连接字符串。  
  
|属性|描述|  
|--------------|-----------------|  
|<xref:System.Configuration.ConnectionStringSettings.Name%2A>|连接字符串的名称。 映射到**名称**属性。|  
|<xref:System.Configuration.ConnectionStringSettings.ProviderName%2A>|完全限定提供程序名。 映射到**providerName**属性。|  
|<xref:System.Configuration.ConnectionStringSettings.ConnectionString%2A>|连接字符串。 映射到**connectionString**属性。|  
  
### <a name="example-listing-all-connection-strings"></a>示例：列出所有连接字符串  
 此示例循环访问 `ConnectionStringSettings` 集合，并在控制台窗口中显示 <xref:System.Configuration.ConnectionStringSettings.Name%2A>、<xref:System.Configuration.ConnectionStringSettings.ProviderName%2A> 和 <xref:System.Configuration.ConnectionStringSettings.ConnectionString%2A> 属性。  
  
> [!NOTE]
>  System.Configuration.dll 并不包含在所有项目类型中，您可能需要对其设置引用才能使用配置类。 特定应用程序配置文件的名称和位置因应用程序类型和宿主进程的不同而有所不同。  
  
 [!code-csharp[DataWorks ConnectionStringSettings.RetrieveFromConfig#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfig/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringSettings.RetrieveFromConfig#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfig/VB/source.vb#1)]  
  
### <a name="example-retrieving-a-connection-string-by-name"></a>示例：按名称检索连接字符串  
 此示例演示如何通过指定连接字符串名称从配置文件中检索连接字符串。 此代码创建一个 <xref:System.Configuration.ConnectionStringSettings> 对象，以将提供的输入参数与 <xref:System.Configuration.ConfigurationManager.ConnectionStrings%2A> 名称相匹配。 如果未找到匹配名称，则该函数返回 `null`（在 Visual Basic 中返回 `Nothing`）。  
  
 [!code-csharp[DataWorks ConnectionStringSettings.RetrieveFromConfigByName#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByName/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringSettings.RetrieveFromConfigByName#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByName/VB/source.vb#1)]  
  
### <a name="example-retrieving-a-connection-string-by-provider-name"></a>示例：按提供程序名称检索连接字符串  
 此示例演示如何通过来检索连接字符串格式指定的提供程序固定名称*System.Data.ProviderName*。 此代码循环访问 <xref:System.Configuration.ConnectionStringSettingsCollection>，并返回找到的第一个 <xref:System.Configuration.ConnectionStringSettings.ProviderName%2A> 的连接字符串。 如果未找到提供程序名称，则该函数返回 `null`（在 Visual Basic 中返回 `Nothing`）。  
  
 [!code-csharp[DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider/VB/source.vb#1)]  
  
## <a name="encrypting-configuration-file-sections-using-protected-configuration"></a>使用受保护配置加密配置文件节  
 ASP.NET 2.0 引入了一个称为的新功能*受保护配置*，，可用于加密配置文件中的敏感信息。 虽然受保护配置主要是为 ASP.NET 应用程序设计的，但它也可以用于加密 Windows 应用程序中的配置文件节。 受保护的配置功能的详细说明，请参阅[加密配置信息使用受保护的配置](http://msdn.microsoft.com/library/51cdfe5b-9d82-458c-94ff-c551c4f38ed1)。  
  
 下面的配置文件片断演示**connectionStrings**部分后已加密。 **ConfigProtectionProvider**指定用于加密和解密连接字符串的受保护的配置提供程序。 **EncryptedData**节包含密文。  
  
```xml  
<connectionStrings configProtectionProvider="DataProtectionConfigurationProvider">  
  <EncryptedData>  
    <CipherData>  
      <CipherValue>AQAAANCMnd8BFdERjHoAwE/Cl+sBAAAAH2... </CipherValue>  
    </CipherData>  
  </EncryptedData>  
</connectionStrings>  
```  
  
 .NET Framework 在运行时检索加密的连接字符串时，使用指定的提供程序来解密**CipherValue**和使其可供你的应用程序。 你无需额外编写任何代码来管理解密过程。  
  
### <a name="protected-configuration-providers"></a>受保护配置提供程序  
 在注册受保护的配置提供程序**configProtectedData**部分**machine.config**文件在本地计算机上，如以下片段中，其中显示了两个中所示使用.NET Framework 提供的受保护的配置提供程序。 此处显示的值已被截断，以便于阅读。  
  
```xml  
<configProtectedData defaultProvider="RsaProtectedConfigurationProvider">  
  <providers>  
    <add name="RsaProtectedConfigurationProvider"   
      type="System.Configuration.RsaProtectedConfigurationProvider, ... />  
    <add name="DataProtectionConfigurationProvider"   
      type="System.Configuration.DpapiProtectedConfigurationProvider, ... />  
  </providers>  
</configProtectedData>  
```  
  
 你可以通过将它们添加到配置其他受保护的配置提供程序**machine.config**文件。 还可以通过从 <xref:System.Configuration.ProtectedConfigurationProvider> 抽象基类继承来创建自己的受保护配置提供程序。 下表描述了 .NET Framework 附带的两个配置文件。  
  
|提供程序|描述|  
|--------------|-----------------|  
|<!--zz<xref:System.Configuration.RSAProtectedConfigurationProvider>-->`System.Configuration.RSAProtectedConfigurationProvider`|使用 RSA 加密算法来加密和解密数据。 RSA 算法既可用于公钥加密，也可用于数字签名。 它还称为“公共密钥”或非对称加密，因为它使用两个不同的密钥。 你可以使用[ASP.NET IIS 注册工具 (Aspnet_regiis.exe)](http://msdn.microsoft.com/library/6491c41e-e2b0-481f-9863-db3614d5f96b)来加密 Web.config 文件中的节和管理加密密钥。 ASP.NET 在处理配置文件时解密该文件。 ASP.NET 应用程序的标识必须对用于加密和解密各加密节的加密密钥具有读取权限。|  
|<!--zz<xref:System.Configuration.DPAPIProtectedConfigurationProvider>-->`System.Configuration.DPAPIProtectedConfigurationProvider`|使用 Windows Data Protection API (DPAPI) 来加密配置节。 它使用 Windows 内置加密服务，并可为计算机特定或用户帐户特定保护进行配置。 对于同一服务器上需要共享信息的多个应用程序来说，计算机特定保护非常有用。 用户帐户特定保护可与以特定用户标识运行的服务（如共享宿主环境）一起使用。 每个应用程序以单独的标识运行，这样就限制了对文件和数据库等资源的访问。|  
  
 这两种提供程序都可以对数据进行强加密。 但是，如果计划在多台服务器（如网络场）上使用相同的加密配置文件，则只有通过 `RsaProtectedConfigurationProvider` 才能导出用于加密数据的加密密钥，并将其导入其他服务器。 有关详细信息，请参阅[导入和导出受保护配置的 RSA 密钥容器](http://msdn.microsoft.com/library/f3022b39-f17f-48c1-b067-025eab0ce8bc)。  
  
### <a name="using-the-configuration-classes"></a>使用配置类  
 <xref:System.Configuration> 命名空间提供以编程方式使用配置设置的类。 <xref:System.Configuration.ConfigurationManager> 类可提供对计算机、应用程序和用户配置文件的访问。 如果要创建 ASP.NET 应用程序，则可以使用<xref:System.Web.Configuration.WebConfigurationManager>类，该类提供相同的功能，同时还允许你访问设置是唯一到 ASP.NET 应用程序，例如那些在 **\<.w e b >**。  
  
> [!NOTE]
>  <xref:System.Security.Cryptography> 命名空间包含提供用于加密和解密数据的其他选项的类。 如果需要采用在使用受保护配置时不可用的加密服务，请使用这些类。 一些类是非托管 Microsoft CryptoAPI 的包装类，而其他类则是纯托管实现。 有关详细信息，请参阅[加密服务](http://msdn.microsoft.com/en-us/68a1e844-c63c-44af-9247-f6716eb23781)。  
  
### <a name="appconfig-example"></a>App.config 示例  
 此示例演示如何加密进行切换**connectionStrings**主题中**app.config** Windows 应用程序的文件。 在此示例中，该过程将应用程序的名称（例如“MyApplication.exe”）作为一个自变量。 **App.config**文件然后进行加密或复制到包含名称"MyApplication.exe.config"可执行文件的文件夹。  
  
> [!NOTE]
>  只能在加密连接字符串的计算机上对其进行解密。  
  
 该代码使用<xref:System.Configuration.ConfigurationManager.OpenExeConfiguration%2A>方法打开**app.config**文件进行编辑，和<xref:System.Configuration.ConfigurationManager.GetSection%2A>方法返回**connectionStrings**部分。 然后，代码检查 <xref:System.Configuration.SectionInformation.IsProtected%2A> 属性，调用 <xref:System.Configuration.SectionInformation.ProtectSection%2A> 以加密未加密的节。 调用 <xref:System.Configuration.SectionInformation.UnprotectSection%2A> 方法以加密该节。 <xref:System.Configuration.Configuration.Save%2A> 方法完成该操作并保存所做更改。  
  
> [!NOTE]
>  必须在要运行代码的项目中设置对 `System.Configuration.dll` 的引用。  
  
 [!code-csharp[DataWorks ConnectionStrings.Encrypt#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStrings.Encrypt/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStrings.Encrypt#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStrings.Encrypt/VB/source.vb#1)]  
  
### <a name="webconfig-example"></a>Web.config 示例  
 此示例使用 <xref:System.Web.Configuration.WebConfigurationManager.OpenWebConfiguration%2A> 的 `WebConfigurationManager` 方法。 请注意，在这种情况下可以提供的相对路径**Web.config**通过使用波形符的文件。 代码需要对 `System.Web.Configuration` 类的引用。  
  
 [!code-csharp[DataWorks ConnectionStringsWeb.Encrypt#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringsWeb.Encrypt/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringsWeb.Encrypt#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringsWeb.Encrypt/VB/source.vb#1)]  
  
 保护 ASP.NET 应用程序的详细信息，请参阅[NIB: ASP.NET 安全](http://msdn.microsoft.com/en-us/04b37532-18d9-40b4-8e5f-ee09a70b311d)和[ASP.NET 2.0 安全方案一眼](http://go.microsoft.com/fwlink/?LinkId=59997)ASP.NET 开发人员中心上。  
  
## <a name="see-also"></a>另请参阅  
 [连接字符串生成器](../../../../docs/framework/data/adonet/connection-string-builders.md)  
 [保护连接信息](../../../../docs/framework/data/adonet/protecting-connection-information.md)  
 [使用配置类](http://msdn.microsoft.com/library/98d2b386-baf6-4a17-974b-76e3b4c87acc)  
 [配置应用程序](../../../../docs/framework/configure-apps/index.md)  
 [ASP.NET 网站管理](http://msdn.microsoft.com/library/1298034b-5f7d-464d-abd1-ad9e6b3eeb7e)  
 [ADO.NET 托管提供程序和数据集开发人员中心](http://go.microsoft.com/fwlink/?LinkId=217917)
