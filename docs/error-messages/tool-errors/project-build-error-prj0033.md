---
title: Error PRJ0033 al compilar el proyecto
ms.date: 11/04/2016
f1_keywords:
- PRJ0033
helpviewer_keywords:
- PRJ0033
ms.assetid: 84d4a052-0586-4b78-9315-81c1e8386c1e
ms.openlocfilehash: e074ee18508271b56686aa16f9012085ed3bd77d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50586217"
---
# <a name="project-build-error-prj0033"></a>Error PRJ0033 al compilar el proyecto

La propiedad 'Dependencias adicionales' para la compilación personalizada del paso de archivo 'archivo' contenía 'macro' que se evalúa como 'expansión_de_macro'.

Un paso de compilación personalizada en un archivo contenía un error en su dependencia adicional, probablemente debido a un problema de evaluación de macro. Este error también puede significar que la ruta de acceso es incorrecto, que contiene caracteres o combinaciones de caracteres que no son válidos en una ruta de acceso de archivo.

Para resolver este error, corrija la macro o corrija la especificación de ruta de acceso. La ruta de acceso evaluada es una ruta de acceso absoluta del directorio de proyecto.