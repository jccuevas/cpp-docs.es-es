---
title: Error del compilador C3646
ms.date: 06/14/2018
f1_keywords:
- C3646
helpviewer_keywords:
- C3646
ms.assetid: 4391ead2-9637-4ca3-aeda-5a991b18d66d
ms.openlocfilehash: 04ff1d026c97c56611f8b786d8a7254db711e4a8
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/01/2019
ms.locfileid: "58769041"
---
# <a name="compiler-error-c3646"></a>Error del compilador C3646

> 'especificador': especificador de invalidación desconocido

## <a name="remarks"></a>Comentarios

El compilador encontró un token en la posición donde esperaba encontrar un especificador de invalidación, pero el compilador no reconoció el token.

Por ejemplo, si la no reconocido *especificador* es **_NOEXCEPT**, reemplácelo por la palabra clave **noexcept**.

Para obtener más información, consulte [especificadores de invalidación](../../extensions/override-specifiers-cpp-component-extensions.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C3646 y muestra cómo corregirlo:

```cpp
// C3646.cpp
// compile with: /clr /c
ref class C {
   void f() unknown;   // C3646
   // try the following line instead
   // virtual void f() abstract;
};
```