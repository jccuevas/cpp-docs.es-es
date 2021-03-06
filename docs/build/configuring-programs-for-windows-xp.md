---
title: Configuración de programas para Windows XP
description: Cómo instalar y usar los conjuntos de herramientas de Windows XP de C++ en Visual Studio.
ms.date: 03/16/2020
ms.assetid: 1e4487b3-d815-4123-878b-5718b22f0fd5
ms.openlocfilehash: 92364d7fd25ac617baacc125b279fb0ee9c92f62
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440479"
---
# <a name="configuring-programs-for-windows-xp"></a>Configuración de programas para Windows XP

Visual Studio admite varios conjuntos de herramientas de plataforma. Esto significa que es posible establecer como destino sistemas operativos y bibliotecas en tiempo de ejecución que no son compatibles con el conjunto de herramientas predeterminado. Por ejemplo, al cambiar el conjunto de herramientas de plataforma, puede usar el compilador de C++ de Visual Studio 2017 para crear aplicaciones que tengan como destino Windows XP y Windows Server 2003. También pude usar conjuntos de herramientas de plataforma anteriores para mantener la compatibilidad binaria del código heredado y seguir aprovechando las características más recientes del IDE de Visual Studio.

::: moniker range="vs-2019"

El conjunto de herramientas v142 que proporciona Visual Studio 2019 no admite la creación de código para Windows XP. La compatibilidad con el desarrollo de Windows XP mediante el uso del conjunto de herramientas v141_xp de Visual Studio 2017 está disponible como componente opcional independiente en el Instalador de Visual Studio.

::: moniker-end

## <a name="install-the-windows-xp-platform-toolset"></a>Instalar el conjunto de herramientas de la plataforma Windows XP

::: moniker range="<=vs-2017"

Para obtener el conjunto de herramientas de plataforma de Visual Studio 2017 y los componentes para elegir como destino Windows XP y Windows Server 2003, ejecute el Instalador de Visual Studio. Cuando instale Visual Studio por primera vez o modifique una instalación existente, asegúrese de seleccionar la carga de trabajo **Desarrollo para el escritorio con C++** . En la lista de componentes opcionales para esta carga de trabajo, elija **Compatibilidad de Windows XP con C++** y, después, elija **Instalar** o **Modificar**.

::: moniker-end

::: moniker range="vs-2019"

Para obtener el conjunto de herramientas de plataforma v141_xp y los componentes para elegir como destino Windows XP y Windows Server 2003, ejecute el Instalador de Visual Studio. Cuando instale Visual Studio por primera vez o modifique una instalación existente, asegúrese de seleccionar la carga de trabajo **Desarrollo para el escritorio con C++** . En la pestaña **Componentes individuales**, en **Compiladores, herramientas de compilación y entornos de ejecución**, elija **Herramientas de compatibilidad de Windows XP con C++ para VS 2017 (v141) \[en desuso]** y seleccione **Instalar** o **Modificar**.

::: moniker-end

## <a name="windows-xp-targeting-experience"></a>Experiencia con Windows XP como destino

El conjunto de herramientas de la plataforma Windows XP que se incluye en Visual Studio es una versión de Windows SDK 7, pero usa el compilador de C++ de Visual Studio 2017. También configura propiedades del proyecto con los valores predeterminados adecuados, como por ejemplo, la especificación de un enlazador compatible para destinos de nivel inferior. Solo las aplicaciones de escritorio de Windows creadas mediante el uso de un conjunto de herramientas de la plataforma Windows XP se pueden ejecutar en Windows XP y Windows Server 2003. Estas aplicaciones también pueden ejecutarse en sistemas operativos Windows más recientes.

### <a name="to-target-windows-xp"></a>Establecer Windows XP como destino

1. En el **Explorador de soluciones**, abra el menú contextual del proyecto y después elija **Propiedades**.

1. En el cuadro de diálogo **Páginas de propiedades** del proyecto, seleccione **Propiedades de configuración** > **General**. Establezca la propiedad **Conjunto de herramientas de la plataforma** en el conjunto de herramientas de Windows XP que prefiera. Por ejemplo, elija **Visual Studio 2017 - Windows XP (v141_xp)** para crear código para Windows XP y Windows Server 2003 mediante el compilador de Microsoft C++ en Visual Studio 2017.

### <a name="c-runtime-support"></a>Compatibilidad con el motor en tiempo de ejecución de C++

Además del conjunto de herramientas de la plataforma Windows XP, varias bibliotecas incluyen compatibilidad con el runtime de Windows XP y Windows Server 2003. Se trata de la biblioteca en tiempo de ejecución de C (CRT), la biblioteca estándar de C++, la Active Template Library (ATL), la biblioteca de runtime de simultaneidad (ConCRT), la Parallel Patterns Library (PPL), la biblioteca MFC (Microsoft Foundation Class) y la biblioteca de AMP de C++ (C++ Accelerated Massive Programming). Para estos sistemas operativos, las versiones mínimas compatibles son las siguientes: Windows XP Service Pack 3 (SP3) para x86, Windows XP Service Pack 2 (SP2) para x64 y Windows Server 2003 Service Pack 2 (SP2) para x86 y x64.

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

Debido a diferencias de compatibilidad de plataformas y bibliotecas, la experiencia de desarrollo para aplicaciones que usan un conjunto de herramientas de la plataforma Windows XP no es tan completa como para las que usan el conjunto de herramientas de la plataforma Visual Studio predeterminado.

- **Características del lenguaje C++**

   Solo las características del lenguaje C++ implementadas en Visual Studio 2012 se admiten en aplicaciones que usan el conjunto de herramientas de la plataforma v110\_xp. Solo las características del lenguaje C++ implementadas en Visual Studio 2013 se admiten en aplicaciones que usan el conjunto de herramientas de la plataforma v120\_xp. Solo las características del lenguaje C++ implementadas en Visual Studio 2015 se admiten en aplicaciones que usan el conjunto de herramientas de la plataforma v140\_xp. Solo las características del lenguaje C++ implementadas en Visual Studio 2017 se admiten en aplicaciones que usan el conjunto de herramientas de la plataforma v141\_xp. Visual Studio usa el compilador correspondiente al compilar con los conjuntos de herramientas de plataforma anteriores. Use el conjunto de herramientas de la plataforma Windows XP más reciente para aprovechar las características adicionales del lenguaje C++ implementadas en esa versión del compilador.

- **Depuración remota**

   Herramientas remotas para Visual Studio no admite la depuración remota en Windows XP o Windows Server 2003. Para depurar una aplicación de manera local o remota en Windows XP o Windows Server 2003, use un depurador de una versión anterior de Visual Studio. Es una experiencia similar a la depuración de una aplicación en Windows Vista, que es un destino de tiempo de ejecución del conjunto de herramientas de plataforma, pero no un destino de depuración remoto.

- **Análisis estático**

   Los conjuntos de herramientas de la plataforma Windows XP no admiten el análisis estático porque las anotaciones SAL de Windows SDK 7 y las bibliotecas en tiempo de ejecución son incompatibles. Todavía puede realizar análisis estáticos en una aplicación compatible con Windows XP o Windows Server 2003. Cambie temporalmente la solución para establecer el conjunto de herramientas de plataforma predeterminado como destino para realizar el análisis y, luego, vuelva al conjunto de herramientas de la plataforma Windows XP para compilar la aplicación.

- **Depuración de gráficos de DirectX**

   Como el depurador de gráficos no es compatible con la API de Direct3D 9, no puede usarse para depurar aplicaciones que usan Direct3D en Windows XP o Windows Server 2003. Aun así, si la aplicación implementa un representador alternativo basado en las API de Direct3D 10 o Direct3D 11, puede usar el depurador de gráficos para diagnosticar problemas.

- **Compilación de HLSL**

   De forma predeterminada, el conjunto de herramientas de Windows XP no compila los archivos de código fuente HLSL. Para compilar estos archivos, descargue e instale el SDK de DirectX de junio de 2010 y configure los directorios VC del proyecto para que lo incluyan. Para más información, vea la sección "DirectX SDK Does Not Register Include/Library Paths with Visual Studio 2010" (DirectX SDK no registra rutas Include/Library con Visual Studio 2010) de la [página de descarga de DirectX SDK de junio de 2010](https://www.microsoft.com/download/details.aspx?displaylang=en&id=6812).
