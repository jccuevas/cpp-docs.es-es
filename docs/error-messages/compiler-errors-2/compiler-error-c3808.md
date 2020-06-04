---
title: Error del compilador C3808
ms.date: 11/04/2016
f1_keywords:
- C3808
helpviewer_keywords:
- C3808
ms.assetid: 2ee8ac97-3ea4-417a-8710-be73a7f98cf4
ms.openlocfilehash: e854764dc3f8d3ede79965302b62055b91df0a4c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165631"
---
# <a name="compiler-error-c3808"></a>Error del compilador C3808

> '*Type*': una clase con el atributo ComImport no puede definir el miembro '*member*'; solo se permiten funciones abstract o DllImport

## <a name="remarks"></a>Observaciones

Un tipo que se deriva de <xref:System.Runtime.InteropServices.ComImportAttribute> no puede definir el *miembro*.

Las opciones del compilador **/clr: Pure** y **/clr: Safe** están en desuso en Visual Studio 2015 y no se admiten en Visual Studio 2017.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C3808.

```cpp
// C3808.cpp
// compile with: /c /clr:pure user32.lib
using namespace System::Runtime::InteropServices;

[System::Runtime::InteropServices::ComImportAttribute()]
ref struct S1 {
   int f() {}   // C3808
   virtual int g() abstract;   // OK

   [DllImport("msvcrt.dll")]
   int printf(System::String ^, int i);   // OK
};
```
