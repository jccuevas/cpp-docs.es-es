---
title: Documentos de varias páginas
ms.date: 11/19/2018
helpviewer_keywords:
- pagination [MFC]
- overriding [MFC], View class functions for printing
- OnPrepareDC method [MFC]
- CPrintInfo structure [MFC], multipage documents
- OnEndPrinting method [MFC]
- protocols [MFC], printing protocol
- document pages vs. printer pages [MFC]
- printer mode [MFC]
- printing [MFC], multipage documents
- printers [MFC], printer mode
- documents [MFC], printing
- OnPreparePrinting method [MFC]
- OnPrint method [MFC]
- DoPreparePrinting method and pagination [MFC]
- OnDraw method [MFC], printing
- pagination [MFC], printing multipage documents
- printing [MFC], protocol
- pages [MFC], printing
- OnBeginPrinting method [MFC]
- multipage documents [MFC]
- printing [MFC], pagination
- documents [MFC], paginating
ms.assetid: 69626b86-73ac-4b74-b126-9955034835ef
ms.openlocfilehash: 87912c06a40740d25530235ee421c6c8bfa11aab
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370730"
---
# <a name="multipage-documents"></a>Documentos de varias páginas

En este artículo se describe el protocolo de impresión de Windows y se explica cómo imprimir documentos que contienen más de una página. El artículo trata los siguientes temas:

- [Protocolo de impresión](#_core_the_printing_protocol)

- [Reemplazar funciones de clase de vista](#_core_overriding_view_class_functions)

- [Paginación](#_core_pagination)

- [Páginas de impresora frente a páginas de documentos](#_core_printer_pages_vs.._document_pages)

- [Paginación en tiempo de impresión](#_core_print.2d.time_pagination)

## <a name="the-printing-protocol"></a><a name="_core_the_printing_protocol"></a>El protocolo de impresión

Para imprimir un documento de varias páginas, el marco de trabajo y la vista interactúan de la siguiente manera. En primer lugar, el marco de trabajo muestra el cuadro de diálogo **Imprimir,** crea un contexto de dispositivo para la impresora y llama a la función miembro [StartDoc](../mfc/reference/cdc-class.md#startdoc) del objeto [CDC.](../mfc/reference/cdc-class.md) A continuación, para cada página del documento, el marco `CDC` de trabajo llama a la [StartPage](../mfc/reference/cdc-class.md#startpage) función miembro del objeto, indica al objeto de vista para imprimir la página y llama a la [EndPage](../mfc/reference/cdc-class.md#endpage) función miembro. Si se debe cambiar el modo de impresora antes de iniciar una página determinada, la vista llama a [ResetDC](../mfc/reference/cdc-class.md#resetdc), que actualiza la estructura [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) que contiene la nueva información del modo de impresora. Cuando se ha impreso todo el documento, el marco de trabajo llama a la [EndDoc](../mfc/reference/cdc-class.md#enddoc) función miembro.

## <a name="overriding-view-class-functions"></a><a name="_core_overriding_view_class_functions"></a>Reemplazar funciones de clase de vista

La clase [CView](../mfc/reference/cview-class.md) define varias funciones miembro a las que llama el marco de trabajo durante la impresión. Al reemplazar estas funciones en la clase de vista, se proporcionan las conexiones entre la lógica de impresión del marco de trabajo y la lógica de impresión de la clase de vista. En la tabla siguiente se enumeran estas funciones miembro.

### <a name="cviews-overridable-functions-for-printing"></a>Funciones reemplazables de CView para imprimir

|Nombre|Razón para anular|
|----------|---------------------------|
|[OnPreparePrinting](../mfc/reference/cview-class.md#onprepareprinting)|Para insertar valores en el cuadro de diálogo Imprimir, especialmente la longitud del documento|
|[OnBeginPrinting](../mfc/reference/cview-class.md#onbeginprinting)|Para asignar fuentes u otros recursos GDI|
|[OnPrepareDC](../mfc/reference/cview-class.md#onpreparedc)|Para ajustar los atributos del contexto del dispositivo para una página determinada, o para realizar la paginación en tiempo de impresión|
|[OnPrint](../mfc/reference/cview-class.md#onprint)|Para imprimir una página determinada|
|[OnEndPrinting](../mfc/reference/cview-class.md#onendprinting)|Para desasignar recursos de GDI|

También puede realizar el procesamiento relacionado con la impresión en otras funciones, pero estas funciones son las que impulsan el proceso de impresión.

La figura siguiente ilustra los pasos implicados en `CView`el proceso de impresión y muestra dónde se llama a cada una de las funciones miembro de impresión de '. El resto de este artículo explica la mayoría de estos pasos con más detalle. En el artículo Asignación de recursos [GDI](../mfc/allocating-gdi-resources.md)se describen partes adicionales del proceso de impresión.

![Proceso de bucle de impresión](../mfc/media/vc37c71.gif "Proceso de bucle de impresión") <br/>
El bucle de impresión

## <a name="pagination"></a><a name="_core_pagination"></a> Paginación

El marco de trabajo almacena gran parte de la información sobre un trabajo de impresión en un [CPrintInfo](../mfc/reference/cprintinfo-structure.md) estructura. Varios de los `CPrintInfo` valores relacionados con la paginación; estos valores son accesibles como se muestra en la tabla siguiente.

### <a name="page-number-information-stored-in-cprintinfo"></a>Información del número de página almacenada en CPrintInfo

|Variable miembro o<br /><br /> nombre(s) de la función (s)|Número de página al que se hace referencia|
|-----------------------------------------------|----------------------------|
|`GetMinPage`/`SetMinPage`|Primera página del documento|
|`GetMaxPage`/`SetMaxPage`|Ultima página del documento|
|`GetFromPage`|Primera página que se imprimirá|
|`GetToPage`|Ultima página que se imprimirá|
|`m_nCurPage`|Página que se está imprimiendo actualmente|

Los números de página comienzan en 1, es decir, la primera página está numerada 1, no 0. Para obtener más información acerca de estos y otros miembros de [CPrintInfo](../mfc/reference/cprintinfo-structure.md), vea la *referencia de MFC*.

Al principio del proceso de impresión, el marco de trabajo llama a `CPrintInfo` la vista [OnPreparePrinting](../mfc/reference/cview-class.md#onprepareprinting) función miembro, pasando un puntero a una estructura. El Asistente para aplicaciones `OnPreparePrinting` proporciona una implementación de `CView`que llama a [DoPreparePrinting](../mfc/reference/cview-class.md#doprepareprinting), otra función miembro de . `DoPreparePrinting`es la función que muestra el cuadro de diálogo Imprimir y crea un contexto de dispositivo de impresora.

En este punto, la aplicación no sabe cuántas páginas hay en el documento. Utiliza los valores predeterminados 1 y 0xFFFF para los números de la primera y última página del documento. Si sabe cuántas páginas tiene `OnPreparePrinting` el documento, invalide y llame a [SetMaxPage]--brokenlink--(reference/cprintinfo-class.md-setmaxpage) para la `CPrintInfo` estructura antes de enviarlo a `DoPreparePrinting`. Esto le permite especificar la longitud del documento.

`DoPreparePrinting`a continuación, muestra el cuadro de diálogo Imprimir. Cuando se devuelve, la `CPrintInfo` estructura contiene los valores especificados por el usuario. Si el usuario desea imprimir solo un rango de páginas seleccionado, puede especificar los números de página inicial y final en el cuadro de diálogo Imprimir. El marco de trabajo `GetFromPage` recupera `GetToPage` estos valores mediante las funciones y de [CPrintInfo](../mfc/reference/cprintinfo-structure.md). Si el usuario no especifica un intervalo `GetMinPage` de `GetMaxPage` páginas, el marco de trabajo llama y usa los valores devueltos para imprimir todo el documento.

Para cada página de un documento que se va a imprimir, el marco de trabajo llama a dos funciones miembro [CDC](../mfc/reference/cdc-class.md) en la clase `CPrintInfo` de vista, [OnPrepareDC](../mfc/reference/cview-class.md#onpreparedc) y [OnPrint](../mfc/reference/cview-class.md#onprint), y pasa cada función dos parámetros: un puntero a un objeto CDC y un puntero a una estructura. Cada vez que `OnPrepareDC` `OnPrint`el marco de trabajo llama y , `CPrintInfo` pasa un valor diferente en el *m_nCurPage* miembro de la estructura. De este modo, el marco de trabajo indica a la vista qué página se debe imprimir.

La función miembro [OnPrepareDC](../mfc/reference/cview-class.md#onpreparedc) también se utiliza para la visualización de pantalla. Realiza ajustes en el contexto del dispositivo antes de realizar el dibujo. `OnPrepareDC`Cumple un papel similar en la impresión, pero hay `CDC` un par de diferencias: en primer lugar, `CPrintInfo` el objeto representa un contexto de dispositivo de impresora en lugar de un contexto de dispositivo de pantalla y, en segundo lugar, un objeto se pasa como un segundo parámetro. (Este parámetro **NULL** es `OnPrepareDC` NULL cuando se llama para la visualización de pantalla.) Reemplazar `OnPrepareDC` para realizar ajustes en el contexto del dispositivo en función de la página que se está imprimiendo. Por ejemplo, puede mover el origen de la ventana gráfica y la región de recorte para asegurarse de que se imprime la parte adecuada del documento.

El [OnPrint](../mfc/reference/cview-class.md#onprint) función miembro realiza la impresión real de la página. El artículo Cómo se realiza la [impresión predeterminada](../mfc/how-default-printing-is-done.md) muestra cómo el marco de trabajo llama a [OnDraw](../mfc/reference/cview-class.md#ondraw) con un contexto de dispositivo de impresora para realizar la impresión. Más precisamente, `OnPrint` el `CPrintInfo` marco de trabajo llama `OnPrint` con una estructura `OnDraw`y un contexto de dispositivo y pasa el contexto del dispositivo a . Reemplazar `OnPrint` para realizar cualquier representación que se debe hacer sólo durante la impresión y no para la visualización de la pantalla. Por ejemplo, para imprimir encabezados o pies de página (consulte el artículo [Encabezados y pies](../mfc/headers-and-footers.md) de página para obtener más información). A `OnDraw` continuación, llame `OnPrint` desde la invalidación de para realizar la representación común a la visualización de pantalla y la impresión.

El hecho `OnDraw` de que la representación para la visualización de la pantalla y la impresión significa que su aplicación es WYSIWYG: "Lo que ves es lo que obtienes." Sin embargo, supongamos que no está escribiendo una aplicación WYSIWYG. Por ejemplo, considere un editor de texto que utiliza una fuente en negrita para imprimir pero muestra códigos de control para indicar texto en negrita en la pantalla. En tal situación, `OnDraw` se utiliza estrictamente para la visualización de pantalla. Al anular `OnPrint`, sustituya `OnDraw` la llamada por una llamada a una función de dibujo independiente. Esa función dibuja el documento de la forma en que aparece en el papel, utilizando los atributos que no se muestran en la pantalla.

## <a name="printer-pages-vs-document-pages"></a><a name="_core_printer_pages_vs.._document_pages"></a>Páginas de impresora frente a páginas de documentos

Cuando se hace referencia a números de página, a veces es necesario distinguir entre el concepto de la impresora de una página y el concepto de un documento de una página. Desde el punto de vista de la impresora, una página es una hoja de papel. Sin embargo, una hoja de papel no es necesariamente igual a una página del documento. Por ejemplo, si está imprimiendo un boletín informativo, donde las hojas deben plegarse, una hoja de papel puede contener la primera y la última página del documento, una al lado de la otra. Del mismo modo, si va a imprimir una hoja de cálculo, el documento no consta de páginas en absoluto. En su lugar, una hoja de papel puede contener las filas del 1 al 20, las columnas 6 a 10.

Todos los números de página de la estructura [CPrintInfo](../mfc/reference/cprintinfo-structure.md) hacen referencia a las páginas de la impresora. El marco `OnPrepareDC` `OnPrint` de trabajo llama y una vez para cada hoja de papel que pasará a través de la impresora. Al reemplazar la función [OnPreparePrinting](../mfc/reference/cview-class.md#onprepareprinting) para especificar la longitud del documento, debe utilizar páginas de impresora. Si hay una correspondencia uno a uno (es decir, una página de impresora es igual a una página de documento), entonces esto es fácil. Si, por el contrario, las páginas de documentos y las páginas de impresora no se corresponden directamente, debe traducir entre ellas. Por ejemplo, considere la posibilidad de imprimir una hoja de cálculo. Al reemplazar `OnPreparePrinting`, debe calcular cuántas hojas de papel se necesitarán para imprimir `SetMaxPage` toda la `CPrintInfo`hoja de cálculo y, a continuación, utilizar ese valor al llamar a la función miembro de . Del mismo modo, al reemplazar `OnPrepareDC`, debe traducir *m_nCurPage* en el rango de filas y columnas que aparecerán en esa hoja en particular y, a continuación, ajustar el origen de la ventana gráfica en consecuencia.

## <a name="print-time-pagination"></a><a name="_core_print.2d.time_pagination"></a>Paginación en tiempo de impresión

En algunas situaciones, es posible que la clase de vista no sepa de antemano cuánto tiempo dura el documento hasta que se haya impreso realmente. Por ejemplo, supongamos que la aplicación no es WYSIWYG, por lo que la longitud de un documento en la pantalla no se corresponde con su longitud cuando se imprime.

Esto provoca un problema al reemplazar [OnPreparePrinting](../mfc/reference/cview-class.md#onprepareprinting) para la clase de `SetMaxPage` vista: no se puede pasar un valor a la función de la [CPrintInfo](../mfc/reference/cprintinfo-structure.md) estructura, porque no se conoce la longitud de un documento. Si el usuario no especifica un número de página para detenerse en el uso del cuadro de diálogo Imprimir, el marco de trabajo no sabe cuándo detener el bucle de impresión. La única manera de determinar cuándo detener el bucle de impresión es imprimir el documento y ver cuándo termina. La clase de vista debe comprobar el final del documento mientras se está imprimiendo y, a continuación, informar al marco de trabajo cuando se alcanza el final.

El marco de trabajo se basa en la función [OnPrepareDC](../mfc/reference/cview-class.md#onpreparedc) de la clase de vista para indicarle cuándo se debe detener. Después de `OnPrepareDC`cada llamada a , `CPrintInfo` el marco de trabajo comprueba un miembro de la estructura denominado *m_bContinuePrinting*. Su valor predeterminado es **TRUE.** Mientras siga siendo así, el marco de trabajo continúa el bucle de impresión. Si se establece en **FALSE**, el marco de trabajo se detiene. Para realizar la paginación `OnPrepareDC` en tiempo de impresión, reemplace para comprobar si se ha alcanzado el final del documento y establezca *m_bContinuePrinting* en **FALSE** cuando lo haya hecho.

La implementación `OnPrepareDC` predeterminada de sets *m_bContinuePrinting* en **FALSE** si la página actual es mayor que 1. Esto significa que si no se especificó la longitud del documento, el marco de trabajo supone que el documento tiene una página. Una consecuencia de esto es que debe tener cuidado `OnPrepareDC`si llama a la versión de clase base de . No suponga que *m_bContinuePrinting* será **TRUE** después de llamar a la versión de la clase base.

### <a name="what-do-you-want-to-know-more-about"></a>¿Qué quieres saber más sobre

- [Encabezados y pies de página](../mfc/headers-and-footers.md)

- [Asignación de recursos de GDI](../mfc/allocating-gdi-resources.md)

## <a name="see-also"></a>Consulte también

[Impresión](../mfc/printing.md)<br/>
[CView (clase)](../mfc/reference/cview-class.md)<br/>
[Clase CDC](../mfc/reference/cdc-class.md)
