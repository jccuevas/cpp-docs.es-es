---
title: Diagnóstico impreso por la función assert
ms.date: 11/04/2016
ms.assetid: 78b64200-520d-40da-9a61-71553f411d4f
ms.openlocfilehash: 666ba22d642b772fe8ad336f57ab1bdd82bd2e18
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/12/2019
ms.locfileid: "56151005"
---
# <a name="diagnostic-printed-by-the-assert-function"></a>Diagnóstico impreso por la función assert

**ANSI 4.2** El diagnóstico impreso por la función **assert** y su comportamiento de finalización

La función **assert** imprime un mensaje de diagnóstico y llama a la rutina **abort** si la expresión es false (0). El mensaje de diagnóstico tiene la forma

> **Error de aserción**: <em>expression</em>**, archivo** <em>filename</em>**, línea** *linenumber*

donde *filename* es el nombre del archivo de código fuente y *linenumber* es el número de línea de la aserción que produjo un error en el archivo de código fuente. No se realiza ninguna acción si la *expresión* es true (distinto de cero).

## <a name="see-also"></a>Vea también

[Funciones de la biblioteca](../c-language/library-functions.md)
