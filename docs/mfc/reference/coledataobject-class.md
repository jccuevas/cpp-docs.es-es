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
ms.openlocfilehash: 5e1545a033ab482e838fbc944b0ca9b3e543d651
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366130"
---
# <a name="coledataobject-class"></a>COleDataObject (clase)

Se utiliza en las transferencias de datos para recuperar datos en diferentes formatos del Portapapeles, mediante arrastrar y colocar o a partir de un elemento OLE incrustado.

## <a name="syntax"></a>Sintaxis

```
class COleDataObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[COleDataObject::COleDataObject](#coledataobject)|Construye un objeto `COleDataObject`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[COleDataObject::Attach](#attach)|Asocia el objeto de datos `COleDataObject`OLE especificado al archivo .|
|[COleDataObject::AttachClipboard](#attachclipboard)|Adjunta el objeto de datos que se encuentra en el Portapapeles.|
|[COleDataObject::BeginEnumFormats](#beginenumformats)|Se prepara para una `GetNextFormat` o más llamadas posteriores.|
|[COleDataObject::Detach](#detach)|Separa el `IDataObject` objeto asociado.|
|[COleDataObject::GetData](#getdata)|Copia datos del objeto de datos OLE adjunto en un formato especificado.|
|[COleDataObject::GetFileData](#getfiledata)|Copia los datos del objeto `CFile` de datos OLE adjunto en un puntero en el formato especificado.|
|[COleDataObject::GetGlobalData](#getglobaldata)|Copia los datos del objeto `HGLOBAL` de datos OLE adjunto en un formato especificado.|
|[COleDataObject::GetNextFormat](#getnextformat)|Devuelve el siguiente formato de datos disponible.|
|[COleDataObject::IsDataAvailable](#isdataavailable)|Comprueba si los datos están disponibles en un formato especificado.|
|[COleDataObject::Release](#release)|Separa y libera `IDataObject` el objeto asociado.|

## <a name="remarks"></a>Observaciones

`COleDataObject`no tiene una clase base.

Estos tipos de transferencias de datos incluyen un origen y un destino. El origen de datos se implementa como un objeto de la [COleDataSource](../../mfc/reference/coledatasource-class.md) clase. Cada vez que una aplicación de destino tiene datos eliminados o se `COleDataObject` le pide que realice una operación de pegar desde el Portapapeles, se debe crear un objeto de la clase.

Esta clase le permite determinar si los datos existen en un formato especificado. También puede enumerar los formatos de datos disponibles o comprobar si un formato determinado está disponible y, a continuación, recuperar los datos en el formato preferido. La recuperación de objetos se puede realizar de varias maneras diferentes, incluido el uso de un [CFile,](../../mfc/reference/cfile-class.md)un HGLOBAL o una `STGMEDIUM` estructura.

Para obtener más información, vea la estructura [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) en el Windows SDK.

Para obtener más información sobre el uso de objetos de datos en la aplicación, vea el artículo Objetos de datos y orígenes de [datos (OLE)](../../mfc/data-objects-and-data-sources-ole.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`COleDataObject`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxole.h

## <a name="coledataobjectattach"></a><a name="attach"></a>COleDataObject::Attach

Llame a esta `COleDataObject` función para asociar el objeto con un objeto de datos OLE.

```
void Attach(
    LPDATAOBJECT lpDataObject,
    BOOL bAutoRelease = TRUE);
```

### <a name="parameters"></a>Parámetros

*lpDataObject*<br/>
Apunta a un objeto de datos OLE.

*bAutoRelease*<br/>
TRUESi el objeto de datos `COleDataObject` OLE debe liberarse cuando se destruye el objeto; de lo contrario FALSO.

### <a name="remarks"></a>Observaciones

Para obtener más información, vea [IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject) en el Windows SDK.

## <a name="coledataobjectattachclipboard"></a><a name="attachclipboard"></a>COleDataObject::AttachClipboard

Llame a esta función para adjuntar el objeto `COleDataObject` de datos que se encuentra actualmente en el Portapapeles al objeto.

```
BOOL AttachClipboard();
```

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

> [!NOTE]
> Al llamar a esta función, se bloquea el Portapapeles hasta que se libera este objeto de datos. El objeto de datos se `COleDataObject`libera en el destructor para el archivo . Para obtener más información, consulte [OpenClipboard](/windows/win32/api/winuser/nf-winuser-openclipboard) y [CloseClipboard](/windows/win32/api/winuser/nf-winuser-closeclipboard) en la documentación de Win32.

## <a name="coledataobjectbeginenumformats"></a><a name="beginenumformats"></a>COleDataObject::BeginEnumFormats

Llame a esta función `GetNextFormat` para prepararse para las llamadas posteriores para recuperar una lista de formatos de datos del elemento.

```
void BeginEnumFormats();
```

### <a name="remarks"></a>Observaciones

Después de `BeginEnumFormats`una llamada a , se almacena la posición del primer formato admitido por este objeto de datos. Las llamadas sucesivas para `GetNextFormat` enumerar la lista de formatos disponibles en el objeto de datos.

Para comprobar la disponibilidad de datos en un formato determinado, utilice [COleDataObject::IsDataAvailable](#isdataavailable).

Para obtener más información, vea [IDataObject::EnumFormatEtc](/windows/win32/api/objidl/nf-objidl-idataobject-enumformatetc) en el Windows SDK.

## <a name="coledataobjectcoledataobject"></a><a name="coledataobject"></a>COleDataObject::COleDataObject

Construye un objeto `COleDataObject`.

```
COleDataObject();
```

### <a name="remarks"></a>Observaciones

Se debe realizar una llamada a [COleDataObject::Attach](#attach) o [COleDataObject::AttachClipboard](#attachclipboard) antes de llamar a otras `COleDataObject` funciones.

> [!NOTE]
> Dado que uno de los parámetros de los controladores `COleDataObject`de arrastrar y colocar es un puntero a un , no hay necesidad de llamar a este constructor para admitir arrastrar y colocar.

## <a name="coledataobjectdetach"></a><a name="detach"></a>COleDataObject::Detach

Llame a esta función para separar el `COleDataObject` objeto de su objeto de datos OLE asociado sin liberar el objeto de datos.

```
LPDATAOBJECT Detach();
```

### <a name="return-value"></a>Valor devuelto

Puntero al objeto de datos OLE que se desprende.

### <a name="remarks"></a>Observaciones

## <a name="coledataobjectgetdata"></a><a name="getdata"></a>COleDataObject::GetData

Llame a esta función para recuperar datos del elemento en el formato especificado.

```
BOOL GetData(
    CLIPFORMAT cfFormat,
    LPSTGMEDIUM lpStgMedium,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Parámetros

*cfFormat*<br/>
El formato en el que se devolverán los datos. Este parámetro puede ser uno de los formatos de Portapapeles predefinidos o el valor devuelto por la función [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) de Windows nativa.

*lpStgMedium*<br/>
Apunta a una estructura [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) que recibirá datos.

*lpFormatEtc*<br/>
Apunta a una estructura [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) que describe el formato en el que se devolverán los datos. Proporcione un valor para este parámetro si desea especificar información de formato adicional más allá del formato del Portapapeles especificado por *cfFormat*. Si es NULL, se usan los valores predeterminados para los demás campos de la `FORMATETC` estructura.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Para obtener más información, vea [IDataObject::GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata), [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1)y [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) en el Windows SDK.

Para obtener más información, consulte [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) en el Windows SDK.

## <a name="coledataobjectgetfiledata"></a><a name="getfiledata"></a>COleDataObject::GetFileData

Llame a esta `CFile` función para crear un objeto o `CFile`-derivado `CFile` y para recuperar datos en el formato especificado en un puntero.

```
CFile* GetFileData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Parámetros

*cfFormat*<br/>
El formato en el que se devolverán los datos. Este parámetro puede ser uno de los formatos de Portapapeles predefinidos o el valor devuelto por la función [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) de Windows nativa.

*lpFormatEtc*<br/>
Apunta a una estructura [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) que describe el formato en el que se devolverán los datos. Proporcione un valor para este parámetro si desea especificar información de formato adicional más allá del formato del Portapapeles especificado por *cfFormat*. Si es NULL, se usan los valores predeterminados para los demás campos de la `FORMATETC` estructura.

### <a name="return-value"></a>Valor devuelto

Puntero al `CFile` objeto `CFile`nuevo o derivado que contiene los datos si se realiza correctamente; NULL.

### <a name="remarks"></a>Observaciones

Dependiendo del medio en el que se almacenen los datos, `CFile` `CSharedFile`el `COleStreamFile`tipo real al que apunta el valor devuelto puede ser , , o .

> [!NOTE]
> El `CFile` objeto al que tiene acceso el valor devuelto de esta función es propiedad del autor de la llamada. Es responsabilidad del autor **delete** de `CFile` la llamada eliminar el objeto, cerrando así el archivo.

Para obtener más información, consulte [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) en el Windows SDK.

Para obtener más información, consulte [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) en el Windows SDK.

## <a name="coledataobjectgetglobaldata"></a><a name="getglobaldata"></a>COleDataObject::GetGlobalData

Llame a esta función para asignar un bloque de memoria global y recuperar datos en el formato especificado en un HGLOBAL.

```
HGLOBAL GetGlobalData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Parámetros

*cfFormat*<br/>
El formato en el que se devolverán los datos. Este parámetro puede ser uno de los formatos de Portapapeles predefinidos o el valor devuelto por la función [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) de Windows nativa.

*lpFormatEtc*<br/>
Apunta a una estructura [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) que describe el formato en el que se devolverán los datos. Proporcione un valor para este parámetro si desea especificar información de formato adicional más allá del formato del Portapapeles especificado por *cfFormat*. Si es NULL, se usan los valores predeterminados para los demás campos de la `FORMATETC` estructura.

### <a name="return-value"></a>Valor devuelto

El identificador del bloque de memoria global que contiene los datos si se realiza correctamente; NULL.

### <a name="remarks"></a>Observaciones

Para obtener más información, consulte [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) en el Windows SDK.

Para obtener más información, consulte [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) en el Windows SDK.

## <a name="coledataobjectgetnextformat"></a><a name="getnextformat"></a>COleDataObject::GetNextFormat

Llame a esta función repetidamente para obtener todos los formatos disponibles para recuperar datos del elemento.

```
BOOL GetNextFormat(LPFORMATETC lpFormatEtc);
```

### <a name="parameters"></a>Parámetros

*lpFormatEtc*<br/>
Apunta a la estructura [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) que recibe la información de formato cuando se devuelve la llamada de función.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si hay otro formato disponible; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Después de una llamada a [COleDataObject::BeginEnumFormats](#beginenumformats), se almacena la posición del primer formato admitido por este objeto de datos. Las llamadas sucesivas para `GetNextFormat` enumerar la lista de formatos disponibles en el objeto de datos. Utilice estas funciones para enumerar los formatos disponibles.

Para comprobar la disponibilidad de un formato determinado, llame a [COleDataObject::IsDataAvailable](#isdataavailable).

Para obtener más información, consulte [IEnumXXXX::Next](/previous-versions//ms695273\(v=vs.85\)) en el Windows SDK.

## <a name="coledataobjectisdataavailable"></a><a name="isdataavailable"></a>COleDataObject::IsDataAvailable

Llame a esta función para determinar si un formato determinado está disponible para recuperar datos del elemento OLE.

```
BOOL IsDataAvailable(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Parámetros

*cfFormat*<br/>
El formato de datos del Portapapeles que se utilizará en la estructura señalada por *lpFormatEtc*. Este parámetro puede ser uno de los formatos de Portapapeles predefinidos o el valor devuelto por la función [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) de Windows nativa.

*lpFormatEtc*<br/>
Señala una estructura [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) que describe el formato deseado. Proporcione un valor para este parámetro solo si desea especificar información de formato adicional más allá del formato del Portapapeles especificado por *cfFormat*. Si es NULL, se usan los valores predeterminados para los demás campos de la `FORMATETC` estructura.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si los datos están disponibles en el formato especificado; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Esta función es `GetData` `GetFileData`útil `GetGlobalData`antes de llamar a , , o .

Para obtener más información, vea [IDataObject::QueryGetData](/windows/win32/api/objidl/nf-objidl-idataobject-querygetdata) y [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) en el Windows SDK.

Para obtener más información, consulte [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) en el Windows SDK.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CRichEditView::QueryAcceptData](../../mfc/reference/cricheditview-class.md#queryacceptdata).

## <a name="coledataobjectrelease"></a><a name="release"></a>COleDataObject::Release

Llame a esta función para liberar la propiedad de `COleDataObject` la [IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject) objeto que se asoció anteriormente con el objeto.

```
void Release();
```

### <a name="remarks"></a>Observaciones

El `IDataObject` se asoció con el `COleDataObject` mediante una llamada `Attach` o `AttachClipboard` explícitamente o por el marco de trabajo. Si el parámetro *bAutoRelease* `Attach` de `IDataObject` es FALSE, el objeto no se liberará. En este caso, el autor `IDataObject` de la llamada es responsable de liberar el mediante una llamada a [IUnknown::Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release).

## <a name="see-also"></a>Consulte también

[Ejemplo de MFC HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[Ejemplo de MFC OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[COleDataSource (clase)](../../mfc/reference/coledatasource-class.md)<br/>
[Clase COleClientItem](../../mfc/reference/coleclientitem-class.md)<br/>
[COleServerItem (clase)](../../mfc/reference/coleserveritem-class.md)
