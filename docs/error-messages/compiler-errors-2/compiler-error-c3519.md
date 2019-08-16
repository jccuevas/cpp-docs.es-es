---
title: Error del compilador C3519
ms.date: 11/04/2016
f1_keywords:
- C3519
helpviewer_keywords:
- C3519
ms.assetid: ca24b2bc-7e90-4448-ae84-3fedddf9bca7
ms.openlocfilehash: e9a998e1c3a6c2fb770fb9d26d97b8a24e5554d3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62360039"
---
# <a name="compiler-error-c3519"></a>Error del compilador C3519

'parámetro no válido': parámetro no válido para el atributo embedded_idl

Se pasó un parámetro a la `embedded_idl` atributo de [#import](../../preprocessor/hash-import-directive-cpp.md), pero el compilador no reconoce el parámetro.

Los únicos parámetros que se permiten para `embedded_idl` son `emitidl` y `no_emitidl`.

El ejemplo siguiente genera C3519:

```
// C3519.cpp
// compile with: /LD
[module(name="MyLib2")];
#import "C:\testdir\bin\importlib.tlb" embedded_idl("no_emitidcl")
// C3519
#import "C:\testdir\bin\importlib.tlb" embedded_idl("no_emitidl")
// OK
```