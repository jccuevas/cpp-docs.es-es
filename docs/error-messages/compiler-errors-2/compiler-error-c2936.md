---
title: Error del compilador C2936
ms.date: 11/04/2016
f1_keywords:
- C2936
helpviewer_keywords:
- C2936
ms.assetid: 5d1ba0fc-0c78-4a37-a83b-1ef8527763be
ms.openlocfilehash: 547690302661656cc5368f5969432de68ac91e3f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62302961"
---
# <a name="compiler-error-c2936"></a>Error del compilador C2936

'clase': el id. de clase de plantilla se ha vuelto a definir como variable de datos global

No se puede usar una clase genérica o de plantilla como variable de datos local.

Este error puede producirse si las llaves no coinciden como es debido.

El ejemplo siguiente genera la advertencia C2936:

```
// C2936.cpp
// compile with: /c
template<class T> struct TC { };
int TC<int>;   // C2936

// OK
struct TC2 { };
int TC2;
```

También se puede producir el error C2936 al usar genéricos:

```
// C2936b.cpp
// compile with: /clr /c
generic<class T>
ref struct GC {};
int GC<int>;   // C2936

// OK
ref struct GC2 {};
int GC2;
```