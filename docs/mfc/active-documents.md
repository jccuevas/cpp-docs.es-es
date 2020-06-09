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
ms.openlocfilehash: bfe91dcb42b97ddfbb0bf0be36a54b45e6dc0809
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625160"
---
# <a name="active-documents"></a>Documentos activos

Los documentos activos amplían la tecnología de documentos compuestos de OLE. Estas extensiones se proporcionan en forma de interfaces adicionales que administran vistas, de modo que los objetos pueden funcionar dentro de contenedores y mantener el control sobre sus funciones de visualización e impresión. Este proceso permite mostrar documentos en marcos externos (como el enlazador de Microsoft Office o Microsoft Internet Explorer) y en marcos nativos (como los puertos de vista propios del producto).

En esta sección se describen los [requisitos funcionales de los documentos activos](#requirements_for_active_documents). El documento activo posee un conjunto de datos y tiene acceso al almacenamiento donde se pueden guardar y recuperar los datos. Puede crear y administrar una o más vistas en sus datos. Además de admitir las interfaces de activación en contexto y de inserción habituales de documentos OLE, el documento activo comunica su capacidad para crear vistas a través de `IOleDocument` . A través de esta interfaz, el contenedor puede solicitar crear (y posiblemente enumerar) las vistas que el documento activo puede mostrar. A través de esta interfaz, el documento activo también puede proporcionar información diversa sobre sí mismo, por ejemplo, si admite varias vistas o rectángulos complejos.

A continuación se encuentra la `IOleDocument` interfaz. Tenga en cuenta que la `IEnumOleDocumentViews` interfaz es un enumerador OLE estándar para los `IOleDocumentView*` tipos.

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

Cada documento activo debe tener un proveedor de marco de vista con esta interfaz. Si el documento no está incrustado dentro de un contenedor, el propio servidor de documentos activo debe proporcionar el marco de la vista. Sin embargo, cuando el documento activo está incrustado en un contenedor de documentos activo, el contenedor proporciona el marco de la vista.

Un documento activo puede crear uno o varios tipos de [vistas](#requirements_for_view_objects) de sus datos (por ejemplo, normal, esquema, diseño de página, etc.). Las vistas actúan como filtros a través de los cuales se pueden ver los datos. Aunque el documento solo tenga un tipo de vista, es posible que desee admitir varias vistas como medio para admitir la nueva funcionalidad de ventana (por ejemplo, el nuevo elemento de **ventana** en el menú **ventana** de las aplicaciones de Office).

## <a name="requirements-for-active-documents"></a><a name="requirements_for_active_documents"></a>Requisitos para documentos activos

Un documento activo que se puede mostrar en un contenedor de documentos activo debe:

- Utilice los archivos compuestos de OLE como su mecanismo de almacenamiento implementando `IPersistStorage` .

- Admite las características básicas de incrustación de documentos OLE, incluido **Create from File**. Esto requiere las interfaces `IPersistFile` , `IOleObject` y `IDataObject` .

- Admite una o más vistas, cada una de las cuales es capaz de realizar la activación en contexto. Es decir, las vistas deben admitir la interfaz `IOleDocumentView` , así como las interfaces `IOleInPlaceObject` y `IOleInPlaceActiveObject` (mediante las `IOleInPlaceSite` interfaces y del contenedor `IOleInPlaceFrame` ).

- Admite las interfaces de documento activo estándar `IOleDocument` , `IOleCommandTarget` y `IPrint` .

La información sobre cuándo y cómo usar las interfaces del lado del contenedor está implícita en estos requisitos.

## <a name="requirements-for-view-objects"></a><a name="requirements_for_view_objects"></a>Requisitos para objetos de vista

Un documento activo puede crear una o más vistas de sus datos. Funcionalmente, estas vistas son como los puertos en un método determinado para mostrar los datos. Si un documento activo solo admite una sola vista, el documento activo y esa vista única se pueden implementar mediante una sola clase. `IOleDocument::CreateView`Devuelve el mismo puntero de `IOleDocumentView` interfaz del objeto.

Para que se represente en un contenedor de documentos activo, un componente de vista debe admitir `IOleInPlaceObject` y `IOleInPlaceActiveObject` además de `IOleDocumentView` :

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

Cada vista tiene un sitio de vista asociado, que encapsula el marco de la vista y el puerto de vista (HWND y un área rectangular en esa ventana). El sitio expone esta funcionalidad a través de la `IOleInPlaceSite` interfaz estándar. Tenga en cuenta que es posible tener más de un puerto de vista en un solo HWND.

Normalmente, cada tipo de vista tiene una representación impresa diferente. Por lo tanto, las vistas y los sitios de vista correspondientes deben implementar las interfaces de impresión si `IPrint` y `IContinueCallback` , respectivamente. El marco de la vista debe negociar con el proveedor de la vista a través del `IPrint` Inicio de la impresión, de modo que los encabezados, pies de página, márgenes y elementos relacionados se impriman correctamente. El proveedor de vistas notifica el marco de eventos relacionados con la impresión a través de `IContinueCallback` . Para obtener más información sobre el uso de estas interfaces, vea [impresión mediante programación](programmatic-printing.md).

Tenga en cuenta que si un documento activo solo admite una vista única, el documento activo y esa vista única se pueden implementar con una sola clase concreta. `IOleDocument::CreateView`simplemente devuelve el mismo puntero de `IOleDocumentView` interfaz del objeto. En Resumen, no es necesario que haya dos instancias de objeto independientes cuando solo se requiere una vista.

Un objeto de vista también puede ser un destino de comando. Al implementar `IOleCommandTarget` una vista, puede recibir comandos que se originan en la interfaz de usuario del contenedor (como **nuevo**, **abrir**, **Guardar como**, **Imprimir** en el menú **archivo** y **copiar**, **pegar**, **Deshacer** en el menú **edición** ). Para obtener más información, vea [control de mensajes y destinos de comandos](message-handling-and-command-targets.md).

## <a name="see-also"></a>Consulte también

[Contención de documentos activos](active-document-containment.md)
