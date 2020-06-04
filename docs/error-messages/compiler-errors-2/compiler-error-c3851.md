---
title: Error del compilador C3851
ms.date: 09/05/2018
f1_keywords:
- C3851
helpviewer_keywords:
- C3851
ms.assetid: da30c21c-33aa-4439-8fb3-2f5021ea4985
ms.openlocfilehash: 97d9ef1eeeffa0e5a63d2c8ae2428a3fad0ff238
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165592"
---
# <a name="compiler-error-c3851"></a>Error del compilador C3851

> '*Char*': un nombre de carácter universal no puede designar un carácter en el juego de caracteres básico

## <a name="remarks"></a>Observaciones

En código compilado como C++, no se puede usar un nombre de carácter universal que representa un carácter del juego básico de caracteres de código fuente fuera un literal de cadena o carácter. Para obtener más información, vea [Character Sets](../../cpp/character-sets.md). En el código compilado como C, no se puede usar un nombre de carácter universal para los caracteres del intervalo 0x20-0x7F, inclusive, excepto 0x24 (' $ '), 0x40 ('\@') o 0x60 ('\`').

## <a name="example"></a>Ejemplo

En los ejemplos siguientes se genera el error C3851 y se muestra cómo corregirlo:

```cpp
// C3851.cpp
int main()
{
   int test1_\u0041 = 0;   // C3851, \u0041 = 'A' in basic character set
   int test2_A = 0;        // OK
}
```
