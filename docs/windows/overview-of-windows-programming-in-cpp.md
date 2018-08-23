---
title: Información general de la programación de Windows en C++ | Microsoft Docs
ms.custom: ''
ms.date: 04/06/2018
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: efc691d7-21f3-47ae-ae56-cab999ccf59d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b66d6d3a7da6c9e3084ce2ef6fa18922e015a459
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42604284"
---
# <a name="overview-of-windows-programming-in-c"></a>Información general de la programación para Windows en C++

Puede usar Visual C++ para escribir muchas clases de programas que se ejecutan en un equipo de Windows (x 86, x64 o ARM), en un servidor de Windows, en la nube o en Xbox. Los programas bien escritos de C++ tienen estas cualidades:
- eficaz en los requisitos de memoria
- económica en el consumo de energía 
- puede aprovechar al máximo de dispositivos de varios núcleos y varios núcleos
- capaz de hacer el cálculo general en la unidad de procesamiento de gráficos (GPGPU)  
- se puede sacar provecho de otros avances recientes en hardware.

Existen varias categorías de aplicaciones de Windows que se pueden desarrollar con Visual C++. Estas categorías tienen distintos modelos de programación o modelos de aplicación, que se han introducido en los años. Cada modelo utiliza diferentes bibliotecas y API para proporcionar acceso a la plataforma y crear interfaces de usuario como ventanas y cuadros de diálogo. La biblioteca estándar de C++, así como bibliotecas de terceros pueden usarse en cualquiera de estas categorías, con algunas restricciones para UWP.

- [Aplicaciones universales de Windows](#BK_WindowsUniversal). La tercera categoría de aplicaciones de Windows se introdujo con Windows 8 y continúa siendo compatible con Windows 10. Estas aplicaciones suelen denominarse “aplicaciones de Windows” e incluyen tanto aplicaciones de escritorio como móviles destinadas a diversos dispositivos. Pueden escribirse en C++/CX, que es un dialecto de C++ compatible con el desarrollo de Windows en tiempo de ejecución, o también en C++ estándar con COM mediante la biblioteca de Windows en tiempo de ejecución (WRL). Estas aplicaciones se diseñaron originalmente para ejecutarse a pantalla completa, aunque en Windows 10 los usuarios tienen la opción de ejecutarlas en una ventana del escritorio. Estas aplicaciones están pensadas para dispositivos táctiles, pero pueden usarse fácilmente con el mouse si así lo prefieren los usuarios o si no se dispone de pantalla táctil. Estas aplicaciones se distribuyen desde la Microsoft Store, un hecho que llevó a llamarlas "Store" aplicaciones.

Aplicaciones para UWP pueden ejecutar en todos los dispositivos Windows 10 como tabletas y teléfonos móviles, así como en el escritorio. En el escritorio pueden ejecutarse como una ventana de escritorio normal en lugar de hacerlo continuamente a pantalla completa. Estas aplicaciones también pueden ejecutarse en la consola Xbox y en futuros dispositivos.  Las aplicaciones UWP se ejecutan en el tiempo de ejecución de Windows, que proporciona una interfaz para los diversos dispositivos de hardware que se admiten en Windows, servicios y elementos de la interfaz de usuario.

Puede escribir aplicaciones para UWP en C++ / c++ / CX, un dialecto de C++, puede usar el [C++ / c++ / WinRT biblioteca](https://moderncpp.com/)para algunos escenarios. Las aplicaciones para UWP compilan a código nativo y tienen una interfaz de usuario XAML o utilizan DirectX. Componentes de Windows en tiempo de ejecución que se escriben en código nativo que pueden consumir las aplicaciones para UWP escritas en otros lenguajes. Para obtener más información, consulte [crear una aplicación plataforma Universal de Windows en C++](http://go.microsoft.com/fwlink/?LinkID=534976), [crea tu primer juego para UWP con DirectX](http://go.microsoft.com/fwlink/p/?LinkId=244656), y [componentes de creación en tiempo de ejecución de Windows en C++](http://go.microsoft.com/fwlink/p/?LinkId=244658).

   En esta categoría se incluye también el uso de C++ para los componentes principales y el código computacional en el contexto de programación de servidor y nube. A veces, el código de rendimiento intensivo que constituye el núcleo de una aplicación de servidor o de nube está escrito en C++ a fin de maximizar el rendimiento. Este código se puede compilar en un archivo DLL y usarlo desde C# o Visual Basic.

- **Aplicaciones .NET Framework** La mayoría de las aplicaciones de .NET Framework se escriben en C# o Visual Basic, pero también puede C++ / c++ / CLI (la `/clr` opción del compilador en Visual C++). Le recomendamos usar C++/CLI para una capa de interoperabilidad mínima en una aplicación mayor que incluya código administrado y nativo.

##  <a name="BK_WindowsUniversal"></a> Windows Universal Apps

Con Windows 10, las aplicaciones pueden ejecutarse en todos los dispositivos que incluyen Windows 10, ya sean tabletas, teléfonos móviles o equipos de escritorio. En el escritorio pueden ejecutarse como una ventana de escritorio normal en lugar de hacerlo continuamente a pantalla completa. Estas aplicaciones también pueden ejecutarse en la consola Xbox y en futuros dispositivos.  El modelo de programación para los dos tipos de aplicaciones es diferente de las aplicaciones de escritorio de Win32. Estas aplicaciones de Windows se ejecutan en Windows en tiempo de ejecución, que proporciona los elementos de la interfaz de usuario, los servicios esenciales para estas aplicaciones y una interfaz para los diversos dispositivos de hardware compatibles. Estas aplicaciones se compilan en código nativo y tienen una interfaz de usuario XAML o usan DirectX. También puede escribir componentes de Windows en tiempo de ejecución en código nativo que otras aplicaciones de Windows pueden consumir; Esto incluye aplicaciones escritas en C#, Visual Basic o JavaScript. Para obtener más información, consulte [crear una aplicación UWP "Hello world" en C++](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp), [crear un juego para UWP simple con DirectX](/windows/uwp/gaming/tutorial--create-your-first-uwp-directx-game), y [componentes de creación en tiempo de ejecución de Windows en C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp).

> [!TIP]
> Para Windows 10, puede usar el Desktop App Converter para empaquetar la aplicación de escritorio existente para la implementación a través de la Microsoft Store. Para obtener más información, vea [Using Visual C++ Runtime in Centennial project](https://blogs.msdn.microsoft.com/vcblog/2016/07/07/using-visual-c-runtime-in-centennial-project) (Usar el tiempo de ejecución de Visual C++ en el proyecto Centennial) y [Convertir la aplicación de escritorio en una aplicación para Plataforma universal de Windows (UWP) con el puente de escritorio](https://msdn.microsoft.com/windows/uwp/porting/desktop-to-uwp-root).

Para obtener ejemplos de la Plataforma universal de Windows, consulte [Windows Universal Samples](https://github.com/Microsoft/Windows-universal-samples)(Ejemplos de Windows Universal) en GitHub.

Si tiene un proyecto de Windows 8.1 y desea trasladarlo a Windows 10 existentes, consulte [migrar a la plataforma Universal de Windows](../porting/porting-to-the-universal-windows-platform-cpp.md). Si tiene existentes bibliotecas de escritorio de Win32 clásicas y algún código que desea integrar en una aplicación para UWP, consulte [Cómo: usar código de C++ existente en una aplicación de plataforma Universal de Windows](../porting/how-to-use-existing-cpp-code-in-a-universal-windows-platform-app.md).

Para obtener más información sobre UWP en general, consulte [¿qué es una aplicación de plataforma Universal de Windows (UWP)?](/windows/uwp/get-started/whats-a-uwp).

Para obtener más información sobre todos estos conceptos, consulte [guía para aplicaciones universales de Windows](http://go.microsoft.com/fwlink/p/?linkid=534605).

##  <a name="BK_Native"></a> Aplicaciones de escritorio y servidores

Para obtener información sobre los fundamentos de escribir aplicaciones cliente de Windows para el escritorio, consulte [Developing Windows Applications in C++](http://msdn.microsoft.com/vstudio//hh304489) (Desarrollo de aplicaciones Windows en C++) e [Introduction to Windows Programming in C++](http://msdn.microsoft.com/library/windows/desktop/ff381398\(v=vs.85\).aspx)(Introducción a la programación para Windows en C++).

En Windows 10, puede usar Visual C++ para crear muchos tipos de programas de escritorio:

- Aplicaciones y utilidades de línea de comandos. Para obtener más información, consulte [aplicaciones de consola](../windows/console-applications-in-visual-cpp.md).

- Aplicaciones de consumidor que cuentan con interfaces gráficas de usuario sofisticadas. Para obtener más información, consulte [Hilo: Developing C++ Applications for Windows](http://go.microsoft.com/fwlink/p/?LinkId=256417)(Hilo: Desarrollar aplicaciones de C++ para Windows).

- Aplicaciones empresariales y de línea de negocio que se ejecutan en .NET Framework. La mayoría de las aplicaciones de .NET Framework se escriben en C# o Visual Basic. Puede usar C++ / c++ / CLI para crear capas de interoperabilidad que permiten al código de .NET consumir bibliotecas nativas de C++. Para obtener más información, consulte [programación de .NET con C++ / c++ / CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md).

- Clientes de base de datos SQL que se ejecutan en código nativo. Para obtener más información, consulte [SQL Server Native Client](/sql/relational-databases/native-client/odbc/sql-server-native-client-odbc).

- Complementos para aplicaciones de Microsoft Office. Para obtener más información, consulte [Creación de un complemento de C++ para Outlook 2010](http://go.microsoft.com/fwlink/p/?LinkId=256420).

- Controladores de dispositivos. Para obtener más información, consulte [Windows Driver Kit (WDK)](http://go.microsoft.com/fwlink/p/?LinkId=256421)(Kit para controladores de Windows [WDK]).

- Servicios de Windows. Para obtener más información, consulta [Introduction to Windows Service Applications](/dotnet/framework/windows-services/introduction-to-windows-service-applications).

Puede utilizar Visual C++ para empaquetar casi cualquier tipo de funcionalidad personalizada de alto rendimiento en archivos DLL Win32 o en archivos DLL COM que pueden usar las aplicaciones de C++ o las aplicaciones escritas en otros lenguajes, por ejemplo C# o Visual Basic. Para obtener más información sobre los archivos DLL WIn32, consulte [DLLs in Visual C++](../build/dlls-in-visual-cpp.md). Para obtener más información sobre el desarrollo COM, vea [modelo de objetos componentes (COM)](https://msdn.microsoft.com/library/windows/desktop/ms680573).

## <a name="games"></a>Juegos

Pueden ejecutar juegos de DirectX en PC o en Xbox. Para obtener más información, consulte [DirectX Developer Center](http://go.microsoft.com/fwlink/p/?LinkId=256418)(Centro para desarrolladores de DirectX).

## <a name="sdks-libraries-and-header-files"></a>Archivos de encabezado, bibliotecas y SDK

Visual C++ incluye la biblioteca en tiempo de ejecución de C (CRT), la biblioteca estándar de C++ y otras bibliotecas específicas de Microsoft. Las carpetas de inclusión que contienen archivos de encabezado para estas bibliotecas se encuentran en el directorio de instalación de Visual Studio en la carpeta \VC\ o en el caso de CRT, en la carpeta de instalación del SDK de Windows.

Puede usar el [Administrador de paquetes de Vcpkg](../vcpkg.md) para instalar cómodamente cientos de bibliotecas de código abierto de terceros para Windows.

Las bibliotecas de Microsoft incluyen:

- Microsoft Foundation Classes (MFC): un marco de trabajo orientado a objetos para crear programas tradicionales de Windows, especialmente aplicaciones empresariales, que tienen interfaces de usuario complejas con botones, cuadros de lista, vistas de árbol y otros controles. Para obtener más información, consulta [MFC Desktop Applications](../mfc/mfc-desktop-applications.md).

- Active Template Library (ATL): una biblioteca auxiliar eficaz para crear componentes COM. Para obtener más información, consulta [ATL COM Desktop Components](../atl/atl-com-desktop-components.md).

- C++ AMP (C++ Accelerated Massive Parallelism): una biblioteca que habilita el trabajo de proceso general de alto rendimiento en la GPU. Para obtener más información, consulta [C++ AMP (C++ Accelerated Massive Parallelism)](../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md).

- Runtime de simultaneidad: una biblioteca que simplifica el trabajo de programación paralela y asincrónica para dispositivos de varios núcleos. Para obtener más información, consulta [Concurrency Runtime](../parallel/concrt/concurrency-runtime.md).

En muchos escenarios de programación para Windows también se requiere Windows SDK, que incluye los archivos de encabezado que permiten el acceso a componentes del sistema operativo Windows. De forma predeterminada, Visual Studio instala el SDK de Windows como un componente de la carga de trabajo de escritorio de C++, que permite el desarrollo de aplicaciones de Windows Universal. Para desarrollar aplicaciones para UWP, necesitará la versión de Windows 10 del SDK de Windows. Para obtener información, consulte [SDK de Windows 10](https://dev.windows.com/downloads/windows-10-sdk). (Para obtener más información sobre los SDK de Windows para las versiones anteriores de Windows, consulte el [archivo de Windows SDK](https://developer.microsoft.com/windows/downloads/sdk-archive)). 

**Programar archivos (x86) \Windows Kits** es la ubicación predeterminada para todas las versiones del SDK de Windows que ha instalado.

Otras plataformas como Xbox y Azure cuentan con sus propios SDK que puede que tenga que instalar. Para obtener más información, vea el Centro para desarrolladores de DirectX y el Centro para desarrolladores de Azure.

## <a name="development-tools"></a>Herramientas del programador

Visual Studio incluye un depurador eficaz de código nativo, herramientas de análisis estático, herramientas de depuración de gráficos, un editor de código completo, compatibilidad con pruebas unitarias, y muchas otras herramientas y utilidades. Para obtener más información, consulte [comience a desarrollar con Visual Studio](/visualstudio/ide/get-started-developing-with-visual-studio), y [IDE y herramientas de desarrollo](../ide/ide-and-tools-for-visual-cpp-development.md).

## <a name="related-articles"></a>Artículos relacionados

|Título|Descripción|
|-----------|-----------------|
|[Visual C++](../visual-cpp-in-visual-studio.md)|Tema primario para el contenido del desarrollador de Visual C++.|