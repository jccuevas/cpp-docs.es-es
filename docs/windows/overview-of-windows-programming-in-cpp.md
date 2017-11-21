---
title: "Información general sobre la programación de Windows en C++ | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: efc691d7-21f3-47ae-ae56-cab999ccf59d
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 30a5138c4ec95b2d57f56b5cc4b5731c1be073ad
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="overview-of-windows-programming-in-c"></a>Información general de la programación para Windows en C++
Se puede utilizar Visual C++ para escribir una gran variedad de programas que se ejecutan en un equipo con Windows (x86, x64 o ARM), en un servidor Windows, en la nube o en Xbox. Los programas de C++ bien escritos son rápidos, eficaces, económicos en cuanto al consumo eléctrico y capaces de sacar el máximo partido de dispositivos de varios núcleos, procesos generales en la unidad de procesamiento de gráficos (GPGPU) y otros avances recientes en hardware.  
  
 Existen varias categorías de aplicaciones de Windows que se pueden desarrollar con Visual C++. Estas categorías tienen distintos modelos de programación o de aplicación, lo que significa que usan diferentes bibliotecas y API que proporcionan acceso a la plataforma y proveen la interfaz de usuario.  
  
-   [Aplicaciones universales de Windows](#BK_WindowsUniversal). La tercera categoría de aplicaciones de Windows se introdujo con Windows 8 y continúa siendo compatible con Windows 10. Estas aplicaciones suelen denominarse “aplicaciones de Windows” e incluyen tanto aplicaciones de escritorio como móviles destinadas a diversos dispositivos. Pueden escribirse en C++/CX, que es un dialecto de C++ compatible con el desarrollo de Windows en tiempo de ejecución, o también en C++ estándar con COM mediante la biblioteca de Windows en tiempo de ejecución (WRL). Estas aplicaciones se diseñaron originalmente para ejecutarse a pantalla completa, aunque en Windows 10 los usuarios tienen la opción de ejecutarlas en una ventana del escritorio. Estas aplicaciones están pensadas para dispositivos táctiles, pero pueden usarse fácilmente con el mouse si así lo prefieren los usuarios o si no se dispone de pantalla táctil. Se distribuyen desde la Tienda Windows, hecho que llevó a llamarlas “Aplicaciones de la Tienda Windows”.  
  
-   [Aplicaciones y juegos de escritorio, servidor y nube](#BK_Native). Esta categoría incluye aplicaciones de escritorio de Windows, a veces denominadas aplicaciones Win32 debido a que usaban la API Win32. Antes de Windows 8, todas las aplicaciones de Windows pertenecían a esta categoría. Las aplicaciones de esta categoría pueden usar MFC para la interfaz de usuario y ATL para interactuar con los componentes de Windows, que normalmente son objetos COM.  
  
     Las aplicaciones, los componentes o las bibliotecas escritos en C++ estándar también entran dentro de esta categoría.  
  
     En esta categoría se incluye también el uso de C++ para los componentes principales y el código computacional en el contexto de programación de servidor y nube. A veces, el código de rendimiento intensivo que constituye el núcleo de una aplicación de servidor o de nube está escrito en C++ a fin de maximizar el rendimiento. Este código se puede compilar en un archivo DLL y usarlo desde C# o Visual Basic.  
  
-   **Aplicaciones .NET Framework** La mayoría de las aplicaciones de .NET Framework están escritas en C# o Visual Basic, pero también se puede usar C++/CLI (la opción de compilador /clr de Visual C++). Le recomendamos usar C++/CLI para una capa de interoperabilidad mínima en una aplicación mayor que incluya código administrado y nativo.  
  
##  <a name="BK_WindowsUniversal"></a> Windows Universal Apps  
 Con Windows 10, las aplicaciones pueden ejecutarse en todos los dispositivos que incluyen Windows 10, ya sean tabletas, teléfonos móviles o equipos de escritorio. En el escritorio pueden ejecutarse como una ventana de escritorio normal en lugar de hacerlo continuamente a pantalla completa. Estas aplicaciones también pueden ejecutarse en la consola Xbox y en futuros dispositivos.  El modelo de programación para los dos tipos de aplicaciones es diferente de las aplicaciones de escritorio de Win32. Estas aplicaciones de Windows se ejecutan en Windows en tiempo de ejecución, que proporciona los elementos de la interfaz de usuario, los servicios esenciales para estas aplicaciones y una interfaz para los diversos dispositivos de hardware compatibles. Estas aplicaciones se compilan en código nativo y tienen una interfaz de usuario XAML o usan DirectX. También puede escribir componentes de Windows en tiempo de ejecución en código nativo que otras aplicaciones de Windows pueden consumir; Esto incluye aplicaciones escritas en C#, Visual Basic o JavaScript. Para obtener más información, consulte [Create your first Windows Store app using C++](http://go.microsoft.com/fwlink/?LinkID=534976)(Crear la primera aplicación de la Tienda Windows con C++), [Create your first Windows Store game using DirectX](http://go.microsoft.com/fwlink/p/?LinkId=244656)(Crear el primer juego de la Tienda Windows con DirectX) y [Crear componentes de Windows en tiempo de ejecución en C++](http://go.microsoft.com/fwlink/p/?LinkId=244658).  

 > [!TIP]  
> Para Windows 10, puede utilizar el convertidor de la aplicación de escritorio para empaquetar la aplicación de escritorio existente para la implementación a través de la tienda de Windows. Para obtener más información, vea [Using Visual C++ Runtime in Centennial project](https://blogs.msdn.microsoft.com/vcblog/2016/07/07/using-visual-c-runtime-in-centennial-project) (Usar el tiempo de ejecución de Visual C++ en el proyecto Centennial) y [Convertir la aplicación de escritorio en una aplicación para Plataforma universal de Windows (UWP) con el puente de escritorio](https://msdn.microsoft.com/en-us/windows/uwp/porting/desktop-to-uwp-root).
  
  
 Para obtener ejemplos de la Plataforma universal de Windows, consulte [Windows Universal Samples](https://github.com/Microsoft/Windows-universal-samples)(Ejemplos de Windows Universal) en GitHub.  
  
 Si tiene un proyecto de Windows 8.1 y desea trasladarlo a Windows 10 existente, vea [migrar a la plataforma Universal de Windows](../porting/porting-to-the-universal-windows-platform-cpp.md). Si tiene Win32 bibliotecas de escritorio clásico y algún código que desea integrar en una aplicación de UWP, vea [Cómo: usar código C++ existente en una aplicación de plataforma Universal de Windows](../porting/how-to-use-existing-cpp-code-in-a-universal-windows-platform-app.md).  
  
 También puede escribir componentes, juegos y aplicaciones universales de Windows sin usar C++ / CX; en su lugar, puede usar la biblioteca de plantillas de C++ de Windows en tiempo de ejecución (biblioteca de plantillas de C++ de Windows en tiempo de ejecución). Para obtener más información, consulte [biblioteca de plantillas de C++ (WRL) de Windows en tiempo de ejecución](../windows/windows-runtime-cpp-template-library-wrl.md).  
  
 Con [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)], puede desarrollar aplicaciones universales de Windows que se ejecutan en dispositivos móviles y equipos de escritorio con Windows 10. También puede desarrollar aplicaciones de Windows 8.1 y Windows Phone 8.1 en [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)], pero para ello debe instalar primero Visual Studio 2013 en el mismo equipo y, después, configurar el proyecto para usar el conjunto de herramientas **Visual Studio 2013 (v120)** . Para configurar esta opción en el proyecto, abra las propiedades del proyecto y, en la sección **General** , establezca el **Conjunto de herramientas de la plataforma** en **Visual Studio 2013 (v120)**.  
  
 Si instala las herramientas de Phone 8.0 del programa de instalación de Visual Studio, también puede desarrollar para Windows Phone 8.0.  
  
 Un nuevo concepto de contratos de API, introducido en Windows 10, reemplaza la antigua práctica de destinar las aplicaciones a versiones específicas de Windows. En su lugar, puede elegir qué contratos de API necesita la aplicación y esta se ejecutará en cualquier dispositivo de Windows que admita esos contratos. Un contrato de API es un conjunto de API estables que proporcionan acceso a los recursos de plataforma o dispositivo. Los contratos de API se pueden incluidos como referencias en el sistema del proyecto. En un proyecto de Visual Studio, si agrega una referencia a un SDK de extensión determinado, Visual Studio agrega los contratos de API apropiados.  
  
 Para obtener más información sobre todos estos conceptos, consulte [Guía de aplicaciones para la Plataforma universal de Windows (UWP)](http://go.microsoft.com/fwlink/?LinkId=534605).  
  
##  <a name="BK_Native"></a> Aplicaciones y juegos de escritorio, servidor y la nube  
 En la nube puede crear ensamblados de código nativo de Azure en C++ y llamarlos desde roles web creados en C#. Para obtener más información, consulte [Azure SDK](http://go.microsoft.com/fwlink/p/?LinkId=256416).  
  
 Para obtener información sobre los fundamentos de escribir aplicaciones cliente de Windows para el escritorio, consulte [Developing Windows Applications in C++](http://msdn.microsoft.com/vstudio//hh304489) (Desarrollo de aplicaciones Windows en C++) e [Introduction to Windows Programming in C++](http://msdn.microsoft.com/library/windows/desktop/ff381398\(v=vs.85\).aspx)(Introducción a la programación para Windows en C++).  
  
 En Windows 10 puede usar Visual C++ para crear muchas clases de programas:  
  
-   Aplicaciones y utilidades de línea de comandos. Para obtener más información, consulte [aplicaciones de consola](../windows/console-applications-in-visual-cpp.md).  
  
-   Juegos DirectX que se ejecutan en PC o en Xbox. Para obtener más información, consulte [DirectX Developer Center](http://go.microsoft.com/fwlink/p/?LinkId=256418)(Centro para desarrolladores de DirectX).  
  
-   Aplicaciones de consumidor que cuentan con interfaces gráficas de usuario sofisticadas. Para obtener más información, consulte [Hilo: Developing C++ Applications for Windows](http://go.microsoft.com/fwlink/p/?LinkId=256417)(Hilo: Desarrollar aplicaciones de C++ para Windows).  
  
-   Aplicaciones empresariales y de línea de negocio que se ejecutan en .NET Framework, o que sirven como puente entre aplicaciones de .NET Framework y aplicaciones o componentes escritos en código nativo. Para obtener más información, consulte [programación de .NET con C++ / CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md).  
  
-   Clientes de base de datos SQL que se ejecutan en código nativo. Para obtener más información, consulte [SQL Server Native Client](http://go.microsoft.com/fwlink/p/?LinkId=256419).  
  
-   Complementos para aplicaciones de Microsoft Office. Para obtener más información, consulte [Creación de un complemento de C++ para Outlook 2010](http://go.microsoft.com/fwlink/p/?LinkId=256420).  
  
-   Controladores de dispositivos. Para obtener más información, consulte [Windows Driver Kit (WDK)](http://go.microsoft.com/fwlink/p/?LinkId=256421)(Kit para controladores de Windows [WDK]).  
  
-   Servicios de Windows. Para obtener más información, consulta [Introduction to Windows Service Applications](/dotnet/framework/windows-services/introduction-to-windows-service-applications).  
  
 Puede utilizar Visual C++ para empaquetar casi cualquier tipo de funcionalidad personalizada de alto rendimiento en archivos DLL Win32 o en archivos DLL COM que pueden usar las aplicaciones de C++ o las aplicaciones escritas en otros lenguajes, por ejemplo C# o Visual Basic. Para obtener más información sobre los archivos DLL WIn32, consulte [DLLs in Visual C++](../build/dlls-in-visual-cpp.md). Para obtener más información sobre el desarrollo COM, consulte [Component Object Model (COM)](http://msdn.microsoft.com/en-us/375d29a7-a1f3-4bd8-8621-bad7a049b2aa).  
  
## <a name="sdks-and-header-files"></a>SDK y archivos de encabezado  
 Visual C++ incluye la biblioteca de tiempo de ejecución de C (CRT), la biblioteca estándar de C++ y otras bibliotecas específicas de Microsoft. Las carpetas de inclusión que contienen archivos de encabezado de estas bibliotecas están ubicadas en el directorio de instalación de Visual Studio en la carpeta \VC\ o en el caso de las funciones de CRT, una carpeta de instalación del SDK de Windows, por ejemplo, Windows Kits\10 en los archivos de programa carpeta para el SDK de Windows 10.  Las bibliotecas de Microsoft incluyen:  
  
-   Microsoft Foundation Classes (MFC): un marco de trabajo orientado a objetos para crear programas tradicionales de Windows, especialmente aplicaciones empresariales, que tienen interfaces de usuario complejas con botones, cuadros de lista, vistas de árbol y otros controles. Para obtener más información, consulta [MFC Desktop Applications](../mfc/mfc-desktop-applications.md).  
  
-   Active Template Library (ATL): una biblioteca auxiliar eficaz para crear componentes COM. Para obtener más información, consulta [ATL COM Desktop Components](../atl/atl-com-desktop-components.md).  
  
-   C++ AMP (C++ Accelerated Massive Parallelism): una biblioteca que habilita el trabajo de proceso general de alto rendimiento en la GPU. Para obtener más información, consulta [C++ AMP (C++ Accelerated Massive Parallelism)](../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md).  
  
-   Runtime de simultaneidad: una biblioteca que simplifica el trabajo de programación paralela y asincrónica para dispositivos de varios núcleos. Para obtener más información, consulta [Concurrency Runtime](../parallel/concrt/concurrency-runtime.md).  
  
 En muchos escenarios de programación para Windows también se requiere Windows SDK, que incluye los archivos de encabezado que permiten el acceso a componentes del sistema operativo Windows. De forma predeterminada, todas las ediciones de Visual Studio 2015 instalan el SDK de Windows, que permite el desarrollo de aplicaciones universales de Windows. Para desarrollar aplicaciones universales de Windows para Windows 10, es necesaria la versión para Windows 10 de Windows SDK. Para obtener información sobre el SDK de Windows 10, consulte [SDK de Windows 10](http://go.microsoft.com/fwlink/p/?LinkId=534603) (para obtener más información sobre los SDK de Windows para versiones anteriores de Windows, consulte [Overview of the Windows SDK](http://msdn.microsoft.com/Library/9a2db508-5b77-43f8-afa4-1ca82d24bb83)).  
  
 Otras plataformas como Xbox y Azure cuentan con sus propios SDK que puede que tenga que instalar. Para obtener más información, vea el Centro para desarrolladores de DirectX y el Centro para desarrolladores de Azure.  
  
## <a name="development-tools"></a>Herramientas del programador  
 Visual Studio incluye un depurador eficaz de código nativo, herramientas de análisis estático, herramientas de depuración de gráficos, un editor de código completo, compatibilidad con pruebas unitarias, y muchas otras herramientas y utilidades. Para obtener más información, consulte [desarrollo de aplicaciones en Visual Studio](http://msdn.microsoft.com/en-us/97490c1b-a247-41fb-8f2c-bc4c201eff68), y [IDE y herramientas de desarrollo](../ide/ide-and-tools-for-visual-cpp-development.md).  
  
## <a name="related-articles"></a>Artículos relacionados  
  
|Título|Descripción|  
|-----------|-----------------|  
|[Visual C++](../visual-cpp-in-visual-studio.md)|Tema primario para el contenido del programador de Visual C++.|