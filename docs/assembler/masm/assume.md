---
title: ASSUME
ms.date: 11/05/2019
f1_keywords:
- ASSUME
helpviewer_keywords:
- ASSUME directive
ms.assetid: cd162070-aee9-4c65-babc-005c6cc73d7c
ms.openlocfilehash: a74a5336e626f561f1fc61e866792ce193332d84
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "75316543"
---
# <a name="assume"></a>ASSUME

Habilita la comprobación de errores para los valores de registro. (solo para MASM de 32 bits).

## <a name="syntax"></a>Sintaxis

> **Asuma**  *segregister* __:__ *nombre* ⟦ __,__ *segregister* __:__ *nombre*... ⟧\
> **Supongamos**que se ha*registrado el registro* __:__ *Type* ⟦ __,__ *Register* __:__ *Type*... ⟧\
> **Supongamos**que se ha*registrado* __: error__ ⟦ __,__ *Register* __: error__... ⟧\
> **Asuma** ⟦*Register* __:__ ⟧**Nothing** ⟦ __,__ *Register* __: Nothing__... ⟧

## <a name="remarks"></a>Notas

Después de **que se aplique** un supuesto, el ensamblador inspecciona los cambios en los valores de los registros especificados. El **error** genera un error si se usa el registro. **Nada** quita la comprobación de errores de registro. Puede combinar diferentes tipos de suposiciones en una instrucción.

## <a name="see-also"></a>Vea también

[Referencia de directivas](directives-reference.md)\
[Gramática BNF de MASM](masm-bnf-grammar.md)
