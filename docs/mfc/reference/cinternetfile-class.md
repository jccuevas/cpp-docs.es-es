---
title: CInternetFile (clase)
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
ms.openlocfilehash: 68a0a0f35d1a1f4519401080f9f207bf76c87079
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78890803"
---
# <a name="cinternetfile-class"></a>CInternetFile (clase)

Permite el acceso a archivos de sistemas remotos que utilizan protocolos de Internet.

## <a name="syntax"></a>Sintaxis

```
class CInternetFile : public CStdioFile
```

## <a name="members"></a>Members

### <a name="protected-constructors"></a>Constructores protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CInternetFile:: CInternetFile](#cinternetfile)|Construye un objeto `CInternetFile`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CInternetFile:: ABORT](#abort)|Cierra el archivo, omitiendo todas las advertencias y errores.|
|[CInternetFile:: Close](#close)|Cierra una `CInternetFile` y libera sus recursos.|
|[CInternetFile:: Flush](#flush)|Vacía el contenido del búfer de escritura y garantiza que los datos de la memoria se escriben en el equipo de destino.|
|[CInternetFile:: GetLength](#getlength)|Devuelve el tamaño del archivo.|
|[CInternetFile:: Read](#read)|Lee el número de bytes especificados.|
|[CInternetFile:: ReadString](#readstring)|Lee un flujo de caracteres.|
|[CInternetFile:: Seek](#seek)|Cambia la posición del puntero en un archivo abierto.|
|[CInternetFile:: SetReadBufferSize](#setreadbuffersize)|Establece el tamaño del búfer donde se leerán los datos.|
|[CInternetFile:: SetWriteBufferSize](#setwritebuffersize)|Establece el tamaño del búfer donde se escribirán los datos.|
|[CInternetFile:: Write](#write)|Escribe el número de bytes especificados.|
|[CInternetFile:: WriteString](#writestring)|Escribe una cadena terminada en null en un archivo.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CInternetFile:: Operator HINTERNET](#operator_hinternet)|Operador de conversión para un identificador de Internet.|

### <a name="protected-data-members"></a>Miembros de datos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CInternetFile:: m_hFile](#m_hfile)|Identificador de un archivo.|

## <a name="remarks"></a>Observaciones

Proporciona una clase base para las clases de archivo [CHttpFile](../../mfc/reference/chttpfile-class.md) y [CGopherFile (](../../mfc/reference/cgopherfile-class.md) . Nunca se crea un objeto `CInternetFile` directamente. En su lugar, cree un objeto de una de sus clases derivadas mediante una llamada a [CGopherConnection:: OpenFile](../../mfc/reference/cgopherconnection-class.md#openfile) o [CHttpConnection (:: OpenRequest](../../mfc/reference/chttpconnection-class.md#openrequest). También puede crear un objeto `CInternetFile` llamando a [CFtpConnection:: OpenFile](../../mfc/reference/cftpconnection-class.md#openfile).

Las funciones miembro de `CInternetFile` `Open`, `LockRange`, `UnlockRange`y `Duplicate` no se implementan para `CInternetFile`. Si llama a estas funciones en un objeto `CInternetFile`, obtendrá un [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).

Para obtener más información sobre cómo funciona `CInternetFile` con las otras clases de Internet de MFC, vea el artículo [programación en Internet con WinInet](../../mfc/win32-internet-extensions-wininet.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[CStdioFile](../../mfc/reference/cstdiofile-class.md)

`CInternetFile`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxinet. h

##  <a name="abort"></a>CInternetFile:: ABORT

Cierra el archivo asociado a este objeto y hace que el archivo no esté disponible para lectura o escritura.

```
virtual void Abort();
```

### <a name="remarks"></a>Observaciones

Si no ha cerrado el archivo antes de destruir el objeto, el destructor lo cierra automáticamente.

Al controlar excepciones, `Abort` difiere de [Close](#close) en dos aspectos importantes. En primer lugar, la función `Abort` no inicia una excepción en los errores porque omite los errores. En segundo lugar, `Abort` no **valida** si el archivo no se ha abierto o se ha cerrado previamente.

##  <a name="cinternetfile"></a>CInternetFile:: CInternetFile

Se llama a esta función miembro cuando se crea un objeto de `CInternetFile`.

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

*hFile*<br/>
Identificador de un archivo de Internet.

*pstrFileName*<br/>
Puntero a una cadena que contiene el nombre de archivo.

*pConnection*<br/>
Un puntero a un objeto [CInternetConnection](../../mfc/reference/cinternetconnection-class.md) .

*bReadMode*<br/>
Indica si el archivo es de solo lectura.

*hSession*<br/>
Identificador de una sesión de Internet.

*pstrServer*<br/>
Puntero a una cadena que contiene el nombre del servidor.

*dwContext*<br/>
Identificador de contexto para el objeto de `CInternetFile`. Vea [aspectos básicos de WinInet](../../mfc/wininet-basics.md) para obtener más información sobre el identificador de contexto.

### <a name="remarks"></a>Observaciones

Nunca se crea un objeto `CInternetFile` directamente. En su lugar, cree un objeto de una de sus clases derivadas mediante una llamada a [CGopherConnection:: OpenFile](../../mfc/reference/cgopherconnection-class.md#openfile) o [CHttpConnection (:: OpenRequest](../../mfc/reference/chttpconnection-class.md#openrequest). También puede crear un objeto `CInternetFile` llamando a [CFtpConnection:: OpenFile](../../mfc/reference/cftpconnection-class.md#openfile).

##  <a name="close"></a>CInternetFile:: Close

Cierra una `CInternetFile` y libera todos sus recursos.

```
virtual void Close();
```

### <a name="remarks"></a>Observaciones

Si el archivo se abrió para escritura, existe una llamada implícita a [Flush](#flush) para asegurarse de que todos los datos almacenados en búfer se escriben en el host. Debe llamar a `Close` cuando termine de utilizar un archivo.

##  <a name="flush"></a>CInternetFile:: Flush

Llame a esta función miembro para vaciar el contenido del búfer de escritura.

```
virtual void Flush();
```

### <a name="remarks"></a>Observaciones

Use `Flush` para asegurarse de que todos los datos de la memoria se han escrito realmente en el equipo de destino y para asegurarse de que se ha completado la transacción con el equipo host. `Flush` solo es efectivo en `CInternetFile` objetos abiertos para escritura.

##  <a name="getlength"></a>CInternetFile:: GetLength

Devuelve el tamaño del archivo.

```
virtual ULONGLONG GetLength() const;
```

##  <a name="m_hfile"></a>CInternetFile:: m_hFile

Identificador del archivo asociado a este objeto.

```
HINTERNET m_hFile;
```

##  <a name="operator_hinternet"></a>CInternetFile:: Operator HINTERNET

Utilice este operador para obtener el identificador de Windows para la sesión de Internet actual.

```
operator HINTERNET() const;
```

##  <a name="read"></a>CInternetFile:: Read

Llame a esta función miembro para leer en la memoria especificada, a partir de *lpvBuf*, el número de bytes especificado, *nCount*.

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

La función devuelve el número de bytes leídos realmente: un número que puede ser menor que *nCount* si el archivo finaliza. Si se produce un error al leer el archivo, la función produce un objeto [CInternetException](../../mfc/reference/cinternetexception-class.md) que describe el error. Tenga en cuenta que leer más allá del final del archivo no se considera un error y no se generará ninguna excepción.

Para asegurarse de que se recuperan todos los datos, una aplicación debe seguir llamando al método `CInternetFile::Read` hasta que el método devuelva cero.

##  <a name="readstring"></a>CInternetFile:: ReadString

Llame a esta función miembro para leer un flujo de caracteres hasta que encuentre un carácter de nueva línea.

```
virtual BOOL ReadString(CString& rString);

virtual LPTSTR ReadString(
    LPTSTR pstr,
    UINT nMax);
```

### <a name="parameters"></a>Parámetros

*pstr*<br/>
Un puntero a una cadena que recibirá la línea que se está leyendo.

*Nmáx.*<br/>
Número máximo de caracteres que se van a leer.

*rString*<br/>
Referencia al objeto [CString](../../atl-mfc-shared/reference/cstringt-class.md) que recibe la línea de lectura.

### <a name="return-value"></a>Valor devuelto

Puntero al búfer que contiene los datos sin formato recuperados del objeto [CInternetFile](../../mfc/reference/cinternetfile-class.md) . Independientemente del tipo de datos del búfer pasado a este método, no realiza manipulaciones en los datos (por ejemplo, la conversión a Unicode), por lo que debe asignar los datos devueltos a la estructura que espera, como si se devolviera el tipo de <strong>\*</strong> **void** .

ES NULL si se ha llegado al final del archivo sin leer ningún dato. o bien, si es booleano, es FALSE si se ha alcanzado el final del archivo sin leer ningún dato.

### <a name="remarks"></a>Observaciones

La función coloca la línea resultante en la memoria a la que hace referencia el parámetro *PSTR* . Deja de leer caracteres cuando alcanza el número máximo de caracteres especificado por *nmáx.* . El búfer siempre recibe un carácter nulo de terminación.

Si llama a `ReadString` sin llamar primero a [SetReadBufferSize](#setreadbuffersize), obtendrá un búfer de 4096 bytes.

##  <a name="seek"></a>CInternetFile:: Seek

Llame a esta función miembro para cambiar la posición del puntero en un archivo abierto previamente.

```
virtual ULONGLONG Seek(
    LONGLONG lOffset,
    UINT nFrom);
```

### <a name="parameters"></a>Parámetros

*lOffset*<br/>
Desplazamiento en bytes para desplazar el puntero de lectura/escritura en el archivo.

*Nde*<br/>
Referencia relativa para el desplazamiento. Debe ser uno de los siguientes valores:

- `CFile::begin` mueve el puntero de archivo *lOff* bytes hacia delante desde el principio del archivo.

- `CFile::current` mover el puntero de archivo *lOff* bytes desde la posición actual del archivo.

- `CFile::end` mueva el puntero de archivo *lOff* bytes desde el final del archivo. *lOff* debe ser negativo para buscar en el archivo existente; los valores positivos buscarán más allá del final del archivo.

### <a name="return-value"></a>Valor devuelto

Nuevo desplazamiento de bytes desde el principio del archivo si la posición solicitada es legal; de lo contrario, el valor es indefinido y se produce un objeto [CInternetException](../../mfc/reference/cinternetexception-class.md) .

### <a name="remarks"></a>Observaciones

La función `Seek` permite el acceso aleatorio al contenido de un archivo moviendo el puntero a una cantidad especificada, de forma absoluta o relativamente. En realidad, no se leen datos durante la búsqueda.

En este momento, una llamada a esta función miembro solo se admite para los datos asociados a objetos de `CHttpFile`. No se admite para las solicitudes FTP o Gopher. Si llama a `Seek` de uno de estos servicios no compatibles, pasará al código de error de Win32 ERROR_INTERNET_INVALID_OPERATION.

Cuando se abre un archivo, el puntero de archivo está en el desplazamiento 0, el principio del archivo.

> [!NOTE]
>  El uso de `Seek` puede producir una llamada implícita a [Flush](#flush).

### <a name="example"></a>Ejemplo

  Vea el ejemplo de la implementación de la clase base ( [CFile:: Seek](../../mfc/reference/cfile-class.md#seek)).

##  <a name="setreadbuffersize"></a>CInternetFile:: SetReadBufferSize

Llame a esta función miembro para establecer el tamaño del búfer de lectura temporal utilizado por un objeto derivado de `CInternetFile`.

```
BOOL SetReadBufferSize(UINT nReadSize);
```

### <a name="parameters"></a>Parámetros

*nReadSize*<br/>
Tamaño deseado del búfer en bytes.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero. Si se produce un error en la llamada, se puede llamar a la función de Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) para determinar la causa del error.

### <a name="remarks"></a>Observaciones

Las API WinInet subyacentes no realizan el almacenamiento en búfer, por lo que debe elegir un tamaño de búfer que permita que la aplicación Lea los datos de forma eficaz, independientemente de la cantidad de datos que se van a leer. Si cada llamada a [Read](#read) normalmente implica una gran aount de datos (por ejemplo, cuatro o más kilobytes), no se necesita un búfer. Sin embargo, si llama a `Read` para obtener fragmentos pequeños de datos, o si usa [ReadString](#readstring) para leer las líneas individuales de una vez, un búfer de lectura mejora el rendimiento de la aplicación.

De forma predeterminada, un objeto `CInternetFile` no proporciona ningún almacenamiento en búfer para la lectura. Si llama a esta función miembro, debe asegurarse de que el archivo se ha abierto para acceso de lectura.

Puede aumentar el tamaño del búfer en cualquier momento, pero la reducción del búfer no tendrá ningún efecto. Si llama a [ReadString](#readstring) sin llamar primero a `SetReadBufferSize`, obtendrá un búfer de 4096 bytes.

##  <a name="setwritebuffersize"></a>CInternetFile:: SetWriteBufferSize

Llame a esta función miembro para establecer el tamaño del búfer de escritura temporal utilizado por un objeto derivado de `CInternetFile`.

```
BOOL SetWriteBufferSize(UINT nWriteSize);
```

### <a name="parameters"></a>Parámetros

*nWriteSize*<br/>
El tamaño del búfer en bytes.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero. Si se produce un error en la llamada, se puede llamar a la función de Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) para determinar la causa del error.

### <a name="remarks"></a>Observaciones

Las API de WinInet subyacentes no realizan el almacenamiento en búfer, por lo que debe elegir un tamaño de búfer que permita que la aplicación escriba datos de forma eficaz independientemente de la cantidad de datos que se van a escribir. Si cada llamada para [escribir](#write) normalmente implica una gran cantidad de datos (por ejemplo, cuatro o más kilobytes a la vez), no se necesita un búfer. Sin embargo, si llama a [Write](#write) para escribir fragmentos pequeños de datos, un búfer de escritura mejora el rendimiento de la aplicación.

De forma predeterminada, un objeto `CInternetFile` no proporciona ningún almacenamiento en búfer para escribir en él. Si llama a esta función miembro, debe asegurarse de que el archivo se ha abierto para el acceso de escritura. Puede cambiar el tamaño del búfer de escritura en cualquier momento, pero si lo hace, se producirá una llamada implícita a [Flush](#flush).

##  <a name="write"></a>CInternetFile:: Write

Llame a esta función miembro para escribir en la memoria determinada, *lpvBuf*, el número de bytes especificado, *nCount*.

```
virtual void Write(
    const void* lpBuf,
    UINT nCount);
```

### <a name="parameters"></a>Parámetros

*lpBuf*<br/>
Puntero al primer byte que se va a escribir.

*nCount*<br/>
Especifica el número de bytes que se van a escribir.

### <a name="remarks"></a>Observaciones

Si se produce algún error al escribir los datos, la función produce un objeto [CInternetException](../../mfc/reference/cinternetexception-class.md) que describe el error.

##  <a name="writestring"></a>CInternetFile:: WriteString

Esta función escribe una cadena terminada en null en el archivo asociado.

```
virtual void WriteString(LPCTSTR pstr);
```

### <a name="parameters"></a>Parámetros

*pstr*<br/>
Puntero a una cadena que contiene el contenido que se va a escribir.

### <a name="remarks"></a>Observaciones

Si se produce algún error al escribir los datos, la función produce un objeto [CInternetException](../../mfc/reference/cinternetexception-class.md) que describe el error.

## <a name="see-also"></a>Consulte también

[CStdioFile (clase)](../../mfc/reference/cstdiofile-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CInternetConnection (clase)](../../mfc/reference/cinternetconnection-class.md)
