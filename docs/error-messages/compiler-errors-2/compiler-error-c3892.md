---
title: Error del compilador C3892
ms.date: 11/04/2016
f1_keywords:
- C3892
helpviewer_keywords:
- C3892
ms.assetid: 83fff42c-ea48-442f-bc2e-b33a6b99d890
ms.openlocfilehash: 73d96c61e918da3aabbfc00b83213fa79a2eedf9
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74736391"
---
# <a name="compiler-error-c3892"></a>Error del compilador C3892

' var ': no se puede asignar a una variable que sea const

Una variable const no se puede cambiar una vez declarada e inicializada.

En el ejemplo siguiente se genera C3892:

```cpp
// C3892.cpp
// compile with: /clr
ref struct Y1 {
   static const int staticConst = 9;
};

int main() {
   Y1::staticConst = 0;   // C3892
}
```
