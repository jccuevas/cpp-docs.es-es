---
title: "helpstringcontext | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc-attr.helpstringcontext"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "helpstringcontext attribute [C++]"
ms.assetid: d4cd135e-d91c-4aa3-9353-8aeb096f52cf
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# helpstringcontext
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Especifica el identificador de un tema de Ayuda en un archivo de .hlp o .chm.  
  
## Sintaxis  
  
```  
  
      [ helpstringcontext(  
   contextID  
) ]  
```  
  
#### Parámetros  
 `contextID`  
 Un identificador de 32 bits de contexto de Ayuda en el archivo de Ayuda.  
  
## Comentarios  
 el atributo de **helpstringcontext** C\+\+ tiene la misma funcionalidad que el atributo de [helpstringcontext](http://msdn.microsoft.com/library/windows/desktop/aa366858) ODL.  
  
## Ejemplo  
  
```  
// cpp_attr_ref_helpstringcontext.cpp  
// compile with: /LD  
#include <unknwn.h>  
[module(name="MyLib")];  
  
[   object,   
   helpstring("help string"),   
   helpstringcontext(1),   
   uuid="11111111-1111-1111-1111-111111111111"  
]  
__interface IMyI   
{  
   HRESULT xx();  
};  
```  
  
## Requisitos  
  
### Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|**clase**, `interface`, método de interfaz|  
|**repetible**|No|  
|**Atributos necesarios**|None|  
|**Atributos no válidos**|None|  
  
 Para obtener más información, vea [Contextos de atributo](../windows/attribute-contexts.md).  
  
## Vea también  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Interface Attributes](../windows/interface-attributes.md)   
 [Class Attributes](../windows/class-attributes.md)   
 [Method Attributes](../windows/method-attributes.md)   
 [módulo](../windows/module-cpp.md)   
 [Attributes Samples](http://msdn.microsoft.com/es-es/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)