---
title: CFileException (clase)
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
ms.openlocfilehash: 2d1025ca33d5641982ba52f1ac539db85df3bfd5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373892"
---
# <a name="cfileexception-class"></a>CFileException (clase)

Representa una condición de excepción relacionada con archivo.

## <a name="syntax"></a>Sintaxis

```
class CFileException : public CException
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CFileException::CFileException](#cfileexception)|Construye un objeto `CFileException`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CFileException::ErrnoToException](#errnotoexception)|Devuelve el código de causa correspondiente a un número de error en tiempo de ejecución.|
|[CFileException::GetErrorMessage](#geterrormessage)|Recupera el mensaje que describe una excepción.|
|[CFileException::OsErrorToException](#oserrortoexception)|Devuelve un código de causa correspondiente a un código de error del sistema operativo.|
|[CFileException::ThrowErrno](#throwerrno)|Produce una excepción de archivo basada en un número de error en tiempo de ejecución.|
|[CFileException::ThrowOsError](#throwoserror)|Produce una excepción de archivo basada en un número de error del sistema operativo.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CFileException::m_cause](#m_cause)|Contiene código portátil correspondiente a la causa de excepción.|
|[CFileException::m_lOsError](#m_loserror)|Contiene el número de error del sistema operativo relacionado.|
|[CFileException::m_strFileName](#m_strfilename)|Contiene el nombre del archivo para esta excepción.|

## <a name="remarks"></a>Observaciones

La `CFileException` clase incluye miembros de datos públicos que contienen el código de causa portátil y el número de error específico del sistema operativo. La clase también proporciona funciones miembro estáticas para producir excepciones de archivo y para devolver códigos de causa para errores del sistema operativo y errores en tiempo de ejecución de C.

`CFileException`objetos se construyen y `CFile` se producen en funciones miembro y en funciones miembro de clases derivadas. Puede tener acceso a estos objetos dentro del ámbito de una expresión **CATCH.** Para la portabilidad, use solo el código de causa para obtener el motivo de una excepción. Para obtener más información acerca de las excepciones, vea el artículo Control de [excepciones (MFC)](../../mfc/exception-handling-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`CFileException`

## <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

## <a name="cfileexceptioncfileexception"></a><a name="cfileexception"></a>CFileException::CFileException

Construye un `CFileException` objeto que almacena el código de causa y el código del sistema operativo en el objeto.

```
CFileException(
    int cause = CFileException::none,
    LONG lOsError = -1,
    LPCTSTR lpszArchiveName = NULL);
```

### <a name="parameters"></a>Parámetros

*Causa*<br/>
Una variable de tipo enumerada que indica el motivo de la excepción. Consulte [CFileException::m_cause](#m_cause) para obtener una lista de los valores posibles.

*lOsError*<br/>
Un motivo específico del sistema operativo para la excepción, si está disponible. El parámetro *lOsError* proporciona más información que *causa.*

*lpszArchiveName*<br/>
Apunta a una cadena que `CFile` contiene el nombre del objeto que causa la excepción.

### <a name="remarks"></a>Observaciones

No utilice este constructor directamente, sino que llame a la función global [AfxThrowFileException](exception-processing.md#afxthrowfileexception).

> [!NOTE]
> La variable *lOsError* `CFile` solo `CStdioFile` se aplica a y objects. La `CMemFile` clase no controla este código de error.

## <a name="cfileexceptionerrnotoexception"></a><a name="errnotoexception"></a>CFileException::ErrnoToException

Convierte un valor de error de `CFileException` biblioteca en tiempo de ejecución determinado en un valor de error enumerado.

```
static int PASCAL ErrnoToException(int nErrno);
```

### <a name="parameters"></a>Parámetros

*nErrno*<br/>
Un código de error entero tal como se define en el archivo de inclusión en tiempo de ejecución ERRNO. H.

### <a name="return-value"></a>Valor devuelto

Valor enumerado que corresponde a un valor de error de biblioteca en tiempo de ejecución determinado.

### <a name="remarks"></a>Observaciones

Consulte [CFileException::m_cause](#m_cause) para obtener una lista de los posibles valores enumerados.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCFiles#26](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_1.cpp)]

## <a name="cfileexceptiongeterrormessage"></a><a name="geterrormessage"></a>CFileException::GetErrorMessage

Recupera texto que describe una excepción.

```
virtual BOOL GetErrorMessage(
    LPTSTR lpszError,
    UINT nMaxError,
    PUINT pnHelpContext = NULL) const;
```

### <a name="parameters"></a>Parámetros

*lpszError*<br/>
[adentro, fuera] Puntero a un búfer que recibe un mensaje de error.

*nMaxError*<br/>
[en] El número máximo de caracteres que puede contener el búfer especificado. Esto incluye el carácter nulo de terminación.

*pnHelpContext*<br/>
[adentro, fuera] Puntero a un entero sin signo que recibe el identificador de contexto de ayuda. Si `NULL`, no se devuelve ningún ID.

### <a name="return-value"></a>Valor devuelto

TRUESi el método se realizó correctamente; de lo contrario FALSO.

### <a name="remarks"></a>Observaciones

Si el búfer especificado es demasiado pequeño, el mensaje de error se trunca.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se utiliza `CFileException::GetErrorMessage`.

[!code-cpp[NVC_MFCExceptions#22](../../mfc/codesnippet/cpp/cfileexception-class_2.cpp)]

## <a name="cfileexceptionm_cause"></a><a name="m_cause"></a>CFileException::m_cause

Contiene los valores definidos por un tipo enumerado `CFileException`.

```
int m_cause;
```

### <a name="remarks"></a>Observaciones

Este miembro de datos es una variable pública de tipo **int**. Los enumeradores y sus significados son los siguientes:

- `CFileException::none`0: No se ha producido ningún error.

- `CFileException::genericException`1: Se ha producido un error no especificado.

- `CFileException::fileNotFound`2: No se pudo encontrar el archivo.

- `CFileException::badPath`3: Todo o parte de la ruta no es válida.

- `CFileException::tooManyOpenFiles`4: Se ha superado el número permitido de archivos abiertos.

- `CFileException::accessDenied`5: No se pudo acceder al archivo.

- `CFileException::invalidFile`6: Se ha intentado utilizar un identificador de archivo no válido.

- `CFileException::removeCurrentDir`7: El directorio de trabajo actual no se puede quitar.

- `CFileException::directoryFull`8: No hay más entradas de directorio.

- `CFileException::badSeek`9: Se ha producido un error al intentar establecer el puntero del archivo.

- `CFileException::hardIO`10: Se ha producido un error de hardware.

- `CFileException::sharingViolation`11: COMPARTIR. EXE no se cargó o se ha bloqueado una región compartida.

- `CFileException::lockViolation`12: Hubo un intento de bloquear una región que ya estaba bloqueada.

- `CFileException::diskFull`14: El disco está lleno.

- `CFileException::endOfFile`15: Se alcanzó el final del archivo.

    > [!NOTE]
    >  Estos enumeradores de causa de `CFileException` son distintos de los enumeradores de causa de `CArchiveException`.

    > [!NOTE]
    > `CArchiveException::generic` está desusada. En su lugar, use `genericException`. Si se utiliza **genérico** en una aplicación y se compila con /clr, los errores de sintaxis resultantes no son fáciles de descifrar.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCFiles#30](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_3.cpp)]

## <a name="cfileexceptionm_loserror"></a><a name="m_loserror"></a>CFileException::m_lOsError

Contiene el código de error del sistema operativo para esta excepción.

```
LONG m_lOsError;
```

### <a name="remarks"></a>Observaciones

Consulte el manual técnico del sistema operativo para obtener una lista de códigos de error. Este miembro de datos es una variable pública de tipo LONG.

## <a name="cfileexceptionm_strfilename"></a><a name="m_strfilename"></a>CFileException::m_strFileName

Contiene el nombre del archivo para esta condición de excepción.

```
CString m_strFileName;
```

## <a name="cfileexceptionoserrortoexception"></a><a name="oserrortoexception"></a>CFileException::OsErrorToException

Devuelve un enumerador que corresponde a un valor *de lOsError* determinado. Si el código de error es `CFileException::generic`desconocido, la función devuelve .

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

## <a name="cfileexceptionthrowerrno"></a><a name="throwerrno"></a>CFileException::ThrowErrno

Construye un `CFileException` objeto correspondiente a un determinado *nErrno* valor y, a continuación, produce la excepción.

```
static void PASCAL ThrowErrno(int nErrno, LPCTSTR lpszFileName = NULL);
```

### <a name="parameters"></a>Parámetros

*nErrno*<br/>
Un código de error entero tal como se define en el archivo de inclusión en tiempo de ejecución ERRNO. H.

*lpszFileName*<br/>
Puntero a la cadena que contiene el nombre del archivo que causó la excepción, si está disponible.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCFiles#28](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_5.cpp)]

## <a name="cfileexceptionthrowoserror"></a><a name="throwoserror"></a>CFileException::ThrowOsError

Produce un `CFileException` correspondiente a un *valor de lOsError* determinado. Si el código de error es desconocido, la `CFileException::generic`función produce una excepción codificada como .

```
static void PASCAL ThrowOsError(LONG lOsError, LPCTSTR lpszFileName = NULL);
```

### <a name="parameters"></a>Parámetros

*lOsError*<br/>
Un código de error específico del sistema operativo.

*lpszFileName*<br/>
Puntero a la cadena que contiene el nombre del archivo que causó la excepción, si está disponible.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCFiles#29](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_6.cpp)]

## <a name="see-also"></a>Consulte también

[Clase CException](../../mfc/reference/cexception-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Procesamiento de excepciones](../../mfc/reference/exception-processing.md)
