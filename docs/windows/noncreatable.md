---
title: "noncreatable | Microsoft Docs"
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
  - "vc-attr.noncreatable"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "noncreatable attribute"
ms.assetid: 4d17937b-0bff-41af-ba57-53e18b7ab5a9
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# noncreatable
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Define un objeto que no se puede crear instancias en sí mismo.  
  
## Sintaxis  
  
```  
  
[noncreatable]  
  
```  
  
## Comentarios  
 El atributo de **noncreatable** C\+\+ tiene la misma funcionalidad que el atributo de [noncreatable](http://msdn.microsoft.com/library/windows/desktop/aa367118) MIDL y automáticamente se pasa al archivo de .IDL por el compilador.  
  
 Cuando este atributo se utiliza dentro de un proyecto que utilice ATL, el comportamiento del atributo cambia.  Además del comportamiento anterior, el atributo también inserta la macro de [OBJECT\_ENTRY\_NON\_CREATEABLE\_EX\_AUTO](../Topic/OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO.md) .  esta macro indica a ATL que el objeto no se puede crear externamente.  
  
## Ejemplo  
  
```  
// cpp_attr_ref_noncreatable.cpp  
// compile with: /LD  
#include <unknwn.h>  
[module(name="MyLib")];  
  
[object, uuid("11111111-1111-1111-1111-111111111111")]  
__interface A   
{  
};  
  
[coclass, uuid("11111111-1111-1111-1111-111111111112"), noncreatable]  
class CMyClass : public A   
{  
   HRESULT xx();  
};  
```  
  
## Requisitos  
  
### Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|**clase**, `struct`|  
|**repetible**|No|  
|**Atributos necesarios**|**CoClass**|  
|**Atributos no válidos**|None|  
  
 Para obtener más información sobre los contextos de atributos, vea [Contextos de atributo](../windows/attribute-contexts.md).  
  
## Vea también  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Class Attributes](../windows/class-attributes.md)   
 [Attributes Samples](http://msdn.microsoft.com/es-es/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)