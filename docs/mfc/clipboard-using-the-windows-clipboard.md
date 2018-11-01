---
title: 'Portapapeles: Usar el Portapapeles de Windows'
ms.date: 11/04/2016
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
ms.openlocfilehash: 67bc337af2cf55a4f39698f730ce14a3369ef742
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50460702"
---
# <a name="clipboard-using-the-windows-clipboard"></a>Portapapeles: Usar el Portapapeles de Windows

Este tema describe cómo usar la API de Portapapeles de Windows estándar dentro de la aplicación MFC.

Mayoría de las aplicaciones para Windows admite Cortar o copiar datos en el Portapapeles de Windows y pegar datos desde el Portapapeles. Varían los formatos de datos del Portapapeles entre aplicaciones. El marco de trabajo admite sólo un número limitado de formatos de Portapapeles para un número limitado de clases. Normalmente se implementarán los comandos relacionados con el Portapapeles, cortar, copiar y pegar, en el menú de edición de la vista. La biblioteca de clases define los identificadores de comando para estos comandos: **ID_EDIT_CUT**, **ID_EDIT_COPY**, y **ID_EDIT_PASTE**. También se definen los símbolos de línea de mensaje.

[Los mensajes y comandos en el marco](../mfc/messages-and-commands-in-the-framework.md) explica cómo controlar los comandos de menú en la aplicación asignando el comando de menú a una función de controlador. Siempre y cuando la aplicación no define las funciones de controlador para los comandos del Portapapeles en el menú Edición, permanecen deshabilitados. Para escribir funciones de controlador para los comandos Cortar y copiar, implemente la selección en la aplicación. Para escribir una función de controlador para el comando Pegar, consulte el Portapapeles para ver si contiene datos en un formato de la aplicación puede aceptar. Por ejemplo, para habilitar el comando Copy, puede escribir a un controlador de algo parecido a lo siguiente:

[!code-cpp[NVC_MFCListView#2](../atl/reference/codesnippet/cpp/clipboard-using-the-windows-clipboard_1.cpp)]

Los comandos Cortar, copiar y pegar solo son significativos en ciertos contextos. Los comandos Cortar y copiar deben habilitarse únicamente cuando se selecciona un elemento y el comando Pegar sólo cuando algo está en el Portapapeles. Puede proporcionar este comportamiento mediante la definición de funciones del controlador de actualización que habilitan o deshabilitan estos comandos en función del contexto. Para obtener más información, consulte [cómo actualizar objetos de interfaz de usuario](../mfc/how-to-update-user-interface-objects.md).

La biblioteca Microsoft Foundation Class proporcionan compatibilidad con el Portapapeles para su edición de texto con el `CEdit` y `CEditView` clases. Las clases OLE también simplifican la implementación las operaciones del Portapapeles que incluyen elementos OLE. Para obtener más información sobre las clases OLE, vea [Portapapeles: usar el mecanismo del Portapapeles OLE](../mfc/clipboard-using-the-ole-clipboard-mechanism.md).

Implementación de otra edición comandos de menú, como deshacer (**ID_EDIT_UNDO**) y Rehacer (**ID_EDIT_REDO**), también se deja para usted. Si la aplicación no es compatible con estos comandos, puede eliminarlos fácilmente desde el archivo de recursos con los editores de recursos de Visual C++.

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Copiar y pegar datos](../mfc/clipboard-copying-and-pasting-data.md)

- [Mediante el mecanismo del Portapapeles de OLE](../mfc/clipboard-using-the-ole-clipboard-mechanism.md)

## <a name="see-also"></a>Vea también

[Portapapeles](../mfc/clipboard.md)

