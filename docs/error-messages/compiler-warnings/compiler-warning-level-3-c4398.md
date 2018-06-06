---
title: Compilador advertencia (nivel 3) C4398 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4398
dev_langs:
- C++
helpviewer_keywords:
- C4398
ms.assetid: b6221432-9fed-4272-a547-a73f587904e6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c38ade6b75242fdd5144481e3415e914cb6773c5
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "34704619"
---
# <a name="compiler-warning-level-3-c4398"></a>Advertencia del compilador (nivel 3) C4398

> '*variable*': objeto global por proceso no funcionen correctamente con varios dominios de aplicación; considere el uso de __declspec (AppDomain)

## <a name="remarks"></a>Comentarios

Una función virtual con [__clrcall](../../cpp/clrcall.md) convención de llamada en un tipo nativo produce la creación de una por vtable de dominio de aplicación. Este tipo de variable no puede corregir correctamente cuando se utiliza en varios dominios de aplicación.

Puede resolver esta advertencia al marcar explícitamente la variable `__declspec(appdomain)`. En versiones de Visual Studio anteriores a Visual Studio de 2017, se puede resolver esta advertencia al compilar con **/CLR: pure**, lo que hace variables globales por appdomain de forma predeterminada. El **/CLR: pure** opción del compilador está en desuso en Visual Studio 2015 y no se admiten en Visual Studio de 2017.

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