---
title: Error PRJ0024 al compilar el proyecto
ms.date: 08/27/2018
f1_keywords:
- PRJ0024
helpviewer_keywords:
- PRJ0024
ms.assetid: 8bde6368-6c1b-4e04-bc5e-3c6d0b8fa1d7
ms.openlocfilehash: 645b898bdffcc6d7b397c25eb3c41cea25cb361f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50589649"
---
# <a name="project-build-error-prj0024"></a>Error PRJ0024 al compilar el proyecto

> Ruta de acceso de Unicode '*ruta*' no se puede traducir a la página de códigos ANSI del usuario.

*ruta de acceso* es la versión Unicode original de la cadena de ruta de acceso. Este error puede producirse en los casos donde hay una ruta de acceso Unicode que no se puede traducir directamente a ANSI para la página de códigos del sistema actual.

Este error puede producirse si está trabajando con un proyecto que se desarrolló en un sistema con una página de códigos que no se encuentra en su equipo.

La resolución de este error consiste en actualizar la ruta de acceso para utilizar texto ANSI o para instalar la página de códigos en el equipo y establecerla como la predeterminada del sistema.