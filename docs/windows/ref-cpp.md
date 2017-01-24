---
title: "ref (C++) | Microsoft Docs"
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
  - "vc-attr.ref"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ref attribute"
ms.assetid: 67e82d3e-07d9-4ef8-bf2b-0a4491d12557
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ref (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Identifica un puntero de referencia.  
  
## Sintaxis  
  
```  
  
[ref]  
  
```  
  
## Comentarios  
 el atributo de `ref` C\+\+ tiene la misma funcionalidad que el atributo de [referencia](http://msdn.microsoft.com/library/windows/desktop/aa367153) MIDL.  
  
## Ejemplo  
 el código siguiente muestra cómo utilizar el atributo de `ref` :  
  
```  
// cpp_attr_ref_ref.cpp  
// compile with: /LD  
#include <windows.h>   
[module(name="ATLFIRELib")];  
[dispinterface, uuid("00000000-0000-0000-0000-000000000001")]  
__interface IFireTabCtrl  
{  
   [id(1), unique] char * GetFirstName([in, ref] char * pszFullName );   
};  
```  
  
## Requisitos  
  
### Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|`typedef`, parámetro de interfaz, método de interfaz|  
|**repetible**|No|  
|**Atributos necesarios**|None|  
|**Atributos no válidos**|None|  
  
 Para obtener más información sobre los contextos de atributos, vea [Contextos de atributo](../windows/attribute-contexts.md).  
  
## Vea también  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Typedef, Enum, Union, and Struct Attributes](../windows/typedef-enum-union-and-struct-attributes.md)   
 [Parameter Attributes](../windows/parameter-attributes.md)   
 [Attributes Samples](http://msdn.microsoft.com/es-es/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)