---
title: "Configurar 11 programas de C++ para Windows XP | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 1e4487b3-d815-4123-878b-5718b22f0fd5
caps.latest.revision: 14
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Configurar 11 programas de C++ para Windows XP
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Como [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] admite varios conjuntos de herramientas de plataforma, puede dirigirse a sistemas operativos y bibliotecas en tiempo de ejecución que no son compatibles con el conjunto de herramientas predeterminado.  Por ejemplo, puede utilizar las mejoras del lenguaje, compiladores, bibliotecas y otras características de C\+\+ 11 que se implementan en [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] para crear aplicaciones dirigidas a [!INCLUDE[winxp](../build/includes/winxp_md.md)] y [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)].  Puede utilizar conjuntos de herramientas de plataforma anteriores para mantener la compatibilidad binaria del código heredado y seguir aprovechando las características más recientes del IDE de [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)].  
  
> [!NOTE]
>  Debe instalar [!INCLUDE[vs_dev11_long](../build/includes/vs_dev11_long_md.md)] Update 4 para dotar a [!INCLUDE[winxp](../build/includes/winxp_md.md)] de compatibilidad con los conjuntos de herramientas de las plataformas [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)] y [!INCLUDE[vs_dev11_long](../build/includes/vs_dev11_long_md.md)].  Para descargar e instalar una copia de [!INCLUDE[vs_dev11_long](../build/includes/vs_dev11_long_md.md)] Update 4, vea [Microsoft Visual Studio Express 2012 para escritorio de Windows](http://go.microsoft.com/fwlink/?LinkID=265464) en el Centro de descarga de Microsoft.  Después, instale [Visual Studio 2012 Update 4](http://go.microsoft.com/fwlink/?LinkID=335900) para obtener el conjunto de herramientas de la plataforma v110\_xp.  Use Windows Update para recibir las últimas actualizaciones de software después de la instalación.  
  
## Experiencia con Windows XP como destino  
 El conjunto de herramientas de la plataforma Windows XP que se incluye en [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] es una versión del [!INCLUDE[win7](../build/includes/win7_md.md)] SDK incluido en [!INCLUDE[vs_dev10_long](../build/includes/vs_dev10_long_md.md)], pero usa el compilador de C\+\+ actual.  También establece valores predeterminados adecuados para las propiedades del proyecto, por ejemplo, la especificación de un vinculador compatible para destinos de nivel inferior.  En [!INCLUDE[winxp](../build/includes/winxp_md.md)] y [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)] solo pueden ejecutarse aplicaciones de escritorio de Windows creadas mediante el conjunto de herramientas de la plataforma Windows XP, pero estas aplicaciones también pueden ejecutarse en sistemas operativos más recientes, como Windows Vista, [!INCLUDE[win7](../build/includes/win7_md.md)], [!INCLUDE[winsvr08](../build/includes/winsvr08_md.md)], [!INCLUDE[win8](../build/includes/win8_md.md)] o [!INCLUDE[winserver8](../build/includes/winserver8_md.md)].  
  
#### Establecer Windows XP como destino  
  
1.  En el **Explorador de soluciones**, abra el menú contextual del proyecto y, a continuación, elija **Propiedades**.  
  
2.  En el cuadro de diálogo **Páginas de propiedades** del proyecto, en **Propiedades de configuración**, **General**, establezca la propiedad **Conjunto de herramientas de la plataforma** al conjunto de herramientas de Windows XP deseado.  Por ejemplo, elija **Visual Studio 2012: Windows XP \(v110\_xp\)** para crear código compatible a nivel binario con las bibliotecas de Microsoft Visual C\+\+ 2012 Redistributable.  
  
### Compatibilidad con el motor en tiempo de ejecución de C\+\+  
 Junto con el conjunto de herramientas de la plataforma Windows XP, la biblioteca en tiempo de ejecución de C \(CRT\), la biblioteca de plantillas estándar \(STL\), la Active Template Library \(ATL\), la biblioteca en tiempo de ejecución de simultaneidad \(ConCRT\), la Parallel Patterns Library \(PPL\), la biblioteca Microsoft Foundation Class \(MFC\) y la biblioteca de AMP de C\+\+ \(C\+\+ Accelerated Massive Programming\) incluyen compatibilidad en tiempo de ejecución para [!INCLUDE[winxp](../build/includes/winxp_md.md)] y [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)].  Para estos sistemas operativos, las versiones compatibles son [!INCLUDE[winxp](../build/includes/winxp_md.md)] Service Pack 3 \(SP3\) para x86, [!INCLUDE[winxp](../build/includes/winxp_md.md)] Service Pack 2 \(SP2\) para x64 y [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)] Service Pack 2 \(SP2\) para x86 y x64.  
  
 Estas bibliotecas son compatibles con los conjuntos de herramientas de plataforma instalados por [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)], en función del destino:  
  
|Biblioteca|Conjunto de herramientas de plataforma predeterminado dirigido a aplicaciones de escritorio de Windows|Conjunto de herramientas de plataforma predeterminado dirigido a aplicaciones de [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)]|Conjunto de herramientas de la plataforma Windows XP dirigido a [!INCLUDE[winxp](../build/includes/winxp_md.md)] y [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)]|  
|----------------|------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|CRT|X|X|X|  
|STL|X|X|X|  
|ATL|X|X|X|  
|ConCRT\/PPL|X|X|X|  
|MFC|X||X|  
|C\+\+ AMP|X|X||  
  
> [!NOTE]
>  Las aplicaciones escritas en C\+\+\/CLI y dirigidas a .NET Framework 4 se ejecutan en [!INCLUDE[winxp](../build/includes/winxp_md.md)] y [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)].  
  
### Diferencias entre los conjuntos de herramientas  
 Debido a diferencias de compatibilidad de plataformas y bibliotecas, la experiencia de desarrollo para aplicaciones que usan un conjunto de herramientas de la plataforma Windows XP no es tan completa como para las que usan el conjunto de herramientas de la plataforma [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] predeterminado.  
  
-   **Características del lenguaje C\+\+**  
  
     Solo las características del lenguaje C\+\+ 11 implementadas en [!INCLUDE[vs_dev11_long](../build/includes/vs_dev11_long_md.md)] se admiten en aplicaciones que utilizan el conjunto de herramientas de la plataforma v110\_xp.  Solo las características de C\+\+ 11 implementadas en [!INCLUDE[vs_dev12](../atl-mfc-shared/includes/vs_dev12_md.md)] se admiten en aplicaciones que utilizan el conjunto de herramientas de la plataforma v120\_xp.  [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] usa el compilador correspondiente al compilar con los conjuntos de herramientas de plataforma anteriores.  Use un conjunto de herramientas de la plataforma Windows XP más reciente para aprovechar las características adicionales de C\+\+ 11 implementadas en esa versión.  
  
-   **Depuración remota**  
  
     Herramientas remotas para [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] no admite la depuración remota en [!INCLUDE[winxp](../build/includes/winxp_md.md)] o [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)].  Una aplicación que se ejecuta en [!INCLUDE[winxp](../build/includes/winxp_md.md)] o [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)] puede depurarse de forma local o remota utilizando un depurador de una versión anterior de [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)].  Es una experiencia similar a la depuración de una aplicación en Windows Vista, que es un destino de tiempo de ejecución del conjunto de herramientas de plataforma, pero no un destino de depuración remoto.  
  
-   **Análisis estático**  
  
     Los conjuntos de herramientas de la plataforma Windows XP no admiten el análisis estático porque las anotaciones SAL del [!INCLUDE[win7](../build/includes/win7_md.md)] SDK y las bibliotecas en tiempo de ejecución son incompatibles.  Cuando quiera realizar un análisis estático en una aplicación compatible con [!INCLUDE[winxp](../build/includes/winxp_md.md)] o [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)], puede establecer temporalmente el conjunto de herramientas de plataforma predeterminado como destino para realizar el análisis, y luego volver al conjunto de herramientas de la plataforma Windows XP para compilar la aplicación.  
  
-   **Depuración de gráficos de DirectX**  
  
     Como el depurador de gráficos no es compatible con la API de Direct3D 9, no puede utilizarse para depurar aplicaciones que usan Direct3D en [!INCLUDE[winxp](../build/includes/winxp_md.md)] o [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)].  Sin embargo, si la aplicación implementa un representador alternativo que usa las API de Direct3D 10 o Direct3D 11, el depurador de gráficos puede utilizarse para diagnosticar problemas en el uso de estas API.  
  
-   **Compilación de HLSL**  
  
     De forma predeterminada, el conjunto de herramientas de Windows XP no compila los archivos de código fuente HLSL.  Para compilar estos archivos, descargue e instale el SDK de DirectX de junio de 2010 y configure los directorios VC del proyecto para que lo incluyan.  Para obtener más información, vea la sección “El SDK de DirectX no registra rutas de acceso de inclusión\/biblioteca con Visual Studio 2010” de la [página de descarga del SDK de DirectX de junio de 2010](http://www.microsoft.com/download/details.aspx?displaylang=en&id=6812).