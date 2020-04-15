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
ms.openlocfilehash: fcf9505a7792aea6807e37f05cd1cb1aaad55830
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366119"
---
# <a name="coledatasource-class"></a>COleDataSource (clase)

Actúa como una memoria caché donde una aplicación coloca los datos que proporcionará durante las operaciones de transferencia de datos, tales como las operaciones del Portapapeles y de arrastrar y colocar.

## <a name="syntax"></a>Sintaxis

```
class COleDataSource : public CCmdTarget
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[COleDataSource::COleDataSource](#coledatasource)|Construye un objeto `COleDataSource`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[COleDataSource::CacheData](#cachedata)|Ofrece datos en un formato `STGMEDIUM` especificado mediante una estructura.|
|[COleDataSource::CacheGlobalData](#cacheglobaldata)|Ofrece datos en un formato especificado mediante un HGLOBAL.|
|[COleDataSource::DelayRenderData](#delayrenderdata)|Ofrece datos en un formato especificado mediante la representación retrasada.|
|[COleDataSource::DelayRenderFileData](#delayrenderfiledata)|Ofrece datos en un formato `CFile` especificado en un puntero.|
|[COleDataSource::DelaySetData](#delaysetdata)|Se llama para cada `OnSetData`formato que se admite en .|
|[COleDataSource::DoDragDrop](#dodragdrop)|Realiza operaciones de arrastrar y colocar con un origen de datos.|
|[COleDataSource::Vacío](#empty)|Vacía el `COleDataSource` objeto de datos.|
|[COleDataSource::FlushClipboard](#flushclipboard)|Representa todos los datos en el Portapapeles.|
|[COleDataSource::GetClipboardOwner](#getclipboardowner)|Comprueba que los datos colocados en el Portapapeles siguen ahí.|
|[COleDataSource::OnRenderData](#onrenderdata)|Recupera datos como parte de la representación retrasada.|
|[COleDataSource::OnRenderFileData](#onrenderfiledata)|Recupera datos en `CFile` una representación retrasada.|
|[COleDataSource::OnRenderGlobalData](#onrenderglobaldata)|Recupera datos en un HGLOBAL como parte de la representación retrasada.|
|[COleDataSource::OnSetData](#onsetdata)|Se llama para reemplazar `COleDataSource` los datos del objeto.|
|[COleDataSource::SetClipboard](#setclipboard)|Coloca `COleDataSource` un objeto en el Portapapeles.|

## <a name="remarks"></a>Observaciones

Puede crear orígenes de datos OLE directamente. Como alternativa, el [COleClientItem](../../mfc/reference/coleclientitem-class.md) y [COleServerItem](../../mfc/reference/coleserveritem-class.md) clases `CopyToClipboard` crean `DoDragDrop` orígenes de datos OLE en respuesta a sus funciones miembro y. Vea [COleServerItem::CopyToClipboard](../../mfc/reference/coleserveritem-class.md#copytoclipboard) para obtener una breve descripción. Invalidar `OnGetClipboardData` la función miembro del elemento cliente o clase de elemento de servidor para `CopyToClipboard` `DoDragDrop` agregar formatos de Portapapeles adicionales a los datos en el origen de datos OLE creado para la o función miembro.

Siempre que desee preparar datos para una transferencia, debe crear un objeto de esta clase y rellenarlo con los datos utilizando el método más adecuado para los datos. La forma en que se inserta en un origen de datos se ve directamente afectada por si los datos se proporcionan inmediatamente (representación inmediata) o a petición (representación retrasada). Para cada formato de Portapapeles en el que se proporcionan datos pasando el formato del Portapapeles que se va a utilizar (y una estructura [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) opcional), llame a [DelayRenderData](#delayrenderdata).

Para obtener más información acerca de los orígenes de datos y la transferencia de datos, vea el artículo Objetos de datos y orígenes de [datos (OLE)](../../mfc/data-objects-and-data-sources-ole.md). Además, el artículo [Temas del Portapapeles](../../mfc/clipboard.md) describe el mecanismo del Portapapeles OLE.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleDataSource`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxole.h

## <a name="coledatasourcecachedata"></a><a name="cachedata"></a>COleDataSource::CacheData

Llame a esta función para especificar un formato en el que se ofrecen datos durante las operaciones de transferencia de datos.

```
void CacheData(
    CLIPFORMAT cfFormat,
    LPSTGMEDIUM lpStgMedium,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Parámetros

*cfFormat*<br/>
El formato del Portapapeles en el que se van a ofrecer los datos. Este parámetro puede ser uno de los formatos de Portapapeles predefinidos o el valor devuelto por la función [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) de Windows nativa.

*lpStgMedium*<br/>
Apunta a una estructura [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) que contiene los datos en el formato especificado.

*lpFormatEtc*<br/>
Señala una estructura [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) que describe el formato en el que se van a ofrecer los datos. Proporcione un valor para este parámetro si desea especificar información de formato adicional más allá del formato del Portapapeles especificado por *cfFormat*. Si es NULL, se usan valores predeterminados `FORMATETC` para los demás campos de la estructura.

### <a name="remarks"></a>Observaciones

Debe proporcionar los datos, porque esta función los proporciona mediante la representación inmediata. Los datos se almacenan en caché hasta que sea necesario.

Proporcione los datos utilizando una estructura [STGMEDIUM.](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) También puede utilizar `CacheGlobalData` la función miembro si la cantidad de datos que está suministrando es lo suficientemente pequeña como para transferirse de forma eficiente mediante un HGLOBAL.

Después de `CacheData` `ptd` la `lpFormatEtc` llamada al miembro y el contenido de *lpStgMedium* son propiedad del objeto de datos, no del autor de la llamada.

Para usar la representación retrasada, llame a la [DelayRenderData](#delayrenderdata) o [DelayRenderFileData](#delayrenderfiledata) función miembro. Para obtener más información sobre la representación retrasada controlada por MFC, vea el artículo Objetos de datos y orígenes de [datos: manipulación](../../mfc/data-objects-and-data-sources-manipulation.md).

Para obtener más información, vea las estructuras [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) y [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) en el Windows SDK.

Para obtener más información, consulte [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) en el Windows SDK.

## <a name="coledatasourcecacheglobaldata"></a><a name="cacheglobaldata"></a>COleDataSource::CacheGlobalData

Llame a esta función para especificar un formato en el que se ofrecen datos durante las operaciones de transferencia de datos.

```
void CacheGlobalData(
    CLIPFORMAT cfFormat,
    HGLOBAL hGlobal,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Parámetros

*cfFormat*<br/>
El formato del Portapapeles en el que se van a ofrecer los datos. Este parámetro puede ser uno de los formatos de Portapapeles predefinidos o el valor devuelto por la función [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) de Windows nativa.

*hGlobal*<br/>
Controle el bloque de memoria global que contiene los datos en el formato especificado.

*lpFormatEtc*<br/>
Señala una estructura [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) que describe el formato en el que se van a ofrecer los datos. Proporcione un valor para este parámetro si desea especificar información de formato adicional más allá del formato del Portapapeles especificado por *cfFormat*. Si es NULL, se usan valores predeterminados `FORMATETC` para los demás campos de la estructura.

### <a name="remarks"></a>Observaciones

Esta función proporciona los datos mediante la representación inmediata, por lo que debe proporcionar los datos al llamar a la función; los datos se almacenan en caché hasta que sea necesario. Utilice `CacheData` la función miembro si va a proporcionar una gran cantidad de datos o si necesita un medio de almacenamiento estructurado.

Para usar la representación retrasada, llame a la [DelayRenderData](#delayrenderdata) o [DelayRenderFileData](#delayrenderfiledata) función miembro. Para obtener más información sobre la representación retrasada controlada por MFC, vea el artículo Objetos de datos y orígenes de [datos: manipulación](../../mfc/data-objects-and-data-sources-manipulation.md).

Para obtener más información, consulte la estructura [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) en el Windows SDK.

Para obtener más información, consulte [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) en el Windows SDK.

## <a name="coledatasourcecoledatasource"></a><a name="coledatasource"></a>COleDataSource::COleDataSource

Construye un objeto `COleDataSource`.

```
COleDataSource();
```

## <a name="coledatasourcedelayrenderdata"></a><a name="delayrenderdata"></a>COleDataSource::DelayRenderData

Llame a esta función para especificar un formato en el que se ofrecen datos durante las operaciones de transferencia de datos.

```
void DelayRenderData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Parámetros

*cfFormat*<br/>
El formato del Portapapeles en el que se van a ofrecer los datos. Este parámetro puede ser uno de los formatos de Portapapeles predefinidos o el valor devuelto por la función [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) de Windows nativa.

*lpFormatEtc*<br/>
Señala una estructura [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) que describe el formato en el que se van a ofrecer los datos. Proporcione un valor para este parámetro si desea especificar información de formato adicional más allá del formato del Portapapeles especificado por *cfFormat*. Si es NULL, se usan valores predeterminados `FORMATETC` para los demás campos de la estructura.

### <a name="remarks"></a>Observaciones

Esta función proporciona los datos mediante la representación retrasada, por lo que los datos no se proporcionan inmediatamente. El [OnRenderData](#onrenderdata) o [OnRenderGlobalData](#onrenderglobaldata) función miembro se llama para solicitar los datos.

Utilice esta función si no va a `CFile` proporcionar sus datos a través de un objeto. Si va a proporcionar los `CFile` datos a través de un objeto, llame a la [DelayRenderFileData](#delayrenderfiledata) función miembro. Para obtener más información sobre la representación retrasada controlada por MFC, vea el artículo Objetos de datos y orígenes de [datos: manipulación](../../mfc/data-objects-and-data-sources-manipulation.md).

Para usar la representación inmediata, llame a la [CacheData](#cachedata) o [CacheGlobalData](#cacheglobaldata) función miembro.

Para obtener más información, consulte la estructura [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) en el Windows SDK.

Para obtener más información, consulte [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) en el Windows SDK.

## <a name="coledatasourcedelayrenderfiledata"></a><a name="delayrenderfiledata"></a>COleDataSource::DelayRenderFileData

Llame a esta función para especificar un formato en el que se ofrecen datos durante las operaciones de transferencia de datos.

```
void DelayRenderFileData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Parámetros

*cfFormat*<br/>
El formato del Portapapeles en el que se van a ofrecer los datos. Este parámetro puede ser uno de los formatos de Portapapeles predefinidos o el valor devuelto por la función [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) de Windows nativa.

*lpFormatEtc*<br/>
Señala una estructura [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) que describe el formato en el que se van a ofrecer los datos. Proporcione un valor para este parámetro si desea especificar información de formato adicional más allá del formato del Portapapeles especificado por *cfFormat*. Si es NULL, se usan valores predeterminados `FORMATETC` para los demás campos de la estructura.

### <a name="remarks"></a>Observaciones

Esta función proporciona los datos mediante la representación retrasada, por lo que los datos no se proporcionan inmediatamente. El [OnRenderFileData](#onrenderfiledata) función miembro se llama para solicitar los datos.

Utilice esta función si va `CFile` a utilizar un objeto para proporcionar los datos. Si no va a `CFile` utilizar un objeto, llame a la [DelayRenderData](#delayrenderdata) función miembro. Para obtener más información sobre la representación retrasada controlada por MFC, vea el artículo Objetos de datos y orígenes de [datos: manipulación](../../mfc/data-objects-and-data-sources-manipulation.md).

Para usar la representación inmediata, llame a la [CacheData](#cachedata) o [CacheGlobalData](#cacheglobaldata) función miembro.

Para obtener más información, consulte la estructura [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) en el Windows SDK.

Para obtener más información, consulte [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) en el Windows SDK.

## <a name="coledatasourcedelaysetdata"></a><a name="delaysetdata"></a>COleDataSource::DelaySetData

Llame a esta función para admitir el cambio del contenido del origen de datos.

```
void DelaySetData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Parámetros

*cfFormat*<br/>
El formato del Portapapeles en el que se van a colocar los datos. Este parámetro puede ser uno de los formatos de Portapapeles predefinidos o el valor devuelto por la función [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) de Windows nativa.

*lpFormatEtc*<br/>
Señala una estructura [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) que describe el formato en el que se van a reemplazar los datos. Proporcione un valor para este parámetro si desea especificar información de formato adicional más allá del formato del Portapapeles especificado por *cfFormat*. Si es NULL, se usan valores predeterminados `FORMATETC` para los demás campos de la estructura.

### <a name="remarks"></a>Observaciones

[OnSetData](#onsetdata) será llamado por el marco de trabajo cuando esto sucede. Esto solo se usa cuando el marco de trabajo devuelve el origen de datos de [COleServerItem::GetDataSource](../../mfc/reference/coleserveritem-class.md#getdatasource). Si `DelaySetData` no se `OnSetData` llama, nunca se llamará a la función. `DelaySetData`debe llamarse para `FORMATETC` cada Portapapeles o formato que admita.

Para obtener más información, consulte la estructura [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) en el Windows SDK.

Para obtener más información, consulte [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) en el Windows SDK.

## <a name="coledatasourcedodragdrop"></a><a name="dodragdrop"></a>COleDataSource::DoDragDrop

Llame `DoDragDrop` a la función miembro para realizar una operación de arrastrar y colocar para este origen de datos, normalmente en un [CWnd::OnLButtonDown](../../mfc/reference/cwnd-class.md#onlbuttondown) controlador.

```
DROPEFFECT DoDragDrop(
    DWORD dwEffects = DROPEFFECT_COPY|DROPEFFECT_MOVE|DROPEFFECT_LINK,
    LPCRECT lpRectStartDrag = NULL,
    COleDropSource* pDropSource = NULL);
```

### <a name="parameters"></a>Parámetros

*dwEffects*<br/>
Operaciones de arrastrar y colocar permitidas en este origen de datos. Puede ser uno o más de los siguientes:

- DROPEFFECT_COPY Se puede realizar una operación de copia.

- DROPEFFECT_MOVE Se puede realizar una operación de movimiento.

- DROPEFFECT_LINK Se podría establecer un vínculo de los datos eliminados a los datos originales.

- DROPEFFECT_SCROLL Indica que podría producirse una operación de desplazamiento de arrastre.

*lpRectStartDrag*<br/>
Puntero al rectángulo que define dónde comienza realmente el arrastre. Para obtener más información, vea la sección Comentarios que se muestra más adelante.

*pDropSource*<br/>
Apunta a una fuente de colocación. Si NULL, a continuación, se usará una implementación predeterminada de [COleDropSource.](../../mfc/reference/coledropsource-class.md)

### <a name="return-value"></a>Valor devuelto

Efecto de colocación generado por la operación de arrastrar y colocar; de lo contrario, DROPEFFECT_NONE si la operación nunca comienza porque el usuario soltó el botón del mouse antes de salir del rectángulo proporcionado.

### <a name="remarks"></a>Observaciones

La operación de arrastrar y colocar no se inicia inmediatamente. Espera hasta que el cursor del mouse deja el rectángulo especificado por *lpRectStartDrag* o hasta que haya pasado un número especificado de milisegundos. Si *lpRectStartDrag* es NULL, el tamaño del rectángulo es un píxel.

El tiempo de retardo se especifica mediante una configuración de clave del Registro. Puede cambiar la hora de retardo llamando a [CWinApp::WriteProfileString](../../mfc/reference/cwinapp-class.md#writeprofilestring) o [CWinApp::WriteProfileInt](../../mfc/reference/cwinapp-class.md#writeprofileint). Si no especifica el tiempo de retardo, se utiliza un valor predeterminado de 200 milisegundos. El tiempo de retardo de arrastre se almacena de la siguiente manera:

- El tiempo de retardo de arrastre de Windows NT se almacena en HKEY_LOCAL_MACHINE,SOFTWARE, Microsoft, Windows, NT, CurrentVersion, IniFileMapping, win.ini, Windows y DragDelay.

- Windows 3.x El tiempo de retardo de arrastre se almacena en el WIN. INI, en la sección [Windows.

- Windows 95/98 El tiempo de retardo de arrastre se almacena en una versión almacenada en caché de WIN. Ini.

Para obtener más información sobre cómo se almacena la información de retardo de arrastre en el registro o en el archivo . INI, vea [WriteProfileString](/windows/win32/api/winbase/nf-winbase-writeprofilestringw) en el Windows SDK.

Para obtener más información, vea el artículo [arrastrar y colocar OLE](../../mfc/drag-and-drop-ole.md).

## <a name="coledatasourceempty"></a><a name="empty"></a>COleDataSource::Vacío

Llame a esta `COleDataSource` función para vaciar el objeto de datos.

```
void Empty();
```

### <a name="remarks"></a>Observaciones

Los formatos de procesamiento almacenados en caché y de retardo se vacían para que se puedan reutilizar.

Para obtener más información, vea [ReleaseStgMedium](/windows/win32/api/ole2/nf-ole2-releasestgmedium) en el Windows SDK.

## <a name="coledatasourceflushclipboard"></a><a name="flushclipboard"></a>COleDataSource::FlushClipboard

Representa los datos que se encuentra en el Portapapeles y, a continuación, le permite pegar datos desde el Portapapeles después de que la aplicación se cierre.

```
static void PASCAL FlushClipboard();
```

### <a name="remarks"></a>Observaciones

Utilice [SetClipboard](#setclipboard) para colocar datos en el Portapapeles.

## <a name="coledatasourcegetclipboardowner"></a><a name="getclipboardowner"></a>COleDataSource::GetClipboardOwner

Determina si los datos del Portapapeles han cambiado desde la última vez que se llamó a [SetClipboard](#setclipboard) y, si es así, identifica al propietario actual.

```
static COleDataSource* PASCAL GetClipboardOwner();
```

### <a name="return-value"></a>Valor devuelto

El origen de datos actualmente en el Portapapeles, o NULL si no hay nada en el Portapapeles o si el Portapapeles no es propiedad de la aplicación que realiza la llamada.

## <a name="coledatasourceonrenderdata"></a><a name="onrenderdata"></a>COleDataSource::OnRenderData

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

El formato especificado es uno `COleDataSource` colocado previamente en el objeto mediante el [DelayRenderData](#delayrenderdata) o [DelayRenderFileData](#delayrenderfiledata) función miembro para la representación retrasada. La implementación predeterminada de esta función llamará a [OnRenderFileData](#onrenderfiledata) o [OnRenderGlobalData](#onrenderglobaldata) si el medio de almacenamiento proporcionado es un archivo o memoria, respectivamente. Si no se proporciona ninguno de estos formatos, la implementación predeterminada devolverá 0 y no hará nada. Para obtener más información sobre la representación retrasada controlada por MFC, vea el artículo Objetos de datos y orígenes de [datos: manipulación](../../mfc/data-objects-and-data-sources-manipulation.md).

Si *lpStgMedium*-> *tymed* es `STGMEDIUM` TYMED_NULL, se debe asignar y rellenar según lo especificado por *lpFormatEtc->tymed*. Si no se TYMED_NULL, se `STGMEDIUM` debe rellenar en su lugar con los datos.

Este es un avanzado reemplazable. Reemplace esta función para proporcionar los datos en el formato y medio solicitados. Dependiendo de los datos, es posible que desee invalidar una de las otras versiones de esta función en su lugar. Si los datos son pequeños `OnRenderGlobalData`y de tamaño fijo, invalide . Si los datos están en un archivo o `OnRenderFileData`tienen un tamaño variable, invalide .

Para obtener más información, vea las estructuras [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) y [FORMATETC,](/windows/win32/api/objidl/ns-objidl-formatetc) el tipo de enumeración [TYMED](/windows/win32/api/objidl/ne-objidl-tymed) y [IDataObject::GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata) en el Windows SDK.

## <a name="coledatasourceonrenderfiledata"></a><a name="onrenderfiledata"></a>COleDataSource::OnRenderFileData

Llamado por el marco de trabajo para recuperar datos en el formato especificado cuando el medio de almacenamiento especificado es un archivo.

```
virtual BOOL OnRenderFileData(
    LPFORMATETC lpFormatEtc,
    CFile* pFile);
```

### <a name="parameters"></a>Parámetros

*lpFormatEtc*<br/>
Señala a la estructura [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) especificando el formato en el que se solicita la información.

*pFile*<br/>
Apunta a un [CFile](../../mfc/reference/cfile-class.md) objeto en el que se van a representar los datos.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

El formato especificado es uno `COleDataSource` colocado previamente en el objeto mediante el [DelayRenderData](#delayrenderdata) función miembro para la representación retrasada. La implementación predeterminada de esta función simplemente devuelve FALSE.

Este es un avanzado reemplazable. Reemplace esta función para proporcionar los datos en el formato y medio solicitados. Dependiendo de los datos, es posible que desee invalidar una de las otras versiones de esta función en su lugar. Si desea controlar varios medios de almacenamiento, reemplace [OnRenderData](#onrenderdata). Si los datos están en un archivo o `OnRenderFileData`tienen un tamaño variable, invalide . Para obtener más información sobre la representación retrasada controlada por MFC, vea el artículo Objetos de datos y orígenes de [datos: manipulación](../../mfc/data-objects-and-data-sources-manipulation.md).

Para obtener más información, vea la estructura [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) y [IDataObject::GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata) en el Windows SDK.

## <a name="coledatasourceonrenderglobaldata"></a><a name="onrenderglobaldata"></a>COleDataSource::OnRenderGlobalData

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
Apunta a un identificador de memoria global en la que se van a devolver los datos. Si aún no se ha asignado uno, este parámetro puede ser NULL.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

El formato especificado es uno `COleDataSource` colocado previamente en el objeto mediante el [DelayRenderData](#delayrenderdata) función miembro para la representación retrasada. La implementación predeterminada de esta función simplemente devuelve FALSE.

Si *phGlobal* es NULL, se debe asignar y devolver un nuevo HGLOBAL en *phGlobal*. De lo contrario, el HGLOBAL especificado por *phGlobal* debe rellenarse con los datos. La cantidad de datos colocados en el HGLOBAL no debe exceder el tamaño actual del bloque de memoria. Además, el bloque no se puede reasignar a un tamaño mayor.

Este es un avanzado reemplazable. Reemplace esta función para proporcionar los datos en el formato y medio solicitados. Dependiendo de los datos, es posible que desee invalidar una de las otras versiones de esta función en su lugar. Si desea controlar varios medios de almacenamiento, reemplace [OnRenderData](#onrenderdata). Si los datos están en un archivo o son de tamaño variable, reemplace [OnRenderFileData](#onrenderfiledata). Para obtener más información sobre la representación retrasada controlada por MFC, vea el artículo Objetos de datos y orígenes de [datos: manipulación](../../mfc/data-objects-and-data-sources-manipulation.md).

Para obtener más información, vea la estructura [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) y [IDataObject::GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata) en el Windows SDK.

## <a name="coledatasourceonsetdata"></a><a name="onsetdata"></a>COleDataSource::OnSetData

Llamado por el marco de trabajo `COleDataSource` para establecer o reemplazar los datos en el objeto en el formato especificado.

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
Apunta a la estructura [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) que contiene los `COleDataSource` datos que reemplazarán el contenido actual del objeto.

*bRelease*<br/>
Indica quién tiene la propiedad del medio de almacenamiento después de completar la llamada de función. El autor de la llamada decide quién es responsable de liberar los recursos asignados en nombre del medio de almacenamiento. El autor de la llamada hace esto estableciendo *bRelease*. Si *bRelease* es distinto de cero, el origen de datos toma la propiedad, liberando el medio cuando ha terminado de usarlo. Cuando *bRelease* es 0, el autor de la llamada conserva la propiedad y el origen de datos puede usar el medio de almacenamiento solo durante la llamada.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

El origen de datos no toma posesión de los datos hasta que los ha obtenido correctamente. Es decir, no toma `OnSetData` posesión si devuelve 0. Si el origen de datos toma la propiedad, libera el medio de almacenamiento mediante una llamada a la [ReleaseStgMedium](/windows/win32/api/ole2/nf-ole2-releasestgmedium) función.

La implementación predeterminada no hace nada. Reemplace esta función para reemplazar los datos en el formato especificado. Este es un avanzado reemplazable.

Para obtener más información, vea las estructuras [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) y [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) y las funciones [ReleaseStgMedium](/windows/win32/api/ole2/nf-ole2-releasestgmedium) e [IDataObject::GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata) en el Windows SDK.

## <a name="coledatasourcesetclipboard"></a><a name="setclipboard"></a>COleDataSource::SetClipboard

Coloca los datos contenidos `COleDataSource` en el objeto en el Portapapeles después de llamar a una de las siguientes funciones: [CacheData](#cachedata), [CacheGlobalData](#cacheglobaldata), [DelayRenderData](#delayrenderdata)o [DelayRenderFileData](#delayrenderfiledata).

```
void SetClipboard();
```

## <a name="see-also"></a>Consulte también

[Ejemplo de MFC HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[Ejemplo de MFC OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[CCmdTarget (clase)](../../mfc/reference/ccmdtarget-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[COleDataObject (clase)](../../mfc/reference/coledataobject-class.md)
