---
title: 'Cómo: Implementar el seguimiento en el código'
ms.date: 11/04/2016
helpviewer_keywords:
- CRectTracker class [MFC], implementing trackers
ms.assetid: baaeca2c-5114-485f-bf58-8807db1bc973
ms.openlocfilehash: 3d71543261021c7e20041d317401b7b7b8d0616e
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621667"
---
# <a name="how-to-implement-tracking-in-your-code"></a>Cómo: Implementar el seguimiento en el código

Para realizar el seguimiento de un elemento OLE, debe controlar ciertos eventos relacionados con el elemento, como hacer clic en el elemento o actualizar la vista del documento. En todos los casos, es suficiente declarar un objeto [CRectTracker](reference/crecttracker-class.md) temporal y manipular el elemento por medio de este objeto.

Cuando un usuario selecciona un elemento o inserta un objeto con un comando de menú, debe inicializar el rastreador con los estilos adecuados para representar el estado del elemento OLE. En la tabla siguiente se describen las convenciones utilizadas por el ejemplo OCLIENT. Para obtener más información sobre estos estilos, vea `CRectTracker` .

### <a name="container-styles-and-states-of-the-ole-item"></a>Estilos y Estados del contenedor del elemento OLE

|Estilo mostrado|Estado del elemento OLE|
|---------------------|-----------------------|
|Borde punteado|El elemento está vinculado|
|Borde sólido|El elemento está incrustado en el documento|
|Controladores de tamaño|El elemento está seleccionado actualmente|
|Borde sombreado|El elemento está activo actualmente en contexto|
|Elemento de superposición del modelo de sombreado|El servidor del elemento está abierto|

Puede controlar esta inicialización fácilmente mediante un procedimiento que comprueba el estado del elemento OLE y establece los estilos adecuados. La `SetupTracker` función que se encuentra en el ejemplo OCLIENT muestra la inicialización del seguimiento. Los parámetros de esta función son la dirección del seguimiento, *pTracker*; un puntero al elemento de cliente relacionado con el rastreador, *pItem*; y un puntero a un rectángulo, *pTrueRect*. Para obtener un ejemplo más completo de esta función, vea el ejemplo de OLE de MFC [OCLIENT](../overview/visual-cpp-samples.md).

En el ejemplo de código **SetupTracker** se presenta una sola función; las líneas de la función se intercalan con la explicación de las características de la función:

[!code-cpp[NVC_MFCOClient#1](codesnippet/cpp/how-to-implement-tracking-in-your-code_1.cpp)]

El rastreador se inicializa estableciendo el tamaño mínimo y borrando el estilo del seguimiento.

[!code-cpp[NVC_MFCOClient#2](codesnippet/cpp/how-to-implement-tracking-in-your-code_2.cpp)]

Las siguientes líneas comprueban si el elemento está seleccionado actualmente y si el elemento está vinculado al documento o incrustado en él. Los controladores de tamaño que se encuentran en el interior del borde se agregan al estilo, lo que indica que el elemento está seleccionado actualmente. Si el elemento está vinculado al documento, se utiliza el estilo de borde punteado. Si el elemento está incrustado, se utiliza un borde sólido.

[!code-cpp[NVC_MFCOClient#3](codesnippet/cpp/how-to-implement-tracking-in-your-code_3.cpp)]

El código siguiente superpone el elemento con un patrón sombreado si el elemento está abierto actualmente.

[!code-cpp[NVC_MFCOClient#4](codesnippet/cpp/how-to-implement-tracking-in-your-code_4.cpp)]

Después, puede llamar a esta función cada vez que se tenga que mostrar el Rastreador. Por ejemplo, llame a esta función desde la `OnDraw` función de la clase de vista. Esto actualiza la apariencia del seguimiento cada vez que se vuelve a dibujar la vista. Para obtener un ejemplo completo, vea la `CMainView::OnDraw` función del ejemplo de OLE de MFC [OCLIENT](../overview/visual-cpp-samples.md).

En la aplicación, se producirán los eventos que requieren código de seguimiento, como el cambio de tamaño, el movimiento o la detección de aciertos. Normalmente, estas acciones indican que se está intentando capturar o trasladar el elemento. En estos casos, tendrá que decidir qué se ha capturado: un controlador de tamaño o una parte del borde entre los controladores de tamaño. El `OnLButtonDown` controlador de mensajes es un buen lugar para probar la posición del mouse con respecto al elemento. Realice una llamada a `CRectTracker::HitTest` . Si la prueba devuelve algo más `CRectTracker::hitOutside` , el tamaño del elemento se cambia o se mueve. Por lo tanto, debe hacer una llamada a la `Track` función miembro. Vea la `CMainView::OnLButtonDown` función que se encuentra en el ejemplo [OCLIENT](../overview/visual-cpp-samples.md) de OLE de MFC para obtener un ejemplo completo.

La `CRectTracker` clase proporciona varias formas de cursor diferentes que se usan para indicar si se está llevando a cabo una operación de movimiento, cambio de tamaño o arrastre. Para controlar este evento, compruebe si está seleccionado el elemento que se encuentra debajo del mouse. Si es así, realice una llamada a `CRectTracker::SetCursor` o llame al controlador predeterminado. El ejemplo siguiente es del ejemplo de OLE de MFC [OCLIENT](../overview/visual-cpp-samples.md):

[!code-cpp[NVC_MFCOClient#5](codesnippet/cpp/how-to-implement-tracking-in-your-code_5.cpp)]

## <a name="see-also"></a>Consulte también

[Seguimiento: Implementar el seguimiento en la aplicación OLE](trackers-implementing-trackers-in-your-ole-application.md)
