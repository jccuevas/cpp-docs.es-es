---
title: ASSUME
ms.date: 11/05/2019
f1_keywords:
- ASSUME
helpviewer_keywords:
- ASSUME directive
ms.assetid: cd162070-aee9-4c65-babc-005c6cc73d7c
ms.openlocfilehash: 73ef8bcc33087a56747b80f94482fcd6c50e3bf6
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/22/2019
ms.locfileid: "74399267"
---
# <a name="assume-32-bit-masm"></a>Suponer (MASM de 32 bits)

Habilita la comprobación de errores para los valores de registro. (solo para MASM de 32 bits).

## <a name="syntax"></a>Sintaxis

> **Asuma**  *segregister* __:__ *nombre* ⟦ __,__ *segregister* __:__ *nombre*... ⟧\
> **Supongamos**que se ha*registrado el registro* __:__ *Type* ⟦ __,__ *Register* __:__ *Type*... ⟧\
> **Supongamos**que se ha*registrado* __: error__ ⟦ __,__ *Register* __: error__... ⟧\
> **Asuma** ⟦*Register* __:__ ⟧**Nothing** ⟦ __,__ *Register* __: Nothing__... ⟧

## <a name="remarks"></a>Comentarios

Después de **que se aplique** un supuesto, el ensamblador inspecciona los cambios en los valores de los registros especificados. El **error** genera un error si se usa el registro. **Nada** quita la comprobación de errores de registro. Puede combinar diferentes tipos de suposiciones en una instrucción.

## <a name="see-also"></a>Vea también

[Referencia de directivas](../../assembler/masm/directives-reference.md)
