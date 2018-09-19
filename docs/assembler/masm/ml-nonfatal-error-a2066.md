---
title: Error recuperable A2066 de ML | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
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
ms.openlocfilehash: 8cf5cbe7d5c77da7f129cbc40ffa97f4051afca6
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2018
ms.locfileid: "43690257"
---
# <a name="ml-nonfatal-error-a2066"></a>Error recuperable A2066 de ML

**tamaño de segmento y de modo incompatible de CPU**

Se intentó abrir un segmento con un **USE16**, **USE32**, o **planos** atributo que no era compatible con la CPU especificada, o para cambiar a una CPU de 16 bits en 32 bits segmento.

El **USE32** y **planos** atributos deben ir precedidos de la.386 o directiva de procesador superior.

## <a name="see-also"></a>Vea también

[Mensajes de error de ML](../../assembler/masm/ml-error-messages.md)<br/>