---
title: 'Tutorial: vcperf y Windows Performance Analyzer'
description: Tutorial sobre cómo usar vcperf y WPA para analizar seguimientos de compilaciones de C++.
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 724df913400abb6d33c333f0a16c20fb982769bc
ms.sourcegitcommit: 98139766b548c55181ff5ec5ad3bfd9db2bf5c89
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/26/2020
ms.locfileid: "83865057"
---
# <a name="tutorial-vcperf-and-windows-performance-analyzer"></a>Tutorial: vcperf y Windows Performance Analyzer

::: moniker range="<=vs-2017"

Las herramientas de C++ Build Insights están disponibles en Visual Studio 2019. Para ver la documentación de estas versiones, establezca el control de selector **Versión** de Visual Studio para este artículo en Visual Studio 2019. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker-end
::: moniker range="vs-2019"

En este tutorial, aprenderá a usar *vcperf.exe* para recopilar un seguimiento de la compilación de C++. También aprenderá a ver este seguimiento en Windows Performance Analyzer.

## <a name="step-1-install-and-configure-windows-performance-analyzer"></a>Paso 1: Instalación y configuración de Windows Performance Analyzer

WPA es un visor de seguimiento disponible en Windows Assessment and Deployment Kit (ADK). Se trata de una utilidad independiente que no forma parte de los componentes que se pueden instalar con el instalador de Visual Studio.

Actualmente, en Windows ADK Insider Preview solo hay disponible una versión de WPA que admite C++ Build Insights. Para acceder a esta versión preliminar, debe registrarse en el [programa Windows Insider](https://insider.windows.com). No es necesario instalar el sistema operativo Windows 10 Insider Preview para obtener la versión preliminar de Windows ADK. Solo tiene que registrar la cuenta de Microsoft con el programa Windows Insider.

### <a name="to-download-and-install-wpa"></a>Descargar e instalar WPA

NOTA: Se requiere Windows 8 o posterior para instalar Windows Performance Analyzer.

1. Vaya a la [página de descarga](https://docs.microsoft.com/windows-hardware/get-started/adk-install) de Windows ADK.

1. Descargue e instale la versión más reciente de Windows ADK.

1. Cuando se le pregunte por las características que desea instalar, seleccione **Windows Performance Toolkit**. Puede seleccionar otras características si quiere, pero no son necesarias para instalar WPA.

   ![Pantalla de selección de características del instalador de Windows Performance Analyzer](media/wpa-installation.png)

### <a name="to-configure-wpa"></a><a name="configuration-steps"></a> Configurar WPA

Para ver los seguimientos de C++ Build Insights en WPA se requiere un complemento especial. Para instalarlo, siga estos pasos:

1. Para obtener el complemento, descargue uno de los componentes siguientes. No es necesario que sean ambos. Elija el que le resulte más conveniente.
    1. [Visual Studio 2019 versión 16.6 y posterior](https://visualstudio.microsoft.com/downloads/).
    1. [Paquete NuGet de C++ Build Insights](https://www.nuget.org/packages/Microsoft.Cpp.BuildInsights/).

1. Copie el archivo `perf_msvcbuildinsights.dll` en el directorio de instalación de WPA.
    1. En la versión 16.6 de Visual Studio 2019 y posterior, ese archivo se encuentra en esta ubicación: `C:\Program Files (x86)\Microsoft Visual Studio\2019\{Edition}\VC\Tools\MSVC\{Version}\bin\Host{Architecture}\{Architecture}`.
    1. En el paquete NuGet de C++ Build Insights, el archivo se encuentra en esta ubicación: `wpa\{Architecture}`.
    1. En las rutas de acceso anteriores, reemplace las variables entre llaves como se indica a continuación:
        1. `{Edition}` es la edición de Visual Studio 2019, como Community, Professional o Enterprise.
        1. `{Version}` es la versión de MSVC. Elija el que tenga el número más alto.
        1. `{Architecture}`: elija `x64` si tiene una versión de 64 bits de Windows. De lo contrario, elija `x86`.
    1. El directorio de instalación de WPA suele ser: `C:\Program Files (x86)\Windows Kits\10\Windows Performance Toolkit`.

1. En el directorio de instalación de WPA, abra el archivo `perfcore.ini` y agregue una entrada para `perf_msvcbuildinsights.dll`.

## <a name="step-2-trace-your-build-with-vcperfexe"></a>Paso 2: Seguimiento de la compilación con vcperf.exe

Para ver los datos de C++ Build Insights, primero debe recopilarlos en un archivo de seguimiento realizando estos pasos:

1. Abra un **símbolo del sistema de las herramientas nativas x86 o **x64** para Visual Studio 2019** en el modo de administrador. Haga clic con el botón derecho en el elemento de menú Inicio y elija **más** > **Ejecutar como administrador**.
    1. Elija **x64** si tiene una versión de 64 bits de Windows. De lo contrario, elija **x86**.

1. En la ventana del símbolo del sistema, escriba este comando:

   **vcperf.exe /start _nombreSesión_**

   Elija un nombre de sesión que recuerde para *nombreSesión*.

1. Compile el proyecto como lo haría normalmente. No es necesario usar la misma ventana del símbolo del sistema para compilar.

1. En la ventana del símbolo del sistema, escriba este comando:

   **vcperf.exe /stop _nombreSesión_ _traceFile.etl_**

   Use el mismo nombre de sesión que eligió antes para *nombreSesión*. Elija un nombre apropiado para el archivo de seguimiento *traceFile.etl*.

Así es cómo se ve una secuencia de comandos típica de *vcperf.exe* en una ventana del símbolo del sistema para desarrolladores:

![Un escenario de uso simple de vcperf.exe](media/vcperf-simple-usage.png)

### <a name="important-notes-about-vcperfexe"></a>Notas importantes sobre vcperf.exe

- Se requieren privilegios de administrador para iniciar o detener un seguimiento de *vcperf.exe*. Use una ventana del símbolo del sistema para desarrolladores que abra con **Ejecutar como administrador**.

- Solo se puede ejecutar una sesión de seguimiento cada vez en una máquina.

- Asegúrese de recordar el nombre de sesión que usó para iniciar el seguimiento. Detener una sesión en ejecución sin conocer su nombre puede ser problemático.

- Al igual que *cl.exe* y *link.exe*, la utilidad de línea de comandos *vcperf.exe* se incluye en una instalación de MSVC. No es necesario realizar ningún paso adicional para obtener este componente.

- *vcperf.exe* recopila información sobre todas las herramientas de MSVC que se ejecutan en el sistema. Como resultado, no tiene que iniciar la compilación desde el mismo símbolo del sistema que usó para recopilar el seguimiento. Puede compilar el proyecto desde un símbolo del sistema diferente o incluso en Visual Studio.

### <a name="vcperfexe-is-open-source"></a>vcperf.exe es de código abierto

Si desea compilar y ejecutar su propia versión de *vcperf.exe*, no dude en clonarla desde el [repositorio vcperf de GitHub](https://github.com/microsoft/vcperf).

## <a name="step-3-view-your-trace-in-windows-performance-analyzer"></a>Paso 3: Visualización del seguimiento en Windows Performance Analyzer

Inicie WPA y abra el seguimiento que acaba de recopilar. WPA debe reconocerlo como seguimiento de C++ Build Insights, y las siguientes vistas deben aparecer en el panel Probador de Graph de la izquierda:

- Explorador de compilaciones
- Archivos
- Funciones
- Creación de instancias de plantilla

Si no puede ver estas vistas, asegúrese de que WPA esté configurado correctamente, tal como se describe en el [paso 1](#configuration-steps). Puede ver los datos de compilación arrastrando las vistas a la ventana Análisis vacía de la derecha, como se muestra aquí:

![Visualización de un seguimiento de C++ Build Insights en Windows Performance Analyzer](media/wpa-viewing-trace.gif)

Hay otras vistas disponibles en el panel Probador de Graph. Arrástrelas a la ventana Análisis cuando le interese la información que contienen. La vista CPU (muestreada) es útil, ya que muestra el uso de CPU en toda la compilación.

## <a name="more-information"></a>Más información

[Tutorial: Conceptos básicos sobre Windows Performance Analyzer](wpa-basics.md)\
Obtenga información sobre las operaciones comunes de WPA que pueden ayudarlo a analizar los seguimientos de compilaciones.

[Referencia: comandos de vcperf](/cpp/build-insights/reference/vcperf-commands)\
En la referencia de comandos de *vcperf.exe* se enumeran todas las opciones de comando disponibles.

[Referencia: Vistas de Windows Performance Analyzer](/cpp/build-insights/reference/wpa-views)\
Consulte este artículo para obtener más información sobre las vistas de C++ Build Insights en WPA.

[Windows Performance Analyzer](/windows-hardware/test/wpt/windows-performance-analyzer)\
El sitio web oficial de la documentación de WPA.

::: moniker-end
