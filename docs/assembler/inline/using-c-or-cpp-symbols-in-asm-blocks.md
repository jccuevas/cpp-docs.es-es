---
title: Usar símbolos de C o C++ en bloques __asm
ms.date: 08/30/2018
helpviewer_keywords:
- __asm keyword [C++], syntax
- symbols, in __asm blocks
- Visual C, symbols in __asm blocks
- __asm keyword [C++], C/C++ elements in
- Visual C++, in __asm blocks
ms.assetid: 0758ffdc-dfe9-41c8-a5e1-fd395bcac328
ms.openlocfilehash: fd9f8b444d263818aca1b16260f70730d5350e7c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169115"
---
# <a name="using-c-or-c-symbols-in-__asm-blocks"></a>Usar símbolos de C o C++ en bloques __asm

**Específicos de Microsoft**

Un bloque `__asm` puede hacer referencia a cualquier símbolo de C o C++ en el ámbito donde aparece el bloque. (Los símbolos de C y C++ son nombres de variable, nombres de función y etiquetas; es decir, nombres que no sean constantes simbólicas ni miembros de `enum`. No se puede llamar a funciones miembro de C++).

Se aplican algunas restricciones al uso de los símbolos de C y C++:

- Cada instrucción del lenguaje de ensamblado solo puede contener un símbolo de C o C++. Solo pueden aparecer varios símbolos en la misma instrucción de ensamblado con expresiones de **longitud**, **tipo**y **tamaño** .

- Las funciones a las que se hace referencia en un bloque `__asm` se deben declarar antes (mediante prototipo) en el programa. De lo contrario, el compilador no podrá distinguir los nombres de función y las etiquetas en el bloque `__asm`.

- En un bloque `__asm` no puede haber ningún símbolo de C o C++ escrito igual que las palabras reservadas de MASM (independientemente de si es en mayúsculas o minúsculas). Las palabras reservadas de MASM incluyen nombres de instrucción como los nombres de las instrucciones de **envío** y de registro como, por ejemplo, si.

- Las etiquetas de estructura y unión no se reconocen en los bloques `__asm`.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Consulte también

[Uso de C o C++ en bloques __asm](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)<br/>
