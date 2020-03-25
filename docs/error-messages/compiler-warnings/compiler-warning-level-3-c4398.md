---
title: Advertencia del compilador (nivel 3) C4398
ms.date: 11/04/2016
f1_keywords:
- C4398
helpviewer_keywords:
- C4398
ms.assetid: b6221432-9fed-4272-a547-a73f587904e6
ms.openlocfilehash: 041bf9f6bfce17b16f301604bb8706be30095c13
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198671"
---
# <a name="compiler-warning-level-3-c4398"></a>Advertencia del compilador (nivel 3) C4398

> '*variable*': el objeto global por proceso podría no funcionar correctamente con varios AppDomains; considerar el uso de __declspec (AppDomain)

## <a name="remarks"></a>Observaciones

Una función virtual con [__clrcall](../../cpp/clrcall.md) Convención de llamada en un tipo nativo produce la creación de una vtable por dominio de aplicación. Este tipo de variable puede no corregirse correctamente cuando se usa en varios dominios de aplicación.

Puede resolver esta advertencia marcando explícitamente la variable `__declspec(appdomain)`. En las versiones de Visual Studio anteriores a Visual Studio 2017, puede resolver esta advertencia compilando con **/clr: Pure**, lo que hace que las variables globales por AppDomain se realicen de forma predeterminada. La opción del compilador **/clr: Pure** ha quedado en desuso en visual Studio 2015 y no se admite en visual Studio 2017.

Para obtener más información, vea [AppDomain](../../cpp/appdomain.md) y [dominios de aplicación C++y visual ](../../dotnet/application-domains-and-visual-cpp.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C4398.

```cpp
// C4398.cpp
// compile with: /clr /W3 /c
struct S {
   virtual void f( System::String ^ );   // String^ parameter makes function __clrcall
};

S glob_s;   // C4398
__declspec(appdomain) S glob_s2;   // OK
```
