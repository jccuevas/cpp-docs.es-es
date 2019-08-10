---
title: Controles Rich Edit sin límite
ms.date: 11/04/2016
helpviewer_keywords:
- bottomless rich edit controls
- rich edit controls [MFC], bottomless
- CRichEditCtrl class [MFC], bottomless
ms.assetid: 2877dd32-1e9a-4fd1-98c0-66dcbbeef1de
ms.openlocfilehash: d5650d34ffc350444061aa6147c38af016458811
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68915266"
---
# <a name="bottomless-rich-edit-controls"></a>Controles Rich Edit sin límite

La aplicación puede cambiar el tamaño de un control Rich Edit ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) según sea necesario para que tenga siempre el mismo tamaño que su contenido. Un control Rich Edit admite esta característica, denominada "sin límite", enviando a su ventana primaria un mensaje de notificación [EN_REQUESTRESIZE](/windows/desktop/Controls/en-requestresize) cada vez que cambia el tamaño de su contenido.

Al procesar el mensaje de notificación **EN_REQUESTRESIZE** , una aplicación debe cambiar el tamaño del control a las dimensiones de la estructura [REQRESIZE](/windows/desktop/api/richedit/ns-richedit-reqresize) especificada. Una aplicación también puede trasladar cualquier información cerca del control para acomodar el cambio de alto del control. Para cambiar el tamaño del control, puede usar la `CWnd` función [SetWindowPos](../mfc/reference/cwnd-class.md#setwindowpos).

Puede forzar que un control Rich Edit ilimitado envíe un mensaje de notificación **EN_REQUESTRESIZE** mediante la función miembro [REQUESTRESIZE](../mfc/reference/cricheditctrl-class.md#requestresize) . Este mensaje puede ser útil en el controlador de [tamaño](../mfc/reference/cwnd-class.md#onsize) .

Para recibir mensajes de notificación de **EN_REQUESTRESIZE** , debe habilitar la notificación mediante la `SetEventMask` función miembro.

## <a name="see-also"></a>Vea también

[Uso de CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
