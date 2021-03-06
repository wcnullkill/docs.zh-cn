---
title: "&lt;标识&gt;的&lt; certificateReference&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ac359c65-c22d-42d2-97de-db53b77cebdb
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 27bcccab90c4627f2c9a1d241af3b1833ae13a18
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/02/2017
---
# <a name="ltcertificatereferencegt-for-ltidentitygt"></a>&lt;标识&gt;的&lt; certificateReference&gt;
指定 X.509 证书验证的设置。 通过此标识连接到终结点的安全 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] 将验证由服务器提供的声明是否包含一个用于构造此标识的标识声明。  
  
 \<标识 >  
\<certificateReference >  
  
## <a name="syntax"></a>语法  
  
```xml  
<certificateReference   
        findValue="String"   
    isChainIncluded="Boolean"  
    storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"storeName="  
  
    storeLocation="LocalMachine/CurrentUser"  
  
X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"  
</certificateReference>  
```  
  
## <a name="attributes-and-elements"></a>特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
  
|特性|描述|  
|---------------|-----------------|  
|findValue|指定要在 X.509 证书存储中搜索的值。 此属性中包含的类型必须满足指定的 `X509FindType` 值的要求。 默认值为一个空字符串。|  
|isChainIncluded|一个布尔值，指定是否使用证书链来执行验证。|  
|storeLocation|指定客户端可用于验证服务器证书的证书存储的位置。<br /><br /> 包括以下有效值：<br /><br /> -LocalMachine： 分配到本地计算机的证书存储。<br />-CurrentUser： 分配给当前用户的证书存储。<br /><br /> 默认值为 LocalMachine。<br /><br /> 此属性的类型为 <xref:System.Security.Cryptography.X509Certificates.StoreLocation>。|  
|storeName|指定要打开的 X.509 证书存储区的名称。<br /><br /> 包括以下有效值：<br /><br /> -AddressBook： 其他用户证书存储区。<br />-AuthRoot： 证书存储第三方证书颁发机构 (Ca)。<br />-CertificateAuthority： 中间 Ca 证书存储区。<br />-不允许： 证书吊销的证书存储。<br />-My： 个人证书的证书存储区。<br />-Root： 受信任的根 Ca 证书存储区。<br />-TrustedPeople： 直接受信任的人和资源的证书存储区。<br />-TrustedPublisher： 直接受信任的发行者的证书存储区。<br /><br /> 默认值为 My。<br /><br /> 此属性的类型为 <xref:System.Security.Cryptography.X509Certificates.StoreName>。|  
|X509FindType|指定要执行的 X.509 搜索的类型。 `findValue` 属性中包含的类型必须满足指定 X509FindType 的要求。<br /><br /> 包括以下有效值：<br /><br /> -FindByThumbPrint<br />-FindBySubjectName<br />-FindBySubjectDistinguishedName<br />-FindByIssuerName<br />-FindByIssuerDistinguishedName<br />-FindBySerialNumber<br />-FindByTimeValid<br />-FindByTimeNotYetValid<br />-FindByTemplateName<br />-FindByApplicationPolicy<br />-FindByCertificatePolicy<br />-FindByExtension<br />-FindByKeyUsage<br />-和 FindBySubjectKeyIdentifier<br /><br /> 默认值为 FindBySubjectDistinguishedName。<br /><br /> 此属性的类型为 <xref:System.Security.Cryptography.X509Certificates.X509FindType>。|  
  
### <a name="child-elements"></a>子元素  
 无。  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|[\<标识 >](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|指定一些设置，与某个终结点交换消息的其他终结点可以使用这些设置对该终结点进行身份验证。|  
  
## <a name="see-also"></a>另请参阅  
 <xref:System.ServiceModel.Configuration.CertificateReferenceElement>  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>
