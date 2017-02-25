---
title: "CAtlArray Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::CAtlArray"
  - "ATL.CAtlArray"
  - "CAtlArray"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAtlArray class"
ms.assetid: 0b503aa8-2357-40af-a326-6654bf1da098
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CAtlArray Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase implementa un objeto array.  
  
## Sintaxis  
  
```  
  
      template<   
   typename E,  
   class ETraits = CElementTraits< E >   
>  
class CAtlArray  
```  
  
#### Parámetros  
 *E*  
 El tipo de datos que se almacenan en la matriz.  
  
 *ETraits*  
 El código utilizado para copiar o mover elementos.  
  
## Members  
  
### Métodos  
  
|||  
|-|-|  
|[Agregar](../Topic/CAtlArray::Add.md)|Llame a este método para agregar un elemento al objeto array.|  
|[Append](../Topic/CAtlArray::Append.md)|Llame a este método para agregar el contenido de una matriz al final de otro.|  
|[AssertValid](../Topic/CAtlArray::AssertValid.md)|Llame a este método para confirmar que el objeto de matriz es válido.|  
|[CAtlArray](../Topic/CAtlArray::CAtlArray.md)|el constructor.|  
|[~CAtlArray](../Topic/CAtlArray::~CAtlArray.md)|El destructor.|  
|[Copiar](../Topic/CAtlArray::Copy.md)|Llame a este método para copiar los elementos de una matriz a otra.|  
|[FreeExtra](../Topic/CAtlArray::FreeExtra.md)|Llame a este método para quitar cualquier los elementos vacíos de la matriz.|  
|[GetAt](../Topic/CAtlArray::GetAt.md)|Llame a este método para recuperar un único elemento de objeto de matriz.|  
|[GetCount](../Topic/CAtlArray::GetCount.md)|Llame a este método para devolver el número de elementos almacenados en la matriz.|  
|[GetData](../Topic/CAtlArray::GetData.md)|Llame a este método para devolver un puntero al primer elemento de la matriz.|  
|[InsertArrayAt](../Topic/CAtlArray::InsertArrayAt.md)|Llame a este método para insertar una matriz en otro.|  
|[InsertAt](../Topic/CAtlArray::InsertAt.md)|Llame a este método para insertar un nuevo elemento \(o varias copias de un elemento\) en el objeto array.|  
|[IsEmpty](../Topic/CAtlArray::IsEmpty.md)|Llame a este método para comprobar si la matriz está vacía.|  
|[RemoveAll](../Topic/CAtlArray::RemoveAll.md)|Llame a este método para quitar todos los elementos del objeto array.|  
|[RemoveAt](../Topic/CAtlArray::RemoveAt.md)|Llame a este método para quitar uno o más elementos de la matriz.|  
|[SetAt](../Topic/CAtlArray::SetAt.md)|Llame a este método para establecer el valor de un elemento en el objeto array.|  
|[SetAtGrow](../Topic/CAtlArray::SetAtGrow.md)|Llame a este método para establecer el valor de un elemento del objeto array, expandiendo la matriz como sea necesario.|  
|[SetCount](../Topic/CAtlArray::SetCount.md)|Llame a este método para establecer el tamaño del objeto array.|  
  
### Operadores  
  
|||  
|-|-|  
|[operator &#91;&#93;](../Topic/CAtlArray::operator.md)|Asigne a este operador para devolver una referencia a un elemento de la matriz.|  
  
### Typedefs  
  
|||  
|-|-|  
|[INARGTYPE](../Topic/CAtlArray::INARGTYPE.md)|El tipo de datos para agregar elementos a la matriz.|  
|[OUTARGTYPE](../Topic/CAtlArray::OUTARGTYPE.md)|El tipo de datos para recuperar elementos de la matriz.|  
  
## Comentarios  
 **CAtlArray** proporciona métodos para crear y administrar una matriz de elementos de un tipo definido por el usuario.  Aunque es similar a las matrices estándar de C, el objeto de **CAtlArray** puede reducir y crecer dinámicamente según sea necesario.  El índice de matriz siempre comienza en la posición 0, y el límite superior se puede corregir, o permitir expandir a medida que se agregan los nuevos elementos.  
  
 Para las matrices con una pequeña cantidad de elementos, la clase [CSimpleArray](../../atl/reference/csimplearray-class.md) ATL se puede usar.  
  
 **CAtlArray** está estrechamente relacionado con la clase de **CArray** de MFC y funcionará en un proyecto MFC, sin embargo sin compatibilidad de serialización.  
  
 Para obtener más información, vea [clases de colección de ATL](../../atl/atl-collection-classes.md).  
  
## Requisitos  
 **encabezado:** atlcoll.h  
  
## Vea también  
 [Ejemplo MMXSwarm](../../top/visual-cpp-samples.md)   
 [Ejemplo DynamicConsumer](../../top/visual-cpp-samples.md)   
 [Ejemplo UpdatePV](../../top/visual-cpp-samples.md)   
 [Ejemplo de la marquesina](../../top/visual-cpp-samples.md)   
 [CArray Class](../../mfc/reference/carray-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)