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
ms.openlocfilehash: bdb91168a7c0ae718ca7d7514448b55965186aa8
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753743"
---
# <a name="coleserveritem-class"></a>COleServerItem (clase)

Proporciona la interfaz del servidor a elementos OLE.

## <a name="syntax"></a>Sintaxis

```
class COleServerItem : public CDocItem
```

## <a name="members"></a>Miembros

### <a name="protected-constructors"></a>Constructores protegidos

|Nombre|Descripción|
|----------|-----------------|
|[COleServerItem::COleServerItem](#coleserveritem)|Construye un objeto `COleServerItem`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[COleServerItem::AddOtherClipboardData](#addotherclipboarddata)|Coloca los formatos `COleDataSource` de presentación y conversión en un objeto.|
|[COleServerItem::CopyToClipboard](#copytoclipboard)|Copia el elemento en el Portapapeles.|
|[COleServerItem::DoDragDrop](#dodragdrop)|Realiza una operación de arrastrar y colocar.|
|[COleServerItem::GetClipboardData](#getclipboarddata)|Obtiene el origen de datos para su uso en la transferencia de datos (arrastrar y colocar o Portapapeles).|
|[COleServerItem::GetDocument](#getdocument)|Devuelve el documento de servidor que contiene el elemento.|
|[COleServerItem::GetEmbedSourceData](#getembedsourcedata)|Obtiene los datos CF_EMBEDSOURCE de un elemento OLE.|
|[COleServerItem::GetItemName](#getitemname)|Devuelve el nombre del elemento. Se utiliza solo para elementos vinculados.|
|[COleServerItem::GetLinkSourceData](#getlinksourcedata)|Obtiene los datos CF_LINKSOURCE de un elemento OLE.|
|[COleServerItem::GetObjectDescriptorData](#getobjectdescriptordata)|Obtiene los datos CF_OBJECTDESCRIPTOR de un elemento OLE.|
|[COleServerItem::IsConnected](#isconnected)|Indica si el elemento está asociado actualmente a un contenedor activo.|
|[COleServerItem::IsLinkedItem](#islinkeditem)|Indica si el elemento representa un elemento OLE vinculado.|
|[COleServerItem::NotifyChanged](#notifychanged)|Actualiza todos los contenedores con actualización automática de vínculos.|
|[COleServerItem::OnDoVerb](#ondoverb)|Se llama para ejecutar un verbo.|
|[COleServerItem::OnDraw](#ondraw)|Se llama cuando el contenedor solicita dibujar el elemento; aplicación requerida.|
|[COleServerItem::OnDrawEx](#ondrawex)|Se llama para el dibujo de elementos especializados.|
|[COleServerItem::OnGetClipboardData](#ongetclipboarddata)|Llamado por el marco de trabajo para obtener los datos que se copiarían en el Portapapeles.|
|[COleServerItem::OnGetExtent](#ongetextent)|Llamado por el marco de trabajo para recuperar el tamaño del elemento OLE.|
|[COleServerItem::OnInitFromData](#oninitfromdata)|Llamado por el marco de trabajo para inicializar un elemento OLE mediante el contenido del objeto de transferencia de datos especificado.|
|[COleServerItem::OnQueryUpdateItems](#onqueryupdateitems)|Se llama para determinar si los elementos vinculados requieren actualización.|
|[COleServerItem::OnRenderData](#onrenderdata)|Recupera datos como parte de la representación retrasada.|
|[COleServerItem::OnRenderFileData](#onrenderfiledata)|Recupera datos en `CFile` un objeto como parte de la representación retrasada.|
|[COleServerItem::OnRenderGlobalData](#onrenderglobaldata)|Recupera datos en un HGLOBAL como parte de la representación retrasada.|
|[COleServerItem::OnSetColorScheme](#onsetcolorscheme)|Se llama para establecer el esquema de color del elemento.|
|[COleServerItem::OnSetData](#onsetdata)|Se llama para establecer los datos del elemento.|
|[COleServerItem::OnSetExtent](#onsetextent)|Llamado por el marco de trabajo para establecer el tamaño del elemento OLE.|
|[COleServerItem::OnUpdate](#onupdate)|Se llama cuando se cambia alguna parte del documento al que pertenece el elemento.|
|[COleServerItem::OnUpdateItems](#onupdateitems)|Se llama para actualizar la caché de presentación de todos los elementos del documento del servidor.|
|[COleServerItem::SetItemName](#setitemname)|Establece el nombre del elemento. Se utiliza solo para elementos vinculados.|

### <a name="protected-methods"></a>Métodos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[COleServerItem::GetDataSource](#getdatasource)|Obtiene el objeto utilizado para almacenar formatos de conversión.|
|[COleServerItem::OnHide](#onhide)|Llamado por el marco de trabajo para ocultar el elemento OLE.|
|[COleServerItem::OnOpen](#onopen)|Llamado por el marco de trabajo para mostrar el elemento OLE en su propia ventana de nivel superior.|
|[COleServerItem::OnShow](#onshow)|Se llama cuando el contenedor solicita mostrar el elemento.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[COleServerItem::m_sizeExtent](#m_sizeextent)|Informa al servidor sobre la cantidad de elemento OLE visible.|

## <a name="remarks"></a>Observaciones

Un elemento vinculado puede representar parte o la totalidad de un documento de servidor. Un elemento incrustado siempre representa un documento de servidor completo.

La `COleServerItem` clase define varias funciones miembro reemplazables a las que llaman las bibliotecas de vínculos dinámicos (DLL) del sistema OLE, normalmente en respuesta a las solicitudes de la aplicación contenedora. Estas funciones miembro permiten a la aplicación contenedora manipular el elemento indirectamente de varias maneras, por ejemplo, mostrándolo, ejecutando sus verbos o recuperando sus datos en varios formatos.

Para `COleServerItem`usar , derive una clase de ella e implemente las funciones miembro [OnDraw](#ondraw) y [Serialize.](../../mfc/reference/cobject-class.md#serialize) La `OnDraw` función proporciona la representación de metarchivo de un elemento, lo que permite que se muestre cuando una aplicación contenedora abre un documento compuesto. La `Serialize` función de `CObject` proporciona la representación nativa de un elemento, lo que permite transferir un elemento incrustado entre el servidor y las aplicaciones contenedoras. [OnGetExtent](#ongetextent) proporciona el tamaño natural del elemento al contenedor, lo que permite al contenedor el tamaño del elemento.

Para obtener más información acerca de los servidores y temas relacionados, vea el artículo [Servidores: implementar un servidor](../../mfc/servers-implementing-a-server.md) y "Creación de una aplicación de contenedor/servidor" en el artículo [Contenedores: características avanzadas](../../mfc/containers-advanced-features.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocItem](../../mfc/reference/cdocitem-class.md)

`COleServerItem`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxole.h

## <a name="coleserveritemaddotherclipboarddata"></a><a name="addotherclipboarddata"></a>COleServerItem::AddOtherClipboardData

Llame a esta función para colocar los formatos `COleDataSource` de presentación y conversión para el elemento OLE en el objeto especificado.

```cpp
void AddOtherClipboardData(COleDataSource* pDataSource);
```

### <a name="parameters"></a>Parámetros

*pDataSource*<br/>
Puntero al `COleDataSource` objeto en el que se deben colocar los datos.

### <a name="remarks"></a>Observaciones

Debe haber implementado el [OnDraw](#ondraw) función miembro para proporcionar el formato de presentación (una imagen de metarchivo) para el elemento. Para admitir otros formatos de conversión, regístrelos mediante el [COleDataSource](../../mfc/reference/coledatasource-class.md) objeto devuelto por [GetDataSource](#getdatasource) e invalidar el [OnRenderData](#onrenderdata) función miembro para proporcionar datos en los formatos que desea admitir.

## <a name="coleserveritemcoleserveritem"></a><a name="coleserveritem"></a>COleServerItem::COleServerItem

Construye un `COleServerItem` objeto y lo agrega a la colección de elementos de documento del documento de servidor.

```
COleServerItem(
    COleServerDoc* pServerDoc,
    BOOL bAutoDelete);
```

### <a name="parameters"></a>Parámetros

*pServerDoc*<br/>
Puntero al documento que contendrá el nuevo elemento.

*bAutoDelete*<br/>
Marcador que indica si el objeto se puede eliminar cuando se libera un vínculo a él. Establezca esta opción `COleServerItem` en FALSE si el objeto es una parte integral de los datos del documento que debe eliminar. Establezca este valor en TRUE si el objeto es una estructura secundaria que se usa para identificar un intervalo en los datos del documento que puede eliminar el marco de trabajo.

## <a name="coleserveritemcopytoclipboard"></a><a name="copytoclipboard"></a>COleServerItem::CopyToClipboard

Llame a esta función para copiar el elemento OLE en el Portapapeles.

```cpp
void CopyToClipboard(BOOL bIncludeLink = FALSE);
```

### <a name="parameters"></a>Parámetros

*bIncludeLink*<br/>
Establezca esta configuración en TRUE si los datos de vínculo se deben copiar en el Portapapeles. Establezca esta configuración en FALSE si la aplicación de servidor no admite vínculos.

### <a name="remarks"></a>Observaciones

La función utiliza el [OnGetClipboardData](#ongetclipboarddata) función miembro para crear un [COleDataSource](../../mfc/reference/coledatasource-class.md) objeto que contiene los datos del elemento OLE en los formatos admitidos. A continuación, `COleDataSource` la función coloca el objeto en el Portapapeles mediante la función [COleDataSource::SetClipboard](../../mfc/reference/coledatasource-class.md#setclipboard) . El `COleDataSource` objeto incluye los datos nativos del elemento y su representación en formato CF_METAFILEPICT, así como datos en cualquier formato de conversión que elija admitir. Debe haber implementado [Serialize](../../mfc/reference/cobject-class.md#serialize) y [OnDraw](#ondraw) para que esta función miembro funcione.

## <a name="coleserveritemdodragdrop"></a><a name="dodragdrop"></a>COleServerItem::DoDragDrop

Llame `DoDragDrop` a la función miembro para realizar una operación de arrastrar y colocar.

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
Rectángulo del elemento en la pantalla, en píxeles, en relación con el área de cliente.

*ptOffset*<br/>
Desplazamiento de *lpItemRect* donde estaba la posición del mouse en el momento del arrastre.

*bIncludeLink*<br/>
Establezca esta configuración en TRUE si los datos de vínculo se deben copiar en el Portapapeles. Establézcalo en FALSE si la aplicación no admite vínculos.

*dwEffects*<br/>
Determina los efectos que el origen de arrastre permitirá en la operación de arrastre (una combinación de Copiar, Mover y Vincular).

*lpRectStartDrag*<br/>
Puntero al rectángulo que define dónde comienza realmente el arrastre. Para obtener más información, vea la sección Comentarios que se muestra más adelante.

### <a name="return-value"></a>Valor devuelto

Valor de la enumeración DROPEFFECT. Si se DROPEFFECT_MOVE, se deben eliminar los datos originales.

### <a name="remarks"></a>Observaciones

La operación de arrastrar y colocar no se inicia inmediatamente. Espera hasta que el cursor del mouse deja el rectángulo especificado por *lpRectStartDrag* o hasta que haya pasado un número especificado de milisegundos. Si *lpRectStartDrag* es NULL, se utiliza un rectángulo predeterminado para que el arrastre se inicia cuando el cursor del mouse mueve un píxel.

El tiempo de retardo se especifica mediante una configuración de clave del Registro. Puede cambiar la hora de retardo llamando a [CWinApp::WriteProfileString](../../mfc/reference/cwinapp-class.md#writeprofilestring) o [CWinApp::WriteProfileInt](../../mfc/reference/cwinapp-class.md#writeprofileint). Si no especifica el tiempo de retardo, se utiliza un valor predeterminado de 200 milisegundos. El tiempo de retardo de arrastre se almacena de la siguiente manera:

- El tiempo de retardo de arrastre de Windows NT se almacena en HKEY_LOCAL_MACHINE,SOFTWARE, Microsoft, Windows, NT, CurrentVersion, IniFileMapping, win.ini, Windows y DragDelay.

- Windows 3.x El tiempo de retardo de arrastre se almacena en el WIN. INI, en la sección [Windows.

- Windows 95/98 El tiempo de retardo de arrastre se almacena en una versión almacenada en caché de WIN. Ini.

Para obtener más información sobre cómo se almacena la información de retardo de arrastre en el registro o en el archivo . INI, vea [WriteProfileString](/windows/win32/api/winbase/nf-winbase-writeprofilestringw) en el Windows SDK.

## <a name="coleserveritemgetclipboarddata"></a><a name="getclipboarddata"></a>COleServerItem::GetClipboardData

Llame a esta función para rellenar el objeto [COleDataSource](../../mfc/reference/coledatasource-class.md) especificado con todos los datos que se copiarían en el Portapapeles si llamara a [CopyToClipboard](#copytoclipboard) (los mismos datos también se transferirían si llamara a [DoDragDrop](#dodragdrop)).

```cpp
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
TRUESi los datos de vínculo deben copiarse en el Portapapeles. FALSE si la aplicación de servidor no admite vínculos.

*lpOffset*<br/>
Desplazamiento, en píxeles, del cursor del ratón desde el origen del objeto.

*lpSize*<br/>
El tamaño del objeto en píxeles.

### <a name="remarks"></a>Observaciones

Esta función llama a la [GetEmbedSourceData](#getembedsourcedata) función miembro para obtener los datos nativos para el elemento OLE y llama a la [AddOtherClipboardData](#addotherclipboarddata) función miembro para obtener el formato de presentación y los formatos de conversión admitidos. Si *bIncludeLink* es TRUE, la función también llama a [GetLinkSourceData](#getlinksourcedata) para obtener los datos de vínculo para el elemento.

Reemplace esta función si desea `COleDataSource` colocar formatos en un `CopyToClipboard`objeto antes o después de los formatos proporcionados por .

## <a name="coleserveritemgetdatasource"></a><a name="getdatasource"></a>COleServerItem::GetDataSource

Llame a esta función para obtener el [COleDataSource](../../mfc/reference/coledatasource-class.md) objeto utilizado para almacenar los formatos de conversión que admite la aplicación de servidor.

```
COleDataSource* GetDataSource();
```

### <a name="return-value"></a>Valor devuelto

Puntero al `COleDataSource` objeto utilizado para almacenar los formatos de conversión.

### <a name="remarks"></a>Observaciones

Si desea que la aplicación de servidor ofrezca datos en una variedad `COleDataSource` de formatos durante las operaciones de transferencia de datos, registre esos formatos con el objeto devuelto por esta función. Por ejemplo, si desea proporcionar una representación CF_TEXT del elemento OLE para las operaciones Portapapeles o arrastrar y colocar, debe registrar el formato con el `COleDataSource` objeto que devuelve esta función y, a continuación, invalidar la `OnRenderXxxData` función miembro para proporcionar los datos.

## <a name="coleserveritemgetdocument"></a><a name="getdocument"></a>COleServerItem::GetDocument

Llame a esta función para obtener un puntero al documento que contiene el elemento.

```
COleServerDoc* GetDocument() const;
```

### <a name="return-value"></a>Valor devuelto

Un puntero al documento que contiene el elemento; NULL si el elemento no forma parte de un documento.

### <a name="remarks"></a>Observaciones

Esto permite el acceso al documento de servidor `COleServerItem` que pasó como argumento al constructor.

## <a name="coleserveritemgetembedsourcedata"></a><a name="getembedsourcedata"></a>COleServerItem::GetEmbedSourceData

Llame a esta función para obtener los datos CF_EMBEDSOURCE de un elemento OLE.

```cpp
void GetEmbedSourceData(LPSTGMEDIUM lpStgMedium);
```

### <a name="parameters"></a>Parámetros

*lpStgMedium*<br/>
Puntero a la [Estructura STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) que recibirá los datos CF_EMBEDSOURCE para el elemento OLE.

### <a name="remarks"></a>Observaciones

Este formato incluye los datos nativos del elemento. Debe haber implementado `Serialize` la función miembro para que esta función funcione correctamente.

A continuación, el resultado se puede agregar a un origen de datos mediante [COleDataSource::CacheData](../../mfc/reference/coledatasource-class.md#cachedata). [COleServerItem::OnGetClipboardData](#ongetclipboarddata)llama automáticamente a esta función.

Para obtener más información, consulte [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) en el Windows SDK.

## <a name="coleserveritemgetitemname"></a><a name="getitemname"></a>COleServerItem::GetItemName

Llame a esta función para obtener el nombre del elemento.

```
const CString& GetItemName() const;
```

### <a name="return-value"></a>Valor devuelto

El nombre del elemento.

### <a name="remarks"></a>Observaciones

Normalmente, se llama a esta función solo para los elementos vinculados.

## <a name="coleserveritemgetlinksourcedata"></a><a name="getlinksourcedata"></a>COleServerItem::GetLinkSourceData

Llame a esta función para obtener los datos CF_LINKSOURCE de un elemento OLE.

```
BOOL GetLinkSourceData(LPSTGMEDIUM lpStgMedium);
```

### <a name="parameters"></a>Parámetros

*lpStgMedium*<br/>
Puntero a la [Estructura STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) que recibirá los datos CF_LINKSOURCE para el elemento OLE.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Este formato incluye el CLSID que describe el tipo del elemento OLE y la información necesaria para buscar el documento que contiene el elemento OLE.

A continuación, el resultado se puede agregar a un origen de datos con [COleDataSource::CacheData](../../mfc/reference/coledatasource-class.md#cachedata). [OnGetClipboardData](#ongetclipboarddata)llama automáticamente a esta función.

Para obtener más información, consulte [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) en el Windows SDK.

## <a name="coleserveritemgetobjectdescriptordata"></a><a name="getobjectdescriptordata"></a>COleServerItem::GetObjectDescriptorData

Llame a esta función para obtener los datos CF_OBJECTDESCRIPTOR de un elemento OLE.

```cpp
void GetObjectDescriptorData(
    LPPOINT lpOffset,
    LPSIZE lpSize,
    LPSTGMEDIUM lpStgMedium);
```

### <a name="parameters"></a>Parámetros

*lpOffset*<br/>
Desplazamiento del clic del mouse desde la esquina superior izquierda del elemento OLE. Puede ser NULL.

*lpSize*<br/>
Tamaño del elemento OLE. Puede ser NULL.

*lpStgMedium*<br/>
Puntero a la [Estructura STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) que recibirá los datos CF_OBJECTDESCRIPTOR para el elemento OLE.

### <a name="remarks"></a>Observaciones

La información se copia `STGMEDIUM` en la estructura señalada por *lpStgMedium*. Este formato incluye la información necesaria para el cuadro de diálogo Pegado especial.

Para obtener más información, consulte [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) en el Windows SDK.

## <a name="coleserveritemisconnected"></a><a name="isconnected"></a>COleServerItem::IsConnected

Llame a esta función para ver si el elemento OLE está conectado.

```
BOOL IsConnected() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el elemento está conectado; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Un elemento OLE se considera conectado si uno o varios contenedores tienen referencias al elemento. Un elemento está conectado si su recuento de referencias es mayor que 0 o si es un elemento incrustado.

## <a name="coleserveritemislinkeditem"></a><a name="islinkeditem"></a>COleServerItem::IsLinkedItem

Llame a esta función para ver si el elemento OLE es un elemento vinculado.

```
BOOL IsLinkedItem() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el elemento es un elemento vinculado; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Un elemento está vinculado si el elemento es válido y no se devuelve en la lista de elementos incrustados del documento. Un elemento vinculado puede o no estar conectado a un contenedor.

Es común usar la misma clase para elementos vinculados e incrustados. `IsLinkedItem`permite hacer que los elementos vinculados se comporten de forma diferente que los elementos incrustados, aunque muchas veces el código es común.

## <a name="coleserveritemm_sizeextent"></a><a name="m_sizeextent"></a>COleServerItem::m_sizeExtent

Este miembro indica al servidor cuánto del objeto está visible en el documento contenedor.

```
CSize m_sizeExtent;
```

### <a name="remarks"></a>Observaciones

La implementación predeterminada de [OnSetExtent](#onsetextent) establece este miembro.

## <a name="coleserveritemnotifychanged"></a><a name="notifychanged"></a>COleServerItem::NotifyChanged

Llame a esta función después de cambiar el elemento vinculado.

```cpp
void NotifyChanged(DVASPECT nDrawAspect = DVASPECT_CONTENT);
```

### <a name="parameters"></a>Parámetros

*nDrawAspect*<br/>
Valor de la enumeración DVASPECT que indica qué aspecto del elemento OLE ha cambiado. Este parámetro puede tener cualquiera de los siguientes valores:

- DVASPECT_CONTENT Item se representa de tal manera que se puede mostrar como un objeto incrustado dentro de su contenedor.

- DVASPECT_THUMBNAIL elemento se representa en una representación "en miniatura" para que se pueda mostrar en una herramienta de exploración.

- DVASPECT_ICON elemento se representa mediante un icono.

- DVASPECT_DOCPRINT Elemento se representa como si se imprimiera mediante el comando Imprimir del menú Archivo.

### <a name="remarks"></a>Observaciones

Si un elemento contenedor está vinculado al documento con un vínculo automático, el elemento se actualiza para reflejar los cambios. En las aplicaciones contenedoras escritas con la biblioteca Microsoft Foundation Class, [COleClientItem::OnChange](../../mfc/reference/coleclientitem-class.md#onchange) se llama en respuesta.

## <a name="coleserveritemondoverb"></a><a name="ondoverb"></a>COleServerItem::OnDoVerb

Llamado por el marco de trabajo para ejecutar el verbo especificado.

```
virtual void OnDoVerb(LONG iVerb);
```

### <a name="parameters"></a>Parámetros

*iVerb*<br/>
Especifica el verbo que se va a ejecutar. Puede ser cualquiera de los siguientes:

|Value|Significado|Símbolo|
|-----------|-------------|------------|
|0|verbo principal|OLEIVERB_PRIMARY|
|1|Verbo secundario|(Ninguna)|
|- 1|Mostrar elemento para editar|OLEIVERB_SHOW|
|- 2|Editar elemento en una ventana separada|OLEIVERB_OPEN|
|- 3|Ocultar artículo|OLEIVERB_HIDE|

El valor -1 suele ser un alias para otro verbo. Si no se admite la edición abierta, -2 tiene el mismo efecto que -1. Para obtener valores adicionales, vea [IOleObject::DoVerb](/windows/win32/api/oleidl/nf-oleidl-ioleobject-doverb) en el Windows SDK.

### <a name="remarks"></a>Observaciones

Si la aplicación contenedora se escribió con la biblioteca Microsoft Foundation Class, se llama `COleClientItem` a esta función cuando se llama a la función miembro [COleClientItem::Activate](../../mfc/reference/coleclientitem-class.md#activate) del objeto correspondiente. La implementación predeterminada llama a la [OnShow](#onshow) función miembro si se especifica el verbo principal o OLEIVERB_SHOW, [OnOpen](#onopen) si se especifica el verbo secundario o OLEIVERB_OPEN y [OnHide](#onhide) si se especifica OLEIVERB_HIDE. La implementación `OnShow` predeterminada llama si *iVerb* no es uno de los verbos enumerados anteriormente.

Reemplace esta función si el verbo principal no muestra el elemento. Por ejemplo, si el elemento es una grabación de sonido y su verbo principal es Reproducir, no tendría que mostrar la aplicación de servidor para reproducir el elemento.

Para obtener más información, vea [IOleObject::DoVerb](/windows/win32/api/oleidl/nf-oleidl-ioleobject-doverb) en el Windows SDK.

## <a name="coleserveritemondraw"></a><a name="ondraw"></a>COleServerItem::OnDraw

Llamado por el marco de trabajo para representar el elemento OLE en un metarchivo.

```
virtual BOOL OnDraw(
    CDC* pDC,
    CSize& rSize) = 0;
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
Puntero al objeto [CDC](../../mfc/reference/cdc-class.md) en el que se va a dibujar el elemento. El contexto de visualización se conecta automáticamente al contexto de visualización de atributos para que pueda llamar a funciones de atributo, aunque al hacerlo sería específico del dispositivo del metarchivo.

*rSize*<br/>
Tamaño, en unidades HIMETRIC, en el que se dibujará el metarchivo.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el elemento se ha dibujado correctamente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

La representación de metarchivo del elemento OLE se utiliza para mostrar el elemento en la aplicación contenedora. Si la aplicación contenedora se escribió con la biblioteca Microsoft Foundation Class, el metarchivo se utiliza la [Draw](../../mfc/reference/coleclientitem-class.md#draw) función miembro de la [correspondiente COleClientItem](../../mfc/reference/coleclientitem-class.md) objeto. No hay ninguna implementación predeterminada. Debe invalidar esta función para dibujar el elemento en el contexto de dispositivo especificado.

## <a name="coleserveritemondrawex"></a><a name="ondrawex"></a>COleServerItem::OnDrawEx

Llamado por el marco de trabajo para todo el dibujo.

```
virtual BOOL OnDrawEx(
    CDC* pDC,
    DVASPECT nDrawAspect,
    CSize& rSize);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
Puntero al objeto [CDC](../../mfc/reference/cdc-class.md) en el que se va a dibujar el elemento. El controlador de dominio se conecta automáticamente al controlador de dominio de atributo para que pueda llamar a funciones de atributo, aunque al hacerlo haría que el dispositivo de metarchivo sea específico.

*nDrawAspect*<br/>
Valor de la enumeración DVASPECT. Este parámetro puede tener cualquiera de los siguientes valores:

- DVASPECT_CONTENT Item se representa de tal manera que se puede mostrar como un objeto incrustado dentro de su contenedor.

- DVASPECT_THUMBNAIL elemento se representa en una representación "en miniatura" para que se pueda mostrar en una herramienta de exploración.

- DVASPECT_ICON elemento se representa mediante un icono.

- DVASPECT_DOCPRINT Elemento se representa como si se imprimiera mediante el comando Imprimir del menú Archivo.

*rSize*<br/>
Tamaño del artículo en unidades HIMETRIC.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el elemento se ha dibujado correctamente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

La implementación `OnDraw` predeterminada llama cuando DVASPECT es igual a DVASPECT_CONTENT; de lo contrario falla.

Reemplace esta función para proporcionar datos de presentación para aspectos distintos de DVASPECT_CONTENT, como DVASPECT_ICON o DVASPECT_THUMBNAIL.

## <a name="coleserveritemongetclipboarddata"></a><a name="ongetclipboarddata"></a>COleServerItem::OnGetClipboardData

Llamado por el marco `COleDataSource` de trabajo para obtener un objeto que contiene todos los datos que se colocarían en el Portapapeles mediante una llamada a la [CopyToClipboard](#copytoclipboard) función miembro.

```
virtual COleDataSource* OnGetClipboardData(
    BOOL bIncludeLink,
    LPPOINT lpOffset,
    LPSIZE lpSize);
```

### <a name="parameters"></a>Parámetros

*bIncludeLink*<br/>
Establezca esta configuración en TRUE si los datos de vínculo se deben copiar en el Portapapeles. Establezca esta configuración en FALSE si la aplicación de servidor no admite vínculos.

*lpOffset*<br/>
Desplazamiento del cursor del ratón desde el origen del objeto en píxeles.

*lpSize*<br/>
El tamaño del objeto en píxeles.

### <a name="return-value"></a>Valor devuelto

Un puntero a un [COleDataSource](../../mfc/reference/coledatasource-class.md) objeto que contiene el Portapapeles datos.

### <a name="remarks"></a>Observaciones

La implementación predeterminada de esta función llama a [GetClipboardData](#getclipboarddata).

## <a name="coleserveritemongetextent"></a><a name="ongetextent"></a>COleServerItem::OnGetExtent

Llamado por el marco de trabajo para recuperar el tamaño, en unidades HIMETRIC, del elemento OLE.

```
virtual BOOL OnGetExtent(
    DVASPECT nDrawAspect,
    CSize& rSize);
```

### <a name="parameters"></a>Parámetros

*nDrawAspect*<br/>
Especifica el aspecto del elemento OLE cuyos límites se van a recuperar. Este parámetro puede tener cualquiera de los siguientes valores:

- DVASPECT_CONTENT Item se representa de tal manera que se puede mostrar como un objeto incrustado dentro de su contenedor.

- DVASPECT_THUMBNAIL elemento se representa en una representación "en miniatura" para que se pueda mostrar en una herramienta de exploración.

- DVASPECT_ICON elemento se representa mediante un icono.

- DVASPECT_DOCPRINT Elemento se representa como si se imprimiera mediante el comando Imprimir del menú Archivo.

*rSize*<br/>
Referencia a `CSize` un objeto que recibirá el tamaño del elemento OLE.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Si la aplicación contenedora se escribió con la biblioteca Microsoft Foundation Class, `COleClientItem` se llama a esta función cuando se llama a la función miembro [GetExtent](../../mfc/reference/coleclientitem-class.md#getextent) del objeto correspondiente. La implementación predeterminada no hace nada. Debe implementarlo usted mismo. Invalide esta función si desea realizar un procesamiento especial al controlar una solicitud para el tamaño del elemento OLE.

## <a name="coleserveritemonhide"></a><a name="onhide"></a>COleServerItem::OnHide

Llamado por el marco de trabajo para ocultar el elemento OLE.

```
virtual void OnHide();
```

### <a name="remarks"></a>Observaciones

El valor `COleServerDoc::OnShowDocument( FALSE )`predeterminado llama . La función también notifica al contenedor que el elemento OLE se ha ocultado. Invalide esta función si desea realizar un procesamiento especial al ocultar un elemento OLE.

## <a name="coleserveritemoninitfromdata"></a><a name="oninitfromdata"></a>COleServerItem::OnInitFromData

Llamado por el marco de trabajo para inicializar un elemento OLE utilizando el contenido de *pDataObject*.

```
virtual BOOL OnInitFromData(
    COleDataObject* pDataObject,
    BOOL bCreation);
```

### <a name="parameters"></a>Parámetros

*pDataObject*<br/>
Puntero a un objeto de datos OLE que contiene datos en varios formatos para inicializar el elemento OLE.

*bCreación*<br/>
TRUESi se llama a la función para inicializar un elemento OLE que se crea recientemente por una aplicación contenedora. FALSE si se llama a la función para reemplazar el contenido de un elemento OLE ya existente.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Si *bCreation* es TRUE, se llama a esta función si un contenedor implementa Insertar nuevo objeto en función de la selección actual. Los datos seleccionados se utilizan al crear el nuevo elemento OLE. Por ejemplo, al seleccionar un rango de celdas en un programa de hoja de cálculo y, a continuación, utilizar Insertar nuevo objeto para crear un gráfico basado en los valores del rango seleccionado. La implementación predeterminada no hace nada. Invalide esta función para elegir un formato aceptable de los ofrecidos por *pDataObject* e inicializar el elemento OLE en función de los datos proporcionados. Este es un avanzado reemplazable.

Para obtener más información, vea [IOleObject::InitFromData](/windows/win32/api/oleidl/nf-oleidl-ioleobject-initfromdata) en el Windows SDK.

## <a name="coleserveritemonopen"></a><a name="onopen"></a>COleServerItem::OnOpen

Llamado por el marco de trabajo para mostrar el elemento OLE en una instancia independiente de la aplicación de servidor, en lugar de en su lugar.

```
virtual void OnOpen();
```

### <a name="remarks"></a>Observaciones

La implementación predeterminada activa la primera ventana de marco que muestra el documento que contiene el elemento OLE; si la aplicación es un miniservidor, la implementación predeterminada muestra la ventana principal. La función también notifica al contenedor que se ha abierto el elemento OLE.

Reemplace esta función si desea realizar un procesamiento especial al abrir un elemento OLE. Esto es especialmente común con los elementos vinculados en los que desea establecer la selección en el vínculo cuando se abre.

Para obtener más información, vea [IOleClientSite::OnShowWindow](/windows/win32/api/oleidl/nf-oleidl-ioleclientsite-onshowwindow) en el Windows SDK.

## <a name="coleserveritemonqueryupdateitems"></a><a name="onqueryupdateitems"></a>COleServerItem::OnQueryUpdateItems

Llamado por el marco de trabajo para determinar si los elementos vinculados en el documento de servidor actual están desactualizados.

```
virtual BOOL OnQueryUpdateItems();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el documento tiene elementos que necesitan actualizaciones; 0 si todos los artículos están actualizados.

### <a name="remarks"></a>Observaciones

Un elemento está desactualizado si se ha cambiado su documento de origen, pero el elemento vinculado no se ha actualizado para reflejar los cambios en el documento.

## <a name="coleserveritemonrenderdata"></a><a name="onrenderdata"></a>COleServerItem::OnRenderData

Llamado por el marco de trabajo para recuperar datos en el formato especificado.

```
virtual BOOL OnRenderData(
    LPFORMATETC lpFormatEtc,
    LPSTGMEDIUM lpStgMedium);
```

### <a name="parameters"></a>Parámetros

*lpFormatEtc*<br/>
Señala a la estructura [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) especificando el formato en el que se solicita la información.

*lpStgMedium*<br/>
Apunta a una estructura [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) en la que se van a devolver los datos.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

El formato especificado es uno `COleDataSource` colocado previamente en el objeto mediante el [DelayRenderData](../../mfc/reference/coledatasource-class.md#delayrenderdata) o [DelayRenderFileData](../../mfc/reference/coledatasource-class.md#delayrenderfiledata) función miembro para la representación retrasada. La implementación predeterminada de esta función llama a [OnRenderFileData](#onrenderfiledata) o [OnRenderGlobalData](#onrenderglobaldata), respectivamente, si el medio de almacenamiento proporcionado es un archivo o memoria. Si no se proporciona ninguno de estos formatos, la implementación predeterminada devuelve 0 y no hace nada.

Si *lpStgMedium*-> *tymed* está TYMED_NULL, el STGMEDIUM debe asignar y rellenar según lo especificado por *lpFormatEtc->tymed*. Si no TYMED_NULL, el STGMEDIUM debe rellenarse con los datos.

Este es un avanzado reemplazable. Reemplace esta función para proporcionar los datos en el formato y medio solicitados. Dependiendo de los datos, es posible que desee invalidar una de las otras versiones de esta función en su lugar. Si los datos son pequeños `OnRenderGlobalData`y de tamaño fijo, invalide . Si los datos están en un archivo o `OnRenderFileData`tienen un tamaño variable, invalide .

Para obtener más información, vea [IDataObject::GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata), [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1), [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)y [TYMED](/windows/win32/api/objidl/ne-objidl-tymed) en el Windows SDK.

## <a name="coleserveritemonrenderfiledata"></a><a name="onrenderfiledata"></a>COleServerItem::OnRenderFileData

Llamado por el marco de trabajo para recuperar datos en el formato especificado cuando el medio de almacenamiento es un archivo.

```
virtual BOOL OnRenderFileData(
    LPFORMATETC lpFormatEtc,
    CFile* pFile);
```

### <a name="parameters"></a>Parámetros

*lpFormatEtc*<br/>
Señala a la estructura [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) especificando el formato en el que se solicita la información.

*pFile*<br/>
Apunta a `CFile` un objeto en el que se van a representar los datos.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

El formato especificado es uno `COleDataSource` colocado previamente en el objeto mediante el [DelayRenderData](../../mfc/reference/coledatasource-class.md#delayrenderdata) función miembro para la representación retrasada. La implementación predeterminada de esta función simplemente devuelve FALSE.

Este es un avanzado reemplazable. Reemplace esta función para proporcionar los datos en el formato y medio solicitados. Dependiendo de los datos, es posible que desee invalidar una de las otras versiones de esta función en su lugar. Si desea controlar varios medios de almacenamiento, reemplace [OnRenderData](#onrenderdata). Si los datos están en un archivo o son de tamaño variable, reemplace [OnRenderFileData](#onrenderfiledata).

Para obtener más información, vea [IDataObject::GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata) y [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) en el Windows SDK.

## <a name="coleserveritemonrenderglobaldata"></a><a name="onrenderglobaldata"></a>COleServerItem::OnRenderGlobalData

Llamado por el marco de trabajo para recuperar datos en el formato especificado cuando el medio de almacenamiento especificado es memoria global.

```
virtual BOOL OnRenderGlobalData(
    LPFORMATETC lpFormatEtc,
    HGLOBAL* phGlobal);
```

### <a name="parameters"></a>Parámetros

*lpFormatEtc*<br/>
Señala a la estructura [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) especificando el formato en el que se solicita la información.

*phGlobal*<br/>
Apunta a un identificador de memoria global en la que se van a devolver los datos. Si no se ha asignado ninguna memoria, este parámetro puede ser NULL.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

El formato especificado es uno `COleDataSource` colocado previamente en el objeto mediante el [DelayRenderData](../../mfc/reference/coledatasource-class.md#delayrenderdata) función miembro para la representación retrasada. La implementación predeterminada de esta función simplemente devuelve FALSE.

Si *phGlobal* es NULL, se debe asignar y devolver un nuevo HGLOBAL en *phGlobal*. De lo contrario, el HGLOBAL especificado por *phGlobal* debe rellenarse con los datos. La cantidad de datos colocados en el HGLOBAL no debe exceder el tamaño actual del bloque de memoria. Además, el bloque no se puede reasignar a un tamaño mayor.

Este es un avanzado reemplazable. Reemplace esta función para proporcionar los datos en el formato y medio solicitados. Dependiendo de los datos, es posible que desee invalidar una de las otras versiones de esta función en su lugar. Si desea controlar varios medios de almacenamiento, reemplace [OnRenderData](#onrenderdata). Si los datos están en un archivo o son de tamaño variable, reemplace [OnRenderFileData](#onrenderfiledata).

Para obtener más información, vea [IDataObject::GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata) y [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) en el Windows SDK.

## <a name="coleserveritemonsetcolorscheme"></a><a name="onsetcolorscheme"></a>COleServerItem::OnSetColorScheme

Llamado por el marco de trabajo para especificar una paleta de colores que se utilizará al editar el elemento OLE.

```
virtual BOOL OnSetColorScheme(const LOGPALETTE* lpLogPalette);
```

### <a name="parameters"></a>Parámetros

*lpLogPalette*<br/>
Puntero a una estructura [LOGPALETTE de](/windows/win32/api/wingdi/ns-wingdi-logpalette) Windows.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se utiliza la paleta de colores; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Si la aplicación contenedora se escribió mediante la biblioteca Microsoft Foundation Class, se llama `COleClientItem` a esta función cuando se llama a la función [IOleObject::SetColorScheme](/windows/win32/api/oleidl/nf-oleidl-ioleobject-setcolorscheme) del objeto correspondiente. La implementación predeterminada devuelve FALSE. Reemplace esta función si desea utilizar la paleta recomendada. No es necesario que la aplicación de servidor utilice la paleta sugerida.

Para obtener más información, vea [IOleObject::SetColorScheme](/windows/win32/api/oleidl/nf-oleidl-ioleobject-setcolorscheme) en el Windows SDK.

## <a name="coleserveritemonsetdata"></a><a name="onsetdata"></a>COleServerItem::OnSetData

Llamado por el marco de trabajo para reemplazar los datos del elemento OLE con los datos especificados.

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
Indica quién tiene la propiedad del medio de almacenamiento después de completar la llamada de función. El autor de la llamada decide quién es responsable de liberar los recursos asignados en nombre del medio de almacenamiento. El autor de la llamada hace esto estableciendo *bRelease*. Si *bRelease* es distinto de cero, el elemento de servidor toma la propiedad, liberando el medio cuando ha terminado de usarlo. Cuando *bRelease* es 0, el autor de la llamada conserva la propiedad y el elemento de servidor puede usar el medio de almacenamiento solo durante la llamada.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

El elemento de servidor no toma posesión de los datos hasta que los ha obtenido correctamente. Es decir, no toma posesión si devuelve 0. Si el origen de datos toma la propiedad, libera el medio de almacenamiento mediante una llamada a la [ReleaseStgMedium](/windows/win32/api/ole2/nf-ole2-releasestgmedium) función.

La implementación predeterminada no hace nada. Reemplace esta función para reemplazar los datos del elemento OLE con los datos especificados. Este es un avanzado reemplazable.

Para obtener más información, vea [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1), [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)y [ReleaseStgMedium](/windows/win32/api/ole2/nf-ole2-releasestgmedium) en el Windows SDK.

## <a name="coleserveritemonsetextent"></a><a name="onsetextent"></a>COleServerItem::OnSetExtent

Llamado por el marco de trabajo para indicar al elemento OLE cuánto espacio está disponible en el documento contenedor.

```
virtual BOOL OnSetExtent(
    DVASPECT nDrawAspect,
    const CSize& size);
```

### <a name="parameters"></a>Parámetros

*nDrawAspect*<br/>
Especifica el aspecto del elemento OLE cuyos límites se especifican. Este parámetro puede tener cualquiera de los siguientes valores:

- DVASPECT_CONTENT Item se representa de tal manera que se puede mostrar como un objeto incrustado dentro de su contenedor.

- DVASPECT_THUMBNAIL elemento se representa en una representación "en miniatura" para que se pueda mostrar en una herramienta de exploración.

- DVASPECT_ICON elemento se representa mediante un icono.

- DVASPECT_DOCPRINT Elemento se representa como si se imprimiera mediante el comando Imprimir del menú Archivo.

*size*<br/>
Una estructura [CSize](../../atl-mfc-shared/reference/csize-class.md) que especifica el nuevo tamaño del elemento OLE.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Si la aplicación contenedora se escribió con la biblioteca Microsoft Foundation Class, `COleClientItem` se llama a esta función cuando se llama a la función miembro [SetExtent](../../mfc/reference/coleclientitem-class.md#setextent) del objeto correspondiente. La implementación predeterminada establece el [miembro de m_sizeExtent](#m_sizeextent) en el tamaño especificado si *nDrawAspect* es DVASPECT_CONTENT; de lo contrario devuelve 0. Reemplace esta función para realizar un procesamiento especial al cambiar el tamaño del elemento.

## <a name="coleserveritemonshow"></a><a name="onshow"></a>COleServerItem::OnShow

Llamado por el marco de trabajo para indicar a la aplicación de servidor para mostrar el elemento OLE en su lugar.

```
virtual void OnShow();
```

### <a name="remarks"></a>Observaciones

Normalmente se llama a esta función cuando el usuario de la aplicación contenedora crea un elemento o ejecuta un verbo, como Editar, que requiere que se muestre el elemento. La implementación predeterminada intenta la activación en contexto. Si se produce un `OnOpen` error, la función llama a la función miembro para mostrar el elemento OLE en una ventana independiente.

Invalide esta función si desea realizar un procesamiento especial cuando se muestra un elemento OLE.

## <a name="coleserveritemonupdate"></a><a name="onupdate"></a>COleServerItem::OnUpdate

Llamado por el marco de trabajo cuando se ha modificado un elemento.

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
Valor de la enumeración DVASPECT. Este parámetro puede tener cualquiera de los siguientes valores:

- DVASPECT_CONTENT Item se representa de tal manera que se puede mostrar como un objeto incrustado dentro de su contenedor.

- DVASPECT_THUMBNAIL elemento se representa en una representación "en miniatura" para que se pueda mostrar en una herramienta de exploración.

- DVASPECT_ICON elemento se representa mediante un icono.

- DVASPECT_DOCPRINT Elemento se representa como si se imprimiera mediante el comando Imprimir del menú Archivo.

### <a name="remarks"></a>Observaciones

La implementación predeterminada llama a [NotifyChanged](#notifychanged), independientemente de la sugerencia o el remitente.

## <a name="coleserveritemonupdateitems"></a><a name="onupdateitems"></a>COleServerItem::OnUpdateItems

Llamado por el marco de trabajo para actualizar todos los elementos del documento de servidor.

```
virtual void OnUpdateItems();
```

### <a name="remarks"></a>Observaciones

La implementación predeterminada llama `COleClientItem` a [UpdateLink](../../mfc/reference/coleclientitem-class.md#updatelink) para todos los objetos del documento.

## <a name="coleserveritemsetitemname"></a><a name="setitemname"></a>COleServerItem::SetItemName

Llame a esta función cuando cree un elemento vinculado para establecer su nombre.

```cpp
void SetItemName(LPCTSTR lpszItemName);
```

### <a name="parameters"></a>Parámetros

*lpszItemName*<br/>
Puntero al nuevo nombre del elemento.

### <a name="remarks"></a>Observaciones

El nombre debe ser único dentro del documento. Cuando se llama a una aplicación de servidor para editar un elemento vinculado, la aplicación utiliza este nombre para buscar el elemento. No es necesario llamar a esta función para los elementos incrustados.

## <a name="see-also"></a>Vea también

[Ejemplo de MFC HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[CDocItem (clase)](../../mfc/reference/cdocitem-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clase COleClientItem](../../mfc/reference/coleclientitem-class.md)<br/>
[Clase COleServerDoc](../../mfc/reference/coleserverdoc-class.md)<br/>
[COleTemplateServer (clase)](../../mfc/reference/coletemplateserver-class.md)
