---
title: Documentos activos
ms.date: 11/04/2016
helpviewer_keywords:
- active documents [MFC]
- active documents [MFC], requirements
- view objects [MFC], requirements
- OLE [MFC], active documents
- views [MFC], active documents
- active documents [MFC], views
ms.assetid: 1378f18e-aaa6-420b-8501-4b974905baa0
ms.openlocfilehash: 519dd51ab9b46adf862999104e97c6e478ccd86b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62394954"
---
# <a name="active-documents"></a>Documentos activos

Documentos activos amplían la tecnología de documento compuesto de OLE. Estas extensiones se proporcionan en forma de interfaces adicionales que administran las vistas, para que pueden funcionar dentro de contenedores de objetos y se mantengan el control de su presentación y las funciones de impresión. Este proceso permite mostrar documentos en marcos externos (por ejemplo, el cuaderno de Microsoft Office o Microsoft Internet Explorer) y en marcos nativos (por ejemplo, los puertos de la vista del producto).

Esta sección describe la funcional [requisitos de documentos activos](#requirements_for_active_documents). El documento activo posee un conjunto de datos y tiene acceso al almacenamiento donde se pueden guardar y recuperar los datos. Puede crear y administrar una o varias vistas en sus datos. Además de admitir la incrustación habituales y las interfaces de activación en contexto de documentos OLE, el documento activo comunica con su capacidad para crear vistas a través de `IOleDocument`. Mediante esta interfaz, el contenedor puede pedir a crear (y posiblemente enumerar) en las vistas que puede mostrar el documento activo. Mediante esta interfaz, el documento activo también puede proporcionar información diversa sobre sí mismo, por ejemplo, si admite varias vistas o rectángulos complejos.

El siguiente es el `IOleDocument` interfaz. Tenga en cuenta que el `IEnumOleDocumentViews` interfaz es un enumerador OLE estándar para `IOleDocumentView*` tipos.

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

Cada documento activo debe tener un proveedor de marco de vista con esta interfaz. Si el documento no está incrustado en un contenedor, el propio servidor de documento activo debe proporcionar el marco de vista. Sin embargo, cuando el documento activo está incrustado en un contenedor de documentos activos, el contenedor proporciona el marco de vista.

Un documento activo puede crear uno o varios tipos de [vistas](#requirements_for_view_objects) de sus datos (por ejemplo, normal, de esquema, diseño de página y así sucesivamente). Las vistas actúan como filtros a través del cual se pueden ver los datos. Incluso si el documento tiene solo un tipo de vista, es posible que aún desea admitir varias vistas como un medio para que admita la nueva funcionalidad de ventana (por ejemplo, el **nueva ventana** de elemento en el **ventana** menú de Office aplicaciones).

##  <a name="requirements_for_active_documents"></a> Requisitos de documentos activos

Un documento activo que se puede mostrar en un contenedor de documentos activos debe:

- Usar archivos compuestos de OLE como mecanismo de almacenamiento mediante la implementación `IPersistStorage`.

- Admite las características básicas de incrustación de documentos OLE, incluida **crear desde archivo**. Esto requiere las interfaces `IPersistFile`, `IOleObject`, y `IDataObject`.

- Admite una o varias vistas, cada uno de los cuales es capaz de activación en contexto. Es decir, las vistas deben admitir la interfaz `IOleDocumentView` , así como las interfaces `IOleInPlaceObject` y `IOleInPlaceActiveObject` (mediante el contenedor `IOleInPlaceSite` y `IOleInPlaceFrame` interfaces).

- Admite las interfaces estándar de documentos activos `IOleDocument`, `IOleCommandTarget`, y `IPrint`.

El conocimiento de cuándo y cómo usar las interfaces del contenedor está implícito en estos requisitos.

##  <a name="requirements_for_view_objects"></a> Requisitos para los objetos de vista

Un documento activo puede crear una o varias vistas de sus datos. Funcionalmente, estas vistas son como puertos de un método concreto para mostrar los datos. Si un documento activo sólo admite una sola vista, el documento activo y esa vista solo pueden implementarse mediante una sola clase. `IOleDocument::CreateView` Devuelve el mismo objeto `IOleDocumentView` puntero de interfaz.

Para que se puede representar dentro de un contenedor de documentos activos, debe ser compatible con un componente de vista `IOleInPlaceObject` y `IOleInPlaceActiveObject` además `IOleDocumentView`:

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

Cada vista tiene un sitio de vista asociada, que encapsula el marco de vista y el puerto de la vista (HWND y un área rectangular en la ventana). El sitio expone esta funcionalidad mediante el estándar `IOleInPlaceSite` interfaz. Tenga en cuenta que es posible tener más de un puerto de vista en un solo HWND.

Normalmente, cada tipo de vista tiene una representación impresa diferente. Por lo tanto, las vistas y los sitios correspondientes de la vista deben implementar las interfaces de impresión si `IPrint` y `IContinueCallback`, respectivamente. El marco de vista debe negociar con el proveedor de vista a través de `IPrint` cuando comienza la impresión, para que los encabezados, pies de página, márgenes y elementos relacionados se impriman correctamente. El proveedor de la vista notifica al marco los eventos relacionados con la impresión a través de `IContinueCallback`. Para obtener más información sobre el uso de estas interfaces, vea [imprimir mediante programación](../mfc/programmatic-printing.md).

Tenga en cuenta que si un documento activo sólo admite una sola vista, a continuación, el documento activo y esa vista pueden implementarse mediante una clase concreta individual. `IOleDocument::CreateView` simplemente devuelve el mismo objeto `IOleDocumentView` puntero de interfaz. En pocas palabras, no es necesario que haya dos instancias de objeto independiente cuando se requiere sólo una vista.

Un objeto de vista también puede ser un destino de comando. Implementando `IOleCommandTarget` una vista puede recibir comandos que se originan en la interfaz de usuario del contenedor (como **New**, **abierto**, **Guardar como**,  **Impresión** en el **archivo** menú; y **copia**, **pegar**, **deshacer** en el **editar** menú). Para obtener más información, consulte [de mensajes y destinos de comando](../mfc/message-handling-and-command-targets.md).

## <a name="see-also"></a>Vea también

[Contención de documentos activos](../mfc/active-document-containment.md)
