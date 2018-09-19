---
title: Definir una Macro NMAKE | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- macros, NMAKE
- defining NMAKE macros
- NMAKE macros, defining
ms.assetid: 45aae451-9d33-4a3d-8799-2e0cae17070d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c266a0be1c5ff16b719e9055f79b377d13ffbf3c
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45715720"
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