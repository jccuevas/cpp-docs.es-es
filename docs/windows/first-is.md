---
title: "first_is | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc-attr.first_is"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "first_is attribute"
ms.assetid: 89acbf56-3b38-4d44-83e8-1ce2f6f74ffd
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# first_is
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Especifica el índice del primer elemento de matriz que se transmitirá.  
  
## Sintaxis  
  
```  
  
      [ first_is(  
   "expression"  
) ]  
```  
  
#### Parámetros  
 *expresión*  
 Una o más expresiones del lenguaje C.  Se permiten las ranuras vacías del argumento.  
  
## Comentarios  
 el atributo de **first\_is** C\+\+ tiene la misma funcionalidad que el atributo de [first\_is](http://msdn.microsoft.com/library/windows/desktop/aa366831) MIDL.  
  
## Ejemplo  
 El código siguiente se muestran varias maneras de especificar una sección en una matriz:  
  
```  
// cpp_attr_ref_first_is.cpp  
// compile with: /LD  
#include "windows.h"  
#include "unknwn.h"  
  
[module(name="MyLib")];  
  
[object, uuid(11111111-1111-1111-1111-111111111111)]  
__interface b   
{  
   [id(0), propget, bindable, displaybind, defaultbind,   
requestedit] HRESULT get_I([out, retval]long *i);  
   HRESULT Proc1([in] short First, [in] short Last,   
[first_is(First), last_is(Last), size_is(Last-First)] char Arr1[]);   
   HRESULT Proc2([in] short First, [in] short Last,   
[last_is(First), size_is(Last)] char Arr2[]);  
};  
```  
  
## Requisitos  
  
### Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|Campo de `struct` o **union**, parámetro de interfaz, método de interfaz|  
|**repetible**|No|  
|**Atributos necesarios**|None|  
|**Atributos no válidos**|None|  
  
 Para obtener más información, vea [Contextos de atributo](../windows/attribute-contexts.md).  
  
## Vea también  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Typedef, Enum, Union, and Struct Attributes](../windows/typedef-enum-union-and-struct-attributes.md)   
 [Parameter Attributes](../windows/parameter-attributes.md)   
 [last\_is](../windows/last-is.md)   
 [max\_is](../windows/max-is.md)   
 [length\_is](../windows/length-is.md)   
 [size\_is](../Topic/size_is.md)   
 [Attributes Samples](http://msdn.microsoft.com/es-es/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)