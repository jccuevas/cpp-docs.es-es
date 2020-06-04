---
title: Procedimiento Depuración de una compilación de versión
ms.date: 11/04/2016
helpviewer_keywords:
- debugging [C++], release builds
- release builds, debugging
ms.assetid: d333e4d1-4e6c-4384-84a9-cb549702da25
ms.openlocfilehash: 6d93fac4e980085c322acb55e6f8758e6cea0a00
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62188969"
---
# <a name="how-to-debug-a-release-build"></a>Procedimiento Depuración de una compilación de versión

Puede depurar una compilación de versión de una aplicación.

### <a name="to-debug-a-release-build"></a>Cómo depurar una compilación de versión

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para más información, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](working-with-project-properties.md).

1. Haga clic en el nodo **C/C++** . Establezca **Formato de información de depuración** en [Compatible con C7 (/Z7)](reference/z7-zi-zi-debug-information-format.md) o **Base de datos de programa (/Zi)** .

1. Expanda **Enlazador** y haga clic en el nodo **General**. Establezca **Habilitar vinculación incremental** en [No (/INCREMENTAL:NO)](reference/incremental-link-incrementally.md).

1. Seleccione el nodo **Depuración**. Establezca **Generar información de depuración** en [Sí (/DEBUG)](reference/debug-generate-debug-info.md).

1. Seleccione el nodo **Optimización**. Establezca **Referencias** en [/OPT:REF](reference/opt-optimizations.md) y **Habilitar plegamiento de COMDAT** en [/OPT:ICF](reference/opt-optimizations.md).

1. Ahora puede depurar la aplicación de la compilación de versión. Para encontrar un problema, ejecute paso a paso el código (o use la depuración Just-in-Time) hasta que encuentre dónde se produce el error y, a continuación, determine los parámetros o el código incorrectos.

   Si una aplicación funciona en una compilación de depuración, pero se produce un error en una compilación de versión, una de las optimizaciones del compilador puede estar exponiendo un problema en el código fuente. Para aislar el problema, deshabilite las optimizaciones seleccionadas para cada archivo de código fuente hasta que encuentre el archivo y la optimización que están causando el problema. (Para acelerar este proceso, puede dividir los archivos en dos grupos, deshabilitar la optimización en uno de los grupos y, cuando encuentre un problema en un grupo, continuar dividiéndolo hasta que aísle el archivo problemático).

   Puede usar [/RTC](reference/rtc-run-time-error-checks.md) para intentar exponer estos errores en las compilaciones de depuración.

   Para obtener más información, vea [Optimizar el código](optimizing-your-code.md).

## <a name="see-also"></a>Vea también

[Solucionar problemas de versiones de lanzamiento](fixing-release-build-problems.md)
