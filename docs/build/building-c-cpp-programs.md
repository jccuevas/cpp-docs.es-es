---
title: Compilar programas de C/C ++ | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2792b49d7d3d3f107e39931ff62e6c4137c9c5ca
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45723273"
---
# <a name="building-cc-programs"></a>Compilar programas de C/C++

Los proyectos de Visual C++ se pueden compilar en Visual Studio o en la línea de comandos. El IDE de Visual Studio usa [MSBuild](../build/msbuild-visual-cpp.md) para compilar proyectos y soluciones. En la línea de comandos, puede usar el compilador (cl.exe) y el vinculador (link.exe) de C/C++ para compilar proyectos sencillos. Para compilar los proyectos más complejos en la línea de comandos, puede usar MSBuild o [NMAKE](../build/nmake-reference.md). Para obtener información general acerca de cómo usar Visual Studio para compilar proyectos y soluciones, consulte [compilar y generar](/visualstudio/ide/compiling-and-building-in-visual-studio).

## <a name="in-this-section"></a>En esta sección

[Compilar proyectos de C++ en Visual Studio](../ide/building-cpp-projects-in-visual-studio.md) explica cómo utilizar el IDE de Visual Studio para compilar el proyecto de C o C++.

[Generar código de C o C++ en la línea de comandos](../build/building-on-the-command-line.md) se explica cómo usar el compilador de línea de comandos de C/C ++ y herramientas de compilación que se incluyen en Visual Studio.

[Compilar aplicaciones aisladas de C/C ++ y ensamblados en paralelo](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md) describe el modelo de implementación de aplicaciones de escritorio de Windows, en función de la idea de aplicaciones aisladas y ensamblados en paralelo.

[Referencia de generación de C o C++](../build/reference/c-cpp-building-reference.md) proporciona vínculos a artículos de referencia sobre cómo compilar programas en C++, el compilador y las opciones del vinculador y diversas herramientas de compilación.

[Configuración de Visual C++ de 64 bits, x64 destinos](../build/configuring-programs-for-64-bit-visual-cpp.md) describe cómo configurar Visual Studio y la línea de comandos para usar el conjunto de herramientas de 64 bits y cómo elegir como destino arquitecturas de 64 bits y se describen problemas comunes de migración cuando el código se traslada a 64 bits arquitecturas.

[Configuración de Visual C++ para procesadores ARM](../build/configuring-programs-for-arm-processors-visual-cpp.md) se describen las convenciones que se usan los procesadores ARM y se abordan problemas comunes de migración cuando el código se traslada a arquitecturas ARM.

[Configurar programas para Windows XP](../build/configuring-programs-for-windows-xp.md) se describe cómo establecer el conjunto de herramientas de la plataforma de desarrollo de Windows XP de destino.

## <a name="related-sections"></a>Secciones relacionadas

[Compilar y generar](/visualstudio/ide/compiling-and-building-in-visual-studio) describe la compilación de Visual Studio herramientas y sistemas.