---
title: 'Tutorial: vcperf y Windows Performance Analyzer'
description: Tutorial sobre cómo utilizar vcperf y WPA para analizar las trazas de compilación de C++.
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: c22f3dfddfd346d4f0eee898cb5164fd8923336e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323421"
---
# <a name="tutorial-vcperf-and-windows-performance-analyzer"></a>Tutorial: vcperf y Windows Performance Analyzer

::: moniker range="<=vs-2017"

Las herramientas de C++ Build Insights están disponibles en Visual Studio 2019. Para ver la documentación de esta versión, establezca el control Selector de **versiones** de Visual Studio para este artículo en Visual Studio 2019. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker-end
::: moniker range="vs-2019"

En este tutorial, aprenderá a usar *vcperf.exe* para recopilar un seguimiento de su compilación de C++. También aprenderá a ver este seguimiento en el Analizador de rendimiento de Windows.

## <a name="step-1-install-and-configure-windows-performance-analyzer"></a>Paso 1: Instalar y configurar Windows Performance Analyzer

WPA es un visor de seguimiento disponible en el Kit de evaluación e implementación de Windows (ADK). Es una utilidad independiente que no forma parte de los componentes que puede instalar con el instalador de Visual Studio.

Una versión de WPA que admita C++ Build Insights actualmente solo está disponible en Windows ADK Insider Preview. Para acceder a esta vista previa, debe registrarse en el [programa Windows Insider](https://insider.windows.com). No es necesario instalar el sistema operativo Windows 10 Insider Preview para obtener la vista previa de Windows ADK. Solo necesita registrar su cuenta Microsoft con el Programa Windows Insider.

### <a name="to-download-and-install-wpa"></a>Para descargar e instalar WPA

NOTA: Se requiere Windows 8 o superior para instalar el Analizador de rendimiento de Windows.

1. Vaya a la página de [descarga](https://www.microsoft.com/en-us/software-download/windowsinsiderpreviewADK)de Windows ADK Insider Preview .

1. Descargue la versión preliminar de Windows ADK Insider. Es una imagen de disco.

1. Abra la imagen de disco y ejecute el instalador *adksetup.exe.*

1. Cuando se le soliciten las características que desea instalar, seleccione el Kit de herramientas de rendimiento de **Windows**. Puede seleccionar otras funciones si lo desea, pero no es necesario instalar WPA.

   ![Pantalla de selección de características del instalador del instalador de Windows Performance Analyzer](media/wpa-installation.png)

### <a name="to-configure-build-insights"></a><a name="configuration-steps"></a>Para configurar Build Insights

1. Inicie WPA.

1. Seleccione **Tablas** > de selección de ventana **(experimental)**.

1. Desplácese hacia abajo hasta la sección **Diagnóstico.**

1. Seleccione todas las vistas de MSVC Build Insights.

   ![Panel de selección de tablas de Windows Performance Analyzer](media/wpa-configuration.png)

## <a name="step-2-trace-your-build-with-vcperfexe"></a>Paso 2: Rastrea tu compilación con vcperf.exe

Para ver los datos de C++ Build Insights, primero recopile los datos en un archivo de seguimiento siguiendo estos pasos:

1. Abra un símbolo del sistema para desarrolladores de herramientas nativas o herramientas cruzadas para Visual Studio 2019 en modo de administrador. (Haga clic con el botón derecho en el elemento de menú Inicio y elija **Más** > **ejecución como administrador**.)

1. En la ventana del símbolo del sistema, ingrese este comando:

   **vcperf.exe /start _SessionName_**

   Elija un nombre de sesión que recordará para *SessionName*.

1. Compile su proyecto como lo haría normalmente. No es necesario usar la misma ventana del símbolo del sistema para compilar.

1. En la ventana del símbolo del sistema, ingrese este comando:

   **vcperf.exe /stop _SessionName_ _traceFile.etl_**

   Utilice el mismo nombre de sesión que eligió para *SessionName* antes. Elija un nombre adecuado para el archivo de seguimiento *traceFile.etl.*

Este es el aspecto típico de una secuencia de comandos *vcperf.exe* en una ventana del símbolo del sistema para desarrolladores:

![Un escenario de uso simple de vcperf.exe](media/vcperf-simple-usage.png)

### <a name="important-notes-about-vcperfexe"></a>Notas importantes sobre vcperf.exe

- Se requieren privilegios de administrador para iniciar o detener un seguimiento *vcperf.exe.* Utilice una ventana del símbolo del sistema para desarrolladores que abra mediante **Ejecutar como administrador**.

- Solo se puede ejecutar una sesión de seguimiento a la vez en un equipo.

- Asegúrese de recordar el nombre de la sesión que utilizó para iniciar el seguimiento. Puede ser problemático detener una sesión en ejecución sin saber su nombre.

- Al igual *que cl.exe* y *link.exe*, la utilidad de línea de comandos *vcperf.exe* se incluye en una instalación de MSVC. No se requieren pasos adicionales para obtener este componente.

- *vcperf.exe* recopila información sobre todas las herramientas MSVC que se ejecutan en su sistema. Como resultado, no es posible iniciar la compilación desde el mismo símbolo del sistema que usó para recopilar el seguimiento. Puede compilar el proyecto desde un símbolo del sistema diferente o incluso en Visual Studio.

## <a name="step-3-view-your-trace-in-windows-performance-analyzer"></a>Paso 3: Ver el seguimiento en Windows Performance Analyzer

Inicie WPA y abra la traza que acaba de recopilar. WPA debe reconocerlo como un seguimiento de C++ Build Insights, y las siguientes vistas deben aparecer en el panel Explorador de gráficos de la izquierda:

- Explorador de compilaciones
- Archivos
- Función

Si no puede ver estas vistas, compruebe que WPA está configurado correctamente, como se describe en el [paso 1.](#configuration-steps) Puede ver los datos de compilación arrastrando las vistas a la ventana de Análisis vacía a la derecha, como se muestra aquí:

![Visualización de un seguimiento de C++ Build Insights en Windows Performance Analyzer](media/wpa-viewing-trace.gif)

Otras vistas están disponibles en el panel Explorador de gráficos. Arrástrelos a la ventana Análisis cuando esté interesado en la información que contienen. Una útil es la vista CPU (muestreada), que muestra la utilización de la CPU a lo largo de la compilación.

## <a name="more-information"></a>Más información

[Tutorial: Conceptos básicos de Windows Performance Analyzer](wpa-basics.md)\
Obtenga información sobre las operaciones WPA comunes que pueden ayudarle a analizar los seguimientos de compilación.

[Referencia: comandos vcperf](/cpp/build-insights/reference/vcperf-commands)\
La referencia de *comandos vcperf.exe* enumera todas las opciones de comando disponibles.

[Referencia: Vistas de Windows Performance Analyzer](/cpp/build-insights/reference/wpa-views)\
Consulte este artículo para obtener más información sobre las vistas de C++ Build Insights en WPA.

[Analizador de rendimiento de Windows](/windows-hardware/test/wpt/windows-performance-analyzer)\
El sitio oficial de documentación WPA.

::: moniker-end
