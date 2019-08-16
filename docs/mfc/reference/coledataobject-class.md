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
ms.openlocfilehash: c25fd7e91c59d7bea06325fbb27471d8f90f589d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504244"
---
# <a name="coledataobject-class"></a>Clase COleDataObject

Se utiliza en las transferencias de datos para recuperar datos en diferentes formatos del Portapapeles, mediante arrastrar y colocar o a partir de un elemento OLE incrustado.

## <a name="syntax"></a>Sintaxis

```
class COleDataObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[COleDataObject::COleDataObject](#coledataobject)|Construye un objeto `COleDataObject`.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[COleDataObject::Attach](#attach)|Adjunta el objeto de datos OLE especificado a `COleDataObject`.|
|[COleDataObject::AttachClipboard](#attachclipboard)|Adjunta el objeto de datos que se encuentra en el portapapeles.|
|[COleDataObject::BeginEnumFormats](#beginenumformats)|Prepara para una o varias llamadas subsiguientes `GetNextFormat` .|
|[COleDataObject::Detach](#detach)|Desasocia el objeto `IDataObject` asociado.|
|[COleDataObject::GetData](#getdata)|Copia datos del objeto de datos OLE adjunto en un formato especificado.|
|[COleDataObject::GetFileData](#getfiledata)|Copia datos del objeto de datos OLE adjunto en un `CFile` puntero con el formato especificado.|
|[COleDataObject::GetGlobalData](#getglobaldata)|Copia datos del objeto de datos OLE adjunto en un `HGLOBAL` con el formato especificado.|
|[COleDataObject::GetNextFormat](#getnextformat)|Devuelve el siguiente formato de datos disponible.|
|[COleDataObject::IsDataAvailable](#isdataavailable)|Comprueba si los datos están disponibles en un formato especificado.|
|[COleDataObject::Release](#release)|Desasocia y libera el objeto `IDataObject` asociado.|

## <a name="remarks"></a>Comentarios

`COleDataObject`no tiene una clase base.

Estos tipos de transferencias de datos incluyen un origen y un destino. El origen de datos se implementa como un objeto de la clase [COleDataSource](../../mfc/reference/coledatasource-class.md) . Cada vez que una aplicación de destino tiene datos quitados o se le pide que realice una operación de pegar desde el portapapeles, se debe crear un objeto de la `COleDataObject` clase.

Esta clase permite determinar si los datos existen en un formato especificado. También puede enumerar los formatos de datos disponibles o comprobar si un formato determinado está disponible y, a continuación, recuperar los datos en el formato preferido. La recuperación de objetos se puede realizar de varias maneras diferentes, como el uso de un objeto [CFile](../../mfc/reference/cfile-class.md), hglobal o `STGMEDIUM` una estructura.

Para obtener más información, vea la estructura [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-stgmedium) en el Windows SDK.

Para obtener más información sobre el uso de objetos de datos en la aplicación, vea el artículo objetos de datos [y orígenes de datos (OLE)](../../mfc/data-objects-and-data-sources-ole.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`COleDataObject`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxole. h

##  <a name="attach"></a>COleDataObject:: Attach

Llame a esta función para asociar el `COleDataObject` objeto a un objeto de datos OLE.

```
void Attach(
    LPDATAOBJECT lpDataObject,
    BOOL bAutoRelease = TRUE);
```

### <a name="parameters"></a>Parámetros

*lpDataObject*<br/>
Apunta a un objeto de datos OLE.

*bAutoRelease*<br/>
True si el objeto de datos OLE se debe liberar cuando `COleDataObject` se destruye el objeto; en caso contrario, false.

### <a name="remarks"></a>Comentarios

Para obtener más información, vea [IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject) en el Windows SDK.

##  <a name="attachclipboard"></a>  COleDataObject::AttachClipboard

Llame a esta función para adjuntar al `COleDataObject` objeto el objeto de datos que se encuentra actualmente en el portapapeles.

```
BOOL AttachClipboard();
```

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

> [!NOTE]
>  La llamada a esta función bloquea el Portapapeles hasta que este objeto de datos se libera. El objeto de datos se libera en el destructor para `COleDataObject`. Para obtener más información, vea [OpenClipboard](/windows/win32/api/winuser/nf-winuser-openclipboard) y [CloseClipboard](/windows/win32/api/winuser/nf-winuser-closeclipboard) en la documentación de Win32.

##  <a name="beginenumformats"></a>  COleDataObject::BeginEnumFormats

Llame a esta función para preparar las llamadas posteriores `GetNextFormat` a para recuperar una lista de formatos de datos del elemento.

```
void BeginEnumFormats();
```

### <a name="remarks"></a>Comentarios

Después de una llamada `BeginEnumFormats`a, se almacena la posición del primer formato admitido por este objeto de datos. En las llamadas `GetNextFormat` sucesivas a se enumerará la lista de formatos disponibles en el objeto de datos.

Para comprobar la disponibilidad de los datos en un formato determinado, use [COleDataObject:: IsDataAvailable](#isdataavailable).

Para obtener más información, vea [IDataObject:: del EnumFormatEtc](/windows/win32/api/objidl/nf-objidl-idataobject-enumformatetc) en el Windows SDK.

##  <a name="coledataobject"></a>  COleDataObject::COleDataObject

Construye un objeto `COleDataObject`.

```
COleDataObject();
```

### <a name="remarks"></a>Comentarios

Se debe realizar una llamada a [COleDataObject:: Attach](#attach) o [COleDataObject:: AttachClipboard](#attachclipboard) antes de llamar `COleDataObject` a otras funciones.

> [!NOTE]
>  Dado que uno de los parámetros de los controladores de arrastrar y colocar es un puntero a `COleDataObject`, no es necesario llamar a este constructor para admitir la función de arrastrar y colocar.

##  <a name="detach"></a>  COleDataObject::Detach

Llame a esta función para desasociar el `COleDataObject` objeto de su objeto de datos OLE asociado sin liberar el objeto de datos.

```
LPDATAOBJECT Detach();
```

### <a name="return-value"></a>Valor devuelto

Puntero al objeto de datos OLE que se desconectó.

### <a name="remarks"></a>Comentarios

##  <a name="getdata"></a>  COleDataObject::GetData

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
Apunta a una estructura [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-stgmedium) que recibirá los datos.

*lpFormatEtc*<br/>
Apunta a una estructura [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) que describe el formato en el que se van a devolver los datos. Proporcione un valor para este parámetro si desea especificar información de formato adicional más allá del formato del portapapeles especificado por *cfFormat*. Si es null, se usan los valores predeterminados para los demás campos de `FORMATETC` la estructura.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Para obtener más información, vea [IDataObject:: GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata), [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-stgmedium)y [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) en el Windows SDK.

Para obtener más información, vea [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) en el Windows SDK.

##  <a name="getfiledata"></a>  COleDataObject::GetFileData

Llame a esta función para crear `CFile` un `CFile`objeto derivado de o y para recuperar datos en el formato especificado en `CFile` un puntero.

```
CFile* GetFileData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Parámetros

*cfFormat*<br/>
Formato en el que se van a devolver los datos. Este parámetro puede ser uno de los formatos predefinidos del portapapeles o el valor devuelto por la función [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) nativa de Windows.

*lpFormatEtc*<br/>
Apunta a una estructura [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) que describe el formato en el que se van a devolver los datos. Proporcione un valor para este parámetro si desea especificar información de formato adicional más allá del formato del portapapeles especificado por *cfFormat*. Si es null, se usan los valores predeterminados para los demás campos de `FORMATETC` la estructura.

### <a name="return-value"></a>Valor devuelto

Puntero al nuevo `CFile` objeto o `CFile`derivado de que contiene los datos si es correcto; de lo contrario, NULL.

### <a name="remarks"></a>Comentarios

Dependiendo del medio en el que se almacenan los datos, el tipo real al que apunta el valor devuelto `CFile`puede `CSharedFile`ser, `COleStreamFile`o.

> [!NOTE]
>  El `CFile` objeto al que se obtiene acceso por el valor devuelto de esta función es propiedad del llamador. Es responsabilidad del autor de la llamada **eliminar** el `CFile` objeto, con lo que se cierra el archivo.

Para obtener más información, consulte [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) en el Windows SDK.

Para obtener más información, vea [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) en el Windows SDK.

##  <a name="getglobaldata"></a>  COleDataObject::GetGlobalData

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
Apunta a una estructura [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) que describe el formato en el que se van a devolver los datos. Proporcione un valor para este parámetro si desea especificar información de formato adicional más allá del formato del portapapeles especificado por *cfFormat*. Si es null, se usan los valores predeterminados para los demás campos de `FORMATETC` la estructura.

### <a name="return-value"></a>Valor devuelto

Identificador del bloque de memoria global que contiene los datos si se realiza correctamente; de lo contrario, NULL.

### <a name="remarks"></a>Comentarios

Para obtener más información, consulte [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) en el Windows SDK.

Para obtener más información, vea [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) en el Windows SDK.

##  <a name="getnextformat"></a>  COleDataObject::GetNextFormat

Llame a esta función varias veces para obtener todos los formatos disponibles para recuperar los datos del elemento.

```
BOOL GetNextFormat(LPFORMATETC lpFormatEtc);
```

### <a name="parameters"></a>Parámetros

*lpFormatEtc*<br/>
Apunta a la estructura [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) que recibe la información de formato cuando se devuelve la llamada de función.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si hay otro formato disponible; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Después de una llamada a [COleDataObject:: BeginEnumFormats](#beginenumformats), se almacena la posición del primer formato admitido por este objeto de datos. En las llamadas `GetNextFormat` sucesivas a se enumerará la lista de formatos disponibles en el objeto de datos. Use estas funciones para enumerar los formatos disponibles.

Para comprobar la disponibilidad de un formato determinado, llame a [COleDataObject:: IsDataAvailable](#isdataavailable).

Para obtener más información, vea [IEnumXXXX:: Next](/previous-versions//ms695273\(v=vs.85\)) en el Windows SDK.

##  <a name="isdataavailable"></a>  COleDataObject::IsDataAvailable

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
Apunta a una estructura [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) que describe el formato deseado. Proporcione un valor para este parámetro solo si desea especificar información de formato adicional más allá del formato del portapapeles especificado por *cfFormat*. Si es null, se usan los valores predeterminados para los demás campos de `FORMATETC` la estructura.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si los datos están disponibles en el formato especificado; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Esta función es útil antes de `GetData`llamar `GetFileData`a, `GetGlobalData`o.

Para obtener más información, vea [IDataObject:: QueryGetData](/windows/win32/api/objidl/nf-objidl-idataobject-querygetdata) y [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) en el Windows SDK.

Para obtener más información, vea [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) en el Windows SDK.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CRichEditView:: QueryAcceptData](../../mfc/reference/cricheditview-class.md#queryacceptdata).

##  <a name="release"></a>COleDataObject:: Release

Llame a esta función para liberar la propiedad del objeto [IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject) que se asoció previamente `COleDataObject` con el objeto.

```
void Release();
```

### <a name="remarks"></a>Comentarios

Se asoció `COleDataObject` a mediante una llamada `Attach` a `AttachClipboard` o explícitamente o por el marco de trabajo. `IDataObject` Si el parámetro *bAutoRelease* de `Attach` es false, el `IDataObject` objeto no se liberará. En este caso, el llamador es responsable de liberar `IDataObject` llamando a [IUnknown:: Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release).

## <a name="see-also"></a>Vea también

[Ejemplo de MFC HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[Ejemplo OCLIENT de MFC](../../overview/visual-cpp-samples.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[COleDataSource (clase)](../../mfc/reference/coledatasource-class.md)<br/>
[COleClientItem (clase)](../../mfc/reference/coleclientitem-class.md)<br/>
[COleServerItem (clase)](../../mfc/reference/coleserveritem-class.md)
