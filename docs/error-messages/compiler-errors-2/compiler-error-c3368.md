---
title: Error del compilador C3368
ms.date: 11/04/2016
f1_keywords:
- C3368
helpviewer_keywords:
- C3368
ms.assetid: 5bfd5be4-dfa9-4b33-9612-010561b40955
ms.openlocfilehash: 8e67655e90b571ea099572cdc34bc39124fc3271
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74751877"
---
# <a name="compiler-error-c3368"></a>Error del compilador C3368

'declaración de función': convención de llamada no válida para IDL

Solo se pueden usar las convenciones de llamada [__stdcall](../../cpp/stdcall.md) o [__cdecl](../../cpp/cdecl.md) en un archivo .idl.

El ejemplo siguiente genera la advertencia C3368:

```cpp
// C3368.cpp
// processor: x86
[idl_module(name="Name", dllname="Some.dll")];

[idl_module(name="Name")]
int __fastcall f1();   // C3368
```
