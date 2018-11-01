---
title: Advertencia del compilador (nivel 3) C4398
ms.date: 11/04/2016
f1_keywords:
- C4398
helpviewer_keywords:
- C4398
ms.assetid: b6221432-9fed-4272-a547-a73f587904e6
ms.openlocfilehash: 4126a1267b41cdf9c0161c7e85a9057b2a301d77
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50578469"
---
# <a name="compiler-warning-level-3-c4398"></a>Advertencia del compilador (nivel 3) C4398

> '*variable*': objeto global por proceso no funcionen correctamente con varios dominios de aplicación; utilice __declspec (AppDomain)

## <a name="remarks"></a>Comentarios

Una función virtual con [__clrcall](../../cpp/clrcall.md) convención de llamada en un tipo nativo hace que la creación de una por vtable de dominio de aplicación. Este tipo de variable no puede corregir correctamente cuando se usa en varios dominios de aplicación.

Puede resolver esta advertencia marque explícitamente la variable `__declspec(appdomain)`. En las versiones de Visual Studio anteriores a Visual Studio 2017, se puede resolver esta advertencia al compilar con **/CLR: pure**, que hace que las variables globales por appdomain de forma predeterminada. El **/CLR: pure** opción del compilador está en desuso en Visual Studio 2015 y no se admite en Visual Studio 2017.

Para obtener más información, consulte [appdomain](../../cpp/appdomain.md) y [dominios de aplicación y Visual C++](../../dotnet/application-domains-and-visual-cpp.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C4398.

```cpp
// C4398.cpp
// compile with: /clr /W3 /c
struct S {
   virtual void f( System::String ^ );   // String^ parameter makes function __clrcall
};

S glob_s;   // C4398
__declspec(appdomain) S glob_s2;   // OK
```