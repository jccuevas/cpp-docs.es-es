---
title: COleServerItem (clase)
ms.date: 11/04/2016
f1_keywords:
- COleServerItem
- AFXOLE/COleServerItem
- AFXOLE/COleServerItem::COleServerItem
- AFXOLE/COleServerItem::AddOtherClipboardData
- AFXOLE/COleServerItem::CopyToClipboard
- AFXOLE/COleServerItem::DoDragDrop
- AFXOLE/COleServerItem::GetClipboardData
- AFXOLE/COleServerItem::GetDocument
- AFXOLE/COleServerItem::GetEmbedSourceData
- AFXOLE/COleServerItem::GetItemName
- AFXOLE/COleServerItem::GetLinkSourceData
- AFXOLE/COleServerItem::GetObjectDescriptorData
- AFXOLE/COleServerItem::IsConnected
- AFXOLE/COleServerItem::IsLinkedItem
- AFXOLE/COleServerItem::NotifyChanged
- AFXOLE/COleServerItem::OnDoVerb
- AFXOLE/COleServerItem::OnDraw
- AFXOLE/COleServerItem::OnDrawEx
- AFXOLE/COleServerItem::OnGetClipboardData
- AFXOLE/COleServerItem::OnGetExtent
- AFXOLE/COleServerItem::OnInitFromData
- AFXOLE/COleServerItem::OnQueryUpdateItems
- AFXOLE/COleServerItem::OnRenderData
- AFXOLE/COleServerItem::OnRenderFileData
- AFXOLE/COleServerItem::OnRenderGlobalData
- AFXOLE/COleServerItem::OnSetColorScheme
- AFXOLE/COleServerItem::OnSetData
- AFXOLE/COleServerItem::OnSetExtent
- AFXOLE/COleServerItem::OnUpdate
- AFXOLE/COleServerItem::OnUpdateItems
- AFXOLE/COleServerItem::SetItemName
- AFXOLE/COleServerItem::GetDataSource
- AFXOLE/COleServerItem::OnHide
- AFXOLE/COleServerItem::OnOpen
- AFXOLE/COleServerItem::OnShow
- AFXOLE/COleServerItem::m_sizeExtent
helpviewer_keywords:
- COleServerItem [MFC], COleServerItem
- COleServerItem [MFC], AddOtherClipboardData
- COleServerItem [MFC], CopyToClipboard
- COleServerItem [MFC], DoDragDrop
- COleServerItem [MFC], GetClipboardData
- COleServerItem [MFC], GetDocument
- COleServerItem [MFC], GetEmbedSourceData
- COleServerItem [MFC], GetItemName
- COleServerItem [MFC], GetLinkSourceData
- COleServerItem [MFC], GetObjectDescriptorData
- COleServerItem [MFC], IsConnected
- COleServerItem [MFC], IsLinkedItem
- COleServerItem [MFC], NotifyChanged
- COleServerItem [MFC], OnDoVerb
- COleServerItem [MFC], OnDraw
- COleServerItem [MFC], OnDrawEx
- COleServerItem [MFC], OnGetClipboardData
- COleServerItem [MFC], OnGetExtent
- COleServerItem [MFC], OnInitFromData
- COleServerItem [MFC], OnQueryUpdateItems
- COleServerItem [MFC], OnRenderData
- COleServerItem [MFC], OnRenderFileData
- COleServerItem [MFC], OnRenderGlobalData
- COleServerItem [MFC], OnSetColorScheme
- COleServerItem [MFC], OnSetData
- COleServerItem [MFC], OnSetExtent
- COleServerItem [MFC], OnUpdate
- COleServerItem [MFC], OnUpdateItems
- COleServerItem [MFC], SetItemName
- COleServerItem [MFC], GetDataSource
- COleServerItem [MFC], OnHide
- COleServerItem [MFC], OnOpen
- COleServerItem [MFC], OnShow
- COleServerItem [MFC], m_sizeExtent
ms.assetid: 80256df6-3888-4256-944b-787d4b2e6b0d
ms.openlocfilehash: c4c026975e9884ac2a0e6aaef31e799c2b5b09bf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62224238"
---
# <a name="coleserveritem-class"></a>COleServerItem (clase)

Proporciona la interfaz del servidor a elementos OLE.

## <a name="syntax"></a>Sintaxis

```
class COleServerItem : public CDocItem
```

## <a name="members"></a>Miembros

### <a name="protected-constructors"></a>Constructores protegidos

|Name|Descripción|
|----------|-----------------|
|[COleServerItem::COleServerItem](#coleserveritem)|Construye un objeto `COleServerItem`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[COleServerItem::AddOtherClipboardData](#addotherclipboarddata)|Coloca los formatos de presentación y conversión en un `COleDataSource` objeto.|
|[COleServerItem::CopyToClipboard](#copytoclipboard)|Copia el elemento en el Portapapeles.|
|[COleServerItem::DoDragDrop](#dodragdrop)|Realiza una operación de arrastrar y colocar.|
|[COleServerItem::GetClipboardData](#getclipboarddata)|Obtiene el origen de datos para su uso en la transferencia de datos (arrastrar y colocar o Portapapeles).|
|[COleServerItem::GetDocument](#getdocument)|Devuelve el documento del servidor que contiene el elemento.|
|[COleServerItem::GetEmbedSourceData](#getembedsourcedata)|Obtiene los datos CF_EMBEDSOURCE para un elemento OLE.|
|[COleServerItem::GetItemName](#getitemname)|Devuelve el nombre del elemento. Usar solo los elementos vinculados.|
|[COleServerItem::GetLinkSourceData](#getlinksourcedata)|Obtiene los datos CF_LINKSOURCE para un elemento OLE.|
|[COleServerItem::GetObjectDescriptorData](#getobjectdescriptordata)|Obtiene los datos CF_OBJECTDESCRIPTOR para un elemento OLE.|
|[COleServerItem::IsConnected](#isconnected)|Indica si el elemento está asociado actualmente a un contenedor activo.|
|[COleServerItem::IsLinkedItem](#islinkeditem)|Indica si el elemento representa un elemento OLE vinculado.|
|[COleServerItem::NotifyChanged](#notifychanged)|Actualiza todos los contenedores con la actualización automática de vínculos.|
|[COleServerItem::OnDoVerb](#ondoverb)|Se llama para ejecutar un verbo.|
|[COleServerItem::OnDraw](#ondraw)|Se llama cuando el contenedor solicita para dibujar el elemento; implementación necesaria.|
|[COleServerItem::OnDrawEx](#ondrawex)|Se llama para dibujar un elemento especializado.|
|[COleServerItem::OnGetClipboardData](#ongetclipboarddata)|Lo llama el marco de trabajo para obtener los datos que se van a copiar en el Portapapeles.|
|[COleServerItem::OnGetExtent](#ongetextent)|Lo llama el marco de trabajo para recuperar el tamaño del elemento OLE.|
|[COleServerItem::OnInitFromData](#oninitfromdata)|Lo llama el marco de trabajo para inicializar un elemento OLE utilizando el contenido del objeto de transferencia de datos especificado.|
|[COleServerItem::OnQueryUpdateItems](#onqueryupdateitems)|Se llama para determinar si hay elementos vinculados requieren actualización.|
|[COleServerItem::OnRenderData](#onrenderdata)|Recupera los datos como parte de la representación aplazada.|
|[COleServerItem::OnRenderFileData](#onrenderfiledata)|Recupera los datos en un `CFile` objeto como parte de la representación aplazada.|
|[COleServerItem::OnRenderGlobalData](#onrenderglobaldata)|Recupera los datos en un HGLOBAL como parte de la representación aplazada.|
|[COleServerItem::OnSetColorScheme](#onsetcolorscheme)|Se llama para establecer la combinación de colores del elemento.|
|[COleServerItem::OnSetData](#onsetdata)|Se llama para establecer los datos del elemento.|
|[COleServerItem::OnSetExtent](#onsetextent)|Lo llama el marco de trabajo para establecer el tamaño del elemento OLE.|
|[COleServerItem::OnUpdate](#onupdate)|Llamado cuando alguna parte del documento el elemento pertenece a se cambia.|
|[COleServerItem::OnUpdateItems](#onupdateitems)|Se llama para actualizar la memoria caché de presentación de todos los elementos del documento de servidor.|
|[COleServerItem::SetItemName](#setitemname)|Establece el nombre del elemento. Usar solo los elementos vinculados.|

### <a name="protected-methods"></a>Métodos protegidos

|Name|Descripción|
|----------|-----------------|
|[COleServerItem::GetDataSource](#getdatasource)|Obtiene el objeto utilizado para almacenar formatos de conversión.|
|[COleServerItem::OnHide](#onhide)|Lo llama el marco para ocultar el elemento OLE.|
|[COleServerItem::OnOpen](#onopen)|Lo llama el marco de trabajo para mostrar el elemento OLE en su propia ventana de nivel superior.|
|[COleServerItem::OnShow](#onshow)|Se llama cuando el contenedor solicita para mostrar el elemento.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[COleServerItem::m_sizeExtent](#m_sizeextent)|Informa al servidor acerca de la cantidad del elemento OLE está visible.|

## <a name="remarks"></a>Comentarios

Un elemento vinculado puede representar algunos o todos de un documento de servidor. Un elemento incrustado siempre representa un documento de todo el servidor.

La `COleServerItem` clase define varias funciones miembro reemplazables que son llamadas por las bibliotecas de vínculos dinámicos del sistema OLE (DLL), normalmente en respuesta a solicitudes de la aplicación contenedora. Estas funciones miembro que la aplicación de contenedor manipular el elemento indirectamente de varias maneras, como mostrarla, ejecutando sus verbos o recuperar sus datos en diversos formatos.

Para usar `COleServerItem`, derivar una clase e implementar el [OnDraw](#ondraw) y [Serialize](../../mfc/reference/cobject-class.md#serialize) funciones miembro. El `OnDraw` función proporciona la representación del metarchivo de un elemento, lo que permite que se muestre cuando una aplicación contenedora abre un documento compuesto. El `Serialize` función de `CObject` proporciona la representación nativa de un elemento, lo que permite un elemento incrustado en transferirse entre las aplicaciones de servidor y un contenedor. [OnGetExtent](#ongetextent) proporciona el tamaño natural del elemento en el contenedor, lo que permite el contenedor cambiar el tamaño del elemento.

Para obtener más información acerca de los servidores y otros temas relacionados, vea el artículo [servidores: Implementación de un servidor](../../mfc/servers-implementing-a-server.md) y "Creación de una aplicación de contenedor y servidor" en el artículo [contenedores: Características avanzadas](../../mfc/containers-advanced-features.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocItem](../../mfc/reference/cdocitem-class.md)

`COleServerItem`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxole.h

##  <a name="addotherclipboarddata"></a>  COleServerItem::AddOtherClipboardData

Llame a esta función para colocar los formatos de presentación y conversión para el elemento OLE en especificado `COleDataSource` objeto.

```
void AddOtherClipboardData(COleDataSource* pDataSource);
```

### <a name="parameters"></a>Parámetros

*pDataSource*<br/>
Puntero a la `COleDataSource` en que se deben colocar los datos de objeto.

### <a name="remarks"></a>Comentarios

Debe haber implementado el [OnDraw](#ondraw) función miembro para proporcionar el formato de presentación (una imagen de metarchivo) para el elemento. Para admitir otros formatos de conversión, registrarlos mediante el [COleDataSource](../../mfc/reference/coledatasource-class.md) objeto devuelto por [GetDataSource](#getdatasource) e invalidar la [OnRenderData](#onrenderdata) función miembro proporcionar los datos en los formatos que desea admitir.

##  <a name="coleserveritem"></a>  COleServerItem::COleServerItem

Construye un `COleServerItem` objeto y lo agrega a la colección del documento de servidor de elementos de documento.

```
COleServerItem(
    COleServerDoc* pServerDoc,
    BOOL bAutoDelete);
```

### <a name="parameters"></a>Parámetros

*pServerDoc*<br/>
Puntero al documento que contendrá el nuevo elemento.

*bAutoDelete*<br/>
Marca que indica si el objeto se puede eliminar cuando se suelta un vínculo a él. Establezca esta opción en FALSE si el `COleServerItem` objeto es una parte integral de los datos del documento que deben eliminar. Establézcalo en TRUE si el objeto es una estructura secundaria usada para identificar un intervalo en los datos del documento que se pueden eliminar mediante el marco de trabajo.

##  <a name="copytoclipboard"></a>  COleServerItem::CopyToClipboard

Llame a esta función para copiar el elemento OLE en el Portapapeles.

```
void CopyToClipboard(BOOL bIncludeLink = FALSE);
```

### <a name="parameters"></a>Parámetros

*bIncludeLink*<br/>
Establezca esta opción en TRUE si se deben copiar los datos del vínculo en el Portapapeles. Establézcalo en FALSE si el servidor de aplicación no admite vínculos.

### <a name="remarks"></a>Comentarios

La función utiliza el [OnGetClipboardData](#ongetclipboarddata) función miembro para crear un [COleDataSource](../../mfc/reference/coledatasource-class.md) objeto que contiene los datos del elemento OLE en los formatos admitidos. La función, a continuación, coloca el `COleDataSource` objeto en el Portapapeles mediante el uso de la [COleDataSource:: SetClipboard](../../mfc/reference/coledatasource-class.md#setclipboard) función. La `COleDataSource` objeto incluye los datos del elemento nativo y su representación en formato CF_METAFILEPICT, así como los datos en cualquier formato de conversión decide admitir. Debe haber implementado [Serialize](../../mfc/reference/cobject-class.md#serialize) y [OnDraw](#ondraw) para esta función miembro para que funcione.

##  <a name="dodragdrop"></a>  COleServerItem::DoDragDrop

Llame a la `DoDragDrop` la función miembro para realizar una operación de arrastrar y colocar.

```
DROPEFFECT DoDragDrop(
    LPCRECT lpRectItem,
    CPoint ptOffset,
    BOOL bIncludeLink = FALSE,
    DWORD dwEffects = DROPEFFECT_COPY | DROPEFFECT_MOVE,
    LPCRECT lpRectStartDrag = NULL);
```

### <a name="parameters"></a>Parámetros

*lpRectItem*<br/>
Rectángulo del elemento en la pantalla, en píxeles, relativo al área cliente.

*ptOffset*<br/>
El desplazamiento desde *lpItemRect* que era la posición del mouse en el momento de la operación de arrastrar.

*bIncludeLink*<br/>
Establezca esta opción en TRUE si se deben copiar los datos del vínculo en el Portapapeles. Establézcalo en FALSE si la aplicación no admite vínculos.

*dwEffects*<br/>
Determina los efectos que permitirá que el origen de arrastre en la operación de arrastre (una combinación de copiar, mover y vínculo).

*lpRectStartDrag*<br/>
Puntero al rectángulo que define el donde realmente comienza la operación de arrastrar. Para obtener más información, vea la sección Comentarios que se muestra más adelante.

### <a name="return-value"></a>Valor devuelto

Un valor de la enumeración EFECTOCOLOCAR. Si es DROPEFFECT_MOVE, deben quitarse los datos originales.

### <a name="remarks"></a>Comentarios

No se inicie inmediatamente la operación de arrastrar y colocar. Espera hasta que el cursor del mouse sale del rectángulo especificado por *lpRectStartDrag* o hasta que un número especificado de milisegundos que ha pasado. Si *lpRectStartDrag* es NULL, se usa un rectángulo predeterminado para que la operación de arrastrar se inicia cuando el cursor del mouse mueve un píxel.

El tiempo de retraso especificado por un valor de clave del registro. Puede cambiar el tiempo de retraso mediante una llamada a [CWinApp::WriteProfileString](../../mfc/reference/cwinapp-class.md#writeprofilestring) o [CWinApp:: Writeprofileint](../../mfc/reference/cwinapp-class.md#writeprofileint). Si no especifica el tiempo de retraso, se usa el valor predeterminado es 200 milisegundos. Tiempo de retraso de arrastre se almacena como sigue:

- Tiempo de retraso de arrastre de Windows NT se almacena en HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\NT\CurrentVersion\IniFileMapping\win.ini\Windows\DragDelay.

- Retrasar hora de Windows 3.x arrastrar se almacena en el archivo WIN. Archivo INI, la sección [Windows}.

- Tiempo de retraso de arrastre de Windows 95/98 se almacena en una versión en caché de WIN. INI.

Para obtener más información acerca de cómo arrastrar se almacena información sobre los retrasos en el registro o el. Archivo INI, consulte [WriteProfileString](/windows/desktop/api/winbase/nf-winbase-writeprofilestringa) en el SDK de Windows.

##  <a name="getclipboarddata"></a>  COleServerItem::GetClipboardData

Llame a esta función para rellenar especificado [COleDataSource](../../mfc/reference/coledatasource-class.md) objeto con todos los datos que se van a copiar al Portapapeles si llama a [CopyToClipboard](#copytoclipboard) (los mismos datos también se transferiría si le llama a [DoDragDrop](#dodragdrop)).

```
void GetClipboardData(
    COleDataSource* pDataSource,
    BOOL bIncludeLink = FALSE,
    LPPOINT lpOffset = NULL,
    LPSIZE lpSize = NULL);
```

### <a name="parameters"></a>Parámetros

*pDataSource*<br/>
Puntero a la `COleDataSource` objeto que recibirá los datos del elemento OLE en todos los formatos admitidos.

*bIncludeLink*<br/>
TRUE si se deben copiar los datos del vínculo en el Portapapeles. FALSE si la aplicación de servidor no admite vínculos.

*lpOffset*<br/>
El desplazamiento, en píxeles, del cursor del mouse desde el origen del objeto.

*lpSize*<br/>
El tamaño del objeto en píxeles.

### <a name="remarks"></a>Comentarios

Esta función llama a la [GetEmbedSourceData](#getembedsourcedata) función miembro para obtener los datos nativos para el elemento OLE y llama el [AddOtherClipboardData](#addotherclipboarddata) para obtener el formato de presentación y cualquier función miembro admite formatos de conversión. Si *bIncludeLink* es TRUE, la función también llamadas [GetLinkSourceData](#getlinksourcedata) para obtener los datos de vínculo para el elemento.

Reemplace esta función si desea colocar los formatos un `COleDataSource` objeto antes o después de esos formatos proporcionados por `CopyToClipboard`.

##  <a name="getdatasource"></a>  COleServerItem::GetDataSource

Llame a esta función para obtener el [COleDataSource](../../mfc/reference/coledatasource-class.md) objeto utilizado para almacenar los formatos de conversión que admite la aplicación de servidor.

```
COleDataSource* GetDataSource();
```

### <a name="return-value"></a>Valor devuelto

Un puntero a la `COleDataSource` objeto utilizado para almacenar los formatos de conversión.

### <a name="remarks"></a>Comentarios

Si desea que la aplicación de servidor para ofrecer datos en una variedad de formatos durante la transferencia de datos de las operaciones, registrar dichos formatos con los `COleDataSource` objeto devuelto por esta función. Por ejemplo, si desea proporcionar una representación CF_TEXT del elemento OLE para Portapapeles u operaciones de arrastrar y colocar, registrar el formato con el `COleDataSource` esta función devuelve el objeto e invalide el `OnRenderXxxData` función miembro proporcionar los datos.

##  <a name="getdocument"></a>  COleServerItem::GetDocument

Llame a esta función para obtener un puntero al documento que contiene el elemento.

```
COleServerDoc* GetDocument() const;
```

### <a name="return-value"></a>Valor devuelto

Un puntero al documento que contiene el elemento; Es NULL si el elemento no forma parte de un documento.

### <a name="remarks"></a>Comentarios

Esto permite el acceso al documento de servidor que pasa como argumento a la `COleServerItem` constructor.

##  <a name="getembedsourcedata"></a>  COleServerItem::GetEmbedSourceData

Llame a esta función para obtener los datos CF_EMBEDSOURCE para un elemento OLE.

```
void GetEmbedSourceData(LPSTGMEDIUM lpStgMedium);
```

### <a name="parameters"></a>Parámetros

*lpStgMedium*<br/>
Puntero a la [STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium) estructura que recibirá los datos CF_EMBEDSOURCE para el elemento OLE.

### <a name="remarks"></a>Comentarios

Este formato incluye los datos del elemento nativo. Debe haber implementado el `Serialize` función miembro de esta función para que funcione correctamente.

El resultado puede agregarse a un origen de datos mediante [:: CacheData](../../mfc/reference/coledatasource-class.md#cachedata). Esta función llama de forma automática [COleServerItem::OnGetClipboardData](#ongetclipboarddata).

Para obtener más información, consulte [STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium) en el SDK de Windows.

##  <a name="getitemname"></a>  COleServerItem::GetItemName

Llame a esta función para obtener el nombre del elemento.

```
const CString& GetItemName() const;
```

### <a name="return-value"></a>Valor devuelto

Nombre del elemento.

### <a name="remarks"></a>Comentarios

Se suele llamar a esta función solo para los elementos vinculados.

##  <a name="getlinksourcedata"></a>  COleServerItem::GetLinkSourceData

Llame a esta función para obtener los datos CF_LINKSOURCE para un elemento OLE.

```
BOOL GetLinkSourceData(LPSTGMEDIUM lpStgMedium);
```

### <a name="parameters"></a>Parámetros

*lpStgMedium*<br/>
Puntero a la [STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium) estructura que recibirá los datos CF_LINKSOURCE para el elemento OLE.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Este formato incluye el CLSID que describe el tipo de elemento OLE y la información necesaria para encontrar el documento que contiene el elemento OLE.

El resultado, a continuación, se puede agregar a un origen de datos con [:: CacheData](../../mfc/reference/coledatasource-class.md#cachedata). Esta función llama de forma automática [OnGetClipboardData](#ongetclipboarddata).

Para obtener más información, consulte [STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium) en el SDK de Windows.

##  <a name="getobjectdescriptordata"></a>  COleServerItem::GetObjectDescriptorData

Llame a esta función para obtener los datos CF_OBJECTDESCRIPTOR para un elemento OLE.

```
void GetObjectDescriptorData(
    LPPOINT lpOffset,
    LPSIZE lpSize,
    LPSTGMEDIUM lpStgMedium);
```

### <a name="parameters"></a>Parámetros

*lpOffset*<br/>
Haga clic en el desplazamiento del mouse en la esquina superior izquierda del elemento OLE. Puede ser NULL.

*lpSize*<br/>
Tamaño del elemento OLE. Puede ser NULL.

*lpStgMedium*<br/>
Puntero a la [STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium) estructura que recibirá los datos CF_OBJECTDESCRIPTOR para el elemento OLE.

### <a name="remarks"></a>Comentarios

La información se copia en el `STGMEDIUM` estructura apunta *lpStgMedium*. Este formato incluye la información necesaria para el cuadro de diálogo Pegado especial.

Para obtener más información, consulte [STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium) en el SDK de Windows.

##  <a name="isconnected"></a>  COleServerItem::IsConnected

Llame a esta función para ver si está conectado el elemento OLE.

```
BOOL IsConnected() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el elemento está conectado; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Un elemento OLE se considera conectado si uno o varios contenedores tienen referencias al elemento. Está conectado a un elemento si su recuento de referencias es mayor que 0 o si es un elemento incrustado.

##  <a name="islinkeditem"></a>  COleServerItem::IsLinkedItem

Llame a esta función para ver si el elemento OLE es un elemento vinculado.

```
BOOL IsLinkedItem() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el elemento es un elemento vinculado; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Está enlazado a un elemento si el elemento es válido y no se devuelve en la lista del documento de los elementos incrustados. Un elemento vinculado podría o no esté conectado a un contenedor.

Es habitual usar la misma clase para los elementos vinculados e incrustados. `IsLinkedItem` permite hacer que los elementos vinculados se comportan de manera diferente a los elementos incrustados, aunque muchas veces el código es común.

##  <a name="m_sizeextent"></a>  COleServerItem::m_sizeExtent

Este miembro indica al servidor la cantidad del objeto está visible en el documento contenedor.

```
CSize m_sizeExtent;
```

### <a name="remarks"></a>Comentarios

La implementación predeterminada de [OnSetExtent](#onsetextent) establece este miembro.

##  <a name="notifychanged"></a>  COleServerItem::NotifyChanged

Llame a esta función después de que el elemento vinculado ha cambiado.

```
void NotifyChanged(DVASPECT nDrawAspect = DVASPECT_CONTENT);
```

### <a name="parameters"></a>Parámetros

*nDrawAspect*<br/>
Ha cambiado un valor de la enumeración DVASPECT que indica qué aspecto del elemento OLE. Este parámetro puede tener cualquiera de los siguientes valores:

- Elemento DVASPECT_CONTENT se representa de manera que puede mostrarse como un objeto incrustado dentro de su contenedor.

- DVASPECT_THUMBNAIL se representa en una representación de "miniatura" para que se puede mostrar en una herramienta de exploración.

- Elemento DVASPECT_ICON se representa mediante un icono.

- Elemento DVASPECT_DOCPRINT se representa como si se imprimiera utilizando el comando de impresión en el menú archivo.

### <a name="remarks"></a>Comentarios

Si un elemento contenedor está vinculado al documento con un vínculo automático, el elemento se actualiza para reflejar los cambios. En las aplicaciones de contenedor escritas mediante la biblioteca Microsoft Foundation Class [COleClientItem](../../mfc/reference/coleclientitem-class.md#onchange) se llama en respuesta.

##  <a name="ondoverb"></a>  COleServerItem::OnDoVerb

Lo llama el marco de trabajo para ejecutar el verbo especificado.

```
virtual void OnDoVerb(LONG iVerb);
```

### <a name="parameters"></a>Parámetros

*iVerb*<br/>
Especifica el verbo que se ejecute. Puede ser cualquiera de las siguientes acciones:

|Valor|Significado|Símbolo|
|-----------|-------------|------------|
|0|verbo principal|OLEIVERB_PRIMARY|
|1|Verbo secundaria|(Ninguno)|
|- 1|Elemento de presentación para su edición|OLEIVERB_SHOW|
|- 2|Editar elemento en una ventana independiente|OLEIVERB_OPEN|
|- 3|Ocultar elementos|OLEIVERB_HIDE|

Normalmente, el valor-1 es un alias para otro verbo. Si no se admite la edición abierto, -2 tiene el mismo efecto que -1. Para los valores adicionales, consulte [DoVerb](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-doverb) en el SDK de Windows.

### <a name="remarks"></a>Comentarios

Si se escribió la aplicación de contenedor con la biblioteca Microsoft Foundation Class, esta función se llama cuando el [COleClientItem::Activate](../../mfc/reference/coleclientitem-class.md#activate) función miembro de la correspondiente `COleClientItem` se denomina objeto. La implementación predeterminada llama el [OnShow](#onshow) función de miembro si se especifica el verbo principal o OLEIVERB_SHOW, [OnOpen](#onopen) si se especifica el verbo secundaria o OLEIVERB_OPEN, y [OnHide ](#onhide) si se especifica OLEIVERB_HIDE. La implementación predeterminada llama `OnShow` si *iVerb* no es uno de los verbos enumerados anteriormente.

Reemplace esta función si el verbo principal no muestra el elemento. Por ejemplo, si el elemento es una grabación de sonido y su verbo principal es reproducir, no tendría que mostrar la aplicación de servidor para reproducir el elemento.

Para obtener más información, consulte [DoVerb](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-doverb) en el SDK de Windows.

##  <a name="ondraw"></a>  COleServerItem::OnDraw

Lo llama el marco de trabajo para representar el elemento OLE en un metarchivo.

```
virtual BOOL OnDraw(
    CDC* pDC,
    CSize& rSize) = 0;
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
Un puntero a la [CDC](../../mfc/reference/cdc-class.md) objeto en el que se va a dibujar el elemento. El contexto de presentación se conecta automáticamente el contexto de presentación de atributo para que pueda llamar a funciones de atributo, aunque el hacerlo implicará que metarchivo específico del dispositivo.

*rSize*<br/>
Tamaño, en unidades HIMETRIC, en el que se va a dibujar el metarchivo.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el elemento se ha dibujado correctamente; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

La representación del metarchivo del elemento OLE se utiliza para mostrar el elemento de la aplicación contenedora. Si se escribió la aplicación de contenedor con la biblioteca Microsoft Foundation Class, metarchivo está usando el [dibujar](../../mfc/reference/coleclientitem-class.md#draw) función miembro de la correspondiente [COleClientItem](../../mfc/reference/coleclientitem-class.md) objeto. No hay ninguna implementación predeterminada. Debe reemplazar esta función para dibujar el elemento en el contexto de dispositivo especificado.

##  <a name="ondrawex"></a>  COleServerItem::OnDrawEx

Lo llama el marco de trabajo para todos los dibujos.

```
virtual BOOL OnDrawEx(
    CDC* pDC,
    DVASPECT nDrawAspect,
    CSize& rSize);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
Un puntero a la [CDC](../../mfc/reference/cdc-class.md) objeto en el que se va a dibujar el elemento. El controlador de dominio se conecta automáticamente el atributo de controlador de dominio para que pueda llamar a funciones de atributo, aunque el hacerlo implicará que metarchivo específico del dispositivo.

*nDrawAspect*<br/>
Un valor de la enumeración DVASPECT. Este parámetro puede tener cualquiera de los siguientes valores:

- Elemento DVASPECT_CONTENT se representa de manera que puede mostrarse como un objeto incrustado dentro de su contenedor.

- DVASPECT_THUMBNAIL se representa en una representación de "miniatura" para que se puede mostrar en una herramienta de exploración.

- Elemento DVASPECT_ICON se representa mediante un icono.

- Elemento DVASPECT_DOCPRINT se representa como si se imprimiera utilizando el comando de impresión en el menú archivo.

*rSize*<br/>
Tamaño del elemento en unidades HIMETRIC.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el elemento se ha dibujado correctamente; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

La implementación predeterminada llama `OnDraw` cuando DVASPECT es igual a DVASPECT_CONTENT; en caso contrario, se produce un error.

Reemplace esta función para proporcionar datos de la presentación de aspectos que no sea DVASPECT_CONTENT como DVASPECT_ICON o DVASPECT_THUMBNAIL.

##  <a name="ongetclipboarddata"></a>  COleServerItem::OnGetClipboardData

Lo llama el marco para obtener un `COleDataSource` objeto que contiene todos los datos que se colocarían en el Portapapeles mediante una llamada a la [CopyToClipboard](#copytoclipboard) función miembro.

```
virtual COleDataSource* OnGetClipboardData(
    BOOL bIncludeLink,
    LPPOINT lpOffset,
    LPSIZE lpSize);
```

### <a name="parameters"></a>Parámetros

*bIncludeLink*<br/>
Establezca esta opción en TRUE si se deben copiar los datos del vínculo en el Portapapeles. Establézcalo en FALSE si el servidor de aplicación no admite vínculos.

*lpOffset*<br/>
El desplazamiento del cursor del mouse desde el origen del objeto en píxeles.

*lpSize*<br/>
El tamaño del objeto en píxeles.

### <a name="return-value"></a>Valor devuelto

Un puntero a un [COleDataSource](../../mfc/reference/coledatasource-class.md) objeto que contiene los datos del Portapapeles.

### <a name="remarks"></a>Comentarios

La implementación predeterminada de esta función llama [GetClipboardData](#getclipboarddata).

##  <a name="ongetextent"></a>  COleServerItem::OnGetExtent

Lo llama el marco de trabajo para recuperar el tamaño, en unidades HIMETRIC del elemento OLE.

```
virtual BOOL OnGetExtent(
    DVASPECT nDrawAspect,
    CSize& rSize);
```

### <a name="parameters"></a>Parámetros

*nDrawAspect*<br/>
Especifica el aspecto del producto OLE cuyos límites se van a recuperar. Este parámetro puede tener cualquiera de los siguientes valores:

- Elemento DVASPECT_CONTENT se representa de manera que puede mostrarse como un objeto incrustado dentro de su contenedor.

- DVASPECT_THUMBNAIL se representa en una representación de "miniatura" para que se puede mostrar en una herramienta de exploración.

- Elemento DVASPECT_ICON se representa mediante un icono.

- Elemento DVASPECT_DOCPRINT se representa como si se imprimiera utilizando el comando de impresión en el menú archivo.

*rSize*<br/>
Hacer referencia a un `CSize` objeto que recibirá el tamaño del elemento OLE.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Si se escribió la aplicación de contenedor con la biblioteca Microsoft Foundation Class, esta función se llama cuando el [GetExtent](../../mfc/reference/coleclientitem-class.md#getextent) función miembro de la correspondiente `COleClientItem` se denomina objeto. La implementación predeterminada no hace nada. Debe implementarlo usted mismo. Reemplace esta función si desea realizar un procesamiento especial cuando controla una solicitud para el tamaño del elemento OLE.

##  <a name="onhide"></a>  COleServerItem::OnHide

Lo llama el marco para ocultar el elemento OLE.

```
virtual void OnHide();
```

### <a name="remarks"></a>Comentarios

Las llamadas de forma predeterminada `COleServerDoc::OnShowDocument( FALSE )`. La función también notifica al contenedor que el elemento OLE se ha ocultado. Reemplace esta función si desea realizar un procesamiento especial al ocultar un elemento OLE.

##  <a name="oninitfromdata"></a>  COleServerItem::OnInitFromData

Lo llama el marco para inicializar un elemento OLE utilizando el contenido de *pDataObject*.

```
virtual BOOL OnInitFromData(
    COleDataObject* pDataObject,
    BOOL bCreation);
```

### <a name="parameters"></a>Parámetros

*pDataObject*<br/>
Puntero a un objeto de datos OLE que contiene los datos en varios formatos para inicializar el elemento OLE.

*bCreation*<br/>
TRUE si la función se llama para inicializar un elemento OLE recién creando una aplicación contenedora. FALSE si se llama a la función para reemplazar el contenido de un elemento OLE ya existente.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Si *bCreation* es TRUE, se llama a esta función si un contenedor implementa Insertar nuevo objeto basándose en la selección actual. Los datos seleccionados se usan al crear el nuevo elemento OLE. Por ejemplo, al seleccionar un rango de celdas en una hoja de cálculo y, a continuación, Insertar nuevo objeto para crear un gráfico según los valores del intervalo seleccionado. La implementación predeterminada no hace nada. Reemplace esta función para elegir un formato aceptable entre los que ofrecen *pDataObject* e inicializar el elemento OLE en función de los datos proporcionados. Esto es un avanzado que se puede invalidar.

Para obtener más información, consulte [IOleObject:: InitFromData](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-initfromdata) en el SDK de Windows.

##  <a name="onopen"></a>  COleServerItem::OnOpen

Lo llama el marco de trabajo para mostrar el elemento OLE en una instancia independiente de la aplicación de servidor, en lugar de en su lugar.

```
virtual void OnOpen();
```

### <a name="remarks"></a>Comentarios

La implementación predeterminada activa la primera ventana de marco que se muestra el documento que contiene el elemento OLE; Si la aplicación es un servidor mínima, la implementación predeterminada muestra la ventana principal. La función también notifica al contenedor que se ha abierto el elemento OLE.

Si desea realizar un procesamiento especial al abrir un elemento OLE, reemplace esta función. Esto es especialmente común con los elementos vinculados donde desee establecer la selección en el vínculo cuando se abre.

Para obtener más información, consulte [IOleClientSite::OnShowWindow](/windows/desktop/api/oleidl/nf-oleidl-ioleclientsite-onshowwindow) en el SDK de Windows.

##  <a name="onqueryupdateitems"></a>  COleServerItem::OnQueryUpdateItems

Lo llama el marco de trabajo para determinar si hay elementos vinculados en el documento del servidor actual no están actualizados.

```
virtual BOOL OnQueryUpdateItems();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el documento tiene los elementos que necesitan actualizaciones; 0 si todos los elementos están actualizados.

### <a name="remarks"></a>Comentarios

Un elemento es obsoleto si se ha cambiado su documento de origen pero el elemento vinculado no se ha actualizado para reflejar los cambios en el documento.

##  <a name="onrenderdata"></a>  COleServerItem::OnRenderData

Lo llama el marco de trabajo para recuperar los datos en el formato especificado.

```
virtual BOOL OnRenderData(
    LPFORMATETC lpFormatEtc,
    LPSTGMEDIUM lpStgMedium);
```

### <a name="parameters"></a>Parámetros

*lpFormatEtc*<br/>
Apunta a la [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) estructura que especifica el formato en el que se solicita información.

*lpStgMedium*<br/>
Apunta a un [STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium) estructura en el que los datos se va a devolver.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

El formato especificado es una colocado anteriormente en el `COleDataSource` objeto utilizando el [DelayRenderData](../../mfc/reference/coledatasource-class.md#delayrenderdata) o [DelayRenderFileData](../../mfc/reference/coledatasource-class.md#delayrenderfiledata) función miembro para la representación aplazada. La implementación predeterminada de esta función llama [OnRenderFileData](#onrenderfiledata) o [OnRenderGlobalData](#onrenderglobaldata), respectivamente, si el medio de almacenamiento proporcionado es un archivo o la memoria. Si se proporciona ninguno de estos formatos, la implementación predeterminada devuelve 0 y no hace nada.

Si *lpStgMedium*-> *tymed* es TYMED_NULL, el STGMEDIUM debe asignado y rellenado según lo especificado por *lpFormatEtc -> tymed*. Si no TYMED_NULL, el STGMEDIUM debe rellenarse en lugar de con los datos.

Esto es un avanzado que se puede invalidar. Reemplace esta función para proporcionar los datos en el formato solicitado y medio. Dependiendo de los datos, puede reemplazar una de las otras versiones de esta función en su lugar. Si los datos están pequeño y un tamaño fijo, invalidar `OnRenderGlobalData`. Si los datos están en un archivo o es de tamaño variable, invalidar `OnRenderFileData`.

Para obtener más información, consulte [IDataObject:: GetData](/windows/desktop/api/objidl/nf-objidl-idataobject-getdata), [STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium), [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc), y [TYMED](/windows/desktop/api/objidl/ne-objidl-tagtymed) en el SDK de Windows.

##  <a name="onrenderfiledata"></a>  COleServerItem::OnRenderFileData

Lo llama el marco de trabajo para recuperar los datos en el formato especificado cuando el medio de almacenamiento es un archivo.

```
virtual BOOL OnRenderFileData(
    LPFORMATETC lpFormatEtc,
    CFile* pFile);
```

### <a name="parameters"></a>Parámetros

*lpFormatEtc*<br/>
Apunta a la [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) estructura que especifica el formato en el que se solicita información.

*pFile*<br/>
Apunta a un `CFile` objeto en el que se va a representar los datos.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

El formato especificado es una colocado anteriormente en el `COleDataSource` objeto utilizando el [DelayRenderData](../../mfc/reference/coledatasource-class.md#delayrenderdata) función miembro para la representación aplazada. La implementación predeterminada de esta función simplemente devuelve FALSE.

Esto es un avanzado que se puede invalidar. Reemplace esta función para proporcionar los datos en el formato solicitado y medio. Dependiendo de los datos, puede reemplazar una de las otras versiones de esta función en su lugar. Si desea controlar varios medios de almacenamiento, reemplace [OnRenderData](#onrenderdata). Si los datos están en un archivo o es de tamaño variable, invalidar [OnRenderFileData](#onrenderfiledata).

Para obtener más información, consulte [IDataObject:: GetData](/windows/desktop/api/objidl/nf-objidl-idataobject-getdata) y [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) en el SDK de Windows.

##  <a name="onrenderglobaldata"></a>  COleServerItem::OnRenderGlobalData

Lo llama el marco de trabajo para recuperar datos en el formato especificado cuando el medio de almacenamiento especificada es una memoria global.

```
virtual BOOL OnRenderGlobalData(
    LPFORMATETC lpFormatEtc,
    HGLOBAL* phGlobal);
```

### <a name="parameters"></a>Parámetros

*lpFormatEtc*<br/>
Apunta a la [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) estructura que especifica el formato en el que se solicita información.

*phGlobal*<br/>
Apunta a un identificador de la memoria global en el que los datos son va a devolver. Si no se ha asignado ninguna memoria, este parámetro puede ser NULL.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

El formato especificado es una colocado anteriormente en el `COleDataSource` objeto utilizando el [DelayRenderData](../../mfc/reference/coledatasource-class.md#delayrenderdata) función miembro para la representación aplazada. La implementación predeterminada de esta función simplemente devuelve FALSE.

Si *phGlobal* es NULL, entonces debe asignado y devueltos en un nuevo HGLOBAL *phGlobal*. En caso contrario, el HGLOBAL especificado por *phGlobal* debe rellenarse con los datos. La cantidad de datos colocados en HGLOBAL no puede superar el tamaño actual del bloque de memoria. Además, el bloque no se puede reasignar a un tamaño mayor.

Esto es un avanzado que se puede invalidar. Reemplace esta función para proporcionar los datos en el formato solicitado y medio. Dependiendo de los datos, puede reemplazar una de las otras versiones de esta función en su lugar. Si desea controlar varios medios de almacenamiento, reemplace [OnRenderData](#onrenderdata). Si los datos están en un archivo o es de tamaño variable, invalidar [OnRenderFileData](#onrenderfiledata).

Para obtener más información, consulte [IDataObject:: GetData](/windows/desktop/api/objidl/nf-objidl-idataobject-getdata) y [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) en el SDK de Windows.

##  <a name="onsetcolorscheme"></a>  COleServerItem::OnSetColorScheme

Lo llama el marco de trabajo para especificar una paleta de colores que se utilizará al editar el elemento OLE.

```
virtual BOOL OnSetColorScheme(const LOGPALETTE* lpLogPalette);
```

### <a name="parameters"></a>Parámetros

*lpLogPalette*<br/>
Puntero a un Windows [LOGPALETTE](/windows/desktop/api/wingdi/ns-wingdi-taglogpalette) estructura.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se usa la paleta de colores; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Si la aplicación contenedora se escribió utilizando la biblioteca Microsoft Foundation Class, esta función se llama cuando el [IOleObject::SetColorScheme](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-setcolorscheme) función de los correspondientes `COleClientItem` se denomina objeto. La implementación predeterminada devuelve FALSE. Reemplace esta función si desea utilizar la paleta recomendada. La aplicación de servidor no es necesario utilizar la paleta sugerida.

Para obtener más información, consulte [IOleObject::SetColorScheme](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-setcolorscheme) en el SDK de Windows.

##  <a name="onsetdata"></a>  COleServerItem::OnSetData

Lo llama el marco de trabajo para reemplazar los datos del elemento OLE con los datos especificados.

```
virtual BOOL OnSetData(
    LPFORMATETC lpFormatEtc,
    LPSTGMEDIUM lpStgMedium,
    BOOL bRelease);
```

### <a name="parameters"></a>Parámetros

*lpFormatEtc*<br/>
Puntero a un [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) estructura que especifica el formato de los datos.

*lpStgMedium*<br/>
Puntero a un [STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium) estructura donde residen los datos.

*bRelease*<br/>
Indica que posee el medio de almacenamiento después de completar la llamada de función. El llamador decide quién es responsable de liberar los recursos asignados en nombre del medio de almacenamiento. El llamador para ello, establezca *bRelease*. Si *bRelease* es distinto de cero, el elemento del servidor toma la propiedad, liberar el medio cuando haya terminado de usarlo. Cuando *bRelease* es 0, el llamador conserva la propiedad y el elemento del servidor puede utilizar el medio de almacenamiento solo para la duración de la llamada.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

El elemento del servidor no tomar posesión de los datos hasta que obtuvo correctamente. Es decir, no tomar posesión si devuelve 0. Si el origen de datos toma posesión, libera el medio de almacenamiento mediante una llamada a la [ReleaseStgMedium](/windows/desktop/api/ole2/nf-ole2-releasestgmedium) función.

La implementación predeterminada no hace nada. Reemplace esta función para reemplazar los datos del elemento OLE con los datos especificados. Esto es un avanzado que se puede invalidar.

Para obtener más información, consulte [STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium), [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc), y [ReleaseStgMedium](/windows/desktop/api/ole2/nf-ole2-releasestgmedium) en el SDK de Windows.

##  <a name="onsetextent"></a>  COleServerItem::OnSetExtent

Lo llama el marco de trabajo para indicar que el elemento OLE cuánto espacio está disponible en él en el documento contenedor.

```
virtual BOOL OnSetExtent(
    DVASPECT nDrawAspect,
    const CSize& size);
```

### <a name="parameters"></a>Parámetros

*nDrawAspect*<br/>
Especifica el aspecto del elemento OLE cuyos límites se especifican. Este parámetro puede tener cualquiera de los siguientes valores:

- Elemento DVASPECT_CONTENT se representa de manera que puede mostrarse como un objeto incrustado dentro de su contenedor.

- DVASPECT_THUMBNAIL se representa en una representación de "miniatura" para que se puede mostrar en una herramienta de exploración.

- Elemento DVASPECT_ICON se representa mediante un icono.

- Elemento DVASPECT_DOCPRINT se representa como si se imprimiera utilizando el comando de impresión en el menú archivo.

*size*<br/>
Un [CSize](../../atl-mfc-shared/reference/csize-class.md) estructura que especifica el nuevo tamaño del elemento OLE.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Si se escribió la aplicación de contenedor con la biblioteca Microsoft Foundation Class, esta función se llama cuando el [SetExtent](../../mfc/reference/coleclientitem-class.md#setextent) función miembro de la correspondiente `COleClientItem` se denomina objeto. La implementación predeterminada configura el [m_sizeExtent](#m_sizeextent) miembro al tamaño especificado si *nDrawAspect* es DVASPECT_CONTENT; en caso contrario, devuelve 0. Reemplace esta función para realizar un procesamiento especial cuando se cambia el tamaño del elemento.

##  <a name="onshow"></a>  COleServerItem::OnShow

Lo llama el marco de trabajo para indicar a la aplicación de servidor para mostrar el elemento OLE en su lugar.

```
virtual void OnShow();
```

### <a name="remarks"></a>Comentarios

Esta función normalmente se llama cuando el usuario de la aplicación de contenedor crea un elemento o ejecuta un verbo, como son editar, que requiere que el elemento que se mostrará. La implementación predeterminada intenta realizar la activación en contexto. Si se produce un error, la función llama a la `OnOpen` la función miembro para mostrar el elemento OLE en una ventana independiente.

Reemplace esta función si desea realizar un procesamiento especial cuando se muestra un elemento OLE.

##  <a name="onupdate"></a>  COleServerItem::OnUpdate

Lo llama el marco de trabajo cuando se ha modificado un elemento.

```
virtual void OnUpdate(
    COleServerItem* pSender,
    LPARAM lHint,
    CObject* pHint,
    DVASPECT nDrawAspect);
```

### <a name="parameters"></a>Parámetros

*pSender*<br/>
Puntero al elemento que se modificó el documento. Puede ser NULL.

*lHint*<br/>
Contiene información sobre la modificación.

*pHint*<br/>
Puntero a un objeto que almacena información sobre la modificación.

*nDrawAspect*<br/>
Un valor de la enumeración DVASPECT. Este parámetro puede tener uno de los siguientes valores:

- Elemento DVASPECT_CONTENT se representa de manera que puede mostrarse como un objeto incrustado dentro de su contenedor.

- DVASPECT_THUMBNAIL se representa en una representación de "miniatura" para que se puede mostrar en una herramienta de exploración.

- Elemento DVASPECT_ICON se representa mediante un icono.

- Elemento DVASPECT_DOCPRINT se representa como si se imprimiera utilizando el comando de impresión en el menú archivo.

### <a name="remarks"></a>Comentarios

La implementación predeterminada llama [NotifyChanged](#notifychanged), independientemente de la sugerencia o remitente.

##  <a name="onupdateitems"></a>  COleServerItem::OnUpdateItems

Lo llama el marco de trabajo para actualizar todos los elementos del documento de servidor.

```
virtual void OnUpdateItems();
```

### <a name="remarks"></a>Comentarios

La implementación predeterminada llama [UpdateLink](../../mfc/reference/coleclientitem-class.md#updatelink) para todos los `COleClientItem` objetos en el documento.

##  <a name="setitemname"></a>  COleServerItem::SetItemName

Llame a esta función cuando se crea un elemento vinculado para establecer su nombre.

```
void SetItemName(LPCTSTR lpszItemName);
```

### <a name="parameters"></a>Parámetros

*lpszItemName*<br/>
Puntero al nuevo nombre del elemento.

### <a name="remarks"></a>Comentarios

El nombre debe ser único dentro del documento. Cuando se llama a una aplicación de servidor para editar un elemento vinculado, la aplicación utiliza este nombre para buscar el elemento. No es necesario llamar a esta función para los elementos incrustados.

## <a name="see-also"></a>Vea también

[Ejemplo HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[CDocItem (clase)](../../mfc/reference/cdocitem-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[COleClientItem (clase)](../../mfc/reference/coleclientitem-class.md)<br/>
[COleServerDoc (clase)](../../mfc/reference/coleserverdoc-class.md)<br/>
[COleTemplateServer (clase)](../../mfc/reference/coletemplateserver-class.md)
