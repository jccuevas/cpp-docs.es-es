---
title: Error del compilador C3851 | Microsoft Docs
ms.custom: ''
ms.date: 09/05/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3851
dev_langs:
- C++
helpviewer_keywords:
- C3851
ms.assetid: da30c21c-33aa-4439-8fb3-2f5021ea4985
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f495a61fd3c157862fe65d82c1ffe5f047d798dd
ms.sourcegitcommit: d10a2382832373b900b1780e1190ab104175397f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/06/2018
ms.locfileid: "43895180"
---
# <a name="compiler-error-c3851"></a>Error del compilador C3851

> '*char*': un nombre de carácter universal no puede designar un carácter en el juego de caracteres básico

## <a name="remarks"></a>Comentarios

En código compilado como C++, no se puede usar un nombre de carácter universal que representa un carácter del juego básico de caracteres de código fuente fuera un literal de cadena o carácter. Para obtener más información, consulte [juegos de caracteres](../../cpp/character-sets.md). En el código compilado como C, no se puede usar un nombre de carácter universal para los caracteres en el intervalo 0 x 20-0x7f, inclusive, excepto 0 x 24 ('$'), 0 x 40 ('\@'), o 0 x 60 ('\`').

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