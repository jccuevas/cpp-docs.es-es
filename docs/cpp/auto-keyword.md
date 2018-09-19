---
title: palabra clave Auto | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 744a41c0-2510-4140-a1be-96257e722908
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 10952e6360fc8170c59e9a67fe3027622cbea4bc
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46055538"
---
# <a name="auto-keyword"></a>auto (Palabra clave)

El **automática** palabra clave es un especificador de declaración. Sin embargo, C++ estándar define un significado original y otro revisado para esta palabra clave. Antes de Visual C++ 2010, la **automática** palabra clave declara una variable en el *automática* clase de almacenamiento; es decir, una variable que tiene una duración local. A partir de Visual C++ 2010, la **automática** palabra clave declara una variable cuyo tipo se deduce de la expresión de inicialización en su declaración. El [/Zc: Auto&#91;-&#93; ](../build/reference/zc-auto-deduce-variable-type.md) controla el significado de la opción del compilador la **automática** palabra clave.

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