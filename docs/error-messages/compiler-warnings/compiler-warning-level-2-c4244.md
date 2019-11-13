---
title: ADVERTENCIA del compilador (nivel 2) C4244
ms.date: 11/04/2016
f1_keywords:
- C4244
helpviewer_keywords:
- C4244
ms.assetid: 2c19d157-21d1-42c2-a6c0-3f30f2ce3813
ms.openlocfilehash: 43d8a992801d556ce85577f5f9da1bec584cb173
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052125"
---
# <a name="compiler-warning-level-2-c4244"></a>ADVERTENCIA del compilador (nivel 2) C4244

' argument ': conversión de ' tipo1 ' a ' tipo2 ', posible pérdida de datos

Un tipo de punto flotante se convirtió a un tipo entero.  Se ha producido una posible pérdida de datos.

Si recibe el error C4244, debe cambiar el programa para que use tipos compatibles o agregar lógica al código, para asegurarse de que el intervalo de valores posibles sea siempre compatible con los tipos que usa.

C4244 también se puede activar en el nivel 3 y 4; vea [Advertencia del compilador (niveles 3 y 4) C4244](../../error-messages/compiler-warnings/compiler-warning-levels-3-and-4-c4244.md) para obtener más información.

## <a name="example"></a>Ejemplo

El siguiente ejemplo genera C4244:

```cpp
// C4244_level2.cpp
// compile with: /W2

int f(int x){ return 0; }
int main() {
   double x = 10.1;
   int i = 10;
   return (f(x));   // C4244
   // try the following line instead
   // return (f(i));
}
```