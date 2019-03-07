---
title: Aplicaciones de escritorio (Visual C++)
ms.date: 11/04/2016
ms.assetid: a020b534-293c-44e2-aa48-516c43ddeb8f
ms.openlocfilehash: 80b85afc52819a742c85512e8e6031b9b2e26e9a
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/15/2018
ms.locfileid: "51694574"
---
# <a name="desktop-applications-visual-c"></a>Aplicaciones de escritorio (Visual C++)

Una *aplicación de escritorio* en C++ es una aplicación nativa que puede acceder al conjunto completo de API de Windows y se ejecuta en una ventana o en la consola del sistema. Pueden ejecutar aplicaciones de escritorio de C++ en Windows XP a Windows 10 (aunque ya no es compatible oficialmente con Windows XP y hay muchas API de Windows que se han introducido desde entonces).

Una aplicación de escritorio es distinta de una aplicación plataforma Universal de Windows (UWP), que puede ejecutar en equipos que ejecutan Windows 10 y también en xBox, Windows Phone, Surface Hub y otros dispositivos. Para obtener más información acerca de desktop vs. Las aplicaciones de UWP, vea [elija su tecnología](/windows/desktop/choose-your-technology).

### <a name="desktop-bridge"></a>Puente de escritorio

En Windows 10 puede empaquetar su aplicación de escritorio existente o un objeto COM como una aplicación para UWP y agregar características UWP como toque o llamar a API desde el conjunto de API de Windows moderno. También puede agregar una aplicación para UWP a una solución de escritorio en Visual Studio y el paquete de ellos juntos en un único paquete y usan las API de Windows para comunicarse entre ellos.

En Visual Studio 2017 versión 15.4 y versiones posterior, puede crear un proyecto de paquete de aplicación de Windows para simplificar en gran medida el trabajo de empaquetado de la aplicación de escritorio existente. Se aplican algunas restricciones con respecto a qué registro se llama o usa las API de la aplicación de escritorio, pero en muchos casos puede crear rutas de acceso del código alternativa para lograr una funcionalidad similar mientras se ejecuta en un paquete de aplicación. Para obtener más información, vea [Puente de dispositivo de escritorio](/windows-uwp/porting/desktop-to-uwp-root).

### <a name="terminology"></a>Terminología

- Un *Win32* aplicación es una aplicación de escritorio de C++ que pueden hacer uso de nativo de Windows [las API de C de Windows o COM APIs](/windows/desktop/apiindex/windows-api-list) CRT y la API de biblioteca estándar y 3ª bibliotecas de terceros. Una aplicación de Win32 que se ejecuta en una ventana requiere que el desarrollador trabaje explícitamente con mensajes de Windows dentro de una función de procedimiento de Windows. A pesar del nombre, una aplicación Win32 puede compilarse como una (x86) 32 bits o 64 bits (x64) binario. En el IDE de Visual Studio, los términos x86 y Win32 son sinónimos.

- El [Modelo de objetos componentes (COM)](/windows/desktop/com/the-component-object-model) es una especificación que permite que los programas escritos en lenguajes diferentes se comuniquen entre sí. Muchos componentes de Windows se implementan como objetos COM y siguen las reglas COM estándar para crear objetos, detectar la interfaz y destruir objetos.  Usar objetos COM desde aplicaciones de escritorio de C++ es relativamente sencillo, pero escribir su propio objeto COM es más avanzado. En [Active Template Library (ATL)](../atl/atl-com-desktop-components.md) se proporcionan macros y funciones auxiliares que simplifican el desarrollo de COM.

- Una aplicación MFC es una aplicación de escritorio de Windows que usan el [Microsoft Foundation Classes](../mfc/mfc-desktop-applications.md) para crear la interfaz de usuario. También puede usar una aplicación MFC componentes COM, así como las API de biblioteca estándar y CRT. MFC proporciona un contenedor delgado de C++ orientado a través de las API de Windows y el bucle de mensajes de ventana. MFC es la opción predeterminada para las aplicaciones, especialmente las aplicaciones de tipo empresarial, que tienen una gran cantidad de controles de interfaz de usuario o controles de usuario personalizados. MFC proporciona clases auxiliares útiles para la administración de ventanas, serialización, manipulación de texto, impresión y elementos de la interfaz de usuario moderna, como la cinta de opciones. Para que sea eficaz con MFC debe estar familiarizado con Win32.

- C++ / c++ / CLI aplicación o componente usa las extensiones a la sintaxis de C++ (según lo permitido por la especificación de C++) para habilitar la interacción entre .NET y el código C ++ nativo.  C++ / c++ / aplicación de la CLI puede tener elementos que se ejecutan de forma nativa y elementos que se ejecutan en .NET Framework con acceso a la biblioteca de clases de Base. NET. C++ / c++ / CLI es la opción preferida cuando haya código C++ nativo que necesita para trabajar con código escrito en C# o Visual Basic. Sirve principalmente para su uso en archivos DLL de .NET en lugar de en el código de la interfaz de usuario. Para obtener más información, consulte [programación de .NET con C++ / c++ / CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md).

Puede usar cualquier aplicación de escritorio de C++ en tiempo de ejecución de C (CRT) y la biblioteca estándar de las clases y funciones, objetos COM y las funciones de Windows públicas, que se conocen colectivamente como la API de Windows. Para obtener una introducción a las aplicaciones de escritorio de Windows en C++, vea [empezar a trabajar con Win32 y C++](/windows/desktop/LearnWin32/learn-to-program-for-windows).

## <a name="in-this-section"></a>En esta sección

|Title|Descripción|
|-----------|-----------------|
|[Aplicaciones de consola de Windows en C++](console-applications-in-visual-cpp.md)|Contiene información acerca de las aplicaciones de consola. Una aplicación de consola Win32 (o Win64) no tiene ninguna ventana propia ni ningún bucle de mensajes. Se ejecuta en la ventana de la consola; la entrada y la salida se controlan a través de la línea de comandos.|
|[Tutorial: Crear aplicaciones de escritorio de Windows (C++)](walkthrough-creating-windows-desktop-applications-cpp.md)|Crear una sencilla aplicación de escritorio de Windows.|
|[Creación de una aplicación de escritorio de Windows vacía](creating-an-empty-windows-desktop-application.md)|Cómo crear un proyecto de escritorio de Windows que no tiene ningún archivo de forma predeterminada.|
|[Adición de archivos a una aplicación de Win32 vacía](adding-files-to-an-empty-win32-applications.md)|Cómo agregar archivos a un proyecto vacío.|
|[Trabajo con archivos de recursos](working-with-resource-files.md)|Cómo agregar imágenes, iconos, las tablas de cadenas y otros recursos a una aplicación de escritorio.|
|[Recursos para crear un juego usando DirectX (C++)](resources-for-creating-a-game-using-directx.md)|Vínculos a contenido para crear juegos en C++.|
|[Tutorial: Crear y utilizar una biblioteca estática](walkthrough-creating-and-using-a-static-library-cpp.md)|Cómo crear un archivo binario .lib.|
|[Procedimiento para usar el SDK de Windows 10 en una aplicación de escritorio de Windows](how-to-use-the-windows-10-sdk-in-a-windows-desktop-application.md)|Indica los pasos necesarios para configurar el proyecto de desarrollo con el SDK de Windows 10.|

## <a name="related-articles"></a>Artículos relacionados

|Título|Descripción|
|-----------|-----------------|
|[Desarrollo de Windows](/windows/desktop/index)|Contiene información sobre la API de Windows y COM. (Algunas API de Windows y archivos DLL de terceros se implementan como objetos COM).|
|[Hilo: desarrollo de aplicaciones en C++ para Windows 7](https://msdn.microsoft.com/library/windows/desktop/ff708696.aspx)|Describe cómo crear una aplicación de escritorio de Windows de cliente que use animaciones de Windows y Direct2D para crear una interfaz de usuario basada en carrusel.  En este tutorial no se ha actualizado desde Windows 7, pero sigue proporcionando una introducción exhaustiva a la programación de Win32.|
|[Información general de la programación para Windows en C++](overview-of-windows-programming-in-cpp.md)|Describe las características clave de programación en C++ de escritorio de Windows.|

## <a name="see-also"></a>Vea también

[Visual C++](../visual-cpp-in-visual-studio.md)
