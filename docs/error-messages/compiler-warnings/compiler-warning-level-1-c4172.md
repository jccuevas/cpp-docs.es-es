---
title: ADVERTENCIA del compilador (nivel 1) C4172
ms.date: 11/04/2016
f1_keywords:
- C4172
helpviewer_keywords:
- C4172
ms.assetid: a8d2bf65-d8b1-4fe3-8340-a223d7e7fde6
ms.openlocfilehash: 7d53972dbcb2e3ab6a95b0b874cc6bb98cd66840
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/05/2019
ms.locfileid: "73624824"
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