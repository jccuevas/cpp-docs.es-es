---
title: "CSimpleArrayEqualHelper Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CSimpleArrayEqualHelper"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSimpleArrayEqualHelper class"
ms.assetid: a2b55d89-78c9-42ef-842c-5304c6d20ad6
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# CSimpleArrayEqualHelper Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

esta clase es una aplicación auxiliar para la clase de [CSimpleArray](../../atl/reference/csimplearray-class.md) .  
  
## Sintaxis  
  
```  
  
      template <  
   class T   
>  
class CSimpleArrayEqualHelper  
```  
  
#### Parámetros  
 `T`  
 una clase derivada.  
  
## Members  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CSimpleArrayEqualHelper::IsEqual](../Topic/CSimpleArrayEqualHelper::IsEqual.md)|\(Estático\) prueba dos elementos de objeto de `CSimpleArray` para comprobar la igualdad.|  
  
## Comentarios  
 Esta clase de los rasgos es un extensor a la clase de `CSimpleArray` .  proporciona un método para comparar dos elementos almacenados en un objeto de `CSimpleArray` .  De forma predeterminada, los elementos se comparan mediante **operator\= \(\)**, pero si la matriz contiene los tipos de datos complejos que null un operador de igualdad, necesitará para invalidar esta clase.  
  
## Requisitos  
 **encabezado:** atlsimpcoll.h  
  
## Vea también  
 [CSimpleArray Class](../../atl/reference/csimplearray-class.md)   
 [CSimpleArrayEqualHelperFalse Class](../../atl/reference/csimplearrayequalhelperfalse-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)