---
title: Error recuperable A2219 de ML
ms.date: 08/30/2018
ms.topic: error-reference
f1_keywords:
- A2219
helpviewer_keywords:
- A2219
ms.assetid: 5ebc2f40-e47e-4f8e-b7b9-960b9cfc9f6d
ms.openlocfilehash: 61fa6bc6d630f1e8a8ac84492b60690c9545fb3e
ms.sourcegitcommit: 79e985d3c6e8ccaf94f6e641972887cae8c6eeb0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/24/2019
ms.locfileid: "66197678"
---
# <a name="ml-nonfatal-error-a2219"></a>Error recuperable A2219 de ML

> Alineación incorrecta de desplazamiento en el código de desenredado

## <a name="remarks"></a>Comentarios

El operando para [ &period;ALLOCSTACK](../../assembler/masm/dot-allocstack.md) y [ &period;SAVEREG](../../assembler/masm/dot-savereg.md) debe ser un múltiplo de 8.  El operando para [ &period;SAVEXMM128](../../assembler/masm/dot-savexmm128.md) y [ &period;SETFRAME](../../assembler/masm/dot-setframe.md) debe ser un múltiplo de 16.

## <a name="see-also"></a>Vea también

[Mensajes de error de ML](../../assembler/masm/ml-error-messages.md)
