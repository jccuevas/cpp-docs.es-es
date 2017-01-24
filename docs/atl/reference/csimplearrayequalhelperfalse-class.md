---
title: "CSimpleArrayEqualHelperFalse Class | Microsoft Docs"
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
  - "ATL.CSimpleArrayEqualHelperFalse<T>"
  - "ATL::CSimpleArrayEqualHelperFalse"
  - "ATL.CSimpleArrayEqualHelperFalse"
  - "ATL::CSimpleArrayEqualHelperFalse<T>"
  - "CSimpleArrayEqualHelperFalse"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSimpleArrayEqualHelperFalse class"
ms.assetid: 6918af6f-d23d-49eb-8482-c44272f5ffeb
caps.latest.revision: 19
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CSimpleArrayEqualHelperFalse Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

esta clase es una aplicación auxiliar para la clase de [CSimpleArray](../../atl/reference/csimplearray-class.md) .  
  
## Sintaxis  
  
```  
  
      template <  
   class T   
>   
class CSimpleArrayEqualHelperFalse  
```  
  
#### Parámetros  
 `T`  
 una clase derivada.  
  
## Members  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CSimpleArrayEqualHelperFalse::IsEqual](../Topic/CSimpleArrayEqualHelperFalse::IsEqual.md)|\(Estático\) devuelve false.|  
  
## Comentarios  
 Esta clase de los rasgos es un complemento de la clase de `CSimpleArray` .  Siempre devuelve false y, además, llama a `ATLASSERT` con un argumento de false si se hace referencia nunca.  En situaciones donde no es suficientemente definido la prueba de igualdad, esta clase permite que los elementos que contienen de una matriz funcionen correctamente para la mayoría de los métodos pero falla de forma bien definida para los métodos que dependen de comparaciones como [CSimpleArray:: Buscar](../Topic/CSimpleArray::Find.md).  
  
## Requisitos  
 **encabezado:** atlsimpcoll.h  
  
## Vea también  
 [CSimpleArrayEqualHelper Class](../../atl/reference/csimplearrayequalhelper-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)