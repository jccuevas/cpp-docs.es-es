---
title: "CSimpleMapEqualHelper Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CSimpleMapEqualHelper"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSimpleMapEqualHelper class"
ms.assetid: 9bb2968a-d609-405c-8272-ff3b42df6164
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# CSimpleMapEqualHelper Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

esta clase es una aplicación auxiliar para la clase de [CSimpleMap](../../atl/reference/csimplemap-class.md) .  
  
## Sintaxis  
  
```  
  
      template <  
   class TKey,  
   class TVal   
>  
class CSimpleMapEqualHelper  
```  
  
#### Parámetros  
 `TKey`  
 el elemento clave.  
  
 `TVal`  
 El elemento del valor.  
  
## Members  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CSimpleMapEqualHelper::IsEqualKey](../Topic/CSimpleMapEqualHelper::IsEqualKey.md)|\(Estático\) prueba dos claves para la igualdad.|  
|[CSimpleMapEqualHelper::IsEqualValue](../Topic/CSimpleMapEqualHelper::IsEqualValue.md)|\(Estático\) prueba dos valores son iguales.|  
  
## Comentarios  
 Esta clase de los rasgos es un extensor a la clase de `CSimpleMap` .  Proporciona métodos para comparar dos elementos de objeto de `CSimpleMap` \(específicamente, la clave y los componentes de valor\) para comprobar la igualdad.  De forma predeterminada, las claves y valores se comparan mediante `operator==()`, pero si la asignación contiene los tipos de datos complejos que null un operador de igualdad, esta clase se puede reemplazar para proporcionar la funcionalidad necesaria adicional.  
  
## Requisitos  
 **encabezado:** atlsimpcoll.h  
  
## Vea también  
 [CSimpleMapEqualHelperFalse Class](../../atl/reference/csimplemapequalhelperfalse-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)