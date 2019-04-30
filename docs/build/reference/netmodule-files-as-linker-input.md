---
title: .Archivos netmodule como entrada del vinculador
ms.date: 11/04/2016
helpviewer_keywords:
- MSIL linking
- linking [C++], modules
- .netmodules
- modules, Visual C++
ms.assetid: a4bcbe8a-4255-451d-853b-f88cfd82f4e1
ms.openlocfilehash: fcba363cff567c69ac0fbd0a541953dfe2c8e910
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62320674"
---
# <a name="netmodule-files-as-linker-input"></a>.Archivos netmodule como entrada del vinculador

Link.exe ahora acepta .obj MSIL y los archivos .netmodule como entrada. El archivo de salida generado por el enlazador es un ensamblado o un archivo .netmodule sin ninguna dependencia de tiempo de ejecución con cualquiera de los archivos .obj o .netmodule que se utilizaron como entrada del vinculador.

archivos .netmodule se crean mediante el compilador de MSVC con [/LN (Create MSIL Module)](ln-create-msil-module.md) o por el enlazador con [/NOASSEMBLY (crear un módulo MSIL)](noassembly-create-a-msil-module.md). archivos .obj siempre se crean en una compilación de Visual C++. Para otros compiladores de Visual Studio, use el **/target: module** opción del compilador.

Debe pasar al vinculador el archivo .obj de la compilación de Visual C++ que creó el .netmodule. Pasar de un archivo .netmodule ya no se admite porque el **/CLR: pure** y **/CLR: safe** opciones del compilador están en desuso en Visual Studio 2015 y no se admite en Visual Studio 2017.

Para obtener información sobre cómo invocar al vinculador desde la línea de comandos, consulte [sintaxis de línea de comandos del vinculador](linking.md), [usar el conjunto de herramientas desde la línea de comandos MSVC](../building-on-the-command-line.md), y [establecer la ruta de acceso y las Variables de entorno para las compilaciones de línea de comandos](../setting-the-path-and-environment-variables-for-command-line-builds.md).

Pasa un archivo .netmodule o .dll al vinculador que se ha compilado con el compilador de MSVC **/CLR** puede dar lugar a un error del vinculador. Para obtener más información, consulte [elección del formato de archivos de entrada .netmodule](choosing-the-format-of-netmodule-input-files.md).

El vinculador acepta archivos .obj nativo, así como archivos .obj MSIL compilados con **/CLR**. Cuando se pasan archivos .obj mixtos en la misma compilación, la capacidad de comprobar el archivo de salida resultante, de forma predeterminada, será igual al nivel inferior de verificabilidad de los módulos de entrada.

Si actualmente tiene una aplicación que se compone de dos o más ensamblados y desea que la aplicación para poder estar contenidos en un ensamblado, debe volver a compilar los ensamblados y, a continuación, vincular los archivos .obj o .netmodule para producir un único ensamblado.

Debe especificar un punto de entrada mediante [/Entry (símbolo de punto de entrada)](entry-entry-point-symbol.md) al crear una imagen ejecutable.

Cuando se vincula con un archivo .obj o .netmodule MSIL, utilice [/LTCG (generación de código de tiempo de vínculo)](ltcg-link-time-code-generation.md), en caso contrario, cuando el vinculador encuentra los archivos .obj MSIL o .netmodule, reiniciará el vínculo con/LTCG.

Los archivos .obj o .netmodule MSIL también se pueden pasar a cl.exe.

MSIL .obj o .netmodule los archivos de entrada no pueden tener recursos incrustados. Un recurso se incrusta en un archivo de salida (módulo o ensamblado) con [/ASSEMBLYRESOURCE (insertar un recurso administrado)](assemblyresource-embed-a-managed-resource.md) opción del vinculador o con el **/Resource** opción del compilador en otros compiladores de Visual Studio.

Al realizar la vinculación de MSIL, y si no se especifica también [/LTCG (generación de código de tiempo de vínculo)](ltcg-link-time-code-generation.md), verá un mensaje informativo que se está reiniciando el vínculo de informes. Este mensaje puede omitirse, pero to mejorar el rendimiento del vinculador con vinculación de MSIL, especifique explícitamente **/LTCG**.

## <a name="example"></a>Ejemplo

En el código de C++ la **catch** bloque de correspondiente **intente** se invocará para una excepción no sean del sistema. Sin embargo, de forma predeterminada, el CLR ajusta las excepciones que no son de sistema con <xref:System.Runtime.CompilerServices.RuntimeWrappedException>. Cuando se crea un ensamblado de los módulos de Visual C++ y que no son de Visual C++ y desea una **catch** bloque de código de C++ que se debe invocar desde el correspondiente **intente** cláusula cuando el **intente**bloque produce una excepción que no son de sistema, debe agregar el `[assembly:System::Runtime::CompilerServices::RuntimeCompatibility(WrapNonExceptionThrows=false)]` atributo al código fuente para los módulos de C++ no.

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

Cambiando el valor booleano de la `WrapNonExceptionThrows` atributo, modifica la capacidad del código de Visual C++ para detectar una excepción que no son de sistema.

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

- [Archivos de entrada de LINK](link-input-files.md)
- [Opciones del enlazador MSVC](linker-options.md)
