---
title: ADVERTENCIA del compilador (nivel 1) C4172
ms.date: 11/04/2016
f1_keywords:
- C4172
helpviewer_keywords:
- C4172
ms.assetid: a8d2bf65-d8b1-4fe3-8340-a223d7e7fde6
ms.openlocfilehash: 7258172c00b1ff4aebb18fa2c715559fd82a2180
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80163551"
---
# <a name="compiler-warning-level-1-c4172"></a>ADVERTENCIA del compilador (nivel 1) C4172

devolver la dirección de la variable local o temporal

Una función devuelve la dirección de una variable local o un objeto temporal. Las variables locales y los objetos temporales se destruyen cuando se devuelve una función, por lo que la dirección devuelta no es válida.

Rediseñe la función para que no devuelva la dirección de un objeto local.

En el ejemplo siguiente se genera C4172:

```cpp
// C4172.cpp
// compile with: /W1 /LD
float f = 10;

const double& bar() {
// try the following line instead
// const float& bar() {
   return f;   // C4172
}
```
