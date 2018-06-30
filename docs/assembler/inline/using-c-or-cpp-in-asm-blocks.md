---
title: Uso de C o C++ en bloques __asm | Documentos de Microsoft
ms.custom: ''
ms.date: 06/25/2018
ms.technology:
- cpp-masm
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- inline assembly, mixing instructions with C/C++ statements
- symbols, in __asm blocks
- macros, __asm blocks
- preprocessor directives, used in __asm blocks
- type names, used in __asm blocks
- preprocessor directives
- preprocessor, directives
- constants, in __asm blocks
- comments, in __asm blocks
- typedef names, used in __asm blocks
- __asm keyword [C++], C/C++ elements in
ms.assetid: ae8b2b52-6b75-42e3-ac0c-ad02d922ed97
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 96ed46cdf44ccacee806dd03bf7eacca26eec32d
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/29/2018
ms.locfileid: "37120955"
---
# <a name="using-c-or-c-in-asm-blocks"></a>Uso de C o C++ en bloques __asm

** Específicos de Microsoft **

Puesto que las instrucciones de ensamblado insertado se pueden combinar con instrucciones de C o C++, pueden hacer referencia a variables de C o C++ por nombre y usar muchos otros elementos de esos lenguajes.

Un bloque `__asm` puede usar los elementos de lenguaje siguientes:

- Símbolos, incluidos etiquetas y nombres de variable y de función

- Constantes, incluidas constantes simbólicas y miembros de `enum`

- Macros y directivas de preprocesador

- Comentarios (tanto __/ \* \* /__ y __//__ )

- Nombres de tipo (dondequiera que un tipo MASM sea legal)

- `typedef` nombres, utilizados normalmente con operadores como **PTR** y **tipo** o especificar miembros de estructura o unión

Dentro de un bloque `__asm`, puede especificar constantes de tipo entero con notación C o notación de base de ensamblador (0x100 y 100h son equivalentes, por ejemplo). Esto permite definir (mediante `#define`) una constante en C y, a continuación, usarla en C o C++ y en partes de ensamblado del programa. También puede especificar constantes en octal precediéndolas con un 0. Por ejemplo, 0777 especifica una constante octal.

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?

- [Uso de operadores en bloques __asm](../../assembler/inline/using-operators-in-asm-blocks.md)

- [Uso de C o C++ símbolos bloques __asm](../../assembler/inline/using-c-or-cpp-symbols-in-asm-blocks.md)

- [Acceso a datos de C o C++ en bloques __asm](../../assembler/inline/accessing-c-or-cpp-data-in-asm-blocks.md)

- [Escribir funciones con ensamblado insertado](../../assembler/inline/writing-functions-with-inline-assembly.md)

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Ensamblador insertado](../../assembler/inline/inline-assembler.md)
