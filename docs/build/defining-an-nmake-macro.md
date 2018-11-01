---
title: Definir una macro NMAKE
ms.date: 11/04/2016
helpviewer_keywords:
- macros, NMAKE
- defining NMAKE macros
- NMAKE macros, defining
ms.assetid: 45aae451-9d33-4a3d-8799-2e0cae17070d
ms.openlocfilehash: 860a5766e0d766f7426cb6c1a7eaf5db02686aa4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50499034"
---
# <a name="defining-an-nmake-macro"></a>Definir una macro NMAKE

## <a name="syntax"></a>Sintaxis

```

macroname=string
```

## <a name="remarks"></a>Comentarios

El *Nombredelamacro* es una combinación de letras, dígitos y caracteres de subrayado (_) hasta 1.024 caracteres y distingue caso. El *Nombredelamacro* puede contener una macro. Si *Nombredelamacro* consta únicamente de una macro, la macro que se va a invocar no puede ser null o undefined.

El `string` puede ser cualquier secuencia de cero o más caracteres. Una cadena nula contiene cero caracteres o solo espacios o tabulaciones. El `string` puede contener una llamada de macro.

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?

[Caracteres especiales en las macros](../build/special-characters-in-macros.md)

[Macros null y no definidas](../build/null-and-undefined-macros.md)

[Dónde definir macros](../build/where-to-define-macros.md)

[Prioridad en definiciones de macro](../build/precedence-in-macro-definitions.md)

## <a name="see-also"></a>Vea también

[Macros y NMAKE](../build/macros-and-nmake.md)