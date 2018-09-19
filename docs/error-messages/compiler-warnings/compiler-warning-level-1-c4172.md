---
title: Del compilador (nivel 1) de la advertencia C4172 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4172
dev_langs:
- C++
helpviewer_keywords:
- C4172
ms.assetid: a8d2bf65-d8b1-4fe3-8340-a223d7e7fde6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 56f606b48fb060472dd67d34800c06946bc41712
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46043513"
---
# <a name="compiler-warning-level-1-c4172"></a>Del compilador (nivel 1) de la advertencia C4172

devolución de dirección de variable local o temporal

Una función devuelve la dirección de un objeto temporal o variable local. Objetos temporales y variables locales se destruyen cuando se devuelve una función, por lo que la dirección devuelta no es válida.

Vuelva a diseñar la función para que no devuelve la dirección de un objeto local.

El ejemplo siguiente genera C4172:

```
// C4172.cpp
// compile with: /W1 /LD
float f = 10;

const double& bar() {
// try the following line instead
// const float& bar() {
   return f;   // C4172
}
```