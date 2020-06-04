---
title: Error PRJ0031 al compilar el proyecto
ms.date: 11/04/2016
f1_keywords:
- PRJ0031
helpviewer_keywords:
- PRJ0031
ms.assetid: b42435c6-e570-4f8e-9ad5-12a7ea69ccb2
ms.openlocfilehash: e13236f65aaca778a297cdd2942c07b75dd701d0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80192502"
---
# <a name="project-build-error-prj0031"></a>Error PRJ0031 al compilar el proyecto

La propiedad ' Outputs ' del paso de compilación personalizada para el archivo ' file ' contiene ' macro ' que se evalúa como ' macro_expansion '.

Un paso de compilación personalizado en un archivo tenía una salida errónea probablemente debido a un problema de evaluación de macros. Este error también puede significar que la ruta de acceso tiene un formato incorrecto, que contiene caracteres o combinaciones de caracteres que no son válidos en una ruta de acceso de archivo.

Para resolver este error, corrija la macro o corrija la especificación de la ruta de acceso. La ruta de acceso evaluada es una ruta de acceso absoluta del directorio del proyecto.
