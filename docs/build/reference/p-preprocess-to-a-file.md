---
title: "/P (Preprocesar y escribir en un archivo) | Microsoft Docs"
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
  - "VC.Project.VCCLCompilerTool.GeneratePreprocessedFile"
  - "/p"
  - "VC.Project.VCCLWCECompilerTool.GeneratePreprocessedFile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/P (opción del compilador) [C++]"
  - "archivos de salida, preprocesador"
  - "P (opción del compilador) [C++]"
  - "-P (opción del compilador) [C++]"
  - "preprocesar archivos de salida"
ms.assetid: 123ee54f-8219-4a6f-9876-4227023d83fc
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /P (Preprocesar y escribir en un archivo)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Preprocesa archivos de código fuente de C y C\+\+ y escribe el resultado preprocesado en un archivo.  
  
## Sintaxis  
  
```  
/P  
```  
  
## Comentarios  
 Este archivo tiene el mismo nombre base que el archivo de código fuente, con la extensión .i.  En el proceso, todas las directivas del preprocesador se procesan, así como las expansiones de macros, y se quitan los comentarios.  Para conservar los comentarios en los resultados preprocesados, utilice la opción [\/C \(Conservar los comentarios durante el preprocesamiento\)](../../build/reference/c-preserve-comments-during-preprocessing.md) junto con **\/P**.  
  
 **\/P** agrega directivas `#line` a los resultados, al principio y al final de cada archivo incluido y alrededor de las líneas quitadas por las directivas de preprocesador para la compilación condicional.  Estas directivas cambian el número de las líneas en el archivo preprocesado.  Como consecuencia, los errores generados durante las fases finales del procesamiento hacen referencia a los números de línea del archivo de código fuente original, no a las del archivo preprocesado.  Para suprimir la generación de directivas `#line`, utilice la opción [\/EP \(Preprocesar para stdout sin directivas \#line\)](../../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md) junto con **\/P**.  
  
 La opción **\/P** suprime la compilación.  No genera ningún archivo .obj, aunque se utilice [\/Fo \(Nombre del archivo objeto\)](../../build/reference/fo-object-file-name.md).  Debe volver a enviar el archivo preprocesado para compilación.  **\/P** también suprime los archivos de salida de las opciones **\/FA**, **\/Fa** y **\/Fm**.  Para obtener más información, vea [\/FA, \/Fa \(Archivo de lista\)](../../build/reference/fa-fa-listing-file.md) y [\/Fm \(Asignar nombre al archivo de asignaciones\)](../../build/reference/fm-name-mapfile.md).  
  
### Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener información detallada, vea [Cómo: Abrir páginas de propiedades del proyecto](../../misc/how-to-open-project-property-pages.md).  
  
2.  Haga clic en la carpeta **C\/C\+\+**.  
  
3.  Haga clic en la página de propiedades **Preprocesador**.  
  
4.  Modifique la propiedad **Generar archivo preprocesado**.  
  
### Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.GeneratePreprocessedFile%2A>.  
  
## Ejemplo  
 La línea de comandos siguiente preprocesa `ADD.C`, conserva los comentarios, agrega directivas `#line` y escribe el resultado en un archivo `ADD.I`:  
  
```  
CL /P /C ADD.C  
```  
  
## Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)   
 [\/Fi \(Preprocesar el nombre del archivo de salida\)](../../build/reference/fi-preprocess-output-file-name.md)