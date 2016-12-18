---
title: "/EP (Preprocesar para stdout sin directivas #line) | Microsoft Docs"
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
  - "/ep"
  - "VC.Project.VCCLCompilerTool.GeneratePreprocessedFileNoLines"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/EP (opción del compilador) [C++]"
  - "copiar los resultados del preprocesador a stdout"
  - "EP (opción del compilador) [C++]"
  - "-EP (opción del compilador) [C++]"
  - "resultados del preprocesador, copiar a stdout"
ms.assetid: 6ec411ae-e33d-4ef5-956e-0054635eabea
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /EP (Preprocesar para stdout sin directivas #line)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Preprocesa archivos de código fuente de C y C\+\+ y copia los archivos preprocesados en el dispositivo de salida estándar.  
  
## Sintaxis  
  
```  
/EP  
```  
  
## Comentarios  
 En el proceso, todas las directivas del preprocesador se procesan, así como las expansiones de macros, y se quitan los comentarios.  Para conservar los comentarios del resultado preprocesado, utilice la opción [\/C \(Conservar los comentarios durante el preprocesamiento\)](../../build/reference/c-preserve-comments-during-preprocessing.md) con **\/EP**.  
  
 La opción **\/EP** suprime la compilación.  Debe volver a enviar el archivo preprocesado para compilación.  **\/EP** también suprime los archivos de salida de las opciones **\/FA**, **\/Fa** y **\/Fm**.  Para obtener más información, vea [\/FA, \/Fa \(Archivo de lista\)](../../build/reference/fa-fa-listing-file.md) y [\/Fm \(Asignar nombre al archivo de asignaciones\)](../../build/reference/fm-name-mapfile.md).  
  
 Los errores generados durante las fases finales del procesamiento hacen referencia a los números de línea del archivo preprocesado, no a los del archivo de código fuente original.  Si desea que los números de línea hagan referencia al archivo de código fuente original, utilice en su lugar [\/E \(Preprocesar para stdout\)](../../build/reference/e-preprocess-to-stdout.md).  La opción **\/E** agrega directivas `#line` al resultado a tal fin.  
  
 Para enviar el resultado preprocesado a un archivo, con directivas `#line`, utilice en su lugar la opción [\/P \(Preprocesar y escribir en un archivo\)](../../build/reference/p-preprocess-to-a-file.md).  
  
 Para enviar el resultado preprocesado a stdout, con directivas `#line`, utilice **\/P** y **\/EP** a la vez.  
  
 No puede usar encabezados precompilados con la opción **\/EP**.  
  
### Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener información detallada, vea [Cómo: Abrir páginas de propiedades del proyecto](../../misc/how-to-open-project-property-pages.md).  
  
2.  Haga clic en la carpeta **C\/C\+\+**.  
  
3.  Haga clic en la página de propiedades **Preprocesador**.  
  
4.  Modifique la propiedad **Generar archivo preprocesado**.  
  
### Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.GeneratePreprocessedFile%2A>.  
  
## Ejemplo  
 La línea de comandos siguiente preprocesa el archivo `ADD.C`, conserva los comentarios y muestra el resultado en el dispositivo de salida estándar:  
  
```  
CL /EP /C ADD.C  
```  
  
## Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)