---
title: Error PRJ0034 al compilar el proyecto
ms.date: 11/04/2016
f1_keywords:
- PRJ0034
helpviewer_keywords:
- PRJ0034
ms.assetid: 1da4a55b-231b-4476-8545-6997628fbc00
ms.openlocfilehash: 7c078a3d2aef24df9151cb10f81c1b7423809e68
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50549063"
---
# <a name="project-build-error-prj0034"></a>Error PRJ0034 al compilar el proyecto

La propiedad 'Dependencias adicionales' personalizada del nivel de proyecto de compilación paso contenido 'macro' que se evalúa como 'expansión_de_macro'.

Un paso de compilación personalizada en un proyecto contenía un error en su dependencia adicional, probablemente debido a un problema de evaluación de macro. Este error también puede significar que la ruta de acceso es incorrecto, que contiene caracteres o combinaciones de caracteres que no son válidos en una ruta de acceso de archivo.

Para resolver este error, corrija la macro o corrija la especificación de ruta de acceso. La ruta de acceso evaluada es una ruta de acceso absoluta del directorio de proyecto.