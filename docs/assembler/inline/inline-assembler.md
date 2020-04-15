---
title: Ensamblador insertado
ms.date: 08/30/2018
helpviewer_keywords:
- assembler [C++]
- assembler [C++], inline
- assembly language [C++], inline
- inline assembler [C++]
- inline assembly [C++]
ms.assetid: 7e13f18f-3628-4306-8b81-4a6d09c043fe
ms.openlocfilehash: 2050f59601755a93c73b743debacbf52ba9cec05
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318076"
---
# <a name="inline-assembler"></a>Ensamblador insertado

**Microsoft Specific**

El lenguaje de ensamblado sirve para muchos propósitos, como mejorar la velocidad del programa, reducir la memoria necesaria y supervisar el hardware. Puede utilizar el ensamblador alineado para incrustar instrucciones de lenguaje de ensamblado directamente en los programas de origen C y C++ sin realizar pasos adicionales de ensamblado y vínculo. El ensamblador alineado se compila en el compilador, por lo que no es necesario un ensamblador independiente como Microsoft Macro Assembler (MASM).

> [!NOTE]
> Los programas con código ensamblador alineado no son totalmente portables a otras plataformas de hardware. Si está diseñando para la portabilidad, evite utilizar el ensamblador alineado.

El ensamblado en línea no se admite en los procesadores ARM y x64.  En los temas siguientes se explica cómo usar el ensamblador alineado de Visual C/C++ con procesadores x86:

- [Información general de ensamblador alineado](../../assembler/inline/inline-assembler-overview.md)

- [Ventajas de ensamblado alineado](../../assembler/inline/advantages-of-inline-assembly.md)

- [__asm](../../assembler/inline/asm.md)

- [Uso del lenguaje de ensamblado en bloques __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)

- [Uso de C o C++ en bloques __asm](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)

- [Uso y conservación de registros en un ensamblado alineado](../../assembler/inline/using-and-preserving-registers-in-inline-assembly.md)

- [Salto a etiquetas en un ensamblado alineado](../../assembler/inline/jumping-to-labels-in-inline-assembly.md)

- [Llamar a las funciones De C en el ensamblaje en línea](../../assembler/inline/calling-c-functions-in-inline-assembly.md)

- [Llamada a funciones C++ en el ensamblado alineado](../../assembler/inline/calling-cpp-functions-in-inline-assembly.md)

- [Definición de bloques __asm como macros de C](../../assembler/inline/defining-asm-blocks-as-c-macros.md)

- [Optimización de un ensamblado alineado](../../assembler/inline/optimizing-inline-assembly.md)

**END Microsoft Specific**

## <a name="see-also"></a>Consulte también

[Intrínsecos del compilador y lenguaje ensamblador](../../intrinsics/compiler-intrinsics-and-assembly-language.md)<br/>
[Referencia del idioma C++](../../cpp/cpp-language-reference.md)<br/>
