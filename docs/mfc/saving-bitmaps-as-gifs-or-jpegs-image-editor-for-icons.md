---
title: "Saving Bitmaps as GIFs or JPEGs (Image Editor for Icons) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.editors.image.editing"
dev_langs: 
  - "C++"
  - "C++"
helpviewer_keywords: 
  - ".gif files, saving bitmaps as"
  - "jpg files, saving bitmaps as"
  - "jpeg files, saving bitmaps as"
  - ".jpg files, saving bitmaps as"
  - "Image editor [C++], converting image formats"
  - "gif files, saving bitmaps as"
  - "bitmaps [C++], converting formats"
  - ".jpeg files, saving bitmaps as"
  - "graphics [C++], converting formats"
  - "images [C++], converting formats"
ms.assetid: 115df69f-10fb-4e6f-906b-853c1e4a54af
caps.latest.revision: 12
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Saving Bitmaps as GIFs or JPEGs (Image Editor for Icons)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Cuando se crea un mapa de bits, la imagen se crea en el formato correspondiente \(.bmp\).  No obstante, es posible guardar la imagen en formato GIF o JPEG o en otros formatos gráficos.  
  
> [!NOTE]
>  Este proceso no se puede aplicar a los iconos y cursores.  
  
### Para crear y guardar un mapa de bits como un archivo .gif o .jpeg  
  
1.  En el menú **Archivo**, elija **Abrir** y, a continuación, haga clic en **Archivo**.  
  
2.  En el **cuadro de diálogo Nuevo archivo**, haga clic en la carpeta de **Visual C\+\+**, seleccione **Archivo de mapa de bits \(.bmp\)** en el cuadro **Plantillas** y haga clic en **Abrir**.  
  
     El mapa de bits se abre en el **Editor de imágenes**.  
  
3.  Haga los cambios necesarios en el nuevo mapa de bits.  
  
4.  Con el mapa de bits todavía abierto en el **Editor de imágenes**, haga clic en **Guardar *nombrearchivo*.bmp como** en el menú **Archivo**.  
  
5.  En el cuadro **Nombre de archivo** del cuadro de diálogo **Guardar archivo como**, escriba el nombre del archivo y la extensión correcta para el tipo de formato de archivo que desee.  Por ejemplo, miarchivo.gif.  
  
     **Nota**  El mapa de bits debe crearse o abrirse fuera del proyecto para poder guardarlo en otro formato.  Si se crea o se abre dentro del proyecto, el comando **Guardar como** no estará disponible.  Para obtener más información, vea [Ver recursos en un archivo de script de recursos fuera de un proyecto \(independiente\)](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md).  
  
6.  Haga clic en **Guardar**.  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Recursos de aplicaciones](../Topic/Resources%20in%20Desktop%20Apps.md) en la *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, cómo obtener acceso a recursos, cómo mostrar recursos estáticos y cómo asignar cadenas de recursos a propiedades, vea [Tutorial: Adaptar formularios Windows Forms](http://msdn.microsoft.com/es-es/9a96220d-a19b-4de0-9f48-01e5d82679e5) y [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md).  
  
## Vea también  
 [Editing Graphical Resources](../mfc/editing-graphical-resources-image-editor-for-icons.md)   
 [Image Editor for Icons](../mfc/image-editor-for-icons.md)