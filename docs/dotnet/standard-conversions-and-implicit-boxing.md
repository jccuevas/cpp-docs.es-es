---
title: Conversiones estándar y conversión boxing implícita
ms.date: 11/04/2016
helpviewer_keywords:
- boxing, implicit
ms.assetid: 33f7fc7d-5674-44a2-a859-0e6a04fae519
ms.openlocfilehash: bc2c804474be55a9aea7d590abb1e0ac2b72ad90
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2019
ms.locfileid: "79545148"
---
# <a name="standard-conversions-and-implicit-boxing"></a>Conversiones estándar y conversión boxing implícita

El compilador elegirá una conversión estándar a través de una conversión que requiere conversión boxing.

## <a name="example"></a>Ejemplo

```cpp
// clr_implicit_boxing_Std_conversion.cpp
// compile with: /clr
int f3(int ^ i) {   // requires boxing
   return 1;
}

int f3(char c) {   // no boxing required, standard conversion
   return 2;
}

int main() {
   int i = 5;
   System::Console::WriteLine(f3(i));
}
```

```Output
2
```

## <a name="see-also"></a>Consulte también

[Conversión boxing](../extensions/boxing-cpp-component-extensions.md)
