---
title: "/FR, /Fr (Crear archivo .Sbr) | Microsoft Docs"
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
  - "VC.Project.VCCLWCECompilerTool.BrowseInformation"
  - "VC.Project.VCCLCompilerTool.BrowseInformation"
  - "/fr"
  - "VC.Project.VCCLCompilerTool.BrowseInformationFile"
  - "VC.Project.VCCLWCECompilerTool.BrowseInformationFile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/FR (opción del compilador) [C++]"
  - "FR (opción del compilador) [C++]"
  - "-FR (opción del compilador) [C++]"
  - "información simbólica del explorador"
ms.assetid: 3fd8f88b-3924-4feb-9393-287036a28896
caps.latest.revision: 18
caps.handback.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /FR, /Fr (Crear archivo .Sbr)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Crea archivos. sbr.  
  
## Sintaxis  
  
```  
/FR[pathname[\filename]]  
/Fr[pathname[\filename]]  
```  
  
## Comentarios  
 Durante el proceso de compilación, la Utilidad de mantenimiento de información de examen de Microsoft \(BSCMAKE\) usa estos archivos para crear un archivo .BSC, que se usa para mostrar la información del examen.  
  
 **\/FR** crea un archivo .sbr con información simbólica completa.  
  
 **\/Fr** crea un archivo .sbr sin información sobre variables locales.  
  
 Si no se especifica el valor de `filename`, el archivo .sbr recibe el mismo nombre base que el archivo de origen.  
  
 **\/Fr** está en desuso. Use **\/FR** en su lugar. Para obtener más información, consulte Opciones de compilador en desuso y quitadas en [Opciones del compilador por categoría](../../build/reference/compiler-options-listed-by-category.md).  
  
> [!NOTE]
>  No cambie la extensión. sbr. BSCMAKE requiere esta extensión en los archivos intermedios.  
  
### Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener información detallada, vea [Cómo: Abrir páginas de propiedades del proyecto](../../misc/how-to-open-project-property-pages.md).  
  
2.  En el panel de navegación, elija **C o C\+\+** y, a continuación, página de propiedades **Información de examen**.  
  
3.  Modifique el **Archivo de información de examen** o la propiedad **Habilitar información de examen**.  
  
### Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.BrowseInformation%2A> y <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.BrowseInformationFile%2A>.  
  
## Vea también  
 [\/F \(Opciones del archivo de resultados\)](../../build/reference/output-file-f-options.md)   
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)   
 [Especificar la ruta de acceso](../../build/reference/specifying-the-pathname.md)