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
ms.openlocfilehash: cbea3e032932477006820c5a71fbbf3e40123bdf
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81322083"
---
# <a name="active-documents"></a>Documentos activos

Los documentos activos amplían la tecnología de documentos compuestos de OLE. Estas extensiones se proporcionan en forma de interfaces adicionales que administran vistas, de modo que los objetos pueden funcionar dentro de contenedores y, sin embargo, conservar el control sobre sus funciones de visualización e impresión. Este proceso permite mostrar documentos tanto en marcos externos (como Microsoft Office Binder o Microsoft Internet Explorer) como en marcos nativos (como los puertos de vista propios del producto).

En esta sección se describen las necesidades funcionales [de los documentos activos.](#requirements_for_active_documents) El documento activo posee un conjunto de datos y tiene acceso al almacenamiento donde se pueden guardar y recuperar los datos. Puede crear y administrar una o más vistas de sus datos. Además de admitir las interfaces habituales de incrustación y activación in situ de `IOleDocument`documentos OLE, el documento activo comunica su capacidad para crear vistas a través de . A través de esta interfaz, el contenedor puede solicitar crear (y posiblemente enumerar) las vistas que puede mostrar el documento activo. A través de esta interfaz, el documento activo también puede proporcionar información diversa sobre sí mismo, como si admite varias vistas o rectángulos complejos.

La siguiente `IOleDocument` es la interfaz. Tenga en `IEnumOleDocumentViews` cuenta que la `IOleDocumentView*` interfaz es un enumerador OLE estándar para los tipos.

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

Cada documento activo debe tener un proveedor de marco de vista con esta interfaz. Si el documento no está incrustado dentro de un contenedor, el propio servidor de documentos activo debe proporcionar el marco de vista. Sin embargo, cuando el documento activo está incrustado en un contenedor de documentos activo, el contenedor proporciona el marco de vista.

Un documento activo puede crear uno o varios tipos de [vistas](#requirements_for_view_objects) de sus datos (por ejemplo, normal, esquema, diseño de página, etc.). Las vistas actúan como filtros a través de los cuales se pueden ver los datos. Incluso si el documento solo tiene un tipo de vista, es posible que desee admitir varias vistas como medio de admitir la nueva funcionalidad de ventana (por ejemplo, el elemento **Nueva ventana** del menú **Ventana** de las aplicaciones de Office).

## <a name="requirements-for-active-documents"></a><a name="requirements_for_active_documents"></a>Requisitos para documentos activos

Un documento activo que se pueda visualizar en un contenedor de documentos activo debe:

- Utilice archivos compuestos de OLE como `IPersistStorage`su mecanismo de almacenamiento mediante la implementación de archivos .

- Admite las características básicas de incrustación de documentos OLE, incluida la opción Crear a **partir de archivos.** Esto requiere las `IPersistFile`interfaces `IOleObject`, `IDataObject`, y .

- Admite una o más vistas, cada una de las cuales es capaz de activarse in situ. Es decir, las vistas `IOleDocumentView` deben admitir la `IOleInPlaceObject` interfaz, así como las interfaces y `IOleInPlaceActiveObject` (mediante las interfaces `IOleInPlaceSite` y `IOleInPlaceFrame` el contenedor).

- Admite las interfaces `IOleDocument`de `IOleCommandTarget`documentos activas estándar, , y `IPrint`.

El conocimiento de cuándo y cómo utilizar las interfaces del lado contenedor está implícito en estos requisitos.

## <a name="requirements-for-view-objects"></a><a name="requirements_for_view_objects"></a>Requisitos para Ver objetos

Un documento activo puede crear una o varias vistas de sus datos. Funcionalmente, estas vistas son como puertos en un método determinado para mostrar los datos. Si un documento activo solo admite una sola vista, el documento activo y esa vista única se pueden implementar mediante una sola clase. `IOleDocument::CreateView`devuelve el puntero `IOleDocumentView` de interfaz del mismo objeto.

Para representarse dentro de un contenedor de `IOleInPlaceObject` documentos activo, un componente de vista debe admitir y `IOleInPlaceActiveObject` además `IOleDocumentView`de:

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

Cada vista tiene un sitio de vista asociado, que encapsula el marco de vista y el puerto de vista (HWND y un área rectangular en esa ventana). El sitio expone esta funcionalidad `IOleInPlaceSite` a través de la interfaz estándar. Tenga en cuenta que es posible tener más de un puerto de vista en un solo HWND.

Normalmente, cada tipo de vista tiene una representación impresa diferente. Por lo tanto, las vistas y los `IPrint` `IContinueCallback`sitios de vista correspondientes deben implementar las interfaces de impresión if y , respectivamente. El marco de vista debe `IPrint` negociar con el proveedor de vista a través de cuando comienza la impresión, de modo que los encabezados, pies de página, márgenes y elementos relacionados se imprimen correctamente. El proveedor de vista notifica el marco `IContinueCallback`de los eventos relacionados con la impresión a través de . Para obtener más información sobre el uso de estas interfaces, consulte [Impresión mediante programación](../mfc/programmatic-printing.md).

Tenga en cuenta que si un documento activo solo admite una sola vista, el documento activo y esa vista única se pueden implementar mediante una sola clase concreta. `IOleDocument::CreateView`simplemente devuelve el puntero `IOleDocumentView` de interfaz del mismo objeto. En resumen, no es necesario que haya dos instancias de objeto independientes cuando solo se requiere una vista.

Un objeto de vista también puede ser un destino de comando. Al `IOleCommandTarget` implementar una vista puede recibir comandos que se originan en la interfaz de usuario del contenedor (como **Nuevo**, **Abrir**, **Guardar como**, **Imprimir** en el menú **Archivo;** y **Copiar**, **Pegar**, **Deshacer** en el menú **Editar).** Para obtener más información, vea Control de mensajes y destinos de [comandos](../mfc/message-handling-and-command-targets.md).

## <a name="see-also"></a>Consulte también

[Contención de documentos activos](../mfc/active-document-containment.md)
