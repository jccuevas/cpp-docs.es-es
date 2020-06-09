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
ms.openlocfilehash: 1b11bfe18443858de0dd7032f72fecadb1d6ebdd
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626038"
---
# <a name="clipboard-using-the-windows-clipboard"></a>Portapapeles: Usar el Portapapeles de Windows

En este tema se describe cómo utilizar la API del portapapeles de Windows estándar en la aplicación MFC.

La mayoría de las aplicaciones para Windows permiten cortar o copiar datos en el portapapeles de Windows y pegar datos del portapapeles. Los formatos de datos del portapapeles varían entre las aplicaciones. El marco de trabajo solo admite un número limitado de formatos del portapapeles para un número limitado de clases. Normalmente, se implementan los comandos relacionados con el portapapeles (cortar, copiar y pegar) en el menú edición de la vista. La biblioteca de clases define los identificadores de comando para estos comandos: **ID_EDIT_CUT**, **ID_EDIT_COPY**y **ID_EDIT_PASTE**. También se definen sus solicitudes de línea de mensaje.

[Mensajes y comandos en el marco de trabajo](messages-and-commands-in-the-framework.md) explica cómo controlar los comandos de menú en la aplicación asignando el comando de menú a una función de controlador. Siempre que la aplicación no defina funciones de controlador para los comandos del portapapeles en el menú Edición, permanecerán deshabilitadas. Para escribir funciones de controlador para los comandos cortar y copiar, implemente la selección en la aplicación. Para escribir una función de controlador para el comando Paste, consulte el portapapeles para ver si contiene datos en un formato que la aplicación puede aceptar. Por ejemplo, para habilitar el comando Copiar, puede escribir un controlador similar al siguiente:

[!code-cpp[NVC_MFCListView#2](../atl/reference/codesnippet/cpp/clipboard-using-the-windows-clipboard_1.cpp)]

Los comandos cortar, copiar y pegar solo son significativos en determinados contextos. Los comandos cortar y copiar solo deben habilitarse cuando se selecciona algo y el comando pegar solo cuando hay algo en el portapapeles. Puede proporcionar este comportamiento definiendo las funciones del controlador de actualización que habilitan o deshabilitan estos comandos en función del contexto. Para obtener más información, vea [Cómo actualizar objetos de la interfaz de usuario](how-to-update-user-interface-objects.md).

La biblioteca MFC proporciona compatibilidad con el portapapeles para la edición de texto con las `CEdit` `CEditView` clases y. Las clases OLE también simplifican la implementación de operaciones del portapapeles que implican elementos OLE. Para obtener más información sobre las clases OLE, vea [portapapeles: usar el mecanismo del portapapeles OLE](clipboard-using-the-ole-clipboard-mechanism.md).

También se le deja la implementación de otros comandos de menú Edición, como deshacer (**ID_EDIT_UNDO**) y rehacer (**ID_EDIT_REDO**). Si la aplicación no admite estos comandos, puede eliminarlos fácilmente del archivo de recursos mediante los Visual C++ editores de recursos.

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Copiado y pegado de datos](clipboard-copying-and-pasting-data.md)

- [Usar el mecanismo del portapapeles OLE](clipboard-using-the-ole-clipboard-mechanism.md)

## <a name="see-also"></a>Consulte también

[Portapapeles](clipboard.md)
