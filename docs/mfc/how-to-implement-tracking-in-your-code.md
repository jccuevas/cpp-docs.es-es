---
title: Filtrar Implementar el seguimiento en el código
ms.date: 11/04/2016
helpviewer_keywords:
- CRectTracker class [MFC], implementing trackers
ms.assetid: baaeca2c-5114-485f-bf58-8807db1bc973
ms.openlocfilehash: af8e1b72bde268a15012515065853daa617936e4
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57283987"
---
# <a name="how-to-implement-tracking-in-your-code"></a>Filtrar Implementar el seguimiento en el código

Para realizar un seguimiento de un elemento OLE, debe controlar ciertos eventos relacionados con el elemento, por ejemplo, al hacer clic en el elemento o actualizar la vista del documento. En todos los casos, es suficiente declarar un archivo temporal [CRectTracker](../mfc/reference/crecttracker-class.md) de objetos y manipular el elemento mediante este objeto.

Cuando un usuario selecciona un elemento o inserta un objeto con un comando de menú, debe inicializar el seguimiento de los estilos adecuados para representar el estado del elemento OLE. En la tabla siguiente se describe las convenciones utilizadas en el ejemplo OCLIENT. Para obtener más información sobre estos estilos, consulte `CRectTracker`.

### <a name="container-styles-and-states-of-the-ole-item"></a>Estilos de contenedor y los Estados del elemento OLE

|Estilo de muestra|Estado del elemento OLE|
|---------------------|-----------------------|
|Borde con puntos|Elemento está vinculado|
|Borde grueso|Elemento que está incrustado en el documento|
|Controladores de tamaño|Elemento actualmente seleccionado|
|Borde sombreado|Elemento está activo actualmente en el contexto|
|Elemento de superposiciones de patrón de sombreado|El servidor del elemento está abierto|

Puede controlar fácilmente esta inicialización mediante un procedimiento que comprueba el estado del elemento OLE y establece los estilos apropiados. El `SetupTracker` función se encuentra en el ejemplo OCLIENT muestra la inicialización de la herramienta de seguimiento. Los parámetros para esta función son la dirección de la herramienta de seguimiento, *pTrueRect*; un puntero al elemento de cliente que está relacionado con la herramienta de seguimiento, *pItem*; y un puntero a un rectángulo, *pTrueRect* . Para obtener un ejemplo más completo de esta función, vea el ejemplo OLE de MFC [OCLIENT](../visual-cpp-samples.md).

El **SetupTracker** código de ejemplo presenta una sola función; líneas de la función se intercalan con análisis de las características de la función:

[!code-cpp[NVC_MFCOClient#1](../mfc/codesnippet/cpp/how-to-implement-tracking-in-your-code_1.cpp)]

Se ha inicializado el seguimiento estableciendo el tamaño mínimo y borrar el estilo de la herramienta de seguimiento.

[!code-cpp[NVC_MFCOClient#2](../mfc/codesnippet/cpp/how-to-implement-tracking-in-your-code_2.cpp)]

Comprueban las siguientes líneas para ver si el elemento está seleccionado actualmente y si el elemento está vinculado al documento o incrustado en él. Controladores de tamaño que se encuentra en el interior del borde se agregan al estilo, que indica que el elemento está seleccionado actualmente. Si el elemento está vinculado a su documento, se usa el estilo de borde con puntos. Borde grueso se utiliza si se incrusta el elemento.

[!code-cpp[NVC_MFCOClient#3](../mfc/codesnippet/cpp/how-to-implement-tracking-in-your-code_3.cpp)]

Abra el elemento con un patrón de sombreado si el elemento está actualmente de las superposiciones de código siguiente.

[!code-cpp[NVC_MFCOClient#4](../mfc/codesnippet/cpp/how-to-implement-tracking-in-your-code_4.cpp)]

A continuación, puede llamar a esta función siempre tiene la herramienta de seguimiento que se muestran. Por ejemplo, llamar a esta función desde el `OnDraw` función de la clase de vista. Esto actualiza la apariencia de la herramienta de seguimiento cada vez que se vuelva a dibujar la vista. Para obtener un ejemplo completo, vea el `CMainView::OnDraw` función de la muestra de OLE de MFC [OCLIENT](../visual-cpp-samples.md).

En la aplicación, los eventos que requieren código de seguimiento, como la detección de cambio de tamaño, mover o visitas, se producirán. Estas acciones suelen indican que se está realizando un intento señalar o mover el elemento. En estos casos, deberá decidir qué se ha señalado: un controlador de tamaño o una parte del borde entre controladores de tamaño. El `OnLButtonDown` el controlador de mensajes es un buen lugar para probar la posición del puntero del mouse en relación con el elemento. Realizar una llamada a `CRectTracker::HitTest`. Si la prueba devuelve algo más que `CRectTracker::hitOutside`, el elemento es el que se va a cambiar el tamaño o mover. Por lo tanto, debe realizar una llamada a la `Track` función miembro. Consulte la `CMainView::OnLButtonDown` función se encuentra en el ejemplo OLE de MFC [OCLIENT](../visual-cpp-samples.md) para obtener un ejemplo completo.

La `CRectTracker` clase proporciona varias formas de cursor diferente que se utiliza para indicar si un movimiento, cambiar el tamaño o arrastre está teniendo lugar la operación. Para controlar este evento, compruebe si se selecciona el elemento situado bajo el mouse. Si es así, realizar una llamada a `CRectTracker::SetCursor`, o llame al controlador predeterminado. El ejemplo siguiente es el ejemplo OLE de MFC [OCLIENT](../visual-cpp-samples.md):

[!code-cpp[NVC_MFCOClient#5](../mfc/codesnippet/cpp/how-to-implement-tracking-in-your-code_5.cpp)]

## <a name="see-also"></a>Vea también

[Seguimiento: Implementar el seguimiento en una aplicación OLE](../mfc/trackers-implementing-trackers-in-your-ole-application.md)
