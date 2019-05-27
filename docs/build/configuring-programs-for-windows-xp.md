---
title: Configuración de programas para Windows XP
ms.date: 05/16/2019
ms.assetid: 1e4487b3-d815-4123-878b-5718b22f0fd5
ms.openlocfilehash: 6c94c6a66d0f22b8707012856a65df4b19965acb
ms.sourcegitcommit: a10c9390413978d36b8096b684d5ed4cf1553bc8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2019
ms.locfileid: "65837135"
---
# <a name="configuring-programs-for-windows-xp"></a>Configuración de programas para Windows XP

Como Visual Studio admite varios conjuntos de herramientas de plataforma, puede elegir como destino sistemas operativos y bibliotecas en tiempo de ejecución que no son compatibles con el conjunto de herramientas predeterminado. Por ejemplo, al cambiar el conjunto de herramientas de plataforma, puede usar las mejoras de lenguaje C++11, C++14 y C++17 admitidas por el compilador de MSVC en Visual Studio para crear aplicaciones que tengan como destino Windows XP y Windows Server 2003. También pude usar conjuntos de herramientas de plataforma anteriores para mantener la compatibilidad binaria del código heredado y seguir aprovechando las características más recientes del IDE de Visual Studio.

Visual Studio 2019 y versiones posteriores no admite la creación de código para Windows XP mediante el uso del conjunto de herramientas v142. La compatibilidad con el desarrollo de Windows XP mediante el uso del conjunto de herramientas v141 que se incluye en Visual Studio 2017 está disponible como componente opcional en el Instalador de Visual Studio.

## <a name="install-the-windows-xp-platform-toolset"></a>Instalar el conjunto de herramientas de la plataforma Windows XP

Para obtener el conjunto de herramientas de plataforma y los componentes para elegir como destino Windows XP y Windows Server 2003 en Visual Studio 2017, ejecute el Instalador de Visual Studio. Cuando instala Visual Studio por primera vez o cuando elige **Modificar** para modificar una instalación existente, asegúrese de que se seleccione la carga de trabajo **Desarrollo para el escritorio con C++**. En la lista de componentes opcionales para esta carga de trabajo, elija **Compatibilidad de Windows XP con C++**  y, después, elija **Instalar** o **Modificar**.

## <a name="windows-xp-targeting-experience"></a>Experiencia con Windows XP como destino

El conjunto de herramientas de la plataforma Windows XP que se incluye en Visual Studio es una versión de Windows SDK 7, pero usa el compilador de C++ actual. También configura propiedades del proyecto con los valores predeterminados adecuados, como por ejemplo, la especificación de un enlazador compatible para destinos de nivel inferior. En Windows XP y Windows Server 2003 solo pueden ejecutarse aplicaciones de escritorio de Windows creadas mediante un conjunto de herramientas de la plataforma Windows XP, pero estas aplicaciones también pueden ejecutarse en sistemas operativos Windows más recientes.

#### <a name="to-target-windows-xp"></a>Establecer Windows XP como destino

1. En el **Explorador de soluciones**, abra el menú contextual del proyecto y después elija **Propiedades**.

1. En el cuadro de diálogo **Páginas de propiedades** del proyecto, en **Propiedades de configuración** > **General**, establezca la propiedad **Conjunto de herramientas de la plataforma** al conjunto de herramientas de Windows XP que prefiera. Por ejemplo, elija **Visual Studio 2017 - Windows XP (v141_xp)** para crear código para Windows XP y Windows Server 2003 mediante el compilador de Microsoft C++ en Visual Studio 2017.

### <a name="c-runtime-support"></a>Compatibilidad con el motor en tiempo de ejecución de C++

Además del conjunto de herramientas de la plataforma Windows XP, también incluyen compatibilidad con el runtime de Windows XP y Windows Server 2003: la biblioteca en tiempo de ejecución de C (CRT), la biblioteca de C++ Standard, la Active Template Library (ATL), la biblioteca de runtime de simultaneidad (ConCRT), la Parallel Patterns Library (PPL), la biblioteca MFC (Microsoft Foundation Class) y la biblioteca de AMP de C++ (C++ Accelerated Massive Programming). Para estos sistemas operativos, las versiones mínimas compatibles son Windows XP Service Pack 3 (SP3) para x86, Windows XP Service Pack 2 (SP2) para x64 y Windows Server 2003 Service Pack 2 (SP2) para x86 y x64.

Estas bibliotecas son compatibles con los conjuntos de herramientas de plataforma instalados por Visual Studio, en función del destino:

|Biblioteca|Conjunto de herramientas de plataforma predeterminado dirigido a aplicaciones de escritorio de Windows|Conjunto de herramientas de plataforma predeterminado destinado a aplicaciones de Microsoft Store|Conjunto de herramientas de plataforma de Windows XP destinadas a Windows XP y Windows Server 2003|
|---|---|---|---|
|CRT|X|X|X|
|Biblioteca estándar de C++|X|X|X|
|ATL|X|X|X|
|ConCRT/PPL|X|X|X|
|MFC|X||X|
|C++ AMP|X|X||

> [!NOTE]
> Aplicaciones escritas en C++/CLI y que tienen como destino la ejecución de .NET Framework 4 en Windows XP y Windows Server 2003.

### <a name="differences-between-the-toolsets"></a>Diferencias entre los conjuntos de herramientas

Debido a diferencias de compatibilidad de plataformas y bibliotecas, la experiencia de desarrollo para aplicaciones que usan un conjunto de herramientas de la plataforma Windows XP no es tan completa como para las que usan el conjunto de herramientas de la plataforma Visual Studio predeterminado.

- **Características del lenguaje C++**

   Solo las características del lenguaje C++ implementadas en Visual Studio 2012 se admiten en aplicaciones que usan el conjunto de herramientas de la plataforma v110\_xp. Solo las características del lenguaje C++ implementadas en Visual Studio 2013 se admiten en aplicaciones que usan el conjunto de herramientas de la plataforma v120\_xp. Solo las características del lenguaje C++ implementadas en Visual Studio 2015 se admiten en aplicaciones que usan el conjunto de herramientas de la plataforma v140\_xp. Visual Studio usa el compilador correspondiente al compilar con los conjuntos de herramientas de plataforma anteriores. Use el conjunto de herramientas de la plataforma Windows XP más reciente para aprovechar las características adicionales del lenguaje C++ implementadas en esa versión del compilador.

- **Depuración remota**

   Herramientas remotas para Visual Studio no admite la depuración remota en Windows XP o Windows Server 2003. Para depurar una aplicación cuando se ejecuta en Windows XP o Windows Server 2003, puede usar un depurador de una versión anterior de Visual Studio y depurarla de manera local o remota. Es una experiencia similar a la depuración de una aplicación en Windows Vista, que es un destino de tiempo de ejecución del conjunto de herramientas de plataforma, pero no un destino de depuración remoto.

- **Análisis estático**

   Los conjuntos de herramientas de la plataforma Windows XP no admiten el análisis estático porque las anotaciones SAL de Windows SDK 7 y las bibliotecas en tiempo de ejecución son incompatibles. Cuando quiera realizar un análisis estático en una aplicación compatible con Windows XP o Windows Server 2003, puede establecer temporalmente el conjunto de herramientas de plataforma predeterminado como destino para realizar el análisis, y luego volver al conjunto de herramientas de la plataforma Windows XP para compilar la aplicación.

- **Depuración de gráficos de DirectX**

   Como el depurador de gráficos no es compatible con la API de Direct3D 9, no puede usarse para depurar aplicaciones que usan Direct3D en Windows XP o Windows Server 2003. Sin embargo, si la aplicación implementa un representador alternativo que usa las API de Direct3D 10 o Direct3D 11, el depurador de gráficos puede utilizarse para diagnosticar problemas en el uso de estas API.

- **Compilación de HLSL**

   De forma predeterminada, el conjunto de herramientas de Windows XP no compila los archivos de código fuente HLSL. Para compilar estos archivos, descargue e instale el SDK de DirectX de junio de 2010 y configure los directorios VC del proyecto para que lo incluyan. Para más información, vea la sección "DirectX SDK Does Not Register Include/Library Paths with Visual Studio 2010" (DirectX SDK no registra rutas Include/Library con Visual Studio 2010) de la [página de descarga de DirectX SDK de junio de 2010](http://www.microsoft.com/download/details.aspx?displaylang=en&id=6812).
