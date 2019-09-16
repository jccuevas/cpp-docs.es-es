---
title: COleServerDoc (clase)
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
ms.openlocfilehash: eec94a32fa0963d4cf2eccae0fb9e2423e75ffdc
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69503823"
---
# <a name="coleserverdoc-class"></a>COleServerDoc (clase)

La clase base para los documentos de servidor OLE.

## <a name="syntax"></a>Sintaxis

```
class AFX_NOVTABLE COleServerDoc : public COleLinkingDoc
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[COleServerDoc::COleServerDoc](#coleserverdoc)|Construye un objeto `COleServerDoc`.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[COleServerDoc::ActivateDocObject](#activatedocobject)|Activa el documento DocObject asociado.|
|[COleServerDoc::ActivateInPlace](#activateinplace)|Activa el documento para la edición en contexto.|
|[COleServerDoc::DeactivateAndUndo](#deactivateandundo)|Desactiva la interfaz de usuario del servidor.|
|[COleServerDoc::DiscardUndoState](#discardundostate)|Descarta la información de estado de deshacer.|
|[COleServerDoc::GetClientSite](#getclientsite)|Recupera un puntero a la interfaz subyacente `IOleClientSite` .|
|[COleServerDoc::GetEmbeddedItem](#getembeddeditem)|Devuelve un puntero a un elemento que representa todo el documento.|
|[COleServerDoc::GetItemClipRect](#getitemcliprect)|Devuelve el rectángulo de recorte actual para la edición en contexto.|
|[COleServerDoc::GetItemPosition](#getitemposition)|Devuelve el rectángulo de posición actual, relativo al área cliente de la aplicación contenedora, para la edición en contexto.|
|[COleServerDoc::GetZoomFactor](#getzoomfactor)|Devuelve el factor de zoom en píxeles.|
|[COleServerDoc::IsDocObject](#isdocobject)|Determina si el documento es un DocObject.|
|[COleServerDoc::IsEmbedded](#isembedded)|Indica si el documento está incrustado en un documento contenedor o en ejecución independiente.|
|[COleServerDoc::IsInPlaceActive](#isinplaceactive)|Devuelve TRUE si el elemento está activado actualmente.|
|[COleServerDoc::NotifyChanged](#notifychanged)|Notifica a los contenedores que el usuario ha cambiado el documento.|
|[COleServerDoc::NotifyClosed](#notifyclosed)|Notifica a los contenedores que el usuario ha cerrado el documento.|
|[COleServerDoc::NotifyRename](#notifyrename)|Notifica a los contenedores que el usuario ha cambiado el nombre del documento.|
|[COleServerDoc::NotifySaved](#notifysaved)|Notifica a los contenedores que el usuario ha guardado el documento.|
|[COleServerDoc::OnDeactivate](#ondeactivate)|Lo llama el marco de trabajo cuando el usuario desactiva un elemento que se activó en contexto.|
|[COleServerDoc::OnDeactivateUI](#ondeactivateui)|Lo llama el marco de trabajo para destruir controles y otros elementos de la interfaz de usuario creados para la activación en contexto.|
|[COleServerDoc::OnDocWindowActivate](#ondocwindowactivate)|Lo llama el marco de trabajo cuando la ventana de marco de documento del contenedor se activa o desactiva.|
|[COleServerDoc::OnResizeBorder](#onresizeborder)|Lo llama el marco de trabajo cuando se cambia el tamaño de la ventana de marco o la ventana de documento de la aplicación contenedora.|
|[COleServerDoc::OnShowControlBars](#onshowcontrolbars)|Lo llama el marco de trabajo para mostrar u ocultar las barras de control de la edición en contexto.|
|[COleServerDoc::OnUpdateDocument](#onupdatedocument)|Lo llama el marco de trabajo cuando se guarda un documento de servidor que es un elemento incrustado, actualizando la copia del contenedor del elemento.|
|[COleServerDoc::RequestPositionChange](#requestpositionchange)|Cambia la posición del marco de edición en contexto.|
|[COleServerDoc::SaveEmbedding](#saveembedding)|Indica a la aplicación contenedora que guarde el documento.|
|[COleServerDoc::ScrollContainerBy](#scrollcontainerby)|Desplaza el documento contenedor.|
|[COleServerDoc::UpdateAllItems](#updateallitems)|Notifica a los contenedores que el usuario ha cambiado el documento.|

### <a name="protected-methods"></a>Métodos protegidos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[COleServerDoc::CreateInPlaceFrame](#createinplaceframe)|Lo llama el marco de trabajo para crear una ventana de marco para la edición en contexto.|
|[COleServerDoc::DestroyInPlaceFrame](#destroyinplaceframe)|Lo llama el marco de trabajo para destruir una ventana de marco para la edición en contexto.|
|[COleServerDoc::GetDocObjectServer](#getdocobjectserver)|Invalide esta función para crear `CDocObjectServer` un nuevo objeto e indicar que este documento es un contenedor de DocObject.|
|[COleServerDoc::OnClose](#onclose)|Lo llama el marco de trabajo cuando un contenedor solicita cerrar el documento.|
|[COleServerDoc::OnExecOleCmd](#onexecolecmd)|Ejecuta un comando especificado o muestra la ayuda del comando.|
|[COleServerDoc::OnFrameWindowActivate](#onframewindowactivate)|Lo llama el marco de trabajo cuando la ventana de marco del contenedor está activada o desactivada.|
|[COleServerDoc::OnGetEmbeddedItem](#ongetembeddeditem)|Se llama para obtener `COleServerItem` un objeto que representa el documento completo; se usa para obtener un elemento incrustado. Implementación requerida.|
|[COleServerDoc::OnReactivateAndUndo](#onreactivateandundo)|Lo llama el marco de trabajo para deshacer los cambios realizados durante la edición en contexto.|
|[COleServerDoc::OnSetHostNames](#onsethostnames)|Lo llama el marco de trabajo cuando un contenedor establece el título de la ventana para un objeto incrustado.|
|[COleServerDoc::OnSetItemRects](#onsetitemrects)|Lo llama el marco de trabajo para colocar la ventana de marco de edición en contexto dentro de la ventana de la aplicación contenedora.|
|[COleServerDoc::OnShowDocument](#onshowdocument)|Lo llama el marco de trabajo para mostrar u ocultar el documento.|

## <a name="remarks"></a>Comentarios

Un documento de servidor puede contener objetos [COleServerItem](../../mfc/reference/coleserveritem-class.md) , que representan la interfaz de servidor para elementos incrustados o vinculados. Cuando un contenedor inicia una aplicación de servidor para editar un elemento incrustado, el elemento se carga como su propio documento de servidor; el `COleServerDoc` objeto contiene un `COleServerItem` solo objeto, compuesto por todo el documento. Cuando un contenedor inicia una aplicación de servidor para editar un elemento vinculado, se carga un documento existente desde el disco. se resalta una parte del contenido del documento para indicar el elemento vinculado.

`COleServerDoc`los objetos también pueden contener elementos de la clase [COleClientItem](../../mfc/reference/coleclientitem-class.md) . Esto le permite crear aplicaciones de servidor de contenedor. El marco de trabajo proporciona funciones para almacenar `COleClientItem` correctamente los elementos mientras se `COleServerItem` atienden los objetos.

Si la aplicación de servidor no admite vínculos, un documento de servidor siempre contendrá un solo elemento de servidor, que representa todo el objeto incrustado como un documento. Si la aplicación de servidor admite vínculos, debe crear un elemento de servidor cada vez que se copie una selección en el portapapeles.

Para usar `COleServerDoc`, derive una clase a partir de ella e implemente la función miembro [OnGetEmbeddedItem](#ongetembeddeditem) , que permite que el servidor admita elementos incrustados. Derive una clase de `COleServerItem` para implementar los elementos de los documentos y devuelva los objetos de esa clase `OnGetEmbeddedItem`desde.

Para admitir elementos vinculados `COleServerDoc` , proporciona la función miembro [OnGetLinkedItem](../../mfc/reference/colelinkingdoc-class.md#ongetlinkeditem) . Puede usar la implementación predeterminada o invalidarla si tiene su propia forma de administrar elementos de documento.

Necesita una `COleServerDoc`clase derivada de cada tipo de documento de servidor que admita la aplicación. Por ejemplo, si la aplicación de servidor admite hojas de cálculo y gráficos, necesitará dos `COleServerDoc`clases derivadas.

Para obtener más información sobre los servidores, consulte [el artículo servidores: Implementar un servidor](../../mfc/servers-implementing-a-server.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocument](../../mfc/reference/cdocument-class.md)

[COleDocument](../../mfc/reference/coledocument-class.md)

[COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)

`COleServerDoc`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxole. h

##  <a name="activatedocobject"></a>  COleServerDoc::ActivateDocObject

Activa el documento DocObject asociado.

```
void ActivateDocObject();
```

### <a name="remarks"></a>Comentarios

De forma predeterminada `COleServerDoc` , no admite documentos activos (también denominados DocObjects). Para habilitar esta compatibilidad, consulte [GetDocObjectServer](#getdocobjectserver) y la clase [CDocObjectServer](../../mfc/reference/cdocobjectserver-class.md).

##  <a name="activateinplace"></a>  COleServerDoc::ActivateInPlace

Activa el elemento para la edición en contexto.

```
BOOL ActivateInPlace();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se realiza correctamente; de lo contrario, 0, que indica que el elemento está totalmente abierto.

### <a name="remarks"></a>Comentarios

Esta función realiza todas las operaciones necesarias para la activación en contexto. Crea una ventana de marco en contexto, la activa y lo dimensiona en el elemento, configura los menús compartidos y otros controles, desplaza el elemento a la vista y establece el foco en la ventana de marco en contexto.

La implementación predeterminada de [COleServerItem:: show](../../mfc/reference/coleserveritem-class.md#onshow)llama a esta función. Llame a esta función si la aplicación admite otro verbo para la activación en contexto (por ejemplo, Play).

##  <a name="coleserverdoc"></a>  COleServerDoc::COleServerDoc

Construye un `COleServerDoc` objeto sin conectar con los archivos DLL del sistema OLE.

```
COleServerDoc();
```

### <a name="remarks"></a>Comentarios

Debe llamar a [COleLinkingDoc:: Register](../../mfc/reference/colelinkingdoc-class.md#register) para abrir Communications con OLE. Si usa [COleTemplateServer](../../mfc/reference/coletemplateserver-class.md) en `COleLinkingDoc::Register` la aplicación, se llama a para usted por `OnOpenDocument` `COleLinkingDoc`la implementación de `OnNewDocument`, y `OnSaveDocument`.

##  <a name="createinplaceframe"></a>  COleServerDoc::CreateInPlaceFrame

El marco de trabajo llama a esta función para crear una ventana de marco para la edición en contexto.

```
virtual COleIPFrameWnd* CreateInPlaceFrame(CWnd* pParentWnd);
```

### <a name="parameters"></a>Parámetros

*pParentWnd*<br/>
Puntero a la ventana primaria de la aplicación contenedora.

### <a name="return-value"></a>Valor devuelto

Un puntero a la ventana de marco en contexto o NULL si no se realiza correctamente.

### <a name="remarks"></a>Comentarios

La implementación predeterminada usa la información especificada en la plantilla de documento para crear el marco. La vista usada es la primera vista que se crea para el documento. Esta vista se separa temporalmente del fotograma original y se adjunta al marco recién creado.

Se trata de un reemplazable avanzado.

##  <a name="deactivateandundo"></a>  COleServerDoc::DeactivateAndUndo

Llame a esta función si la aplicación admite la operación de deshacer y el usuario elige deshacer después de activar un elemento, pero antes de editarlo.

```
BOOL DeactivateAndUndo();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero en caso de éxito; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Si la aplicación contenedora se escribe utilizando el biblioteca MFC, la llamada a esta función hace que se llame a [COleClientItem:: OnDeactivateAndUndo](../../mfc/reference/coleclientitem-class.md#ondeactivateandundo) , lo que desactiva la interfaz de usuario del servidor.

##  <a name="destroyinplaceframe"></a>  COleServerDoc::DestroyInPlaceFrame

El marco de trabajo llama a esta función para destruir una ventana de marco en contexto y devolver la ventana de documento de la aplicación de servidor a su estado anterior a la activación en contexto.

```
virtual void DestroyInPlaceFrame(COleIPFrameWnd* pFrameWnd);
```

### <a name="parameters"></a>Parámetros

*pFrameWnd*<br/>
Puntero a la ventana de marco en contexto que se va a destruir.

### <a name="remarks"></a>Comentarios

Se trata de un reemplazable avanzado.

##  <a name="discardundostate"></a>  COleServerDoc::DiscardUndoState

Si el usuario realiza una operación de edición que no se puede deshacer, llame a esta función para obligar a la aplicación contenedora a descartar la información de estado de deshacer.

```
BOOL DiscardUndoState();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero en caso de éxito; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Esta función se proporciona para que los servidores que admiten la operación de deshacer puedan liberar recursos que de otro modo podrían consumirse en la información de estado de deshacer que no se puede usar.

##  <a name="getclientsite"></a>  COleServerDoc::GetClientSite

Recupera un puntero a la interfaz subyacente `IOleClientSite` .

```
LPOLECLIENTSITE GetClientSite() const;
```

### <a name="return-value"></a>Valor devuelto

Recupera un puntero a la interfaz [IOleClientSite](/windows/win32/api/oleidl/nn-oleidl-ioleclientsite) subyacente.

##  <a name="getdocobjectserver"></a>  COleServerDoc::GetDocObjectServer

Invalide esta función para crear `CDocObjectServer` un nuevo elemento y devolver un puntero a él.

```
virtual CDocObjectServer* GetDocObjectServer(LPOLEDOCUMENTSITE pDocSite);
```

### <a name="parameters"></a>Parámetros

*pDocSite*<br/>
Puntero a la `IOleDocumentSite` interfaz que va a conectar este documento al servidor.

### <a name="return-value"></a>Valor devuelto

Un puntero a un `CDocObjectServer`; NULL si se produjo un error en la operación.

### <a name="remarks"></a>Comentarios

Cuando se activa un servidor DocObject, la devolución de un puntero que no es NULL muestra que el cliente puede admitir DocObjects. La implementación predeterminada devuelve NULL.

Una implementación típica para un documento que admita DocObjects simplemente asignará un nuevo `CDocObjectServer` objeto y lo devolverá al autor de la llamada. Por ejemplo:

[!code-cpp[NVC_MFCOleServer#3](../../mfc/codesnippet/cpp/coleserverdoc-class_1.cpp)]

##  <a name="getembeddeditem"></a>  COleServerDoc::GetEmbeddedItem

Llame a esta función para obtener un puntero a un elemento que represente todo el documento.

```
COleServerItem* GetEmbeddedItem();
```

### <a name="return-value"></a>Valor devuelto

Un puntero a un elemento que representa todo el documento; NULL si se produjo un error en la operación.

### <a name="remarks"></a>Comentarios

Llama a [COleServerDoc:: OnGetEmbeddedItem](#ongetembeddeditem), una función virtual sin implementación predeterminada.

##  <a name="getitemcliprect"></a>  COleServerDoc::GetItemClipRect

Llame a `GetItemClipRect` la función miembro para obtener las coordenadas del rectángulo de recorte del elemento que se está editando en contexto.

```
void GetItemClipRect(LPRECT lpClipRect) const;
```

### <a name="parameters"></a>Parámetros

*lpClipRect*<br/>
Puntero a una `RECT` estructura o un `CRect` objeto para recibir las coordenadas del rectángulo de recorte del elemento.

### <a name="remarks"></a>Comentarios

Las coordenadas están en píxeles en relación con el área de cliente de la ventana de la aplicación contenedora.

El dibujo no debe aparecer fuera del rectángulo de recorte. Normalmente, el dibujo se restringe automáticamente. Utilice esta función para determinar si el usuario se ha desplazado fuera de la parte visible del documento; Si es así, desplácese por el documento contenedor según sea necesario mediante una llamada a [ScrollContainerBy](#scrollcontainerby).

##  <a name="getitemposition"></a>  COleServerDoc::GetItemPosition

Llame a `GetItemPosition` la función miembro para obtener las coordenadas del elemento que se está editando en contexto.

```
void GetItemPosition(LPRECT lpPosRect) const;
```

### <a name="parameters"></a>Parámetros

*lpPosRect*<br/>
Puntero a una `RECT` estructura o un `CRect` objeto para recibir las coordenadas del elemento.

### <a name="remarks"></a>Comentarios

Las coordenadas están en píxeles en relación con el área de cliente de la ventana de la aplicación contenedora.

La posición del elemento puede compararse con el rectángulo de recorte actual para determinar la medida en la que el elemento es visible (o no visible) en la pantalla.

##  <a name="getzoomfactor"></a>  COleServerDoc::GetZoomFactor

La `GetZoomFactor` función miembro determina el "factor de zoom" de un elemento que se ha activado para la edición en contexto.

```
BOOL GetZoomFactor(
    LPSIZE lpSizeNum = NULL,
    LPSIZE lpSizeDenom = NULL,
    LPCRECT lpPosRect = NULL) const;
```

### <a name="parameters"></a>Parámetros

*lpSizeNum*<br/>
Puntero a un objeto de clase `CSize` que contendrá el numerador del factor de zoom. Puede ser NULL.

*lpSizeDenom*<br/>
Puntero a un objeto de clase `CSize` que contendrá el denominador del factor de zoom. Puede ser NULL.

*lpPosRect*<br/>
Puntero a un objeto de la `CRect` clase que describe la nueva posición del elemento. Si este argumento es NULL, la función utiliza la posición actual del elemento.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el elemento está activado para la edición en contexto y su factor de zoom es distinto del 100% (1:1); de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

El factor de zoom, en píxeles, es la proporción del tamaño del elemento con respecto a su extensión actual. Si la aplicación contenedora no ha establecido la extensión del elemento, se utiliza su extensión natural (según lo determinado por [COleServerItem:: OnGetExtent](../../mfc/reference/coleserveritem-class.md#ongetextent)).

La función establece los dos primeros argumentos en el numerador y el denominador del "factor de zoom" del elemento. Si el elemento no se está editando en contexto, la función establece estos argumentos en un valor predeterminado de 100% (o 1:1) y devuelve cero. Para obtener más información, vea la nota técnica 40, [cambio de tamaño y zoom en contexto de MFC/OLE](../../mfc/tn040-mfc-ole-in-place-resizing-and-zooming.md).

##  <a name="isdocobject"></a>  COleServerDoc::IsDocObject

Determina si el documento es un DocObject.

```
BOOL IsDocObject() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE si el documento es un DocObject; en caso contrario, FALSE.

##  <a name="isembedded"></a>  COleServerDoc::IsEmbedded

Llame a `IsEmbedded` la función miembro para determinar si el documento representa un objeto incrustado en un contenedor.

```
BOOL IsEmbedded() const;
```

### <a name="return-value"></a>Valor devuelto

Es distinto de cero `COleServerDoc` si el objeto es un documento que representa un objeto incrustado en un contenedor; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Un documento que se carga desde un archivo no se incrusta, aunque puede ser manipulado por una aplicación contenedora como un vínculo. Se considera que un documento que está incrustado en un documento de contenedor está incrustado.

##  <a name="isinplaceactive"></a>  COleServerDoc::IsInPlaceActive

Llame a `IsInPlaceActive` la función miembro para determinar si el elemento está actualmente en el estado activo en contexto.

```
BOOL IsInPlaceActive() const;
```

### <a name="return-value"></a>Valor devuelto

Es distinto de cero `COleServerDoc` si el objeto está activo en contexto; de lo contrario, es 0.

##  <a name="notifychanged"></a>  COleServerDoc::NotifyChanged

Llame a esta función para notificar a todos los elementos vinculados conectados al documento que el documento ha cambiado.

```
void NotifyChanged();
```

### <a name="remarks"></a>Comentarios

Normalmente, se llama a esta función una vez que el usuario cambia algún atributo global, como las dimensiones del documento del servidor. Si un elemento OLE está vinculado al documento con un vínculo automático, el elemento se actualiza para reflejar los cambios. En las aplicaciones contenedoras escritas con la biblioteca MFC, se llama a la función miembro [OnChange](../../mfc/reference/coleclientitem-class.md#onchange) de `COleClientItem` en su lugar.

> [!NOTE]
>  Esta función se incluye por compatibilidad con OLE 1. Las nuevas aplicaciones deben usar [UpdateAllItems](#updateallitems).

##  <a name="notifyclosed"></a>  COleServerDoc::NotifyClosed

Llame a esta función para notificar a los contenedores que el documento se ha cerrado.

```
void NotifyClosed();
```

### <a name="remarks"></a>Comentarios

Cuando el usuario elige el comando cerrar en el menú Archivo, `NotifyClosed` se llama mediante `COleServerDoc`la implementación de la función miembro [OnCloseDocument](../../mfc/reference/cdocument-class.md#onclosedocument) . En las aplicaciones contenedoras escritas con la biblioteca MFC, se llama a la función miembro [OnChange](../../mfc/reference/coleclientitem-class.md#onchange) de `COleClientItem` en su lugar.

##  <a name="notifyrename"></a>  COleServerDoc::NotifyRename

Llame a esta función después de que el usuario cambie el nombre del documento del servidor.

```
void NotifyRename(LPCTSTR lpszNewName);
```

### <a name="parameters"></a>Parámetros

*lpszNewName*<br/>
Puntero a una cadena que especifica el nuevo nombre del documento del servidor; suele ser una ruta de acceso completa.

### <a name="remarks"></a>Comentarios

Cuando el usuario elige el comando Guardar como en el menú Archivo, `NotifyRename` se llama mediante `COleServerDoc`la implementación de la función miembro [OnSaveDocument](../../mfc/reference/cdocument-class.md#onsavedocument) . Esta función notifica a los archivos DLL del sistema OLE, que a su vez notifican a los contenedores. En las aplicaciones contenedoras escritas con la biblioteca MFC, se llama a la función miembro [OnChange](../../mfc/reference/coleclientitem-class.md#onchange) de `COleClientItem` en su lugar.

##  <a name="notifysaved"></a>  COleServerDoc::NotifySaved

Llame a esta función después de que el usuario guarde el documento del servidor.

```
void NotifySaved();
```

### <a name="remarks"></a>Comentarios

Cuando el usuario elige el comando Guardar en el menú Archivo, `NotifySaved` se le llama para `COleServerDoc`la implementación de [OnSaveDocument](../../mfc/reference/cdocument-class.md#onsavedocument). Esta función notifica a los archivos DLL del sistema OLE, que a su vez notifican a los contenedores. En las aplicaciones contenedoras escritas con la biblioteca MFC, se llama a la función miembro [OnChange](../../mfc/reference/coleclientitem-class.md#onchange) de `COleClientItem` en su lugar.

##  <a name="onclose"></a>  COleServerDoc::OnClose

Lo llama el marco de trabajo cuando un contenedor solicita que se cierre el documento del servidor.

```
virtual void OnClose(OLECLOSE dwCloseOption);
```

### <a name="parameters"></a>Parámetros

*dwCloseOption*<br/>
Un valor de la enumeración OLECLOSE. Este parámetro puede tener uno de los valores siguientes:

- OLECLOSE_SAVEIFDIRTY el archivo se guarda si se ha modificado.

- OLECLOSE_NOSAVE el archivo se cierra sin guardarse.

- OLECLOSE_PROMPTSAVE si se ha modificado el archivo, se le pedirá al usuario que lo guarde.

### <a name="remarks"></a>Comentarios

La implementación predeterminada llama `CDocument::OnCloseDocument`a.

Para obtener más información y valores adicionales, vea [OLECLOSE](/windows/win32/api/oleidl/ne-oleidl-oleclose) en el Windows SDK.

##  <a name="ondeactivate"></a>  COleServerDoc::OnDeactivate

Lo llama el marco de trabajo cuando el usuario desactiva un elemento incrustado o vinculado que actualmente está activo en contexto.

```
virtual void OnDeactivate();
```

### <a name="remarks"></a>Comentarios

Esta función restaura la interfaz de usuario de la aplicación contenedora a su estado original y destruye los menús y otros controles que se crearon para la activación en contexto.

La información de estado de la operación de deshacer se debe liberar incondicionalmente en este momento.

Para obtener más información, vea el artículo [activación](../../mfc/activation-cpp.md).

##  <a name="ondeactivateui"></a>  COleServerDoc::OnDeactivateUI

Se llama cuando el usuario desactiva un elemento que se activó en contexto.

```
virtual void OnDeactivateUI(BOOL bUndoable);
```

### <a name="parameters"></a>Parámetros

*bUndoable*<br/>
Especifica si se pueden deshacer los cambios de edición.

### <a name="remarks"></a>Comentarios

Esta función restaura la interfaz de usuario de la aplicación contenedora a su estado original, ocultando los menús y otros controles que se crearon para la activación en contexto.

El marco siempre establece *bUndoable* en false. Si el servidor admite deshacer y hay una operación que se puede deshacer, llame a la implementación de la clase base con *bUndoable* establecido en true.

##  <a name="ondocwindowactivate"></a>  COleServerDoc::OnDocWindowActivate

El marco de trabajo llama a esta función para activar o desactivar una ventana de documento para la edición en contexto.

```
virtual void OnDocWindowActivate(BOOL bActivate);
```

### <a name="parameters"></a>Parámetros

*bActivate*<br/>
Especifica si la ventana de documento se va a activar o desactivar.

### <a name="remarks"></a>Comentarios

La implementación predeterminada quita o agrega los elementos de la interfaz de usuario en el nivel de marco según corresponda. Invalide esta función si desea realizar acciones adicionales cuando el documento que contiene el elemento está activado o desactivado.

Para obtener más información, vea el artículo [activación](../../mfc/activation-cpp.md).

##  <a name="onexecolecmd"></a>  COleServerDoc::OnExecOleCmd

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
Un puntero a un GUID que identifica un conjunto de comandos. Puede ser NULL para indicar el grupo de comandos predeterminado.

*nCmdID*<br/>
Comando que se va a ejecutar. Debe estar en el grupo identificado por *pguidCmdGroup*.

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

|Valor|DESCRIPCIÓN|
|-----------|-----------------|
|E_UNEXPECTED|Error inesperado|
|E_FAIL|Error|
|E_NOTIMPL|Indica que MFC debe intentar traducir y enviar el comando|
|OLECMDERR_E_UNKNOWNGROUP|*pguidCmdGroup* no es null, pero no especifica un grupo de comandos reconocido|
|OLECMDERR_E_NOTSUPPORTED|*nCmdID* no se reconoce como un comando válido en el grupo *pguidCmdGroup*|
|OLECMDERR_DISABLED|El comando identificado por *nCmdID* está deshabilitado y no se puede ejecutar|
|OLECMDERR_NOHELP|El autor de la llamada solicitó ayuda sobre el comando identificado por *nCmdID* , pero no hay ayuda disponible|
|OLECMDERR_CANCELED|El usuario canceló la ejecución|

### <a name="remarks"></a>Comentarios

`COleCmdUI`se puede usar para habilitar, actualizar y establecer otras propiedades de los comandos de la interfaz de usuario de DocObject. Una vez inicializados los comandos, puede ejecutarlos con `OnExecOleCmd`.

El marco de trabajo llama a la función antes de intentar traducir y enviar un comando de documento OLE. No es necesario invalidar esta función para controlar los comandos de documento OLE estándar, pero debe proporcionar una invalidación a esta función si desea administrar sus propios comandos personalizados o controlar los comandos que aceptan parámetros o devuelven resultados.

La mayoría de los comandos no toman argumentos o valores devueltos. Para la mayoría de los comandos, el llamador puede pasar valores NULL para *pvarargIn* y *pvarargOut*. Para los comandos que esperan valores de entrada, el autor de la llamada puede declarar e inicializar una variable VARIANTARG y pasar un puntero a la variable en *pvarargIn*. En el caso de los comandos que requieren un valor único, el argumento se puede almacenar directamente en VARIANTARG y pasarse a la función. Se deben empaquetar varios argumentos en el VARIANTARG con uno de los tipos admitidos ( `IDispatch` como y SafeArray).

Del mismo modo, si un comando devuelve argumentos, se espera que el autor de la llamada declare un VARIANTARG, lo inicialice en VT_EMPTY y pase su dirección en *pvarargOut*. Si un comando devuelve un valor único, el objeto puede almacenar ese valor directamente en *pvarargOut*. Se deben empaquetar varios valores de salida de alguna manera adecuada para VARIANTARG.

La implementación de la clase base de esta función recorrerá las estructuras OLE_COMMAND_MAP asociadas al destino del comando e intentará enviar el comando a un controlador adecuado. La implementación de la clase base solo funciona con comandos que no aceptan argumentos o valores devueltos. Si necesita controlar comandos que aceptan argumentos o valores devueltos, debe invalidar esta función y trabajar con los parámetros *pvarargIn* y *pvarargOut* .

##  <a name="onframewindowactivate"></a>  COleServerDoc::OnFrameWindowActivate

El marco de trabajo llama a esta función cuando la ventana de marco de la aplicación contenedora está activada o desactivada.

```
virtual void OnFrameWindowActivate(BOOL bActivate);
```

### <a name="parameters"></a>Parámetros

*bActivate*<br/>
Especifica si la ventana de marco se va a activar o desactivar.

### <a name="remarks"></a>Comentarios

La implementación predeterminada cancela cualquier modo de ayuda que pueda haber en la ventana de marco. Invalide esta función si desea realizar un procesamiento especial cuando la ventana de marco esté activada o desactivada.

Para obtener más información, vea el artículo [activación](../../mfc/activation-cpp.md).

##  <a name="ongetembeddeditem"></a>  COleServerDoc::OnGetEmbeddedItem

Lo llama el marco de trabajo cuando una aplicación contenedora llama a la aplicación de servidor para crear o editar un elemento incrustado.

```
virtual COleServerItem* OnGetEmbeddedItem() = 0;
```

### <a name="return-value"></a>Valor devuelto

Un puntero a un elemento que representa todo el documento; NULL si se produjo un error en la operación.

### <a name="remarks"></a>Comentarios

No hay ninguna implementación predeterminada. Debe reemplazar esta función para devolver un elemento que represente todo el documento. Este valor devuelto debe ser un objeto de `COleServerItem`una clase derivada de.

##  <a name="onreactivateandundo"></a>  COleServerDoc::OnReactivateAndUndo

El marco de trabajo llama a esta función cuando el usuario elige deshacer los cambios realizados en un elemento que se ha activado en contexto, ha cambiado y se ha desactivado posteriormente.

```
virtual BOOL OnReactivateAndUndo();
```

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

La implementación predeterminada no realiza ninguna excepción, salvo que devuelve FALSE para indicar un error.

Invalide esta función si la aplicación admite la operación de deshacer. Normalmente se realiza la operación de deshacer y, a continuación, se `ActivateInPlace`activa el elemento mediante una llamada a. Si la aplicación contenedora se escribe con el biblioteca MFC, `COleClientItem::ReactivateAndUndo` la llamada a hace que se llame a esta función.

##  <a name="onresizeborder"></a>  COleServerDoc::OnResizeBorder

El marco de trabajo llama a esta función cuando las ventanas de marco de la aplicación contenedora cambian el tamaño.

```
virtual void OnResizeBorder(
    LPCRECT lpRectBorder,
    LPOLEINPLACEUIWINDOW lpUIWindow,
    BOOL bFrame);
```

### <a name="parameters"></a>Parámetros

*lpRectBorder*<br/>
Puntero a una `RECT` estructura o un `CRect` objeto que especifica las coordenadas del borde.

*lpUIWindow*<br/>
Puntero a un objeto de clase `IOleInPlaceUIWindow` que posee la sesión de edición en contexto actual.

*bFrame*<br/>
TRUE si *lpUIWindow* apunta a la ventana de marco de nivel superior de la aplicación contenedora o false si *lpUIWindow* apunta a la ventana de marco de nivel de documento de la aplicación contenedora.

### <a name="remarks"></a>Comentarios

Esta función cambia el tamaño y ajusta las barras de herramientas y otros elementos de la interfaz de usuario de acuerdo con el nuevo tamaño de la ventana.

Para obtener más información, vea [IOleInPlaceUIWindow](/windows/win32/api/oleidl/nn-oleidl-ioleinplaceuiwindow) en el Windows SDK.

Se trata de un reemplazable avanzado.

##  <a name="onsethostnames"></a>  COleServerDoc::OnSetHostNames

Lo llama el marco de trabajo cuando el contenedor establece o cambia los nombres de host para este documento.

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

### <a name="remarks"></a>Comentarios

La implementación predeterminada cambia el título del documento para todas las vistas que hacen referencia a este documento.

Invalide esta función si la aplicación establece los títulos a través de un mecanismo diferente.

##  <a name="onsetitemrects"></a>  COleServerDoc::OnSetItemRects

El marco de trabajo llama a esta función para colocar la ventana de marco de edición en contexto dentro de la ventana de marco de la aplicación contenedora.

```
virtual void OnSetItemRects(
    LPCRECT lpPosRect,
    LPCRECT lpClipRect);
```

### <a name="parameters"></a>Parámetros

*lpPosRect*<br/>
Puntero a una `RECT` estructura o un `CRect` objeto que especifica la posición de la ventana de marco en contexto con respecto al área de cliente de la aplicación contenedora.

*lpClipRect*<br/>
Puntero a una `RECT` estructura o un `CRect` objeto que especifica el rectángulo de recorte de la ventana de marco en contexto en relación con el área de cliente de la aplicación contenedora.

### <a name="remarks"></a>Comentarios

Invalide esta función para actualizar el factor de zoom de la vista, si es necesario.

Normalmente, se llama a esta función en respuesta `RequestPositionChange` a una llamada, aunque el contenedor puede llamar en cualquier momento para solicitar un cambio de posición para el elemento en contexto.

##  <a name="onshowcontrolbars"></a>  COleServerDoc::OnShowControlBars

El marco de trabajo llama a esta función para mostrar u ocultar las barras de control de la aplicación de servidor asociadas a la ventana de marco identificada por *pFrameWnd*.

```
virtual void OnShowControlBars(
    CFrameWnd* pFrameWnd,
    BOOL bShow);
```

### <a name="parameters"></a>Parámetros

*pFrameWnd*<br/>
Puntero a la ventana de marco cuyas barras de control deben ocultarse o mostrarse.

*bShow*<br/>
Determina si se muestran o se ocultan las barras de control.

### <a name="remarks"></a>Comentarios

En la implementación predeterminada se enumeran todas las barras de control que son propiedad de esa ventana de marco y se ocultan o se muestran.

##  <a name="onshowdocument"></a>  COleServerDoc::OnShowDocument

El marco de trabajo `OnShowDocument` llama a la función cuando se debe ocultar o mostrar el documento del servidor.

```
virtual void OnShowDocument(BOOL bShow);
```

### <a name="parameters"></a>Parámetros

*bShow*<br/>
Especifica si la interfaz de usuario del documento se va a mostrar u ocultar.

### <a name="remarks"></a>Comentarios

Si *bShow* es true, la implementación predeterminada activa la aplicación de servidor, si es necesario, y hace que la aplicación contenedora desplace su ventana para que el elemento esté visible. Si *bShow* es false, la implementación predeterminada desactiva el elemento a través de una llamada a `OnDeactivate`; a continuación, destruye u oculta todas las ventanas de marco que se han creado para el documento, excepto la primera. Si no queda ningún documento visible, la implementación predeterminada oculta la aplicación de servidor.

##  <a name="onupdatedocument"></a>  COleServerDoc::OnUpdateDocument

Lo llama el marco de trabajo al guardar un documento que es un elemento incrustado en un documento compuesto.

```
virtual BOOL OnUpdateDocument();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el documento se actualizó correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

La implementación predeterminada llama a las funciones miembro [COleServerDoc:: NotifySaved](#notifysaved) y [COleServerDoc:: SaveEmbedding](#saveembedding) y, a continuación, marca el documento como Clean. Invalide esta función si desea realizar un procesamiento especial al actualizar un elemento incrustado.

##  <a name="requestpositionchange"></a>  COleServerDoc::RequestPositionChange

Llame a esta función miembro para que la aplicación contenedora cambie la posición del elemento.

```
void RequestPositionChange(LPCRECT lpPosRect);
```

### <a name="parameters"></a>Parámetros

*lpPosRect*<br/>
Puntero a una `RECT` estructura o un `CRect` objeto que contiene la nueva posición del elemento.

### <a name="remarks"></a>Comentarios

Normalmente, se llama a esta función (junto `UpdateAllItems`con) cuando cambian los datos de un elemento activo en contexto. Después de esta llamada, el contenedor puede o no realizar el cambio llamando a `OnSetItemRects`. La posición resultante puede ser diferente de la solicitada.

##  <a name="saveembedding"></a>  COleServerDoc::SaveEmbedding

Llame a esta función para indicar a la aplicación contenedora que guarde el objeto incrustado.

```
void SaveEmbedding();
```

### <a name="remarks"></a>Comentarios

Se llama a esta función automáticamente `OnUpdateDocument`desde. Tenga en cuenta que esta función hace que el elemento se actualice en el disco, por lo que normalmente solo se llama como resultado de una acción del usuario específica.

##  <a name="scrollcontainerby"></a>  COleServerDoc::ScrollContainerBy

Llame a `ScrollContainerBy` la función miembro para desplazar el documento contenedor por la cantidad, en píxeles `sizeScroll`, indicada por.

```
BOOL ScrollContainerBy(CSize sizeScroll);
```

### <a name="parameters"></a>Parámetros

*sizeScroll*<br/>
Indica hasta qué punto se va a desplazar el documento del contenedor.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Los valores positivos indican desplazarse hacia abajo y hacia la derecha; los valores negativos indican desplazarse hacia arriba y hacia la izquierda.

##  <a name="updateallitems"></a>  COleServerDoc::UpdateAllItems

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

- El elemento DVASPECT_CONTENT se representa de tal forma que se puede mostrar como un objeto incrustado dentro de su contenedor.

- El elemento DVASPECT_THUMBNAIL se representa en una representación "en miniatura" para que se pueda mostrar en una herramienta de exploración.

- El elemento DVASPECT_ICON se representa mediante un icono.

- El elemento DVASPECT_DOCPRINT se representa como si se imprimiera con el comando imprimir del menú archivo.

### <a name="remarks"></a>Comentarios

Normalmente, se llama a esta función después de que el usuario cambie el documento del servidor. Si un elemento OLE está vinculado al documento con un vínculo automático, el elemento se actualiza para reflejar los cambios. En las aplicaciones contenedoras escritas con la biblioteca MFC, se llama a la función miembro [OnChange](../../mfc/reference/coleclientitem-class.md#onchange) de `COleClientItem` en su lugar.

Esta función llama a `OnUpdate` la función miembro para cada uno de los elementos del documento excepto el elemento de envío, pasando *pHint*, *lHint*y *nDrawAspect*. Utilice estos parámetros para pasar información a los elementos sobre las modificaciones realizadas en el documento. Puede codificar información mediante *lHint* o puede definir una `CObject`clase derivada de para almacenar información sobre las modificaciones y pasar un objeto de esa clase mediante *pHint*. Invalide la `OnUpdate` función miembro `COleServerItem`en la clase derivada de para optimizar la actualización de cada elemento en función de si su presentación ha cambiado.

## <a name="see-also"></a>Vea también

[Ejemplo de MFC HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[COleLinkingDoc (clase)](../../mfc/reference/colelinkingdoc-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[COleDocument (clase)](../../mfc/reference/coledocument-class.md)<br/>
[COleLinkingDoc (clase)](../../mfc/reference/colelinkingdoc-class.md)<br/>
[COleTemplateServer (clase)](../../mfc/reference/coletemplateserver-class.md)
