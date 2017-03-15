---
title: "vararg | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc-attr.vararg"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "vararg attribute"
ms.assetid: 20fc3244-18e9-411c-990e-d5b4fa29a570
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# vararg
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Especifica que la función toma un número variable de argumentos.  
  
## Sintaxis  
  
```  
  
[vararg]  
  
```  
  
## Comentarios  
 el atributo de **vararg** C\+\+ tiene la misma funcionalidad que el atributo de [vararg](http://msdn.microsoft.com/library/windows/desktop/aa367304) MIDL.  
  
## Ejemplo  
 El código siguiente se muestra un uso de **vararg**:  
  
```  
// cpp_attr_ref_vararg.cpp  
// compile with: /LD  
#include "unknwn.h"  
#include "oaidl.h"  
[module(name="MyLibrary")];  
  
[object, uuid("00000000-0000-0000-0000-000000000001")]  
__interface X : public IUnknown   
{  
   [vararg] HRESULT Button([in, satype(VARIANT)]SAFEARRAY *psa);  
};  
```  
  
## Requisitos  
  
### Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|método de interfaz|  
|**repetible**|No|  
|**Atributos necesarios**|None|  
|**Atributos no válidos**|None|  
  
 Para obtener más información sobre los contextos de atributos, vea [Contextos de atributo](../windows/attribute-contexts.md).  
  
## Vea también  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Method Attributes](../windows/method-attributes.md)   
 [Attributes Samples](http://msdn.microsoft.com/es-es/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)