---
title: Directivas y operadores de datos de ensamblado insertado
ms.date: 08/30/2018
helpviewer_keywords:
- data directives [C++]
- __asm keyword [C++], referencing limitations
- MASM (Microsoft Macro Assembler), directives
- directives [C++], MASM
- MASM (Microsoft Macro Assembler), structures
- operators [MASM]
- inline assembly, operators
- inline assembly, data directives
- MASM (Microsoft Macro Assembler), operators
- structures [C++], MASM
ms.assetid: fb7410c7-156a-4131-bcfc-211aa70533e3
ms.openlocfilehash: 52e20c37f3066122a062e3fc9c64ced576b6c302
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62167236"
---
# <a name="data-directives-and-operators-in-inline-assembly"></a>Directivas y operadores de datos de ensamblado insertado

**Específicos de Microsoft**

Aunque un bloque `__asm` puede hacer referencia a tipos de datos y objetos de C o C++, no puede definir objetos de datos con directivas u operadores de MASM. En concreto, no se puede usar las directivas de definición **DB**, `DW`, **DD**, `DQ`, `DT`, y `DF`, o los operadores `DUP` o  **Esto**. Las estructuras y los registros de MASM tampoco están disponibles. El ensamblador alineado no acepta las directivas `STRUC`, `RECORD`, **ancho**, o **máscara**.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Uso del lenguaje de ensamblado en bloques __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>