---
title: Error del compilador C3706
ms.date: 11/04/2016
f1_keywords:
- C3706
helpviewer_keywords:
- C3706
ms.assetid: d20a33eb-d625-46c5-ac87-32075a590d07
ms.openlocfilehash: 810ec59a814b04349913648fb49a03eb63912cd9
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757987"
---
# <a name="compiler-error-c3706"></a>Error del compilador C3706

' función ': debe ser una interfaz COM para desencadenar eventos COM

La interfaz de eventos que se usa para desencadenar eventos COM debe ser una interfaz COM. En esta situación, la interfaz debe definirse mediante un atributo visual C++ o importarse mediante [#import](../../preprocessor/hash-import-directive-cpp.md) de una biblioteca de tipos con el atributo embedded_idl de #import.

Tenga en cuenta que las líneas de `#include` de los archivos de encabezado ATL que se muestran en el ejemplo siguiente son necesarias para el uso de eventos COM. Para corregir este error, cree `IEvents` (la interfaz de eventos) una interfaz COM aplicando uno de los siguientes atributos a la definición de interfaz: [objeto](../../windows/object-cpp.md), [doble](../../windows/dual.md)o [dispinterface](../../windows/dispinterface.md).

Si una interfaz es de un archivo de encabezado generado por MIDL, el compilador no lo reconocerá como una interfaz COM.

En el ejemplo siguiente se genera C3706:

```cpp
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
