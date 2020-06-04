---
title: Error recuperable A2006 de ML
ms.date: 12/17/2019
ms.custom: error-reference
f1_keywords:
- A2006
helpviewer_keywords:
- A2006
ms.assetid: b8a8f096-95df-42b5-85ed-d2530560a84c
ms.openlocfilehash: 058100984acbd42ac2993732ab619c0a27c0edd2
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "75317089"
---
# <a name="ml-nonfatal-error-a2006"></a>Error recuperable A2006 de ML

**símbolo sin definir: identificador**

Se intentó usar un símbolo que no se definió.

Se puede haber producido una de las siguientes acciones:

- No se definió un símbolo.

- Un campo no era miembro de la estructura especificada.

- Se definió un símbolo en un archivo de inclusión que no se incluyó.

- Se usó un símbolo externo sin una directiva [extern](extern-masm.md) o [EXTERNDEF](externdef.md) .

- No se ha escrito correctamente un nombre de símbolo.

- Se hizo referencia A una etiqueta de código local fuera de su ámbito.

## <a name="see-also"></a>Vea también

[Mensajes de error de ML](ml-error-messages.md)
