---
title: "/MANIFESTFILE (Nombre del archivo de manifiesto) | Microsoft Docs"
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
  - "VC.Project.VCLinkerTool.ManifestFile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/MANIFESTFILE (opción del vinculador)"
  - "MANIFESTFILE (opción del vinculador)"
  - "-MANIFESTFILE (opción del vinculador)"
ms.assetid: befa5ab2-a9cf-4c9b-969a-e7b4a930f08d
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /MANIFESTFILE (Nombre del archivo de manifiesto)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/MANIFESTFILE:filename  
```  
  
## Comentarios  
 \/MANIFESTFILE permite cambiar el nombre predeterminado del archivo de manifiesto.  El nombre predeterminado del archivo de manifiesto es el nombre de archivo con .manifest anexado.  
  
 \/MANIFESTFILE no tendrá ningún efecto si no vincula también con [\/MANIFEST](../../build/reference/manifest-create-side-by-side-assembly-manifest.md).  
  
### Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener información detallada, vea [Cómo: Abrir páginas de propiedades del proyecto](../../misc/how-to-open-project-property-pages.md).  
  
2.  Expanda el nodo **Propiedades de configuración**.  
  
3.  Expanda el nodo **Vinculador**.  
  
4.  Seleccione la página de propiedades **Archivo de manifiesto**.  
  
5.  Modifique la propiedad **Archivo de manifiesto**.  
  
### Para establecer esta opción del vinculador mediante programación  
  
1.  Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ManifestFile%2A>.  
  
## Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)