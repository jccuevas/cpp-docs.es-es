---
title: "Informaci&#243;n general de la programaci&#243;n para Windows en C++ | Microsoft Docs"
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
ms.assetid: efc691d7-21f3-47ae-ae56-cab999ccf59d
caps.latest.revision: 22
caps.handback.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Informaci&#243;n general de la programaci&#243;n para Windows en C++
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Se puede utilizar Visual C\+\+ para escribir una gran variedad de programas que se ejecutan en un equipo con Windows \(x86, x64 o ARM\), en un servidor Windows, en la nube o en Xbox. Los programas de C\+\+ bien escritos son rápidos, eficaces, económicos en cuanto al consumo eléctrico y capaces de sacar el máximo partido de dispositivos de varios núcleos, procesos generales en la unidad de procesamiento de gráficos \(GPGPU\) y otros avances recientes en hardware.  
  
 Existen varias categorías de aplicaciones de Windows que se pueden desarrollar con Visual C\+\+. Estas categorías tienen distintos modelos de programación o de aplicación, lo que significa que usan diferentes bibliotecas y API que proporcionan acceso a la plataforma y proveen la interfaz de usuario.  
  
-   [Aplicaciones universales de Windows](#BK_WindowsUniversal). La tercera categoría de aplicaciones de Windows se introdujo con Windows 8 y continúa siendo compatible con Windows 10. Estas aplicaciones suelen denominarse “aplicaciones de Windows” e incluyen tanto aplicaciones de escritorio como móviles destinadas a diversos dispositivos. Pueden escribirse en C\+\+\/CX, que es un dialecto de C\+\+ compatible con el desarrollo de Windows en tiempo de ejecución, o también en C\+\+ estándar con COM mediante la biblioteca de Windows en tiempo de ejecución \(WRL\). Estas aplicaciones se diseñaron originalmente para ejecutarse a pantalla completa, aunque en Windows 10 los usuarios tienen la opción de ejecutarlas en una ventana del escritorio. Estas aplicaciones están pensadas para dispositivos táctiles, pero pueden usarse fácilmente con el mouse si así lo prefieren los usuarios o si no se dispone de pantalla táctil. Se distribuyen desde la Tienda Windows, hecho que llevó a llamarlas “Aplicaciones de la Tienda Windows”.  
  
-   [Aplicaciones y juegos de escritorio, servidor y nube](#BK_Native). Esta categoría incluye aplicaciones de escritorio de Windows, a veces denominadas aplicaciones Win32 debido a que usaban la API Win32. Antes de Windows 8, todas las aplicaciones de Windows pertenecían a esta categoría. Las aplicaciones de esta categoría pueden usar MFC para la interfaz de usuario y ATL para interactuar con los componentes de Windows, que normalmente son objetos COM.  
  
     Las aplicaciones, los componentes o las bibliotecas escritos en C\+\+ estándar también entran dentro de esta categoría.  
  
     En esta categoría se incluye también el uso de C\+\+ para los componentes principales y el código computacional en el contexto de programación de servidor y nube. A veces, el código de rendimiento intensivo que constituye el núcleo de una aplicación de servidor o de nube está escrito en C\+\+ a fin de maximizar el rendimiento. Este código se puede compilar en un archivo DLL y usarlo desde C\# o Visual Basic.  
  
-   **Aplicaciones .NET Framework** La mayoría de las aplicaciones de .NET Framework están escritas en C\# o Visual Basic, pero también se puede usar C\+\+\/CLI \(la opción de compilador \/clr de Visual C\+\+\). Le recomendamos usar C\+\+\/CLI para una capa de interoperabilidad mínima en una aplicación mayor que incluya código administrado y nativo.  
  
##  <a name="BK_WindowsUniversal"></a> Aplicaciones universales de Windows  
 Con Windows 10, las aplicaciones pueden ejecutarse en todos los dispositivos que incluyen Windows 10, ya sean tabletas, teléfonos móviles o equipos de escritorio. En el escritorio pueden ejecutarse como una ventana de escritorio normal en lugar de hacerlo continuamente a pantalla completa. Estas aplicaciones también pueden ejecutarse en la consola Xbox y en futuros dispositivos.  El modelo de programación para los dos tipos de aplicaciones es diferente de las aplicaciones de escritorio de Win32. Estas aplicaciones de Windows se ejecutan en Windows en tiempo de ejecución, que proporciona los elementos de la interfaz de usuario, los servicios esenciales para estas aplicaciones y una interfaz para los diversos dispositivos de hardware compatibles. Estas aplicaciones se compilan en código nativo y tienen una interfaz de usuario XAML o usan DirectX. También puede escribir componentes de [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] en código nativo que otras aplicaciones de Windows pueden consumir; esto incluye aplicaciones escritas en C\#, Visual Basic o JavaScript. Para obtener más información, consulte [Create your first Windows Store app using C\+\+](http://go.microsoft.com/fwlink/?LinkID=534976) \(Crear la primera aplicación de la Tienda Windows con C\+\+\), [Create your first Windows Store game using DirectX](http://go.microsoft.com/fwlink/p/?LinkId=244656) \(Crear el primer juego de la Tienda Windows con DirectX\) y [Crear componentes de Windows en tiempo de ejecución en C\+\+](http://go.microsoft.com/fwlink/p/?LinkId=244658).  
  
 Para obtener ejemplos de la Plataforma universal de Windows, consulte [Windows Universal Samples](https://github.com/Microsoft/Windows-universal-samples) \(Ejemplos de Windows Universal\) en GitHub.  
  
 Si tiene un proyecto de Windows 8.1 y quiere trasladarlo a Windows 10, consulte [Migración a la Plataforma universal de Windows](../porting/porting-to-the-universal-windows-platform-cpp.md). Si tiene bibliotecas de escritorio de Win32 clásico y algún código que quiera integrar en una aplicación UWP, consulte [Cómo: utilizar código C\+\+ existente en una aplicación universal de la plataforma Windows](../porting/how-to-use-existing-cpp-code-in-a-universal-windows-platform-app.md).  
  
 También puede escribir aplicaciones, juegos y componentes universales de Windows sin usar [!INCLUDE[cppwrt](../build/reference/includes/cppwrt_md.md)] \([!INCLUDE[cppwrt_short](../build/reference/includes/cppwrt_short_md.md)]\); en su lugar, puede usar la [!INCLUDE[cppwrl](../windows/includes/cppwrl_md.md)] \([!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)]\). Para obtener más información, consulta [Biblioteca de plantillas de Windows Runtime C\+\+ \(WRL\)](../Topic/Windows%20Runtime%20C++%20Template%20Library%20\(WRL\).md).  
  
 Con [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)], puede desarrollar aplicaciones universales de Windows que se ejecutan en dispositivos móviles y equipos de escritorio con Windows 10. También puede desarrollar aplicaciones de Windows 8.1 y Windows Phone 8.1 en [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)], pero para ello debe instalar primero Visual Studio 2013 en el mismo equipo y, después, configurar el proyecto para usar el conjunto de herramientas **Visual Studio 2013 \(v120\)**. Para configurar esta opción en el proyecto, abra las propiedades del proyecto y, en la sección **General**, establezca el **Conjunto de herramientas de la plataforma** en **Visual Studio 2013 \(v120\)**.  
  
 Si instala las herramientas de Phone 8.0 del programa de instalación de Visual Studio, también puede desarrollar para Windows Phone 8.0.  
  
 Un nuevo concepto de contratos de API, introducido en Windows 10, reemplaza la antigua práctica de destinar las aplicaciones a versiones específicas de Windows. En su lugar, puede elegir qué contratos de API necesita la aplicación y esta se ejecutará en cualquier dispositivo de Windows que admita esos contratos. Un contrato de API es un conjunto de API estables que proporcionan acceso a los recursos de plataforma o dispositivo. Los contratos de API se pueden incluidos como referencias en el sistema del proyecto. En un proyecto de Visual Studio, si agrega una referencia a un SDK de extensión determinado, Visual Studio agrega los contratos de API apropiados.  
  
 Para obtener más información sobre todos estos conceptos, consulte [Guía de aplicaciones para la Plataforma universal de Windows \(UWP\)](http://go.microsoft.com/fwlink/?LinkId=534605).  
  
##  <a name="BK_Win32"></a> Aplicaciones y juegos de escritorio, servidor y la nube  
 En la nube puede crear ensamblados de código nativo de Azure en C\+\+ y llamarlos desde roles web creados en C\#. Para obtener más información, consulte [Azure SDK](http://go.microsoft.com/fwlink/p/?LinkId=256416).  
  
 Para obtener información sobre los fundamentos de escribir aplicaciones cliente de Windows para el escritorio, consulte [Developing Windows Applications in C\+\+](http://msdn.microsoft.com/vstudio//hh304489) \(Desarrollo de aplicaciones Windows en C\+\+\) e [Introduction to Windows Programming in C\+\+](http://msdn.microsoft.com/library/windows/desktop/ff381398\(v=vs.85\).aspx) \(Introducción a la programación para Windows en C\+\+\).  
  
 En Windows 10 puede usar Visual C\+\+ para crear muchas clases de programas:  
  
-   Aplicaciones y utilidades de línea de comandos. Para obtener más información, consulta [Aplicaciones de consola](../Topic/Console%20Applications%20in%20Visual%20C++.md).  
  
-   Juegos DirectX que se ejecutan en PC o en Xbox. Para obtener más información, consulte [DirectX Developer Center](http://go.microsoft.com/fwlink/p/?LinkId=256418) \(Centro para desarrolladores de DirectX\).  
  
-   Aplicaciones de consumidor que cuentan con interfaces gráficas de usuario sofisticadas. Para obtener más información, consulte [Hilo: Developing C\+\+ Applications for Windows](http://go.microsoft.com/fwlink/p/?LinkId=256417) \(Hilo: Desarrollar aplicaciones de C\+\+ para Windows\).  
  
-   Aplicaciones empresariales y de línea de negocio que se ejecutan en .NET Framework, o que sirven como puente entre aplicaciones de .NET Framework y aplicaciones o componentes escritos en código nativo. Para obtener más información, consulta [Programación de .NET con C\+\+\/CLI](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md).  
  
-   Clientes de base de datos SQL que se ejecutan en código nativo. Para obtener más información, consulte [SQL Server Native Client](http://go.microsoft.com/fwlink/p/?LinkId=256419).  
  
-   Complementos para aplicaciones de Microsoft Office. Para obtener más información, consulte [Creación de un complemento de C\+\+ para Outlook 2010](http://go.microsoft.com/fwlink/p/?LinkId=256420).  
  
-   Controladores de dispositivos. Para obtener más información, consulte [Windows Driver Kit \(WDK\)](http://go.microsoft.com/fwlink/p/?LinkId=256421) \(Kit para controladores de Windows \[WDK\]\).  
  
-   Servicios de Windows. Para obtener más información, consulta [Introduction to Windows Service Applications](../Topic/Introduction%20to%20Windows%20Service%20Applications.md).  
  
 Puede utilizar Visual C\+\+ para empaquetar casi cualquier tipo de funcionalidad personalizada de alto rendimiento en archivos DLL Win32 o en archivos DLL COM que pueden usar las aplicaciones de C\+\+ o las aplicaciones escritas en otros lenguajes, por ejemplo C\# o Visual Basic. Para obtener más información sobre los archivos DLL WIn32, consulte [Archivos DLL en Visual C\+\+](../build/dlls-in-visual-cpp.md). Para obtener más información sobre el desarrollo COM, consulte [Component Object Model \(COM\)](http://msdn.microsoft.com/es-es/375d29a7-a1f3-4bd8-8621-bad7a049b2aa).  
  
## SDK y archivos de encabezado  
 Visual C\+\+ incluye bibliotecas estándar de C y C\+\+, la biblioteca de plantillas estándar \(STL\) y otras bibliotecas específicas de Microsoft. Las carpetas de inclusión que contienen los archivos de encabezado de estas bibliotecas están ubicadas en el directorio de instalación de Visual Studio, dentro de la carpeta \\VC\\; en el caso de la biblioteca en tiempo de ejecución de C \(CRT\), están ubicadas en la carpeta de instalación de Windows SDK \(por ejemplo, Windows Kits\\10\), dentro de la carpeta Archivos de programa para el SDK de Windows 10.  Entre las bibliotecas de Microsoft se incluyen:  
  
-   Microsoft Foundation Classes \(MFC\): un marco de trabajo orientado a objetos para crear programas tradicionales de Windows, especialmente aplicaciones empresariales, que tienen interfaces de usuario complejas con botones, cuadros de lista, vistas de árbol y otros controles. Para obtener más información, consulta [Aplicaciones de escritorio de MFC](../mfc/mfc-desktop-applications.md).  
  
-   Active Template Library \(ATL\): una biblioteca auxiliar eficaz para crear componentes COM. Para obtener más información, consulta [ATL COM Desktop Components](../atl/atl-com-desktop-components.md).  
  
-   C\+\+ AMP \(C\+\+ Accelerated Massive Parallelism\): una biblioteca que habilita el trabajo de proceso general de alto rendimiento en la GPU. Para obtener más información, consulta [C\+\+ AMP \(C\+\+ Accelerated Massive Parallelism\)](../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md).  
  
-   Runtime de simultaneidad: una biblioteca que simplifica el trabajo de programación paralela y asincrónica para dispositivos de varios núcleos. Para obtener más información, consulta [Runtime de simultaneidad](../parallel/concrt/concurrency-runtime.md).  
  
 En muchos escenarios de programación para Windows también se requiere Windows SDK, que incluye los archivos de encabezado que permiten el acceso a componentes del sistema operativo Windows. De forma predeterminada, todas las ediciones de [!INCLUDE[vs_dev14](../ide/includes/vs_dev14_md.md)] instalan Windows SDK, que permite el desarrollo de aplicaciones universales de Windows. Para desarrollar aplicaciones universales de Windows para Windows 10, es necesaria la versión para Windows 10 de Windows SDK. Para obtener información sobre el SDK de Windows 10, consulte [SDK de Windows 10](http://go.microsoft.com/fwlink/p/?LinkId=534603) \(para obtener más información sobre los SDK de Windows para versiones anteriores de Windows, consulte [Overview of the Windows SDK](../Topic/Overview%20of%20the%20Windows%20SDK.md)\).  
  
 Otras plataformas como Xbox y Azure cuentan con sus propios SDK que puede que tenga que instalar. Para obtener más información, vea el Centro para desarrolladores de DirectX y el Centro para desarrolladores de Azure.  
  
## Herramientas del programador  
 Visual Studio incluye un depurador eficaz de código nativo, herramientas de análisis estático, herramientas de depuración de gráficos, un editor de código completo, compatibilidad con pruebas unitarias, y muchas otras herramientas y utilidades. Para obtener más información, consulte [Desarrollo de aplicaciones en Visual Studio](http://msdn.microsoft.com/es-es/97490c1b-a247-41fb-8f2c-bc4c201eff68) y [IDE y herramientas de desarrollo](../ide/ide-and-tools-for-visual-cpp-development.md).  
  
## Artículos relacionados  
  
|Título|Descripción|  
|------------|-----------------|  
|[Visual C\+\+](../top/visual-cpp-in-visual-studio-2015.md)|Tema primario del contenido de MSDN Library sobre C\+\+.|