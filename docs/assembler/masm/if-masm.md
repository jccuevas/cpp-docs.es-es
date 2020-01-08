---
title: IF (MASM)
ms.date: 12/17/2019
f1_keywords:
- if
helpviewer_keywords:
- IF directive
ms.assetid: 82e43712-4f0c-4bf6-90ce-0663e81af707
ms.openlocfilehash: 38d366a3a41e7b08759594899cdcbb2cb84dfbfa
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "75317297"
---
# <a name="if"></a>IF

Concede el ensamblado de *ifstatements* si *expression1* es true (distinto de cero) o *elseifstatements* si *expression1* es false (0) y *expression2* es true.

## <a name="syntax"></a>Sintaxis

> **Si** *expression1*\
> *If-statements*\
> ⟦**ELSEIF** *expresión2*\
> *elseif-statements*⟧ \
> ⟦**ELSE**\
> *else-statements*⟧ \
> **ENDIF**

## <a name="remarks"></a>Notas

Las siguientes directivas se pueden sustituir por [ELSEIF](elseif-masm.md): **ELSEIFB**, **elseifdef (** , **ELSEIFDIF**, **ELSEIFDIFI**, **ELSEIFE**, **ELSEIFIDN**, **ELSEIFIDNI**, **ELSEIFNB**y **elseifndef (** . Opcionalmente, ensambla las *instrucciones else* si la expresión anterior es falsa. Tenga en cuenta que las expresiones se evalúan en el momento del ensamblado.

## <a name="see-also"></a>Vea también

[Referencia de directivas](directives-reference.md)\
[Gramática BNF de MASM](masm-bnf-grammar.md)
