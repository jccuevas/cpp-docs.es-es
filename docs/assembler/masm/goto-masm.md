---
title: GOTO (MASM)
ms.date: 12/16/2019
f1_keywords:
- goto
helpviewer_keywords:
- GOTO directive
ms.assetid: 6a5f73e7-6784-4eae-ac52-4fc77a7f369f
ms.openlocfilehash: f198658f9a4b85e0b5ec9b7a0c122241e57286f6
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "75317284"
---
# <a name="goto"></a>GOTO

Transfiere el ensamblado a la línea marcada **:** _macrolabel_.

## <a name="syntax"></a>Sintaxis

> **Goto** *macrolabel*

## <a name="remarks"></a>Notas

**Goto** solo se permite dentro de [macros](macro.md), [para](for-masm.md)los bloques, [FORC](forc.md), [REPEAT](repeat.md)y [While](while-masm.md) . El destino *macrolabel* debe ser la única directiva en la línea y debe ir precedido por un signo de dos puntos iniciales.

## <a name="see-also"></a>Vea también

[Referencia de directivas](directives-reference.md)\
[Gramática BNF de MASM](masm-bnf-grammar.md)
