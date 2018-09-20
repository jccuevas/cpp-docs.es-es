---
title: Mostrar u ocultar la barra de herramientas del Editor de cuadro de diálogo (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- controls [C++], showing or hiding Dialog editor toolbar
- toolbars [C++], showing
- toolbars [C++], hiding
- Dialog Editor [C++], showing or hiding toolbar
ms.assetid: 93c255e1-90eb-48b6-8602-450acda75bed
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 02deeeed3eecf717cff380e43317e5a75c1fddf7
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46381249"
---
# <a name="showing-or-hiding-the-dialog-editor-toolbar-c"></a>Mostrar u ocultar la barra de herramientas del Editor de cuadro de diálogo (C++)

Al abrir el **diálogo** editor en un proyecto de C++, el **Editor de cuadro de diálogo** barra de herramientas aparece automáticamente en la parte superior de la solución.

### <a name="dialog-editor-toolbar"></a>Barra de herramientas del Editor de cuadros de diálogo

|Iconos|Significado|Iconos|Significado|
|----------|-------------|----------|-------------|
|![Botón de cuadro de diálogo de prueba](../mfc/media/vcdialogeditortestdialog.png "vcDialogEditorTestDialog")|Probar cuadro de diálogo|![Botón espaciar horizontalmente](../mfc/media/vcdialogeditoracross.png "vcDialogEditorAcross")|Horizontalmente|
|![Botón Alinear lados izquierdos](../mfc/media/vcdialogeditoralignlefts.png "vcDialogEditorAlignLefts")|Alinear lados izquierdos|![Botón Espaciar verticalmente](../mfc/media/vcdialogeditordown.png "vcDialogEditorDown")|Verticalmente|
|![Botón Alinear lados derechos](../mfc/media/vcdialogeditoralignrights.png "vcDialogEditorAlignRights")|Alinear lados derechos|![Asegúrese de mismo ancho botón](../mfc/media/vcdialogeditorsamewidth.png "vcDialogEditorSameWidth")|Igualar ancho|
|![Botón Alinear lados superiores](../mfc/media/vcdialogeditoraligntops.png "vcDialogEditorAlignTops")|Alinear lados superiores|![Botón de la misma altura de Make](../mfc/media/vcdialogeditormakesameheight.png "vcDialogEditorMakeSameHeight")|Igualar alto|
|![Botón Alinear lados inferiores](../mfc/media/vcdialogeditoralignbottoms.png "vcDialogEditorAlignBottoms")|Alinear lados inferiores|![Botón de tamaño de la misma marca](../mfc/media/vcdialogeditorsamesize.png "vcDialogEditorSameSize")|Igualar tamaño|
|![Botón Centrar verticalmente](../mfc/media/vcdialogeditorvertical.png "vcDialogEditorVertical")|Vertical|![Botón Alternar cuadrícula](../mfc/media/vcdialogeditortogglegrid.png "vcDialogEditorToggleGrid")|Alternar cuadrícula|
|![Botón Centrar horizontalmente](../mfc/media/vcdialogeditorhorizontal.png "vcDialogEditorHorizontal")|Horizontal|![Botón Alternar guías](../mfc/media/vcdialogeditortoggleguides.png "vcDialogEditorToggleGuides")|Alternar guías|

El **Editor de cuadro de diálogo** barra de herramientas contiene botones para organizar el diseño de controles en el cuadro de diálogo, por ejemplo tamaño y la alineación. **Cuadro de diálogo Editor** botones de barra de herramientas se corresponden con los comandos de la **formato** menú. Para obtener más información, consulte [teclas de aceleración del Editor de cuadros de diálogo](../windows/accelerator-keys-for-the-dialog-editor.md).

Cuando esté en el **diálogo** editor, puede alternar la presentación de la **Editor de cuadro de diálogo** barra de herramientas, selecciónelo en la lista de ventanas y barras de herramientas disponibles.

### <a name="to-show-or-hide-the-dialog-editor-toolbar"></a>Para mostrar u ocultar la barra de herramientas del editor de cuadro de diálogo

1. En el **vista** menú haga clic en **las barras de herramientas** , a continuación, elija **Editor de cuadro de diálogo** desde el submenú.

   > [!NOTE]
   > El **Editor de cuadro de diálogo** barra de herramientas se muestra de forma predeterminada al abrir un recurso de cuadro de diálogo en el editor de cuadro de diálogo; sin embargo, si cierra explícitamente la barra de herramientas, debe invocarse la próxima vez que abra un recurso de cuadro de diálogo.

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Distribución de los controles en los cuadros de diálogo](../windows/arrangement-of-controls-on-dialog-boxes.md)<br/>
[Procedimiento para crear un recurso](../windows/how-to-create-a-resource.md)<br/>
[Archivos de recursos](../windows/resource-files-visual-studio.md)<br/>
[Editor de cuadros de diálogo](../windows/dialog-editor.md)