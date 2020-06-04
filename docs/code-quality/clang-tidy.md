---
title: Uso de Clang-Tidy en Visual Studio
description: Cómo usar Clang-Tidy en Visual Studio para el análisis de código de Microsoft C++.
ms.date: 02/19/2020
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.clangtidy
author: frozenpandaman
ms.author: efessler
ms.openlocfilehash: ff32f522eaacee67e19aedaa1153b2c68edc98d4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81355158"
---
# <a name="using-clang-tidy-in-visual-studio"></a>Uso de Clang-Tidy en Visual Studio

::: moniker range="<=vs-2017"

La compatibilidad con Clang-Tidy requiere Visual Studio 2019 versión 16.4 o posterior. Para ver la documentación de esta versión, establezca el control Selector de **versiones** de Visual Studio para este artículo en Visual Studio 2019. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker-end

::: moniker range=">=vs-2019"

Análisis de código admite de forma nativa [Clang-Tidy](https://clang.llvm.org/extra/clang-tidy/) para proyectos de MSBuild y CMake, ya sea mediante conjuntos de herramientas Clang o MSVC. Las comprobaciones de Clang-Tidy se pueden ejecutar como parte del análisis de código de fondo. Aparecen como advertencias en el editor (squiggles) y se muestran en la lista de errores.

La compatibilidad con Clang-Tidy está disponible a partir de Visual Studio 2019 versión 16.4. Se incluye automáticamente al elegir una carga de trabajo de C++ en el instalador de Visual Studio.

Clang-Tidy es la herramienta de análisis predeterminada cuando se utiliza el conjunto de herramientas LLVM/clang-cl, disponible en MSBuild y CMake. Puede configurarlo al utilizar un conjunto de herramientas MSVC para ejecutarse junto a la experiencia estándar de análisis de código o para reemplazarla. Si utiliza el conjunto de herramientas clang-cl, Microsoft Code Analysis no está disponible.

Clang-Tidy se ejecuta después de una compilación correcta. Es posible que deba resolver errores de código fuente para obtener resultados de Clang-Tidy.

## <a name="msbuild"></a>MSBuild

Puede configurar Clang-Tidy para que se ejecute como parte de Análisis de código y compilar en la página**General** **de análisis** > de código en la ventana Propiedades del proyecto. Las opciones para configurar la herramienta se pueden encontrar en el submenú Clang-Tidy.

Para obtener más información, consulte Cómo: Establecer propiedades de análisis de código [para proyectos C/C++.](../code-quality/how-to-set-code-analysis-properties-for-c-cpp-projects.md)

## <a name="cmake"></a>CMake

En los proyectos DeC, puede configurar las `CMakeSettings.json`comprobaciones de Clang-Tidy en . Una vez abierto, haga clic en "Editar JSON" en la esquina superior derecha del Editor de configuración del proyecto CMake. Se reconocen las siguientes claves:

- `enableMicrosoftCodeAnalysis`: Habilita el análisis de código de Microsoft
- `enableClangTidyCodeAnalysis`: Permite el análisis de Clang-Tidy
- `clangTidyChecks`: Configuración de Clang-Tidy, especificada como una lista separada por comas, es decir, comprueba que se habilite o deshabilite

Si no se especifica ninguna de las opciones "habilitar", Visual Studio seleccionará la herramienta de análisis que coincida con el conjunto de herramientas de plataforma utilizado.

## <a name="warning-display"></a>Visualización de advertencia

Las ejecuciones de Clang-Tidy dan como resultado advertencias que se muestran en la lista de errores y, a medida que el editor se ondea debajo de las secciones relevantes del código. Utilice la columna "Categoría" de la lista de errores para ordenar y organizar las advertencias de Clang-Tidy. Puede configurar advertencias en el editor alternando la opción "Desactivar ondulaciones de análisis de código" **en** > **Opciones**de herramientas .

## <a name="clang-tidy-configuration"></a>Configuración de Clang-Tidy

Puede configurar las comprobaciones que clang-tidy se ejecuta dentro de Visual Studio a través de la **Clang-Tidy Checks** opción. Esta entrada se proporciona al argumento **--checks** de la herramienta. Cualquier configuración adicional se *`.clang-tidy`* puede incluir en archivos personalizados. Para obtener más información, consulte la documentación de [Clang-Tidy sobre LLVM.org](https://clang.llvm.org/extra/clang-tidy/).

## <a name="see-also"></a>Consulte también

- [Compatibilidad con Clang/LLVM para proyectos de MSBuild](https://devblogs.microsoft.com/cppblog/clang-llvm-support-for-msbuild-projects/)
- [Soporte de Clang/LLVM para proyectos CMake](https://devblogs.microsoft.com/cppblog/visual-studio-cmake-support-clang-llvm-cmake-3-14-vcpkg-and-performance-improvements/)

::: moniker-end
