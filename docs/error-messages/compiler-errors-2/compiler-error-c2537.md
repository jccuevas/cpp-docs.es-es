---
title: Error del compilador C2537 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2537
dev_langs:
- C++
helpviewer_keywords:
- C2537
ms.assetid: aee81d8e-300e-4a8b-b6c4-b3828398b34e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 65db4fa66d147cc46c1a6013d07048892dfa0800
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46136028"
---
# <a name="compiler-error-c2537"></a>Error del compilador C2537

'especificador': especificación de vinculación no válida

Causas posibles:

1. No se admite el especificador de vinculación. Se admite solo el especificador de vinculación de "C".

1. Vinculación de "C" se especifica más de una función de un conjunto de funciones sobrecargadas. Esto no está permitido.

El ejemplo siguiente genera C2537:

```
// C2537.cpp
// compile with: /c
extern "c" void func();   // C2537
extern "C" void func2();   // OK
```