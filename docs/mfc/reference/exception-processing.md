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
ms.openlocfilehash: 337fe03ab09a6ed3da283f45dd4eb58aaaad5bc5
ms.sourcegitcommit: 16c0392fc8d96e814c3a40b0c5346d7389aeb525
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/12/2019
ms.locfileid: "68957503"
---
# <a name="exception-processing"></a>Procesamiento de excepciones

Cuando se ejecuta un programa, pueden producirse varias condiciones anómalas y errores denominados "excepciones". Estos pueden incluir la falta de memoria, errores de asignación de recursos y errores de búsqueda de archivos.

En el biblioteca MFC se usa un esquema de control de excepciones que se modela estrechamente después del propuesto por el Comité de estándares C++ANSI para. Se debe configurar un controlador de excepciones antes de llamar a una función que pueda encontrar una situación anómala. Si la función encuentra una condición anómala, produce una excepción y el control se pasa al controlador de excepciones.

Varias macros incluidas con la biblioteca MFC configurarán los controladores de excepciones. Una serie de otras funciones globales ayudan a producir excepciones especializadas y finalizar programas, si es necesario. Estas macros y funciones globales se dividen en las siguientes categorías:

- Macros de excepción, que estructuran el controlador de excepciones.

- Funciones de generación de excepciones), que generan excepciones de tipos específicos.

- Funciones de finalización, que provocan la finalización del programa.

Para obtener ejemplos y más detalles, vea el artículo [excepciones](../../mfc/exception-handling-in-mfc.md).

### <a name="exception-macros"></a>Macros de excepción

|||
|-|-|
|[TRY](#try)|Designa un bloque de código para el procesamiento de excepciones.|
|[CATCH](#catch)|Designa un bloque de código para detectar una excepción del bloque **try** anterior.|
|[CATCH_ALL](#catch_all)|Designa un bloque de código para detectar todas las excepciones del bloque **try** anterior.|
|[AND_CATCH](#and_catch)|Designa un bloque de código para detectar tipos de excepción adicionales del bloque **try** anterior.|
|[AND_CATCH_ALL](#and_catch_all)|Designa un bloque de código para detectar todos los demás tipos de excepción adicionales que se producen en un bloque **try** anterior.|
|[END_CATCH](#end_catch)|Finaliza el último bloque de código **catch** o **AND_CATCH** .|
|[END_CATCH_ALL](#end_catch_all)|Finaliza el último bloque de código **CATCH_ALL** .|
|[NOTIMPLEMENTEDEXCEPTION](#throw)|Produce una excepción especificada.|
|[THROW_LAST](#throw_last)|Produce la excepción administrada actualmente al siguiente controlador externo.|

### <a name="exception-throwing-functions"></a>Funciones de generación de excepciones

|||
|-|-|
|[AfxThrowArchiveException](#afxthrowarchiveexception)|Produce una excepción de archivo.|
|[AfxThrowFileException](#afxthrowfileexception)|Produce una excepción de archivo.|
|[AfxThrowInvalidArgException](#afxthrowinvalidargexception)|Produce una excepción de argumento no válido.|
|[AfxThrowMemoryException](#afxthrowmemoryexception)|Produce una excepción de memoria.|
|[AfxThrowNotSupportedException](#afxthrownotsupportedexception)|Produce una excepción no admitida.|
|[AfxThrowResourceException](#afxthrowresourceexception)|Produce una excepción de recurso no encontrado de Windows.|
|[AfxThrowUserException](#afxthrowuserexception)|Produce una excepción en una acción del programa iniciada por el usuario.|

MFC proporciona dos funciones de generación de excepciones específicamente para las excepciones OLE:

### <a name="ole-exception-functions"></a>Funciones de excepción OLE

|||
|-|-|
|[AfxThrowOleDispatchException](#afxthrowoledispatchexception)|Produce una excepción en una función de automatización OLE.|
|[AfxThrowOleException](#afxthrowoleexception)|Produce una excepción OLE.|

Para admitir las excepciones de base de datos, las clases de base `CDBException` de `CDaoException`datos proporcionan dos clases de excepción, y y funciones globales para admitir los tipos de excepción:

### <a name="dao-exception-functions"></a>Funciones de excepción de DAO

|||
|-|-|
|[AfxThrowDAOException](#afxthrowdaoexception)|Produce [CDaoException](../../mfc/reference/cdaoexception-class.md) desde su propio código.|
|[AfxThrowDBException](#afxthrowdbexception)|Produce una [excepción CDBException](../../mfc/reference/cdbexception-class.md) a partir de su propio código.|

MFC proporciona la siguiente función de terminación:

### <a name="termination-functions"></a>Funciones de finalización

|||
|-|-|
|[AfxAbort](#afxabort)|Se llama para finalizar una aplicación cuando se produce un error irrecuperable.|

##  <a name="try"></a>PRUEBA

Configura un bloque **try** .

```
TRY
```

### <a name="remarks"></a>Comentarios

Un bloque **try** identifica un bloque de código que puede producir excepciones. Dichas excepciones se controlan en los siguientes bloques **catch** y **AND_CATCH** . Se permite la recursividad: las excepciones se pueden pasar a un bloque **try** externo, ya sea pasando por alto o mediante la macro THROW_LAST. Finalice el bloque **try** con una macro END_CATCH o END_CATCH_ALL.

Para obtener más información, vea el artículo [excepciones](../../mfc/exception-handling-in-mfc.md).

### <a name="example"></a>Ejemplo

Vea el ejemplo de [catch](#catch).

### <a name="requirements"></a>Requisitos

Encabezado: AFX. h

##  <a name="catch"></a>CATCH

Define un bloque de código que detecta el primer tipo de excepción que se produce en el bloque **try** anterior.

```
CATCH(exception_class, exception_object_pointer_name)
```

### <a name="parameters"></a>Parámetros

*exception_class*<br/>
Especifica el tipo de excepción que se va a comprobar. Para obtener una lista de clases de excepción estándar, vea la clase [CException](../../mfc/reference/cexception-class.md).

*exception_object_pointer_name*<br/>
Especifica un nombre para un puntero de objeto de excepción que se creará mediante la macro. Puede usar el nombre del puntero para tener acceso al objeto de excepción dentro del bloque **catch** . Esta variable se declara automáticamente.

### <a name="remarks"></a>Comentarios

El código de procesamiento de excepciones puede interrogar el objeto de excepción, si procede, para obtener más información sobre la causa específica de la excepción. Invoque la macro THROW_LAST para cambiar el procesamiento al siguiente marco de excepción exterior. Finalice el bloque **try** con una macro END_CATCH.

Si *exception_class* es la clase `CException`, se detectarán todos los tipos de excepción. Puede usar la función miembro [CObject:: IsKindOf](../../mfc/reference/cobject-class.md#iskindof) para determinar qué excepción específica se produjo. Una manera mejor de detectar varios tipos de excepciones es usar instrucciones **AND_CATCH** secuenciales, cada una con un tipo de excepción diferente.

La macro crea el puntero del objeto de excepción. No es necesario declararlo usted mismo.

> [!NOTE]
>  El bloque **catch** se define como un C++ ámbito delimitado por llaves. Si se declaran variables en este ámbito, solo se puede tener acceso a ellas dentro de ese ámbito. Esto también se aplica a *exception_object_pointer_name*.

Para obtener más información sobre las excepciones y la macro CATCH, vea el artículo [excepciones](../../mfc/exception-handling-in-mfc.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCExceptions#26](../../mfc/codesnippet/cpp/exception-processing_1.cpp)]

##  <a name="catch_all"></a>  CATCH_ALL

Define un bloque de código que detecta todos los tipos de excepción que se producen en el bloque **try** anterior.

```
CATCH_ALL(exception_object_pointer_name)
```

### <a name="parameters"></a>Parámetros

*exception_object_pointer_name*<br/>
Especifica un nombre para un puntero de objeto de excepción que se creará mediante la macro. Puede usar el nombre del puntero para tener acceso al objeto de excepción `CATCH_ALL` en el bloque. Esta variable se declara automáticamente.

### <a name="remarks"></a>Comentarios

El código de procesamiento de excepciones puede interrogar el objeto de excepción, si procede, para obtener más información sobre la causa específica de la excepción. Invocar `THROW_LAST` la macro para desplazar el procesamiento al siguiente marco de excepción exterior. Si usa **CATCH_ALL**, finalice el bloque **try** con una macro END_CATCH_ALL.

> [!NOTE]
>  El bloque **CATCH_ALL** se define como un C++ ámbito delimitado por llaves. Si se declaran variables en este ámbito, solo se puede tener acceso a ellas dentro de ese ámbito.

Para obtener más información sobre excepciones, vea el artículo [excepciones](../../mfc/exception-handling-in-mfc.md).

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CFile:: ABORT](../../mfc/reference/cfile-class.md#abort).

### <a name="requirements"></a>Requisitos

  **Encabezado** AFX. h

##  <a name="and_catch"></a>AND_CATCH

Define un bloque de código para detectar los tipos de excepción adicionales que se producen en un bloque **try** anterior.

```
AND_CATCH(exception_class, exception_object_pointer_name)
```

### <a name="parameters"></a>Parámetros

*exception_class*<br/>
Especifica el tipo de excepción que se va a comprobar. Para obtener una lista de clases de excepción estándar, vea la clase [CException](../../mfc/reference/cexception-class.md).

*exception_object_pointer_name*<br/>
Un nombre para un puntero de objeto de excepción que se creará mediante la macro. Puede usar el nombre del puntero para tener acceso al objeto de excepción en el bloque **AND_CATCH** . Esta variable se declara automáticamente.

### <a name="remarks"></a>Comentarios

Use la macro CATCH para detectar un tipo de excepción y, a continuación, la macro AND_CATCH para detectar cada tipo subsiguiente. Finalice el bloque **try** con una macro END_CATCH.

El código de procesamiento de excepciones puede interrogar el objeto de excepción, si procede, para obtener más información sobre la causa específica de la excepción. Llame a la macro THROW_LAST en el bloque **AND_CATCH** para cambiar el procesamiento al siguiente marco de excepción exterior. **AND_CATCH** marca el final del bloque **catch** o **AND_CATCH** anterior.

> [!NOTE]
>  El bloque **AND_CATCH** se define como un C++ ámbito (delimitado por llaves). Si declara variables en este ámbito, recuerde que solo se puede tener acceso a ellas dentro de ese ámbito. Esto también se aplica a la variable *exception_object_pointer_name* .

### <a name="example"></a>Ejemplo

Vea el ejemplo de [catch](#catch).

### <a name="requirements"></a>Requisitos

  **Encabezado** AFX. h
##  <a name="and_catch_all"></a>  AND_CATCH_ALL

Define un bloque de código para detectar los tipos de excepción adicionales que se producen en un bloque **try** anterior.

```
AND_CATCH_ALL(exception_object_pointer_name)
```

### <a name="parameters"></a>Parámetros

*exception_object_pointer_name*<br/>
Un nombre para un puntero de objeto de excepción que se creará mediante la macro. Puede usar el nombre del puntero para tener acceso al objeto de excepción en el bloque **AND_CATCH_ALL** . Esta variable se declara automáticamente.

### <a name="remarks"></a>Comentarios

Use la macro **catch** para detectar un tipo de excepción y, a continuación, la macro AND_CATCH_ALL para detectar todos los demás tipos subsiguientes. Si usa AND_CATCH_ALL, finalice el bloque **try** con una macro END_CATCH_ALL.

El código de procesamiento de excepciones puede interrogar el objeto de excepción, si procede, para obtener más información sobre la causa específica de la excepción. Llame a la macro THROW_LAST en el bloque **AND_CATCH_ALL** para cambiar el procesamiento al siguiente marco de excepción exterior. **AND_CATCH_ALL** marca el final del bloque **catch** o **AND_CATCH_ALL** anterior.

> [!NOTE]
>  El bloque **AND_CATCH_ALL** se define como un C++ ámbito (delimitado por llaves). Si declara variables en este ámbito, recuerde que solo se puede tener acceso a ellas dentro de ese ámbito.

### <a name="requirements"></a>Requisitos

  **Encabezado** AFX. h

##  <a name="end_catch"></a>END_CATCH

Marca el final del último bloque **catch** o **AND_CATCH** .

```
END_CATCH
```

### <a name="remarks"></a>Comentarios

Para obtener más información sobre la macro END_CATCH, vea el artículo [excepciones](../../mfc/exception-handling-in-mfc.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** AFX. h

##  <a name="end_catch_all"></a>END_CATCH_ALL

Marca el final del último bloque **CATCH_ALL88** o **AND_CATCH_ALL** .

```
END_CATCH_ALL
```

### <a name="requirements"></a>Requisitos

  **Encabezado** AFX. h

##  <a name="throw"></a>THROW (MFC)

Produce la excepción especificada.

```
THROW(exception_object_pointer)
```

### <a name="parameters"></a>Parámetros

*exception_object_pointer*<br/>
Apunta a un objeto de excepción derivado `CException`de.

### <a name="remarks"></a>Comentarios

**Throw** interrumpe la ejecución del programa, pasando el control al bloque **catch** asociado del programa. Si no se ha proporcionado el bloque **catch** , el control se pasa a un módulo de biblioteca MFC que imprime un mensaje de error y se cierra.

Para obtener más información, vea el artículo [excepciones](../../mfc/exception-handling-in-mfc.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** AFX. h

##  <a name="throw_last"></a>  THROW_LAST

Vuelve a producir la excepción al siguiente bloque **catch** externo.

```
THROW_LAST()
```

### <a name="remarks"></a>Comentarios

Esta macro permite producir una excepción creada localmente. Si intenta iniciar una excepción que acaba de detectar, normalmente se quedará fuera del ámbito y se eliminará. Con **THROW_LAST**, la excepción se pasa correctamente al siguiente controlador **catch** .

Para obtener más información, vea el artículo [excepciones](../../mfc/exception-handling-in-mfc.md).

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CFile:: ABORT](../../mfc/reference/cfile-class.md#abort).

### <a name="requirements"></a>Requisitos

  **Encabezado** AFX. h

##  <a name="afxthrowarchiveexception"></a>  AfxThrowArchiveException

Produce una excepción de archivo.

```
void  AfxThrowArchiveException(int cause, LPCTSTR lpszArchiveName);
```

### <a name="parameters"></a>Parámetros

*cause*<br/>
Especifica un entero que indica la razón de la excepción. Para obtener una lista de los valores posibles, vea [CArchiveException:: m_cause](../../mfc/reference/carchiveexception-class.md#m_cause).

*lpszArchiveName*<br/>
Apunta a una cadena que contiene el nombre del `CArchive` objeto que produjo la excepción (si está disponible).

### <a name="requirements"></a>Requisitos

  **Encabezado** AFX. h

##  <a name="afxthrowfileexception"></a>  AfxThrowFileException

Produce una excepción de archivo.

```
void AfxThrowFileException(
    int cause,
    LONG lOsError = -1,
    LPCTSTR lpszFileName = NULL);
```

### <a name="parameters"></a>Parámetros

*cause*<br/>
Especifica un entero que indica la razón de la excepción. Para obtener una lista de los valores posibles, vea [CFileException:: m_cause](../../mfc/reference/cfileexception-class.md#m_cause).

*lOsError*<br/>
Contiene el número de error del sistema operativo (si está disponible) que indica la razón de la excepción. Consulte el manual del sistema operativo para obtener una lista de códigos de error.

*lpszFileName*<br/>
Apunta a una cadena que contiene el nombre del archivo que produjo la excepción (si está disponible).

### <a name="remarks"></a>Comentarios

Usted es responsable de determinar la causa en función del código de error del sistema operativo.

### <a name="requirements"></a>Requisitos

  **Encabezado** AFX. h

## <a name="afxthrowinvalidargexception"></a>  AfxThrowInvalidArgException

Produce una excepción de argumento no válido.

### <a name="syntax"></a>Sintaxis

```
void AfxThrowInvalidArgException( );
```

### <a name="remarks"></a>Comentarios

Se llama a esta función cuando se usan argumentos no válidos.

### <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

##  <a name="afxthrowmemoryexception"></a>  AfxThrowMemoryException

Produce una excepción de memoria.

```
void AfxThrowMemoryException();
```

### <a name="remarks"></a>Comentarios

Llame a esta función si se produce un error en las llamadas a asignadores de memoria del sistema subyacentes (como **malloc** y la función de Windows [GlobalAlloc](/windows/desktop/api/winbase/nf-winbase-globalalloc) ). No es necesario llamarlo para **nuevo** porque **New** producirá automáticamente una excepción de memoria si se produce un error en la asignación de memoria.

### <a name="requirements"></a>Requisitos

  **Encabezado** AFX. h

##  <a name="afxthrownotsupportedexception"></a>  AfxThrowNotSupportedException

Produce una excepción que es el resultado de una solicitud de una característica no admitida.

```
void AfxThrowNotSupportedException();
```

### <a name="requirements"></a>Requisitos

  **Encabezado** AFX. h

##  <a name="afxthrowresourceexception"></a>  AfxThrowResourceException

Produce una excepción de recurso.

```
void  AfxThrowResourceException();
```

### <a name="remarks"></a>Comentarios

Normalmente, se llama a esta función cuando no se puede cargar un recurso de Windows.

### <a name="requirements"></a>Requisitos

  **Encabezado** AFX. h

##  <a name="afxthrowuserexception"></a>  AfxThrowUserException

Produce una excepción para detener una operación de usuario final.

```
void AfxThrowUserException();
```

### <a name="remarks"></a>Comentarios

Normalmente, se llama a esta función `AfxMessageBox` inmediatamente después de que haya detectado un error al usuario.

### <a name="requirements"></a>Requisitos

  **Encabezado** AFX. h

##  <a name="afxthrowoledispatchexception"></a>  AfxThrowOleDispatchException

Utilice esta función para producir una excepción en una función de automatización OLE.

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
IDENTIFICADOR de recurso para la descripción del error verbal.

*nHelpID*<br/>
Un contexto de ayuda para la ayuda de la aplicación (. HLP).

### <a name="remarks"></a>Comentarios

La aplicación de conducción (Microsoft Visual Basic u otra aplicación cliente de automatización OLE) puede mostrar la información proporcionada a esta función.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCExceptions#25](../../mfc/codesnippet/cpp/exception-processing_2.cpp)]

### <a name="requirements"></a>Requisitos

  **Encabezado** AFX. h

##  <a name="afxthrowoleexception"></a>  AfxThrowOleException

Crea un objeto de tipo `COleException` y produce una excepción.

```
void AFXAPI AfxThrowOleException(SCODE sc);
void AFXAPI AfxThrowOleException(HRESULT hr);
```

### <a name="parameters"></a>Parámetros

*sc*<br/>
Un código de estado OLE que indica la razón de la excepción.

*hr*<br/>
Identificador de un código de resultado que indica la razón de la excepción.

### <a name="remarks"></a>Comentarios

La versión que toma HRESULT como argumento convierte ese código de resultado en el SCODE correspondiente. Para obtener más información sobre HRESULT y SCODE, vea [estructura de los códigos de error com](/windows/desktop/com/structure-of-com-error-codes) en el Windows SDK.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdao. h

##  <a name="afxthrowdaoexception"></a>  AfxThrowDaoException

Llame a esta función para iniciar una excepción de tipo [CDaoException](../../mfc/reference/cdaoexception-class.md) desde su propio código.

```
void AFXAPI AfxThrowDaoException(
    int nAfxDaoError = NO_AFX_DAO_ERROR,
    SCODE scode = S_OK);
```

### <a name="parameters"></a>Parámetros

*nAfxDaoError*<br/>
Un valor entero que representa un código de error extendido de DAO, que puede ser uno de los valores enumerados en [CDaoException:: m_nAfxDaoError](../../mfc/reference/cdaoexception-class.md#m_nafxdaoerror).

*scode*<br/>
Un código de error OLE de DAO, de tipo SCODE. Para obtener información, consulte [CDaoException:: m_scode](../../mfc/reference/cdaoexception-class.md#m_scode).

### <a name="remarks"></a>Comentarios

El marco de trabajo `AfxThrowDaoException`también llama a. En la llamada, puede pasar uno de los parámetros o ambos. Por ejemplo, si desea producir uno de los errores definidos en **CDaoException:: nAfxDaoError** pero no le preocupa el parámetro *SCODE* , pase un código válido en el parámetro *nAfxDaoError* y acepte el valor predeterminado para *SCODE*.

Para obtener información sobre las excepciones relacionadas con las clases DAO de MFC `CDaoException` , vea la clase en este [libro y el artículo excepciones: Excepciones](../../mfc/exceptions-database-exceptions.md)de base de datos.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdb. h

##  <a name="afxthrowdbexception"></a>  AfxThrowDBException

Llame a esta función para iniciar una excepción de `CDBException` tipo desde su propio código.

```
void AfxThrowDBException(
    RETCODE nRetCode,
    CDatabase* pdb,
    HSTMT hstmt);
```

### <a name="parameters"></a>Parámetros

*nRetCode*<br/>
Un valor de tipo RETCODE, que define el tipo de error que provocó que se produjera la excepción.

*pdb*<br/>
Puntero al `CDatabase` objeto que representa la conexión del origen de datos a la que está asociada la excepción.

*hstmt*<br/>
Identificador HSTMT de ODBC que especifica el identificador de instrucción al que está asociada la excepción.

### <a name="remarks"></a>Comentarios

El marco de `AfxThrowDBException` trabajo llama a cuando recibe un RETCODE de ODBC de una llamada a una función de la API de ODBC e interpreta RETCODE como una condición excepcional en lugar de un error esperado. Por ejemplo, una operación de acceso a datos podría producir errores debido a un error de lectura de disco.

Para obtener información sobre los valores de RETCODE definidos por ODBC, vea el capítulo 8, "recuperar el estado y la información del error", en el Windows SDK. Para obtener información sobre las extensiones MFC para estos códigos, vea la clase [CDBException](../../mfc/reference/cdbexception-class.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** AFX. h

##  <a name="afxabort"></a>AfxAbort

La función de terminación predeterminada proporcionada por MFC.

```
void  AfxAbort();
```

### <a name="remarks"></a>Comentarios

`AfxAbort`llama internamente a las funciones miembro de MFC cuando se produce un error irrecuperable, como una excepción no detectada que no se puede controlar. Puede llamar a `AfxAbort` en el caso excepcional cuando se produce un error catastrófico del que no se puede recuperar.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [catch](#catch).

### <a name="requirements"></a>Requisitos

  **Encabezado** AFX. h

## <a name="see-also"></a>Vea también

[Macros y variables globales](mfc-macros-and-globals.md)<br/>
[CException (clase)](cexception-class.md)<br/>
[CInvalidArgException (clase)](cinvalidargexception-class.md)
