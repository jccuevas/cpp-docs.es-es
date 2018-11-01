---
title: Usar atexit
ms.date: 11/04/2016
f1_keywords:
- atexit
helpviewer_keywords:
- atexit function
ms.assetid: d28fda17-c3d4-4af6-ba44-f44886bbb237
ms.openlocfilehash: 06baba59b5765f853f081b34d73be28a187730ba
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50637455"
---
# <a name="using-atexit"></a>Usar atexit

Con el [atexit](../c-runtime-library/reference/atexit.md) función, puede especificar una función de procesamiento de salida que se ejecuta antes de la finalización del programa. No hay objetos estáticos globales inicializados antes de la llamada a **atexit** se destruyen antes de la ejecución de la función de procesamiento de salida.

## <a name="see-also"></a>Vea también

[Consideraciones de finalización adicionales](../cpp/additional-termination-considerations.md)