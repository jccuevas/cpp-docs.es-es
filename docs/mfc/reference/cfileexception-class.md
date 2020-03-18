---
title: Clase CFileException
ms.date: 11/04/2016
f1_keywords:
- CFileException
- AFX/CFileException
- AFX/CFileException::CFileException
- AFX/CFileException::ErrnoToException
- AFX/CFileException::GetErrorMessage
- AFX/CFileException::OsErrorToException
- AFX/CFileException::ThrowErrno
- AFX/CFileException::ThrowOsError
- AFX/CFileException::m_cause
- AFX/CFileException::m_lOsError
- AFX/CFileException::m_strFileName
helpviewer_keywords:
- CFileException [MFC], CFileException
- CFileException [MFC], ErrnoToException
- CFileException [MFC], GetErrorMessage
- CFileException [MFC], OsErrorToException
- CFileException [MFC], ThrowErrno
- CFileException [MFC], ThrowOsError
- CFileException [MFC], m_cause
- CFileException [MFC], m_lOsError
- CFileException [MFC], m_strFileName
ms.assetid: f6491bb9-bfbc-42fd-a952-b33f9b62323f
ms.openlocfilehash: a3514c76d4136fe2bc0b096cc382e6f7f4dd3392
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79424420"
---
# <a name="cfileexception-class"></a>Clase CFileException

Representa una condición de excepción relacionada con archivo.

## <a name="syntax"></a>Sintaxis

```
class CFileException : public CException
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CFileException::CFileException](#cfileexception)|Construye un objeto `CFileException`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CFileException::ErrnoToException](#errnotoexception)|Devuelve el código que corresponde a un número de error en tiempo de ejecución.|
|[CFileException::GetErrorMessage](#geterrormessage)|Recupera el mensaje que describe una excepción.|
|[CFileException::OsErrorToException](#oserrortoexception)|Devuelve un código de causa correspondiente a un código de error del sistema operativo.|
|[CFileException::ThrowErrno](#throwerrno)|Produce una excepción de archivo basada en un número de error en tiempo de ejecución.|
|[CFileException::ThrowOsError](#throwoserror)|Produce una excepción de archivo basada en un número de error del sistema operativo.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CFileException:: m_cause](#m_cause)|Contiene código portable que corresponde a la causa de la excepción.|
|[CFileException:: m_lOsError](#m_loserror)|Contiene el número de error del sistema operativo relacionado.|
|[CFileException:: m_strFileName](#m_strfilename)|Contiene el nombre del archivo para esta excepción.|

## <a name="remarks"></a>Observaciones

La clase `CFileException` incluye miembros de datos públicos que contienen el código de causa portátil y el número de error específico del sistema operativo. La clase también proporciona funciones miembro estáticas para producir excepciones de archivo y para devolver códigos de causa para errores del sistema operativo y errores en tiempo de ejecución de C.

`CFileException` objetos se construyen y se producen en `CFile` funciones miembro y en funciones miembro de clases derivadas. Puede tener acceso a estos objetos dentro del ámbito de una expresión **catch** . Para la portabilidad, use solo el código de causa para obtener el motivo de una excepción. Para obtener más información sobre las excepciones, vea el artículo [control de excepciones (MFC)](../../mfc/exception-handling-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CException (](../../mfc/reference/cexception-class.md)

`CFileException`

## <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

##  <a name="cfileexception"></a>CFileException::CFileException

Construye un objeto `CFileException` que almacena el código de la causa y el código del sistema operativo en el objeto.

```
CFileException(
    int cause = CFileException::none,
    LONG lOsError = -1,
    LPCTSTR lpszArchiveName = NULL);
```

### <a name="parameters"></a>Parámetros

*cause*<br/>
Variable de tipo enumerado que indica la razón de la excepción. Vea [CFileException:: m_cause](#m_cause) para obtener una lista de los valores posibles.

*lOsError*<br/>
Un motivo específico del sistema operativo para la excepción, si está disponible. El parámetro *lOsError* proporciona más información de la *causa* .

*lpszArchiveName*<br/>
Apunta a una cadena que contiene el nombre del objeto `CFile` que produce la excepción.

### <a name="remarks"></a>Observaciones

No utilice este constructor directamente, sino que llame a la función global [AfxThrowFileException](exception-processing.md#afxthrowfileexception).

> [!NOTE]
>  La variable *lOsError* solo se aplica a los objetos `CFile` y `CStdioFile`. La clase `CMemFile` no controla este código de error.

##  <a name="errnotoexception"></a>CFileException::ErrnoToException

Convierte un valor de error de la biblioteca en tiempo de ejecución dado en un valor de error enumerado `CFileException`.

```
static int PASCAL ErrnoToException(int nErrno);
```

### <a name="parameters"></a>Parámetros

*nErrno*<br/>
Un código de error entero, tal como se define en el archivo de inclusión en tiempo de ejecución ERRNO. C.

### <a name="return-value"></a>Valor devuelto

Valor enumerado que corresponde a un valor de error de la biblioteca en tiempo de ejecución determinado.

### <a name="remarks"></a>Observaciones

Vea [CFileException:: m_cause](#m_cause) para obtener una lista de los valores enumerados posibles.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCFiles#26](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_1.cpp)]

##  <a name="geterrormessage"></a>CFileException::GetErrorMessage

Recupera el texto que describe una excepción.

```
virtual BOOL GetErrorMessage(
    LPTSTR lpszError,
    UINT nMaxError,
    PUINT pnHelpContext = NULL) const;
```

### <a name="parameters"></a>Parámetros

*lpszError*<br/>
[in, out] Puntero a un búfer que recibe un mensaje de error.

*nMaxError*<br/>
de Número máximo de caracteres que puede contener el búfer especificado. Esto incluye el carácter nulo de terminación.

*pnHelpContext*<br/>
[in, out] Puntero a un entero sin signo que recibe el identificador del contexto de ayuda. Si `NULL`, no se devuelve ningún identificador.

### <a name="return-value"></a>Valor devuelto

TRUE si el método se realizó correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Observaciones

Si el búfer especificado es demasiado pequeño, el mensaje de error se trunca.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se utiliza `CFileException::GetErrorMessage`.

[!code-cpp[NVC_MFCExceptions#22](../../mfc/codesnippet/cpp/cfileexception-class_2.cpp)]

##  <a name="m_cause"></a>CFileException:: m_cause

Contiene los valores definidos por un tipo enumerado `CFileException`.

```
int m_cause;
```

### <a name="remarks"></a>Observaciones

Este miembro de datos es una variable pública de tipo **int**. Los enumeradores y su significado son los siguientes:

- `CFileException::none` 0: no se ha producido ningún error.

- `CFileException::genericException` 1: se ha producido un error no especificado.

- `CFileException::fileNotFound` 2: no se encontró el archivo.

- `CFileException::badPath` 3: todo o parte de la ruta de acceso no es válido.

- `CFileException::tooManyOpenFiles` 4: se superó el número permitido de archivos abiertos.

- `CFileException::accessDenied` 5: no se pudo obtener acceso al archivo.

- `CFileException::invalidFile` 6: se produjo un intento de usar un identificador de archivo no válido.

- `CFileException::removeCurrentDir` 7: no se puede quitar el directorio de trabajo actual.

- `CFileException::directoryFull` 8: no hay más entradas de directorio.

- `CFileException::badSeek` 9: error al intentar establecer el puntero de archivo.

- `CFileException::hardIO` 10: se produjo un error de hardware.

- `CFileException::sharingViolation` 11: compartir. EXE no se cargó o se bloqueó una región compartida.

- `CFileException::lockViolation` 12: se produjo un intento de bloquear una región que ya estaba bloqueada.

- `CFileException::diskFull` 14: el disco está lleno.

- `CFileException::endOfFile` 15: se alcanzó el final del archivo.

    > [!NOTE]
    >  Estos enumeradores de causa de `CFileException` son distintos de los enumeradores de causa de `CArchiveException`.

    > [!NOTE]
    > `CArchiveException::generic` está desusada. En su lugar, use `genericException`. Si se usa **Generic** en una aplicación y se genera con/CLR, los errores de sintaxis resultantes no son fáciles de descifrar.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCFiles#30](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_3.cpp)]

##  <a name="m_loserror"></a>CFileException:: m_lOsError

Contiene el código de error del sistema operativo para esta excepción.

```
LONG m_lOsError;
```

### <a name="remarks"></a>Observaciones

Consulte el manual técnico del sistema operativo para obtener una lista de códigos de error. Este miembro de datos es una variable pública de tipo LONG.

##  <a name="m_strfilename"></a>CFileException:: m_strFileName

Contiene el nombre del archivo para esta condición de excepción.

```
CString m_strFileName;
```

##  <a name="oserrortoexception"></a>CFileException::OsErrorToException

Devuelve un enumerador que corresponde a un valor *lOsError* determinado. Si el código de error es desconocido, la función devuelve `CFileException::generic`.

```
static int PASCAL OsErrorToException(LONG lOsError);
```

### <a name="parameters"></a>Parámetros

*lOsError*<br/>
Un código de error específico del sistema operativo.

### <a name="return-value"></a>Valor devuelto

Valor enumerado que corresponde a un valor de error del sistema operativo determinado.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCFiles#27](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_4.cpp)]

##  <a name="throwerrno"></a>CFileException::ThrowErrno

Construye un objeto `CFileException` correspondiente a un valor *nErrno* determinado y, a continuación, produce la excepción.

```
static void PASCAL ThrowErrno(int nErrno, LPCTSTR lpszFileName = NULL);
```

### <a name="parameters"></a>Parámetros

*nErrno*<br/>
Un código de error entero, tal como se define en el archivo de inclusión en tiempo de ejecución ERRNO. C.

*lpszFileName*<br/>
Un puntero a la cadena que contiene el nombre del archivo que produjo la excepción, si está disponible.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCFiles#28](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_5.cpp)]

##  <a name="throwoserror"></a>CFileException::ThrowOsError

Produce una `CFileException` correspondiente a un valor *lOsError* determinado. Si el código de error es desconocido, la función produce una excepción codificada como `CFileException::generic`.

```
static void PASCAL ThrowOsError(LONG lOsError, LPCTSTR lpszFileName = NULL);
```

### <a name="parameters"></a>Parámetros

*lOsError*<br/>
Un código de error específico del sistema operativo.

*lpszFileName*<br/>
Un puntero a la cadena que contiene el nombre del archivo que produjo la excepción, si está disponible.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCFiles#29](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_6.cpp)]

## <a name="see-also"></a>Consulte también

[CException (clase)](../../mfc/reference/cexception-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Procesamiento de excepciones](../../mfc/reference/exception-processing.md)
