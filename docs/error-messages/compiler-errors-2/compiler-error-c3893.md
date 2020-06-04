---
title: Error del compilador C3893
ms.date: 11/04/2016
f1_keywords:
- C3893
helpviewer_keywords:
- C3893
ms.assetid: 90d52eae-6ef2-4db1-b7ad-92f9e8b140fb
ms.openlocfilehash: 20c17eaa6555b5511ecbc930eacdb2ec92475b23
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74749508"
---
# <a name="compiler-error-c3893"></a>Error del compilador C3893

' var ': el uso del valor l del miembro de datos initonly solo se permite en un constructor de instancia de la clase ' type_name '

Los miembros de datos [InitOnly](../../dotnet/initonly-cpp-cli.md) estáticos solo pueden tomar su dirección en un constructor estático.

Los miembros de datos initonly (no estáticos) de instancia solo pueden tomar su dirección en constructores de instancia (no estáticos).

En el ejemplo siguiente se genera C3893:

```cpp
// C3893.cpp
// compile with: /clr
ref struct Y1 {
   Y1() : data_var(0) {
      int% i = data_var;   // OK
   }
   initonly int data_var;
};

int main(){
   Y1^ y= gcnew Y1;
   int% i = y->data_var;   // C3893
}
```
