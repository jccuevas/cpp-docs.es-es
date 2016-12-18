---
title: "/FUNCTIONPADMIN (Crear una imagen a la que se puede aplicar una revisi&#243;n reciente) | Microsoft Docs"
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
  - "/functionpadmin"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/FUNCTIONPADMIN (opción del vinculador)"
  - "-FUNCTIONPADMIN (opción del vinculador)"
ms.assetid: 25b02c13-1add-4fbd-add9-fcb30eb2cae7
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /FUNCTIONPADMIN (Crear una imagen a la que se puede aplicar una revisi&#243;n reciente)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Prepara una imagen para aplicar una revisión activa.  
  
## Sintaxis  
  
```  
/FUNCTIONPADMIN[:space]  
```  
  
## Comentarios  
 where,  
  
 `space` \(opcional\)  
 La cantidad de relleno a agregar al principio de cada función, 5, 6, 16. imágenes x86 requieren cinco bytes de relleno, imágenes x64 requieren 6 bytes, y las imágenes de compilación para la familia de procesadores Itanium requieren 16 bytes de relleno al principio de cada función.  
  
 De manera predeterminada, el compilador agregará la cantidad de espacio correcta a la imagen, en función del tipo de equipo de la imagen.  
  
 Para que el vinculador genere una imagen a la que se pueda aplicar una revisión reciente, los archivos .obj se deben haber compilado con [\/hotpatch \(Crear una imagen a la que se puede aplicar una revisión reciente\)](../../build/reference/hotpatch-create-hotpatchable-image.md).  
  
 Cuando compila y vincula una imagen con una invocación única de cl.exe, **\/hotpatch** implica **\/functionpadmin**.  
  
### Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener más información, vea [Establecer las propiedades de un proyecto de Visual C\+\+](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en la carpeta **Vinculador**.  
  
3.  Haga clic en la página de propiedades **Línea de comandos**.  
  
4.  Escriba la opción en el cuadro **Opciones adicionales**.  
  
### Para establecer esta opción del vinculador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.  
  
## Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)