---
title: Error PRJ0024 al compilar del proyecto | Microsoft Docs
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0024
dev_langs:
- C++
helpviewer_keywords:
- PRJ0024
ms.assetid: 8bde6368-6c1b-4e04-bc5e-3c6d0b8fa1d7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: eb539a5f1ee5f1aa5f9d828d93fa6d0dc8690c22
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43215603"
---
# <a name="project-build-error-prj0024"></a>Error PRJ0024 al compilar el proyecto

> Ruta de acceso de Unicode '*ruta*' no se puede traducir a la página de códigos ANSI del usuario.

*ruta de acceso* es la versión Unicode original de la cadena de ruta de acceso. Este error puede producirse en los casos donde hay una ruta de acceso Unicode que no se puede traducir directamente a ANSI para la página de códigos del sistema actual.

Este error puede producirse si está trabajando con un proyecto que se desarrolló en un sistema con una página de códigos que no se encuentra en su equipo.

La resolución de este error consiste en actualizar la ruta de acceso para utilizar texto ANSI o para instalar la página de códigos en el equipo y establecerla como la predeterminada del sistema.