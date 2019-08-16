---
title: Clase COleStreamFile
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
ms.openlocfilehash: 96e8fee71f02ea750fd8b33f41fd2fd517e9081e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69503686"
---
# <a name="colestreamfile-class"></a>Clase COleStreamFile

Representa una secuencia de datos (`IStream`) en un archivo compuesto como parte de almacenamiento estructurado OLE.

## <a name="syntax"></a>Sintaxis

```
class COleStreamFile : public CFile
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[COleStreamFile::COleStreamFile](#colestreamfile)|Construye un objeto `COleStreamFile`.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[COleStreamFile::Attach](#attach)|Asocia un flujo con el objeto.|
|[COleStreamFile::CreateMemoryStream](#creatememorystream)|Crea un flujo a partir de la memoria global y lo asocia al objeto.|
|[COleStreamFile::CreateStream](#createstream)|Crea una secuencia y la asocia al objeto.|
|[COleStreamFile::Detach](#detach)|Desasocia el flujo del objeto.|
|[COleStreamFile::GetStream](#getstream)|Devuelve la secuencia actual.|
|[COleStreamFile::OpenStream](#openstream)|Abre de forma segura una secuencia y la asocia al objeto.|

## <a name="remarks"></a>Comentarios

Debe `IStorage` existir un objeto antes de que se pueda abrir o crear el flujo a menos que sea una secuencia de memoria.

`COleStreamFile`los objetos se manipulan exactamente igual que los objetos [CFile](../../mfc/reference/cfile-class.md) .

Para obtener más información sobre cómo manipular flujos y almacenamientos, consulte el [artículo contenedores: Archivos](../../mfc/containers-compound-files.md)compuestos..

Para obtener más información, vea [IStream](/windows/win32/api/objidl/nn-objidl-istream) y [IStorage](/windows/win32/api/objidl/nn-objidl-istorage) en el Windows SDK.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

`COleStreamFile`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxole. h

##  <a name="attach"></a>  COleStreamFile::Attach

Asocia el flujo OLE proporcionado al `COleStreamFile` objeto.

```
void Attach(LPSTREAM lpStream);
```

### <a name="parameters"></a>Parámetros

*lpStream*<br/>
Apunta al flujo OLE (`IStream`) que se va a asociar al objeto. No puede ser nulo.

### <a name="remarks"></a>Comentarios

El objeto no debe estar ya asociado a un flujo OLE.

Para obtener más información, vea [IStream](/windows/win32/api/objidl/nn-objidl-istream) en el Windows SDK.

##  <a name="colestreamfile"></a>  COleStreamFile::COleStreamFile

Crea un objeto `COleStreamFile`.

```
COleStreamFile(LPSTREAM lpStream = NULL);
```

### <a name="parameters"></a>Parámetros

*lpStream*<br/>
Puntero a la secuencia OLE que se va a asociar al objeto.

### <a name="remarks"></a>Comentarios

Si *lpStream* es null, el objeto no está asociado a un flujo OLE; de lo contrario, el objeto está asociado a la secuencia OLE proporcionada.

Para obtener más información, vea [IStream](/windows/win32/api/objidl/nn-objidl-istream) en el Windows SDK.

##  <a name="creatememorystream"></a>  COleStreamFile::CreateMemoryStream

Crea de forma segura un flujo nuevo fuera de la memoria compartida global donde un error es una condición normal y esperada.

```
BOOL CreateMemoryStream(CFileException* pError = NULL);
```

### <a name="parameters"></a>Parámetros

*pError*<br/>
Apunta a un objeto [CFileException](../../mfc/reference/cfileexception-class.md) o null que indica el estado de finalización de la operación de creación. Proporcione este parámetro si desea supervisar las posibles excepciones que se generan al intentar crear la secuencia.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la secuencia se crea correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

El subsistema OLE asigna la memoria.

Para obtener más información, vea [CreateStreamOnHGlobal](/windows/win32/api/combaseapi/nf-combaseapi-createstreamonhglobal) en el Windows SDK.

##  <a name="createstream"></a>  COleStreamFile::CreateStream

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
Apunta al objeto de almacenamiento OLE que contiene la secuencia que se va a crear. No puede ser nulo.

*lpszStreamName*<br/>
Nombre del flujo que se va a crear. No puede ser nulo.

*nOpenFlags*<br/>
Modo de acceso que se va a utilizar al abrir la secuencia. De forma predeterminada, se usan los modos exclusivo, de lectura/escritura y de creación. Para obtener una lista completa de los modos disponibles, vea [CFile:: CFile](../../mfc/reference/cfile-class.md#cfile).

*pError*<br/>
Apunta a un objeto [CFileException](../../mfc/reference/cfileexception-class.md) o null. Proporcione este parámetro si desea supervisar las posibles excepciones que se generan al intentar crear la secuencia.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la secuencia se crea correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Se producirá una excepción de archivo si se produce un error de apertura y el perror no es NULL.

Para obtener más información, vea [IStorage:: CreateStream (](/windows/win32/api/objidl/nf-objidl-istorage-createstream) en el Windows SDK.

##  <a name="detach"></a>  COleStreamFile::Detach

Desasocia la secuencia del objeto sin cerrar la secuencia.

```
LPSTREAM Detach();
```

### <a name="return-value"></a>Valor devuelto

Puntero a la secuencia (`IStream`) asociada al objeto.

### <a name="remarks"></a>Comentarios

La secuencia se debe cerrar de otra manera antes de que finalice el programa.

Para obtener más información, vea [IStream](/windows/win32/api/objidl/nn-objidl-istream) en el Windows SDK.

##  <a name="getstream"></a>  COleStreamFile::GetStream

Llame a esta función para devolver un puntero al flujo actual.

```
IStream* GetStream() const;
```

### <a name="return-value"></a>Valor devuelto

Puntero a la interfaz de flujo actual ( [IStream](/windows/win32/api/objidl/nn-objidl-istream)).

##  <a name="openstream"></a>  COleStreamFile::OpenStream

Abre un flujo existente.

```
BOOL OpenStream(
    LPSTORAGE lpStorage,
    LPCTSTR lpszStreamName,
    DWORD nOpenFlags = modeReadWrite|shareExclusive,
    CFileException* pError = NULL);
```

### <a name="parameters"></a>Parámetros

*lpStorage*<br/>
Apunta al objeto de almacenamiento OLE que contiene la secuencia que se va a abrir. No puede ser nulo.

*lpszStreamName*<br/>
Nombre del flujo que se va a abrir. No puede ser nulo.

*nOpenFlags*<br/>
Modo de acceso que se va a utilizar al abrir la secuencia. De forma predeterminada, se usan los modos exclusivo y de lectura y escritura. Para obtener la lista completa de los modos disponibles, vea [CFile:: CFile](../../mfc/reference/cfile-class.md#cfile).

*pError*<br/>
Apunta a un objeto [CFileException](../../mfc/reference/cfileexception-class.md) o null. Proporcione este parámetro si desea supervisar las posibles excepciones que se generan al intentar abrir la secuencia.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la secuencia se abre correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Se producirá una excepción de archivo si se produce un error de apertura y el perror no es NULL.

Para obtener más información, vea [IStorage:: OpenStream](/windows/win32/api/objidl/nf-objidl-istorage-openstream) en el Windows SDK.

## <a name="see-also"></a>Vea también

[CFile (clase)](../../mfc/reference/cfile-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)
