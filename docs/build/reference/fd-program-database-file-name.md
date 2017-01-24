---
title: "/Fd (Nombre del archivo de base de datos del programa) | Microsoft Docs"
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
  - "/FD"
  - "VC.Project.VCCLWCECompilerTool.ProgramDataBaseFileName"
  - "VC.Project.VCCLCompilerTool.ProgramDataBaseFileName"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".pdb (archivos), crear"
  - "/FD (opción del compilador) [C++]"
  - "FD (opción del compilador) [C++]"
  - "-FD (opción del compilador) [C++]"
  - "PDB (archivos), crear"
  - "base de datos de programa (opción del compilador) [C++]"
  - "nombre de archivo de la base de datos de programa [C++]"
ms.assetid: 3977a9ed-f0ac-45df-bf06-01cedd2ba85a
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /Fd (Nombre del archivo de base de datos del programa)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Especifica un nombre de archivo para el archivo de base de datos de programa \(PDB\) creado mediante [\/Z7, \/Zi, \/ZI \(Formato de la información de depuración\)](../../build/reference/z7-zi-zi-debug-information-format.md).  
  
## Sintaxis  
  
```  
/Fdpathname  
```  
  
## Comentarios  
 Sin **\/Fd**, el nombre de archivo PDB tiene el valor predeterminado VC`x`0.pdb., donde `x` es la versión principal de Visual C\+\+ en uso.  
  
 Si especifica un nombre de ruta de acceso que no contiene un nombre de archivo \(finaliza la ruta en la barra diagonal inversa\), el compilador crea un archivo .pdb denominado VC`x`0.pdb en el directorio especificado.  
  
 Si especifica un nombre de archivo sin extensión, el compilador usa la extensión .pdb.  
  
 Esta opción también asigna un nombre al archivo de estado \(.idb\) que se utiliza para la recompilación mínima y la compilación incremental.  
  
### Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener información detallada, vea [Cómo: Abrir páginas de propiedades del proyecto](../../misc/how-to-open-project-property-pages.md).  
  
2.  Haga clic en la carpeta **C\/C\+\+**.  
  
3.  Haga clic en la página de propiedades **Archivos de resultados**.  
  
4.  Modifique la propiedad **Nombre de archivo de la base de datos de programas**.  
  
### Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ProgramDataBaseFileName%2A>.  
  
## Ejemplo  
 Esta línea de comandos crea un archivo .pdb denominado PROG.pdb y un archivo .idb denominado PROG.idb:  
  
```  
CL /DDEBUG /Zi /FdPROG.PDB PROG.CPP  
```  
  
## Vea también  
 [\/F \(Opciones del archivo de resultados\)](../../build/reference/output-file-f-options.md)   
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)   
 [Especificar la ruta de acceso](../../build/reference/specifying-the-pathname.md)