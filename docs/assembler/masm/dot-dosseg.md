---
title: .DOSSEG
ms.date: 11/05/2019
f1_keywords:
- .DOSSEG
helpviewer_keywords:
- .DOSSEG directive
ms.assetid: 175ad470-0a2b-4e2b-b078-65e224fec040
ms.openlocfilehash: e27b0ae185542c11ee29119575d5c8225501f71e
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "75313852"
---
# <a name="dosseg-32-bit-masm"></a>. DOSSEG ((MASM de 32 bits)

Ordena los segmentos según la Convención de segmentos de MS-DOS: CODE First y, a continuación, segmentos que no están en DGROUP y, a continuación, Segments en DGROUP. (solo para MASM de 32 bits).

## <a name="syntax"></a>Sintaxis

> **.DOSSEG**

## <a name="remarks"></a>Notas

Los segmentos de DGROUP siguen este orden: los segmentos no están en el BSS o la pila, los segmentos de BSS y, por último, los segmentos de pila. Se utiliza principalmente para garantizar la compatibilidad con CodeView en programas independientes de MASM. Igual que [dosseg (](dosseg.md).

## <a name="see-also"></a>Vea también

[Referencia de directivas](directives-reference.md)\
[Gramática BNF de MASM](masm-bnf-grammar.md)
