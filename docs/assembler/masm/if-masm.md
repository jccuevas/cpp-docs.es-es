---
title: IF (MASM)
ms.date: 12/17/2019
helpviewer_keywords:
- IF directive
ms.assetid: 82e43712-4f0c-4bf6-90ce-0663e81af707
ms.openlocfilehash: 6e63f5c8075b3c94370ad8863d224c097cf0ecdf
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440749"
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

## <a name="remarks"></a>Observaciones

Las siguientes directivas se pueden sustituir por [ELSEIF](elseif-masm.md): **ELSEIFB**, **elseifdef (** , **ELSEIFDIF**, **ELSEIFDIFI**, **ELSEIFE**, **ELSEIFIDN**, **ELSEIFIDNI**, **ELSEIFNB**y **elseifndef (** . Opcionalmente, ensambla las *instrucciones else* si la expresión anterior es falsa. Tenga en cuenta que las expresiones se evalúan en el momento del ensamblado.

## <a name="see-also"></a>Consulte también

[Referencia de directivas](directives-reference.md)\
[Gramática BNF de MASM](masm-bnf-grammar.md)
