---
title: Información general del control Rich Edit
ms.date: 11/04/2016
helpviewer_keywords:
- rich edit controls [MFC]
ms.assetid: ad589b9f-a3fd-4820-bf1f-6b1965997e68
ms.openlocfilehash: 9ef696bc348dfb18b797b487224b97261020e11c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366871"
---
# <a name="overview-of-the-rich-edit-control"></a>Información general del control Rich Edit

> [!IMPORTANT]
> Si utiliza un control de edición enriquecido en un cuadro de diálogo (independientemente de si la aplicación es SDI, MDI o basada en cuadros de diálogo), debe llamar a [AfxInitRichEdit](../mfc/reference/application-information-and-management.md#afxinitrichedit) una vez antes de que se muestre el cuadro de diálogo. Un lugar típico para llamar a esta `InitInstance` función está en la función miembro del programa. No es necesario llamarlo para cada vez que se muestra el cuadro de diálogo, sólo la primera vez. No tiene que `AfxInitRichEdit` llamar si está `CRichEditView`trabajando con .

Los controles de edición enriquecidos ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) proporcionan una interfaz de programación para dar formato al texto. Sin embargo, una aplicación debe implementar los componentes de la interfaz de usuario necesarios para que las operaciones de formato estén disponibles para el usuario. Es decir, el control rich edit admite cambiar los atributos de carácter o párrafo del texto seleccionado. Algunos ejemplos de atributos de caracteres son negrita, cursiva, familia de fuentes y tamaño de punto. Entre los ejemplos de atributos de párrafo se incluyen la alineación, los márgenes y las tabulaciones. Sin embargo, depende de usted proporcionar la interfaz de usuario, ya sean botones de barra de herramientas, elementos de menú o un cuadro de diálogo de caracteres de formato. También hay funciones para consultar el control rich edit para los atributos de la selección actual. Utilice estas funciones para mostrar la configuración actual de los atributos, por ejemplo, estableciendo una marca de verificación en la interfaz de usuario del comando si la selección tiene el atributo de formato de caracteres en negrita.

Para obtener más información sobre el formato de caracteres y párrafos, vea Formato de [caracteres](../mfc/character-formatting-in-rich-edit-controls.md) y formato de [párrafo](../mfc/paragraph-formatting-in-rich-edit-controls.md) más adelante en este tema.

Los controles de edición enriquecidos admiten casi todas las operaciones y mensajes de notificación utilizados con controles de edición multilínea. Por lo tanto, las aplicaciones que ya utilizan controles de edición se pueden cambiar fácilmente para utilizar controles de edición enriquecidos. Los mensajes y notificaciones adicionales permiten a las aplicaciones acceder a la funcionalidad exclusiva de los controles de edición enriquecidos. Para obtener información sobre los controles de edición, vea [CEdit](../mfc/reference/cedit-class.md).

Para obtener más información sobre las notificaciones, vea [Notificaciones de un control de edición enriquecida](../mfc/notifications-from-a-rich-edit-control.md) más adelante en este tema.

## <a name="see-also"></a>Consulte también

[Uso de CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
