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
ms.openlocfilehash: 7ef4267c311c1de516f75c3b54677adfbfaba5c9
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68916436"
---
# <a name="multipage-documents"></a>Documentos de varias páginas

En este artículo se describe el protocolo de impresión de Windows y se explica cómo imprimir documentos que contienen más de una página. En este artículo se tratan los temas siguientes:

- [Protocolo de impresión](#_core_the_printing_protocol)

- [Reemplazar funciones de clase de vista](#_core_overriding_view_class_functions)

- [Expuesto](#_core_pagination)

- [Páginas de impresora frente a páginas de documento](#_core_printer_pages_vs.._document_pages)

- [Paginación en tiempo de impresión](#_core_print.2d.time_pagination)

##  <a name="_core_the_printing_protocol"></a>El protocolo de impresión

Para imprimir un documento de páginas multipágina, el marco de trabajo y la vista interactúan de la siguiente manera. En primer lugar, el marco de trabajo muestra el cuadro de diálogo **Imprimir** , crea un contexto de dispositivo para la impresora y llama a la función miembro [StartDoc](../mfc/reference/cdc-class.md#startdoc) del objeto [CDC](../mfc/reference/cdc-class.md) . A continuación, para cada página del documento, el marco de trabajo llama a la función miembro [StartPage](../mfc/reference/cdc-class.md#startpage) del objeto `CDC`, indica al objeto de vista que imprima la página y llama a la función miembro [EndPage](../mfc/reference/cdc-class.md#endpage). Si el modo de impresión debe cambiarse antes de iniciar una página determinada, la vista llama a [ResetDC](../mfc/reference/cdc-class.md#resetdc), que actualiza la estructura [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) que contiene la nueva información del modo de impresora. Cuando se ha impreso todo el documento, el marco de trabajo llama a la función miembro [EndDoc](../mfc/reference/cdc-class.md#enddoc) .

##  <a name="_core_overriding_view_class_functions"></a>Reemplazar funciones de clase de vista

La clase [CView](../mfc/reference/cview-class.md) define varias funciones miembro a las que llama el marco de trabajo durante la impresión. Al invalidar estas funciones en la clase de vista, se proporcionan las conexiones entre la lógica de impresión del marco y la lógica de impresión de la clase de vista. En la tabla siguiente se enumeran estas funciones miembro.

### <a name="cviews-overridable-functions-for-printing"></a>Funciones reemplazables de CView para imprimir

|NOMBRE|Motivo de la invalidación|
|----------|---------------------------|
|[OnPreparePrinting](../mfc/reference/cview-class.md#onprepareprinting)|Para insertar valores en el cuadro de diálogo Imprimir, especialmente la longitud del documento|
|[OnBeginPrinting](../mfc/reference/cview-class.md#onbeginprinting)|Para asignar fuentes u otros recursos GDI|
|[OnPrepareDC](../mfc/reference/cview-class.md#onpreparedc)|Para ajustar los atributos del contexto de dispositivo para una página determinada o para realizar la paginación en tiempo de impresión|
|[OnPrint](../mfc/reference/cview-class.md#onprint)|Para imprimir una página determinada|
|[OnEndPrinting](../mfc/reference/cview-class.md#onendprinting)|Para desasignar recursos GDI|

También puede realizar el procesamiento relacionado con la impresión en otras funciones, pero estas funciones son las que controlan el proceso de impresión.

En la ilustración siguiente se muestran los pasos implicados en el proceso de impresión y se muestra `CView`dónde se llama a cada una de las funciones miembro de impresión. En el resto de este artículo se explica con más detalle la mayoría de estos pasos. En el artículo [asignar recursos GDI](../mfc/allocating-gdi-resources.md)se describen otras partes del proceso de impresión.

![Proceso de bucle de impresión](../mfc/media/vc37c71.gif "Proceso de bucle de impresión") <br/>
El bucle de impresión

##  <a name="_core_pagination"></a>Expuesto

El marco almacena gran parte de la información sobre un trabajo de impresión en una estructura [CPrintInfo](../mfc/reference/cprintinfo-structure.md) . Algunos de los valores de `CPrintInfo` pertenecen a la paginación; estos valores son accesibles, tal como se muestra en la tabla siguiente.

### <a name="page-number-information-stored-in-cprintinfo"></a>Información de número de página almacenada en CPrintInfo

|Variable miembro o<br /><br /> nombres de función|Número de página al que se hace referencia|
|-----------------------------------------------|----------------------------|
|`GetMinPage`/`SetMinPage`|Primera página del documento|
|`GetMaxPage`/`SetMaxPage`|Última página del documento|
|`GetFromPage`|Primera página que se va a imprimir|
|`GetToPage`|Última página que se va a imprimir|
|`m_nCurPage`|Página que se está imprimiendo actualmente|

Los números de página comienzan en 1, es decir, la primera página tiene el número 1, no 0. Para obtener más información sobre estos y otros miembros de [CPrintInfo](../mfc/reference/cprintinfo-structure.md), vea la *referencia de MFC*.

Al principio del proceso de impresión, el marco de trabajo llama a la función miembro [OnPreparePrinting](../mfc/reference/cview-class.md#onprepareprinting) de la vista, pasando un `CPrintInfo` puntero a una estructura. El Asistente para aplicaciones proporciona una implementación `OnPreparePrinting` de que llama a [DoPreparePrinting](../mfc/reference/cview-class.md#doprepareprinting), otra función `CView`miembro de. `DoPreparePrinting`es la función que muestra el cuadro de diálogo Imprimir y crea un contexto de dispositivo de impresora.

En este momento, la aplicación no sabe el número de páginas que hay en el documento. Usa los valores predeterminados 1 y 0xFFFF para los números de la primera y la última página del documento. Si sabe cuántas páginas tiene el documento, invalide `OnPreparePrinting` y llame a [SetMaxPage]--brokenlink--(Reference/CPrintInfo-Class. MD # SetMaxPage) para `CPrintInfo` la estructura antes de enviarla `DoPreparePrinting`a. Esto le permite especificar la longitud del documento.

`DoPreparePrinting`a continuación, muestra el cuadro de diálogo Imprimir. Cuando devuelve, la `CPrintInfo` estructura contiene los valores especificados por el usuario. Si el usuario desea imprimir solo un intervalo de páginas seleccionado, puede especificar los números de página inicial y final en el cuadro de diálogo Imprimir. El marco de trabajo recupera estos valores mediante `GetFromPage` las `GetToPage` funciones y de [CPrintInfo](../mfc/reference/cprintinfo-structure.md). Si el usuario no especifica un intervalo de páginas, el marco `GetMinPage` de `GetMaxPage` trabajo llama a y y usa los valores devueltos para imprimir todo el documento.

Para cada página de un documento que se va a imprimir, el marco de trabajo llama a dos funciones miembro en la clase de vista, [OnPrepareDC](../mfc/reference/cview-class.md#onpreparedc) y [OnPrint](../mfc/reference/cview-class.md#onprint), y pasa cada función dos parámetros: un puntero a un objeto [CDC](../mfc/reference/cdc-class.md) `CPrintInfo` y un puntero a estructuras. Cada vez que el marco `OnPrepareDC` de `OnPrint`trabajo llama a y, pasa un valor diferente en el miembro `CPrintInfo` m_nCurPage de la estructura. De este modo, el marco de trabajo indica a la vista qué página se debe imprimir.

La función miembro [OnPrepareDC](../mfc/reference/cview-class.md#onpreparedc) también se utiliza para la presentación en pantalla. Realiza ajustes en el contexto del dispositivo antes de que tenga lugar el dibujo. `OnPrepareDC`sirve de un rol similar en la impresión, pero hay un par de diferencias: en primer `CDC` lugar, el objeto representa un contexto de dispositivo de impresora en lugar de un contexto de dispositivo `CPrintInfo` de pantalla y, en segundo lugar, se pasa un objeto como segundo parámetro. (Este parámetro es **null** cuando `OnPrepareDC` se llama a para la presentación en pantalla). Invalide `OnPrepareDC` para realizar ajustes en el contexto del dispositivo en función de la página que se va a imprimir. Por ejemplo, puede trasladar el origen de la ventanilla y la región de recorte para asegurarse de que se imprime la parte adecuada del documento.

La función miembro [OnPrint](../mfc/reference/cview-class.md#onprint) realiza la impresión real de la página. En el artículo [Cómo se realiza la impresión predeterminada](../mfc/how-default-printing-is-done.md) se muestra cómo llama el marco de trabajo a [OnDraw](../mfc/reference/cview-class.md#ondraw)con un contexto de dispositivo de impresora para realizar la impresión. Más concretamente, el marco `OnPrint` de trabajo `CPrintInfo` llama a con una estructura y un `OnPrint` contexto de dispositivo, y `OnDraw`pasa el contexto del dispositivo a. Invalide `OnPrint` para realizar cualquier representación que solo debe realizarse durante la impresión y no para la presentación en pantalla. Por ejemplo, para imprimir encabezados o pies de página (vea los [encabezados y pies](../mfc/headers-and-footers.md) de página del artículo para obtener más información). A continuación `OnDraw` , llame a desde `OnPrint` la invalidación de para realizar la representación común para la presentación en pantalla y la impresión.

El hecho de `OnDraw` que la representación para la presentación en pantalla y la impresión signifique que la aplicación es WYSIWYG: "Lo que ve es lo que obtiene". Sin embargo, supongamos que no está escribiendo una aplicación WYSIWYG. Por ejemplo, considere un editor de texto que use una fuente en negrita para imprimir pero que muestre códigos de control para indicar texto en negrita en la pantalla. En tal situación, se usa `OnDraw` estrictamente para la presentación en pantalla. Cuando invalide `OnPrint`, sustituya la `OnDraw` llamada a por una llamada a una función de dibujo independiente. Esa función dibuja el documento tal como aparece en el papel, usando los atributos que no se muestran en la pantalla.

##  <a name="_core_printer_pages_vs.._document_pages"></a>Páginas de impresora frente a Páginas del documento

Cuando se hace referencia a los números de página, a veces es necesario distinguir entre el concepto de la impresora de una página y el concepto de documento de una página. Desde el punto de vista de la impresora, una página es una hoja de papel. Sin embargo, una hoja de papel no es necesariamente igual a una página del documento. Por ejemplo, si está imprimiendo un boletín, donde se van a doblar las hojas, una hoja de papel podría contener la primera y la última página del documento, en paralelo. Del mismo modo, si está imprimiendo una hoja de cálculo, el documento no se compone de páginas. En su lugar, una hoja de papel puede contener las filas 1 a 20, las columnas 6 a 10.

Todos los números de página de la estructura [CPrintInfo](../mfc/reference/cprintinfo-structure.md) hacen referencia a las páginas de la impresora. El marco de `OnPrepareDC` trabajo `OnPrint` llama a y una vez para cada hoja de papel que pasará a través de la impresora. Al invalidar la función [OnPreparePrinting](../mfc/reference/cview-class.md#onprepareprinting) para especificar la longitud del documento, debe utilizar las páginas de la impresora. Si hay una correspondencia uno a uno (es decir, una página de la impresora es igual a una página de documento), esto es fácil. Si, por otro lado, las páginas de documento y las páginas de impresora no se corresponden directamente, debe traducir entre ellas. Por ejemplo, considere la posibilidad de imprimir una hoja de cálculo. Al reemplazar `OnPreparePrinting`, debe calcular el número de hojas de papel que se requerirán para imprimir toda la hoja de cálculo y, a continuación, usar ese valor al `CPrintInfo`llamar a la `SetMaxPage` función miembro de. Del mismo modo, al `OnPrepareDC`reemplazar, debe traducir *m_nCurPage* en el intervalo de filas y columnas que aparecerán en esa hoja concreta y, a continuación, ajustar el origen de la ventanilla en consecuencia.

##  <a name="_core_print.2d.time_pagination"></a>Paginación en tiempo de impresión

En algunas situaciones, es posible que la clase de vista no sepa de antemano cuánto tiempo el documento es hasta que se haya impreso realmente. Por ejemplo, supongamos que la aplicación no es WYSIWYG, por lo que la longitud de un documento en la pantalla no se corresponde con su longitud cuando se imprime.

Esto provoca un problema cuando se invalida [OnPreparePrinting](../mfc/reference/cview-class.md#onprepareprinting) para la clase de vista: no se puede pasar un valor `SetMaxPage` a la función de la estructura [CPrintInfo](../mfc/reference/cprintinfo-structure.md) , porque no se conoce la longitud de un documento. Si el usuario no especifica un número de página para detenerse en el cuadro de diálogo Imprimir, el marco de trabajo no sabe cuándo se debe detener el bucle de impresión. La única manera de determinar cuándo detener el bucle de impresión es imprimir el documento y ver cuándo finaliza. La clase de vista debe comprobar el final del documento mientras se imprime y, a continuación, informar al marco de trabajo cuando se alcance el final.

El marco de trabajo se basa en la función [OnPrepareDC](../mfc/reference/cview-class.md#onpreparedc) de la clase de vista para indicarle Cuándo debe detenerse. Después de cada llamada `OnPrepareDC`a, el marco de trabajo comprueba un `CPrintInfo` miembro de la estructura denominada *m_bContinuePrinting*. Su valor predeterminado es **true.** Siempre y cuando permanezca así, el marco continúa el bucle de impresión. Si se establece en **false**, el marco de trabajo se detiene. Para realizar la paginación en tiempo de `OnPrepareDC` impresión, invalide para comprobar si se ha alcanzado el final del documento y establezca *m_bContinuePrinting* en **false** cuando tenga.

La implementación predeterminada de `OnPrepareDC` establece *m_bContinuePrinting* en **false** si la página actual es mayor que 1. Esto significa que si no se especifica la longitud del documento, el marco de trabajo supone que el documento tiene una página de longitud. Una consecuencia de esto es que debe tener cuidado si llama a la versión de la clase base `OnPrepareDC`de. No asuma que *m_bContinuePrinting* será **true** después de llamar a la versión de la clase base.

### <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Encabezados y pies de página](../mfc/headers-and-footers.md)

- [Asignar recursos GDI](../mfc/allocating-gdi-resources.md)

## <a name="see-also"></a>Vea también

[Impresión](../mfc/printing.md)<br/>
[CView (clase)](../mfc/reference/cview-class.md)<br/>
[CDC (clase)](../mfc/reference/cdc-class.md)
