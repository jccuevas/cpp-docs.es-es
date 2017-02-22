---
title: "bindable | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc-attr.bindable"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "bindable attribute"
ms.assetid: a2360f92-927b-4af8-98cc-6eca7f4ec954
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# bindable
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Indica que la propiedad admite enlace de datos.  
  
## Sintaxis  
  
```  
  
[bindable]  
  
```  
  
## Comentarios  
 el atributo de **enlazable** C\+\+ tiene la misma funcionalidad que el atributo de [enlazable](http://msdn.microsoft.com/library/windows/desktop/aa366738) MIDL.  Puede utilizarlo en propiedades definidas con [propget](../windows/propget.md), [propput](../windows/propput.md), o los atributos de [propputref](../windows/propputref.md) , o puede definir manualmente un método enlazable.  
  
 Ejemplos de MFC muestran el uso de **enlazable**:  
  
-   [ejemplos de Controles: Controles ActiveX basadas](http://msdn.microsoft.com/es-es/a44adf86-0ba0-4504-bedb-512b6cba2e63)  
  
-   [Ejemplo CIRC: control ActiveX](http://msdn.microsoft.com/es-es/9ba34d04-280e-49f4-90ae-41a6be44c95b)  
  
-   [Ejemplo TESTHELP: control ActiveX con información sobre herramientas y ayuda](http://msdn.microsoft.com/es-es/d822861d-c6f0-4d0a-ad11-970eebb1e8cd)  
  
## Ejemplo  
 El código siguiente muestra cómo puede utilizar **enlazable** en una propiedad:  
  
```  
// cpp_attr_ref_bindable.cpp  
// compile with: /LD  
#include <windows.h>  
[  
   uuid("479B29E3-9A2C-11D0-B696-00A0C903487A"),  
   dispinterface,  
   helpstring("property demo Interface")  
]  
__interface IPropDemo : IDispatch {  
  
   [propget, id(1), bindable, displaybind, defaultbind, requestedit] HRESULT P1([out, retval] long *nSize);  
   [propput, id(1), bindable, displaybind, defaultbind, requestedit] HRESULT P1([in] long nSize);  
   [id(3), bindable, propget] HRESULT Object([out, retval] IDispatch **ppObj);  
   [id(3), bindable, propputref] HRESULT Object([in] IDispatch* pObj);     
   [id(-552), helpstring("method AboutBox")] HRESULT AboutBox();  
};  
  
[ module(name="PropDemoLib", uuid="479B29E2-9A2C-11D0-B696-00A0C903487A", version="1.0", helpstring="property demo") ];  
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
 [defaultbind](../windows/defaultbind.md)   
 [displaybind](../windows/displaybind.md)   
 [immediatebind](../windows/immediatebind.md)   
 [requestedit](../windows/requestedit.md)   
 [Attributes Samples](http://msdn.microsoft.com/es-es/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)