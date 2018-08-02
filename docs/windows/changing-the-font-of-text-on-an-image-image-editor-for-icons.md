---
title: Cambiar la fuente del texto de una imagen (Editor de imágenes para iconos) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- fonts, changing on an image
ms.assetid: b8849d40-d401-4e06-808f-e615cb2bee3b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 16d01d634b44b4e6da425c40e011106021638305
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/02/2018
ms.locfileid: "39461743"
---
# <a name="changing-the-font-of-text-on-an-image-image-editor-for-icons"></a>Cambiar la fuente o el texto de una imagen (Editor de imágenes para iconos)
El procedimiento siguiente es un ejemplo de cómo:  
  
-   Agregar texto a un icono en una aplicación de Windows  
  
-   Manipular la fuente del texto  
  
### <a name="to-change-the-font-of-text-on-an-image"></a>Para cambiar la fuente del texto de una imagen  
  
1.  Cree una aplicación de formularios de Windows de C++. Para obtener más información, consulte [crear un proyecto de aplicación Windows](http://msdn.microsoft.com/b2f93fed-c635-4705-8d0e-cf079a264efa). El [plantilla de aplicación de Windows Forms](http://msdn.microsoft.com/1babdebf-ab3f-4a64-a608-98499a5b9cea) agrega un archivo denominado app.ico al proyecto de forma predeterminada.  
  
2.  En el Explorador de soluciones, haga doble clic en el archivo app.ico. El [Editor de imágenes](../windows/image-editor-for-icons.md) se abrirá.  
  
3.  Desde el **imagen** menú, seleccione **herramientas** y, a continuación, seleccione **texto herramienta**. El [cuadro de diálogo Herramienta de texto](../windows/text-tool-dialog-box-image-editor-for-icons.md) aparecerá.  
  
4.  En el **texto herramienta** cuadro de diálogo, escriba `C++` en el área de texto vacío. Este texto aparecerá en un cuadro de tamaño ajustable ubicado en la esquina superior izquierda del archivo app.ico, en el **Editor de imágenes**.  
  
5.  En el **Editor de imágenes**, arrastre el cuadro de tamaño variable en el centro del archivo app.ico para mejorar la legibilidad del texto.  
  
6.  En el **texto herramienta** cuadro de diálogo, haga clic en el **fuente** botón. El [cuadro de diálogo fuente de herramienta de texto](../windows/text-tool-font-dialog-box-image-editor-for-icons.md) aparecerá.  
  
7.  En el **fuente de herramienta de texto** cuadro de diálogo, seleccione **Times New Roman** en la lista de fuentes disponibles que aparecen en la **fuente** cuadro de lista.  
  
8.  Seleccione **negrita** en la lista de estilos de fuentes disponibles aparecen en la **estilo de fuente** cuadro de lista.  
  
9. Seleccione **10** en la lista de disponibles, seleccione tamaños que se muestran en el **tamaño** cuadro de lista.  
  
10. Haga clic en el **Aceptar** botón. El **fuente de herramienta de texto** cuadro de diálogo se cerrará y se aplicará la nueva configuración de fuente al texto.  
  
11. Haga clic en el **cerrar** situado en la **texto herramienta** cuadro de diálogo. El cuadro de tamaño ajustable alrededor del texto desaparecerá del Editor de imágenes.  
  
## <a name="see-also"></a>Vea también  
 [Editar recursos gráficos](../windows/editing-graphical-resources-image-editor-for-icons.md)   
 [Toolbar](../windows/toolbar-image-editor-for-icons.md)