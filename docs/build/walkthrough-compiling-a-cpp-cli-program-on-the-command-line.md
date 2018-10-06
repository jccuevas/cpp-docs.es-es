---
title: 'Tutorial: Compilar un C++ / c++ / CLI programa en la línea de comandos | Microsoft Docs'
ms.custom: ''
ms.date: 09/24/2018
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: cef41c88-faf9-439d-8423-25aa3f5674dd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bdc09d5c1de2e74f7e24b72439910068fe9f6c1a
ms.sourcegitcommit: a738519aa491a493a8f213971354356c0e6a5f3a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/05/2018
ms.locfileid: "48820637"
---
# <a name="walkthrough-compiling-a-ccli-program-on-the-command-line"></a>Tutorial: Compilar un programa de C++/CLI en la línea de comandos

Puede crear programas de Visual C++ destinados a Common Language Runtime (CLR) que usen .NET Framework y compilarlos en la línea de comandos. Visual C++ admite el lenguaje de programación C++/CLI, con tipos y operadores adicionales para tener como destino el modelo de programación .NET. Para obtener información general sobre C++ / c++ / lenguaje CLI, consulte [programación de .NET con C++ / c++ / CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md).

En este tutorial, utilizará un editor de texto para crear un programa básico de C++/CLI y, luego, lo compilará en la línea de comandos. (Puede usar su propio programa de C++/CLI en lugar de escribir el que se muestra, o usar un código de ejemplo de C++/CLI de otro artículo de ayuda. Esta técnica es útil para compilar y probar módulos pequeños que no tienen ningún elemento de interfaz de usuario).

> [!NOTE]
> También puede usar el IDE de Visual Studio para compilar programas de C++/CLI. Para obtener más información, consulte [Tutorial: compilar un programa de C++ orientado a CLR en Visual Studio](../ide/walkthrough-compiling-a-cpp-program-that-targets-the-clr-in-visual-studio.md).

## <a name="prerequisites"></a>Requisitos previos

Comprender los aspectos básicos del lenguaje C++.

## <a name="compiling-a-ccli-program"></a>Compilación de un programa de C++/CLI

En los pasos siguientes, se muestra cómo compilar una aplicación de consola de C++/CLI que utiliza clases de .NET Framework.

Para habilitar la compilación de C / c++ / CLI, debe usar el [/CLR](../build/reference/clr-common-language-runtime-compilation.md) opción del compilador. El compilador de Visual C++ genera un archivo .exe que contiene código MSIL (o código nativo y MSIL combinado) y que vincula a las bibliotecas .NET Framework necesarias.

### <a name="to-compile-a-ccli-application-on-the-command-line"></a>Para compilar una aplicación de C++/CLI en la línea de comandos

1. Abra un **símbolo** ventana. Para obtener instrucciones específicas, consulte [para abrir una ventana de símbolo del sistema para desarrolladores](../build/building-on-the-command-line.md#developer_command_prompt).

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
[Compilación de programas de C/C++](../build/building-c-cpp-programs.md)<br/>
[Opciones del compilador](../build/reference/compiler-options.md)
