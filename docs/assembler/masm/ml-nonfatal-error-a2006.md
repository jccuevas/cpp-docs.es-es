---
title: Error recuperable A2006 de ML
ms.date: 08/30/2018
ms.custom: error-reference
f1_keywords:
- A2006
helpviewer_keywords:
- A2006
ms.assetid: b8a8f096-95df-42b5-85ed-d2530560a84c
ms.openlocfilehash: 6c55cb66d6eaeaf620aeedc1dd924f6618cbf817
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "74856788"
---
# <a name="ml-nonfatal-error-a2006"></a>Error recuperable A2006 de ML

**símbolo sin definir: identificador**

Se intentó usar un símbolo que no se definió.

Se puede haber producido una de las siguientes acciones:

- No se definió un símbolo.

- Un campo no era miembro de la estructura especificada.

- Se definió un símbolo en un archivo de inclusión que no se incluyó.

- Se usó un símbolo externo sin una directiva [extern](../../assembler/masm/extern-masm.md) o [EXTERNDEF](../../assembler/masm/externdef.md) .

- No se ha escrito correctamente un nombre de símbolo.

- Se hizo referencia A una etiqueta de código local fuera de su ámbito.

## <a name="see-also"></a>Vea también

[Mensajes de error de ML](../../assembler/masm/ml-error-messages.md)<br/>