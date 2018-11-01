---
title: Advertencia del compilador (nivel 1) C4377
ms.date: 11/04/2016
f1_keywords:
- C4377
helpviewer_keywords:
- C4377
ms.assetid: a1c797b8-cd5e-4a56-b430-d07932e811cf
ms.openlocfilehash: d8c89967e0dc900e098ca03d22932451f26a6a0a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50531037"
---
# <a name="compiler-warning-level-1-c4377"></a>Advertencia del compilador (nivel 1) C4377

tipos nativos son privados de forma predeterminada; -d1PrivateNativeTypes está en desuso

En versiones anteriores, los tipos nativos en ensamblados eran públicos de forma predeterminada y una opción de compilador interno y no documentada (**/d1PrivateNativeTypes**) se usó para que sean privados.

Todos los tipos, nativos y CLR, ahora son privados de forma predeterminada en un ensamblado, por lo que **/d1PrivateNativeTypes** ya no es necesario.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C4377.

```
// C4377.cpp
// compile with: /clr /d1PrivateNativeTypes /W1
// C4377 warning expected
int main() {}
```