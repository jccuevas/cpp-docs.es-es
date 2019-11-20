---
title: Advertencia del compilador (nivel 3) C4646
ms.date: 11/04/2016
f1_keywords:
- C4646
helpviewer_keywords:
- C4646
ms.assetid: 23677e8e-603e-40e0-b99a-2e4894a1278e
ms.openlocfilehash: 2f156bfbe92fbfb3437a7f0b9ac77a91976c2b1c
ms.sourcegitcommit: 217fac22604639ebd62d366a69e6071ad5b724ac
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/19/2019
ms.locfileid: "74189388"
---
# <a name="compiler-warning-level-3-c4646"></a>Advertencia del compilador (nivel 3) C4646

la función declarada con __declspec(noreturn) tiene un tipo de valor devuelto distinto de void

Una función marcada con el modificador [noreturn](../../cpp/noreturn.md) `__declspec` debe tener un tipo de vuelto [void](../../cpp/void-cpp.md) .

El ejemplo siguiente genera la advertencia C4646:

```cpp
// C4646.cpp
// compile with: /W3 /WX
int __declspec(noreturn) TestFunction()
{   // C4646  make return type void
}
```