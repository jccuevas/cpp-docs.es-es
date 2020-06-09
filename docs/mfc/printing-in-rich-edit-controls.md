---
title: Imprimir controles Rich Edit
ms.date: 11/04/2016
helpviewer_keywords:
- printing [MFC], CRichEditCtrl
- rich edit controls [MFC], printing
- CRichEditCtrl class [MFC], printing
ms.assetid: dbda0e40-018f-424e-b5d8-7b489aaf27af
ms.openlocfilehash: f275078fbef9026363305bb714da3a2af333c91f
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619818"
---
# <a name="printing-in-rich-edit-controls"></a>Imprimir controles Rich Edit

Puede indicar a un control Rich Edit ([CRichEditCtrl](reference/cricheditctrl-class.md)) que represente su salida para un dispositivo especificado, como una impresora. También puede especificar el dispositivo de salida para el que un control Rich Edit da formato a su texto.

Para dar formato a parte del contenido de un control Rich Edit para un dispositivo específico, puede usar la función miembro [FormatRange](reference/cricheditctrl-class.md#formatrange) . La estructura [FORMATRANGE](/windows/win32/api/richedit/ns-richedit-formatrange) usada con esta función especifica el intervalo de texto al que se va a dar formato, así como el contexto de dispositivo (DC) del dispositivo de destino.

Después de dar formato al texto de un dispositivo de salida, puede enviar el resultado al dispositivo mediante la función miembro [DisplayBand](reference/cricheditctrl-class.md#displayband) . Mediante el uso de `FormatRange` y `DisplayBand` , una aplicación que imprime el contenido de un control Rich Edit puede implementar bandas. (El uso de bandas es la división de la salida en partes más pequeñas para fines de impresión).

Puede usar la función miembro [SetTargetDevice](reference/cricheditctrl-class.md#settargetdevice) para especificar el dispositivo de destino para el que un control Rich Edit da formato a su texto. Esta función es útil para el formato WYSIWYG (lo que se ve es lo que se obtiene), en el que una aplicación coloca el texto con las métricas de fuente de la impresora predeterminada en lugar de la de la pantalla.

## <a name="see-also"></a>Consulte también

[Uso de CRichEditCtrl](using-cricheditctrl.md)<br/>
[Permite](controls-mfc.md)
