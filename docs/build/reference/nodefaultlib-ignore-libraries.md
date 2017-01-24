---
title: "/NODEFAULTLIB (Omitir bibliotecas) | Microsoft Docs"
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
  - "VC.Project.VCLinkerTool.IgnoreAllDefaultLibraries"
  - "VC.Project.VCLinkerTool.IgnoreDefaultLibraryNames"
  - "/nodefaultlib"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/NODEFAULTLIB (opción del vinculador)"
  - "bibliotecas predeterminadas, quitar"
  - "omitir bibliotecas (opción del vinculador)"
  - "bibliotecas, omitir"
  - "NODEFAULTLIB (opción del vinculador)"
  - "-NODEFAULTLIB (opción del vinculador)"
ms.assetid: 7270b673-6711-468e-97a7-c2925ac2be6e
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /NODEFAULTLIB (Omitir bibliotecas)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/NODEFAULTLIB[:library]   
```  
  
## Comentarios  
 donde:  
  
 *library*  
 Biblioteca que deberá omitir el vinculador cuando resuelva referencias externas.  
  
## Comentarios  
 La opción \/NODEFAULTLIB indica al vinculador que quite una o varias bibliotecas predeterminadas de la lista de bibliotecas en la que realiza búsquedas al resolver referencias externas.  
  
 Para crear un archivo .obj que no contenga referencias las bibliotecas predeterminadas, utilice [\/Zl \(Omitir nombres de biblioteca predeterminada\)](../../build/reference/zl-omit-default-library-name.md).  
  
 De forma predeterminada, esta opción quitará todas las bibliotecas predeterminadas de la lista de bibliotecas en las que se busca al resolver referencias externas.  El parámetro opcional *library* permite quitar una o más bibliotecas especificadas de dicha lista.  Se deberá especificar tan sólo una opción \/NODEFAULTLIB por cada biblioteca que se desee excluir.  
  
 El vinculador resuelve las referencias a definiciones externas buscando en primer lugar en las bibliotecas especificadas de forma explícita, después, en las bibliotecas especificadas con la opción \/DEFAULTLIB y, por último, en las bibliotecas predeterminadas mencionadas en los archivos .obj.  
  
 La opción \/NODEFAULTLIB:*library* reemplazará a [\/DEFAULTLIB:](../../build/reference/defaultlib-specify-default-library.md)*library* si en ambas opciones se especifica el mismo nombre de biblioteca.  
  
 Si utiliza \/NODEFAULTLIB, por ejemplo, para compilar un programa sin la biblioteca en tiempo de ejecución de C, quizá deba usar también [\/ENTRY](../../build/reference/entry-entry-point-symbol.md) para especificar el punto de entrada \(función\) del programa.  Para obtener más información, vea [Características de la biblioteca CRT](../../c-runtime-library/crt-library-features.md).  
  
### Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener más información, vea [Establecer las propiedades de un proyecto de Visual C\+\+](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en la carpeta **Vinculador**.  
  
3.  Haga clic en la página de propiedades **Entrada**.  
  
4.  Seleccione la propiedad **Omitir todas las bibliotecas predeterminadas** o especifique una lista de las bibliotecas que desea omitir en la propiedad **Omitir biblioteca específica**.  La página de propiedades **Línea de comandos** mostrará el efecto de los cambios que efectúe en estas propiedades.  
  
### Para establecer esta opción del vinculador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreDefaultLibraryNames%2A> y <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreAllDefaultLibraries%2A>.  
  
## Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)