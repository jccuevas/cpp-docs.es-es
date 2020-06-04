---
title: EXTERN (MASM)
ms.date: 12/06/2019
helpviewer_keywords:
- EXTERN directive
ms.assetid: 667d703d-3aaf-4139-a586-29bc5dab1aff
ms.openlocfilehash: 2674f358fe22f74c5272d90a0d8cbff234ddcd11
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440886"
---
# <a name="extern"></a>EXTERN

Define una o varias variables, etiquetas o símbolos externos denominados *nombre* cuyo tipo es *Type*.

## <a name="syntax"></a>Sintaxis

> **Extern** ⟦*Language-Type*⟧ *Name* ⟦ __(__ *altid* __)__ ⟧ __:__ *Type* ⟦ __,__ ⟦*Language-Type*⟧ *Name* ⟦ __(__ *altid* __)__ ⟧ __:__ *Type* ... ⟧

## <a name="remarks"></a>Observaciones

El argumento *de tipo de lenguaje* solo es válido en MASM de 32 bits.

El *tipo* puede ser [ABS](operator-abs.md), que importa *el nombre* como una constante. Igual que [EXTRN](extrn.md).

## <a name="see-also"></a>Consulte también

[Referencia de directivas](directives-reference.md)\
[Gramática BNF de MASM](masm-bnf-grammar.md)
