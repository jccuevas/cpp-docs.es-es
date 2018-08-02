---
title: puede enlazar | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.bindable
dev_langs:
- C++
helpviewer_keywords:
- bindable attribute
ms.assetid: a2360f92-927b-4af8-98cc-6eca7f4ec954
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1a216aa5fb5be727e82313c30aa2aa72d887cb4c
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/02/2018
ms.locfileid: "39467149"
---
# <a name="bindable"></a>bindable
Indica que la propiedad admite enlace de datos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
[bindable]  
```  
  
## <a name="remarks"></a>Comentarios  
 El **enlazable** atributo de C++ tiene la misma funcionalidad que el [enlazable](http://msdn.microsoft.com/library/windows/desktop/aa366738) atributo MIDL. Se puede usar en las propiedades definidas con el [propget](../windows/propget.md), [propput](../windows/propput.md), o [propputref](../windows/propputref.md) atributos, o bien puede definir un método se puede enlazar manualmente.  
  
 Los siguientes ejemplos MFC muestran el uso de **enlazable**:  
  
-   [Ejemplos de controles: Controles de ActiveX basados en MFC](http://msdn.microsoft.com/a44adf86-0ba0-4504-bedb-512b6cba2e63)  
  
-   [Ejemplo CIRC: Control ActiveX](http://msdn.microsoft.com/9ba34d04-280e-49f4-90ae-41a6be44c95b)  
  
-   [Ejemplo TESTHELP: Control de ActiveX con información sobre herramientas y ayuda](http://msdn.microsoft.com/d822861d-c6f0-4d0a-ad11-970eebb1e8cd)  
  
## <a name="example"></a>Ejemplo  
 El código siguiente muestra cómo puede usar **enlazable** en una propiedad:  
  
```cpp  
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
  
## <a name="requirements"></a>Requisitos  
  
### <a name="attribute-context"></a>Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|Método de interfaz|  
|**Reiterativo**|No|  
|**Atributos requeridos**|Ninguna|  
|**Atributos no válidos**|Ninguna|  
  
 Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Vea también  
 [Atributos IDL](../windows/idl-attributes.md)   
 [Atributos de método](../windows/method-attributes.md)   
 [defaultbind](../windows/defaultbind.md)   
 [displaybind](../windows/displaybind.md)   
 [immediatebind](../windows/immediatebind.md)   
 [requestedit](../windows/requestedit.md)   