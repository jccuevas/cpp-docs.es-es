---
title: .REPEAT
ms.date: 11/05/2019
f1_keywords:
- .REPEAT
helpviewer_keywords:
- .REPEAT directive
ms.assetid: cb8ad8c6-587b-42f9-a0ad-b5316a24918c
ms.openlocfilehash: 2a447cb13fa78b0f2ad3cf61e2d0ff77a5b8cfd9
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/22/2019
ms.locfileid: "74398005"
---
# <a name="repeat-32-bit-masm"></a>. REPEAT (de 32 bits, MASM)

Genera código que repite la ejecución del bloque de *instrucciones* hasta que la *condición* sea true. [. UNTILCXZ](../../assembler/masm/dot-untilcxz.md), que se convierte en true cuando CX es cero, se puede sustituir por [. HASTA](../../assembler/masm/dot-until.md). La *condición* es opcional con **. UNTILCXZ**. (solo para MASM de 32 bits).

## <a name="syntax"></a>Sintaxis

> **. REPETIR**\
> *instrucciones*\
> **.**  *Condición* Until

## <a name="see-also"></a>Vea también

[Referencia de directivas](directives-reference.md)
