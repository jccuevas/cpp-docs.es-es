---
title: Error recuperable A2066 de ML
ms.date: 08/30/2018
ms.custom: error-reference
f1_keywords:
- A2066
helpviewer_keywords:
- A2066
ms.assetid: 58220fdf-fb8f-47fc-a36d-737867361185
ms.openlocfilehash: 8dc3000b2edc2b1ecda7cc3952b554296de19aa3
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "74855884"
---
# <a name="ml-nonfatal-error-a2066"></a>Error recuperable A2066 de ML

**modo de CPU no compatible y tamaño de segmento**

Se intentó abrir un segmento con un atributo **USE16**, **USE32**o **Flat** que no era compatible con la CPU especificada, o para cambiar a una CPU de 16 bits mientras estaba en un segmento de 32 bits.

Los atributos **planos** y **USE32** deben ir precedidos de la directiva de procesador. 386 o superior.

## <a name="see-also"></a>Vea también

[Mensajes de error de ML](../../assembler/masm/ml-error-messages.md)<br/>