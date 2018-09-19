---
title: Las directivas de datos y los operadores en código ensamblador en línea | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: conceptual
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6aff2f4c5ce5e7f5592aa9ec707d002c57f0eac0
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2018
ms.locfileid: "43678742"
---
# <a name="data-directives-and-operators-in-inline-assembly"></a>Directivas y operadores de datos de ensamblado insertado

**Específicos de Microsoft**

Aunque un bloque `__asm` puede hacer referencia a tipos de datos y objetos de C o C++, no puede definir objetos de datos con directivas u operadores de MASM. En concreto, no se puede usar las directivas de definición **DB**, `DW`, **DD**, `DQ`, `DT`, y `DF`, o los operadores `DUP` o  **Esto**. Las estructuras y los registros de MASM tampoco están disponibles. El ensamblador alineado no acepta las directivas `STRUC`, `RECORD`, **ancho**, o **máscara**.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Uso del lenguaje de ensamblado en bloques __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>