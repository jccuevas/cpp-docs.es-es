---
title: Formato de caracteres en los controles Rich Edit | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- formatting [MFC], characters
- rich edit controls [MFC], character formatting in
- CRichEditCtrl class [MFC], character formatting in
ms.assetid: c80f4305-75ad-45f9-8d17-d83d0fe79be5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e7b56570a2821cef3cd2d2676a5260f42bc2ffaf
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43210775"
---
# <a name="character-formatting-in-rich-edit-controls"></a>Formato de los caracteres en los controles Rich Edit
Puede usar las funciones miembro de control rich edit ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) para dar formato de caracteres y recuperar información de formato. Para los caracteres, puede especificar el tipo de letra, tamaño, color y efectos como negrita, cursiva y protegido.  
  
 Puede aplicar formato de caracteres utilizando el [SetSelectionCharFormat](../mfc/reference/cricheditctrl-class.md#setselectioncharformat) y [SetWordCharFormat](../mfc/reference/cricheditctrl-class.md#setwordcharformat) funciones miembro. Para determinar el formato del texto seleccionado de caracteres actual, use el [GetSelectionCharFormat](../mfc/reference/cricheditctrl-class.md#getselectioncharformat) función miembro. El [CHARFORMAT](/windows/desktop/api/richedit/ns-richedit-_charformat) estructura se usa con estas funciones miembro para especificar atributos de carácter. Uno de los miembros importantes de **CHARFORMAT** es **dwMask**. En `SetSelectionCharFormat` y `SetWordCharFormat`, **dwMask** especifica qué atributos de carácter que establecerá esta llamada de función. `GetSelectionCharFormat` informa de los atributos del primer carácter en la selección; **dwMask** especifica los atributos que son coherentes a lo largo de la selección.  
  
 También puede obtener y establecer el "formato de caracteres predeterminado," ¿Cuál es el formato aplicado a cualquier carácter insertado posteriormente. Por ejemplo, si una aplicación establece el carácter predeterminado de formato para poner en negrita y el usuario, a continuación, escribe un carácter, ese carácter está en negrita. Para obtener y establecer el formato de caracteres predeterminado, utilice el [funciones GetDefaultCharFormat](../mfc/reference/cricheditctrl-class.md#getdefaultcharformat) y [SetDefaultCharFormat](../mfc/reference/cricheditctrl-class.md#setdefaultcharformat) funciones miembro.  
  
 El atributo "protegido" carácter no cambia la apariencia del texto. Si el usuario intenta modificar texto protegido, un control rich edit envía su ventana primaria un **EN_PROTECTED** mensaje de notificación, lo que permite la ventana primaria permitir o impedir el cambio. Para recibir este mensaje de notificación, debe habilitarlo utilizando el [SetEventMask](../mfc/reference/cricheditctrl-class.md#seteventmask) función miembro. Para obtener más información acerca de la máscara de eventos, consulte [notificaciones desde un Control Rich Edit](../mfc/notifications-from-a-rich-edit-control.md), más adelante en este tema.  
  
 Color de primer plano es un atributo de carácter, pero el color de fondo es una propiedad del control rich edit. Para establecer el color de fondo, use la [función miembro SetBackgroundColor](../mfc/reference/cricheditctrl-class.md#setbackgroundcolor) función miembro.  
  
## <a name="see-also"></a>Vea también  
 [Usar CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [Controles](../mfc/controls-mfc.md)

