---
title: Error recuperable A2066 de ML | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A2066
dev_langs:
- C++
helpviewer_keywords:
- A2066
ms.assetid: 58220fdf-fb8f-47fc-a36d-737867361185
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 92cc0daf183f617767ff5ff119c5e95b8f34cd51
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/28/2018
ms.locfileid: "32054268"
---
# <a name="ml-nonfatal-error-a2066"></a>Error recuperable A2066 de ML
**tamaño de modo y el segmento de CPU incompatible**  
  
 Se intentó abrir un segmento con un **USE16**, **USE32**, o **FLAT** atributo que no es compatible con la CPU especificada, o para cambiar a una CPU de 16 bits en 32 bits segmento.  
  
 El **USE32** y **FLAT** atributos deben ir precedidos de la.386 o directiva de procesador mayor.  
  
## <a name="see-also"></a>Vea también  
 [Mensajes de error de ML](../../assembler/masm/ml-error-messages.md)