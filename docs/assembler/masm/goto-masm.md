---
title: GOTO (MASM)
ms.date: 12/16/2019
helpviewer_keywords:
- GOTO directive
ms.assetid: 6a5f73e7-6784-4eae-ac52-4fc77a7f369f
ms.openlocfilehash: 18f286d8634202b57dea788aa6984755a5afb197
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440793"
---
# <a name="goto"></a>GOTO

Transfiere el ensamblado a la línea marcada **:** _macrolabel_.

## <a name="syntax"></a>Sintaxis

> **Goto** *macrolabel*

## <a name="remarks"></a>Observaciones

**Goto** solo se permite dentro de [macros](macro.md), [para](for-masm.md)los bloques, [FORC](forc.md), [REPEAT](repeat.md)y [While](while-masm.md) . El destino *macrolabel* debe ser la única directiva en la línea y debe ir precedido por un signo de dos puntos iniciales.

## <a name="see-also"></a>Consulte también

[Referencia de directivas](directives-reference.md)\
[Gramática BNF de MASM](masm-bnf-grammar.md)
