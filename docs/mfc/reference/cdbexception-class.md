---
title: Clase CDBException | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDBException
- AFXDB/CDBException
- AFXDB/CDBException::m_nRetCode
- AFXDB/CDBException::m_strError
- AFXDB/CDBException::m_strStateNativeOrigin
dev_langs:
- C++
helpviewer_keywords:
- CDBException [MFC], m_nRetCode
- CDBException [MFC], m_strError
- CDBException [MFC], m_strStateNativeOrigin
ms.assetid: eb9e1119-89f5-49a7-b9d4-b91cee1ccc82
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7766b56e75edefda4f40194a5ce18572c8d6d78d
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/26/2018
ms.locfileid: "36952253"
---
# <a name="cdbexception-class"></a>Clase CDBException
Representa una condición de excepción que surge de las clases de base de datos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CDBException : public CException  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDBException::m_nRetCode](#m_nretcode)|Contiene un código de retorno de Open Database Connectivity (ODBC), del tipo **RETCODE**.|  
|[CDBException::m_strError](#m_strerror)|Contiene una cadena que describe el error en términos alfanuméricos.|  
|[CDBException::m_strStateNativeOrigin](#m_strstatenativeorigin)|Contiene una cadena que describe el error en cuanto a los códigos de error devueltos por ODBC.|  
  
## <a name="remarks"></a>Comentarios  
 La clase incluye a dos miembros de datos públicos que se puede utilizar para determinar la causa de la excepción o para mostrar un mensaje de texto que describe la excepción. `CDBException` los objetos se construyen y producidos por las funciones miembro de las clases de base de datos.  
  
> [!NOTE]
>  Esta clase es una de las clases de MFC Open Database Connectivity (ODBC). Si usas las nuevas clases de Data Access Objects (DAO) en su lugar, use [CDaoException](../../mfc/reference/cdaoexception-class.md) en su lugar. Todos los nombres de clase DAO tienen "CDao" como prefijo. Para obtener más información, vea el artículo [información general: programación de base de datos](../../data/data-access-programming-mfc-atl.md).  
  
 Las excepciones son casos de ejecución anómala que implican condiciones fuera del control del programa, como el origen de datos o errores de E/S de red. Errores que podrían esperar para ver en el curso normal de ejecutar el programa normalmente no se consideran excepciones.  
  
 Puede tener acceso a estos objetos dentro del ámbito de un **CATCH** expresión. También se puede producir `CDBException` objetos desde su propio código con el `AfxThrowDBException` función global.  
  
 Para obtener más información sobre el control de excepciones en general o sobre `CDBException` objetos, consulte los artículos [de control de excepciones (MFC)](../../mfc/exception-handling-in-mfc.md) y [excepciones: excepciones de base de datos](../../mfc/exceptions-database-exceptions.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 `CDBException`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdb.h  
  
##  <a name="m_nretcode"></a>  CDBException::m_nRetCode  
 Contiene un código de error ODBC de tipo **RETCODE** devuelto por una función (API) de la interfaz de programación de aplicaciones de ODBC.  
  
### <a name="remarks"></a>Comentarios  
 Este tipo incluye el prefijo SQL códigos de definidas por ODBC y el prefijo AFX_SQL definidas por las clases de base de datos. Para una `CDBException`, este miembro contendrá uno de los valores siguientes:  
  
- **AFX_SQL_ERROR_API_CONFORMANCE** el controlador para un `CDatabase::OpenEx` o `CDatabase::Open` llamada no se ajusta a un nivel de conformidad de la API de ODBC requiere 1 ( **SQL_OAC_LEVEL1**).  
  
- **AFX_SQL_ERROR_CONNECT_FAIL** no se pudo conectar al origen de datos. Se pasa un **NULL** `CDatabase` tomando como puntero a su constructor de conjunto de registros y el intento siguiente para crear una conexión `GetDefaultConnect` error.  
  
- **AFX_SQL_ERROR_DATA_TRUNCATED** solicita más datos de los que ha proporcionado para el almacenamiento de información. Para obtener información acerca de cómo aumentar el almacenamiento de datos proporcionado para `CString` o `CByteArray` tipos de datos, vea el `nMaxLength` argumento para [RFX_Text](record-field-exchange-functions.md#rfx_text) y [RFX_Binary](record-field-exchange-functions.md#rfx_binary) en "Macros y Globals."  
  
- **AFX_SQL_ERROR_DYNASET_NOT_SUPPORTED** una llamada a `CRecordset::Open` solicitar un conjunto de registros dinámicos no se pudo. Conjuntos de registros dinámicos no admiten el controlador.  
  
- **AFX_SQL_ERROR_EMPTY_COLUMN_LIST** ha intentado abrir una tabla (o lo que se le asignó no pudo identificarse como una llamada a procedimiento o **seleccione** instrucción) pero no hay ninguna columna identificada en el intercambio de campos de registros (RFX) función que se llama su `DoFieldExchange` invalidar.  
  
- **AFX_SQL_ERROR_FIELD_SCHEMA_MISMATCH** el tipo de una función RFX en su `DoFieldExchange` invalidación no es compatible con el tipo de datos de columna del conjunto de registros.  
  
- **AFX_SQL_ERROR_ILLEGAL_MODE** se llamó `CRecordset::Update` sin llamar previamente `CRecordset::AddNew` o `CRecordset::Edit`.  
  
- **AFX_SQL_ERROR_LOCK_MODE_NOT_SUPPORTED** no se ha podido cumplir la solicitud a los registros de bloqueo de actualización porque el controlador ODBC no admite el bloqueo.  
  
- **AFX_SQL_ERROR_MULTIPLE_ROWS_AFFECTED** se llamó `CRecordset::Update` o `Delete` para una tabla con ninguna clave única y cambiar varios registros.  
  
- **AFX_SQL_ERROR_NO_CURRENT_RECORD** se intentó editar o eliminar un registro eliminado previamente. Debe desplazar a un nuevo registro actual después de una operación de eliminación.  
  
- **AFX_SQL_ERROR_NO_POSITIONED_UPDATES** su solicitud para un conjunto de registros dinámicos no se pudo cumplir porque el controlador ODBC no admite actualizaciones posicionadas.  
  
- **AFX_SQL_ERROR_NO_ROWS_AFFECTED** se llamó `CRecordset::Update` o `Delete`, pero cuando se inició la operación ya no se encontró el registro.  
  
- **AFX_SQL_ERROR_ODBC_LOAD_FAILED** tratar de cargar el archivo ODBC. No se pudo DLL; Windows no se pudo encontrar o no pudo cargar este archivo DLL. Este error es irrecuperable.  
  
- **AFX_SQL_ERROR_ODBC_V2_REQUIRED** no se ha podido cumplir la solicitud para un conjunto de registros dinámicos porque se requiere un controlador ODBC nivel 2 compatible.  
  
- **AFX_SQL_ERROR_RECORDSET_FORWARD_ONLY** intenta desplazarse no se realizó correctamente porque el origen de datos no admite el desplazamiento hacia atrás.  
  
- **AFX_SQL_ERROR_SNAPSHOT_NOT_SUPPORTED** una llamada a `CRecordset::Open` solicitar una instantánea de error. No se admiten las instantáneas por el controlador. (Esto solo debe ocurrir cuando la biblioteca de cursores ODBC ODBCCURS. DLL no está presente).  
  
- **AFX_SQL_ERROR_SQL_CONFORMANCE** el controlador para un `CDatabase::OpenEx` o `CDatabase::Open` llamada no cumple el nivel de conformidad de SQL de ODBC requerido del "Mínimo" ( **SQL_OSC_MINIMUM**).  
  
- **AFX_SQL_ERROR_SQL_NO_TOTAL** controlador ODBC el no pudo especificar el tamaño total de un `CLongBinary` valor de datos. Probablemente se error en la operación porque no se pudo preasignado un bloque de memoria global.  
  
- **AFX_SQL_ERROR_RECORDSET_READONLY** ha intentado actualizar un conjunto de registros de solo lectura o el origen de datos es de solo lectura. No hay ninguna operación de actualización puede realizarse con el conjunto de registros o el `CDatabase` que está asociado el objeto.  
  
- **SQL_ERROR** error de la función. El mensaje de error devuelto por la función ODBC `SQLError` se almacena en la **m_strError** miembro de datos.  
  
- **SQL_INVALID_HANDLE** función error debido a un identificador de entorno no válido, el identificador de conexión o el identificador de instrucción. Esto indica un error de programación. No hay información adicional está disponible en la función ODBC **SQLError**.  
  
 Los códigos de prefijo de SQL se definen mediante ODBC. Los códigos de prefijo AFX se definen en AFXDB. H, se encuentra en MFC\INCLUDE.  
  
##  <a name="m_strerror"></a>  CDBException::m_strError  
 Contiene una cadena que describe el error que provocó la excepción.  
  
### <a name="remarks"></a>Comentarios  
 La cadena describe el error en términos alfanuméricos. Para obtener más información y un ejemplo, vea **m_strStateNativeOrigin**.  
  
##  <a name="m_strstatenativeorigin"></a>  CDBException::m_strStateNativeOrigin  
 Contiene una cadena que describe el error que provocó la excepción.  
  
### <a name="remarks"></a>Comentarios  
 La cadena tiene la forma "estado: % s, nativo: % ld, origen: % s", donde los códigos de formato, en orden, se reemplazan por valores que describen:  
  
-   El **SQLSTATE**, una cadena terminada en null que contiene un código de error de cinco caracteres devuelto en el *szSqlState* parámetro de la función ODBC `SQLError`. **SQLSTATE** valores se muestran en el apéndice A, [códigos de Error de ODBC](https://msdn.microsoft.com/library/ms714687.aspx), en la *referencia del programador de ODBC*. Ejemplo: "S0022".  
  
-   Devuelve el código de error nativo, específico del origen de datos, en la *pfNativeError* parámetro de la `SQLError` (función). Ejemplo: 207.  
  
-   El texto del mensaje de error devuelto en el *szErrorMsg* parámetro de la `SQLError` (función). Este mensaje está formada por varios nombres entre corchetes. Tal y como se pasa un error de su origen para el usuario, cada componente ODBC (origen de datos, controlador, el Administrador de controladores) anexa su propio nombre. Esta información ayuda a identificar el origen del error. Ejemplo: [Microsoft] [controlador ODBC SQL Server] [SQL Server]  
  
 El marco de trabajo interpretará la cadena de error y pone sus componentes en **m_strStateNativeOrigin**; si **m_strStateNativeOrigin** contiene información por más de un error, los errores se separan por líneas nuevas. El marco de trabajo coloca el texto del error alfanuméricos en **m_strError**.  
  
 Para obtener información adicional acerca de los códigos que se utilizan para recuperar esta cadena, vea la [SQLError](https://msdn.microsoft.com/library/ms716312.aspx) funcionando en el *referencia del programador de ODBC*.  
  
### <a name="example"></a>Ejemplo  
  De ODBC: "Estado: S0022, nativo: 207, origen: [Microsoft] [controlador ODBC SQL Server] nombre de columna no válido [SQL Server] 'ColName'"  
  
 En **m_strStateNativeOrigin**: "estado: S0022, nativo: 207, origen: [Microsoft] [controlador ODBC SQL Server] [SQL Server]"  
  
 En **m_strError**: "nombre de columna no válido 'ColName'"  
  
## <a name="see-also"></a>Vea también  
 [CException (clase)](../../mfc/reference/cexception-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CDatabase (clase)](../../mfc/reference/cdatabase-class.md)   
 [CRecordset (clase)](../../mfc/reference/crecordset-class.md)   
 [Clase CFieldExchange](../../mfc/reference/cfieldexchange-class.md)   
 [CRecordset:: Update](../../mfc/reference/crecordset-class.md#update)   
 [CRecordset::Delete](../../mfc/reference/crecordset-class.md#delete)   
 [CException (clase)](../../mfc/reference/cexception-class.md)
