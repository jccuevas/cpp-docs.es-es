---
title: Error PRJ0009 al compilar el proyecto
ms.date: 11/04/2016
f1_keywords:
- PRJ0009
helpviewer_keywords:
- PRJ0009
ms.assetid: 89291778-cda4-495d-983f-ddcc06dfc98b
ms.openlocfilehash: d02325504b04a13cd15dee0bd70891bf5a63b62e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80192970"
---
# <a name="project-build-error-prj0009"></a>Error PRJ0009 al compilar el proyecto

No se pudo abrir el registro de compilación para escribir en él.

**Asegúrese de que el archivo no está abierto por otro proceso y no está protegido contra escritura.**

Después de establecer la propiedad de **registro de compilación** en **sí** y realizar una compilación o C++ recompilación, visual no pudo abrir el registro de compilación en modo exclusivo.

Revise la configuración de registro de la **compilación** abriendo el cuadro de diálogo **Opciones** (en el menú **herramientas** , haga clic en el comando **Opciones** ) y, a continuación, seleccione **compilación de VC + +** en la carpeta **proyectos** . El archivo de compilación se denomina BuildLog. htm y se escribe en el directorio intermedio $ (IntDir).

Causas posibles de este error:

- Está ejecutando dos procesos de Visual C++ y intentando compilar la misma configuración del mismo proyecto simultáneamente.

- El archivo de registro de compilación se abre en un proceso que bloquea el archivo.

- El usuario no tiene permiso para crear un archivo.

- El usuario actual no tiene acceso de escritura al archivo BuildLog. htm.
