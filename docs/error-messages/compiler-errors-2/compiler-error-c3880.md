---
title: Error del compilador C3880
ms.date: 11/04/2016
f1_keywords:
- C3880
helpviewer_keywords:
- C3880
ms.assetid: b0e05d1e-32d0-4034-9246-f37d23573ea9
ms.openlocfilehash: 60b96a9e704215ec1cbbab63eb77ca5d43ccb627
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50626947"
---
# <a name="compiler-error-c3880"></a>Error del compilador C3880

'var': no puede ser un miembro de datos literal

El tipo de un [literal](../../windows/literal-cpp-component-extensions.md) atributo debe ser, o convertible de tiempo de compilación a uno de los tipos siguientes:

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