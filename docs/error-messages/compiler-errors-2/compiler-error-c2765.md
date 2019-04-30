---
title: Error del compilador C2765
ms.date: 11/04/2016
f1_keywords:
- C2765
helpviewer_keywords:
- C2765
ms.assetid: 47ad86f3-a7e0-47ad-85ff-0f5534458cb9
ms.openlocfilehash: 7b34bd8b352e8872722e9402d8d0113ae6157292
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62257652"
---
# <a name="compiler-error-c2765"></a>Error del compilador C2765

'function': una especialización explícita de una plantilla de función no puede tener ningún argumento predeterminado

No se permiten argumentos predeterminados en una especialización explícita de una plantilla de función. Para obtener más información, consulte [especialización explícita de plantillas de función](../../cpp/explicit-specialization-of-function-templates.md).

El ejemplo siguiente genera C2765:

```
// C2765.cpp
template<class T> void f(T t) {};

template<> void f<char>(char c = 'a') {}   // C2765
// try the following line instead
// template<> void f<char>(char c) {}
```