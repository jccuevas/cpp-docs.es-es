---
title: ADVERTENCIA del compilador (nivel 1) C4965
ms.date: 11/04/2016
f1_keywords:
- C4965
helpviewer_keywords:
- C4965
ms.assetid: 47f3f6dc-459b-4a25-9947-f394c8966cb5
ms.openlocfilehash: ac1ffc1626a8b72fd7c9026afb6c6a54bace3750
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052232"
---
# <a name="compiler-warning-level-1-c4965"></a>ADVERTENCIA del compilador (nivel 1) C4965

cuadro implícito de entero 0; usar nullptr o conversión explícita

Características C++ visuales conversión boxing implícita de tipos de valor. Una instrucción que dio como resultado una asignación nula con extensiones administradas para C++ ahora se convierte en una asignación a un int con conversión boxing.

Para obtener más información, consulta [Boxing](../../extensions/boxing-cpp-component-extensions.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C4965.

```cpp
// C4965.cpp
// compile with: /clr /W1
int main() {
   System::Object ^o = 0;   // C4965

   // the previous line is the same as the following line
   // using Managed Extensions for C++
   // System::Object *o = __box(0);

   // OK
   System::Object ^o2 = nullptr;
   System::Object ^o3 = safe_cast<System::Object^>(0);
}
```