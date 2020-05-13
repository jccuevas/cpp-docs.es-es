---
title: Error PRJ0008 al compilar el proyecto
ms.date: 11/04/2016
f1_keywords:
- PRJ0008
helpviewer_keywords:
- PRJ0008
ms.assetid: 6bf7f17a-d2a8-4826-99c7-d600d846952f
ms.openlocfilehash: 7d1c11ab7539f25d371c0bfbd2853b6155c9661c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80192964"
---
# <a name="project-build-error-prj0008"></a>Error PRJ0008 al compilar el proyecto

No se pudo eliminar el archivo ' archivo '.

**Asegúrese de que el archivo no está abierto por otro proceso y no está protegido contra escritura.**

Durante una recompilación o limpieza, C++ visual elimina todos los archivos intermedios y de salida conocidos de la compilación, así como cualquier archivo que cumpla las especificaciones de caracteres comodín de la propiedad **extensiones para eliminar al limpiar** en la [Página de propiedades opciones de configuración generales](../../build/reference/general-property-page-project.md).

Verá este error si visual C++ no puede eliminar un archivo. Para resolver el error, haga que el archivo y su directorio sean grabables para el usuario que realiza la compilación.
