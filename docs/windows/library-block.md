---
title: "library_block | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc-attr.library_block"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "library_block attribute"
ms.assetid: ae7a7ebe-5e1a-4eda-a058-11bbd058ece8
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# library_block
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Coloca una construcción dentro del bloque de biblioteca IDL.  
  
## Sintaxis  
  
```  
  
[library_block]  
  
```  
  
## Comentarios  
 Cuando coloca una construcción dentro del bloque de la biblioteca, se garantiza que se pasa en la biblioteca de tipos, independientemente de si se hace referencia.  De forma predeterminada, solo las construcciones modificadas por [CoClass](../windows/coclass.md), [dispinterface](../windows/dispinterface.md), y los atributos de [idl\_module](../windows/idl-module.md) se colocan en el bloque de la biblioteca.  
  
## Ejemplo  
 En el código siguiente, una interfaz personalizada se coloca dentro del bloque de la biblioteca.  
  
```  
// cpp_attr_ref_library_block.cpp  
// compile with: /LD  
#include <windows.h>  
[module(name="MyLib")];  
[object, library_block, uuid("9E66A290-4365-11D2-A997-00C04FA37DDB")]  
__interface IMyInterface {  
   HRESULT f1();  
};  
```  
  
## Requisitos  
  
### Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|Cualquier parte|  
|**repetible**|No|  
|**Atributos necesarios**|None|  
|**Atributos no válidos**|None|  
  
 Para obtener más información, vea [Contextos de atributo](../windows/attribute-contexts.md).  
  
## Vea también  
 [Compiler Attributes](../windows/compiler-attributes.md)   
 [Stand\-Alone Attributes](../Topic/Stand-Alone%20Attributes.md)   
 [Attributes Samples](http://msdn.microsoft.com/es-es/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)