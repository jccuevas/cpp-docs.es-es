---
title: Error del compilador C3646
ms.date: 06/14/2018
f1_keywords:
- C3646
helpviewer_keywords:
- C3646
ms.assetid: 4391ead2-9637-4ca3-aeda-5a991b18d66d
ms.openlocfilehash: 13a3ebeb6e7783687abc73cd0dcc018abe827809
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80200478"
---
# <a name="compiler-error-c3646"></a>Error del compilador C3646

> ' Specifier ': especificador de invalidación desconocido

## <a name="remarks"></a>Observaciones

El compilador encontró un token en la posición donde esperaba encontrar un especificador de invalidación, pero el compilador no reconoció el token.

Por ejemplo, si el *especificador* no reconocido es **_NOEXCEPT**, reemplácelo por la palabra clave **noexception**.

Para obtener más información, vea [especificadores de invalidación](../../extensions/override-specifiers-cpp-component-extensions.md).

## <a name="example"></a>Ejemplo

En el siguiente ejemplo se genera C3646 y se muestra una manera de corregirlo:

```cpp
// C3646.cpp
// compile with: /clr /c
ref class C {
   void f() unknown;   // C3646
   // try the following line instead
   // virtual void f() abstract;
};
```
