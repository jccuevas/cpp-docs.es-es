---
title: CFileException (clase)
ms.date: 06/09/2020
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
ms.openlocfilehash: f58ba02862e9c0f0c0c0d24797be939276ca8035
ms.sourcegitcommit: 8167c67d76de58a7c2df3b4dcbf3d53e3b151b77
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/10/2020
ms.locfileid: "84664344"
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

|NOMBRE|Descripción|
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

La `CFileException` clase incluye miembros de datos públicos que contienen el código de causa portátil y el número de error específico del sistema operativo. La clase también proporciona funciones miembro estáticas para producir excepciones de archivo y para devolver códigos de causa para errores del sistema operativo y errores en tiempo de ejecución de C.

`CFileException`los objetos se construyen y se inician en `CFile` funciones miembro y en funciones miembro de clases derivadas. Puede tener acceso a estos objetos dentro del ámbito de una expresión **catch** . Para la portabilidad, use solo el código de causa para obtener el motivo de una excepción. Para obtener más información sobre las excepciones, vea el artículo [control de excepciones (MFC)](../../mfc/exception-handling-in-mfc.md).

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

*dará*<br/>
Variable de tipo enumerado que indica la razón de la excepción. Vea [CFileException:: m_cause](#m_cause) para obtener una lista de los valores posibles.

*lOsError*<br/>
Un motivo específico del sistema operativo para la excepción, si está disponible. El parámetro *lOsError* proporciona más información de la *causa* .

*lpszArchiveName*<br/>
Apunta a una cadena que contiene el nombre del `CFile` objeto que produce la excepción.

### <a name="remarks"></a>Observaciones

No utilice este constructor directamente, sino que llame a la función global [AfxThrowFileException](exception-processing.md#afxthrowfileexception).

> [!NOTE]
> La variable *lOsError* solo se aplica a los `CFile` `CStdioFile` objetos y. La `CMemFile` clase no controla este código de error.

## <a name="cfileexceptionerrnotoexception"></a><a name="errnotoexception"></a>CFileException::ErrnoToException

Convierte un valor de error de la biblioteca en tiempo de ejecución dado en un `CFileException` valor de error enumerado.

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

## <a name="cfileexceptiongeterrormessage"></a><a name="geterrormessage"></a>CFileException::GetErrorMessage

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
[in, out] Puntero a un entero sin signo que recibe el identificador del contexto de ayuda. Si `NULL` es, no se devuelve ningún identificador.

### <a name="return-value"></a>Valor devuelto

TRUE si el método se realizó correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Observaciones

Si el búfer especificado es demasiado pequeño, el mensaje de error se trunca.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se utiliza `CFileException::GetErrorMessage`.

[!code-cpp[NVC_MFCExceptions#22](../../mfc/codesnippet/cpp/cfileexception-class_2.cpp)]

## <a name="cfileexceptionm_cause"></a><a name="m_cause"></a>CFileException:: m_cause

Contiene los valores definidos por un tipo enumerado `CFileException`.

```
int m_cause;
```

### <a name="remarks"></a>Observaciones

Este miembro de datos es una variable pública de tipo **int**. Los enumeradores y su significado son los siguientes:

| Error | Valor y significado |
|--|--|
| `CFileException::none` |    0: no se ha producido ningún error. |
| `CFileException::genericException` |    1: se ha producido un error no especificado. |
| `CFileException::fileNotFound` |    2: no se pudo encontrar el archivo. |
| `CFileException::badPath` |    3: la ruta de acceso no es válida parcial o totalmente. |
| `CFileException::tooManyOpenFiles` |    4: se superó el número de archivos abiertos permitido. |
| `CFileException::accessDenied` |    5: no se pudo acceder al archivo. |
| `CFileException::invalidFile` |    6: se produjo un intento de usar un identificador de archivos no válido. |
| `CFileException::removeCurrentDir` |    7: el directorio de trabajo actual no se puede quitar. |
| `CFileException::directoryFull` |    8: no hay más entradas de directorio. |
| `CFileException::badSeek` |    9: se produjo un error al intentar establecer el puntero de archivo. |
| `CFileException::hardIO` |    10: se produjo un error de hardware. |
| `CFileException::sharingViolation` |    11: SHARE.EXE no se cargó o una región compartida estaba bloqueada. |
| `CFileException::lockViolation` |    12: se produjo un intento de bloquear una región que ya estaba bloqueada. |
| `CFileException::diskFull` | 13: el disco está lleno. |
| `CFileException::endOfFile` | 14: se alcanzó el final del archivo. |

    > [!NOTE]
    >  These `CFileException` cause enumerators are distinct from the `CArchiveException` cause enumerators.

    > [!NOTE]
    > `CArchiveException::generic` is deprecated. Use `genericException` instead. If **generic** is used in an application and built with /clr, the resulting syntax errors are not easy to decipher.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCFiles#30](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_3.cpp)]

## <a name="cfileexceptionm_loserror"></a><a name="m_loserror"></a>CFileException:: m_lOsError

Contiene el código de error del sistema operativo para esta excepción.

```
LONG m_lOsError;
```

### <a name="remarks"></a>Observaciones

Consulte el manual técnico del sistema operativo para obtener una lista de códigos de error. Este miembro de datos es una variable pública de tipo LONG.

## <a name="cfileexceptionm_strfilename"></a><a name="m_strfilename"></a>CFileException:: m_strFileName

Contiene el nombre del archivo para esta condición de excepción.

```
CString m_strFileName;
```

## <a name="cfileexceptionoserrortoexception"></a><a name="oserrortoexception"></a>CFileException::OsErrorToException

Devuelve un enumerador que corresponde a un valor *lOsError* determinado. Si el código de error es desconocido, la función devuelve `CFileException::generic` .

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

Construye un `CFileException` objeto que corresponde a un valor *nErrno* determinado y, a continuación, produce la excepción.

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

## <a name="cfileexceptionthrowoserror"></a><a name="throwoserror"></a>CFileException::ThrowOsError

Produce una excepción `CFileException` correspondiente a un valor *lOsError* determinado. Si el código de error es desconocido, la función produce una excepción codificada como `CFileException::generic` .

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
