---
title: Directivas de Macro MASM de ensamblado en línea | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: cfd8e3ca5fb6bf65a288c17b1754d567b2b081a8
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/28/2018
ms.locfileid: "32049856"
---
# <a name="masm-macro-directives-in-inline-assembly"></a>Directivas de macro de MASM de ensamblado insertado
## <a name="microsoft-specific"></a>Específicos de Microsoft  
 El ensamblador alineado no es un Macro Assembler. No se puede usar directivas de macro MASM (**MACRO**, `REPT`, **IRC**, `IRP`, y `ENDM`) u operadores de macro (**<>**, **!** , **&**, `%`, y `.TYPE`). Sin embargo, un bloque `__asm` puede usar directivas de preprocesador de C. Vea [uso de C o C++ en bloques __asm](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md) para obtener más información.  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Uso del lenguaje de ensamblado en bloques __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)