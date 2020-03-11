---
title: Clase COleDataObject
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
ms.openlocfilehash: e706489a84ad564949e2c2d3d193173fc19b9828
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78883675"
---
# <a name="coledataobject-class"></a>Clase COleDataObject

Se utiliza en las transferencias de datos para recuperar datos en diferentes formatos del Portapapeles, mediante arrastrar y colocar o a partir de un elemento OLE incrustado.

## <a name="syntax"></a>Sintaxis

```
class COleDataObject
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[COleDataObject::COleDataObject](#coledataobject)|Construye un objeto `COleDataObject`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[COleDataObject:: Attach](#attach)|Adjunta el objeto de datos OLE especificado al `COleDataObject`.|
|[COleDataObject::AttachClipboard](#attachclipboard)|Adjunta el objeto de datos que se encuentra en el portapapeles.|
|[COleDataObject::BeginEnumFormats](#beginenumformats)|Prepara para una o varias llamadas de `GetNextFormat` posteriores.|
|[COleDataObject::D Etach](#detach)|Desasocia el objeto de `IDataObject` asociado.|
|[COleDataObject:: GetData](#getdata)|Copia datos del objeto de datos OLE adjunto en un formato especificado.|
|[COleDataObject::GetFileData](#getfiledata)|Copia datos del objeto de datos OLE adjunto en un puntero `CFile` en el formato especificado.|
|[COleDataObject::GetGlobalData](#getglobaldata)|Copia los datos del objeto de datos OLE adjunto en un `HGLOBAL` en el formato especificado.|
|[COleDataObject::GetNextFormat](#getnextformat)|Devuelve el siguiente formato de datos disponible.|
|[COleDataObject::IsDataAvailable](#isdataavailable)|Comprueba si los datos están disponibles en un formato especificado.|
|[COleDataObject:: Release](#release)|Desasocia y libera el objeto de `IDataObject` asociado.|

## <a name="remarks"></a>Observaciones

`COleDataObject` no tiene una clase base.

Estos tipos de transferencias de datos incluyen un origen y un destino. El origen de datos se implementa como un objeto de la clase [COleDataSource](../../mfc/reference/coledatasource-class.md) . Cada vez que una aplicación de destino tiene datos quitados o se le pide que realice una operación de pegar desde el portapapeles, se debe crear un objeto de la clase `COleDataObject`.

Esta clase permite determinar si los datos existen en un formato especificado. También puede enumerar los formatos de datos disponibles o comprobar si un formato determinado está disponible y, a continuación, recuperar los datos en el formato preferido. La recuperación de objetos se puede realizar de varias maneras diferentes, como el uso de un objeto [CFile](../../mfc/reference/cfile-class.md), hglobal o una estructura `STGMEDIUM`.

Para obtener más información, vea la estructura [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) en el Windows SDK.

Para obtener más información sobre el uso de objetos de datos en la aplicación, vea el artículo objetos de datos [y orígenes de datos (OLE)](../../mfc/data-objects-and-data-sources-ole.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`COleDataObject`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxole. h

##  <a name="attach"></a>COleDataObject:: Attach

Llame a esta función para asociar el objeto `COleDataObject` a un objeto de datos OLE.

```
void Attach(
    LPDATAOBJECT lpDataObject,
    BOOL bAutoRelease = TRUE);
```

### <a name="parameters"></a>Parámetros

*lpDataObject*<br/>
Apunta a un objeto de datos OLE.

*bAutoRelease*<br/>
TRUE si se debe liberar el objeto de datos OLE cuando se destruye el objeto de `COleDataObject`; en caso contrario, FALSE.

### <a name="remarks"></a>Observaciones

Para obtener más información, vea [IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject) en el Windows SDK.

##  <a name="attachclipboard"></a>COleDataObject::AttachClipboard

Llame a esta función para adjuntar al objeto `COleDataObject` el objeto de datos que se encuentra actualmente en el portapapeles.

```
BOOL AttachClipboard();
```

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

> [!NOTE]
>  La llamada a esta función bloquea el Portapapeles hasta que este objeto de datos se libera. El objeto de datos se libera en el destructor del `COleDataObject`. Para obtener más información, vea [OpenClipboard](/windows/win32/api/winuser/nf-winuser-openclipboard) y [CloseClipboard](/windows/win32/api/winuser/nf-winuser-closeclipboard) en la documentación de Win32.

##  <a name="beginenumformats"></a>COleDataObject::BeginEnumFormats

Llame a esta función para preparar las llamadas posteriores a `GetNextFormat` para recuperar una lista de formatos de datos del elemento.

```
void BeginEnumFormats();
```

### <a name="remarks"></a>Observaciones

Después de una llamada a `BeginEnumFormats`, se almacena la posición del primer formato admitido por este objeto de datos. Las llamadas sucesivas a `GetNextFormat` enumerarán la lista de formatos disponibles en el objeto de datos.

Para comprobar la disponibilidad de los datos en un formato determinado, use [COleDataObject:: IsDataAvailable](#isdataavailable).

Para obtener más información, vea [IDataObject:: del EnumFormatEtc](/windows/win32/api/objidl/nf-objidl-idataobject-enumformatetc) en el Windows SDK.

##  <a name="coledataobject"></a>COleDataObject::COleDataObject

Construye un objeto `COleDataObject`.

```
COleDataObject();
```

### <a name="remarks"></a>Observaciones

Se debe realizar una llamada a [COleDataObject:: Attach](#attach) o [COleDataObject:: AttachClipboard](#attachclipboard) antes de llamar a otras funciones de `COleDataObject`.

> [!NOTE]
>  Dado que uno de los parámetros de los controladores de arrastrar y colocar es un puntero a un `COleDataObject`, no es necesario llamar a este constructor para admitir la función de arrastrar y colocar.

##  <a name="detach"></a>COleDataObject::D Etach

Llame a esta función para separar el objeto de `COleDataObject` de su objeto de datos OLE asociado sin liberar el objeto de datos.

```
LPDATAOBJECT Detach();
```

### <a name="return-value"></a>Valor devuelto

Puntero al objeto de datos OLE que se desconectó.

### <a name="remarks"></a>Observaciones

##  <a name="getdata"></a>COleDataObject:: GetData

Llame a esta función para recuperar los datos del elemento en el formato especificado.

```
BOOL GetData(
    CLIPFORMAT cfFormat,
    LPSTGMEDIUM lpStgMedium,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Parámetros

*cfFormat*<br/>
Formato en el que se van a devolver los datos. Este parámetro puede ser uno de los formatos predefinidos del portapapeles o el valor devuelto por la función [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) nativa de Windows.

*lpStgMedium*<br/>
Apunta a una estructura [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) que recibirá los datos.

*lpFormatEtc*<br/>
Apunta a una estructura [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) que describe el formato en el que se van a devolver los datos. Proporcione un valor para este parámetro si desea especificar información de formato adicional más allá del formato del portapapeles especificado por *cfFormat*. Si es NULL, se usan los valores predeterminados para los demás campos de la estructura `FORMATETC`.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Para obtener más información, vea [IDataObject:: GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata), [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1)y [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) en el Windows SDK.

Para obtener más información, vea [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) en el Windows SDK.

##  <a name="getfiledata"></a>COleDataObject::GetFileData

Llame a esta función para crear una `CFile` o un objeto derivado de `CFile`y para recuperar datos en el formato especificado en un puntero de `CFile`.

```
CFile* GetFileData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Parámetros

*cfFormat*<br/>
Formato en el que se van a devolver los datos. Este parámetro puede ser uno de los formatos predefinidos del portapapeles o el valor devuelto por la función [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) nativa de Windows.

*lpFormatEtc*<br/>
Apunta a una estructura [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) que describe el formato en el que se van a devolver los datos. Proporcione un valor para este parámetro si desea especificar información de formato adicional más allá del formato del portapapeles especificado por *cfFormat*. Si es NULL, se usan los valores predeterminados para los demás campos de la estructura `FORMATETC`.

### <a name="return-value"></a>Valor devuelto

Puntero al nuevo `CFile` o objeto derivado de `CFile`que contiene los datos si se realiza correctamente; de lo contrario, NULL.

### <a name="remarks"></a>Observaciones

Dependiendo del medio en el que se almacenan los datos, el tipo real al que apunta el valor devuelto puede ser `CFile`, `CSharedFile`o `COleStreamFile`.

> [!NOTE]
>  El objeto de `CFile` al que tiene acceso el valor devuelto de esta función es propiedad del llamador. Es responsabilidad del autor de la llamada **eliminar** el objeto de `CFile`, con lo que se cierra el archivo.

Para obtener más información, consulte [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) en el Windows SDK.

Para obtener más información, vea [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) en el Windows SDK.

##  <a name="getglobaldata"></a>COleDataObject::GetGlobalData

Llame a esta función para asignar un bloque de memoria global y recuperar los datos del formato especificado en un HGLOBAL.

```
HGLOBAL GetGlobalData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Parámetros

*cfFormat*<br/>
Formato en el que se van a devolver los datos. Este parámetro puede ser uno de los formatos predefinidos del portapapeles o el valor devuelto por la función [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) nativa de Windows.

*lpFormatEtc*<br/>
Apunta a una estructura [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) que describe el formato en el que se van a devolver los datos. Proporcione un valor para este parámetro si desea especificar información de formato adicional más allá del formato del portapapeles especificado por *cfFormat*. Si es NULL, se usan los valores predeterminados para los demás campos de la estructura `FORMATETC`.

### <a name="return-value"></a>Valor devuelto

Identificador del bloque de memoria global que contiene los datos si se realiza correctamente; de lo contrario, NULL.

### <a name="remarks"></a>Observaciones

Para obtener más información, consulte [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) en el Windows SDK.

Para obtener más información, vea [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) en el Windows SDK.

##  <a name="getnextformat"></a>COleDataObject::GetNextFormat

Llame a esta función varias veces para obtener todos los formatos disponibles para recuperar los datos del elemento.

```
BOOL GetNextFormat(LPFORMATETC lpFormatEtc);
```

### <a name="parameters"></a>Parámetros

*lpFormatEtc*<br/>
Apunta a la estructura [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) que recibe la información de formato cuando se devuelve la llamada de función.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si hay otro formato disponible; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

Después de una llamada a [COleDataObject:: BeginEnumFormats](#beginenumformats), se almacena la posición del primer formato admitido por este objeto de datos. Las llamadas sucesivas a `GetNextFormat` enumerarán la lista de formatos disponibles en el objeto de datos. Use estas funciones para enumerar los formatos disponibles.

Para comprobar la disponibilidad de un formato determinado, llame a [COleDataObject:: IsDataAvailable](#isdataavailable).

Para obtener más información, vea [IEnumXXXX:: Next](/previous-versions//ms695273\(v=vs.85\)) en el Windows SDK.

##  <a name="isdataavailable"></a>COleDataObject::IsDataAvailable

Llame a esta función para determinar si un formato determinado está disponible para recuperar datos del elemento OLE.

```
BOOL IsDataAvailable(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Parámetros

*cfFormat*<br/>
El formato de datos del portapapeles que se va a usar en la estructura a la que apunta *lpFormatEtc*. Este parámetro puede ser uno de los formatos predefinidos del portapapeles o el valor devuelto por la función [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) nativa de Windows.

*lpFormatEtc*<br/>
Apunta a una estructura [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) que describe el formato deseado. Proporcione un valor para este parámetro solo si desea especificar información de formato adicional más allá del formato del portapapeles especificado por *cfFormat*. Si es NULL, se usan los valores predeterminados para los demás campos de la estructura `FORMATETC`.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si los datos están disponibles en el formato especificado; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

Esta función es útil antes de llamar a `GetData`, `GetFileData`o `GetGlobalData`.

Para obtener más información, vea [IDataObject:: QueryGetData](/windows/win32/api/objidl/nf-objidl-idataobject-querygetdata) y [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) en el Windows SDK.

Para obtener más información, vea [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) en el Windows SDK.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CRichEditView:: QueryAcceptData](../../mfc/reference/cricheditview-class.md#queryacceptdata).

##  <a name="release"></a>COleDataObject:: Release

Llame a esta función para liberar la propiedad del objeto [IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject) que se asoció previamente con el objeto `COleDataObject`.

```
void Release();
```

### <a name="remarks"></a>Observaciones

El `IDataObject` se asoció al `COleDataObject` llamando a `Attach` o `AttachClipboard` explícitamente o por el marco de trabajo. Si el parámetro *bAutoRelease* de `Attach` es false, no se liberará el objeto `IDataObject`. En este caso, el llamador es responsable de liberar el `IDataObject` llamando a [IUnknown:: Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release).

## <a name="see-also"></a>Consulte también

[Ejemplo de MFC HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[Ejemplo OCLIENT de MFC](../../overview/visual-cpp-samples.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[COleDataSource (clase)](../../mfc/reference/coledatasource-class.md)<br/>
[COleClientItem (clase)](../../mfc/reference/coleclientitem-class.md)<br/>
[COleServerItem (clase)](../../mfc/reference/coleserveritem-class.md)
