---
title: Portabilidad en los límites de ABI
description: Acople C++ las interfaces a las convenciones de llamada de C en los límites de la interfaz binaria.
ms.date: 11/19/2019
ms.topic: conceptual
ms.assetid: abbd405e-3038-427c-8c24-e00598f0936a
ms.openlocfilehash: b3b2b217739ff5900c8ef0329ff3e8909a3fe036
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303324"
---
# <a name="portability-at-abi-boundaries"></a>Portabilidad en los límites de ABI

Utilice tipos y convenciones suficientemente portátiles en los límites de la interfaz binaria. Un "tipo portátil" es un tipo integrado de C o un struct que solo contiene tipos integrados de C. Los tipos de clase solo se pueden usar cuando el llamador y el destinatario acuerdan el diseño, la Convención de llamada, etc. Esto solo es posible cuando ambos se compilan con la misma configuración del compilador y del compilador.

## <a name="how-to-flatten-a-class-for-c-portability"></a>Cómo aplanar una clase para la portabilidad de C

Cuando los autores de la llamada se pueden compilar con otro lenguaje o compilador, "aplanar" en una API de **"C" externa** con una Convención de llamada específica:

```cpp
// class widget {
//   widget();
//   ~widget();
//   double method( int, gadget& );
// };
extern "C" {        // functions using explicit "this"
   struct widget;   // opaque type (forward declaration only)
   widget* STDCALL widget_create();      // constructor creates new "this"
   void STDCALL widget_destroy(widget*); // destructor consumes "this"
   double STDCALL widget_method(widget*, int, gadget*); // method uses "this"
}
```

## <a name="see-also"></a>Vea también

[Bienvenido de nuevo aC++](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[Referencia del lenguaje C++](../cpp/cpp-language-reference.md)<br/>
[Biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)
