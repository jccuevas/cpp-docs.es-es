---
title: Aplicaciones de escritorio ( C++visual)
ms.date: 07/28/2019
ms.assetid: a020b534-293c-44e2-aa48-516c43ddeb8f
ms.topic: overview
ms.openlocfilehash: 91fcc596a4c30e3fa74043c846eda6f06b666f2c
ms.sourcegitcommit: 7750e4c291d56221c8893120c56a1fe6c9af60d6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274724"
---
# <a name="desktop-applications-visual-c"></a>Aplicaciones de escritorio ( C++visual)

Una *aplicación de escritorio* en C++ es una aplicación nativa que puede acceder al conjunto completo de API de Windows y se ejecuta en una ventana o en la consola del sistema. Pueden ejecutar aplicaciones de escritorio de C++ en Windows XP a Windows 10 (aunque ya no es compatible oficialmente con Windows XP y hay muchas API de Windows que se han introducido desde entonces). 

Una aplicación de escritorio es distinta de una aplicación plataforma Universal de Windows (UWP), que puede ejecutar en equipos que ejecutan Windows 10 y también en xBox, Windows Phone, Surface Hub y otros dispositivos. Para obtener más información sobre el escritorio y Aplicaciones para UWP, consulte [elección de la tecnología](/windows/win32/choose-your-technology).

### <a name="desktop-bridge"></a>Puente de escritorio

En Windows 10 puede empaquetar la aplicación de escritorio existente o el objeto COM como una aplicación de UWP y agregar características de UWP, como Touch, o llamar a las API del conjunto de API de Windows moderno. También puede Agregar una aplicación de UWP a una solución de escritorio en Visual Studio y empaquetarlas juntas en un único paquete y usar las API de Windows para comunicarse entre ellas.

En la versión 15,4 de Visual Studio 2017 y versiones posteriores, puede crear un proyecto de paquete de aplicación de Windows para simplificar considerablemente el trabajo de empaquetar la aplicación de escritorio existente. Se aplican algunas restricciones con respecto a las llamadas del registro o las API que usa la aplicación de escritorio, pero en muchos casos puede crear rutas de acceso de código alternativas para lograr una funcionalidad similar mientras se ejecuta en un paquete de la aplicación. Para obtener más información, vea [Puente de dispositivo de escritorio](/windows/uwp/porting/desktop-to-uwp-root).

### <a name="terminology"></a>Terminología

- Una aplicación de *Win32* es una aplicación de escritorio C++ de Windows en que puede usar las API de [Windows C nativas y/o](/windows/win32/apiindex/windows-api-list) las API de biblioteca CRT y estándar de API de com y las bibliotecas de terceros. Una aplicación de Win32 que se ejecuta en una ventana requiere que el desarrollador trabaje explícitamente con mensajes de Windows dentro de una función de procedimiento de Windows. A pesar del nombre, una aplicación Win32 se puede compilar como un binario de 32 bits (x86) o 64 bits (x64). En el IDE de Visual Studio, los términos x86 y Win32 son sinónimos.

- El [Modelo de objetos componentes (COM)](/windows/win32/com/the-component-object-model) es una especificación que permite que los programas escritos en lenguajes diferentes se comuniquen entre sí. Muchos componentes de Windows se implementan como objetos COM y siguen las reglas COM estándar para crear objetos, detectar la interfaz y destruir objetos.  El uso de objetos C++ com desde aplicaciones de escritorio es relativamente sencillo, pero escribir su propio objeto com es más avanzado. En [Active Template Library (ATL)](../atl/atl-com-desktop-components.md) se proporcionan macros y funciones auxiliares que simplifican el desarrollo de COM.

- Una aplicación MFC es una aplicación de escritorio de Windows que utiliza el [Microsoft Foundation Classes](../mfc/mfc-desktop-applications.md) para crear la interfaz de usuario. Una aplicación MFC también puede utilizar componentes COM, así como las API de la biblioteca estándar y CRT. MFC proporciona un contenedor C++ fino orientado a objetos sobre el bucle de mensajes de ventana y las API de Windows. MFC es la opción predeterminada para las aplicaciones, especialmente las aplicaciones de tipo empresarial, que tienen muchos controles de interfaz de usuario o controles de usuario personalizados. MFC proporciona clases auxiliares útiles para la administración de ventanas, la serialización, la manipulación de texto, la impresión y los elementos de la interfaz de usuario moderna, como la cinta de opciones. Para que sea eficaz con MFC, debe estar familiarizado con Win32.

- Una C++aplicación o componente/CLI usa extensiones para C++ la sintaxis (según lo permitido C++ por el estándar) para habilitar la interacción entre .net y código nativo de C + +.  Una C++aplicación/CLI puede tener partes que se ejecutan de forma nativa y partes que se ejecutan en el .NET Framework con acceso a la biblioteca de clases base de .net. C++/CLI es la opción preferida cuando se tiene C++ código nativo que necesita trabajar con código escrito en C# o Visual Basic. Está diseñado para su uso en archivos dll de .NET en lugar de en el código de la interfaz de usuario. Par obtener más información, consulte el artículo sobre [la programación de .NET con C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md).

Cualquier aplicación de escritorio C++ en puede usar el tiempo de ejecución de C (CRT) y las clases y funciones de la biblioteca estándar, los objetos com y las funciones de Windows públicas, que se conocen colectivamente como la API de Windows. Para obtener una introducción a las aplicaciones de C++escritorio de Windows en, vea Introducción a [Win32 y C++ ](/windows/win32/LearnWin32/learn-to-program-for-windows).

## <a name="in-this-section"></a>En esta sección

|Title|Descripción|
|-----------|-----------------|
|[Aplicaciones de consola de Windows en C++](console-applications-in-visual-cpp.md)|Contiene información acerca de las aplicaciones de consola. Una aplicación de consola Win32 (o Win64) no tiene ninguna ventana propia ni ningún bucle de mensajes. Se ejecuta en la ventana de la consola; la entrada y la salida se controlan a través de la línea de comandos.|
|[Tutorial: Crear aplicaciones de escritorio de Windows (C++)](walkthrough-creating-windows-desktop-applications-cpp.md)|Cree una sencilla aplicación de escritorio de Windows.|
|[Creación de una aplicación de escritorio de Windows vacía](creating-an-empty-windows-desktop-application.md)|Cómo crear un proyecto de escritorio de Windows que no tenga archivos predeterminados.|
|[Adición de archivos a una aplicación de Win32 vacía](adding-files-to-an-empty-win32-applications.md)|Cómo agregar archivos a un proyecto vacío.|
|[Trabajo con archivos de recursos](working-with-resource-files.md)|Cómo agregar imágenes, iconos, tablas de cadenas y otros recursos a una aplicación de escritorio.|
|[Recursos para crear un juego con DirectX (C++)](resources-for-creating-a-game-using-directx.md)|Vínculos a contenido para crear juegos en C++.|
|[Tutorial: Crear y usar una biblioteca estática](walkthrough-creating-and-using-a-static-library-cpp.md)|Cómo crear un archivo binario. lib.|
|[Cómo: Usar el SDK de Windows 10 en una aplicación de escritorio de Windows](how-to-use-the-windows-10-sdk-in-a-windows-desktop-application.md)|Indica los pasos necesarios para configurar el proyecto de desarrollo con el SDK de Windows 10.|

## <a name="related-articles"></a>Artículos relacionados

|Title|Descripción|
|-----------|-----------------|
|[Desarrollo de Windows](/windows/win32/index)|Contiene información sobre la API de Windows y COM. (Algunas API de Windows y archivos DLL de terceros se implementan como objetos COM).|
|[Hilo Desarrollo C++ de aplicaciones para Windows 7](https://msdn.microsoft.com/library/windows/desktop/ff708696.aspx)|Describe cómo crear una aplicación de escritorio de Windows de cliente que use animaciones de Windows y Direct2D para crear una interfaz de usuario basada en carrusel.  Este tutorial no se ha actualizado desde Windows 7, pero todavía proporciona una introducción exhaustiva a la programación de Win32.|
|[Información general de la programación para Windows en C++](overview-of-windows-programming-in-cpp.md)|Describe las características clave de la programación del C++escritorio de Windows en.|

## <a name="see-also"></a>Vea también

[C++ en Visual Studio](../overview/visual-cpp-in-visual-studio.md)
