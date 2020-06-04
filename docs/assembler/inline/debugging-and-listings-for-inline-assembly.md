---
title: Depuración y listas para el ensamblado insertado
ms.date: 08/30/2018
helpviewer_keywords:
- source level debugger
- __asm keyword [C++], debugging
- inline assembly, listings
- bugs, __asm blocks
- debugging [C++], inline assembly code
- inline assembly, debugging
ms.assetid: 69266930-6f9a-433d-b704-f4f44e7b2583
ms.openlocfilehash: 3254fb6b750466de0a38230c5e1cfa067c476f5e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169518"
---
# <a name="debugging-and-listings-for-inline-assembly"></a>Depuración y listas para el ensamblado insertado

**Específicos de Microsoft**

Los programas que contienen código de ensamblado alineado se pueden depurar con un depurador de nivel de origen si se compila con la opción [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md) .

En el depurador, puede establecer puntos de interrupción en las líneas de C o C++ y de lenguaje de ensamblado. Si habilita el modo de ensamblado mixto y de origen, puede mostrar la forma de origen y desensamblada del código de ensamblado.

Tenga en cuenta que la inclusión de varias instrucciones de ensamblado o del lenguaje de origen en una línea pueden dificultar la depuración. En modo de origen, puede utilizar el depurador para establecer puntos de interrupción en una línea, pero no en instrucciones individuales en la misma línea. El mismo principio se aplica a un bloque `__asm` definido como una macro de C, que se expande en una sola línea lógica.

Si crea una lista de ensamblados y de origen mixto con la opción del compilador [/FAS](../../build/reference/fa-fa-listing-file.md) , la lista contiene las formas de origen y de ensamblado de cada línea del lenguaje de ensamblado. Las macros no se expanden en listados, sino durante la compilación.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Consulte también

[Uso del lenguaje de ensamblado en bloques __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>
