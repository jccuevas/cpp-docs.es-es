---
title: .REPEAT
ms.date: 11/05/2019
f1_keywords:
- .REPEAT
helpviewer_keywords:
- .REPEAT directive
ms.assetid: cb8ad8c6-587b-42f9-a0ad-b5316a24918c
ms.openlocfilehash: f21f3f3cc4cb86b1ca2503d515dcd7fbcdffe622
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "75318285"
---
# <a name="repeat-32-bit-masm"></a>. REPEAT (de 32 bits, MASM)

Genera código que repite la ejecución del bloque de *instrucciones* hasta que la *condición* sea true. [. UNTILCXZ](dot-untilcxz.md), que se convierte en true cuando CX es cero, se puede sustituir por [. HASTA](dot-until.md). La *condición* es opcional con **. UNTILCXZ**. (solo para MASM de 32 bits).

## <a name="syntax"></a>Sintaxis

> **. REPETIR**\
> *instrucciones*\
> **.**  *Condición* Until

## <a name="see-also"></a>Vea también

[Referencia de directivas](directives-reference.md)\
[Gramática BNF de MASM](masm-bnf-grammar.md)
