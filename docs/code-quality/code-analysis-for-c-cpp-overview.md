---
title: Análisis de código para obtener información general de C/C++
ms.date: 04/28/2018
ms.topic: conceptual
helpviewer_keywords:
- annotations, code analysis
- build integration, code analysis
- C/C++ code analysis
- IDE, code analysis
- pragma directive, code analysis
- code analysis, C/C++
- code analysis tool
- command line, code analysis
- C++, code analysis
- check-in policies, code analysis
- '#pragma directives, code analysis'
- C, code analysis
ms.assetid: 81f0c9e8-f471-4de5-aac4-99db336a8809
ms.openlocfilehash: 26168e66fcb2809bc1eab68d3c8fa1ccf7495568
ms.sourcegitcommit: 7bea0420d0e476287641edeb33a9d5689a98cb98
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/17/2020
ms.locfileid: "79467266"
---
# <a name="code-analysis-for-cc-overview"></a>Análisis de código para obtener información general de C/C++

La herramienta deC++ análisis de código c/proporciona información sobre posibles defectos en elC++ código fuente de c/. Entre los errores de codificación más frecuentes notificados por esta herramienta se incluyen saturaciones de búfer, memoria sin inicializar, desreferencias de puntero NULL, y pérdidas de memoria y recursos. La herramienta también puede ejecutar comprobaciones en las [ C++ instrucciones básicas](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md).

## <a name="ide-integrated-development-environment-integration"></a>Integración del IDE (entorno de desarrollo integrado)

La herramienta de análisis de código está totalmente integrada en el IDE de Visual Studio.

Durante el proceso de compilación, las advertencias generadas para el código fuente aparecen en la lista de errores. Puede navegar al código fuente que causó la advertencia y ver información adicional sobre la causa y las posibles soluciones del problema.

## <a name="command-line-support"></a>Compatibilidad con la línea de comandos

También puede usar la herramienta de análisis desde la línea de comandos, tal y como se muestra en el ejemplo siguiente:

```cmd
C:\>cl /analyze Sample.cpp
```

**Visual Studio 2017 versión 15,7 y versiones posteriores:** Puede ejecutar la herramienta desde la línea de comandos con cualquier sistema de compilación, incluido CMake.

## <a name="pragma-support"></a>compatibilidad con #pragma

Puede usar la Directiva `#pragma` para tratar las advertencias como errores. habilitar o deshabilitar advertencias y suprimir advertencias para líneas de código individuales. Para obtener más información, vea [Directives pragma y la palabra clave __pragma](/cpp/preprocessor/pragma-directives-and-the-pragma-keyword).

## <a name="annotation-support"></a>Compatibilidad con anotaciones

Las anotaciones mejoran la precisión del análisis de código. Las anotaciones proporcionan información adicional sobre las condiciones previas y posteriores en los parámetros de función y los tipos de valor devuelto. Para obtener más información, consulte [uso de anotaciones sal para reducir defectosC++ de código C/](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md).

## <a name="run-analysis-tool-as-part-of-check-in-policy"></a>Ejecución de la herramienta de análisis como parte de la directiva de inserción en el repositorio

Puede que sea necesario exigir que todas las inserciones en el repositorio de código fuente cumplan determinadas directivas. En concreto, le conviene asegurarse de que se ejecutó un análisis como un paso de la compilación local más reciente. Para obtener más información sobre cómo habilitar una directiva de protección de análisis de código, vea [crear y usar directivas de protección de análisis de código](/visualstudio/code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies).

## <a name="team-build-integration"></a>Integración de Team Build

Puede usar las características integradas del sistema de compilación para ejecutar la herramienta de análisis de código como paso del proceso de compilación de Azure DevOps. Para obtener más información, consulte [Azure Pipelines](/azure/devops/pipelines/index?view=vsts).

## <a name="see-also"></a>Consulte también

- [Inicio rápido: Análisis de código para C/C++](quick-start-code-analysis-for-c-cpp.md)
- [Tutorial: analizar C/C++ code para detectar defectos](walkthrough-analyzing-c-cpp-code-for-defects.md)
- [Análisis de código para advertencias de C/C++](code-analysis-for-c-cpp-warnings.md)
- [Usar los comprobadores de C++ Core Guidelines](using-the-cpp-core-guidelines-checkers.md)
- [C++Referencia del comprobador de directrices básicas](code-analysis-for-cpp-corecheck.md)
- [Usar conjuntos de reglas para especificar C++ las reglas que se van a ejecutar](using-rule-sets-to-specify-the-cpp-rules-to-run.md)
- [Analizar la calidad de los controladores mediante herramientas de análisis de código](/windows-hardware/drivers/develop/analyzing-driver-quality-by-using-code-analysis-tools)
- [Advertencias de análisis de código para controladores](/windows-hardware/drivers/devtest/prefast-for-drivers-warnings)
