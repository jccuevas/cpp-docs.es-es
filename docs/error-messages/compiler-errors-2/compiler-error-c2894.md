---
title: Error del compilador C2894
ms.date: 11/04/2016
f1_keywords:
- C2894
helpviewer_keywords:
- C2894
ms.assetid: 4e250579-2b59-4993-a6f4-49273e7ecf06
ms.openlocfilehash: 4184f6360e36a4e8ca0cfc55dc6d9c515cf655d5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385971"
---
# <a name="compiler-error-c2894"></a>Error del compilador C2894

las plantillas no se pueden declarar tenga vinculación 'C'

Este error puede deberse a una plantilla definida dentro de un `extern` bloque "C".

El ejemplo siguiente genera C2894:

```
// C2894.cpp
extern "C" {
   template<class T> class stack {};   // C2894 fail

   template<class T> void f(const T &aT) {}   // C2894
}
```

El ejemplo siguiente genera C2894:

```
// C2894b.cpp
// compile with: /c
extern "C" template<class T> void f(const T &aT) {}   // C2894

template<class T> void f2(const T &aT) {}   // OK
```