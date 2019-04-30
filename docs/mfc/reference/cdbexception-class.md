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
ms.openlocfilehash: 755b89635eedd7808f900dc63cd3039845db1dd3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62253418"
---
# <a name="cdbexception-class"></a>CDBException (clase)

Representa una condición de excepción que surge de las clases de base de datos.

## <a name="syntax"></a>Sintaxis

```
class CDBException : public CException
```

## <a name="members"></a>Miembros

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[CDBException::m_nRetCode](#m_nretcode)|Contiene un código de retorno de Open Database Connectivity (ODBC), de tipo RETCODE.|
|[CDBException::m_strError](#m_strerror)|Contiene una cadena que describe el error en términos alfanuméricos.|
|[CDBException::m_strStateNativeOrigin](#m_strstatenativeorigin)|Contiene una cadena que describe el error en cuanto a los códigos de error devuelto por ODBC.|

## <a name="remarks"></a>Comentarios

La clase incluye a dos miembros de datos públicos que puede usar para determinar la causa de la excepción o para mostrar un mensaje de texto que describe la excepción. `CDBException` los objetos se construye y producidos por las funciones miembro de las clases de base de datos.

> [!NOTE]
>  Esta clase es una de las clases de MFC Open Database Connectivity (ODBC). Si utiliza las clases de objetos de acceso a datos (DAO) más reciente en su lugar, use [CDaoException](../../mfc/reference/cdaoexception-class.md) en su lugar. Todos los nombres de clases DAO tengan "CDao" como prefijo. Para obtener más información, vea el artículo [información general: Programación de base de datos](../../data/data-access-programming-mfc-atl.md).

Las excepciones son casos de que impliquen condiciones ajenos al control del programa, como origen de datos de ejecución anormal o errores de E/S de red. Errores que es probable que vea en el curso normal de ejecutar el programa normalmente no se consideran excepciones.

Puede tener acceso a estos objetos dentro del ámbito de un **CATCH** expresión. También se puede producir `CDBException` objetos desde su propio código con el `AfxThrowDBException` función global.

Para obtener más información sobre el control de excepciones en general, o sobre `CDBException` objetos, consulte los artículos [de control de excepciones (MFC)](../../mfc/exception-handling-in-mfc.md) y [excepciones: Excepciones de base de datos](../../mfc/exceptions-database-exceptions.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`CDBException`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdb.h

##  <a name="m_nretcode"></a>  CDBException::m_nRetCode

Contiene un código de error ODBC de tipo RETCODE devuelto por una función de interfaz (API) de programación de aplicaciones de ODBC.

### <a name="remarks"></a>Comentarios

Este tipo incluye el prefijo SQL códigos de definida por ODBC y el prefijo AFX_SQL definido por las clases de base de datos. Para un `CDBException`, este miembro contendrá uno de los valores siguientes:

- El controlador AFX_SQL_ERROR_API_CONFORMANCE para un `CDatabase::OpenEx` o `CDatabase::Open` llamada no se ajusta a un nivel de conformidad de la API de ODBC requiere 1 (SQL_OAC_LEVEL1).

- No se pudo AFX_SQL_ERROR_CONNECT_FAIL conexión al origen de datos. Se pasó un valor NULL`CDatabase` puntero a su constructor de conjunto de registros y el intento siguiente para crear una conexión según `GetDefaultConnect` error.

- AFX_SQL_ERROR_DATA_TRUNCATED había solicitado más datos que ha proporcionado para el almacenamiento de información. Para obtener información acerca de cómo aumentar el almacenamiento de datos proporcionado para `CString` o `CByteArray` tipos de datos, vea el `nMaxLength` argumento para [RFX_Text](record-field-exchange-functions.md#rfx_text) y [RFX_Binary](record-field-exchange-functions.md#rfx_binary) bajo "Macros y Globals."

- Llamada A AFX_SQL_ERROR_DYNASET_NOT_SUPPORTED a `CRecordset::Open` que solicita un conjunto de registros dinámicos no se pudo. Conjuntos de registros dinámicos no admiten el controlador.

- AFX_SQL_ERROR_EMPTY_COLUMN_LIST ha intentado abrir una tabla (o lo que se le asignó no se puede identificar como una llamada a procedimiento o **seleccione** instrucción) pero no hay ninguna columna identificada en llamadas a funciones en campos de registros (RFX) de exchange su `DoFieldExchange` invalidar.

- El tipo de un RFX AFX_SQL_ERROR_FIELD_SCHEMA_MISMATCH funcionando en su `DoFieldExchange` reemplazo no es compatible con el tipo de datos de columna del conjunto de registros.

- AFX_SQL_ERROR_ILLEGAL_MODE se llamó `CRecordset::Update` sin antes de llamar a `CRecordset::AddNew` o `CRecordset::Edit`.

- No se pudo cumplir AFX_SQL_ERROR_LOCK_MODE_NOT_SUPPORTED su solicitud a los registros de bloqueo de actualización porque el controlador ODBC no admite el bloqueo.

- AFX_SQL_ERROR_MULTIPLE_ROWS_AFFECTED se llamó `CRecordset::Update` o `Delete` para una tabla con ninguna clave única y cambiar varios registros.

- AFX_SQL_ERROR_NO_CURRENT_RECORD ha intentado editar o eliminar un registro eliminado previamente. Debe desplazarse a un nuevo registro actual después de una eliminación.

- No se pudo cumplir la solicitud para un conjunto de registros dinámicos porque no es compatible con el controlador ODBC de AFX_SQL_ERROR_NO_POSITIONED_UPDATES actualizaciones posicionadas.

- AFX_SQL_ERROR_NO_ROWS_AFFECTED se llamó `CRecordset::Update` o `Delete`, pero cuando se inició la operación ya no se encontró el registro.

- AFX_SQL_ERROR_ODBC_LOAD_FAILED tratar de cargar el archivo ODBC. Error en la DLL; Windows no se podrían encontrar o no podrían cargar este archivo DLL. Este error es irrecuperable.

- AFX_SQL_ERROR_ODBC_V2_REQUIRED que no se pudo cumplir la solicitud para un conjunto de registros dinámicos porque es necesario un controlador ODBC nivel 2 conforme.

- Un intento de desplazar AFX_SQL_ERROR_RECORDSET_FORWARD_ONLY no se realizó correctamente porque el origen de datos no admite desplazamiento hacia atrás.

- Llamada A AFX_SQL_ERROR_SNAPSHOT_NOT_SUPPORTED a `CRecordset::Open` error solicitando una instantánea. No se admiten las instantáneas por el controlador. (Esto solo debe producirse cuando la biblioteca de cursores ODBC ODBCCURS. DLL no está presente.)

- El controlador AFX_SQL_ERROR_SQL_CONFORMANCE para un `CDatabase::OpenEx` o `CDatabase::Open` llamada no cumple el nivel de conformidad de ODBC SQL requerido de "Mínimo" (SQL_OSC_MINIMUM).

- Controlador ODBC AFX_SQL_ERROR_SQL_NO_TOTAL no pudo especificar el tamaño total de un `CLongBinary` valor de datos. La operación probablemente no se pudo porque no se pudo preasignado un bloque de memoria global.

- AFX_SQL_ERROR_RECORDSET_READONLY intentó actualizar un conjunto de registros de solo lectura o el origen de datos es de solo lectura. Puede realizarse ninguna operación de actualización con el conjunto de registros o el `CDatabase` está asociado el objeto.

- Error de la función SQL_ERROR. El mensaje de error devuelto por la función ODBC `SQLError` se almacena en el `m_strError` miembro de datos.

- No se pudo SQL_INVALID_HANDLE función debido a un identificador de entorno no válido, el identificador de conexión o el identificador de instrucción. Esto indica un error de programación. No hay información adicional está disponible en la función ODBC `SQLError`.

Los códigos de prefijo de SQL se definen mediante ODBC. Los códigos AFX fija se definen en AFXDB. H, se encuentra en MFC\INCLUDE.

##  <a name="m_strerror"></a>  CDBException::m_strError

Contiene una cadena que describe el error que provocó la excepción.

### <a name="remarks"></a>Comentarios

La cadena que describe el error en términos alfanuméricos. Para obtener más información y un ejemplo, consulte `m_strStateNativeOrigin`.

##  <a name="m_strstatenativeorigin"></a>  CDBException::m_strStateNativeOrigin

Contiene una cadena que describe el error que provocó la excepción.

### <a name="remarks"></a>Comentarios

La cadena tiene el formato "estado: % s, nativo: % ld, origen: % s", donde los códigos de formato, en orden, se reemplazan por valores que describen:

- El valor de SQLSTATE, una cadena terminada en null que contiene un código de error de cinco caracteres devuelto en el *szSqlState* parámetro de la función ODBC `SQLError`. Los valores de SQLSTATE se enumeran en el apéndice A, [códigos de Error ODBC](/previous-versions/windows/desktop/ms714687(v=vs.85)), en el *referencia del programador de ODBC*. Ejemplo: "S0022".

- Devuelve el código de error nativo específico del origen de datos, en el *pfNativeError* parámetro de la `SQLError` función. Ejemplo: 207.

- El texto del mensaje de error devuelto en el *szErrorMsg* parámetro de la `SQLError` función. Este mensaje se compone de varios nombres entre corchetes. Como un error se pasa desde su origen para el usuario, cada componente ODBC (origen de datos, controladores, Administrador de controladores) anexa su propio nombre. Esta información ayuda a identificar el origen del error. Ejemplo: [Microsoft] [controlador ODBC SQL Server] [SQL Server]

El marco de trabajo interpreta la cadena de error y pone sus componentes en `m_strStateNativeOrigin`; si `m_strStateNativeOrigin` contiene información de más de un error, los errores están separados por nuevas líneas. El marco de trabajo coloca el texto del error alfanumérico en `m_strError`.

Para obtener más información acerca de los códigos que se utiliza para realizar esta cadena, consulte la [SQLError](/previous-versions/windows/desktop/ms716312(v=vs.85)) funcionando en el *referencia del programador de ODBC*.

### <a name="example"></a>Ejemplo

  Desde ODBC: "Estado: S0022, nativo: 207, origen:\[Microsoft]\[controlador ODBC para SQL Server]\[SQL Server] nombre de columna no válido 'ColName'"

En `m_strStateNativeOrigin`: "Estado: S0022, nativo: 207, origen:\[Microsoft]\[controlador ODBC SQL Server]\[SQL Server]"

En `m_strError`: "Nombre de columna no válido 'ColName'"

## <a name="see-also"></a>Vea también

[CException (clase)](../../mfc/reference/cexception-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CDatabase (clase)](../../mfc/reference/cdatabase-class.md)<br/>
[CRecordset (clase)](../../mfc/reference/crecordset-class.md)<br/>
[CFieldExchange (clase)](../../mfc/reference/cfieldexchange-class.md)<br/>
[CRecordset::Update](../../mfc/reference/crecordset-class.md#update)<br/>
[CRecordset::Delete](../../mfc/reference/crecordset-class.md#delete)<br/>
[CException (clase)](../../mfc/reference/cexception-class.md)
