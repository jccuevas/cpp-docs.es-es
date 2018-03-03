---
title: 'Servidores: Implementar ventanas de marco en contexto | Documentos de Microsoft'
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
- frame windows [MFC], implementing
- OLE server applications [MFC], frame windows
- servers, in-place frame windows
- frame windows [MFC], in-place
- in-place frame windows
ms.assetid: 09bde4d8-15e2-4fba-8d14-9b954d926b92
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7e26cbb0099f897c65ab3e39338f3c36e77112e0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="servers-implementing-in-place-frame-windows"></a>Servidores: Implementar ventanas de marco en contexto
Este artículo explica lo que debe hacer para implementar ventanas de marco en contexto en la aplicación de servidor de edición visual si no utiliza al Asistente para aplicaciones para crear la aplicación de servidor. En lugar de seguir el procedimiento descrito en este artículo, podría utilizar una clase de ventana de marco en contexto existente de una aplicación generada por el asistente o un ejemplo que se proporciona con Visual C++.  
  
#### <a name="to-declare-an-in-place-frame-window-class"></a>Para declarar una clase de ventana de marco en contexto  
  
1.  Derivar una clase de ventana de marco en contexto desde `COleIPFrameWnd`.  
  
    -   Use la `DECLARE_DYNCREATE` macro en el archivo de encabezado de clase.  
  
    -   Use la `IMPLEMENT_DYNCREATE` macro en el archivo de implementación (.cpp) de la clase. Esto permite que los objetos de esta clase que se creará en el marco de trabajo.  
  
2.  Declarar un `COleResizeBar` miembro en la clase de ventana de marco. Esto es necesario si desea admitir el cambio de tamaño en contexto en las aplicaciones de servidor.  
  
     Declarar un `OnCreate` controlador de mensajes (mediante el **propiedades** ventana) y llame a **crear** para su `COleResizeBar` miembro, si se ha definido.  
  
3.  Si tiene una barra de herramientas, declare un `CToolBar` miembro en la clase de ventana de marco.  
  
     Invalidar el `OnCreateControlBars` función de miembro para crear una barra de herramientas cuando el servidor está activo en su lugar. Por ejemplo:  
  
     [!code-cpp[NVC_MFCOleServer#1](../mfc/codesnippet/cpp/servers-implementing-in-place-frame-windows_1.cpp)]  
  
     Vea la explicación de este código después del paso 5.  
  
4.  Incluir el archivo de encabezado para esta clase de ventana de marco en contexto en el archivo .cpp principal.  
  
5.  En `InitInstance` para la clase de aplicación, llame a la `SetServerInfo` función del objeto de plantilla de documento para especificar los recursos y la ventana de marco en contexto que se usará en la edición abierta y en contexto.  
  
 Llama a la serie de función en la **si** instrucción crea la barra de herramientas de los recursos del servidor que le proporcionado. En este momento, la barra de herramientas es parte de la jerarquía de la ventana del contenedor. Dado que se deriva de esta barra de herramientas `CToolBar`, pasará sus mensajes a su propietario, la ventana de marco de la aplicación contenedora, a menos que cambie el propietario. Por eso la llamada a `SetOwner` es necesario. Esta llamada cambia la ventana donde se envían los comandos como ventana de marco en contexto del servidor, haciendo que los mensajes que se va a pasar al servidor. Esto permite que el servidor reaccionar a las operaciones en la barra de herramientas que proporciona.  
  
 El identificador del mapa de bits de barra de herramientas debe ser igual que los otros recursos en contexto definidos en la aplicación de servidor. Vea [menús y recursos: adiciones de servidor](../mfc/menus-and-resources-server-additions.md) para obtener más información.  
  
 Para obtener más información, consulte [COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md), [COleResizeBar](../mfc/reference/coleresizebar-class.md), y [CDocTemplate:: SetServerInfo](../mfc/reference/cdoctemplate-class.md#setserverinfo) en el *Class Library Reference*.  
  
## <a name="see-also"></a>Vea también  
 [Servidores](../mfc/servers.md)   
 [Servidores: Implementar un servidor](../mfc/servers-implementing-a-server.md)   
 [Servidores: Implementar documentos de servidor](../mfc/servers-implementing-server-documents.md)   
 [Servidores: Elementos de servidor](../mfc/servers-server-items.md)

