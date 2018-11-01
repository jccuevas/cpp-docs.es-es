---
title: Error PRJ0008 al compilar el proyecto
ms.date: 11/04/2016
f1_keywords:
- PRJ0008
helpviewer_keywords:
- PRJ0008
ms.assetid: 6bf7f17a-d2a8-4826-99c7-d600d846952f
ms.openlocfilehash: 696b77e9906b231a680027a3faaf23e53d8fb6e9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50525911"
---
# <a name="project-build-error-prj0008"></a>Error PRJ0008 al compilar el proyecto

No se pudo eliminar el archivo 'archivo'.

**Asegúrese de que el archivo no está abierto por otro proceso y no está protegido contra escritura.**

Durante una regeneración o limpiar, Visual C++ elimina todos los archivos conocidos de intermedios y de salida de la compilación, así como los archivos que cumplan las especificaciones del comodín en el **extensiones para eliminar al limpiar** propiedad en el [General Página de propiedades de opciones de configuración](../../ide/general-property-page-project.md).

Verá este error si no puede eliminar un archivo de Visual C++. Para resolver el error, asegúrese del archivo y su directorio de escritura para el usuario que se va a generar.