---
title: Separaciones de palabras en los controles Rich Edit
ms.date: 11/04/2016
helpviewer_keywords:
- CRichEditCtrl class [MFC], word breaks in
- word breaks
- breaking words in CRichEditCtrl
- rich edit controls [MFC], word breaks in
ms.assetid: 641dcf9e-7b40-4dc0-85f7-575a8c142f73
ms.openlocfilehash: efe4a0a2c06c14d913d43c51d1f0100f27c6a537
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50632601"
---
# <a name="word-breaks-in-rich-edit-controls"></a>Separaciones de palabras en los controles Rich Edit

Un control rich edit ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) llama a una función denominada "word salto procedimiento" para encontrar los separadores de palabras y para determinar dónde se pueden romper líneas. El control utiliza esta información al realizar operaciones de ajuste automático y al procesar las combinaciones de teclas CTRL+FLECHA izquierda y derecha. Una aplicación puede enviar mensajes a un control rich edit para reemplazar el procedimiento de separadores de palabras de forma predeterminada, para recuperar información de la separación de palabra y para determinar en qué línea de un carácter determinado se encuentra.

## <a name="see-also"></a>Vea también

[Uso de CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)

