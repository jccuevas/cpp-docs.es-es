---
title: Configuración de programas para Windows XP
ms.date: 02/02/2018
ms.assetid: 1e4487b3-d815-4123-878b-5718b22f0fd5
ms.openlocfilehash: 73fc66c358f2bfa390177557da2f114f225cec1a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50582747"
---
# <a name="configuring-programs-for-windows-xp"></a>Configuración de programas para Windows XP

Dado que Visual Studio admite varios conjuntos de herramientas de plataforma, puede dirigirse a los sistemas operativos y las bibliotecas en tiempo de ejecución que no son compatibles con el conjunto de herramientas predeterminada. Por ejemplo, al cambiar el conjunto de herramientas de plataforma, puede usar C ++ 11, C ++ 14 y mejoras del lenguaje C ++ 17 admitidas por el compilador de Visual C++ en Visual Studio para crear aplicaciones que tienen como destino Windows XP y Windows Server 2003. Puede también usar conjuntos de herramientas de plataforma anteriores para mantener la compatibilidad binaria de código heredado y seguir aprovechando las características más recientes del IDE de Visual Studio.

## <a name="install-the-windows-xp-platform-toolset"></a>Instalar el conjunto de herramientas de la plataforma Windows XP

Para obtener el conjunto de herramientas de plataforma y los componentes de destino Windows XP y Windows Server 2003 en Visual Studio 2017, ejecute al instalador de Visual Studio. Instalación inicial de Visual Studio o cuando se elige **modificar** para modificar una instalación existente, asegúrese de que el **desarrollo de escritorio con C++** está activada la carga de trabajo. En la lista de componentes opcionales para esta carga de trabajo, elija **soporte técnico de Windows XP para C++** y, a continuación, elija **instalar** o **modificar**.

## <a name="windows-xp-targeting-experience"></a>Experiencia con Windows XP como destino

El conjunto de herramientas de la plataforma de Windows XP que se incluye en Visual Studio es una versión del SDK de Windows 7, pero usa el compilador de C++ actual. También configura las propiedades del proyecto para los valores predeterminados adecuados, por ejemplo, la especificación de un vinculador compatible para destinos de nivel inferior. Sólo Windows aplicaciones de escritorio que se crean mediante el uso de un conjunto de herramientas de plataforma de Windows XP ejecutan en Windows XP y Windows Server 2003, pero esas aplicaciones, también pueden ejecutar en sistemas operativos de Windows más recientes.

#### <a name="to-target-windows-xp"></a>Establecer Windows XP como destino

1. En el **Explorador de soluciones**, abra el menú contextual del proyecto y después elija **Propiedades**.

1. En el **páginas de propiedades** cuadro de diálogo para el proyecto, en **propiedades de configuración** > **General**, establezca el **delconjuntodeherramientasdeplataforma** propiedad para el conjunto de herramientas de Windows XP deseado. Por ejemplo, elija **Visual Studio 2017: Windows XP (v141_xp)** para crear código para Windows XP y Windows Server 2003 mediante el compilador de Microsoft Visual C++ 2017.

### <a name="c-runtime-support"></a>Compatibilidad con el motor en tiempo de ejecución de C++

Junto con el conjunto de herramientas de la plataforma Windows XP, la biblioteca en tiempo de ejecución de C (CRT), biblioteca estándar de C++, Active Template Library (ATL), biblioteca de Runtime de simultaneidad (ConCRT), Parallel Patterns Library (PPL), Foundation clase biblioteca MFC (Microsoft) y C++ AMP (C++ Aceleradas programación masivo) biblioteca incluyen compatibilidad en tiempo de ejecución para Windows XP y Windows Server 2003. Para estos sistemas operativos, las versiones mínimas admitidas son Windows XP Service Pack 3 (SP3) para x86, Windows XP Service Pack 2 (SP2) para x64 y Windows Server 2003 Service Pack 2 (SP2) para x86 y x64.

Estas bibliotecas son compatibles con los conjuntos de herramientas de plataforma instalados por Visual Studio, dependiendo del destino:

|Biblioteca|Conjunto de herramientas de plataforma predeterminado dirigido a aplicaciones de escritorio de Windows|Destinatarios Store aplicaciones de conjunto de herramientas de plataforma de forma predeterminada|Conjunto de herramientas de plataforma de Windows XP como destino Windows XP, Windows Server 2003|
|---|---|---|---|
|CRT|X|X|X|
|Biblioteca estándar de C++|X|X|X|
|ATL|X|X|X|
|ConCRT/PPL|X|X|X|
|MFC|X||X|
|C++ AMP|X|X||

> [!NOTE]
> Las aplicaciones escritas en C++ / c++ / CLI y dirigidas a .NET Framework 4 se ejecutan en Windows XP y Windows Server 2003.

### <a name="differences-between-the-toolsets"></a>Diferencias entre los conjuntos de herramientas

Debido a diferencias en la compatibilidad de plataformas y bibliotecas, la experiencia de desarrollo para aplicaciones que usan un conjunto de herramientas de la plataforma Windows XP no es tan completa como para las aplicaciones que usan el conjunto de herramientas de plataforma de Visual Studio de forma predeterminada.

- **Características del lenguaje C++**

   Solo características del lenguaje C++ implementadas en Visual Studio 2012 se admiten en las aplicaciones que usan el v110\_xp conjunto de herramientas de plataforma. Solo características del lenguaje C++ implementadas en Visual Studio 2013 se admiten en las aplicaciones que usan el v120\_xp conjunto de herramientas de plataforma. Solo características del lenguaje C++ implementadas en Visual Studio 2015 se admiten en las aplicaciones que usan el v140\_xp conjunto de herramientas de plataforma. Visual Studio usa el compilador correspondiente al compilar con los conjuntos de herramientas de plataforma anteriores. Utilice el conjunto de herramientas de plataforma más reciente de Windows XP para aprovechar las características del lenguaje C++ implementadas en esa versión del compilador adicionales.

- **Depuración remota**

   Herramientas remotas para Visual Studio no admite la depuración remota en Windows XP o Windows Server 2003. Para depurar una aplicación cuando se ejecuta en Windows XP o Windows Server 2003, puede usar a un depurador desde una versión anterior de Visual Studio para depurarlo de forma local o remota. Es una experiencia similar a la depuración de una aplicación en Windows Vista, que es un destino de tiempo de ejecución del conjunto de herramientas de plataforma, pero no un destino de depuración remoto.

- **Análisis estático**

   Los conjuntos de herramientas de la plataforma Windows XP no admiten el análisis estático porque las anotaciones SAL para el SDK de Windows 7 y las bibliotecas en tiempo de ejecución no son compatibles. Cuando desea realizar un análisis estático en una aplicación compatible con Windows XP o Windows Server 2003, puede cambiar temporalmente la solución para el conjunto de herramientas de plataforma predeterminado para realizar el análisis de destino y vuelva a que el conjunto de herramientas de plataforma de Windows XP para compilar la aplicación.

- **Depuración de gráficos de DirectX**

   Dado que el depurador de gráficos no es compatible con la API de Direct3D 9, no se puede usar para depurar aplicaciones que usan Direct3D en Windows XP o Windows Server 2003. Sin embargo, si la aplicación implementa un representador alternativo que usa las API de Direct3D 10 o Direct3D 11, el depurador de gráficos puede utilizarse para diagnosticar problemas en el uso de estas API.

- **Compilación de HLSL**

   De forma predeterminada, el conjunto de herramientas de Windows XP no compila los archivos de código fuente HLSL. Para compilar estos archivos, descargue e instale el SDK de DirectX de junio de 2010 y configure los directorios VC del proyecto para que lo incluyan. Para obtener más información, consulte la "SDK de DirectX no registra rutas de acceso de inclusión/biblioteca con Visual Studio 2010" sección de la [junio de 2010 página de descarga del SDK de DirectX](http://www.microsoft.com/download/details.aspx?displaylang=en&id=6812).
