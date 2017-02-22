---
title: "-clr (compilaci&#243;n de Common Language Runtime) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/CLR"
  - "VC.Project.VCNMakeTool.CompileAsManaged"
  - "VC.Project.VCCLCompilerTool.CompileAsManaged"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Opción del compilador cl.exe, Common Language Runtime"
  - "-clr (opción del compilador) [C++]"
  - "clr (opción del compilador) [C++]"
  - "/clr (opción del compilador) [C++]"
  - "Extensiones administradas para C++, compilación"
  - "Opción del compilador /clr, Common Language Runtime"
ms.assetid: fec5a8c0-40ec-484c-a213-8dec918c1d6c
caps.latest.revision: 72
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 72
---
# /clr (Compilaci&#243;n de Common Language Runtime)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Permite que las aplicaciones y los componentes usen las características de Common Language Runtime \(CLR\).  
  
## Sintaxis  
  
```  
/clr[:options]  
```  
  
## Argumentos  
 `options`  
 Uno o varios de los siguientes modificadores, separados por comas.  
  
 **\/clr**  
 Crea metadatos para la aplicación. Los metadatos pueden usarlos otras aplicaciones de CLR y permiten que la aplicación use tipos y datos en los metadatos de otros componentes de CLR.  
  
 Para obtener más información, vea  
  
 [Ensamblados mixtos \(nativos y administrados\)](../../dotnet/mixed-native-and-managed-assemblies.md) y  
  
 [Cómo: Migrar a \/clr](../../dotnet/how-to-migrate-to-clr.md).  
  
 **\/clr:pure**  
 Genera un archivo de salida de solo Lenguaje Intermedio de Microsoft \(MSIL\) que no tiene ningún código nativo ejecutable. Sin embargo, puede contener tipos nativos compilados en MSIL.  
  
 Para obtener más información, consulta [Código puro y comprobable](../../dotnet/pure-and-verifiable-code-cpp-cli.md).  
  
 \/clr:pure está desusada. Es posible que una versión futura del compilador no admita esta opción. Se recomienda trasladar el código que deba ser MSIL puro a C\#.  
  
 **\/clr:safe**  
 Genera un archivo de salida de solo MSIL \(sin código ejecutable nativo\) comprobable.**\/clr:safe** habilita el diagnóstico de comprobación \([Herramienta PEVerify \(Peverify.exe\)](../Topic/Peverify.exe%20\(PEVerify%20Tool\).md)\).  
  
 Para obtener más información, consulte [Escribir código seguro comprobable](http://msdn.microsoft.com/es-es/d18f10ef-3b48-4f47-8726-96714021547b).  
  
 \/clr:safe está desusada. Es posible que una versión futura del compilador no admita esta opción. Se recomienda trasladar el código que deba ser MSIL puro y comprobable a C\#.  
  
 **\/clr:noAssembly**  
 Especifica que no se debe insertar un manifiesto de ensamblado en el archivo de salida. De forma predeterminada, la opción **noAssembly** no está activada.  
  
 La opción **noAssembly** está en desuso. Utilice [\/LN \(Crear un módulo MSIL\)](../../build/reference/ln-create-msil-module.md) en su lugar.  
  
 Un programa administrado que no tiene datos de ensamblado en el manifiesto se conoce como *módulo*. La opción **noAssembly** solo puede usarse para generar un módulo. Si compila con [\/c](../../build/reference/c-compile-without-linking.md) y **\/clr:noAssembly**, especifique la opción [\/NOASSEMBLY](../../build/reference/noassembly-create-a-msil-module.md) en la fase del enlazador para crear un módulo.  
  
 Antes de Visual C\+\+ 2005, **\/clr:noAssembly** requería **\/LD**. Ahora, **\/LD** está implícita cuando especifica **\/clr:noAssembly**.  
  
 **\/clr:initialAppDomain**  
 Permite que una aplicación de [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] se ejecute en la versión 1 de CLR. Si usa **initialAppDomain**, puede ver algunos de los problemas que se describen en [BUG: AppDomainUnloaded exception when you use managed extensions for Visual C\+\+ components \(ERROR: excepción AppDomainUnloaded al usar extensiones administradas para los componentes de Visual C\+\+\)](http://go.microsoft.com/fwlink/?LinkID=169465) en el sitio web de soporte técnico de Microsoft.  
  
 Las aplicaciones que se compilan con **initialAppDomain** no se deben usar en otras que usan ASP.NET porque estas no son compatibles con la versión 1 de CLR.  
  
 **\/clr:nostdlib**  
 Indica al compilador que omita el directorio \\clr predeterminado. El compilador genera errores si se incluyen varias versiones de un archivo DLL como System.dll. Esta opción le permite especificar el marco concreto que se usa durante la compilación.  
  
## Comentarios  
 Código administrado es código que se puede inspeccionar y administrar con el CLR. El código administrado puede tener acceso a los objetos administrados. Para obtener más información, consulta [Restricciones de \/clr](../../build/reference/clr-restrictions.md).  
  
 Para obtener información sobre cómo desarrollar aplicaciones que definan y usen tipos administrados, consulte [Extensiones de componentes para plataformas de tiempo de ejecución](../../windows/component-extensions-for-runtime-platforms.md).  
  
 Una aplicación compilada mediante **\/clr** puede contener o no datos administrados.  
  
 Para habilitar la depuración en una aplicación administrada, consulte [\/ASSEMBLYDEBUG \(Agregar DebuggableAttribute\)](../../build/reference/assemblydebug-add-debuggableattribute.md).  
  
 Solo se crearán instancias de tipos CLR en el montón de recolección de elementos no utilizados. Para obtener más información, consulta [Clases y structs](../../windows/classes-and-structs-cpp-component-extensions.md). Para compilar una función en código nativo, use la pragma `unmanaged`. Para obtener más información, consulta [managed, unmanaged](../../preprocessor/managed-unmanaged.md).  
  
 De forma predeterminada, la opción **\/clr** no está activada. Cuando **\/clr** está activada, **\/MD** también lo está. Para obtener más información, consulta [\/MD, \/MT, \/LD \(Utilizar la biblioteca en tiempo de ejecución\)](../../build/reference/md-mt-ld-use-run-time-library.md).**\/MD** garantiza que las versiones multiproceso vinculadas dinámicamente de las rutinas en tiempo de ejecución se seleccionen de los archivos de encabezado estándar \(.h\). El subprocesamiento múltiple es necesario para la programación administrada porque el recolector de elementos no utilizados de CLR ejecuta los finalizadores en un subproceso auxiliar.  
  
 Si compila con **\/c**, puede especificar el tipo CLR \(IJW, seguro o puro\) del archivo de salida resultante con [\/CLRIMAGETYPE](../../build/reference/clrimagetype-specify-type-of-clr-image.md).  
  
 **\/clr** implica **\/EHa**, y ninguna otra opción de **\/EH** es compatible con **\/clr**. Para obtener más información, consulta [\/EH \(Modelo de control de excepciones\)](../../build/reference/eh-exception-handling-model.md).  
  
 Para obtener más información sobre cómo determinar el tipo de imagen de CLR de un archivo, consulte [\/CLRHEADER](../../build/reference/clrheader.md).  
  
 Todos los módulos que se pasen a una invocación específica del enlazador tienen que haberse compilado con la misma opción de compilador de la biblioteca en tiempo de ejecución \(**\/MD** o **\/LD**\).  
  
 Use la opción de enlazador [\/ASSEMBLYRESOURCE](../../build/reference/assemblyresource-embed-a-managed-resource.md) opción del enlazador para insertar un recurso en un ensamblado. Las opciones del enlazador [\/DELAYSIGN](../../build/reference/delaysign-partially-sign-an-assembly.md), [\/KEYCONTAINER](../../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md) y [\/KEYFILE](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md) también le permiten personalizar cómo se crea un ensamblado.  
  
 Cuando se usa **\/clr**, el símbolo `_MANAGED` se establece en 1. Para obtener más información, consulta [Macros predefinidas](../../preprocessor/predefined-macros.md).  
  
 Primero se inicializan las variables globales de un archivo de objeto nativo \(durante DllMain si el ejecutable es un archivo DLL\) y luego las variables globales de la sección administrada \(antes de que se ejecute cualquier código administrado\).`#pragma`[init\_seg](../../preprocessor/init-seg.md) solo afecta al orden de inicialización en las categorías administradas y no administradas.  
  
 La compilación con **\/clr:safe** es análoga a la compilación con [\/platform:anycpu](../Topic/-platform%20\(C%23%20Compiler%20Options\).md) en lenguajes como C\#.  
  
## Imágenes puras y seguras  
 Una imagen pura usa una versión CLR de la biblioteca en tiempo de ejecución de C \(CRT\). Sin embargo, CRT no es comprobable, por lo que no puede usar CRT al compilar con **\/clr:safe**. Para obtener más información, consulta [Características de la biblioteca CRT](../../c-runtime-library/crt-library-features.md).  
  
 Entre los ejemplos de código nativo que no puede aparecer en una imagen pura se incluye ensamblado en línea, [setjmp](../../c-runtime-library/reference/setjmp.md) y [longjmp](../../c-runtime-library/reference/longjmp.md).  
  
 Se administra cada punto de entrada de una imagen pura o segura. Cuando se compila con **\/clr**, el punto de entrada es nativo. Para obtener más información, consulta [\_\_clrcall](../../cpp/clrcall.md).  
  
 Cuando se compila con **\/clr:safe**, de forma predeterminada, las variables son [appdomain](../../cpp/appdomain.md) y no pueden ser por proceso. Para **\/clr:pure**, aunque **appdomain** es el valor predeterminado, puede usar variables [process](../../cpp/process.md).  
  
 Cuando se ejecuta un archivo .exe de 32 bits que se ha compilado con **\/clr** o **\/clr:pure** en un sistema operativo de 64 bits, la aplicación se ejecuta bajo WOW64, que permite que una aplicación de 32 bits se ejecute en el CLR de 32 bits o en un sistema operativo de 64 bits. De forma predeterminada, un archivo .exe que se compile con **\/clr:safe** se ejecutará en el CLR de 64 bits en un equipo que ejecute un sistema operativo de 64 bits. \(En un sistema operativo de 32 bits, el mismo archivo .exe se ejecuta en el CLR de 32 bits\). Sin embargo, una aplicación segura podría cargar un componente de 32 bits. En ese caso, una imagen segura que se ejecute con compatibilidad de 64 bits del sistema operativo no podrá cargar la aplicación de 32 bits \(BadFormatException\). Para asegurarse de que una imagen segura continuará ejecutándose cuando cargue una imagen de 32 bits en un sistema operativo de 64 bits, debe usar [\/CLRIMAGETYPE](../../build/reference/clrimagetype-specify-type-of-clr-image.md) para cambiar los metadatos \(.corflags\) y marcarla para que se ejecute bajo WOW64. La línea de comandos siguiente es un ejemplo. \(Sustituya su propio símbolo de entrada\).  
  
 **cl \/clr:safe t.cpp \/link \/clrimagetype:pure \/entry:?main@@$$HYMHXZ \/subsystem:console**  
  
 Para obtener más información sobre cómo obtener un nombre representativo, consulte [Nombres representativos](../../build/reference/decorated-names.md). Para obtener más información sobre la programación de 64 bits, consulte [Configurar programas de 64 bits](../../build/configuring-programs-for-64-bit-visual-cpp.md). Para obtener información sobre el uso de código CLR puro, consulte [Cómo: Migrar a \/clr:pure](../../dotnet/how-to-migrate-to-clr-pure-cpp-cli.md) y [Código puro y comprobable](../../dotnet/pure-and-verifiable-code-cpp-cli.md).  
  
## Metadatos y clases sin nombre  
 Las clases sin nombre aparecerán en metadatos denominados de la manera siguiente: `$UnnamedClass$`*crc\-of\-current\-file\-name*`$`*index*`$`, donde *index* es un recuento secuencial de las clases sin nombre en la compilación. Por ejemplo, el siguiente ejemplo de código genera una clase sin nombre en los metadatos.  
  
```  
// clr_unnamed_class.cpp  
// compile by using: /clr /LD  
class {} x;  
```  
  
 Use ildasm.exe para ver los metadatos.  
  
## Extensiones administradas de C\+\+  
 Visual C\+\+ ya no admite la opción **\/clr:oldsyntax**. Esta opción quedó desusada en Visual Studio 2005. La sintaxis admitida para escribir código administrado en C\+\+ es C\+\+\/CLI. Para obtener más información, consulta [Extensiones de componentes para plataformas de tiempo de ejecución](../../windows/component-extensions-for-runtime-platforms.md).  
  
 Si tiene código que usa extensiones administradas para C\+\+, se recomienda que las traslade para usar la sintaxis C\+\+\/CLI. Para obtener más información sobre cómo trasladar su código, consulte [Manual de migraciones C\+\+\/CLI](../../dotnet/cpp-cli-migration-primer.md).  
  
#### Para establecer esta opción del compilador en Visual Studio  
  
1.  En el **Explorador de soluciones**, haga clic con el botón secundario en el nombre del proyecto y luego haga clic en **Páginas de propiedades** para abrir el cuadro de diálogo **Páginas de propiedades**.  
  
2.  Seleccione la carpeta **Propiedades de configuración**.  
  
3.  En la página de propiedades **General**, modifique la propiedad **Compatible con Common Language Runtime**.  
  
    > [!NOTE]
    >  Cuando se habilita **\/clr** en el cuadro de diálogo **Páginas de propiedades**, las propiedades de la opción de compilador que no son compatibles con **\/clr** también se ajustan según sea necesario. Por ejemplo, si se establece **\/RTC** y luego se habilita **\/clr**, **\/RTC** se desactivará.  
    >   
    >  Además, cuando depure una aplicación de **\/clr**, establezca la propiedad **Tipo de depurador** en **Mixto** o **Solo administrado**. Para obtener más información, consulta [Configuración del proyecto para una configuración de depuración de C\+\+](../Topic/Project%20Settings%20for%20a%20C++%20Debug%20Configuration.md).  
  
     Para obtener más información sobre cómo crear un módulo, consulte [\/NOASSEMBLY \(Crear un módulo MSIL\)](../../build/reference/noassembly-create-a-msil-module.md).  
  
#### Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.CompileAsManaged%2A>.  
  
## Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)