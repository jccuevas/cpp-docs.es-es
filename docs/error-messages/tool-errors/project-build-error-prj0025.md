---
title: Error PRJ0025 al compilar del proyecto | Microsoft Docs
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0025
dev_langs:
- C++
helpviewer_keywords:
- PRJ0025
ms.assetid: 57725c78-bc63-44f3-9667-2969b2d7c41d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 949e36424fc213459e56332c0802d2719581bac1
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43209817"
---
# <a name="project-build-error-prj0025"></a>Error PRJ0025 al compilar el proyecto

> Archivo por lotes '*archivo*' incluye contenido Unicode que no se puede traducir a la página de códigos ANSI del usuario.
>
> *Contenido UNICODE del archivo*

El sistema de proyectos encontró contenido Unicode en un personalizado regla de generación o evento de compilación que no se puede traducir correctamente a la página de códigos ANSI actual del usuario.

La resolución de este error consiste en actualizar el contenido de la regla de compilación o evento para que utilice ANSI o para instalar la página de códigos en el equipo y establecerla como valor predeterminado del sistema de compilación.

Para obtener más información sobre custom pasos de compilación y los eventos de compilación, consulte [Introducción a los pasos de compilación personalizada y eventos de compilación](../../ide/understanding-custom-build-steps-and-build-events.md).