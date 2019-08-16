---
title: Error PRJ0008 al compilar el proyecto
ms.date: 11/04/2016
f1_keywords:
- PRJ0008
helpviewer_keywords:
- PRJ0008
ms.assetid: 6bf7f17a-d2a8-4826-99c7-d600d846952f
ms.openlocfilehash: 5741b7ef8cb9a7ae53d64874d3531e9271c09e0f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62359493"
---
# <a name="project-build-error-prj0008"></a>Error PRJ0008 al compilar el proyecto

No se pudo eliminar el archivo 'archivo'.

**Asegúrese de que el archivo no está abierto por otro proceso y no está protegido contra escritura.**

Durante una regeneración o limpiar, Visual C++ elimina todos los archivos conocidos de intermedios y de salida de la compilación, así como los archivos que cumplan las especificaciones del comodín en el **extensiones para eliminar al limpiar** propiedad en el [General Página de propiedades de opciones de configuración](../../build/reference/general-property-page-project.md).

Verá este error si no puede eliminar un archivo de Visual C++. Para resolver el error, asegúrese del archivo y su directorio de escritura para el usuario que se va a generar.