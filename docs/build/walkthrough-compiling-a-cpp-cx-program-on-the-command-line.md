---
title: 'Tutorial: Compilación de un programa de C++/CX en la línea de comandos'
ms.date: 04/23/2019
ms.assetid: 626f5544-69ed-4736-83a9-f11389b371b2
ms.openlocfilehash: 83369fc7b458463ea1f44a347bbcd0ca4eb32224
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078207"
---
# <a name="walkthrough-compiling-a-ccx-program-on-the-command-line"></a>Tutorial: Compilación de un programa de C++/CX en la línea de comandos

> [!NOTE]
> En el caso de las nuevas aplicaciones y componentes de UWP, se recomienda usar [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/), una proyección del lenguaje C++17 estándar para API de Windows Runtime. C++/WinRT está disponible en el SDK de Windows 10 a partir de la versión 1803. C++/WinRT se implementa completamente en los archivos de encabezado y está diseñado para proporcionar acceso de primera clase a la API moderna de Windows.

El compilador de Microsoft C++ (MSVC) admite las extensiones de componentes de C++ (C++/CX), con tipos y operadores adicionales para seleccionar como destino el modelo de programación de Windows Runtime. Puede usar C++/CX para compilar aplicaciones para la Plataforma universal de Windows y el escritorio de Windows. Para obtener más información, vea [Un recorrido por C++/CX](https://msdn.microsoft.com/magazine/dn166929.aspx) y [Extensiones de componentes para plataformas de tiempo de ejecución](../extensions/component-extensions-for-runtime-platforms.md).

En este tutorial, utilizará un editor de texto para crear un programa básico de C++/CX y, a continuación, lo compilará en la línea de comandos. (Puede usar su propio programa de C++/CX en lugar de escribir el que se muestra o usar un código de ejemplo de C++/CX de otro artículo de ayuda. Esta técnica es útil para compilar y probar módulos pequeños sin elementos de la interfaz de usuario).

> [!NOTE]
> También puede usar el IDE de Visual Studio para compilar programas de C++/CX. Como el IDE incluye compatibilidad con el diseño, la depuración, la emulación y la implementación que no está disponible en la línea de comandos, se recomienda usarlo para compilar aplicaciones de la Plataforma universal de Windows (UWP). Para obtener más información, vea [Creación de una aplicación para UWP en C++](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp).

## <a name="prerequisites"></a>Requisitos previos

Conocer los aspectos básicos del lenguaje C++.

## <a name="compiling-a-ccx-program"></a>Compilación de un programa de C++/CX

Para habilitar la compilación de C++/CX, debe usar la opción del compilador [/ZW](reference/zw-windows-runtime-compilation.md). El compilador de MSVC genera un archivo .exe destinado a Windows Runtime y vincula las bibliotecas necesarias.

#### <a name="to-compile-a-ccx-application-on-the-command-line"></a>Para compilar una aplicación de C++/CX en la línea de comandos

1. Abra una ventana de **Símbolo del sistema para desarrolladores**. (En la ventana **Inicio**, abra **Aplicaciones**. Abra la carpeta **Visual Studio Tools** de la versión de Visual Studio y, después, elija el acceso directo **Símbolo del sistema para desarrolladores**). Para obtener más información sobre cómo abrir una ventana del Símbolo del sistema para desarrolladores, vea [Uso del conjunto de herramientas de MSVC desde la línea de comandos](building-on-the-command-line.md).

   Puede que se requieran credenciales de administrador para compilar el código correctamente,en función del sistema operativo y de la configuración del equipo. Para ejecutar la ventana del símbolo del sistema como administrador, abra el menú contextual de **Símbolo del sistema para desarrolladores** y, luego, elija **Ejecutar como administrador**.

1. En el símbolo del sistema, escriba **notepad basiccx.cpp**.

   Elija **Sí** cuando se le pida que cree un archivo.

1. En el Bloc de notas, escriba estas líneas:

    ```cpp
    using namespace Platform;

    int main(Platform::Array<Platform::String^>^ args)
    {
        Platform::Details::Console::WriteLine("This is a C++/CX program.");
    }
    ```

1. En la barra de menús, seleccione **Archivo** > **Guardar**.

   Acaba de crear un archivo de origen de C++ que usa el espacio de nombres [Espacio de nombres de plataforma](../cppcx/platform-namespace-c-cx.md) de Windows Runtime.

1. En el símbolo del sistema, escriba **cl /EHsc /ZW basiccx.cpp /link /SUBSYSTEM:CONSOLE**. El compilador cl.exe compila el código fuente en un archivo .obj y, después, ejecuta el enlazador para generar un programa ejecutable llamado basiccx.exe. (La opción del compilador [/EHsc](reference/eh-exception-handling-model.md) especifica el modelo de control de excepciones de C++ y la marca [/link](reference/link-pass-options-to-linker.md) especifica una aplicación de consola).

1. Para ejecutar el programa basiccx.exe, escriba **basiccx** en el símbolo del sistema.

   El programa mostrará este texto y se cerrará:

    ```Output
    This is a C++/CX program.
    ```

## <a name="see-also"></a>Vea también

[Proyectos y sistemas de compilación](projects-and-build-systems-cpp.md)<br/>
[Opciones del compilador de MSVC](reference/compiler-options.md)
