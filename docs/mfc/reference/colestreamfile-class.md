---
title: COleStreamFile (Clase)
ms.date: 11/04/2016
f1_keywords:
- COleStreamFile
- AFXOLE/COleStreamFile
- AFXOLE/COleStreamFile::COleStreamFile
- AFXOLE/COleStreamFile::Attach
- AFXOLE/COleStreamFile::CreateMemoryStream
- AFXOLE/COleStreamFile::CreateStream
- AFXOLE/COleStreamFile::Detach
- AFXOLE/COleStreamFile::GetStream
- AFXOLE/COleStreamFile::OpenStream
helpviewer_keywords:
- COleStreamFile [MFC], COleStreamFile
- COleStreamFile [MFC], Attach
- COleStreamFile [MFC], CreateMemoryStream
- COleStreamFile [MFC], CreateStream
- COleStreamFile [MFC], Detach
- COleStreamFile [MFC], GetStream
- COleStreamFile [MFC], OpenStream
ms.assetid: e4f93698-e17c-4a18-a7c0-4b4df8eb4d93
ms.openlocfilehash: 1f53d3bd55fbff45257c06af2ab11f066d421a54
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376097"
---
# <a name="colestreamfile-class"></a>COleStreamFile (Clase)

Representa una secuencia de datos (`IStream`) en un archivo compuesto como parte de almacenamiento estructurado OLE.

## <a name="syntax"></a>Sintaxis

```
class COleStreamFile : public CFile
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[COleStreamFile::COleStreamFile](#colestreamfile)|Construye un objeto `COleStreamFile`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[COleStreamFile::Attach](#attach)|Asocia una secuencia con el objeto.|
|[COleStreamFile::CreateMemoryStream](#creatememorystream)|Crea una secuencia a partir de memoria global y la asocia con el objeto.|
|[COleStreamFile::CreateStream](#createstream)|Crea una secuencia y la asocia con el objeto.|
|[COleStreamFile::Detach](#detach)|Desasocia la secuencia del objeto.|
|[COleStreamFile::GetStream](#getstream)|Devuelve la secuencia actual.|
|[COleStreamFile::OpenStream](#openstream)|Abre una secuencia de forma segura y la asocia con el objeto.|

## <a name="remarks"></a>Observaciones

Un `IStorage` objeto debe existir antes de que la secuencia se pueda abrir o crear a menos que sea una secuencia de memoria.

`COleStreamFile`objetos se manipulan exactamente igual [que CFile](../../mfc/reference/cfile-class.md) objetos.

Para obtener más información acerca de la manipulación de secuencias y almacenamientos, consulte el artículo [Contenedores: archivos compuestos](../../mfc/containers-compound-files.md)..

Para obtener más información, consulte [IStream](/windows/win32/api/objidl/nn-objidl-istream) e [IStorage](/windows/win32/api/objidl/nn-objidl-istorage) en el Windows SDK.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

`COleStreamFile`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxole.h

## <a name="colestreamfileattach"></a><a name="attach"></a>COleStreamFile::Attach

Asocia la secuencia OLE `COleStreamFile` proporcionada con el objeto.

```
void Attach(LPSTREAM lpStream);
```

### <a name="parameters"></a>Parámetros

*lpStream*<br/>
Apunta a la`IStream`secuencia OLE ( ) que se asociará al objeto. No puede ser NULL.

### <a name="remarks"></a>Observaciones

El objeto no debe estar asociado ya a una secuencia OLE.

Para obtener más información, consulte [IStream](/windows/win32/api/objidl/nn-objidl-istream) en el Windows SDK.

## <a name="colestreamfilecolestreamfile"></a><a name="colestreamfile"></a>COleStreamFile::COleStreamFile

Crea un objeto `COleStreamFile` .

```
COleStreamFile(LPSTREAM lpStream = NULL);
```

### <a name="parameters"></a>Parámetros

*lpStream*<br/>
Puntero a la secuencia OLE que se asociará con el objeto.

### <a name="remarks"></a>Observaciones

Si *lpStream* es NULL, el objeto no está asociado a una secuencia OLE, de lo contrario, el objeto está asociado a la secuencia OLE proporcionada.

Para obtener más información, consulte [IStream](/windows/win32/api/objidl/nn-objidl-istream) en el Windows SDK.

## <a name="colestreamfilecreatememorystream"></a><a name="creatememorystream"></a>COleStreamFile::CreateMemoryStream

Crea de forma segura una nueva secuencia a partir de memoria compartida global donde un error es una condición normal y esperada.

```
BOOL CreateMemoryStream(CFileException* pError = NULL);
```

### <a name="parameters"></a>Parámetros

*pError*<br/>
Apunta a un [CFileException](../../mfc/reference/cfileexception-class.md) objeto o NULL que indica el estado de finalización de la operación de creación. Proporcione este parámetro si desea supervisar las posibles excepciones generadas al intentar crear la secuencia.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la secuencia se crea correctamente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

El subsistema OLE asigna la memoria.

Para obtener más información, consulte [CreateStreamOnHGlobal](/windows/win32/api/combaseapi/nf-combaseapi-createstreamonhglobal) en el Windows SDK.

## <a name="colestreamfilecreatestream"></a><a name="createstream"></a>COleStreamFile::CreateStream

Crea de forma segura una nueva secuencia en el objeto de almacenamiento proporcionado donde un error es una condición normal y esperada.

```
BOOL CreateStream(
    LPSTORAGE lpStorage,
    LPCTSTR lpszStreamName,
    DWORD nOpenFlags = modeReadWrite|shareExclusive|modeCreate,
    CFileException* pError = NULL);
```

### <a name="parameters"></a>Parámetros

*lpStorage*<br/>
Apunta al objeto de almacenamiento OLE que contiene la secuencia que se va a crear. No puede ser NULL.

*lpszStreamName*<br/>
Nombre de la secuencia que se va a crear. No puede ser NULL.

*nOpenFlags*<br/>
Modo de acceso que se utilizará al abrir la secuencia. Los modos exclusivos, de lectura/escritura y de creación se utilizan de forma predeterminada. Para obtener una lista completa de los modos disponibles, vea [CFile::CFile](../../mfc/reference/cfile-class.md#cfile).

*pError*<br/>
Apunta a un [CFileException](../../mfc/reference/cfileexception-class.md) objeto o NULL. Proporcione este parámetro si desea supervisar las posibles excepciones generadas al intentar crear la secuencia.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la secuencia se crea correctamente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Se producirá una excepción de archivo si se produce un error en la apertura y *pError* no es NULL.

Para obtener más información, consulte [IStorage::CreateStream](/windows/win32/api/objidl/nf-objidl-istorage-createstream) en el Windows SDK.

## <a name="colestreamfiledetach"></a><a name="detach"></a>COleStreamFile::Detach

Desasocia la secuencia del objeto sin cerrar la secuencia.

```
LPSTREAM Detach();
```

### <a name="return-value"></a>Valor devuelto

Puntero a la`IStream`secuencia ( ) que se asoció con el objeto.

### <a name="remarks"></a>Observaciones

La secuencia debe cerrarse de alguna otra manera antes de que finalice el programa.

Para obtener más información, consulte [IStream](/windows/win32/api/objidl/nn-objidl-istream) en el Windows SDK.

## <a name="colestreamfilegetstream"></a><a name="getstream"></a>COleStreamFile::GetStream

Llame a esta función para devolver un puntero a la secuencia actual.

```
IStream* GetStream() const;
```

### <a name="return-value"></a>Valor devuelto

Un puntero a la interfaz de secuencia actual ( [IStream](/windows/win32/api/objidl/nn-objidl-istream)).

## <a name="colestreamfileopenstream"></a><a name="openstream"></a>COleStreamFile::OpenStream

Abre una secuencia existente.

```
BOOL OpenStream(
    LPSTORAGE lpStorage,
    LPCTSTR lpszStreamName,
    DWORD nOpenFlags = modeReadWrite|shareExclusive,
    CFileException* pError = NULL);
```

### <a name="parameters"></a>Parámetros

*lpStorage*<br/>
Apunta al objeto de almacenamiento OLE que contiene la secuencia que se va a abrir. No puede ser NULL.

*lpszStreamName*<br/>
Nombre de la secuencia que se va a abrir. No puede ser NULL.

*nOpenFlags*<br/>
Modo de acceso que se utilizará al abrir la secuencia. Los modos exclusivos y de lectura/escritura se utilizan de forma predeterminada. Para obtener la lista completa de los modos disponibles, consulte [CFile::CFile](../../mfc/reference/cfile-class.md#cfile).

*pError*<br/>
Apunta a un [CFileException](../../mfc/reference/cfileexception-class.md) objeto o NULL. Proporcione este parámetro si desea supervisar las posibles excepciones generadas al intentar abrir la secuencia.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la secuencia se abre correctamente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Se producirá una excepción de archivo si se produce un error en la apertura y *pError* no es NULL.

Para obtener más información, consulte [IStorage::OpenStream](/windows/win32/api/objidl/nf-objidl-istorage-openstream) en el Windows SDK.

## <a name="see-also"></a>Consulte también

[CFile (clase)](../../mfc/reference/cfile-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)
