---
title: Formato de los caracteres en los controles Rich Edit
ms.date: 11/04/2016
helpviewer_keywords:
- formatting [MFC], characters
- rich edit controls [MFC], character formatting in
- CRichEditCtrl class [MFC], character formatting in
ms.assetid: c80f4305-75ad-45f9-8d17-d83d0fe79be5
ms.openlocfilehash: 3ff9be0909a36179802e5f210e728c2bf57b1f02
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/06/2019
ms.locfileid: "70739518"
---
# <a name="character-formatting-in-rich-edit-controls"></a>Formato de los caracteres en los controles Rich Edit

Puede utilizar las funciones miembro del control Rich Edit ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) para dar formato a los caracteres y recuperar la información de formato. En el caso de los caracteres, puede especificar el tipo de letra, el tamaño, el color y los efectos, como Bold, Italic y protected.

Puede aplicar el formato de caracteres mediante las funciones miembro [SetSelectionCharFormat](../mfc/reference/cricheditctrl-class.md#setselectioncharformat) y [SetWordCharFormat](../mfc/reference/cricheditctrl-class.md#setwordcharformat) . Para determinar el formato de caracteres actual del texto seleccionado, utilice la función miembro [GetSelectionCharFormat](../mfc/reference/cricheditctrl-class.md#getselectioncharformat) . La estructura [Charformat](/windows/win32/api/richedit/ns-richedit-charformata) se utiliza con estas funciones miembro para especificar atributos de caracteres. Uno de los miembros importantes de **Charformat** es **dwMask**. En `SetSelectionCharFormat` y`SetWordCharFormat`, **dwMask** especifica qué atributos de caracteres se establecerán mediante esta llamada de función. `GetSelectionCharFormat`notifica los atributos del primer carácter de la selección; **dwMask** especifica los atributos que son coherentes a lo largo de la selección.

También puede obtener y establecer el "formato de caracteres predeterminado", que es el formato que se aplica a los caracteres insertados posteriormente. Por ejemplo, si una aplicación establece el formato de caracteres predeterminado en negrita y el usuario escribe un carácter, ese carácter está en negrita. Para obtener y establecer el formato de caracteres predeterminado, utilice las funciones miembro [GetDefaultCharFormat](../mfc/reference/cricheditctrl-class.md#getdefaultcharformat) y [SetDefaultCharFormat](../mfc/reference/cricheditctrl-class.md#setdefaultcharformat) .

El atributo de carácter "protegido" no cambia la apariencia del texto. Si el usuario intenta modificar texto protegido, un control Rich Edit envía a su ventana primaria un mensaje de notificación **EN_PROTECTED** , lo que permite a la ventana primaria permitir o impedir el cambio. Para recibir este mensaje de notificación, debe habilitarlo mediante la función miembro [SetEventMask](../mfc/reference/cricheditctrl-class.md#seteventmask) . Para obtener más información acerca de la máscara de eventos, vea [notificaciones de un control Rich Edit](../mfc/notifications-from-a-rich-edit-control.md), más adelante en este tema.

El color de primer plano es un atributo de carácter, pero el color de fondo es una propiedad del control Rich Edit. Para establecer el color de fondo, utilice la función miembro [SetBackgroundColor](../mfc/reference/cricheditctrl-class.md#setbackgroundcolor) .

## <a name="see-also"></a>Vea también

[Uso de CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
