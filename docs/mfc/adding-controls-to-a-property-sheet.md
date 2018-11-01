---
title: Agregar controles a una hoja de propiedades
ms.date: 11/04/2016
helpviewer_keywords:
- controls [MFC], adding to property sheets
- property sheets, adding controls
ms.assetid: 24ad4c0b-c1db-4850-b9f0-34aae8d74571
ms.openlocfilehash: 141339bd146fec20f02e73e24bb9dae387f4e3ed
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50502783"
---
# <a name="adding-controls-to-a-property-sheet"></a>Agregar controles a una hoja de propiedades

De forma predeterminada, una hoja de propiedades asigna el área de ventana para las páginas de propiedades, el índice de tabulación y los botones Aceptar, Cancelar y aplicar. (Una hoja de propiedades no modal no tiene el acuerdo, Cancelar y aplicar los botones.) Puede agregar otros controles a la hoja de propiedades. Por ejemplo, puede agregar una ventana de vista previa a la derecha del área de la página de propiedades para mostrar al usuario cuál sería la configuración actual si se aplica a un objeto externo.

Puede agregar controles al cuadro de diálogo de hoja de propiedades en el `OnCreate` controlador. Colocar los controles adicionales normalmente requiere aumentar el tamaño del cuadro de diálogo de hoja de propiedades. Después de llamar a la clase base **CPropertySheet:: OnCreate**, llame a [GetWindowRect](../mfc/reference/cwnd-class.md#getwindowrect) para obtener el ancho y alto de la ventana de la hoja de propiedades asignada actualmente, expanda el rectángulo dimensiones y llamada [MoveWindow](../mfc/reference/cwnd-class.md#movewindow) para cambiar el tamaño de la ventana de la hoja de propiedades.

## <a name="see-also"></a>Vea también

[Hojas de propiedades](../mfc/property-sheets-mfc.md)<br/>
[CPropertyPage (clase)](../mfc/reference/cpropertypage-class.md)<br/>
[CPropertySheet (clase)](../mfc/reference/cpropertysheet-class.md)
