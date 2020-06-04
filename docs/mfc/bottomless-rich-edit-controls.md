---
title: Controles Rich Edit sin límite
ms.date: 11/04/2016
helpviewer_keywords:
- bottomless rich edit controls
- rich edit controls [MFC], bottomless
- CRichEditCtrl class [MFC], bottomless
ms.assetid: 2877dd32-1e9a-4fd1-98c0-66dcbbeef1de
ms.openlocfilehash: 4affdbeed723ea83beda785116dc4c45771073b2
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69509148"
---
# <a name="bottomless-rich-edit-controls"></a>Controles Rich Edit sin límite

La aplicación puede cambiar el tamaño de un control Rich Edit ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) según sea necesario para que tenga siempre el mismo tamaño que su contenido. Un control Rich Edit admite esta característica, denominada "sin límite", enviando a su ventana primaria un mensaje de notificación [EN_REQUESTRESIZE](/windows/win32/Controls/en-requestresize) cada vez que cambia el tamaño de su contenido.

Al procesar el mensaje de notificación **EN_REQUESTRESIZE** , una aplicación debe cambiar el tamaño del control a las dimensiones de la estructura [REQRESIZE](/windows/win32/api/richedit/ns-richedit-reqresize) especificada. Una aplicación también puede trasladar cualquier información cerca del control para acomodar el cambio de alto del control. Para cambiar el tamaño del control, puede usar la `CWnd` función [SetWindowPos](../mfc/reference/cwnd-class.md#setwindowpos).

Puede forzar que un control Rich Edit ilimitado envíe un mensaje de notificación **EN_REQUESTRESIZE** mediante la función miembro [REQUESTRESIZE](../mfc/reference/cricheditctrl-class.md#requestresize) . Este mensaje puede ser útil en el controlador de [tamaño](../mfc/reference/cwnd-class.md#onsize) .

Para recibir mensajes de notificación de **EN_REQUESTRESIZE** , debe habilitar la notificación mediante la `SetEventMask` función miembro.

## <a name="see-also"></a>Vea también

[Uso de CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
