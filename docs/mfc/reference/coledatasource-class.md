---
title: COleDataSource (clase)
ms.date: 11/04/2016
f1_keywords:
- COleDataSource
- AFXOLE/COleDataSource
- AFXOLE/COleDataSource::COleDataSource
- AFXOLE/COleDataSource::CacheData
- AFXOLE/COleDataSource::CacheGlobalData
- AFXOLE/COleDataSource::DelayRenderData
- AFXOLE/COleDataSource::DelayRenderFileData
- AFXOLE/COleDataSource::DelaySetData
- AFXOLE/COleDataSource::DoDragDrop
- AFXOLE/COleDataSource::Empty
- AFXOLE/COleDataSource::FlushClipboard
- AFXOLE/COleDataSource::GetClipboardOwner
- AFXOLE/COleDataSource::OnRenderData
- AFXOLE/COleDataSource::OnRenderFileData
- AFXOLE/COleDataSource::OnRenderGlobalData
- AFXOLE/COleDataSource::OnSetData
- AFXOLE/COleDataSource::SetClipboard
helpviewer_keywords:
- COleDataSource [MFC], COleDataSource
- COleDataSource [MFC], CacheData
- COleDataSource [MFC], CacheGlobalData
- COleDataSource [MFC], DelayRenderData
- COleDataSource [MFC], DelayRenderFileData
- COleDataSource [MFC], DelaySetData
- COleDataSource [MFC], DoDragDrop
- COleDataSource [MFC], Empty
- COleDataSource [MFC], FlushClipboard
- COleDataSource [MFC], GetClipboardOwner
- COleDataSource [MFC], OnRenderData
- COleDataSource [MFC], OnRenderFileData
- COleDataSource [MFC], OnRenderGlobalData
- COleDataSource [MFC], OnSetData
- COleDataSource [MFC], SetClipboard
ms.assetid: 02c8ee7d-8e10-4463-8613-bb2a0305ca69
ms.openlocfilehash: 5cd573590bc1adb303e0b4c5cd600b9fa6c685b2
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79426526"
---
# <a name="coledatasource-class"></a>COleDataSource (clase)

Actúa como una memoria caché donde una aplicación coloca los datos que proporcionará durante las operaciones de transferencia de datos, tales como las operaciones del Portapapeles y de arrastrar y colocar.

## <a name="syntax"></a>Sintaxis

```
class COleDataSource : public CCmdTarget
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[COleDataSource:: COleDataSource](#coledatasource)|Construye un objeto `COleDataSource`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[COleDataSource:: CacheData](#cachedata)|Proporciona datos en un formato especificado mediante una estructura de `STGMEDIUM`.|
|[COleDataSource:: CacheGlobalData](#cacheglobaldata)|Proporciona datos en un formato especificado mediante un HGLOBAL.|
|[COleDataSource::D elayRenderData](#delayrenderdata)|Ofrece datos en un formato especificado mediante la representación retrasada.|
|[COleDataSource::D elayRenderFileData](#delayrenderfiledata)|Proporciona datos en un formato especificado en un puntero `CFile`.|
|[COleDataSource::D elaySetData](#delaysetdata)|Se llama para cada formato admitido en `OnSetData`.|
|[COleDataSource::D oDragDrop](#dodragdrop)|Realiza operaciones de arrastrar y colocar con un origen de datos.|
|[COleDataSource:: Empty](#empty)|Vacía el objeto de `COleDataSource` de datos.|
|[COleDataSource:: FlushClipboard](#flushclipboard)|Representa todos los datos en el portapapeles.|
|[COleDataSource:: GetClipboardOwner](#getclipboardowner)|Comprueba que los datos colocados en el portapapeles siguen ahí.|
|[COleDataSource:: OnRenderData](#onrenderdata)|Recupera los datos como parte de la representación retrasada.|
|[COleDataSource:: OnRenderFileData](#onrenderfiledata)|Recupera datos en un `CFile` como parte de la representación retrasada.|
|[COleDataSource:: OnRenderGlobalData](#onrenderglobaldata)|Recupera datos en un HGLOBAL como parte de la representación retrasada.|
|[COleDataSource:: OnSetData](#onsetdata)|Se llama para reemplazar los datos del objeto `COleDataSource`.|
|[COleDataSource:: SetClipboard](#setclipboard)|Coloca un objeto `COleDataSource` en el portapapeles.|

## <a name="remarks"></a>Observaciones

Puede crear directamente orígenes de datos OLE. Como alternativa, las clases [COleClientItem](../../mfc/reference/coleclientitem-class.md) y [COleServerItem](../../mfc/reference/coleserveritem-class.md) crean orígenes de datos OLE en respuesta a sus funciones miembro `CopyToClipboard` y `DoDragDrop`. Vea [COleServerItem:: CopyToClipboard](../../mfc/reference/coleserveritem-class.md#copytoclipboard) para obtener una breve descripción. Invalide el `OnGetClipboardData` función miembro de la clase de elemento de cliente o de servidor para agregar formatos de Portapapeles adicionales a los datos del origen de datos OLE creado para la función miembro `CopyToClipboard` o `DoDragDrop`.

Siempre que desee preparar los datos para una transferencia, debe crear un objeto de esta clase y rellenarlo con los datos usando el método más adecuado para los datos. El modo en que se inserta en un origen de datos se ve directamente afectado por si los datos se proporcionan inmediatamente (representación inmediata) o a petición (representación diferida). Para cada formato del portapapeles en el que esté proporcionando datos pasando el formato del portapapeles que se va a usar (y una estructura [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) opcional), llame a [DelayRenderData](#delayrenderdata).

Para obtener más información sobre los orígenes de datos y la transferencia de datos, vea el artículo [objetos de datos y orígenes de datos (OLE)](../../mfc/data-objects-and-data-sources-ole.md). Además, en el artículo [sobre el portapapeles](../../mfc/clipboard.md) se describe el mecanismo del portapapeles OLE.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleDataSource`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxole. h

##  <a name="cachedata"></a>COleDataSource:: CacheData

Llame a esta función para especificar un formato en el que se ofrecen los datos durante las operaciones de transferencia de datos.

```
void CacheData(
    CLIPFORMAT cfFormat,
    LPSTGMEDIUM lpStgMedium,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Parámetros

*cfFormat*<br/>
Formato del portapapeles en el que se van a ofrecer los datos. Este parámetro puede ser uno de los formatos predefinidos del portapapeles o el valor devuelto por la función [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) nativa de Windows.

*lpStgMedium*<br/>
Apunta a una estructura [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) que contiene los datos en el formato especificado.

*lpFormatEtc*<br/>
Apunta a una estructura [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) que describe el formato en el que se van a ofrecer los datos. Proporcione un valor para este parámetro si desea especificar información de formato adicional más allá del formato del portapapeles especificado por *cfFormat*. Si es NULL, se usan los valores predeterminados para los demás campos de la estructura `FORMATETC`.

### <a name="remarks"></a>Observaciones

Debe proporcionar los datos, ya que esta función lo proporciona mediante la representación inmediata. Los datos se almacenan en caché hasta que sea necesario.

Proporcione los datos mediante una estructura [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) . También puede usar la función miembro `CacheGlobalData` si la cantidad de datos que está proporcionando es lo suficientemente pequeña como para transferirse de forma eficaz mediante un HGLOBAL.

Después de la llamada a `CacheData` el miembro de `ptd` de `lpFormatEtc` y el contenido de *lpStgMedium* es propiedad del objeto de datos, no del llamador.

Para usar la representación diferida, llame a la función miembro [DelayRenderData](#delayrenderdata) o [DelayRenderFileData](#delayrenderfiledata) . Para obtener más información sobre la representación diferida tal como la controla MFC, vea el artículo [objetos de datos y orígenes de datos: manipulación](../../mfc/data-objects-and-data-sources-manipulation.md).

Para obtener más información, vea las estructuras [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) y [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) en el Windows SDK.

Para obtener más información, vea [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) en el Windows SDK.

##  <a name="cacheglobaldata"></a>COleDataSource:: CacheGlobalData

Llame a esta función para especificar un formato en el que se ofrecen los datos durante las operaciones de transferencia de datos.

```
void CacheGlobalData(
    CLIPFORMAT cfFormat,
    HGLOBAL hGlobal,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Parámetros

*cfFormat*<br/>
Formato del portapapeles en el que se van a ofrecer los datos. Este parámetro puede ser uno de los formatos predefinidos del portapapeles o el valor devuelto por la función [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) nativa de Windows.

*hGlobal*<br/>
Identificador del bloque de memoria global que contiene los datos en el formato especificado.

*lpFormatEtc*<br/>
Apunta a una estructura [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) que describe el formato en el que se van a ofrecer los datos. Proporcione un valor para este parámetro si desea especificar información de formato adicional más allá del formato del portapapeles especificado por *cfFormat*. Si es NULL, se usan los valores predeterminados para los demás campos de la estructura `FORMATETC`.

### <a name="remarks"></a>Observaciones

Esta función proporciona los datos mediante la representación inmediata, por lo que debe proporcionar los datos al llamar a la función. los datos se almacenan en caché hasta que sea necesario. Utilice la función miembro `CacheData` si va a proporcionar una gran cantidad de datos o si necesita un medio de almacenamiento estructurado.

Para usar la representación diferida, llame a la función miembro [DelayRenderData](#delayrenderdata) o [DelayRenderFileData](#delayrenderfiledata) . Para obtener más información sobre la representación diferida tal como la controla MFC, vea el artículo [objetos de datos y orígenes de datos: manipulación](../../mfc/data-objects-and-data-sources-manipulation.md).

Para obtener más información, vea la estructura [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) en el Windows SDK.

Para obtener más información, vea [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) en el Windows SDK.

##  <a name="coledatasource"></a>COleDataSource:: COleDataSource

Construye un objeto `COleDataSource`.

```
COleDataSource();
```

##  <a name="delayrenderdata"></a>COleDataSource::D elayRenderData

Llame a esta función para especificar un formato en el que se ofrecen los datos durante las operaciones de transferencia de datos.

```
void DelayRenderData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Parámetros

*cfFormat*<br/>
Formato del portapapeles en el que se van a ofrecer los datos. Este parámetro puede ser uno de los formatos predefinidos del portapapeles o el valor devuelto por la función [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) nativa de Windows.

*lpFormatEtc*<br/>
Apunta a una estructura [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) que describe el formato en el que se van a ofrecer los datos. Proporcione un valor para este parámetro si desea especificar información de formato adicional más allá del formato del portapapeles especificado por *cfFormat*. Si es NULL, se usan los valores predeterminados para los demás campos de la estructura `FORMATETC`.

### <a name="remarks"></a>Observaciones

Esta función proporciona los datos mediante la representación retrasada, por lo que los datos no se suministran inmediatamente. Se llama a la función miembro [OnRenderData](#onrenderdata) o [OnRenderGlobalData](#onrenderglobaldata) para solicitar los datos.

Use esta función si no va a proporcionar los datos a través de un objeto de `CFile`. Si va a proporcionar los datos a través de un objeto `CFile`, llame a la función miembro [DelayRenderFileData](#delayrenderfiledata) . Para obtener más información sobre la representación diferida tal como la controla MFC, vea el artículo [objetos de datos y orígenes de datos: manipulación](../../mfc/data-objects-and-data-sources-manipulation.md).

Para usar la representación inmediata, llame a la función miembro [CacheData](#cachedata) o [CacheGlobalData](#cacheglobaldata) .

Para obtener más información, vea la estructura [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) en el Windows SDK.

Para obtener más información, vea [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) en el Windows SDK.

##  <a name="delayrenderfiledata"></a>COleDataSource::D elayRenderFileData

Llame a esta función para especificar un formato en el que se ofrecen los datos durante las operaciones de transferencia de datos.

```
void DelayRenderFileData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Parámetros

*cfFormat*<br/>
Formato del portapapeles en el que se van a ofrecer los datos. Este parámetro puede ser uno de los formatos predefinidos del portapapeles o el valor devuelto por la función [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) nativa de Windows.

*lpFormatEtc*<br/>
Apunta a una estructura [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) que describe el formato en el que se van a ofrecer los datos. Proporcione un valor para este parámetro si desea especificar información de formato adicional más allá del formato del portapapeles especificado por *cfFormat*. Si es NULL, se usan los valores predeterminados para los demás campos de la estructura `FORMATETC`.

### <a name="remarks"></a>Observaciones

Esta función proporciona los datos mediante la representación retrasada, por lo que los datos no se suministran inmediatamente. Se llama a la función miembro [OnRenderFileData](#onrenderfiledata) para solicitar los datos.

Use esta función si va a utilizar un objeto `CFile` para proporcionar los datos. Si no va a usar un objeto `CFile`, llame a la función miembro [DelayRenderData](#delayrenderdata) . Para obtener más información sobre la representación diferida tal como la controla MFC, vea el artículo [objetos de datos y orígenes de datos: manipulación](../../mfc/data-objects-and-data-sources-manipulation.md).

Para usar la representación inmediata, llame a la función miembro [CacheData](#cachedata) o [CacheGlobalData](#cacheglobaldata) .

Para obtener más información, vea la estructura [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) en el Windows SDK.

Para obtener más información, vea [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) en el Windows SDK.

##  <a name="delaysetdata"></a>COleDataSource::D elaySetData

Llame a esta función para admitir el cambio del contenido del origen de datos.

```
void DelaySetData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Parámetros

*cfFormat*<br/>
Formato del portapapeles en el que se van a colocar los datos. Este parámetro puede ser uno de los formatos predefinidos del portapapeles o el valor devuelto por la función [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) nativa de Windows.

*lpFormatEtc*<br/>
Apunta a una estructura [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) que describe el formato en el que se van a reemplazar los datos. Proporcione un valor para este parámetro si desea especificar información de formato adicional más allá del formato del portapapeles especificado por *cfFormat*. Si es NULL, se usan los valores predeterminados para los demás campos de la estructura `FORMATETC`.

### <a name="remarks"></a>Observaciones

El marco de trabajo llamará a [OnSetData](#onsetdata) cuando esto suceda. Solo se usa cuando el marco de trabajo devuelve el origen de datos de [COleServerItem:: GetDataSource](../../mfc/reference/coleserveritem-class.md#getdatasource). Si no se llama a `DelaySetData`, nunca se llamará a la función `OnSetData`. se debe llamar a `DelaySetData` para cada portapapeles o formato de `FORMATETC` que admita.

Para obtener más información, vea la estructura [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) en el Windows SDK.

Para obtener más información, vea [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) en el Windows SDK.

##  <a name="dodragdrop"></a>COleDataSource::D oDragDrop

Llame a la función miembro `DoDragDrop` para realizar una operación de arrastrar y colocar para este origen de datos, normalmente en un controlador [CWnd:: OnLButtonDown](../../mfc/reference/cwnd-class.md#onlbuttondown) .

```
DROPEFFECT DoDragDrop(
    DWORD dwEffects = DROPEFFECT_COPY|DROPEFFECT_MOVE|DROPEFFECT_LINK,
    LPCRECT lpRectStartDrag = NULL,
    COleDropSource* pDropSource = NULL);
```

### <a name="parameters"></a>Parámetros

*dwEffects*<br/>
Operaciones de arrastrar y colocar que se permiten en este origen de datos. Puede ser uno o varios de los siguientes:

- DROPEFFECT_COPY se puede realizar una operación de copia.

- DROPEFFECT_MOVE se puede realizar una operación de movimiento.

- DROPEFFECT_LINK se podría establecer un vínculo entre los datos colocados y los datos originales.

- DROPEFFECT_SCROLL indica que podría producirse una operación de desplazamiento de arrastre.

*lpRectStartDrag*<br/>
Puntero al rectángulo que define dónde se inicia realmente la acción de arrastrar. Para obtener más información, vea la sección Comentarios que se muestra más adelante.

*pDropSource*<br/>
Apunta a un origen de colocación. Si es NULL, se usará una implementación predeterminada de [COleDropSource](../../mfc/reference/coledropsource-class.md) .

### <a name="return-value"></a>Valor devuelto

Efecto de colocación generado por la operación de arrastrar y colocar; de lo contrario DROPEFFECT_NONE si la operación nunca comienza porque el usuario suelta el botón del mouse antes de que abandone el rectángulo proporcionado.

### <a name="remarks"></a>Observaciones

La operación de arrastrar y colocar no se inicia inmediatamente. Espera hasta que el cursor del mouse salga del rectángulo especificado por *lpRectStartDrag* o hasta que haya transcurrido un número de milisegundos especificado. Si *lpRectStartDrag* es null, el tamaño del rectángulo es un píxel.

El tiempo de retraso se especifica mediante una configuración de clave del registro. Puede cambiar el tiempo de retraso llamando a [CWinApp:: WriteProfileString](../../mfc/reference/cwinapp-class.md#writeprofilestring) o [CWinApp:: WriteProfileInt](../../mfc/reference/cwinapp-class.md#writeprofileint). Si no especifica el tiempo de retraso, se usa un valor predeterminado de 200 milisegundos. La hora de retraso de arrastre se almacena de la siguiente manera:

- El tiempo de retraso de arrastre de Windows NT se almacena en HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\Windows\NT\CurrentVersion\IniFileMapping\win.ini\Windows\DragDelay.

- El tiempo de retraso de arrastre de Windows 3. x se almacena en el archivo WIN. Archivo INI, en la sección [Windows}.

- El tiempo de retraso de arrastre de Windows 95/98 se almacena en una versión almacenada en caché de WIN. INI.

Para obtener más información sobre cómo se almacena la información de retraso de arrastre en el registro o en. Archivo INI, consulte [WriteProfileString](/windows/win32/api/winbase/nf-winbase-writeprofilestringw) en el Windows SDK.

Para obtener más información, vea el artículo [arrastrar y colocar de OLE](../../mfc/drag-and-drop-ole.md).

##  <a name="empty"></a>COleDataSource:: Empty

Llame a esta función para vaciar el `COleDataSource` objeto de datos.

```
void Empty();
```

### <a name="remarks"></a>Observaciones

Los formatos de representación en caché y de retardo se vacían para que se puedan volver a usar.

Para obtener más información, vea [ReleaseStgMedium](/windows/win32/api/ole2/nf-ole2-releasestgmedium) en el Windows SDK.

##  <a name="flushclipboard"></a>COleDataSource:: FlushClipboard

Representa los datos que están en el portapapeles y, a continuación, permite pegar datos del portapapeles después de cerrar la aplicación.

```
static void PASCAL FlushClipboard();
```

### <a name="remarks"></a>Observaciones

Use [SetClipboard](#setclipboard) para colocar los datos en el portapapeles.

##  <a name="getclipboardowner"></a>COleDataSource:: GetClipboardOwner

Determina si los datos del portapapeles han cambiado desde que se llamó a [SetClipboard](#setclipboard) por última vez y, en ese caso, identifica al propietario actual.

```
static COleDataSource* PASCAL GetClipboardOwner();
```

### <a name="return-value"></a>Valor devuelto

Origen de datos que se encuentra actualmente en el portapapeles, o NULL si no hay nada en el portapapeles o si el portapapeles no es propiedad de la aplicación que realiza la llamada.

##  <a name="onrenderdata"></a>COleDataSource:: OnRenderData

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

### <a name="remarks"></a>Observaciones

El formato especificado se colocó previamente en el objeto `COleDataSource` mediante la función miembro [DelayRenderData](#delayrenderdata) o [DelayRenderFileData](#delayrenderfiledata) para la representación diferida. La implementación predeterminada de esta función llamará a [OnRenderFileData](#onrenderfiledata) o [OnRenderGlobalData](#onrenderglobaldata) si el medio de almacenamiento proporcionado es un archivo o memoria, respectivamente. Si no se proporciona ninguno de estos formatos, la implementación predeterminada devolverá 0 y no hará nada. Para obtener más información sobre la representación diferida tal como la controla MFC, vea el artículo [objetos de datos y orígenes de datos: manipulación](../../mfc/data-objects-and-data-sources-manipulation.md).

Si *lpStgMedium*-> *tymed* es TYMED_NULL, el `STGMEDIUM` debe estar asignado y rellenado según lo especificado por *lpFormatEtc-> tymed*. Si no se TYMED_NULL, el `STGMEDIUM` debe rellenarse con los datos.

Se trata de un reemplazable avanzado. Invalide esta función para proporcionar los datos en el formato y medio solicitados. En función de los datos, puede que desee reemplazar una de las otras versiones de esta función en su lugar. Si los datos son pequeños y tienen un tamaño fijo, invalide `OnRenderGlobalData`. Si los datos están en un archivo o tiene un tamaño variable, invalide `OnRenderFileData`.

Para obtener más información, vea las estructuras [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) y [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) , el tipo de enumeración [TYMED](/windows/win32/api/objidl/ne-objidl-tymed) y [IDataObject:: GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata) en el Windows SDK.

##  <a name="onrenderfiledata"></a>COleDataSource:: OnRenderFileData

Lo llama el marco de trabajo para recuperar los datos en el formato especificado cuando el medio de almacenamiento especificado es un archivo.

```
virtual BOOL OnRenderFileData(
    LPFORMATETC lpFormatEtc,
    CFile* pFile);
```

### <a name="parameters"></a>Parámetros

*lpFormatEtc*<br/>
Apunta a la estructura [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) especificando el formato en el que se solicita información.

*pFile*<br/>
Señala a un objeto [CFile](../../mfc/reference/cfile-class.md) en el que se van a representar los datos.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

El formato especificado es el que se colocó previamente en el objeto `COleDataSource` mediante la función miembro [DelayRenderData](#delayrenderdata) para la representación diferida. La implementación predeterminada de esta función simplemente devuelve FALSE.

Se trata de un reemplazable avanzado. Invalide esta función para proporcionar los datos en el formato y medio solicitados. En función de los datos, es posible que desee invalidar una de las otras versiones de esta función en su lugar. Si desea administrar varios medios de almacenamiento, invalide [OnRenderData](#onrenderdata). Si los datos están en un archivo o tiene un tamaño variable, invalide `OnRenderFileData`. Para obtener más información sobre la representación diferida tal como la controla MFC, vea el artículo [objetos de datos y orígenes de datos: manipulación](../../mfc/data-objects-and-data-sources-manipulation.md).

Para obtener más información, vea la estructura [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) y [IDataObject:: GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata) en el Windows SDK.

##  <a name="onrenderglobaldata"></a>COleDataSource:: OnRenderGlobalData

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
Apunta a un identificador de la memoria global en la que se van a devolver los datos. Si aún no se ha asignado ninguno, este parámetro puede ser NULL.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

El formato especificado es el que se colocó previamente en el objeto `COleDataSource` mediante la función miembro [DelayRenderData](#delayrenderdata) para la representación diferida. La implementación predeterminada de esta función simplemente devuelve FALSE.

Si *phGlobal* es null, se debe asignar y devolver un nuevo hglobal en *phGlobal*. De lo contrario, el HGLOBAL especificado por *phGlobal* se debe rellenar con los datos. La cantidad de datos que se colocan en el HGLOBAL no debe superar el tamaño actual del bloque de memoria. Además, el bloque no se puede reasignar a un tamaño mayor.

Se trata de un reemplazable avanzado. Invalide esta función para proporcionar los datos en el formato y medio solicitados. En función de los datos, puede que desee reemplazar una de las otras versiones de esta función en su lugar. Si desea administrar varios medios de almacenamiento, invalide [OnRenderData](#onrenderdata). Si los datos están en un archivo o tiene un tamaño variable, invalide [OnRenderFileData](#onrenderfiledata). Para obtener más información sobre la representación diferida tal como la controla MFC, vea el artículo [objetos de datos y orígenes de datos: manipulación](../../mfc/data-objects-and-data-sources-manipulation.md).

Para obtener más información, vea la estructura [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) y [IDataObject:: GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata) en el Windows SDK.

##  <a name="onsetdata"></a>COleDataSource:: OnSetData

Lo llama el marco de trabajo para establecer o reemplazar los datos del objeto `COleDataSource` en el formato especificado.

```
virtual BOOL OnSetData(
    LPFORMATETC lpFormatEtc,
    LPSTGMEDIUM lpStgMedium,
    BOOL bRelease);
```

### <a name="parameters"></a>Parámetros

*lpFormatEtc*<br/>
Apunta a la estructura [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) especificando el formato en el que se reemplazan los datos.

*lpStgMedium*<br/>
Apunta a la estructura [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) que contiene los datos que reemplazarán el contenido actual del objeto `COleDataSource`.

*bRelease*<br/>
Indica quién tiene la propiedad del medio de almacenamiento después de completar la llamada de función. El autor de la llamada decide quién es responsable de liberar los recursos asignados en nombre del medio de almacenamiento. Para ello, el autor de la llamada establece *bRelease*. Si *bRelease* es distinto de cero, el origen de datos toma la propiedad, liberando el medio cuando ha terminado de usarlo. Cuando *bRelease* es 0, el llamador conserva la propiedad y el origen de datos puede usar el medio de almacenamiento solo mientras dure la llamada.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

El origen de datos no toma la propiedad de los datos hasta que se hayan obtenido correctamente. Es decir, no toma la propiedad si `OnSetData` devuelve 0. Si el origen de datos toma posesión, libera el medio de almacenamiento mediante una llamada a la función [ReleaseStgMedium](/windows/win32/api/ole2/nf-ole2-releasestgmedium) .

La implementación predeterminada no hace nada. Invalide esta función para reemplazar los datos en el formato especificado. Se trata de un reemplazable avanzado.

Para obtener más información, vea las estructuras [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) y [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) y las funciones [ReleaseStgMedium](/windows/win32/api/ole2/nf-ole2-releasestgmedium) y [IDataObject:: GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata) en el Windows SDK.

##  <a name="setclipboard"></a>COleDataSource:: SetClipboard

Coloca los datos contenidos en el objeto de `COleDataSource` en el portapapeles después de llamar a una de las siguientes funciones: [CacheData](#cachedata), [CacheGlobalData](#cacheglobaldata), [DelayRenderData](#delayrenderdata)o [DelayRenderFileData](#delayrenderfiledata).

```
void SetClipboard();
```

## <a name="see-also"></a>Consulte también

[Ejemplo de MFC HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[Ejemplo OCLIENT de MFC](../../overview/visual-cpp-samples.md)<br/>
[CCmdTarget (clase)](../../mfc/reference/ccmdtarget-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[COleDataObject (clase)](../../mfc/reference/coledataobject-class.md)
