---
title: "CSimpleArray Class | Microsoft Docs"
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
  - "ATL.CSimpleArray"
  - "ATL::CSimpleArray"
  - "CSimpleArray"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSimpleArray class"
ms.assetid: ee0c9f39-b61c-4c18-bc43-4eada21dca3a
caps.latest.revision: 20
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CSimpleArray Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase proporciona métodos para administrar una simple matriz.  
  
## Sintaxis  
  
```  
  
      template <  
   class T,  
   class TEqual = CSimpleArrayEqualHelper< T >  
>   
class CSimpleArray  
```  
  
#### Parámetros  
 `T`  
 El tipo de datos a almacenar en la matriz.  
  
 `TEqual`  
 Un objeto de característica, definiendo la prueba de igualdad para los elementos de `T`escrito.  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CSimpleArray::CSimpleArray](../Topic/CSimpleArray::CSimpleArray.md)|El constructor para la matriz simple.|  
|[CSimpleArray::~CSimpleArray](../Topic/CSimpleArray::~CSimpleArray.md)|El destructor para la matriz simple.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CSimpleArray::Add](../Topic/CSimpleArray::Add.md)|Agrega un nuevo elemento en la matriz.|  
|[CSimpleArray::Find](../Topic/CSimpleArray::Find.md)|Busca un elemento en la matriz.|  
|[CSimpleArray::GetData](../Topic/CSimpleArray::GetData.md)|Devuelve un puntero a los datos almacenados en la matriz.|  
|[CSimpleArray::GetSize](../Topic/CSimpleArray::GetSize.md)|Devuelve el número de elementos almacenados en la matriz.|  
|[CSimpleArray::Remove](../Topic/CSimpleArray::Remove.md)|Quita un elemento especificado de la matriz.|  
|[CSimpleArray::RemoveAll](../Topic/CSimpleArray::RemoveAll.md)|Quita todos los elementos de la matriz.|  
|[CSimpleArray::RemoveAt](../Topic/CSimpleArray::RemoveAt.md)|Quita el elemento especificado de la matriz.|  
|[CSimpleArray::SetAtIndex](../Topic/CSimpleArray::SetAtIndex.md)|Establece el elemento especificado de la matriz.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CSimpleArray::operator](../Topic/CSimpleArray::operator.md)|Recupera un elemento de matriz.|  
|[CSimpleArray::operator \=](../Topic/CSimpleArray::operator%20=.md)|Operador de asignación.|  
  
## Comentarios  
 `CSimpleArray` proporciona métodos para crear y administrar una matriz simple, de cualquier tipo especificado `T`.  
  
 El parámetro `TEqual` proporciona un medio para definir una función de igualdad de dos elementos de `T`escrito.  Creando una clase similar a [CSimpleArrayEqualHelper](../../atl/reference/csimplearrayequalhelper-class.md), es posible modificar el comportamiento de la prueba de igualdad para cualquier matriz especificado.  Por ejemplo, al trabajar con una matriz de punteros, puede ser útil definir la igualdad como dependiendo de los valores punteros hacen referencia.  la implementación predeterminada utiliza **operator\= \(\)**.  
  
 `CSimpleArray` y [CSimpleMap](../../atl/reference/csimplemap-class.md) están diseñados para una pequeña cantidad de elementos.  [CAtlArray](../../atl/reference/catlarray-class.md) y [CAtlMap](../../atl/reference/catlmap-class.md) deben utilizar cuando la matriz contiene un gran número de elementos.  
  
## Requisitos  
 **encabezado:** atlsimpcoll.h  
  
## Ejemplo  
 [!code-cpp[NVC_ATL_Utilities#86](../../atl/codesnippet/CPP/csimplearray-class_1.cpp)]  
  
## Vea también  
 [Class Overview](../../atl/atl-class-overview.md)