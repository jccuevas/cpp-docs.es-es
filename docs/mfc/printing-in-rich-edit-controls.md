---
title: Imprimir controles Rich Edit
ms.date: 11/04/2016
helpviewer_keywords:
- printing [MFC], CRichEditCtrl
- rich edit controls [MFC], printing
- CRichEditCtrl class [MFC], printing
ms.assetid: dbda0e40-018f-424e-b5d8-7b489aaf27af
ms.openlocfilehash: 6ae7212eaa8eed1088a507973c80311f169c7751
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68916264"
---
# <a name="printing-in-rich-edit-controls"></a>Imprimir controles Rich Edit

Puede indicar a un control Rich Edit ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) que represente su salida para un dispositivo especificado, como una impresora. También puede especificar el dispositivo de salida para el que un control Rich Edit da formato a su texto.

Para dar formato a parte del contenido de un control Rich Edit para un dispositivo específico, puede usar la función miembro [FormatRange](../mfc/reference/cricheditctrl-class.md#formatrange) . La estructura [FORMATRANGE](/windows/desktop/api/richedit/ns-richedit-formatrange) usada con esta función especifica el intervalo de texto al que se va a dar formato, así como el contexto de dispositivo (DC) del dispositivo de destino.

Después de dar formato al texto de un dispositivo de salida, puede enviar el resultado al dispositivo mediante la función miembro [DisplayBand](../mfc/reference/cricheditctrl-class.md#displayband) . Mediante el uso `FormatRange` de `DisplayBand`y, una aplicación que imprime el contenido de un control Rich Edit puede implementar bandas. (El uso de bandas es la división de la salida en partes más pequeñas para fines de impresión).

Puede usar la función miembro [SetTargetDevice](../mfc/reference/cricheditctrl-class.md#settargetdevice) para especificar el dispositivo de destino para el que un control Rich Edit da formato a su texto. Esta función es útil para el formato WYSIWYG (lo que se ve es lo que se obtiene), en el que una aplicación coloca el texto con las métricas de fuente de la impresora predeterminada en lugar de la de la pantalla.

## <a name="see-also"></a>Vea también

[Uso de CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
