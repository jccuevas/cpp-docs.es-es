---
title: Del compilador (nivel 1) de la advertencia C4075 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4075
dev_langs:
- C++
helpviewer_keywords:
- C4075
ms.assetid: 19a700b6-f210-4b9d-a2f2-76cfe39ab178
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5056c4bbca66b47ca991daf4c65485e80e43e0db
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46073036"
---
# <a name="compiler-warning-level-1-c4075"></a>Advertencia del compilador (nivel 1) C4075

inicializadores situados en un área de inicialización no reconocida

Un comando [#pragma init_seg](../../preprocessor/init-seg.md) usa un nombre de sección no reconocido. El compilador omite el comando **pragma** .

El ejemplo siguiente genera la advertencia C4075:

```
// C4075.cpp
// compile with: /W1
#pragma init_seg("mysegg")   // C4075

// try..
// #pragma init_seg(user)

int main() {
}
```