---
title: Error recuperable A2008 de ML
ms.date: 08/30/2018
ms.topic: error-reference
f1_keywords:
- A2008
helpviewer_keywords:
- A2008
ms.assetid: ca24157f-c88a-4678-ae06-3bc3cd956001
ms.openlocfilehash: 7f85a3aabb7b1955cede912168dfc04618b8f2b2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50630378"
---
# <a name="ml-nonfatal-error-a2008"></a>Error recuperable A2008 de ML

**error de sintaxis:**

Un token en la ubicación actual produjo un error de sintaxis.

Puede haberse producido uno de los siguientes:

- Se agregó un prefijo de punto o se omite en una directiva.

- Una palabra reservada (como **C** o **tamaño**) se utiliza como identificador.

- Se utilizó una instrucción que no estaba disponible con la selección actual del procesador o coprocesador.

- Un operador de tiempo de ejecución de comparación (como `==`) se usó en una instrucción condicional de ensamblado en lugar de un operador relacional (como [EQ](../../assembler/masm/operator-eq.md)).

- Una instrucción o la directiva se ha especificado demasiado pocos operandos.

- Se usó una directiva obsoleta.

## <a name="see-also"></a>Vea también

[Mensajes de error de ML](../../assembler/masm/ml-error-messages.md)<br/>