---
title: Error del compilador C3208
ms.date: 11/04/2016
f1_keywords:
- C3208
helpviewer_keywords:
- C3208
ms.assetid: 6d060bfe-52cf-4599-8f70-bdeb5a670df3
ms.openlocfilehash: fa665f17de7ff6bec00ecdaf9d1749b0626c9181
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50628155"
---
# <a name="compiler-error-c3208"></a>Error del compilador C3208

'function': la lista de parámetros de plantilla de clase 'class' no coincide con la lista de parámetros de plantilla del parámetro 'parameter'

Un parámetro de plantilla no tiene el mismo número de parámetros de plantilla que la plantilla de clase proporcionada.

El ejemplo siguiente genera la advertencia C3208:

```
// C3208.cpp
template <template <class T> class TT >
int f();

template <class T1, class T2>
struct S;

template <class T1>
struct R;

int i = f<S>();   // C3208
// try the following line instead
// int i = f<R>();
```