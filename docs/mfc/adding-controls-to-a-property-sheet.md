---
title: Agregar controles a una hoja de propiedades
ms.date: 11/04/2016
helpviewer_keywords:
- controls [MFC], adding to property sheets
- property sheets, adding controls
ms.assetid: 24ad4c0b-c1db-4850-b9f0-34aae8d74571
ms.openlocfilehash: 527c0a5ef6e9dc4fcc9d7668c12e15ec956b0e70
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616060"
---
# <a name="adding-controls-to-a-property-sheet"></a>Agregar controles a una hoja de propiedades

De forma predeterminada, una hoja de propiedades asigna el área de ventana para las páginas de propiedades, el índice de tabulación y los botones aceptar, cancelar y aplicar. (Una hoja de propiedades no modal no tiene los botones aceptar, cancelar y aplicar). Puede agregar otros controles a la hoja de propiedades. Por ejemplo, puede Agregar una ventana de vista previa a la derecha del área de la página de propiedades para mostrar al usuario el aspecto que tendría la configuración actual si se aplica a un objeto externo.

Puede Agregar controles al cuadro de diálogo de la hoja de propiedades en el `OnCreate` controlador. La adaptación de controles adicionales normalmente requiere expandir el tamaño del cuadro de diálogo de la hoja de propiedades. Después de llamar a la clase base **CPropertySheet:: Alcreate**, llame a [GetWindowRect](reference/cwnd-class.md#getwindowrect) para obtener el ancho y el alto de la ventana de la hoja de propiedades asignada actualmente, expanda las dimensiones del rectángulo y llame a [MoveWindow](reference/cwnd-class.md#movewindow) para cambiar el tamaño de la ventana de la hoja de propiedades.

## <a name="see-also"></a>Consulte también

[Hojas de propiedades](property-sheets-mfc.md)<br/>
[CPropertyPage (clase)](reference/cpropertypage-class.md)<br/>
[CPropertySheet (clase)](reference/cpropertysheet-class.md)
