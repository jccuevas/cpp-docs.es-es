---
title: Clase CStdioFile
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
ms.openlocfilehash: 80ee65aa339a38b3d8434bc4c7cb977e263f037b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366014"
---
# <a name="cstdiofile-class"></a>Clase CStdioFile

Representa un archivo de secuencia en tiempo de ejecución de C abierto por la función en tiempo de ejecución [fopen](../../c-runtime-library/reference/fopen-wfopen.md).

## <a name="syntax"></a>Sintaxis

```
class CStdioFile : public CFile
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CStdioFile::CStdioFile](#cstdiofile)|Construye un `CStdioFile` objeto a partir de una ruta de acceso o puntero de archivo.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CStdioFile::Abrir](#open)|Sobrecargado. Open está diseñado para `CStdioFile` su uso con el constructor predeterminado (Overrides [CFile::Open](../../mfc/reference/cfile-class.md#open)).|
|[CStdioFile::ReadString](#readstring)|Lee una sola línea de texto.|
|[CStdioFile::Buscar](#seek)|Coloca el puntero de archivo actual.|
|[CStdioFile::WriteString](#writestring)|Escribe una sola línea de texto.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CStdioFile::m_pStream](#m_pstream)|Contiene un puntero a un archivo abierto.|

## <a name="remarks"></a>Observaciones

Los archivos de secuencia se almacenan en búfer y se pueden abrir en modo de texto (valor predeterminado) o en modo binario.

El modo de texto proporciona un procesamiento especial para los pares de avance de línea de retorno de carro. Cuando se escribe un carácter de avance de línea (nueva `CStdioFile` línea) (0x0A) en un objeto de modo de texto, el par de bytes (0x0D, 0x0A) se envía al archivo. Cuando usted lee, el par de bytes (0x0D, 0x0A) se traduce a un solo byte 0x0A.

Las funciones [CFile](../../mfc/reference/cfile-class.md) [Duplicate](../../mfc/reference/cfile-class.md#duplicate), [LockRange](../../mfc/reference/cfile-class.md#lockrange)y `CStdioFile` [UnlockRange](../../mfc/reference/cfile-class.md#unlockrange) no son compatibles con .

Si llama a estas `CStdioFile`funciones en un , obtendrá una [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).

Para obtener más `CStdioFile`información sobre el uso , vea los artículos [Archivos en MFC](../../mfc/files-in-mfc.md) y [Control](../../c-runtime-library/file-handling.md) de archivos en la Referencia de biblioteca en tiempo *de ejecución*.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

`CStdioFile`

## <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

## <a name="cstdiofilecstdiofile"></a><a name="cstdiofile"></a>CStdioFile::CStdioFile

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
Especifica el puntero de archivo devuelto por una llamada a la función en tiempo de ejecución de C [fopen](../../c-runtime-library/reference/fopen-wfopen.md).

*lpszFileName*<br/>
Especifica una cadena que es la ruta de acceso al archivo deseado. La ruta de acceso puede ser relativa o absoluta.

*nOpenFlags*<br/>
Especifica las opciones para la creación de archivos, el uso compartido de archivos y los modos de acceso a archivos. Puede especificar varias opciones mediante el **|** operador OR ( ).

Se requiere una opción de modo de acceso a archivos; otros modos son opcionales. Consulte [CFile::CFile](../../mfc/reference/cfile-class.md#cfile) para obtener una lista de opciones de modo y otras marcas. En MFC versión 3.0 y versiones posteriores, se permiten marcas de recurso compartido.

*Ptm*<br/>
Puntero a CAtlTransactionManager objeto.

### <a name="remarks"></a>Observaciones

El constructor predeterminado no adjunta `CStdioFile` un archivo al objeto. Al utilizar este constructor, `CStdioFile::Open` debe usar el método para `CStdioFile` abrir un archivo y adjuntarlo al objeto.

El constructor de un solo parámetro adjunta `CStdioFile` una secuencia de archivos abierta al objeto. Los valores de puntero permitidos incluyen los punteros de archivo de entrada/salida predefinidos *stdin*, *stdout*o *stderr*.

El constructor de dos `CStdioFile` parámetros crea un objeto y abre el archivo correspondiente con la ruta de acceso dada.

Si se pasa NULL para *pOpenStream* o *lpszFileName*, el constructor produce un `CInvalidArgException*`archivo .

Si el archivo no se puede abrir `CFileException*`o crear, el constructor produce un archivo .

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCFiles#37](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_1.cpp)]

## <a name="cstdiofilem_pstream"></a><a name="m_pstream"></a>CStdioFile::m_pStream

El `m_pStream` miembro de datos es el puntero a un archivo `fopen`abierto tal como lo devuelve la función en tiempo de ejecución de C.

```
FILE* m_pStream;
```

### <a name="remarks"></a>Observaciones

Es NULL si el archivo nunca se ha abierto o se ha cerrado.

## <a name="cstdiofileopen"></a><a name="open"></a>CStdioFile::Abrir

Sobrecargado. Open está diseñado para `CStdioFile` su uso con el constructor predeterminado.

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
Modo de acceso y uso compartido. Especifica la acción que se debe realizar al abrir el archivo. Puede combinar opciones mediante el operador OR (&#124;) bit a bit. Se requiere un permiso de acceso y una opción de recurso compartido; los modos modeCreate y modeNoInherit son opcionales.

*pError*<br/>
Puntero a un objeto de excepción de archivo existente que recibirá el estado de una operación con errores.

*Ptm*<br/>
Puntero a `CAtlTransactionManager` un objeto.

### <a name="return-value"></a>Valor devuelto

TRUE si es correcto; en caso contrario, FALSE.

### <a name="remarks"></a>Observaciones

## <a name="cstdiofilereadstring"></a><a name="readstring"></a>CStdioFile::ReadString

Lee los datos de texto en un búfer, hasta un límite de `CStdioFile` *caracteres nMax*-1, del archivo asociado al objeto.

```
virtual LPTSTR ReadString(
    LPTSTR lpsz,
    UINT nMax);

virtual BOOL ReadString(CString& rString);
```

### <a name="parameters"></a>Parámetros

*lpsz*<br/>
Especifica un puntero a un búfer proporcionado por el usuario que recibirá una cadena de texto terminada en null.

*nMax*<br/>
Especifica el número máximo de caracteres que se leerá, sin contar el carácter nulo de terminación.

*rString*<br/>
Una referencia `CString` a un objeto que contendrá la cadena cuando se devuelve la función.

### <a name="return-value"></a>Valor devuelto

Puntero al búfer que contiene los datos de texto. NULL si se alcanzó el final del archivo sin leer ningún dato; o si es booleano, FALSE si se alcanzó el final del archivo sin leer ningún dato.

### <a name="remarks"></a>Observaciones

La lectura se detiene por el primer carácter de nueva línea. Si, en ese caso, se han leído menos de *caracteres nMax*-1, se almacena un carácter de nueva línea en el búfer. En cualquier caso, se añade un carácter nulo ('-0').

[CFile::Read](../../mfc/reference/cfile-class.md#read) también está disponible para la entrada en modo de texto, pero no termina en un par de avance de línea de retorno de carro.

> [!NOTE]
> La `CString` versión de esta `'\n'` función quita el if presente; la versión LPTSTR no lo hace.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCFiles#38](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_2.cpp)]

## <a name="cstdiofileseek"></a><a name="seek"></a>CStdioFile::Buscar

Cambia la posición del puntero en un archivo abierto anteriormente.

```
virtual ULONGLONG Seek(
    LONGLONG lOff,
    UINT nFrom);
```

### <a name="parameters"></a>Parámetros

*Loff*<br/>
Número de bytes para mover el puntero.

*nDe*<br/>
Modo de movimiento del puntero. Debe ser uno de los siguientes valores: 

- `CFile::begin`: mueva el puntero de archivo *lOff* bytes hacia delante desde el principio del archivo.

- `CFile::current`: mueva el puntero de archivo *lOff* bytes desde la posición actual en el archivo.

- `CFile::end`: mueva el puntero de archivo *lOff* bytes desde el final del archivo. Tenga en cuenta que *lOff* debe ser negativo para buscar en el archivo existente; valores positivos buscarán más allá del final del archivo.

### <a name="return-value"></a>Valor devuelto

Si la posición solicitada `Seek` es legal, devuelve el nuevo desplazamiento de bytes desde el principio del archivo. De lo contrario, el valor `CFileException` devuelto es indefinido y se produce un objeto.

### <a name="remarks"></a>Observaciones

La `Seek` función permite el acceso aleatorio al contenido de un archivo moviendo el puntero una cantidad especificada, absoluta o relativamente. No se lee ningún dato durante la búsqueda. Si la posición solicitada es mayor que el tamaño del archivo, la longitud del archivo se extenderá a esa posición y no se producirá ninguna excepción.

Cuando se abre un archivo, el puntero del archivo se coloca en el desplazamiento 0, al principio del archivo.

Esta implementación se `Seek` basa en la función `fseek`Biblioteca en tiempo de ejecución (CRT). Hay varios límites en `Seek` el uso de las secuencias abiertas en modo de texto. Para obtener más información, consulte [fseek, _fseeki64](../../c-runtime-library/reference/fseek-fseeki64.md).

### <a name="example"></a>Ejemplo

En el ejemplo siguiente `Seek` se muestra cómo utilizar para mover el `cfile` puntero 1000 bytes desde el principio del archivo. Tenga `Seek` en cuenta que no lee datos, por lo que debe llamar posteriormente a [CStdioFile::ReadString](#readstring) para leer los datos.

[!code-cpp[NVC_MFCFiles#39](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_3.cpp)]

## <a name="cstdiofilewritestring"></a><a name="writestring"></a>CStdioFile::WriteString

Escribe datos de un búfer en `CStdioFile` el archivo asociado al objeto.

```
virtual void WriteString(LPCTSTR lpsz);
```

### <a name="parameters"></a>Parámetros

*lpsz*<br/>
Especifica un puntero a un búfer que contiene una cadena terminada en null.

### <a name="remarks"></a>Observaciones

El carácter nulo `\0`de terminación ( ) no se escribe en el archivo. Este método escribe caracteres de nueva línea en *lpsz* en el archivo como un par de avance de línea de retorno de carro.

Si desea escribir datos que no están terminados en `CStdioFile::Write` null en un archivo, utilice o [CFile::Write](../../mfc/reference/cfile-class.md#write).

Este método produce `CInvalidArgException*` un si especifica NULL para el *lpsz* parámetro.

Este método produce `CFileException*` una respuesta en respuesta a errores del sistema de archivos.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCFiles#40](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_4.cpp)]

## <a name="see-also"></a>Consulte también

[CFile (clase)](../../mfc/reference/cfile-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CFile (clase)](../../mfc/reference/cfile-class.md)<br/>
[CFile::Duplicate](../../mfc/reference/cfile-class.md#duplicate)<br/>
[CFile::LockRange](../../mfc/reference/cfile-class.md#lockrange)<br/>
[CFile::UnlockRange](../../mfc/reference/cfile-class.md#unlockrange)<br/>
[Clase CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)
