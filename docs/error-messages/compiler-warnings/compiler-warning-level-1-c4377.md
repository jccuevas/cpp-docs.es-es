---
title: Advertencia del compilador (nivel 1) C4377
ms.date: 11/04/2016
f1_keywords:
- C4377
helpviewer_keywords:
- C4377
ms.assetid: a1c797b8-cd5e-4a56-b430-d07932e811cf
ms.openlocfilehash: b75b6bee88d0b72e77b32e58ae2f4634a9c30fa0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187003"
---
# <a name="compiler-warning-level-1-c4377"></a>Advertencia del compilador (nivel 1) C4377

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
