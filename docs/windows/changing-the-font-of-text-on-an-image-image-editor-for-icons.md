---
title: "Cambiar la fuente del texto de una imagen (Editor de imágenes para iconos) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: fonts, changing on an image
ms.assetid: b8849d40-d401-4e06-808f-e615cb2bee3b
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 86942af0085bf749c8e1bbbab27a9a674164da79
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="changing-the-font-of-text-on-an-image-image-editor-for-icons"></a>Cambiar la fuente o el texto de una imagen (Editor de imágenes para iconos)
El procedimiento siguiente es un ejemplo de cómo:  
  
-   Agregar texto a un icono en una aplicación de Windows  
  
-   Manipular la fuente del texto  
  
### <a name="to-change-the-font-of-text-on-an-image"></a>Para cambiar la fuente del texto de una imagen  
  
1.  Cree una aplicación de formularios de Windows en C++. Para obtener más información, consulte [crear un proyecto de aplicación de Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa). El [plantilla de aplicación de Windows Forms](http://msdn.microsoft.com/en-us/1babdebf-ab3f-4a64-a608-98499a5b9cea) agrega un archivo denominado app.ico al proyecto de forma predeterminada.  
  
2.  En el Explorador de soluciones, haga doble clic en el archivo app.ico. El [Editor de imágenes](../windows/image-editor-for-icons.md) se abrirá.  
  
3.  Desde el **imagen** menú, seleccione **herramientas** y, a continuación, seleccione **herramienta texto**. El [cuadro de diálogo Herramienta de texto](../windows/text-tool-dialog-box-image-editor-for-icons.md) aparecerá.  
  
4.  En el cuadro de diálogo Herramienta de texto, escriba `C++` en el área de texto vacío. Este texto aparecerá en un cuadro redimensionable situado en la esquina superior izquierda del archivo app.ico, en el Editor de imágenes.  
  
5.  En el Editor de imágenes, arrastre el cuadro de tamaño variable en el centro del archivo app.ico para mejorar la legibilidad del texto.  
  
6.  En el cuadro de diálogo Herramienta de texto, haga clic en el **fuente** botón. El [cuadro de diálogo fuente de herramienta de texto](../windows/text-tool-font-dialog-box-image-editor-for-icons.md) aparecerá.  
  
7.  En el cuadro de diálogo fuente de herramienta de texto, seleccione **Times New Roman** en la lista de fuentes disponibles que aparecen en la **fuente** cuadro de lista.  
  
8.  Seleccione **negrita** en la lista de estilos de fuente disponibles aparecen en la **estilo de fuente** cuadro de lista.  
  
9. Seleccione **10** en la lista de elementos disponibles, seleccione tamaños que se muestran en la **tamaño** cuadro de lista.  
  
10. Haga clic en el **Aceptar** botón. Se cerrará el cuadro de diálogo de fuente de herramienta de texto y se aplicará la nueva configuración de fuente al texto.  
  
11. Haga clic en el **cerrar** botón en el cuadro de diálogo Herramienta de texto. El cuadro redimensionable que rodea el texto desaparecerá del Editor de imágenes.  
  
## <a name="see-also"></a>Vea también  
 [Editar recursos gráficos](../windows/editing-graphical-resources-image-editor-for-icons.md)   
 [Barra de herramientas](../windows/toolbar-image-editor-for-icons.md)

