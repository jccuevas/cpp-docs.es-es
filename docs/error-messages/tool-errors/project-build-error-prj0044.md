---
title: Error PRJ0044 al compilar el proyecto
ms.date: 11/04/2016
f1_keywords:
- PRJ0044
helpviewer_keywords:
- PRJ0044
ms.assetid: 5d78c45a-f9e9-4d2b-a3b6-5a5d1421ab84
ms.openlocfilehash: 48b6a6beb7391901e8c824a0f8ad2bc175de11bc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50614944"
---
# <a name="project-build-error-prj0044"></a>Error PRJ0044 al compilar el proyecto

La propiedad 'Dependencias adicionales' para la regla de compilación personalizada 'rule' asignada al archivo 'archivo' no es válida. La propiedad contenía una cadena 'string' que se evalúa en 'value'.

El **dependencias adicionales** propiedad evaluado como una cadena vacía, o en una cadena que contiene caracteres no válidos (es decir, cualquier carácter que no pueden estar en un nombre de archivo o directorio). Las reglas de compilación personalizadas necesitan la salida de la acción de compilación.

Para obtener más información, consulte [Specifying Custom Build Tools](../../ide/specifying-custom-build-tools.md).

## <a name="see-also"></a>Vea también

[Errores y advertencias de compilación del proyecto (PRJxxxx)](../../error-messages/tool-errors/project-build-errors-and-warnings-prjxxxx.md)