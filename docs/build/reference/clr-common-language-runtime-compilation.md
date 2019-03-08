---
title: /clr (Compilación de Common Language Runtime)
ms.date: 09/18/2018
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
ms.openlocfilehash: 5a908fc49776eaca68d9a79fb679b759155853d9
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57418859"
---
# <a name="clr-common-language-runtime-compilation"></a>/clr (Compilación de Common Language Runtime)

Permite que las aplicaciones y los componentes usen las características de Common Language Runtime (CLR).

## <a name="syntax"></a>Sintaxis

> **/clr**[**:**_options_]

## <a name="arguments"></a>Argumentos

*options*<br/>
Uno o varios de los siguientes modificadores, separados por comas.

- ninguna

   Sin opciones, **/CLR** crea metadatos para la aplicación. Los metadatos pueden usarlos otras aplicaciones de CLR y permiten que la aplicación use tipos y datos en los metadatos de otros componentes de CLR. Para obtener más información, consulte [ensamblados mixtos (nativos y administrados)](../../dotnet/mixed-native-and-managed-assemblies.md).

- **pure**

   **/ CLR: pure está desusada**. Se quita la opción en Visual Studio 2017. Se recomienda trasladar el código que deba ser MSIL puro a C#.

- **safe**

   **/ CLR: safe está en desuso**. Se quita la opción en Visual Studio 2017. Se recomienda trasladar el código que deba ser MSIL seguro en C#.

- **noAssembly**

   **/ CLR: noAssembly está en desuso**. Utilice [/LN (Create MSIL Module)](../../build/reference/ln-create-msil-module.md) en su lugar.

   Especifica que no se debe insertar un manifiesto de ensamblado en el archivo de salida. De forma predeterminada, la opción **noAssembly** no está activada.

   Un programa administrado que no tiene datos de ensamblado en el manifiesto se conoce como *módulo*. La opción **noAssembly** solo puede usarse para generar un módulo. Si compila con [/c](../../build/reference/c-compile-without-linking.md) y **/clr:noAssembly**, especifique la opción [/NOASSEMBLY](../../build/reference/noassembly-create-a-msil-module.md) en la fase del enlazador para crear un módulo.

   Antes de Visual C++ 2005, **/clr:noAssembly** requería **/LD**. Ahora,**/LD** está implícita cuando especifica **/clr:noAssembly**.

- **initialAppDomain**

   Permite que una aplicación de Visual C++ para ejecutarse en la versión 1 de CLR.  Las aplicaciones que se compilan con **initialAppDomain** no se deben usar en otras que usan ASP.NET porque estas no son compatibles con la versión 1 de CLR.

- **nostdlib**

   Indica al compilador que omita el directorio \clr predeterminado. El compilador genera errores si se incluyen varias versiones de un archivo DLL como System.dll. Esta opción le permite especificar el marco concreto que se usa durante la compilación.

## <a name="remarks"></a>Comentarios

Código administrado es código que se puede inspeccionar y administrar con el CLR. El código administrado puede tener acceso a los objetos administrados. Para obtener más información, consulta [/clr Restrictions](../../build/reference/clr-restrictions.md).

Para obtener información sobre cómo desarrollar aplicaciones que definan y usen tipos administrados, consulte [Component Extensions for Runtime Platforms](../../windows/component-extensions-for-runtime-platforms.md).

Una aplicación compilada mediante **/clr** puede contener o no datos administrados.

Para habilitar la depuración en una aplicación administrada, consulte [/ASSEMBLYDEBUG (Agregar DebuggableAttribute)](../../build/reference/assemblydebug-add-debuggableattribute.md).

Solo se crearán instancias de tipos CLR en el montón de recolección de elementos no utilizados. Para obtener más información, consulte [clases y Structs](../../windows/classes-and-structs-cpp-component-extensions.md). Para compilar una función en código nativo, use la pragma `unmanaged` . Para obtener más información, consulte [managed, unmanaged](../../preprocessor/managed-unmanaged.md).

De forma predeterminada, la opción **/clr** no está activada. Cuando **/clr** está activada, **/MD** también lo está. Para obtener más información, consulte [/MD, / MT, /LD (Utilizar la biblioteca en tiempo de ejecución)](../../build/reference/md-mt-ld-use-run-time-library.md). **/MD** garantiza que las versiones multiproceso vinculadas dinámicamente de las rutinas en tiempo de ejecución se seleccionen de los archivos de encabezado estándar (.h). El subprocesamiento múltiple es necesario para la programación administrada porque el recolector de elementos no utilizados de CLR ejecuta los finalizadores en un subproceso auxiliar.

Si se compila con **/c**, puede especificar el tipo CLR del archivo de salida resultante con [/CLRIMAGETYPE](../../build/reference/clrimagetype-specify-type-of-clr-image.md).

**/clr** implica **/EHa**, y ninguna otra opción de **/EH** es compatible con **/clr**. Para obtener más información, consulte [/EH (Modelo de control de excepciones)](../../build/reference/eh-exception-handling-model.md).

Para obtener más información sobre cómo determinar el tipo de imagen de CLR de un archivo, consulte [/CLRHEADER](../../build/reference/clrheader.md).

Todos los módulos que se pasen a una invocación específica del enlazador tienen que haberse compilado con la misma opción de compilador de la biblioteca en tiempo de ejecución (**/MD** o **/LD**).

Use la opción de enlazador [/ASSEMBLYRESOURCE](../../build/reference/assemblyresource-embed-a-managed-resource.md) opción del enlazador para insertar un recurso en un ensamblado. Las opciones del enlazador[/DELAYSIGN](../../build/reference/delaysign-partially-sign-an-assembly.md), [/KEYCONTAINER](../../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md)y [/KEYFILE](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md) también le permiten personalizar cómo se crea un ensamblado.

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

[Opciones del compilador](../../build/reference/compiler-options.md)<br/>
[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)
