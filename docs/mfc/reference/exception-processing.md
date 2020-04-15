---
title: Procesamiento de excepciones
ms.date: 11/04/2016
helpviewer_keywords:
- macros [MFC], exception handling
- DAO (Data Access Objects), exceptions [MFC]
- OLE exceptions [MFC], MFC functions
- exceptions [MFC], processing
- exception macros [MFC]
- termination functions, MFC
- MFC, exceptions
- exceptions [MFC], MFC throwing functions
ms.assetid: 26d4457c-8350-48f5-916e-78f919787c30
ms.openlocfilehash: d819c170f47ea259e776bce6db0a6971e3f54bec
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365714"
---
# <a name="exception-processing"></a>Procesamiento de excepciones

Cuando se ejecuta un programa, pueden producirse una serie de condiciones anormales y errores llamados "excepciones". Estos pueden incluir quedarse sin memoria, errores de asignación de recursos y no encontrar archivos.

La biblioteca Microsoft Foundation Class utiliza un esquema de control de excepciones que se modela estrechamente según el propuesto por el comité de estándares ANSI para C++. Se debe configurar un controlador de excepciones antes de llamar a una función que pueda encontrar una situación anormal. Si la función encuentra una condición anormal, produce una excepción y el control se pasa al controlador de excepciones.

Varias macros incluidas con la biblioteca Microsoft Foundation Class configurarán controladores de excepciones. Otras funciones globales ayudan a producir excepciones especializadas y terminar programas, si es necesario. Estas macros y funciones globales se dividen en las siguientes categorías:

- Macros de excepción, que estructuran el controlador de excepciones.

- Funciones de lanzamiento de excepciones), que generan excepciones de tipos específicos.

- Funciones de terminación, que causan la terminación del programa.

Para obtener ejemplos y más detalles, consulte el artículo [Excepciones](../../mfc/exception-handling-in-mfc.md).

### <a name="exception-macros"></a>Macros de excepción

|||
|-|-|
|[Tratar](#try)|Designa un bloque de código para el procesamiento de excepciones.|
|[atrapar](#catch)|Designa un bloque de código para detectar una excepción del bloque **TRY** anterior.|
|[CATCH_ALL](#catch_all)|Designa un bloque de código para detectar todas las excepciones del bloque **TRY** anterior.|
|[AND_CATCH](#and_catch)|Designa un bloque de código para detectar tipos de excepción adicionales del bloque **TRY** anterior.|
|[AND_CATCH_ALL](#and_catch_all)|Designa un bloque de código para detectar todos los demás tipos de excepción adicionales detectados en un bloque **TRY** anterior.|
|[END_CATCH](#end_catch)|Finaliza el último bloque de código **CATCH** o **AND_CATCH.**|
|[END_CATCH_ALL](#end_catch_all)|Finaliza el último bloque de código **CATCH_ALL.**|
|[THROW](#throw)|Produce una excepción especificada.|
|[THROW_LAST](#throw_last)|Produce la excepción controlada actualmente en el siguiente controlador externo.|

### <a name="exception-throwing-functions"></a>Funciones de lanzamiento de excepciones

|||
|-|-|
|[AfxThrowArchiveException](#afxthrowarchiveexception)|Produce una excepción de archivo.|
|[AfxThrowFileException](#afxthrowfileexception)|Produce una excepción de archivo.|
|[AfxThrowInvalidArgException](#afxthrowinvalidargexception)|Produce una excepción de argumento no válido.|
|[AfxThrowMemoryException](#afxthrowmemoryexception)|Produce una excepción de memoria.|
|[AfxThrowNotSupportedException](#afxthrownotsupportedexception)|Produce una excepción no admitida.|
|[AfxThrowResourceException](#afxthrowresourceexception)|Produce una excepción de windows no encontrada por recursos.|
|[AfxThrowUserException](#afxthrowuserexception)|Produce una excepción en una acción de programa iniciada por el usuario.|

MFC proporciona dos funciones de lanzamiento de excepciones específicamente para excepciones OLE:

### <a name="ole-exception-functions"></a>Funciones de excepción OLE

|||
|-|-|
|[AfxThrowOleDispatchException](#afxthrowoledispatchexception)|Produce una excepción dentro de una función de automatización OLE.|
|[AfxThrowOleException](#afxthrowoleexception)|Produce una excepción OLE.|

Para admitir excepciones de base de datos, las clases de base de datos proporcionan dos clases `CDBException` de excepción y `CDaoException`, y funciones globales para admitir los tipos de excepción:

### <a name="dao-exception-functions"></a>Funciones de excepción DAO

|||
|-|-|
|[AfxThrowDAOException](#afxthrowdaoexception)|Produce una [CDaoException](../../mfc/reference/cdaoexception-class.md) desde su propio código.|
|[AfxThrowDBException](#afxthrowdbexception)|Produce una [CDBException](../../mfc/reference/cdbexception-class.md) desde su propio código.|

MFC proporciona la siguiente función de terminación:

### <a name="termination-functions"></a>Funciones de terminación

|||
|-|-|
|[AfxAbort](#afxabort)|Se llama para terminar una aplicación cuando se produce un error grave.|

## <a name="try"></a><a name="try"></a>Tratar

Configura un bloque **TRY.**

```
TRY
```

### <a name="remarks"></a>Observaciones

Un bloque **TRY** identifica un bloque de código que podría producir excepciones. Esas excepciones se controlan en los siguientes bloques **CATCH** y **AND_CATCH.** Se permite la recursividad: las excepciones se pueden pasar a un bloque **TRY** externo, ya sea ignorándolas o utilizando la macro THROW_LAST. Finalice el bloque **TRY** con una macro END_CATCH o END_CATCH_ALL.

Para obtener más información, consulte el artículo [Excepciones](../../mfc/exception-handling-in-mfc.md).

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CATCH](#catch).

### <a name="requirements"></a>Requisitos

Encabezado: afx.h

## <a name="catch"></a><a name="catch"></a>atrapar

Define un bloque de código que detecta el primer tipo de excepción producido en el bloque **TRY** anterior.

```
CATCH(exception_class, exception_object_pointer_name)
```

### <a name="parameters"></a>Parámetros

*exception_class*<br/>
Especifica el tipo de excepción que se va a probar. Para obtener una lista de clases de excepción estándar, vea la clase [CException](../../mfc/reference/cexception-class.md).

*exception_object_pointer_name*<br/>
Especifica un nombre para un puntero de objeto de excepción que creará la macro. Puede utilizar el nombre del puntero para tener acceso al objeto de excepción dentro del bloque **CATCH.** Esta variable se declara por usted.

### <a name="remarks"></a>Observaciones

El código de procesamiento de excepciones puede interrogar el objeto de excepción, si procede, para obtener más información sobre la causa específica de la excepción. Invoque la macro THROW_LAST para desplazar el procesamiento al siguiente marco de excepción externo. Finalice el bloque **TRY** con una macro END_CATCH.

Si *exception_class* es `CException`la clase , se detectarán todos los tipos de excepción. Puede usar el [CObject::IsKindOf](../../mfc/reference/cobject-class.md#iskindof) función miembro para determinar qué excepción específica se ha producido. Una mejor manera de detectar varios tipos de excepciones es usar **instrucciones AND_CATCH** secuenciales, cada una con un tipo de excepción diferente.

La macro crea el puntero de objeto de excepción. No es necesario que lo declare usted mismo.

> [!NOTE]
> El bloque **CATCH** se define como un ámbito C++ delineado por llaves. Si declara variables en este ámbito, solo son accesibles dentro de ese ámbito. Esto también se aplica a *exception_object_pointer_name*.

Para obtener más información sobre las excepciones y la macro CATCH, vea el artículo [Excepciones](../../mfc/exception-handling-in-mfc.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCExceptions#26](../../mfc/codesnippet/cpp/exception-processing_1.cpp)]

## <a name="catch_all"></a><a name="catch_all"></a>CATCH_ALL

Define un bloque de código que detecta todos los tipos de excepción producidos en el bloque **TRY** anterior.

```
CATCH_ALL(exception_object_pointer_name)
```

### <a name="parameters"></a>Parámetros

*exception_object_pointer_name*<br/>
Especifica un nombre para un puntero de objeto de excepción que creará la macro. Puede utilizar el nombre del puntero para `CATCH_ALL` tener acceso al objeto de excepción dentro del bloque. Esta variable se declara por usted.

### <a name="remarks"></a>Observaciones

El código de procesamiento de excepciones puede interrogar el objeto de excepción, si procede, para obtener más información sobre la causa específica de la excepción. Invoque la macro para desplazar el `THROW_LAST` procesamiento al siguiente marco de excepción externo. Si utiliza **CATCH_ALL**, finalice el bloque **TRY** con una macro END_CATCH_ALL.

> [!NOTE]
> El bloque **CATCH_ALL** se define como un ámbito C++ delineado por llaves. Si declara variables en este ámbito, solo son accesibles dentro de ese ámbito.

Para obtener más información sobre las excepciones, vea el artículo [Excepciones](../../mfc/exception-handling-in-mfc.md).

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CFile::Abort](../../mfc/reference/cfile-class.md#abort).

### <a name="requirements"></a>Requisitos

  **Encabezado** afx.h

## <a name="and_catch"></a><a name="and_catch"></a>AND_CATCH

Define un bloque de código para detectar tipos de excepción adicionales producidos en un bloque **TRY** anterior.

```
AND_CATCH(exception_class, exception_object_pointer_name)
```

### <a name="parameters"></a>Parámetros

*exception_class*<br/>
Especifica el tipo de excepción que se va a probar. Para obtener una lista de clases de excepción estándar, vea la clase [CException](../../mfc/reference/cexception-class.md).

*exception_object_pointer_name*<br/>
Un nombre para un puntero de objeto de excepción que creará la macro. Puede utilizar el nombre del puntero para tener acceso al objeto de excepción dentro del bloque **AND_CATCH.** Esta variable se declara por usted.

### <a name="remarks"></a>Observaciones

Utilice la macro CATCH para detectar un tipo de excepción y, a continuación, la AND_CATCH macro para detectar cada tipo subsiguiente. Finalice el bloque **TRY** con una macro END_CATCH.

El código de procesamiento de excepciones puede interrogar el objeto de excepción, si procede, para obtener más información sobre la causa específica de la excepción. Llame a la macro THROW_LAST dentro del bloque **AND_CATCH** para desplazar el procesamiento al siguiente marco de excepción externo. **AND_CATCH** marca el final del bloque **CATCH** o **AND_CATCH** anterior.

> [!NOTE]
> El bloque **AND_CATCH** se define como un ámbito C++ (delineado por llaves). Si declara variables en este ámbito, recuerde que solo son accesibles dentro de ese ámbito. Esto también se aplica a la variable *exception_object_pointer_name.*

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CATCH](#catch).

### <a name="requirements"></a>Requisitos

  **Encabezado** afx.h

## <a name="and_catch_all"></a><a name="and_catch_all"></a>AND_CATCH_ALL

Define un bloque de código para detectar tipos de excepción adicionales producidos en un bloque **TRY** anterior.

```
AND_CATCH_ALL(exception_object_pointer_name)
```

### <a name="parameters"></a>Parámetros

*exception_object_pointer_name*<br/>
Un nombre para un puntero de objeto de excepción que creará la macro. Puede utilizar el nombre del puntero para tener acceso al objeto de excepción dentro del bloque **AND_CATCH_ALL.** Esta variable se declara por usted.

### <a name="remarks"></a>Observaciones

Utilice la macro **CATCH** para detectar un tipo de excepción y, a continuación, la macro AND_CATCH_ALL para detectar todos los demás tipos subsiguientes. Si utiliza AND_CATCH_ALL, finalice el bloque **TRY** con una macro END_CATCH_ALL.

El código de procesamiento de excepciones puede interrogar el objeto de excepción, si procede, para obtener más información sobre la causa específica de la excepción. Llame a la macro THROW_LAST dentro del bloque **AND_CATCH_ALL** para desplazar el procesamiento al siguiente marco de excepción externo. **AND_CATCH_ALL** marca el final del bloque **CATCH** o **AND_CATCH_ALL** anterior.

> [!NOTE]
> El bloque **AND_CATCH_ALL** se define como un ámbito C++ (delineado por llaves). Si declara variables en este ámbito, recuerde que solo son accesibles dentro de ese ámbito.

### <a name="requirements"></a>Requisitos

  **Encabezado** afx.h

## <a name="end_catch"></a><a name="end_catch"></a>END_CATCH

Marca el final del último bloque **CATCH** o **AND_CATCH.**

```
END_CATCH
```

### <a name="remarks"></a>Observaciones

Para obtener más información sobre la macro END_CATCH, consulte el artículo [Excepciones](../../mfc/exception-handling-in-mfc.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afx.h

## <a name="end_catch_all"></a><a name="end_catch_all"></a>END_CATCH_ALL

Marca el final del último **CATCH_ALL88** o **AND_CATCH_ALL** bloque.

```
END_CATCH_ALL
```

### <a name="requirements"></a>Requisitos

  **Encabezado** afx.h

## <a name="throw-mfc"></a><a name="throw"></a>THROW (MFC)

Produce la excepción especificada.

```
THROW(exception_object_pointer)
```

### <a name="parameters"></a>Parámetros

*exception_object_pointer*<br/>
Apunta a un objeto `CException`de excepción derivado de .

### <a name="remarks"></a>Observaciones

**THROW** interrumpe la ejecución del programa, pasando el control al bloque **CATCH** asociado en el programa. Si no ha proporcionado el bloque **CATCH,** el control se pasa a un módulo de microsoft Foundation Class Library que imprime un mensaje de error y se cierra.

Para obtener más información, consulte el artículo [Excepciones](../../mfc/exception-handling-in-mfc.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afx.h

## <a name="throw_last"></a><a name="throw_last"></a>THROW_LAST

Devuelve la excepción al siguiente bloque **CATCH** externo.

```
THROW_LAST()
```

### <a name="remarks"></a>Observaciones

Esta macro le permite producir una excepción creada localmente. Si intenta producir una excepción que acaba de detectar, normalmente saldrá del ámbito y se eliminará. Con **THROW_LAST**, la excepción se pasa correctamente al siguiente controlador **CATCH.**

Para obtener más información, consulte el artículo [Excepciones](../../mfc/exception-handling-in-mfc.md).

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CFile::Abort](../../mfc/reference/cfile-class.md#abort).

### <a name="requirements"></a>Requisitos

  **Encabezado** afx.h

## <a name="afxthrowarchiveexception"></a><a name="afxthrowarchiveexception"></a>AfxThrowArchiveException

Produce una excepción de archivo.

```
void  AfxThrowArchiveException(int cause, LPCTSTR lpszArchiveName);
```

### <a name="parameters"></a>Parámetros

*Causa*<br/>
Especifica un entero que indica el motivo de la excepción. Para obtener una lista de los valores posibles, vea [CArchiveException::m_cause](../../mfc/reference/carchiveexception-class.md#m_cause).

*lpszArchiveName*<br/>
Apunta a una cadena que `CArchive` contiene el nombre del objeto que causó la excepción (si está disponible).

### <a name="requirements"></a>Requisitos

  **Encabezado** afx.h

## <a name="afxthrowfileexception"></a><a name="afxthrowfileexception"></a>AfxThrowFileException

Produce una excepción de archivo.

```
void AfxThrowFileException(
    int cause,
    LONG lOsError = -1,
    LPCTSTR lpszFileName = NULL);
```

### <a name="parameters"></a>Parámetros

*Causa*<br/>
Especifica un entero que indica el motivo de la excepción. Para obtener una lista de los valores posibles, vea [CFileException::m_cause](../../mfc/reference/cfileexception-class.md#m_cause).

*lOsError*<br/>
Contiene el número de error del sistema operativo (si está disponible) que indica el motivo de la excepción. Consulte el manual del sistema operativo para obtener una lista de códigos de error.

*lpszFileName*<br/>
Apunta a una cadena que contiene el nombre del archivo que causó la excepción (si está disponible).

### <a name="remarks"></a>Observaciones

Usted es responsable de determinar la causa en función del código de error del sistema operativo.

### <a name="requirements"></a>Requisitos

  **Encabezado** afx.h

## <a name="afxthrowinvalidargexception"></a><a name="afxthrowinvalidargexception"></a>AfxThrowInvalidArgException

Produce una excepción de argumento no válido.

### <a name="syntax"></a>Sintaxis

```
void AfxThrowInvalidArgException( );
```

### <a name="remarks"></a>Observaciones

Se llama a esta función cuando se utilizan argumentos no válidos.

### <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

## <a name="afxthrowmemoryexception"></a><a name="afxthrowmemoryexception"></a>AfxThrowMemoryException

Produce una excepción de memoria.

```
void AfxThrowMemoryException();
```

### <a name="remarks"></a>Observaciones

Llame a esta función si se produce un error en las llamadas a asignadores de memoria del sistema subyacentes (como **malloc** y la función [GlobalAlloc](/windows/win32/api/winbase/nf-winbase-globalalloc) de Windows). No es necesario llamarlo para **nuevo** porque **new** producirá una excepción de memoria automáticamente si se produce un error en la asignación de memoria.

### <a name="requirements"></a>Requisitos

  **Encabezado** afx.h

## <a name="afxthrownotsupportedexception"></a><a name="afxthrownotsupportedexception"></a>AfxThrowNotSupportedException

Produce una excepción que es el resultado de una solicitud de una característica no admitida.

```
void AfxThrowNotSupportedException();
```

### <a name="requirements"></a>Requisitos

  **Encabezado** afx.h

## <a name="afxthrowresourceexception"></a><a name="afxthrowresourceexception"></a>AfxThrowResourceException

Produce una excepción de recurso.

```
void  AfxThrowResourceException();
```

### <a name="remarks"></a>Observaciones

Normalmente se llama a esta función cuando no se puede cargar un recurso de Windows.

### <a name="requirements"></a>Requisitos

  **Encabezado** afx.h

## <a name="afxthrowuserexception"></a><a name="afxthrowuserexception"></a>AfxThrowUserException

Produce una excepción para detener una operación de usuario final.

```
void AfxThrowUserException();
```

### <a name="remarks"></a>Observaciones

Esta función se `AfxMessageBox` llama normalmente inmediatamente después de haber informado de un error al usuario.

### <a name="requirements"></a>Requisitos

  **Encabezado** afx.h

## <a name="afxthrowoledispatchexception"></a><a name="afxthrowoledispatchexception"></a>AfxThrowOleDispatchException

Utilice esta función para producir una excepción dentro de una función de automatización OLE.

```
void AFXAPI AfxThrowOleDispatchException(
    WORD wCode ,
    LPCSTR lpszDescription,
    UINT nHelpID = 0);

void AFXAPI AfxThrowOleDispatchException(
    WORD wCode,
    UINT nDescriptionID,
    UINT nHelpID = -1);
```

### <a name="parameters"></a>Parámetros

*wCode*<br/>
Un código de error específico de la aplicación.

*lpszDescription*<br/>
Descripción verbal del error.

*nDescriptionID*<br/>
Id. de recurso para la descripción del error verbal.

*nHelpID*<br/>
Un contexto de ayuda para la ayuda de la aplicación (. HLP).

### <a name="remarks"></a>Observaciones

La información proporcionada a esta función se puede mostrar mediante la aplicación conductora (Microsoft Visual Basic u otra aplicación cliente de automatización OLE).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCExceptions#25](../../mfc/codesnippet/cpp/exception-processing_2.cpp)]

### <a name="requirements"></a>Requisitos

  **Encabezado** afx.h

## <a name="afxthrowoleexception"></a><a name="afxthrowoleexception"></a>AfxThrowOleException

Crea un objeto `COleException` de tipo y produce una excepción.

```
void AFXAPI AfxThrowOleException(SCODE sc);
void AFXAPI AfxThrowOleException(HRESULT hr);
```

### <a name="parameters"></a>Parámetros

*Sc*<br/>
Código de estado OLE que indica el motivo de la excepción.

*Hr*<br/>
Controlar un código de resultado que indica el motivo de la excepción.

### <a name="remarks"></a>Observaciones

La versión que toma un HRESULT como argumento convierte ese código de resultado en el SCODE correspondiente. Para obtener más información sobre HRESULT y SCODE, vea [Estructura de códigos de error COM](/windows/win32/com/structure-of-com-error-codes) en el Windows SDK.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdao.h

## <a name="afxthrowdaoexception"></a><a name="afxthrowdaoexception"></a>AfxThrowDaoException

Llame a esta función para producir una excepción de tipo [CDaoException](../../mfc/reference/cdaoexception-class.md) desde su propio código.

```
void AFXAPI AfxThrowDaoException(
    int nAfxDaoError = NO_AFX_DAO_ERROR,
    SCODE scode = S_OK);
```

### <a name="parameters"></a>Parámetros

*nAfxDaoError*<br/>
Un valor entero que representa un código de error extendido DAO, que puede ser uno de los valores enumerados en [CDaoException::m_nAfxDaoError](../../mfc/reference/cdaoexception-class.md#m_nafxdaoerror).

*scode*<br/>
Un código de error OLE de DAO, de tipo SCODE. Para obtener información, vea [CDaoException::m_scode](../../mfc/reference/cdaoexception-class.md#m_scode).

### <a name="remarks"></a>Observaciones

El marco `AfxThrowDaoException`de trabajo también llama a . En la llamada, puede pasar uno de los parámetros o ambos. Por ejemplo, si desea generar uno de los errores definidos en **CDaoException::nAfxDaoError** pero no le importa el parámetro *scode,* pase un código válido en el parámetro *nAfxDaoError* y acepte el valor predeterminado para *scode*.

Para obtener información acerca de las excepciones `CDaoException` relacionadas con las clases DAO de MFC, vea la clase de este libro y el artículo [Excepciones: excepciones](../../mfc/exceptions-database-exceptions.md)de base de datos .

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdb.h

## <a name="afxthrowdbexception"></a><a name="afxthrowdbexception"></a>AfxThrowDBException

Llame a esta función `CDBException` para producir una excepción de tipo desde su propio código.

```
void AfxThrowDBException(
    RETCODE nRetCode,
    CDatabase* pdb,
    HSTMT hstmt);
```

### <a name="parameters"></a>Parámetros

*nRetCode*<br/>
Valor de tipo RETCODE, que define el tipo de error que provocó la excepción.

*Pdb*<br/>
Puntero al `CDatabase` objeto que representa la conexión de origen de datos con la que está asociada la excepción.

*hstmt*<br/>
Identificador ODBC HSTMT que especifica el identificador de instrucción con el que está asociada la excepción.

### <a name="remarks"></a>Observaciones

El marco `AfxThrowDBException` de trabajo llama cuando recibe un ODBC RETCODE de una llamada a una función de API ODBC e interpreta el RETCODE como una condición excepcional en lugar de un error expectable. Por ejemplo, una operación de acceso a datos puede producir un error debido a un error de lectura de disco.

Para obtener información acerca de los valores RETCODE definidos por ODBC, vea Capítulo 8, "Recuperación de información de estado y error", en el Windows SDK. Para obtener información acerca de las extensiones MFC a estos códigos, vea la clase [CDBException](../../mfc/reference/cdbexception-class.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afx.h

## <a name="afxabort"></a><a name="afxabort"></a>AfxAbort

La función de terminación predeterminada proporcionada por MFC.

```
void  AfxAbort();
```

### <a name="remarks"></a>Observaciones

`AfxAbort`se llama internamente por las funciones miembro de MFC cuando hay un error fatal, como una excepción no detectada que no se puede controlar. Usted puede `AfxAbort` llamar en el caso raro cuando usted encuentra un error catastrófico del cual usted no puede recuperar.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CATCH](#catch).

### <a name="requirements"></a>Requisitos

  **Encabezado** afx.h

## <a name="see-also"></a>Consulte también

[Macros y variables globales](mfc-macros-and-globals.md)<br/>
[Clase CException](cexception-class.md)<br/>
[Clase CInvalidArgException](cinvalidargexception-class.md)
