---
title: "/Fx (Combinar c&#243;digo insertado) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCCLWCECompilerTool.ExpandAttributedSource"
  - "/Fx"
  - "VC.Project.VCCLCompilerTool.ExpandAttributedSource"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Fx (opción del compilador) [C++]"
  - "-Fx (opción del compilador) [C++]"
  - "código insertado"
  - "combinar código insertado"
  - "/Fx (opción del compilador) [C++]"
ms.assetid: 14f0e301-3bab-45a3-bbdf-e7ce66f20560
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# /Fx (Combinar c&#243;digo insertado)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Genera una copia de cada archivo de origen con código insertado combinado en el origen.  
  
## Sintaxis  
  
```  
/Fx  
```  
  
## Comentarios  
 Para distinguir un archivo de origen combinado de un archivo de origen original, **\/Fx** agrega una extensión .mrg entre el nombre de archivo y la extensión de archivo. Por ejemplo, un archivo denominado MyCode.cpp que contiene código con atributos creado con **\/Fx** crea un archivo denominado MyCode.mrg.cpp que contiene el código siguiente:  
  
```  
//+++ Start Injected Code [no_injected_text(true)];      // Suppress injected text, it has // already been injected #pragma warning(disable: 4543) // Suppress warnings about skipping // injected text #pragma warning(disable: 4199) // Suppress warnings from attribute // providers //--- End Injected Code  
```  
  
 En un archivo .mrg, el código insertado a causa de un atributo se delimita de la siguiente manera:  
  
```  
//+++ Start Injected Code ... //--- End Injected Code  
```  
  
 El atributo [no\_injected\_text](../../windows/no-injected-text.md) está insertado en un archivo .mrg, lo que permite la compilación del archivo .mrg sin volver a insertar texto.  
  
 Debe tener en cuenta que el archivo de origen .mrg está diseñado para ser una representación del código fuente insertado por el compilador. Es posible que el archivo .mrg no se compile ni ejecute exactamente como el archivo de origen.  
  
 Las macros no se expanden en el archivo .mrg.  
  
 Si el programa incluye un archivo de encabezado que usa código insertado, **\/Fx** genera un archivo .mrg.h para ese encabezado.**\/Fx** no combina archivos incluidos que no usan código insertado.  
  
### Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener información detallada, vea [Cómo: Abrir páginas de propiedades del proyecto](../../misc/how-to-open-project-property-pages.md).  
  
2.  Haga clic en la carpeta **C\/C\+\+**.  
  
3.  Haga clic en la página de propiedades **Archivos de salida**.  
  
4.  Modifique la propiedad **Código fuente con atributos expandidos**.  
  
### Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ExpandAttributedSource%2A>.  
  
## Vea también  
 [\/F \(Opciones del archivo de resultados\)](../../build/reference/output-file-f-options.md)   
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)