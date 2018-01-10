---
title: Configurar programas para Windows XP | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 1e4487b3-d815-4123-878b-5718b22f0fd5
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ff80109c1f3a5e03ecb85406cdaea24804f96783
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/03/2018
---
# <a name="configuring-programs-for-windows-xp"></a>Configurar programas para Windows XP
Dado que Visual Studio admite varios conjuntos de herramientas de plataforma, puede tener como destino los sistemas operativos y las bibliotecas en tiempo de ejecución que no son compatibles con el conjunto de herramientas de forma predeterminada. Por ejemplo, al cambiar el conjunto de herramientas de plataforma, puede usar la C ++ 11, C ++ 14 y mejoras de lenguaje C ++ 17 admitidas por el compilador de Visual C++ en Visual Studio para crear aplicaciones que tienen como destino [!INCLUDE[winxp](../build/includes/winxp_md.md)] y [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)]. Puede usar conjuntos de herramientas de plataforma anteriores para mantener la compatibilidad binaria del código heredado y seguir aprovechando las características más recientes del IDE de Visual Studio.  
  
> [!NOTE]
>  Si utilizas [!INCLUDE[vs_dev11_long](../build/includes/vs_dev11_long_md.md)], debe instalar [!INCLUDE[vs_dev11_long](../build/includes/vs_dev11_long_md.md)] Update 4 para agregar compatibilidad de conjunto de herramientas de plataforma para [!INCLUDE[winxp](../build/includes/winxp_md.md)] y [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)]. Para descargar e instalar una copia de [!INCLUDE[vs_dev11_long](../build/includes/vs_dev11_long_md.md)] Update 4, vea [Microsoft Visual Studio Express 2012 para escritorio de Windows](http://go.microsoft.com/fwlink/p/?linkid=265464) en Microsoft Download Center. A continuación, instale [Visual Studio 2012 Update 4](http://go.microsoft.com/fwlink/p/?linkid=335900) para obtener el conjunto de herramientas de la plataforma v110_xp. Use Windows Update para recibir las últimas actualizaciones de software después de la instalación.  
  
## <a name="windows-xp-targeting-experience"></a>Experiencia con Windows XP como destino  
 El conjunto de herramientas de la plataforma de Windows XP que se incluye en Visual Studio es una versión de la [!INCLUDE[win7](../build/includes/win7_md.md)] SDK que se incluía en [!INCLUDE[vs_dev10_long](../build/includes/vs_dev10_long_md.md)], pero usa el compilador de C++ actual. También establece valores predeterminados adecuados para las propiedades del proyecto, por ejemplo, la especificación de un vinculador compatible para destinos de nivel inferior. Solo se ejecutan aplicaciones de escritorio que se crean mediante el conjunto de herramientas de la plataforma Windows XP en Windows [!INCLUDE[winxp](../build/includes/winxp_md.md)] y [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)], pero estas aplicaciones también pueden ejecutarse en sistemas operativos de Windows más recientes.  
  
#### <a name="to-target-windows-xp"></a>Establecer Windows XP como destino  
  
1.  En el **Explorador de soluciones**, abra el menú contextual del proyecto y después elija **Propiedades**.  
  
2.  En el **páginas de propiedades** cuadro de diálogo para el proyecto, en **propiedades de configuración**, **General**, establezca el **conjunto de herramientas de plataforma** propiedad de conjunto de herramientas de Windows XP deseado. Por ejemplo, elegir **Visual Studio 2015: Windows XP (v140_xp)** para crear código para [!INCLUDE[winxp](../build/includes/winxp_md.md)] y [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)] mediante el compilador de Microsoft Visual C++ 2015.  
  
### <a name="c-runtime-support"></a>Compatibilidad con el motor en tiempo de ejecución de C++  
 Junto con el conjunto de herramientas de la plataforma Windows XP, la biblioteca de tiempo de ejecución de C (CRT), biblioteca estándar de C++, Active Template Library (ATL), biblioteca de Runtime de simultaneidad (ConCRT), Parallel Patterns Library (PPL), Foundation clase biblioteca MFC (Microsoft) y C++ AMP (C++ Accelerated Massive programación) biblioteca incluyen compatibilidad en tiempo de ejecución con [!INCLUDE[winxp](../build/includes/winxp_md.md)] y [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)]. Para estos sistemas operativos, las versiones mínimas admitidas son [!INCLUDE[winxp](../build/includes/winxp_md.md)] Service Pack 3 (SP3) para x86, [!INCLUDE[winxp](../build/includes/winxp_md.md)] Service Pack 2 (SP2) para x64, y [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)] Service Pack 2 (SP2) para x x86 y x64.  
  
 Estas bibliotecas son compatibles con los conjuntos de herramientas de plataforma que instala Visual Studio, dependiendo del destino:  
  
|Biblioteca|Conjunto de herramientas de plataforma predeterminado dirigido a aplicaciones de escritorio de Windows|Conjunto de herramientas de plataforma predeterminado dirigido a aplicaciones de [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)]|Conjunto de herramientas de la plataforma Windows XP dirigido a [!INCLUDE[winxp](../build/includes/winxp_md.md)] y [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)]|  
|-------------|-------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------|  
|CRT|X|X|X|  
|Biblioteca estándar de C++|X|X|X|  
|ATL|X|X|X|  
|ConCRT/PPL|X|X|X|  
|MFC|X||X|  
|C++ AMP|X|X||  
  
> [!NOTE]
>  Las aplicaciones escritas en C++/CLI y dirigidas a .NET Framework 4 se ejecutan en [!INCLUDE[winxp](../build/includes/winxp_md.md)] y [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)].  
  
### <a name="differences-between-the-toolsets"></a>Diferencias entre los conjuntos de herramientas  
 Debido a diferencias en la compatibilidad de plataformas y bibliotecas, la experiencia de desarrollo para aplicaciones que usan un conjunto de herramientas de la plataforma Windows XP no es tan completa como para aplicaciones que usan el conjunto de herramientas de plataforma de Visual Studio de forma predeterminada.  
  
-   **Características del lenguaje C++**  
  
     Características del lenguaje C++ solo se implementan en [!INCLUDE[vs_dev11_long](../build/includes/vs_dev11_long_md.md)] se admiten en aplicaciones que utilizan el conjunto de herramientas de la plataforma v110_xp. Características del lenguaje C++ solo se implementan en [!INCLUDE[vs_dev12](../atl-mfc-shared/includes/vs_dev12_md.md)] se admiten en aplicaciones que utilizan el conjunto de herramientas de la plataforma v120_xp. Visual Studio usa el compilador correspondiente al compilar con los conjuntos de herramientas de plataforma anteriores. Use el conjunto de herramientas de plataforma de Windows XP más reciente para aprovechar las características adicionales de lenguaje C++ implementadas en esa versión del compilador.  
  
-   **Depuración remota**  
  
     Herramientas remotas para Visual Studio no admite la depuración remota en [!INCLUDE[winxp](../build/includes/winxp_md.md)] o [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)]. Para depurar una aplicación cuando se está ejecutando en [!INCLUDE[winxp](../build/includes/winxp_md.md)] o [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)], puede usar un depurador desde una versión anterior de Visual Studio para depurar de forma local o remota. Es una experiencia similar a la depuración de una aplicación en Windows Vista, que es un destino de tiempo de ejecución del conjunto de herramientas de plataforma, pero no un destino de depuración remoto.  
  
-   **Análisis estático**  
  
     Los conjuntos de herramientas de la plataforma Windows XP no admiten el análisis estático porque las anotaciones SAL del [!INCLUDE[win7](../build/includes/win7_md.md)] SDK y las bibliotecas en tiempo de ejecución son incompatibles. Cuando quiera realizar un análisis estático en una aplicación compatible con [!INCLUDE[winxp](../build/includes/winxp_md.md)] o [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)], puede establecer temporalmente el conjunto de herramientas de plataforma predeterminado como destino para realizar el análisis, y luego volver al conjunto de herramientas de la plataforma Windows XP para compilar la aplicación.  
  
-   **Depuración de gráficos de DirectX**  
  
     Como el depurador de gráficos no es compatible con la API de Direct3D 9, no puede utilizarse para depurar aplicaciones que usan Direct3D en [!INCLUDE[winxp](../build/includes/winxp_md.md)] o [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)]. Sin embargo, si la aplicación implementa un representador alternativo que usa las API de Direct3D 10 o Direct3D 11, el depurador de gráficos puede utilizarse para diagnosticar problemas en el uso de estas API.  
  
-   **Compilación de HLSL**  
  
     De forma predeterminada, el conjunto de herramientas de Windows XP no compila los archivos de código fuente HLSL. Para compilar estos archivos, descargue e instale el SDK de DirectX de junio de 2010 y configure los directorios VC del proyecto para que lo incluyan. Para obtener más información, consulte la "SDK de DirectX no registra rutas de acceso de inclusión/biblioteca con Visual Studio 2010" sección de la [junio de 2010 página de descarga del SDK de DirectX](http://www.microsoft.com/download/details.aspx?displaylang=en&id=6812).