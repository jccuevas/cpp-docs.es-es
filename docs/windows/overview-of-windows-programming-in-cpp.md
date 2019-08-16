---
title: Información general de la programación para Windows en C++
ms.date: 07/28/2019
ms.assetid: efc691d7-21f3-47ae-ae56-cab999ccf59d
ms.openlocfilehash: 10ef9698e27099d5856c1ed5f8ed2f21cea72c24
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514794"
---
# <a name="overview-of-windows-programming-in-c"></a>Información general de la programación para Windows en C++

Hay varias categorías amplias de aplicaciones Windows que se pueden crear con C++. Cada uno tiene su propio modelo de programación y conjunto de bibliotecas específicas de Windows, C++ pero la biblioteca estándar y las C++ bibliotecas de terceros se pueden usar en cualquiera de ellas. 

En esta sección se describe cómo usar Visual Studio y las bibliotecas contenedoras de MFC y ATL para crear programas de Windows. Para obtener documentación sobre la propia plataforma Windows, consulte la [documentación de Windows](/windows/index).

## <a name="command-line-console-applications"></a>Aplicaciones de línea de comandos (consola)

Las aplicaciones de consola de C++ se ejecutan desde la línea de comandos en una ventana de consola y solo pueden mostrar la salida de texto. Para obtener más información, consulte [Aplicaciones de consola](console-applications-in-visual-cpp.md).

## <a name="native-desktop-client-applications"></a>Aplicaciones cliente de escritorio nativo

Una *aplicación cliente de escritorio nativo* es una aplicación C++ de c o con ventanas que usa las API nativas de [Windows c originales o las API del modelo de objetos componentes (com)](/windows/win32/apiindex/windows-api-list) para tener acceso al sistema operativo. Esas API se escriben principalmente en C. Hay más de una manera de crear una aplicación de escritorio nativo: Puede programar mediante las API de Win32 directamente, mediante un bucle de mensajes de estilo C que procesa los eventos del sistema operativo. O bien, puede programar con *Microsoft Foundation Classes* (MFC), una biblioteca ligeramente orientada C++ a objetos que contiene Win32. Ninguno de los enfoques se considera "moderno" en comparación con el Plataforma universal de Windows (UWP), pero ambos siguen siendo totalmente compatibles y tienen millones de líneas de código que se ejecutan en el mundo de hoy en día. Una aplicación de Win32 que se ejecuta en una ventana requiere que el desarrollador trabaje explícitamente con mensajes de Windows dentro de una función de procedimiento de Windows. A pesar del nombre, una aplicación Win32 se puede compilar como un binario de 32 bits (x86) o 64 bits (x64). En el IDE de Visual Studio, los términos x86 y Win32 son sinónimos.

Para empezar a trabajar con la C++ programación tradicional de Windows, consulte Introducción [a C++Win32 y ](/windows/win32/LearnWin32/learn-to-program-for-windows). Una vez que conozca el funcionamiento de Win32, será más fácil obtener información sobre [las aplicaciones de escritorio de MFC](../mfc/mfc-desktop-applications.md). Para ver un ejemplo de una C++ aplicación de escritorio tradicional que usa gráficos sofisticados, consulte [hilo: Desarrollo C++ de aplicaciones para](https://msdn.microsoft.com/library/windows/desktop/ff708696.aspx)Windows.

### <a name="c-or-net"></a>C++o .NET?

En general, la programación de C# .net en es menos compleja, menos propensa a errores y tiene una API orientada a objetos más moderna que Win32 o MFC. En la mayoría de los casos, su rendimiento es más que adecuado. .NET incluye el Windows Presentation Foundation (WPF) para gráficos enriquecidos, y puede consumir tanto Win32 como la API moderna Windows Runtime. Como norma general, se recomienda usar C++ para aplicaciones de escritorio cuando necesite lo siguiente:

- control preciso del uso de memoria
- la mayor economía en el consumo de energía
- uso de la GPU para la informática general
- acceso a DirectX
- uso intensivo de las C++ bibliotecas estándar

También es posible combinar la eficacia y la eficacia de con C++ la programación de .net. Puede crear una interfaz de usuario en C# y usar C++/CLI para permitir que la aplicación consuma bibliotecas C++ nativas. Para obtener más información, vea [programación de C++.net con/CLI](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md).

## <a name="com-components"></a>Componentes COM

El [Modelo de objetos componentes (COM)](/windows/win32/com/the-component-object-model) es una especificación que permite que los programas escritos en lenguajes diferentes se comuniquen entre sí. Muchos componentes de Windows se implementan como objetos COM y siguen las reglas COM estándar para la creación de objetos, la detección de interfaces y la destrucción de objetos.  El uso de objetos C++ com desde aplicaciones de escritorio es relativamente sencillo, pero escribir su propio objeto com es más avanzado. En [Active Template Library (ATL)](../atl/atl-com-desktop-components.md) se proporcionan macros y funciones auxiliares que simplifican el desarrollo de COM. Para obtener más información, vea [componentes de escritorio com de ATL](../atl/atl-com-desktop-components.md).

## <a name="universal-windows-platform-apps"></a>Aplicaciones de la Plataforma universal de Windows

El Plataforma universal de Windows (UWP) es la API moderna de Windows. Las aplicaciones de UWP se ejecutan en cualquier dispositivo de Windows 10, usan XAML para la interfaz de usuario y están totalmente habilitados para la interacción. Para obtener más información sobre UWP, consulte [¿Qué es una aplicación plataforma universal de Windows (UWP)?](/windows/uwp/get-started/whats-a-uwp) y [Guía para aplicaciones universales de Windows](/windows/uwp/get-started/universal-application-platform-guide).

La compatibilidad C++ original con UWP constaba de (1) C++/CX, un dialecto de C++ con extensiones de sintaxis o (2) la biblioteca de Windows Runtime (WRL), que se basa en C++ estándares y com. Tanto C++/CX como WRL todavía se admiten. En el caso de los proyectos nuevos, se recomienda [ C++/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt), que se C++ basa completamente en el estándar y proporciona un rendimiento más rápido.

## <a name="desktop-bridge"></a>Puente de escritorio

En Windows 10, puede empaquetar la aplicación de escritorio existente o el objeto COM como una aplicación de UWP y agregar características de UWP como Touch o llamar a las API desde el conjunto de API de Windows moderno. También puede Agregar una aplicación de UWP a una solución de escritorio en Visual Studio y empaquetarlas juntas en un único paquete y usar las API de Windows para comunicarse entre ellas.

Visual Studio 2017, versión 15,4 y versiones posteriores, le permite crear un proyecto de paquete de aplicación de Windows para simplificar considerablemente el trabajo de empaquetar la aplicación de escritorio existente. Se aplican algunas restricciones a las llamadas o API del registro que puede usar la aplicación de escritorio. Sin embargo, en muchos casos, puede crear rutas de acceso de código alternativas para lograr una funcionalidad similar mientras se ejecuta en un paquete de la aplicación. Para obtener más información, vea [Puente de dispositivo de escritorio](/windows/uwp/porting/desktop-to-uwp-root).

## <a name="games"></a>Juegos

Los juegos de DirectX se pueden ejecutar en PC o en Xbox. Para obtener más información, consulte [gráficos y juegos de DirectX](/windows/win32/directx).

## <a name="sql-server-database-clients"></a>Clientes de SQL Server Database

Para tener acceso a las bases de datos de SQL Server desde código nativo, use ODBC o OLE DB. Para obtener más información, consulte [SQL Server Native Client](/sql/relational-databases/native-client/odbc/sql-server-native-client-odbc).

## <a name="windows-device-drivers"></a>Controladores de dispositivos de Windows

Los controladores son componentes de bajo nivel que hacen que los datos de los dispositivos de hardware sean accesibles a las aplicaciones y otros componentes del sistema operativo. Para obtener más información, consulte [Kit de controladores de Windows (WDK)](/windows-hardware/drivers/index).

## <a name="windows-services"></a>Servicios de Windows

Un *servicio* de Windows es un programa que se puede ejecutar en segundo plano con poca o ninguna interacción del usuario. Estos programas se denominan *demonios* en sistemas Unix. Para obtener más información, consulte [servicios](/windows/win32/services/services).

## <a name="sdks-libraries-and-header-files"></a>SDK, bibliotecas y archivos de encabezado

Visual Studio incluye la biblioteca en tiempo de ejecución de C ( C++ CRT), la biblioteca estándar y otras bibliotecas específicas de Microsoft. La mayoría de las carpetas de inclusión que contienen archivos de encabezado para estas bibliotecas se encuentran en el directorio de instalación de Visual Studio, en la carpeta \VC\; Los archivos de encabezado de Windows y CRT se encuentran en la carpeta de instalación de Windows SDK.

El [Administrador de paquetes de Vcpkg](../build/vcpkg.md) le permite instalar de forma cómoda cientos de bibliotecas de código abierto de terceros para Windows.

Las bibliotecas de Microsoft incluyen:

- Microsoft Foundation Classes (MFC): Marco de trabajo orientado a objetos para crear programas tradicionales de Windows, especialmente aplicaciones empresariales, que tienen interfaces de usuario enriquecidas que incluyen botones, cuadros de lista, vistas de árbol y otros controles. Para obtener más información, consulta [MFC Desktop Applications](../mfc/mfc-desktop-applications.md).

- Active Template Library (ATL): Biblioteca auxiliar eficaz para crear componentes COM. Para obtener más información, consulta [ATL COM Desktop Components](../atl/atl-com-desktop-components.md).

- C++AMP (C++ paralelismo masivo acelerado): Una biblioteca que habilita el trabajo de cálculo general de alto rendimiento en la GPU. Para obtener más información, consulta [C++ AMP (C++ Accelerated Massive Parallelism)](../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md).

- Runtime de simultaneidad: Biblioteca que simplifica el trabajo de programación paralela y asincrónica para dispositivos de varios núcleos y núcleos. Para obtener más información, consulta [Concurrency Runtime](../parallel/concrt/concurrency-runtime.md).

En muchos escenarios de programación para Windows también se requiere Windows SDK, que incluye los archivos de encabezado que permiten el acceso a componentes del sistema operativo Windows. De forma predeterminada, Visual Studio instala el Windows SDK como un componente de la C++ carga de trabajo de escritorio, que permite el desarrollo de aplicaciones universales de Windows. Para desarrollar aplicaciones para UWP, necesita la versión de Windows 10 de la Windows SDK. Para obtener más información, consulte el [SDK de Windows 10](https://dev.windows.com/downloads/windows-10-sdk). (Para obtener más información sobre los SDK de Windows para versiones anteriores de Windows, consulte el [archivo Windows SDK](https://developer.microsoft.com/windows/downloads/sdk-archive)).

**Archivos de programa (x86) \Windows kits** es la ubicación predeterminada de todas las versiones de los Windows SDK que ha instalado.

Otras plataformas como Xbox y Azure cuentan con sus propios SDK que puede que tenga que instalar. Para obtener más información, vea el Centro para desarrolladores de DirectX y el Centro para desarrolladores de Azure.

## <a name="development-tools"></a>Herramientas del programador

Visual Studio incluye un depurador eficaz de código nativo, herramientas de análisis estático, herramientas de depuración de gráficos, un editor de código completo, compatibilidad con pruebas unitarias, y muchas otras herramientas y utilidades. Para obtener más información, vea Introducción al desarrollo [con Visual Studio](/visualstudio/ide/get-started-developing-with-visual-studio)e información [General C++ sobre el desarrollo en Visual Studio](../overview/overview-of-cpp-development.md).

## <a name="in-this-section"></a>En esta sección
|Title|DESCRIPCIÓN|
|-----------|-----------------|
|[Tutorial: Creación de un programa de C++ estándar](walkthrough-creating-a-standard-cpp-program-cpp.md)| Cree una aplicación de consola de Windows.|
|[Tutorial: Crear aplicaciones de escritorio de Windows (C++)](walkthrough-creating-windows-desktop-applications-cpp.md)|Cree una aplicación de escritorio de Windows nativa.|
|[Asistente para escritorio de Windows](windows-desktop-wizard.md)|Use el Asistente para crear nuevos proyectos de Windows.|
|[Biblioteca de plantillas activas (ATL)](../atl/atl-com-desktop-components.md)|Utilice la biblioteca ATL para crear componentes COM en C++.|
|[Microsoft Foundation Classes (MFC)](../mfc/mfc-desktop-applications.md)|Usar MFC para crear aplicaciones de Windows grandes o pequeñas con cuadros de diálogo y controles|
|[Clases compartidas ATL y MFC](../atl-mfc-shared/atl-mfc-shared-classes.md)|Usar clases como CString compartidas en ATL y MFC.|
|[Acceso a datos](../data/data-access-in-cpp.md)| OLE DB y ODBC|
|[Texto y cadenas](../text/text-and-strings-in-visual-cpp.md)|Varios tipos de cadena en Windows.|
|[Recursos para crear un juego mediante DirectX](resources-for-creating-a-game-using-directx.md)
|[Cómo: Usar el SDK de Windows 10 en una aplicación de escritorio de Windows](how-to-use-the-windows-10-sdk-in-a-windows-desktop-application.md)|Windows SDK|
|[Trabajo con archivos de recursos](working-with-resource-files.md)|Cómo agregar imágenes, iconos, tablas de cadenas y otros recursos a una aplicación de escritorio.|
|[Recursos para crear un juego con DirectX (C++)](resources-for-creating-a-game-using-directx.md)|Vínculos a contenido para crear juegos en C++.|
|[Procedimientos: Usar el SDK de Windows 10 en una aplicación de escritorio de Windows](how-to-use-the-windows-10-sdk-in-a-windows-desktop-application.md)|Indica los pasos necesarios para configurar el proyecto de desarrollo con el SDK de Windows 10.|
|[Implementación de aplicaciones de escritorio nativas](deploying-native-desktop-applications-visual-cpp.md)|Implementar aplicaciones nativas en Windows.|

## <a name="related-articles"></a>Artículos relacionados

|Título|DESCRIPCIÓN|
|-----------|-----------------|
|[C++ en Visual Studio](../overview/visual-cpp-in-visual-studio.md)|Tema primario del contenido C++ del desarrollador visual.|
[Desarrollo de .NET con C++/CLI](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)|Cree contenedores para bibliotecas nativas C++ que permitan la comunicación con aplicaciones y componentes de .net.|
|[Extensiones de componentes de .NET y UWP](../extensions/component-extensions-for-runtime-platforms.md)|Referencia de los elementos de sintaxis C++compartidos por/CX y C++/CLI.|
|[Aplicaciones de Windows universales (C++)](../cppcx/universal-windows-apps-cpp.md)|Escriba aplicaciones para UWP C++con/cx o Windows Runtime biblioteca de plantillas (WRL).|
|[Atributos de C++ para COM y .NET](attributes/cpp-attributes-com-net.md)|Atributos no estándar para la programación solo de Windows mediante .NET o COM.|
