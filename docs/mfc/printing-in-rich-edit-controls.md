---
title: Imprimir controles Rich Edit | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- printing [MFC], CRichEditCtrl
- rich edit controls [MFC], printing
- CRichEditCtrl class [MFC], printing
ms.assetid: dbda0e40-018f-424e-b5d8-7b489aaf27af
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 23b958e6c770260082af069544480102f6d79926
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33347668"
---
# <a name="printing-in-rich-edit-controls"></a>Imprimir controles Rich Edit
Puede indicar un control rich edit ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) para representar la salida para un dispositivo específico, como una impresora. También puede especificar el dispositivo de salida para el que un control rich edit da formato a su texto.  
  
 Para dar formato a parte del contenido de un control rich edit para un dispositivo específico, puede usar el [FormatRange](../mfc/reference/cricheditctrl-class.md#formatrange) función miembro. El [FORMATRANGE](http://msdn.microsoft.com/library/windows/desktop/bb787911) estructura que se utiliza con esta función especifica el intervalo de texto que se va a dar formato, así como el contexto de dispositivo (DC) para el dispositivo de destino.  
  
 Después de dar formato al texto de un dispositivo de salida, puede enviar la salida al dispositivo mediante el [DisplayBand](../mfc/reference/cricheditctrl-class.md#displayband) función miembro. Si utiliza varias veces `FormatRange` y `DisplayBand`, puede implementar una aplicación que imprime el contenido de un control rich edit bandas. (Bandas es división de los resultados en partes más pequeñas para impresión.)  
  
 Puede usar el [función miembro SetTargetDevice](../mfc/reference/cricheditctrl-class.md#settargetdevice) función de miembro para especificar el dispositivo de destino para el que un control rich edit da formato a su texto. Esta función es útil para WYSIWYG (lo que ve es lo que imprime) formato, en el que una aplicación coloca texto utilizando métricas de fuente de la impresora predeterminada en lugar de la pantalla.  
  
## <a name="see-also"></a>Vea también  
 [Usar CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [Controles](../mfc/controls-mfc.md)

