---
title: Mostrar u ocultar la barra de herramientas del Editor de diálogos | Documentos de Microsoft
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
- Dialog editor, showing or hiding toolbar
ms.assetid: 93c255e1-90eb-48b6-8602-450acda75bed
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ad456d37252b40be72217e6cbc40a2a399bb34ef
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
---
# <a name="showing-or-hiding-the-dialog-editor-toolbar"></a>Mostrar u ocultar la barra de herramientas del Editor de cuadros de diálogo
Cuando se abre el editor de cuadro de diálogo, la barra de herramientas del Editor de cuadro de diálogo aparece automáticamente en la parte superior de la solución.  
  
### <a name="dialog-editor-toolbar"></a>Barra de herramientas del Editor de cuadros de diálogo  
  
|Iconos|Significado|Iconos|Significado|  
|----------|-------------|----------|-------------|  
|![Botón de cuadro de diálogo de prueba](../mfc/media/vcdialogeditortestdialog.png "vcDialogEditorTestDialog")|Probar cuadro de diálogo|![Botón espaciar horizontalmente](../mfc/media/vcdialogeditoracross.png "vcDialogEditorAcross")|Horizontalmente|  
|![Botón Alinear lados izquierdos](../mfc/media/vcdialogeditoralignlefts.png "vcDialogEditorAlignLefts")|Alinear lados izquierdos|![Botón Espaciar verticalmente](../mfc/media/vcdialogeditordown.png "vcDialogEditorDown")|Verticalmente|  
|![Botón Alinear lados derechos](../mfc/media/vcdialogeditoralignrights.png "vcDialogEditorAlignRights")|Alinear lados derechos|![Botón de marca mismo ancho](../mfc/media/vcdialogeditorsamewidth.png "vcDialogEditorSameWidth")|Igualar ancho|  
|![Botón Alinear lados superiores](../mfc/media/vcdialogeditoraligntops.png "vcDialogEditorAlignTops")|Alinear lados superiores|![Asegúrese de alto botón](../mfc/media/vcdialogeditormakesameheight.png "vcDialogEditorMakeSameHeight")|Igualar alto|  
|![Botón Alinear lados inferiores](../mfc/media/vcdialogeditoralignbottoms.png "vcDialogEditorAlignBottoms")|Alinear lados inferiores|![Asegúrese de tamaño mismo botón](../mfc/media/vcdialogeditorsamesize.png "vcDialogEditorSameSize")|Igualar tamaño|  
|![Botón Centrar verticalmente](../mfc/media/vcdialogeditorvertical.png "vcDialogEditorVertical")|Vertical|![Botón Alternar cuadrícula](../mfc/media/vcdialogeditortogglegrid.png "vcDialogEditorToggleGrid")|Alternar cuadrícula|  
|![Botón Centrar horizontalmente](../mfc/media/vcdialogeditorhorizontal.png "vcDialogEditorHorizontal")|Horizontal|![Botón Alternar guías](../mfc/media/vcdialogeditortoggleguides.png "vcDialogEditorToggleGuides")|Alternar guías|  
  
 La barra de herramientas del Editor de cuadro de diálogo contiene botones para organizar el diseño de los controles en el cuadro de diálogo, por ejemplo, tamaño y alineación. Botones de barra de herramientas del Editor de cuadro de diálogo se corresponden con los comandos del menú de formato. Para obtener más información, consulte [teclas de aceleración del Editor de cuadros de diálogo](../windows/accelerator-keys-for-the-dialog-editor.md).  
  
 Cuando esté en el editor de cuadro de diálogo, puede alternar la visualización de la barra de herramientas del Editor de cuadro de diálogo, selecciónelo en la lista de ventanas y barras de herramientas disponibles.  
  
### <a name="to-show-or-hide-the-dialog-editor-toolbar"></a>Para mostrar u ocultar la barra de herramientas del editor de cuadro de diálogo  
  
1.  En el **vista** menú haga clic en **las barras de herramientas** , a continuación, elija **Editor de cuadro de diálogo** del submenú.  
  
    > [!NOTE]
    >  La barra de herramientas del Editor de cuadro de diálogo se muestra de forma predeterminada al abrir un recurso de cuadro de diálogo en el editor de cuadro de diálogo; Sin embargo, si cierra explícitamente la barra de herramientas, debe invocar la próxima vez que abra un recurso de cuadro de diálogo.  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [recursos en aplicaciones de escritorio](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework.* Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, tener acceso a recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).  
  
 Requisitos  
  
 Win32  
  
## <a name="see-also"></a>Vea también  
 [Organización de los controles de cuadros de diálogo](../windows/arrangement-of-controls-on-dialog-boxes.md)   
 [Cómo: crear un recurso](../windows/how-to-create-a-resource.md)   
 [Archivos de recursos](../windows/resource-files-visual-studio.md)   
 [Editor de cuadros de diálogo](../windows/dialog-editor.md)

