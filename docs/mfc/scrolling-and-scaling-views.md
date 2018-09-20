---
title: Desplazar y escalar vistas | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- message handlers [MFC]
- scaling views [MFC]
- message handling [MFC], scroll bars in view class [MFC]
- scroll bars [MFC], messages
- scrolling views [MFC]
ms.assetid: f98a3421-c336-407e-97ee-dbb2ffd76fbd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 85741e2d58f6189d00af63d2c4b1c95c5b87307c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46422745"
---
# <a name="scrolling-and-scaling-views"></a>Desplazar y escalar vistas

MFC admite vistas que se desplazan y vistas que se escalan automáticamente al tamaño de la ventana de marco que mostrarlos. Clase `CScrollView` admite ambos tipos de vistas.

Para obtener más información acerca de desplazar y escalar, vea la clase [CScrollView](../mfc/reference/cscrollview-class.md) en el *referencia de MFC*. Para obtener un ejemplo de desplazamiento, vea el [ejemplo Scribble](../visual-cpp-samples.md).

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

