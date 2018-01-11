---
title: Formato de caracteres en los controles Rich Edit | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- formatting [MFC], characters
- rich edit controls [MFC], character formatting in
- CRichEditCtrl class [MFC], character formatting in
ms.assetid: c80f4305-75ad-45f9-8d17-d83d0fe79be5
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 93bb2cda113a56276ad54edb5ccdb6c9d430ed06
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="character-formatting-in-rich-edit-controls"></a>Formato de los caracteres en los controles Rich Edit
Puede utilizar las funciones miembro de control rich edit ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) para dar formato de caracteres y recuperar información de formato. Para los caracteres, puede especificar el tipo de letra, tamaño, color y efectos como negrita, cursiva y protegido.  
  
 Puede aplicar formato de caracteres mediante el uso de la [SetSelectionCharFormat](../mfc/reference/cricheditctrl-class.md#setselectioncharformat) y [SetWordCharFormat](../mfc/reference/cricheditctrl-class.md#setwordcharformat) funciones miembro. Para determinar el formato para el texto seleccionado de caracteres actual, use la [GetSelectionCharFormat](../mfc/reference/cricheditctrl-class.md#getselectioncharformat) función miembro. El [CHARFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb787881) estructura se utiliza con estas funciones miembro para especificar atributos de carácter. Uno de los miembros importantes de **CHARFORMAT** es **dwMask**. En `SetSelectionCharFormat` y `SetWordCharFormat`, **dwMask** especifica qué atributos de carácter se establecerá mediante esta llamada a función. `GetSelectionCharFormat`informa de los atributos del primer carácter de la selección; **dwMask** especifica los atributos que son coherentes en toda la selección.  
  
 Se puede obtener y establecer el "formato de caracteres predeterminado," ¿Cuál es el formato aplicado a cualquier carácter insertado posteriormente. Por ejemplo, si una aplicación establece el carácter predeterminado de formato para poner en negrita y el usuario, a continuación, escribe un carácter, ese carácter está en negrita. Para obtener y establecer el formato de caracteres predeterminado, utilice la [funciones GetDefaultCharFormat](../mfc/reference/cricheditctrl-class.md#getdefaultcharformat) y [SetDefaultCharFormat](../mfc/reference/cricheditctrl-class.md#setdefaultcharformat) funciones miembro.  
  
 El atributo de carácter "protegido" no cambia la apariencia del texto. Si el usuario intenta modificar texto protegido, un control rich edit envía su ventana primaria un **EN_PROTECTED** mensaje de notificación, lo que permite la ventana primaria permitir o impedir el cambio. Para recibir este mensaje de notificación, debe habilitarlo utilizando el [SetEventMask](../mfc/reference/cricheditctrl-class.md#seteventmask) función miembro. Para obtener más información acerca de la máscara de eventos, vea [notificaciones desde un Control Rich Edit](../mfc/notifications-from-a-rich-edit-control.md), más adelante en este tema.  
  
 Color de primer plano es un atributo de carácter, pero el color de fondo es una propiedad del control rich edit. Para establecer el color de fondo, utilice la [función miembro SetBackgroundColor](../mfc/reference/cricheditctrl-class.md#setbackgroundcolor) función miembro.  
  
## <a name="see-also"></a>Vea también  
 [Usar CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [Controles](../mfc/controls-mfc.md)

