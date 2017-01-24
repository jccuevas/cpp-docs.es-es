---
title: "Visual C++ en Visual Studio 2015 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "visual c++"
  - "visual c"
  - "vc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "código no administrado, C++"
  - "entorno de desarrollo, Visual C++"
  - "código no administrado"
  - "Visual C++"
  - "Visual C++, referencia"
ms.assetid: e8dcc44c-a3e2-4ffe-887c-fd15b18dc458
caps.latest.revision: 61
caps.handback.revision: 61
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Visual C++ en Visual Studio 2015
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El lenguaje de programación y las herramientas de desarrollo de [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] le ayudan a desarrollar aplicaciones universales de Windows nativas, aplicaciones de servidor y de escritorio nativas, bibliotecas multiplataforma que se ejecutan en iOS, Android y Windows, así como aplicaciones administradas que se ejecutan en .NET Framework.  
  
 **¿A quién está dirigida esta documentación?**  
  
 Este contenido es para desarrolladores de C\+\+ que escriben programas.  
  
-   Si busca un paquete redistribuible de C\+\+ y los componentes de tiempo de ejecución que le permitan ejecutar un programa, vaya al [Centro de descarga de Microsoft](http://www.microsoft.com/en-us/download/) y escriba **Visual C\+\+** en el cuadro de búsqueda.  
  
-   Si busca conceptos introductorios de programación de C\+\+, visite uno de los muchos sitios web que ofrecen este contenido o adquiera el libro [Programming \-\- Principles and Practice Using C\+\+ \(Second Edition\)](http://stroustrup.com/Programming/), escrito por el creador de C\+\+, Bjarne Stroustup. El contenido de Visual C\+\+ supone que ya tiene un conocimiento básico de C\+\+.  
  
-   Si busca el compilador de Visual C\+\+, debe descargar una edición de pago o gratuita de Visual Studio 2015 de [https:\/\/www.visualstudio.com\/](https://www.visualstudio.com/).  
  
> [!WARNING]
>  En Visual Studio 2015, Visual C\+\+ no se instala de forma predeterminada. Durante la instalación, asegúrese de elegir la instalación **Personalizada** y luego seleccione los componentes de C\+\+ que desee. En caso de que Visual Studio ya esté instalado, elija **Archivo &#124; Nuevo &#124; Proyecto &#124; C\+\+** y se le pedirá que instale los componentes necesarios.  
  
## Información general sobre Visual C\+\+  
 [Novedades de Visual C\+\+](../top/what-s-new-for-visual-cpp-in-visual-studio-2015.md)  
 Descubra las novedades de Visual C\+\+.  
  
 [Cambios importantes en Visual C\+\+ 2015](../porting/visual-cpp-change-history-2003-20151.md)  
 Obtenga información sobre los cambios importantes de esta versión.  
  
 [Aquí está otra vez C\+\+](../cpp/welcome-back-to-cpp-modern-cpp.md)  
 Obtenga más información sobre técnicas de programación modernas de C\+\+ basadas en C\+\+11 y C\+\+14 que le permiten escribir código seguro y rápido, y evite muchos de los problemas de programación de estilo C.  
  
 [How to Report a Problem with the Visual C\+\+ Toolset](../Topic/How%20to%20Report%20a%20Problem%20with%20the%20Visual%20C++%20Toolset.md)  
 Aprenda a crear informes de error eficaces en el conjunto de herramientas de Visual C\+\+ \(compilador, enlazador y otras herramientas\) y las formas de enviar el informe.  
  
 [Guía de migración y actualización de Visual C\+\+](../porting/visual-cpp-porting-and-upgrading-guide.md)  
 Guía para migrar el código y actualizar proyectos a Visual C\+\+ en [!INCLUDE[vs_dev14](../ide/includes/vs_dev14_md.md)], incluida la migración del código de C\+\+ a Windows 10 y a la Plataforma universal de Windows.  
  
 [Compatibilidad con las características de C\+\+11\/14\/17](../cpp/support-for-cpp11-14-17-features-modern-cpp.md)  
 Obtenga información sobre la compatibilidad con las características de C\+\+11 y C\+\+14 en Visual C\+\+.  
  
 [Blog del equipo de Visual C\+\+](http://blogs.msdn.com/b/vcblog/)  
 Obtenga más información acerca de las nuevas características y la información más reciente de los desarrolladores de [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)].  
  
 [Descargas de Visual Studio](http://go.microsoft.com/fwlink/?LinkId=235233)  
 Descargue Visual C\+\+.  
  
 [Herramientas y plantillas de Visual C\+\+ en las versiones de Visual Studio](../ide/visual-cpp-tools-and-templates-in-visual-studio-editions.md)  
 Obtenga información sobre diferentes ediciones de Visual Studio.  
  
 [Plataformas compatibles](../top/supported-platforms-visual-cpp.md)  
 Compruebe cuáles son las plataformas admitidas.  
  
 [Ejemplos de Visual C\+\+](../top/visual-cpp-samples.md)  
 Información acerca de los ejemplos.  
  
 [Comunidad de Visual Studio](http://go.microsoft.com/fwlink/?LinkId=235296)  
 Descubra cómo obtener ayuda, errores de archivo y hacer sugerencias para Visual Studio.  
  
## Escribir aplicaciones en C\+\+  
 [Aplicaciones Windows universales](../windows/universal-windows-apps-cpp.md)  
 Encuentre guías y contenido de referencia en el Centro de desarrollo de Windows. Para obtener información sobre el desarrollo de aplicaciones de la Tienda Windows, vea [Desarrollar aplicaciones de la Tienda Windows con Visual Studio](http://go.microsoft.com/fwlink/p/?LinkId=248364) y [Guía básica para crear aplicaciones de la Tienda Windows con C\+\+](http://go.microsoft.com/fwlink/p/?LinkId=244654).  
  
 [Aplicaciones de escritorio de Windows \(Visual C\+\+\)](../windows/desktop-applications-visual-cpp.md)  
 Obtenga información sobre cómo crear aplicaciones de escritorio que tienen un bucle de mensajes y devoluciones de llamada.  
  
 [Archivos DLL en Visual C\+\+](../build/dlls-in-visual-cpp.md)  
 Descubra cómo utilizar Win32, ATL y MFC para crear archivos DLL de escritorio de Windows, e información sobre cómo compilar y registrar un archivo DLL.  
  
 [Programación en paralelo](../parallel/parallel-programming-in-visual-cpp.md)  
 Obtenga información sobre el uso de la Biblioteca de patrones de procesamiento paralelo, C\+\+ AMP, OpenMP y otras características relacionadas con multithreading en Windows.  
  
 [Procedimientos recomendados](../top/security-best-practices-for-cpp.md)  
 Obtenga información sobre cómo proteger las aplicaciones del código malintencionado y el uso no autorizado.  
  
 [Programación web y para la nube](../Topic/Cloud%20and%20Web%20Programming%20in%20Visual%20C++.md)  
 En C\+\+, existen varias opciones para conectarse a la Web y a la nube.  
  
 [Acceso a datos en ASP.NET \(Visual Studio\)](../Topic/Data%20Access%20in%20Visual%20C++.md)  
 Conectarse a bases de datos mediante ODBC y otras tecnologías de acceso a bases de datos.  
  
 [Texto y cadenas](../text/text-and-strings-in-visual-cpp.md)  
 Obtenga información sobre cómo trabajar con diferentes codificaciones y formatos de texto y cadenas para el desarrollo local e internacional.  
  
## Herramientas de desarrollo de C\+\+  
 Si quiere saber más sobre cómo crear proyectos, trabajar con archivos de código fuente, vincular a bibliotecas, compilar, depurar, generar perfiles, implementar etc., vea [IDE y herramientas de desarrollo](../ide/ide-and-tools-for-visual-cpp-development.md).  
  
## Referencia del lenguaje C\+\+  
 Para obtener información sobre el lenguaje C\+\+, vea [Referencia de lenguaje C\+\+](../cpp/cpp-language-reference.md).  
  
 Para obtener información sobre el preprocesador de C\+\+, vea [Referencia del preprocesador de C\/C\+\+](../preprocessor/c-cpp-preprocessor-reference.md).  
  
## Bibliotecas de C\+\+ en Visual Studio  
 En las secciones siguientes se proporciona información sobre las distintas bibliotecas de C\+\+ que se incluyen en Visual C\+\+.  
  
 [Referencia de la biblioteca en tiempo de ejecución de C](../c-runtime-library/c-run-time-library-reference.md)  
 Incluye alternativas de seguridad mejoradas a las funciones que tienen problemas de seguridad conocidos.  
  
 [Biblioteca estándar de C\+\+](../standard-library/cpp-standard-library-reference.md)  
 La Biblioteca de plantillas estándar \(STL\).  
  
 [Biblioteca de plantillas activas \(ATL\)](../atl/atl-com-desktop-components.md)  
 Compatibilidad con aplicaciones y componentes COM.  
  
 [Bibliotecas de Microsoft Foundation Class \(MFC\)](../mfc/mfc-desktop-applications.md)  
 Compatibilidad para la creación de aplicaciones de escritorio que tienen interfaces de usuario tradicionales o del estilo de Office.  
  
 [Parallel Patterns Library \(PPL\)](../parallel/concrt/parallel-patterns-library-ppl.md)  
 Algoritmos asincrónicos y paralelos que se ejecutan en la CPU.  
  
 [C\+\+ AMP \(C\+\+ Accelerated Massive Parallelism\)](../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)  
 Algoritmos con gran paralelismo que se ejecutan en la GPU.  
  
 [Biblioteca de plantillas de Windows Runtime \(WRL\)](http://msdn.microsoft.com/library/windows/apps/hh438466.aspx)  
 Aplicaciones y componentes de [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)].  
  
 [Programación de .NET con C\+\+\/CLI](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)  
 Programación para Common Language Runtime \(CLR\).  
  
 Vea también la documentación de [STL\/CLR](../dotnet/stl-clr-library-reference.md) y la [Biblioteca de compatibilidad de C\+\+](../dotnet/cpp-support-library.md).  
  
## Otras bibliotecas de C\+\+  
 Esta sección contiene vínculos a bibliotecas que no están incluidas en Visual Studio, pero que se pueden descargar y usar con Visual C\+\+.  
  
 [Boost](http://www.boost.org/)  
 Se trata de una biblioteca popular y muy usada.  
  
 [C\+\+ REST SDK](http://casablanca.codeplex.com).  
 Una biblioteca de Microsoft para comunicarse con servicios web a través de HTTP.  
  
## Más recursos  
 [Recursos de Visual C\+\+](http://msdn.microsoft.com/vstudio/hh386302.aspx)  
 Más recursos de Visual C\+\+.  
  
 [Standard C\+\+](http://isocpp.org/)  
 Obtenga información sobre C\+\+, obtenga información general sobre Modern C\+\+, así como vínculos a libros, artículos, conferencias y eventos  
  
 [Aprender Visual C\+\+](http://msdn.microsoft.com/vstudio/hh386302.aspx)  
 Comience el aprendizaje de C\+\+.  
  
## Vea también  
 [Referencia de lenguaje C](../c-language/c-language-reference.md)   
 [Referencia de la biblioteca en tiempo de ejecución de C](../c-runtime-library/c-run-time-library-reference.md)   
 [Intrínsecos del compilador y del lenguaje ensamblador](../intrinsics/compiler-intrinsics-and-assembly-language.md)