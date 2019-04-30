---
title: COleStreamFile (clase)
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
ms.openlocfilehash: 2bc943c74f456302b13db77bf28b6e4b21a5524b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62373519"
---
# <a name="colestreamfile-class"></a>COleStreamFile (clase)

Representa una secuencia de datos (`IStream`) en un archivo compuesto como parte de almacenamiento estructurado OLE.

## <a name="syntax"></a>Sintaxis

```
class COleStreamFile : public CFile
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[COleStreamFile::COleStreamFile](#colestreamfile)|Construye un objeto `COleStreamFile`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[COleStreamFile::Attach](#attach)|Asocia un flujo con el objeto.|
|[COleStreamFile::CreateMemoryStream](#creatememorystream)|Crea una secuencia de la memoria global y lo asocia con el objeto.|
|[COleStreamFile::CreateStream](#createstream)|Crea una secuencia y lo asocia con el objeto.|
|[COleStreamFile::Detach](#detach)|Desasocia la secuencia desde el objeto.|
|[COleStreamFile::GetStream](#getstream)|Devuelve la secuencia actual.|
|[COleStreamFile::OpenStream](#openstream)|Abre una secuencia y lo asocia con el objeto de forma segura.|

## <a name="remarks"></a>Comentarios

Un `IStorage` objeto debe existir antes de la secuencia se puede abrir o crear a menos que sea una secuencia de memoria.

`COleStreamFile` se manipulan los objetos exactamente igual que [CFile](../../mfc/reference/cfile-class.md) objetos.

Para obtener más información acerca de la manipulación de secuencias y almacenamientos, vea el artículo [contenedores: Archivos compuestos](../../mfc/containers-compound-files.md)...

Para obtener más información, consulte [IStream](/windows/desktop/api/objidl/nn-objidl-istream) y [IStorage](/windows/desktop/api/objidl/nn-objidl-istorage) en el SDK de Windows.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

`COleStreamFile`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxole.h

##  <a name="attach"></a>  COleStreamFile::Attach

Asocia la secuencia OLE suministrada con el `COleStreamFile` objeto.

```
void Attach(LPSTREAM lpStream);
```

### <a name="parameters"></a>Parámetros

*lpStream*<br/>
Apunta a la secuencia OLE (`IStream`) que se asociará con el objeto. No puede ser nulo.

### <a name="remarks"></a>Comentarios

El objeto no ya debe estar asociado con una secuencia OLE.

Para obtener más información, consulte [IStream](/windows/desktop/api/objidl/nn-objidl-istream) en el SDK de Windows.

##  <a name="colestreamfile"></a>  COleStreamFile::COleStreamFile

Crea un objeto `COleStreamFile`.

```
COleStreamFile(LPSTREAM lpStream = NULL);
```

### <a name="parameters"></a>Parámetros

*lpStream*<br/>
Puntero a la secuencia OLE que se asociará con el objeto.

### <a name="remarks"></a>Comentarios

Si *lpStream* es NULL, el objeto no está asociado con una secuencia OLE, de lo contrario, el objeto está asociado con la secuencia proporcionada de OLE.

Para obtener más información, consulte [IStream](/windows/desktop/api/objidl/nn-objidl-istream) en el SDK de Windows.

##  <a name="creatememorystream"></a>  COleStreamFile::CreateMemoryStream

Con seguridad crea un nuevo flujo fuera de la memoria compartida global donde es una condición normal, se esperaba un error.

```
BOOL CreateMemoryStream(CFileException* pError = NULL);
```

### <a name="parameters"></a>Parámetros

*pError*<br/>
Apunta a un [CFileException](../../mfc/reference/cfileexception-class.md) objeto o NULL que indica el estado de finalización de la operación de creación. Proporcione este parámetro si desea supervisar posibles excepciones que se genera al intentar crear la secuencia.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la secuencia se ha creado correctamente; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

La memoria está asignada por el subsistema OLE.

Para obtener más información, consulte [CreateStreamOnHGlobal](/windows/desktop/api/combaseapi/nf-combaseapi-createstreamonhglobal) en el SDK de Windows.

##  <a name="createstream"></a>  COleStreamFile::CreateStream

Con seguridad crea un nuevo flujo en el objeto de almacenamiento proporcionada donde es una condición normal, se esperaba un error.

```
BOOL CreateStream(
    LPSTORAGE lpStorage,
    LPCTSTR lpszStreamName,
    DWORD nOpenFlags = modeReadWrite|shareExclusive|modeCreate,
    CFileException* pError = NULL);
```

### <a name="parameters"></a>Parámetros

*lpStorage*<br/>
Señala al objeto OLE de almacenamiento que contiene la secuencia que se va a crear. No puede ser nulo.

*lpszStreamName*<br/>
Nombre de la secuencia que se va a crear. No puede ser nulo.

*nOpenFlags*<br/>
Modo de acceso que se utilizará al abrir la secuencia. Exclusivo, lectura y escritura y los modos de crear se usan de forma predeterminada. Para obtener una lista completa de los modos disponibles, consulte [CFile::CFile](../../mfc/reference/cfile-class.md#cfile).

*pError*<br/>
Apunta a un [CFileException](../../mfc/reference/cfileexception-class.md) objeto o NULL. Proporcione este parámetro si desea supervisar posibles excepciones que se genera al intentar crear la secuencia.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la secuencia se ha creado correctamente; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Si se produce un error en la apertura, se producirá una excepción de archivo y *pError* no es NULL.

Para obtener más información, consulte [IStorage::CreateStream](/windows/desktop/api/objidl/nf-objidl-istorage-createstream) en el SDK de Windows.

##  <a name="detach"></a>  COleStreamFile::Detach

Desasocia la secuencia desde el objeto sin cerrar la secuencia.

```
LPSTREAM Detach();
```

### <a name="return-value"></a>Valor devuelto

Un puntero a la secuencia (`IStream`) que estaba asociado con el objeto.

### <a name="remarks"></a>Comentarios

Debe cerrarse la secuencia de algún otro modo antes de que el programa finaliza.

Para obtener más información, consulte [IStream](/windows/desktop/api/objidl/nn-objidl-istream) en el SDK de Windows.

##  <a name="getstream"></a>  COleStreamFile::GetStream

Llame a esta función para devolver un puntero a la secuencia actual.

```
IStream* GetStream() const;
```

### <a name="return-value"></a>Valor devuelto

Un puntero a la interfaz de la secuencia actual ( [IStream](/windows/desktop/api/objidl/nn-objidl-istream)).

##  <a name="openstream"></a>  COleStreamFile::OpenStream

Se abre una secuencia existente.

```
BOOL OpenStream(
    LPSTORAGE lpStorage,
    LPCTSTR lpszStreamName,
    DWORD nOpenFlags = modeReadWrite|shareExclusive,
    CFileException* pError = NULL);
```

### <a name="parameters"></a>Parámetros

*lpStorage*<br/>
Señala al objeto OLE de almacenamiento que contiene la secuencia que se puede abrir. No puede ser nulo.

*lpszStreamName*<br/>
Nombre de la secuencia que se puede abrir. No puede ser nulo.

*nOpenFlags*<br/>
Modo de acceso que se utilizará al abrir la secuencia. Exclusivo y lectura/escritura se usan los modos de forma predeterminada. Para obtener la lista completa de los modos disponibles, consulte [CFile::CFile](../../mfc/reference/cfile-class.md#cfile).

*pError*<br/>
Apunta a un [CFileException](../../mfc/reference/cfileexception-class.md) objeto o NULL. Proporcione este parámetro si desea supervisar posibles excepciones que se generan al intentar abrir la secuencia.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el flujo se abre correctamente; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Si se produce un error en la apertura, se producirá una excepción de archivo y *pError* no es NULL.

Para obtener más información, consulte [IStorage::OpenStream](/windows/desktop/api/objidl/nf-objidl-istorage-openstream) en el SDK de Windows.

## <a name="see-also"></a>Vea también

[CFile (clase)](../../mfc/reference/cfile-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)
