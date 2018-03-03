---
title: "Excepción al procesar | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: adad6183d15b378feb7ec96aedff6a0013a2dd24
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="exception-processing"></a>Procesamiento de excepciones
Cuando se ejecuta un programa, puede producirse un número de errores que se denominan "excepciones" y las condiciones irregulares. Estos pueden incluir quedarse sin memoria, errores de asignación de recursos y de errores para buscar archivos.  
  
 La biblioteca Microsoft Foundation Class utiliza un esquema de control de excepciones que se modela estrechamente después de que el uno propuestos por el Comité de normas ANSI para C++. Un controlador de excepciones debe estar configurado antes de llamar a una función que puede encontrar una situación anómala. Si la función encuentra una condición anormal, produce una excepción y el control se pasa al controlador de excepciones.  
  
 Varias macros que se incluye con la biblioteca Microsoft Foundation Class a configurar los controladores de excepciones. Un número de otras funciones globales ayuda a producir excepciones especializadas y finalizar programas, si es necesario. Estas macros y funciones globales se dividen en las siguientes categorías:  
  
- Macros de excepción, que el controlador de excepciones de la estructura.  
  
- Funciones de Exception-Throwing), que generan excepciones de tipos específicos.  
  
- Funciones de finalización, lo que dar lugar a la finalización del programa.  
  
 Para obtener ejemplos y obtener más información, vea el artículo [excepciones](../../mfc/exception-handling-in-mfc.md).  
  
### <a name="exception-macros"></a>Macros de excepción  
  
|||  
|-|-|  
|[TRY](#try)|Designa un bloque de código para el procesamiento de la excepción.|  
|[CATCH](#catch)|Designa un bloque de código para detectar una excepción de los anteriores **intente** bloque.|  
|[CATCH_ALL](#catch_all)|Designa un bloque de código para detectar todas las excepciones de los anteriores **intente** bloque.|  
|[AND_CATCH](#and_catch)|Designa un bloque de código para detectar tipos de excepciones adicionales desde la anterior **intente** bloque.|  
|[AND_CATCH_ALL](#and_catch_all)|Designa un bloque de código para detectar todos los demás tipos de adicional de la excepción que se produce en una anterior **intente** bloque.|  
|[END_CATCH](#end_catch)|Finaliza la última **CATCH** o `AND_CATCH` bloque de código.|  
|[END_CATCH_ALL](#end_catch_all)|Finaliza la última `CATCH_ALL` bloque de código.|  
|[THROW](#throw)|Produce una excepción especificada.|  
|[THROW_LAST](#throw_last)|Produce la excepción está controlada al siguiente controlador externo.|  
  
### <a name="exception-throwing-functions"></a>Funciones de generación de excepciones  
  
|||  
|-|-|  
|[AfxThrowArchiveException](#afxthrowarchiveexception)|Produce una excepción de archivo.|  
|[AfxThrowFileException](#afxthrowfileexception)|Produce una excepción de archivo.|  
|[AfxThrowInvalidArgException](#afxthrowinvalidargexception)|Produce una excepción de argumento no válido.|
|[AfxThrowMemoryException](#afxthrowmemoryexception)|Produce una excepción de memoria.|  
|[AfxThrowNotSupportedException](#afxthrownotsupportedexception)|Produce una excepción no admitidos.|  
|[AfxThrowResourceException](#afxthrowresourceexception)|Produce una excepción de recurso no encontrado en Windows.|  
|[AfxThrowUserException](#afxthrowuserexception)|Produce una excepción en una acción iniciada por el usuario programa.|  
  
 MFC proporciona dos funciones de generación de excepciones específicamente para excepciones OLE:  
  
### <a name="ole-exception-functions"></a>Funciones de excepciones OLE  
  
|||  
|-|-|  
|[AfxThrowOleDispatchException](#afxthrowoledispatchexception)|Produce una excepción dentro de una función de automatización OLE.|  
|[AfxThrowOleException](#afxthrowoleexception)|Produce una excepción de OLE.|  
  
 Para admitir las excepciones de base de datos, las clases de base de datos proporcionan dos clases de excepción, `CDBException` y `CDaoException`y funciones globales para admitir los tipos de excepción:  
  
### <a name="dao-exception-functions"></a>Funciones de excepciones de DAO  
  
|||  
|-|-|  
|[AfxThrowDAOException](#afxthrowdaoexception)|Produce una [CDaoException](../../mfc/reference/cdaoexception-class.md) desde su propio código.|  
|[AfxThrowDBException](#afxthrowdbexception)|Produce una [CDBException](../../mfc/reference/cdbexception-class.md) desde su propio código.|  
  
 MFC proporciona la siguiente función de finalización:  
  
### <a name="termination-functions"></a>Funciones de finalización  
  
|||  
|-|-|  
|[AfxAbort](#afxabort)|Llama finalizar una aplicación cuando un error irrecuperable se produce.|  
  
##  <a name="try"></a>TRY  
 Configura un **intente** bloque.  
  
```   
TRY   
```  
  
### <a name="remarks"></a>Comentarios  
 A **intente** bloque identifica un bloque de código que podría producir excepciones. Esas excepciones se controlan en la siguiente **CATCH** y `AND_CATCH` bloques. La recursión se permite: las excepciones se pueden pasar a un exterior **intente** bloque, pasando por alto ellos o mediante el `THROW_LAST` macro. Final del **intente** bloque con un `END_CATCH` o `END_CATCH_ALL` macro.  
  
 Para obtener más información, vea el artículo [excepciones](../../mfc/exception-handling-in-mfc.md).  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [CATCH](#catch).  

### <a name="requirements"></a>Requisitos
Encabezado: afx.h

##  <a name="catch"></a>CATCH  
 Define un bloque de código que detecta el primer tipo de excepción que se produce en los anteriores **intente** bloque.  
  
```   
CATCH(exception_class, exception_object_pointer_name)  
 
```  
  
### <a name="parameters"></a>Parámetros  
 *exception_class*  
 Especifica el tipo de excepción va a comprobar. Para obtener una lista de clases de excepción estándar, vea la clase [CException](../../mfc/reference/cexception-class.md).  
  
 *exception_object_pointer_name*  
 Especifica un nombre para un puntero de objeto de excepción que se va a crear la macro. Puede usar el nombre de puntero para tener acceso al objeto de excepción dentro de la **CATCH** bloque. Esta variable se declara para usted.  
  
### <a name="remarks"></a>Comentarios  
 El código de procesamiento de la excepción puede consultar el objeto de excepción, si procede, para obtener más información sobre la causa específica de la excepción. Invocar el `THROW_LAST` macro para desplazar el procesamiento al marco siguiente excepción externa. Final del **intente** bloque con un `END_CATCH` macro.  
  
 Si *exception_class* es la clase `CException`, a continuación, se detectarán todos los tipos de excepción. Puede usar el [CObject:: IsKindOf](../../mfc/reference/cobject-class.md#iskindof) función de miembro para determinar qué excepción concreta. Una mejor manera de detectar varias clases de excepciones es usar secuencial `AND_CATCH` instrucciones, cada uno con un tipo de excepción diferente.  
  
 El puntero de objeto de excepción se crea mediante la macro. No es necesario declarar usted mismo.  
  
> [!NOTE]
>  El **CATCH** bloque se define como un ámbito de C++ que se escriben entre llaves. Si declara variables en este ámbito, son accesibles solo dentro de ese ámbito. Esto también se aplica a *exception_object_pointer_name*.  
  
 Para obtener más información sobre las excepciones y el **CATCH** macro, vea el artículo [excepciones](../../mfc/exception-handling-in-mfc.md).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCExceptions#26](../../mfc/codesnippet/cpp/exception-processing_1.cpp)]  
  
##  <a name="catch_all"></a>CATCH_ALL  
 Define un bloque de código que detecta todos los tipos de excepción que se produce en los anteriores **intente** bloque.  
  
```   
CATCH_ALL(exception_object_pointer_name)   
```  
  
### <a name="parameters"></a>Parámetros  
 *exception_object_pointer_name*  
 Especifica un nombre para un puntero de objeto de excepción que se va a crear la macro. Puede usar el nombre de puntero para tener acceso al objeto de excepción dentro de la `CATCH_ALL` bloque. Esta variable se declara para usted.  
  
### <a name="remarks"></a>Comentarios  
 El código de procesamiento de la excepción puede consultar el objeto de excepción, si procede, para obtener más información sobre la causa específica de la excepción. Invocar el `THROW_LAST` macro para desplazar el procesamiento al marco siguiente excepción externa. Si usa `CATCH_ALL`, final la **intente** bloque con un `END_CATCH_ALL` macro.  
  
> [!NOTE]
>  El `CATCH_ALL` bloque se define como un ámbito de C++ que se escriben entre llaves. Si declara variables en este ámbito, son accesibles solo dentro de ese ámbito.  
  
 Para obtener más información sobre excepciones, vea el artículo [excepciones](../../mfc/exception-handling-in-mfc.md).  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [CFile::Abort](../../mfc/reference/cfile-class.md#abort).  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afx.h  

##  <a name="and_catch"></a>AND_CATCH  
 Define un bloque de código para detectar tipos de adicional de la excepción que se produce en una anterior **intente** bloque.  
  
```   
AND_CATCH(exception_class, exception_object_pointer_name)   
```  
  
### <a name="parameters"></a>Parámetros  
 *exception_class*  
 Especifica el tipo de excepción va a comprobar. Para obtener una lista de clases de excepción estándar, vea la clase [CException](../../mfc/reference/cexception-class.md).  
  
 *exception_object_pointer_name*  
 Un nombre para un puntero de objeto de excepción que se va a crear la macro. Puede usar el nombre de puntero para tener acceso al objeto de excepción dentro de la `AND_CATCH` bloque. Esta variable se declara para usted.  
  
### <a name="remarks"></a>Comentarios  
 Use la **CATCH** macro para detectar un tipo de excepción, la `AND_CATCH` macro para detectar cada tipo posterior. Final del **intente** bloque con un `END_CATCH` macro.  
  
 El código de procesamiento de la excepción puede consultar el objeto de excepción, si procede, para obtener más información sobre la causa específica de la excepción. Llame a la `THROW_LAST` macro dentro de la `AND_CATCH` bloquear al desplazar el procesamiento al marco siguiente excepción externa. `AND_CATCH`marca el final de los anteriores **CATCH** o `AND_CATCH` bloque.  
  
> [!NOTE]
>  El `AND_CATCH` bloque se define como un ámbito de C++ (delimitado por llaves). Si declara variables en este ámbito, recuerde que es accesibles únicamente dentro de ese ámbito. Esto también se aplica a la *exception_object_pointer_name* variable.  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [CATCH](#catch).  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afx.h  
##  <a name="and_catch_all"></a>AND_CATCH_ALL  
 Define un bloque de código para detectar tipos de adicional de la excepción que se produce en una anterior **intente** bloque.  
  
```   
AND_CATCH_ALL(exception_object_pointer_name)  
```  
  
### <a name="parameters"></a>Parámetros  
 *exception_object_pointer_name*  
 Un nombre para un puntero de objeto de excepción que se va a crear la macro. Puede usar el nombre de puntero para tener acceso al objeto de excepción dentro de la `AND_CATCH_ALL` bloque. Esta variable se declara para usted.  
  
### <a name="remarks"></a>Comentarios  
 Use la **CATCH** macro para detectar un tipo de excepción, la `AND_CATCH_ALL` macro para detectar todos los demás tipos subsiguientes. Si usa `AND_CATCH_ALL`, final la **intente** bloque con un `END_CATCH_ALL` macro.  
  
 El código de procesamiento de la excepción puede consultar el objeto de excepción, si procede, para obtener más información sobre la causa específica de la excepción. Llame a la `THROW_LAST` macro dentro de la `AND_CATCH_ALL` bloquear al desplazar el procesamiento al marco siguiente excepción externa. `AND_CATCH_ALL`marca el final de los anteriores **CATCH** o `AND_CATCH_ALL` bloque.  
  
> [!NOTE]
>  El `AND_CATCH_ALL` bloque se define como un ámbito de C++ (delimitado por llaves). Si declara variables en este ámbito, recuerde que es accesibles únicamente dentro de ese ámbito.  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afx.h  
  
##  <a name="end_catch"></a>END_CATCH  
 Marca el final de la última **CATCH** o `AND_CATCH` bloque.  
  
```   
END_CATCH  
```  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información sobre la `END_CATCH` macro, vea el artículo [excepciones](../../mfc/exception-handling-in-mfc.md).  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afx.h  
  
##  <a name="end_catch_all"></a>END_CATCH_ALL  
 Marca el final de la última `CATCH_ALL` o `AND_CATCH_ALL` bloque.  
  
```   
END_CATCH_ALL  
```  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afx.h  
  
##  <a name="throw"></a>THROW (MFC)  
 Produce la excepción especificada.  
  
```   
THROW(exception_object_pointer) 
```  
  
### <a name="parameters"></a>Parámetros  
 *exception_object_pointer*  
 Apunta a un objeto de excepción que se deriva de `CException`.  
  
### <a name="remarks"></a>Comentarios  
 **INICIAR** interrupciones de la ejecución, pasar el control a la categoría asociada del programa **CATCH** bloquear en su programa. Si no ha proporcionado el **CATCH** bloquear, a continuación, el control se pasa a un módulo de biblioteca Microsoft Foundation Class que imprime un error de mensaje y se cierra.  
  
 Para obtener más información, vea el artículo [excepciones](../../mfc/exception-handling-in-mfc.md).  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afx.h  
  
##  <a name="throw_last"></a>THROW_LAST  
 Produce la excepción de nuevo a la siguiente externa **CATCH** bloque.  
  
```   
THROW_LAST()   
```  
  
### <a name="remarks"></a>Comentarios  
 Esta macro puede producir una excepción creada localmente. Si intenta iniciar una excepción que acaba de capturar, normalmente se salen del ámbito y eliminarse. Con `THROW_LAST`, la excepción se pasa correctamente al siguiente **CATCH** controlador.  
  
 Para obtener más información, vea el artículo [excepciones](../../mfc/exception-handling-in-mfc.md).  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [CFile::Abort](../../mfc/reference/cfile-class.md#abort).  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afx.h  
  
##  <a name="afxthrowarchiveexception"></a>AfxThrowArchiveException  
 Produce una excepción de archivo.  
  
```   
void  AfxThrowArchiveException(int cause, LPCTSTR lpszArchiveName); 
```  
  
### <a name="parameters"></a>Parámetros  
 `cause`  
 Especifica un entero que indica el motivo de la excepción. Para obtener una lista de los valores posibles, consulte [CArchiveException::m_cause](../../mfc/reference/carchiveexception-class.md#m_cause).  
  
 `lpszArchiveName`  
 Señala a una cadena que contiene el nombre de la `CArchive` objeto que produjo la excepción (si está disponible).  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afx.h  
  
##  <a name="afxthrowfileexception"></a>AfxThrowFileException  
 Produce una excepción de archivo.  
  
```   
void AfxThrowFileException(
    int cause,  
    LONG lOsError = -1,  
    LPCTSTR lpszFileName = NULL); 
```  
  
### <a name="parameters"></a>Parámetros  
 `cause`  
 Especifica un entero que indica el motivo de la excepción. Para obtener una lista de los valores posibles, consulte [CFileException::m_cause](../../mfc/reference/cfileexception-class.md#m_cause).  
  
 `lOsError`  
 Contiene el número de error de sistema operativo (si está disponible) que indica el motivo de la excepción. Consulte el manual del sistema operativo para obtener una lista de códigos de error.  
  
 `lpszFileName`  
 Apunta a una cadena que contiene el nombre del archivo que produjo la excepción (si está disponible).  
  
### <a name="remarks"></a>Comentarios  
 Usted es responsable de determinar la causa en función del código de error del sistema operativo.  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afx.h  

## <a name="afxthrowinvalidargexception"></a>AfxThrowInvalidArgException
Produce una excepción de argumento no válido.  
   
### <a name="syntax"></a>Sintaxis    
```
void AfxThrowInvalidArgException( );  
```  
   
### <a name="remarks"></a>Comentarios  
 Esta función se invoca cuando se utilizan argumentos no válidos.  
   
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h  
   
### <a name="see-also"></a>Vea también  
 [Macros y funciones globales](mfc-macros-and-globals.md)   
 [Clase CInvalidArgException](cinvalidargexception-class.md)   
 [THROW](#throw)
  
  
##  <a name="afxthrowmemoryexception"></a>AfxThrowMemoryException  
 Produce una excepción de memoria.  
  
```   
void AfxThrowMemoryException(); 
```  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función si las llamadas a asignadores de memoria de sistema subyacente (como `malloc` y [GlobalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366574) la función de Windows) producirá un error. No es necesario para que se llame para **nueva** porque **nueva** inicia una excepción de memoria automáticamente si se produce un error en la asignación de memoria.  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afx.h  
  
##  <a name="afxthrownotsupportedexception"></a>AfxThrowNotSupportedException  
 Produce una excepción que es el resultado de una solicitud de una característica no compatible.  
  
```  
void AfxThrowNotSupportedException(); 
```  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afx.h  
  
##  <a name="afxthrowresourceexception"></a>AfxThrowResourceException  
 Produce una excepción de recursos.  
  
```   
void  AfxThrowResourceException(); 
```  
  
### <a name="remarks"></a>Comentarios  
 Normalmente, esta función se invoca cuando no se puede cargar un recurso de Windows.  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afx.h  
  
##  <a name="afxthrowuserexception"></a>AfxThrowUserException  
 Produce una excepción para detener una operación del usuario final.  
  
```   
void AfxThrowUserException(); 
```  
  
### <a name="remarks"></a>Comentarios  
 Esta función normalmente se llama inmediatamente después de `AfxMessageBox` ha notificado un error al usuario.  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afx.h  
  
##  <a name="afxthrowoledispatchexception"></a>AfxThrowOleDispatchException  
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
 `wCode`  
 Un código de error específico de la aplicación.  
  
 `lpszDescription`  
 Verbal descripción del error.  
  
 `nDescriptionID`  
 Id. de recurso para la descripción del error.  
  
 `nHelpID`  
 Un contexto de ayuda para obtener ayuda de la aplicación (. Archivo HLP).  
  
### <a name="remarks"></a>Comentarios  
 La información proporcionada para esta función se puede mostrar por la aplicación determinante (Microsoft Visual Basic u otra aplicación de cliente de automatización OLE).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCExceptions#25](../../mfc/codesnippet/cpp/exception-processing_2.cpp)]  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afx.h  
  
##  <a name="afxthrowoleexception"></a>AfxThrowOleException  
 Crea un objeto de tipo `COleException` y produce una excepción.  
  
``` 
void AFXAPI AfxThrowOleException(SCODE sc);
void AFXAPI AfxThrowOleException(HRESULT hr); 
```  
  
### <a name="parameters"></a>Parámetros  
 `sc`  
 Un código de estado OLE que indica el motivo de la excepción.  
  
 `hr`  
 Identificador de un código de resultado que indica el motivo de la excepción.  
  
### <a name="remarks"></a>Comentarios  
 La versión que toma una `HRESULT` como un argumento convierte ese código de resultado en la correspondiente `SCODE`. Para obtener más información sobre `HRESULT` y `SCODE`, consulte [estructura de códigos de Error COM](http://msdn.microsoft.com/library/windows/desktop/ms690088) del SDK de Windows.  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdao.h  
  
##  <a name="afxthrowdaoexception"></a>AfxThrowDaoException  
 Llame a esta función para producir una excepción de tipo [CDaoException](../../mfc/reference/cdaoexception-class.md) desde su propio código.  
  
```   
void AFXAPI AfxThrowDaoException(
    int nAfxDaoError = NO_AFX_DAO_ERROR,  
    SCODE scode = S_OK); 
```  
  
### <a name="parameters"></a>Parámetros  
 `nAfxDaoError`  
 Un valor entero que representa un código de error extendido de DAO, que puede ser uno de los valores enumerado en [CDaoException::m_nAfxDaoError](../../mfc/reference/cdaoexception-class.md#m_nafxdaoerror).  
  
 *SCODE*  
 Un código de error OLE de DAO, de tipo `SCODE`. Para obtener información, consulte [CDaoException::m_scode](../../mfc/reference/cdaoexception-class.md#m_scode).  
  
### <a name="remarks"></a>Comentarios  
 También llama el marco de trabajo `AfxThrowDaoException`. En la llamada, puede pasar uno de los parámetros o ambos. Por ejemplo, si desea generar uno de los errores se definen en **CDaoException::nAfxDaoError** pero no le preocupa la *scode* parámetro, pasar un código válido en el `nAfxDaoError` parámetro y aceptar el valor predeterminado de *scode*.  
  
 Para obtener información acerca de las excepciones relacionadas con las clases DAO de MFC, vea la clase `CDaoException` en este libro y el artículo [excepciones: excepciones de base de datos](../../mfc/exceptions-database-exceptions.md).  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdb.h  
  
##  <a name="afxthrowdbexception"></a>AfxThrowDBException  
 Llame a esta función para producir una excepción de tipo `CDBException` desde su propio código.  
  
```  
void AfxThrowDBException(
    RETCODE nRetCode,  
    CDatabase* pdb,  
    HSTMT hstmt);  
```  
  
### <a name="parameters"></a>Parámetros  
 `nRetCode`  
 Un valor de tipo **RETCODE**, definir el tipo de error que provocó la excepción.  
  
 `pdb`  
 Un puntero a la `CDatabase` objeto que representa la conexión de origen de datos con el que está asociada la excepción.  
  
 `hstmt`  
 Un ODBC **HSTMT** identificador que especifica el identificador de instrucción con el que está asociada la excepción.  
  
### <a name="remarks"></a>Comentarios  
 Las llamadas de framework `AfxThrowDBException` cuando recibe un ODBC **RETCODE** de una llamada a una API de ODBC función e interpreta la **RETCODE** como una condición excepcional en lugar de un error expectable. Por ejemplo, una operación de acceso a datos podría fallar debido a un error de lectura de disco.  
  
 Para obtener información sobre la **RETCODE** valores definidos por ODBC, consulte el capítulo 8, "Recuperación de información de estado y Error", en el SDK de Windows. Para obtener información acerca de las extensiones MFC para estos códigos, vea la clase [CDBException](../../mfc/reference/cdbexception-class.md).  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afx.h  
  
##  <a name="afxabort"></a>AfxAbort  
 La función de finalización predeterminada proporcionada por MFC.  
  
```   
void  AfxAbort(); 
```  
  
### <a name="remarks"></a>Comentarios  
 `AfxAbort`se llama internamente a las funciones miembro de MFC cuando hay un error grave, como una excepción no detectada que no se puede controlar. Puede llamar a `AfxAbort` en el caso excepcional si se produce un error grave desde el que no se puede recuperar.  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [CATCH](#catch).  

### <a name="requirements"></a>Requisitos  
  **Encabezado** afx.h   
  
## <a name="see-also"></a>Vea también  
 [Macros y funciones globales](../../mfc/reference/mfc-macros-and-globals.md)   
 [CException (clase)](../../mfc/reference/cexception-class.md)
