---
title: "ISupportErrorInfoImpl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::ISupportErrorInfoImpl<piid>"
  - "ATL::ISupportErrorInfoImpl"
  - "ISupportErrorInfoImpl"
  - "ATL.ISupportErrorInfoImpl<piid>"
  - "ATL.ISupportErrorInfoImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "error information, ATL"
  - "ISupportErrorInfo ATL implementation"
  - "ISupportErrorInfoImpl class"
ms.assetid: e33a4b11-a123-41cf-bcea-7b19743902af
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 26
---
# ISupportErrorInfoImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase proporciona una implementación predeterminada de [ISupportErrorInfo Interface](http://msdn.microsoft.com/es-es/42d33066-36b4-4a5b-aa5d-46682e560f32) y se puede utilizar cuando una sola interfaz genera errores en un objeto.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)].  
  
## Sintaxis  
  
```  
  
      template<  
const IID* piid   
>  
class ATL_NO_VTABLE ISupportErrorInfoImpl :  
public ISupportErrorInfo  
```  
  
#### Parámetros  
 `piid`  
 Un puntero al identificador IID de una interfaz que admite [IErrorInfo](http://msdn.microsoft.com/es-es/4dda6909-2d9a-4727-ae0c-b5f90dcfa447).  
  
## Members  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[ISupportErrorInfoImpl::InterfaceSupportsErrorInfo](../Topic/ISupportErrorInfoImpl::InterfaceSupportsErrorInfo.md)|indica si la interfaz identificada por `riid` admite la interfaz de [IErrorInfo](http://msdn.microsoft.com/es-es/4dda6909-2d9a-4727-ae0c-b5f90dcfa447) .|  
  
## Comentarios  
 [ISupportErrorInfo Interface](http://msdn.microsoft.com/es-es/42d33066-36b4-4a5b-aa5d-46682e560f32) garantiza que la información de error se puede devolver al cliente.  los objetos que utilizan **IErrorInfo** deben implementar **ISupportErrorInfo**.  
  
 La clase `ISupportErrorInfoImpl` proporciona una implementación predeterminada de **ISupportErrorInfo** y se puede utilizar cuando una sola interfaz genera errores en un objeto.  Por ejemplo:  
  
 [!code-cpp[NVC_ATL_COM#48](../../atl/codesnippet/CPP/isupporterrorinfoimpl-class_1.h)]  
  
## Jerarquía de herencia  
 `ISupportErrorInfo`  
  
 `ISupportErrorInfoImpl`  
  
## Requisitos  
 **encabezado:** atlcom.h  
  
## Vea también  
 [Class Overview](../../atl/atl-class-overview.md)