---
title: Error recuperable A2096 de ML
ms.date: 08/30/2018
ms.custom: error-reference
f1_keywords:
- A2096
helpviewer_keywords:
- A2096
ms.assetid: bab0b5ee-b39f-4e44-a41a-3f949fab4297
ms.openlocfilehash: 14fb30214cf7badf51368672dc52635d50a067f1
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "74855479"
---
# <a name="ml-nonfatal-error-a2096"></a>Error recuperable A2096 de ML

**se esperaba un segmento, un grupo o un registro de segmento**

Se esperaba un segmento o un grupo, pero no se encontró.

Se produjo uno de los siguientes pasos:

- El operando izquierdo especificado con el operador de invalidación de segmento ( **:** ) no era un registro de segmento (CS, DS, SS, es, FS o GS), nombre de grupo, nombre de segmento o expresión de segmento.

- La directiva [asuma](../../assembler/masm/assume.md) un registro de segmento sin una dirección de segmento, un registro de segmento, un grupo o un grupo **plano** especial válidos.

## <a name="see-also"></a>Vea también

[Mensajes de error de ML](../../assembler/masm/ml-error-messages.md)<br/>