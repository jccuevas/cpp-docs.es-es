---
title: Agregar un controlador de mensajes ATL
ms.date: 11/04/2016
helpviewer_keywords:
- message handlers [C++]
- ATL, windows
- message handling [C++], ATL message handler
- windows [C++], ATL
- ATL, message handlers
ms.assetid: cdea38a1-0d9b-4f8d-bbd5-b4f063fb3eeb
ms.openlocfilehash: 6d812c70e7cec4739ee9477d30ad9744b4fddc50
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50565507"
---
# <a name="adding-an-atl-message-handler"></a>Agregar un controlador de mensajes ATL

Para agregar un controlador de mensajes (una función miembro que controla los mensajes de Windows) a un control, seleccione primero el control en la vista de clases. A continuación, abra el **propiedades** ventana, seleccione el **mensajes** icono y haga clic en la lista desplegable de control en el cuadro opuesto al mensaje requerido. Esto agregará una declaración para el controlador de mensajes en el archivo de encabezado del control y una implementación esqueleto del controlador en el archivo .cpp del control. También agregará el mapa de mensajes y agregue una entrada para el controlador.

Agregar un controlador de mensajes en ATL es similar a agregar un controlador de mensajes a una clase de MFC. Consulte [agregar un controlador de mensajes MFC](../mfc/reference/adding-an-mfc-message-handler.md) para obtener más información.

Las condiciones siguientes se aplican solo a agregar un controlador de mensajes ATL:

- Los controladores de mensajes siguen la misma convención de nomenclatura como MFC.

- Se agregan las nuevas entradas de mapa de mensajes en el mapa de mensajes principal. No reconoce el Asistente para mapas de mensajes alternativos y encadenamiento.

## <a name="see-also"></a>Vea también

[Implementar una ventana](../atl/implementing-a-window.md)

