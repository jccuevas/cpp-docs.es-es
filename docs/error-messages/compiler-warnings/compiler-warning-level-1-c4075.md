---
title: Advertencia del compilador (nivel 1) C4075
ms.date: 11/04/2016
f1_keywords:
- C4075
helpviewer_keywords:
- C4075
ms.assetid: 19a700b6-f210-4b9d-a2f2-76cfe39ab178
ms.openlocfilehash: f739e0363cc08d31bd26b063ef13658a392398bd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62208021"
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