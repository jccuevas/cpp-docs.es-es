---
title: Error PRJ0032 al compilar el proyecto
ms.date: 11/04/2016
f1_keywords:
- PRJ0032
helpviewer_keywords:
- PRJ0032
ms.assetid: bc6acbea-4041-4237-8b5a-f0434705d89f
ms.openlocfilehash: 62efa0e72c6fbe4bd38983ff0507923392427c04
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80192489"
---
# <a name="project-build-error-prj0032"></a>Error PRJ0032 al compilar el proyecto

La propiedad ' Outputs ' del paso de compilación personalizada del nivel de proyecto contenía ' macro ' que se evalúa como ' macro_expansion '.

Un paso de compilación personalizado en un proyecto tenía una salida errónea probablemente debido a un problema de evaluación de macro. Este error también puede significar que la ruta de acceso tiene un formato incorrecto, que contiene caracteres o combinaciones de caracteres que no son válidos en una ruta de acceso de archivo.

Para resolver este error, corrija la macro o corrija la especificación de la ruta de acceso. La ruta de acceso evaluada es una ruta de acceso absoluta del directorio del proyecto.
