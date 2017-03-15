---
title: Plataformas compatibles (Visual C++) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- Visual C++, platforms supported
- platforms [C++]
ms.assetid: 0d893056-4008-411a-b3d1-5f57fd7da95c
caps.latest.revision: 22
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 0192e9bd6ef9d93e274c43c24137a27e5aa53dab
ms.openlocfilehash: c0c209c16ad4a264b851321a2879104112da81f2
ms.lasthandoff: 02/24/2017

---
# <a name="supported-platforms-visual-c"></a>Plataformas compatibles (Visual C++)
Las aplicaciones compiladas con [!INCLUDE[vsprvs](assembler/masm/includes/vsprvs_md.md)] pueden tener como destino distintas plataformas, tal y como se indica a continuación.  
  
|Sistema operativo|x86|x64|ARM|  
|----------------------|---------|---------|---------|  
|Windows XP|X*|X*||  
|[!INCLUDE[WinXPSvr](build/includes/winxpsvr_md.md)]|X*|X*||  
|Windows Vista|X|X||  
|Windows Server 2008|X|X||  
|Windows 7|X|X||  
|Windows Server 2012 R2|X|X||  
|Windows 8|X|X|X|  
|Windows 8.1|X|X|X|  
|Windows 10 |X|X|X|  
|Android**|X|X|X|  
|iOS**|X|X|x|  
  
 \* Para la compilación de proyectos de Windows XP y [!INCLUDE[WinXPSvr](build/includes/winxpsvr_md.md)], puede usar el conjunto de herramientas de la plataforma Windows XP incluido en Visual Studio 2015, Visual Studio 2013 y Visual Studio 2012 Update 1 o posterior. Para más información sobre cómo usar este conjunto de herramientas de la plataforma, vea [Configurar&11; programas de C++ para Windows XP](build/configuring-programs-for-windows-xp.md). Para más información sobre cómo cambiar el conjunto de herramientas de la plataforma, vea [Cómo: Modificar versión de .NET Framework de destino y el conjunto de herramientas de la plataforma](build/how-to-modify-the-target-framework-and-platform-toolset.md).  
  
 **Si desea compilar para las plataformas iOS o Android, instale el componente opcional de Visual C++ para el desarrollo móvil multiplataforma que se incluye en el programa de instalación de Visual Studio 2015. Para obtener instrucciones, vea [Instalar Visual C++ para el desarrollo móvil multiplataforma](/visualstudio/cross-platform/install-visual-cpp-for-cross-platform-mobile-development). Para compilar código de iOS, debe tener un equipo Mac y además cumplir otros requisitos. Para obtener una lista de los requisitos previos e instrucciones de instalación, vea [Instalar y configurar herramientas para compilar con iOS](/visualstudio/cross-platform/install-and-configure-tools-to-build-using-ios). Puede compilar código ARM o x86 para que coincida con el hardware de destino. Use configuraciones x86 en compilaciones para el simulador de iOS, el emulador de Microsoft Visual Studio para Android y algunos dispositivos Android. Use configuraciones de ARM en compilaciones para dispositivos iOS y la mayoría de los dispositivos Android.  
  
 Para más información sobre cómo configurar la plataforma de destino, vea [Cómo: Configurar proyectos de Visual C++ en plataformas de 64 bits de destino](build/how-to-configure-visual-cpp-projects-to-target-64-bit-platforms.md).  
  
## <a name="see-also"></a>Vea también  
 [Visual C++ Tools and Features in Visual Studio Editions (Herramientas y características de Visual C++ en las ediciones de Visual Studio)](ide/visual-cpp-tools-and-features-in-visual-studio-editions.md)   
 [Introducción](/visualstudio/ide/getting-started-with-visual-cpp-in-visual-studio)
