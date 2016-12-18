---
title: "Arrastrar im&#225;genes de una lista de im&#225;genes | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CImageList (clase), arrastrar imágenes desde"
  - "arrastrar imágenes de las listas de imágenes"
  - "listas de imágenes [C++], arrastrar imágenes desde"
  - "imágenes [C++], arrastrar de las listas de imágenes"
ms.assetid: af691db8-e4f0-4046-b7b9-9acc68d3713d
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Arrastrar im&#225;genes de una lista de im&#225;genes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[CImageList](../mfc/reference/cimagelist-class.md) incluye funciones para arrastrar una imagen en la pantalla.  Las funciones que arrastre mueven una imagen fácilmente, color, y sin parpadeo del cursor.  Las imágenes enmascaradas y desenmascaradas pueden arrastrarse.  
  
 Comienza de funciones miembro de [BeginDrag](../Topic/CImageList::BeginDrag.md) una operación de arrastre.  Los parámetros incluyen el índice de la imagen para arrastrar y la ubicación de la zona activa dentro de la imagen.  La zona activa es un único píxel que las funciones que arrastre reconocen como ubicación exacta de la imagen.  Normalmente, una aplicación establece la zona activa de modo que coincida con la zona activa del cursor.  La función miembro de [DragMove](../Topic/CImageList::DragMove.md) mueve la imagen a una nueva ubicación.  
  
 La función miembro de [DragEnter](../Topic/CImageList::DragEnter.md) establece la posición inicial de la imagen de arrastre dentro de una ventana y dibuje la imagen en la posición.  Los parámetros incluyen un puntero a la ventana en la que se va a dibujar la imagen y un punto que especifica las coordenadas de posición inicial dentro de la ventana.  Las coordenadas son relativas a la esquina superior izquierda de la ventana, no el área cliente.  Lo mismo se aplica a todas las funciones imagen\- que arrastre que toman coordenadas como parámetros.  Esto significa que debe desplazar los anchos de los elementos de la ventana, como el borde, la barra de título, y la barra de menús, al especificar las coordenadas.  Si especifica un identificador de ventana de **nulo** al llamar a `DragEnter`, las funciones que arrastre dibujan la imagen en el contexto de dispositivo asociado a la ventana del escritorio, y las coordenadas son relativas a la esquina superior izquierda de la pantalla.  
  
 `DragEnter` bloquea el resto de las actualizaciones de la ventana especificada durante la operación de arrastre.  Si necesita realizar cualquier gráfico durante una operación de arrastrar, como resaltar el destino de una operación de arrastrar y colocar, puede ocultar temporalmente la imagen arrastrada utilizando la función miembro de [DragLeave](../Topic/CImageList::DragLeave.md) .  También puede utilizar la función miembro de [DragShowNoLock](../Topic/CImageList::DragShowNolock.md) .  
  
 Llame a [EndDrag](../Topic/CImageList::EndDrag.md) cuando se haga que arrastra la imagen.  
  
 La función miembro de [SetDragCursorImage](../Topic/CImageList::SetDragCursorImage.md) crea una nueva imagen de arrastre combinando la imagen determinada \(normalmente una imagen del cursor del mouse\) con la imagen actual de arrastre.  Dado que las funciones que arrastre usan la nueva imagen durante una operación de arrastre, debe utilizar la función de Windows [ShowCursor](http://msdn.microsoft.com/library/windows/desktop/ms648396) para ocultar el mouse real el cursor después de llamar a `SetDragCursorImage`.  Si no, el sistema puede producirse para tener dos cursores de mouse durante la operación de arrastre.  
  
 Cuando una aplicación llama a `BeginDrag`, el sistema crea una imagen temporal, interna lista y copia imágenes especificada de arrastre a la lista interna.  Puede recuperar un puntero a la lista temporal de la imagen de arrastre utilizando la función miembro de [GetDragImage](../Topic/CImageList::GetDragImage.md) .  La función también recupera la posición actual de arrastre y el desplazamiento de la imagen de arrastre en relación con la posición de arrastre.  
  
## Vea también  
 [Usar CImageList](../mfc/using-cimagelist.md)   
 [Controles](../mfc/controls-mfc.md)