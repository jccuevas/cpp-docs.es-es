---
title: ADVERTENCIA del compilador (nivel 1) C4377
ms.date: 11/04/2016
f1_keywords:
- C4377
helpviewer_keywords:
- C4377
ms.assetid: a1c797b8-cd5e-4a56-b430-d07932e811cf
ms.openlocfilehash: 30e2ecb1d5e0de290c028cdfb53c7df831a732b4
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966460"
---
# <a name="compiler-warning-level-1-c4377"></a>ADVERTENCIA del compilador (nivel 1) C4377

de forma predeterminada, los tipos nativos son privados; -d1PrivateNativeTypes está en desuso

En versiones anteriores, los tipos nativos de los ensamblados eran públicos de forma predeterminada y se usaba una opción del compilador interna, no documentada ( **/d1PrivateNativeTypes**) para hacerlos privados.

Todos los tipos, nativo y CLR, son ahora privados de forma predeterminada en un ensamblado, por lo que **/d1PrivateNativeTypes** ya no es necesario.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C4377.

```cpp
// C4377.cpp
// compile with: /clr /d1PrivateNativeTypes /W1
// C4377 warning expected
int main() {}
```