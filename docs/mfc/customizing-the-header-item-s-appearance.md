---
title: Personalizar la apariencia del elemento de encabezado&#39;s
ms.date: 11/04/2016
helpviewer_keywords:
- header controls [MFC], customization of items
- CHeaderCtrl class [MFC], customizing the items
- HDS_ styles
ms.assetid: b1e1e326-ec7d-4dbd-a46f-96a3e2055618
ms.openlocfilehash: 8bf1bdad6a0408746b50b6b0dcbecbce308f5ede
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84617086"
---
# <a name="customizing-the-header-item39s-appearance"></a>Personalizar la apariencia del elemento de encabezado&#39;s

Al establecer el parámetro *dwStyle* al crear por primera vez un control de encabezado ([CHeaderCtrl:: Create](reference/cheaderctrl-class.md#create)), puede definir la apariencia y el comportamiento de los elementos de encabezado o del propio control de encabezado.

A continuación se muestra un muestreo de los estilos que puede establecer y su finalidad:

- Para que un elemento de encabezado tenga el aspecto de un pulsador, utilice el estilo **HDS_BUTTONS** .

   Use este estilo si desea realizar acciones en respuesta a los clics del mouse en un elemento de encabezado, como la ordenación de datos por una columna determinada, como se hace en Microsoft Outlook.

- Para asignar a los elementos de encabezado un aspecto de "seguimiento activo" cuando el cursor del mouse pasa sobre ellos, use el estilo de **HDS_HOTTRACK** .

   El seguimiento activo muestra un esquema 3D a medida que el puntero pasa sobre un elemento en una barra plana de otro modo.

- Para indicar que el control de encabezado debe ocultarse, use el estilo **HDS_HIDDEN** .

   El estilo **HDS_HIDDEN** indica que el control de encabezado está pensado para usarse como un contenedor de datos y no como un control visual. Este estilo no oculta automáticamente el control, sino que, en su lugar, afecta al comportamiento de `CHeaderCtrl::Layout` . El valor devuelto en el miembro *CY* de la `WINDOWPOS` estructura será cero, lo que indica que el control no debe estar visible para el usuario.

Para obtener más información acerca de estas propiedades, vea [elementos](/windows/win32/Controls/header-controls) en el Windows SDK. Para obtener información sobre cómo agregar elementos a un control de encabezado, vea [Agregar elementos al control de encabezado](adding-items-to-the-header-control.md).

## <a name="see-also"></a>Consulte también

[Uso de CHeaderCtrl](using-cheaderctrl.md)<br/>
[Permite](controls-mfc.md)
