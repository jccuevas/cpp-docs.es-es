---
title: Advertencia del compilador (nivel 1) C4965
ms.date: 11/04/2016
f1_keywords:
- C4965
helpviewer_keywords:
- C4965
ms.assetid: 47f3f6dc-459b-4a25-9947-f394c8966cb5
ms.openlocfilehash: 7d77df395d680b467d1a04a3f59c9822842f99f5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50653107"
---
# <a name="compiler-warning-level-1-c4965"></a>Advertencia del compilador (nivel 1) C4965

conversión boxing implícita de entero 0; Utilice nullptr o conversión explícita

Visual C++ incluye la conversión boxing implícita de tipos de valor. Una instrucción que dieron lugar a una asignación de valores null mediante extensiones administradas para C++ ahora se convierte en una asignación a un int con conversión boxing.

Para obtener más información, consulta [Boxing](../../windows/boxing-cpp-component-extensions.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C4965.

```
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