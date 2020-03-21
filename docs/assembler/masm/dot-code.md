---
title: .CODE
ms.date: 12/17/2019
f1_keywords:
- .CODE
helpviewer_keywords:
- .CODE directive
ms.assetid: 2b8c882c-c0d2-4fa3-8335-e6b12717a4f4
ms.openlocfilehash: 7e53befcc46319d0ecf2287ab96a19a73a0b0b85
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "80076276"
---
# <a name="code"></a>.CODE

(solo para MASM de 32 bits). Cuando se utiliza con [. MODELO](dot-model.md), indica el inicio de un segmento de código.

## <a name="syntax"></a>Sintaxis

> **. CÓDIGO** ⟦*nombre*⟧ \
> ⟦ *segmentItem* ⟧... \
> ⟦ *codesegmentnameId* **finaliza**;; ⟧\

### <a name="parameters"></a>Parámetros

*nombre*\
Parámetro opcional que especifica el nombre del segmento de código. El nombre predeterminado es **_TEXT** para los [modelos](dot-model.md)minúsculo, pequeño, compacto y plano. El nombre predeterminado es *modulename*_TEXT para otros modelos.

## <a name="see-also"></a>Consulte también

[Referencia de directivas](directives-reference.md)\
[. ](dot-data.md)\ de datos
[Gramática BNF de MASM](masm-bnf-grammar.md)
