---
title: "CWordArray Class | Microsoft Docs"
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
  - "CWordArray"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "matrices [C++], indizadas"
  - "CWordArray class"
  - "indexed arrays"
  - "INT"
  - "UINT"
  - "WORD data type"
ms.assetid: 2ba2c194-2c6c-40ff-9db4-e9dbe57e1f57
caps.latest.revision: 26
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CWordArray Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Admite matrices de palabras de 16 bits.  
  
## Sintaxis  
  
```  
class CWordArray : public CObject  
```  
  
## Miembros  
 Las funciones miembro de `CWordArray` son similares a las funciones miembro de clases [CObArray](../../mfc/reference/cobarray-class.md).  Debido a esta similitud, puede utilizar la documentación de referencia de `CObArray` para las características de la función miembro.  Siempre que aparezca un puntero de [CObject](../../mfc/reference/cobject-class.md) como un parámetro o valor devuelto de la función, sustituya **WORD**.  
  
 `CObject* CObArray::GetAt( int <nIndex> ) const;`  
  
 por ejemplo, convierte a  
  
 `WORD CWordArray::GetAt( int <nIndex> ) const;`  
  
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
 `CWordArray` escribe la macro de [IMPLEMENT\_SERIAL](../Topic/IMPLEMENT_SERIAL.md) para admitir la serialización y volcar de sus elementos.  Si una matriz de palabras se almacena en un archivo, con un operador sobrecargado de inserción o con la función miembro de [CObject::Serialize](../Topic/CObject::Serialize.md) , cada elemento, a su vez, se serializa.  
  
> [!NOTE]
>  Antes de utilizar una matriz, utilice `SetSize` para establecer su tamaño y para asignar memoria para ella.  Si no utiliza `SetSize`, agregar elementos a la matriz hace con frecuencia que se reasignara y copiar.  La reasignación frecuente y la copia son ineficaces y pueden fragmentar la memoria.  
  
 Si necesita un volcado de memoria de elementos individuales de la matriz, debe establecer el nivel de contexto de volcado de memoria en 1 o posterior.  
  
 Para obtener más información sobre cómo utilizar `CWordArray`, vea el artículo [colecciones](../../mfc/collections.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CWordArray`  
  
## Requisitos  
 **encabezado:** afxcoll.h  
  
## Vea también  
 [El ejemplo de MFC como GET](../../top/visual-cpp-samples.md)   
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)