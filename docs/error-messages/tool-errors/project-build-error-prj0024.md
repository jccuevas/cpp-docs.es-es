---
title: Error PRJ0024 al compilar el proyecto
ms.date: 08/27/2018
f1_keywords:
- PRJ0024
helpviewer_keywords:
- PRJ0024
ms.assetid: 8bde6368-6c1b-4e04-bc5e-3c6d0b8fa1d7
ms.openlocfilehash: bcfdcce54618acca0e22daa54e95083cf3ee9d50
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80192619"
---
# <a name="project-build-error-prj0024"></a>Error PRJ0024 al compilar el proyecto

> La ruta de acceso Unicode '*path*' no se puede traducir a la página de códigos ANSI del usuario.

*path* es la versión de Unicode original de la cadena de ruta de acceso. Este error puede producirse en casos en los que hay una ruta de acceso Unicode que no se puede traducir directamente a ANSI para la página de códigos del sistema actual.

Este error puede producirse si está trabajando con un proyecto desarrollado en un sistema con una página de códigos que no está en el equipo.

La solución para este error es actualizar la ruta de acceso para usar texto ANSI o instalar la página de códigos en el equipo y establecerla como predeterminada del sistema.
