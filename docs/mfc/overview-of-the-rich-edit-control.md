---
title: Información general del control Rich Edit
ms.date: 11/04/2016
helpviewer_keywords:
- rich edit controls [MFC]
ms.assetid: ad589b9f-a3fd-4820-bf1f-6b1965997e68
ms.openlocfilehash: c45cb638ec860bb803c7de32065606dc3cc176b2
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57287718"
---
# <a name="overview-of-the-rich-edit-control"></a>Información general del control Rich Edit

> [!IMPORTANT]
>  Si utilizas un control rich edit en un cuadro de diálogo (independientemente de si la aplicación es SDI, MDI o basada en el cuadro de diálogo), debe llamar a [AfxInitRichEdit](../mfc/reference/application-information-and-management.md#afxinitrichedit) una vez antes el cuadro de diálogo se muestra el cuadro. Es un lugar típico para llamar a esta función en el programa `InitInstance` función miembro. No es necesario llamarlo para cada vez que se muestre el cuadro de diálogo, solo la primera vez. No es necesario llamar a `AfxInitRichEdit` si está trabajando con `CRichEditView`.

Controles Rich edit ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) proporcionan una interfaz de programación para dar formato al texto. Sin embargo, una aplicación debe implementar los componentes de interfaz de usuario necesarios para realizar operaciones de formato disponibles para el usuario. Es decir, el control rich edit admite cambiar los atributos de carácter o de párrafo del texto seleccionado. Algunos ejemplos de caracteres son atributos de negrita, cursiva, familia de fuentes y tamaño de punto. Alineación, márgenes y tabulaciones son ejemplos de atributos de párrafo. Sin embargo, resulta depende de usted para proporcionar la interfaz de usuario, ya sea los botones de barra de herramientas, los elementos de menú o un cuadro de diálogo Formato de caracteres. También hay funciones para consultar el control rich edit para los atributos de la selección actual. Utilice estas funciones para mostrar la configuración actual de los atributos, por ejemplo, establecer una marca de verificación en la interfaz de usuario de comandos si la selección tiene el atributo de formato de caracteres en negrita.

Para obtener más información sobre caracteres y el formato de párrafo, consulte [formato de caracteres](../mfc/character-formatting-in-rich-edit-controls.md) y [el formato de párrafo](../mfc/paragraph-formatting-in-rich-edit-controls.md) más adelante en este tema.

Controles Rich edit admiten casi todas las operaciones y mensajes de notificación utilizados con controles de edición multilínea. Por lo tanto, las aplicaciones que ya utilizan controles de edición pueden modificarse fácilmente para usar a enriquecido controles de edición. Las notificaciones y los mensajes adicionales permiten a las aplicaciones tener acceso a los controles de edición exclusivas enriquecido de funcionalidad. Para obtener información acerca de los controles de edición, vea [CEdit](../mfc/reference/cedit-class.md).

Para obtener más información acerca de las notificaciones, consulte [notificaciones desde un Control Rich Edit](../mfc/notifications-from-a-rich-edit-control.md) más adelante en este tema.

## <a name="see-also"></a>Vea también

[Uso de CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
