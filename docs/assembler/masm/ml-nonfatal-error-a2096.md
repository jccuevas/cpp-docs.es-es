---
title: Error recuperable A2096 de ML | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A2096
dev_langs:
- C++
helpviewer_keywords:
- A2096
ms.assetid: bab0b5ee-b39f-4e44-a41a-3f949fab4297
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 82f4ef76dca10b1208a931bc3e1cc09d82a639d2
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2018
ms.locfileid: "43679603"
---
# <a name="ml-nonfatal-error-a2096"></a>Error recuperable A2096 de ML

**se esperaba el registro de segmento, grupo o segmento**

Un segmento o el grupo se esperaba pero no se encontró.

Se produjo alguna de las siguientes acciones:

- El operando izquierdo especificado con el segmento de reemplazar el operador (**:**) no es un nombre de grupo (CS, DS, SS, ES, FS o GS), registro de segmento, el nombre del segmento o la expresión de segmento.

- El [ASSUME](../../assembler/masm/assume.md) directiva se proporcionó un registro de segmento sin una dirección de segmento válido, registro de segmento, grupo o especial **planos** grupo.

## <a name="see-also"></a>Vea también

[Mensajes de error de ML](../../assembler/masm/ml-error-messages.md)<br/>