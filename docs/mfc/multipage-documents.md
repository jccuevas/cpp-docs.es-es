---
title: Documentos de varias páginas | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8a7179c74347f3c710f542fb1fc83bb79d2acb38
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43220546"
---
# <a name="multipage-documents"></a>Documentos de varias páginas
En este artículo se describe el protocolo de impresión de Windows y se explica cómo imprimir documentos que contienen más de una página. El artículo tratan los temas siguientes:  
  
-   [Protocolo de impresión](#_core_the_printing_protocol)  
  
-   [Reemplazar funciones de clase de vista](#_core_overriding_view_class_functions)  
  
-   [Paginación](#_core_pagination)  
  
-   [Páginas de la impresora frente a páginas del documento](#_core_printer_pages_vs.._document_pages)  
  
-   [Paginación en tiempo de impresión](#_core_print.2d.time_pagination)  
  
##  <a name="_core_the_printing_protocol"></a> El protocolo de impresión  
 Para imprimir un documento de varias páginas, el marco de trabajo y la vista interactúan de la siguiente manera. Primero se muestra el marco de trabajo la **impresión** cuadro de diálogo, crea un contexto de dispositivo para la impresora y llama a la [StartDoc](../mfc/reference/cdc-class.md#startdoc) función miembro de la [CDC](../mfc/reference/cdc-class.md) objeto. A continuación, para cada página del documento, el marco llama a la [StartPage](../mfc/reference/cdc-class.md#startpage) función miembro de la `CDC` de objetos, indica al objeto de vista para imprimir la página y llama a la [EndPage](../mfc/reference/cdc-class.md#endpage) función miembro. Si es necesario cambiar el modo de impresora antes de iniciar una página determinada, llama la vista [ResetDC](../mfc/reference/cdc-class.md#resetdc), las actualizaciones que la [DEVMODE](/windows/desktop/api/wingdi/ns-wingdi-_devicemodea) estructura que contiene la nueva información de modo de impresora. Cuando se ha imprimido todo el documento, el marco llama a la [EndDoc](../mfc/reference/cdc-class.md#enddoc) función miembro.  
  
##  <a name="_core_overriding_view_class_functions"></a> Reemplazar funciones de clase de vista  
 El [CView](../mfc/reference/cview-class.md) clase define varias funciones miembro que llaman el marco de trabajo durante la impresión. Mediante la invalidación de estas funciones en la clase de vista, se proporcionan las conexiones entre la lógica de impresión del marco de trabajo y lógica de impresión de la clase de vista. En la tabla siguiente se enumera estas funciones miembro.  
  
### <a name="cviews-overridable-functions-for-printing"></a>Funciones reemplazables de CView para la impresión  
  
|nombre|Motivo de invalidación|  
|----------|---------------------------|  
|[OnPreparePrinting](../mfc/reference/cview-class.md#onprepareprinting)|Para insertar valores en el cuadro de diálogo Imprimir, especialmente la longitud del documento|  
|[OnBeginPrinting](../mfc/reference/cview-class.md#onbeginprinting)|Para asignar fuentes u otros recursos GDI|  
|[OnPrepareDC](../mfc/reference/cview-class.md#onpreparedc)|Para ajustar los atributos del contexto de dispositivo para una página determinada, o para realizar la paginación de la hora de impresión|  
|[OnPrint](../mfc/reference/cview-class.md#onprint)|Para imprimir una página determinada|  
|[OnEndPrinting](../mfc/reference/cview-class.md#onendprinting)|Para desasignar los recursos de GDI|  
  
 Se puede realizar procesamiento relacionado con la impresión en otras funciones, así, pero estas funciones son las que controlan el proceso de impresión.  
  
 La siguiente ilustración se muestran los pasos implicados en el proceso de impresión y se muestra dónde cada uno de `CView`de impresión de miembro se llama a funciones. El resto de este artículo explica la mayoría de estos pasos con más detalle. Elementos adicionales del proceso de impresión se describen en el artículo [asignar recursos GDI](../mfc/allocating-gdi-resources.md).  
  
 ![Proceso de bucle de impresión](../mfc/media/vc37c71.gif "vc37c71")  
El bucle de impresión  
  
##  <a name="_core_pagination"></a> Paginación  
 El marco de trabajo almacena mucha información acerca de un trabajo de impresión en un [CPrintInfo](../mfc/reference/cprintinfo-structure.md) estructura. Algunos de los valores de `CPrintInfo` corresponden a la paginación; estos valores son accesibles como se muestra en la tabla siguiente.  
  
### <a name="page-number-information-stored-in-cprintinfo"></a>Información de número de página almacenada en CPrintInfo  
  
|Variable de miembro o<br /><br /> nombres de función|Número de página al que hace referencia|  
|-----------------------------------------------|----------------------------|  
|`GetMinPage`/`SetMinPage`|Primera página del documento|  
|`GetMaxPage`/`SetMaxPage`|Última página del documento|  
|`GetFromPage`|Primera página que se van a imprimir|  
|`GetToPage`|Última página que se van a imprimir|  
|`m_nCurPage`|Página que se está imprimiendo actualmente|  
  
 Números de página comienzan en 1, es decir, la primera página se asigna un número 1, no en 0. Para obtener más información sobre estos y otros miembros de [CPrintInfo](../mfc/reference/cprintinfo-structure.md), consulte el *referencia de MFC*.  
  
 Al principio del proceso de impresión, el marco llama a la vista [OnPreparePrinting](../mfc/reference/cview-class.md#onprepareprinting) función miembro, pasando un puntero a un `CPrintInfo` estructura. El Asistente para aplicaciones proporciona una implementación de `OnPreparePrinting` que llama a [DoPreparePrinting](../mfc/reference/cview-class.md#doprepareprinting), otra función miembro de `CView`. `DoPreparePrinting` es la función que muestra el cuadro de diálogo Imprimir y crea un contexto de dispositivo de impresora.  
  
 En este momento la aplicación no sabe cuántas páginas se encuentran en el documento. Usa los valores predeterminados 1 y 0xFFFF para los números de la primera y última página del documento. Si sabe cuántas páginas tiene el documento, invalidar `OnPreparePrinting` y llame a [SetMaxPage]--brokenlink--(reference/cprintinfo-class.md#setmaxpage) para el `CPrintInfo` estructura antes de enviarlo a `DoPreparePrinting`. Esto le permite especificar la longitud del documento.  
  
 `DoPreparePrinting` a continuación, muestra el cuadro de diálogo Imprimir. Cuando se devuelve, el `CPrintInfo` estructura contiene los valores especificados por el usuario. Si el usuario desea imprimir sólo un intervalo seleccionado de páginas, puede especificar la iniciales y finales de los números de página en el cuadro de diálogo Imprimir. El marco de trabajo recupera estos valores con el `GetFromPage` y `GetToPage` funciones de [CPrintInfo](../mfc/reference/cprintinfo-structure.md). Si el usuario no especifica un intervalo de páginas, el marco llama a `GetMinPage` y `GetMaxPage` y usa los valores devueltos para imprimir todo el documento.  
  
 Para cada página del que se imprima un documento, el marco llama a dos funciones miembro de la clase de vista, [OnPrepareDC](../mfc/reference/cview-class.md#onpreparedc) y [OnPrint](../mfc/reference/cview-class.md#onprint)y cada función se pasan dos parámetros: un puntero a un [ CDC](../mfc/reference/cdc-class.md) objeto y un puntero a un `CPrintInfo` estructura. Cada vez que llama el marco `OnPrepareDC` y `OnPrint`, pasa un valor distinto en el *m_nCurPage* miembro de la `CPrintInfo` estructura. De este modo el marco de trabajo indica a la vista qué página debe imprimirse.  
  
 El [OnPrepareDC](../mfc/reference/cview-class.md#onpreparedc) función miembro también se usa para la presentación en pantalla. Realiza ajustes en el contexto de dispositivo antes de dibujar. `OnPrepareDC` ofrece una función similar en la impresión, pero hay un par de diferencias: primero, el `CDC` objeto representa un contexto de dispositivo de impresora en lugar de un contexto de dispositivo de pantalla y, segundo, un `CPrintInfo` objeto se pasa como segundo parámetro. (Este parámetro es **NULL** cuando `OnPrepareDC` se llama para presentación en pantalla.) Invalidar `OnPrepareDC` realizar ajustes en el contexto de dispositivo en función de página que se va a imprimir. Por ejemplo, puede mover el origen de la ventanilla y la región de recorte para asegurarse de que la parte correspondiente del documento se imprime.  
  
 El [OnPrint](../mfc/reference/cview-class.md#onprint) función miembro realiza la impresión real de la página. El artículo [cómo predeterminado impresión se realiza](../mfc/how-default-printing-is-done.md) muestra cómo el marco llama [OnDraw](../mfc/reference/cview-class.md#ondraw) con un contexto de dispositivo de impresora para realizar la impresión. Más concretamente, las llamadas de framework `OnPrint` con un `CPrintInfo` estructura y un contexto de dispositivo y `OnPrint` pasa el contexto de dispositivo a `OnDraw`. Invalidar `OnPrint` para realizar cualquier procesamiento que debe realizarse durante la impresión y no para la presentación en pantalla. Por ejemplo, para imprimir los encabezados o pies de página (consulte el artículo [encabezados y pies de página](../mfc/headers-and-footers.md) para obtener más información). A continuación, llame a `OnDraw` desde el reemplazo de `OnPrint` para realizar la representación común tanto presentación en pantalla e impresión.  
  
 El hecho de que `OnDraw` realiza la representación para ambos presentación en pantalla y la impresión significa que la aplicación es WYSIWYG: "lo que ve es lo obtenemos." Sin embargo, suponga que no está escribiendo una aplicación WYSIWYG. Por ejemplo, considere la posibilidad de un texto de editor que utilice una fuente en negrita para la impresión, pero muestra los códigos de control para indicar el texto en negrita en la pantalla. En esta situación, usa `OnDraw` estrictamente para su presentación en pantalla. Cuando invalide `OnPrint`, sustituya la llamada a `OnDraw` con una llamada a una función de dibujo diferente. Esa función dibuja el documento tal como aparece en el papel, usando los atributos que no se muestran en la pantalla.  
  
##  <a name="_core_printer_pages_vs.._document_pages"></a> Frente a las páginas de impresora. Páginas del documento  
 Cuando se hace referencia a los números de página, a veces es necesario distinguir entre el concepto de la impresora de una página y el concepto de un documento de una página. Desde el punto de vista de la impresora, una página es una hoja de papel. Sin embargo, una hoja de papel no necesariamente igual que una página del documento. Por ejemplo, si va a imprimir un boletín, donde las hojas se van a doblar, una hoja de papel podría contener las páginas primeros y últimas del documento, en paralelo. De forma similar, si va a imprimir una hoja de cálculo, el documento no constan de páginas en absoluto. En su lugar, una hoja de papel podría contener las filas 1 a 20, 6 a 10 columnas.  
  
 La página todos los números en el [CPrintInfo](../mfc/reference/cprintinfo-structure.md) estructura hacen referencia a las páginas de la impresora. Las llamadas de framework `OnPrepareDC` y `OnPrint` una vez para cada hoja de papel que pasará a través de la impresora. Cuando invalide el [OnPreparePrinting](../mfc/reference/cview-class.md#onprepareprinting) de función para especificar la longitud del documento, debe usar páginas de la impresora. Si hay una correspondencia uno a uno (es decir, una página de la impresora es igual a una página del documento), entonces es fácil. Si, por otro lado, las páginas del documento y páginas de la impresora no se corresponden directamente con, debe traducir entre ellos. Por ejemplo, considere la posibilidad de imprimir una hoja de cálculo. Cuando se reemplaza `OnPreparePrinting`, debe calcular el número de hojas de papel será necesario para imprimir la hoja de cálculo completo y, a continuación, usar ese valor cuando se llama a la `SetMaxPage` función miembro de `CPrintInfo`. De forma similar, cuando se reemplaza `OnPrepareDC`, debe traducir *m_nCurPage* en el intervalo de filas y columnas que aparecen en esa hoja en particular y, a continuación, ajustar el origen de la ventanilla en consecuencia.  
  
##  <a name="_core_print.2d.time_pagination"></a> Paginación en tiempo de impresión  
 En algunas situaciones, la clase de vista puede no saber de antemano cuánto tiempo el documento hasta que realmente se ha impreso. Por ejemplo, supongamos que su aplicación no WYSIWYG, por lo que la longitud de un documento en la pantalla no se corresponde con su longitud cuando se imprima.  
  
 Esto hace que un problema cuando se reemplaza [OnPreparePrinting](../mfc/reference/cview-class.md#onprepareprinting) para la clase de vista: no se puede pasar un valor para el `SetMaxPage` función de la [CPrintInfo](../mfc/reference/cprintinfo-structure.md) estructura, puesto que desconoce la longitud de un documento. Si el usuario no especifica un número de página debe detenerse mediante el cuadro de diálogo de impresión, el marco de trabajo no sabe cuándo detener el bucle de impresión. Es la única manera de determinar cuándo se debe detener el bucle de impresión imprimir el documento y ver cuando termina. La clase de vista debe comprobar si el final del documento mientras se está imprimiendo y, a continuación, informar el marco de trabajo cuando se alcanza el final.  
  
 El marco de trabajo se basa en la clase de vista [OnPrepareDC](../mfc/reference/cview-class.md#onpreparedc) función le indiquen cuándo se debe detener. Después de cada llamada a `OnPrepareDC`, el marco de trabajo comprueba un miembro de la `CPrintInfo` estructura denominada *m_bContinuePrinting*. Su valor predeterminado es **es TRUE.** Mientras permanece así, el marco de trabajo continuará el bucle de impresión. Si se establece en **FALSE**, los delimitadores de marco de trabajo. Para realizar la paginación en tiempo de impresión, reemplace `OnPrepareDC` para comprobar si tiene ha alcanzado el final del documento y establecer *m_bContinuePrinting* a **FALSE** cuando lo tiene.  
  
 La implementación predeterminada de `OnPrepareDC` establece *m_bContinuePrinting* a **FALSE** si la página actual es mayor que 1. Esto significa que si no se especificó la longitud del documento, el marco de trabajo supone que el documento es una página larga. Una consecuencia de esto es que debe tener cuidado si se llama a la versión de la clase base `OnPrepareDC`. No suponga que *m_bContinuePrinting* será **TRUE** después de llamar a la versión de la clase base.  
  
### <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre  
  
-   [Encabezados y pies de página](../mfc/headers-and-footers.md)  
  
-   [Asignar recursos de GDI](../mfc/allocating-gdi-resources.md)  
  
## <a name="see-also"></a>Vea también  
 [Imprimir](../mfc/printing.md)   
 [CView (clase)](../mfc/reference/cview-class.md)   
 [CDC (clase)](../mfc/reference/cdc-class.md)