---
title: .CODE
ms.date: 08/30/2018
f1_keywords:
- .CODE
helpviewer_keywords:
- .CODE directive
ms.assetid: 2b8c882c-c0d2-4fa3-8335-e6b12717a4f4
ms.openlocfilehash: a5b6608ca71a2b406c54a06cd44ac2865211a8ac
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/22/2019
ms.locfileid: "74398576"
---
# <a name="code"></a>.CODE

Cuando se utiliza con [. MODELO](../../assembler/masm/dot-model.md), indica el inicio de un segmento de código.

## <a name="syntax"></a>Sintaxis

> **. CÓDIGO** ⟦*nombre*⟧

### <a name="parameters"></a>Parámetros

*nombre*\
Parámetro opcional que especifica el nombre del segmento de código. El nombre predeterminado es **_TEXT** para los [modelos](../../assembler/masm/dot-model.md)minúsculo, pequeño, compacto y plano. El nombre predeterminado es *modulename*_TEXT para otros modelos.

## <a name="see-also"></a>Vea también

[Referencia de directivas](../../assembler/masm/directives-reference.md)\
[.DATA](../../assembler/masm/dot-data.md)
