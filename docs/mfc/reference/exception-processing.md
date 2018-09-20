---
title: Procesamiento de excepciones | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.macros.exceptions
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1711e634fca1b4350e8aca5f75f0de8a4b3a0e5f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46417363"
---
# <a name="exception-processing"></a>Procesamiento de excepciones

Cuando se ejecuta un programa, puede producirse una serie de condiciones irregulares y errores que se denominan "excepciones". Estos pueden incluir quedarse sin memoria, errores de asignación de recursos y no se encontró los archivos.

La biblioteca Microsoft Foundation Class utiliza un esquema de control de excepciones que se modela estrechamente aquel propuestas por el Comité de estándares ANSI para C++. Debe configurar un controlador de excepciones antes de llamar a una función que puede encontrar una situación anómala. Si la función encuentra una condición anormal, produce una excepción y el control se pasa al controlador de excepciones.

Varias macros que se incluye con la biblioteca Microsoft Foundation Class configurará los controladores de excepciones. Un número de otras funciones globales de ayuda a producir excepciones especializadas y finalizar los programas, si es necesario. Estas macros y funciones globales se dividen en las siguientes categorías:

- Macros de excepción, que se estructura el controlador de excepciones.

- Exception-Throwing funciones), que generan excepciones de tipos específicos.

- Funciones de finalización, lo que provocar la finalización del programa.

Para obtener ejemplos y obtener más información, consulte el artículo [excepciones](../../mfc/exception-handling-in-mfc.md).

### <a name="exception-macros"></a>Macros de excepción

|||
|-|-|
|[TRY](#try)|Designa un bloque de código para el procesamiento de la excepción.|
|[CATCH](#catch)|Designa un bloque de código para detectar una excepción anterior **intente** bloque.|
|[CATCH_ALL](#catch_all)|Designa un bloque de código para detectar todas las excepciones de los anteriores **intente** bloque.|
|[AND_CATCH](#and_catch)|Designa un bloque de código para detectar tipos de excepción adicionales desde la anterior **intente** bloque.|
|[AND_CATCH_ALL](#and_catch_all)|Designa un bloque de código para detectar todos los demás tipos de excepción adicional que se produce en una anterior **intente** bloque.|
|[END_CATCH](#end_catch)|Finaliza la última **CATCH** o **AND_CATCH** bloque de código.|
|[END_CATCH_ALL](#end_catch_all)|Finaliza la última **CATCH_ALL** bloque de código.|
|[THROW](#throw)|Se produce una excepción especificada.|
|[THROW_LAST](#throw_last)|Produce la excepción controlada actualmente al siguiente controlador externo.|

### <a name="exception-throwing-functions"></a>Excepciones de funciones

|||
|-|-|
|[AfxThrowArchiveException](#afxthrowarchiveexception)|Se produce una excepción de archivo.|
|[AfxThrowFileException](#afxthrowfileexception)|Produce una excepción de archivo.|
|[AfxThrowInvalidArgException](#afxthrowinvalidargexception)|Se produce una excepción de argumento no válido.|
|[AfxThrowMemoryException](#afxthrowmemoryexception)|Produce una excepción de memoria.|
|[AfxThrowNotSupportedException](#afxthrownotsupportedexception)|Produce una excepción no admitida.|
|[AfxThrowResourceException](#afxthrowresourceexception)|Produce una excepción de recurso no encontrado en Windows.|
|[AfxThrowUserException](#afxthrowuserexception)|Produce una excepción en una acción iniciada por el usuario programa.|

MFC proporciona dos funciones excepciones específicamente para excepciones OLE:

### <a name="ole-exception-functions"></a>Funciones de excepción OLE

|||
|-|-|
|[AfxThrowOleDispatchException](#afxthrowoledispatchexception)|Se produce una excepción dentro de una función de automatización OLE.|
|[AfxThrowOleException](#afxthrowoleexception)|Se produce una excepción OLE.|

Para admitir las excepciones de base de datos, las clases de base de datos proporcionan dos clases de excepción, `CDBException` y `CDaoException`y funciones globales para admitir los tipos de excepción:

### <a name="dao-exception-functions"></a>Funciones de la excepción de DAO

|||
|-|-|
|[AfxThrowDAOException](#afxthrowdaoexception)|Se produce un [CDaoException](../../mfc/reference/cdaoexception-class.md) desde su propio código.|
|[AfxThrowDBException](#afxthrowdbexception)|Se produce un [CDBException](../../mfc/reference/cdbexception-class.md) desde su propio código.|

MFC proporciona la siguiente función de finalización:

### <a name="termination-functions"></a>Funciones de finalización

|||
|-|-|
|[AfxAbort](#afxabort)|Llamado finalizar una aplicación cuando un error irrecuperable se produce.|

##  <a name="try"></a>  TRY

Configura un **intente** bloque.

```
TRY
```

### <a name="remarks"></a>Comentarios

Un **intente** bloque identifica un bloque de código que se puede producir excepciones. Esas excepciones se controlan en el siguiente **CATCH** y **AND_CATCH** bloques. Se permite la recursividad: excepciones pueden pasarse a un exterior **intente** bloque, omitirlos o mediante el uso de la macro THROW_LAST. Final del **intente** bloque con una macro END_CATCH o END_CATCH_ALL.

Para obtener más información, vea el artículo [excepciones](../../mfc/exception-handling-in-mfc.md).

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CATCH](#catch).

### <a name="requirements"></a>Requisitos

Encabezado: afx.h

##  <a name="catch"></a>  CATCH

Define un bloque de código que detecta el primer tipo de excepción producido en el anterior **intente** bloque.

```
CATCH(exception_class, exception_object_pointer_name)

```

### <a name="parameters"></a>Parámetros

*exception_class*<br/>
Especifica el tipo de excepción va a comprobar. Para obtener una lista de clases de excepción estándar, vea la clase [CException](../../mfc/reference/cexception-class.md).

*exception_object_pointer_name*<br/>
Especifica un nombre para un puntero de objeto de excepción que se crearán con la macro. Puede usar el nombre del puntero para tener acceso al objeto de excepción dentro de la **CATCH** bloque. Esta variable se declara para usted.

### <a name="remarks"></a>Comentarios

El código de procesamiento de excepciones puede consultar el objeto de excepción, si es necesario obtener más información sobre la causa específica de la excepción. Invoque el THROW_LAST (macro) para cambiar el procesamiento en el siguiente fotograma de excepción externa. Final del **intente** bloque con un END_CATCH (macro).

Si *exception_class* es la clase `CException`, a continuación, se detectarán todos los tipos de excepción. Puede usar el [CObject:: IsKindOf](../../mfc/reference/cobject-class.md#iskindof) función miembro para determinar qué se produjo una excepción específica. Una mejor manera de detectar varios tipos de excepciones es usar secuencial **AND_CATCH** instrucciones, cada uno con un tipo de excepción diferente.

El puntero de objeto de excepción se crea mediante la macro. No es necesario declarar usted mismo.

> [!NOTE]
>  El **CATCH** bloque se define como un ámbito de C++ delimitado por llaves. Si declara variables en este ámbito, son accesibles solo dentro de ese ámbito. Esto también se aplica a *exception_object_pointer_name*.

Para obtener más información sobre las excepciones y la macro CATCH, vea el artículo [excepciones](../../mfc/exception-handling-in-mfc.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCExceptions#26](../../mfc/codesnippet/cpp/exception-processing_1.cpp)]

##  <a name="catch_all"></a>  CATCH_ALL

Define un bloque de código que detecta todos los tipos de excepción que se produce en el anterior **intente** bloque.

```
CATCH_ALL(exception_object_pointer_name)
```

### <a name="parameters"></a>Parámetros

*exception_object_pointer_name*<br/>
Especifica un nombre para un puntero de objeto de excepción que se crearán con la macro. Puede usar el nombre del puntero para tener acceso al objeto de excepción dentro de la `CATCH_ALL` bloque. Esta variable se declara para usted.

### <a name="remarks"></a>Comentarios

El código de procesamiento de excepciones puede consultar el objeto de excepción, si es necesario obtener más información sobre la causa específica de la excepción. Invocar el `THROW_LAST` macro para desplazar el procesamiento en el siguiente fotograma de excepción externa. Si usas **CATCH_ALL**, final el **intente** bloque con un end_catch_all (macro).

> [!NOTE]
>  El **CATCH_ALL** bloque se define como un ámbito de C++ delimitado por llaves. Si declara variables en este ámbito, son accesibles solo dentro de ese ámbito.

Para obtener más información sobre excepciones, vea el artículo [excepciones](../../mfc/exception-handling-in-mfc.md).

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CFile::Abort](../../mfc/reference/cfile-class.md#abort).

### <a name="requirements"></a>Requisitos

  **Encabezado** afx.h

##  <a name="and_catch"></a>  AND_CATCH

Define un bloque de código para detectar tipos de excepciones adicionales que se produce en una anterior **intente** bloque.

```
AND_CATCH(exception_class, exception_object_pointer_name)
```

### <a name="parameters"></a>Parámetros

*exception_class*<br/>
Especifica el tipo de excepción va a comprobar. Para obtener una lista de clases de excepción estándar, vea la clase [CException](../../mfc/reference/cexception-class.md).

*exception_object_pointer_name*<br/>
Un nombre para un puntero de objeto de excepción que se crearán con la macro. Puede usar el nombre del puntero para tener acceso al objeto de excepción dentro de la **AND_CATCH** bloque. Esta variable se declara para usted.

### <a name="remarks"></a>Comentarios

Utilice la macro CATCH para detectar un tipo de excepción y, a continuación, la macro AND_CATCH para detectar cada tipo subsiguientes. Final del **intente** bloque con un END_CATCH (macro).

El código de procesamiento de excepciones puede consultar el objeto de excepción, si es necesario obtener más información sobre la causa específica de la excepción. Llamar a la macro THROW_LAST dentro de la **AND_CATCH** bloquear para desplazar el procesamiento en el siguiente fotograma de excepción externa. **AND_CATCH** marca el final de los anteriores **CATCH** o **AND_CATCH** bloque.

> [!NOTE]
>  El **AND_CATCH** bloque se define como un ámbito de C++ (delimitado por llaves). Si declara variables en este ámbito, recuerde que estén accesibles solo dentro de ese ámbito. Esto también se aplica a la *exception_object_pointer_name* variable.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CATCH](#catch).

### <a name="requirements"></a>Requisitos

  **Encabezado** afx.h
##  <a name="and_catch_all"></a>  AND_CATCH_ALL

Define un bloque de código para detectar tipos de excepciones adicionales que se produce en una anterior **intente** bloque.

```
AND_CATCH_ALL(exception_object_pointer_name)
```

### <a name="parameters"></a>Parámetros

*exception_object_pointer_name*<br/>
Un nombre para un puntero de objeto de excepción que se crearán con la macro. Puede usar el nombre del puntero para tener acceso al objeto de excepción dentro de la **AND_CATCH_ALL** bloque. Esta variable se declara para usted.

### <a name="remarks"></a>Comentarios

Use la **CATCH** macro para detectar un tipo de excepción y, a continuación, el and_catch_all (macro) para detectar todos los demás tipos posteriores. Si usa AND_CATCH_ALL, finalizar el **intente** bloque con un end_catch_all (macro).

El código de procesamiento de excepciones puede consultar el objeto de excepción, si es necesario obtener más información sobre la causa específica de la excepción. Llamar a la macro THROW_LAST dentro de la **AND_CATCH_ALL** bloquear para desplazar el procesamiento en el siguiente fotograma de excepción externa. **AND_CATCH_ALL** marca el final de los anteriores **CATCH** o **AND_CATCH_ALL** bloque.

> [!NOTE]
>  El **AND_CATCH_ALL** bloque se define como un ámbito de C++ (delimitado por llaves). Si declara variables en este ámbito, recuerde que estén accesibles solo dentro de ese ámbito.

### <a name="requirements"></a>Requisitos

  **Encabezado** afx.h

##  <a name="end_catch"></a>  END_CATCH

Marca el final de la última **CATCH** o **AND_CATCH** bloque.

```
END_CATCH
```

### <a name="remarks"></a>Comentarios

Para obtener más información sobre la macro END_CATCH, vea el artículo [excepciones](../../mfc/exception-handling-in-mfc.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afx.h

##  <a name="end_catch_all"></a>  END_CATCH_ALL

Marca el final de la última ** CATCH_ALL88 o **AND_CATCH_ALL** bloque.

```
END_CATCH_ALL
```

### <a name="requirements"></a>Requisitos

  **Encabezado** afx.h

##  <a name="throw"></a>  THROW (MFC)

Se produce la excepción especificada.

```
THROW(exception_object_pointer)
```

### <a name="parameters"></a>Parámetros

*exception_object_pointer*<br/>
Apunta a un objeto de excepción derivada de `CException`.

### <a name="remarks"></a>Comentarios

**PRODUCIR** interrumpe la ejecución, pasando el control asociado del programa **CATCH** bloquear en su programa. Si no ha proporcionado el **CATCH** bloquea, a continuación, el control pasa a un módulo de la biblioteca Microsoft Foundation Class que imprime un error del mensaje y se cierra.

Para obtener más información, vea el artículo [excepciones](../../mfc/exception-handling-in-mfc.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afx.h

##  <a name="throw_last"></a>  THROW_LAST

Produce la excepción de vuelta a la siguiente externa **CATCH** bloque.

```
THROW_LAST()
```

### <a name="remarks"></a>Comentarios

Esta macro permite producir una excepción creada localmente. Si intenta iniciar una excepción que simplemente se detectó, normalmente saldrá del ámbito y eliminarse. Con **THROW_LAST**, la excepción se pasa correctamente a la siguiente **CATCH** controlador.

Para obtener más información, vea el artículo [excepciones](../../mfc/exception-handling-in-mfc.md).

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CFile::Abort](../../mfc/reference/cfile-class.md#abort).

### <a name="requirements"></a>Requisitos

  **Encabezado** afx.h

##  <a name="afxthrowarchiveexception"></a>  AfxThrowArchiveException

Se produce una excepción de archivo.

```
void  AfxThrowArchiveException(int cause, LPCTSTR lpszArchiveName);
```

### <a name="parameters"></a>Parámetros

*Causa*<br/>
Especifica un entero que indica el motivo de la excepción. Para obtener una lista de los valores posibles, vea [CArchiveException::m_cause](../../mfc/reference/carchiveexception-class.md#m_cause).

*lpszArchiveName*<br/>
Señala a una cadena que contiene el nombre de la `CArchive` objeto que produjo la excepción (si está disponible).

### <a name="requirements"></a>Requisitos

  **Encabezado** afx.h

##  <a name="afxthrowfileexception"></a>  AfxThrowFileException

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
Contiene el número de errores del sistema operativo (si está disponible) que indica el motivo de la excepción. Consulte el manual del sistema operativo para obtener una lista de códigos de error.

*lpszFileName*<br/>
Apunta a una cadena que contiene el nombre del archivo que produjo la excepción (si está disponible).

### <a name="remarks"></a>Comentarios

Usted es responsable de determinar la causa según el código de error del sistema operativo.

### <a name="requirements"></a>Requisitos

  **Encabezado** afx.h

## <a name="afxthrowinvalidargexception"></a>  AfxThrowInvalidArgException

Se produce una excepción de argumento no válido.

### <a name="syntax"></a>Sintaxis

```
void AfxThrowInvalidArgException( );
```

### <a name="remarks"></a>Comentarios

Esta función se invoca cuando se usan argumentos no válidos.

### <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

### <a name="see-also"></a>Vea también

[Macros y funciones globales](mfc-macros-and-globals.md)<br/>
[CInvalidArgException (clase)](cinvalidargexception-class.md)<br/>
[THROW](#throw)


##  <a name="afxthrowmemoryexception"></a>  AfxThrowMemoryException

Produce una excepción de memoria.

```
void AfxThrowMemoryException();
```

### <a name="remarks"></a>Comentarios

Llame a esta función si las llamadas a los asignadores de memoria de sistema subyacente (como **malloc** y [GlobalAlloc](/windows/desktop/api/winbase/nf-winbase-globalalloc) función de Windows) producirá un error. No es necesario llamarlo para **nueva** porque **nuevo** producirá una excepción de memoria automáticamente si se produce un error en la asignación de memoria.

### <a name="requirements"></a>Requisitos

  **Encabezado** afx.h

##  <a name="afxthrownotsupportedexception"></a>  AfxThrowNotSupportedException

Se produce una excepción que es el resultado de una solicitud para una función no admitida.

```
void AfxThrowNotSupportedException();
```

### <a name="requirements"></a>Requisitos

  **Encabezado** afx.h

##  <a name="afxthrowresourceexception"></a>  AfxThrowResourceException

Produce una excepción de recursos.

```
void  AfxThrowResourceException();
```

### <a name="remarks"></a>Comentarios

Esta función normalmente se llama cuando no se puede cargar un recurso de Windows.

### <a name="requirements"></a>Requisitos

  **Encabezado** afx.h

##  <a name="afxthrowuserexception"></a>  AfxThrowUserException

Produce una excepción para detener una operación del usuario final.

```
void AfxThrowUserException();
```

### <a name="remarks"></a>Comentarios

Esta función normalmente se llama inmediatamente después de `AfxMessageBox` ha detectado un error al usuario.

### <a name="requirements"></a>Requisitos

  **Encabezado** afx.h

##  <a name="afxthrowoledispatchexception"></a>  AfxThrowOleDispatchException

Use esta función para producir una excepción dentro de una función de automatización OLE.

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

*WCode*<br/>
Un código de error específico para su aplicación.

*lpszDescripción*<br/>
Verbal descripción del error.

*nDescriptionID*<br/>
Identificador de recurso para la descripción del error.

*nIDAyuda*<br/>
Un contexto de ayuda para obtener ayuda de la aplicación (. Archivo HLP).

### <a name="remarks"></a>Comentarios

La información proporcionada a esta función se puede mostrar por la aplicación de conducción (Microsoft Visual Basic u otra aplicación de cliente de automatización OLE).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCExceptions#25](../../mfc/codesnippet/cpp/exception-processing_2.cpp)]

### <a name="requirements"></a>Requisitos

  **Encabezado** afx.h

##  <a name="afxthrowoleexception"></a>  AfxThrowOleException

Crea un objeto de tipo `COleException` y produce una excepción.

```
void AFXAPI AfxThrowOleException(SCODE sc);
void AFXAPI AfxThrowOleException(HRESULT hr);
```

### <a name="parameters"></a>Parámetros

*SC*<br/>
Un código de estado OLE que indica el motivo de la excepción.

*recursos humanos*<br/>
Identificador de un código de resultado que indica el motivo de la excepción.

### <a name="remarks"></a>Comentarios

La versión que toma HRESULT como argumento convierte ese código de resultado en la correspondiente SCODE. Para obtener más información sobre el valor HRESULT y SCODE, consulte [estructura de códigos de Error COM](/windows/desktop/com/structure-of-com-error-codes) en el SDK de Windows.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdao.h

##  <a name="afxthrowdaoexception"></a>  AfxThrowDaoException

Llame a esta función para producir una excepción de tipo [CDaoException](../../mfc/reference/cdaoexception-class.md) desde su propio código.

```
void AFXAPI AfxThrowDaoException(
    int nAfxDaoError = NO_AFX_DAO_ERROR,
    SCODE scode = S_OK);
```

### <a name="parameters"></a>Parámetros

*nAfxDaoError*<br/>
Un valor entero que representa un código de error extendido de DAO, que puede ser uno de los valores anuncie [CDaoException::m_nAfxDaoError](../../mfc/reference/cdaoexception-class.md#m_nafxdaoerror).

*SCODE*<br/>
Un código de error OLE de DAO de tipo SCODE. Para obtener información, consulte [CDaoException::m_scode](../../mfc/reference/cdaoexception-class.md#m_scode).

### <a name="remarks"></a>Comentarios

También se llama el marco de trabajo `AfxThrowDaoException`. En la llamada, puede pasar uno de los parámetros o ambos. Por ejemplo, si desea generar uno de los errores se definen en **CDaoException::nAfxDaoError** pero no preocupa la *scode* parámetro, pase un código válido en el *nAfxDaoError* parámetro y aceptar el valor predeterminado de *scode*.

Para obtener información acerca de las excepciones relacionadas con las clases DAO de MFC, vea la clase `CDaoException` en este libro y el artículo [excepciones: excepciones de base de datos](../../mfc/exceptions-database-exceptions.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdb.h

##  <a name="afxthrowdbexception"></a>  AfxThrowDBException

Llame a esta función para producir una excepción de tipo `CDBException` desde su propio código.

```
void AfxThrowDBException(
    RETCODE nRetCode,
    CDatabase* pdb,
    HSTMT hstmt);
```

### <a name="parameters"></a>Parámetros

*nRetCode*<br/>
Un valor de tipo RETCODE, definir el tipo de error que provocó la excepción que se produzca.

*PDB*<br/>
Un puntero a la `CDatabase` objeto que representa la conexión de origen de datos que está asociada la excepción.

*HStmt*<br/>
Identificador de ODBC HSTMT que especifica el identificador de instrucción que está asociada la excepción.

### <a name="remarks"></a>Comentarios

Las llamadas de framework `AfxThrowDBException` cuando recibe un RETCODE ODBC en una llamada a una función API de ODBC e interpreta RETCODE como una condición excepcional, en lugar de un error expectable. Por ejemplo, una operación de acceso a datos puede producir un error debido a un error de lectura de disco.

Para obtener información acerca de los valores RETCODE definida por ODBC, consulte el capítulo 8, "Recuperación de información de estado y Error", en el SDK de Windows. Para obtener información acerca de las extensiones MFC para estos códigos, vea la clase [CDBException](../../mfc/reference/cdbexception-class.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afx.h

##  <a name="afxabort"></a>  AfxAbort

La función de finalización predeterminada proporcionada por MFC.

```
void  AfxAbort();
```

### <a name="remarks"></a>Comentarios

`AfxAbort` se llama internamente a funciones miembro de MFC cuando hay un error irrecuperable, como una excepción no detectada que no se puede controlar. Puede llamar a `AfxAbort` en el caso excepcional si se produce un error grave desde el que no puede recuperar.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CATCH](#catch).

### <a name="requirements"></a>Requisitos

  **Encabezado** afx.h

## <a name="see-also"></a>Vea también

[Macros y funciones globales](../../mfc/reference/mfc-macros-and-globals.md)<br/>
[CException (clase)](../../mfc/reference/cexception-class.md)
