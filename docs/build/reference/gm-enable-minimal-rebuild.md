---
title: "/Gm (Habilitar recompilaci&#243;n m&#237;nima) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCCLCompilerTool.MinimalRebuild"
  - "/Gm"
  - "/FD"
  - "VC.Project.VCCLWCECompilerTool.MinimalRebuild"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Gm (opción del compilador) [C++]"
  - "habilitar recompilación mínima (opción del compilador) [C++]"
  - "Gm (opción del compilador) [C++]"
  - "-Gm (opción del compilador) [C++]"
  - "recompilación mínima"
ms.assetid: d8869ce0-d2ea-40eb-8dae-6d2cdb61dd59
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# /Gm (Habilitar recompilaci&#243;n m&#237;nima)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Habilita la recompilación mínima, que determina si es necesario recompilar los archivos de origen de C\+\+ que incluyen definiciones de clases de C\+\+ cambiadas \(almacenadas en archivos de encabezado \(.h\)\).  
  
## Sintaxis  
  
```  
/Gm  
```  
  
## Comentarios  
 El compilador almacena la información de dependencias entre los archivos de origen y las definiciones de clases en el archivo .idb del proyecto durante la primera compilación.  \(La información de dependencias indica qué archivo de origen depende de qué definición de clase y en qué archivo .h está ubicada la definición\). En las compilaciones sucesivas, se usa la información almacenada en el archivo .idb para determinar si es necesario compilar un archivo de origen, aunque incluya un archivo .h modificado.  
  
> [!NOTE]
>  La recompilación mínima se basa en las definiciones de clases que no cambian entre los archivos de inclusión.  Las definiciones de clases deben ser globales del proyecto \(solo debe haber una definición de cada clase\), porque la información de dependencias del archivo .idb se crea para todo el proyecto.  Si alguna clase del proyecto tiene más de una definición, deshabilite la recompilación mínima.  
  
 Dado que el enlazador incremental no admite los metadatos de Windows incluidos en los archivos .obj con la opción [\/ZW \(Compilación de Windows en tiempo de ejecución\)](../../build/reference/zw-windows-runtime-compilation.md), la opción **\/Gm** es incompatible con **\/ZW**.  
  
### Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener información detallada, vea [Cómo: Abrir páginas de propiedades del proyecto](../../misc/how-to-open-project-property-pages.md).  
  
2.  Haga clic en la carpeta **C\/C\+\+**.  
  
3.  Haga clic en la página de propiedades **Generación de código**.  
  
4.  Modifique la propiedad **Habilitar recompilación mínima**.  
  
### Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.MinimalRebuild%2A>.  
  
## Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)