---
title: 'Cómo: Usar la referencia cruzada del mapa de mensajes'
ms.date: 11/04/2016
f1_keywords:
- vc.mfc.messages
helpviewer_keywords:
- windows [MFC], message maps
ms.assetid: 2e863d23-9e58-45ba-b5e4-a8ceefccd0c8
ms.openlocfilehash: 71c46e7c30eab414534012c2fe314999568d2bd8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50457803"
---
# <a name="how-to-use-the-message-map-cross-reference"></a>Cómo: Usar la referencia cruzada del mapa de mensajes

En las entradas con la etiqueta \<memberFxn >, escribir su propia función de miembro para un derivado [CWnd](../../mfc/reference/cwnd-class.md) clase. Asigne a la función de cualquier nombre que desee. Las demás funciones, como `OnActivate`, son funciones miembro de clase `CWnd`. Si se llama, pasan el mensaje a la `DefWindowProc` función de Windows. Para procesar mensajes de notificación de Windows, reemplace el correspondiente `CWnd` función en la clase derivada. La función debe llamar a la función invalidada en su clase base para permitir que la clase base y Windows responden al mensaje.

En todos los casos, coloque el prototipo de función en el `CWnd`: encabezado de la clase derivada y la entrada de asignación de mensaje, como se muestra de código.

Se utilizan los términos siguientes:

|Término|de esquema JSON|
|----------|----------------|
|id|Cualquier Id. de elemento de menú definido por el usuario (mensajes WM_COMMAND) o el Id. de control (mensajes de notificación de ventana secundaria).|
|"mensaje" y "wNotifyCode"|Identificadores de mensajes de Windows tal como se define en WINDOWS. H.|
|nMessageVariable|Nombre de una variable que contiene el valor devuelto por la `RegisterWindowMessage` función de Windows.|

## <a name="see-also"></a>Vea también

[Mapas de mensajes](../../mfc/reference/message-maps-mfc.md)

