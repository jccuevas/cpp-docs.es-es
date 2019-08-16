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
ms.openlocfilehash: 7064880c5ceef8e7dc3e35bb7ef5bc700b0842d2
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69511230"
---
# <a name="scrolling-and-scaling-views"></a>Desplazar y escalar vistas

MFC admite vistas que se desplazan y las vistas que se escalan automáticamente al tamaño de la ventana de marco que las muestra. La `CScrollView` clase admite ambos tipos de vistas.

Para obtener más información sobre el desplazamiento y el escalado, vea la clase [CScrollView](../mfc/reference/cscrollview-class.md) en la *referencia de MFC*. Para ver un ejemplo de desplazamiento, vea el [ejemplo Scribble](../overview/visual-cpp-samples.md).

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- Desplazar una vista

- Escalado de una vista

- [Ver coordenadas](/windows/win32/gdi/window-coordinate-system)

##  <a name="_core_scrolling_a_view"></a>Desplazar una vista

Con frecuencia, el tamaño de un documento es mayor que el tamaño que puede mostrar su vista. Esto puede deberse a que los datos del documento aumentan o a que el usuario reduce la ventana que rodea la vista. En tales casos, la vista debe admitir el desplazamiento.

Cualquier vista puede controlar los mensajes de la barra de `OnHScroll` desplazamiento `OnVScroll` en sus funciones miembro y. Puede implementar el control de mensajes de la barra de desplazamiento en estas funciones, haciendo todo el trabajo, o bien puede usar `CScrollView` la clase para controlar el desplazamiento.

`CScrollView` hace lo siguiente:

- Administra los tamaños de ventana y de ventanilla y los modos de asignación

- Se desplaza automáticamente en respuesta a los mensajes de la barra de desplazamiento

Puede especificar la cantidad de desplazamiento de una "página" (cuando el usuario hace clic en un eje de barra de desplazamiento) y una "línea" (cuando el usuario hace clic en una flecha de desplazamiento). Planee estos valores para que se adapten a la naturaleza de la vista. Por ejemplo, puede que desee desplazarse en incrementos de 1 píxel para una vista de gráficos, pero en incrementos basados en el alto de línea en los documentos de texto.

##  <a name="_core_scaling_a_view"></a>Escalado de una vista

Si desea que la vista se ajuste automáticamente al tamaño de la ventana de marco, puede usar `CScrollView` para el ajuste de escala en lugar de desplazarse. La vista lógica se estira o se reduce para ajustarse exactamente al área cliente de la ventana. Una vista escalada no tiene barras de desplazamiento.

## <a name="see-also"></a>Vea también

[Uso de vistas](../mfc/using-views.md)
