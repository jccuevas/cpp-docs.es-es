---
title: "transmit_as | Microsoft Docs"
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
  - "vc-attr.transmit_as"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "transmit_as attribute"
ms.assetid: 53d0b8ab-5b06-423e-83eb-3d01a10424b2
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# transmit_as
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Indica al compilador para asociar un actual tipo que las aplicaciones cliente y servidor manipular, con un tipo transmitido.  
  
## Sintaxis  
  
```  
  
      [ transmit_as(  
   type  
) ]  
```  
  
#### Parámetros  
 `type`  
 Especifica el tipo de datos que se transmiten entre el cliente y el servidor.  
  
## Comentarios  
 el atributo de **transmit\_as** C\+\+ tiene la misma funcionalidad que el atributo de [transmit\_as](http://msdn.microsoft.com/library/windows/desktop/aa367286) MIDL.  
  
## Ejemplo  
 El código siguiente se muestra un uso de atributo de **transmit\_as** :  
  
```  
// cpp_attr_ref_transmit_as.cpp  
// compile with: /LD  
#include "windows.h"  
[module(name="MyLibrary")];  
  
[export] typedef struct _TREE_NODE_TYPE {  
unsigned short data;   
struct _TREE_NODE_TYPE * left;  
struct _TREE_NODE_TYPE * right;   
} TREE_NODE_TYPE;  
  
[export] struct PACKED_NODE {  
   unsigned short data;   // same as normal node  
   int index;   // array index of parent  
};  
  
// A left node recursive built array of  
// the nodes in the tree.  Can be unpacked with  
// that knowledge  
[export] typedef struct _TREE_XMIT_TYPE {  
   int count;  
   [size_is(count)] PACKED_NODE node[];  
} TREE_XMIT_TYPE;  
  
[transmit_as(TREE_XMIT_TYPE)] typedef TREE_NODE_TYPE * TREE_TYPE;  
```  
  
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