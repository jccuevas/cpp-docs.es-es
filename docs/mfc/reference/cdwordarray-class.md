---
title: "CDWordArray Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CDWordArray"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDWordArray class"
  - "CObArray class, CDWordArray"
  - "doublewords"
  - "doublewords, array of"
ms.assetid: 581be11e-ced6-47d1-8679-e0b8e7d99494
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# CDWordArray Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Admite matrices de palabras dobles de 32 bits.  
  
## Sintaxis  
  
```  
class CDWordArray : public CObject  
```  
  
## Members  
 Las funciones miembro de `CDWordArray` son similares a las funciones miembro de clases [CObArray](../../mfc/reference/cobarray-class.md).  Debido a esta similitud, puede utilizar la documentación de referencia de `CObArray` para las características de la función miembro.  Siempre que aparezca un puntero de `CObject` como un parámetro o valor devuelto de la función, sustituya `DWORD`.  
  
 `CObject* CObArray::GetAt( int <nIndex> ) const;`  
  
 por ejemplo, convierte a  
  
 `DWORD CDWordArray::GetAt( int <nIndex> ) const;`  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CObArray::CObArray](../Topic/CObArray::CObArray.md)|Crea una matriz vacía.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CObArray::Add](../Topic/CObArray::Add.md)|Agrega un elemento al final de la matriz; aumenta la matriz en caso necesario.|  
|[CObArray::Append](../Topic/CObArray::Append.md)|Anexa otra matriz a la matriz; aumenta la matriz en caso necesario.|  
|[CObArray::Copy](../Topic/CObArray::Copy.md)|Copia otra matriz a la matriz; aumenta la matriz en caso necesario.|  
|[CObArray::ElementAt](../Topic/CObArray::ElementAt.md)|Devuelve una referencia temporal a byte dentro de la matriz.|  
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
 `CDWordArray` escribe la macro de `IMPLEMENT_SERIAL` para admitir la serialización y volcar de sus elementos.  Si una matriz de palabras dobles se almacena en un archivo, con el operador sobrecargado de inserción \(**\<\<**\) o con la función miembro de `Serialize` , cada elemento, a su vez, se serializa.  
  
> [!NOTE]
>  Antes de utilizar una matriz, utilice `SetSize` para establecer su tamaño y para asignar memoria para ella.  Si no utiliza `SetSize`, agregar elementos a la matriz hace con frecuencia que se reasignara y copiar.  La reasignación frecuente y la copia son ineficaces y pueden fragmentar la memoria.  
  
 Si necesita depuración generar de elementos individuales de la matriz, debe establecer la profundidad del objeto de `CDumpContext` en 1 o posterior.  
  
 Para obtener más información sobre cómo utilizar `CDWordArray`, vea el artículo [colecciones](../../mfc/collections.md).  
  
## Requisitos  
 **encabezado:** afxcoll.h  
  
## Vea también  
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CObArray Class](../../mfc/reference/cobarray-class.md)