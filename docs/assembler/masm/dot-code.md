---
title: .CODE
ms.date: 12/17/2019
f1_keywords:
- .CODE
helpviewer_keywords:
- .CODE directive
ms.assetid: 2b8c882c-c0d2-4fa3-8335-e6b12717a4f4
ms.openlocfilehash: 0975e96e670400b7fa221ae2d1b9982b5cee613b
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "75314151"
---
# <a name="code"></a>.CODE

(solo para MASM de 32 bits). Cuando se utiliza con [. MODELO](dot-model.md), indica el inicio de un segmento de código.

## <a name="syntax"></a>Sintaxis

> **. CÓDIGO** ⟦*nombre*⟧ \
> ⟦ *segmentItem* ⟧... \
> ⟦ *codesegmentnameId* **finaliza**;; ⟧\

### <a name="parameters"></a>Parameters

*nombre*\
Parámetro opcional que especifica el nombre del segmento de código. El nombre predeterminado es **_TEXT** para los [modelos](dot-model.md)minúsculo, pequeño, compacto y plano. El nombre predeterminado es *modulename*_TEXT para otros modelos.

## <a name="see-also"></a>Vea también

[Referencia de directivas](directives-reference.md)\
[. ](dot-data.md)\ de datos
[Gramática BNF de MASM](masm-bnf-grammar.md)

