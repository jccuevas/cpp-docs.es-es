---
title: 'Tutorial: Compilación de C++ / c++ / CLI programa en la línea de comandos'
ms.date: 04/23/2019
ms.assetid: cef41c88-faf9-439d-8423-25aa3f5674dd
ms.openlocfilehash: 8a5c5659367350a80725b365ef9c431bbec209d1
ms.sourcegitcommit: 18d3b1e9cdb4fc3a76f7a650c31994bdbd2bde64
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/29/2019
ms.locfileid: "64877453"
---
# <a name="walkthrough-compiling-a-ccli-program-on-the-command-line"></a>Tutorial: Compilación de C++ / c++ / CLI programa en la línea de comandos

Puede crear programas de Visual C++ destinados a Common Language Runtime (CLR) que usen .NET Framework y compilarlos en la línea de comandos. Visual C++ admite el lenguaje de programación C++/CLI, con tipos y operadores adicionales para tener como destino el modelo de programación .NET. Para obtener información general sobre C++ / c++ / lenguaje CLI, consulte [programación de .NET con C++ / c++ / CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md).

En este tutorial, utilizará un editor de texto para crear un programa básico de C++/CLI y, luego, lo compilará en la línea de comandos. (Puede usar su propio programa de C++/CLI en lugar de escribir el que se muestra, o usar un código de ejemplo de C++/CLI de otro artículo de ayuda. Esta técnica es útil para compilar y probar módulos pequeños que no tienen ningún elemento de interfaz de usuario).

## <a name="prerequisites"></a>Requisitos previos

Comprender los aspectos básicos del lenguaje C++.

## <a name="compiling-a-ccli-program"></a>Compilación de un programa de C++/CLI

En los pasos siguientes, se muestra cómo compilar una aplicación de consola de C++/CLI que utiliza clases de .NET Framework.

Para habilitar la compilación de C / c++ / CLI, debe usar el [/CLR](reference/clr-common-language-runtime-compilation.md) opción del compilador. El compilador de MSVC genera un archivo .exe que contiene código MSIL, o código nativo y MSIL combinado y vínculos a las bibliotecas de .NET Framework necesarias.

### <a name="to-compile-a-ccli-application-on-the-command-line"></a>Para compilar una aplicación de C++/CLI en la línea de comandos

1. Abra un **símbolo** ventana. Para obtener instrucciones específicas, consulte [para abrir una ventana de símbolo del sistema para desarrolladores](building-on-the-command-line.md#developer_command_prompt).

   Puede que se requieran credenciales de administrador para compilar el código correctamente,en función del sistema operativo y de la configuración del equipo. Para ejecutar la ventana de símbolo del sistema como administrador, haga doble clic para abrir el menú contextual de la línea de comandos y, a continuación, elija **más** > **ejecutar como administrador**.

1. En el símbolo del sistema, escriba `notepad basicclr.cpp`.

   Elija **Sí** cuando se le pedirá que cree un archivo.

1. En el Bloc de notas, escriba estas líneas:

   ```cpp
   int main()
   {
       System::Console::WriteLine("This is a C++/CLI program.");
   }
   ```

1. En la barra de menús, elija **archivo** > **guardar**.

   Ha creado un archivo de código fuente de Visual C++ que usa una clase de .NET Framework (<xref:System.Console>) en el <xref:System> espacio de nombres.

1. En el símbolo del sistema, escriba `cl /clr basicclr.cpp`. El compilador cl.exe compila el código fuente en un archivo .obj que contiene código MSIL y, después, ejecuta el enlazador para generar un programa ejecutable llamado basicclr.exe.

1. Para ejecutar el programa basicclr.exe, en el símbolo del sistema, escriba `basicclr`.

   El programa mostrará este texto y se cerrará:

   ```Output
   This is a C++/CLI program.
   ```

## <a name="see-also"></a>Vea también

[Referencia del lenguaje C++](../cpp/cpp-language-reference.md)<br/>
[Proyectos y sistemas de compilación](projects-and-build-systems-cpp.md)<br/>
[Opciones del compilador de MSVC](reference/compiler-options.md)
