---
title: abort (Función)
ms.date: 12/01/2017
helpviewer_keywords:
- abort function
ms.assetid: 3352bcc4-1a8a-4e1f-8dcc-fe30f6b50f2d
ms.openlocfilehash: 7c87cb4fe7349a0d623c765c20e7e213a8454571
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50451238"
---
# <a name="abort-function"></a>abort (Función)

El **anular** función, también se declaran en el archivo de inclusión estándar \<stdlib.h >, finaliza un programa de C++. La diferencia entre `exit` y **anular** es que `exit` permite el procesamiento de terminación de tiempo de ejecución de C++ que tenga lugar (objeto global se llamará a los destructores), mientras que **anular** finaliza el programa inmediatamente. Para obtener más información, consulte [anular](../c-runtime-library/reference/abort.md) en el *referencia de la biblioteca de tiempo de ejecución*.

## <a name="see-also"></a>Vea también

[Finalización del programa](../cpp/program-termination.md)