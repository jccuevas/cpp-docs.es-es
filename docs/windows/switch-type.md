---
title: "switch_type | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc-attr.switch_type"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "switch_type attribute"
ms.assetid: e24544dc-b3bc-48ae-b249-f967db49271e
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# switch_type
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Identifica el tipo de la variable utilizada como unión discriminante.  
  
## Sintaxis  
  
```  
  
[switch_type(  
type  
}]  
  
```  
  
#### Parámetros  
 `type`  
 El tipo de modificador, puede ser un entero, un carácter, un booleano, o tipo de enumeración.  
  
## Comentarios  
 el atributo de **switch\_type** C\+\+ tiene la misma funcionalidad que el atributo de [switch\_type](http://msdn.microsoft.com/library/windows/desktop/aa367276) MIDL.  
  
 los atributos de C\+\+ no admiten [uniones encapsuladas](http://msdn.microsoft.com/library/windows/desktop/aa366811).  [uniones de Nonencapsulated](http://msdn.microsoft.com/library/windows/desktop/aa367119) solo se admite en el formato siguiente:  
  
```  
// cpp_attr_ref_switch_type.cpp  
// compile with: /LD  
#include <windows.h>  
[module(name="MyLibrary")];  
[ export ]  
struct SizedValue2 {  
   [switch_type("char"), switch_is(kind)] union {  
      [case(1), string]  
         wchar_t* wval;  
      [default, string]  
         char* val;  
   };  
   char kind;  
};  
```  
  
## Ejemplo  
 Vea el ejemplo de [mayúsculas\/minúsculas](../windows/case-cpp.md) para un ejemplo de uso de **switch\_type**.  
  
## Requisitos  
  
### Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|`typedef`|  
|**repetible**|No|  
|**Atributos necesarios**|None|  
|**Atributos no válidos**|None|  
  
 Para obtener más información sobre los contextos de atributos, vea [Contextos de atributo](../windows/attribute-contexts.md).  
  
## Vea también  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Typedef, Enum, Union, and Struct Attributes](../windows/typedef-enum-union-and-struct-attributes.md)   
 [export](../windows/export.md)   
 [Attributes Samples](http://msdn.microsoft.com/es-es/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)