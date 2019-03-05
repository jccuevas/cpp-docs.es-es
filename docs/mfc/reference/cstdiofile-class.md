---
title: CStdioFile (clase)
ms.date: 11/04/2016
f1_keywords:
- CStdioFile
- AFX/CStdioFile
- AFX/CStdioFile::CStdioFile
- AFX/CStdioFile::Open
- AFX/CStdioFile::ReadString
- AFX/CStdioFile::Seek
- AFX/CStdioFile::WriteString
- AFX/CStdioFile::m_pStream
helpviewer_keywords:
- CStdioFile [MFC], CStdioFile
- CStdioFile [MFC], Open
- CStdioFile [MFC], ReadString
- CStdioFile [MFC], Seek
- CStdioFile [MFC], WriteString
- CStdioFile [MFC], m_pStream
ms.assetid: 88c2274c-4f0e-4327-882a-557ba4b3ae15
ms.openlocfilehash: fd42934107591905a1bbc273ee9eec4b37e58ea7
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57258793"
---
# <a name="cstdiofile-class"></a>CStdioFile (clase)

Representa un archivo de secuencia de tiempo de ejecución de C tal como lo abre la función de tiempo de ejecución [fopen](../../c-runtime-library/reference/fopen-wfopen.md).

## <a name="syntax"></a>Sintaxis

```
class CStdioFile : public CFile
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CStdioFile::CStdioFile](#cstdiofile)|Construye un `CStdioFile` objeto de un puntero de archivo o ruta de acceso.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CStdioFile::Open](#open)|Sobrecargado. Abrir está diseñado para su uso con el valor predeterminado `CStdioFile` constructor (invalidaciones [CFile::Open](../../mfc/reference/cfile-class.md#open)).|
|[CStdioFile::ReadString](#readstring)|Lee una sola línea de texto.|
|[CStdioFile::Seek](#seek)|Coloca el puntero de archivo actual.|
|[CStdioFile::WriteString](#writestring)|Escribe una sola línea de texto.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[CStdioFile::m_pStream](#m_pstream)|Contiene un puntero a un archivo abierto.|

## <a name="remarks"></a>Comentarios

Archivos de Stream se almacenan en búfer y se pueden abrir en modo de texto (valor predeterminado) o modo binario.

Modo de texto proporciona un procesamiento especial para pares de retorno de carro. Al escribir una nueva línea (0x0A) de caracteres a un modo de texto `CStdioFile` (objeto), el par de bytes (0x0D, 0x0A) se envía al archivo. Al leer, el par de bytes (0x0D, 0x0A) se traduce en un solo byte 0x0A.

El [CFile](../../mfc/reference/cfile-class.md) funciones [duplicar](../../mfc/reference/cfile-class.md#duplicate), [LockRange](../../mfc/reference/cfile-class.md#lockrange), y [UnlockRange](../../mfc/reference/cfile-class.md#unlockrange) no son compatibles con `CStdioFile`.

Si se llama a estas funciones en un `CStdioFile`, obtendrá un [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).

Para obtener más información sobre el uso de `CStdioFile`, consulte los artículos [archivos en MFC](../../mfc/files-in-mfc.md) y [manejo de archivos](../../c-runtime-library/file-handling.md) en el *referencia de la biblioteca de tiempo de ejecución*.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

`CStdioFile`

## <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

##  <a name="cstdiofile"></a>  CStdioFile::CStdioFile

Construye e inicializa un objeto `CStdioFile`.

```
CStdioFile();
CStdioFile(CAtlTransactionManager* pTM);
  CStdioFile(FILE* pOpenStream);

CStdioFile(
    LPCTSTR lpszFileName,
    UINT nOpenFlags);

CStdioFile(
    LPCTSTR lpszFileName,
    UINT nOpenFlags,
    CAtlTransactionManager* pTM);
```

### <a name="parameters"></a>Parámetros

*pOpenStream*<br/>
Especifica el puntero de archivo devuelto por una llamada a la función de tiempo de ejecución de C [fopen](../../c-runtime-library/reference/fopen-wfopen.md).

*lpszFileName*<br/>
Especifica una cadena que es la ruta de acceso al archivo deseado. La ruta de acceso puede ser relativa o absoluta.

*nOpenFlags*<br/>
Especifica opciones para la creación de archivos, uso compartido de archivos y los modos de acceso de archivo. Puede especificar varias opciones mediante el uso de la operación OR bit a bit ( **|** ) operador.

Falta una opción de modo de acceso de archivo; otros modos son opcionales. Consulte [CFile::CFile](../../mfc/reference/cfile-class.md#cfile) para obtener una lista de opciones del modo y otras marcas. En la versión 3.0 y versiones posterior de MFC, se permiten las marcas de recurso compartido.

*pTM*<br/>
Puntero al objeto CAtlTransactionManager.

### <a name="remarks"></a>Comentarios

El constructor predeterminado no adjunta un archivo a la `CStdioFile` objeto. Al usar este constructor, debe usar el `CStdioFile::Open` método para abrir un archivo y adjuntarlo a la `CStdioFile` objeto.

El único parámetro constructor asocia una secuencia de archivos abiertos para el `CStdioFile` objeto. Permite a los valores de puntero incluyen los punteros a archivos de entrada/salida predefinido *stdin*, *stdout*, o *stderr*.

Lo dos parámetros constructor crea un `CStdioFile` de objetos y abre el archivo correspondiente con la ruta de acceso dada.

Si se pasa NULL para cualquiera *pOpenStream* o *lpszFileName*, el constructor produce una `CInvalidArgException*`.

Si no se abrió o creó el archivo, el constructor produce una `CFileException*`.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCFiles#37](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_1.cpp)]

##  <a name="m_pstream"></a>  CStdioFile::m_pStream

El `m_pStream` miembro de datos es el puntero a un archivo abierto, tal como lo devuelve la función de tiempo de ejecución de C `fopen`.

```
FILE* m_pStream;
```

### <a name="remarks"></a>Comentarios

Es NULL si el archivo no se ha abierto nunca o se ha cerrado.

##  <a name="open"></a>  CStdioFile::Open

Sobrecargado. Abrir está diseñado para su uso con el valor predeterminado `CStdioFile` constructor.

```
virtual BOOL Open(
    LPCTSTR lpszFileName,
    UINT nOpenFlags,
    CFileException* pError = NULL);

virtual BOOL Open(
    LPCTSTR lpszFileName,
    UINT nOpenFlags,
    CAtlTransactionManager* pTM,
    CFileException* pError = NULL);
```

### <a name="parameters"></a>Parámetros

*lpszFileName*<br/>
Cadena que es la ruta de acceso al archivo deseado. La ruta de acceso puede ser relativa o absoluta.

*nOpenFlags*<br/>
Modo de acceso y uso compartido. Especifica la acción que se realizará al abrir el archivo. Puede combinar las opciones mediante el uso de la operación bit a bit OR (&#124;) operador. Permiso de acceso uno a y un recurso compartido de opción son necesarios; los modos de modeCreate y modeNoInherit son opcionales.

*pError*<br/>
Un puntero a un objeto de excepción de archivo existente que va a recibir el estado de una operación con errores.

*pTM*<br/>
Puntero a un `CAtlTransactionManager` objeto.

### <a name="return-value"></a>Valor devuelto

TRUE si es correcto; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

##  <a name="readstring"></a>  CStdioFile::ReadString

Lee datos de texto en un búfer, hasta un límite de *Nmáx*-1 caracteres, desde el archivo asociado con el `CStdioFile` objeto.

```
virtual LPTSTR ReadString(
    LPTSTR lpsz,
    UINT nMax);

virtual BOOL ReadString(CString& rString);
```

### <a name="parameters"></a>Parámetros

*lpsz*<br/>
Especifica un puntero a un búfer proporcionado por el usuario que va a recibir una cadena de texto terminada en null.

*nMax*<br/>
Especifica el número máximo de caracteres que se va a leer, sin contar el carácter nulo de terminación.

*rString*<br/>
Una referencia a un `CString` objeto que va a contener la cadena de resultado que devuelve la función.

### <a name="return-value"></a>Valor devuelto

Un puntero al búfer que contiene los datos de texto. NULL si se alcanzó el final de archivo sin necesidad de leer los datos; o bien, si se alcanzó boolean, FALSE si el final de archivo sin necesidad de leer los datos.

### <a name="remarks"></a>Comentarios

Lectura se ha detenido por el primer carácter de nueva línea. Si, en ese caso, que tenga menos de *Nmáx*se han leído-1 caracteres, un carácter de nueva línea se almacena en el búfer. En cualquier caso, se anexa un carácter nulo ('\0').

[CFile:: Read](../../mfc/reference/cfile-class.md#read) también está disponible para su entrada de modo de texto, pero no termina en un par de retorno de carro.

> [!NOTE]
>  El `CString` versión de esta función quita el `'\n'` si está presente; la versión LPTSTR no lo hace.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCFiles#38](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_2.cpp)]

##  <a name="seek"></a>  CStdioFile::Seek

Recoloca el puntero en un archivo abierto anteriormente.

```
virtual ULONGLONG Seek(
    LONGLONG lOff,
    UINT nFrom);
```

### <a name="parameters"></a>Parámetros

*lOff*<br/>
Número de bytes para mover el puntero.

*nFrom*<br/>
Modo de movimiento del puntero. Debe ser uno de los siguientes valores:

- `CFile::begin`: Mueva el puntero de archivo *lOff* reenvían bytes desde el principio del archivo.

- `CFile::current`: Mueva el puntero de archivo *lOff* bytes desde la posición actual en el archivo.

- `CFile::end`: Mueva el puntero de archivo *lOff* bytes desde el final del archivo. Tenga en cuenta que *lOff* debe ser negativo para buscar en las existentes archivo; positivo buscarán valores más allá del final del archivo.

### <a name="return-value"></a>Valor devuelto

Si la posición solicitada es legal, `Seek` devuelve el nuevo desplazamiento de bytes desde el principio del archivo. En caso contrario, el valor devuelto es indefinido y un `CFileException` se produce el objeto.

### <a name="remarks"></a>Comentarios

El `Seek` función permite el acceso aleatorio al contenido de un archivo, mueva el puntero una cantidad especificada, absoluta o relativa. No hay datos que se lean durante la búsqueda. Si la posición solicitada es mayor que el tamaño del archivo, la longitud del archivo se extenderá a esa posición y no se producirá ninguna excepción.

Cuando se abre un archivo, se coloca el puntero de archivo en el desplazamiento 0, el principio del archivo.

Esta implementación de `Seek` se basa en la función de biblioteca en tiempo de ejecución (CRT) `fseek`. Existen varios límites sobre el uso de `Seek` en secuencias que se abre en modo de texto. Para obtener más información, consulte [fseek, _fseeki64](../../c-runtime-library/reference/fseek-fseeki64.md).

### <a name="example"></a>Ejemplo

El ejemplo siguiente muestra cómo usar `Seek` para mover el puntero de 1000 bytes desde el principio de la `cfile` archivo. Tenga en cuenta que `Seek` no lee los datos, por lo que debe llamar posteriormente [CStdioFile::ReadString](#readstring) para leer los datos.

[!code-cpp[NVC_MFCFiles#39](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_3.cpp)]

##  <a name="writestring"></a>  CStdioFile::WriteString

Escribe datos de un búfer en el archivo asociado con el `CStdioFile` objeto.

```
virtual void WriteString(LPCTSTR lpsz);
```

### <a name="parameters"></a>Parámetros

*lpsz*<br/>
Especifica un puntero a un búfer que contiene una cadena terminada en null.

### <a name="remarks"></a>Comentarios

El carácter nulo final ( `\0`) no se escribe en el archivo. Este método escribe caracteres de nueva línea *lpsz* en el archivo como un par de carro o salto de línea.

Si desea escribir los datos que no está terminada en null en un archivo, use `CStdioFile::Write` o [CFile::Write](../../mfc/reference/cfile-class.md#write).

Este método produce una `CInvalidArgException*` si especifica NULL para el *lpsz* parámetro.

Este método produce una `CFileException*` en respuesta a errores de sistema de archivos.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCFiles#40](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_4.cpp)]

## <a name="see-also"></a>Vea también

[CFile (clase)](../../mfc/reference/cfile-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CFile (clase)](../../mfc/reference/cfile-class.md)<br/>
[CFile::Duplicate](../../mfc/reference/cfile-class.md#duplicate)<br/>
[CFile::LockRange](../../mfc/reference/cfile-class.md#lockrange)<br/>
[CFile::UnlockRange](../../mfc/reference/cfile-class.md#unlockrange)<br/>
[CNotSupportedException (clase)](../../mfc/reference/cnotsupportedexception-class.md)
