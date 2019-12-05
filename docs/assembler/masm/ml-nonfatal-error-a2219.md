---
title: Error recuperable A2219 de ML
ms.date: 08/30/2018
ms.custom: error-reference
f1_keywords:
- A2219
helpviewer_keywords:
- A2219
ms.assetid: 5ebc2f40-e47e-4f8e-b7b9-960b9cfc9f6d
ms.openlocfilehash: cf2be5db2aa9c21597c199a6840f4aaa50e0a681
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "74854594"
---
# <a name="ml-nonfatal-error-a2219"></a>Error recuperable A2219 de ML

> Alineación incorrecta para el desplazamiento en el código de desenredado

## <a name="remarks"></a>Notas

El operando para [&period;ALLOCSTACK](../../assembler/masm/dot-allocstack.md) y [&period;SAVEREG](../../assembler/masm/dot-savereg.md) debe ser un múltiplo de 8.  El operando para [&period;SAVEXMM128](../../assembler/masm/dot-savexmm128.md) y [&period;SETFRAME](../../assembler/masm/dot-setframe.md) debe ser un múltiplo de 16.

## <a name="see-also"></a>Vea también

[Mensajes de error de ML](../../assembler/masm/ml-error-messages.md)
