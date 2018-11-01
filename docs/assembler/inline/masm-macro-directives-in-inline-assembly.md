---
title: Directivas de macro de MASM de ensamblado insertado
ms.date: 08/30/2018
helpviewer_keywords:
- directives, macros
- inline assembly, macro directives
- macros, directives
- MASM (Microsoft Macro Assembler), inline assembly macro directives
ms.assetid: 83643a09-1699-40a8-8ef2-13502bc4ac2c
ms.openlocfilehash: 7e1bed782d28a5bf7c934c3f57f50aae70038578
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50508932"
---
# <a name="masm-macro-directives-in-inline-assembly"></a>Directivas de macro de MASM de ensamblado insertado

**Específicos de Microsoft**

El ensamblador alineado no es un Macro Assembler. No se puede usar directivas de macro MASM (**MACRO**, `REPT`, **IRC**, `IRP`, y `ENDM`) ni operadores de macro (**<>**, **!** , **&**, `%`, y `.TYPE`). Sin embargo, un bloque `__asm` puede usar directivas de preprocesador de C. Consulte [uso de C o C++ en bloques __asm](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md) para obtener más información.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Uso del lenguaje de ensamblado en bloques __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>