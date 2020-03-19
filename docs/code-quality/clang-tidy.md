---
title: Uso de Clang-ordenado en Visual Studio
description: Cómo usar Clang en Visual Studio para el análisis de código C++ de Microsoft.
ms.date: 02/19/2020
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.clangtidy
author: frozenpandaman
ms.author: efessler
ms.openlocfilehash: 3dbe66e9d7117c027c0ec867011189824c59ce31
ms.sourcegitcommit: 21e168731b8fe0eaff18f070cee5d54aa5782c2d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/24/2020
ms.locfileid: "79469900"
---
# <a name="using-clang-tidy-in-visual-studio"></a>Uso de Clang-ordenado en Visual Studio

::: moniker range="<=vs-2017"

La compatibilidad con Clang-ordenado requiere Visual Studio 2019 versión 16,4 o posterior. Para ver la documentación, elija Visual Studio 2019 en el selector de versión de la documentación.

::: moniker-end

::: moniker range=">=vs-2019"

El análisis de código admite de forma nativa [Clang](https://clang.llvm.org/extra/clang-tidy/) para proyectos de MSBuild y CMake, ya sea mediante conjuntos de herramientas Clang o MSVC. Las comprobaciones de Clang se pueden ejecutar como parte del análisis de código en segundo plano. Aparecen como advertencias en el editor (zigzag) y se muestran en el Lista de errores.

La compatibilidad con Clang está disponible a partir de la versión 16,4 de Visual Studio 2019. Se incluye automáticamente al elegir una C++ carga de trabajo en el instalador de Visual Studio.

Clang es la herramienta de análisis predeterminada cuando se usa el conjunto de herramientas LLVM/Clang-cl, disponible tanto en MSBuild como en CMake. Puede configurarlo al usar un conjunto de herramientas de MSVC para ejecutarse junto con o reemplazar la experiencia de análisis de código estándar. Si usa el conjunto de herramientas Clang-cl, el análisis de código de Microsoft no está disponible.

Clang: se ejecuta después de una compilación correcta. Es posible que tenga que resolver los errores de código fuente para obtener resultados Clang.

## <a name="msbuild"></a>MSBuild

Puede configurar Clang-ordenado para que se ejecute como parte del análisis de código y compilar en la página **análisis de código** > **General** en el ventana Propiedades del proyecto. Las opciones para configurar la herramienta se pueden encontrar en el submenú Clang-ordenado.

Para obtener más información, vea [Cómo: establecer propiedades de análisis de código paraC++ proyectos de C/](../code-quality/how-to-set-code-analysis-properties-for-c-cpp-projects.md).

## <a name="cmake"></a>CMake

En los proyectos de CMake, puede configurar las comprobaciones de Clang en `CMakeSettings.json`. Una vez abierto, haga clic en "editar JSON" en la esquina superior derecha del editor de configuración del proyecto CMake. Se reconocen las claves siguientes:

- `enableMicrosoftCodeAnalysis`: habilita el análisis de código de Microsoft
- `enableClangTidyCodeAnalysis`: habilita el análisis Clang
- `clangTidyChecks`: configuración Clang, especificada como una lista separada por comas, es decir, las comprobaciones para habilitar o deshabilitar

Si no se especifica ninguna de las opciones "habilitar", Visual Studio seleccionará la herramienta de análisis que coincida con el conjunto de herramientas de la plataforma que se usa.

## <a name="warning-display"></a>Pantalla de advertencia

Clang: las ejecuciones no ordenadas provocan que se muestren advertencias en el Lista de errores y, como los subrayados en el editor, en secciones relevantes del código. Use la columna "categoría" en el Lista de errores para ordenar y organizar las advertencias de Clang. Puede configurar las advertencias en el editor activando la opción "deshabilitar subrayados de análisis de código" en **herramientas** > **Opciones**.

## <a name="clang-tidy-configuration"></a>Clang: configuración ordenada

Puede configurar las comprobaciones que Clang se ejecuta dentro de Visual Studio a través de la opción **de comprobaciones Clang** . Esta entrada se proporciona al argumento **--Checks** de la herramienta. Cualquier configuración adicional puede incluirse en archivos de *`.clang-tidy`* personalizados. Para obtener más información, consulte la [documentación de Clang en LLVM.org](https://clang.llvm.org/extra/clang-tidy/).

## <a name="see-also"></a>Consulte también

- [Compatibilidad de Clang/LLVM con proyectos de MSBuild](https://devblogs.microsoft.com/cppblog/clang-llvm-support-for-msbuild-projects/)
- [Compatibilidad de Clang/LLVM con proyectos de CMake](https://devblogs.microsoft.com/cppblog/visual-studio-cmake-support-clang-llvm-cmake-3-14-vcpkg-and-performance-improvements/)

::: moniker-end
