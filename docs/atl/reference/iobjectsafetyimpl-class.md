---
title: "IObjectSafetyImpl Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "IObjectSafetyImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "controles [ATL], safe"
  - "IObjectSafety, implementación de ATL"
  - "IObjectSafetyImpl class"
  - "safe for scripting and initialization (controls)"
ms.assetid: 64e32082-d910-4a8a-a5bf-ebed9145359d
caps.latest.revision: 20
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IObjectSafetyImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase proporciona una implementación predeterminada de la interfaz de `IObjectSafety` para permitir que un cliente recupere y establezca los niveles de seguridad de un objeto.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)].  
  
## Sintaxis  
  
```  
  
      template <class   
      T  
      , DWORD   
      dwSupportedSafety  
      >  
class IObjectSafetyImpl  
```  
  
#### Parámetros  
 `T`  
 la clase, derivada de `IObjectSafetyImpl`.  
  
 *dwSupportedSafety*  
 Especifica las opciones admitidas de seguridad para el control.  Puede presentar uno de los siguientes valores:  
  
-   La interfaz de**INTERFACESAFE\_FOR\_UNTRUSTED\_CALLER** The identificada por el parámetro `riid` de [SetInterfaceSafetyOptions](../Topic/IObjectSafetyImpl::SetInterfaceSafetyOptions.md) debe crearse segura para el script.  
  
-   La interfaz de**INTERFACESAFE\_FOR\_UNTRUSTED\_DATA** The identificada por el parámetro `riid` de `SetInterfaceSafetyOptions` debe crearse segura para los datos que no es de confianza durante la inicialización.  
  
## Members  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[IObjectSafetyImpl::GetInterfaceSafetyOptions](../Topic/IObjectSafetyImpl::GetInterfaceSafetyOptions.md)|Recupera las opciones de seguridad que admite el objeto, así como las opciones de seguridad establecidas actualmente para el objeto.|  
|[IObjectSafetyImpl::SetInterfaceSafetyOptions](../Topic/IObjectSafetyImpl::SetInterfaceSafetyOptions.md)|Crea safe de objeto para la inicialización o el script.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[IObjectSafetyImpl::m\_dwCurrentSafety](../Topic/IObjectSafetyImpl::m_dwCurrentSafety.md)|Almacena el nivel actual de la seguridad de objetos.|  
  
## Comentarios  
 la clase `IObjectSafetyImpl` proporciona una implementación predeterminada de `IObjectSafety`.  La interfaz de `IObjectSafety` permite a un cliente recuperar y establecer los niveles de seguridad de un objeto.  Por ejemplo, un explorador web puede llamar **IObjectSafety:: SetInterfaceSafetyOptions** para crear una caja fuerte de control para la inicialización o safe para el script.  
  
 Observe que mediante la macro de [IMPLEMENTED\_CATEGORY](../Topic/IMPLEMENTED_CATEGORY.md) con **CATID\_SafeForScripting** y categorías componentes de **CATID\_SafeForInitializing** proporcionan una manera alternativa de especificar que un componente es seguro.  
  
 **artículos relacionados** [tutorial de ATL](../../atl/active-template-library-atl-tutorial.md), [Crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md)  
  
## Jerarquía de herencia  
 `IObjectSafety`  
  
 `IObjectSafetyImpl`  
  
## Requisitos  
 **encabezado:** atlctl.h  
  
## Vea también  
 [IObjectSafety Interface](https://msdn.microsoft.com/en-us/library/aa768224.aspx)   
 [Class Overview](../../atl/atl-class-overview.md)