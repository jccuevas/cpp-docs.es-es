---
title: "CSimpleMap Class | Microsoft Docs"
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
  - "ATL::CSimpleMap"
  - "ATL.CSimpleMap"
  - "CSimpleMap"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSimpleMap class"
ms.assetid: 61b06eb4-ae73-44b0-a305-0afb5a33e8b1
caps.latest.revision: 21
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CSimpleMap Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase proporciona compatibilidad para una matriz simple de asignación.  
  
## Sintaxis  
  
```  
  
      template <   
   class TKey,  
   class TVal,  
   class TEqual = CSimpleMapEqualHelper< TKey, TVal >   
>   
class CSimpleMap  
```  
  
#### Parámetros  
 `TKey`  
 el tipo de elemento clave.  
  
 `TVal`  
 El tipo de elemento del valor.  
  
 `TEqual`  
 Un objeto de característica, definiendo la prueba de igualdad para los elementos de `T`escrito.  
  
## Members  
  
### Typedefs públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|[CSimpleMap::\_ArrayElementType](../Topic/CSimpleMap::_ArrayElementType.md)|Typedef para el tipo de valor.|  
|[CSimpleMap::\_ArrayKeyType](../Topic/CSimpleMap::_ArrayKeyType.md)|Typedef para cierra el tipo.|  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CSimpleMap::CSimpleMap](../Topic/CSimpleMap::CSimpleMap.md)|el constructor.|  
|[CSimpleMap::~CSimpleMap](../Topic/CSimpleMap::~CSimpleMap.md)|El destructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CSimpleMap::Add](../Topic/CSimpleMap::Add.md)|Agrega una clave y un valor asociado a la matriz de mapa.|  
|[CSimpleMap::FindKey](../Topic/CSimpleMap::FindKey.md)|Encuentra una clave concreta.|  
|[CSimpleMap::FindVal](../Topic/CSimpleMap::FindVal.md)|Encuentra un valor concreto.|  
|[CSimpleMap::GetKeyAt](../Topic/CSimpleMap::GetKeyAt.md)|Recupera la clave especificada.|  
|[CSimpleMap::GetSize](../Topic/CSimpleMap::GetSize.md)|Devuelve el número de entradas de la matriz de asignación.|  
|[CSimpleMap::GetValueAt](../Topic/CSimpleMap::GetValueAt.md)|Recupera el valor especificado.|  
|[CSimpleMap::Lookup](../Topic/CSimpleMap::Lookup.md)|Devuelve el valor asociado a la clave especificada.|  
|[CSimpleMap::Remove](../Topic/CSimpleMap::Remove.md)|Quita un valor clave y coincidente.|  
|[CSimpleMap::RemoveAll](../Topic/CSimpleMap::RemoveAll.md)|Quita todas las claves y valores.|  
|[CSimpleMap::RemoveAt](../Topic/CSimpleMap::RemoveAt.md)|Quita una clave concreta y un valor correspondiente.|  
|[CSimpleMap::ReverseLookup](../Topic/CSimpleMap::ReverseLookup.md)|Devuelve la clave asociada al valor especificado.|  
|[CSimpleMap::SetAt](../Topic/CSimpleMap::SetAt.md)|Establece el valor asociado a la clave especificada.|  
|[CSimpleMap::SetAtIndex](../Topic/CSimpleMap::SetAtIndex.md)|Establece la clave y el valor específicos.|  
  
## Comentarios  
 `CSimpleMap` proporciona compatibilidad para una matriz simple de asignación de cualquier tipo especificado `T`, administrar una matriz desordenado de elementos clave y sus valores asociados.  
  
 El parámetro `TEqual` proporciona un medio para definir una función de igualdad de dos elementos de `T`escrito.  Creando una clase similar a [CSimpleMapEqualHelper](../../atl/reference/csimplemapequalhelper-class.md), es posible modificar el comportamiento de la prueba de igualdad para cualquier matriz especificado.  Por ejemplo, al trabajar con una matriz de punteros, puede ser útil definir la igualdad como dependiendo de los valores punteros hacen referencia.  La implementación predeterminada utiliza **operator\=\=\(\)**.  
  
 `CSimpleMap` y [CSimpleArray](../../atl/reference/csimplearray-class.md) se proporciona por motivos de compatibilidad con versiones anteriores de ATL, y completan más y implementaciones eficaces de la colección son proporcionadas por [CAtlArray](../../atl/reference/catlarray-class.md) y [CAtlMap](../../atl/reference/catlmap-class.md).  
  
 A diferencia de otras colecciones de mapa en ATL y MFC, esta clase se implementa con una matriz simple, y las búsquedas de búsqueda requieren una búsqueda lineal.  `CAtlMap` debe usar cuando la matriz contiene un gran número de elementos.  
  
## Requisitos  
 **encabezado:** atlsimpcoll.h  
  
## Ejemplo  
 [!code-cpp[NVC_ATL_Utilities#91](../../atl/codesnippet/CPP/csimplemap-class_1.cpp)]  
  
## Vea también  
 [Class Overview](../../atl/atl-class-overview.md)