---
title: Error irrecuperable A1007 de ML
ms.date: 12/17/2019
ms.custom: error-reference
f1_keywords:
- A1007
helpviewer_keywords:
- A1007
ms.assetid: bcf9c826-beb3-4e93-91fe-1ffd34995fbf
ms.openlocfilehash: c9527769e0d9397de90f49cbce98b2cca42bed50
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "75317128"
---
# <a name="ml-fatal-error-a1007"></a>Error irrecuperable A1007 de ML

**nivel de anidamiento demasiado profundo**

El ensamblador ha alcanzado su límite de anidamiento. El límite es de 20 niveles excepto cuando se indica lo contrario.

Uno de los siguientes elementos estaba anidado demasiado profundamente:

- Una directiva de alto nivel como [. Si](dot-if.md)es, [. Repita el procedimiento](dot-repeat.md)o [. WHILE](dot-while.md).

- Definición de estructura.

- Una directiva de ensamblado condicional.

- Definición de procedimiento.

- Una directiva [PUSHCONTEXT](pushcontext.md) (el límite es 10).

- Definición de segmento.

- Un archivo de inclusión.

- Una macro.

## <a name="see-also"></a>Vea también

[Mensajes de error de ML](ml-error-messages.md)
