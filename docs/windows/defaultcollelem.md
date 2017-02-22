---
title: "defaultcollelem | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc-attr.defaultcollelem"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "defaultcollelem attribute"
ms.assetid: 3dbbd293-8b83-4f70-a36b-64cc1d0b6713
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# defaultcollelem
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Se utiliza para la optimización del código de Visual Basic.  
  
## Sintaxis  
  
```  
  
[defaultcollelem]  
  
```  
  
## Comentarios  
 el atributo de **defaultcollelem** C\+\+ tiene la misma funcionalidad que el atributo de [defaultcollelem](http://msdn.microsoft.com/library/windows/desktop/aa366792) MIDL.  
  
## Ejemplo  
 El código siguiente muestra un método de interfaz con el atributo de **defaultcollelem** :  
  
```  
// cpp_attr_ref_defaultcollelem.cpp  
// compile with: /LD  
#include <unknwn.h>  
[module(name="MyLib")];  
[object, uuid("00000000-0000-0000-0000-000000000001")]  
__interface IMyForm   
{     
   [propget, id(1), bindable, defaultcollelem, displaybind,   
   defaultbind, requestedit] HRESULT P1([out, retval] long *nSize);  
   [propput, id(1), bindable, defaultcollelem, displaybind,   
   defaultbind, requestedit] HRESULT P1([in] long nSize);  
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
  
 Para obtener más información, vea [Contextos de atributo](../windows/attribute-contexts.md).  
  
## Vea también  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Method Attributes](../windows/method-attributes.md)   
 [Attributes Samples](http://msdn.microsoft.com/es-es/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)