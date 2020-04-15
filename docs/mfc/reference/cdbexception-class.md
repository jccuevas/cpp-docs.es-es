---
title: CDBException (clase)
ms.date: 11/04/2016
f1_keywords:
- CDBException
- AFXDB/CDBException
- AFXDB/CDBException::m_nRetCode
- AFXDB/CDBException::m_strError
- AFXDB/CDBException::m_strStateNativeOrigin
helpviewer_keywords:
- CDBException [MFC], m_nRetCode
- CDBException [MFC], m_strError
- CDBException [MFC], m_strStateNativeOrigin
ms.assetid: eb9e1119-89f5-49a7-b9d4-b91cee1ccc82
ms.openlocfilehash: 1ab7daeb3af55c92985c951c632b1d4050681474
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321893"
---
# <a name="cdbexception-class"></a>CDBException (clase)

Representa una condición de excepción que surge de las clases de base de datos.

## <a name="syntax"></a>Sintaxis

```
class CDBException : public CException
```

## <a name="members"></a>Miembros

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CDBException::m_nRetCode](#m_nretcode)|Contiene un código de retorno de conectividad abierta de base de datos (ODBC), de tipo RETCODE.|
|[CDBException::m_strError](#m_strerror)|Contiene una cadena que describe el error en términos alfanuméricos.|
|[CDBException::m_strStateNativeOrigin](#m_strstatenativeorigin)|Contiene una cadena que describe el error en términos de los códigos de error devueltos por ODBC.|

## <a name="remarks"></a>Observaciones

La clase incluye dos miembros de datos públicos que puede usar para determinar la causa de la excepción o para mostrar un mensaje de texto que describe la excepción. `CDBException`objetos se construyen y se producen mediante las funciones miembro de las clases de base de datos.

> [!NOTE]
> Esta clase es una de las clases de conectividad de base de datos abierta (ODBC) de MFC. Si en su lugar está utilizando las clases de objetos de acceso a datos (DAO) más recientes, utilice [CDaoException](../../mfc/reference/cdaoexception-class.md) en su lugar. Todos los nombres de clase DAO tienen "CDao" como prefijo. Para obtener más información, consulte el artículo [Información general: Programación](../../data/data-access-programming-mfc-atl.md)de bases de datos .

Las excepciones son casos de ejecución anormal que implican condiciones fuera del control del programa, como errores de E/S de red o de origen de datos. Los errores que puede esperar ver en el curso normal de la ejecución del programa normalmente no se consideran excepciones.

Puede tener acceso a estos objetos dentro del ámbito de una expresión **CATCH.** También puede `CDBException` lanzar objetos desde `AfxThrowDBException` su propio código con la función global.

Para obtener más información sobre el `CDBException` control de excepciones en general o sobre objetos, vea los artículos Control de excepciones [(MFC)](../../mfc/exception-handling-in-mfc.md) y [Excepciones: Excepciones](../../mfc/exceptions-database-exceptions.md)de base de datos .

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`CDBException`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdb.h

## <a name="cdbexceptionm_nretcode"></a><a name="m_nretcode"></a>CDBException::m_nRetCode

Contiene un código de error ODBC de tipo RETCODE devuelto por una función de interfaz de programación de aplicaciones (API) ODBC.

### <a name="remarks"></a>Observaciones

Este tipo incluye códigos con prefijo SQL definidos por ODBC y códigos con prefijo AFX_SQL definidos por las clases de base de datos. Para `CDBException`un , este miembro contendrá uno de los siguientes valores:

- AFX_SQL_ERROR_API_CONFORMANCE El controlador `CDatabase::OpenEx` `CDatabase::Open` de una llamada o no se ajusta al nivel de conformidad de la API ODBC requerido 1 ( SQL_OAC_LEVEL1).

- AFX_SQL_ERROR_CONNECT_FAIL Error en la conexión al origen de datos. Pasó un`CDatabase` puntero NULL al constructor del conjunto de registros y el intento posterior de crear una conexión basada en `GetDefaultConnect` un error.

- AFX_SQL_ERROR_DATA_TRUNCATED Ha solicitado más datos de los que ha proporcionado almacenamiento. Para obtener información sobre cómo `CString` `CByteArray` aumentar el almacenamiento `nMaxLength` de datos proporcionado para los tipos de datos o el almacenamiento de datos, consulte el argumento de [RFX_Text](record-field-exchange-functions.md#rfx_text) y [RFX_Binary](record-field-exchange-functions.md#rfx_binary) en "Macros y valores globales."

- Error AFX_SQL_ERROR_DYNASET_NOT_SUPPORTED `CRecordset::Open` una llamada a la solicitud de un conjunto de registros dinámicos. Dynasets no son compatibles con el controlador.

- AFX_SQL_ERROR_EMPTY_COLUMN_LIST Intentó abrir una tabla (o lo que proporcionó no se pudo identificar como una llamada a procedimiento o una `DoFieldExchange` instrucción **SELECT)** pero no hay columnas identificadas en las llamadas de función de intercambio de campos de registros (RFX) en la invalidación.

- AFX_SQL_ERROR_FIELD_SCHEMA_MISMATCH El tipo de una `DoFieldExchange` función RFX en la invalidación no es compatible con el tipo de datos de columna en el conjunto de registros.

- AFX_SQL_ERROR_ILLEGAL_MODE Llamaste `CRecordset::Update` sin llamar `CRecordset::AddNew` o . `CRecordset::Edit`

- AFX_SQL_ERROR_LOCK_MODE_NOT_SUPPORTED No se pudo cumplir la solicitud de bloqueo de registros para la actualización porque el controlador ODBC no admite el bloqueo.

- AFX_SQL_ERROR_MULTIPLE_ROWS_AFFECTED llamó `CRecordset::Update` `Delete` o para una tabla sin clave única y cambió varios registros.

- AFX_SQL_ERROR_NO_CURRENT_RECORD Ha intentado editar o eliminar un registro eliminado anteriormente. Debe desplazarse a un nuevo registro actual después de una eliminación.

- AFX_SQL_ERROR_NO_POSITIONED_UPDATES No se pudo satisfacer la solicitud de un conjunto de registros dinámicos porque el controlador ODBC no admite actualizaciones posicionadas.

- AFX_SQL_ERROR_NO_ROWS_AFFECTED llamó `CRecordset::Update` `Delete`o , pero cuando comenzó la operación, ya no se pudo encontrar el registro.

- AFX_SQL_ERROR_ODBC_LOAD_FAILED Un intento de cargar ODBC. Error en DLL; Windows no pudo encontrar o no pudo cargar este archivo DLL. Este error es fatal.

- AFX_SQL_ERROR_ODBC_V2_REQUIRED No se pudo satisfacer la solicitud de un conjunto de registros dinámicos porque se requiere un controlador ODBC compatible con Level 2.

- AFX_SQL_ERROR_RECORDSET_FORWARD_ONLY Un intento de desplazamiento no se realizó correctamente porque el origen de datos no admite el desplazamiento hacia atrás.

- Error AFX_SQL_ERROR_SNAPSHOT_NOT_SUPPORTED `CRecordset::Open` una llamada a la solicitud de una instantánea. El controlador no admite las instantáneas. (Esto solo debe ocurrir cuando la biblioteca de cursores ODBCCURS. DLL no está presente.)

- AFX_SQL_ERROR_SQL_CONFORMANCE El controlador `CDatabase::OpenEx` `CDatabase::Open` de una llamada o llamada no se ajusta al nivel de conformidad SQL ODBC necesario de "Mínimo" (SQL_OSC_MINIMUM).

- AFX_SQL_ERROR_SQL_NO_TOTAL El controlador ODBC no pudo especificar `CLongBinary` el tamaño total de un valor de datos. La operación probablemente falló porque no se pudo preasignar un bloque de memoria global.

- AFX_SQL_ERROR_RECORDSET_READONLY Ha intentado actualizar un conjunto de registros de solo lectura o el origen de datos es de solo lectura. No se puede realizar ninguna operación de actualización con el conjunto de registros o el `CDatabase` objeto al que está asociado.

- Error en la función de SQL_ERROR. El mensaje de error `SQLError` devuelto por `m_strError` la función ODBC se almacena en el miembro de datos.

- SQL_INVALID_HANDLE Función ha fallado debido a un identificador de entorno no válido, identificador de conexión o identificador de instrucción. Esto indica un error de programación. No hay información adicional disponible `SQLError`en la función ODBC .

ODBC define los códigos con prefijo SQL. Los códigos con prefijo AFX se definen en AFXDB. H, que se encuentra en MFC-INCLUDE.

## <a name="cdbexceptionm_strerror"></a><a name="m_strerror"></a>CDBException::m_strError

Contiene una cadena que describe el error que causó la excepción.

### <a name="remarks"></a>Observaciones

La cadena describe el error en términos alfanuméricos. Para obtener información más detallada `m_strStateNativeOrigin`y un ejemplo, consulte .

## <a name="cdbexceptionm_strstatenativeorigin"></a><a name="m_strstatenativeorigin"></a>CDBException::m_strStateNativeOrigin

Contiene una cadena que describe el error que causó la excepción.

### <a name="remarks"></a>Observaciones

La cadena tiene la forma "State:%s,Native:%ld,Origin:%s", donde los códigos de formato, en orden, se reemplazan por valores que describen:

- SQLSTATE, una cadena terminada en null que contiene un código de error de cinco `SQLError`caracteres devuelto en el parámetro *szSqlState* de la función ODBC . Los valores SQLSTATE se enumeran en el Apéndice A, [Códigos](/sql/odbc/reference/appendixes/appendix-a-odbc-error-codes)de error ODBC , en Referencia *del programador ODBC*. Ejemplo: "S0022".

- El código de error nativo, específico del origen de datos, devuelto en el parámetro *pfNativeError* de la `SQLError` función. Ejemplo: 207.

- El texto del mensaje de error devuelto `SQLError` en el parámetro *szErrorMsg* de la función. Este mensaje consta de varios nombres entre corchetes. A medida que se pasa un error de su origen al usuario, cada componente ODBC (origen de datos, controlador, Administrador de controladores) anexa su propio nombre. Esta información ayuda a identificar el origen del error. Ejemplo: [Microsoft][Controlador DE SQL Server ODBC][SQL Server]

El marco de trabajo interpreta la cadena `m_strStateNativeOrigin`de error y coloca sus componentes en ; si `m_strStateNativeOrigin` contiene información para más de un error, los errores están separados por líneas nuevas. El marco de trabajo coloca `m_strError`el texto de error alfanumérico en .

Para obtener información adicional acerca de los códigos utilizados para componer esta cadena, vea la función [SQLError](/sql/odbc/reference/syntax/sqlerror-function) en la *referencia del programador ODBC*.

### <a name="example"></a>Ejemplo

Desde ODBC:\["State:S0022,Native:207,Origin:\[Microsoft] ODBC\[SQL Server Driver] SQL Server] Nombre de columna no válido 'ColName'"

En `m_strStateNativeOrigin`:\["State:S0022,Native:207,Origin:\[Microsoft] ODBC\[SQL Server Driver] SQL Server]"

En `m_strError`: "Nombre de columna no válido 'ColName'"

## <a name="see-also"></a>Consulte también

[Clase CException](../../mfc/reference/cexception-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clase CDatabase](../../mfc/reference/cdatabase-class.md)<br/>
[Clase CRecordset](../../mfc/reference/crecordset-class.md)<br/>
[Clase CFieldExchange](../../mfc/reference/cfieldexchange-class.md)<br/>
[CRecordset::Update](../../mfc/reference/crecordset-class.md#update)<br/>
[CRecordset::Delete](../../mfc/reference/crecordset-class.md#delete)<br/>
[Clase CException](../../mfc/reference/cexception-class.md)
