---
title: archivos .netmodule como entrada del vinculador | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MSIL linking
- linking [C++], modules
- .netmodules
- modules, Visual C++
ms.assetid: a4bcbe8a-4255-451d-853b-f88cfd82f4e1
caps.latest.revision: "22"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: adafad3532b17573278e7afd82bc33f2c3c50b67
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="netmodule-files-as-linker-input"></a>.Archivos netmodule como entrada del vinculador
Link.exe ahora acepta archivos MSIL .obj y .netmodule como entrada. El archivo de salida generado por el vinculador será un ensamblado o un archivo .netmodule sin ninguna dependencia de tiempo de ejecución de cualquiera de los archivos .obj o .netmodule que se utilizaron como entrada al vinculador.  
  
 archivos .netmodule creados por el compilador de Visual C++ con [/LN (crear un módulo MSIL)](../../build/reference/ln-create-msil-module.md) o el vinculador con [/NOASSEMBLY (crear un módulo MSIL)](../../build/reference/noassembly-create-a-msil-module.md). archivos .obj siempre se crean en una compilación de Visual C++. Para otros compiladores de Visual Studio, use la **/target: module** opción del compilador.  
  
 En la mayoría de los casos, debe pasar al vinculador el archivo .obj desde la compilación de Visual C++ que creó el archivo .netmodule, a menos que el archivo .netmodule se creó con [/clr (compilación de Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md). Archivos MSIL .netmodule utilizados como entrada al vinculador deben ser MSIL puro, que se puede generar mediante el compilador de Visual C++ utilizando **/CLR: safe**. Las opciones del compilador **/clr:pure** y **/clr:safe** están en desuso en Visual Studio 2015. Los compiladores de .NET de Visual Studio generan módulos MSIL puros de forma predeterminada.  
  
 Para obtener información sobre cómo invocar al vinculador desde la línea de comandos, consulte [sintaxis de línea de comandos del vinculador](../../build/reference/linker-command-line-syntax.md), [de compilación de C/C ++ en la línea de comandos](../../build/building-on-the-command-line.md), y [establecer la ruta de acceso y las Variables de entorno Compilaciones de línea de comandos](../../build/setting-the-path-and-environment-variables-for-command-line-builds.md).  
  
 Pasa un archivo .netmodule o .dll al vinculador que se compiló mediante el compilador de Visual C++ con **/CLR** o con **/CLR: pure** puede dar lugar a un error del vinculador. Para obtener más información, consulte [elegir el formato de archivos de entrada .netmodule](../../build/reference/choosing-the-format-of-netmodule-input-files.md).  
  
 El vinculador acepta archivos .obj nativos así como archivos .obj MSIL compilados con **/CLR**, **/CLR: pure**, o **/CLR: safe**. Cuando se pasan archivos .obj mixtos en la misma compilación, la capacidad del archivo de salida resultante, de forma predeterminada, será igual al nivel más bajo de la capacidad de los módulos de entrada. Por ejemplo, si se pasa un .obj seguro y uno puro al vinculador, el archivo de salida será puro. [/CLRIMAGETYPE (Especificar tipo de imagen de CLR)](../../build/reference/clrimagetype-specify-type-of-clr-image.md) permite especificar un nivel inferior de capacidad, si eso es lo necesita.  
  
 Si actualmente tiene una aplicación que se compone de dos o más ensamblados y desea que la aplicación para poder estar contenidos en un ensamblado, debe volver a compilar los ensamblados y, a continuación, vincular los archivos .obj y .netmodule para producir un único ensamblado.  
  
 Debe especificar un punto de entrada mediante [/ENTRY (símbolo de punto de entrada)](../../build/reference/entry-entry-point-symbol.md) al crear una imagen ejecutable.  
  
 Cuando se vincula con un archivo .obj o .netmodule MSIL, use [/LTCG (generación de código de tiempo de vínculo)](../../build/reference/ltcg-link-time-code-generation.md), en caso contrario, cuando el vinculador encuentra los archivos MSIL .obj o .netmodule, reiniciará el vínculo con/LTCG.  
  
 Los archivos MSIL .obj o .netmodule también pueden pasarse a cl.exe.  
  
 Archivos de entrada MSIL .obj o .netmodule no pueden tener recursos incrustados. Un recurso se incrusta en un archivo de salida (módulo o ensamblado) con [/ASSEMBLYRESOURCE (incrustar un recurso administrado)](../../build/reference/assemblyresource-embed-a-managed-resource.md) opción del vinculador o con el **/Resource** opción del compilador en otros compiladores de Visual Studio.  
  
 Al realizar la vinculación de MSIL, y si no se especifica también [/LTCG (generación de código de tiempo de vínculo)](../../build/reference/ltcg-link-time-code-generation.md), verá un mensaje informativo reporting que se está reiniciando el vínculo. Este mensaje puede omitirse, pero to mejorar el rendimiento del vinculador con vinculación de MSIL, especifique explícitamente **/LTCG**.  
  
## <a name="example"></a>Ejemplo  
 En el código de C++ se invocará el bloque catch de un bloque try correspondiente para una excepción no sean del sistema. Sin embargo, de forma predeterminada, CLR contiene excepciones no dependen del sistema con <xref:System.Runtime.CompilerServices.RuntimeWrappedException>. Cuando se crea un ensamblado de Visual C++ y los módulos de Visual C++ no y desea que un bloque catch en el código de C++ que deben invocarse desde su correspondiente cláusula try cuando el bloque try produce una excepción no dependen del sistema, debe agregar el  
  
 [assembly:System::Runtime::CompilerServices::RuntimeCompatibility(WrapNonExceptionThrows=false)] el atributo en el código fuente para los módulos que no sean de C++.  
  
```  
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
 Al cambiar el valor booleano del atributo WrapNonExceptionThrows, modifica la capacidad del código de Visual C++ para detectar una excepción no sean del sistema.  
  
```  
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
 [Archivos de entrada de vínculo](../../build/reference/link-input-files.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)