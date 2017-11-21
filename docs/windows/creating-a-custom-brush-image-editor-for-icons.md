---
title: "Crear un pincel personalizado (Editor de imágenes para iconos) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- colors [C++], brush
- brushes, colors
- brushes, creating custom
- images [C++], creating custom brushes
- graphics [C++], custom brushes
- custom brushes
ms.assetid: 750881aa-6f47-4de9-8ca6-a7a12afc6383
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: bbef35e0cfb19cf7bd705e7cf3ba09dabe8092ec
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="creating-a-custom-brush-image-editor-for-icons"></a>Crear un pincel personalizado (Editor de imágenes para iconos)
Un pincel personalizado es una parte rectangular de una imagen que recoja y usar como uno de los pinceles listos para usar el editor de imágenes. Todas las operaciones que puede realizar en una selección, puede realizar en un pincel personalizado también.  
  
### <a name="to-create-a-custom-brush-from-a-portion-of-an-image"></a>Para crear un pincel personalizado a partir de una parte de una imagen  
  
1.  [Seleccione la parte de la imagen](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md) que desea usar para un pincel.  
  
2.  Que contiene el **MAYÚS** clave hacia abajo, haga clic en la selección y arrastre el puntero sobre la imagen.  
  
     \- o -  
  
3.  Desde el **imagen** menú, elija **usar la selección como pincel**.  
  
     La selección se convierte en un pincel personalizado que distribuye los colores de la selección en la imagen. Se mantienen copias de la selección a lo largo de la ruta de acceso de arrastrar. Cuanto más lenta arrastre, se realizan las copias más.  
  
     **Tenga en cuenta** al hacer clic en el **utilizar una selección como pincel** sin seleccionar antes una parte de la imagen se utiliza toda la imagen como un pincel. El resultado de usar un pincel personalizado también depende de si ha seleccionado un [fondo transparente u opaco](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md).  
  
 Píxeles en un pincel personalizado que coinciden con el color de fondo actual normalmente son transparentes: no pintan la imagen existente. Puede cambiar este comportamiento para que los píxeles de color de fondo pintar sobre la imagen existente.  
  
 Puede utilizar el pincel personalizado como un sello o una galería de símbolos para crear una variedad de efectos especiales.  
  
#### <a name="to-draw-custom-brush-shapes-in-the-background-color"></a>Para dibujar formas de pincel personalizado en el color de fondo  
  
1.  [Seleccionar un fondo transparente u opaco](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md).  
  
2.  [Establecer el color de fondo](../windows/selecting-foreground-or-background-colors-image-editor-for-icons.md) el color en el que va a dibujar.  
  
3.  Sitúe el pincel personalizado donde va a dibujar.  
  
4.  Haga clic en el botón secundario del mouse. Las regiones opacas del pincel personalizado se dibujan en el color de fondo.  
  
#### <a name="to-double-or-halve-the-custom-brush-size"></a>Para duplicar o a la mitad el tamaño del pincel personalizado  
  
1.  Presione el **signo** (**+**) clave duplicar el tamaño del pincel, o la **signo** (**-**) para dividirlo .  
  
#### <a name="to-cancel-the-custom-brush"></a>Para cancelar el pincel personalizado  
  
1.  Presione **ESC** o elija otra herramienta de dibujo.  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [recursos en aplicaciones de escritorio](https://msdn.microsoft.com/library/f45fce5x.aspx) en el *Guía del desarrollador de .NET Framework.* Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, tener acceso a recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](https://msdn.microsoft.com/library/xbx3z216.aspx). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](https://msdn.microsoft.com/library/h6270d0z.aspx).  
  
### <a name="requirements"></a>Requisitos  
 Ninguna  
  
## <a name="see-also"></a>Vea también  
 [Teclas de aceleración](../windows/accelerator-keys-image-editor-for-icons.md)   
 [Editar recursos gráficos](../windows/editing-graphical-resources-image-editor-for-icons.md)   
 [Editor de imágenes para iconos](../windows/image-editor-for-icons.md)

