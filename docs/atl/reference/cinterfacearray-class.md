---
title: "CInterfaceArray Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CInterfaceArray"
  - "CInterfaceArray"
  - "ATL::CInterfaceArray"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CInterfaceArray class"
ms.assetid: 1f29cf66-a086-4a7b-b6a8-64f73da39f79
caps.latest.revision: 18
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CInterfaceArray Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase proporciona métodos útiles al crear una matriz de punteros de interfaz COM.  
  
## Sintaxis  
  
```  
  
      template<  
   class I,  
   const IID* piid = & __uuidof( I )  
>  
class CInterfaceArray : public CAtlArray<  
   ATL::CComQIPtr< I, piid >,  
   CComQIPtrElementTraits< I, piid >  
>  
```  
  
#### Parámetros  
 `I`  
 Una interfaz COM que especifica el tipo de puntero que se va a almacenar.  
  
 `piid`  
 Un puntero al identificador IID de `I`.  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CInterfaceArray::CInterfaceArray](../Topic/CInterfaceArray::CInterfaceArray.md)|El constructor para la matriz de interfaz.|  
  
## Comentarios  
 Esta clase proporciona un constructor y métodos derivados para crear una matriz de punteros de interfaz COM.  Uso [CInterfaceList](../../atl/reference/cinterfacelist-class.md) cuando se requiere una lista.  
  
 Para obtener más información, vea [clases de colección de ATL](../../atl/atl-collection-classes.md).  
  
## Jerarquía de herencia  
 `CAtlArray`  
  
 `CInterfaceArray`  
  
## Requisitos  
 **encabezado:** atlcoll.h  
  
## Vea también  
 [CAtlArray Class](../../atl/reference/catlarray-class.md)   
 [CComQIPtr Class](../../atl/reference/ccomqiptr-class.md)   
 [CComQIPtrElementTraits Class](../../atl/reference/ccomqiptrelementtraits-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)