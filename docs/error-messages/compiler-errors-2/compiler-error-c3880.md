---
title: Error del compilador C3880
ms.date: 11/04/2016
f1_keywords:
- C3880
helpviewer_keywords:
- C3880
ms.assetid: b0e05d1e-32d0-4034-9246-f37d23573ea9
ms.openlocfilehash: 0b169309db88291f8a83b6d1192787b6396e84a5
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/01/2019
ms.locfileid: "58770513"
---
# <a name="compiler-error-c3880"></a>Error del compilador C3880

'var': no puede ser un miembro de datos literal

El tipo de un [literal](../../extensions/literal-cpp-component-extensions.md) atributo debe ser, o convertible de tiempo de compilación a uno de los tipos siguientes:

- tipo entero

- cadena

- enumeración con un tipo entero o subyacente

El ejemplo siguiente genera C3880:

```
// C3880.cpp
// compile with: /clr /c
ref struct Y1 {
   literal System::Decimal staticConst1 = 10;   // C3880
   literal int staticConst2 = 10;   // OK
};
```