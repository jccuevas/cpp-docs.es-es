---
title: Error recuperable A2066 de ML
ms.date: 12/17/2019
ms.custom: error-reference
f1_keywords:
- A2066
helpviewer_keywords:
- A2066
ms.assetid: 58220fdf-fb8f-47fc-a36d-737867361185
ms.openlocfilehash: 4c7c32264fe5daa6cd4e14f47cff111899e8f8d6
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "75316894"
---
# <a name="ml-nonfatal-error-a2066"></a>Error recuperable A2066 de ML

**modo de CPU no compatible y tamaño de segmento**

Se intentó abrir un segmento con un atributo **USE16**, **USE32**o **Flat** que no era compatible con la CPU especificada, o para cambiar a una CPU de 16 bits mientras estaba en un segmento de 32 bits.

Los atributos **planos** y **USE32** deben ir precedidos de la directiva de procesador. 386 o superior.

## <a name="see-also"></a>Vea también

[Mensajes de error de ML](ml-error-messages.md)
