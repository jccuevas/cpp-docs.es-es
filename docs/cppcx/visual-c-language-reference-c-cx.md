---
title: "Referencia del lenguaje Visual C++ (C++-CX) | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3f6abf92-4e5e-4ed8-8e11-f9252380d30a
caps.latest.revision: 27
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 27
---
# Referencia del lenguaje Visual C++ (C++-CX)
[!INCLUDE[cppwrt](../cppcx/includes/cppwrt-md.md)] \([!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)]\) es un conjunto de extensiones del lenguaje C\+\+ que permite la creación de aplicaciones de Windows y componentes de [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] en un idioma lo más próximo posible al lenguaje C\+\+ moderno. Use [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] para escribir aplicaciones y componentes de Windows en código nativo que interactúen fácilmente con Visual C\#, Visual Basic y JavaScript, y otros lenguajes que admitan [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]. En los pocos casos en que se necesite acceso directo a las interfaces COM sin procesar, o a código no excepcional, puedes usar [Biblioteca de plantillas de Windows Runtime C\+\+ \(WRL\)](../Topic/Windows%20Runtime%20C++%20Template%20Library%20\(WRL\).md).  
  
 El nuevo modelo representa la siguiente generación de programación de C\+\+ nativo en Windows. Mediante su uso, puedes crear:  
  
-   Aplicaciones de Windows en C\+\+ que usan XAML para definir la interfaz de usuario y la pila nativa. Para obtener más información, vea [Create a "hello world" app in C\+\+ \(Windows 10\)](http://msdn.microsoft.com/library/windows/apps/dn996906.aspx) \[Crear una aplicación "hola a todos" en C\+\+ \(Windows 10\)\].  
  
-   Componentes de [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] en C\+\+ que pueden utilizarse en aplicaciones de Windows basadas en JavaScript. Para obtener más información, vea [Crear componentes de Windows en tiempo de ejecución en C\+\+](http://msdn.microsoft.com/library/hh441569.aspx)[Crear componentes de Windows en tiempo de ejecución en C\+\+](../Topic/Creating%20Windows%20Runtime%20Components%20in%20C++.md).  
  
-   Aplicaciones con numerosos gráficos y juegos DirectX de Windows. Para obtener más información, vea [Crear un juego de Plataforma universal de Windows \(UWP\) simple con DirectX](http://msdn.microsoft.com/library/windows/apps/xaml/mt210793.aspx).  
  
## Artículos relacionados  
  
|||  
|-|-|  
|[Referencia rápida](../cppcx/quick-reference-c-cx.md)|Tabla de palabras clave y operadores para [!INCLUDE[cppwrt](../cppcx/includes/cppwrt-md.md)] \([!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)]\).|  
|[Sistema de tipos](../cppcx/type-system-c-cx.md)|Describe los tipos básicos de [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] y las construcciones de programación, así como la forma de utilizar [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] para utilizar y crear tipos de [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)].|  
|[Compilar aplicaciones y bibliotecas](../cppcx/building-apps-and-libraries-c-cx.md)|Explica cómo utilizar el IDE para compilar aplicaciones y vincular a bibliotecas estáticas y archivos DLL.|  
|[Interoperar con otros lenguajes](../cppcx/interoperating-with-other-languages-c-cx.md)|Explica cómo los componentes que se escriben [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] se pueden usar con los componentes que se escriben en JavaScript, cualquier lenguaje administrado o [!INCLUDE[cppwrl](../cppcx/includes/cppwrl-md.md)].|  
|[Subprocesamiento y cálculo de referencias](../cppcx/threading-and-marshaling-c-cx.md)|Describe cómo especificar el comportamiento de subprocesamiento y cálculo de referencias de los componentes que crees.|  
|[Referencia de espacios de nombres](../cppcx/namespaces-reference-c-cx.md)|Hace referencia a documentación para el espacio de nombres predeterminado, el espacio de nombres Platform, Platform::Collections y los espacios de nombres relacionados.|  
|[Funciones de CRT no admitidas en aplicaciones de la Plataforma universal de Windows](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)|Enumera las funciones de CRT que no se pueden usar en aplicaciones de Windows Runtime.|  
|[Guías de procedimientos para las aplicaciones de Windows 10](http://msdn.microsoft.com/library/windows/apps/xaml/mt244352.aspx)|Proporcionan orientación de alto nivel sobre las aplicaciones de Windows 10 y vínculos a más información.|  
  
1.  [C\+\+\/CX Part 0 of \[n\]: An Introduction \(C\+\+\/CX Parte 0 de \[n\]: introducción\)](http://blogs.msdn.com/b/vcblog/archive/2012/08/29/cxxcxpart00anintroduction.aspx)  
  
2.  [C\+\+\/CX Part 0 of \[n\]: An Introduction \(C\+\+\/CX Parte 0 de \[n\]: introducción\)](http://blogs.msdn.com/b/vcblog/archive/2012/08/29/cxxcxpart00anintroduction.aspx)  
  
3.  [C\+\+\/CX Part 2 of \[n\]: Types That Wear Hats \(C\+\+\/CX Parte 2 de \[n\]: tipos que llevan sombreros\)](http://blogs.msdn.com/b/vcblog/archive/2012/09/17/cxxcxpart02typesthatwearhats.aspx)  
  
4.  [C\+\+\/CX Part 3 of \[n\]: Under Construction \(C\+\+\/CX Parte 3 de \[n\]: en construcción\)](http://blogs.msdn.com/b/vcblog/archive/2012/10/05/cxxcxpart03underconstruction.aspx)  
  
5.  [C\+\+\/CX Part 4 of \[n\]: Static Member Functions \(C\+\+\/CX Parte 4 de \[n\]: funciones miembro estáticas\)](http://blogs.msdn.com/b/vcblog/archive/2012/10/19/cxxcxpart04staticmemberfunctions.aspx)