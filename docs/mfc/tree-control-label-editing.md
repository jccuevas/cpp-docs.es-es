---
title: "Edici&#243;n de etiquetas de control de &#225;rbol | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CTreeCtrl (clase), editar etiquetas"
  - "editar etiquetas de control de árbol"
  - "edición de etiquetas en la clase CTreeCtrl"
  - "controles de árbol, edición de etiquetas"
ms.assetid: 6cde2ac3-43ee-468f-bac2-cf1a228ad32d
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Edici&#243;n de etiquetas de control de &#225;rbol
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El usuario puede modificar directamente las etiquetas de elementos en un control de árbol \([CTreeCtrl](../mfc/reference/ctreectrl-class.md)\) con el estilo de **TVS\_EDITLABELS** .  El usuario inicia edición haciendo clic en la etiqueta del elemento que tiene el foco.  Se inicia una aplicación edición utilizando la función miembro de [EditLabel](../Topic/CTreeCtrl::EditLabel.md) .  El control de árbol envía la notificación al editar comienza y cuando se cancela o completado.  Cuando se completa la edición, es responsable de actualizar la etiqueta de elemento, si es adecuado.  
  
 Cuando la edición de la etiqueta, un control de árbol envía un mensaje de notificación de [TVN\_BEGINLABELEDIT](http://msdn.microsoft.com/library/windows/desktop/bb773506) .  Procesando esta notificación, puede permitir la edición de algunas etiquetas y evitar la edición de otras.  Devolver 0 permite la edición, y el cambio se lo impide.  
  
 Cuando la edición de la etiqueta se cancela o completada, un control de árbol envía un mensaje de notificación de [TVN\_ENDLABELEDIT](http://msdn.microsoft.com/library/windows/desktop/bb773515) .  El parámetro de `lParam` es la dirección de una estructura de [NMTVDISPINFO](http://msdn.microsoft.com/library/windows/desktop/bb773418) .  El miembro de **item** es una estructura de [TVITEM](http://msdn.microsoft.com/library/windows/desktop/bb773456) que identifica el elemento e incluye el texto editado.  Es responsable de actualizar la etiqueta de elemento, si es necesario, quizás después de validar la cadena editada.  El miembro de **pszText** de `TV_ITEM` es 0 si la edición se cancela.  
  
 Durante la modificación de la etiqueta, normalmente en respuesta al mensaje de notificación de [TVN\_BEGINLABELEDIT](http://msdn.microsoft.com/library/windows/desktop/bb773506) , puede obtener un puntero al control de edición utilizado para la edición de la etiqueta utilizando la función miembro de [GetEditControl](../Topic/CTreeCtrl::GetEditControl.md) .  Puede llamar a la función miembro de [SetLimitText](../Topic/CEdit::SetLimitText.md) del control de edición para limitar la cantidad de texto que un usuario puede escribir o subclases con el control de edición para interceptar y para descartar caracteres no válidos.  Observe, sin embargo, que el control de edición se muestra únicamente después de que se envía**TVN\_BEGINLABELEDIT** .  
  
## Vea también  
 [Usar CTreeCtrl](../mfc/using-ctreectrl.md)   
 [Controles](../mfc/controls-mfc.md)