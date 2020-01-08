---
title: .IF
ms.date: 11/05/2019
f1_keywords:
- .IF
helpviewer_keywords:
- .IF directive
ms.assetid: dccc7615-8fc7-4829-9f39-0ee405f6c1e3
ms.openlocfilehash: 6992ec8b151a83b3f9fa920997845c20caf0476d
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "75317752"
---
# <a name="if-32-bit-masm"></a>. IF (MASM de 32 bits)

Genera código que prueba *condition1* (por ejemplo, AX > 7) y ejecuta las *instrucciones* si esa condición es true. (solo para MASM de 32 bits).

## <a name="syntax"></a>Sintaxis

> **. Si** *condition1*\
> *instrucciones*\
> ⟦ **.\ ELSEIF** *condition2*
> *instrucciones*⟧ \
> ⟦ **. ELSE**\
> *instrucciones*⟧ \
> **.ENDIF**

## <a name="remarks"></a>Notas

Si es [. Más adelante,](dot-else.md) sus instrucciones se ejecutan si la condición original fuera falsa. Tenga en cuenta que las condiciones se evalúan en tiempo de ejecución.

## <a name="see-also"></a>Vea también

[Referencia de directivas](directives-reference.md)\
[Gramática BNF de MASM](masm-bnf-grammar.md)
