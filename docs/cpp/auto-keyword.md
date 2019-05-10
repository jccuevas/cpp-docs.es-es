---
title: auto (Palabra clave)
ms.date: 05/07/2019
ms.assetid: 744a41c0-2510-4140-a1be-96257e722908
ms.openlocfilehash: a695c33ab55601bb8d81b00f963646f6a48f09d5
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2019
ms.locfileid: "65222253"
---
# <a name="auto-keyword"></a>auto (Palabra clave)

El **automática** palabra clave es un especificador de declaración. Sin embargo, C++ estándar define un significado original y otro revisado para esta palabra clave. Antes de Visual Studio 2010, el **automática** palabra clave declara una variable en el *automática* clase de almacenamiento; es decir, una variable que tiene una duración local. A partir de Visual Studio 2010, el **automática** palabra clave declara una variable cuyo tipo se deduce de la expresión de inicialización en su declaración. El [/Zc: Auto&#91;-&#93; ](../build/reference/zc-auto-deduce-variable-type.md) controla el significado de la opción del compilador la **automática** palabra clave.

## <a name="syntax"></a>Sintaxis

```cpp
auto declarator ;
auto declarator initializer;
```

## <a name="remarks"></a>Comentarios

La definición de la **automática** los cambios en el lenguaje de programación de C++, pero no en el lenguaje de programación de C de palabra clave.

Los temas siguientes describen el **automática** palabra clave y la opción del compilador correspondiente:

- [Auto](../cpp/auto-cpp.md) describe la nueva definición de la **automática** palabra clave.

- [/ Zc: Auto (deducir tipo de Variable)](../build/reference/zc-auto-deduce-variable-type.md) describe la opción del compilador que indica al compilador qué definición de la **automática** palabra clave para usar.

## <a name="see-also"></a>Vea también

[Palabras clave](../cpp/keywords-cpp.md)