---
title: Clase COleServerDoc
ms.date: 11/04/2016
f1_keywords:
- COleServerDoc
- AFXOLE/COleServerDoc
- AFXOLE/COleServerDoc::COleServerDoc
- AFXOLE/COleServerDoc::ActivateDocObject
- AFXOLE/COleServerDoc::ActivateInPlace
- AFXOLE/COleServerDoc::DeactivateAndUndo
- AFXOLE/COleServerDoc::DiscardUndoState
- AFXOLE/COleServerDoc::GetClientSite
- AFXOLE/COleServerDoc::GetEmbeddedItem
- AFXOLE/COleServerDoc::GetItemClipRect
- AFXOLE/COleServerDoc::GetItemPosition
- AFXOLE/COleServerDoc::GetZoomFactor
- AFXOLE/COleServerDoc::IsDocObject
- AFXOLE/COleServerDoc::IsEmbedded
- AFXOLE/COleServerDoc::IsInPlaceActive
- AFXOLE/COleServerDoc::NotifyChanged
- AFXOLE/COleServerDoc::NotifyClosed
- AFXOLE/COleServerDoc::NotifyRename
- AFXOLE/COleServerDoc::NotifySaved
- AFXOLE/COleServerDoc::OnDeactivate
- AFXOLE/COleServerDoc::OnDeactivateUI
- AFXOLE/COleServerDoc::OnDocWindowActivate
- AFXOLE/COleServerDoc::OnResizeBorder
- AFXOLE/COleServerDoc::OnShowControlBars
- AFXOLE/COleServerDoc::OnUpdateDocument
- AFXOLE/COleServerDoc::RequestPositionChange
- AFXOLE/COleServerDoc::SaveEmbedding
- AFXOLE/COleServerDoc::ScrollContainerBy
- AFXOLE/COleServerDoc::UpdateAllItems
- AFXOLE/COleServerDoc::CreateInPlaceFrame
- AFXOLE/COleServerDoc::DestroyInPlaceFrame
- AFXOLE/COleServerDoc::GetDocObjectServer
- AFXOLE/COleServerDoc::OnClose
- AFXOLE/COleServerDoc::OnExecOleCmd
- AFXOLE/COleServerDoc::OnFrameWindowActivate
- AFXOLE/COleServerDoc::OnGetEmbeddedItem
- AFXOLE/COleServerDoc::OnReactivateAndUndo
- AFXOLE/COleServerDoc::OnSetHostNames
- AFXOLE/COleServerDoc::OnSetItemRects
- AFXOLE/COleServerDoc::OnShowDocument
helpviewer_keywords:
- COleServerDoc [MFC], COleServerDoc
- COleServerDoc [MFC], ActivateDocObject
- COleServerDoc [MFC], ActivateInPlace
- COleServerDoc [MFC], DeactivateAndUndo
- COleServerDoc [MFC], DiscardUndoState
- COleServerDoc [MFC], GetClientSite
- COleServerDoc [MFC], GetEmbeddedItem
- COleServerDoc [MFC], GetItemClipRect
- COleServerDoc [MFC], GetItemPosition
- COleServerDoc [MFC], GetZoomFactor
- COleServerDoc [MFC], IsDocObject
- COleServerDoc [MFC], IsEmbedded
- COleServerDoc [MFC], IsInPlaceActive
- COleServerDoc [MFC], NotifyChanged
- COleServerDoc [MFC], NotifyClosed
- COleServerDoc [MFC], NotifyRename
- COleServerDoc [MFC], NotifySaved
- COleServerDoc [MFC], OnDeactivate
- COleServerDoc [MFC], OnDeactivateUI
- COleServerDoc [MFC], OnDocWindowActivate
- COleServerDoc [MFC], OnResizeBorder
- COleServerDoc [MFC], OnShowControlBars
- COleServerDoc [MFC], OnUpdateDocument
- COleServerDoc [MFC], RequestPositionChange
- COleServerDoc [MFC], SaveEmbedding
- COleServerDoc [MFC], ScrollContainerBy
- COleServerDoc [MFC], UpdateAllItems
- COleServerDoc [MFC], CreateInPlaceFrame
- COleServerDoc [MFC], DestroyInPlaceFrame
- COleServerDoc [MFC], GetDocObjectServer
- COleServerDoc [MFC], OnClose
- COleServerDoc [MFC], OnExecOleCmd
- COleServerDoc [MFC], OnFrameWindowActivate
- COleServerDoc [MFC], OnGetEmbeddedItem
- COleServerDoc [MFC], OnReactivateAndUndo
- COleServerDoc [MFC], OnSetHostNames
- COleServerDoc [MFC], OnSetItemRects
- COleServerDoc [MFC], OnShowDocument
ms.assetid: a9cdd96a-e0ac-43bb-9203-2c29237e965c
ms.openlocfilehash: b535cc23901ba39e4beeb66d8ca6bb18d4abe2b8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376127"
---
# <a name="coleserverdoc-class"></a>Clase COleServerDoc

La clase base para los documentos de servidor OLE.

## <a name="syntax"></a>Sintaxis

```
class AFX_NOVTABLE COleServerDoc : public COleLinkingDoc
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[COleServerDoc::COleServerDoc](#coleserverdoc)|Construye un objeto `COleServerDoc`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[COleServerDoc::ActivateDocObject](#activatedocobject)|Activa el documento DocObject asociado.|
|[COleServerDoc::ActivateInPlace](#activateinplace)|Activa el documento para la edición in situ.|
|[COleServerDoc::DeactivateAndUndo](#deactivateandundo)|Desactiva la interfaz de usuario del servidor.|
|[COleServerDoc::DiscardUndoState](#discardundostate)|Descarta la información de deshacer estado.|
|[COleServerDoc::GetClientSite](#getclientsite)|Recupera un puntero a `IOleClientSite` la interfaz subyacente.|
|[COleServerDoc::GetEmbeddedItem](#getembeddeditem)|Devuelve un puntero a un elemento que representa todo el documento.|
|[COleServerDoc::GetItemClipRect](#getitemcliprect)|Devuelve el rectángulo delimitador actual para la edición in situ.|
|[COleServerDoc::GetItemPosition](#getitemposition)|Devuelve el rectángulo de posición actual, en relación con el área de cliente de la aplicación contenedora, para la edición in situ.|
|[COleServerDoc::GetZoomFactor](#getzoomfactor)|Devuelve el factor de zoom en píxeles.|
|[COleServerDoc::IsDocObject](#isdocobject)|Determina si el documento es un DocObject.|
|[COleServerDoc::IsEmbedded](#isembedded)|Indica si el documento está incrustado en un documento contenedor o en ejecución de forma independiente.|
|[COleServerDoc::IsInPlaceActive](#isinplaceactive)|Devuelve TRUE si el elemento está activado actualmente en su lugar.|
|[COleServerDoc::NotifyChanged](#notifychanged)|Notifica a los contenedores que el usuario ha cambiado el documento.|
|[COleServerDoc::NotifyClosed](#notifyclosed)|Notifica a los contenedores que el usuario ha cerrado el documento.|
|[COleServerDoc::NotifyRename](#notifyrename)|Notifica a los contenedores que el usuario ha cambiado el nombre del documento.|
|[COleServerDoc::NotifySaved](#notifysaved)|Notifica a los contenedores que el usuario ha guardado el documento.|
|[COleServerDoc::OnDeactivate](#ondeactivate)|Llamado por el marco de trabajo cuando el usuario desactiva un elemento que se activó en su lugar.|
|[COleServerDoc::OnDeactivateUI](#ondeactivateui)|Llamado por el marco de trabajo para destruir controles y otros elementos de interfaz de usuario creados para la activación en contexto.|
|[COleServerDoc::OnDocWindowActivate](#ondocwindowactivate)|Llamado por el marco de trabajo cuando se activa o desactiva la ventana de marco de documento del contenedor.|
|[COleServerDoc::OnResizeBorder](#onresizeborder)|Llamado por el marco de trabajo cuando se cambia el tamaño de la ventana de marco o la ventana de documento de la aplicación contenedora.|
|[COleServerDoc::OnShowControlBars](#onshowcontrolbars)|Llamado por el marco de trabajo para mostrar u ocultar barras de control para la edición in situ.|
|[COleServerDoc::OnUpdateDocument](#onupdatedocument)|Llamado por el marco de trabajo cuando se guarda un documento de servidor que es un elemento incrustado, actualizando la copia del contenedor del elemento.|
|[COleServerDoc::RequestPositionChange](#requestpositionchange)|Cambia la posición del marco de edición in situ.|
|[COleServerDoc::SaveEmbedding](#saveembedding)|Indica a la aplicación contenedora que guarde el documento.|
|[COleServerDoc::ScrollContainerBy](#scrollcontainerby)|Desplaza el documento contenedor.|
|[COleServerDoc::UpdateAllItems](#updateallitems)|Notifica a los contenedores que el usuario ha cambiado el documento.|

### <a name="protected-methods"></a>Métodos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[COleServerDoc::CreateInPlaceFrame](#createinplaceframe)|Llamado por el marco de trabajo para crear una ventana de marco para la edición in situ.|
|[COleServerDoc::DestroyInPlaceFrame](#destroyinplaceframe)|Llamado por el marco de trabajo para destruir una ventana de marco para la edición in situ.|
|[COleServerDoc::GetDocObjectServer](#getdocobjectserver)|Reemplace esta función `CDocObjectServer` para crear un nuevo objeto e indique que este documento es un contenedor DocObject.|
|[COleServerDoc::OnClose](#onclose)|Llamado por el marco de trabajo cuando un contenedor solicita cerrar el documento.|
|[COleServerDoc::OnExecOleCmd](#onexecolecmd)|Ejecuta un comando especificado o muestra ayuda para el comando.|
|[COleServerDoc::OnFrameWindowActivate](#onframewindowactivate)|Llamado por el marco de trabajo cuando se activa o desactiva la ventana de marco del contenedor.|
|[COleServerDoc::OnGetEmbeddedItem](#ongetembeddeditem)|Llamado para `COleServerItem` obtener un que representa todo el documento; para obtener un elemento incrustado. Se requiere implementación.|
|[COleServerDoc::OnReactivateAndUndo](#onreactivateandundo)|Llamado por el marco de trabajo para deshacer los cambios realizados durante la edición in situ.|
|[COleServerDoc::OnSetHostNames](#onsethostnames)|Llamado por el marco de trabajo cuando un contenedor establece el título de la ventana para un objeto incrustado.|
|[COleServerDoc::OnSetItemRects](#onsetitemrects)|Llamado por el marco de trabajo para colocar la ventana de marco de edición in situ dentro de la ventana de la aplicación contenedora.|
|[COleServerDoc::OnShowDocument](#onshowdocument)|Llamado por el marco de trabajo para mostrar u ocultar el documento.|

## <a name="remarks"></a>Observaciones

Un documento de servidor puede contener [COleServerItem](../../mfc/reference/coleserveritem-class.md) objetos, que representan la interfaz de servidor para elementos incrustados o vinculados. Cuando un contenedor inicia una aplicación de servidor para editar un elemento incrustado, el elemento se carga como su propio documento de servidor; el `COleServerDoc` objeto contiene `COleServerItem` un solo objeto, que consta de todo el documento. Cuando un contenedor inicia una aplicación de servidor para editar un elemento vinculado, se carga un documento existente desde el disco; una parte del contenido del documento se resalta para indicar el elemento vinculado.

`COleServerDoc`objetos también pueden contener elementos de la [COleClientItem](../../mfc/reference/coleclientitem-class.md) clase. Esto le permite crear aplicaciones de servidor de contenedor. El marco de trabajo `COleClientItem` proporciona funciones `COleServerItem` para almacenar correctamente los elementos mientras se dan servicio a los objetos.

Si la aplicación de servidor no admite vínculos, un documento de servidor siempre contendrá solo un elemento de servidor, que representa todo el objeto incrustado como documento. Si la aplicación de servidor admite vínculos, debe crear un elemento de servidor cada vez que se copie una selección en el Portapapeles.

Para `COleServerDoc`usar , derive una clase de ella e implemente la función miembro [OnGetEmbeddedItem,](#ongetembeddeditem) que permite que el servidor admita elementos incrustados. Derive una `COleServerItem` clase de la que implementar los elementos `OnGetEmbeddedItem`de los documentos y devuelva objetos de esa clase desde .

Para admitir elementos vinculados, `COleServerDoc` proporciona el [OnGetLinkedItem](../../mfc/reference/colelinkingdoc-class.md#ongetlinkeditem) función miembro. Puede usar la implementación predeterminada o invalidarla si tiene su propia forma de administrar elementos de documento.

Necesita una `COleServerDoc`clase derivada para cada tipo de documento de servidor compatible con la aplicación. Por ejemplo, si la aplicación de servidor admite `COleServerDoc`hojas de cálculo y gráficos, necesita dos clases derivadas.

Para obtener más información sobre los servidores, consulte el artículo [Servidores: implementar un servidor](../../mfc/servers-implementing-a-server.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocument](../../mfc/reference/cdocument-class.md)

[COleDocument](../../mfc/reference/coledocument-class.md)

[COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)

`COleServerDoc`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxole.h

## <a name="coleserverdocactivatedocobject"></a><a name="activatedocobject"></a>COleServerDoc::ActivateDocObject

Activa el documento DocObject asociado.

```
void ActivateDocObject();
```

### <a name="remarks"></a>Observaciones

De forma `COleServerDoc` predeterminada, no admite documentos activos (también denominados DocObjects). Para habilitar esta compatibilidad, vea [GetDocObjectServer](#getdocobjectserver) y la clase [CDocObjectServer](../../mfc/reference/cdocobjectserver-class.md).

## <a name="coleserverdocactivateinplace"></a><a name="activateinplace"></a>COleServerDoc::ActivateInPlace

Activa el elemento para la edición in situ.

```
BOOL ActivateInPlace();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se realiza correctamente; de lo contrario 0, lo que indica que el elemento está completamente abierto.

### <a name="remarks"></a>Observaciones

Esta función realiza todas las operaciones necesarias para la activación in situ. Crea una ventana de marco in situ, la activa y la dimensiona en el elemento, configura menús compartidos y otros controles, desplaza el elemento a la vista y establece el foco en la ventana de marco in situ.

La implementación predeterminada de [COleServerItem::OnShow](../../mfc/reference/coleserveritem-class.md#onshow)llama a esta función. Llame a esta función si la aplicación admite otro verbo para la activación en contexto (como Reproducir).

## <a name="coleserverdoccoleserverdoc"></a><a name="coleserverdoc"></a>COleServerDoc::COleServerDoc

Construye un `COleServerDoc` objeto sin conectarse con los archivos DLL del sistema OLE.

```
COleServerDoc();
```

### <a name="remarks"></a>Observaciones

Debe llamar a [COleLinkingDoc::Register](../../mfc/reference/colelinkingdoc-class.md#register) para abrir comunicaciones con OLE. Si usa [COleTemplateServer](../../mfc/reference/coletemplateserver-class.md) en la `COleLinkingDoc::Register` aplicación, se `COleLinkingDoc`llama por `OnNewDocument` `OnOpenDocument`la `OnSaveDocument`implementación de , , y .

## <a name="coleserverdoccreateinplaceframe"></a><a name="createinplaceframe"></a>COleServerDoc::CreateInPlaceFrame

El marco de trabajo llama a esta función para crear una ventana de marco para la edición in situ.

```
virtual COleIPFrameWnd* CreateInPlaceFrame(CWnd* pParentWnd);
```

### <a name="parameters"></a>Parámetros

*pParentWnd*<br/>
Puntero a la ventana primaria de la aplicación contenedora.

### <a name="return-value"></a>Valor devuelto

Un puntero a la ventana de marco en su lugar, o NULL si no se realiza correctamente.

### <a name="remarks"></a>Observaciones

La implementación predeterminada utiliza la información especificada en la plantilla de documento para crear el marco. La vista utilizada es la primera vista creada para el documento. Esta vista se separa temporalmente del marco original y se adjunta al marco recién creado.

Este es un avanzado reemplazable.

## <a name="coleserverdocdeactivateandundo"></a><a name="deactivateandundo"></a>COleServerDoc::DeactivateAndUndo

Llame a esta función si la aplicación admite Deshacer y el usuario elige Deshacer después de activar un elemento, pero antes de editarlo.

```
BOOL DeactivateAndUndo();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero en caso de éxito; en caso contrario, es 0.

### <a name="remarks"></a>Observaciones

Si la aplicación contenedora se escribe mediante la biblioteca Microsoft Foundation Class, llamar a esta función hace que [cOleClientItem::OnDeactivateAndUndo](../../mfc/reference/coleclientitem-class.md#ondeactivateandundo) se llame, lo que desactiva la interfaz de usuario del servidor.

## <a name="coleserverdocdestroyinplaceframe"></a><a name="destroyinplaceframe"></a>COleServerDoc::DestroyInPlaceFrame

El marco de trabajo llama a esta función para destruir una ventana de marco en contexto y devolver la ventana de documento de la aplicación de servidor a su estado antes de la activación en contexto.

```
virtual void DestroyInPlaceFrame(COleIPFrameWnd* pFrameWnd);
```

### <a name="parameters"></a>Parámetros

*pFrameWnd*<br/>
Puntero a la ventana de marco in situ que se va a destruir.

### <a name="remarks"></a>Observaciones

Este es un avanzado reemplazable.

## <a name="coleserverdocdiscardundostate"></a><a name="discardundostate"></a>COleServerDoc::DiscardUndoState

Si el usuario realiza una operación de edición que no se puede deshacer, llame a esta función para forzar a la aplicación contenedora a descartar su información de estado de deshacer.

```
BOOL DiscardUndoState();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero en caso de éxito; en caso contrario, es 0.

### <a name="remarks"></a>Observaciones

Esta función se proporciona para que los servidores que admiten Deshacer puedan liberar recursos que, de lo contrario, se consumirían mediante información de estado de deshacer que no se puede usar.

## <a name="coleserverdocgetclientsite"></a><a name="getclientsite"></a>COleServerDoc::GetClientSite

Recupera un puntero a `IOleClientSite` la interfaz subyacente.

```
LPOLECLIENTSITE GetClientSite() const;
```

### <a name="return-value"></a>Valor devuelto

Recupera un puntero a la subyacente [IOleClientSite](/windows/win32/api/oleidl/nn-oleidl-ioleclientsite) interfaz.

## <a name="coleserverdocgetdocobjectserver"></a><a name="getdocobjectserver"></a>COleServerDoc::GetDocObjectServer

Reemplace esta función `CDocObjectServer` para crear un nuevo elemento y devolver le devuelva un puntero.

```
virtual CDocObjectServer* GetDocObjectServer(LPOLEDOCUMENTSITE pDocSite);
```

### <a name="parameters"></a>Parámetros

*pDocSite*<br/>
Puntero a `IOleDocumentSite` la interfaz que conectará este documento al servidor.

### <a name="return-value"></a>Valor devuelto

Un puntero `CDocObjectServer`a un ; NULL si se produce un error en la operación.

### <a name="remarks"></a>Observaciones

Cuando se activa un servidor DocObject, la devolución de un puntero no NULL muestra que el cliente puede admitir DocObjects. La implementación predeterminada devuelve NULL.

Una implementación típica para un documento que `CDocObjectServer` admite DocObjects simplemente asignará un nuevo objeto y lo devolverá al autor de la llamada. Por ejemplo:

[!code-cpp[NVC_MFCOleServer#3](../../mfc/codesnippet/cpp/coleserverdoc-class_1.cpp)]

## <a name="coleserverdocgetembeddeditem"></a><a name="getembeddeditem"></a>COleServerDoc::GetEmbeddedItem

Llame a esta función para obtener un puntero a un elemento que representa todo el documento.

```
COleServerItem* GetEmbeddedItem();
```

### <a name="return-value"></a>Valor devuelto

Un puntero a un elemento que representa todo el documento; NULL si se produce un error en la operación.

### <a name="remarks"></a>Observaciones

Llama a [COleServerDoc::OnGetEmbeddedItem](#ongetembeddeditem), una función virtual sin implementación predeterminada.

## <a name="coleserverdocgetitemcliprect"></a><a name="getitemcliprect"></a>COleServerDoc::GetItemClipRect

Llame `GetItemClipRect` a la función miembro para obtener las coordenadas de rectángulo de recorte del elemento que se está editando en su lugar.

```
void GetItemClipRect(LPRECT lpClipRect) const;
```

### <a name="parameters"></a>Parámetros

*lpClipRect*<br/>
Puntero a `RECT` una `CRect` estructura o un objeto para recibir las coordenadas de rectángulo de recorte del elemento.

### <a name="remarks"></a>Observaciones

Las coordenadas están en píxeles en relación con el área de cliente de la ventana de aplicación contenedora.

El dibujo no debe producirse fuera del rectángulo delimitador. Normalmente, el dibujo se restringe automáticamente. Utilice esta función para determinar si el usuario se ha desplazado fuera de la parte visible del documento; si es así, desplácese por el documento contenedor según sea necesario mediante una llamada a [ScrollContainerBy](#scrollcontainerby).

## <a name="coleserverdocgetitemposition"></a><a name="getitemposition"></a>COleServerDoc::GetItemPosition

Llame `GetItemPosition` a la función miembro para obtener las coordenadas del elemento que se está editando en su lugar.

```
void GetItemPosition(LPRECT lpPosRect) const;
```

### <a name="parameters"></a>Parámetros

*lpPosRect*<br/>
Puntero a `RECT` una `CRect` estructura u objeto para recibir las coordenadas del elemento.

### <a name="remarks"></a>Observaciones

Las coordenadas están en píxeles en relación con el área de cliente de la ventana de aplicación contenedora.

La posición del elemento se puede comparar con el rectángulo delimitador actual para determinar la medida en que el elemento está visible (o no visible) en la pantalla.

## <a name="coleserverdocgetzoomfactor"></a><a name="getzoomfactor"></a>COleServerDoc::GetZoomFactor

La `GetZoomFactor` función miembro determina el "factor de zoom" de un elemento que se ha activado para la edición in situ.

```
BOOL GetZoomFactor(
    LPSIZE lpSizeNum = NULL,
    LPSIZE lpSizeDenom = NULL,
    LPCRECT lpPosRect = NULL) const;
```

### <a name="parameters"></a>Parámetros

*lpSizeNum*<br/>
Puntero a un `CSize` objeto de clase que contendrá el numerador del factor de zoom. Puede ser NULL.

*lpSizeDenom*<br/>
Puntero a un `CSize` objeto de clase que contendrá el denominador del factor de zoom. Puede ser NULL.

*lpPosRect*<br/>
Puntero a un `CRect` objeto de clase que describe la nueva posición del elemento. Si este argumento es NULL, la función utiliza la posición actual del elemento.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el elemento está activado para la edición in situ y su factor de zoom es distinto del 100% (1:1); de lo contrario 0.

### <a name="remarks"></a>Observaciones

El factor de zoom, en píxeles, es la proporción del tamaño del elemento a su extensión actual. Si la aplicación contenedora no ha establecido la extensión del elemento, se utiliza su extensión natural (según lo determinado por [COleServerItem::OnGetExtent](../../mfc/reference/coleserveritem-class.md#ongetextent)).

La función establece sus dos primeros argumentos en el numerador y denominador del "factor de zoom" del elemento. Si el elemento no se está editando en su lugar, la función establece estos argumentos en un valor predeterminado de 100% (o 1:1) y devuelve cero. Para obtener más información, vea Nota técnica 40, Cambio de tamaño y zoom in [situ MFC/OLE](../../mfc/tn040-mfc-ole-in-place-resizing-and-zooming.md).

## <a name="coleserverdocisdocobject"></a><a name="isdocobject"></a>COleServerDoc::IsDocObject

Determina si el documento es un DocObject.

```
BOOL IsDocObject() const;
```

### <a name="return-value"></a>Valor devuelto

TRUESi el documento es un DocObject; de lo contrario FALSO.

## <a name="coleserverdocisembedded"></a><a name="isembedded"></a>COleServerDoc::IsEmbedded

Llame `IsEmbedded` a la función miembro para determinar si el documento representa un objeto incrustado en un contenedor.

```
BOOL IsEmbedded() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de `COleServerDoc` cero si el objeto es un documento que representa un objeto incrustado en un contenedor; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Un documento cargado desde un archivo no está incrustado aunque puede ser manipulado por una aplicación contenedora como un vínculo. Un documento incrustado en un documento contenedor se considera incrustado.

## <a name="coleserverdocisinplaceactive"></a><a name="isinplaceactive"></a>COleServerDoc::IsInPlaceActive

Llame `IsInPlaceActive` a la función miembro para determinar si el elemento está actualmente en el estado activo en el lugar.

```
BOOL IsInPlaceActive() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de `COleServerDoc` cero si el objeto está activo en su lugar; de lo contrario 0.

## <a name="coleserverdocnotifychanged"></a><a name="notifychanged"></a>COleServerDoc::NotifyChanged

Llame a esta función para notificar a todos los elementos vinculados conectados al documento que el documento ha cambiado.

```
void NotifyChanged();
```

### <a name="remarks"></a>Observaciones

Normalmente, se llama a esta función después de que el usuario cambie algún atributo global, como las dimensiones del documento de servidor. Si un elemento OLE está vinculado al documento con un vínculo automático, el elemento se actualiza para reflejar los cambios. En las aplicaciones contenedoras escritas con la biblioteca `COleClientItem` Microsoft Foundation Class, se llama a la función miembro [OnChange](../../mfc/reference/coleclientitem-class.md#onchange) de .

> [!NOTE]
> Esta función se incluye por compatibilidad con OLE 1. Las nuevas aplicaciones deben usar [UpdateAllItems](#updateallitems).

## <a name="coleserverdocnotifyclosed"></a><a name="notifyclosed"></a>COleServerDoc::NotifyClosed

Llame a esta función para notificar a los contenedores que el documento se ha cerrado.

```
void NotifyClosed();
```

### <a name="remarks"></a>Observaciones

Cuando el usuario elige el cerrar comando `NotifyClosed` desde `COleServerDoc`el archivo menú, se llama mediante 's implementación de la [OnCloseDocument](../../mfc/reference/cdocument-class.md#onclosedocument) función miembro. En las aplicaciones contenedoras escritas con la biblioteca `COleClientItem` Microsoft Foundation Class, se llama a la función miembro [OnChange](../../mfc/reference/coleclientitem-class.md#onchange) de .

## <a name="coleserverdocnotifyrename"></a><a name="notifyrename"></a>COleServerDoc::NotifyRename

Llame a esta función después de que el usuario cambie el nombre del documento de servidor.

```
void NotifyRename(LPCTSTR lpszNewName);
```

### <a name="parameters"></a>Parámetros

*lpszNewName*<br/>
Puntero a una cadena que especifica el nuevo nombre del documento de servidor; esto es típicamente una ruta totalmente calificada.

### <a name="remarks"></a>Observaciones

Cuando el usuario elige el guardar como `NotifyRename` comando desde `COleServerDoc`el archivo menú, se llama mediante 's implementación de la [OnSaveDocument](../../mfc/reference/cdocument-class.md#onsavedocument) función miembro. Esta función notifica a los archivos DLL del sistema OLE, que a su vez notifican a los contenedores. En las aplicaciones contenedoras escritas con la biblioteca `COleClientItem` Microsoft Foundation Class, se llama a la función miembro [OnChange](../../mfc/reference/coleclientitem-class.md#onchange) de .

## <a name="coleserverdocnotifysaved"></a><a name="notifysaved"></a>COleServerDoc::NotifySaved

Llame a esta función después de que el usuario guarde el documento del servidor.

```
void NotifySaved();
```

### <a name="remarks"></a>Observaciones

Cuando el usuario elige el comando Guardar `NotifySaved` en el `COleServerDoc`menú Archivo, se llama automáticamente por la implementación de [OnSaveDocument](../../mfc/reference/cdocument-class.md#onsavedocument). Esta función notifica a los archivos DLL del sistema OLE, que a su vez notifican a los contenedores. En las aplicaciones contenedoras escritas con la biblioteca `COleClientItem` Microsoft Foundation Class, se llama a la función miembro [OnChange](../../mfc/reference/coleclientitem-class.md#onchange) de .

## <a name="coleserverdoconclose"></a><a name="onclose"></a>COleServerDoc::OnClose

Llamado por el marco de trabajo cuando un contenedor solicita que se cierre el documento de servidor.

```
virtual void OnClose(OLECLOSE dwCloseOption);
```

### <a name="parameters"></a>Parámetros

*dwCloseOption*<br/>
Un valor de la enumeración OLECLOSE. Este parámetro puede tener uno de los valores siguientes:

- OLECLOSE_SAVEIFDIRTY El archivo se guarda si se ha modificado.

- OLECLOSE_NOSAVE El archivo se cierra sin guardarse.

- OLECLOSE_PROMPTSAVE Si se ha modificado el archivo, se le pedirá al usuario que lo guarde.

### <a name="remarks"></a>Observaciones

La implementación `CDocument::OnCloseDocument`predeterminada llama a .

Para obtener más información y valores adicionales, vea [OLECLOSE](/windows/win32/api/oleidl/ne-oleidl-oleclose) en el Windows SDK.

## <a name="coleserverdocondeactivate"></a><a name="ondeactivate"></a>COleServerDoc::OnDeactivate

Llamado por el marco de trabajo cuando el usuario desactiva un elemento incrustado o vinculado que está activo actualmente en su lugar.

```
virtual void OnDeactivate();
```

### <a name="remarks"></a>Observaciones

Esta función restaura la interfaz de usuario de la aplicación contenedora a su estado original y destruye los menús y otros controles creados para la activación en contexto.

La información del estado de deshacer debe publicarse incondicionalmente en este momento.

Para obtener más información, consulte el artículo [Activación](../../mfc/activation-cpp.md)..

## <a name="coleserverdocondeactivateui"></a><a name="ondeactivateui"></a>COleServerDoc::OnDeactivateUI

Se llama cuando el usuario desactiva un elemento que se activó en su lugar.

```
virtual void OnDeactivateUI(BOOL bUndoable);
```

### <a name="parameters"></a>Parámetros

*bUndoable*<br/>
Especifica si los cambios de edición se pueden deshacer.

### <a name="remarks"></a>Observaciones

Esta función restaura la interfaz de usuario de la aplicación contenedora a su estado original, ocultando los menús y otros controles que se crearon para la activación en contexto.

El marco de trabajo siempre establece *bUndoable* en FALSE. Si el servidor admite deshacer y hay una operación que se puede deshacer, llame a la implementación de clase base con *bUndoable* establecido en TRUE.

## <a name="coleserverdocondocwindowactivate"></a><a name="ondocwindowactivate"></a>COleServerDoc::OnDocWindowActivate

El marco de trabajo llama a esta función para activar o desactivar una ventana de documento para la edición in situ.

```
virtual void OnDocWindowActivate(BOOL bActivate);
```

### <a name="parameters"></a>Parámetros

*bActivar*<br/>
Especifica si la ventana del documento se va a activar o desactivar.

### <a name="remarks"></a>Observaciones

La implementación predeterminada quita o agrega los elementos de la interfaz de usuario de nivel de marco según corresponda. Reemplace esta función si desea realizar acciones adicionales cuando el documento que contiene el elemento está activado o desactivado.

Para obtener más información, consulte el artículo [Activación](../../mfc/activation-cpp.md)..

## <a name="coleserverdoconexecolecmd"></a><a name="onexecolecmd"></a>COleServerDoc::OnExecOleCmd

El marco de trabajo llama a esta función para ejecutar un comando especificado o mostrar ayuda para el comando.

```
virtual HRESULT OnExecOleCmd(
    const GUID* pguidCmdGroup,
    DWORD nCmdID,
    DWORD nCmdExecOpt,
    VARIANTARG* pvarargIn,
    VARIANTARG* pvarargOut);
```

### <a name="parameters"></a>Parámetros

*pguidCmdGroup*<br/>
Puntero a un GUID que identifica un conjunto de comandos. Puede ser NULL para indicar el grupo de comandos predeterminado.

*nCmdID*<br/>
El comando que se debe ejecutar. Debe estar en el grupo identificado por *pguidCmdGroup*.

*nCmdExecOut*<br/>
La forma en que el objeto debe ejecutar el comando, uno o varios de los siguientes valores de la enumeración OLECMDEXECOPT:

OLECMDEXECOPT_DODEFAULT

OLECMDEXECOPT_PROMPTUSER

OLECMDEXECOPT_DONTPROMPTUSER

OLECMDEXECOPT_SHOWHELP

*pvarargIn*<br/>
Puntero a un VARIANTARG que contiene argumentos de entrada para el comando. Puede ser NULL.

*pvarargOut*<br/>
Puntero a un VARIANTARG para recibir los valores devueltos de salida del comando. Puede ser NULL.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se realiza correctamente; de lo contrario, uno de los siguientes códigos de error:

|Value|Descripción|
|-----------|-----------------|
|E_UNEXPECTED|Error inesperado|
|E_FAIL|Se produjo un error|
|E_NOTIMPL|Indica que MFC debe intentar traducir y distribuir el comando|
|OLECMDERR_E_UNKNOWNGROUP|*pguidCmdGroup* no es NULL, pero no especifica un grupo de comandos reconocido|
|OLECMDERR_E_NOTSUPPORTED|*nCmdID* no se reconoce como un comando válido en el grupo *pguidCmdGroup*|
|OLECMDERR_DISABLED|El comando identificado por *nCmdID* está deshabilitado y no se puede ejecutar|
|OLECMDERR_NOHELP|El autor de la llamada pidió ayuda en el comando identificado por *nCmdID,* pero no hay ayuda disponible|
|OLECMDERR_CANCELED|El usuario canceló la ejecución|

### <a name="remarks"></a>Observaciones

`COleCmdUI`se puede utilizar para habilitar, actualizar y establecer otras propiedades de los comandos de la interfaz de usuario de DocObject. Después de inicializar los comandos, `OnExecOleCmd`puede ejecutarlos con .

El marco de trabajo llama a la función antes de intentar traducir y distribuir un comando de documento OLE. No es necesario invalidar esta función para controlar los comandos de documento OLE estándar, pero debe proporcionar una invalidación a esta función si desea controlar sus propios comandos personalizados o controlar comandos que acepten parámetros o devuelvan resultados.

La mayoría de los comandos no toman argumentos ni devuelven valores. Para la mayoría de los comandos, el autor de la llamada puede pasar los NULL para *pvarargIn* y *pvarargOut*. Para los comandos que esperan valores de entrada, el llamador puede declarar e inicializar una variable VARIANTARG y pasar un puntero a la variable en *pvarargIn*. Para los comandos que requieren un único valor, el argumento se puede almacenar directamente en el VARIANTARG y pasar a la función. Se deben empaquetar varios argumentos dentro de VARIANTARG utilizando uno de los tipos admitidos (como `IDispatch` y SAFEARRAY ).

De forma similar, si un comando devuelve argumentos, se espera que el autor de la llamada declare un VARIANTARG, inicialícelo en VT_EMPTY y pase su dirección en *pvarargOut*. Si un comando devuelve un único valor, el objeto puede almacenar ese valor directamente en *pvarargOut*. Se deben empaquetar varios valores de salida de alguna manera adecuados para EL VARIANTARG.

La implementación de clase base de esta función recorrerá las estructuras OLE_COMMAND_MAP asociadas con el destino del comando e intentará distribuir el comando a un controlador adecuado. La implementación de clase base solo funciona con comandos que no aceptan argumentos ni devuelven valores. Si necesita controlar comandos que aceptan argumentos o valores devueltos, debe invalidar esta función y trabajar con los parámetros *pvarargIn* y *pvarargOut* usted mismo.

## <a name="coleserverdoconframewindowactivate"></a><a name="onframewindowactivate"></a>COleServerDoc::OnFrameWindowActivate

El marco de trabajo llama a esta función cuando se activa o desactiva la ventana de marco de la aplicación contenedora.

```
virtual void OnFrameWindowActivate(BOOL bActivate);
```

### <a name="parameters"></a>Parámetros

*bActivar*<br/>
Especifica si la ventana de marco se va a activar o desactivar.

### <a name="remarks"></a>Observaciones

La implementación predeterminada cancela los modos de ayuda en los que puede estar la ventana de marco. Reemplace esta función si desea realizar un procesamiento especial cuando la ventana de marco está activada o desactivada.

Para obtener más información, consulte el artículo [Activación](../../mfc/activation-cpp.md)..

## <a name="coleserverdocongetembeddeditem"></a><a name="ongetembeddeditem"></a>COleServerDoc::OnGetEmbeddedItem

Llamado por el marco de trabajo cuando una aplicación contenedora llama a la aplicación de servidor para crear o editar un elemento incrustado.

```
virtual COleServerItem* OnGetEmbeddedItem() = 0;
```

### <a name="return-value"></a>Valor devuelto

Un puntero a un elemento que representa todo el documento; NULL si se produce un error en la operación.

### <a name="remarks"></a>Observaciones

No hay ninguna implementación predeterminada. Debe invalidar esta función para devolver un elemento que representa todo el documento. Este valor devuelto debe ser `COleServerItem`un objeto de una clase derivada.

## <a name="coleserverdoconreactivateandundo"></a><a name="onreactivateandundo"></a>COleServerDoc::OnReactivateAndUndo

El marco de trabajo llama a esta función cuando el usuario elige deshacer los cambios realizados en un elemento que se ha activado en su lugar, cambiado y posteriormente desactivado.

```
virtual BOOL OnReactivateAndUndo();
```

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

La implementación predeterminada no hace nada excepto devolver FALSE para indicar un error.

Invalide esta función si la aplicación admite deshacer. Normalmente, realizaría la operación de deshacer `ActivateInPlace`y, a continuación, activar el elemento llamando a . Si la aplicación contenedora se escribe con `COleClientItem::ReactivateAndUndo` la biblioteca Microsoft Foundation Class, la llamada hace que se llame a esta función.

## <a name="coleserverdoconresizeborder"></a><a name="onresizeborder"></a>COleServerDoc::OnResizeBorder

El marco de trabajo llama a esta función cuando las ventanas de marco de la aplicación contenedora cambian de tamaño.

```
virtual void OnResizeBorder(
    LPCRECT lpRectBorder,
    LPOLEINPLACEUIWINDOW lpUIWindow,
    BOOL bFrame);
```

### <a name="parameters"></a>Parámetros

*lpRectBorder*<br/>
Puntero a `RECT` una `CRect` estructura o un objeto que especifica las coordenadas del borde.

*lpUIWindow*<br/>
Puntero a un `IOleInPlaceUIWindow` objeto de clase que posee la sesión de edición in situ actual.

*bFrame*<br/>
TRUESi *lpUIWindow* apunta a la ventana de marco de nivel superior de la aplicación contenedora, o FALSE si *lpUIWindow* apunta a la ventana de marco de nivel de documento de la aplicación contenedora.

### <a name="remarks"></a>Observaciones

Esta función cambia el tamaño y ajusta las barras de herramientas y otros elementos de la interfaz de usuario de acuerdo con el nuevo tamaño de ventana.

Para obtener más información, vea [IOleInPlaceUIWindow](/windows/win32/api/oleidl/nn-oleidl-ioleinplaceuiwindow) en el Windows SDK.

Este es un avanzado reemplazable.

## <a name="coleserverdoconsethostnames"></a><a name="onsethostnames"></a>COleServerDoc::OnSetHostNames

Llamado por el marco de trabajo cuando el contenedor establece o cambia los nombres de host para este documento.

```
virtual void OnSetHostNames(
    LPCTSTR lpszHost,
    LPCTSTR lpszHostObj);
```

### <a name="parameters"></a>Parámetros

*lpszHost*<br/>
Puntero a una cadena que especifica el nombre de la aplicación contenedora.

*lpszHostObj*<br/>
Puntero a una cadena que especifica el nombre del contenedor para el documento.

### <a name="remarks"></a>Observaciones

La implementación predeterminada cambia el título del documento para todas las vistas que hacen referencia a este documento.

Invalide esta función si la aplicación establece los títulos a través de un mecanismo diferente.

## <a name="coleserverdoconsetitemrects"></a><a name="onsetitemrects"></a>COleServerDoc::OnSetItemRects

El marco de trabajo llama a esta función para colocar la ventana de marco de edición in situ dentro de la ventana de marco de la aplicación contenedora.

```
virtual void OnSetItemRects(
    LPCRECT lpPosRect,
    LPCRECT lpClipRect);
```

### <a name="parameters"></a>Parámetros

*lpPosRect*<br/>
Puntero a `RECT` una `CRect` estructura o a un objeto que especifica la posición de la ventana de marco en su lugar en relación con el área de cliente de la aplicación contenedora.

*lpClipRect*<br/>
Puntero a `RECT` una `CRect` estructura o a un objeto que especifica el rectángulo delimitador de la ventana de marco in situ en relación con el área de cliente de la aplicación contenedora.

### <a name="remarks"></a>Observaciones

Reemplace esta función para actualizar el factor de zoom de la vista, si es necesario.

Normalmente se llama a `RequestPositionChange` esta función en respuesta a una llamada, aunque el contenedor puede llamarla en cualquier momento para solicitar un cambio de posición para el elemento en el lugar.

## <a name="coleserverdoconshowcontrolbars"></a><a name="onshowcontrolbars"></a>COleServerDoc::OnShowControlBars

El marco de trabajo llama a esta función para mostrar u ocultar las barras de control de la aplicación de servidor asociadas con la ventana de marco identificada por *pFrameWnd*.

```
virtual void OnShowControlBars(
    CFrameWnd* pFrameWnd,
    BOOL bShow);
```

### <a name="parameters"></a>Parámetros

*pFrameWnd*<br/>
Puntero a la ventana de marco cuyas barras de control deben estar ocultas o mostrarse.

*bMostrar*<br/>
Determina si las barras de control se muestran u ocultan.

### <a name="remarks"></a>Observaciones

La implementación predeterminada enumera todas las barras de control propiedad de esa ventana de marco y las oculta o muestra.

## <a name="coleserverdoconshowdocument"></a><a name="onshowdocument"></a>COleServerDoc::OnShowDocument

El marco `OnShowDocument` de trabajo llama a la función cuando el documento de servidor debe estar oculto o mostrarse.

```
virtual void OnShowDocument(BOOL bShow);
```

### <a name="parameters"></a>Parámetros

*bMostrar*<br/>
Especifica si la interfaz de usuario del documento debe mostrarse u ocultarse.

### <a name="remarks"></a>Observaciones

Si *bShow* es TRUE, la implementación predeterminada activa la aplicación de servidor, si es necesario, y hace que la aplicación contenedora desplácese por su ventana para que el elemento esté visible. Si *bShow* es FALSE, la implementación predeterminada desactiva `OnDeactivate`el elemento mediante una llamada a , a continuación, destruye u oculta todas las ventanas de marco que se han creado para el documento, excepto la primera. Si no quedan documentos visibles, la implementación predeterminada oculta la aplicación de servidor.

## <a name="coleserverdoconupdatedocument"></a><a name="onupdatedocument"></a>COleServerDoc::OnUpdateDocument

Llamado por el marco de trabajo al guardar un documento que es un elemento incrustado en un documento compuesto.

```
virtual BOOL OnUpdateDocument();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el documento se actualizó correctamente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

La implementación predeterminada llama a las funciones miembro [COleServerDoc::NotifySaved](#notifysaved) y [COleServerDoc::SaveEmbedding](#saveembedding) y, a continuación, marca el documento como limpio. Reemplace esta función si desea realizar un procesamiento especial al actualizar un elemento incrustado.

## <a name="coleserverdocrequestpositionchange"></a><a name="requestpositionchange"></a>COleServerDoc::RequestPositionChange

Llame a esta función miembro para que la aplicación contenedora cambie la posición del elemento.

```
void RequestPositionChange(LPCRECT lpPosRect);
```

### <a name="parameters"></a>Parámetros

*lpPosRect*<br/>
Puntero a `RECT` una `CRect` estructura o a un objeto que contiene la nueva posición del elemento.

### <a name="remarks"></a>Observaciones

Normalmente se llama a `UpdateAllItems`esta función (junto con ) cuando los datos de un elemento activo in situ han cambiado. Después de esta llamada, el contenedor puede `OnSetItemRects`o no realizar el cambio mediante una llamada a . La posición resultante puede ser diferente de la solicitada.

## <a name="coleserverdocsaveembedding"></a><a name="saveembedding"></a>COleServerDoc::SaveEmbedding

Llame a esta función para indicar a la aplicación contenedora que guarde el objeto incrustado.

```
void SaveEmbedding();
```

### <a name="remarks"></a>Observaciones

Esta función se `OnUpdateDocument`llama automáticamente desde . Tenga en cuenta que esta función hace que el elemento se actualice en el disco, por lo que normalmente se llama solo como resultado de una acción de usuario específica.

## <a name="coleserverdocscrollcontainerby"></a><a name="scrollcontainerby"></a>COleServerDoc::ScrollContainerBy

Llame `ScrollContainerBy` a la función miembro para desplazar el documento `sizeScroll`contenedor por la cantidad, en píxeles, indicada por .

```
BOOL ScrollContainerBy(CSize sizeScroll);
```

### <a name="parameters"></a>Parámetros

*sizeScroll*<br/>
Indica hasta qué punto se debe desplazar el documento contenedor.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Los valores positivos indican que se desplaza hacia abajo y hacia la derecha; los valores negativos indican desplazarse hacia arriba y hacia la izquierda.

## <a name="coleserverdocupdateallitems"></a><a name="updateallitems"></a>COleServerDoc::UpdateAllItems

Llame a esta función para notificar a todos los elementos vinculados conectados al documento que el documento ha cambiado.

```
void UpdateAllItems(
    COleServerItem* pSender,
    LPARAM lHint = 0L,
    CObject* pHint = NULL,
    DVASPECT nDrawAspect = DVASPECT_CONTENT);
```

### <a name="parameters"></a>Parámetros

*pSender*<br/>
Puntero al elemento que modificó el documento, o NULL si se van a actualizar todos los elementos.

*lHint*<br/>
Contiene información sobre la modificación.

*pHint*<br/>
Puntero a un objeto que almacena información sobre la modificación.

*nDrawAspect*<br/>
Determina cómo se va a dibujar el elemento. Este es un valor de la enumeración DVASPECT. Este parámetro puede tener uno de los valores siguientes:

- DVASPECT_CONTENT Item se representa de tal manera que se puede mostrar como un objeto incrustado dentro de su contenedor.

- DVASPECT_THUMBNAIL elemento se representa en una representación "en miniatura" para que se pueda mostrar en una herramienta de exploración.

- DVASPECT_ICON elemento se representa mediante un icono.

- DVASPECT_DOCPRINT Elemento se representa como si se imprimiera mediante el comando Imprimir del menú Archivo.

### <a name="remarks"></a>Observaciones

Normalmente se llama a esta función después de que el usuario cambia el documento de servidor. Si un elemento OLE está vinculado al documento con un vínculo automático, el elemento se actualiza para reflejar los cambios. En las aplicaciones contenedoras escritas con la biblioteca `COleClientItem` Microsoft Foundation Class, se llama a la función miembro [OnChange](../../mfc/reference/coleclientitem-class.md#onchange) de .

Esta función `OnUpdate` llama a la función miembro para cada uno de los elementos del documento excepto el elemento de envío, pasando *pHint*, *lHint*y *nDrawAspect*. Utilice estos parámetros para pasar información a los elementos sobre las modificaciones realizadas en el documento. Puede codificar información mediante *lHint* o `CObject`puede definir una clase derivada para almacenar información sobre las modificaciones y pasar un objeto de esa clase mediante *pHint*. Invalide `OnUpdate` la función miembro en la clase `COleServerItem`derivada para optimizar la actualización de cada elemento en función de si su presentación ha cambiado.

## <a name="see-also"></a>Consulte también

[Ejemplo de MFC HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[COleLinkingDoc (clase)](../../mfc/reference/colelinkingdoc-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[COleDocument (Clase)](../../mfc/reference/coledocument-class.md)<br/>
[COleLinkingDoc (clase)](../../mfc/reference/colelinkingdoc-class.md)<br/>
[COleTemplateServer (clase)](../../mfc/reference/coletemplateserver-class.md)
