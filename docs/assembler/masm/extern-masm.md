---
title: EXTERN (MASM)
ms.date: 12/06/2019
f1_keywords:
- extern
helpviewer_keywords:
- EXTERN directive
ms.assetid: 667d703d-3aaf-4139-a586-29bc5dab1aff
ms.openlocfilehash: 38ea50e75f2a8e19a7a99860f691904053b6739a
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2019
ms.locfileid: "74987857"
---
# <a name="extern-masm"></a>EXTERN (MASM)

Define una o varias variables, etiquetas o símbolos externos denominados *nombre* cuyo tipo es *Type*.

## <a name="syntax"></a>Sintaxis

> **Extern** ⟦*Language-Type*⟧ *Name* ⟦ __(__ *altid* __)__ ⟧ __:__ *Type* ⟦ __,__ ⟦*Language-Type*⟧ *Name* ⟦ __(__ *altid* __)__ ⟧ __:__ *Type* ... ⟧

## <a name="remarks"></a>Notas

El argumento *de tipo de lenguaje* solo es válido en MASM de 32 bits.

El *tipo* puede ser [ABS](../../assembler/masm/operator-abs.md), que importa *el nombre* como una constante. Igual que [EXTRN](../../assembler/masm/extrn.md).

## <a name="see-also"></a>Vea también

[Referencia de directivas](../../assembler/masm/directives-reference.md)
