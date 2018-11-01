---
title: Error PRJ0035 al compilar el proyecto
ms.date: 08/27/2018
f1_keywords:
- PRJ0035
helpviewer_keywords:
- PRJ0035
ms.assetid: 0667116d-338c-40a4-972c-da875f778cb5
ms.openlocfilehash: e221fd85f1260ed04d49b43dea3d13407f504847
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50472350"
---
# <a name="project-build-error-prj0035"></a>Error PRJ0035 al compilar el proyecto

> Archivo XML '*archivo*' incluye contenido Unicode que no se puede traducir a la página de códigos ANSI del usuario.
>
> *Contenido UNICODE del archivo*

*archivo* es el archivo XML creado como línea de comandos para la herramienta de implementación Web.

El sistema de proyectos encontró caracteres Unicode en algunas propiedades en la página de propiedades de implementación Web que no se puede traducir correctamente a ANSI.

La resolución de este error consiste en actualizar el contenido de la propiedad para que utilice ANSI o para instalar la página de códigos en el equipo y establecerla como la predeterminada del sistema.