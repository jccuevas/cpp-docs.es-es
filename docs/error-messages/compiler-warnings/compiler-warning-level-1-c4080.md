---
title: Del compilador (nivel 1) de la advertencia C4080 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4080
dev_langs:
- C++
helpviewer_keywords:
- C4080
ms.assetid: 964fb3f4-b9fd-450b-aa23-35cece126172
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 08ec1b7c65342ece3a7aebae673fce9a0d19b7a6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46074713"
---
# <a name="compiler-warning-level-1-c4080"></a>Advertencia del compilador (nivel 1) C4080

se esperaba un identificador para el nombre de segmento; se encontró 'símbolo'

El nombre del segmento en [#pragma alloc_text](../../preprocessor/alloc-text.md) debe ser una cadena o un identificador. El compilador omite el pragma si no se encuentra un identificador válido.

El ejemplo siguiente genera la advertencia C4080:

```
// C4080.cpp
// compile with: /W1
extern "C" void func(void);

#pragma alloc_text()   // C4080

// try this line to resolve the warning
// #pragma alloc_text("mysection", func)

int main() {
}

void func(void) {
}
```