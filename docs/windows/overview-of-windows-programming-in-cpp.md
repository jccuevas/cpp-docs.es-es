---
title: Información general de la programación para Windows en C++
ms.date: 07/02/2019
ms.assetid: efc691d7-21f3-47ae-ae56-cab999ccf59d
ms.openlocfilehash: 1f49c9f8f78f83d6ae991b7427b28f7f5cbf7f0c
ms.sourcegitcommit: 9b904e490b1e262293a602bd1291a8f3045e755b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/03/2019
ms.locfileid: "67552302"
---
# <a name="overview-of-windows-programming-in-c"></a>Información general de la programación para Windows en C++

Existen varias categorías de aplicaciones de Windows que se pueden crear con C++. Cada uno tiene su propio modelo de programación y un conjunto de bibliotecas específicas de Windows, pero la C++ biblioteca estándar y terceros C++ bibliotecas pueden usarse en cualquiera de ellos.

## <a name="command-line-console-applications"></a>Aplicaciones de línea de comandos (consola)

Las aplicaciones de consola de C++ se ejecutan desde la línea de comandos en una ventana de consola y solo pueden mostrar la salida de texto. Para obtener más información, consulte [Aplicaciones de consola](console-applications-in-visual-cpp.md).

## <a name="native-desktop-client-applications"></a>Aplicaciones cliente de escritorio nativas

Un *aplicación cliente de escritorio nativa* es una C o C++ aplicación división de particiones que utiliza la nativa original [las API de C de Windows o el modelo de objetos componentes (COM) API](/windows/desktop/apiindex/windows-api-list) para tener acceso al sistema operativo. Estas API son escrito principalmente en C. Hay más de una forma de crear una aplicación de escritorio nativa: Puede programar mediante las API Win32 directamente, utilizando un bucle de mensajes de estilo C que procesa los eventos del sistema operativo. O bien, puede programar utilizando *Microsoft Foundation Classes* (MFC), un menor grado orientada a objetos C++ biblioteca que encapsula Win32. No se considera "moderno" enfoque en comparación a la plataforma Universal de Windows (UWP), pero ambas siguen siendo totalmente compatibles y tienen millones de líneas de código que se ejecuta en el mundo de hoy en día. Una aplicación de Win32 que se ejecuta en una ventana requiere que el desarrollador trabaje explícitamente con mensajes de Windows dentro de una función de procedimiento de Windows. A pesar del nombre, una aplicación Win32 puede compilarse como una (x86) 32 bits o 64 bits (x64) binario. En el IDE de Visual Studio, los términos x86 y Win32 son sinónimos.

Para empezar a trabajar con programación C++ tradicional de Windows, consulte [empezar a trabajar con Win32 y C++](/windows/desktop/LearnWin32/learn-to-program-for-windows). Después de tener cierto conocimiento de Win32, será más fácil obtener información sobre [MFC Desktop Applications](../mfc/mfc-desktop-applications.md). Para obtener un ejemplo de una aplicación de escritorio de C++ tradicional que usa gráficos sofisticados, consulte [Hilo: Desarrollo de aplicaciones de C++ para Windows](https://msdn.microsoft.com/library/windows/desktop/ff708696.aspx).

### <a name="c-or-net"></a>¿C++ o. NET?

En general, programación de .NET en C# es menos compleja, menos propensas a errores y tiene una API orientada a objetos más moderna que Win32 o MFC. En la mayoría de los casos, su rendimiento es más que adecuado. Windows Presentation Foundation (WPF) para gráficos enriquecidos de .NET Framework, y puede consumir Win32 y la API de tiempo de ejecución de Windows moderna. Como norma general, se recomienda usar C++ para aplicaciones de escritorio cuando necesite lo siguiente:

- control preciso sobre el uso de memoria
- la mayor economía en consumo de energía
- uso de la GPU para el cálculo general
- acceso a DirectX
- uso intensivo de bibliotecas estándar de C++

También es posible combinar la eficacia y la eficacia de C++ con programación de. NET. Puede crear una interfaz de usuario en C# y usar C / c++ / CLI para habilitar la aplicación para utilizar bibliotecas nativas de C++. Para obtener más información, consulte [programación de .NET con C++ / c++ / CLI](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md).

## <a name="com-components"></a>Componentes COM

El [Modelo de objetos componentes (COM)](/windows/desktop/com/the-component-object-model) es una especificación que permite que los programas escritos en lenguajes diferentes se comuniquen entre sí. Muchos componentes de Windows se implementan como objetos COM y seguir las reglas COM estándares para la creación de objetos, detección de interfaz y la destrucción de objetos.  Usar objetos COM desde aplicaciones de escritorio de C++ es relativamente sencillo, pero escribir su propio objeto COM es más avanzado. En [Active Template Library (ATL)](../atl/atl-com-desktop-components.md) se proporcionan macros y funciones auxiliares que simplifican el desarrollo de COM. Para obtener más información, consulte [componentes de escritorio ATL COM](../atl/atl-com-desktop-components.md).

## <a name="universal-windows-platform-apps"></a>Aplicaciones de la Plataforma universal de Windows

La plataforma Universal de Windows (UWP) es la API de Windows moderna. Las aplicaciones para UWP ejecutan en cualquier dispositivo Windows 10, usar XAML para la interfaz de usuario y están totalmente habilitados para toque. Para obtener más información sobre UWP, consulte [¿qué es una aplicación de plataforma Universal de Windows (UWP)?](/windows/uwp/get-started/whats-a-uwp) y [guía para aplicaciones universales de Windows](/windows/uwp/get-started/universal-application-platform-guide).

La versión original C++ la compatibilidad con UWP consistió en (1) C++/CX, un dialecto de C++ con las extensiones de sintaxis, o (2) la biblioteca de Windows en tiempo de ejecución (WRL), que se basa en estándar C++ y COM. C++ / c++ / CX y WRL todavía se admiten. Para proyectos nuevos, se recomienda [ C++/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt), que se basa completamente en estándar C++ y proporciona un rendimiento más rápido.

## <a name="desktop-bridge"></a>Puente de escritorio

En Windows 10, puede empaquetar su aplicación de escritorio existente o un objeto COM como una aplicación para UWP y agregar características UWP como toque o llamar a API desde el conjunto de API de Windows moderno. También puede agregar una aplicación para UWP a una solución de escritorio en Visual Studio y el paquete de ellos juntos en un único paquete y usan las API de Windows para comunicarse entre ellos.

Visual Studio 2017 versión 15.4 y versiones posterior le permite crear un proyecto de paquete de aplicación de Windows para simplificar en gran medida el trabajo de empaquetado de la aplicación de escritorio existente. Algunas restricciones se aplican a las llamadas de registro o las API que puede usar la aplicación de escritorio. Sin embargo, en muchos casos puede crear rutas de acceso del código alternativa para lograr una funcionalidad similar mientras se ejecuta en un paquete de aplicación. Para obtener más información, vea [Puente de dispositivo de escritorio](/windows/uwp/porting/desktop-to-uwp-root).

## <a name="games"></a>Juegos

Pueden ejecutar juegos de DirectX en PC o en Xbox. Para obtener más información, consulte [juegos y gráficos de DirectX](/windows/desktop/directx).

## <a name="sql-server-database-clients"></a>Clientes de base de datos de SQL Server

Para obtener acceso a las bases de datos de SQL Server desde el código nativo, utilice ODBC u OLE DB. Para obtener más información, consulte [SQL Server Native Client](/sql/relational-databases/native-client/odbc/sql-server-native-client-odbc).

## <a name="windows-device-drivers"></a>Controladores de dispositivos de Windows

Los controladores son los componentes de bajo nivel que facilitan el acceso a aplicaciones de datos de dispositivos de hardware y otros componentes del sistema operativo. Para obtener más información, consulte [Windows Driver Kit (WDK)](/windows-hardware/drivers/index).

## <a name="windows-services"></a>Servicios de Windows

Un Windows *servicio* es un programa que se puede ejecutar en segundo plano con poca o ninguna interacción del usuario. Estos programas se denominan *demonios* en sistemas UNIX. Para obtener más información, consulte [servicios](/windows/desktop/services/services).

## <a name="sdks-libraries-and-header-files"></a>Archivos de encabezado, bibliotecas y SDK

Visual Studio incluye la biblioteca en tiempo de ejecución de C (CRT), la biblioteca estándar de C++ y otras bibliotecas específicas de Microsoft. La mayoría de las carpetas de inclusión que contienen archivos de encabezado para estas bibliotecas se encuentra en el directorio de instalación de Visual Studio en la carpeta \VC\. Los archivos de encabezado de Windows y CRT se encuentran en la carpeta de instalación del SDK de Windows.

El [Administrador de paquetes de Vcpkg](../build/vcpkg.md) le permite instalar cómodamente cientos de bibliotecas de código abierto de terceros para Windows.

Las bibliotecas de Microsoft incluyen:

- Microsoft Foundation Classes (MFC): Un marco orientado a objetos para crear programas tradicionales de Windows, especialmente aplicaciones empresariales, que tienen interfaces de usuario enriquecidas, botones, cuadros de lista, vistas de árbol y otros controles. Para obtener más información, consulta [MFC Desktop Applications](../mfc/mfc-desktop-applications.md).

- Active Template Library (ATL): Una biblioteca auxiliar eficaz para crear componentes COM. Para obtener más información, consulta [ATL COM Desktop Components](../atl/atl-com-desktop-components.md).

- C++ AMP (C++ Accelerated Massive Parallelism): Una biblioteca que permite el trabajo de proceso general de alto rendimiento en la GPU. Para obtener más información, consulta [C++ AMP (C++ Accelerated Massive Parallelism)](../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md).

- Runtime de simultaneidad: Una biblioteca que simplifica el trabajo de programación paralela y asincrónica para dispositivos de varios núcleos y varios núcleos. Para obtener más información, consulta [Concurrency Runtime](../parallel/concrt/concurrency-runtime.md).

En muchos escenarios de programación para Windows también se requiere Windows SDK, que incluye los archivos de encabezado que permiten el acceso a componentes del sistema operativo Windows. De forma predeterminada, Visual Studio instala el SDK de Windows como un componente de la carga de trabajo de escritorio de C++, que permite el desarrollo de aplicaciones de Windows Universal. Para desarrollar aplicaciones para UWP, necesitará la versión de Windows 10 del SDK de Windows. Para obtener información, consulte [SDK de Windows 10](https://dev.windows.com/downloads/windows-10-sdk). (Para obtener más información sobre los SDK de Windows para las versiones anteriores de Windows, consulte el [archivo de Windows SDK](https://developer.microsoft.com/windows/downloads/sdk-archive)).

**Programar archivos (x86) \Windows Kits** es la ubicación predeterminada para todas las versiones del SDK de Windows que haya instalado.

Otras plataformas como Xbox y Azure cuentan con sus propios SDK que puede que tenga que instalar. Para obtener más información, vea el Centro para desarrolladores de DirectX y el Centro para desarrolladores de Azure.

## <a name="development-tools"></a>Herramientas del programador

Visual Studio incluye un depurador eficaz de código nativo, herramientas de análisis estático, herramientas de depuración de gráficos, un editor de código completo, compatibilidad con pruebas unitarias, y muchas otras herramientas y utilidades. Para obtener más información, consulte [comience a desarrollar con Visual Studio](/visualstudio/ide/get-started-developing-with-visual-studio), y [desarrollo información general de C++ en Visual Studio](../overview/overview-of-cpp-development.md).

## <a name="in-this-section"></a>En esta sección
|Title|Descripción|
|-----------|-----------------|
|[Tutorial: Creación de un programa de C++ estándar](walkthrough-creating-a-standard-cpp-program-cpp.md)| Cree una aplicación de consola de Windows.|
|[Tutorial: Crear aplicaciones de escritorio de Windows (C++)](walkthrough-creating-windows-desktop-applications-cpp.md)|Crear una aplicación nativa de escritorio de Windows.|
|[Asistente para escritorio de Windows](windows-desktop-wizard.md)|Use el Asistente para crear nuevos proyectos de Windows.|
|[Biblioteca de plantillas activas (ATL)](../atl/atl-com-desktop-components.md)|Utilice la biblioteca ATL para crear componentes COM en C++.|
|[Microsoft Foundation Classes (MFC)](../mfc/mfc-desktop-applications.md)|Usar MFC para crear grandes o pequeñas aplicaciones de Windows con controles y cuadros de diálogo|
|[Clases compartidas ATL y MFC](../atl-mfc-shared/atl-mfc-shared-classes.md)|Utilice las clases como CString que se comparten en ATL y MFC.|
|[Acceso a datos](../data/data-access-in-cpp.md)| OLE DB y ODBC|
|[Texto y cadenas](../text/text-and-strings-in-visual-cpp.md)|Distintos tipos de cadenas en Windows.|
|[Recursos para crear un juego mediante DirectX](resources-for-creating-a-game-using-directx.md)
|[Cómo: Usar el SDK de Windows 10 en una aplicación de escritorio de Windows](how-to-use-the-windows-10-sdk-in-a-windows-desktop-application.md)|Windows SDK|
|[Trabajo con archivos de recursos](working-with-resource-files.md)|Cómo agregar imágenes, iconos, las tablas de cadenas y otros recursos a una aplicación de escritorio.|
|[Recursos para crear un juego usando DirectX (C++)](resources-for-creating-a-game-using-directx.md)|Vínculos a contenido para crear juegos en C++.|
|[Cómo: Usar el SDK de Windows 10 en una aplicación de escritorio de Windows](how-to-use-the-windows-10-sdk-in-a-windows-desktop-application.md)|Indica los pasos necesarios para configurar el proyecto de desarrollo con el SDK de Windows 10.|
|[Implementación de aplicaciones de escritorio nativas](deploying-native-desktop-applications-visual-cpp.md)|Implementar aplicaciones nativas en Windows.|

## <a name="related-articles"></a>Artículos relacionados

|Título|Descripción|
|-----------|-----------------|
|[C++ en Visual Studio](../overview/visual-cpp-in-visual-studio.md)|Tema primario para el contenido del desarrollador de Visual C++.|
[Desarrollo de .NET con C++/CLI](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)|Crear contenedores para las bibliotecas nativas de C++ que le permiten la comunicación con aplicaciones de .NET y componentes.|
|[Extensiones de componentes de .NET y UWP](../extensions/component-extensions-for-runtime-platforms.md)|Referencia de elementos de sintaxis compartidos por C++ / c++ / CX y c++ / CLI.|
|[Aplicaciones de Windows universales (C++)](../cppcx/universal-windows-apps-cpp.md)|Escribir aplicaciones para UWP con C++ / c++ / CX o biblioteca de plantillas de Windows en tiempo de ejecución (WRL).|
|[Atributos de C++ para COM y .NET](attributes/cpp-attributes-com-net.md)|Atributos no estándares para la programación de Windows solo mediante .NET o COM.|
