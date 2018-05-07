---
title: Ilustración de enrutamiento de comandos | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC, command routing
- command handling [MFC], routing commands
- command routing [MFC], OnCmdMsg handler
ms.assetid: 4b7b4741-565f-4878-b076-fd85c670f87f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a12a5cd19177761dfbf484c64f528d8def194ca5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="command-routing-illustration"></a>Ilustración de enrutamiento de comandos
Como ejemplo, considere un mensaje de comando de un elemento de menú Borrar todo en el menú de edición de una aplicación MDI. Suponga que la función de controlador para este comando resulta ser una función miembro de clase de documento de la aplicación. Le mostramos cómo ese comando llega a su controlador después de que el usuario elija el elemento de menú:  
  
1.  La ventana de marco principal recibe el mensaje de comando en primer lugar.  
  
2.  La ventana de marco principal MDI da una oportunidad para controlar el comando de la ventana secundaria MDI activa actualmente.  
  
3.  El enrutamiento estándar de una ventana de marco secundaria MDI da su vista una oportunidad en la línea de comandos antes de comprobar su propio mapa de mensajes.  
  
4.  La vista comprueba su propio mapa de mensajes en primer lugar y, a continuación no encontrar ningún controlador, enruta el comando hacia su documento asociado.  
  
5.  El documento comprueba su mapa de mensajes y encuentra un controlador. Se llama a esta función de miembro de documento y el enrutamiento se detiene.  
  
 Si el documento no tenía un controlador, se enrutaría el comando a su plantilla de documento. A continuación, el comando volvería a la vista y, a continuación, en la ventana de marco. Por último, la ventana de marco comprobaría su mapa de mensajes. Si la comprobación no se pudo así, el comando se enrutaría a la ventana de marco principal MDI y, a continuación, en el objeto de aplicación: el destino final de los comandos no controlados.  
  
## <a name="see-also"></a>Vea también  
 [Cómo el marco llama a un controlador](../mfc/how-the-framework-calls-a-handler.md)

