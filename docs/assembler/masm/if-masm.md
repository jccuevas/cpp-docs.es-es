---
title: IF (MASM)
ms.date: 08/30/2018
f1_keywords:
- if
helpviewer_keywords:
- IF directive
ms.assetid: 82e43712-4f0c-4bf6-90ce-0663e81af707
ms.openlocfilehash: ed7b9e63bb19dcc16539dbdaaf1f6a7f16566b3c
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/22/2019
ms.locfileid: "74397465"
---
# <a name="if-masm"></a>IF (MASM)

Concede el ensamblado de *ifstatements* si *expression1* es true (distinto de cero) o *elseifstatements* si *expression1* es false (0) y *expression2* es true.

## <a name="syntax"></a>Sintaxis

> **Si** *expression1*\
> *If-statements*\
> ⟦**ELSEIF** *expresión2*\
> *elseif-statements*⟧ \
> ⟦**ELSE**\
> *else-statements*⟧ \
> **ENDIF**

## <a name="remarks"></a>Comentarios

Las siguientes directivas se pueden sustituir por [ELSEIF](../../assembler/masm/elseif-masm.md): **ELSEIFB**, **elseifdef (** , **ELSEIFDIF**, **ELSEIFDIFI**, **ELSEIFE**, **ELSEIFIDN**, **ELSEIFIDNI**, **ELSEIFNB**y **elseifndef (** . Opcionalmente, ensambla las *instrucciones else* si la expresión anterior es falsa. Tenga en cuenta que las expresiones se evalúan en el momento del ensamblado.

## <a name="see-also"></a>Vea también

[Referencia de directivas](directives-reference.md)
