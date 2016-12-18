---
title: "Documentos de varias p&#225;ginas | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CPrintInfo (estructura), documentos de varias páginas"
  - "documentos de varias páginas frente a páginas de la impresora"
  - "documentos, paginación"
  - "documentos, imprimir"
  - "DoPreparePrinting (método y paginación)"
  - "documentos de varias páginas"
  - "OnBeginPrinting (método)"
  - "OnDraw (método), imprimir"
  - "OnEndPrinting (método)"
  - "OnPrepareDC (método)"
  - "OnPreparePrinting (método)"
  - "OnPrint (método)"
  - "reemplazar, funciones de la clase vista para imprimir"
  - "páginas, imprimir"
  - "paginación"
  - "paginación, imprimir documentos de varias páginas"
  - "modo de impresora"
  - "impresoras, modo de impresora"
  - "imprimir [MFC], documentos de varias páginas"
  - "imprimir [MFC], paginación"
  - "imprimir [MFC], protocolo"
  - "protocolos, imprimir protocolo"
ms.assetid: 69626b86-73ac-4b74-b126-9955034835ef
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Documentos de varias p&#225;ginas
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este artículo se describe Windows que imprime protocolo y explica cómo imprimir documentos que contienen más de una página.  El artículo se tratan los siguientes temas:  
  
-   [Protocolo de impresión](#_core_the_printing_protocol)  
  
-   [Reemplazar funciones de clase de vista](#_core_overriding_view_class_functions)  
  
-   [Paginación](#_core_pagination)  
  
-   [Páginas de la impresora con las páginas de un documento](#_core_printer_pages_vs.._document_pages)  
  
-   [Paginación de IMPR\- Tiempo](#_core_print.2d.time_pagination)  
  
##  <a name="_core_the_printing_protocol"></a> El protocolo de impresión  
 Para imprimir un documento de varias páginas, el marco y la vista interactivos de la manera siguiente.  Primero el marco muestra el cuadro de diálogo de **Impresión** , crea un contexto para la impresora, y llama a la función miembro de [StartDoc](../Topic/CDC::StartDoc.md) del objeto de [CDC](../mfc/reference/cdc-class.md) .  A continuación, cada página del documento, el marco pide la función miembro de [StartPage](../Topic/CDC::StartPage.md) del objeto de `CDC` , indica al objeto de vista para imprimir la página, y llama a la función miembro de [EndPage](../Topic/CDC::EndPage.md) .  Si el modo impresora debe cambiar antes de iniciar una página específica, la vista llama [ResetDC](../Topic/CDC::ResetDC.md), que actualiza la estructura de [DEVMODE](http://msdn.microsoft.com/library/windows/desktop/dd183565) que contiene la nueva información de modo impresora.  Cuando se ha imprimir todo el documento, el marco de trabajo llama a la función miembro de [EndDoc](../Topic/CDC::EndDoc.md) .  
  
##  <a name="_core_overriding_view_class_functions"></a> Reemplazar funciones de clase de vista  
 La clase de [CView](../mfc/reference/cview-class.md) define varias funciones miembro que son llamadas por el marco durante la impresión.  Reemplazar estas funciones en la clase de vista, proporciona las conexiones entre la lógica que imprime de marco y la lógica de impresión de la clase de vista.  La tabla siguiente se muestran estas funciones miembro.  
  
### Overridable CView funciona para imprimir  
  
|Name|Motivo de reemplazar|  
|----------|--------------------------|  
|[OnPreparePrinting](../Topic/CView::OnPreparePrinting.md)|Para insertar valores en el cuadro de diálogo imprimir, especialmente la longitud del documento|  
|[OnBeginPrinting](../Topic/CView::OnBeginPrinting.md)|Para asignar las fuentes u otros recursos de GDI|  
|[OnPrepareDC](../Topic/CView::OnPrepareDC.md)|Para ajustar los atributos de contexto para una página determinada, o hacer la paginación de IMPR\- Tiempo|  
|[OnPrint](../Topic/CView::OnPrint.md)|Para imprimir una página determinada|  
|[OnEndPrinting](../Topic/CView::OnEndPrinting.md)|Para desasignar los recursos de GDI|  
  
 Puede realizar el procesamiento impresión\- relacionado en otras funciones también, pero estas funciones son las que controlan el proceso de impresión.  
  
 La siguiente ilustración muestra los pasos implicados en el proceso de impresión y muestra donde cada uno de `CView` que imprime funciones miembro se denomina.  El resto de este artículo se explica la mayoría de estos pasos con más detalle.  Las partes adicionales del proceso de impresión se describen en el caso [Asignar recursos de GDI](../mfc/allocating-gdi-resources.md).  
  
 ![Proceso de bucle de impresión](../mfc/media/vc37c71.png "vc37C71")  
El bucle de impresión  
  
##  <a name="_core_pagination"></a> Paginación  
 El marco almacena gran parte de la información de un trabajo de impresión en una estructura de [CPrintInfo](../mfc/reference/cprintinfo-structure.md) .  Algunos de los valores de `CPrintInfo` pertenecen a la paginación; estos valores son accesibles como se muestra en la tabla siguiente.  
  
### Información de número de página almacenada en CPrintInfo  
  
|Variable miembro o<br /><br /> nombres de función|Número de página hace referencia|  
|-----------------------------------------------|--------------------------------------|  
|`GetMinPage`\/`SetMinPage`|Primera página del documento|  
|`GetMaxPage`\/`SetMaxPage`|Última página del documento|  
|`GetFromPage`|Primera página que se imprimirá|  
|`GetToPage`|Última página que se imprimirá|  
|`m_nCurPage`|Página que es impresa actualmente|  
  
 Los números de página comienzan en 1, es decir, la primera página se numera 1, no 0.  Para obtener más información sobre éstos y otros miembros de [CPrintInfo](../mfc/reference/cprintinfo-structure.md), vea *la referencia de MFC*.  
  
 Al principio del proceso de impresión, el marco de trabajo llama a la función miembro de [OnPreparePrinting](../Topic/CView::OnPreparePrinting.md) de vista, pasando un puntero a una estructura de `CPrintInfo` .  El Asistente para aplicaciones proporciona una implementación de `OnPreparePrinting` que llame a [DoPreparePrinting](../Topic/CView::DoPreparePrinting.md), otra función miembro de `CView`.  `DoPreparePrinting` es la función que muestra el cuadro de diálogo imprimir y crea un contexto de dispositivo de impresora.  
  
 En este punto la aplicación no sabe cuántas páginas están en el documento.  Utiliza los valores predeterminados 1 y 0xFFFF para los números de la primera y la última página del documento.  Si sabe cuántas páginas tiene el documento, reemplace `OnPreparePrinting` y la llamada [SetMaxPage](../Topic/CPrintInfo::SetMaxPage.md) para la estructura de `CPrintInfo` antes de que se envíe a `DoPreparePrinting`.  Esto permite especificar la longitud del documento.  
  
 `DoPreparePrinting` después muestra el cuadro de diálogo imprimir.  Cuando vuelve, la estructura de `CPrintInfo` contiene los valores especificados por el usuario.  Si el usuario imprima sólo un intervalo seleccionado de páginas, de él o la ella pueden especificar números de página inicial y final en el cuadro de diálogo imprimir.  El marco recupera estos valores con las funciones de `GetFromPage` y de `GetToPage` de [CPrintInfo](../mfc/reference/cprintinfo-structure.md).  Si el usuario no especifica un intervalo de páginas, el marco de trabajo llama a `GetMinPage` y `GetMaxPage` y utiliza los valores devueltos para imprimir todo el documento.  
  
 Para cada página de un documento que se imprimirá, el marco dos funciones miembro de la clase de vista, [OnPrepareDC](../Topic/CView::OnPrepareDC.md) y [OnPrint](../Topic/CView::OnPrint.md), y pasar parámetros de cada función dos: un puntero a un objeto de [CDC](../mfc/reference/cdc-class.md) y un puntero a una estructura de `CPrintInfo` .  Cada vez que el marco de trabajo llama a `OnPrepareDC` y `OnPrint`, pasa un valor diferente en el miembro de `m_nCurPage` de la estructura de `CPrintInfo` .  De esta manera el marco indica a vista qué página debe ser impresa.  
  
 La función miembro de [OnPrepareDC](../Topic/CView::OnPrepareDC.md) también se utiliza para la presentación en pantalla.  Crea ajustes al contexto de dispositivo antes de que tenga lugar el dibujo.  `OnPrepareDC` desempeña un rol similar en la impresión, pero hay un par de diferencias: primero, el objeto de `CDC` representa un contexto de dispositivo de impresora en lugar de un contexto de dispositivo de pantalla y, a continuación, un objeto de `CPrintInfo` se pasa como segundo parámetro. \(Este parámetro es **nulo** cuando `OnPrepareDC` se llama para la presentación en pantalla\). Reemplace `OnPrepareDC` para ajustar el contexto de dispositivo basado en se imprime qué página.  Por ejemplo, puede mover el origen de la ventanilla y la zona de recorte para asegurarse de que la parte correspondiente del documento obtiene impreso.  
  
 La función miembro de [OnPrint](../Topic/CView::OnPrint.md) realiza la impresión real de la página.  El artículo [Cómo predeterminados se hace la impresión](../mfc/how-default-printing-is-done.md) muestra cómo el marco de trabajo llama a [OnDraw](../Topic/CView::OnDraw.md) con un contexto de dispositivo de impresora para realizar la impresión.  Más concretamente, el marco de trabajo llama a `OnPrint` con una estructura de `CPrintInfo` y un contexto de dispositivo, y `OnPrint` pasa el contexto del dispositivo a `OnDraw`.  Reemplace `OnPrint` para realizar cualquier representación que debe hacer solo durante la impresión y no para la presentación en pantalla.  Por ejemplo, imprimir encabezados o pies de página \(vea el artículo [Encabezados y pies de página](../mfc/headers-and-footers.md) para obtener más información\).  A continuación llamada `OnDraw` de reemplazo de `OnPrint` para hacer el común de representación a la presentación en pantalla y la impresión.  
  
 El hecho de que `OnDraw` haga la representación para la presentación en pantalla y la impresión significa que la aplicación está en modo WYSIWYG: “Lo que se ve es lo que se obtiene”. Sin embargo, suponga que no está escribiendo una aplicación WYSIWYG.  Por ejemplo, piense en un editor de texto que utiliza una fuente negrita para que los códigos de control el imprimir pero de muestra indican texto en negrita en la pantalla.  En esta situación, se utiliza `OnDraw` estrictamente para la presentación en pantalla.  Cuando se invalida `OnPrint`, sustituya la llamada a `OnDraw` con una llamada a una función independiente del gráfico.  Que la función dibuja el documento la forma que aparece en el papel, utilizando los atributos que no muestra en pantalla.  
  
##  <a name="_core_printer_pages_vs.._document_pages"></a> Páginas de la impresora con las páginas de un documento  
 Al hacer referencia a los números de página, a veces es necesario diferenciar entre el concepto de impresora de una página y el concepto de un documento de una página.  Desde el punto de vista de la impresora, una página es una hoja de papel.  Sin embargo, una hoja de papel no es necesariamente una página del documento.  Por ejemplo, si va a imprimir un boletín, donde se plegado hojas, una hoja de papel puede contener ambas la primera y la última páginas de documento, en paralelo.  De igual forma, si está imprimir una hoja de cálculo, el documento no consta de páginas en absoluto.  En su lugar, una hoja de papel podría contener las filas 1 a 20, columnas 6 a 10.  
  
 Todos los números de página en la estructura de [CPrintInfo](../mfc/reference/cprintinfo-structure.md) hacen referencia a las páginas de la impresora.  El marco de trabajo llama a `OnPrepareDC` y `OnPrint` una vez para cada hoja de papel que pasa a través de la impresora.  Cuando se reemplaza la función de [OnPreparePrinting](../Topic/CView::OnPreparePrinting.md) para especificar la longitud del documento, debe usar las páginas de la impresora.  Si hay una correspondencia \(es decir, una página de la impresora es una página de un documento\), entonces esto es fácil.  Si, por otro lado, las páginas de un documento y las páginas de la impresora no corresponden directamente, debe traducir entre ellas.  Por ejemplo, considere imprimir una hoja de cálculo.  Al reemplazar `OnPreparePrinting`, debe calcular cuántas hojas de papel serán necesarias imprimir la hoja de cálculo completa y después utilizar ese valor al llamar a la función miembro de `SetMaxPage` de `CPrintInfo`.  De igual forma, al reemplazar `OnPrepareDC`, debe convertir `m_nCurPage` al intervalo de las filas y columnas que aparecerán en la hoja determinada y después se ajustarán el origen de la ventanilla en consecuencia.  
  
##  <a name="_core_print.2d.time_pagination"></a> Paginación de IMPR\- Tiempo  
 En algunas situaciones, la clase de vista no puede saber de antemano cuánto tiempo es el documento hasta que se haya impreso realmente.  Por ejemplo, suponga que la aplicación no está en modo WYSIWYG, por lo que una longitud de documento en la pantalla no corresponde a su longitud al imprimirse.  
  
 Esto produce un problema cuando se reemplaza [OnPreparePrinting](../Topic/CView::OnPreparePrinting.md) para la clase de vista: no puede pasar un valor a la función de `SetMaxPage` de la estructura de [CPrintInfo](../mfc/reference/cprintinfo-structure.md) , porque no conoce la longitud de un documento.  Si el usuario no especifica un número de página para detener en mediante el cuadro de diálogo imprimir, el marco no sabe cuándo detener el bucle de impresión.  La única manera de determinar cuándo dejar el bucle de impresión es imprimir el documento y considerar cuando finaliza.  La clase de vista debe comprobar el final del documento mientras se imprimir, y después informar al marco cuando se alcanza el final.  
  
 El marco se basa en la función de [OnPrepareDC](../Topic/CView::OnPrepareDC.md) de la clase de vista para indicar que cuándo detener.  Después de cada llamada a `OnPrepareDC`, el marco compruebe un miembro de la estructura de `CPrintInfo` denominada `m_bContinuePrinting`.  El valor predeterminado es **TRUE.** Si es así, el marco continúa el bucle de impresión.  Si se establece en **FALSE**, el marco se detiene.  Para realizar la paginación de IMPR\- Tiempo, la invalidación `OnPrepareDC` para comprobar si el final del documento se ha alcanzado, y el conjunto `m_bContinuePrinting` a **FALSE** cuando tiene.  
  
 La implementación predeterminada de los conjuntos `m_bContinuePrinting` de `OnPrepareDC` a **FALSE** si la página actual es mayor que 1.  Esto significa que si la longitud del documento no se ha especificado, el marco se supone que el documento es de longitud.  Una consecuencia de esto es que debería tener en cuenta si se llama a la versión de la clase base de `OnPrepareDC`.  No suponga que `m_bContinuePrinting` se **VERDADERO** después de llamar a la versión de la clase base.  
  
### ¿Sobre qué desea obtener más información?  
  
-   [Encabezados y pies de página](../mfc/headers-and-footers.md)  
  
-   [Asignar recursos de GDI](../mfc/allocating-gdi-resources.md)  
  
## Vea también  
 [Imprimir](../mfc/printing.md)   
 [CView Class](../mfc/reference/cview-class.md)   
 [CDC \(clase\)](../mfc/reference/cdc-class.md)