---
title: Error del compilador C2384
ms.date: 11/04/2016
f1_keywords:
- C2384
helpviewer_keywords:
- C2384
ms.assetid: 8145f7ad-31b1-406d-ac43-0d557feab635
ms.openlocfilehash: 2ce5c2f2540fbd2aca3509fa1dac55073a002abb
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74745270"
---
# <a name="compiler-error-c2384"></a>Error del compilador C2384

'member': no se puede aplicar __declspec(thread) a un miembro de una clase WinRT o administrada

No se puede usar el modificador `__declspec` del [subproceso](../../cpp/thread.md) en un miembro de una clase administrada o Windows Runtime.

El almacenamiento local para el subproceso estático solo puede usarse con DLL cargadas estáticamente; la DLL debe cargarse de manera estática al iniciarse el proceso. Windows Runtime no admite el almacenamiento local para el subproceso.

La siguiente línea genera C2384 y muestra cómo corregirlo en código C++/CLI:

```cpp
// C2384.cpp
// compile with: /clr /c
public ref class B {
public:
   __declspec( thread ) static int tls_i = 1;   // C2384

   // OK - declare with attribute instead
   [System::ThreadStaticAttribute]
   static int tls_j;
};
```
