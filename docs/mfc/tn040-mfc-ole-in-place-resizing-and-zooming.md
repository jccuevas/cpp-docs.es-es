---
title: "TN040: MFC OLE en contexto de cambio de tamaño y zoom | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.ole
dev_langs:
- C++
helpviewer_keywords:
- resizing in-place
- TN040
- zooming and in-place activation
- in-place activation, zooming and resizing
ms.assetid: 4d7859bd-0b2e-4254-be62-2735cecf02c6
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b1113da01e58ec00cd4420aab4424b1c20e127e0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="tn040-mfcole-in-place-resizing-and-zooming"></a>TN040: Cambio de tamaño y zoom en contexto de MFC/OLE
> [!NOTE]
>  La nota técnica siguiente no se ha actualizado desde que se incluyó por primera vez en la documentación en línea. Como resultado, algunos procedimientos y temas podrían estar obsoletos o ser incorrectos. Para obtener información más reciente, se recomienda buscar el tema de interés en el índice de la documentación en línea.  
  
 Esta nota tratará los problemas relativos a la edición en contexto y cómo un servidor debe realizar zoom correcta y el cambio de tamaño en contexto. Con la activación en contexto, el concepto WYSIWYG adopta un paso más allá de ese contenedores y servidores cooperarán entre sí y, en particular interpretan la especificación de OLE en gran parte de la misma manera.  
  
 Debido a la estrecha interacción entre un contenedor y un servidor que admita la activación en contexto hay un número de las expectativas del usuario final que se debe mantener:  
  
-   La pantalla de presentación (el metarchivo dibujado el `COleServerItem::OnDraw` invalidar) debe ser exactamente el mismo que cuando se dibuja para su edición (salvo que herramientas de edición no están visibles).  
  
-   Cuando se amplía el contenedor, la ventana de servidor debe demasiado!  
  
-   El contenedor y el servidor deben mostrar los objetos para poder editarlo mediante las mismas métricas. Esto significa que se utiliza un modo de asignación en función del número de *lógico* píxeles por pulgada, no físicos píxeles por pulgada, al representar en el dispositivo de pantalla.  
  
> [!NOTE]
>  Dado que la activación en contexto solo se aplica a los elementos que se incrustan (no vinculados), solo zoom se aplica a objetos incrustados. Verá las API en ambos `COleServerDoc` y `COleServerItem` que se usan para ajustar el zoom. El motivo de este dichotomy es que sólo las funciones que son válidas para los elementos vinculados e incrustados son en `COleServerItem` (Esto le permite tener una implementación común) y funciones que solo son válidas para los objetos incrustados se encuentran en el `COleServerDoc` clase (desde la perspectiva del servidor, es el `document` incrustados).  
  
 La mayor parte de la carga se coloca en el implementador de servidor, en que el servidor debe tener en cuenta el factor de zoom del contenedor y modificar su edición interfaz según corresponda. Pero ¿cómo se determina el factor de zoom que está usando el contenedor en el servidor  
  
## <a name="mfc-support-for-zooming"></a>Compatibilidad con MFC para ajustar el zoom  
 Se puede determinar el factor de zoom actual mediante una llamada a `COleServerDoc::GetZoomFactor`. Si se llama cuando el documento no está activo en contexto producirá siempre un factor de zoom del 100% (o proporción 1:1). Lo llaman mientras activo en contexto puede devolver un valor distinto de 100%.  
  
 Para obtener un ejemplo de zoom correctamente, vea el ejemplo de MFC OLE [HIERSVR](../visual-cpp-samples.md). Acercar HIERSVR resulta complicada por el hecho de que se muestre texto y texto, por lo general, no se ajusta de forma lineal (sugerencias, convenciones tipográficas, diseño, alto y el ancho todos complicar la cuestión). Aún así, HIERSVR es una referencia razonable para implementar zoom correctamente y, por lo que es el Tutorial de MFC [SCRIBBLE](../visual-cpp-samples.md) (paso 7).  
  
 `COleServerDoc::GetZoomFactor`Determina el factor de zoom en función de un número de diferentes métricas disponibles desde el contenedor o desde la implementación de su `COleServerItem` y `COleServerDoc` clases. En resumen, el factor de zoom actual viene determinado por la fórmula siguiente:  
  
```  
Position Rectangle (PR) / Container Extent (CE)  
```  
  
 El rectángulo de posición está determinado por el contenedor. Se devuelve al servidor durante la activación en contexto al `COleClientItem::OnGetItemPosition` se llama y se actualiza cuando el contenedor llama el servidor `COleServerDoc::OnSetItemRects` (con una llamada a `COleClientItem::SetItemRects`).  
  
 La extensión de contenedor es ligeramente más compleja para calcular. Si el contenedor se denomina `COleServerItem::OnSetExtent` (con una llamada a `COleClientItem::SetExtent`), a continuación, la extensión de contenedor es este valor convertido en píxeles en función del número de píxeles por pulgada lógica. Si el contenedor no llamado SetExtent (que suele ser el caso), la extensión de contenedor es el tamaño devuelto desde `COleServerItem::OnGetExtent`. Por lo tanto, si el contenedor no llamado SetExtent, el marco de trabajo se da por supuesto que si lo hiciera el contenedor habría lo han llamado con 100% de la extensión natural (el valor devuelto de **COleServerItem::GetExtent**). Expresado de otra forma, el marco de trabajo, se da por supuesto que el contenedor muestra 100% (no más, pero no menos) del elemento.  
  
 Es importante tener en cuenta que aunque `COleServerItem::OnSetExtent` y `COleServerItem::OnGetExtent` tienen nombres similares, no controlará el mismo atributo del elemento. `OnSetExtent`se llama para comunicar el servidor de la cantidad del objeto está visible en el contenedor (sin tener en cuenta el factor de zoom) y `OnGetExtent` se llama por el contenedor para determinar el tamaño ideal del objeto.  
  
 Si se observan en cada una de las API implicadas, puede obtener una imagen más clara:  
  
## <a name="coleserveritemongetextent"></a>COleServerItem::OnGetExtent  
 Esta función debe devolver el "tamaño natural" en unidades HIMETRIC del elemento. Es la mejor manera de pensar en el "tamaño natural" definir como el tamaño, podría aparecer cuando se imprima. El tamaño devuelto aquí es constante para un elemento determinado un contenido (muy como metarchivo, que es una constante para un elemento determinado). Este tamaño no cambia cuando el zoom se aplica al elemento. Normalmente no cambia cuando el contenedor da más o menos espacio en el elemento mediante una llamada a `OnSetExtent`. Un ejemplo de un cambio podría ser un editor de texto simple con ninguna capacidad de "margen" que ajusta el texto en función de la última extensión enviada por el contenedor. Si cambia un servidor, el servidor probablemente debe establecer el valor del bit en el registro del sistema OLEMISC_RECOMPOSEONRESIZE (vea la documentación de SDK de OLE para obtener más información sobre esta opción).  
  
## <a name="coleserveritemonsetextent"></a>COleServerItem::OnSetExtent  
 Esta función se invoca cuando el contenedor de muestra "más" del objeto. Mayoría de los contenedores no llamará a este en absoluto. La implementación predeterminada almacena el último valor recibido desde el contenedor en 'm_sizeExtent', que se usa en `COleServerDoc::GetZoomFactor` al calcular el valor de extensión de contenedor se ha descrito anteriormente.  
  
## <a name="coleserverdoconsetitemrects"></a>COleServerDoc::OnSetItemRects  
 Esta función se invoca cuando el documento activo en contexto. Se llama cuando el contenedor actualiza la posición del elemento o el recorte que se aplica al elemento. El rectángulo de posición, como se dijo anteriormente, proporciona el numerador para el cálculo del factor de zoom. Puede solicitar un servidor que puede cambiar la posición de los elementos mediante una llamada a `COleServerDoc::RequestPositionChange`. El contenedor puede o no puede responder a esta solicitud mediante una llamada a `OnSetItemRects` (con una llamada a **COleServerItem::SetItemRects**).  
  
## <a name="coleserverdocondraw"></a>COleServerDoc::OnDraw  
 Es importante tener en cuenta que el metarchivo creado mediante la invalidación de `COleServerItem::OnDraw` produce exactamente el mismo metarchivo, con independencia del factor de zoom actual. El contenedor escalará el metarchivo según corresponda. Se trata de una diferencia importante entre la vista `OnDraw` y el elemento de servidor `OnDraw`. Los identificadores de vista zoom, el elemento simplemente crea un *puede acercar* Metarchivo y deja hasta el contenedor para hacer el zoom adecuado.  
  
 La mejor manera de asegurarse de que el servidor se comporta correctamente consiste en usar la implementación de `COleServerDoc::GetZoomFactor` si el documento está activo en contexto.  
  
## <a name="mfc-support-for-in-place-resizing"></a>Compatibilidad con MFC para cambiar el tamaño en contexto  
 MFC implementa por completo la interfaz de cambio de tamaño en contexto como se describe en la especificación de OLE 2. La interfaz de usuario es compatible con la `COleResizeBar` de la clase, un mensaje personalizado **WM_SIZECHILD**y un tratamiento especial de este mensaje en `COleIPFrameWnd`.  
  
 Puede que desee implementar un tratamiento distinto de este mensaje a lo que se proporciona el marco de trabajo. Como se describió anteriormente, el marco de trabajo deja los resultados de cambio de tamaño vigentes hasta el contenedor, el servidor responde a los cambios en el factor de zoom. Si el contenedor reacciona estableciendo tanto extensión de contenedor y el rectángulo de posición durante el procesamiento de su `COleClientItem::OnChangeItemPosition` (denominado como resultado de una llamada a `COleServerDoc::RequestPositionChange`), a continuación, se producirá el cambio de tamaño en contexto para mostrar "más o menos" del elemento en la edición ventana. Si el contenedor reacciona estableciendo simplemente el rectángulo de posición durante el procesamiento de `COleClientItem::OnChangeItemPosition`, cambiará el factor de zoom y el elemento se mostrará "acercado o alejar".  
  
 Un servidor puede controlar (hasta cierto punto), lo que sucede durante esta negociación. Por ejemplo, una hoja de cálculo, podría decidir mostrar más o menos celdas cuando el usuario cambia el tamaño de la ventana mientras se edita el elemento de contexto. Un procesador de textos podría optar por cambiar los márgenes de página"" para que sean la misma que la ventana y ajustar el texto en el margen nuevo. Implementan servidores esto cambiando la extensión natural (el tamaño devuelto desde `COleServerItem::OnGetExtent`) cuando se realiza el cambio de tamaño. Esto hará que el rectángulo de posición y la extensión de contenedor que se va a cambiar en la misma cantidad, lo que produce el mismo factor de zoom, pero un mayor o menor área de visualización. Además, más o menos del documento estará visible en el metarchivo generado por `OnDraw`. En este caso, el propio documento cambia cuando el usuario cambia el tamaño del elemento, en lugar de simplemente el área de visualización.  
  
 Puede implementar el cambio de tamaño personalizado y seguir aprovechando la interfaz de usuario proporcionada por `COleResizeBar` invalidando el **WM_SIZECHILD** el mensaje en su `COleIPFrameWnd` clase. Para obtener más información sobre las características específicas de **WM_SIZECHILD**, consulte [Nota técnica 24](../mfc/tn024-mfc-defined-messages-and-resources.md).  
  
## <a name="see-also"></a>Vea también  
 [Notas técnicas por número](../mfc/technical-notes-by-number.md)   
 [Notas técnicas por categoría](../mfc/technical-notes-by-category.md)

