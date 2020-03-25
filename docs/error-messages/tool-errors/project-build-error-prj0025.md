---
title: Error PRJ0025 al compilar el proyecto
ms.date: 08/27/2018
f1_keywords:
- PRJ0025
helpviewer_keywords:
- PRJ0025
ms.assetid: 57725c78-bc63-44f3-9667-2969b2d7c41d
ms.openlocfilehash: 30445a3abc2a6ad05c983448f57ed5b93df6e61f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80192359"
---
# <a name="project-build-error-prj0025"></a>Error PRJ0025 al compilar el proyecto

> El archivo por lotes '*archivo*' contiene contenido Unicode que no se puede traducir a la página de códigos ANSI del usuario.
>
> *Contenido Unicode del archivo*

El sistema del proyecto encontró contenido Unicode en una regla de compilación personalizada o un evento de compilación que no se puede traducir correctamente a la página de códigos ANSI actual del usuario.

La solución para este error es actualizar el contenido de la regla de compilación o el evento de compilación para usar ANSI o instalar la página de códigos en el equipo y establecerla como el valor predeterminado del sistema.

Para obtener más información sobre los pasos de compilación personalizada y los eventos de compilación, vea Descripción de los pasos de compilación [personalizada y eventos de compilación](../../build/understanding-custom-build-steps-and-build-events.md).
