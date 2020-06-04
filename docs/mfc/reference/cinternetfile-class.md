---
title: Clase CInternetFile
ms.date: 11/04/2016
f1_keywords:
- CInternetFile
- AFXINET/CInternetFile
- AFXINET/CInternetFile::CInternetFile
- AFXINET/CInternetFile::Abort
- AFXINET/CInternetFile::Close
- AFXINET/CInternetFile::Flush
- AFXINET/CInternetFile::GetLength
- AFXINET/CInternetFile::Read
- AFXINET/CInternetFile::ReadString
- AFXINET/CInternetFile::Seek
- AFXINET/CInternetFile::SetReadBufferSize
- AFXINET/CInternetFile::SetWriteBufferSize
- AFXINET/CInternetFile::Write
- AFXINET/CInternetFile::WriteString
- AFXINET/CInternetFile::m_hFile
helpviewer_keywords:
- CInternetFile [MFC], CInternetFile
- CInternetFile [MFC], Abort
- CInternetFile [MFC], Close
- CInternetFile [MFC], Flush
- CInternetFile [MFC], GetLength
- CInternetFile [MFC], Read
- CInternetFile [MFC], ReadString
- CInternetFile [MFC], Seek
- CInternetFile [MFC], SetReadBufferSize
- CInternetFile [MFC], SetWriteBufferSize
- CInternetFile [MFC], Write
- CInternetFile [MFC], WriteString
- CInternetFile [MFC], m_hFile
ms.assetid: 96935681-ee71-4a8d-9783-5abc7b3e6f10
ms.openlocfilehash: e3f1a7167f5464423754951764c4441513197841
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372398"
---
# <a name="cinternetfile-class"></a>Clase CInternetFile

Permite el acceso a archivos en sistemas remotos que utilizan protocolos de Internet.

## <a name="syntax"></a>Sintaxis

```
class CInternetFile : public CStdioFile
```

## <a name="members"></a>Miembros

### <a name="protected-constructors"></a>Constructores protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CInternetFile::CInternetFile](#cinternetfile)|Construye un objeto `CInternetFile`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CInternetFile::Abortar](#abort)|Cierra el archivo, ignorando todas las advertencias y errores.|
|[CInternetFile::Cerrar](#close)|Cierra a `CInternetFile` y libera sus recursos.|
|[CInternetFile::Flush](#flush)|Vacía el contenido del búfer de escritura y se asegura de que los datos en memoria se escriben en el equipo de destino.|
|[CInternetFile::GetLength](#getlength)|Devuelve el tamaño del archivo.|
|[CInternetFile::Leer](#read)|Lee el número de bytes especificados.|
|[CInternetFile::ReadString](#readstring)|Lee una secuencia de caracteres.|
|[CInternetFile::Buscar](#seek)|Cambia la posición del puntero en un archivo abierto.|
|[CInternetFile::SetReadBufferSize](#setreadbuffersize)|Establece el tamaño del búfer donde se leerán los datos.|
|[CInternetFile::SetWriteBufferSize](#setwritebuffersize)|Establece el tamaño del búfer donde se escribirán los datos.|
|[CInternetFile::Escribir](#write)|Escribe el número de bytes especificados.|
|[CInternetFile::WriteString](#writestring)|Escribe una cadena terminada en null en un archivo.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CInternetFile::operador HINTERNET](#operator_hinternet)|Un operador de fundición para un identificador de Internet.|

### <a name="protected-data-members"></a>Miembros de datos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CInternetFile::m_hFile](#m_hfile)|Un identificador de un archivo.|

## <a name="remarks"></a>Observaciones

Proporciona una clase base para las clases de archivo [CHttpFile](../../mfc/reference/chttpfile-class.md) y [CGopherFile.](../../mfc/reference/cgopherfile-class.md) Nunca se `CInternetFile` crea un objeto directamente. En su lugar, cree un objeto de una de sus clases derivadas llamando a [CGopherConnection::OpenFile](../../mfc/reference/cgopherconnection-class.md#openfile) o [CHttpConnection::OpenRequest](../../mfc/reference/chttpconnection-class.md#openrequest). También puede crear `CInternetFile` un objeto llamando a [CFtpConnection::OpenFile](../../mfc/reference/cftpconnection-class.md#openfile).

Las `CInternetFile` `Open`funciones `LockRange` `UnlockRange`miembro `Duplicate` , , , `CInternetFile`y no se implementan para . Si llama a estas `CInternetFile` funciones en un objeto, obtendrá una [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).

Para obtener más `CInternetFile` información sobre cómo funciona con las otras clases de Internet MFC, vea el artículo Programación de [Internet con WinInet](../../mfc/win32-internet-extensions-wininet.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[CStdioFile](../../mfc/reference/cstdiofile-class.md)

`CInternetFile`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxinet.h

## <a name="cinternetfileabort"></a><a name="abort"></a>CInternetFile::Abortar

Cierra el archivo asociado a este objeto y hace que el archivo no esté disponible para su lectura o escritura.

```
virtual void Abort();
```

### <a name="remarks"></a>Observaciones

Si no ha cerrado el archivo antes de destruir el objeto, el destructor lo cierra por usted.

Al controlar excepciones, `Abort` difiere de [Cerrar](#close) de dos maneras importantes. En primer `Abort` lugar, la función no produce una excepción en los errores porque omite los errores. En `Abort` segundo lugar, no **ASSERT** si el archivo no se ha abierto o se ha cerrado previamente.

## <a name="cinternetfilecinternetfile"></a><a name="cinternetfile"></a>CInternetFile::CInternetFile

Se llama a esta `CInternetFile` función miembro cuando se crea un objeto.

```
CInternetFile(
    HINTERNET hFile,
    LPCTSTR pstrFileName,
    CInternetConnection* pConnection,
    BOOL bReadMode);

CInternetFile(
    HINTERNET hFile,
    HINTERNET hSession,
    LPCTSTR pstrFileName,
    LPCTSTR pstrServer,
    DWORD_PTR dwContext,
    BOOL bReadMode);
```

### <a name="parameters"></a>Parámetros

*hArchivo*<br/>
Identificador de un archivo de Internet.

*pstrFileName*<br/>
Puntero a una cadena que contiene el nombre de archivo.

*pConexión*<br/>
Un puntero a un [CInternetConnection](../../mfc/reference/cinternetconnection-class.md) objeto.

*bReadMode*<br/>
Indica si el archivo es de solo lectura.

*hSesión*<br/>
Un identificador de una sesión de Internet.

*pstrServer*<br/>
Puntero a una cadena que contiene el nombre del servidor.

*dwContext*<br/>
Identificador de contexto `CInternetFile` para el objeto. Consulte [Conceptos básicos de WinInet](../../mfc/wininet-basics.md) para obtener más información sobre el identificador de contexto.

### <a name="remarks"></a>Observaciones

Nunca se `CInternetFile` crea un objeto directamente. En su lugar, cree un objeto de una de sus clases derivadas llamando a [CGopherConnection::OpenFile](../../mfc/reference/cgopherconnection-class.md#openfile) o [CHttpConnection::OpenRequest](../../mfc/reference/chttpconnection-class.md#openrequest). También puede crear `CInternetFile` un objeto llamando a [CFtpConnection::OpenFile](../../mfc/reference/cftpconnection-class.md#openfile).

## <a name="cinternetfileclose"></a><a name="close"></a>CInternetFile::Cerrar

Cierra a `CInternetFile` y libera cualquiera de sus recursos.

```
virtual void Close();
```

### <a name="remarks"></a>Observaciones

Si el archivo se abrió para su escritura, hay una llamada implícita a [Flush](#flush) para asegurarse de que todos los datos almacenados en búfer se escriben en el host. Debe llamar `Close` cuando haya terminado de usar un archivo.

## <a name="cinternetfileflush"></a><a name="flush"></a>CInternetFile::Flush

Llame a esta función miembro para vaciar el contenido del búfer de escritura.

```
virtual void Flush();
```

### <a name="remarks"></a>Observaciones

Se `Flush` utiliza para asegurarse de que todos los datos de la memoria se han escrito realmente en el equipo de destino y para garantizar que se ha completado la transacción con el equipo host. `Flush`sólo es `CInternetFile` eficaz en los objetos abiertos para la escritura.

## <a name="cinternetfilegetlength"></a><a name="getlength"></a>CInternetFile::GetLength

Devuelve el tamaño del archivo.

```
virtual ULONGLONG GetLength() const;
```

## <a name="cinternetfilem_hfile"></a><a name="m_hfile"></a>CInternetFile::m_hFile

Identificador del archivo asociado a este objeto.

```
HINTERNET m_hFile;
```

## <a name="cinternetfileoperator-hinternet"></a><a name="operator_hinternet"></a>CInternetFile::operador HINTERNET

Utilice este operador para obtener el identificador de Windows para la sesión de Internet actual.

```
operator HINTERNET() const;
```

## <a name="cinternetfileread"></a><a name="read"></a>CInternetFile::Leer

Llame a esta función miembro para leer en la memoria dada, comenzando en *lpvBuf*, el número especificado de bytes, *nCount*.

```
virtual UINT Read(
    void* lpBuf,
    UINT nCount);
```

### <a name="parameters"></a>Parámetros

*lpBuf*<br/>
Puntero a una dirección de memoria para la que se leen datos de archivo.

*nCount*<br/>
Número de bytes que se escribirán.

### <a name="return-value"></a>Valor devuelto

Número de bytes que se transfieren al búfer. El valor devuelto puede ser menor que *nCount* si se alcanzó el final del archivo.

### <a name="remarks"></a>Observaciones

La función devuelve el número de bytes realmente leídos, un número que puede ser menor que *nCount* si finaliza el archivo. Si se produce un error al leer el archivo, la función produce un [CInternetException](../../mfc/reference/cinternetexception-class.md) objeto que describe el error. Tenga en cuenta que leer más allá del final del archivo no se considera un error y no se generará ninguna excepción.

Para asegurarse de que se recuperan todos `CInternetFile::Read` los datos, una aplicación debe seguir llamando al método hasta que el método devuelve cero.

## <a name="cinternetfilereadstring"></a><a name="readstring"></a>CInternetFile::ReadString

Llame a esta función miembro para leer una secuencia de caracteres hasta que encuentre un carácter de nueva línea.

```
virtual BOOL ReadString(CString& rString);

virtual LPTSTR ReadString(
    LPTSTR pstr,
    UINT nMax);
```

### <a name="parameters"></a>Parámetros

*Pstr*<br/>
Puntero a una cadena que recibirá la línea que se está leyendo.

*nMax*<br/>
El número máximo de caracteres que se leerán.

*rString*<br/>
Una referencia a la [CString](../../atl-mfc-shared/reference/cstringt-class.md) objeto que recibe la línea de lectura.

### <a name="return-value"></a>Valor devuelto

Puntero al búfer que contiene datos sin formato recuperados del objeto [CInternetFile.](../../mfc/reference/cinternetfile-class.md) Independientemente del tipo de datos del búfer pasado a este método, no realiza ninguna manipulación en los datos (por ejemplo, la conversión a Unicode), por lo que debe asignar los datos devueltos a la estructura que espera, como si se devolviera el tipo **void.** <strong>\*</strong>

NULL si se alcanzó el final del archivo sin leer ningún dato; o, si booleano, FALSE si se alcanzó el final del archivo sin leer ningún dato.

### <a name="remarks"></a>Observaciones

La función coloca la línea resultante en la memoria a la que hace referencia el parámetro *pstr.* Detiene la lectura de caracteres cuando alcanza el número máximo de caracteres, especificado por *nMax*. El búfer siempre recibe un carácter nulo de terminación.

Si llama `ReadString` sin llamar primero a [SetReadBufferSize](#setreadbuffersize), obtendrá un búfer de 4096 bytes.

## <a name="cinternetfileseek"></a><a name="seek"></a>CInternetFile::Buscar

Llame a esta función miembro para cambiar la posición del puntero en un archivo abierto anteriormente.

```
virtual ULONGLONG Seek(
    LONGLONG lOffset,
    UINT nFrom);
```

### <a name="parameters"></a>Parámetros

*lOffset*<br/>
Desplazamiento en bytes para mover el puntero de lectura y escritura en el archivo.

*nDe*<br/>
Referencia relativa para el desfase. Debe ser uno de los siguientes valores: 

- `CFile::begin`Mueva el puntero de archivo *lOff* bytes hacia delante desde el principio del archivo.

- `CFile::current`Mueva el puntero de archivo *lOff* bytes desde la posición actual en el archivo.

- `CFile::end`Mueva el puntero de archivo *lOff* bytes desde el final del archivo. *lOff* debe ser negativo para buscar en el archivo existente; valores positivos buscarán más allá del final del archivo.

### <a name="return-value"></a>Valor devuelto

El nuevo desplazamiento de bytes desde el principio del archivo si la posición solicitada es legal; de lo contrario, el valor es indefinido y se produce un [cInternetException](../../mfc/reference/cinternetexception-class.md) objeto.

### <a name="remarks"></a>Observaciones

La `Seek` función permite el acceso aleatorio al contenido de un archivo moviendo el puntero una cantidad especificada, absoluta o relativamente. No se lee ningún dato durante la búsqueda.

En este momento, una llamada a esta función `CHttpFile` miembro solo se admite para los datos asociados a objetos. No es compatible con solicitudes FTP o gopher. Si llama `Seek` a uno de estos servicios no compatibles, le pasará de vuelta al código de error Win32 ERROR_INTERNET_INVALID_OPERATION.

Cuando se abre un archivo, el puntero del archivo se encuentra en el desplazamiento 0, al principio del archivo.

> [!NOTE]
> El `Seek` uso puede provocar una llamada implícita a [Flush](#flush).

### <a name="example"></a>Ejemplo

  Vea el ejemplo de la implementación de la clase base ( [CFile::Seek](../../mfc/reference/cfile-class.md#seek)).

## <a name="cinternetfilesetreadbuffersize"></a><a name="setreadbuffersize"></a>CInternetFile::SetReadBufferSize

Llame a esta función miembro para establecer el `CInternetFile`tamaño del búfer de lectura temporal utilizado por un -objeto derivado.

```
BOOL SetReadBufferSize(UINT nReadSize);
```

### <a name="parameters"></a>Parámetros

*nReadSize*<br/>
Tamaño deseado del búfer en bytes.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero. Si se produce un error en la llamada, se puede llamar a la función [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) de Win32 para determinar la causa del error.

### <a name="remarks"></a>Observaciones

Las API de WinInet subyacentes no realizan el almacenamiento en búfer, así que elija un tamaño de búfer que permita a la aplicación leer los datos de forma eficaz, independientemente de la cantidad de datos que se van a leer. Si cada llamada a [Read](#read) normalmente implica un gran aount de datos (por ejemplo, cuatro o más kilobytes), no debe necesitar un búfer. Sin embargo, `Read` si llama para obtener pequeños fragmentos de datos, o si usa [ReadString](#readstring) para leer líneas individuales a la vez, un búfer de lectura mejora el rendimiento de la aplicación.

De forma `CInternetFile` predeterminada, un objeto no proporciona ningún almacenamiento en búfer para la lectura. Si llama a esta función miembro, debe asegurarse de que el archivo se ha abierto para el acceso de lectura.

Puede aumentar el tamaño del búfer en cualquier momento, pero reducir el búfer no tendrá ningún efecto. Si llama a [ReadString](#readstring) sin llamar `SetReadBufferSize`primero, obtendrá un búfer de 4096 bytes.

## <a name="cinternetfilesetwritebuffersize"></a><a name="setwritebuffersize"></a>CInternetFile::SetWriteBufferSize

Llame a esta función miembro para establecer el `CInternetFile`tamaño del búfer de escritura temporal utilizado por un -objeto derivado.

```
BOOL SetWriteBufferSize(UINT nWriteSize);
```

### <a name="parameters"></a>Parámetros

*nWriteSize*<br/>
Tamaño del búfer en bytes.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero. Si se produce un error en la llamada, se puede llamar a la función [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) de Win32 para determinar la causa del error.

### <a name="remarks"></a>Observaciones

Las API de WinInet subyacentes no realizan el almacenamiento en búfer, así que elija un tamaño de búfer que permita a la aplicación escribir datos de forma eficaz independientemente de la cantidad de datos que se escriban. Si cada llamada a [Write](#write) normalmente implica una gran cantidad de datos (por ejemplo, cuatro o más kilobytes a la vez), no debe necesitar un búfer. Sin embargo, si llama a [Write](#write) para escribir pequeños fragmentos de datos, un búfer de escritura mejora el rendimiento de la aplicación.

De forma `CInternetFile` predeterminada, un objeto no proporciona ningún almacenamiento en búfer para escribir. Si llama a esta función miembro, debe asegurarse de que el archivo se ha abierto para el acceso de escritura. Puede cambiar el tamaño del búfer de escritura en cualquier momento, pero al hacerlo se produce una llamada implícita a [Flush](#flush).

## <a name="cinternetfilewrite"></a><a name="write"></a>CInternetFile::Escribir

Llame a esta función miembro para escribir en la memoria dada, *lpvBuf*, el número especificado de bytes, *nCount*.

```
virtual void Write(
    const void* lpBuf,
    UINT nCount);
```

### <a name="parameters"></a>Parámetros

*lpBuf*<br/>
Un puntero al primer byte que se va a escribir.

*nCount*<br/>
Especifica el número de bytes que se van a escribir.

### <a name="remarks"></a>Observaciones

Si se produce algún error al escribir los datos, la función produce un [CInternetException](../../mfc/reference/cinternetexception-class.md) objeto que describe el error.

## <a name="cinternetfilewritestring"></a><a name="writestring"></a>CInternetFile::WriteString

Esta función escribe una cadena terminada en null en el archivo asociado.

```
virtual void WriteString(LPCTSTR pstr);
```

### <a name="parameters"></a>Parámetros

*Pstr*<br/>
Puntero a una cadena que contiene el contenido que se va a escribir.

### <a name="remarks"></a>Observaciones

Si se produce algún error al escribir los datos, la función produce un [CInternetException](../../mfc/reference/cinternetexception-class.md) objeto que describe el error.

## <a name="see-also"></a>Consulte también

[Clase CStdioFile](../../mfc/reference/cstdiofile-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CInternetConnection (clase)](../../mfc/reference/cinternetconnection-class.md)
