---
title: Definir una macro NMAKE
ms.date: 11/04/2016
helpviewer_keywords:
- macros, NMAKE
- defining NMAKE macros
- NMAKE macros, defining
ms.assetid: 45aae451-9d33-4a3d-8799-2e0cae17070d
ms.openlocfilehash: b163c3dcbfb079a532bd1babca4ee881407bafc1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62272235"
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

[Caracteres especiales en las macros](special-characters-in-macros.md)

[Macros null y no definidas](null-and-undefined-macros.md)

[Dónde definir macros](where-to-define-macros.md)

[Prioridad en definiciones de macro](precedence-in-macro-definitions.md)

## <a name="see-also"></a>Vea también

[Macros y NMAKE](macros-and-nmake.md)
