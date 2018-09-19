---
title: Error del compilador C2765 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2765
dev_langs:
- C++
helpviewer_keywords:
- C2765
ms.assetid: 47ad86f3-a7e0-47ad-85ff-0f5534458cb9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 708a4c326e87cf580208e26ef5ffe540afd52f95
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46085139"
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