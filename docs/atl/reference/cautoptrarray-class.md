---
title: "CAutoPtrArray Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::CAutoPtrArray<E>"
  - "CAutoPtrArray"
  - "ATL::CAutoPtrArray"
  - "ATL.CAutoPtrArray<E>"
  - "ATL.CAutoPtrArray"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAutoPtrArray class"
ms.assetid: 880a70da-8c81-4427-8ac6-49aa8d424244
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CAutoPtrArray Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase proporciona métodos útiles al crear una matriz de punteros inteligentes.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en Windows en tiempo de ejecución.  
  
## Sintaxis  
  
```  
  
      template<  
typename E  
>  
class CAutoPtrArray : public CAtlArray<  
ATL::CAutoPtr< E>,  
CAutoPtrElementTraits< E>  
>  
```  
  
#### Parámetros  
 `E`  
 el tipo de puntero.  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAutoPtrArray::CAutoPtrArray](../Topic/CAutoPtrArray::CAutoPtrArray.md)|el constructor.|  
  
## Comentarios  
 Esta clase proporciona un constructor y deriva métodos de [CAtlArray](../../atl/reference/catlarray-class.md) y de [CAutoPtrElementTraits](../../atl/reference/cautoptrelementtraits-class.md) para facilitar la creación de un objeto de clase de colección que almacena punteros inteligentes.  
  
 Para obtener más información, vea [clases de colección de ATL](../../atl/atl-collection-classes.md).  
  
## Jerarquía de herencia  
 `CAtlArray`  
  
 `CAutoPtrArray`  
  
## Requisitos  
 **encabezado:** atlcoll.h  
  
## Vea también  
 [CAtlArray Class](../../atl/reference/catlarray-class.md)   
 [CAutoPtrElementTraits Class](../../atl/reference/cautoptrelementtraits-class.md)   
 [CAutoPtrList Class](../../atl/reference/cautoptrlist-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)