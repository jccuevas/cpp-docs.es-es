---
title: Compilar proyectos externos | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- external projects
- Visual C++ projects, external projects
- builds [C++], external projects
- projects [C++], external projects
- Makefile projects, external projects
ms.assetid: 650b7803-ea91-489d-bee3-8f3e990e223c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 97b6aa1e5939afe55644df6529bf75ba043f20bb
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "33330351"
---
# <a name="building-external-projects"></a>Compilar proyectos externos
Un proyecto externo es un proyecto de Visual C++ que usa un archivo Make u otros servicios que se encuentran fuera (que son externos) del entorno de desarrollo de Visual C++.  
  
 Si tiene un proyecto externo (por ejemplo, un proyecto de archivo Make) que quiera compilar en el entorno de desarrollo de Visual C++, cree un proyecto de archivos Make y especifique el comando de compilación y la salida del proyecto en el Asistente para aplicaciones de archivos Make. Para obtener más información, vea [Crear un proyecto de archivos Make](../ide/creating-a-makefile-project.md).  
  
 Tenga en cuenta que Visual C++ ya no admite la capacidad de exportar un archivo Make para el proyecto activo desde el entorno de desarrollo. Use [Modificadores de línea de comandos para Devenv](/visualstudio/ide/reference/devenv-command-line-switches) para compilar los proyectos de Visual Studio desde la línea de comandos.  
  
## <a name="see-also"></a>Vea también  
 [Compilar proyectos de C++ en Visual Studio](../ide/building-cpp-projects-in-visual-studio.md)