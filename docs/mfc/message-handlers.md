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
ms.openlocfilehash: 1d775fc98fc97236cd63caf1e4422d32a9245410
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50588661"
---
# <a name="message-handlers"></a>Controladores de mensajes

En MFC, dedicada *controlador* función procesa cada mensaje independiente. Las funciones de controlador de mensajes son funciones miembro de una clase. Esta documentación utiliza los términos *función miembro de controlador de mensajes*, *función de controlador de mensajes*, *controlador de mensajes*, y *controlador*indistintamente. Algunos tipos de controladores de mensajes también se denominan "controladores de comandos".

Escribir controladores de mensajes supone una gran parte de su trabajo en la escritura de una aplicación de framework. Esta serie de artículos describe cómo funciona el mecanismo de procesamiento de mensajes.

Lo que hace el controlador para un mensaje hacerlo lo que desea hacer en respuesta a ese mensaje. Puede crear los controladores mediante el uso de la ventana Propiedades de la clase y, a continuación, rellene el código del controlador mediante el editor de código fuente.

Puede usar todos los servicios de Microsoft Visual C++ y MFC para escribir los controladores. Para obtener una lista de todas las clases, vea [Class Library Overview](../mfc/class-library-overview.md) en el *referencia de MFC*.

## <a name="see-also"></a>Vea también

[Mensajes y comandos en el marco](../mfc/messages-and-commands-in-the-framework.md)

