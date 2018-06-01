---
title: archivos .netmodule como entrada del vinculador | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- MSIL linking
- linking [C++], modules
- .netmodules
- modules, Visual C++
ms.assetid: a4bcbe8a-4255-451d-853b-f88cfd82f4e1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bbb2ab74e8c9d0285b9bec2f9979257d89797022
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/01/2018
ms.locfileid: "34704570"
---
# <a name="netmodule-files-as-linker-input"></a>.Archivos netmodule como entrada del vinculador

Link.exe ahora acepta archivos MSIL .obj y .netmodule como entrada. El archivo de salida generado por el vinculador será un ensamblado o un archivo .netmodule sin ninguna dependencia de tiempo de ejecución de cualquiera de los archivos .obj o .netmodule que se utilizaron como entrada al vinculador.

archivos .netmodule creados por el compilador de Visual C++ con [/LN (crear un módulo MSIL)](../../build/reference/ln-create-msil-module.md) o el vinculador con [/NOASSEMBLY (crear un módulo MSIL)](../../build/reference/noassembly-create-a-msil-module.md). archivos .obj siempre se crean en una compilación de Visual C++. Para otros compiladores de Visual Studio, use la **/target: module** opción del compilador.

Debe pasar al vinculador el archivo .obj desde la compilación de Visual C++ que creó el archivo .netmodule. Pasar en un archivo .netmodule ya no se admite porque el **/CLR: pure** y **/CLR: safe** opciones del compilador están en desuso en Visual Studio 2015 y no se admiten en Visual Studio de 2017.

Para obtener información sobre cómo invocar al vinculador desde la línea de comandos, consulte [sintaxis de línea de comandos del vinculador](../../build/reference/linker-command-line-syntax.md), [de compilación de C/C ++ en la línea de comandos](../../build/building-on-the-command-line.md), y [establecer la ruta de acceso y las Variables de entorno Compilaciones de línea de comandos](../../build/setting-the-path-and-environment-variables-for-command-line-builds.md).

Pasa un archivo .netmodule o .dll al vinculador que se compiló mediante el compilador de Visual C++ con **/CLR** puede dar lugar a un error del vinculador. Para obtener más información, consulte [elegir el formato de archivos de entrada .netmodule](../../build/reference/choosing-the-format-of-netmodule-input-files.md).

El vinculador acepta archivos .obj nativos así como archivos .obj MSIL compilados con **/CLR**. Cuando se pasan archivos .obj mixtos en la misma compilación, la capacidad del archivo de salida resultante, de forma predeterminada, será igual al nivel más bajo de la capacidad de los módulos de entrada.

Si actualmente tiene una aplicación que se compone de dos o más ensamblados y desea que la aplicación para poder estar contenidos en un ensamblado, debe volver a compilar los ensamblados y, a continuación, vincular los archivos .obj y .netmodule para producir un único ensamblado.

Debe especificar un punto de entrada mediante [/ENTRY (símbolo de punto de entrada)](../../build/reference/entry-entry-point-symbol.md) al crear una imagen ejecutable.

Cuando se vincula con un archivo .obj o .netmodule MSIL, use [/LTCG (generación de código de tiempo de vínculo)](../../build/reference/ltcg-link-time-code-generation.md), en caso contrario, cuando el vinculador encuentra los archivos MSIL .obj o .netmodule, reiniciará el vínculo con/LTCG.

Los archivos MSIL .obj o .netmodule también pueden pasarse a cl.exe.

Archivos de entrada MSIL .obj o .netmodule no pueden tener recursos incrustados. Un recurso se incrusta en un archivo de salida (módulo o ensamblado) con [/ASSEMBLYRESOURCE (incrustar un recurso administrado)](../../build/reference/assemblyresource-embed-a-managed-resource.md) opción del vinculador o con el **/Resource** opción del compilador en otros compiladores de Visual Studio.

Al realizar la vinculación de MSIL, y si no se especifica también [/LTCG (generación de código de tiempo de vínculo)](../../build/reference/ltcg-link-time-code-generation.md), verá un mensaje informativo reporting que se está reiniciando el vínculo. Este mensaje puede omitirse, pero to mejorar el rendimiento del vinculador con vinculación de MSIL, especifique explícitamente **/LTCG**.

## <a name="example"></a>Ejemplo

En el código de C++ la **catch** bloque de correspondiente **intente** se invocará para una excepción no sean del sistema. Sin embargo, de forma predeterminada, CLR contiene excepciones no son del sistema con <xref:System.Runtime.CompilerServices.RuntimeWrappedException>. Cuando se crea un ensamblado de módulos de Visual C++ y no de Visual C++ y desea un **catch** bloque de código de C++ que se debe invocar desde el correspondiente **intente** cláusula cuando el **intente**bloque produce una excepción no son del sistema, debe agregar el `[assembly:System::Runtime::CompilerServices::RuntimeCompatibility(WrapNonExceptionThrows=false)]` de atributo en el código fuente para los módulos que no sean de C++.

```cpp
// MSIL_linking.cpp
// compile with: /c /clr
value struct V {};

ref struct MCPP {
   static void Test() {
      try {
         throw (gcnew V);
      }
      catch (V ^) {
         System::Console::WriteLine("caught non System exception in C++ source code file");
      }
   }
};

/*
int main() {
   MCPP::Test();
}
*/
```

## <a name="example"></a>Ejemplo

Cambiando el valor booleano de la `WrapNonExceptionThrows` atributo, se modifica la capacidad del código de Visual C++ para detectar una excepción no son del sistema.

```cpp
// MSIL_linking_2.cs
// compile with: /target:module /addmodule:MSIL_linking.obj
// post-build command: link /LTCG MSIL_linking.obj MSIL_linking_2.netmodule /entry:MLinkTest.Main /out:MSIL_linking_2.exe /subsystem:console
using System.Runtime.CompilerServices;

// enable non System exceptions
[assembly:RuntimeCompatibility(WrapNonExceptionThrows=false)]

class MLinkTest {
   public static void Main() {
      try {
         MCPP.Test();
      }
      catch (RuntimeWrappedException) {
         System.Console.WriteLine("caught a wrapped exception in C#");
      }
   }
}
```

```Output
caught non System exception in C++ source code file
```

## <a name="see-also"></a>Vea también

- [Archivos de entrada de LINK](../../build/reference/link-input-files.md)
- [Opciones del vinculador](../../build/reference/linker-options.md)
