---
title: Error recuperable A2006 de ML | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A2006
dev_langs:
- C++
helpviewer_keywords:
- A2006
ms.assetid: b8a8f096-95df-42b5-85ed-d2530560a84c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f287c6ab46c6af71ba6dc0032f332ce3cc489454
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2018
ms.locfileid: "43677410"
---
# <a name="ml-nonfatal-error-a2006"></a>Error recuperable A2006 de ML

**símbolo no definido: identificador**

Se intentó usar un símbolo que no se definió.

Puede haberse producido uno de los siguientes:

- No se definió un símbolo.

- Un campo no era miembro de la estructura especificada.

- Se definió un símbolo en un archivo de inclusión que no se incluyó.

- Se usó un símbolo externo sin un [EXTERN](../../assembler/masm/extern-masm.md) o [EXTERNDEF](../../assembler/masm/externdef.md) directiva.

- Un nombre de símbolo se escribió correctamente.

- Se hace referencia a una etiqueta de código local fuera de su ámbito.

## <a name="see-also"></a>Vea también

[Mensajes de error de ML](../../assembler/masm/ml-error-messages.md)<br/>