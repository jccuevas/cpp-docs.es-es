---
title: Compilar proyectos externos | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- external projects
- Visual C++ projects, external projects
- builds [C++], external projects
- projects [C++], external projects
- Makefile projects, external projects
ms.assetid: 650b7803-ea91-489d-bee3-8f3e990e223c
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 16b73349a220f392730dd5526fd5f3d59e59754d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="building-external-projects"></a>Compilar proyectos externos
Un proyecto externo es un proyecto de Visual C++ que utiliza un archivo MAKE u otros servicios que se encuentran fuera (externa o externos) el entorno de desarrollo de Visual C++.  
  
 Si tiene un proyecto externo (por ejemplo, un proyecto de archivos MAKE) que se desea compilar en el entorno de desarrollo de Visual C++, cree un proyecto de archivo MAKE y especificar el proyecto crear comandos y salida en el Asistente para aplicaciones de archivos MAKE. Para obtener más información, consulte [crear un proyecto de archivos MAKE](../ide/creating-a-makefile-project.md).  
  
 Tenga en cuenta que Visual C++ ya no admite la capacidad de exportar un archivo MAKE para el proyecto activo desde el entorno de desarrollo. Use [Devenv Command Line Switches](/visualstudio/ide/reference/devenv-command-line-switches) para generar proyectos de Visual Studio desde la línea de comandos.  
  
## <a name="see-also"></a>Vea también  
 [Compilar proyectos de C++ en Visual Studio](../ide/building-cpp-projects-in-visual-studio.md)