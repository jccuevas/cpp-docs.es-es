---
title: "helpstringdll | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc-attr.helpstringdll"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "helpstringdll attribute [C++]"
ms.assetid: 121271fa-f061-492b-b87f-bbfcf4b02e7b
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# helpstringdll
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Especifica el nombre de DLL para utilizar para realizar la búsqueda de la cadena del documento \(localización\).  
  
## Sintaxis  
  
```  
  
      [ helpstringdll(  
   "string"  
) ]  
```  
  
#### Parámetros  
 `string`  
 DLL a utilizar para realizar la búsqueda de la cadena del documento.  
  
## Comentarios  
 el atributo de **helpstringdll** C\+\+ tiene la misma funcionalidad que el atributo de [helpstringdll](http://msdn.microsoft.com/library/windows/desktop/aa366860) MIDL.  
  
## Ejemplo  
  
```  
// cpp_attr_ref_helpstringdll.cpp  
// compile with: /LD  
#include <unknwn.h>  
[module(name="MyLib", helpstringdll="xx.dll")];  
  
[object, uuid("00000000-0000-0000-0000-000000000001")]  
__interface IMyI   
{  
   HRESULT xxx();  
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
 [Attributes Samples](http://msdn.microsoft.com/es-es/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)