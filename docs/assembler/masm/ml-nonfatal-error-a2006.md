---
title: Error recuperable A2006 de ML
ms.date: 08/30/2018
ms.topic: error-reference
f1_keywords:
- A2006
helpviewer_keywords:
- A2006
ms.assetid: b8a8f096-95df-42b5-85ed-d2530560a84c
ms.openlocfilehash: 80283bde4dff36e32d276c998f6797b6eeed8160
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50490069"
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