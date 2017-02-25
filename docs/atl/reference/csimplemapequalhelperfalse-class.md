---
title: "CSimpleMapEqualHelperFalse Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::CSimpleMapEqualHelperFalse"
  - "CSimpleMapEqualHelperFalse"
  - "ATL.CSimpleMapEqualHelperFalse"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSimpleMapEqualHelperFalse class"
ms.assetid: a873eea3-e130-45cc-a476-61ee79511c3b
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# CSimpleMapEqualHelperFalse Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

esta clase es una aplicación auxiliar para la clase de [CSimpleMap](../../atl/reference/csimplemap-class.md) .  
  
## Sintaxis  
  
```  
  
template < class TKey, class TVal > class CSimpleMapEqualHelperFalse  
  
```  
  
## Members  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CSimpleMapEqualHelperFalse::IsEqualKey](../Topic/CSimpleMapEqualHelperFalse::IsEqualKey.md)|\(Estático\) prueba dos claves para la igualdad.|  
|[CSimpleMapEqualHelperFalse::IsEqualValue](../Topic/CSimpleMapEqualHelperFalse::IsEqualValue.md)|\(Estático\) devuelve false.|  
  
## Comentarios  
 Esta clase de los rasgos es un extensor a la clase de `CSimpleMap` .  Proporciona un método para comparar dos elementos contenidos en el objeto de `CSimpleMap` , específicamente dos elementos de valor o dos elementos clave.  
  
 La comparación de valor siempre devolverá false y, además, llama a `ATLASSERT` con un argumento de false si se hace referencia nunca.  En situaciones donde no es suficientemente definido la prueba de igualdad, esta clase permite un mapa que contiene pares clave\-valor funcione correctamente en la mayoría de los métodos pero falla de forma bien definida para los métodos que dependen de comparaciones como [CSimpleMap:: FindVal](../Topic/CSimpleMap::FindVal.md).  
  
## Requisitos  
 **encabezado:** atlsimpcoll.h  
  
## Vea también  
 [CSimpleMapEqualHelper Class](../../atl/reference/csimplemapequalhelper-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)