---
title: Conversiones estándar y conversión boxing implícita
ms.date: 11/04/2016
helpviewer_keywords:
- boxing, implicit
ms.assetid: 33f7fc7d-5674-44a2-a859-0e6a04fae519
ms.openlocfilehash: b771f9e9c1dc05fcd2ead19f5202747d7c475a09
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/01/2019
ms.locfileid: "58774456"
---
# <a name="standard-conversions-and-implicit-boxing"></a>Conversiones estándar y conversión boxing implícita

El compilador elegirá una conversión estándar a través de una conversión que requiere la conversión boxing.

## <a name="example"></a>Ejemplo

```
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

## <a name="see-also"></a>Vea también

[Conversión boxing](../extensions/boxing-cpp-component-extensions.md)
