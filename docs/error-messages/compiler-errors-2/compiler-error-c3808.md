---
title: Error del compilador C3808 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3808
dev_langs:
- C++
helpviewer_keywords:
- C3808
ms.assetid: 2ee8ac97-3ea4-417a-8710-be73a7f98cf4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 40668b8b2cc1a1f85b0ad4a7ef63d89956e922b3
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "34705210"
---
# <a name="compiler-error-c3808"></a>Error del compilador C3808

> '*tipo*': una clase con el atributo ComImport no puede definir el miembro '*miembro*', solo abstracta o se permiten funciones de dllimport

## <a name="remarks"></a>Comentarios

Un tipo que deriva de <xref:System.Runtime.InteropServices.ComImportAttribute> no se puede definir *miembro*.

El **/CLR: pure** y **/CLR: safe** opciones del compilador están en desuso en Visual Studio 2015 y no se admiten en Visual Studio de 2017.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C3808.

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