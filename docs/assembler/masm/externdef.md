---
title: EXTERNDEF
ms.date: 12/06/2019
f1_keywords:
- EXTERNDEF
helpviewer_keywords:
- EXTERNDEF directive
ms.assetid: 95a10de6-c345-4428-a2f2-90f7d411dc86
ms.openlocfilehash: e757781151bd1bb57940e5c54f7333a5daa93c74
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2019
ms.locfileid: "74987897"
---
# <a name="externdef"></a>EXTERNDEF

Define una o varias variables, etiquetas o símbolos externos denominados *nombre* cuyo tipo es *Type*.

## <a name="syntax"></a>Sintaxis

> **EXTERNDEF** ⟦*Language-Type*⟧ *Name* __:__ *Type* ⟦ __,__ ⟦*Language-Type*⟧ *Name* __:__ *Type* ... ⟧

## <a name="remarks"></a>Notas

El argumento *de tipo de lenguaje* solo es válido en MASM de 32 bits.

Si *Name* se define en el módulo, se trata como [Public](../../assembler/masm/public-masm.md). Si se hace referencia al *nombre* en el módulo, se trata como [extern](../../assembler/masm/extern-masm.md). Si no se hace referencia al *nombre* , se omite. El *tipo* puede ser [ABS](../../assembler/masm/operator-abs.md), que importa *el nombre* como una constante. Normalmente se usa en archivos de inclusión.

## <a name="see-also"></a>Vea también

[Referencia de directivas](../../assembler/masm/directives-reference.md)
