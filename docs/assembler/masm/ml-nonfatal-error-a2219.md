---
title: Error recuperable A2219 de ML
ms.date: 12/17/2019
ms.custom: error-reference
f1_keywords:
- A2219
helpviewer_keywords:
- A2219
ms.assetid: 5ebc2f40-e47e-4f8e-b7b9-960b9cfc9f6d
ms.openlocfilehash: 611be49a1d4018eeb4edd9ee750d5a0614a83abe
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "75311954"
---
# <a name="ml-nonfatal-error-a2219"></a>Error recuperable A2219 de ML

> Alineación incorrecta para el desplazamiento en el código de desenredado

## <a name="remarks"></a>Notas

El operando para [&period;ALLOCSTACK](dot-allocstack.md) y [&period;SAVEREG](dot-savereg.md) debe ser un múltiplo de 8.  El operando para [&period;SAVEXMM128](dot-savexmm128.md) y [&period;SETFRAME](dot-setframe.md) debe ser un múltiplo de 16.

## <a name="see-also"></a>Vea también

[Mensajes de error de ML](ml-error-messages.md)
