---
title: '&lt;trustedIssuers&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d818c917-07b4-40db-9801-8676561859fd
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 33ef3ca88462595d81d269a92a643b43c9aea025
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/21/2017
---
# <a name="lttrustedissuersgt"></a>&lt;trustedIssuers&gt;
配置使用的基于配置的颁发者名称注册表的受信任颁发者证书的列表 (<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>)。  
  
 \<system.identityModel >  
\<identityConfiguration >  
\<securityTokenHandlers >  
\<securityTokenHandlerConfiguration >  
\<issuerNameRegistry >  
\<trustedIssuers >  
  
## <a name="syntax"></a>语法  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <issuerNameRegistry>  
          <trustedIssuers>  
            <add thumbprint=xs:string name=xs:string>  
            <clear>  
            <remove thumbprint=xs:string>  
          </trustedIssuers>  
        </issuerNameRegistry>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
 无  
  
### <a name="child-elements"></a>子元素  
  
|元素|描述|  
|-------------|-----------------|  
|`<add thumbprint=xs:string name=xs:string>`|将证书添加到受信任的颁发者的集合。 使用指定的证书`thumbprint`属性。 此属性是必需的并且应包含证书指纹的 ASN.1 编码形式。 `name`属性是可选的可以用于指定证书的友好名称。|  
|`<clear>`|清除所有证书的受信任颁发者的集合。|  
|`<remove thumbprint=xs:string>`|从受信任颁发者集合中删除证书。 使用指定的证书`thumbprint`属性。 该属性是必选项。|  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|[\<issuerNameRegistry >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuernameregistry.md)|配置颁发者名称注册表。 **重要说明：** `type`属性`<issuerNameRegistry>`元素必须引用<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>类`<trustedIssuers>`元素有效。|  
  
## <a name="remarks"></a>备注  
 Windows Identity Foundation (WIF) 提供的单个实现<xref:System.IdentityModel.Tokens.IssuerNameRegistry>现成类<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>类。 配置颁发者名称注册表维护从配置加载的受信任颁发者列表。 列表将每个颁发者名称与验证生成的颁发者的令牌的签名时需要的 X.509 证书相关联。 受信任颁发者证书的列表下指定`<trustedIssuers>`元素。 在列表中的每个元素将与验证生成的该颁发者的令牌的签名时需要的 X.509 证书关联的助记键的颁发者名称。 受信任的证书指定使用 ASN.1 编码形式的证书指纹和通过使用添加集合`<add>`元素。 您可以清除或从列表中删除颁发者 （证书），通过使用`<clear>`和`<remove>`元素。  
  
 `type`属性`<issuerNameRegistry>`元素必须引用<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>类`<trustedIssuers>`元素有效。  
  
## <a name="example"></a>示例  
 下面的 XML 演示如何指定配置基于颁发者名称注册表。  
  
```xml  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB2F32 … B1DC01EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
```  
  
## <a name="see-also"></a>另请参阅  
 <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>  
 <xref:System.IdentityModel.Tokens.IssuerNameRegistry>
