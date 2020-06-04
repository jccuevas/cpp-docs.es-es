---
title: EXTERNDEF
ms.date: 12/06/2019
f1_keywords:
- EXTERNDEF
helpviewer_keywords:
- EXTERNDEF directive
ms.assetid: 95a10de6-c345-4428-a2f2-90f7d411dc86
ms.openlocfilehash: 2cc5884a7473da9175a6b6af4b4251314deffeb4
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "75313397"
---
# <a name="externdef"></a>EXTERNDEF

Define una o varias variables, etiquetas o símbolos externos denominados *nombre* cuyo tipo es *Type*.

## <a name="syntax"></a>Sintaxis

> **EXTERNDEF** ⟦*Language-Type*⟧ *Name* __:__ *Type* ⟦ __,__ ⟦*Language-Type*⟧ *Name* __:__ *Type* ... ⟧

## <a name="remarks"></a>Notas

El argumento *de tipo de lenguaje* solo es válido en MASM de 32 bits.

Si *Name* se define en el módulo, se trata como [Public](public-masm.md). Si se hace referencia al *nombre* en el módulo, se trata como [extern](extern-masm.md). Si no se hace referencia al *nombre* , se omite. El *tipo* puede ser [ABS](operator-abs.md), que importa *el nombre* como una constante. Normalmente se usa en archivos de inclusión.

## <a name="see-also"></a>Vea también

[Referencia de directivas](directives-reference.md)\
[Gramática BNF de MASM](masm-bnf-grammar.md)
