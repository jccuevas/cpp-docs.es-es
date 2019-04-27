---
title: Procedimiento Depurar una versión de lanzamiento
ms.date: 11/04/2016
helpviewer_keywords:
- debugging [C++], release builds
- release builds, debugging
ms.assetid: d333e4d1-4e6c-4384-84a9-cb549702da25
ms.openlocfilehash: 6d93fac4e980085c322acb55e6f8758e6cea0a00
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62188969"
---
# <a name="how-to-debug-a-release-build"></a>Procedimiento Depurar una versión de lanzamiento

Puede depurar una versión de lanzamiento de una aplicación.

### <a name="to-debug-a-release-build"></a>Para depurar una versión de lanzamiento

1. Abra el **páginas de propiedades** cuadro de diálogo para el proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](working-with-project-properties.md).

1. Haga clic en el **C o C++** nodo. Establecer **formato de información de depuración** a [compatible con C7 (/ Z7)](reference/z7-zi-zi-debug-information-format.md) o **base de datos de programa (/Zi)**.

1. Expanda **vinculador** y haga clic en el **General** nodo. Establecer **habilitar vinculación Incremental** a [No (/ INCREMENTAL: NO)](reference/incremental-link-incrementally.md).

1. Seleccione el **depuración** nodo. Establecer **generar información de depuración** a [Sí (/Debug)](reference/debug-generate-debug-info.md).

1. Seleccione el **optimización** nodo. Establecer **referencias** a [/OPT: ref](reference/opt-optimizations.md) y **Habilitar plegamiento de COMDAT** a [/OPT: ICF](reference/opt-optimizations.md).

1. Ahora puede depurar la aplicación de la compilación de versión. Para detectar un problema, paso a través del código (o la depuración Just-In-Time de uso) hasta que encuentre dónde se produce el error y, a continuación, determine los parámetros incorrectos o código.

   Si una aplicación funciona en una compilación de depuración, pero se produce un error en una versión de lanzamiento, una de las optimizaciones del compilador puede exponer un defecto en el código fuente. Para aislar el problema, deshabilitar las optimizaciones seleccionadas para cada archivo de código fuente hasta encontrar el archivo y la optimización que está causando el problema. (Para acelerar el proceso, puede dividir los archivos en dos grupos, deshabilite la optimización en un grupo y cuando encuentre un problema en un grupo, siga dividiendo hasta aislar el problema al archivo.)

   Puede usar [/RTC](reference/rtc-run-time-error-checks.md) para intentar exponer este tipo de errores en las compilaciones de depuración.

   Para obtener más información, consulte [optimizar el código](optimizing-your-code.md).

## <a name="see-also"></a>Vea también

[Solucionar problemas de versiones de lanzamiento](fixing-release-build-problems.md)
