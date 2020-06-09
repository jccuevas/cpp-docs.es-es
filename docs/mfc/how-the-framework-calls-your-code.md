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
ms.openlocfilehash: 318ca9558d705ca483d41867a1fe2ad46c36666f
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622606"
---
# <a name="how-the-framework-calls-your-code"></a>Cómo el marco llama al código

Es fundamental comprender la relación entre el código fuente y el código en el marco de trabajo de MFC. Cuando se ejecuta la aplicación, la mayor parte del flujo de control reside en el código del marco. El marco de trabajo administra el bucle de mensajes que recibe los mensajes de Windows cuando el usuario elige comandos y edita datos en una vista. Los eventos que el marco de trabajo puede controlar por sí mismos no se basan en el código. Por ejemplo, el marco de trabajo sabe cómo cerrar Windows y cómo salir de la aplicación en respuesta a los comandos del usuario. Dado que controla estas tareas, el marco de trabajo usa controladores de mensajes y funciones virtuales de C++ para ofrecer también oportunidades para responder a estos eventos. Sin embargo, el código no está en el control; el marco de trabajo es.

El marco de trabajo llama al código para los eventos específicos de la aplicación. Por ejemplo, cuando el usuario elige un comando de menú, el marco de trabajo enruta el comando a lo largo de una secuencia de objetos de C++: la vista actual y la ventana de marco, el documento asociado a la vista, la plantilla de documento del documento y el objeto de aplicación. Si uno de estos objetos puede controlar el comando, lo hace y llama a la función de controlador de mensajes adecuada. Para cualquier comando dado, el código llamado puede ser suyo o puede ser el del marco.

Esta disposición es un poco familiar para los programadores experimentados con programación tradicional para Windows o programación controlada por eventos.

En temas relacionados, leerá lo que hace el marco de trabajo mientras inicializa y ejecuta la aplicación y, a continuación, se limpia cuando finaliza la aplicación. También sabrá dónde encaja el código que escribe.

Para obtener más información, vea [la clase CWinApp: la clase de aplicación](cwinapp-the-application-class.md) y las [plantillas de documento y el proceso de creación de documentos y vistas](document-templates-and-the-document-view-creation-process.md).

## <a name="see-also"></a>Consulte también

[Compilar en el marco](building-on-the-framework.md)
