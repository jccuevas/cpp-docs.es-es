---
title: 'TN040: Cambio de tamaño de MFC / OLE en contexto y zoom'
ms.date: 11/04/2016
f1_keywords:
- vc.mfc.ole
helpviewer_keywords:
- resizing in-place
- TN040
- zooming and in-place activation
- in-place activation, zooming and resizing
ms.assetid: 4d7859bd-0b2e-4254-be62-2735cecf02c6
ms.openlocfilehash: c2cb25388184ac969bec7c01d8077a458c03a03a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62305468"
---
# <a name="tn040-mfcole-in-place-resizing-and-zooming"></a>TN040: Cambio de tamaño de MFC/OLE en contexto y zoom

> [!NOTE]
>  La nota técnica siguiente no se ha actualizado desde que se incluyó por primera vez en la documentación en línea. Como resultado, algunos procedimientos y temas podrían estar obsoletos o ser incorrectos. Para obtener información más reciente, se recomienda buscar el tema de interés en el índice de la documentación en línea.

Esta nota tratan los problemas relativos a la edición en contexto y cómo un servidor debe realizar zoom correcta y el cambio de tamaño en contexto. Con la activación en contexto, el concepto de WYSIWYG quedo un paso más allá en que los contenedores y servidores cooperarán entre sí y, en particular al interpretar la especificación de OLE en gran parte del mismo modo.

Debido a la interacción entre un contenedor y un servidor compatible con la activación en contexto cerrar hay una serie de las expectativas del usuario final que se debe mantener:

- La pantalla de presentación (metarchivo dibujado la `COleServerItem::OnDraw` invalidar) debe exactamente la misma apariencia que cuando se dibuja para su edición (salvo que no están visibles las herramientas de edición).

- Cuando se amplía el contenedor, la ventana del servidor debe también!

- El contenedor y el servidor deben mostrar los objetos para la edición con las mismas métricas. Esto implica el uso de un modo de asignación en función del número de *lógico* píxeles por pulgada, no físicos píxeles por pulgada, al representar en el dispositivo de pantalla.

> [!NOTE]
>  Dado que la activación en contexto solo se aplica a los elementos que se incrustan (no vinculados), solo zoom se aplica a objetos incrustados. Verá las API en ambos `COleServerDoc` y `COleServerItem` que se usan para ajustar el zoom. El motivo de este dichotomy es que solo las funciones que son válidas para los elementos vinculados e incrustados están en `COleServerItem` (Esto le permite tener una implementación común) y las funciones que solo son válidas para los objetos incrustados se encuentran en el `COleServerDoc` clase (desde la perspectiva del servidor, es el **documento** incrustados).

La mayoría de la carga se coloca en el implementador de servidor en que el servidor debe tener en cuenta el factor de zoom del contenedor y modificar su interfaz de edición según corresponda. Pero ¿cómo se determina el factor de zoom que usa el contenedor en el servidor

## <a name="mfc-support-for-zooming"></a>Compatibilidad con MFC para ajustar el zoom

Se puede determinar el factor de zoom actual mediante una llamada a `COleServerDoc::GetZoomFactor`. Si se llama cuando el documento no está activo en contexto producirá siempre un factor de zoom del 100% (o la relación 1:1). Llamarlo mientras activo en contexto puede devolver un valor distinto de 100%.

Para obtener un ejemplo de zoom correctamente, vea el ejemplo OLE de MFC [HIERSVR](../overview/visual-cpp-samples.md). Acercar HIERSVR resulta complicada por el hecho de que muestra el texto y texto, en general, no se escala de forma lineal (sugerencias, convenciones tipográficas, diseño anchos y altos todas complicar el asunto). Aun así, HIERSVR es una referencia razonable para implementar correctamente zoom, y por lo que es el Tutorial de MFC [SCRIBBLE](../overview/visual-cpp-samples.md) (paso 7).

`COleServerDoc::GetZoomFactor` Determina el factor de zoom según una serie de diferentes métricas disponibles del contenedor o desde la implementación de su `COleServerItem` y `COleServerDoc` clases. En resumen, el factor de zoom actual se determina mediante la fórmula siguiente:

```
Position Rectangle (PR) / Container Extent (CE)
```

El rectángulo de posición viene determinada por el contenedor. Se devuelve al servidor durante la activación en contexto cuando `COleClientItem::OnGetItemPosition` se denomina y se actualiza cuando el contenedor llama el servidor `COleServerDoc::OnSetItemRects` (con una llamada a `COleClientItem::SetItemRects`).

La extensión de contenedor es un poco más difícil de calcular. Si el contenedor se denomina `COleServerItem::OnSetExtent` (con una llamada a `COleClientItem::SetExtent`), a continuación, la extensión de contenedor es este valor se convierte a píxeles en función del número de píxeles por pulgada lógica. Si el contenedor no llamado SetExtent (que suele ser el caso), la extensión de contenedor es el tamaño devuelto de `COleServerItem::OnGetExtent`. Por lo tanto, si el contenedor no llamado SetExtent, el marco de trabajo se supone que si lo hiciera el contenedor habría llama, con 100% de la extensión natural (el valor devuelto de `COleServerItem::GetExtent`). Expresado de otra forma, el marco de trabajo, se da por supuesto que el contenedor está mostrando 100% (no más, no hay menos) del elemento.

Es importante tener en cuenta que aunque `COleServerItem::OnSetExtent` y `COleServerItem::OnGetExtent` tienen nombres similares, no manipulan el mismo atributo del elemento. `OnSetExtent` se llama para que el servidor sepa cuánto del objeto está visible en el contenedor (sin tener en cuenta el factor de zoom) y `OnGetExtent` es llamado por el contenedor para determinar el tamaño ideal del objeto.

Si examina cada una de las API implicadas, puede obtener una imagen más clara:

## <a name="coleserveritemongetextent"></a>COleServerItem::OnGetExtent

Esta función debe devolver el "tamaño natural" en unidades HIMETRIC del elemento. Es la mejor manera de pensar en "tamaño natural" definirlo como el tamaño, puede aparecer cuando se imprima. El tamaño devuelto aquí es constante para un contenido de elemento en particular (muy similar a metarchivo, que es una constante para un elemento determinado). Este tamaño no cambia cuando el zoom se aplica al elemento. Normalmente, no cambia cuando el contenedor proporciona el elemento más o menos espacio mediante una llamada a `OnSetExtent`. Un ejemplo de un cambio podría ser de un editor de texto simple con ninguna funcionalidad de "margen" que ajusta el texto en función de la última extensión enviada por el contenedor. Si cambia un servidor, el servidor probablemente debe establecer el bit en el registro del sistema OLEMISC_RECOMPOSEONRESIZE (consulte la documentación del SDK de OLE para obtener más información sobre esta opción).

## <a name="coleserveritemonsetextent"></a>COleServerItem::OnSetExtent

Esta función se llama cuando el contenedor muestra "más o menos" del objeto. Mayoría de los contenedores no llamará a esto en absoluto. La implementación predeterminada almacena el último valor recibido desde el contenedor en 'm_sizeExtent', que se utiliza en `COleServerDoc::GetZoomFactor` al calcular el valor de la extensión de contenedor se ha descrito anteriormente.

## <a name="coleserverdoconsetitemrects"></a>COleServerDoc::OnSetItemRects

Esta función se invoca cuando el documento activo en contexto. Se llama cuando el contenedor actualiza la posición del elemento o el recorte aplicado al elemento. El rectángulo de posición, como se dijo anteriormente, proporciona el numerador para el cálculo del factor de zoom. Un servidor puede solicitar que se puede cambiar la posición del elemento mediante una llamada a `COleServerDoc::RequestPositionChange`. El contenedor puede o no puede responder a esta solicitud mediante una llamada a `OnSetItemRects` (con una llamada a `COleServerItem::SetItemRects`).

## <a name="coleserverdocondraw"></a>COleServerDoc::OnDraw

Es importante tener en cuenta que el metarchivo creado mediante la invalidación de `COleServerItem::OnDraw` produce exactamente el mismo metarchivo, sin tener en cuenta el factor de zoom actual. El contenedor escalará el metarchivo según corresponda. Se trata de una diferencia importante entre la vista `OnDraw` y el elemento de servidor `OnDraw`. Los controladores de vista de zoom, el elemento simplemente crea un *se puede acercar* Metarchivo y deja el contenedor para realizar la función de zoom adecuado.

La mejor manera de asegurarse de que el servidor se comporta correctamente es usar la implementación de `COleServerDoc::GetZoomFactor` si el documento está activo en contexto.

## <a name="mfc-support-for-in-place-resizing"></a>Compatibilidad de MFC con el cambio de tamaño en contexto

MFC totalmente implementa la interfaz de cambio de tamaño en contexto como se describe en la especificación de OLE 2. La interfaz de usuario es compatible con la `COleResizeBar` clase, un mensaje personalizado WM_SIZECHILD y un tratamiento especial de este mensaje en `COleIPFrameWnd`.

Desea implementar un tratamiento distinto de este mensaje de que la que proporciona el marco de trabajo. Como se describió anteriormente, el marco de trabajo deja los resultados de cambio de tamaño en contexto hasta el contenedor, el servidor responde al cambio en el factor de zoom. Si el contenedor reacciona estableciendo tanto extensión de contenedor y el rectángulo de posición durante el procesamiento de su `COleClientItem::OnChangeItemPosition` (llamado como resultado de una llamada a `COleServerDoc::RequestPositionChange`), a continuación, dará como resultado el cambio de tamaño en contexto que muestra "más o menos" del elemento en la edición ventana. Si el contenedor reacciona estableciendo el rectángulo de posición solo durante el procesamiento de `COleClientItem::OnChangeItemPosition`, cambiará el factor de zoom y el elemento se mostrará "se acerca o aleja."

Un servidor puede controlar (hasta cierto punto), lo que sucede durante esta negociación. Una hoja de cálculo, por ejemplo podrían optar por mostrar más o menos celdas cuando el usuario cambia el tamaño de la ventana mientras edita el elemento local. Un procesador de textos podría optar por cambiar los márgenes de página"" para que sean la misma que la ventana y ajustar el texto en el margen nuevo. Implementan servidores esto cambiando la extensión natural (el tamaño devuelto desde `COleServerItem::OnGetExtent`) cuando se realiza el cambio de tamaño. Esto hará que el rectángulo de posición y la extensión de contenedor para cambiar en la misma cantidad, lo que produce el mismo factor de zoom, pero un mayor o menor tamaño el área de visualización. Además, más o menos del documento será visible en el metarchivo generado por `OnDraw`. En este caso, el propio documento cambia cuando el usuario cambia el tamaño del elemento, en lugar de simplemente el área de visualización.

Puede implementar el cambio de tamaño personalizado y seguir aprovechando la interfaz de usuario proporcionada por `COleResizeBar` invalidando el mensaje WM_SIZECHILD en su `COleIPFrameWnd` clase. Para obtener más información sobre las características específicas de WM_SIZECHILD, consulte [Nota técnica 24](../mfc/tn024-mfc-defined-messages-and-resources.md).

## <a name="see-also"></a>Vea también

[Notas técnicas por número](../mfc/technical-notes-by-number.md)<br/>
[Notas técnicas por categoría](../mfc/technical-notes-by-category.md)
