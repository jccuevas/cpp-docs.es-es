---
title: .CODE
ms.date: 12/06/2019
f1_keywords:
- .CODE
helpviewer_keywords:
- .CODE directive
ms.assetid: 2b8c882c-c0d2-4fa3-8335-e6b12717a4f4
ms.openlocfilehash: 36d9c01d2a24b446ddc91fe73f3cb677067b3e4c
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2019
ms.locfileid: "74987920"
---
# <a name="code-32-bit-masm"></a>. CÓDIGO (MASM de 32 bits)

Cuando se utiliza con [. MODELO](../../assembler/masm/dot-model.md), indica el inicio de un segmento de código.

## <a name="syntax"></a>Sintaxis

> **. CÓDIGO** ⟦*nombre*⟧

### <a name="parameters"></a>Parameters

*nombre*\
Parámetro opcional que especifica el nombre del segmento de código. El nombre predeterminado es **_TEXT** para los [modelos](../../assembler/masm/dot-model.md)minúsculo, pequeño, compacto y plano. El nombre predeterminado es *modulename*_TEXT para otros modelos.

## <a name="see-also"></a>Vea también

[Referencia de directivas](../../assembler/masm/directives-reference.md)\
[.DATA](../../assembler/masm/dot-data.md)
