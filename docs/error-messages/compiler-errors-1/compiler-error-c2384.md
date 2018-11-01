---
title: Error del compilador C2384
ms.date: 11/04/2016
f1_keywords:
- C2384
helpviewer_keywords:
- C2384
ms.assetid: 8145f7ad-31b1-406d-ac43-0d557feab635
ms.openlocfilehash: 1909fb999dd0f60224029b726f773c11fa69ee40
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50460325"
---
# <a name="compiler-error-c2384"></a>Error del compilador C2384

'member': no se puede aplicar __declspec(thread) a un miembro de una clase WinRT o administrada

El [subproceso](../../cpp/thread.md) `__declspec` modificador no se puede usar en un miembro de una clase administrada o una clase en tiempo de ejecución de Windows.

El almacenamiento local para el subproceso estático solo puede usarse con DLL cargadas estáticamente; la DLL debe cargarse de manera estática al iniciarse el proceso. El tiempo de ejecución de Windows no admite el almacenamiento local para el subproceso.

La siguiente línea genera C2384 y muestra cómo corregirlo en código C++/CLI:

```
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