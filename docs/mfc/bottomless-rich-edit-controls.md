---
title: Controles Rich Edit sin límite
ms.date: 11/04/2016
helpviewer_keywords:
- bottomless rich edit controls
- rich edit controls [MFC], bottomless
- CRichEditCtrl class [MFC], bottomless
ms.assetid: 2877dd32-1e9a-4fd1-98c0-66dcbbeef1de
ms.openlocfilehash: 567bb5b7f2eb2c203b40b9f1f6add82f5451d672
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616432"
---
# <a name="bottomless-rich-edit-controls"></a>Controles Rich Edit sin límite

La aplicación puede cambiar el tamaño de un control Rich Edit ([CRichEditCtrl](reference/cricheditctrl-class.md)) según sea necesario para que tenga siempre el mismo tamaño que su contenido. Un control Rich Edit es compatible con esta característica denominada "sin límite" mediante el envío de su ventana primaria a un mensaje de notificación de [EN_REQUESTRESIZE](/windows/win32/Controls/en-requestresize) cada vez que cambia el tamaño de su contenido.

Al procesar el mensaje de notificación de **EN_REQUESTRESIZE** , una aplicación debe cambiar el tamaño del control a las dimensiones de la estructura [REQRESIZE](/windows/win32/api/richedit/ns-richedit-reqresize) especificada. Una aplicación también puede trasladar cualquier información cerca del control para acomodar el cambio de alto del control. Para cambiar el tamaño del control, puede usar la `CWnd` función [SetWindowPos](reference/cwnd-class.md#setwindowpos).

Puede forzar que un control Rich Edit ilimitado envíe un mensaje de notificación de **EN_REQUESTRESIZE** mediante la función miembro [REQUESTRESIZE](reference/cricheditctrl-class.md#requestresize) . Este mensaje puede ser útil en el controlador de [tamaño](reference/cwnd-class.md#onsize) .

Para recibir mensajes de notificación de **EN_REQUESTRESIZE** , debe habilitar la notificación mediante la `SetEventMask` función miembro.

## <a name="see-also"></a>Consulte también

[Uso de CRichEditCtrl](using-cricheditctrl.md)<br/>
[Permite](controls-mfc.md)
