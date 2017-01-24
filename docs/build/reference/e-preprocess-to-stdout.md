---
title: "/E (Preprocesar para stdout) | Microsoft Docs"
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
  - "/e"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/E (opción del compilador) [C++]"
  - "-E (opción del compilador) [C++]"
  - "resultados del preprocesador"
  - "resultados del preprocesador, copiar a stdout"
ms.assetid: ddbb1725-d950-4978-ab2f-30a5cd7b778c
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /E (Preprocesar para stdout)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Preprocesa archivos de código fuente de C y C\+\+ y copia los archivos preprocesados en el dispositivo de salida estándar.  
  
## Sintaxis  
  
```  
/E  
```  
  
## Comentarios  
 En esta operación, se procesan todas las directivas del preprocesador y las expansiones de macros, y se quitan los comentarios.  Para conservar los comentarios en el resultado preprocesado, utilice la opción del compilador [\/C \(Conservar los comentarios durante el preprocesamiento\)](../../build/reference/c-preserve-comments-during-preprocessing.md).  
  
 **\/E** agrega directivas `#line` a los resultados, al principio y al final de cada archivo incluido y alrededor de las líneas quitadas por las directivas del preprocesador para la compilación condicional.  Estas directivas cambian el número de las líneas en el archivo preprocesado.  Como consecuencia, los errores generados durante las fases finales del procesamiento hacen referencia a los números de línea del archivo de código fuente original, no a las del archivo preprocesado.  
  
 La opción **\/E** suprime la compilación.  Debe volver a enviar el archivo preprocesado para compilación.  **\/E** también suprime los archivos de salida de las opciones **\/FA**, **\/Fa** y **\/Fm**.  Para obtener más información, vea [\/FA, \/Fa \(Archivo de lista\)](../../build/reference/fa-fa-listing-file.md) y [\/Fm \(Asignar nombre al archivo de asignaciones\)](../../build/reference/fm-name-mapfile.md).  
  
 Para suprimir directivas `#line`, utilice en su lugar la opción [\/EP \(Preprocesar para stdout sin directivas \#line\)](../../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md).  
  
 Para enviar el resultado preprocesado a un archivo, en vez de hacerlo a `stdout`, utilice en su lugar la opción [\/P \(Preprocesar y escribir en un archivo\)](../../build/reference/p-preprocess-to-a-file.md).  
  
 Para suprimir directivas `#line` y enviar el resultado preprocesado a un archivo, utilice **\/P** y **\/EP** a la vez.  
  
 No puede usar encabezados precompilados con la opción **\/E**.  
  
 Tenga en cuenta que, cuando se preprocesa en un archivo independiente, no se emiten espacios después de los símbolos \(tokens\).  Esto puede generar un programa no válido o causar efectos secundarios inesperados.  El programa siguiente compila correctamente:  
  
```  
#define m(x) x  
m(int)main( )  
{  
   return 0;  
}  
```  
  
 No obstante, si se compila con:  
  
```  
cl -E test.cpp > test2.cpp  
```  
  
 `int main` en test2.cpp será incorrectamente `intmain`.  
  
### Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener información detallada, vea [Cómo: Abrir páginas de propiedades del proyecto](../../misc/how-to-open-project-property-pages.md).  
  
2.  Haga clic en la carpeta **C\/C\+\+**.  
  
3.  Haga clic en la página de propiedades **Línea de comandos**.  
  
4.  Escriba la opción del compilador en el cuadro **Opciones adicionales**.  
  
### Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.GeneratePreprocessedFile%2A>.  
  
## Ejemplo  
 La línea de comandos siguiente preprocesa `ADD.C`, conserva los comentarios, agrega directivas `#line` y muestra el resultado en el dispositivo de salida estándar:  
  
```  
CL /E /C ADD.C  
```  
  
## Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)