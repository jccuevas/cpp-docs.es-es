---
title: Error PRJ0009 al compilar del proyecto | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0009
dev_langs:
- C++
helpviewer_keywords:
- PRJ0009
ms.assetid: 89291778-cda4-495d-983f-ddcc06dfc98b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: efeb110823e801dd86a503a7069c4898f400769e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46057189"
---
# <a name="project-build-error-prj0009"></a>Error PRJ0009 al compilar el proyecto

Crear registro no se pudo abrir para escritura.

**Asegúrese de que el archivo no está abierto por otro proceso y no está protegido contra escritura.**

Después de establecer el **registro de generación** propiedad **Sí** y realizar una compilación o recompilación, Visual C++ no pudo abrir el registro de compilación en modo exclusivo.

Inspeccionar el **registro de generación** establecer abriendo el **opciones** cuadro de diálogo (en el **herramientas** menú, haga clic en **opciones** comando) y, a continuación, seleccionar **generación de VC ++** en el **proyectos** carpeta. El archivo de compilación se denomina BuildLog.htm y se escribe en el directorio intermedio $(IntDir).

Posibles razones para este error:

- Son dos procesos de Visual C++ en ejecución e intenta realizar la compilación de la misma configuración del mismo proyecto en ambas al mismo tiempo.

- Se abre el archivo de registro de compilación en un proceso que bloquea el archivo.

- El usuario no tiene permiso para crear un archivo.

- El usuario actual no tiene acceso de escritura al archivo BuildLog.htm.