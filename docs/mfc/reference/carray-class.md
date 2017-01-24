---
title: "CArray Class | Microsoft Docs"
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
  - "CArray"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "matrices [C++], clases"
  - "CArray class"
  - "clases de colección, template-based"
  - "plantillas, clases de colección"
ms.assetid: fead8b00-4cfd-4625-ad0e-251df62ba92f
caps.latest.revision: 33
caps.handback.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CArray Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Admite matrices que son como las matrices de C, pero puede reducir y crecer dinámicamente según sea necesario.  
  
## Sintaxis  
  
```  
template < class TYPE, class ARG_TYPE = const TYPE& >   
class CArray :   
   public CObject  
```  
  
#### Parámetros  
 `TYPE`  
 El parámetro de plantilla que especifica el tipo de objetos almacenados en la matriz.  `TYPE` es un parámetro devuelto por `CArray`.  
  
 `ARG` *\_* `TYPE`  
 El parámetro de plantilla que especifica el argumento escribe que se utiliza para tener acceso a los objetos almacenados en la matriz.  a menudo una referencia a `TYPE`.  `ARG_TYPE` es un parámetro que se pasa a `CArray`.  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CArray::CArray](../Topic/CArray::CArray.md)|Crea una matriz vacía.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CArray::Add](../Topic/CArray::Add.md)|Agrega un elemento al final de la matriz; aumenta la matriz en caso necesario.|  
|[CArray::Append](../Topic/CArray::Append.md)|Anexa otra matriz a la matriz; aumenta la matriz en caso necesario|  
|[CArray::Copy](../Topic/CArray::Copy.md)|Copia otra matriz a la matriz; aumenta la matriz en caso necesario.|  
|[CArray::ElementAt](../Topic/CArray::ElementAt.md)|Devuelve una referencia temporal a puntero de elemento dentro de la matriz.|  
|[CArray::FreeExtra](../Topic/CArray::FreeExtra.md)|Libera toda la memoria no utilizada sobre el límite superior actual.|  
|[CArray::GetAt](../Topic/CArray::GetAt.md)|Devuelve el valor en el índice especificado.|  
|[CArray::GetCount](../Topic/CArray::GetCount.md)|Obtiene el número de elementos en esta matriz.|  
|[CArray::GetData](../Topic/CArray::GetData.md)|Permite el acceso a los elementos de la matriz.  puede ser **NULL**.|  
|[CArray::GetSize](../Topic/CArray::GetSize.md)|Obtiene el número de elementos en esta matriz.|  
|[CArray::GetUpperBound](../Topic/CArray::GetUpperBound.md)|Devuelve el índice válido mayor.|  
|[CArray::InsertAt](../Topic/CArray::InsertAt.md)|Inserta un elemento \(o todos los elementos en otra matriz\) en el índice especificado.|  
|[CArray::IsEmpty](../Topic/CArray::IsEmpty.md)|Determina si la matriz está vacía.|  
|[CArray::RemoveAll](../Topic/CArray::RemoveAll.md)|Quita todos los elementos de esta matriz.|  
|[CArray::RemoveAt](../Topic/CArray::RemoveAt.md)|quita un elemento en un índice específico.|  
|[CArray::SetAt](../Topic/CArray::SetAt.md)|Establece el valor en el índice especificado; matriz no permitido crecer.|  
|[CArray::SetAtGrow](../Topic/CArray::SetAtGrow.md)|Establece el valor en el índice especificado; aumenta la matriz en caso necesario.|  
|[CArray::SetSize](../Topic/CArray::SetSize.md)|Establece el número de elementos que se contendrán en esta matriz.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CArray::operator](../Topic/CArray::operator.md)|Establece u obtiene el elemento en el índice especificado.|  
  
## Comentarios  
 Los índices de matriz siempre empiezan en la posición 0.  Puede decidir si corregir el límite superior o permitir a la matriz para expandir cuando agregue elementos más allá del límite de la actual.  La memoria se asigna uno junto al límite superior, aunque algunos elementos es null.  
  
> [!NOTE]
>  La mayoría de los métodos que cambian el tamaño de un objeto de `CArray` o agregue elementos al uso [memcpy\_s](../../c-runtime-library/reference/memcpy-s-wmemcpy-s.md) a los elementos de movimiento.  Esto supone un problema porque `memcpy_s` no es compatible con ningún objeto que requieren el constructor llamar.  Si los elementos de `CArray` no son compatibles con `memcpy_s`, debe crear un nuevo `CArray` de tamaño adecuado.  Debe utilizar [CArray::Copy](../Topic/CArray::Copy.md) y [CArray::SetAt](../Topic/CArray::SetAt.md) para rellenar la nueva matriz porque esos métodos utilizan un operador de asignación en lugar de `memcpy_s`.  
  
 Como con la matriz de C\/C\+\+., tiempo de acceso para un elemento indizado `CArray` es constante y es independiente del tamaño de la matriz.  
  
> [!TIP]
>  Antes de utilizar una matriz, utilice [SetSize](../Topic/CArray::SetSize.md) para establecer su tamaño y para asignar memoria para ella.  Si no utiliza `SetSize`, agregar elementos a la matriz hace con frecuencia que se reasignara y copiar.  La reasignación frecuente y la copia son ineficaces y pueden fragmentar la memoria.  
  
 Si necesita un volcado de elementos individuales en una matriz, debe establecer la profundidad del objeto de [CDumpContext](../../mfc/reference/cdumpcontext-class.md) a 1 o mayor.  
  
 Algunas funciones miembro de las funciones globales de esta de la clase auxiliar de llamada que se deben personalizar para la mayoría de utilizan la clase de `CArray` .  Vea el tema [aplicaciones auxiliares de la clase de colección](../../mfc/reference/collection-class-helpers.md) en la sección de macros y Globals MFC.  
  
 Derivación de la clase array es como la derivación de lista.  
  
 Para obtener más información sobre cómo utilizar `CArray`, vea el artículo [colecciones](../../mfc/collections.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CArray`  
  
## Requisitos  
 `Header:` afxtempl.h  
  
## Vea también  
 [El ejemplo de MFC como GET](../../top/visual-cpp-samples.md)   
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CObArray Class](../../mfc/reference/cobarray-class.md)   
 [Aplicaciones auxiliares de clase de colección](../../mfc/reference/collection-class-helpers.md)