---
title: "/I (Directorios de inclusi&#243;n adicionales) | Microsoft Docs"
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
  - "VC.Project.VCCLWCECompilerTool.AdditionalIncludeDirectories"
  - "VC.Project.VCCLCompilerTool.AdditionalIncludeDirectories"
  - "/I"
  - "VC.Project.VCNMakeTool.IncludeSearchPath"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/I (opción del compilador) [C++]"
  - "Directorios de inclusión adicionales (opción de compilador)"
  - "I (opción del compilador) [C++]"
  - "-I (opción del compilador) [C++]"
  - "directorios de inclusión, opción del compilador [C++]"
  - "establecer directorios de inclusión"
ms.assetid: 3e9add2a-5ed8-4d15-ad79-5b411e313a49
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /I (Directorios de inclusi&#243;n adicionales)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Agrega un directorio a la lista de directorios donde se buscan archivos de inclusión.  
  
## Sintaxis  
  
```  
/I[ ]directory  
```  
  
## Argumentos  
 `directory`  
 Directorio que se agrega a la lista de directorios donde se buscan archivos de inclusión.  
  
## Comentarios  
 Para agregar más de un directorio, use esta opción varias veces.  Sólo se busca en los directorios hasta que se encuentra el archivo de inclusión especificado.  
  
 Puede utilizar esta opción junto con la opción Omitir rutas de acceso de inclusión estándar \([\/X \(Omitir rutas de acceso de inclusión estándar\)](../../build/reference/x-ignore-standard-include-paths.md)\).  
  
 El compilador busca en los directorios en el orden siguiente:  
  
1.  Los directorios que contienen el archivo de código fuente.  
  
2.  Los directorios especificados con la opción **\/I**, en el orden en que CL los encuentra.  
  
3.  Los directorios especificados en la variable de entorno **INCLUDE**.  
  
### Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener información detallada, vea [Cómo: Abrir páginas de propiedades del proyecto](../../misc/how-to-open-project-property-pages.md).  
  
2.  Haga clic en la carpeta **C\/C\+\+**.  
  
3.  Haga clic en la página de propiedades **General**.  
  
4.  Modifique la propiedad **Directorios de inclusión adicionales**.  
  
### Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalIncludeDirectories%2A>.  
  
## Ejemplo  
 El comando siguiente busca los archivos de inclusión solicitados por MAIN.c en el orden siguiente: primero en el directorio donde se encuentra MAIN.c, después en el directorio \\INCLUDE, después en el directorio \\MY\\INCLUDE y, por último, en los directorios asignados a la variable de entorno INCLUDE.  
  
```  
CL /I \INCLUDE /I\MY\INCLUDE MAIN.C  
```  
  
## Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)