---
title: 'TN040: Cambio de tamaño y zoom in situ MFC-OLE'
ms.date: 11/04/2016
helpviewer_keywords:
- resizing in-place
- TN040
- zooming and in-place activation
- in-place activation, zooming and resizing
ms.assetid: 4d7859bd-0b2e-4254-be62-2735cecf02c6
ms.openlocfilehash: 65f9ef04c9740e8e6f0a8e72d9d6c39008198755
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372165"
---
# <a name="tn040-mfcole-in-place-resizing-and-zooming"></a>TN040: Cambio de tamaño y zoom en contexto de MFC/OLE

> [!NOTE]
> La nota técnica siguiente no se ha actualizado desde que se incluyó por primera vez en la documentación en línea. Como resultado, algunos procedimientos y temas podrían estar obsoletos o ser incorrectos. Para obtener información más reciente, se recomienda buscar el tema de interés en el índice de la documentación en línea.

Esta nota discutirá los problemas relacionados con la edición in situ y cómo un servidor debe lograr el zoom correcto y el cambio de tamaño in situ. Con la activación in situ, el concepto WYSIWYG se da un paso más en que los contenedores y servidores cooperan entre sí, y en particular interpretan la especificación OLE de la misma manera.

Debido a la estrecha interacción entre un contenedor y un servidor que admite la activación in situ, hay una serie de expectativas del usuario final que se deben mantener:

- La visualización de la presentación `COleServerItem::OnDraw` (el metarchivo dibujado en la invalidación) debe tener exactamente el mismo aspecto que cuando se dibuja para su edición (excepto que las herramientas de edición no son visibles).

- Cuando el contenedor se acerca, la ventana del servidor también debería!

- Tanto el contenedor como el servidor deben mostrar objetos para editarlos con las mismas métricas. Esto significa utilizar un modo de asignación basado en el número de píxeles *lógicos* por pulgada, no píxeles físicos por pulgada, al renderizar en el dispositivo de visualización.

> [!NOTE]
> Dado que la activación in situ solo se aplica a los elementos incrustados (no vinculados), el zoom solo se aplica a los objetos incrustados. Verá las API en `COleServerDoc` `COleServerItem` ambos y que se utilizan para el zoom. La razón de esta dicotomía es que solo se encuentran `COleServerItem` en la `COleServerDoc` clase funciones que son válidas tanto para elementos vinculados como incrustados (esto permite tener una implementación común) y las funciones que solo son válidas para objetos incrustados (desde la perspectiva del servidor, es el **documento** incrustado).

La mayor parte de la carga se coloca en el implementador del servidor, ya que el servidor debe ser consciente del factor de zoom del contenedor y modificar su interfaz de edición según corresponda. Pero, ¿cómo determina el servidor el factor de zoom que utiliza el contenedor

## <a name="mfc-support-for-zooming"></a>Compatibilidad con MFC para zoom

El factor de zoom actual `COleServerDoc::GetZoomFactor`se puede determinar llamando a . Llamar a esto cuando el documento no está activo en el lugar siempre dará como resultado un factor de zoom del 100% (o una relación 1:1). Llamarlo mientras está activo en el lugar puede devolver algo distinto del 100%.

Para obtener un ejemplo de zoom correctamente, vea el ejemplo OLE de MFC [HIERSVR](../overview/visual-cpp-samples.md). El zoom en HIERSVR se complica por el hecho de que muestra texto, y el texto, en general, no se escala de forma lineal (pistas, convenciones tipográficas, anchos de diseño y alturas complican la materia). Aún así, HIERSVR es una referencia razonable para implementar el zoom correctamente, al igual que el Tutorial de MFC [SCRIBBLE](../overview/visual-cpp-samples.md) (paso 7).

`COleServerDoc::GetZoomFactor`determina el factor de zoom en función de una serie de métricas diferentes disponibles desde el contenedor o desde la implementación de su `COleServerItem` y `COleServerDoc` las clases. En resumen, el factor de zoom actual viene determinado por la siguiente fórmula:

```
Position Rectangle (PR) / Container Extent (CE)
```

El RECTANGLE DE POSITION viene determinado por el contenedor. Se devuelve al servidor durante la `COleClientItem::OnGetItemPosition` activación en contexto cuando se llama `COleServerDoc::OnSetItemRects` y se actualiza `COleClientItem::SetItemRects`cuando el contenedor llama al servidor (con una llamada a ).

La EXTENT DEL CONTENEDOR es un poco más compleja de calcular. Si el contenedor `COleServerItem::OnSetExtent` ha llamado `COleClientItem::SetExtent`(con una llamada a ), el CONTAINER EXTENT es este valor convertido en píxeles en función del número de píxeles por pulgada lógica. Si el contenedor no ha llamado SetExtent (que suele ser el `COleServerItem::OnGetExtent`caso), CONTAINER EXTENT es el tamaño devuelto desde . Por lo tanto, si el contenedor no ha llamado SetExtent, el marco de trabajo supone que si lo `COleServerItem::GetExtent`hizo el contenedor lo habría llamado con el 100% de la extensión natural (el valor devuelto desde ). Dicho de otra manera, el marco de trabajo supone que el contenedor muestra el 100% (ni más, ni menos) del elemento.

Es importante tener en `COleServerItem::OnSetExtent` `COleServerItem::OnGetExtent` cuenta que aunque y tienen nombres similares, no manipulan el mismo atributo del elemento. `OnSetExtent`se llama para que el servidor sepa cuánto del objeto está visible en `OnGetExtent` el contenedor (independientemente del factor de zoom) y es llamado por el contenedor para determinar el tamaño ideal del objeto.

Al examinar cada una de las API involucradas, puede obtener una imagen más clara:

## <a name="coleserveritemongetextent"></a>COleServerItem::OnGetExtent

Esta función debe devolver el "tamaño natural" en las unidades HIMETRIC del elemento. La mejor manera de pensar en el "tamaño natural" es definirlo como el tamaño que podría aparecer cuando se imprime. El tamaño devuelto aquí es constante para un contenido de elemento determinado (al igual que el metarchivo, que es constante para un elemento determinado). Este tamaño no cambia cuando se aplica el zoom al elemento. Normalmente no cambia cuando el contenedor da al `OnSetExtent`elemento más o menos espacio llamando a . Un ejemplo de un cambio podría ser el de un editor de texto simple sin capacidad de "margen" que ajusta el texto en función de la última extensión enviada por el contenedor. Si un servidor cambia, es probable que el servidor debería establecer el OLEMISC_RECOMPOSEONRESIZE bit en el registro del sistema (consulte la documentación del SDK de OLE para obtener más información sobre esta opción).

## <a name="coleserveritemonsetextent"></a>COleServerItem::OnSetExtent

Esta función se llama cuando el contenedor muestra "más o menos" del objeto. La mayoría de los contenedores no llamarán a esto en absoluto. La implementación predeterminada almacena el último valor recibido del contenedor `COleServerDoc::GetZoomFactor` en 'm_sizeExtent', que se utiliza al calcular el valor CONTAINER EXTENT descrito anteriormente.

## <a name="coleserverdoconsetitemrects"></a>COleServerDoc::OnSetItemRects

Esta función solo se llama cuando el documento está activo in situ. Se llama cuando el contenedor actualiza la posición del elemento o el recorte aplicado al elemento. POSITION RECTANGLE, como se ha explicado anteriormente, proporciona el numerador para el cálculo del factor de zoom. Un servidor puede solicitar que se `COleServerDoc::RequestPositionChange`cambie la posición del elemento llamando a . El contenedor puede o no responder `OnSetItemRects` a esta solicitud `COleServerItem::SetItemRects`llamando (con una llamada a ).

## <a name="coleserverdocondraw"></a>COleServerDoc::OnDraw

Es importante tener en cuenta que el `COleServerItem::OnDraw` metarchivo creado mediante la invalidación de produce exactamente el mismo metarchivo, independientemente del factor de zoom actual. El contenedor escalará el metarchivo según corresponda. Esta es una distinción importante `OnDraw` entre la vista `OnDraw`y la del elemento de servidor. La vista controla el zoom, el elemento simplemente crea un metarchivo *ampliable* y lo deja en el contenedor para hacer el zoom adecuado.

La mejor manera de asegurarse de que el servidor `COleServerDoc::GetZoomFactor` se comporta correctamente es usar la implementación de si el documento está activo en el lugar.

## <a name="mfc-support-for-in-place-resizing"></a>Compatibilidad con MFC para el cambio de tamaño in situ

MFC implementa completamente la interfaz de cambio de tamaño en el lugar como se describe en la especificación OLE 2. La interfaz de usuario `COleResizeBar` es compatible con la clase, un `COleIPFrameWnd`mensaje personalizado WM_SIZECHILD y un control especial de este mensaje en .

Es posible que desee implementar un control diferente de este mensaje que lo que proporciona el marco de trabajo. Como se ha descrito anteriormente, el marco deja los resultados del cambio de tamaño in situ hasta el contenedor: el servidor responde al cambio en el factor de zoom. Si el contenedor reacciona estableciendo el CONTAINER EXTENT y `COleClientItem::OnChangeItemPosition` POSITION RECTANGLE durante el procesamiento `COleServerDoc::RequestPositionChange`de su (llamado como resultado de una llamada a ) entonces el cambio de tamaño in situ dará como resultado mostrar "más o menos" del elemento en la ventana de edición. Si el contenedor reacciona simplemente configurando POSITION `COleClientItem::OnChangeItemPosition`RECTANGLE durante el procesamiento de , el factor de zoom cambiará y el elemento se mostrará "zoomed in or out."

Un servidor puede controlar (hasta cierto punto) lo que sucede durante esta negociación. Una hoja de cálculo, por ejemplo, podría optar por mostrar más o menos celdas cuando el usuario cambia el tamaño de la ventana mientras edita el elemento in situ. Un procesador de palabras podría optar por cambiar los "márgenes de página" para que sean los mismos que la ventana y volver a ajustar el texto al nuevo margen. Los servidores implementan esto cambiando la `COleServerItem::OnGetExtent`extensión natural (el tamaño devuelto desde ) cuando se realiza el cambio de tamaño. Esto hará que tanto POSITION RECTANGLE como CONTAINER EXTENT cambien en la misma cantidad, lo que resulta en el mismo factor de zoom, pero un área de visualización más grande o menor. Además, más o menos del documento será visible `OnDraw`en el metarchivo generado por . En este caso, el propio documento está cambiando cuando el usuario cambia el tamaño del elemento, en lugar de solo el área de visualización.

Puede implementar el cambio de tamaño personalizado y `COleResizeBar` aprovechar la interfaz `COleIPFrameWnd` de usuario proporcionada reemplazando el mensaje WM_SIZECHILD de la clase. Para obtener más información sobre los detalles de WM_SIZECHILD, véase la [Nota técnica 24](../mfc/tn024-mfc-defined-messages-and-resources.md).

## <a name="see-also"></a>Consulte también

[Notas técnicas por número](../mfc/technical-notes-by-number.md)<br/>
[Notas técnicas por categoría](../mfc/technical-notes-by-category.md)
