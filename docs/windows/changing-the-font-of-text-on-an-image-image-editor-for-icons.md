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
ms.openlocfilehash: 5a49cb4fa88b3a014d79969cc86fc03fa1136efa
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46405351"
---
# <a name="changing-the-font-of-text-on-an-image-image-editor-for-icons"></a>Cambiar la fuente o el texto de una imagen (Editor de imágenes para iconos)

El procedimiento siguiente es un ejemplo de cómo:

- Agregar texto a un icono en una aplicación de Windows

- Manipular la fuente del texto

### <a name="to-change-the-font-of-text-on-an-image"></a>Para cambiar la fuente del texto de una imagen

1. Cree una aplicación de formularios de Windows de C++. Para obtener más información, consulte [crear un proyecto de aplicación Windows](/previous-versions/visualstudio/visual-studio-2010/42wc9kk5\(v=vs.100\)). Un `app.ico` archivo se agrega al proyecto de forma predeterminada.

2. En **el Explorador de soluciones**, haga doble clic en el archivo app.ico. El [Editor de imágenes](../windows/image-editor-for-icons.md) se abrirá.

3. Desde el **imagen** menú, seleccione **herramientas** y, a continuación, seleccione **texto herramienta**. El [cuadro de diálogo Herramienta de texto](../windows/text-tool-dialog-box-image-editor-for-icons.md) aparecerá.

4. En el **texto herramienta** cuadro de diálogo, escriba `C++` en el área de texto vacío. Este texto aparecerá en un cuadro de tamaño ajustable ubicado en la esquina superior izquierda de `app.ico`, en el **Editor de imágenes**.

5. En el **Editor de imágenes**, arrastre el cuadro de tamaño variable en el centro del archivo app.ico para mejorar la legibilidad del texto.

6. En el **texto herramienta** cuadro de diálogo, haga clic en el **fuente** botón. El [cuadro de diálogo fuente de herramienta de texto](../windows/text-tool-font-dialog-box-image-editor-for-icons.md) aparecerá.

7. En el **fuente de herramienta de texto** cuadro de diálogo, seleccione **Times New Roman** en la lista de fuentes disponibles que aparecen en la **fuente** cuadro de lista.

8. Seleccione **negrita** en la lista de estilos de fuentes disponibles aparecen en la **estilo de fuente** cuadro de lista.

9. Seleccione **10** en la lista de disponibles, seleccione tamaños que se muestran en el **tamaño** cuadro de lista.

10. Haga clic en el **Aceptar** botón. El **fuente de herramienta de texto** cuadro de diálogo se cerrará y se aplicará la nueva configuración de fuente al texto.

11. Haga clic en el **cerrar** situado en la **texto herramienta** cuadro de diálogo. El cuadro de tamaño ajustable alrededor del texto desaparecerá de la **Editor de imágenes**.

## <a name="see-also"></a>Vea también

[Editar recursos gráficos](../windows/editing-graphical-resources-image-editor-for-icons.md)<br/>
[Toolbar](../windows/toolbar-image-editor-for-icons.md)