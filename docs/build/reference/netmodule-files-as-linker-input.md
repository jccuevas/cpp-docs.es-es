---
title: .netmodule archivos como entrada del vinculador
description: Describe cómo usar Mixed.obj etc.netmodule archivos como entrada del vinculador al crear ensamblados .NET.
ms.date: 01/30/2020
helpviewer_keywords:
- MSIL linking
- linking [C++], modules
- .netmodule files
- modules, Visual C++
ms.assetid: a4bcbe8a-4255-451d-853b-f88cfd82f4e1
no-loc:
- obj
- netmodule
- clr
- pure
- safe
ms.openlocfilehash: 83eab25624bdb81ba9191e4efe6a774551502ee0
ms.sourcegitcommit: c4528a7424d35039454f17778baf1b5f98fbbee7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/01/2020
ms.locfileid: "76912827"
---
# <a name="opno-locnetmodule-files-as-linker-input"></a>.netmodule archivos como entrada del vinculador

Link. exe acepta *`.obj`* MSIL y archivos de *`.netmodule`* como entrada. El archivo de salida generado por el enlazador es un ensamblado o un archivo *`.netmodule`* sin dependencia en tiempo de ejecución en ninguno de los archivos *`.obj`* o *`.netmodule`* que se han introducido en el enlazador.

## <a name="remarks"></a>Notas

los archivos *`.netmodule`* los crea el compilador MSVC con [/LN (crear un módulo MSIL)](ln-create-msil-module.md) o el enlazador con [/noAssembly (crear un módulo MSIL)](noassembly-create-a-msil-module.md). los archivos *`.obj`* se crean siempre en C++ una compilación. Para otros compiladores de Visual Studio, use la opción **/target:module** del compilador.

Se debe pasar al enlazador el archivo *`.obj`* de la C++ compilación que creó el *`.netmodule`* . Ya no se admite el paso de un *`.netmodule`* porque las opciones **/clr:pure** y **/clr:safe** del compilador están en desuso en Visual Studio 2015 y no se admiten en Visual Studio 2017 y versiones posteriores.

Para obtener información sobre cómo invocar el enlazador desde la línea de comandos, vea sintaxis de la [línea de comandos del enlazador](linking.md), [usar el conjunto de herramientas MSVC desde la línea de comandos](../building-on-the-command-line.md)y [establecer la ruta de acceso y las variables de entorno para las compilaciones de línea de comandos](../setting-the-path-and-environment-variables-for-command-line-builds.md).

Pasar un *`.netmodule`* o *`.dll`* archivo al vinculador compilado por el compilador MSVC con **/clr** puede producir un error del vinculador. Para obtener más información, vea [elegir el formato de los archivos de entrada.netmodule ](choosing-the-format-of-netmodule-input-files.md).

El enlazador acepta archivos de *`.obj`* nativos y archivos de *`.obj`* MSIL compilados con **/clr** . Puede pasar archivos *`.obj`* mixtos en la misma compilación. La capacidad de comprobación predeterminada del archivo de salida resultante es la misma que la del módulo de entrada más bajo.

Puede cambiar una aplicación compuesta por dos o más ensamblados que se incluirán en un ensamblado. Vuelva a compilar los orígenes de los ensamblados y, a continuación, vincule los archivos de *`.obj`* o *`.netmodule`* para generar un único ensamblado.

Especifique un punto de entrada mediante [/entry (símbolo de punto de entrada)](entry-entry-point-symbol.md) al crear una imagen ejecutable.

Al vincular con un archivo MSIL *`.obj`* o *`.netmodule`* , utilice [/LTCG (generación de código en tiempo de vínculo)](ltcg-link-time-code-generation.md), de lo contrario, cuando el vinculador encuentre el *`.obj`* o *`.netmodule`* de MSIL, reiniciará el vínculo con **/LTCG**. Verá un mensaje informativo de que el vínculo se está reiniciando. Puede omitir este mensaje, pero para mejorar el rendimiento del vinculador, especifique explícitamente **/LTCG**.

Los archivos *`.obj`* o *`.netmodule`* de MSIL también se pueden pasar a cl. exe.

Los archivos *`.obj`* o *`.netmodule`* de MSIL de entrada no pueden tener recursos incrustados. Inserte recursos en un módulo de salida o en un archivo de ensamblado mediante la opción del enlazador [/assemblyresource (insertar un recurso administrado)](assemblyresource-embed-a-managed-resource.md) . O bien, use la opción del compilador **/Resource** en otros compiladores de Visual Studio.

## <a name="examples"></a>Ejemplos

En C++ el código, se invocará el bloque de **`catch`** de una **`try`** correspondiente para una excepción no`System`. Sin embargo, de forma predeterminada, CLR ajusta las excepciones que no son de`System` con <xref:System.Runtime.CompilerServices.RuntimeWrappedException>. Cuando se crea un ensamblado C++ a partir deC++ módulos que no son de y se desea que C++ un bloque **`catch`** en el código se invoque desde su cláusula de **`try`** correspondiente cuando el bloque de **`try`** produce una excepción no`System`, debe agregar el atributo `[assembly:System::Runtime::CompilerServices::RuntimeCompatibility(WrapNonExceptionThrows=false)]` al código fuente para losC++ módulos que no son de.

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

Al cambiar el valor `Boolean` del atributo `WrapNonExceptionThrows`, se modifica la capacidad del C++ código para detectar una excepción no`System`.

```csharp
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
