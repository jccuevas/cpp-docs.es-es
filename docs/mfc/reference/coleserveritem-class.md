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
ms.openlocfilehash: dcae304e8571ecb5743002638ea23f13c3e21517
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/06/2019
ms.locfileid: "70741346"
---
# <a name="coleserveritem-class"></a>COleServerItem (clase)

Proporciona la interfaz del servidor a elementos OLE.

## <a name="syntax"></a>Sintaxis

```
class COleServerItem : public CDocItem
```

## <a name="members"></a>Miembros

### <a name="protected-constructors"></a>Constructores protegidos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[COleServerItem::COleServerItem](#coleserveritem)|Construye un objeto `COleServerItem`.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[COleServerItem::AddOtherClipboardData](#addotherclipboarddata)|Coloca los formatos de presentación y conversión `COleDataSource` en un objeto.|
|[COleServerItem::CopyToClipboard](#copytoclipboard)|Copia el elemento en el portapapeles.|
|[COleServerItem::DoDragDrop](#dodragdrop)|Realiza una operación de arrastrar y colocar.|
|[COleServerItem::GetClipboardData](#getclipboarddata)|Obtiene el origen de datos que se va a usar en la transferencia de datos (arrastrar y colocar o portapapeles).|
|[COleServerItem::GetDocument](#getdocument)|Devuelve el documento de servidor que contiene el elemento.|
|[COleServerItem::GetEmbedSourceData](#getembedsourcedata)|Obtiene los datos de CF_EMBEDSOURCE para un elemento OLE.|
|[COleServerItem::GetItemName](#getitemname)|Devuelve el nombre del elemento. Se usa solo para los elementos vinculados.|
|[COleServerItem::GetLinkSourceData](#getlinksourcedata)|Obtiene los datos de CF_LINKSOURCE para un elemento OLE.|
|[COleServerItem::GetObjectDescriptorData](#getobjectdescriptordata)|Obtiene los datos de CF_OBJECTDESCRIPTOR para un elemento OLE.|
|[COleServerItem::IsConnected](#isconnected)|Indica si el elemento está asociado actualmente a un contenedor activo.|
|[COleServerItem::IsLinkedItem](#islinkeditem)|Indica si el elemento representa un elemento OLE vinculado.|
|[COleServerItem::NotifyChanged](#notifychanged)|Actualiza todos los contenedores con actualización automática de vínculos.|
|[COleServerItem::OnDoVerb](#ondoverb)|Se llama para ejecutar un verbo.|
|[COleServerItem::OnDraw](#ondraw)|Se llama cuando el contenedor solicita dibujar el elemento; implementación requerida.|
|[COleServerItem::OnDrawEx](#ondrawex)|Se llama para dibujar elementos especializados.|
|[COleServerItem::OnGetClipboardData](#ongetclipboarddata)|Lo llama el marco de trabajo para obtener los datos que se copiarían en el portapapeles.|
|[COleServerItem::OnGetExtent](#ongetextent)|Lo llama el marco de trabajo para recuperar el tamaño del elemento OLE.|
|[COleServerItem::OnInitFromData](#oninitfromdata)|Lo llama el marco de trabajo para inicializar un elemento OLE utilizando el contenido del objeto de transferencia de datos especificado.|
|[COleServerItem::OnQueryUpdateItems](#onqueryupdateitems)|Se llama para determinar si es necesario actualizar algún elemento vinculado.|
|[COleServerItem::OnRenderData](#onrenderdata)|Recupera los datos como parte de la representación retrasada.|
|[COleServerItem::OnRenderFileData](#onrenderfiledata)|Recupera datos en un objeto `CFile` como parte de la representación retrasada.|
|[COleServerItem::OnRenderGlobalData](#onrenderglobaldata)|Recupera datos en un HGLOBAL como parte de la representación retrasada.|
|[COleServerItem::OnSetColorScheme](#onsetcolorscheme)|Se llama para establecer la combinación de colores del elemento.|
|[COleServerItem::OnSetData](#onsetdata)|Se llama para establecer los datos del elemento.|
|[COleServerItem::OnSetExtent](#onsetextent)|Lo llama el marco de trabajo para establecer el tamaño del elemento OLE.|
|[COleServerItem::OnUpdate](#onupdate)|Se llama cuando cambia alguna parte del documento a la que pertenece el elemento.|
|[COleServerItem::OnUpdateItems](#onupdateitems)|Se llama para actualizar la caché de presentación de todos los elementos del documento del servidor.|
|[COleServerItem::SetItemName](#setitemname)|Establece el nombre del elemento. Se usa solo para los elementos vinculados.|

### <a name="protected-methods"></a>Métodos protegidos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[COleServerItem::GetDataSource](#getdatasource)|Obtiene el objeto que se usa para almacenar los formatos de conversión.|
|[COleServerItem::OnHide](#onhide)|Lo llama el marco de trabajo para ocultar el elemento OLE.|
|[COleServerItem::OnOpen](#onopen)|Lo llama el marco de trabajo para mostrar el elemento OLE en su propia ventana de nivel superior.|
|[COleServerItem::OnShow](#onshow)|Se llama cuando el contenedor solicita mostrar el elemento.|

### <a name="public-data-members"></a>Miembros de datos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[COleServerItem::m_sizeExtent](#m_sizeextent)|Informa al servidor sobre la cantidad del elemento OLE visible.|

## <a name="remarks"></a>Comentarios

Un elemento vinculado puede representar algunos o todos los documentos de servidor. Un elemento incrustado siempre representa un documento de servidor completo.

La `COleServerItem` clase define varias funciones miembro reemplazables a las que llaman las bibliotecas de vínculos dinámicos (dll) del sistema OLE, normalmente en respuesta a las solicitudes de la aplicación contenedora. Estas funciones miembro permiten a la aplicación contenedora manipular el elemento indirectamente de varias maneras, como mostrarlo, ejecutar sus verbos o recuperar sus datos en varios formatos.

Para usar `COleServerItem`, derive una clase a partir de ella e implemente las funciones miembro [OnDraw](#ondraw) y [Serialize](../../mfc/reference/cobject-class.md#serialize) . La `OnDraw` función proporciona la representación de metarchivo de un elemento, lo que permite que se muestre cuando una aplicación contenedora abre un documento compuesto. La `Serialize` función de `CObject` proporciona la representación nativa de un elemento, lo que permite la transferencia de un elemento incrustado entre las aplicaciones de servidor y de contenedor. [OnGetExtent](#ongetextent) proporciona el tamaño natural del elemento al contenedor, lo que permite al contenedor ajustar el tamaño del elemento.

Para obtener más información acerca de los servidores y los temas relacionados [, consulte el artículo servidores: Implementación de un](../../mfc/servers-implementing-a-server.md) servidor y "creación de una aplicación de contenedor/servidor" [en el artículo contenedores: Características](../../mfc/containers-advanced-features.md)avanzadas.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocItem](../../mfc/reference/cdocitem-class.md)

`COleServerItem`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxole. h

##  <a name="addotherclipboarddata"></a>  COleServerItem::AddOtherClipboardData

Llame a esta función para colocar los formatos de conversión y presentación del elemento OLE en el `COleDataSource` objeto especificado.

```
void AddOtherClipboardData(COleDataSource* pDataSource);
```

### <a name="parameters"></a>Parámetros

*pDataSource*<br/>
Puntero al `COleDataSource` objeto en el que se deben colocar los datos.

### <a name="remarks"></a>Comentarios

Debe haber implementado la función miembro [OnDraw](#ondraw) para proporcionar el formato de presentación (imagen de metarchivo) para el elemento. Para admitir otros formatos de conversión, regístrelo con el objeto [COleDataSource](../../mfc/reference/coledatasource-class.md) devuelto por [GetDataSource](#getdatasource) e invalide la función miembro [OnRenderData](#onrenderdata) para proporcionar los datos en los formatos que desea admitir.

##  <a name="coleserveritem"></a>  COleServerItem::COleServerItem

Construye un `COleServerItem` objeto y lo agrega a la colección del documento del servidor de elementos de documento.

```
COleServerItem(
    COleServerDoc* pServerDoc,
    BOOL bAutoDelete);
```

### <a name="parameters"></a>Parámetros

*pServerDoc*<br/>
Puntero al documento que contendrá el nuevo elemento.

*bAutoDelete*<br/>
Marca que indica si el objeto se puede eliminar cuando se libera un vínculo a él. Establézcalo en false si el `COleServerItem` objeto es una parte integral de los datos del documento que debe eliminar. Establézcalo en TRUE si el objeto es una estructura secundaria que se usa para identificar un intervalo en los datos del documento que puede ser eliminado por el marco de trabajo.

##  <a name="copytoclipboard"></a>  COleServerItem::CopyToClipboard

Llame a esta función para copiar el elemento OLE en el portapapeles.

```
void CopyToClipboard(BOOL bIncludeLink = FALSE);
```

### <a name="parameters"></a>Parámetros

*bIncludeLink*<br/>
Establézcalo en TRUE si los datos de los vínculos se deben copiar en el portapapeles. Establézcalo en FALSE si la aplicación de servidor no admite vínculos.

### <a name="remarks"></a>Comentarios

La función utiliza la función miembro [OnGetClipboardData](#ongetclipboarddata) para crear un objeto [COleDataSource](../../mfc/reference/coledatasource-class.md) que contiene los datos del elemento OLE en los formatos admitidos. A continuación, la función `COleDataSource` coloca el objeto en el portapapeles mediante la función [COleDataSource:: SetClipboard](../../mfc/reference/coledatasource-class.md#setclipboard) . El `COleDataSource` objeto incluye los datos nativos del elemento y su representación en formato CF_METAFILEPICT, así como los datos en los formatos de conversión que decida admitir. Debe haber implementado [Serialize](../../mfc/reference/cobject-class.md#serialize) y [OnDraw](#ondraw) para que esta función miembro funcione.

##  <a name="dodragdrop"></a>  COleServerItem::DoDragDrop

Llame a `DoDragDrop` la función miembro para realizar una operación de arrastrar y colocar.

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
Rectángulo del elemento en la pantalla, en píxeles, con respecto al área cliente.

*ptOffset*<br/>
Desplazamiento desde *lpItemRect* donde se encontraba la posición del mouse en el momento de arrastrar.

*bIncludeLink*<br/>
Establézcalo en TRUE si los datos de los vínculos se deben copiar en el portapapeles. Establézcalo en FALSE si la aplicación no admite vínculos.

*dwEffects*<br/>
Determina los efectos que el origen de arrastre permitirá en la operación de arrastre (una combinación de copiar, movimiento y vínculo).

*lpRectStartDrag*<br/>
Puntero al rectángulo que define dónde se inicia realmente la acción de arrastrar. Para obtener más información, vea la sección Comentarios que se muestra más adelante.

### <a name="return-value"></a>Valor devuelto

Un valor de la enumeración DROPEFFECT. Si es DROPEFFECT_MOVE, se deben quitar los datos originales.

### <a name="remarks"></a>Comentarios

La operación de arrastrar y colocar no se inicia inmediatamente. Espera hasta que el cursor del mouse salga del rectángulo especificado por *lpRectStartDrag* o hasta que haya transcurrido un número de milisegundos especificado. Si *lpRectStartDrag* es null, se utiliza un rectángulo predeterminado para que el arrastre se inicie cuando el cursor del mouse se mueva un píxel.

El tiempo de retraso se especifica mediante una configuración de clave del registro. Puede cambiar el tiempo de retraso llamando a [CWinApp:: WriteProfileString](../../mfc/reference/cwinapp-class.md#writeprofilestring) o [CWinApp:: WriteProfileInt](../../mfc/reference/cwinapp-class.md#writeprofileint). Si no especifica el tiempo de retraso, se usa un valor predeterminado de 200 milisegundos. La hora de retraso de arrastre se almacena de la siguiente manera:

- El tiempo de retraso de arrastre de Windows NT se almacena en HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\NT\CurrentVersion\IniFileMapping\win.ini\Windows\DragDelay.

- El tiempo de retraso de arrastre de Windows 3. x se almacena en el archivo WIN. Archivo INI, en la sección [Windows}.

- El tiempo de retraso de arrastre de Windows 95/98 se almacena en una versión almacenada en caché de WIN. INI.

Para obtener más información sobre cómo se almacena la información de retraso de arrastre en el registro o en. Archivo INI, consulte [WriteProfileString](/windows/win32/api/winbase/nf-winbase-writeprofilestringw) en el Windows SDK.

##  <a name="getclipboarddata"></a>  COleServerItem::GetClipboardData

Llame a esta función para rellenar el objeto [COleDataSource](../../mfc/reference/coledatasource-class.md) especificado con todos los datos que se copiarían en el portapapeles si llamó a [CopyToClipboard](#copytoclipboard) (los mismos datos también se transferirían si llamó a [DoDragDrop](#dodragdrop)).

```
void GetClipboardData(
    COleDataSource* pDataSource,
    BOOL bIncludeLink = FALSE,
    LPPOINT lpOffset = NULL,
    LPSIZE lpSize = NULL);
```

### <a name="parameters"></a>Parámetros

*pDataSource*<br/>
Puntero al `COleDataSource` objeto que recibirá los datos del elemento OLE en todos los formatos admitidos.

*bIncludeLink*<br/>
TRUE si los datos de vínculo se deben copiar en el portapapeles. FALSE si la aplicación de servidor no admite vínculos.

*lpOffset*<br/>
Desplazamiento, en píxeles, del cursor del mouse desde el origen del objeto.

*lpSize*<br/>
Tamaño del objeto en píxeles.

### <a name="remarks"></a>Comentarios

Esta función llama a la función miembro [GetEmbedSourceData](#getembedsourcedata) para obtener los datos nativos del elemento OLE y llama a la función miembro [AddOtherClipboardData](#addotherclipboarddata) para obtener el formato de presentación y cualquier formato de conversión compatible. Si *bIncludeLink* es true, la función también llama a [GetLinkSourceData](#getlinksourcedata) para obtener los datos de vínculo del elemento.

Invalide esta función si desea colocar formatos en un `COleDataSource` objeto antes o después de los formatos proporcionados por. `CopyToClipboard`

##  <a name="getdatasource"></a>  COleServerItem::GetDataSource

Llame a esta función para obtener el objeto [COleDataSource](../../mfc/reference/coledatasource-class.md) que se usa para almacenar los formatos de conversión que admite la aplicación de servidor.

```
COleDataSource* GetDataSource();
```

### <a name="return-value"></a>Valor devuelto

Puntero al `COleDataSource` objeto que se usa para almacenar los formatos de conversión.

### <a name="remarks"></a>Comentarios

Si desea que la aplicación de servidor ofrezca datos en diversos formatos durante las operaciones de transferencia de datos, registre esos formatos con `COleDataSource` el objeto devuelto por esta función. Por ejemplo, si desea proporcionar una representación CF_TEXT del elemento OLE para las operaciones de arrastrar y colocar del portapapeles, debe registrar el formato con el `COleDataSource` objeto devuelto por esta función y, a continuación, invalidar la `OnRenderXxxData` función miembro como proporcione los datos.

##  <a name="getdocument"></a>  COleServerItem::GetDocument

Llame a esta función para obtener un puntero al documento que contiene el elemento.

```
COleServerDoc* GetDocument() const;
```

### <a name="return-value"></a>Valor devuelto

Un puntero al documento que contiene el elemento; Es NULL si el elemento no forma parte de un documento.

### <a name="remarks"></a>Comentarios

Esto permite el acceso al documento de servidor que pasó como argumento al `COleServerItem` constructor.

##  <a name="getembedsourcedata"></a>  COleServerItem::GetEmbedSourceData

Llame a esta función para obtener los datos de CF_EMBEDSOURCE para un elemento OLE.

```
void GetEmbedSourceData(LPSTGMEDIUM lpStgMedium);
```

### <a name="parameters"></a>Parámetros

*lpStgMedium*<br/>
Puntero a la estructura [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) que recibirá los datos de CF_EMBEDSOURCE para el elemento OLE.

### <a name="remarks"></a>Comentarios

Este formato incluye los datos nativos del elemento. Debe haber implementado la `Serialize` función miembro para que esta función funcione correctamente.

Después, el resultado se puede Agregar a un origen de datos mediante [COleDataSource:: CacheData](../../mfc/reference/coledatasource-class.md#cachedata). [COleServerItem:: OnGetClipboardData](#ongetclipboarddata)llama automáticamente a esta función.

Para obtener más información, consulte [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) en el Windows SDK.

##  <a name="getitemname"></a>  COleServerItem::GetItemName

Llame a esta función para obtener el nombre del elemento.

```
const CString& GetItemName() const;
```

### <a name="return-value"></a>Valor devuelto

Nombre del elemento.

### <a name="remarks"></a>Comentarios

Normalmente, solo se llama a esta función para los elementos vinculados.

##  <a name="getlinksourcedata"></a>  COleServerItem::GetLinkSourceData

Llame a esta función para obtener los datos de CF_LINKSOURCE para un elemento OLE.

```
BOOL GetLinkSourceData(LPSTGMEDIUM lpStgMedium);
```

### <a name="parameters"></a>Parámetros

*lpStgMedium*<br/>
Puntero a la estructura [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) que recibirá los datos de CF_LINKSOURCE para el elemento OLE.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Este formato incluye el CLSID que describe el tipo del elemento OLE y la información necesaria para buscar el documento que contiene el elemento OLE.

Después, el resultado se puede Agregar a un origen de datos con [COleDataSource:: CacheData](../../mfc/reference/coledatasource-class.md#cachedata). [OnGetClipboardData](#ongetclipboarddata)llama automáticamente a esta función.

Para obtener más información, consulte [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) en el Windows SDK.

##  <a name="getobjectdescriptordata"></a>  COleServerItem::GetObjectDescriptorData

Llame a esta función para obtener los datos de CF_OBJECTDESCRIPTOR para un elemento OLE.

```
void GetObjectDescriptorData(
    LPPOINT lpOffset,
    LPSIZE lpSize,
    LPSTGMEDIUM lpStgMedium);
```

### <a name="parameters"></a>Parámetros

*lpOffset*<br/>
Desplazamiento del clic del mouse en la esquina superior izquierda del elemento OLE. Puede ser NULL.

*lpSize*<br/>
Tamaño del elemento OLE. Puede ser NULL.

*lpStgMedium*<br/>
Puntero a la estructura [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) que recibirá los datos de CF_OBJECTDESCRIPTOR para el elemento OLE.

### <a name="remarks"></a>Comentarios

La información se copia en la `STGMEDIUM` estructura a la que apunta *lpStgMedium*. Este formato incluye la información necesaria para el cuadro de diálogo Pegar especial.

Para obtener más información, consulte [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) en el Windows SDK.

##  <a name="isconnected"></a>  COleServerItem::IsConnected

Llame a esta función para ver si el elemento OLE está conectado.

```
BOOL IsConnected() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el elemento está conectado; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Un elemento OLE se considera conectado si uno o varios contenedores tienen referencias al elemento. Un elemento se conecta si su recuento de referencias es mayor que 0 o si es un elemento incrustado.

##  <a name="islinkeditem"></a>  COleServerItem::IsLinkedItem

Llame a esta función para ver si el elemento OLE es un elemento vinculado.

```
BOOL IsLinkedItem() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el elemento es un elemento vinculado; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Un elemento se vincula si el elemento es válido y no se devuelve en la lista de elementos incrustados del documento. Un elemento vinculado puede o no estar conectado a un contenedor.

Es habitual utilizar la misma clase para los elementos vinculados y los incrustados. `IsLinkedItem`permite que los elementos vinculados se comporten de manera diferente a los elementos incrustados, aunque muchas veces el código es común.

##  <a name="m_sizeextent"></a>  COleServerItem::m_sizeExtent

Este miembro indica al servidor qué parte del objeto está visible en el documento contenedor.

```
CSize m_sizeExtent;
```

### <a name="remarks"></a>Comentarios

La implementación predeterminada de [OnSetExtent](#onsetextent) establece este miembro.

##  <a name="notifychanged"></a>  COleServerItem::NotifyChanged

Llame a esta función después de que se haya cambiado el elemento vinculado.

```
void NotifyChanged(DVASPECT nDrawAspect = DVASPECT_CONTENT);
```

### <a name="parameters"></a>Parámetros

*nDrawAspect*<br/>
Un valor de la enumeración DVASPECT que indica qué aspecto del elemento OLE ha cambiado. Este parámetro puede tener cualquiera de los siguientes valores:

- El elemento DVASPECT_CONTENT se representa de tal forma que se puede mostrar como un objeto incrustado dentro de su contenedor.

- El elemento DVASPECT_THUMBNAIL se representa en una representación "en miniatura" para que se pueda mostrar en una herramienta de exploración.

- El elemento DVASPECT_ICON se representa mediante un icono.

- El elemento DVASPECT_DOCPRINT se representa como si se imprimiera con el comando imprimir del menú archivo.

### <a name="remarks"></a>Comentarios

Si un elemento contenedor está vinculado al documento con un vínculo automático, el elemento se actualiza para reflejar los cambios. En las aplicaciones contenedoras escritas con el biblioteca MFC, se llama a [COleClientItem:: onchange](../../mfc/reference/coleclientitem-class.md#onchange) en respuesta.

##  <a name="ondoverb"></a>  COleServerItem::OnDoVerb

Lo llama el marco de trabajo para ejecutar el verbo especificado.

```
virtual void OnDoVerb(LONG iVerb);
```

### <a name="parameters"></a>Parámetros

*iVerb*<br/>
Especifica el verbo que se va a ejecutar. Puede ser cualquiera de los siguientes:

|Valor|Significado|Símbolo|
|-----------|-------------|------------|
|0|verbo principal|OLEIVERB_PRIMARY|
|1|Verbo secundario|(Ninguno)|
|- 1|Mostrar elemento para editar|OLEIVERB_SHOW|
|- 2|Editar elemento en una ventana independiente|OLEIVERB_OPEN|
|- 3|Ocultar elemento|OLEIVERB_HIDE|

El valor-1 suele ser un alias de otro verbo. Si no se admite la edición abierta,-2 tiene el mismo efecto que-1. Para obtener más valores, vea [IOleObject::D overb](/windows/win32/api/oleidl/nf-oleidl-ioleobject-doverb) en el Windows SDK.

### <a name="remarks"></a>Comentarios

Si la aplicación contenedora se escribió con el biblioteca MFC, se llama a esta función cuando se llama a la función miembro [COleClientItem:: Activate](../../mfc/reference/coleclientitem-class.md#activate) del objeto correspondiente `COleClientItem` . La implementación predeterminada llama a la función miembro [Show](#onshow) si se especifica el verbo principal o OLEIVERB_SHOW, [OnOpen](#onopen) si se especifica el verbo secundario o OLEIVERB_OPEN, y [Hide](#onhide) si se especifica OLEIVERB_HIDE. La implementación predeterminada llama `OnShow` a si *iVerb* no es uno de los verbos enumerados anteriormente.

Invalide esta función si el verbo principal no muestra el elemento. Por ejemplo, si el elemento es una grabación de sonido y su verbo principal es reproducir, no tendría que mostrar la aplicación de servidor para reproducir el elemento.

Para obtener más información, vea [IOleObject::D overb](/windows/win32/api/oleidl/nf-oleidl-ioleobject-doverb) en el Windows SDK.

##  <a name="ondraw"></a>  COleServerItem::OnDraw

Lo llama el marco de trabajo para representar el elemento OLE en un metarchivo.

```
virtual BOOL OnDraw(
    CDC* pDC,
    CSize& rSize) = 0;
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
Puntero al objeto [CDC](../../mfc/reference/cdc-class.md) en el que se va a dibujar el elemento. El contexto de presentación se conecta automáticamente al contexto de presentación de atributos para que pueda llamar a las funciones de atributo, aunque esto haría que el metarchivo fuera específico del dispositivo.

*rSize*<br/>
Tamaño, en unidades de HIMETRIC, en el que se va a dibujar el metarchivo.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el elemento se dibujó correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

La representación de metarchivo del elemento OLE se usa para mostrar el elemento en la aplicación contenedora. Si la aplicación contenedora se escribió con el biblioteca MFC, la función miembro [Draw](../../mfc/reference/coleclientitem-class.md#draw) del objeto [COleClientItem](../../mfc/reference/coleclientitem-class.md) correspondiente utiliza el metarchivo. No hay ninguna implementación predeterminada. Debe reemplazar esta función para dibujar el elemento en el contexto de dispositivo especificado.

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
Puntero al objeto [CDC](../../mfc/reference/cdc-class.md) en el que se va a dibujar el elemento. El controlador de dominio se conecta automáticamente al controlador de dominio para que pueda llamar a las funciones de atributo, aunque esto haría que el metarchivo fuera específico del dispositivo.

*nDrawAspect*<br/>
Un valor de la enumeración DVASPECT. Este parámetro puede tener cualquiera de los siguientes valores:

- El elemento DVASPECT_CONTENT se representa de tal forma que se puede mostrar como un objeto incrustado dentro de su contenedor.

- El elemento DVASPECT_THUMBNAIL se representa en una representación "en miniatura" para que se pueda mostrar en una herramienta de exploración.

- El elemento DVASPECT_ICON se representa mediante un icono.

- El elemento DVASPECT_DOCPRINT se representa como si se imprimiera con el comando imprimir del menú archivo.

*rSize*<br/>
Tamaño del elemento en unidades de HIMETRIC.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el elemento se dibujó correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

La implementación predeterminada llama `OnDraw` a cuando DVASPECT es igual a DVASPECT_CONTENT; de lo contrario, se produce un error.

Invalide esta función para proporcionar datos de presentación para aspectos distintos de DVASPECT_CONTENT, como DVASPECT_ICON o DVASPECT_THUMBNAIL.

##  <a name="ongetclipboarddata"></a>  COleServerItem::OnGetClipboardData

Lo llama el marco de trabajo para `COleDataSource` obtener un objeto que contiene todos los datos que se colocarían en el portapapeles mediante una llamada a la función miembro [CopyToClipboard](#copytoclipboard) .

```
virtual COleDataSource* OnGetClipboardData(
    BOOL bIncludeLink,
    LPPOINT lpOffset,
    LPSIZE lpSize);
```

### <a name="parameters"></a>Parámetros

*bIncludeLink*<br/>
Establézcalo en TRUE si los datos de los vínculos se deben copiar en el portapapeles. Establézcalo en FALSE si la aplicación de servidor no admite vínculos.

*lpOffset*<br/>
Desplazamiento del cursor del mouse desde el origen del objeto en píxeles.

*lpSize*<br/>
Tamaño del objeto en píxeles.

### <a name="return-value"></a>Valor devuelto

Un puntero a un objeto [COleDataSource](../../mfc/reference/coledatasource-class.md) que contiene los datos del portapapeles.

### <a name="remarks"></a>Comentarios

La implementación predeterminada de esta función llama a [GetClipboardData](#getclipboarddata).

##  <a name="ongetextent"></a>  COleServerItem::OnGetExtent

Lo llama el marco de trabajo para recuperar el tamaño, en unidades de HIMETRIC, del elemento OLE.

```
virtual BOOL OnGetExtent(
    DVASPECT nDrawAspect,
    CSize& rSize);
```

### <a name="parameters"></a>Parámetros

*nDrawAspect*<br/>
Especifica el aspecto del elemento OLE cuyos límites se van a recuperar. Este parámetro puede tener cualquiera de los siguientes valores:

- El elemento DVASPECT_CONTENT se representa de tal forma que se puede mostrar como un objeto incrustado dentro de su contenedor.

- El elemento DVASPECT_THUMBNAIL se representa en una representación "en miniatura" para que se pueda mostrar en una herramienta de exploración.

- El elemento DVASPECT_ICON se representa mediante un icono.

- El elemento DVASPECT_DOCPRINT se representa como si se imprimiera con el comando imprimir del menú archivo.

*rSize*<br/>
Referencia a un `CSize` objeto que recibirá el tamaño del elemento OLE.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Si la aplicación contenedora se escribió con el biblioteca MFC, se llama a esta función cuando se llama a la función miembro [GetExtent](../../mfc/reference/coleclientitem-class.md#getextent) del objeto `COleClientItem` correspondiente. La implementación predeterminada no hace nada. Debe implementarla usted mismo. Invalide esta función si desea realizar un procesamiento especial al controlar una solicitud para el tamaño del elemento OLE.

##  <a name="onhide"></a>  COleServerItem::OnHide

Lo llama el marco de trabajo para ocultar el elemento OLE.

```
virtual void OnHide();
```

### <a name="remarks"></a>Comentarios

Llamadas `COleServerDoc::OnShowDocument( FALSE )`predeterminadas. La función también notifica al contenedor que se ha ocultado el elemento OLE. Invalide esta función si desea realizar un procesamiento especial al ocultar un elemento OLE.

##  <a name="oninitfromdata"></a>  COleServerItem::OnInitFromData

Lo llama el marco de trabajo para inicializar un elemento OLE utilizando el contenido de *pDataObject*.

```
virtual BOOL OnInitFromData(
    COleDataObject* pDataObject,
    BOOL bCreation);
```

### <a name="parameters"></a>Parámetros

*pDataObject*<br/>
Puntero a un objeto de datos OLE que contiene datos en varios formatos para inicializar el elemento OLE.

*bCreation*<br/>
TRUE si se llama a la función para inicializar un elemento OLE recién creado por una aplicación contenedora. FALSE si se llama a la función para reemplazar el contenido de un elemento OLE ya existente.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Si *bCreation* es true, se llama a esta función si un contenedor implementa Insert New Object basado en la selección actual. Los datos seleccionados se utilizan al crear el nuevo elemento OLE. Por ejemplo, al seleccionar un rango de celdas en un programa de hoja de cálculo y, a continuación, usar insertar nuevo objeto para crear un gráfico basado en los valores del intervalo seleccionado. La implementación predeterminada no hace nada. Invalide esta función para elegir un formato aceptable de los proporcionados por *pDataObject* e inicializar el elemento OLE en función de los datos proporcionados. Se trata de un reemplazable avanzado.

Para obtener más información, vea [IOleObject:: InitFromData](/windows/win32/api/oleidl/nf-oleidl-ioleobject-initfromdata) en el Windows SDK.

##  <a name="onopen"></a>  COleServerItem::OnOpen

Lo llama el marco de trabajo para mostrar el elemento OLE en una instancia independiente de la aplicación de servidor, en lugar de en su lugar.

```
virtual void OnOpen();
```

### <a name="remarks"></a>Comentarios

La implementación predeterminada activa la primera ventana de marco que muestra el documento que contiene el elemento OLE. Si la aplicación es un servidor pequeño, la implementación predeterminada muestra la ventana principal. La función también notifica al contenedor que se ha abierto el elemento OLE.

Invalide esta función si desea realizar un procesamiento especial al abrir un elemento OLE. Esto es especialmente común con los elementos vinculados en los que desea establecer la selección en el vínculo cuando se abre.

Para obtener más información, vea [IOleClientSite:: OnShowWindow](/windows/win32/api/oleidl/nf-oleidl-ioleclientsite-onshowwindow) en el Windows SDK.

##  <a name="onqueryupdateitems"></a>  COleServerItem::OnQueryUpdateItems

Lo llama el marco de trabajo para determinar si alguno de los elementos vinculados en el documento del servidor actual no está actualizado.

```
virtual BOOL OnQueryUpdateItems();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el documento tiene elementos que necesitan actualizaciones; 0 si todos los elementos están actualizados.

### <a name="remarks"></a>Comentarios

Un elemento no está actualizado si su documento de origen ha cambiado, pero el elemento vinculado no se ha actualizado para reflejar los cambios en el documento.

##  <a name="onrenderdata"></a>  COleServerItem::OnRenderData

Lo llama el marco de trabajo para recuperar los datos en el formato especificado.

```
virtual BOOL OnRenderData(
    LPFORMATETC lpFormatEtc,
    LPSTGMEDIUM lpStgMedium);
```

### <a name="parameters"></a>Parámetros

*lpFormatEtc*<br/>
Apunta a la estructura [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) especificando el formato en el que se solicita información.

*lpStgMedium*<br/>
Apunta a una estructura [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) en la que se van a devolver los datos.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

El formato especificado es el que se colocó previamente `COleDataSource` en el objeto mediante la función miembro [DelayRenderData](../../mfc/reference/coledatasource-class.md#delayrenderdata) o [DelayRenderFileData](../../mfc/reference/coledatasource-class.md#delayrenderfiledata) para la representación diferida. La implementación predeterminada de esta función llama a [OnRenderFileData](#onrenderfiledata) o [OnRenderGlobalData](#onrenderglobaldata), respectivamente, si el medio de almacenamiento proporcionado es un archivo o una memoria. Si no se proporciona ninguno de estos formatos, la implementación predeterminada devuelve 0 y no hace nada.

Si *lpStgMedium*-> *tymed* es TYMED_NULL, se debe asignar y rellenar el STGMEDIUM según lo especificado por *lpFormatEtc-> tymed*. Si no se TYMED_NULL, se debe rellenar el STGMEDIUM con los datos.

Se trata de un reemplazable avanzado. Invalide esta función para proporcionar los datos en el formato y medio solicitados. En función de los datos, puede que desee reemplazar una de las otras versiones de esta función en su lugar. Si los datos son pequeños y tienen un tamaño fijo, `OnRenderGlobalData`invalide. Si los datos están en un archivo o tiene un tamaño variable, invalide `OnRenderFileData`.

Para obtener más información, vea [IDataObject:: GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata), [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1), [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)y [TYMED](/windows/win32/api/objidl/ne-objidl-tymed) en el Windows SDK.

##  <a name="onrenderfiledata"></a>  COleServerItem::OnRenderFileData

Lo llama el marco de trabajo para recuperar los datos en el formato especificado cuando el medio de almacenamiento es un archivo.

```
virtual BOOL OnRenderFileData(
    LPFORMATETC lpFormatEtc,
    CFile* pFile);
```

### <a name="parameters"></a>Parámetros

*lpFormatEtc*<br/>
Apunta a la estructura [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) especificando el formato en el que se solicita información.

*pFile*<br/>
Señala a un `CFile` objeto en el que se van a representar los datos.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

El formato especificado es el que se colocó previamente `COleDataSource` en el objeto mediante la función miembro [DelayRenderData](../../mfc/reference/coledatasource-class.md#delayrenderdata) para la representación diferida. La implementación predeterminada de esta función simplemente devuelve FALSE.

Se trata de un reemplazable avanzado. Invalide esta función para proporcionar los datos en el formato y medio solicitados. En función de los datos, es posible que desee invalidar una de las otras versiones de esta función en su lugar. Si desea administrar varios medios de almacenamiento, invalide [OnRenderData](#onrenderdata). Si los datos están en un archivo o tiene un tamaño variable, invalide [OnRenderFileData](#onrenderfiledata).

Para obtener más información, vea [IDataObject:: GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata) y [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) en el Windows SDK.

##  <a name="onrenderglobaldata"></a>  COleServerItem::OnRenderGlobalData

Lo llama el marco de trabajo para recuperar los datos en el formato especificado cuando el medio de almacenamiento especificado es una memoria global.

```
virtual BOOL OnRenderGlobalData(
    LPFORMATETC lpFormatEtc,
    HGLOBAL* phGlobal);
```

### <a name="parameters"></a>Parámetros

*lpFormatEtc*<br/>
Apunta a la estructura [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) especificando el formato en el que se solicita información.

*phGlobal*<br/>
Apunta a un identificador de la memoria global en la que se van a devolver los datos. Si no se ha asignado ninguna memoria, este parámetro puede ser NULL.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

El formato especificado es el que se colocó previamente `COleDataSource` en el objeto mediante la función miembro [DelayRenderData](../../mfc/reference/coledatasource-class.md#delayrenderdata) para la representación diferida. La implementación predeterminada de esta función simplemente devuelve FALSE.

Si *phGlobal* es null, se debe asignar y devolver un nuevo hglobal en *phGlobal*. De lo contrario, el HGLOBAL especificado por *phGlobal* se debe rellenar con los datos. La cantidad de datos que se colocan en el HGLOBAL no debe superar el tamaño actual del bloque de memoria. Además, el bloque no se puede reasignar a un tamaño mayor.

Se trata de un reemplazable avanzado. Invalide esta función para proporcionar los datos en el formato y medio solicitados. En función de los datos, puede que desee reemplazar una de las otras versiones de esta función en su lugar. Si desea administrar varios medios de almacenamiento, invalide [OnRenderData](#onrenderdata). Si los datos están en un archivo o tiene un tamaño variable, invalide [OnRenderFileData](#onrenderfiledata).

Para obtener más información, vea [IDataObject:: GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata) y [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) en el Windows SDK.

##  <a name="onsetcolorscheme"></a>  COleServerItem::OnSetColorScheme

Lo llama el marco de trabajo para especificar la paleta de colores que se va a utilizar al editar el elemento OLE.

```
virtual BOOL OnSetColorScheme(const LOGPALETTE* lpLogPalette);
```

### <a name="parameters"></a>Parámetros

*lpLogPalette*<br/>
Puntero a una estructura [LOGPALETTE](/windows/win32/api/wingdi/ns-wingdi-logpalette) de Windows.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se utiliza la paleta de colores; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Si la aplicación contenedora se escribió con el biblioteca MFC, se llama a esta función cuando se llama a la función [IOleObject:: SetColorScheme](/windows/win32/api/oleidl/nf-oleidl-ioleobject-setcolorscheme) del objeto correspondiente `COleClientItem` . La implementación predeterminada devuelve FALSE. Reemplace esta función si desea utilizar la paleta recomendada. No es necesario que la aplicación de servidor use la paleta sugerida.

Para obtener más información, vea [IOleObject:: SetColorScheme](/windows/win32/api/oleidl/nf-oleidl-ioleobject-setcolorscheme) en el Windows SDK.

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
Puntero a una estructura [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) que especifica el formato de los datos.

*lpStgMedium*<br/>
Puntero a una estructura [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) en la que residen los datos.

*bRelease*<br/>
Indica quién tiene la propiedad del medio de almacenamiento después de completar la llamada de función. El autor de la llamada decide quién es responsable de liberar los recursos asignados en nombre del medio de almacenamiento. Para ello, el autor de la llamada establece *bRelease*. Si *bRelease* es distinto de cero, el elemento de servidor toma la propiedad, liberando el medio cuando ha terminado de usarlo. Cuando *bRelease* es 0, el llamador conserva la propiedad y el elemento de servidor puede usar el medio de almacenamiento solo mientras dure la llamada.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

El elemento de servidor no toma la propiedad de los datos hasta que se obtiene correctamente. Es decir, no toma la propiedad si devuelve 0. Si el origen de datos toma posesión, libera el medio de almacenamiento mediante una llamada a la función [ReleaseStgMedium](/windows/win32/api/ole2/nf-ole2-releasestgmedium) .

La implementación predeterminada no hace nada. Invalide esta función para reemplazar los datos del elemento OLE por los datos especificados. Se trata de un reemplazable avanzado.

Para obtener más información, consulte [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1), [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)y [ReleaseStgMedium](/windows/win32/api/ole2/nf-ole2-releasestgmedium) en el Windows SDK.

##  <a name="onsetextent"></a>  COleServerItem::OnSetExtent

Lo llama el marco de trabajo para indicar al elemento OLE cuánto espacio está disponible en el documento contenedor.

```
virtual BOOL OnSetExtent(
    DVASPECT nDrawAspect,
    const CSize& size);
```

### <a name="parameters"></a>Parámetros

*nDrawAspect*<br/>
Especifica el aspecto del elemento OLE cuyos límites se especifican. Este parámetro puede tener cualquiera de los siguientes valores:

- El elemento DVASPECT_CONTENT se representa de tal forma que se puede mostrar como un objeto incrustado dentro de su contenedor.

- El elemento DVASPECT_THUMBNAIL se representa en una representación "en miniatura" para que se pueda mostrar en una herramienta de exploración.

- El elemento DVASPECT_ICON se representa mediante un icono.

- El elemento DVASPECT_DOCPRINT se representa como si se imprimiera con el comando imprimir del menú archivo.

*size*<br/>
Estructura [CSize](../../atl-mfc-shared/reference/csize-class.md) que especifica el nuevo tamaño del elemento OLE.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Si la aplicación contenedora se escribió con el biblioteca MFC, se llama a esta función cuando se llama a la función miembro [SetExtent](../../mfc/reference/coleclientitem-class.md#setextent) del objeto `COleClientItem` correspondiente. La implementación predeterminada establece el miembro [m_sizeExtent](#m_sizeextent) en el tamaño especificado si *nDrawAspect* es DVASPECT_CONTENT; en caso contrario, devuelve 0. Invalide esta función para realizar un procesamiento especial al cambiar el tamaño del elemento.

##  <a name="onshow"></a>  COleServerItem::OnShow

Lo llama el marco de trabajo para indicar a la aplicación de servidor que muestre el elemento OLE en contexto.

```
virtual void OnShow();
```

### <a name="remarks"></a>Comentarios

Normalmente, se llama a esta función cuando el usuario de la aplicación contenedora crea un elemento o ejecuta un verbo, como Edit, que requiere que se muestre el elemento. La implementación predeterminada intenta realizar la activación en contexto. Si se produce un error, la función `OnOpen` llama a la función miembro para mostrar el elemento OLE en una ventana independiente.

Invalide esta función si desea realizar un procesamiento especial cuando se muestre un elemento OLE.

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
Puntero al elemento que modificó el documento. Puede ser NULL.

*lHint*<br/>
Contiene información sobre la modificación.

*pHint*<br/>
Puntero a un objeto que almacena información sobre la modificación.

*nDrawAspect*<br/>
Un valor de la enumeración DVASPECT. Este parámetro puede tener cualquiera de los siguientes valores:

- El elemento DVASPECT_CONTENT se representa de tal forma que se puede mostrar como un objeto incrustado dentro de su contenedor.

- El elemento DVASPECT_THUMBNAIL se representa en una representación "en miniatura" para que se pueda mostrar en una herramienta de exploración.

- El elemento DVASPECT_ICON se representa mediante un icono.

- El elemento DVASPECT_DOCPRINT se representa como si se imprimiera con el comando imprimir del menú archivo.

### <a name="remarks"></a>Comentarios

La implementación predeterminada llama a [NotifyChanged](#notifychanged), independientemente de la sugerencia o del remitente.

##  <a name="onupdateitems"></a>  COleServerItem::OnUpdateItems

Lo llama el marco de trabajo para actualizar todos los elementos del documento del servidor.

```
virtual void OnUpdateItems();
```

### <a name="remarks"></a>Comentarios

La implementación predeterminada llama a [UpdateLink](../../mfc/reference/coleclientitem-class.md#updatelink) para `COleClientItem` todos los objetos del documento.

##  <a name="setitemname"></a>  COleServerItem::SetItemName

Llame a esta función cuando cree un elemento vinculado para establecer su nombre.

```
void SetItemName(LPCTSTR lpszItemName);
```

### <a name="parameters"></a>Parámetros

*lpszItemName*<br/>
Puntero al nuevo nombre del elemento.

### <a name="remarks"></a>Comentarios

El nombre debe ser único dentro del documento. Cuando se llama a una aplicación de servidor para editar un elemento vinculado, la aplicación usa este nombre para buscar el elemento. No es necesario llamar a esta función para los elementos incrustados.

## <a name="see-also"></a>Vea también

[Ejemplo de MFC HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[CDocItem (clase)](../../mfc/reference/cdocitem-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[COleClientItem (clase)](../../mfc/reference/coleclientitem-class.md)<br/>
[COleServerDoc (clase)](../../mfc/reference/coleserverdoc-class.md)<br/>
[COleTemplateServer (clase)](../../mfc/reference/coletemplateserver-class.md)
