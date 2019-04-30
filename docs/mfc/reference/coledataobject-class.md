---
title: COleDataObject (clase)
ms.date: 11/04/2016
f1_keywords:
- COleDataObject
- AFXOLE/COleDataObject
- AFXOLE/COleDataObject::COleDataObject
- AFXOLE/COleDataObject::Attach
- AFXOLE/COleDataObject::AttachClipboard
- AFXOLE/COleDataObject::BeginEnumFormats
- AFXOLE/COleDataObject::Detach
- AFXOLE/COleDataObject::GetData
- AFXOLE/COleDataObject::GetFileData
- AFXOLE/COleDataObject::GetGlobalData
- AFXOLE/COleDataObject::GetNextFormat
- AFXOLE/COleDataObject::IsDataAvailable
- AFXOLE/COleDataObject::Release
helpviewer_keywords:
- COleDataObject [MFC], COleDataObject
- COleDataObject [MFC], Attach
- COleDataObject [MFC], AttachClipboard
- COleDataObject [MFC], BeginEnumFormats
- COleDataObject [MFC], Detach
- COleDataObject [MFC], GetData
- COleDataObject [MFC], GetFileData
- COleDataObject [MFC], GetGlobalData
- COleDataObject [MFC], GetNextFormat
- COleDataObject [MFC], IsDataAvailable
- COleDataObject [MFC], Release
ms.assetid: d1cc84be-2e1c-4bb3-a8a0-565eb08aaa34
ms.openlocfilehash: 24d79c684226d57839161946255781c3bdd5a043
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "64341701"
---
# <a name="coledataobject-class"></a>COleDataObject (clase)

Se utiliza en las transferencias de datos para recuperar datos en diferentes formatos del Portapapeles, mediante arrastrar y colocar o a partir de un elemento OLE incrustado.

## <a name="syntax"></a>Sintaxis

```
class COleDataObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[COleDataObject::COleDataObject](#coledataobject)|Construye un objeto `COleDataObject`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[COleDataObject::Attach](#attach)|Asocia el objeto de datos OLE especificado en el `COleDataObject`.|
|[COleDataObject::AttachClipboard](#attachclipboard)|Asocia el objeto de datos que se encuentra en el Portapapeles.|
|[COleDataObject::BeginEnumFormats](#beginenumformats)|Se prepara para uno o más subsiguiente `GetNextFormat` llamadas.|
|[COleDataObject::Detach](#detach)|Desasocia asociado `IDataObject` objeto.|
|[COleDataObject::GetData](#getdata)|Copia datos desde el objeto de datos OLE adjunto en un formato especificado.|
|[COleDataObject::GetFileData](#getfiledata)|Copia datos desde el objeto de datos OLE adjunto en un `CFile` puntero en el formato especificado.|
|[COleDataObject::GetGlobalData](#getglobaldata)|Copia datos desde el objeto de datos OLE adjunto en un `HGLOBAL` con el formato especificado.|
|[COleDataObject::GetNextFormat](#getnextformat)|Devuelve el siguiente formato de datos disponible.|
|[COleDataObject::IsDataAvailable](#isdataavailable)|Comprueba si los datos están disponibles en un formato especificado.|
|[COleDataObject::Release](#release)|Desconecta y libera asociado `IDataObject` objeto.|

## <a name="remarks"></a>Comentarios

`COleDataObject` no tiene una clase base.

Estos tipos de transferencias de datos incluyen un origen y un destino. El origen de datos se implementa como un objeto de la [COleDataSource](../../mfc/reference/coledatasource-class.md) clase. Cada vez que una aplicación de destino tiene datos que se colocan en él o se le solicitará que realice una operación de pegar desde el Portapapeles, un objeto de la `COleDataObject` debe crearse la clase.

Esta clase le permite determinar si los datos existen en un formato especificado. Puede también para enumerar los formatos de datos disponibles o comprobar si un formato determinado está disponible y, a continuación, recuperar los datos en el formato preferido. Recuperación de objetos puede realizarse de varias maneras diferentes, incluido el uso de un [CFile](../../mfc/reference/cfile-class.md), un HGLOBAL o un `STGMEDIUM` estructura.

Para obtener más información, consulte el [STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium) estructura en el SDK de Windows.

Para obtener más información sobre el uso de objetos de datos en la aplicación, consulte el artículo [objetos de datos y orígenes de datos (OLE)](../../mfc/data-objects-and-data-sources-ole.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`COleDataObject`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxole.h

##  <a name="attach"></a>  COleDataObject::Attach

Llame a esta función para asociar el `COleDataObject` objeto con un objeto de datos OLE.

```
void Attach(
    LPDATAOBJECT lpDataObject,
    BOOL bAutoRelease = TRUE);
```

### <a name="parameters"></a>Parámetros

*lpDataObject*<br/>
Apunta a un objeto de datos OLE.

*bAutoRelease*<br/>
TRUE si el objeto de datos OLE debe estar publicado cuando la `COleDataObject` objeto se destruye; de lo contrario, FALSE.

### <a name="remarks"></a>Comentarios

Para obtener más información, consulte [IDataObject](/windows/desktop/api/objidl/nn-objidl-idataobject) en el SDK de Windows.

##  <a name="attachclipboard"></a>  COleDataObject::AttachClipboard

Llame a esta función para asociar el objeto de datos que se encuentra actualmente en el Portapapeles para el `COleDataObject` objeto.

```
BOOL AttachClipboard();
```

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

> [!NOTE]
>  Llamar a esta función bloquea el Portapapeles hasta que se publique este objeto de datos. El objeto de datos que se publica en el destructor para la `COleDataObject`. Para obtener más información, consulte [llamar a OpenClipboard](/windows/desktop/api/winuser/nf-winuser-openclipboard) y [CloseClipboard](/windows/desktop/api/winuser/nf-winuser-closeclipboard) en la documentación de Win32.

##  <a name="beginenumformats"></a>  COleDataObject::BeginEnumFormats

Llame a esta función para prepararse para las llamadas subsiguientes a `GetNextFormat` para recuperar una lista de formatos de datos desde el elemento.

```
void BeginEnumFormats();
```

### <a name="remarks"></a>Comentarios

Después de llamar a `BeginEnumFormats`, se almacena la posición del primer formato admitido por este objeto de datos. Las llamadas sucesivas a `GetNextFormat` enumerará la lista de formatos disponibles en el objeto de datos.

Para comprobar la disponibilidad de datos en un formato determinado, utilice [COleDataObject:: IsDataAvailable](#isdataavailable).

Para obtener más información, consulte [IDataObject:: EnumFormatEtc](/windows/desktop/api/objidl/nf-objidl-idataobject-enumformatetc) en el SDK de Windows.

##  <a name="coledataobject"></a>  COleDataObject::COleDataObject

Construye un objeto `COleDataObject`.

```
COleDataObject();
```

### <a name="remarks"></a>Comentarios

Una llamada a [COleDataObject::Attach](#attach) o [COleDataObject::AttachClipboard](#attachclipboard) deben realizarse antes de llamar a otro `COleDataObject` funciones.

> [!NOTE]
>  Dado que uno de los parámetros a los controladores de arrastrar y colocar es un puntero a un `COleDataObject`, no hay ninguna necesidad de llamar a este constructor para la compatibilidad con arrastrar y colocar.

##  <a name="detach"></a>  COleDataObject::Detach

Llame a esta función para desasociar el `COleDataObject` objeto de su objeto de datos OLE asociado sin liberar el objeto de datos.

```
LPDATAOBJECT Detach();
```

### <a name="return-value"></a>Valor devuelto

Un puntero al objeto de datos OLE que se ha separado.

### <a name="remarks"></a>Comentarios

##  <a name="getdata"></a>  COleDataObject::GetData

Llame a esta función para recuperar datos desde el elemento en el formato especificado.

```
BOOL GetData(
    CLIPFORMAT cfFormat,
    LPSTGMEDIUM lpStgMedium,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Parámetros

*cfFormat*<br/>
El formato en el que se devolverán datos. Este parámetro puede ser uno de los formatos de Portapapeles predefinidos o el valor devuelto por el Windows nativo [RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata) función.

*lpStgMedium*<br/>
Apunta a un [STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium) estructura que recibirá los datos.

*lpFormatEtc*<br/>
Apunta a un [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) estructura que describe el formato en el que se devolverán datos. Proporcionar un valor para este parámetro si desea especificar información de formato adicionales más allá del formato de Portapapeles especificado por *cfFormat*. Si es NULL, se usan los valores predeterminados para los demás campos en el `FORMATETC` estructura.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Para obtener más información, consulte [IDataObject:: GetData](/windows/desktop/api/objidl/nf-objidl-idataobject-getdata), [STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium), y [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) en el SDK de Windows.

Para obtener más información, consulte [RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata) en el SDK de Windows.

##  <a name="getfiledata"></a>  COleDataObject::GetFileData

Llame a esta función para crear un `CFile` o `CFile`-objeto derivado y recuperar datos en el formato especificado en un `CFile` puntero.

```
CFile* GetFileData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Parámetros

*cfFormat*<br/>
El formato en el que se devolverán datos. Este parámetro puede ser uno de los formatos de Portapapeles predefinidos o el valor devuelto por el Windows nativo [RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata) función.

*lpFormatEtc*<br/>
Apunta a un [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) estructura que describe el formato en el que se devolverán datos. Proporcionar un valor para este parámetro si desea especificar información de formato adicionales más allá del formato de Portapapeles especificado por *cfFormat*. Si es NULL, se usan los valores predeterminados para los demás campos en el `FORMATETC` estructura.

### <a name="return-value"></a>Valor devuelto

Puntero a la nueva `CFile` o `CFile`-derivados de objeto que contiene los datos si es correcto; de lo contrario, NULL.

### <a name="remarks"></a>Comentarios

Según el medio de los datos se almacenan en el tipo real que apunta el valor devuelto puede ser `CFile`, `CSharedFile`, o `COleStreamFile`.

> [!NOTE]
>  La `CFile` objeto acceder por el valor devuelto de esta función es propiedad del llamador. Es responsabilidad del llamador **eliminar** el `CFile` objeto, con lo que se cierre el archivo.

Para obtener más información, consulte [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) en el SDK de Windows.

Para obtener más información, consulte [RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata) en el SDK de Windows.

##  <a name="getglobaldata"></a>  COleDataObject::GetGlobalData

Llame a esta función para asignar un bloque de memoria global y para recuperar datos en el formato especificado en un HGLOBAL.

```
HGLOBAL GetGlobalData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Parámetros

*cfFormat*<br/>
El formato en el que se devolverán datos. Este parámetro puede ser uno de los formatos de Portapapeles predefinidos o el valor devuelto por el Windows nativo [RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata) función.

*lpFormatEtc*<br/>
Apunta a un [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) estructura que describe el formato en el que se devolverán datos. Proporcionar un valor para este parámetro si desea especificar información de formato adicionales más allá del formato de Portapapeles especificado por *cfFormat*. Si es NULL, se usan los valores predeterminados para los demás campos en el `FORMATETC` estructura.

### <a name="return-value"></a>Valor devuelto

El identificador del bloque de memoria global que contiene los datos si se realiza correctamente; en caso contrario, es NULL.

### <a name="remarks"></a>Comentarios

Para obtener más información, consulte [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) en el SDK de Windows.

Para obtener más información, consulte [RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata) en el SDK de Windows.

##  <a name="getnextformat"></a>  COleDataObject::GetNextFormat

Llame a esta función varias veces para obtener todos los formatos disponibles para recuperar datos desde el elemento.

```
BOOL GetNextFormat(LPFORMATETC lpFormatEtc);
```

### <a name="parameters"></a>Parámetros

*lpFormatEtc*<br/>
Apunta a la [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) estructura que recibe la información de formato cuando finaliza la llamada de función.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si está disponible; otro formato en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Después de llamar a [COleDataObject:: BeginEnumFormats](#beginenumformats), se almacena la posición del primer formato admitido por este objeto de datos. Las llamadas sucesivas a `GetNextFormat` enumerará la lista de formatos disponibles en el objeto de datos. Use estas funciones para enumerar los formatos disponibles.

Para comprobar la disponibilidad de un formato determinado, llame a [COleDataObject:: IsDataAvailable](#isdataavailable).

Para obtener más información, consulte [IEnumXXXX::Next](https://msdn.microsoft.com/library/ms695273.aspx) en el SDK de Windows.

##  <a name="isdataavailable"></a>  COleDataObject::IsDataAvailable

Llame a esta función para determinar si un formato determinado está disponible para recuperar datos desde el elemento OLE.

```
BOOL IsDataAvailable(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Parámetros

*cfFormat*<br/>
El formato de datos del Portapapeles para su uso en la estructura que señala *lpFormatEtc*. Este parámetro puede ser uno de los formatos de Portapapeles predefinidos o el valor devuelto por el Windows nativo [RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata) función.

*lpFormatEtc*<br/>
Apunta a un [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) estructura que describe el formato deseado. Proporcionar un valor para este parámetro solo si desea especificar información de formato adicionales más allá del formato de Portapapeles especificado por *cfFormat*. Si es NULL, se usan los valores predeterminados para los demás campos en el `FORMATETC` estructura.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si los datos están disponibles en el formato especificado; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Esta función resulta útil antes de llamar a `GetData`, `GetFileData`, o `GetGlobalData`.

Para obtener más información, consulte [IDataObject:: QueryGetData](/windows/desktop/api/objidl/nf-objidl-idataobject-querygetdata) y [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) en el SDK de Windows.

Para obtener más información, consulte [RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata) en el SDK de Windows.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CRichEditView::QueryAcceptData](../../mfc/reference/cricheditview-class.md#queryacceptdata).

##  <a name="release"></a>  COleDataObject::Release

Llame a esta función para liberar la propiedad de la [IDataObject](/windows/desktop/api/objidl/nn-objidl-idataobject) objeto que estaba asociado previamente el `COleDataObject` objeto.

```
void Release();
```

### <a name="remarks"></a>Comentarios

El `IDataObject` asoció la `COleDataObject` mediante una llamada a `Attach` o `AttachClipboard` explícitamente o el marco de trabajo. Si el *bAutoRelease* parámetro de `Attach` es FALSE, el `IDataObject` no se publicará el objeto. En este caso, el llamador es responsable de liberar el `IDataObject` mediante una llamada a [IUnknown:: Release](/windows/desktop/api/unknwn/nf-unknwn-iunknown-release).

## <a name="see-also"></a>Vea también

[Ejemplo HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[Ejemplo MFC OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[COleDataSource (clase)](../../mfc/reference/coledatasource-class.md)<br/>
[COleClientItem (clase)](../../mfc/reference/coleclientitem-class.md)<br/>
[COleServerItem (clase)](../../mfc/reference/coleserveritem-class.md)
