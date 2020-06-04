---
title: Controladores de mensajes
ms.date: 11/04/2016
helpviewer_keywords:
- message handlers [MFC]
- command handling [MFC], message handlers
- handlers [MFC]
- message handling [MFC], message handler functions
- handlers [MFC], command
- handlers [MFC], message
ms.assetid: 51bc4e76-dbe3-4cc2-b026-3199d56b2fa9
ms.openlocfilehash: 25805187f88c5423ea41cd7cbe346e44e7d7d36a
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907461"
---
# <a name="message-handlers"></a>Controladores de mensajes

En MFC, una función de *controlador* dedicada procesa cada mensaje independiente. Las funciones de controlador de mensajes son funciones miembro de una clase. En esta documentación se usa la *función miembro de controlador de mensajes*, la *función de controlador de mensajes*, el controlador de *mensajes*y el *controlador* indistintamente. Algunos tipos de controladores de mensajes también se denominan "controladores de comandos".

La escritura de controladores de mensajes cuenta con una gran proporción de su trabajo en la escritura de una aplicación de marco. En esta familia de artículos se describe cómo funciona el mecanismo de procesamiento de mensajes.

Lo que hace el controlador de un mensaje hace todo lo que desea hacer en respuesta a ese mensaje. Puede crear los controladores mediante el [Asistente para clases](reference/mfc-class-wizard.md) de la clase y, a continuación, rellenar el código del controlador mediante el editor de código fuente.

Puede usar todas las funciones de Microsoft Visual C++ y MFC para escribir los controladores. Para obtener una lista de todas las clases, vea [información general sobre la biblioteca de clases](../mfc/class-library-overview.md) en la *referencia de MFC*.

## <a name="see-also"></a>Vea también

[Mensajes y comandos en el marco](../mfc/messages-and-commands-in-the-framework.md)
