---
title: "/bigobj (Aumentar el n&#250;mero de secciones en el archivo .Obj) | Microsoft Docs"
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
  - "/bigobj"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/bigobj (opción del compilador) [C++]"
  - "bigobj (opción del compilador) [C++]"
  - "-bigobj (opción del compilador) [C++]"
ms.assetid: ba94d602-4015-4a8d-86ec-49241ab74c12
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /bigobj (Aumentar el n&#250;mero de secciones en el archivo .Obj)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**\/bigobj** incrementa el número de secciones que un archivo objeto puede contener.  
  
## Sintaxis  
  
```  
/bigobj  
```  
  
## Comentarios  
 De manera predeterminada, un archivo objeto puede contener hasta 65.536 \(2^16\) secciones direccionables.  Este es el caso independientemente de la plataforma de destino que se especifique.  **\/bigobj** incrementa esa capacidad de direccionamiento a 4.294.967.296 \(2^32\).  
  
 La mayoría de los módulos nunca generarán un archivo .obj que contenga más de 65.536 secciones.  Sin embargo, un código generado por el equipo o un código que usa intensivamente las bibliotecas de plantillas puede requerir archivos .obj que puedan contener más secciones.  La opción **\/bigobj** está habilitada de forma predeterminada en los proyectos de la Tienda Windows porque el código XAML generado por el equipo incluye un gran número de encabezados.  Si deshabilita esta opción en un proyecto de aplicación de la Tienda Windows, probablemente encontrará el error del compilador C1128.  
  
 Los vinculadores distribuidos antes de Visual C\+\+ 2005 no pueden leer archivos .obj que se hayan generado con **\/bigobj**.  
  
### Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener información detallada, vea [Cómo: Abrir páginas de propiedades del proyecto](../../misc/how-to-open-project-property-pages.md).  
  
2.  Haga clic en la carpeta **C\/C\+\+**.  
  
3.  Haga clic en la página de propiedades **Línea de comandos**.  
  
4.  Escriba la opción del compilador en el cuadro **Opciones adicionales**.  
  
### Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)