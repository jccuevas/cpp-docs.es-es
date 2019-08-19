---
title: Operaciones de secuencia en los controles Rich Edit
ms.date: 11/04/2016
helpviewer_keywords:
- CRichEditCtrl class [MFC], stream operations
- CRichEditCtrl class [MFC], stream storage
- rich edit controls [MFC], stream operations
- storage, stream in CRichEditCtrl
- stream operations in CRichEditCtrl
- stream storage and CRichEditCtrl
ms.assetid: 110b4684-1e76-4ca6-9ef0-5bc8b2d93c78
ms.openlocfilehash: 73277f59dc0ad4dfe21d481d0b893903ed407ea9
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69512941"
---
# <a name="stream-operations-in-rich-edit-controls"></a>Operaciones de secuencia en los controles Rich Edit

Puede usar secuencias para transferir datos dentro o fuera de un control Rich Edit ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)). Una secuencia se define mediante una estructura [EDITSTREAM](/windows/win32/api/richedit/ns-richedit-editstream) , que especifica un búfer y una función de devolución de llamada definida por la aplicación.

Para leer los datos en un control Rich Edit (es decir, hacer streaming de los datos en), use la función miembro [StreamIn](../mfc/reference/cricheditctrl-class.md#streamin). El control llama repetidamente a la función de devolución de llamada definida por la aplicación, que transfiere una parte de los datos en el búfer cada vez.

Para guardar el contenido de un control Rich Edit (es decir, hacer streaming de los datos), puede usar la función miembro [StreamOut](../mfc/reference/cricheditctrl-class.md#streamout) . El control escribe repetidamente en el búfer y, a continuación, llama a la función de devolución de llamada definida por la aplicación. Para cada llamada, la función de devolución de llamada guarda el contenido del búfer.

## <a name="see-also"></a>Vea también

[Uso de CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
