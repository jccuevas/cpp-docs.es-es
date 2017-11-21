---
title: "Controles de edición de las operaciones del Portapapeles en enriquecido | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- pasting Clipboard data
- CRichEditCtrl class [MFC], paste operation
- cut operation in CRichEditCtrl class [MFC]
- CRichEditCtrl class [MFC], Clipboard operations
- copy operations in rich edit controls
- Clipboard, operations in CRichEditCtrl
- rich edit controls [MFC], Clipboard operations
ms.assetid: 15ce66bc-2636-4a35-a2ae-d52285dc1af6
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d36daeea830517527ccc4e9db35439dcbe2feed1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="clipboard-operations-in-rich-edit-controls"></a>Operaciones de portapapeles en los controles Rich Edit
La aplicación puede pegar el contenido del Portapapeles en un control rich edit ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) con el mejor formato disponible del Portapapeles o un formato de Portapapeles específico. También puede determinar si un control rich edit es capaz de pegar un formato de Portapapeles.  
  
 Puede copiar o cortar el contenido de la selección actual mediante el uso de la [copia](../mfc/reference/cricheditctrl-class.md#copy) o [cortar](../mfc/reference/cricheditctrl-class.md#cut) función miembro. De forma similar, puede pegar el contenido del Portapapeles en un control rich edit utilizando la [pegar](../mfc/reference/cricheditctrl-class.md#paste) función miembro. El control pega el primer formato disponible que reconoce, que es probablemente el formato más descriptivo.  
  
 Para pegar un formato de Portapapeles específico, puede usar el [PasteSpecial](../mfc/reference/cricheditctrl-class.md#pastespecial) función miembro. Esta función es útil para las aplicaciones con un comando Pegado especial que permite al usuario seleccionar el formato del Portapapeles. Puede usar el [CanPaste](../mfc/reference/cricheditctrl-class.md#canpaste) función de miembro para determinar si se reconoce un formato especificado por el control.  
  
 También puede utilizar `CanPaste` para determinar si un control rich edit reconoce cualquier formato disponible del Portapapeles. Esta función es útil en el `OnInitMenuPopup` controlador. Una aplicación puede habilitar o atenuar su comando Pegar dependiendo de si el control puede pegar cualquier formato disponible.  
  
 Controles Rich Edit. register dos formatos de Portapapeles: formato de texto enriquecido y un formato denominado objetos y texto RichEdit. Una aplicación puede registrar estos formatos mediante la [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) funcione, especificando el **valores CF_RTF** y **CF_RETEXTOBJ** valores.  
  
## <a name="see-also"></a>Vea también  
 [Usar CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [Controles](../mfc/controls-mfc.md)

