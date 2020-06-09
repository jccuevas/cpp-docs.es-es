---
title: Información general del control Rich Edit
ms.date: 11/04/2016
helpviewer_keywords:
- rich edit controls [MFC]
ms.assetid: ad589b9f-a3fd-4820-bf1f-6b1965997e68
ms.openlocfilehash: b99a5c6faaae4679b6aef67f240febbfb0f596e8
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84617708"
---
# <a name="overview-of-the-rich-edit-control"></a>Información general del control Rich Edit

> [!IMPORTANT]
> Si usa un control Rich Edit en un cuadro de diálogo (independientemente de si la aplicación es SDI, MDI o basada en cuadros de diálogo), debe llamar a [AfxInitRichEdit](reference/application-information-and-management.md#afxinitrichedit) una vez antes de que se muestre el cuadro de diálogo. Un lugar típico para llamar a esta función es en la `InitInstance` función miembro del programa. No es necesario llamarlo para cada vez que se muestra el cuadro de diálogo, solo la primera vez. No es necesario llamar a `AfxInitRichEdit` si está trabajando con `CRichEditView` .

Los controles Rich Edit ([CRichEditCtrl](reference/cricheditctrl-class.md)) proporcionan una interfaz de programación para dar formato al texto. Sin embargo, una aplicación debe implementar los componentes de interfaz de usuario necesarios para que las operaciones de formato estén disponibles para el usuario. Es decir, el control Rich Edit permite cambiar el carácter o los atributos de párrafo del texto seleccionado. Algunos ejemplos de atributos de caracteres son negrita, cursiva, familia de fuentes y tamaño de los puntos. Entre los ejemplos de atributos de párrafo se incluyen alineación, márgenes y tabulaciones. Sin embargo, depende de usted proporcionar la interfaz de usuario, independientemente de que sea un botón de la barra de herramientas, elementos de menú o un cuadro de diálogo de caracteres de formato. También hay funciones para consultar el control Rich Edit para los atributos de la selección actual. Use estas funciones para mostrar la configuración actual de los atributos, por ejemplo, estableciendo una marca de verificación en la interfaz de usuario de comandos si la selección tiene el atributo de formato de caracteres en negrita.

Para obtener más información sobre el formato de caracteres y párrafos, vea [formato de caracteres](character-formatting-in-rich-edit-controls.md) y [formato de párrafo](paragraph-formatting-in-rich-edit-controls.md) más adelante en este tema.

Los controles Rich Edit admiten casi todas las operaciones y mensajes de notificación que se usan con controles de edición multilínea. Por lo tanto, las aplicaciones que ya usan controles de edición se pueden cambiar fácilmente para usar controles Rich Edit. Los mensajes y las notificaciones adicionales permiten a las aplicaciones tener acceso a la funcionalidad única de los controles Rich Edit. Para obtener información sobre los controles de edición, vea [CEDIT](reference/cedit-class.md).

Para obtener más información sobre las notificaciones, vea [notificaciones de un control Rich Edit](notifications-from-a-rich-edit-control.md) más adelante en este tema.

## <a name="see-also"></a>Consulte también

[Uso de CRichEditCtrl](using-cricheditctrl.md)<br/>
[Permite](controls-mfc.md)
