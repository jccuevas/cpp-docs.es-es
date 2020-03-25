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
ms.openlocfilehash: 916dce0346bebfc5ff65ca558ae75317a187660a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169544"
---
# <a name="data-directives-and-operators-in-inline-assembly"></a>Directivas y operadores de datos de ensamblado insertado

**Específicos de Microsoft**

Aunque un bloque `__asm` puede hacer referencia a tipos de datos y objetos de C o C++, no puede definir objetos de datos con directivas u operadores de MASM. En concreto, no puede usar las directivas de definición **dB**, `DW`, **DD**, `DQ`, `DT`y `DF`, ni los operadores `DUP` o **this**. Las estructuras y los registros de MASM tampoco están disponibles. El ensamblador alineado no acepta las directivas `STRUC`, `RECORD`, **width**o **Mask**.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Consulte también

[Uso del lenguaje de ensamblado en bloques __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>
