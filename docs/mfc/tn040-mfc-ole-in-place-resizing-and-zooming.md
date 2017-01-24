---
title: "TN040: Cambio de tama&#241;o y zoom en contexto de MFC/OLE | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.ole"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "activación en contexto, zoom y cambiar el tamaño"
  - "cambiar el tamaño en contexto"
  - "TN040"
  - "zoom y activación en contexto"
ms.assetid: 4d7859bd-0b2e-4254-be62-2735cecf02c6
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# TN040: Cambio de tama&#241;o y zoom en contexto de MFC/OLE
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  La nota técnica siguiente no se ha actualizado desde que se incluyó por primera vez en la documentación en línea.  Como resultado, algunos procedimientos y temas podrían estar obsoletos o ser incorrectos.  Para obtener información más reciente, se recomienda buscar el tema de interés en el índice de la documentación en línea.  
  
 Esta nota discutir los problemas relacionados con la edición en contexto y cómo un servidor debe lograr zoom correcto y cambiar el tamaño en contexto.  Con la activación en contexto, el concepto WYSIWYG es un paso más allá tomado de contenedores y servidores cooperan entre sí y, en particular interpreta la especificación OLE casi de la misma manera.  
  
 Debido a la interacción próxima entre un contenedor y un servidor que admiten la activación de contexto hay varias expectativas del usuario final que debe mantenerse:  
  
-   La pantalla de presentación \(el metarchivo dibujado en la invalidación de `COleServerItem::OnDraw` \) debe ser exactamente igual que cuando se dibuja para edición \(salvo que las herramientas de edición no está visible\).  
  
-   ¡Cuándo deben los controles de zoom del contenedor, la ventana de servidor también\!  
  
-   El contenedor y el servidor deben mostrar los objetos para editar utilizando la misma métricas.  Esto significa utilizando un modo de asignación según el número de píxeles por pulgada *lógicos* — píxeles por pulgada no físicos, al generar en el dispositivo de pantalla.  
  
> [!NOTE]
>  Dado que la activación en contexto sólo se aplica a los elementos se insertan que \(no vinculado\), zoom sólo se aplica a los objetos incrustados.  Se verán API en los `COleServerDoc` y `COleServerItem` que se utilizan para ampliarla.  El motivo de este dicotomía es que sólo las funciones que son válidas para los elementos vinculados y insertados están en `COleServerItem` \(esto le permite tener una implementación común\) y las funciones que sean válidos sólo para los objetos incrustados se encuentran en la clase de `COleServerDoc` \(desde la perspectiva del servidor, es `document` insertada\).  
  
 La mayor parte de la carga se coloca en el implementador del servidor, en que el servidor debe tener en cuenta el factor de zoom del contenedor y modificar su interfaz de edición según corresponda.  ¿Pero cómo el servidor determina el factor de zoom que el contenedor utiliza?  
  
## Compatibilidad con MFC para acercar  
 El factor de zoom actual se puede determinar mediante `COleServerDoc::GetZoomFactor`.  Llamar a este método cuando el documento no está activo en contexto producirá siempre un factor de zoom de 100% \(o la proporción de 1:1\).  Llamarlo mientras el activo en contexto puede devolver algo distinto de 100%.  
  
 Para obtener un ejemplo de zoom correctamente vea a MFC el ejemplo OLE [HIERSVR](../top/visual-cpp-samples.md).  Zoom en HIERSVR es complicado por el hecho de que muestra el texto, y el texto, no escala normalmente en un modo lineal \(las sugerencias, convenciones tipográficas, los anchos de diseño, y altos todos complican la planeación\).  No obstante, HIERSVR es una referencia razonable para implementar zoom correctamente y, por lo que es MFC [SCRIBBLE](../top/visual-cpp-samples.md) tutorial \(paso 7\).  
  
 `COleServerDoc::GetZoomFactor` determina el factor de zoom basado en varios distintas métricas disponibles del contenedor o la implementación de las clases de `COleServerItem` y de `COleServerDoc` .  En resumen, el factor de zoom actual está determinado por la siguiente fórmula:  
  
```  
Position Rectangle (PR) / Container Extent (CE)  
```  
  
 El RECTÁNGULO de la POSICIÓN viene determinado por el contenedor.  Se devuelve al servidor durante la activación de contexto cuando se llama a `COleClientItem::OnGetItemPosition` y se actualiza cuando el contenedor llama `COleServerDoc::OnSetItemRects` de servidor \(con una llamada a `COleClientItem::SetItemRects`\).  
  
 La EXTENSIÓN CONTAINER es algo más complicada calcular.  Si el contenedor se denomina `COleServerItem::OnSetExtent` \(con una llamada a `COleClientItem::SetExtent`\), la EXTENSIÓN CONTAINER es este valor convertido a píxeles basándose en el número de píxeles por pulgada lógica.  Si el contenedor no ha denominado SetExtent \(que suele ser el caso\), la EXTENSIÓN CONTAINER es el tamaño devuelto de `COleServerItem::OnGetExtent`.  Así, si el contenedor no ha denominado SetExtent, el marco supone que si hiciera el contenedor se habría denominado con 100% de la extensión natural \(el valor devuelto de **COleServerItem::GetExtent**\).  Dijo otra manera, el marco supone que el contenedor muestra 100% \(no más, menor\) del elemento.  
  
 Es importante tener en cuenta que aunque `COleServerItem::OnSetExtent` y `COleServerItem::OnGetExtent` tienen nombres similares, no manipular el mismo atributo del elemento.  `OnSetExtent` se denomina para permitir al servidor saber cuánto de objeto está visible en el contenedor \(independientemente del factor de zoom\) y `OnGetExtent` llama el contenedor para determinar el tamaño ideal del objeto.  
  
 Examinando cada una de las API completo, puede obtener una imagen más clara:  
  
## COleServerItem::OnGetExtent  
 Esta función debe devolver el “tamaño natural” en unidades de HIMETRIC del elemento.  La mejor manera de pensar en “tamaño natural” es definirlo como el tamaño podría aparecer cuando se imprima.  El tamaño devuelto es constante para el contenido de un elemento determinado \(como el metarchivo, que es constante a un elemento determinado\).  Este tamaño no cambia cuando zoom se aplica al elemento.  No cambia normalmente cuando el contenedor proporciona el elemento más o menos espacio llamando a `OnSetExtent`.  Un ejemplo de un cambio puede ser el de un editor de texto simple sin la capacidad de “el” que ajustó texto según la extensión última enviada por el contenedor.  Si un servidor cambia, el servidor debe establecer probablemente el bit de OLEMISC\_RECOMPOSEONRESIZE del sistema \(consulte la documentación OLE de SDK para obtener más información sobre esta opción\).  
  
## COleServerItem::OnSetExtent  
 Se llama a esta función cuando el contenedor muestra “más o menos” del objeto.  La mayoría de los contenedores no llamará esto en absoluto.  La implementación predeterminada almacena el último valor recibido del contenedor en “m\_sizeExtent”, que se utiliza en `COleServerDoc::GetZoomFactor` al calcular el valor de la EXTENSIÓN CONTAINER descrito anteriormente.  
  
## COleServerDoc::OnSetItemRects  
 Esta función se denomina sólo cuando el documento activo en contexto.  Se llama cuando el contenedor actualiza o la posición del elemento o el recorte aplicado al elemento.  El RECTÁNGULO de la POSICIÓN, tal y como se describe anteriormente, proporciona el numerador para el cálculo del factor de zoom.  Un servidor puede solicitar que el elemento colocar sea cambiado llamando a `COleServerDoc::RequestPositionChange`.  El contenedor puede o no puede responder a esta solicitud llamando a `OnSetItemRects` \(con una llamada a **COleServerItem::SetItemRects**\).  
  
## COleServerDoc::OnDraw  
 Es importante realizar que el metarchivo creado reemplazando de `COleServerItem::OnDraw` genera exactamente el mismo metarchivo, independientemente del factor de zoom actual.  El contenedor escalará el metarchivo según corresponda.  Esta distinción es importante entre `OnDraw` de la vista y `OnDraw`del elemento del servidor.  La vista controla el zoom, el elemento inmediatamente crea un metarchivo *zoom* y deja hasta el contenedor para hacer zoom adecuado.  
  
 La mejor manera de garantizar que el servidor se comporta correctamente es utilizar la implementación de `COleServerDoc::GetZoomFactor` si el documento activo en contexto.  
  
## Compatibilidad de MFC con el cambio de contexto  
 MFC implementa totalmente la interfaz que cambia el tamaño de contexto como se describe en la especificación OLE 2.  La interfaz de usuario se admite en la clase de `COleResizeBar` , un mensaje **WM\_SIZECHILD**de custom, y un control especial de este mensaje en `COleIPFrameWnd`.  
  
 Quizá desee implementar diferente administrar de este mensaje proporcionada por el marco.  Como se ha descrito anteriormente, el marco permite los resultados de cambiar el tamaño de contexto hasta el contenedor \(el servidor responde al cambio del factor de zoom.  Si el contenedor reacciona estableciendo la EXTENSIÓN CONTAINER y el RECTÁNGULO de la POSICIÓN durante el procesamiento del `COleClientItem::OnChangeItemPosition` \(denominado como resultado de una llamada a `COleServerDoc::RequestPositionChange`\) que ese en contexto cambian el tamaño provocarán mostrar “más o menos” del elemento en la ventana de edición.  Si el contenedor reacciona simplemente estableciendo el RECTÁNGULO de la POSICIÓN durante el procesamiento de `COleClientItem::OnChangeItemPosition`, el factor de zoom cambiará y el elemento se mostrará “acercado o out”.  
  
 Un servidor puede controlar \(a cierto grado\) qué sucede durante esta negociación.  Una hoja de cálculo, por ejemplo puede decidir mostrar más o menos a celdas cuando el usuario cambia el tamaño de la ventana mientras edita el elemento de contexto.  Un equipo de procesamiento de textos podría elegir cambiar “los márgenes de página” de modo que son iguales que la ventana y el rewrap texto al nuevo formato.  Los Servidores implementan esto cambiando la extensión natural \(el tamaño devuelto de `COleServerItem::OnGetExtent`\) cuando se realiza el cambio de tamaño.  Esto hace que el RECTÁNGULO de la POSICIÓN y la EXTENSIÓN CONTAINER el cambio por la misma cantidad, lo que produce el mismo factor de zoom, pero un área de visualización mayor o menor.  Además, más o menos de documento estarán visibles en el metarchivo generado por `OnDraw`.  En este caso, el documento propio cambia cuando el usuario cambia el tamaño del elemento, en lugar de solo el área de visualización.  
  
 Puede implementar personalizada que cambia el tamaño y todavía aprovechar la interfaz de usuario proporcionada por `COleResizeBar` invalidando el mensaje de **WM\_SIZECHILD** en la clase de `COleIPFrameWnd` .  Para obtener más información sobre las características de **WM\_SIZECHILD**, vea [Nota técnica 24](../mfc/tn024-mfc-defined-messages-and-resources.md).  
  
## Vea también  
 [Notas técnicas por número](../mfc/technical-notes-by-number.md)   
 [Notas técnicas por categoría](../mfc/technical-notes-by-category.md)