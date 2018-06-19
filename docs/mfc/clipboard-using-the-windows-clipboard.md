---
title: 'Portapapeles: Usar el Portapapeles de Windows | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Clipboard commands
- Cut/Copy and Paste command handler functions [MFC]
- handler functions, Cut/Copy and Paste commands
- Clipboard [MFC], commands
- commands [MFC], implementing Edit
- Clipboard commands [MFC], implementing
- Windows Clipboard [MFC]
- Clipboard [MFC], Windows Clipboard API
ms.assetid: 24415b42-9301-4a70-b69a-44c97918319f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3ed1b3e9cc0cdd368a37657a751df67bed3f72dc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33342113"
---
# <a name="clipboard-using-the-windows-clipboard"></a>Portapapeles: Usar el Portapapeles de Windows
Este tema describe cómo utilizar la API del Portapapeles de Windows estándar dentro de la aplicación MFC.  
  
 Mayoría de las aplicaciones para Windows admite Cortar o copiar datos en el Portapapeles de Windows y pegar datos desde el Portapapeles. Los formatos de datos del Portapapeles varían de una aplicación. El marco de trabajo admite solo un número limitado de formatos del Portapapeles para un número limitado de clases. Normalmente implementará los comandos relacionados con el Portapapeles, cortar, copiar y pegar, en el menú de edición de la vista. La biblioteca de clases define los identificadores de comando para estos comandos: **ID_EDIT_CUT**, **ID_EDIT_COPY**, y **ID_EDIT_PASTE**. También se definen los símbolos de línea de mensaje.  
  
 [Mensajes y comandos en el marco de trabajo](../mfc/messages-and-commands-in-the-framework.md) explica cómo controlar los comandos de menú en la aplicación asignando el comando de menú a una función de controlador. Siempre y cuando la aplicación no define las funciones de controlador para los comandos del Portapapeles en el menú Edición, estas funciones permanecen deshabilitadas. Para escribir funciones del controlador para los comandos Cortar y copiar, implemente la selección en la aplicación. Para escribir una función de controlador para el comando Pegar, consulte el Portapapeles para ver si contiene datos en un formato que pueda aceptar la aplicación. Por ejemplo, para habilitar el comando de copia, puede escribir a un controlador algo parecido a lo siguiente:  
  
 [!code-cpp[NVC_MFCListView#2](../atl/reference/codesnippet/cpp/clipboard-using-the-windows-clipboard_1.cpp)]  
  
 Los comandos Cortar, copiar y pegar solo son significativos en ciertos contextos. Los comandos Cortar y copiar deben habilitarse solo cuando se selecciona un elemento y el comando Pegar sólo cuando haya algo en el Portapapeles. Puede proporcionar este comportamiento mediante la definición de funciones del controlador de actualización que habilitan o deshabilitan estos comandos dependiendo del contexto. Para obtener más información, consulte [cómo actualizar objetos de interfaz de usuario](../mfc/how-to-update-user-interface-objects.md).  
  
 La biblioteca Microsoft Foundation Class proporciona compatibilidad del Portapapeles para la edición de texto con el `CEdit` y `CEditView` clases. Las clases OLE también simplifican la implementación las operaciones del Portapapeles que incluyen elementos OLE. Para obtener más información sobre las clases OLE, vea [Portapapeles: usar el mecanismo del Portapapeles OLE](../mfc/clipboard-using-the-ole-clipboard-mechanism.md).  
  
 Implementar otros Editar comandos de menú, como deshacer (**ID_EDIT_UNDO**) y Rehacer (**ID_EDIT_REDO**), también se deja para usted. Si la aplicación no admite estos comandos, puede eliminarlas fácilmente desde el archivo de recursos mediante los editores de recursos de Visual C++.  
  
## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea obtener más información acerca de  
  
-   [Copiar y pegar datos](../mfc/clipboard-copying-and-pasting-data.md)  
  
-   [Usar el mecanismo del Portapapeles de OLE](../mfc/clipboard-using-the-ole-clipboard-mechanism.md)  
  
## <a name="see-also"></a>Vea también  
 [Portapapeles](../mfc/clipboard.md)

