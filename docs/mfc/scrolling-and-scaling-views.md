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
ms.openlocfilehash: 7d26bc656dec3fdcbb8fc5ea4918ec7d59bc5afc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62308607"
---
# <a name="scrolling-and-scaling-views"></a>Desplazar y escalar vistas

MFC admite vistas que se desplazan y vistas que se escalan automáticamente al tamaño de la ventana de marco que mostrarlos. Clase `CScrollView` admite ambos tipos de vistas.

Para obtener más información acerca de desplazar y escalar, vea la clase [CScrollView](../mfc/reference/cscrollview-class.md) en el *referencia de MFC*. Para obtener un ejemplo de desplazamiento, vea el [ejemplo Scribble](../overview/visual-cpp-samples.md).

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- Desplazamiento de una vista

- Escalado de una vista

- [Coordenadas de la vista](/windows/desktop/gdi/window-coordinate-system)

##  <a name="_core_scrolling_a_view"></a> Desplazamiento de una vista

Con frecuencia el tamaño de un documento es mayor que el tamaño que puede mostrar su vista. Esto puede ocurrir porque los datos del documento aumentan o reduce la ventana que rodea a la vista de usuario. En tales casos, la vista debe admitir el desplazamiento.

Cualquier vista puede controlar mensajes de la barra de desplazamiento en su `OnHScroll` y `OnVScroll` funciones miembro. Puede hacer todo el trabajo usted mismo cualquier control de mensajes de barra de desplazamiento de implementar en estas funciones, o puede usar el `CScrollView` clase para controlar el desplazamiento por usted.

`CScrollView` hace lo siguiente:

- Administra los tamaños de ventana y la ventanilla y modos de asignación.

- Se desplaza automáticamente en respuesta a mensajes de la barra de desplazamiento

Puede especificar cuánto para desplazarse de una "página" (cuando el usuario hace clic en un eje de la barra de desplazamiento) y una "línea" (cuando el usuario hace clic en una flecha de desplazamiento). Planear estos valores para que se ajuste a la naturaleza de la vista. Por ejemplo, es posible que desee desplazarse en incrementos de 1 píxel para una vista de gráficos, pero en incrementos según el alto de línea en documentos de texto.

##  <a name="_core_scaling_a_view"></a> Escalado de una vista

Si desea que la vista se ajuste automáticamente el tamaño de su ventana de marco, puede usar `CScrollView` para el escalado en lugar de desplazamiento. La vista lógica se estira o se encoge para ajustarse exactamente a área de cliente de la ventana. Una vista ajustada no tiene ninguna barra de desplazamiento.

## <a name="see-also"></a>Vea también

[Uso de vistas](../mfc/using-views.md)
