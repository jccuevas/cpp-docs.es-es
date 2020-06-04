---
title: Personalizar el aspecto del elemento&#39;de encabezado
ms.date: 11/04/2016
helpviewer_keywords:
- header controls [MFC], customization of items
- CHeaderCtrl class [MFC], customizing the items
- HDS_ styles
ms.assetid: b1e1e326-ec7d-4dbd-a46f-96a3e2055618
ms.openlocfilehash: 6ce676695d717fcc5d418fe4ed5df91b4f9bca95
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508717"
---
# <a name="customizing-the-header-item39s-appearance"></a>Personalizar el aspecto del elemento&#39;de encabezado

Al establecer el parámetro *dwStyle* al crear por primera vez un control de encabezado ([CHeaderCtrl:: Create](../mfc/reference/cheaderctrl-class.md#create)), puede definir la apariencia y el comportamiento de los elementos de encabezado o del propio control de encabezado.

A continuación se muestra un muestreo de los estilos que puede establecer y su finalidad:

- Para que un elemento de encabezado tenga el aspecto de un pulsador, use el estilo **HDS_BUTTONS** .

   Use este estilo si desea realizar acciones en respuesta a los clics del mouse en un elemento de encabezado, como la ordenación de datos por una columna determinada, como se hace en Microsoft Outlook.

- Para asignar a los elementos de encabezado un aspecto de "seguimiento activo" cuando el cursor del mouse pasa sobre ellos, use el estilo **HDS_HOTTRACK** .

   El seguimiento activo muestra un esquema 3D a medida que el puntero pasa sobre un elemento en una barra plana de otro modo.

- Para indicar que se debe ocultar el control de encabezado, use el estilo **HDS_HIDDEN** .

   El estilo **HDS_HIDDEN** indica que el control de encabezado está pensado para usarse como un contenedor de datos y no como un control visual. Este estilo no oculta automáticamente el control, sino que, en su lugar, afecta al `CHeaderCtrl::Layout`comportamiento de. El valor devuelto en el miembro *CY* de `WINDOWPOS` la estructura será cero, lo que indica que el control no debe estar visible para el usuario.

Para obtener más información acerca de estas propiedades, vea [elementos](/windows/win32/Controls/header-controls) en el Windows SDK. Para obtener información sobre cómo agregar elementos a un control de encabezado, vea [Agregar elementos al control de encabezado](../mfc/adding-items-to-the-header-control.md).

## <a name="see-also"></a>Vea también

[Uso de CHeaderCtrl](../mfc/using-cheaderctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
