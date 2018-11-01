---
title: Funciones miembro de control deslizante
ms.date: 11/04/2016
helpviewer_keywords:
- CSliderCtrl class [MFC], methods
- slider controls [MFC], member functions
ms.assetid: dbde49ee-7306-4d14-a6ce-d09aa198178f
ms.openlocfilehash: 25414b1d98c87c67c1dc8e13bb44bdc25869db94
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50472654"
---
# <a name="slider-control-member-functions"></a>Funciones miembro de control deslizante

Una aplicación puede llamar el control deslizante de las funciones de miembro del control para recuperar información sobre el control deslizante ([CSliderCtrl](../mfc/reference/csliderctrl-class.md)) y cambiar sus características.

Para recuperar la posición del control deslizante (es decir, el valor que el usuario ha elegido), use el [GetPos](../mfc/reference/csliderctrl-class.md#getpos) función miembro. Para establecer la posición del control deslizante, use el [SetPos](../mfc/reference/csliderctrl-class.md#setpos) función miembro. En cualquier momento puede usar el `VerifyPos` función miembro para asegurarse de que el control deslizante está entre los valores mínimo y máximos.

El intervalo de un control deslizante es el conjunto de valores contiguos que puede representar el control deslizante. La mayoría de las aplicaciones utiliza la [SetRange](../mfc/reference/csliderctrl-class.md#setrange) función miembro para establecer el intervalo de un control deslizante cuando se crea en primer lugar. Las aplicaciones pueden modificar dinámicamente el intervalo de una vez creado el control deslizante mediante el uso de la [funciones miembro SetRangeMax](../mfc/reference/csliderctrl-class.md#setrangemax) y [SetRangeMin](../mfc/reference/csliderctrl-class.md#setrangemin) funciones miembro. Una aplicación que permite que el intervalo que se puede cambiar dinámicamente normalmente recupera los valores del intervalo final cuando el usuario ha terminado de trabajar con el control deslizante. Para recuperar estos valores, use el [GetRange](../mfc/reference/csliderctrl-class.md#getrange), [GetRangeMax](../mfc/reference/csliderctrl-class.md#getrangemax), y [GetRangeMin](../mfc/reference/csliderctrl-class.md#getrangemin) funciones miembro.

Una aplicación puede usar el estilo TBS_AUTOTICKS para tener marcas de graduación de un control deslizante muestra automáticamente. Si una aplicación necesita controlar la posición o la frecuencia de las marcas de graduación, sin embargo, se puede usar una serie de funciones de miembro.

Para establecer la posición de una marca de graduación, una aplicación puede utilizar el [SetTic](../mfc/reference/csliderctrl-class.md#settic) función miembro. El [SetTicFreq](../mfc/reference/csliderctrl-class.md#setticfreq) función miembro permite que una aplicación establecer las marcas que aparecen a intervalos regulares en el intervalo del control deslizante de marcas de graduación. Por ejemplo, la aplicación puede usar esta función miembro para mostrar sólo 10 marcas de graduación de un intervalo de 1 a 100.

Para recuperar el índice en el intervalo correspondiente a una marca de graduación, use el [función miembro GetTic](../mfc/reference/csliderctrl-class.md#gettic) función miembro. El [función miembro GetTicArray](../mfc/reference/csliderctrl-class.md#getticarray) función miembro recupera una matriz de estos índices. Para recuperar la posición de una marca de graduación, en coordenadas de cliente, use el [función miembro GetTicPos](../mfc/reference/csliderctrl-class.md#getticpos) función miembro. Una aplicación puede recuperar el número de marcas de graduación mediante la [función miembro GetNumTics](../mfc/reference/csliderctrl-class.md#getnumtics) función miembro.

El [función miembro ClearTics](../mfc/reference/csliderctrl-class.md#cleartics) función miembro quita todas las marcas de graduación de un control deslizante.

Tamaño de la línea de un control deslizante determina hasta qué punto se mueve el control deslizante cuando una aplicación recibe un mensaje de notificación TB_LINEDOWN o TB_LINEUP. De forma similar, el tamaño de página determina la respuesta a los mensajes de notificación TB_PAGEDOWN y TB_PAGEUP. Las aplicaciones pueden recuperar y establecer los valores de tamaño de línea y de página mediante el [funciones miembro GetLineSize](../mfc/reference/csliderctrl-class.md#getlinesize), [SetLineSize](../mfc/reference/csliderctrl-class.md#setlinesize), [GetPageSize](../mfc/reference/csliderctrl-class.md#getpagesize), y [SetPageSize](../mfc/reference/csliderctrl-class.md#setpagesize) funciones miembro.

Una aplicación puede utilizar las funciones miembro para recuperar las dimensiones de un control deslizante. El [función miembro GetThumbRect](../mfc/reference/csliderctrl-class.md#getthumbrect) función miembro recupera el rectángulo delimitador para el control deslizante. El [función miembro GetChannelRect](../mfc/reference/csliderctrl-class.md#getchannelrect) función miembro recupera el rectángulo delimitador para el canal del control deslizante. (El canal es el área sobre la que se mueve el control deslizante y que contiene la parte resaltada cuando se selecciona un intervalo).

Si un control deslizante tiene el estilo TBS_ENABLESELRANGE, el usuario puede seleccionar un intervalo de valores contiguos de él. Un número de funciones miembro permite ajustar dinámicamente el intervalo de selección. El [SetSelection](../mfc/reference/csliderctrl-class.md#setselection) función miembro establece iniciales y finales de las posiciones de una selección. Cuando el usuario ha terminado de establecer un intervalo de selección, una aplicación puede recuperar la configuración mediante el [función miembro GetSelection](../mfc/reference/csliderctrl-class.md#getselection) función miembro. Para borrar la selección de un usuario, use el [función miembro ClearSel](../mfc/reference/csliderctrl-class.md#clearsel) función miembro.

## <a name="see-also"></a>Vea también

[Uso de CSliderCtrl](../mfc/using-csliderctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)

