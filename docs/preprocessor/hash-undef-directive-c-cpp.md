---
title: '#undef (Directiva) (C/C++)'
ms.date: 08/29/2019
f1_keywords:
- '#undef'
helpviewer_keywords:
- '#undef directive'
- undef directive (#undef)
- preprocessor, directives
ms.assetid: 88900e0e-2c19-4a63-b681-f3d3133c24ca
ms.openlocfilehash: 1a69bc568579e7da7c7e3816cb67c8153b8f1a27
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220216"
---
# <a name="undef-directive-cc"></a>#undef (Directiva) (C++C/)

Quita (anula la definición de) un nombre creado previamente con `#define`.

## <a name="syntax"></a>Sintaxis

> **#undef** *identificador* de

## <a name="remarks"></a>Comentarios

La directiva **#undef** quita la definición actual del *identificador*. Por consiguiente, el preprocesador omite las apariciones posteriores del *identificador* . Para quitar una definición de macro mediante **#undef**, proporcione solo el *identificador*de macro, no una lista de parámetros.

También puede aplicar la directiva **#undef** a un identificador que no tiene ninguna definición anterior. De este modo se garantiza que el identificador no esté definido. El reemplazo de macros no se realiza dentro de **#undef** instrucciones.

Normalmente, la directiva **#undef** se empareja con una `#define` Directiva para crear una región en un programa de origen en el que un identificador tiene un significado especial. Por ejemplo, una función específica del programa de origen puede utilizar constantes de manifiesto para definir valores específicos del entorno que no afecten al resto del programa. La directiva **#undef** también funciona con la `#if` Directiva para controlar la compilación condicional del programa de origen. Para obtener más información, vea [las directivas #if, #elif, #else y #endif](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md).

En el ejemplo siguiente, la directiva **#undef** quita las definiciones de una constante simbólica y una macro. Observe que solo se proporciona el identificador de la macro.

```C
#define WIDTH 80
#define ADD( X, Y ) ((X) + (Y))
.
.
.
#undef WIDTH
#undef ADD
```

**Específicos de Microsoft**

Las macros pueden estar sin definir desde la línea de comandos `/U` mediante la opción, seguido de los nombres de macro que no se van a definir. El efecto de emitir este comando es equivalente a una secuencia de instrucciones `#undef` de *nombre de macro* al principio del archivo.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Directivas de preprocesador](../preprocessor/preprocessor-directives.md)
