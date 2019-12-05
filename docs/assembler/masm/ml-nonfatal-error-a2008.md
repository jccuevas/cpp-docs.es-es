---
title: Error recuperable A2008 de ML
ms.date: 08/30/2018
ms.custom: error-reference
f1_keywords:
- A2008
helpviewer_keywords:
- A2008
ms.assetid: ca24157f-c88a-4678-ae06-3bc3cd956001
ms.openlocfilehash: 192d82186a58d4e6b534ab5ec65b696d4d7ce3ee
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "74856758"
---
# <a name="ml-nonfatal-error-a2008"></a>Error recuperable A2008 de ML

**error de sintaxis:**

Un token en la ubicación actual provocó un error de sintaxis.

Se puede haber producido una de las siguientes acciones:

- Se agregó o se omitió un prefijo de punto en una directiva.

- Se usó una palabra reservada (como **C** o **tamaño**) como identificador.

- Se usó una instrucción que no estaba disponible con la selección de procesador o coprocesador actual.

- Se utilizó un operador de tiempo de ejecución de comparación (como `==`) en una instrucción de ensamblado condicional en lugar de un operador relacional (como [EQ](../../assembler/masm/operator-eq.md)).

- A una instrucción o Directiva se le proporcionó demasiado pocos operandos.

- Se usó una directiva obsoleta.

## <a name="see-also"></a>Vea también

[Mensajes de error de ML](../../assembler/masm/ml-error-messages.md)<br/>