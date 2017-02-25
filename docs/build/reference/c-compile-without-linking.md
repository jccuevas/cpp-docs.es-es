---
title: "/c (Compilar sin vincular) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/c"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/c (opción del compilador) [C++]"
  - "c (opción del compilador) [C++]"
  - "-c (opción del compilador) [C++]"
  - "cl.exe (compilador), compilar sin vincular"
  - "suprimir vínculo"
ms.assetid: 8017fc3d-e5dd-4668-a1f7-3120daa95d20
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# /c (Compilar sin vincular)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Evita la llamada automática a LINK.  
  
## Sintaxis  
  
```  
/c  
```  
  
## Comentarios  
 La compilación con **\/c** crea solamente archivos .obj.  Debe llamar a LINK de manera explícita con los archivos y opciones correctos para realizar la fase de vinculación de la compilación.  
  
 Todos los proyectos internos creados en el entorno de desarrollo usan de forma predeterminada la opción **\/c**.  
  
### Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
-   Esta opción no está disponible dentro del entorno de desarrollo.  
  
### Para establecer esta opción del compilador mediante programación  
  
-   Para establecer esta opción del compilador mediante programación, vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.CompileOnly%2A>.  
  
## Ejemplo  
 La línea de comandos siguiente crea los archivos de objeto FIRST.obj y SECOND.obj.  THIRD.obj se omite.  
  
```  
CL /c FIRST.C SECOND.C THIRD.OBJ  
```  
  
 Para crear un archivo ejecutable, debe invocar LINK:  
  
```  
LINK firsti.obj second.obj third.obj /OUT:filename.exe  
```  
  
## Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)