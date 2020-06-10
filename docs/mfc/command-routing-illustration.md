---
title: Ilustración de enrutamiento de comandos
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, command routing
- command handling [MFC], routing commands
- command routing [MFC], OnCmdMsg handler
ms.assetid: 4b7b4741-565f-4878-b076-fd85c670f87f
ms.openlocfilehash: d362cfe54a9b5a562237c7bb9632edae6e58228b
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622907"
---
# <a name="command-routing-illustration"></a>Ilustración de enrutamiento de comandos

Para ilustrarlo, considere un mensaje de comando de un elemento de menú borrar todo en el menú edición de una aplicación MDI. Suponga que la función de controlador para este comando es una función miembro de la clase de documento de la aplicación. Aquí se muestra cómo el comando alcanza su controlador después de que el usuario elija el elemento de menú:

1. La ventana de marco principal recibe el mensaje de comando en primer lugar.

1. La ventana principal del marco MDI proporciona a la ventana secundaria MDI activa actualmente una oportunidad de controlar el comando.

1. El enrutamiento estándar de una ventana de marco secundario MDI ofrece a su vista una oportunidad en el comando antes de comprobar su propio mapa de mensajes.

1. La vista comprueba su propio mapa de mensajes primero y, si no encuentra ningún controlador, enruta el comando a su documento asociado.

1. El documento comprueba su mapa de mensajes y busca un controlador. Se llama a esta función miembro de documento y se detiene el enrutamiento.

Si el documento no tenía un controlador, el siguiente enrutaría el comando a su plantilla de documento. Después, el comando volvería a la vista y, a continuación, a la ventana de marco. Por último, la ventana de marco comprobaría su mapa de mensajes. Si esta comprobación no se realiza correctamente, el comando se enrutaría a la ventana de marco MDI principal y después al objeto de aplicación, el destino final de los comandos no controlados.

## <a name="see-also"></a>Consulte también

[Cómo el marco llama a un controlador](how-the-framework-calls-a-handler.md)
