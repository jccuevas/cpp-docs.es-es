---
title: Directivas de Macro MASM de ensamblado insertado | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- directives, macros
- inline assembly, macro directives
- macros, directives
- MASM (Microsoft Macro Assembler), inline assembly macro directives
ms.assetid: 83643a09-1699-40a8-8ef2-13502bc4ac2c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 35ad22a9a4b79a31665ab6b156f8174d395bb0ee
ms.sourcegitcommit: fb9448eb96c6351a77df04af16ec5c0fb9457d9e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/13/2018
ms.locfileid: "43687978"
---
# <a name="masm-macro-directives-in-inline-assembly"></a>Directivas de macro de MASM de ensamblado insertado

**Específicos de Microsoft**

El ensamblador alineado no es un Macro Assembler. No se puede usar directivas de macro MASM (**MACRO**, `REPT`, **IRC**, `IRP`, y `ENDM`) ni operadores de macro (**<>**, **!** , **&**, `%`, y `.TYPE`). Sin embargo, un bloque `__asm` puede usar directivas de preprocesador de C. Consulte [uso de C o C++ en bloques __asm](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md) para obtener más información.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Uso del lenguaje de ensamblado en bloques __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>