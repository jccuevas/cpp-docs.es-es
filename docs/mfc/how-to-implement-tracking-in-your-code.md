---
title: 'Cómo: implementar el seguimiento en el código | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CRectTracker class [MFC], implementing trackers
ms.assetid: baaeca2c-5114-485f-bf58-8807db1bc973
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dc21369dd8d241bd00da2a0a8005c977094c3abf
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2018
ms.locfileid: "36932099"
---
# <a name="how-to-implement-tracking-in-your-code"></a>Cómo: Implementar el seguimiento en el código
Para realizar el seguimiento de un elemento OLE, debe controlar determinados eventos relacionados con el elemento, por ejemplo, al hacer clic en el elemento o actualizar la vista del documento. En todos los casos, es suficiente declarar un archivo temporal [CRectTracker](../mfc/reference/crecttracker-class.md) objeto y manipular el elemento mediante este objeto.  
  
 Cuando un usuario selecciona un elemento o inserta un objeto con un comando de menú, debe inicializar la herramienta de seguimiento con los estilos apropiados para representar el estado del elemento OLE. En la tabla siguiente se describe las convenciones usadas por el ejemplo OCLIENT. Para obtener más información sobre estos estilos, consulte `CRectTracker`.  
  
### <a name="container-styles-and-states-of-the-ole-item"></a>Estilos de contenedor y Estados del elemento OLE  
  
|Estilo mostrado|Estado del elemento OLE|  
|---------------------|-----------------------|  
|Borde con puntos|Elemento está vinculado|  
|Borde sólido|Elemento está incrustado en el documento|  
|Controladores de tamaño|Elemento está seleccionado actualmente|  
|Borde sombreado|Elemento está activo actualmente en el contexto|  
|Elemento de superposiciones de modelo de sombreado|El servidor del elemento está abierto|  
  
 Puede controlar fácilmente esta inicialización mediante un procedimiento que comprueba el estado del elemento OLE y establece los estilos apropiados. El `SetupTracker` función que se encuentra en el ejemplo OCLIENT muestra la inicialización de la herramienta de seguimiento. Los parámetros para esta función son la dirección de la herramienta de seguimiento, *pTrueRect*; un puntero al elemento de cliente que está relacionado con la herramienta de seguimiento, *pItem*; y un puntero a un rectángulo, *pTrueRect* . Para obtener un ejemplo más completo de esta función, vea el ejemplo de MFC OLE [OCLIENT](../visual-cpp-samples.md).  
  
 El **SetupTracker** ejemplo de código muestra una sola función; líneas de la función se alternan con comentarios acerca de las características de la función:  
  
 [!code-cpp[NVC_MFCOClient#1](../mfc/codesnippet/cpp/how-to-implement-tracking-in-your-code_1.cpp)]  
  
 La herramienta de seguimiento se inicializa estableciendo el tamaño mínimo y borrar el estilo de la herramienta de seguimiento.  
  
 [!code-cpp[NVC_MFCOClient#2](../mfc/codesnippet/cpp/how-to-implement-tracking-in-your-code_2.cpp)]  
  
 Comprueban las líneas siguientes para ver si el elemento está seleccionado actualmente y si el elemento está vinculado al documento o incrustado en el elemento. Controladores de tamaño que se encuentran en el interior del borde se agregan al estilo, que indica que el elemento está seleccionado actualmente. Si el elemento está vinculado al documento, se utiliza el estilo de borde con puntos. Si se inserta el elemento, se usa un borde sólido.  
  
 [!code-cpp[NVC_MFCOClient#3](../mfc/codesnippet/cpp/how-to-implement-tracking-in-your-code_3.cpp)]  
  
 Abra el elemento con un patrón sombreado si el elemento está actualmente de las superposiciones de código siguiente.  
  
 [!code-cpp[NVC_MFCOClient#4](../mfc/codesnippet/cpp/how-to-implement-tracking-in-your-code_4.cpp)]  
  
 A continuación, puede llamar a esta función siempre que la herramienta de seguimiento debe mostrarse. Por ejemplo, llamar a esta función desde la `OnDraw` función de la clase de vista. Esto actualiza la apariencia de la herramienta de seguimiento cada vez que se vuelve a dibujar la vista. Para obtener un ejemplo completo, vea el `CMainView::OnDraw` función de la muestra de OLE de MFC [OCLIENT](../visual-cpp-samples.md).  
  
 En la aplicación, se producen los eventos que requieren código de seguimiento, como la detección de cambio de tamaño, mover o visitas. Estas acciones suelen indican que se está realizando un intento para señalar o mover el elemento. En estos casos, debe decidir qué se ha señalado: un controlador de tamaño o en una parte del borde entre controladores de tamaño. El `OnLButtonDown` el controlador de mensajes es un buen lugar para probar la posición del mouse en relación con el elemento. Realizar una llamada a `CRectTracker::HitTest`. Si la prueba devuelve un valor distinto `CRectTracker::hitOutside`, el elemento es el que se va a cambiar de tamaño o mover. Por lo tanto, debe realizar una llamada a la `Track` función miembro. Consulte la `CMainView::OnLButtonDown` función ubicado en el ejemplo de MFC OLE [OCLIENT](../visual-cpp-samples.md) para obtener un ejemplo completo.  
  
 La `CRectTracker` clase proporciona varias formas de cursor diferente que se utiliza para indicar si una operación de traslado, cambiar el tamaño o arrastre tiene lugar en la operación. Para controlar este evento, compruebe si se selecciona el elemento situado bajo el mouse. Si es así, realizar una llamada a `CRectTracker::SetCursor`, o llame al controlador predeterminado. El ejemplo siguiente es el ejemplo OLE de MFC de [OCLIENT](../visual-cpp-samples.md):  
  
 [!code-cpp[NVC_MFCOClient#5](../mfc/codesnippet/cpp/how-to-implement-tracking-in-your-code_5.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [Seguimiento: Implementar el seguimiento en la aplicación OLE](../mfc/trackers-implementing-trackers-in-your-ole-application.md)

