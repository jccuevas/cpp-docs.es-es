---
title: Error del compilador C3706 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3706
dev_langs:
- C++
helpviewer_keywords:
- C3706
ms.assetid: d20a33eb-d625-46c5-ac87-32075a590d07
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 20f7e14d22e1994213624d88ccab098844aa6ac4
ms.contentlocale: es-es
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3706"></a>Error del compilador C3706
'función': debe ser una interfaz COM para desencadenar eventos COM  
  
 La interfaz de evento que se utiliza para desencadenar eventos COM debe ser una interfaz COM. En esta situación, la interfaz debería definirse con un atributo de Visual C++, o se importa utilizando [#import](../../preprocessor/hash-import-directive-cpp.md) desde una biblioteca de tipos con el atributo embedded_idl de #import.  
  
 Tenga en cuenta que el `#include` son necesarias para el uso de eventos COM líneas de los archivos de encabezado ATL se muestra en el ejemplo siguiente. Para corregir este error, asegúrese de `IEvents` (la interfaz de eventos) una interfaz COM aplicando uno de los siguientes atributos a la definición de interfaz: [objeto](../../windows/object-cpp.md), [dual](../../windows/dual.md), o [ dispinterface](../../windows/dispinterface.md).  
  
 Es una interfaz de un archivo de encabezado generado por MIDL, el compilador no reconocerlo como una interfaz COM.  
  
 El ejemplo siguiente genera C3706:  
  
```  
// C3706.cpp  
// compile with: /c  
// C3706 expected  
#define _ATL_ATTRIBUTES 1  
#include <atlbase.h>  
#include <atlcom.h>  
#include <atlctl.h>  
  
[module(dll, name="idid", uuid="12341234-1234-1234-1234-123412341234")];  
  
// Uncomment the following line to resolve.  
// [object, uuid="12341234-1234-1234-1234-123412341237"]  
__interface IEvents : IUnknown {  
   HRESULT event1(/*[in]*/ int i);   // uncomment [in]  
};  
  
[dual, uuid="12341234-1234-1234-1234-123412341235"]  
__interface IBase {  
   HRESULT fireEvents();  
};  
  
[coclass, event_source(com), uuid="12341234-1234-1234-1234-123412341236"]  
class CEventSrc : public IBase {  
   public:  
   __event __interface IEvents;  
  
   HRESULT fireEvents() {  
      HRESULT hr = IEvents_event1(123);  
      return hr;  
   }  
};  
```
