---
title: 'Tutorial: Compilar un programa de C++/CX en la línea de comandos'
ms.date: 04/23/2019
ms.assetid: 626f5544-69ed-4736-83a9-f11389b371b2
ms.openlocfilehash: 83369fc7b458463ea1f44a347bbcd0ca4eb32224
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078207"
---
# <a name="walkthrough-compiling-a-ccx-program-on-the-command-line"></a>Tutorial: Compilar un programa de C++/CX en la línea de comandos

> [!NOTE]
> En el caso de las nuevas aplicaciones y componentes de UWP, se recomienda usar [ C++/WinRT](/windows/uwp/cpp-and-winrt-apis/), una proyección de lenguaje c++ 17 estándar para API de Windows Runtime. C++/WinRT está disponible en el SDK de Windows 10 de la versión 1803 en adelante. C++/WinRT se implementa completamente en los archivos de encabezado y está diseñado para proporcionarle acceso de primera clase a la API moderna de Windows.

El compilador de Microsoft C++ ( C++ MSVC) esC++compatible con las extensiones de componentes (/CX), que tiene tipos y operadores adicionales para tener como destino el modelo de programación de Windows Runtime. Puede usar C++/CX para compilar aplicaciones para plataforma universal de Windows (UWP) y el escritorio de Windows. Para obtener más información, consulte [un paseo C++por/CX](https://msdn.microsoft.com/magazine/dn166929.aspx) y [extensiones de componentes para plataformas en tiempo de ejecución](../extensions/component-extensions-for-runtime-platforms.md).

En este tutorial, utilizará un editor de texto para crear un programa básico de C++/CX y, a continuación, lo compilará en la línea de comandos. (Puede usar su propio programa de C++/CX en lugar de escribir el que se muestra o usar un código de ejemplo de C++/CX de otro artículo de ayuda. Esta técnica es útil para compilar y probar módulos pequeños que no tienen elementos de interfaz de usuario).

> [!NOTE]
> También puede usar el IDE de Visual Studio para compilar programas de C++/CX. Dado que el IDE incluye compatibilidad de diseño, depuración, emulación e implementación que no está disponible en la línea de comandos, se recomienda usar el IDE para compilar aplicaciones Plataforma universal de Windows (UWP). Para obtener más información, consulte [crear una aplicación para C++UWP en ](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp).

## <a name="prerequisites"></a>Prerequisites

Comprende los aspectos básicos del C++ lenguaje.

## <a name="compiling-a-ccx-program"></a>Compilación de un programa de C++/CX

Para habilitar la compilación C++de/CX, debe usar la opción del compilador [/ZW](reference/zw-windows-runtime-compilation.md) . El compilador MSVC genera un archivo. exe que tiene como destino el Windows Runtime y vínculos a las bibliotecas necesarias.

#### <a name="to-compile-a-ccx-application-on-the-command-line"></a>Para compilar una aplicación de C++/CX en la línea de comandos

1. Abra una ventana de **símbolo del sistema para desarrolladores** . (En la ventana **Inicio** , Abra **aplicaciones**. Abra la carpeta **Visual Studio Tools** bajo su versión de Visual Studio y, a continuación, elija el acceso directo **símbolo del sistema para desarrolladores** ). Para obtener más información sobre cómo abrir una ventana de Símbolo del sistema para desarrolladores, vea [usar el conjunto de herramientas MSVC desde la línea de comandos](building-on-the-command-line.md).

   Puede que se requieran credenciales de administrador para compilar el código correctamente,en función del sistema operativo y de la configuración del equipo. Para ejecutar la ventana del símbolo del sistema como administrador, abra el menú contextual de **símbolo del sistema para desarrolladores** y, a continuación, elija **Ejecutar como administrador**.

1. En el símbolo del sistema, escriba **Notepad basiccx. cpp**.

   Elija **sí** cuando se le pida que cree un archivo.

1. En el Bloc de notas, escriba estas líneas:

    ```cpp
    using namespace Platform;

    int main(Platform::Array<Platform::String^>^ args)
    {
        Platform::Details::Console::WriteLine("This is a C++/CX program.");
    }
    ```

1. En la barra de menús, elija **archivo** > **Guardar**.

   Ha creado un C++ archivo de código fuente que utiliza el espacio de nombres del [espacio de nombres](../cppcx/platform-namespace-c-cx.md) de Windows Runtime Platform.

1. En el símbolo del sistema, escriba **cl/EHSC/ZW basiccx. cpp/Link/Subsystem: Console**. El compilador cl.exe compila el código fuente en un archivo .obj y, después, ejecuta el enlazador para generar un programa ejecutable llamado basiccx.exe. (La [/EHsc](reference/eh-exception-handling-model.md) opción del compilador C++ /EHsc especifica el modelo de control de excepciones y la marca [/Link](reference/link-pass-options-to-linker.md) especifica una aplicación de consola).

1. Para ejecutar el programa basiccx. exe, en el símbolo del sistema, escriba **basiccx**.

   El programa mostrará este texto y se cerrará:

    ```Output
    This is a C++/CX program.
    ```

## <a name="see-also"></a>Consulte también

[Proyectos y sistemas de compilación](projects-and-build-systems-cpp.md)<br/>
[Opciones del compilador de MSVC](reference/compiler-options.md)
