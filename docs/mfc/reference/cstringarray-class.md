---
title: "CStringArray Class | Microsoft Docs"
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
  - "CStringArray"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "matrices [C++], cadenas"
  - "CStringArray class"
  - "string arrays"
  - "cadenas [C++], colecciones"
ms.assetid: 6c637e06-bba8-4c08-b0fc-cf8cb067ce34
caps.latest.revision: 24
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CStringArray Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Admite matrices de objetos [CString](../../atl-mfc-shared/using-cstring.md).  
  
## Sintaxis  
  
```  
class CStringArray : public CObject  
```  
  
## Miembros  
 Las funciones miembro de `CStringArray` son similares a las funciones miembro de la clase [CObArray](../../mfc/reference/cobarray-class.md).  Debido a esta similitud, puede utilizar la documentación de referencia de `CObArray` para obtener información específica de la función miembro.  Siempre que vea un puntero `CObject` como valor devuelto, use un objeto [CString](../../atl-mfc-shared/using-cstring.md) \(no un puntero [CString](../../atl-mfc-shared/using-cstring.md)\).  Siempre que vea un puntero `CObject` como un parámetro de función, use un `LPCTSTR`.  
  
 `CObject* CObArray::GetAt( int <nIndex> ) const;`  
  
 por ejemplo, se traduce en  
  
 `CString CStringArray::GetAt( int <nIndex> ) const;`  
  
 y  
  
 `void SetAt( int <nIndex>, CObject* <newElement> )`  
  
 se traduce en  
  
 `void SetAt( int <nIndex>, LPCTSTR <newElement> )`  
  
### Constructores públicos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[CObArray::CObArray](../Topic/CObArray::CObArray.md)|Construye una matriz vacía.|  
  
### Métodos públicos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[CObArray::Add](../Topic/CObArray::Add.md)|Agrega un elemento al final de la matriz; aumenta el tamaño de la matriz si es necesario.|  
|[CObArray::Append](../Topic/CObArray::Append.md)|Anexa otra matriz a la matriz; aumenta el tamaño de la matriz si es necesario.|  
|[CObArray::Copy](../Topic/CObArray::Copy.md)|Copia otra matriz a la matriz; aumenta el tamaño de la matriz si es necesario.|  
|[CObArray::ElementAt](../Topic/CObArray::ElementAt.md)|Devuelve una referencia temporal al puntero del elemento dentro de la matriz.|  
|[CObArray::FreeExtra](../Topic/CObArray::FreeExtra.md)|Libera toda la memoria no usada por encima del límite superior actual.|  
|[CObArray::GetAt](../Topic/CObArray::GetAt.md)|Devuelve el valor en un índice dado.|  
|[CObArray::GetCount](../Topic/CObArray::GetCount.md)|Obtiene el número de elementos de esta matriz.|  
|[CObArray::GetData](../Topic/CObArray::GetData.md)|Permite el acceso a los elementos de la matriz.  Puede ser **NULL**.|  
|[CObArray::GetSize](../Topic/CObArray::GetSize.md)|Obtiene el número de elementos de esta matriz.|  
|[CObArray::GetUpperBound](../Topic/CObArray::GetUpperBound.md)|Devuelve el índice válido de mayor tamaño.|  
|[CObArray::InsertAt](../Topic/CObArray::InsertAt.md)|Inserta un elemento \(o todos los elementos de otra matriz\) en un índice especificado.|  
|[CObArray::IsEmpty](../Topic/CObArray::IsEmpty.md)|Determina si la matriz está vacía.|  
|[CObArray::RemoveAll](../Topic/CObArray::RemoveAll.md)|Quita todos los elementos de esta matriz.|  
|[CObArray::RemoveAt](../Topic/CObArray::RemoveAt.md)|Quita un elemento en un índice específico.|  
|[CObArray::SetAt](../Topic/CObArray::SetAt.md)|Establece el valor de un índice dado; la matriz no puede aumentar de tamaño.|  
|[CObArray::SetAtGrow](../Topic/CObArray::SetAtGrow.md)|Establece el valor de un índice dado; aumenta el tamaño de la matriz si es necesario.|  
|[CObArray::SetSize](../Topic/CObArray::SetSize.md)|Establece el número de elementos que contendrá esta matriz.|  
  
### Operadores públicos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[CObArray::operator](../Topic/CObArray::operator.md)|Establece u obtiene el elemento en el índice especificado.|  
  
## Comentarios  
 `CStringArray` incorpora la macro `IMPLEMENT_SERIAL` para admitir la serialización y el volcado de sus elementos.  Si una matriz de objetos `CString` se almacena en un archivo, bien con un operador de inserción sobrecargado, o bien con la función miembro `Serialize`, cada elemento se serializa a su vez.  
  
> [!NOTE]
>  Antes de usar una matriz, use `SetSize` para establecer su tamaño y asignarle memoria.  Si no usa `SetSize`, al agregar elementos a la matriz, esta se reasigna y se copia con frecuencia.  La reasignación y copia frecuentes son ineficaces y pueden fragmentar la memoria.  
  
 Si se necesita un volcado de elementos de cadena individuales en la matriz, se debe establecer la profundidad del contexto de volcado en 1 o un valor superior.  
  
 Cuando se elimina una matriz `CString` o cuando se quitan sus elementos, se libera memoria de cadenas según corresponda.  
  
 Para obtener más información sobre cómo utilizar `CStringArray`, vea el artículo [Colecciones](../../mfc/collections.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CStringArray`  
  
## Requisitos  
 **Encabezado:** afxcoll.h  
  
## Vea también  
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)