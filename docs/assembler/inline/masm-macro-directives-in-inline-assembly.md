---
title: Directivas de macro de MASM de ensamblado insertado
ms.date: 08/30/2018
helpviewer_keywords:
- directives, macros
- inline assembly, macro directives
- macros, directives
- MASM (Microsoft Macro Assembler), inline assembly macro directives
ms.assetid: 83643a09-1699-40a8-8ef2-13502bc4ac2c
ms.openlocfilehash: 38b73346fc52f6b5efe478f8eb960ad049fae924
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169284"
---
# <a name="masm-macro-directives-in-inline-assembly"></a>Directivas de macro de MASM de ensamblado insertado

**Específicos de Microsoft**

El ensamblador alineado no es un Macro Assembler. No se pueden usar las directivas de macro de MASM (**macro**, `REPT`, **IRC**, `IRP`y `ENDM`) ni los operadores de macro ( **<>** , **!** , **&** , `%`y `.TYPE`). Sin embargo, un bloque `__asm` puede usar directivas de preprocesador de C. Vea [uso de C C++ o en bloques de __asm](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md) para obtener más información.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Consulte también

[Uso del lenguaje de ensamblado en bloques __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>
