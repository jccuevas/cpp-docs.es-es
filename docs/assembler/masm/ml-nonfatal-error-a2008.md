---
title: Error recuperable A2008 de ML
ms.date: 12/17/2019
ms.custom: error-reference
f1_keywords:
- A2008
helpviewer_keywords:
- A2008
ms.assetid: ca24157f-c88a-4678-ae06-3bc3cd956001
ms.openlocfilehash: 79448f9358ffd422b8b25a69ac2b83693e58560e
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "75318051"
---
# <a name="ml-nonfatal-error-a2008"></a>Error recuperable A2008 de ML

**error de sintaxis:**

Un token en la ubicación actual provocó un error de sintaxis.

Se puede haber producido una de las siguientes acciones:

- Se agregó o se omitió un prefijo de punto en una directiva.

- Se usó una palabra reservada (como **C** o **tamaño**) como identificador.

- Se usó una instrucción que no estaba disponible con la selección de procesador o coprocesador actual.

- Se utilizó un operador de tiempo de ejecución de comparación (como `==`) en una instrucción de ensamblado condicional en lugar de un operador relacional (como [EQ](operator-eq.md)).

- A una instrucción o Directiva se le proporcionó demasiado pocos operandos.

- Se usó una directiva obsoleta.

## <a name="see-also"></a>Vea también

[Mensajes de error de ML](ml-error-messages.md)
