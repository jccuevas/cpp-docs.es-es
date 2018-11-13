---
title: Diagnóstico impreso por la función assert
ms.date: 11/04/2016
ms.assetid: 78b64200-520d-40da-9a61-71553f411d4f
ms.openlocfilehash: 330c694b53957cab2e44da7cb8b52031c33fb5a2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50549050"
---
# <a name="diagnostic-printed-by-the-assert-function"></a>Diagnóstico impreso por la función assert

**ANSI 4.2** El diagnóstico impreso por la función **assert** y su comportamiento de finalización

La función **assert** imprime un mensaje de diagnóstico y llama a la rutina **abort** si la expresión es false (0). El mensaje de diagnóstico tiene la forma

> **Error de aserción**: <em>expression</em>**, archivo** <em>filename</em>**, línea** *linenumber*

donde *filename* es el nombre del archivo de código fuente y *linenumber* es el número de línea de la aserción que produjo un error en el archivo de código fuente. No se realiza ninguna acción si la *expresión* es true (distinto de cero).

## <a name="see-also"></a>Vea también

[Funciones de la biblioteca](../c-language/library-functions.md)