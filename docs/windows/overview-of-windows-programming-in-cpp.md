---
title: Información general de la programación para Windows en C++
ms.date: 11/15/2018
ms.assetid: efc691d7-21f3-47ae-ae56-cab999ccf59d
ms.openlocfilehash: b33236df6e4c7f679ff1dd9f9f8bc409c86e011a
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/15/2018
ms.locfileid: "51693869"
---
# <a name="overview-of-windows-programming-in-c"></a>Información general de la programación para Windows en C++

Existen varias categorías de aplicaciones de Windows que se pueden crear con C++. Cada uno tiene su propio modelo de programación y el conjunto de bibliotecas específicas de Windows, pero se pueden usar la biblioteca estándar de C++, así como las bibliotecas de C++ de terceros en cualquiera de ellos. 

## <a name="command-line-console-applications"></a>Aplicaciones de línea de comandos (consola)

Las aplicaciones de consola de C++ se ejecutan desde la línea de comandos en una ventana de consola y solo pueden mostrar la salida de texto. Para obtener más información, consulte [Aplicaciones de consola](console-applications-in-visual-cpp.md).
 
## <a name="native-desktop-client-applications"></a>Aplicaciones cliente de escritorio nativas

El término *aplicación cliente de escritorio nativa* hace referencia a una aplicación de división de particiones de C o C++ que usa las API de Win32 de Windows original para tener acceso al sistema operativo. Estas API son escrito principalmente en C. Al crear este tipo de aplicación, tiene la posibilidad de programar directamente con un bucle de mensajes de estilo C que procesa los eventos del sistema operativo, o utilizando *Microsoft Foundation Classes* (MFC), una biblioteca de C++ que se ajusta a Win32 de manera que es un poco orientada a objetos. No se considera "moderna" en comparación con la plataforma Universal de Windows (ver abajo), pero ambas siguen siendo totalmente compatibles y tienen millones de líneas de código que se ejecuta en el mundo de hoy en día.

Para empezar a trabajar con programación C++ tradicional de Windows, consulte [empezar a trabajar con Win32 y C++](/windows/desktop/LearnWin32/learn-to-program-for-windows). Después de tener cierto conocimiento de Win32, será más fácil obtener información sobre [MFC Desktop Applications](/mfc/mfc-desktop-applications). Para obtener un ejemplo de una aplicación de escritorio de C++ tradicional que usa gráficos sofisticados, consulte [Hilo: desarrollar aplicaciones de C++ para Windows](https://msdn.microsoft.com/library/windows/desktop/ff708696.aspx).

### <a name="c-or-net"></a>¿C++ o. NET? 

	Para la mayoría de escenarios de aplicaciones de escritorio (es decir, que no se dirigen a UWP), considere la posibilidad de usar C# y .NET. Esto se debe a que la programación de .NET suele ser menos compleja y menos propensa a errores, además de tener una API orientada a objetos más moderna que Win32 o MFC. En la mayoría de los casos, su rendimiento es más que adecuado. .NET cuenta con Windows Presentation Foundation (WPF) para obtener gráficos enriquecidos, y puede consumir Win32, así como la API moderna de Windows Runtime (consulte UWP a continuación). Como norma general, se recomienda usar C++ para aplicaciones de escritorio cuando necesite lo siguiente:

- control preciso sobre el uso de memoria
- la mayor economía en consumo de energía
- uso de la GPU para el cálculo general
- acceso a DirectX
- uso intensivo de bibliotecas estándar de C++

## <a name="com-components"></a>Componentes COM

Muchas partes del sistema operativo Windows se basan en el modelo de objetos componentes (COM) que define un estándar binario que permite que el componente se utilice en las aplicaciones cliente escritas en cualquier lenguaje informático. Puede usar Active Template Library (ATL) para simplificar el trabajo de crear sus propios componentes COM en C++. Para obtener más información, consulte [modelo de objetos componentes (COM)](/windows/desktop/com/component-object-model--com--portal) y [componentes de escritorio ATL COM](../atl/atl-com-desktop-components.md).

## <a name="windows-universal-apps"></a>Aplicaciones universales de Windows

La plataforma Universal de Windows (UWP) es la API de Windows moderna. Las aplicaciones para UWP ejecutan en cualquier dispositivo Windows 10, usar XAML para la interfaz de usuario y están totalmente habilitados para toque. Para obtener más información sobre UWP, consulte [¿qué es una aplicación de plataforma Universal de Windows (UWP)?](/windows/uwp/get-started/whats-a-uwp) y [guía para aplicaciones universales de Windows](/windows/uwp/get-started/universal-application-platform-guide).

La compatibilidad original de C++ para UWP constaba de (1) C++ / c++ / CX, un dialecto de C++ con las extensiones de sintaxis o (2) la biblioteca de tiempo de ejecución de Windows (WRL) que se basa en el estándar C++ y COM. C++ / c++ / CX y WRL todavía se admiten. Se recomienda para nuevos proyectos [C++ / c++ / WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt) que se basa completamente en C++ estándar y proporciona un rendimiento más rápido. 

Para Windows 10, puede empaquetar la aplicación de escritorio de C++ existente como-es para la implementación a través de la Microsoft Store. Para obtener más información, consulte [empaquetar aplicaciones de escritorio (Desktop Bridge)](/windows/uwp/porting/desktop-to-uwp-root).

## <a name="games"></a>Juegos

Pueden ejecutar juegos de DirectX en PC o en Xbox. Para obtener más información, consulte [juegos y gráficos de DirectX](/windows/desktop/directx).

## <a name="net-wrappers-for-c-libraries"></a>Contenedores de .NET para las bibliotecas de C++

Puede usar C++ / c++ / CLI para crear una capa de interoperabilidad que permite que el código de .NET consumir bibliotecas nativas de C++. Para obtener más información, consulte [programación de .NET con C++ / c++ / CLI](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md).

## <a name="sql-server-database-clients"></a>Clientes de base de datos de SQL Server

Para obtener acceso a las bases de datos de SQL Server desde el código nativo, utilice ODBC u OLE DB. Para obtener más información, consulte [SQL Server Native Client](/sql/relational-databases/native-client/odbc/sql-server-native-client-odbc).

## <a name="windows-device-drivers"></a>Controladores de dispositivos de Windows

Los controladores son los componentes de bajo nivel que facilitan el acceso a aplicaciones de datos de dispositivos de hardware y otros componentes del sistema operativo. Para obtener más información, consulte [Windows Driver Kit (WDK)](/windows-hardware/drivers/index).

## <a name="windows-services"></a>Servicios de Windows

Un Windows *servicio* es un programa que se puede ejecutar en segundo plano con poca o ninguna interacción del usuario. En UNIX se denominan *demonios*. Para obtener más información, consulte [servicios](/windows/desktop/services/services).

## <a name="sdks-libraries-and-header-files"></a>Archivos de encabezado, bibliotecas y SDK

Visual Studio incluye la biblioteca en tiempo de ejecución de C (CRT), la biblioteca estándar de C++ y otras bibliotecas específicas de Microsoft. Las carpetas de inclusión que contienen archivos de encabezado para estas bibliotecas se encuentran en el directorio de instalación de Visual Studio en la carpeta \VC\ o en el caso de CRT, en la carpeta de instalación del SDK de Windows.

Puede usar el [Administrador de paquetes de Vcpkg](../vcpkg.md) para instalar cómodamente cientos de bibliotecas de código abierto de terceros para Windows.

Las bibliotecas de Microsoft incluyen:

- Microsoft Foundation Classes (MFC): un marco de trabajo orientado a objetos para crear programas tradicionales de Windows, especialmente aplicaciones empresariales, que tienen interfaces de usuario complejas con botones, cuadros de lista, vistas de árbol y otros controles. Para obtener más información, consulta [MFC Desktop Applications](../mfc/mfc-desktop-applications.md).

- Active Template Library (ATL): una biblioteca del asistente eficaz para crear componentes COM. Para obtener más información, consulta [ATL COM Desktop Components](../atl/atl-com-desktop-components.md).

- C++ AMP (C++ Accelerated Massive Parallelism): una biblioteca que habilita el trabajo de proceso general de alto rendimiento en la GPU. Para obtener más información, consulta [C++ AMP (C++ Accelerated Massive Parallelism)](../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md).

- Runtime de simultaneidad: una biblioteca que simplifica el trabajo de programación paralela y asincrónica para dispositivos de varios núcleos. Para obtener más información, consulta [Concurrency Runtime](../parallel/concrt/concurrency-runtime.md).

En muchos escenarios de programación para Windows también se requiere Windows SDK, que incluye los archivos de encabezado que permiten el acceso a componentes del sistema operativo Windows. De forma predeterminada, Visual Studio instala el SDK de Windows como un componente de la carga de trabajo de escritorio de C++, que permite el desarrollo de aplicaciones de Windows Universal. Para desarrollar aplicaciones para UWP, necesitará la versión de Windows 10 del SDK de Windows. Para obtener información, consulte [SDK de Windows 10](https://dev.windows.com/downloads/windows-10-sdk). (Para obtener más información sobre los SDK de Windows para las versiones anteriores de Windows, consulte el [archivo de Windows SDK](https://developer.microsoft.com/windows/downloads/sdk-archive)).

**Programar archivos (x86) \Windows Kits** es la ubicación predeterminada para todas las versiones del SDK de Windows que ha instalado.

Otras plataformas como Xbox y Azure cuentan con sus propios SDK que puede que tenga que instalar. Para obtener más información, vea el Centro para desarrolladores de DirectX y el Centro para desarrolladores de Azure.

## <a name="development-tools"></a>Herramientas del programador

Visual Studio incluye un depurador eficaz de código nativo, herramientas de análisis estático, herramientas de depuración de gráficos, un editor de código completo, compatibilidad con pruebas unitarias, y muchas otras herramientas y utilidades. Para obtener más información, consulte [comience a desarrollar con Visual Studio](/visualstudio/ide/get-started-developing-with-visual-studio), y [IDE y herramientas de desarrollo](../ide/ide-and-tools-for-visual-cpp-development.md).

## <a name="in-this-section"></a>En esta sección
|Title|Descripción|
|-----------|-----------------|
|[Aplicaciones de escritorio de Windows en C++](desktop-applications-visual-cpp.md)| Cómo crear aplicaciones de escritorio tradicionales.|
|[Biblioteca de plantillas activas (ATL)](../atl/TOC.md)|Utilice la biblioteca ATL para crear componentes COM en C++.|
|[Microsoft Foundation Classes (MFC)](../mfc/TOC.md)|Usar MFC para crear grandes o pequeñas aplicaciones de Windows con controles y cuadros de diálogo|
|[Clases compartidas ATL y MFC](../atl-mfc-shared/TOC.md)|Utilice las clases como CString que se comparten en ATL y MFC.|
|[Desarrollo de .NET con C++/CLI](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)|Crear contenedores para las bibliotecas nativas de C++ que le permiten la comunicación con aplicaciones de .NET y componentes.|
|[Extensiones de componentes de .NET y UWP](component-extensions-for-runtime-platforms.md)|Referencia de elementos de sintaxis compartidos por C++ / c++ / CX y c++ / CLI.|
|[Aplicaciones de Windows universales (C++)](universal-windows-apps-cpp.md)|Escribir aplicaciones para UWP con C++ / c++ / CX o biblioteca de plantillas de Windows en tiempo de ejecución (WRL).|
|[Atributos de C++ para COM y .NET](attributes/cpp-attributes-com-net.md)|Atributos no estándares para la programación de Windows solo mediante .NET o COM.|

## <a name="related-articles"></a>Artículos relacionados

|Título|Descripción|
|-----------|-----------------|
|[Visual C++](../visual-cpp-in-visual-studio.md)|Tema primario para el contenido del desarrollador de Visual C++.|
