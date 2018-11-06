---
title: Error PRJ0050 al compilar el proyecto
ms.date: 11/04/2016
f1_keywords:
- PRJ0050
helpviewer_keywords:
- PRJ0050
ms.assetid: ceef3b37-0acf-4abd-ac62-aa830b4fa145
ms.openlocfilehash: ec2490bad70d2b2eb72cbb48771900f09f8c2f67
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50593432"
---
# <a name="project-build-error-prj0050"></a>Error PRJ0050 al compilar el proyecto

No se pudo registrar la salida. Asegúrese de que tener los permisos adecuados para modificar el registro.

El sistema de compilación de Visual C++ no pudo registrar la salida de la compilación (dll o .exe). Debe haber iniciado sesión como administrador para modificar el registro.

Si va a compilar un archivo .dll, puede intentar registrar el archivo .dll manualmente utilizando regsvr32.exe, esto debería mostrar información sobre el motivo del error de la compilación.

Si no se genera un archivo .dll, examine el registro de compilación para el comando que se produce un error.