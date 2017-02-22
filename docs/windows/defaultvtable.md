---
title: "defaultvtable | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc-attr.defaultvtable"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "defaultvtable attribute"
ms.assetid: 5b3ed483-f69e-44dd-80fc-952028eb9d73
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# defaultvtable
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Define una interfaz como interfaz vtable predeterminada para un objeto COM.  
  
## Sintaxis  
  
```  
  
      [ defaultvtable(  
   interface  
) ]  
```  
  
#### Parámetros  
 `interface`  
 La interfaz designado que desea que el valor predeterminado vtable para el objeto COM.  
  
## Comentarios  
 el atributo de **defaultvtable** C\+\+ tiene la misma funcionalidad que el atributo de [defaultvtable](http://msdn.microsoft.com/library/windows/desktop/aa366795) MIDL.  
  
## Ejemplo  
 El código siguiente muestra los atributos de una clase que utilizan **defaultvtable** para especificar una interfaz predeterminada:  
  
```  
// cpp_attr_ref_defaultvtable.cpp  
// compile with: /LD  
#include <unknwn.h>  
[module(name="MyLib")];  
  
[object, uuid("00000000-0000-0000-0000-000000000001")]  
__interface IMyI1 {  
   HRESULT x();  
};  
  
[object, uuid("00000000-0000-0000-0000-000000000002")]  
__interface IMyI2 {  
   HRESULT x();  
};  
  
[object, uuid("00000000-0000-0000-0000-000000000003")]  
__interface IMyI3 {  
   HRESULT x();  
};  
  
[coclass, source(IMyI3, IMyI1), default(IMyI3, IMyI2), defaultvtable(IMyI1),  
uuid("00000000-0000-0000-0000-000000000004")]  
class CMyC3 : public IMyI3 {};  
```  
  
## Requisitos  
  
### Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|**clase**, `struct`|  
|**repetible**|No|  
|**Atributos necesarios**|**CoClass**|  
|**Atributos no válidos**|None|  
  
 Para obtener más información, vea [Contextos de atributo](../windows/attribute-contexts.md).  
  
## Vea también  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Class Attributes](../windows/class-attributes.md)   
 [Attributes Samples](http://msdn.microsoft.com/es-es/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)