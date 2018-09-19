---
title: Error del compilador C2448 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2448
dev_langs:
- C++
helpviewer_keywords:
- C2448
ms.assetid: e255df3c-f861-4b4d-a193-8768cef061a5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b5d3de3b8d4d5d184bb33214679842c557aadf7d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46136002"
---
# <a name="compiler-error-c2448"></a>Error del compilador C2448

'identifier': inicializador de estilo de función parece ser una definición de función

La definición de función no es correcta.

Este error puede deberse a una lista formal del lenguaje C de estilo antiguo.

El ejemplo siguiente genera C2448:

```
// C2448.cpp
void func(c)
   int c;
{}   // C2448
```