---
title: "La imagen de menú (Editor de imágenes para iconos) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.editors.bitmap
dev_langs: C++
helpviewer_keywords: Image menu
ms.assetid: ac2b4d53-1919-4fd1-a0af-d3c085c45af2
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 49da8f90703190be068fe2d35a808b2cafed6f0c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="image-menu-image-editor-for-icons"></a>Imagen (Menú) (Editor de imágenes para iconos)
El menú imagen, que aparece únicamente cuando el editor de imágenes está activo, contiene comandos de edición de imágenes, administración de paletas de colores y establecer opciones de la ventana de Editor de imágenes. Además, los comandos para el uso de imágenes de dispositivos están disponibles cuando se trabaja con iconos y cursores.  
  
 **Invertir colores**  
 Invierte los colores. Para obtener más información, consulte [invertir los colores de una selección](../windows/inverting-the-colors-in-a-selection-image-editor-for-icons.md).  
  
 **Voltear horizontalmente**  
 Voltea la imagen o la selección en sentido horizontal. Para obtener más información, consulte [voltear una imagen](../windows/flipping-an-image-image-editor-for-icons.md).  
  
 **Voltear verticalmente**  
 Voltea la imagen o la selección en sentido vertical. Para obtener más información, consulte [voltear una imagen](../windows/flipping-an-image-image-editor-for-icons.md).  
  
 **Girar 90 grados**  
 Gira la imagen o la selección 90 grados. Para obtener más información, consulte [voltear una imagen](../windows/flipping-an-image-image-editor-for-icons.md).  
  
 **Mostrar ventana colores**  
 Se abre la [ventana colores](../windows/colors-window-image-editor-for-icons.md), en la que puede elegir los colores que se usará para la imagen. Para obtener más información, consulte [trabajar con colores](../windows/working-with-color-image-editor-for-icons.md).  
  
 **Usar la selección como pincel**  
 Le permite crear un pincel personalizado a partir de una parte de una imagen. La selección se convierte en un pincel personalizado que distribuye los colores de la selección en la imagen. Se mantienen copias de la selección a lo largo de la ruta de acceso de arrastrar. Cuanto más lenta arrastre, se realizan las copias más. Para obtener más información, consulte [crear un pincel personalizado](../windows/creating-a-custom-brush-image-editor-for-icons.md).  
  
 **Copiar y resaltar selección**  
 Crea una copia de la selección actual y la resalta. Si el color de fondo está incluido en la selección actual, se excluirá si tienes [transparente](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md) seleccionado.  
  
 **Ajustar colores**  
 Se abre la [Selector de colores personalizados](../windows/custom-color-selector-dialog-box-image-editor-for-icons.md), que le permite personalizar los colores utilizados en la imagen. Para obtener más información, consulte [personalizar o cambiar colores](../windows/customizing-or-changing-colors-image-editor-for-icons.md).  
  
 **Cargar paleta**  
 Se abre la [cuadro de diálogo Cargar paleta de colores](../windows/load-palette-colors-dialog-box-image-editor-for-icons.md), lo que permite cargar paletas de colores guardadas anteriormente en un archivo. PAL.  
  
 **Guardar paleta**  
 Guarda la paleta de colores en un archivo. PAL.  
  
 **Dibujar opaco**  
 Cuando se selecciona, hace que la selección actual opaco. Cuando está desactivada, clarifica la selección actual. Para obtener más información, consulte [elegir un fondo transparente u opaco](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md).  
  
 **Editor de barras de herramientas**  
 Se abre la [cuadro de diálogo nuevo recurso de barra de herramientas](../windows/new-toolbar-resource-dialog-box.md).  
  
 **Configuración de la cuadrícula**  
 Se abre la [cuadro de diálogo de configuración de la cuadrícula](../windows/grid-settings-dialog-box-image-editor-for-icons.md) en el que puede especificar cuadrículas para la imagen.  
  
 **Nuevo tipo de imagen**  
 Se abre la [New \<dispositivo > cuadro de diálogo tipo de imagen](../windows/new-device-image-type-dialog-box-image-editor-for-icons.md). Un solo recurso de icono puede contener varias imágenes de tamaños diferentes; Windows pueden usar el tamaño de icono adecuado dependiendo de cómo se van a mostrarse. Un nuevo tipo de dispositivo no modifica el tamaño del icono, sino que crea una nueva imagen en el icono. Solo se aplica a los iconos y cursores.  
  
 **Tipo de imagen de icono/Cursor actual**  
 Se abre un submenú que contiene el primer cursor o icono de imágenes disponibles (las nueve primeras). El último comando en el submenú, **más...** , se abre la [abiertos \<dispositivo > cuadro de diálogo imagen](../windows/open-device-image-dialog-box-image-editor-for-icons.md).  
  
 **Eliminar tipo de imagen**  
 Elimina la imagen de dispositivo seleccionado.  
  
 **Herramientas**  
 Inicia un submenú que contiene todas las herramientas disponibles en la [barra de herramientas del Editor de imágenes](../windows/toolbar-image-editor-for-icons.md).  
  
## <a name="requirements"></a>Requisitos  
 Ninguna  
  
## <a name="see-also"></a>Vea también  
 [Teclas de aceleración](../windows/accelerator-keys-image-editor-for-icons.md)   
 [Editor de imágenes para iconos](../windows/image-editor-for-icons.md)

