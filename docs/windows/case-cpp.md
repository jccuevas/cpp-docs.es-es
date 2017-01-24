---
title: "case (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc-attr.case"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "case attribute"
ms.assetid: 6fb883c3-0526-4932-a901-b4564dcaeb7d
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# case (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

utilizado con el atributo de [switch\_type](../windows/switch-type.md) en **union**.  
  
## Sintaxis  
  
```  
  
      [ case(  
   value  
) ]  
```  
  
#### Parámetros  
 *valor*  
 Un valor posible de entrada para la que desea proporcionar el procesamiento.  El tipo de **Valor** puede ser uno de los tipos siguientes:  
  
-   `int`  
  
-   `char`  
  
-   **boolean**  
  
-   `enum`  
  
 o un identificador de dicho tipo.  
  
## Comentarios  
 el atributo de **mayúsculas\/minúsculas** C\+\+ tiene la misma funcionalidad que el atributo de **mayúsculas\/minúsculas** MIDL.  Este atributo se utiliza únicamente con el atributo de [switch\_type](../windows/switch-type.md) .  
  
## Ejemplo  
 El código siguiente se muestra un uso de atributo de **mayúsculas\/minúsculas** :  
  
```  
// cpp_attr_ref_case.cpp  
// compile with: /LD  
#include <unknwn.h>  
[export]  
struct SizedValue2 {  
   [switch_type(char), switch_is(kind)] union {  
      [case(1), string]  
          wchar_t* wval;  
      [default, string]  
          char* val;  
   };  
    char kind;  
};  
[module(name="ATLFIRELib")];  
```  
  
## Requisitos  
  
### Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|miembro de **clase** o de `struct`|  
|**repetible**|No|  
|**Atributos necesarios**|None|  
|**Atributos no válidos**|None|  
  
 Para obtener más información sobre los contextos de atributos, vea [Contextos de atributo](../windows/attribute-contexts.md).  
  
## Vea también  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Typedef, Enum, Union, and Struct Attributes](../windows/typedef-enum-union-and-struct-attributes.md)   
 [Class Attributes](../windows/class-attributes.md)   
 [Attributes Samples](http://msdn.microsoft.com/es-es/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)