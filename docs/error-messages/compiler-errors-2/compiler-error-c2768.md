---
title: Error del compilador C2768 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2768
dev_langs:
- C++
helpviewer_keywords:
- C2768
ms.assetid: a7f6047a-6a80-4737-ad5c-c12868639fb5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4c76173f99dbc2fb415b60212109242845501694
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46109111"
---
# <a name="compiler-error-c2768"></a>Error del compilador C2768

'function': uso no válido de argumentos de plantilla explícitos

El compilador no pudo determinar si una definición de función se suponía que debía para ser una especialización explícita de una plantilla de función o si la definición de función se suponía que debía para ser para una nueva función.

Este error se introdujo en Visual Studio .NET 2003 como parte de las mejoras de conformidad del compilador.

El ejemplo siguiente genera C2768:

```
// C2768.cpp
template<typename T>
void f(T) {}

void f<int>(int) {}   // C2768

// an explicit specialization
template<>
void f<int>(int) {}

// global nontemplate function overload
void f(int) {}
```