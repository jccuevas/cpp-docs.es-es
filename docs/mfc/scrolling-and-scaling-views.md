---
title: Desplazar y escalar vistas
ms.date: 11/04/2016
helpviewer_keywords:
- message handlers [MFC]
- scaling views [MFC]
- message handling [MFC], scroll bars in view class [MFC]
- scroll bars [MFC], messages
- scrolling views [MFC]
ms.assetid: f98a3421-c336-407e-97ee-dbb2ffd76fbd
ms.openlocfilehash: 366f0e2953e5190f80a2877804bff2fc7dbbd520
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372785"
---
# <a name="scrolling-and-scaling-views"></a>Desplazar y escalar vistas

MFC admite vistas que se desplazan y las vistas que se escalan automáticamente al tamaño de la ventana de marco que las muestra. La `CScrollView` clase admite ambos tipos de vistas.

Para obtener más información sobre el desplazamiento y el escalado, vea la clase [CScrollView](../mfc/reference/cscrollview-class.md) en la *referencia de MFC*. Para obtener un ejemplo de desplazamiento, vea el [ejemplo Scribble](../overview/visual-cpp-samples.md).

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué quieres saber más sobre

- Desplazamiento de una vista

- Escalado de una vista

- [Ver coordenadas](/windows/win32/gdi/window-coordinate-system)

## <a name="scrolling-a-view"></a><a name="_core_scrolling_a_view"></a>Desplazamiento de una vista

Con frecuencia, el tamaño de un documento es mayor que el tamaño que puede mostrar su vista. Esto puede ocurrir porque los datos del documento aumentan o el usuario reduce la ventana que enmarca la vista. En tales casos, la vista debe admitir el desplazamiento.

Cualquier vista puede controlar los `OnHScroll` mensajes `OnVScroll` de la barra de desplazamiento en sus funciones miembro y en sus. Puede implementar el control de mensajes de barra de desplazamiento en estas `CScrollView` funciones, haciendo todo el trabajo usted mismo, o puede usar la clase para controlar el desplazamiento por usted.

`CScrollView` realiza las operaciones siguientes:

- Administra los tamaños de ventanas y ventanas gráficas y los modos de asignación

- Se desplaza automáticamente en respuesta a los mensajes de la barra de desplazamiento

Puede especificar cuánto desplazarse por una "página" (cuando el usuario hace clic en un eje de barra de desplazamiento) y una "línea" (cuando el usuario hace clic en una flecha de desplazamiento). Planifique estos valores para adaptarse a la naturaleza de su punto de vista. Por ejemplo, es posible que desee desplazarse en incrementos de 1 píxel para una vista de gráficos, pero en incrementos basados en la altura de línea en documentos de texto.

## <a name="scaling-a-view"></a><a name="_core_scaling_a_view"></a>Escalado de una vista

Si desea que la vista se ajuste automáticamente al `CScrollView` tamaño de su ventana de marco, puede utilizarla para escalar en lugar de desplazarse. La vista lógica se estira o se retiene para ajustarse exactamente al área de cliente de la ventana. Una vista escalada no tiene barras de desplazamiento.

## <a name="see-also"></a>Consulte también

[Uso de vistas](../mfc/using-views.md)
