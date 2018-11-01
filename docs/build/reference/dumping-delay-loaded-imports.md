---
title: Volcar importaciones de carga retrasada
ms.date: 11/04/2016
helpviewer_keywords:
- delay-loaded imports, dumping
- imports (delay-loaded)
- delay-loaded imports
ms.assetid: f766acf4-9df8-4b85-8cf6-0be3ffc4c124
ms.openlocfilehash: 782da0d29024a8308de0bb4d00656b850629c8ba
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50444166"
---
# <a name="dumping-delay-loaded-imports"></a>Volcar importaciones de carga retrasada

Importaciones de carga retrasada se pueden volcar mediante [dumpbin /imports](../../build/reference/imports-dumpbin.md) y mostrarse con información ligeramente diferente de las importaciones estándar. Que se segregan en su propia sección del volcado /imports y se etiquetan explícitamente como importaciones de carga retrasada. Si no hay que descargar la información presente en la imagen, que se indica. Si no hay información de enlace, se indica la marca de fecha y hora de la DLL de destino junto con las direcciones de enlace de las importaciones.

## <a name="see-also"></a>Vea también

[Compatibilidad del vinculador con las DLL de carga retrasada](../../build/reference/linker-support-for-delay-loaded-dlls.md)