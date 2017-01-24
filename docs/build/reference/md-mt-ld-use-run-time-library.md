---
title: "/MD, /MT, /LD (Utilizar la biblioteca en tiempo de ejecuci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/ld"
  - "/mt"
  - "VC.Project.VCCLWCECompilerTool.RuntimeLibrary"
  - "VC.Project.VCCLCompilerTool.RuntimeLibrary"
  - "/md"
  - "/ml"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/LD (opción del compilador) [C++]"
  - "/MD (opción del compilador) [C++]"
  - "/MDd (opción del compilador) [C++]"
  - "/MT (opción del compilador) [C++]"
  - "/MTd (opción del compilador) [C++]"
  - "_STATIC_CPPLIB (símbolo)"
  - "DLL [C++], opciones del compilador"
  - "LD (opción del compilador) [C++]"
  - "-LD (opción del compilador) [C++]"
  - "LIBC.lib"
  - "LIBCD.lib"
  - "LIBCMT.lib"
  - "LIBCMTD.lib"
  - "MD (opción del compilador) [C++]"
  - "-MD (opción del compilador) [C++]"
  - "MDd (opción del compilador) [C++]"
  - "-MDd (opción del compilador) [C++]"
  - "MSVCRT.lib"
  - "MSVCRTD.lib"
  - "MT (opción del compilador) [C++]"
  - "-MT (opción del compilador) [C++]"
  - "MTd (opción del compilador) [C++]"
  - "-MTd (opción del compilador) [C++]"
  - "multithread (opción del compilador)"
  - "subprocesamiento [C++], multithread (opción del compilador)"
ms.assetid: cf7ed652-dc3a-49b3-aab9-ad60e5395579
caps.latest.revision: 19
caps.handback.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /MD, /MT, /LD (Utilizar la biblioteca en tiempo de ejecuci&#243;n)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Indica si un módulo multiproceso es un archivo DLL y especifica versiones comerciales o de depuración de la biblioteca en tiempo de ejecución.  
  
## Sintaxis  
  
```  
/MD[d]  
/MT[d]  
/LD[d]  
```  
  
## Comentarios  
  
|Opción|Descripción|  
|------------|-----------------|  
|**\/MD**|Hace que la aplicación use la versión específica para multiproceso y la versión específica para DLL de la biblioteca en tiempo de ejecución.  Define `_MT` y `_DLL` y hace que el compilador sitúe el nombre de la biblioteca MSVCRT.lib en el archivo .obj.<br /><br /> Las aplicaciones compiladas con esta opción se vinculan estáticamente con MSVCRT.lib.  Esta biblioteca proporciona un nivel de código que permite al vinculador resolver referencias externas.  El código de trabajo real reside en el archivo MSVCR*versionnumber*.DLL, que debe estar disponible en tiempo de ejecución para las aplicaciones vinculadas con MSVCRT.lib.|  
|**\/MDd**|Define `_DEBUG`, `_MT` y `_DLL` y hace que la aplicación use la versión de depuración multiproceso y la versión específica para DLL de la biblioteca en tiempo de ejecución.  También hace que el compilador coloque el nombre de la biblioteca MSVCRTD.lib en el archivo .obj.|  
|**\/MT**|Hace que la aplicación use la versión estática multiproceso de la biblioteca en tiempo de ejecución.  Define `_MT` y hace que el compilador sitúe el nombre de biblioteca LIBCMT.lib en el archivo .obj para que el vinculador utilice LIBCMT.lib al resolver símbolos externos.|  
|**\/MTd**|Define `_DEBUG` y `_MT`.  Esta opción también hace que el compilador coloque el nombre de la biblioteca LIBCMTD.lib en el archivo .obj, así el vinculador usará LIBCMTD.lib para resolver los símbolos externos.|  
|**\/LD**|Crea un archivo DLL.<br /><br /> Pasa la opción **\/DLL** al vinculador.  El vinculador busca una función `DllMain`, aunque esta función no es obligatoria.  Si no escribe una función `DllMain`, el vinculador inserta una función `DllMain` que devuelve TRUE.<br /><br /> Vincula el código de inicio de DLL.<br /><br /> Crea una biblioteca de importación \(.lib\) si no se especifica un archivo de exportación \(.exp\) en la línea de comandos.  Vincula la biblioteca de importación con aplicaciones que llaman al archivo DLL.<br /><br /> Interpreta [\/Fe \(Asignar nombre a un archivo ejecutable\)](../../build/reference/fe-name-exe-file.md) para asignar como nombre un archivo DLL en lugar de un archivo .exe.  De forma predeterminada, el nombre del programa se convierte en *basename*.dll en lugar de en *basename*.exe.<br /><br /> Implica **\/MT**, a menos que se especifique explícitamente **\/MD**.|  
|**\/LDd**|Crea un archivo DLL de depuración.  Define `_MT` y `_DEBUG`.|  
  
 Para obtener más información sobre las bibliotecas en tiempo de ejecución de C y las bibliotecas que se utilizan para compilar con [\/clr \(Compilación de Common Language Runtime\)](../../build/reference/clr-common-language-runtime-compilation.md), vea [Características de la biblioteca CRT](../../c-runtime-library/crt-library-features.md).  
  
 Todos los módulos que se pasen a una invocación específica del vinculador tienen que haberse compilado con la misma opción de compilador de la biblioteca en tiempo de ejecución \(**\/MD**, **\/MT** o **\/LD**\).  
  
 Para obtener más información sobre el uso de las versiones de depuración de las bibliotecas en tiempo de ejecución, vea [Referencia de la biblioteca en tiempo de ejecución de C](../../c-runtime-library/c-run-time-library-reference.md).  
  
 En el artículo Q140584 de Knowledge Base también se explica cómo puede elegir la biblioteca en tiempo de ejecución de C apropiada.  
  
 Para obtener más información sobre los archivos DLL, vea [Archivos DLL en Visual C\+\+](../../build/dlls-in-visual-cpp.md).  
  
### Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener información detallada, vea [Cómo: Abrir páginas de propiedades del proyecto](../../misc/how-to-open-project-property-pages.md).  
  
2.  Expanda la carpeta **C\/C\+\+**.  
  
3.  Seleccione la página de propiedades **Generación de código**.  
  
4.  Modifique la propiedad **Biblioteca en tiempo de ejecución**.  
  
### Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.RuntimeLibrary%2A>.  
  
## Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)