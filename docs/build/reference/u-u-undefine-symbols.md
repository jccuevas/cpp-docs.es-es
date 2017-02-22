---
title: "/U, /u (Anular la definici&#243;n de s&#237;mbolos) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCCLCompilerTool.UndefinePreprocessorDefinitions"
  - "VC.Project.VCCLWCECompilerTool.UndefinePreprocessorDefinitions"
  - "VC.Project.VCCLCompilerTool.UndefineAllPreprocessorDefinitions"
  - "/u"
  - "VC.Project.VCCLWCECompilerTool.UndefineAllPreprocessorDefinitions"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/U (opción del compilador) [C++]"
  - "U (opción del compilador) [C++]"
  - "-U (opción del compilador) [C++]"
  - "anular la definición de símbolos (opción del compilador)"
ms.assetid: 7bc0474f-6d1f-419b-807d-0d8816763b2a
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# /U, /u (Anular la definici&#243;n de s&#237;mbolos)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La opción del compilador **\/U** anula la definición del símbolo de preprocesador especificado.  La opción del compilador **\/u** anula la definición de los símbolos específicos de Microsoft definidos por el compilador.  
  
## Sintaxis  
  
```  
/U[ ]symbol  
/u  
```  
  
## Argumentos  
 `symbol`  
 Símbolo del preprocesador cuya definición se anulará.  
  
## Comentarios  
 Las opciones **\/U** o **\/u** no pueden anular la definición de un símbolo creado mediante la directiva **\#define**.  
  
 La opción **\/U** puede anular la definición de un símbolo que se definió previamente mediante la opción **\/D**.  
  
 De forma predeterminada, el compilador define los símbolos específicos de Microsoft siguientes.  
  
|Símbolo|Función|  
|-------------|-------------|  
|\_CHAR\_UNSIGNED|El tipo char predeterminado es unsigned.  Se define cuando se especifica la opción [\/J](../../build/reference/j-default-char-type-is-unsigned.md).|  
|\_CPPRTTI|Se define para el código compilado con la opción [\/GR](../../build/reference/gr-enable-run-time-type-information.md).|  
|\_CPPUNWIND|Se define para el código compilado con la opción [\/EHsc](../../build/reference/eh-exception-handling-model.md).|  
|\_DLL|Se define cuando se especifica la opción [\/MD](../../build/reference/md-mt-ld-use-run-time-library.md).|  
|\_M\_IX86|Se define en 600, de forma predeterminada, para los destinos de x86.|  
|\_MSC\_VER|Para obtener más información, vea [Macros predefinidas](../../preprocessor/predefined-macros.md).|  
|\_WIN32|Se define para las aplicaciones WIN32.  Siempre definido.|  
|\_MT|Se define cuando se especifica la opción [\/MD o \/MT](../../build/reference/md-mt-ld-use-run-time-library.md).|  
  
### Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener información detallada, vea [Cómo: Abrir páginas de propiedades del proyecto](../../misc/how-to-open-project-property-pages.md).  
  
2.  Haga clic en la carpeta **C\/C\+\+**.  
  
3.  Haga clic en la página de propiedades **Avanzadas**.  
  
4.  Modifique las propiedades **Anular definiciones del preprocesador** o **Anular todas las definiciones del preprocesador**.  
  
### Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UndefineAllPreprocessorDefinitions%2A> o <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UndefinePreprocessorDefinitions%2A>.  
  
## Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)   
 [\/J \(El tipo de carácter predeterminado no tiene signo\)](../../build/reference/j-default-char-type-is-unsigned.md)   
 [\/GR \(Habilitar la información de tipo en tiempo de ejecución\)](../../build/reference/gr-enable-run-time-type-information.md)   
 [\/EH \(Modelo de control de excepciones\)](../../build/reference/eh-exception-handling-model.md)   
 [\/MD, \/MT, \/LD \(Utilizar la biblioteca en tiempo de ejecución\)](../../build/reference/md-mt-ld-use-run-time-library.md)