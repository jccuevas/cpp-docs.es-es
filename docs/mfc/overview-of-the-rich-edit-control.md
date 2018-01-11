---
title: "Información general sobre el Control Rich Edit | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: rich edit controls [MFC]
ms.assetid: ad589b9f-a3fd-4820-bf1f-6b1965997e68
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: bffab7b72e99dc6587f1d2cbff84407949dd374b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="overview-of-the-rich-edit-control"></a>Información general del control Rich Edit
> [!IMPORTANT]
>  Si está utilizando un control rich edit en un cuadro de diálogo (independientemente de si la aplicación es SDI, MDI o basada en cuadros de diálogo), debe llamar a [AfxInitRichEdit](../mfc/reference/application-information-and-management.md#afxinitrichedit) una vez antes el cuadro de diálogo se muestra el cuadro. Un lugar típico para llamar a esta función está en el programa `InitInstance` función miembro. No es necesario para que se llame para cada hora de que mostrar el cuadro de diálogo, sólo la primera vez. No es necesario llamar a `AfxInitRichEdit` si está trabajando con `CRichEditView`.  
  
 Controles Rich edit ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) proporcionan una interfaz de programación para dar formato al texto. Sin embargo, una aplicación debe implementar los componentes de interfaz de usuario necesarios para realizar operaciones de formato disponibles para el usuario. Es decir, el control rich edit admite cambiar los atributos de carácter o de párrafo del texto seleccionado. Algunos ejemplos de atributos son de carácter negrita, cursiva, familia de fuentes y tamaño de punto. Ejemplos de atributos de párrafo incluyen la alineación, márgenes y tabulaciones. Sin embargo, resulta depende de usted para proporcionar la interfaz de usuario, ya sea botones de barra de herramientas, elementos de menú o un cuadro de diálogo de caracteres de formato. También existen funciones para consultar el control de edición enriquecida para los atributos de la selección actual. Use estas funciones para mostrar la configuración actual para los atributos, por ejemplo, establecer una marca de verificación en la interfaz de usuario de comandos si la selección tiene el atributo de formato de caracteres negrita.  
  
 Para obtener más información sobre el formato de carácter y párrafo, consulte [formato de carácter](../mfc/character-formatting-in-rich-edit-controls.md) y [el formato de párrafo](../mfc/paragraph-formatting-in-rich-edit-controls.md) más adelante en este tema.  
  
 Controles Rich edit admiten casi todas las operaciones y mensajes de notificación utilizados con controles de edición multilínea. Por lo tanto, las aplicaciones que ya utilizan controles de edición pueden puede modificarse fácilmente para usar a datos completos de controles de edición. Las notificaciones y mensajes adicionales permiten que las aplicaciones tener acceso a los controles de edición único Rich de funcionalidad. Para obtener información acerca de los controles de edición, vea [CEdit](../mfc/reference/cedit-class.md).  
  
 Para obtener más información acerca de las notificaciones, consulte [notificaciones desde un Control Rich Edit](../mfc/notifications-from-a-rich-edit-control.md) más adelante en este tema.  
  
## <a name="see-also"></a>Vea también  
 [Usar CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [Controles](../mfc/controls-mfc.md)

