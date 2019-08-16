---
title: .Archivos netmodule como entrada del vinculador
ms.date: 05/16/2019
helpviewer_keywords:
- MSIL linking
- linking [C++], modules
- .netmodules
- modules, Visual C++
ms.assetid: a4bcbe8a-4255-451d-853b-f88cfd82f4e1
ms.openlocfilehash: 50a0f0a1ff5f65a7512e8372de2fe5296c866dca
ms.sourcegitcommit: a10c9390413978d36b8096b684d5ed4cf1553bc8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2019
ms.locfileid: "65837423"
---
# <a name="netmodule-files-as-linker-input"></a>.Archivos netmodule como entrada del vinculador

link.exe ahora acepta archivos .obj y .netmodule de MSIL como entrada. El archivo de salida generado por el enlazador es un ensamblado o un archivo .netmodule sin ninguna dependencia en tiempo de ejecución de cualquier otro archivo .obj o .netmodule introducido por el enlazador.

Los archivos .netmodule se crean mediante el compilador de MSVC con [/LN (Crear un módulo MSIL)](ln-create-msil-module.md) o mediante el enlazador con [/NOASSEMBLY (Crear un módulo MSIL)](noassembly-create-a-msil-module.md). Los archivos .obj siempre se crean en una compilación de Visual C++. Para otros compiladores de Visual Studio, use la opción **/target:module** del compilador.

Debe pasar al enlazador el archivo .obj de la compilación de Visual C++ que creó el archivo .netmodule. Ya no se admite la posibilidad de pasar un archivo .netmodule porque las opciones del compilador **/clr:pure** y **/clr:safe** han quedado en desuso en Visual Studio 2015 y no se admiten en Visual Studio 2017 y versiones posteriores.

Para saber más sobre cómo invocar el enlazador desde la línea de comandos, vea [Sintaxis de la línea de comandos del enlazador](linking.md), [Usar el conjunto de herramientas de MSVC desde la línea de comandos](../building-on-the-command-line.md) y [Establecer la ruta de acceso y las Variables de entorno para compilaciones de línea de comandos](../setting-the-path-and-environment-variables-for-command-line-builds.md).

Si se pasa al enlazador un archivo .netmodule o .dll que se compiló mediante el compilador de MSVC con **/clr**, puede producirse un error. Para más información, vea [Elegir el formato de los archivos de entrada .netmodule](choosing-the-format-of-netmodule-input-files.md).

El enlazador acepta archivos .obj nativos y archivos .obj de MSIL compilados con **/clr**. Cuando se pasan archivos .objs mixtos en la misma compilación, la capacidad de comprobar el archivo de salida será, de forma predeterminada, igual al nivel inferior de la capacidad de comprobar los módulos de entrada.

Si actualmente tiene una aplicación que se compone de dos o más ensamblados y quiere que la aplicación se incluya en un solo ensamblado, debe volver a compilar los ensamblados y, después, vincularlos a los archivos .obj o .netmodule para generar un único ensamblado.

Debe especificar un punto de entrada mediante [/ENTRY (símbolo de punto de entrada)](entry-entry-point-symbol.md) al crear una imagen ejecutable.

Al vincular con un archivo .obj o .netmodule de MSIL, use [/LTCG (Generación de código en tiempo de vínculo)](ltcg-link-time-code-generation.md). En caso contrario, cuando el enlazador encuentra los archivos .obj o .netmodule de MSIL, reiniciará el vínculo con /LTCG.

Los archivos .obj o .netmodule de MSIL también se pueden pasar a cl.exe.

Los archivos .obj o .netmodule de MSIL no pueden tener recursos insertados. Un recurso se inserta en un archivo de salida (módulo o ensamblado) con la opción del enlazador [/ASSEMBLYRESOURCE (Insertar un recurso administrado)](assemblyresource-embed-a-managed-resource.md) o con la opción del compilador **/resource** en otros compiladores de Visual Studio.

Al realizar la vinculación de MSIL, si no se especifica también [/LTCG (Generación de código en tiempo de vínculo)](ltcg-link-time-code-generation.md), se mostrará un mensaje informativo que indica que se está reiniciando el vínculo. Este mensaje puede omitirse, pero para mejorar el rendimiento del enlazador con la vinculación de MSIL, especifique explícitamente **/LTCG**.

## <a name="example"></a>Ejemplo

En el código de C++, se invocará el bloque **catch** del elemento **try** correspondiente para una excepción que no sea del sistema. Aunque, de forma predeterminada, el CLR encapsula excepciones que no son del sistema con <xref:System.Runtime.CompilerServices.RuntimeWrappedException>. Cuando se crea un ensamblado desde módulos de Visual C++ y distintos de Visual C++ y quiere que se invoque un bloque **catch** en el código de C++ desde su cláusula **try** correspondiente cuando el bloque **try** produce una excepción que no es del sistema, debe agregar el atributo `[assembly:System::Runtime::CompilerServices::RuntimeCompatibility(WrapNonExceptionThrows=false)]` al código fuente para los módulos que no son de C++.

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

Al cambiar el valor booleano del atributo `WrapNonExceptionThrows`, se modifica la capacidad del código Visual C++ de detectar una excepción que no sea del sistema.

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
