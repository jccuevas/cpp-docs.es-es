---
title: CStdioFile (clase)
ms.date: 08/29/2019
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
ms.openlocfilehash: 4b667f4121d92863335befda3a7beef74f29ad1a
ms.sourcegitcommit: e10a5feea193c249ddc5a6faba48e7c6d8784e73
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/30/2019
ms.locfileid: "70177482"
---
# <a name="cstdiofile-class"></a>CStdioFile (clase)

Representa un archivo de secuencia en tiempo de ejecución de C tal como lo abre la función de tiempo de ejecución [fopen](../../c-runtime-library/reference/fopen-wfopen.md).

## <a name="syntax"></a>Sintaxis

```
class CStdioFile : public CFile
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CStdioFile::CStdioFile](#cstdiofile)|Construye un `CStdioFile` objeto a partir de una ruta de acceso o un puntero de archivo.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CStdioFile::Open](#open)|Sobrecargado. Open está diseñado para su uso con el `CStdioFile` constructor predeterminado (invalida [CFile:: Open](../../mfc/reference/cfile-class.md#open)).|
|[CStdioFile::ReadString](#readstring)|Lee una sola línea de texto.|
|[CStdioFile::Seek](#seek)|Coloca el puntero de archivo actual.|
|[CStdioFile::WriteString](#writestring)|Escribe una sola línea de texto.|

### <a name="public-data-members"></a>Miembros de datos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CStdioFile::m_pStream](#m_pstream)|Contiene un puntero a un archivo abierto.|

## <a name="remarks"></a>Comentarios

Los archivos de secuencia se almacenan en búfer y se pueden abrir en modo de texto (valor predeterminado) o en modo binario.

El modo de texto proporciona un procesamiento especial para los pares de retorno de carro y avance de línea. Al escribir un carácter de avance de línea (nueva línea) (0x0a) en un objeto `CStdioFile` de modo de texto, el par de bytes (0x0d, 0x0a) se envía al archivo. Al leer, el par de bytes (0x0D, 0x0A) se traduce a un solo byte 0x0A.

Las funciones [CFile](../../mfc/reference/cfile-class.md) [Duplicate](../../mfc/reference/cfile-class.md#duplicate), [LockRange](../../mfc/reference/cfile-class.md#lockrange)y [UnlockRange](../../mfc/reference/cfile-class.md#unlockrange) no son compatibles `CStdioFile`con.

Si llama a estas funciones en un `CStdioFile`, obtendrá un [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).

Para obtener más información sobre `CStdioFile`el uso de, vea los artículos [archivos en MFC](../../mfc/files-in-mfc.md) y [control de archivos](../../c-runtime-library/file-handling.md) en la referencia de la *biblioteca en tiempo de ejecución*.

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
Especifica opciones para la creación de archivos, el uso compartido de archivos y los modos de acceso a archivos. Puede especificar varias opciones mediante el operador bit a bit or **|** ().

Se requiere una opción de modo de acceso a archivos; otros modos son opcionales. Vea [CFile:: CFile](../../mfc/reference/cfile-class.md#cfile) para obtener una lista de opciones de modo y otras marcas. En la versión 3,0 de MFC y versiones posteriores, se permiten marcas de uso compartido.

*pTM*<br/>
Puntero al objeto CAtlTransactionManager.

### <a name="remarks"></a>Comentarios

El constructor predeterminado no adjunta un archivo al `CStdioFile` objeto. Al usar este constructor, debe utilizar el `CStdioFile::Open` método para abrir un archivo y adjuntarlo `CStdioFile` al objeto.

El constructor de un solo parámetro adjunta una secuencia de archivos abiertos al `CStdioFile` objeto. Entre los valores de puntero permitidos se incluyen los punteros de archivo de entrada y salida predefinidos *stdin*, *stdout*o *stderr*.

El constructor de dos parámetros crea un `CStdioFile` objeto y abre el archivo correspondiente con la ruta de acceso especificada.

Si pasa NULL para *pOpenStream* o *lpszFileName*, el constructor produce una `CInvalidArgException*`excepción.

Si no se puede abrir o crear el archivo, el constructor produce una `CFileException*`excepción.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCFiles#37](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_1.cpp)]

##  <a name="m_pstream"></a>  CStdioFile::m_pStream

El `m_pStream` miembro de datos es el puntero a un archivo abierto devuelto por la función `fopen`en tiempo de ejecución de C.

```
FILE* m_pStream;
```

### <a name="remarks"></a>Comentarios

Es NULL si el archivo no se ha abierto nunca o se ha cerrado.

##  <a name="open"></a>  CStdioFile::Open

Sobrecargado. Open está diseñado para su uso con el `CStdioFile` constructor predeterminado.

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
Uso compartido y modo de acceso. Especifica la acción que se realizará al abrir el archivo. Puede combinar opciones mediante el operador bit a bit or (&#124;). Se requieren un permiso de acceso y una opción de recurso compartido; los modos modeCreate y modeNoInherit son opcionales.

*pError*<br/>
Un puntero a un objeto de excepción de archivo existente que recibirá el estado de una operación con errores.

*pTM*<br/>
Puntero a un `CAtlTransactionManager` objeto.

### <a name="return-value"></a>Valor devuelto

TRUE si es correcto; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

##  <a name="readstring"></a>  CStdioFile::ReadString

Lee datos de texto en un búfer, hasta un límite de *nmáx.* -1 caracteres, del archivo asociado `CStdioFile` al objeto.

```
virtual LPTSTR ReadString(
    LPTSTR lpsz,
    UINT nMax);

virtual BOOL ReadString(CString& rString);
```

### <a name="parameters"></a>Parámetros

*lpsz*<br/>
Especifica un puntero a un búfer proporcionado por el usuario que recibirá una cadena de texto terminada en NULL.

*Nmáx.*<br/>
Especifica el número máximo de caracteres que se van a leer, sin contar el carácter nulo de finalización.

*rString*<br/>
Referencia a un objeto `CString` que contendrá la cadena cuando la función devuelva un valor.

### <a name="return-value"></a>Valor devuelto

Puntero al búfer que contiene los datos de texto. ES NULL si se ha llegado al final del archivo sin leer ningún dato. o bien, si es booleano, FALSE si se alcanzó el final del archivo sin leer ningún dato.

### <a name="remarks"></a>Comentarios

La lectura se detiene por el primer carácter de nueva línea. Si, en ese caso, se han leído menos de *nmáx.* -1, se almacena un carácter de nueva línea en el búfer. En cualquier caso, se anexa un carácter nulo (' \ 0 ').

[CFile:: Read](../../mfc/reference/cfile-class.md#read) también está disponible para la entrada en modo de texto, pero no termina en un par de retorno de carro y avance de línea.

> [!NOTE]
>  La `CString` versión de esta función quita el `'\n'` si está presente; la versión de LPTSTR no lo hace.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCFiles#38](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_2.cpp)]

##  <a name="seek"></a>  CStdioFile::Seek

Cambia la posición del puntero en un archivo abierto previamente.

```
virtual ULONGLONG Seek(
    LONGLONG lOff,
    UINT nFrom);
```

### <a name="parameters"></a>Parámetros

*lOff*<br/>
Número de bytes que se van a trasladar al puntero.

*nFrom*<br/>
Modo de movimiento del puntero. Debe ser uno de los siguientes valores:

- `CFile::begin`: Mueva el puntero de archivo *lOff* bytes hacia delante desde el principio del archivo.

- `CFile::current`: Mueva el puntero de archivo *lOff* bytes desde la posición actual del archivo.

- `CFile::end`: Mueva el puntero de archivo *lOff* bytes desde el final del archivo. Tenga en cuenta que *lOff* debe ser negativo para buscar en el archivo existente; los valores positivos buscarán más allá del final del archivo.

### <a name="return-value"></a>Valor devuelto

Si la posición solicitada es válida `Seek` , devuelve el nuevo desplazamiento de bytes desde el principio del archivo. De lo contrario, el valor devuelto es indefinido y se produce un `CFileException` objeto.

### <a name="remarks"></a>Comentarios

La `Seek` función permite el acceso aleatorio al contenido de un archivo moviendo el puntero a una cantidad especificada, absoluta o relativamente. En realidad, no se leen datos durante la búsqueda. Si la posición solicitada es mayor que el tamaño del archivo, la longitud del archivo se extenderá a esa posición y no se producirá ninguna excepción.

Cuando se abre un archivo, el puntero de archivo se coloca en el desplazamiento 0, el principio del archivo.

Esta implementación de `Seek` se basa en la función `fseek`de biblioteca en tiempo de ejecución (CRT). Hay varios límites en el uso de `Seek` en las secuencias abiertas en modo de texto. Para obtener más información, vea [fseek, _fseeki64](../../c-runtime-library/reference/fseek-fseeki64.md).

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo `Seek` usar para pasar el puntero 1000 bytes desde el principio `cfile` del archivo. Tenga en `Seek` cuenta que no lee los datos, por lo que debe llamar a [CStdioFile:: ReadString](#readstring) posteriormente para leer los datos.

[!code-cpp[NVC_MFCFiles#39](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_3.cpp)]

##  <a name="writestring"></a>  CStdioFile::WriteString

Escribe los datos de un búfer en el archivo asociado `CStdioFile` al objeto.

```
virtual void WriteString(LPCTSTR lpsz);
```

### <a name="parameters"></a>Parámetros

*lpsz*<br/>
Especifica un puntero a un búfer que contiene una cadena terminada en NULL.

### <a name="remarks"></a>Comentarios

El carácter nulo de terminación `\0`() no se escribe en el archivo. Este método escribe los caracteres de nueva línea en *lpsz* en el archivo como un par de retorno de carro y avance de línea.

Si desea escribir datos que no terminan en null en un archivo, use `CStdioFile::Write` o [CFile:: Write](../../mfc/reference/cfile-class.md#write).

Este método produce una `CInvalidArgException*` excepción si se especifica null para el parámetro *lpsz* .

Este método produce una `CFileException*` excepción en respuesta a los errores del sistema de archivos.

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
