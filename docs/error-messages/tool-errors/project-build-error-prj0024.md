---
title: Error PRJ0024 al compilar del proyecto | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: PRJ0024
dev_langs: C++
helpviewer_keywords: PRJ0024
ms.assetid: 8bde6368-6c1b-4e04-bc5e-3c6d0b8fa1d7
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: cfd51c58fa11ae19c014365dbfbc57c6cd7eb687
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="project-build-error-prj0024"></a>Error PRJ0024 al compilar el proyecto
Ruta de acceso de Unicode 'path' no se puede traducir a la página de códigos ANSI del usuario.  
  
 ***ruta de acceso*** es la versión Unicode original de la cadena de ruta de acceso. Este error puede producirse en los casos donde hay una ruta de acceso de Unicode que no se puede convertir directamente a ANSI para la página de códigos del sistema actual.  
  
 Este error puede producirse si está trabajando con un proyecto que se desarrolló en un sistema que utiliza una página de códigos que no está en el equipo.  
  
 La resolución de este error consiste en actualizar la ruta de acceso para utilizar texto ANSI o para instalar la página de códigos en el equipo y establézcalo como el valor predeterminado del sistema.