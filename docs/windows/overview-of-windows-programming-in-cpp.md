---
title: Información general de la programación para Windows en C++
ms.date: 09/17/2019
ms.assetid: efc691d7-21f3-47ae-ae56-cab999ccf59d
ms.openlocfilehash: 8ab7fbf7c955b1c828ef583aa639eda7409cf167
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81359942"
---
# <a name="overview-of-windows-programming-in-c"></a>Información general de la programación para Windows en C++

Hay varias categorías amplias de aplicaciones de Windows que puede crear con C++. Cada uno tiene su propio modelo de programación y un conjunto de bibliotecas específicas de Windows, pero la biblioteca estándar C++ y las bibliotecas C++ de terceros se pueden utilizar en cualquiera de ellas.

En esta sección se describe cómo usar Visual Studio y las bibliotecas contenedoras MFC/ATL para crear programas de Windows. Para obtener documentación sobre la propia plataforma Windows, consulte la documentación de [Windows.](/windows/index)

## <a name="command-line-console-applications"></a>Aplicaciones de línea de comandos (consola)

Las aplicaciones de consola C++ se ejecutan desde la línea de comandos en una ventana de consola y solo pueden mostrar la salida de texto. Para obtener más información, consulte Crear un proyecto de aplicación de [consola C++.](../get-started/tutorial-console-cpp.md)

## <a name="native-desktop-client-applications"></a>Aplicaciones cliente de escritorio nativas

Una *aplicación cliente* de escritorio nativa es una aplicación con ventanas C o C++ que utiliza las API nativas originales de Windows C o las API del modelo de objetos componentes [(COM)](/windows/win32/apiindex/windows-api-list) para tener acceso al sistema operativo. Esas API se escriben principalmente en C. Hay más de una manera de crear una aplicación de escritorio nativa: puede programar utilizando las API de Win32 directamente, utilizando un bucle de mensajes de estilo C que procesa los eventos del sistema operativo. O bien, puede programar mediante *Microsoft Foundation Classes* (MFC), una biblioteca C++ ligeramente orientada a objetos que ajusta Win32. Ninguno de los dos enfoques se considera "moderno" en comparación con la Plataforma universal de Windows (UWP), pero ambos siguen siendo totalmente compatibles y tienen millones de líneas de código ejecutándose en el mundo hoy en día. Una aplicación Win32 que se ejecuta en una ventana requiere que el desarrollador trabaje explícitamente con mensajes de Windows dentro de una función de procedimiento de Windows. A pesar del nombre, una aplicación Win32 se puede compilar como un binario de 32 bits (x86) o 64 bits (x64). En el IDE de Visual Studio, los términos x86 y Win32 son sinónimos.

Para empezar a utilizar la programación tradicional de Windows C++, consulte [Introducción a Win32 y C++.](/windows/win32/LearnWin32/learn-to-program-for-windows) Después de obtener un poco de comprensión de Win32, será más fácil aprender acerca de las aplicaciones de [escritorio MFC](../mfc/mfc-desktop-applications.md). Para obtener un ejemplo de una aplicación de escritorio C++ tradicional que utiliza gráficos sofisticados, consulte [Hilo: Developing C++ Applications for Windows](https://msdn.microsoft.com/library/windows/desktop/ff708696.aspx).

### <a name="c-or-net"></a>¿C++ o .NET?

En general, la programación de .NET en C- es menos compleja, menos propensa a errores y tiene una API orientada a objetos más moderna que Win32 o MFC. En la mayoría de los casos, su rendimiento es más que adecuado. .NET cuenta con Windows Presentation Foundation (WPF) para gráficos enriquecidos y puede consumir Win32 y la API moderna de Windows en tiempo de ejecución. Como regla general, recomendamos usar C++ para aplicaciones de escritorio cuando necesite:

- control preciso sobre el uso de memoria
- la máxima economía en el consumo de energía
- uso de la GPU para la computación general
- acceso a DirectX
- uso intensivo de las bibliotecas estándar de C++

También es posible combinar la potencia y la eficiencia de C++ con la programación .NET. Puede crear una interfaz de usuario en C- y utilizar C++/CLI para permitir que la aplicación consuma bibliotecas nativas de C++. Para obtener más información, consulte Programación de [.NET con C++/CLI](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md).

## <a name="com-components"></a>Componentes COM

El modelo de objetos componentes [(COM)](/windows/win32/com/the-component-object-model) es una especificación que permite que los programas escritos en diferentes idiomas se comuniquen entre sí. Muchos componentes de Windows se implementan como objetos COM y siguen reglas COM estándar para la creación de objetos, la detección de interfaces y la destrucción de objetos.  El uso de objetos COM de aplicaciones de escritorio C++ es relativamente sencillo, pero escribir su propio objeto COM es más avanzado. [Active Template Library (ATL)](../atl/atl-com-desktop-components.md) proporciona macros y funciones auxiliares que simplifican el desarrollo COM. Para obtener más información, consulte Componentes de [escritorio COM de ATL.](../atl/atl-com-desktop-components.md)

## <a name="universal-windows-platform-apps"></a>Aplicaciones de la Plataforma universal de Windows

La Plataforma universal de Windows (UWP) es la API de Windows moderna. Las aplicaciones para UWP se ejecutan en cualquier dispositivo Windows 10, usan XAML para la interfaz de usuario y están totalmente habilitadas para el tacto. Para obtener más información acerca de UWP, consulta ¿Qué es una aplicación para la Plataforma universal de [Windows (UWP)?](/windows/uwp/get-started/whats-a-uwp) y [Guía de aplicaciones universales](/windows/uwp/get-started/universal-application-platform-guide)de Windows .

La compatibilidad original de C++ para UWP consistía en (1) C++/CX, un dialecto de C++ con extensiones de sintaxis, o (2) la biblioteca en tiempo de ejecución de Windows (WRL), que se basa en C++ y COM estándar. Tanto C++/CX como WRL siguen siendo compatibles. Para nuevos proyectos, recomendamos [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt), que se basa totalmente en C+ + estándar y proporciona un rendimiento más rápido.

## <a name="desktop-bridge"></a>Puente de dispositivo de escritorio

En Windows 10, puedes empaquetar la aplicación de escritorio existente o el objeto COM como una aplicación para UWP y agregar características para UWP, como tocar o llamar a las API desde el conjunto de API de Windows moderno. También puedes agregar una aplicación para UWP a una solución de escritorio en Visual Studio y empaquetarlas en un solo paquete y usar las API de Windows para comunicarse entre ellas.

Visual Studio 2017 versión 15.4 y versiones posteriores le permite crear un proyecto de paquete de aplicación de Windows para simplificar en gran medida el trabajo de empaquetado de la aplicación de escritorio existente. Se aplican algunas restricciones a las llamadas del Registro o a las API que puede usar la aplicación de escritorio. Sin embargo, en muchos casos puede crear rutas de código alternativas para lograr una funcionalidad similar mientras se ejecuta en un paquete de aplicación. Para obtener más información, vea [Puente de dispositivo de escritorio](/windows/uwp/porting/desktop-to-uwp-root).

## <a name="games"></a>Juegos

Los juegos de DirectX se pueden ejecutar en el PC o Xbox. Para obtener más información, consulte [Gráficos y juegos de DirectX](/windows/win32/directx).

## <a name="sql-server-database-clients"></a>Clientes de base de datos de SQL Server

Para tener acceso a las bases de datos de SQL Server desde código nativo, use ODBC u OLE DB. Para obtener más información, consulte [SQL Server Native Client](/sql/relational-databases/native-client/odbc/sql-server-native-client-odbc).

## <a name="windows-device-drivers"></a>Controladores de dispositivos de Windows

Los controladores son componentes de bajo nivel que hacen que los datos de los dispositivos de hardware sean accesibles para las aplicaciones y otros componentes del sistema operativo. Para obtener más información, consulte Kit de controladores de [Windows (WDK)](/windows-hardware/drivers/index).

## <a name="windows-services"></a>Servicios de Windows

Un *servicio* de Windows es un programa que se puede ejecutar en segundo plano con poca o ninguna interacción del usuario. Estos programas se denominan *demonios* en sistemas UNIX. Para obtener más información, consulte [Servicios](/windows/win32/services/services).

## <a name="sdks-libraries-and-header-files"></a>SDKs, bibliotecas y archivos de encabezado

Visual Studio incluye la biblioteca en tiempo de ejecución de C (CRT), la biblioteca estándar de C++ y otras bibliotecas específicas de Microsoft. La mayoría de las carpetas de inclusión que contienen archivos de encabezado para estas bibliotecas se encuentran en el directorio de instalación de Visual Studio, en la carpeta . Los archivos de encabezado de Windows y CRT se encuentran en la carpeta de instalación de Windows SDK.

El administrador de [paquetes Vcpkg](../build/vcpkg.md) le permite instalar convenientemente cientos de bibliotecas de código abierto de terceros para Windows.

Las bibliotecas de Microsoft incluyen:

- Microsoft Foundation Classes (MFC): un marco de trabajo orientado a objetos para crear programas tradicionales de Windows, especialmente aplicaciones empresariales, que tienen interfaces de usuario complejas con botones, cuadros de lista, vistas de árbol y otros controles. Para obtener más información, consulta [MFC Desktop Applications](../mfc/mfc-desktop-applications.md).

- Active Template Library (ATL): una biblioteca del asistente eficaz para crear componentes COM. Para obtener más información, consulta [ATL COM Desktop Components](../atl/atl-com-desktop-components.md).

- C++ AMP (C++ Accelerated Massive Parallelism): una biblioteca que habilita el trabajo de proceso general de alto rendimiento en la GPU. Para obtener más información, consulta [C++ AMP (C++ Accelerated Massive Parallelism)](../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md).

- Runtime de simultaneidad: una biblioteca que simplifica el trabajo de programación paralela y asincrónica para dispositivos de varios núcleos. Para obtener más información, consulta [Concurrency Runtime](../parallel/concrt/concurrency-runtime.md).

En muchos escenarios de programación para Windows también se requiere Windows SDK, que incluye los archivos de encabezado que permiten el acceso a componentes del sistema operativo Windows. De forma predeterminada, Visual Studio instala el SDK de Windows como un componente de la carga de trabajo de escritorio de C++, que permite el desarrollo de aplicaciones universales de Windows. Para desarrollar aplicaciones para UWP, necesitas la versión de Windows 10 del Windows SDK. Para obtener más información, consulte SDK de [Windows 10](https://dev.windows.com/downloads/windows-10-sdk). (Para obtener más información acerca de los SDK de Windows para versiones anteriores de Windows, vea el archivo de [Windows SDK](https://developer.microsoft.com/windows/downloads/sdk-archive)).

Archivos de programa **(x86)-Kits** de Windows es la ubicación predeterminada para todas las versiones del SDK de Windows que ha instalado.

Otras plataformas como Xbox y Azure cuentan con sus propios SDK que puede que tenga que instalar. Para obtener más información, vea el Centro para desarrolladores de DirectX y el Centro para desarrolladores de Azure.

## <a name="development-tools"></a>Herramientas de desarrollo

Visual Studio incluye un depurador eficaz de código nativo, herramientas de análisis estático, herramientas de depuración de gráficos, un editor de código completo, compatibilidad con pruebas unitarias, y muchas otras herramientas y utilidades. Para obtener más información, vea [Introducción al desarrollo con Visual Studio](/visualstudio/ide/get-started-developing-with-visual-studio)y Información general sobre el desarrollo de [C++ en Visual Studio](../overview/overview-of-cpp-development.md).

## <a name="in-this-section"></a>En esta sección

|Título|Descripción|
|-----------|-----------------|
|[Tutorial: Creación de un programa C++ estándar](walkthrough-creating-a-standard-cpp-program-cpp.md)| Cree una aplicación de consola de Windows.|
|[Tutorial: Crear aplicaciones de escritorio de Windows (C++)](walkthrough-creating-windows-desktop-applications-cpp.md)|Cree una aplicación de escritorio nativa de Windows.|
|[Asistente para escritorio de Windows](windows-desktop-wizard.md)|Utilice el asistente para crear nuevos proyectos de Windows.|
|[Biblioteca de plantillas activas (ATL)](../atl/atl-com-desktop-components.md)|Utilice la biblioteca ATL para crear componentes COM en C++.|
|[Microsoft Foundation Classes (MFC)](../mfc/mfc-desktop-applications.md)|Utilice MFC para crear aplicaciones windows grandes o pequeñas con cuadros de diálogo y controles|
|[Clases compartidas ATL y MFC](../atl-mfc-shared/atl-mfc-shared-classes.md)|Use clases como CString que se comparten en ATL y MFC.|
|[Acceso a datos](../data/data-access-in-cpp.md)| OLE DB y ODBC|
|[Texto y cadenas](../text/text-and-strings-in-visual-cpp.md)|Varios tipos de cadena en Windows.|
|[Recursos para crear un juego con DirectX](resources-for-creating-a-game-using-directx.md)
|[Procedimiento de uso del SDK de Windows 10 en una aplicación de escritorio de Windows](how-to-use-the-windows-10-sdk-in-a-windows-desktop-application.md)|Windows SDK|
|[Trabajar con archivos de recursos](working-with-resource-files.md)|Cómo agregar imágenes, iconos, tablas de cadenas y otros recursos a una aplicación de escritorio.|
|[Recursos para crear un juego usando DirectX (C++)](resources-for-creating-a-game-using-directx.md)|Enlaces al contenido para crear juegos en C++.|
|[Procedimiento de uso del SDK de Windows 10 en una aplicación de escritorio de Windows](how-to-use-the-windows-10-sdk-in-a-windows-desktop-application.md)|Indica los pasos necesarios para configurar el proyecto de desarrollo con el SDK de Windows 10.|
|[Implementación de aplicaciones de escritorio nativas](deploying-native-desktop-applications-visual-cpp.md)|Implemente aplicaciones nativas en Windows.|

## <a name="related-articles"></a>Artículos relacionados

|Título|Descripción|
|-----------|-----------------|
|[C++ en Visual Studio](../overview/visual-cpp-in-visual-studio.md)|Tema principal para el contenido del desarrollador de Visual C++.|
[Desarrollo de .NET con C++/CLI](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)|Cree contenedores para bibliotecas nativas de C++ que le permitan la comunicación con aplicaciones y componentes de .NET.|
|[Extensiones de componentes para .NET y UWP](../extensions/component-extensions-for-runtime-platforms.md)|Referencia para elementos de sintaxis compartidos por C++/CX y C++/CLI.|
|[Aplicaciones Windows universales (C++)](../cppcx/universal-windows-apps-cpp.md)|Escribe aplicaciones para UWP con C++/CX o la biblioteca de plantillas de Windows en tiempo de ejecución (WRL).|
|[Atributos de C++ para COM y .NET](attributes/cpp-attributes-com-net.md)|Atributos no estándar para programación solo de Windows mediante .NET o COM.|
