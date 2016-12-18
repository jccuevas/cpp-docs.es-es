---
title: "CAtlMap Class | Microsoft Docs"
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
  - "ATL.CAtlMap"
  - "CAtlMap"
  - "ATL::CAtlMap"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAtlMap class"
ms.assetid: 5e2fe028-8e6d-4686-93df-1433d2080ec3
caps.latest.revision: 21
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CAtlMap Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase proporciona métodos para crear y administrar un objeto de asignación.  
  
## Sintaxis  
  
```  
  
      template<  
   typename K,  
   typename V,  
   class KTraits = CElementTraits< K >,  
   class VTraits = CElementTraits< V >  
>  
class CAtlMap  
```  
  
#### Parámetros  
 `K`  
 el tipo de elemento clave.  
  
 V  
 El tipo de elemento del valor.  
  
 `KTraits`  
 El código utilizado para copiar o mover elementos clave.  Vea [clase de CElementTraits](../../atl/reference/celementtraits-class.md) para más detalles.  
  
 `VTraits`  
 El código utilizado para copiar o mover elementos de valor.  
  
## Members  
  
### Typedefs públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAtlMap::KINARGTYPE](../Topic/CAtlMap::KINARGTYPE.md)|Escriba utilizado cuando una tecla se pasa como argumento de entrada|  
|[CAtlMap::KOUTARGTYPE](../Topic/CAtlMap::KOUTARGTYPE.md)|Tipo utilizado cuando una tecla se devuelve como argumento de salida.|  
|[CAtlMap::VINARGTYPE](../Topic/CAtlMap::VINARGTYPE.md)|Tipo utilizado cuando un valor se pasa como argumento de entrada.|  
|[CAtlMap::VOUTARGTYPE](../Topic/CAtlMap::VOUTARGTYPE.md)|Tipo utilizado cuando un valor se pasa como argumento de salida.|  
  
### Clases pública  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAtlMap::CPair Class](../Topic/CAtlMap::CPair%20Class.md)|Una clase que contiene los elementos de clave y valor.|  
  
### Miembros de datos de CPair  
  
|Name|Descripción|  
|----------|-----------------|  
|[CPair::m\_key](../Topic/CAtlMap::CPair::m_key.md)|el miembro de datos que almacena el elemento clave.|  
|[CPair::m\_value](../Topic/CAtlMap::CPair::m_value.md)|El miembro de datos que almacena el elemento del valor.|  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAtlMap::CAtlMap](../Topic/CAtlMap::CAtlMap.md)|el constructor.|  
|[CAtlMap::~CAtlMap](../Topic/CAtlMap::~CAtlMap.md)|El destructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAtlMap::AssertValid](../Topic/CAtlMap::AssertValid.md)|Llame a este método para producir ASSERT si `CAtlMap` no es válido.|  
|[CAtlMap::DisableAutoRehash](../Topic/CAtlMap::DisableAutoRehash.md)|Llame a este método para deshabilitar rehashing automático del objeto de `CAtlMap` .|  
|[CAtlMap::EnableAutoRehash](../Topic/CAtlMap::EnableAutoRehash.md)|Llame a este método para habilitar rehashing automático del objeto de `CAtlMap` .|  
|[CAtlMap::GetAt](../Topic/CAtlMap::GetAt.md)|Llame a este método para devolver el elemento en una posición especificada del mapa.|  
|[CAtlMap::GetCount](../Topic/CAtlMap::GetCount.md)|Llame a este método para recuperar el número de elementos del mapa.|  
|[CAtlMap::GetHashTableSize](../Topic/CAtlMap::GetHashTableSize.md)|Llame a este método para determinar el número de bandejas en la tabla hash del mapa.|  
|[CAtlMap::GetKeyAt](../Topic/CAtlMap::GetKeyAt.md)|Llame a este método para recuperar la clave almacenada en la posición especificada en el objeto de `CAtlMap` .|  
|[CAtlMap::GetNext](../Topic/CAtlMap::GetNext.md)|Llame a este método para obtener un puntero a los siguientes pares de elementos almacenados en el objeto de `CAtlMap` .|  
|[CAtlMap::GetNextAssoc](../Topic/CAtlMap::GetNextAssoc.md)|Obtiene el elemento siguiente para recorrer.|  
|[CAtlMap::GetNextKey](../Topic/CAtlMap::GetNextKey.md)|Llame a este método para recuperar la siguiente clave del objeto de `CAtlMap` .|  
|[CAtlMap::GetNextValue](../Topic/CAtlMap::GetNextValue.md)|Llame a este método para obtener el siguiente valor de objeto de `CAtlMap` .|  
|[CAtlMap::GetStartPosition](../Topic/CAtlMap::GetStartPosition.md)|Llame a este método para iniciar una iteración del mapa.|  
|[CAtlMap::GetValueAt](../Topic/CAtlMap::GetValueAt.md)|Llame a este método para recuperar el valor almacenado en una posición determinada del objeto de `CAtlMap` .|  
|[CAtlMap::InitHashTable](../Topic/CAtlMap::InitHashTable.md)|Llame a este método para inicializar la tabla hash.|  
|[CAtlMap::IsEmpty](../Topic/CAtlMap::IsEmpty.md)|Llame a este método para probar un objeto de mapa vacío.|  
|[CAtlMap::Lookup](../Topic/CAtlMap::Lookup.md)|Llame a este método para buscar las claves o valores en el objeto de `CAtlMap` .|  
|[CAtlMap::Rehash](../Topic/CAtlMap::Rehash.md)|Llame a este método a la refundición el objeto de `CAtlMap` .|  
|[CAtlMap::RemoveAll](../Topic/CAtlMap::RemoveAll.md)|Llame a este método para quitar todos los elementos del objeto de `CAtlMap` .|  
|[CAtlMap::RemoveAtPos](../Topic/CAtlMap::RemoveAtPos.md)|Llame a este método para quitar el elemento en la posición especificada en el objeto de `CAtlMap` .|  
|[CAtlMap::RemoveKey](../Topic/CAtlMap::RemoveKey.md)|Llame a este método para quitar un elemento de objeto de `CAtlMap` , dada la clave.|  
|[CAtlMap::SetAt](../Topic/CAtlMap::SetAt.md)|Llame a este método para insertar un par de elementos del mapa.|  
|[CAtlMap::SetOptimalLoad](../Topic/CAtlMap::SetOptimalLoad.md)|Llame a este método para establecer la carga óptima del objeto de `CAtlMap` .|  
|[CAtlMap::SetValueAt](../Topic/CAtlMap::SetValueAt.md)|Llame a este método para cambiar el valor almacenado en una posición determinada del objeto de `CAtlMap` .|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAtlMap::operator](../Topic/CAtlMap::operator.md)|Reemplaza o agrega un nuevo elemento a `CAtlMap`.|  
  
## Comentarios  
 `CAtlMap` proporciona compatibilidad para una matriz de asignación de tipo, administrar una matriz desordenado de elementos clave y sus valores asociados.  Los elementos \(se compone de una clave y un valor\) se almacenan utilizando un algoritmo hash, lo que recuperans grandes volúmenes de datos eficazmente están almacenados y.  
  
 Los parámetros de `KTraits` y de `VTraits` son clases de con los que contienen cualquier código complementario necesario para copiar o mover elementos.  
  
 Una alternativa a `CAtlMap` proporciona la clase de [CRBMap](../../atl/reference/crbmap-class.md) .  De`CRBMap` los pares clave\-valor de almacenes también, pero presentan distintas características de rendimiento.  El tiempo que se tarda en insertar un elemento, para buscar una clave, o para eliminar una clave de un objeto de `CRBMap` tiene el *registro\(n\)*, donde *n* es el número de elementos.  Para `CAtlMap`, todas estas operaciones requieren normalmente un tiempo constante, aunque los escenarios pesimista pueden ser de orden *n*.  Por consiguiente, en un caso típico, `CAtlMap` es más rápido.  
  
 Otra diferencia entre `CRBMap` y `CAtlMap` se hace evidente al recorrer en iteración los elementos almacenados.  En `CRBMap`, los elementos se visitan en un forma ordenada.  En `CAtlMap`, los elementos no se ordenan, y ningún orden puede deducir.  
  
 Cuando una pequeña cantidad de elementos deben estar almacenados, considere la clase de [CSimpleMap](../../atl/reference/csimplemap-class.md) en su lugar.  
  
 Para obtener más información, vea [clases de colección de ATL](../../atl/atl-collection-classes.md).  
  
## Requisitos  
 **encabezado:** atlcoll.h  
  
## Vea también  
 [Ejemplo de la marquesina](../../top/visual-cpp-samples.md)   
 [Ejemplo UpdatePV](../../top/visual-cpp-samples.md)   
 [Class Overview](../../atl/atl-class-overview.md)