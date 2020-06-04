---
title: Uso de C o C++ en bloques __asm
ms.date: 08/30/2018
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
ms.openlocfilehash: 16b298b92a4ba40d9091499a1821ad4f3c413d6c
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "74854529"
---
# <a name="using-c-or-c-in-__asm-blocks"></a>Uso de C o C++ en bloques __asm

**Específicos de Microsoft**

Puesto que las instrucciones de ensamblado insertado se pueden combinar con instrucciones de C o C++, pueden hacer referencia a variables de C o C++ por nombre y usar muchos otros elementos de esos lenguajes.

Un bloque `__asm` puede usar los elementos de lenguaje siguientes:

- Símbolos, incluidos etiquetas y nombres de variable y de función

- Constantes, incluidas constantes simbólicas y miembros de `enum`

- Macros y directivas de preprocesador

- Comentarios (ambos __/\* \*/__ y __//__ )

- Nombres de tipo (dondequiera que un tipo MASM sea legal)

- nombres de `typedef`, utilizados generalmente con operadores como **ptr** y **tipo** , o para especificar miembros de estructura o Unión

Dentro de un bloque `__asm`, puede especificar constantes de tipo entero con notación C o notación de base de ensamblador (0x100 y 100h son equivalentes, por ejemplo). Esto permite definir (mediante `#define`) una constante en C y, a continuación, usarla en C o C++ y en partes de ensamblado del programa. También puede especificar constantes en octal precediéndolas con un 0. Por ejemplo, 0777 especifica una constante octal.

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?

- [Uso de operadores en bloques __asm](../../assembler/inline/using-operators-in-asm-blocks.md)

- [Usar bloques de C++ __Asm de C o Symbols_in](../../assembler/inline/using-c-or-cpp-symbols-in-asm-blocks.md)

- [Acceso a datos de C o C++ en bloques __asm](../../assembler/inline/accessing-c-or-cpp-data-in-asm-blocks.md)

- [Escribir funciones con ensamblado insertado](../../assembler/inline/writing-functions-with-inline-assembly.md)

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Ensamblador insertado](../../assembler/inline/inline-assembler.md)<br/>
