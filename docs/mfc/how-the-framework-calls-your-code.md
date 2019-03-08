---
title: Cómo el marco llama al código
ms.date: 11/04/2016
helpviewer_keywords:
- control flow [MFC], MFC framework and your code
- events [MFC], command routing in MFC
- command routing [MFC], framework
- command handling [MFC], calling handlers and code in MFC
- events [MFC], event-driven programming
- MFC, calling code from
- MFC, calling code
- application-specific events [MFC]
- command routing [MFC], MFC
ms.assetid: 39e68189-a580-40d0-9e35-bf5cd24a8ecf
ms.openlocfilehash: 81b0749167391a841badff5494023a2ca5d3147e
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57279710"
---
# <a name="how-the-framework-calls-your-code"></a>Cómo el marco llama al código

Es fundamental comprender la relación entre el código fuente y el código en el marco de trabajo MFC. Cuando se ejecuta la aplicación, la mayor parte del flujo de control se encuentra en el código de .NET framework. El marco de trabajo administra el bucle de mensajes que recibe mensajes de Windows cuando el usuario elige los comandos y edita datos en una vista. Eventos que el marco de trabajo puede controlar por sí solo no confían en el código en absoluto. Por ejemplo, el marco de trabajo sabe cómo cerrar ventanas y cómo salir de la aplicación en respuesta a los comandos de usuario. A medida que controla estas tareas, el marco de trabajo utiliza controladores de mensajes y funciones virtuales de C++ para ofrecer oportunidades para responder a estos eventos también. El código es no en el control, sin embargo; es el marco de trabajo.

El marco de trabajo llama al código para los eventos específicos de la aplicación. Por ejemplo, cuando el usuario elige un comando de menú, el marco de trabajo enruta el comando a lo largo de una secuencia de objetos de C++: la ventana de vista y el marco actual, el documento asociado a la vista de plantilla de documento del documento y el objeto de aplicación. Si uno de estos objetos puede controlar el comando, lo hace, llamar a la función de controlador de mensajes adecuado. Para un determinado comando, el código que llama puede ser suyo o es posible que el marco de trabajo.

Esta disposición es familiar para los programadores con experiencia en la programación tradicional de Windows o la programación orientada a eventos.

En otros temas relacionados, leerá lo que el marco de trabajo tal como se inicializa y ejecuta la aplicación y, a continuación, limpia como la aplicación finaliza. También comprenderá dónde encaja el código que escriba.

Para obtener más información, consulte [clase CWinApp: La clase Application](../mfc/cwinapp-the-application-class.md) y [plantillas de documento y el proceso de creación de documento/vista](../mfc/document-templates-and-the-document-view-creation-process.md).

## <a name="see-also"></a>Vea también

[Compilación en el marco](../mfc/building-on-the-framework.md)
