---
title: "/FS (forzar escrituras de PDB sincr&#243;nicas) | Microsoft Docs"
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
  - "/FS"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "-FS (opción del compilador) [C++]"
  - "/FS (opción del compilador) [C++]"
ms.assetid: b2caaffe-f6e1-4963-b068-648f06b105e0
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /FS (forzar escrituras de PDB sincr&#243;nicas)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Fuerza que las escrituras en el archivo de base de datos de programa \(PDB\) \(creado por [\/Zi](../../build/reference/z7-zi-zi-debug-information-format.md) o [\/ZI](../../build/reference/z7-zi-zi-debug-information-format.md)\) se serialicen con MSPDBSRV.EXE.  
  
## Sintaxis  
  
```  
/FS  
```  
  
## Comentarios  
 De forma predeterminada, cuando se especifica **\/Zi** o **\/ZI**, el compilador bloquea los archivos PDB para escribir información de tipo y de depuración simbólica.  Esto puede reducir significativamente el tiempo que tarda el compilador en generar la información de tipos cuando hay muchos tipos.  Si otro proceso bloquea temporalmente el archivo PDB \(por ejemplo, un programa antivirus\), las escrituras del compilador pueden producir errores y puede aparecer un error irrecuperable.  Este problema también puede ocurrir cuando varias copias de cl.exe tienen acceso al mismo archivo PDB, por ejemplo, si la solución tiene proyectos independientes que utilizan los mismos directorios intermedios o si están habilitados los directorios de salida y las compilaciones en paralelo.  La opción del compilador **\/FS** evita que el compilador bloquee el archivo PDB y fuerza las escrituras a través de MSPDBSRV.EXE, que serializa el acceso.  Esto puede prolongar las compilaciones y no evita todos los errores que pueden aparecer cuando varias instancias de cl.exe tienen acceso al archivo PDB al mismo tiempo.  Recomendamos cambiar la solución de forma que los proyectos independientes escriban en ubicaciones intermedias y de salida separadas, o de forma que uno de los proyectos dependa del otro para forzar las compilaciones de proyecto serializadas.  
  
 La opción [\/MP](../../build/reference/mp-build-with-multiple-processes.md) habilita **\/FS** de forma predeterminada.  
  
### Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener información detallada, vea [Trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Seleccione la carpeta **C\/C\+\+**.  
  
3.  Seleccione la página de propiedades **Línea de comandos**.  
  
4.  Modifique la propiedad **Opciones adicionales** para incluir `/FS` y, a continuación, elija **Aceptar**.  
  
### Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)