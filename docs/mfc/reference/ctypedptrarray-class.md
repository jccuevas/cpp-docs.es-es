---
title: "CTypedPtrArray Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CTypedPtrArray"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CTypedPtrArray class"
  - "pointer arrays"
ms.assetid: e3ecdf1a-a889-4156-92dd-ddbd36ccd919
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CTypedPtrArray Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Proporciona un “contenedor seguro” para los objetos de la clase `CPtrArray` o `CObArray`.  
  
## Sintaxis  
  
```  
template< class BASE_CLASS, class TYPE >  
class CTypedPtrArray : public BASE_CLASS  
```  
  
#### Parámetros  
 `BASE_CLASS`  
 Clase base del tipo de clase de la matriz de puntero; debe ser una clase array \(`CObArray` o `CPtrArray`\).  
  
 `TYPE`  
 Tipo de los elementos almacenados en la matriz de la clase base.  
  
## Miembros  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CTypedPtrArray::Add](../Topic/CTypedPtrArray::Add.md)|Agrega un nuevo elemento al final de una matriz.  Aumenta la matriz en caso necesario|  
|[CTypedPtrArray::Append](../Topic/CTypedPtrArray::Append.md)|Agrega el contenido de una matriz al final de otro.  Aumenta la matriz en caso necesario|  
|[CTypedPtrArray::Copy](../Topic/CTypedPtrArray::Copy.md)|Copia otra matriz a la matriz; aumenta la matriz en caso necesario.|  
|[CTypedPtrArray::ElementAt](../Topic/CTypedPtrArray::ElementAt.md)|Devuelve una referencia temporal a puntero de elemento dentro de la matriz.|  
|[CTypedPtrArray::GetAt](../Topic/CTypedPtrArray::GetAt.md)|Devuelve el valor en el índice especificado.|  
|[CTypedPtrArray::InsertAt](../Topic/CTypedPtrArray::InsertAt.md)|Inserta un elemento \(o todos los elementos en otra matriz\) en el índice especificado.|  
|[CTypedPtrArray::SetAt](../Topic/CTypedPtrArray::SetAt.md)|Establece el valor en el índice especificado; matriz no permitido crecer.|  
|[CTypedPtrArray::SetAtGrow](../Topic/CTypedPtrArray::SetAtGrow.md)|Establece el valor en el índice especificado; aumenta la matriz en caso necesario.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CTypedPtrArray::operator](../Topic/CTypedPtrArray::operator.md)|Establece u obtiene el elemento en el índice especificado.|  
  
## Comentarios  
 Cuando se utiliza `CTypedPtrArray` en lugar de `CPtrArray` o `CObArray`, ayuda a facilitar la comprobación de tipos de C\+\+ eliminan los errores producidos por los tipos de puntero no coincidentes.  
  
 Además, el contenedor de `CTypedPtrArray` realiza muchos del marco que es obligatorio si utilizó `CObArray` o `CPtrArray`.  
  
 Dado que todas las funciones de `CTypedPtrArray` inline, el uso de esta plantilla no afecta significativamente el tamaño o la velocidad del código.  
  
 Para obtener más información sobre cómo utilizar `CTypedPtrArray`, vea los artículos [colecciones](../../mfc/collections.md) y [Clases basadas en plantillas](../../mfc/template-based-classes.md).  
  
## Jerarquía de herencia  
 `BASE_CLASS`  
  
 `CTypedPtrArray`  
  
## Requisitos  
 **encabezado:** afxtempl.h  
  
## Vea también  
 [El ejemplo de MFC como GET](../../top/visual-cpp-samples.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CPtrArray Class](../../mfc/reference/cptrarray-class.md)   
 [CObArray Class](../../mfc/reference/cobarray-class.md)