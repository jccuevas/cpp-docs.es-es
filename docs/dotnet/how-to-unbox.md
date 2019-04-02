---
title: Filtrar aplicar la conversión unboxing
ms.date: 11/04/2016
helpviewer_keywords:
- unboxing
ms.assetid: 75794696-9275-47bf-9a7d-5abe6585ab91
ms.openlocfilehash: 640d2488d0fa1111262af371d88aea8f61511fa8
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/01/2019
ms.locfileid: "58780904"
---
# <a name="how-to-unbox"></a>Filtrar aplicar la conversión unboxing

Muestra cómo aplicar la conversión unboxing y modificar un valor.

## <a name="example"></a>Ejemplo

```
// vcmcppv2_unboxing.cpp
// compile with: /clr
using namespace System;

int main() {
   int ^ i = gcnew int(13);
   int j;
   Console::WriteLine(*i);   // unboxing
   *i = 14;   // unboxing and assignment
   Console::WriteLine(*i);
   j = safe_cast<int>(i);   // unboxing and assignment
   Console::WriteLine(j);
}
```

```Output
13
14
14
```

## <a name="see-also"></a>Vea también

[Conversión boxing](../extensions/boxing-cpp-component-extensions.md)
