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
ms.openlocfilehash: bc3d9f089dc6289331c79c6a1e18eccbc9ff4993
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57296980"
---
# <a name="coledatasource-class"></a>COleDataSource (clase)

Actúa como una memoria caché donde una aplicación coloca los datos que proporcionará durante las operaciones de transferencia de datos, tales como las operaciones del Portapapeles y de arrastrar y colocar.

## <a name="syntax"></a>Sintaxis

```
class COleDataSource : public CCmdTarget
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[COleDataSource::COleDataSource](#coledatasource)|Construye un objeto `COleDataSource`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[COleDataSource::CacheData](#cachedata)|Ofrece los datos en un formato especificado mediante un `STGMEDIUM` estructura.|
|[COleDataSource::CacheGlobalData](#cacheglobaldata)|Ofrece los datos en un formato especificado mediante un identificador HGLOBAL.|
|[COleDataSource::DelayRenderData](#delayrenderdata)|Ofrece los datos en un formato especificado mediante la representación aplazada.|
|[COleDataSource::DelayRenderFileData](#delayrenderfiledata)|Ofrece los datos en un formato especificado en un `CFile` puntero.|
|[COleDataSource::DelaySetData](#delaysetdata)|Llamado para todos los formatos que se admiten en `OnSetData`.|
|[COleDataSource::DoDragDrop](#dodragdrop)|Realiza las operaciones de arrastrar y colocar con un origen de datos.|
|[COleDataSource::Empty](#empty)|Vacía la `COleDataSource` objeto de datos.|
|[COleDataSource::FlushClipboard](#flushclipboard)|Representa todos los datos en el Portapapeles.|
|[COleDataSource::GetClipboardOwner](#getclipboardowner)|Comprueba que los datos que se coloca en el Portapapeles están aún allí.|
|[COleDataSource::OnRenderData](#onrenderdata)|Recupera los datos como parte de la representación aplazada.|
|[COleDataSource::OnRenderFileData](#onrenderfiledata)|Recupera los datos en un `CFile` como parte de la representación aplazada.|
|[COleDataSource::OnRenderGlobalData](#onrenderglobaldata)|Recupera los datos en un HGLOBAL como parte de la representación aplazada.|
|[COleDataSource::OnSetData](#onsetdata)|Se llama para reemplazar los datos de la `COleDataSource` objeto.|
|[COleDataSource::SetClipboard](#setclipboard)|Coloca un `COleDataSource` objeto en el Portapapeles.|

## <a name="remarks"></a>Comentarios

Puede crear orígenes de datos OLE directamente. Como alternativa, el [COleClientItem](../../mfc/reference/coleclientitem-class.md) y [COleServerItem](../../mfc/reference/coleserveritem-class.md) clases crean orígenes de datos OLE en respuesta a sus `CopyToClipboard` y `DoDragDrop` funciones miembro. Consulte [COleServerItem::CopyToClipboard](../../mfc/reference/coleserveritem-class.md#copytoclipboard) para obtener una descripción breve. Invalidar el `OnGetClipboardData` función miembro de la clase de elemento de elemento o el servidor de cliente para agregar los formatos de Portapapeles adicionales a los datos en el origen de datos OLE creado para el `CopyToClipboard` o `DoDragDrop` función miembro.

Siempre que quiera preparar una transferencia de datos, debe crear un objeto de esta clase y rellenarlo con los datos mediante el método más adecuado para los datos. La forma en se inserta en un origen de datos se ve directamente afectada por si los datos se proporcionan inmediatamente (procesamiento inmediato) o a petición (procesamiento aplazado). Para cada formato de Portapapeles en el que va a proporcionar datos pasando el formato del Portapapeles que se usará (opcional [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) estructura), llame a [DelayRenderData](#delayrenderdata).

Para obtener más información acerca de los orígenes de datos y transferencia de datos, vea el artículo [objetos de datos y orígenes de datos (OLE)](../../mfc/data-objects-and-data-sources-ole.md). Además, el artículo [Portapapeles temas](../../mfc/clipboard.md) describe el mecanismo del Portapapeles de OLE.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleDataSource`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxole.h

##  <a name="cachedata"></a>  COleDataSource::CacheData

Llame a esta función para especificar un formato en el que datos se ofrezcan durante los datos de las operaciones de transferencia.

```
void CacheData(
    CLIPFORMAT cfFormat,
    LPSTGMEDIUM lpStgMedium,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Parámetros

*cfFormat*<br/>
El formato de Portapapeles en el que se ofrecerá los datos. Este parámetro puede ser uno de los formatos de Portapapeles predefinidos o el valor devuelto por el Windows nativo [RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata) función.

*lpStgMedium*<br/>
Apunta a un [STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium) estructura que contiene los datos en el formato especificado.

*lpFormatEtc*<br/>
Apunta a un [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) estructura que describe el formato en el que se les ofrecerá los datos. Proporcionar un valor para este parámetro si desea especificar información de formato adicionales más allá del formato de Portapapeles especificado por *cfFormat*. Si es NULL, se usan los valores predeterminados para los demás campos en el `FORMATETC` estructura.

### <a name="remarks"></a>Comentarios

Debe suministrar los datos, ya que esta función proporciona mediante el uso de procesamiento inmediato. Los datos se almacena en caché hasta que sea necesario.

Proporcione los datos mediante un [STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium) estructura. También puede usar el `CacheGlobalData` función de miembro si la cantidad de datos que está proporcionando es lo suficientemente pequeño como para transferir eficazmente mediante un identificador HGLOBAL.

Después de llamar a `CacheData` el `ptd` miembro de `lpFormatEtc` y el contenido de *lpStgMedium* son propiedad del objeto de datos, no por el llamador.

Para usar la representación aplazada, llame a la [DelayRenderData](#delayrenderdata) o [DelayRenderFileData](#delayrenderfiledata) función miembro. Para obtener más información sobre la representación aplazada como controlado por MFC, vea el artículo [objetos de datos y orígenes de datos: Manipulación](../../mfc/data-objects-and-data-sources-manipulation.md).

Para obtener más información, consulte el [STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium) y [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) estructuras en el SDK de Windows.

Para obtener más información, consulte [RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata) en el SDK de Windows.

##  <a name="cacheglobaldata"></a>  COleDataSource::CacheGlobalData

Llame a esta función para especificar un formato en el que datos se ofrezcan durante los datos de las operaciones de transferencia.

```
void CacheGlobalData(
    CLIPFORMAT cfFormat,
    HGLOBAL hGlobal,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Parámetros

*cfFormat*<br/>
El formato de Portapapeles en el que se ofrecerá los datos. Este parámetro puede ser uno de los formatos de Portapapeles predefinidos o el valor devuelto por el Windows nativo [RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata) función.

*hGlobal*<br/>
Identificador del bloque de memoria global que contiene los datos en el formato especificado.

*lpFormatEtc*<br/>
Apunta a un [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) estructura que describe el formato en el que se les ofrecerá los datos. Proporcionar un valor para este parámetro si desea especificar información de formato adicionales más allá del formato de Portapapeles especificado por *cfFormat*. Si es NULL, se usan los valores predeterminados para los demás campos en el `FORMATETC` estructura.

### <a name="remarks"></a>Comentarios

Esta función proporciona los datos mediante la representación de inmediato, por lo que debe suministrar los datos al llamar a la función; los datos se almacena en caché hasta que sea necesario. Use el `CacheData` función de miembro si se proporciona una gran cantidad de datos o si requiere un medio de almacenamiento estructurado.

Para usar la representación aplazada, llame a la [DelayRenderData](#delayrenderdata) o [DelayRenderFileData](#delayrenderfiledata) función miembro. Para obtener más información sobre la representación aplazada como controlado por MFC, vea el artículo [objetos de datos y orígenes de datos: Manipulación](../../mfc/data-objects-and-data-sources-manipulation.md).

Para obtener más información, consulte el [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) estructura en el SDK de Windows.

Para obtener más información, consulte [RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata) en el SDK de Windows.

##  <a name="coledatasource"></a>  COleDataSource::COleDataSource

Construye un objeto `COleDataSource`.

```
COleDataSource();
```

##  <a name="delayrenderdata"></a>  COleDataSource::DelayRenderData

Llame a esta función para especificar un formato en el que datos se ofrezcan durante los datos de las operaciones de transferencia.

```
void DelayRenderData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Parámetros

*cfFormat*<br/>
El formato de Portapapeles en el que se ofrecerá los datos. Este parámetro puede ser uno de los formatos de Portapapeles predefinidos o el valor devuelto por el Windows nativo [RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata) función.

*lpFormatEtc*<br/>
Apunta a un [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) estructura que describe el formato en el que se les ofrecerá los datos. Proporcionar un valor para este parámetro si desea especificar información de formato adicionales más allá del formato de Portapapeles especificado por *cfFormat*. Si es NULL, se usan los valores predeterminados para los demás campos en el `FORMATETC` estructura.

### <a name="remarks"></a>Comentarios

Esta función proporciona los datos con representación retrasada, de modo que los datos no se proporcionan inmediatamente. El [OnRenderData](#onrenderdata) o [OnRenderGlobalData](#onrenderglobaldata) función miembro se llama para solicitar los datos.

Use esta función si no va a proporcionar los datos a través de un `CFile` objeto. Si va a proporcionar los datos a través de un `CFile` de objeto, llame a la [DelayRenderFileData](#delayrenderfiledata) función miembro. Para obtener más información sobre la representación aplazada como controlado por MFC, vea el artículo [objetos de datos y orígenes de datos: Manipulación](../../mfc/data-objects-and-data-sources-manipulation.md).

Para utilizar procesamiento inmediato, llame a la [CacheData](#cachedata) o [CacheGlobalData](#cacheglobaldata) función miembro.

Para obtener más información, consulte el [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) estructura en el SDK de Windows.

Para obtener más información, consulte [RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata) en el SDK de Windows.

##  <a name="delayrenderfiledata"></a>  COleDataSource::DelayRenderFileData

Llame a esta función para especificar un formato en el que datos se ofrezcan durante los datos de las operaciones de transferencia.

```
void DelayRenderFileData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Parámetros

*cfFormat*<br/>
El formato de Portapapeles en el que se ofrecerá los datos. Este parámetro puede ser uno de los formatos de Portapapeles predefinidos o el valor devuelto por el Windows nativo [RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata) función.

*lpFormatEtc*<br/>
Apunta a un [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) estructura que describe el formato en el que se les ofrecerá los datos. Proporcionar un valor para este parámetro si desea especificar información de formato adicionales más allá del formato de Portapapeles especificado por *cfFormat*. Si es NULL, se usan los valores predeterminados para los demás campos en el `FORMATETC` estructura.

### <a name="remarks"></a>Comentarios

Esta función proporciona los datos con representación retrasada, de modo que los datos no se proporcionan inmediatamente. El [OnRenderFileData](#onrenderfiledata) función miembro se llama para solicitar los datos.

Use esta función si va a usar un `CFile` objeto para proporcionar los datos. Si no va a usar un `CFile` de objeto, llame a la [DelayRenderData](#delayrenderdata) función miembro. Para obtener más información sobre la representación aplazada como controlado por MFC, vea el artículo [objetos de datos y orígenes de datos: Manipulación](../../mfc/data-objects-and-data-sources-manipulation.md).

Para utilizar procesamiento inmediato, llame a la [CacheData](#cachedata) o [CacheGlobalData](#cacheglobaldata) función miembro.

Para obtener más información, consulte el [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) estructura en el SDK de Windows.

Para obtener más información, consulte [RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata) en el SDK de Windows.

##  <a name="delaysetdata"></a>  COleDataSource::DelaySetData

Llame a esta función para admitir el cambio del contenido del origen de datos.

```
void DelaySetData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Parámetros

*cfFormat*<br/>
El formato del Portapapeles en el que los datos consiste en colocar. Este parámetro puede ser uno de los formatos de Portapapeles predefinidos o el valor devuelto por el Windows nativo [RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata) función.

*lpFormatEtc*<br/>
Apunta a un [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) estructura que describe el formato en el que se reemplazará los datos. Proporcionar un valor para este parámetro si desea especificar información de formato adicionales más allá del formato de Portapapeles especificado por *cfFormat*. Si es NULL, se usan los valores predeterminados para los demás campos en el `FORMATETC` estructura.

### <a name="remarks"></a>Comentarios

[OnSetData](#onsetdata) se llamará el marco de trabajo cuando esto sucede. Solo se usa el marco de trabajo que devuelve el origen de datos de [COleServerItem::GetDataSource](../../mfc/reference/coleserveritem-class.md#getdatasource). Si `DelaySetData` no se llama a su `OnSetData` nunca se llamará la función. `DelaySetData` debe llamarse para cada Portapapeles o `FORMATETC` compatibilidad con el formato.

Para obtener más información, consulte el [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) estructura en el SDK de Windows.

Para obtener más información, consulte [RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata) en el SDK de Windows.

##  <a name="dodragdrop"></a>  COleDataSource::DoDragDrop

Llame a la `DoDragDrop` función miembro para realizar una operación de arrastrar y colocar para este origen de datos, normalmente en un [CWnd::OnLButtonDown](../../mfc/reference/cwnd-class.md#onlbuttondown) controlador.

```
DROPEFFECT DoDragDrop(
    DWORD dwEffects = DROPEFFECT_COPY|DROPEFFECT_MOVE|DROPEFFECT_LINK,
    LPCRECT lpRectStartDrag = NULL,
    COleDropSource* pDropSource = NULL);
```

### <a name="parameters"></a>Parámetros

*dwEffects*<br/>
Operaciones de arrastrar y colocar que se permiten en este origen de datos. Puede ser uno o varios de los siguientes:

- DROPEFFECT_COPY se pudo realizar una operación de copia.

- DROPEFFECT_MOVE se pudo realizar una operación de movimiento.

- Se puede establecer el vínculo de un DROPEFFECT_LINK de los datos colocados en los datos originales.

- DROPEFFECT_SCROLL indica que se puede producir una operación de desplazamiento de arrastre.

*lpRectStartDrag*<br/>
Puntero al rectángulo que define el donde realmente comienza la operación de arrastrar. Para obtener más información, vea la sección Comentarios que se muestra más adelante.

*pDropSource*<br/>
Apunta a un origen de colocación. Si es NULL, a continuación, una implementación predeterminada de [COleDropSource](../../mfc/reference/coledropsource-class.md) se usará.

### <a name="return-value"></a>Valor devuelto

Efecto generado por la operación de arrastrar y colocar; paralela DROPEFFECT_NONE en caso contrario, si nunca se comienza la operación porque el usuario suelta el botón del mouse antes de abandonar el rectángulo proporcionado.

### <a name="remarks"></a>Comentarios

No se inicie inmediatamente la operación de arrastrar y colocar. Espera hasta que el cursor del mouse sale del rectángulo especificado por *lpRectStartDrag* o hasta que un número especificado de milisegundos que ha pasado. Si *lpRectStartDrag* es NULL, el tamaño del rectángulo es un píxel.

El tiempo de retraso especificado por un valor de clave del registro. Puede cambiar el tiempo de retraso mediante una llamada a [CWinApp::WriteProfileString](../../mfc/reference/cwinapp-class.md#writeprofilestring) o [CWinApp:: Writeprofileint](../../mfc/reference/cwinapp-class.md#writeprofileint). Si no especifica el tiempo de retraso, se usa el valor predeterminado es 200 milisegundos. Tiempo de retraso de arrastre se almacena como sigue:

- Tiempo de retraso de arrastre de Windows NT se almacena en HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\NT\CurrentVersion\IniFileMapping\win.ini\Windows\DragDelay.

- Retrasar hora de Windows 3.x arrastrar se almacena en el archivo WIN. Archivo INI, la sección [Windows}.

- Tiempo de retraso de arrastre de Windows 95/98 se almacena en una versión en caché de WIN. INI.

Para obtener más información acerca de cómo arrastrar se almacena información sobre los retrasos en el registro o el. Archivo INI, consulte [WriteProfileString](/windows/desktop/api/winbase/nf-winbase-writeprofilestringa) en el SDK de Windows.

Para obtener más información, vea el artículo [arrastrar y colocar: Implementación de un origen de colocación](../../mfc/drag-and-drop-implementing-a-drop-source.md).

##  <a name="empty"></a>  COleDataSource::Empty

Llame a esta función para vaciar el `COleDataSource` objeto de datos.

```
void Empty();
```

### <a name="remarks"></a>Comentarios

Ambos se almacenan en caché y formatos de representación de retraso se vacía por lo que puede volver a usar.

Para obtener más información, consulte [ReleaseStgMedium](/windows/desktop/api/ole2/nf-ole2-releasestgmedium) en el SDK de Windows.

##  <a name="flushclipboard"></a>  COleDataSource::FlushClipboard

Representa los datos que se encuentra en el Portapapeles y, a continuación, le permite pegar datos del Portapapeles después de que se cierra la aplicación.

```
static void PASCAL FlushClipboard();
```

### <a name="remarks"></a>Comentarios

Use [SetClipboard](#setclipboard) para colocar datos en el Portapapeles.

##  <a name="getclipboardowner"></a>  COleDataSource::GetClipboardOwner

Determina si los datos en el Portapapeles ha cambiado desde [SetClipboard](#setclipboard) por última vez y, si es así, identifica al propietario actual.

```
static COleDataSource* PASCAL GetClipboardOwner();
```

### <a name="return-value"></a>Valor devuelto

Los datos de origen actualmente en el Portapapeles, o NULL si no hay nada en el Portapapeles o si el Portapapeles no pertenece a la aplicación que realiza la llamada.

##  <a name="onrenderdata"></a>  COleDataSource::OnRenderData

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

El formato especificado es una colocado anteriormente en el `COleDataSource` objeto utilizando el [DelayRenderData](#delayrenderdata) o [DelayRenderFileData](#delayrenderfiledata) función miembro para la representación aplazada. La implementación predeterminada de esta función llamará [OnRenderFileData](#onrenderfiledata) o [OnRenderGlobalData](#onrenderglobaldata) si el medio de almacenamiento proporcionado es un archivo o la memoria, respectivamente. Si se proporciona ninguno de estos formatos, a continuación, la implementación predeterminada devolverá 0 y no hacer nada. Para obtener más información sobre la representación aplazada como controlado por MFC, vea el artículo [objetos de datos y orígenes de datos: Manipulación](../../mfc/data-objects-and-data-sources-manipulation.md).

Si *lpStgMedium*-> *tymed* es TYMED_NULL, el `STGMEDIUM` debe ser asignado y rellenado según lo especificado por *lpFormatEtc -> tymed*. Si no es TYMED_NULL, el `STGMEDIUM` debe rellenarse en lugar de con los datos.

Esto es un avanzado que se puede invalidar. Reemplace esta función para proporcionar los datos en el formato solicitado y medio. Dependiendo de los datos, puede reemplazar una de las otras versiones de esta función en su lugar. Si los datos están pequeño y un tamaño fijo, invalidar `OnRenderGlobalData`. Si los datos están en un archivo o es de tamaño variable, invalidar `OnRenderFileData`.

Para obtener más información, consulte el [STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium) y [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) estructuras, la [TYMED](/windows/desktop/api/objidl/ne-objidl-tagtymed) tipo de enumeración, y [IDataObject:: GetData](/windows/desktop/api/objidl/nf-objidl-idataobject-getdata) en el SDK de Windows.

##  <a name="onrenderfiledata"></a>  COleDataSource::OnRenderFileData

Lo llama el marco de trabajo para recuperar los datos en el formato especificado cuando el medio de almacenamiento especificado es un archivo.

```
virtual BOOL OnRenderFileData(
    LPFORMATETC lpFormatEtc,
    CFile* pFile);
```

### <a name="parameters"></a>Parámetros

*lpFormatEtc*<br/>
Apunta a la [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) estructura que especifica el formato en el que se solicita información.

*pFile*<br/>
Apunta a un [CFile](../../mfc/reference/cfile-class.md) objeto en el que se va a representar los datos.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

El formato especificado es una colocado anteriormente en el `COleDataSource` objeto utilizando el [DelayRenderData](#delayrenderdata) función miembro para la representación aplazada. La implementación predeterminada de esta función simplemente devuelve FALSE.

Esto es un avanzado que se puede invalidar. Reemplace esta función para proporcionar los datos en el formato solicitado y medio. Dependiendo de los datos, puede reemplazar una de las otras versiones de esta función en su lugar. Si desea controlar varios medios de almacenamiento, reemplace [OnRenderData](#onrenderdata). Si los datos están en un archivo o es de tamaño variable, invalidar `OnRenderFileData`. Para obtener más información sobre la representación aplazada como controlado por MFC, vea el artículo [objetos de datos y orígenes de datos: Manipulación](../../mfc/data-objects-and-data-sources-manipulation.md).

Para obtener más información, consulte el [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) estructura y [IDataObject:: GetData](/windows/desktop/api/objidl/nf-objidl-idataobject-getdata) en el SDK de Windows.

##  <a name="onrenderglobaldata"></a>  COleDataSource::OnRenderGlobalData

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
Apunta a un identificador de la memoria global en el que los datos son va a devolver. Si uno no se ha asignado todavía, este parámetro puede ser NULL.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

El formato especificado es una colocado anteriormente en el `COleDataSource` objeto utilizando el [DelayRenderData](#delayrenderdata) función miembro para la representación aplazada. La implementación predeterminada de esta función simplemente devuelve FALSE.

Si *phGlobal* es NULL, entonces debe asignado y devueltos en un nuevo HGLOBAL *phGlobal*. En caso contrario, el HGLOBAL especificado por *phGlobal* debe rellenarse con los datos. La cantidad de datos colocados en HGLOBAL no puede superar el tamaño actual del bloque de memoria. Además, el bloque no se puede reasignar a un tamaño mayor.

Esto es un avanzado que se puede invalidar. Reemplace esta función para proporcionar los datos en el formato solicitado y medio. Dependiendo de los datos, puede reemplazar una de las otras versiones de esta función en su lugar. Si desea controlar varios medios de almacenamiento, reemplace [OnRenderData](#onrenderdata). Si los datos están en un archivo o es de tamaño variable, invalidar [OnRenderFileData](#onrenderfiledata). Para obtener más información sobre la representación aplazada como controlado por MFC, vea el artículo [objetos de datos y orígenes de datos: Manipulación](../../mfc/data-objects-and-data-sources-manipulation.md).

Para obtener más información, consulte el [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) estructura y [IDataObject:: GetData](/windows/desktop/api/objidl/nf-objidl-idataobject-getdata) en el SDK de Windows.

##  <a name="onsetdata"></a>  COleDataSource::OnSetData

Lo llama el marco para establecer o reemplazar los datos de la `COleDataSource` objeto en el formato especificado.

```
virtual BOOL OnSetData(
    LPFORMATETC lpFormatEtc,
    LPSTGMEDIUM lpStgMedium,
    BOOL bRelease);
```

### <a name="parameters"></a>Parámetros

*lpFormatEtc*<br/>
Apunta a la [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) estructura que especifica el formato en el que se va a reemplazar los datos.

*lpStgMedium*<br/>
Apunta a la [STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium) estructura que contiene los datos que va a reemplazar el contenido actual de la `COleDataSource` objeto.

*bRelease*<br/>
Indica que posee el medio de almacenamiento después de completar la llamada de función. El llamador decide quién es responsable de liberar los recursos asignados en nombre del medio de almacenamiento. El llamador para ello, establezca *bRelease*. Si *bRelease* es distinto de cero, el origen de datos toma la propiedad, liberar el medio cuando haya terminado de usarlo. Cuando *bRelease* es 0, el llamador conserva la propiedad y el origen de datos puede utilizar el medio de almacenamiento solo para la duración de la llamada.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

El origen de datos no tomar posesión de los datos hasta que obtuvo correctamente. Es decir, no tiene la propiedad si `OnSetData` devuelve 0. Si el origen de datos toma posesión, libera el medio de almacenamiento mediante una llamada a la [ReleaseStgMedium](/windows/desktop/api/ole2/nf-ole2-releasestgmedium) función.

La implementación predeterminada no hace nada. Reemplace esta función para reemplazar los datos en el formato especificado. Esto es un avanzado que se puede invalidar.

Para obtener más información, consulte el [STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium) y [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) estructuras y los [ReleaseStgMedium](/windows/desktop/api/ole2/nf-ole2-releasestgmedium) y [IDataObject:: GetData](/windows/desktop/api/objidl/nf-objidl-idataobject-getdata) funciones en el SDK de Windows.

##  <a name="setclipboard"></a>  COleDataSource::SetClipboard

Coloca los datos contenidos en la `COleDataSource` objeto en el Portapapeles después de llamar a una de las funciones siguientes: [CacheData](#cachedata), [CacheGlobalData](#cacheglobaldata), [DelayRenderData](#delayrenderdata), o [DelayRenderFileData](#delayrenderfiledata).

```
void SetClipboard();
```

## <a name="see-also"></a>Vea también

[Ejemplo HIERSVR](../../visual-cpp-samples.md)<br/>
[Ejemplo MFC OCLIENT](../../visual-cpp-samples.md)<br/>
[CCmdTarget (clase)](../../mfc/reference/ccmdtarget-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[COleDataObject (clase)](../../mfc/reference/coledataobject-class.md)
