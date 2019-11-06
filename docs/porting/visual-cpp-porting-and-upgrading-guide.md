---
title: Guía C++ de migración y actualización de Microsoft
description: Actualice el C++ código de Microsoft a la versión más reciente de Visual Studio.
ms.date: 10/29/2019
ms.assetid: f5fbcc3d-aa72-41a6-ad9a-a706af2166fb
ms.topic: overview
ms.openlocfilehash: d67c2665574242a46d697f6e9f24321556146958
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/05/2019
ms.locfileid: "73625681"
---
# <a name="microsoft-c-porting-and-upgrading-guide"></a>Guía C++ de migración y actualización de Microsoft

En este tema se proporciona una guía para actualizar C++ el código de Microsoft a la versión más reciente de Visual Studio. Si va a actualizar desde un proyecto creado en Visual Studio 2008 o una versión anterior, primero debe usar Visual Studio 2010 para convertir el proyecto al formato MSBuild y luego abrir el proyecto en Visual Studio 2019. En el caso de los proyectos creados en Visual Studio 2010 a 2015, solo tiene que abrir el proyecto en Visual Studio 2019. Para obtener instrucciones completas, vea [actualizar C++ proyectos de versiones anteriores de Visual Studio](upgrading-projects-from-earlier-versions-of-visual-cpp.md).

Los conjuntos de herramientas de Visual Studio 2015, Visual Studio 2017 y Visual Studio 2019 son compatibles con archivos binarios, lo que permite actualizar a una versión más reciente del compilador sin tener que actualizar las dependencias de la biblioteca. Para obtener más información, consulte [ C++ compatibilidad binaria entre 2015 y 2019](binary-compat-2015-2017.md).

Al actualizar proyectos que utilizan bibliotecas de código abierto o que están diseñados para ejecutarse en varias plataformas, se recomienda migrar a un proyecto basado en CMake. Para obtener más información, vea [CMake Projects in Visual Studio](../build/cmake-projects-in-visual-studio.md)

## <a name="reasons-to-upgrade-c-code"></a>Razones para actualizar C++ el código

Si una aplicación heredada se ejecuta correctamente, en un entorno seguro y no está en desarrollo activo, es posible que no haya muchos incentivos para actualizarla. Sin embargo, si una aplicación requiere un mantenimiento continuo o un nuevo desarrollo de características que incluye mejoras de rendimiento o seguridad, es posible que considere la posibilidad de actualizar el código por cualquiera de los siguientes motivos:

- El mismo código puede ejecutarse más rápido debido a las optimizaciones del compilador mejoradas.

- Las C++ características modernas y las prácticas de programación eliminan muchas causas comunes de errores y es mucho más fácil de mantener esas expresiones de estilo C más antiguas.

- Los tiempos de compilación son significativamente más rápidos, debido a las mejoras de rendimiento en el compilador y el vinculador.

- Mejor conformidad con los estándares. La opción del compilador [/permissive-](../build/reference/permissive-standards-conformance.md) permite identificar código que anteriormente permitía el compilador de Microsoft C++ , pero que no C++ cumple con el estándar actual.

- Mejor seguridad en tiempo de ejecución, incluidas características de la [biblioteca en]() tiempo de ejecución de C más seguras y características del compilador, como la comprobación de la [protección](../build/reference/guard-enable-guard-checks.md) y los saneados de direcciones (Visual Studio 2019 versión 16,4).

## <a name="multitargeting-vs-upgrading"></a>Compatibilidad con múltiples versiones y actualización

Si la actualización de la base de código a un nuevo conjunto de herramientas no es una opción, todavía puede usar una versión reciente de Visual Studio para compilar y editar proyectos que se compilan con bibliotecas y conjuntos de herramientas más antiguos. En Visual Studio 2019 puede aprovechar las ventajas de las características de como:

- herramientas de análisis estático moderno, incluidos C++ los comprobadores de directrices principales y Clang, para ayudar a identificar posibles problemas en el código fuente.

- el formato automático de acuerdo con la elección de los estilos modernos puede ayudar a que el código heredado sea mucho más legible.

Para obtener más información, vea [Use native multi-targeting in Visual Studio to build old projects](use-native-multi-targeting.md) (Usar compatibilidad nativa con múltiples versiones en Visual Studio para compilar proyectos antiguos).

## <a name="in-this-section"></a>En esta sección

|Title|Descripción|
|-----------|-----------------|
|[Actualizar C++ proyectos desde versiones anteriores de Visual Studio](upgrading-projects-from-earlier-versions-of-visual-cpp.md)|Cómo actualizar la base de código a Visual Studio 2019 y v142 del compilador.|
|[C++Compatibilidad binaria entre 2015 y 2019](binary-compat-2015-2017.md)|Consuma bibliotecas de V140 tal cual desde proyectos de v142.|
|[Usar compatibilidad nativa con múltiples versiones en Visual Studio para compilar proyectos antiguos](use-native-multi-targeting.md)|Use Visual Studio 2019 con compiladores y bibliotecas más antiguos.|
|[Historial de cambios en Visual C++ 2003-2015](visual-cpp-change-history-2003-2015.md)|Una lista de todos los cambios de las bibliotecas C++ de Microsoft y las herramientas de compilación de Visual Studio 2003 a 2015 que podrían requerir cambios en el código.|
|[Novedades de Visual C++ de 2003 a 2015](visual-cpp-what-s-new-2003-through-2015.md)|Toda la información sobre novedades de Microsoft C++ de visual Studio 2003 a través de visual Studio 2015.|
|[Migración y actualización: ejemplos y casos prácticos](porting-and-upgrading-examples-and-case-studies.md)|En esta sección migramos y actualizamos varios ejemplos y aplicaciones y analizamos las experiencias y los resultados. Puede que leer estos ejemplos le dé una idea de lo que conlleva el proceso de migración y actualización. Durante el proceso ofreceremos sugerencias y trucos para llevar a cabo la actualización y mostraremos cómo se corrigieron errores concretos.|
|[Migrar a la Plataforma universal de Windows](porting-to-the-universal-windows-platform-cpp.md)|Contiene información sobre el traslado de código a Windows 10.|
|[Introducción a Visual C++ para los usuarios de UNIX](introduction-to-visual-cpp-for-unix-users.md)|Proporciona información a los usuarios de UNIX que no estén familiarizados con Visual C++ y quieran ser más productivos con él.|
|[Ejecución de programas de Linux en Windows](porting-from-unix-to-win32.md)|Describe las opciones para migrar aplicaciones de UNIX a Windows.|

## <a name="see-also"></a>Vea también

[C++ en Visual Studio](../overview/visual-cpp-in-visual-studio.md)<br/>
[Novedades del compilador de C++ en Visual Studio](../overview/what-s-new-for-visual-cpp-in-visual-studio.md)<br/>
[Mejoras de conformidad de C++ en Visual Studio](../overview/cpp-conformance-improvements.md)<br/>
