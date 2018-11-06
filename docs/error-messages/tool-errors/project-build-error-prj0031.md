---
title: Error PRJ0031 al compilar el proyecto
ms.date: 11/04/2016
f1_keywords:
- PRJ0031
helpviewer_keywords:
- PRJ0031
ms.assetid: b42435c6-e570-4f8e-9ad5-12a7ea69ccb2
ms.openlocfilehash: e5edae0c1b7464e4a3a5e9523332ce956d0dcf92
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50648596"
---
# <a name="project-build-error-prj0031"></a>Error PRJ0031 al compilar el proyecto

La propiedad 'Outputs' de la compilación personalizada del paso de archivo 'archivo' contenía 'macro' que se evalúa como 'expansión_de_macro'.

Un paso de compilación personalizada en un archivo tenía un resultado erróneo debido probablemente a un problema de evaluación de macro. Este error también puede significar que la ruta de acceso es incorrecto, que contiene caracteres o combinaciones de caracteres que no son válidos en una ruta de acceso de archivo.

Para resolver este error, corrija la macro o corrija la especificación de ruta de acceso. La ruta de acceso evaluada es una ruta de acceso absoluta del directorio de proyecto.