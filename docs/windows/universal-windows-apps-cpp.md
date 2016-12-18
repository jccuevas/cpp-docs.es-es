---
title: "Aplicaciones Windows universales (C++) | Microsoft Docs"
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
ms.assetid: 357121cc-d390-4bae-b34a-39614861a9f4
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Aplicaciones Windows universales (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las aplicaciones de la Plataforma universal de Windows \(UWP\) representan un conjunto de principios de diseño que se centra en crear interfaces de usuario sencillas en torno a un contenido que se ajusta automáticamente a los diferentes tamaños de pantalla de los diversos dispositivos. La interfaz de usuario se crea en el marcado XAML y el código subyacente en C\+\+ nativo. También puede crear componentes \(archivos DLL\) que las aplicaciones para UWP escritas en otros lenguajes pueden consumir. La superficie de la API de las aplicaciones para UWP es [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)], que es una biblioteca factorizada correctamente que proporciona una gran variedad de servicios del sistema operativo.  
  
> [!NOTE]
>  Gran parte de la documentación para el desarrollo de aplicaciones para UWP en C\+\+ se encuentra en el sitio web del [Centro de desarrollo de Windows](http://go.microsoft.com/fwlink/p/?LinkId=255563). Algunos de los vínculos de este artículo van a ese sitio web.  
  
## Aplicaciones para UWP que usan C\+\+\/CX  
  
|||  
|-|-|  
|[Referencia del lenguaje Visual C\+\+ \(C\+\+\/CX\)](http://go.microsoft.com/fwlink/p/?LinkId=255561)|Describe el conjunto de extensiones que simplifican el uso en C\+\+ de las API de [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] y habilitan el control de errores basado en excepciones.|  
|[Compilar aplicaciones y bibliotecas \(C\+\+\/CX\)](http://go.microsoft.com/fwlink/p/?LinkId=264858)|Describe cómo crear bibliotecas DLL y estáticas a las que se puede tener acceso desde una aplicación o componente de C\+\+\/CX.|  
|[Tutorial: crear la primera aplicación de Tienda Windows con C\+\+](http://go.microsoft.com/fwlink/p/?LinkId=255556)|Un tutorial que presenta los conceptos básicos de desarrollo de aplicaciones de la [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] en C\+\+. \(Aún no se ha actualizado para el desarrollo de UWP en Windows 10\).|  
|[Guía básica para aplicaciones de la Tienda Windows con C\+\+](http://go.microsoft.com/fwlink/p/?LinkId=255553)|Proporciona vínculos a artículos sobre el desarrollo de aplicaciones y juegos de la [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] en C\+\+.|  
|[Crear componentes de Windows en tiempo de ejecución en C\+\+](http://go.microsoft.com/fwlink/p/?LinkId=255559)|Describe cómo crear bibliotecas DLL que otras aplicaciones y componentes de la [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] pueden utilizar.|  
|[Desarrollar juegos](http://go.microsoft.com/fwlink/p/?LinkId=255554)|Describe cómo utilizar DirectX y C\+\+ para crear juegos.|  
  
## Aplicaciones de la [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] que utilizan [!INCLUDE[cppwrl](../windows/includes/cppwrl_md.md)] \([!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)]\)  
 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] proporciona interfaces COM de bajo nivel por las que el código ISO C\+\+ puede tener acceso a [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] en un entorno sin excepciones. En la mayoría de los casos, recomendamos utilizar C\+\+\/CX en lugar de [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] para el desarrollo de aplicaciones de la [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)]. Para obtener más información sobre [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)], vea [Biblioteca de plantillas de Windows Runtime C\+\+ \(WRL\)](../Topic/Windows%20Runtime%20C++%20Template%20Library%20\(WRL\).md).  
  
## Vea también  
 [Visual C\+\+](../top/visual-cpp-in-visual-studio-2015.md)