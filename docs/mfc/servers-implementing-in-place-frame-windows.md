---
title: 'Servidores: Implementación de ventanas de marco en contexto'
ms.date: 09/09/2019
helpviewer_keywords:
- frame windows [MFC], implementing
- OLE server applications [MFC], frame windows
- servers, in-place frame windows
- frame windows [MFC], in-place
- in-place frame windows
ms.assetid: 09bde4d8-15e2-4fba-8d14-9b954d926b92
ms.openlocfilehash: bc5439003b7c891ac3f4000c9b7820746aec4c8d
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907538"
---
# <a name="servers-implementing-in-place-frame-windows"></a>Servidores: Implementación de ventanas de marco en contexto

En este artículo se explica lo que debe hacer para implementar ventanas de marco en contexto en la aplicación del servidor de edición visual si no usa el Asistente para aplicaciones para crear la aplicación de servidor. En lugar de seguir el procedimiento descrito en este artículo, puede usar una clase de ventana de marco en contexto existente de una aplicación generada por el Asistente para aplicaciones o de un ejemplo proporcionado con Visual C++.

#### <a name="to-declare-an-in-place-frame-window-class"></a>Para declarar una clase de ventana de marco en contexto

1. Derive una clase de ventana de marco en contexto de `COleIPFrameWnd`.

   - Use la macro DECLARE_DYNCREATE en el archivo de encabezado de clase.

   - Use la macro IMPLEMENT_DYNCREATE en el archivo de implementación de clase (. cpp). Esto permite que el marco de trabajo cree los objetos de esta clase.

1. Declare `COleResizeBar` un miembro en la clase de ventana de marco. Esto es necesario si desea admitir el cambio de tamaño en contexto en aplicaciones de servidor.

   Declare `OnCreate` un controlador de mensajes (mediante el [Asistente para clases](reference/mfc-class-wizard.md)) `Create` y llame `COleResizeBar` a para su miembro, si lo ha definido.

1. Si tiene una barra de herramientas, declare un `CToolBar` miembro en la clase de ventana de marco.

   Invalide la `OnCreateControlBars` función miembro para crear una barra de herramientas cuando el servidor esté activo. Por ejemplo:

   [!code-cpp[NVC_MFCOleServer#1](../mfc/codesnippet/cpp/servers-implementing-in-place-frame-windows_1.cpp)]

   Vea la explicación de este código después del paso 5.

1. Incluya el archivo de encabezado para esta clase de ventana de marco en contexto en el archivo main. cpp.

1. En `InitInstance` para la clase de aplicación, llame `SetServerInfo` a la función del objeto de plantilla de documento para especificar los recursos y la ventana de marco en contexto que se utilizará en la edición abierta y en contexto.

La serie de llamadas de función en la instrucción **If** crea la barra de herramientas a partir de los recursos proporcionados por el servidor. En este punto, la barra de herramientas forma parte de la jerarquía de ventanas del contenedor. Dado que esta barra de herramientas `CToolBar`se deriva de, pasará sus mensajes a su propietario, la ventana de marco de la aplicación contenedora, a menos que cambie el propietario. Esa es la razón por la `SetOwner` que es necesaria la llamada a. Esta llamada cambia la ventana donde se envían los comandos a la ventana de marco en contexto del servidor, lo que hace que los mensajes se pasen al servidor. Esto permite que el servidor reaccione a las operaciones en la barra de herramientas que proporciona.

El identificador del mapa de bits de la barra de herramientas debe ser el mismo que el de los demás recursos en contexto definidos en la aplicación de servidor. Vea [menús y recursos: Adiciones](../mfc/menus-and-resources-server-additions.md) de servidor para obtener más información.

Para obtener más información, vea [COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md), [COleResizeBar](../mfc/reference/coleresizebar-class.md)y [CDocTemplate:: SetServerInfo](../mfc/reference/cdoctemplate-class.md#setserverinfo) en la *referencia*de la biblioteca de clases.

## <a name="see-also"></a>Vea también

[Servidores](../mfc/servers.md)<br/>
[Servidores: implementar un servidor](../mfc/servers-implementing-a-server.md)<br/>
[Servidores: implementar documentos de servidor](../mfc/servers-implementing-server-documents.md)<br/>
[Servidores: elementos del servidor](../mfc/servers-server-items.md)
