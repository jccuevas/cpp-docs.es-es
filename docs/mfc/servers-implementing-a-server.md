---
title: 'Servidores: Implementación de un servidor'
ms.date: 11/04/2016
helpviewer_keywords:
- servers, implementing
- OLE server applications [MFC], implementing OLE servers
ms.assetid: 5bd57e8e-3b23-4f23-9597-496fac2d24b5
ms.openlocfilehash: 953d157f4bbad0b460947740a2622074dfc90f4f
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57267568"
---
# <a name="servers-implementing-a-server"></a>Servidores: Implementación de un servidor

En este artículo se explica el código que MFC Application Wizard se crea para una aplicación de servidor de edición visual. Si no utiliza al Asistente para aplicaciones, este artículo enumeran las áreas donde debe escribir código para implementar una aplicación de servidor.

Si usas al Asistente para aplicaciones para crear una nueva aplicación de servidor, proporciona una cantidad significativa de código específico de servidor para usted. Si va a agregar la funcionalidad del servidor de edición visual a una aplicación existente, debe duplicar el código que habría proporciona el Asistente para aplicaciones antes de agregar el resto del código de servidor necesario.

El código del servidor que proporciona el Asistente para la aplicación se divide en varias categorías:

- Definir recursos de servidor:

  - El recurso de menú que se utiliza cuando el servidor está modificando un elemento incrustado en su propia ventana.

  - Los recursos de menú y barra de herramientas usa cuando el servidor está activo en su lugar.

  Para obtener más información acerca de estos recursos, consulte [menús y recursos: Adiciones de servidor](../mfc/menus-and-resources-server-additions.md).

- Definir una clase de elemento derivado de `COleServerItem`. Para obtener más información sobre los elementos del servidor, consulte [servidores: Los elementos del servidor](../mfc/servers-server-items.md).

- Cambiar la clase base de la clase de documento para `COleServerDoc`. Para obtener más información, consulte [servidores: Implementar documentos de servidor](../mfc/servers-implementing-server-documents.md).

- Definir una clase de ventana de marco deriva `COleIPFrameWnd`. Para obtener más información, consulte [servidores: Implementación de Windows de marco en contexto](../mfc/servers-implementing-in-place-frame-windows.md).

- Creación de una entrada para la aplicación de servidor en la base de datos de registro de Windows y registrar la nueva instancia del servidor con el sistema OLE. Para obtener información sobre este tema, consulte [registro](../mfc/registration.md).

- Inicializar e iniciar la aplicación de servidor. Para obtener información sobre este tema, consulte [registro](../mfc/registration.md).

Para obtener más información, consulte [COleServerItem](../mfc/reference/coleserveritem-class.md), [COleServerDoc](../mfc/reference/coleserverdoc-class.md), y [COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md) en el *Class Library Reference*.

## <a name="see-also"></a>Vea también

[Servidores](../mfc/servers.md)<br/>
[Contenedores](../mfc/containers.md)<br/>
[Menús y recursos (OLE)](../mfc/menus-and-resources-ole.md)<br/>
[Registro](../mfc/registration.md)
