---
title: Documentos activos | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- active documents [MFC]
- active documents [MFC], requirements
- view objects [MFC], requirements
- OLE [MFC], active documents
- views [MFC], active documents
- active documents [MFC], views
ms.assetid: 1378f18e-aaa6-420b-8501-4b974905baa0
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 52f3165f69d47f63fc52ae01bbbd1947e7755a43
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="active-documents"></a>Documentos activos
Documentos activos amplían la tecnología de documentos compuestos de OLE. Estas extensiones se proporcionan en forma de interfaces adicionales que administran vistas, para que funcione dentro de los contenedores y mantengan el control de su presentación y las funciones de impresión objetos. Este proceso permite mostrar documentos en marcos externos (por ejemplo, el enlazador de Microsoft Office o Microsoft Internet Explorer) y en marcos nativos (por ejemplo, los puertos de vista del producto).  
  
 Esta sección describe la funcional [requisitos para documentos activos](#requirements_for_active_documents). El documento activo posee un conjunto de datos y tiene acceso al almacenamiento donde se pueden guardar y recuperar los datos. Puede crear y administrar una o varias vistas en sus datos. Además de admitir la incrustación habitual y las interfaces de activación en contexto de documentos OLE, el documento activo comunica su capacidad para crear vistas a través de `IOleDocument`. Mediante esta interfaz, el contenedor puede pedir a crear (y posiblemente enumerar) en las vistas que puede mostrar el documento activo. A través de esta interfaz, el documento activo también puede proporcionar información diversa acerca de sí mismo, por ejemplo, si admite varias vistas o rectángulos complejos.  
  
 Éste es el **IOleDocument** interfaz. Tenga en cuenta que la **IEnumOleDocumentViews** interfaz es un enumerador OLE estándar para **IOleDocumentView \***  tipos.  
  
```  
interface IOleDocument : IUnknown  
    {  
    HRESULT CreateView(  
        [in] IOleInPlaceSite *pIPSite,  
        [in] IStream *pstm,  
        [in] DWORD dwReserved,  
        [out] IOleDocumentView **ppView);  

    HRESULT GetDocMiscStatus([out] DWORD *pdwStatus);  

    HRESULT EnumViews(  
        [out] IEnumOleDocumentViews **ppEnum,  
        [out] IOleDocumentView **ppView);  
    }  
```  
  
 Cada documento activo debe tener un proveedor de marco de vista con esta interfaz. Si el documento no se incrusta dentro de un contenedor, el propio servidor de documento activo debe proporcionar el marco de la vista. Sin embargo, cuando el documento activo está incrustado en un contenedor de documentos activos, el contenedor proporciona el marco de la vista.  
  
 Un documento activo puede crear uno o más tipos de [vistas](#requirements_for_view_objects) de sus datos (por ejemplo, normal, esquema, diseño de página y así sucesivamente). Las vistas actúan como filtros a través del cual se pueden ver los datos. Incluso si el documento tiene solo un tipo de vista, todavía puede admitir varias vistas como medio para admitir la nueva funcionalidad de la ventana (por ejemplo, el **nueva ventana** de elemento en el **ventana** menú de Office aplicaciones).  
  
##  <a name="requirements_for_active_documents"></a>Requisitos de documentos activos  
 Un documento activo que se pueden mostrar en un contenedor de documentos activos debe:  
  
-   Usar archivos compuestos de OLE como mecanismo de almacenamiento mediante la implementación de `IPersistStorage`.  
  
-   Admite las características básicas de incrustación de documentos OLE, incluida **crear desde archivo**. Esto requiere las interfaces `IPersistFile`, `IOleObject`, y `IDataObject`.  
  
-   Admite una o varias vistas, cada uno de los cuales es capaz de activación en contexto. Es decir, las vistas deben admitir la interfaz `IOleDocumentView` , así como las interfaces `IOleInPlaceObject` y `IOleInPlaceActiveObject` (usando el contenedor **IOleInPlaceSite** y **IOleInPlaceFrame** interfaces).  
  
-   Admite las interfaces estándar de documentos activos `IOleDocument`, `IOleCommandTarget`, y `IPrint`.  
  
 El conocimiento de cuándo y cómo usar las interfaces del contenedor está implícito en estos requisitos.  
  
##  <a name="requirements_for_view_objects"></a>Requisitos para los objetos de vista  
 Un documento activo puede crear una o varias vistas de sus datos. Funcionalmente, estas vistas son similares a los puertos a un método concreto para mostrar los datos. Si un documento activo sólo admite una vista única, el documento activo y esa vista solo se pueden implementar mediante una sola clase. **IOleDocument:: CreateView** devuelve el mismo objeto `IOleDocumentView` puntero de interfaz.  
  
 Para representar dentro de un contenedor de documentos activos, debe ser compatible con un componente de vista **IOleInPlaceObject** y **IOleInPlaceActiveObject** además `IOleDocumentView`:  
  
```  
interface IOleDocumentView : IUnknown  
    {  
    HRESULT SetInPlaceSite([in] IOleInPlaceSite *pIPSite);  
    HRESULT GetInPlaceSite([out] IOleInPlaceSite **ppIPSite);  
    HRESULT GetDocument([out] IUnknown **ppunk);  
    [input_sync] HRESULT SetRect([in] LPRECT prcView);  
    HRESULT GetRect([in] LPRECT prcView);  
    [input_sync] HRESULT SetRectComplex(  
        [in] LPRECT prcView,  
        [in] LPRECT prcHScroll,  
        [in] LPRECT prcVScroll,  
        [in] LPRECT prcSizeBox);  
    HRESULT Show([in] BOOL fShow);  
    HRESULT UIActivate([in] BOOL fUIActivate);  
    HRESULT Open(void);  
    HRESULT CloseView([in] DWORD dwReserved);  
    HRESULT SaveViewState([in] IStream *pstm);  
    HRESULT ApplyViewState([in] IStream *pstm);  
    HRESULT Clone(  
        [in] IOleInPlaceSite *pIPSiteNew,  
        [out] IOleDocumentView **ppViewNew);  
    }  
```  
  
 Cada vista tiene un sitio de vista asociado que encapsula el marco de la vista y el puerto de vista (HWND y un área rectangular en la ventana). El sitio expone esta funcionalidad mediante el estándar **IOleInPlaceSite** interfaz. Tenga en cuenta que es posible tener más de un puerto de vista en un solo HWND.  
  
 Normalmente, cada tipo de vista tiene una representación impresa diferente. Por lo tanto, las vistas y los sitios de vista correspondientes deben implementar las interfaces de impresión si `IPrint` y `IContinueCallback`, respectivamente. El marco de la vista debe negociar con el proveedor de vista a través de **IPrint** cuando comienza la impresión, para que los encabezados, pies de página, márgenes y elementos relacionados se impriman correctamente. El proveedor de vista notifica al marco los eventos relacionados con la impresión a través de `IContinueCallback`. Para obtener más información sobre el uso de estas interfaces, vea [imprimir mediante programación](../mfc/programmatic-printing.md).  
  
 Tenga en cuenta que si un documento activo sólo admite una sola vista, a continuación, el documento activo y esa vista se pueden implementar mediante una sola clase concreta. **IOleDocument:: CreateView** simplemente devuelve el mismo objeto `IOleDocumentView` puntero de interfaz. En resumen, no es necesario que haya dos instancias de un objeto independiente cuando se requiere una única vista.  
  
 Un objeto de vista también puede ser un destino del comando. Implementando `IOleCommandTarget` una vista puede recibir comandos que se originan en la interfaz de usuario del contenedor (como **New**, **abiertos**, **Guardar como**,  **Impresión** en el **archivo** menú; y **copia**, **pegar**, **deshacer** en el **editar** menú). Para obtener más información, consulte [control de mensajes y destinos de comando](../mfc/message-handling-and-command-targets.md).  
  
## <a name="see-also"></a>Vea también  
 [Contención de documentos activos](../mfc/active-document-containment.md)

