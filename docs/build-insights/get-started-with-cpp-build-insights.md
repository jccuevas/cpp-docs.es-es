---
title: Introducción a la C++ información de compilación
description: Información general de alto nivel sobre cómo usar las herramientas de análisis de rendimiento en tiempo de compilación que forman C++ parte de la información de compilación.
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 9c31d317cd7b9c6465362e3e532db2128303f602
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/05/2019
ms.locfileid: "73633229"
---
# <a name="get-started-with-c-build-insights"></a>Introducción a la C++ información de compilación

::: moniker range="<=vs-2017"

Las C++ herramientas de Build Insights están disponibles en Visual Studio 2019. Para ver la documentación de esa versión, establezca el control selector de versión de Visual Studio para este artículo en Visual Studio 2019.

::: moniker-end
::: moniker range="vs-2019"

C++Build Insights es una colección de herramientas que proporciona mayor visibilidad en la cadena de herramientas C++ de Microsoft Visual (MSVC). Las herramientas recopilan datos sobre C++ las compilaciones y la presentan en un formato que puede ayudarle a responder a preguntas comunes, como:

- ¿Las compilaciones son suficientemente paralelas?
- ¿Qué debo incluir en mi encabezado precompilado (PCH)?
- ¿Hay un cuello de botella específico en el que se debe centrar para aumentar la velocidad de compilación?

Los dos componentes principales de esta tecnología son la utilidad de línea de comandos *vcperf. exe* y un complemento para el visor de seguimiento del analizador de rendimiento de Windows (WPA). La utilidad se usa para recopilar seguimientos de la compilación, mientras que el complemento permite verlas en WPA. Siga estos pasos para empezar a usar estas dos herramientas.

## <a name="step-1-install-and-configure-windows-performance-analyzer"></a>Paso 1: instalar y configurar el analizador de rendimiento de Windows

WPA es un visor de seguimiento disponible en Windows Assessment and Deployment Kit (ADK). Es una utilidad independiente que no forma parte de los componentes que se pueden instalar con el instalador de Visual Studio.

Actualmente, una versión de WPA C++ que admite Build Insights solo está disponible en la versión preliminar de Windows ADK Insider. Para obtener acceso a esta vista previa, debe registrarse en el [programa Windows Insider](https://insider.windows.com). No es necesario instalar el sistema operativo Windows 10 Insider Preview para obtener la versión preliminar de Windows ADK. Solo tiene que registrar el cuenta de Microsoft con el programa Windows Insider.

### <a name="to-download-and-install-wpa"></a>Para descargar e instalar WPA

1. Vaya a la [Página de descarga](https://www.microsoft.com/software-download/windowsinsiderpreviewADK)de Windows ADK Insider Preview.

1. Descargue Windows ADK Insider Preview. Es una imagen de disco.

1. Abra la imagen de disco y ejecute el instalador de *adksetup. exe* .

1. Cuando se le pidan las características que desea instalar, seleccione el **Kit de herramientas de rendimiento de Windows**. Puede seleccionar otras características si lo desea, pero no es necesario instalar WPA.

   ![Pantalla de selección de características del instalador del analizador de rendimiento de Windows](media/wpa-installation.png)

### <a name="configuration-steps"></a>Para configurar la información de compilación

1. Inicie WPA.

1. Seleccione **ventana** > **seleccionar tablas (experimental)** .

1. Desplácese hacia abajo hasta la sección **diagnósticos** .

1. Seleccione todas las vistas de MSVC Build Insights.

   ![Panel de selección de tabla de Windows Performance Analyzer](media/wpa-configuration.png)

## <a name="step-2-trace-your-build-with-vcperfexe"></a>Paso 2: realizar un seguimiento de la compilación con vcperf. exe

Para ver C++ los datos de Build Insights, primero debe recopilarlos en un archivo de seguimiento siguiendo estos pasos:

1. Abra un símbolo del sistema para desarrolladores de herramientas nativas o Cross Tools para Visual Studio 2019 en modo de administrador. (Haga clic con el botón secundario en el elemento de menú Inicio y elija **más** > **Ejecutar como administrador**).

1. En la ventana del símbolo del sistema, escriba este comando:

   **vcperf. exe/start _nombresesión_**

   Elija un nombre de sesión que recuerde para *nombresesión*.

1. Compile el proyecto como lo haría normalmente. No es necesario usar la misma ventana del símbolo del sistema para compilar.

1. En la ventana del símbolo del sistema, escriba este comando:

   **vcperf. exe/stop _nombresesión_ _. ETL_**

   Use el mismo nombre de sesión que eligió para *nombresesión* antes. Elija un nombre apropiado para el archivo de seguimiento de seguimiento *. ETL* .

Este es el aspecto de una secuencia de comandos típica de *vcperf. exe* en una ventana del símbolo del sistema para desarrolladores:

![Un escenario simple de uso de vcperf. exe](media/vcperf-simple-usage.png)

### <a name="important-notes-about-vcperfexe"></a>Notas importantes acerca de vcperf. exe

- Se requieren privilegios de administrador para iniciar o detener un seguimiento de *vcperf. exe* . Use una ventana del símbolo del sistema para desarrolladores que abra con **Ejecutar como administrador**.

- Solo se puede ejecutar una sesión de seguimiento cada vez en un equipo.

- Asegúrese de recordar el nombre de sesión que usó para iniciar el seguimiento. Puede ser problemático detener una sesión en ejecución sin conocer su nombre.

- Al igual que *cl. exe* y *Link. exe*, la utilidad de línea de comandos *vcperf. exe* se incluye en una instalación de MSVC. No es necesario realizar ningún paso adicional para obtener este componente.

- *vcperf. exe* recopila información sobre todas las herramientas de MSVC que se ejecutan en el sistema. Como resultado, no tiene que iniciar la compilación desde el mismo símbolo del sistema que usó para recopilar el seguimiento. Puede compilar el proyecto desde un símbolo del sistema diferente o incluso en Visual Studio.

## <a name="step-3-view-your-trace-in-windows-performance-analyzer"></a>Paso 3: ver el seguimiento en el analizador de rendimiento de Windows

Inicie WPA y abra el seguimiento que acaba de recopilar. WPA debe reconocerla como C++ seguimiento de Build Insights y las siguientes vistas deben aparecer en el panel del explorador de gráficos de la izquierda:

- Build Explorer
- Archivos
- Función

Si no puede ver estas vistas, asegúrese de que WPA esté configurado correctamente, tal y como se describe en el [paso 1](#configuration-steps). Puede ver los datos de compilación arrastrando las vistas a la ventana de análisis vacía a la derecha, como se muestra aquí:

![Ver un C++ seguimiento de Build Insights en el analizador de rendimiento de Windows](media/wpa-viewing-trace.gif)

Hay otras vistas disponibles en el panel del explorador de gráficos. Arrástrelos a la ventana de análisis cuando esté interesado en la información que contienen. Una utilidad es la vista de CPU (muestreada), que muestra el uso de CPU a lo largo de la compilación.

## <a name="more-information"></a>Más información

[Aspectos básicos del analizador de rendimiento de Windows](wpa-basics.md)\
Obtenga información acerca de las operaciones comunes de WPA que pueden ayudarle a analizar los seguimientos de compilación.

\ de [referencia de vcperf. exe](vcperf-reference.md)
La referencia de comandos de *vcperf. exe* muestra todas las opciones de comando disponibles.

[Referencia](wpa-views-reference.md) de las vistas del analizador de rendimiento de Windows\
Consulte este artículo para obtener más información sobre C++ las vistas de Build Insights en WPA.

[Analizador de rendimiento de Windows](/windows-hardware/test/wpt/windows-performance-analyzer)\
El sitio de documentación de WPA oficial.

::: moniker-end