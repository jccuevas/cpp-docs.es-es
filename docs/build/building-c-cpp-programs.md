---
title: Compilar programas de C ++ | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vcbuilding
- buildingaprogramVC
dev_langs:
- C++
helpviewer_keywords:
- builds [C++]
- Visual C++ projects, building
- projects [C++], building
- builds [C++], options
- Visual C++, build options
ms.assetid: fa6ed4ff-334a-4d99-b5e2-a1f83d2b3008
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cc4b8c70c7be83e108104cf91d4629072a9324f4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="building-cc-programs"></a>Compilar programas de C/C++

Los proyectos de Visual C++ se pueden compilar en Visual Studio o en la línea de comandos. El IDE de Visual Studio utiliza [MSBuild](../build/msbuild-visual-cpp.md) para compilar proyectos y soluciones. En la línea de comandos, puede usar el compilador (cl.exe) y el vinculador (link.exe) de C/C++ para compilar proyectos sencillos. Para compilar proyectos más complejos en la línea de comandos, puede usar MSBuild o [NMAKE](../build/nmake-reference.md). Para obtener información general sobre cómo usar [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] para compilar proyectos y soluciones, consulte [compilar y generar](/visualstudio/ide/compiling-and-building-in-visual-studio).  
  
## <a name="in-this-section"></a>En esta sección  

[Compilar proyectos de C++ en Visual Studio](../ide/building-cpp-projects-in-visual-studio.md)  
Se aborda el uso del IDE de Visual Studio para compilar proyectos de C/C++.  
  
[Compilación de código de C o C++ en la línea de comandos](../build/building-on-the-command-line.md)  
Se aborda el uso del compilador de línea de comandos y las herramientas de compilación de C/C++ que se incluyen en Visual Studio.  
  
[Compilación de aplicaciones aisladas y ensamblados simultáneos de C/C++](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)  
Se describe el modelo de implementación de aplicaciones de escritorio de Windows según los conceptos de aplicaciones aisladas y ensamblados en paralelo.  
  
[Referencia de compilación de C/C++](../build/reference/c-cpp-building-reference.md)  
Contiene vínculos a artículos de referencia sobre cómo compilar programas en C++, sobre las opciones de compilador y vinculador, y sobre otras herramientas de compilación.  
  
[Configuración de Visual C++ en destinos de 64 bits, x64](../build/configuring-programs-for-64-bit-visual-cpp.md)  
Se explica cómo configurar Visual Studio y la línea de comandos para usar el conjunto de herramientas de 64 bits y cómo tener como destino arquitecturas de 64 bits. Asimismo, se abordan los problemas de migración más comunes cuando el código se traslada a arquitecturas de 64 bits.  
  
[Configuración de Visual C++ para procesadores ARM](../build/configuring-programs-for-arm-processors-visual-cpp.md)  
Se describen las convenciones que usan los procesadores de ARM y se abordan los problemas de migración más comunes cuando el código se traslada a arquitecturas de ARM.  
  
[Configuración de programas para Windows XP](../build/configuring-programs-for-windows-xp.md)  
Se describe cómo configurar el conjunto de herramientas de la plataforma para tener como destino el desarrollo en Windows XP.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Compilar y generar en Visual Studio](/visualstudio/ide/compiling-and-building-in-visual-studio)  
 Describe las herramientas y el sistema de compilación de Visual Studio.