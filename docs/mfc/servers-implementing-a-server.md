---
title: 'Servidores: Implementar un servidor | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- servers, implementing
- OLE server applications [MFC], implementing OLE servers
ms.assetid: 5bd57e8e-3b23-4f23-9597-496fac2d24b5
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 148a3da3c904f5c314c75fb71deede3c92163cc6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="servers-implementing-a-server"></a>Servidores: Implementar un servidor
Este artículo explica el código que crea el Asistente para aplicaciones MFC para una aplicación de servidor de edición visual. Si no se usa al Asistente para aplicaciones, este artículo enumeran las áreas donde debe escribir código para implementar una aplicación de servidor.  
  
 Si está utilizando al Asistente para aplicaciones para crear una nueva aplicación de servidor, proporciona una gran cantidad de código específico del servidor de. Si va a agregar la funcionalidad del servidor de edición visual a una aplicación existente, debe duplicar el código proporcionado por el Asistente para aplicaciones antes de agregar el resto del código de servidor necesario.  
  
 El código del servidor que proporciona el Asistente para la aplicación se divide en varias categorías:  
  
-   Definir recursos de servidor:  
  
    -   El recurso de menú que se utiliza cuando el servidor está modificando un elemento incrustado en su propia ventana.  
  
    -   Los recursos de menú y barra de herramientas que se usa cuando el servidor está activo en su lugar.  
  
     Para obtener más información acerca de estos recursos, consulte [menús y recursos: adiciones de servidor](../mfc/menus-and-resources-server-additions.md).  
  
-   Definir una clase de elemento derivado de `COleServerItem`. Para obtener más información sobre elementos del servidor, consulte [servidores: elementos de servidor](../mfc/servers-server-items.md).  
  
-   Cambiar la clase base de la clase de documento para `COleServerDoc`. Para obtener más información, consulte [servidores: implementar documentos de servidor](../mfc/servers-implementing-server-documents.md).  
  
-   Definir una clase de ventana de marco derivadas de `COleIPFrameWnd`. Para obtener más información, consulte [servidores: implementar ventanas de marco en contexto](../mfc/servers-implementing-in-place-frame-windows.md).  
  
-   Crear una entrada para la aplicación de servidor en la base de datos de registro de Windows y registrar la nueva instancia del servidor con el sistema OLE. Para obtener información acerca de este tema, consulte [registro](../mfc/registration.md).  
  
-   Inicializar e iniciar la aplicación de servidor. Para obtener información acerca de este tema, consulte [registro](../mfc/registration.md).  
  
 Para obtener más información, consulte [COleServerItem](../mfc/reference/coleserveritem-class.md), [COleServerDoc](../mfc/reference/coleserverdoc-class.md), y [COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md) en el *Class Library Reference*.  
  
## <a name="see-also"></a>Vea también  
 [Servidores](../mfc/servers.md)   
 [Contenedores](../mfc/containers.md)   
 [Menús y recursos (OLE)](../mfc/menus-and-resources-ole.md)   
 [Registro](../mfc/registration.md)

