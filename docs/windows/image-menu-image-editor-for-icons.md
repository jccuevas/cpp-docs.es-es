---
title: "Imagen (Men&#250;) (Editor de im&#225;genes para iconos) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.editors.bitmap"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Imagen (menú)"
ms.assetid: ac2b4d53-1919-4fd1-a0af-d3c085c45af2
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 4
---
# Imagen (Men&#250;) (Editor de im&#225;genes para iconos)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El menú Imagen, que aparece únicamente mientras el Editor de imágenes está activo, contiene comandos de edición de imágenes, administración de paletas de colores y configuración de opciones de la ventana del Editor de imágenes.  Asimismo, ofrece comandos para uso de imágenes de dispositivos cuando se trabaja con iconos y cursores.  
  
 **Invertir colores**  
 Invierte los colores.  Para obtener más información, vea [Invertir los colores de una selección](../windows/inverting-the-colors-in-a-selection-image-editor-for-icons.md).  
  
 **Voltear horizontalmente**  
 Voltea la imagen o la selección en sentido horizontal.  Para obtener más información, vea [Voltear una imagen](../mfc/flipping-an-image-image-editor-for-icons.md).  
  
 **Voltear verticalmente**  
 Voltea la imagen o la selección en sentido vertical.  Para obtener más información, vea [Voltear una imagen](../mfc/flipping-an-image-image-editor-for-icons.md).  
  
 **Girar 90 grados**  
 Gira la imagen o la selección 90 grados.  Para obtener más información, vea [Voltear una imagen](../mfc/flipping-an-image-image-editor-for-icons.md).  
  
 **Mostrar ventana Colores**  
 Abre la [ventana Colores](../Topic/Colors%20Window%20\(Image%20Editor%20for%20Icons\).md), donde pueden elegirse los colores que utiliza la imagen.  Para obtener más información, vea [Trabajar con colores](../mfc/working-with-color-image-editor-for-icons.md).  
  
 **Usar la selección como pincel**  
 Permite crear un pincel personalizado a partir de una parte de una imagen.  La selección se convierte en un pincel personalizado que distribuye los colores que contiene en la imagen.  Se sitúan copias de la selección a lo largo de la trayectoria de arrastre.  Cuanto menor sea la velocidad de arrastre, más copias se crearán.  Para obtener más información, vea [Crear un pincel personalizado](../mfc/creating-a-custom-brush-image-editor-for-icons.md).  
  
 **Copiar y resaltar selección**  
 Crea una copia de la selección actual y la resalta.  Si la selección actual contiene el color de fondo, se excluirá si ha seleccionado [transparente](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md).  
  
 **Ajustar colores**  
 Abre el [Selector de colores personalizados](../windows/custom-color-selector-dialog-box-image-editor-for-icons.md), que permite personalizar los colores utilizados en la imagen.  Para obtener más información, vea [Personalizar o cambiar colores](../windows/customizing-or-changing-colors-image-editor-for-icons.md).  
  
 **Cargar paleta**  
 Abre el [cuadro de diálogo Cargar paleta de colores](../windows/load-palette-colors-dialog-box-image-editor-for-icons.md), que permite cargar paletas de colores guardadas anteriormente en un archivo .pal.  
  
 **Guardar paleta**  
 Guarda los colores de la paleta en un archivo .pal.  
  
 **Dibujar figuras opacas**  
 Si está seleccionada, convierte en opaca la selección actual.  De lo contrario, la convierte en transparente.  Para obtener más información, vea [Elegir un fondo transparente u opaco](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md).  
  
 **Editor de barras de herramientas**  
 Se abrirá el [cuadro de diálogo Nuevo recurso de la barra de herramientas](../mfc/new-toolbar-resource-dialog-box.md).  
  
 **Configuración de la cuadrícula**  
 Abre el [cuadro de diálogo Configuración de cuadrícula](../mfc/grid-settings-dialog-box-image-editor-for-icons.md), donde se especifican las opciones de la cuadrícula de las imágenes.  
  
 **Nuevo tipo de imagen**  
 Abre el [cuadro de diálogo Nuevo tipo de imagen de \<dispositivo\>](../mfc/new-device-image-type-dialog-box-image-editor-for-icons.md).  Un solo recurso de icono puede contener varias imágenes de tamaños diferentes; las ventanas pueden usar el tamaño de icono apropiado, dependiendo de cómo sea su presentación.  Un tipo de dispositivo nuevo no modifica el tamaño del icono, sino crea una imagen nueva dentro del icono.  Esto solamente se aplica a los iconos y los cursores.  
  
 **Tipos de imagen de icono\/cursor actual**  
 Abre un submenú con las primeras imágenes disponibles de cursor o icono \(las nueve primeras\).  El último comando del submenú, **Más**, abre el [cuadro de diálogo Abrir imagen de \<dispositivo\>](../mfc/open-device-image-dialog-box-image-editor-for-icons.md).  
  
 **Eliminar tipo de imagen**  
 Elimina la imagen de dispositivo seleccionada.  
  
 **Herramientas**  
 Inicia un submenú que contiene todas las herramientas disponibles en la [barra de herramientas del Editor de imágenes](../mfc/toolbar-image-editor-for-icons.md).  
  
## Requisitos  
 None  
  
## Vea también  
 [Accelerator Keys](../mfc/accelerator-keys-image-editor-for-icons.md)   
 [Image Editor for Icons](../mfc/image-editor-for-icons.md)