---
title: -clr (Common Language Runtime Compilation) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /CLR
- VC.Project.VCNMakeTool.CompileAsManaged
- VC.Project.VCCLCompilerTool.CompileAsManaged
dev_langs:
- C++
helpviewer_keywords:
- cl.exe compiler, common language runtime option
- -clr compiler option [C++]
- clr compiler option [C++]
- /clr compiler option [C++]
- Managed Extensions for C++, compiling
- common language runtime, /clr compiler option
ms.assetid: fec5a8c0-40ec-484c-a213-8dec918c1d6c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6b7ec520d27d52bb3e50a58780d822363016ef76
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42606868"
---
# <a name="clr-common-language-runtime-compilation"></a>/clr (Compilación de Common Language Runtime)
Permite que las aplicaciones y los componentes usen las características de Common Language Runtime (CLR).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
/clr[:options]  
```  
  
## <a name="arguments"></a>Argumentos  
 `options`  
 Uno o varios de los siguientes modificadores, separados por comas.  
  
 **/clr**  
 Crea metadatos para la aplicación. Los metadatos pueden usarlos otras aplicaciones de CLR y permiten que la aplicación use tipos y datos en los metadatos de otros componentes de CLR.  
  
 Para obtener más información, consulte  
  
 [Ensamblados mixtos (nativos y administrados)](../../dotnet/mixed-native-and-managed-assemblies.md) y  
  
 [Cómo: migrar a/CLR](../../dotnet/how-to-migrate-to-clr.md).  
  
 **/clr:pure**  
 /clr:pure está desusada. Es posible que una versión futura del compilador no admita esta opción. Se recomienda trasladar el código que deba ser MSIL puro a C#.  
  
 **/clr:safe**  
 /clr:safe está desusada. Es posible que una versión futura del compilador no admita esta opción. Se recomienda trasladar el código que deba ser MSIL seguro en C#. 
  
 **/clr:noAssembly**  
 Especifica que no se debe insertar un manifiesto de ensamblado en el archivo de salida. De forma predeterminada, la opción **noAssembly** no está activada.  
  
 La opción **noAssembly** está en desuso. Utilice [/LN (Create MSIL Module)](../../build/reference/ln-create-msil-module.md) en su lugar.  
  
 Un programa administrado que no tiene datos de ensamblado en el manifiesto se conoce como *módulo*. La opción **noAssembly** solo puede usarse para generar un módulo. Si compila con [/c](../../build/reference/c-compile-without-linking.md) y **/clr:noAssembly**, especifique la opción [/NOASSEMBLY](../../build/reference/noassembly-create-a-msil-module.md) en la fase del enlazador para crear un módulo.  
  
 Antes de Visual C++ 2005, **/clr:noAssembly** requería **/LD**. Ahora,**/LD** está implícita cuando especifica **/clr:noAssembly**.  
  
 **/clr:initialAppDomain**  
 Permite que una aplicación de Visual C++ para ejecutarse en la versión 1 de CLR. Si usas **initialAppDomain**, puede ver algunos de los problemas que se describen en [error: excepción de AppDomainUnloaded al usar extensiones administradas para los componentes de Visual C++](http://go.microsoft.com/fwlink/p/?linkid=169465) en Microsoft Sitio Web de soporte técnico.  
  
 Las aplicaciones que se compilan con **initialAppDomain** no se deben usar en otras que usan ASP.NET porque estas no son compatibles con la versión 1 de CLR.  
  
 **/clr:nostdlib**  
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
  
 Primero se inicializan las variables globales de un archivo de objeto nativo (durante DllMain si el ejecutable es un archivo DLL) y luego las variables globales de la sección administrada (antes de que se ejecute cualquier código administrado). `#pragma`[init_seg](../../preprocessor/init-seg.md) solo afecta al orden de inicialización en las categorías administradas y no administradas.  
  
## <a name="metadata-and-unnamed-classes"></a>Metadatos y clases sin nombre  
 Las clases sin nombre aparecerán en metadatos denominados de la manera siguiente: `$UnnamedClass$`*crc-of-current-file-name*`$`*index*`$`, donde *index* es un recuento secuencial de las clases sin nombre en la compilación. Por ejemplo, el siguiente ejemplo de código genera una clase sin nombre en los metadatos.  
  
```  
// clr_unnamed_class.cpp  
// compile by using: /clr /LD  
class {} x;  
```  
  
 Use ildasm.exe para ver los metadatos.  
  
## <a name="managed-extensions-for-c"></a>Extensiones administradas de C++  
 Visual C++ ya no admite la opción **/clr:oldsyntax** . Esta opción quedó desusada en Visual Studio 2005. La sintaxis admitida para escribir código administrado en C++ es C++/CLI. Para obtener más información, consulta [Component Extensions for Runtime Platforms](../../windows/component-extensions-for-runtime-platforms.md).  
  
 Si tiene código que usa extensiones administradas para C++, se recomienda que las traslade para usar la sintaxis C++/CLI. Para obtener más información sobre cómo trasladar su código, consulte [C++/CLI Migration Primer](../../dotnet/cpp-cli-migration-primer.md).  
  
#### <a name="to-set-this-compiler-option-in-visual-studio"></a>Para establecer esta opción del compilador en Visual Studio  
  
1.  En el **Explorador de soluciones**, haga clic con el botón secundario en el nombre del proyecto y luego haga clic en **Páginas de propiedades** para abrir el cuadro de diálogo **Páginas de propiedades** .  
  
2.  Seleccione la carpeta **Propiedades de configuración** .  
  
3.  En la página de propiedades **General** , modifique la propiedad **Compatible con Common Language Runtime** .  
  
    > [!NOTE]
    >  Cuando se habilita **/clr** en el cuadro de diálogo **Páginas de propiedades** , las propiedades de la opción de compilador que no son compatibles con **/clr** también se ajustan según sea necesario. Por ejemplo, si se establece **/RTC** y luego se habilita **/clr** , **/RTC** se desactivará.  
    >   
    >  Además, cuando depure una aplicación de **/clr** , establezca la propiedad **Tipo de depurador** en **Mixto** o **Solo administrado**. Para obtener más información, consulte [configuración del proyecto para una configuración de depuración de C++](/visualstudio/debugger/project-settings-for-a-cpp-debug-configuration).  
  
     Para obtener información acerca de cómo crear un módulo, consulte [/NOASSEMBLY (crear un módulo MSIL)](../../build/reference/noassembly-create-a-msil-module.md).  
  
#### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.CompileAsManaged%2A>.  
  
## <a name="see-also"></a>Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)