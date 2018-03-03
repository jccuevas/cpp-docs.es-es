---
title: "Cómo el marco de trabajo llama al código | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 83eeb1c7fd3032ae33c213f17522b171bdb46e55
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="how-the-framework-calls-your-code"></a>Cómo el marco llama al código
Es fundamental entender la relación entre el código fuente y el código en el marco de trabajo MFC. Cuando se ejecuta la aplicación, la mayor parte del flujo de control se encuentra en el código del marco de trabajo. El marco de trabajo administra el bucle de mensajes que recibe mensajes de Windows como el usuario selecciona comandos y edita datos en una vista. Eventos que el marco de trabajo puede controlar por sí solo no confían en el código en absoluto. Por ejemplo, el marco de trabajo sabe cómo cerrar ventanas y cómo salir de la aplicación en respuesta a los comandos de usuario. A medida que controla estas tareas, el marco de trabajo usa controladores de mensajes y funciones virtuales de C++ para darle oportunidades para responder a estos eventos también. El código es no en el control, sin embargo; es el marco de trabajo.  
  
 El marco de trabajo llama al código para los eventos específicos de la aplicación. Por ejemplo, cuando el usuario elige un comando de menú, el marco de trabajo enruta el comando a lo largo de una secuencia de objetos de C++: la ventana de vista y el marco actual, el documento asociado a la vista, plantilla de documento del documento y el objeto de aplicación. Si uno de estos objetos puede controlar el comando, lo hace, al llamar a la función de controlador de mensajes adecuado. Para un determinado comando, el código que llama puede ser suyo o puede ser el marco de trabajo.  
  
 Esta disposición es un poco familiar para los programadores que tienen experimentados con la programación tradicional para Windows o programación orientada a eventos.  
  
 En otros temas relacionados, leerá lo que el marco de trabajo tal como se inicializa y ejecuta la aplicación y, a continuación, se limpia cuando finaliza la aplicación. También sabrá dónde encaja el código que escribe.  
  
 Para obtener más información, consulte [clase CWinApp: la clase de aplicación](../mfc/cwinapp-the-application-class.md) y [plantillas de documento y el proceso de creación de documento/vista](../mfc/document-templates-and-the-document-view-creation-process.md).  
  
## <a name="see-also"></a>Vea también  
 [Compilación en el marco](../mfc/building-on-the-framework.md)

