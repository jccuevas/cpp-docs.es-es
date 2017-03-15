---
title: "Changing the Font of Text on an Image (Image Editor for Icons) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "fonts, changing on an image"
ms.assetid: b8849d40-d401-4e06-808f-e615cb2bee3b
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 4
---
# Changing the Font of Text on an Image (Image Editor for Icons)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El siguiente procedimiento es un ejemplo de la forma de:  
  
-   Agregar texto a un icono en una aplicación para Windows  
  
-   Manipular la fuente del texto  
  
### Para cambiar la fuente de texto en una imagen  
  
1.  Cree una aplicación de Windows Forms de C\+\+.  Para obtener más información, vea [Crear un proyecto de aplicación para Windows](http://msdn.microsoft.com/es-es/b2f93fed-c635-4705-8d0e-cf079a264efa).  La [plantilla de aplicación de Windows Forms](http://msdn.microsoft.com/es-es/1babdebf-ab3f-4a64-a608-98499a5b9cea) agrega un archivo denominado app.ico al proyecto de forma predeterminada.  
  
2.  En el Explorador de soluciones, haga doble clic en el archivo app.ico.  Se abrirá el [Editor de imágenes](../mfc/image-editor-for-icons.md).  
  
3.  En el menú **Imagen**, seleccione **Herramientas** y, a continuación, seleccione **Herramienta de texto**.  Aparecerá el [cuadro de diálogo Herramienta de texto](../mfc/text-tool-dialog-box-image-editor-for-icons.md).  
  
4.  En el cuadro de diálogo Herramienta de texto, escriba `C++` en el área de texto vacía.  Este texto aparecerá en un cuadro redimensionable situado en la esquina superior izquierda del archivo app.ico, en el Editor de imágenes.  
  
5.  En el Editor de imágenes, arrastre el cuadro redimensionable hacia el centro del archivo app.ico para mejorar la legibilidad del texto.  
  
6.  En el cuadro de diálogo Herramienta de texto, haga clic en el botón **Fuente**.  Aparecerá el [cuadro de diálogo Fuente de herramienta de texto](../mfc/text-tool-font-dialog-box-image-editor-for-icons.md).  
  
7.  En el cuadro de diálogo Fuente de herramienta de texto, seleccione **Times New Roman** en la lista de fuentes disponibles que se muestra en el cuadro de lista **Fuente**.  
  
8.  Seleccione **Negrita** en la lista de estilos de fuente disponibles que se muestra en el cuadro de lista **Estilo de fuente**.  
  
9. Seleccione **10** en la lista de tamaños en puntos disponibles que se muestra en el cuadro de lista **Tamaño**.  
  
10. Haga clic en el botón **Aceptar**.  El cuadro de diálogo Fuente de herramienta de texto se cerrará y la nueva configuración de fuente se aplicará al texto.  
  
11. Haga clic en el botón **Cerrar** del cuadro de diálogo Herramienta de texto.  El cuadro redimensionable que rodea al texto desaparecerá del Editor de imágenes.  
  
## Vea también  
 [Editing Graphical Resources](../mfc/editing-graphical-resources-image-editor-for-icons.md)   
 [Toolbar](../mfc/toolbar-image-editor-for-icons.md)