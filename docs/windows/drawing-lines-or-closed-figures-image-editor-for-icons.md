---
title: Dibujar líneas o figuras cerradas (Editor de imágenes para iconos) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- closed figures, drawing
- lines [C++], painting
- lines [C++], drawing
- Image editor [C++], drawing lines
- shapes, drawing
ms.assetid: 7edd86db-77b1-451f-8001-bbfed9c6304f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6e2defbde7963c6e58cdfe3f4a25ea550ad88e5f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
---
# <a name="drawing-lines-or-closed-figures-image-editor-for-icons"></a>Dibujar líneas o figuras cerradas (Editor de imágenes para iconos)
El editor de imágenes de las herramientas de dibujo de líneas y figuras cerradas todas las funcionan de la misma manera: coloque el punto de inserción en un punto y arrastre a otro. Para las líneas, estos puntos son los puntos de conexión. Figuras cerradas, estos puntos son los vértices opuestos de un rectángulo delimitador en la ilustración.  
  
 Las líneas se dibujan con un ancho determinado por la selección de pincel actual, y las figuras enmarcadas se dibujan con un ancho determinado por la selección actual de ancho. Líneas y las figuras, tanto enmarcadas como las rellenas, se dibujan en el color de primer plano actual si presiona el botón primario del mouse, o en el color de fondo actual, si presiona el botón secundario del mouse.  
  
### <a name="to-draw-a-line"></a>Para dibujar una línea  
  
1.  En el [barra de herramientas del Editor de imágenes](../windows/toolbar-image-editor-for-icons.md) (o desde el **imagen** menú, **herramientas** comandos), haga clic en el **línea** herramienta.  
  
2.  Si es necesario, seleccione los colores y un pincel:  
  
    -   En el [paleta de colores](../windows/colors-window-image-editor-for-icons.md), haga clic en el botón primario del mouse para seleccionar un color de primer plano o el botón secundario del mouse para seleccionar un color de fondo.  
  
    -   En el [selector de opciones](../windows/toolbar-image-editor-for-icons.md), haga clic en una forma que representa el pincel que se va a utilizar.  
  
3.  Coloque el puntero en el punto de partida de la línea.  
  
4.  Arrastre hasta el extremo de la línea.  
  
### <a name="to-draw-a-closed-figure"></a>Para dibujar una figura cerrada.  
  
1.  En el **Editor de imágenes** barra de herramientas (o desde el **imagen** menú, **herramientas** comandos), haga clic en un **dibujo de figuras cerradas** herramienta.  
  
     El **dibujo de figuras cerradas** herramientas crean figuras tal como se indica en sus respectivos botones.  
  
2.  Si es necesario, seleccione los colores y un ancho de línea.  
  
3.  Mueva el puntero a una de las esquinas del área rectangular en la que va a dibujar en la ilustración.  
  
4.  Arrastre el puntero hacia la esquina diagonalmente opuesta.  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [recursos en aplicaciones de escritorio](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework.* Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, tener acceso a recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).  
  
 Requisitos  
  
 Ninguna  
  
## <a name="see-also"></a>Vea también  
 [Teclas de aceleración](../windows/accelerator-keys-image-editor-for-icons.md)   
 [Editar recursos gráficos](../windows/editing-graphical-resources-image-editor-for-icons.md)   
 [Editor de imágenes para iconos](../windows/image-editor-for-icons.md)   
 [Trabajar con colores](../windows/working-with-color-image-editor-for-icons.md)

