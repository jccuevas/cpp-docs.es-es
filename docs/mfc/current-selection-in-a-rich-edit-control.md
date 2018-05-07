---
title: Selección actual en un Control Rich Edit | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- current selection in CRichEditCtrls
- CRichEditCtrl class [MFC], current selection in
- rich edit controls [MFC], current selection in
- selection, current in CRichEditCtrl
ms.assetid: f6b2a2b6-5481-4ad3-9720-6dd772ea6fc8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 782984bc53bc16f8dc89e4e705811fef24b8931e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="current-selection-in-a-rich-edit-control"></a>Selección actual en un control Rich Edit
El usuario puede seleccionar texto en un control rich edit ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) mediante el mouse o el teclado. La selección actual es el intervalo de caracteres seleccionados o la posición del punto de inserción si no hay caracteres seleccionados. Una aplicación puede obtener información acerca de la selección actual, establecer la selección actual, determinar cuándo resaltar los cambios de selección actual y mostrar u ocultar la selección.  
  
 Para determinar la selección actual en un control rich edit, utilice la [función miembro GetSel](../mfc/reference/cricheditctrl-class.md#getsel) función miembro. Para establecer la selección actual, utilice la [función miembro SetSel](../mfc/reference/cricheditctrl-class.md#setsel) función miembro. El [CHARRANGE](http://msdn.microsoft.com/library/windows/desktop/bb787885) estructura se utiliza con estas funciones para especificar un intervalo de caracteres. Para recuperar información sobre el contenido de la selección actual, puede usar el [función miembro GetSelectionType](../mfc/reference/cricheditctrl-class.md#getselectiontype) función miembro.  
  
 De forma predeterminada, un control rich edit muestra y oculta el resalte de la selección cuando recibe y pierde el foco. Puede mostrar u ocultar el resalte de la selección en cualquier momento mediante el [HideSelection](../mfc/reference/cricheditctrl-class.md#hideselection) función miembro. Por ejemplo, una aplicación podría proporcionar un cuadro de diálogo de búsqueda para buscar texto en un control rich edit. La aplicación podría seleccionar el texto coincidente sin cerrar el cuadro de diálogo, en cuyo caso debe usar `HideSelection` para resaltar la selección.  
  
 Para obtener el texto seleccionado en un control rich edit, utilice la [función miembro GetSelText](../mfc/reference/cricheditctrl-class.md#getseltext) función miembro. El texto se copia en la matriz de caracteres especificada. Debe asegurarse de que la matriz es lo suficientemente grande como para contener el texto seleccionado junto con un carácter nulo de terminación.  
  
 Puede buscar una cadena en un control rich edit utilizando la [FindText](../mfc/reference/cricheditctrl-class.md#findtext) función miembro la [FINDTEXTEX](http://msdn.microsoft.com/library/windows/desktop/bb787909) estructura que se utiliza con esta función especifica el intervalo de texto en la búsqueda y la cadena de búsqueda. También puede especificar opciones tales como la búsqueda no distingue entre mayúsculas y minúsculas.  
  
## <a name="see-also"></a>Vea también  
 [Usar CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [Controles](../mfc/controls-mfc.md)

