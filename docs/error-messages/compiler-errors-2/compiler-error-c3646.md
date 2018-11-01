---
title: Error del compilador C3646
ms.date: 06/14/2018
f1_keywords:
- C3646
helpviewer_keywords:
- C3646
ms.assetid: 4391ead2-9637-4ca3-aeda-5a991b18d66d
ms.openlocfilehash: df2e52631ed75cc4a473429ea35e136ed0a88f98
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50606731"
---
# <a name="compiler-error-c3646"></a>Error del compilador C3646

> 'especificador': especificador de invalidación desconocido

## <a name="remarks"></a>Comentarios

El compilador encontró un token en la posición donde esperaba encontrar un especificador de invalidación, pero el compilador no reconoció el token.

Por ejemplo, si la no reconocido *especificador* es **_NOEXCEPT**, reemplácelo por la palabra clave **noexcept**.

Para obtener más información, consulte [especificadores de invalidación](../../windows/override-specifiers-cpp-component-extensions.md).

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