---
title: /clr (Compilación de Common Language Runtime)
ms.date: 05/16/2019
f1_keywords:
- /CLR
- VC.Project.VCNMakeTool.CompileAsManaged
- VC.Project.VCCLCompilerTool.CompileAsManaged
helpviewer_keywords:
- cl.exe compiler, common language runtime option
- -clr compiler option [C++]
- clr compiler option [C++]
- /clr compiler option [C++]
- Managed Extensions for C++, compiling
- common language runtime, /clr compiler option
ms.assetid: fec5a8c0-40ec-484c-a213-8dec918c1d6c
ms.openlocfilehash: fa2be3d3ce17df104cda121e4869c975ec6dd440
ms.sourcegitcommit: a10c9390413978d36b8096b684d5ed4cf1553bc8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2019
ms.locfileid: "65837308"
---
# <a name="clr-common-language-runtime-compilation"></a>/clr (Compilación de Common Language Runtime)

Permite que las aplicaciones y los componentes usen las características de Common Language Runtime (CLR).

## <a name="syntax"></a>Sintaxis

> **/clr**[ **:** _options_]

## <a name="arguments"></a>Argumentos

*options*<br/>
Uno o varios de los siguientes modificadores, separados por comas.

- ninguna

   Sin opciones, **/clr** crea metadatos para la aplicación. Los metadatos pueden usarlos otras aplicaciones de CLR y permiten que la aplicación use tipos y datos en los metadatos de otros componentes de CLR. Para más información, vea [Ensamblados mixtos (nativos y administrados)](../../dotnet/mixed-native-and-managed-assemblies.md).

- **pure**

   **/clr:pure está en desuso**. Esta opción se ha quitado de Visual Studio 2017 y versiones posteriores. Se recomienda trasladar el código que deba ser MSIL puro a C#.

- **safe**

   **/clr:safe está en desuso**. Esta opción se ha quitado de Visual Studio 2017 y versiones posteriores. Se recomienda trasladar a C# el código de puerto que deba ser seguro para MSIL.

- **noAssembly**

   **/clr:noAssembly está en desuso**. Utilice [/LN (Create MSIL Module)](ln-create-msil-module.md) en su lugar.

   Especifica que no se debe insertar un manifiesto de ensamblado en el archivo de salida. De forma predeterminada, la opción **noAssembly** no está activada.

   Un programa administrado que no tiene datos de ensamblado en el manifiesto se conoce como *módulo*. La opción **noAssembly** solo puede usarse para generar un módulo. Si compila con [/c](c-compile-without-linking.md) y **/clr:noAssembly**, especifique la opción [/NOASSEMBLY](noassembly-create-a-msil-module.md) en la fase del enlazador para crear un módulo.

   Antes de Visual Studio 2005, **/clr:noAssembly** necesitaba **/LD**. Ahora, **/LD** está implícita cuando especifica **/clr:noAssembly**.

- **initialAppDomain**

   Permite que una aplicación de Visual C++ se ejecute en la versión 1 de CLR.  Las aplicaciones que se compilan con **initialAppDomain** no se deben usar en otras que usan ASP.NET porque estas no son compatibles con la versión 1 de CLR.

- **nostdlib**

   Indica al compilador que omita el directorio \clr predeterminado. El compilador genera errores si se incluyen varias versiones de un archivo DLL como System.dll. Esta opción le permite especificar el marco concreto que se usa durante la compilación.

## <a name="remarks"></a>Comentarios

Código administrado es código que se puede inspeccionar y administrar con el CLR. El código administrado puede tener acceso a los objetos administrados. Para obtener más información, consulta [/clr Restrictions](clr-restrictions.md).

Para obtener información sobre cómo desarrollar aplicaciones que definan y usen tipos administrados, consulte [Component Extensions for Runtime Platforms](../../extensions/component-extensions-for-runtime-platforms.md).

Una aplicación compilada mediante **/clr** puede contener o no datos administrados.

Para habilitar la depuración en una aplicación administrada, vea [/ASSEMBLYDEBUG (Agregar DebuggableAttribute)](assemblydebug-add-debuggableattribute.md).

Solo se crearán instancias de tipos CLR en el montón de recolección de elementos no utilizados. Para más información, vea [ref class and ref struct (C++/CLI and C++/CX)](../../extensions/classes-and-structs-cpp-component-extensions.md) [ref class y ref struct (C++/CLI y C++/CX)]. Para compilar una función en código nativo, use la pragma `unmanaged` . Para más información, vea [managed, unmanaged](../../preprocessor/managed-unmanaged.md) (Compilación como managed o unmanaged).

De forma predeterminada, la opción **/clr** no está activada. Cuando **/clr** está activada, **/MD** también lo está. Para obtener más información, consulte [/MD, / MT, /LD (Utilizar la biblioteca en tiempo de ejecución)](md-mt-ld-use-run-time-library.md). **/MD** garantiza que las versiones multiproceso vinculadas dinámicamente de las rutinas en tiempo de ejecución se seleccionen de los archivos de encabezado estándar (.h). El subprocesamiento múltiple es necesario para la programación administrada porque el recolector de elementos no utilizados de CLR ejecuta los finalizadores en un subproceso auxiliar.

Si compila con **/c**, puede especificar el tipo CLR del archivo de salida resultante con [/CLRIMAGETYPE](clrimagetype-specify-type-of-clr-image.md).

**/clr** implica **/EHa**, y ninguna otra opción de **/EH** es compatible con **/clr**. Para obtener más información, consulte [/EH (Modelo de control de excepciones)](eh-exception-handling-model.md).

Para obtener más información sobre cómo determinar el tipo de imagen de CLR de un archivo, consulte [/CLRHEADER](clrheader.md).

Todos los módulos que se pasen a una invocación específica del enlazador tienen que haberse compilado con la misma opción de compilador de la biblioteca en tiempo de ejecución ( **/MD** o **/LD**).

Use la opción de enlazador [/ASSEMBLYRESOURCE](assemblyresource-embed-a-managed-resource.md) opción del enlazador para insertar un recurso en un ensamblado. Las opciones del enlazador[/DELAYSIGN](delaysign-partially-sign-an-assembly.md), [/KEYCONTAINER](keycontainer-specify-a-key-container-to-sign-an-assembly.md)y [/KEYFILE](keyfile-specify-key-or-key-pair-to-sign-an-assembly.md) también le permiten personalizar cómo se crea un ensamblado.

Cuando se usa **/clr** , el símbolo `_MANAGED` se establece en 1. Para obtener más información, consulta [Predefined Macros](../../preprocessor/predefined-macros.md).

Primero se inicializan las variables globales de un archivo de objeto nativo (durante DllMain si el ejecutable es un archivo DLL) y luego las variables globales de la sección administrada (antes de que se ejecute cualquier código administrado). `#pragma` [init_seg](../../preprocessor/init-seg.md) solo afecta al orden de inicialización en las categorías administradas y no administradas.

## <a name="metadata-and-unnamed-classes"></a>Metadatos y clases sin nombre

Las clases sin nombre aparecerán en metadatos denominados de la manera siguiente: `$UnnamedClass$`*crc-of-current-file-name*`$`*index*`$`, donde *index* es un recuento secuencial de las clases sin nombre en la compilación. Por ejemplo, el siguiente ejemplo de código genera una clase sin nombre en los metadatos.

```cpp
// clr_unnamed_class.cpp
// compile by using: /clr /LD
class {} x;
```

Use ildasm.exe para ver los metadatos.

## <a name="see-also"></a>Vea también

[Opciones del compilador de MSVC](compiler-options.md)<br/>
[Sintaxis de la línea de comandos del compilador MSVC](compiler-command-line-syntax.md)
