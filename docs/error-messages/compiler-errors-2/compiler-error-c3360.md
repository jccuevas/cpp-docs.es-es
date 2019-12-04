---
title: Error del compilador C3360
ms.date: 11/04/2016
f1_keywords:
- C3360
helpviewer_keywords:
- C3360
ms.assetid: 6acf983a-dbb6-422b-b045-a34bb4ba6761
ms.openlocfilehash: 785dbf3a96e97b68f2f8a5ede79ac8288eba4b21
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757376"
---
# <a name="compiler-error-c3360"></a>Error del compilador C3360

'string': no se puede crear el nombre

El valor que se pasó al atributo [uuid](../../windows/uuid-cpp-attributes.md) no era válido.

El ejemplo siguiente genera la advertencia C3360:

```cpp
// C3360.cpp
[ uuid("1") ]
// try this line instead
// [ uuid("12341234-1234-1234-1234-123412341234") ]
struct A   // C3360
{
};

int main()
{
}
```
