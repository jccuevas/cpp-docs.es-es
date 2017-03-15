---
title: "Plataformas compatibles (Visual C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "plataformas [C++]"
  - "Visual C++, plataformas compatibles"
ms.assetid: 0d893056-4008-411a-b3d1-5f57fd7da95c
caps.latest.revision: 22
caps.handback.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Plataformas compatibles (Visual C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las aplicaciones compiladas con [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] pueden tener como destino distintas plataformas, tal y como se indica a continuación.  
  
|Sistema operativo|x86|x64|ARM|  
|-----------------------|---------|---------|---------|  
|Windows XP|X\*|X\*||  
|[!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)]|X\*|X\*||  
|Windows Vista|X|X||  
|Windows Server 2008|X|X||  
|Windows 7|X|X||  
|Windows Server 2012 R2|X|X||  
|Windows 8|X|X|X|  
|Windows 8.1|X|X|X|  
|Windows 10|X|X|X|  
|Android\*\*|X|X|X|  
|iOS\*\*|X|X|X|  
  
 \*Para la compilación de proyectos de Windows XP y [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)], puede usar el conjunto de herramientas de la plataforma de Windows XP que viene incluida en Visual Studio 2015, Visual Studio 2013 y Visual Studio 2012 Update 1 o posterior.  Para obtener más información sobre cómo usar este conjunto de herramientas de plataforma, vea el tema sobre [Configurar 11 programas de C\+\+ para Windows XP](../build/configuring-programs-for-windows-xp.md).  Para más información sobre cómo cambiar el conjunto de herramientas de la plataforma, vea [Cómo: Modificar versión de .NET Framework de destino y el conjunto de herramientas de la plataforma](../build/how-to-modify-the-target-framework-and-platform-toolset.md).  
  
 \*\*Si desea compilar para las plataformas iOS o Android, instale el componente opcional de Visual C\+\+ para el desarrollo móvil multiplataforma que se incluye en el programa de instalación de Visual Studio 2015.  Para obtener instrucciones, vea el tema sobre [Instalar Visual C\+\+ para el desarrollo móvil multiplataforma](../Topic/Install%20Visual%20C++%20for%20Cross-Platform%20Mobile%20Development.md).  Para compilar código de iOS, debe tener un equipo Mac y además cumplir otros requisitos.  Para ver una lista de los requisitos previos e instrucciones de instalación, vea el tema sobre [Instalar y configurar herramientas para compilar con iOS](../Topic/Install%20And%20Configure%20Tools%20to%20Build%20using%20iOS.md).  Puede compilar código ARM o x86 para que coincida con el hardware de destino.  Use configuraciones x86 en compilaciones para el simulador de iOS, el emulador de Microsoft Visual Studio para Android y algunos dispositivos Android.  Use configuraciones de ARM en compilaciones para dispositivos iOS y la mayoría de los dispositivos Android.  
  
 Si quiere saber más sobre cómo configurar la plataforma de destino, vea [Cómo: Configurar proyectos de Visual C\+\+ en plataformas de 64 bits de destino](../build/how-to-configure-visual-cpp-projects-to-target-64-bit-platforms.md).  
  
## Vea también  
 [Herramientas y plantillas de Visual C\+\+ en las versiones de Visual Studio](../ide/visual-cpp-tools-and-templates-in-visual-studio-editions.md)   
 [Introducción](../misc/getting-started-with-visual-cpp-in-visual-studio-2015.md)