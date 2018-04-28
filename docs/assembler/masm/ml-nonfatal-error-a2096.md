---
title: Error recuperable A2096 de ML | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 6e5d07afa864c9f6f4214de953aa9e03fe0e7e4f
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/28/2018
---
# <a name="ml-nonfatal-error-a2096"></a>Error recuperable A2096 de ML
**segmento, grupo o registro de segmento se esperaba**  
  
 Un segmento o el grupo se esperaba pero no se encontró.  
  
 Se produjo uno de los siguientes:  
  
-   El operando izquierdo especificado con el segmento anulan al operador (**:**) no es un nombre de grupo (CS, DS, SS, ES, FS o GS), registro de segmento, el nombre del segmento o la expresión de segmento.  
  
-   El [ASUMIR](../../assembler/masm/assume.md) directiva se proporcionó un registro de segmento sin una dirección de segmento válido, registro de segmento, grupo o especial **FLAT** grupo.  
  
## <a name="see-also"></a>Vea también  
 [Mensajes de error de ML](../../assembler/masm/ml-error-messages.md)