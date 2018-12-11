---
title: Advertencia de la línea de comandos D9035
ms.date: 12/10/2018
f1_keywords:
- D9035
helpviewer_keywords:
- D9035
ms.assetid: 6254f933-e37a-45ba-b860-1a870d1bc8e8
ms.openlocfilehash: 9c0a159dcf193b4ad016069bafd86c557e9e1281
ms.sourcegitcommit: 6990f842fefc27b522b15cf352f3517b319d78da
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/11/2018
ms.locfileid: "53248525"
---
# <a name="command-line-warning-d9035"></a>Advertencia de la línea de comandos D9035

> opción '*opción*' está desusado y se quitará en una versión futura

## <a name="remarks"></a>Comentarios

Ha especificado una opción del compilador que se quitará en una versión futura del compilador. Si no hay un reemplazo sugerido para *opción*, esta advertencia va seguida de advertencia [D9036](../../error-messages/tool-errors/command-line-warning-d9036.md).

La opción especificada sigue funcionando, pero debe actualizar la configuración de compilación ahora. Como resultado, el proyecto es más probable que seguirán compilándose al actualizar el compilador.

## <a name="see-also"></a>Vea también

[Opciones del compilador en desuso y quitadas](../../build/reference/compiler-options-listed-by-category.md#deprecated-and-removed-compiler-options)<br/>
[Advertencia de la línea de comandos D9036](command-line-warning-d9036.md)