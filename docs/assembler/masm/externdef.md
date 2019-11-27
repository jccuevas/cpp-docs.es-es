---
title: EXTERNDEF
ms.date: 08/30/2018
f1_keywords:
- EXTERNDEF
helpviewer_keywords:
- EXTERNDEF directive
ms.assetid: 95a10de6-c345-4428-a2f2-90f7d411dc86
ms.openlocfilehash: 469b49832c171ee78336a0c457f0d269acd3b59d
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/22/2019
ms.locfileid: "74397538"
---
# <a name="externdef"></a>EXTERNDEF

Define una o varias variables, etiquetas o símbolos externos denominados *nombre* cuyo tipo es *Type*.

## <a name="syntax"></a>Sintaxis

> **EXTERNDEF** ⟦*Language-Type*⟧ *Name* __:__ *Type* ⟦ __,__ ⟦*Language-Type*⟧ *Name* __:__ *Type* ... ⟧

## <a name="remarks"></a>Comentarios

Si *Name* se define en el módulo, se trata como [Public](../../assembler/masm/public-masm.md). Si se hace referencia al *nombre* en el módulo, se trata como [extern](../../assembler/masm/extern-masm.md). Si no se hace referencia al *nombre* , se omite. El *tipo* puede ser [ABS](../../assembler/masm/operator-abs.md), que importa *el nombre* como una constante. Normalmente se usa en archivos de inclusión.

## <a name="see-also"></a>Vea también

[Referencia de directivas](../../assembler/masm/directives-reference.md)
