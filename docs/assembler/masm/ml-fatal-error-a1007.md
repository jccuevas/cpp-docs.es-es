---
title: Error irrecuperable A1007 de ML
ms.date: 08/30/2018
ms.custom: error-reference
f1_keywords:
- A1007
helpviewer_keywords:
- A1007
ms.assetid: bcf9c826-beb3-4e93-91fe-1ffd34995fbf
ms.openlocfilehash: 01633b4fa084b7d5e14af5a5c6e51e3dca684d2a
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "74856922"
---
# <a name="ml-fatal-error-a1007"></a>Error irrecuperable A1007 de ML

**nivel de anidamiento demasiado profundo**

El ensamblador ha alcanzado su límite de anidamiento. El límite es de 20 niveles excepto cuando se indica lo contrario.

Uno de los siguientes elementos estaba anidado demasiado profundamente:

- Una directiva de alto nivel como [. Si](../../assembler/masm/dot-if.md)es, [. Repita el procedimiento](../../assembler/masm/dot-repeat.md)o [. WHILE](../../assembler/masm/dot-while.md).

- Definición de estructura.

- Una directiva de ensamblado condicional.

- Definición de procedimiento.

- Una directiva [PUSHCONTEXT](../../assembler/masm/pushcontext.md) (el límite es 10).

- Definición de segmento.

- Un archivo de inclusión.

- Una macro.

## <a name="see-also"></a>Vea también

[Mensajes de error de ML](../../assembler/masm/ml-error-messages.md)<br/>