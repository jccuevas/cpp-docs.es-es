---
title: "CObArray Class | Microsoft Docs"
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
  - "CObArray"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "matrices [C++], Object (tipo)"
  - "matrices [C++], punteros"
  - "CObArray class"
  - "matrices de objetos, CObArray class"
ms.assetid: 27894efd-2370-4776-9ed9-24a98492af17
caps.latest.revision: 20
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CObArray Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

admite las matrices de los punteros de `CObject` .  
  
## Sintaxis  
  
```  
class CObArray : public CObject  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CObArray::CObArray](../Topic/CObArray::CObArray.md)|Crea una matriz vacía para punteros de `CObject` .|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CObArray::Add](../Topic/CObArray::Add.md)|Agrega un elemento al final de la matriz; aumenta la matriz en caso necesario.|  
|[CObArray::Append](../Topic/CObArray::Append.md)|Anexa otra matriz a la matriz; aumenta la matriz en caso necesario.|  
|[CObArray::Copy](../Topic/CObArray::Copy.md)|Copia otra matriz a la matriz; aumenta la matriz en caso necesario.|  
|[CObArray::ElementAt](../Topic/CObArray::ElementAt.md)|Devuelve una referencia temporal a puntero de elemento dentro de la matriz.|  
|[CObArray::FreeExtra](../Topic/CObArray::FreeExtra.md)|Libera toda la memoria no utilizada sobre el límite superior actual.|  
|[CObArray::GetAt](../Topic/CObArray::GetAt.md)|Devuelve el valor en el índice especificado.|  
|[CObArray::GetCount](../Topic/CObArray::GetCount.md)|Obtiene el número de elementos en esta matriz.|  
|[CObArray::GetData](../Topic/CObArray::GetData.md)|Permite el acceso a los elementos de la matriz.  puede ser **NULL**.|  
|[CObArray::GetSize](../Topic/CObArray::GetSize.md)|Obtiene el número de elementos en esta matriz.|  
|[CObArray::GetUpperBound](../Topic/CObArray::GetUpperBound.md)|Devuelve el índice válido mayor.|  
|[CObArray::InsertAt](../Topic/CObArray::InsertAt.md)|Inserta un elemento \(o todos los elementos en otra matriz\) en el índice especificado.|  
|[CObArray::IsEmpty](../Topic/CObArray::IsEmpty.md)|Determina si la matriz está vacía.|  
|[CObArray::RemoveAll](../Topic/CObArray::RemoveAll.md)|Quita todos los elementos de esta matriz.|  
|[CObArray::RemoveAt](../Topic/CObArray::RemoveAt.md)|quita un elemento en un índice específico.|  
|[CObArray::SetAt](../Topic/CObArray::SetAt.md)|Establece el valor en el índice especificado; matriz no permitido crecer.|  
|[CObArray::SetAtGrow](../Topic/CObArray::SetAtGrow.md)|Establece el valor en el índice especificado; aumenta la matriz en caso necesario.|  
|[CObArray::SetSize](../Topic/CObArray::SetSize.md)|Establece el número de elementos que se contendrán en esta matriz.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CObArray::operator](../Topic/CObArray::operator.md)|Establece u obtiene el elemento en el índice especificado.|  
  
## Comentarios  
 Estas matrices de objetos son similares a las matrices de C, pero pueden reducir y crecer dinámicamente según sea necesario.  
  
 Los índices de matriz siempre empiezan en la posición 0.  Puede decidir si corregir el límite superior o permitir que la matriz expanda cuando agregue elementos más allá de la actual enlazada.  La memoria se asigna uno junto al límite superior, aunque algunos elementos es null.  
  
 En Win32, el tamaño de un objeto de `CObArray` está restringida sólo a la memoria disponible.  
  
 Como con la matriz de C\/C\+\+., tiempo de acceso para un elemento indizado `CObArray` es constante y es independiente del tamaño de la matriz.  
  
 `CObArray` escribe la macro de `IMPLEMENT_SERIAL` para admitir la serialización y volcar de sus elementos.  Si una matriz de punteros de `CObject` se almacena en un archivo, con el operador sobrecargado de inserción o con la función miembro de `Serialize` , cada elemento de `CObject` , a su vez, se serializa junto con su índice de matriz.  
  
 Si necesita un volcado de memoria de los elementos individuales de `CObject` en una matriz, debe establecer la profundidad del objeto de `CDumpContext` en 1 o posterior.  
  
 Cuando se elimina un objeto de `CObArray` , o cuando se quitan los elementos, solo se quitan los punteros de `CObject` , no objetos que hacen referencia.  
  
> [!NOTE]
>  Antes de utilizar una matriz, utilice `SetSize` para establecer su tamaño y para asignar memoria para ella.  Si no utiliza `SetSize`, agregar elementos a la matriz hace con frecuencia que se reasignara y copiar.  La reasignación frecuente y la copia son ineficaces y pueden fragmentar la memoria.  
  
 Derivación de la clase array es similar a la derivación de lista.  Para obtener detalles sobre la derivación de una clase especial de la lista, vea el artículo [colecciones](../../mfc/collections.md).  
  
> [!NOTE]
>  Debe utilizar la macro de `IMPLEMENT_SERIAL` en la implementación de la clase derivada si desea serializar la matriz.  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CObArray`  
  
## Requisitos  
 **encabezado:** afxcoll.h  
  
## Vea también  
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CStringArray Class](../../mfc/reference/cstringarray-class.md)   
 [CPtrArray Class](../../mfc/reference/cptrarray-class.md)   
 [CByteArray Class](../../mfc/reference/cbytearray-class.md)   
 [CWordArray Class](../../mfc/reference/cwordarray-class.md)   
 [CDWordArray Class](../../mfc/reference/cdwordarray-class.md)