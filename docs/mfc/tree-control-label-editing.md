---
title: Etiquetas de Control de árbol edición | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- editing tree control labels
- CTreeCtrl class [MFC], editing labels
- label editing in CTreeCtrl class [MFC]
- tree controls [MFC], label editing
ms.assetid: 6cde2ac3-43ee-468f-bac2-cf1a228ad32d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fd2157755146606b2bdacf8ae5a1da9cd0966b21
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="tree-control-label-editing"></a>Edición de etiquetas de control de árbol
El usuario puede editar directamente las etiquetas de elementos en un control de árbol ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) que tiene el **TVS_EDITLABELS** estilo. El usuario comienza a editar haciendo clic en la etiqueta del elemento que tiene el foco. Una aplicación comienza la edición usando el [función miembro EditLabel](../mfc/reference/ctreectrl-class.md#editlabel) función miembro. El control de árbol envía la notificación al editar comienza y cuando se cancela o completado. Cuando se completa la edición, es responsable de actualizar la etiqueta del elemento, si procede.  
  
 Cuando etiqueta comienza la edición, un control de árbol envía un [TVN_BEGINLABELEDIT](http://msdn.microsoft.com/library/windows/desktop/bb773506) mensaje de notificación. Mediante el procesamiento de esta notificación, puede permitir la edición de algunas etiquetas y evitar las modificaciones de los demás. Devolver 0 permite la edición y devolver un valor distinto de cero le impidiera.  
  
 Cuando la edición de la etiqueta se cancela o completado, un control de árbol envía un [TVN_ENDLABELEDIT](http://msdn.microsoft.com/library/windows/desktop/bb773515) mensaje de notificación. El `lParam` parámetro es la dirección de un [estructura NMTVDISPINFO](http://msdn.microsoft.com/library/windows/desktop/bb773418) estructura. El **elemento** miembro es una [estructura TVITEM](http://msdn.microsoft.com/library/windows/desktop/bb773456) estructura que identifica el elemento e incluye el texto editado. Usted es responsable de actualizar la etiqueta del elemento, si procede, tal vez después de validar la cadena editada. El **pszText** miembro de `TV_ITEM` es 0 si se cancela la edición.  
  
 Durante la edición de etiquetas, normalmente en respuesta a la [TVN_BEGINLABELEDIT](http://msdn.microsoft.com/library/windows/desktop/bb773506) mensaje de notificación, puede obtener un puntero para el control de edición que se utiliza para la edición de etiquetas mediante el uso de la [función miembro GetEditControl](../mfc/reference/ctreectrl-class.md#geteditcontrol) miembro función. Puede llamar el control de edición [SetLimitText](../mfc/reference/cedit-class.md#setlimittext) función de miembro para limitar la cantidad de texto que un usuario puede escribir o subclase el control de edición para interceptar y descartar caracteres no válidos. Sin embargo, tenga en cuenta que el control de edición se muestra solo *después* **TVN_BEGINLABELEDIT** se envía.  
  
## <a name="see-also"></a>Vea también  
 [Usar CTreeCtrl](../mfc/using-ctreectrl.md)   
 [Controles](../mfc/controls-mfc.md)

