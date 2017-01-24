---
title: ".Archivos netmodule como entrada del vinculador | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".netmodule"
  - "vincular [C++], módulos"
  - "módulos, Visual C++"
  - "vinculación de MSIL"
ms.assetid: a4bcbe8a-4255-451d-853b-f88cfd82f4e1
caps.latest.revision: 22
caps.handback.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# .Archivos netmodule como entrada del vinculador
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

link.exe ahora acepta MSIL .obj y .netmodules como entrada.  El archivo de salida generado por el vinculador será un ensamblado o un .netmodule sin dependencia en tiempo de ejecución en .obj o .netmodules cualquiera de los que se especifican al vinculador.  
  
 .netmodules son creados por el compilador de Visual C\+\+ con [\/LN \(Crear un módulo MSIL\)](../../build/reference/ln-create-msil-module.md) o por el vinculador con [\/NOASSEMBLY \(Crear un módulo MSIL\)](../../build/reference/noassembly-create-a-msil-module.md). Los archivos .obj siempre se crean en una compilación de Visual C\+\+.  Para otros compiladores de Visual Studio, utilice la opción del compilador **\/target:module**.  
  
 En la mayoría de los casos, deberá pasar al vinculador el archivo .obj de compilación de Visual C\+\+ que creó el .netmodule, a menos que el .netmodule se creó con [\/clr \(Compilación de Common Language Runtime\)](../../build/reference/clr-common-language-runtime-compilation.md).  MSIL .netmodules utilizado como entrada del vinculador debe ser MSIL puro, que se pueden generar mediante el compilador de Visual C\+\+ mediante **\/clr:safe**.  Otros compiladores de Visual Studio generan de manera predeterminada módulos MSIL puros.  
  
 Para obtener información sobre cómo invocar al vinculador desde la línea de comandos, vea [Sintaxis de la línea de comandos del vinculador](../../build/reference/linker-command-line-syntax.md) y [Establecer la ruta de acceso y las variables de entorno para compilar desde la línea de comandos](../../build/setting-the-path-and-environment-variables-for-command-line-builds.md).  
  
 Pasar un archivo .netmodule o .dll al vinculador compilado en el compilador de Visual C\+\+ con **\/clr** o con **\/clr:pure** puede producir un error del vinculador.  Para obtener más información, vea [Elegir el formato de los archivos de entrada .netmodule](../../build/reference/choosing-the-format-of-netmodule-input-files.md).  
  
 El vinculador acepta los archivos .obj nativos así como archivos .obj MSIL compilados con **\/clr**, **\/clr:pure** o **\/clr:safe**.  Cuando se pasan archivos .obj mixtos en la misma versión de compilación, la verificabilidad del archivo de salida será, de forma predeterminada, igual al nivel inferior de verificabilidad de los módulos de entrada.  Por ejemplo, si pasa un .obj seguro y uno puro al vinculador, el archivo de salida será puro.  [\/CLRIMAGETYPE \(Especificar tipo de imagen CLR\)](../../build/reference/clrimagetype-specify-type-of-clr-image.md) permite especificar un nivel inferior de verificabilidad, si eso es lo que necesita.  
  
 Si tiene actualmente una aplicación que se compone de dos o más ensamblados y desea que la aplicación esté contenido en un ensamblado, debe volver a compilar ensamblados y después vincular el .objs o el .netmodules para generar un ensamblado único.  
  
 Debe especificar un punto de entrada mediante [\/ENTRY \(Símbolo de punto de entrada\)](../../build/reference/entry-entry-point-symbol.md) al crear una imagen ejecutable.  
  
 Al vincular con MSIL .obj o el archivo .netmodule, utilice [\/LTCG \(Generación de código en tiempo de enlace\)](../../build/reference/ltcg-link-time-code-generation.md), si no cuando el vinculador encuentra MSIL .obj o .netmodule, reiniciará el vínculo con \/LTCG.  
  
 MSIL .obj o archivos .netmodule también se puede pasar a cl.exe.  
  
 La entrada MSIL .obj o archivos .netmodule no puede tener recursos incrustados.  Un recurso se incrusta en un archivo de salida \(módulo o ensamblado\) con la opción del vinculador [\/ASSEMBLYRESOURCE \(Incrustar un recurso administrado\)](../../build/reference/assemblyresource-embed-a-managed-resource.md) o con la opción del compilador **\/resource** en otros compiladores de Visual Studio.  
  
 Cuando realice una vinculación de MSIL, y si tampoco especifica [\/LTCG \(Generación de código en tiempo de enlace\)](../../build/reference/ltcg-link-time-code-generation.md), verá un mensaje informativo que indica que el vínculo se está reiniciando.  Este mensaje se puede omitir pero, para mejorar el rendimiento del vinculador con vinculación con MSIL, especifique explícitamente **\/LTCG**.  
  
## Ejemplo  
 En código C\+\+, se llamará al bloque Catch del Try correspondiente para una excepción que no sea del sistema.  Sin embargo, de forma predeterminada, CLR contiene excepciones que no son del sistema con <xref:System.Runtime.CompilerServices.RuntimeWrappedException>.  Si se crea un ensamblado desde módulos de Visual C\+\+ y que no sean de Visual C\+\+, y desea que se llame un bloque Catch en código C\+\+ desde su correspondiente cláusula Try cuando el bloque Try produce una excepción que no es del sistema, debe agregar el atributo  
  
 \[assembly:System::Runtime::CompilerServices::RuntimeCompatibility \(WrapNonExceptionThrows\=false\)\] al código fuente para los módulos que no sean de C\+\+.  
  
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
  
## Ejemplo  
 Al cambiar el valor booleano del atributo WrapNonExceptionThrows, modifica la capacidad del código de Visual C\+\+ para detectar una excepción que no sea del sistema.  
  
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
  
  **se detectó una excepción que no es del sistema en el archivo de código fuente de C\+\+**   
## Vea también  
 [Archivos de entrada de LINK](../../build/reference/link-input-files.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)