---
title: Error del compilador C3857
ms.date: 11/04/2016
f1_keywords:
- C3857
helpviewer_keywords:
- C3857
ms.assetid: 9f746d1e-9708-4945-bc29-3150d5371d3c
ms.openlocfilehash: 1270d09c870bfdf9f390d6afb1625ad3e99e01a0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50456893"
---
# <a name="compiler-error-c3857"></a>Error del compilador C3857

'type': no se permiten varias listas de parámetros de tipo

Se especificó más de una plantilla o genérico para el mismo tipo, lo cual no está permitido.

El ejemplo siguiente genera C3857:

```
// C3857.cpp
template <class T, class TT>
template <class T2>    // C3857
struct B {};
```

Posible resolución:

```
// C3857b.cpp
// compile with: /c
template <class T, class TT, class T2>
struct B {};
```

C3857 también puede producirse al usar genéricos:

```
// C3857c.cpp
// compile with: /clr
generic <typename T>
generic <typename U>
ref class GC;   // C3857
```

Posible resolución:

```
// C3857d.cpp
// compile with: /clr /c
generic <typename U>
ref class GC;
```