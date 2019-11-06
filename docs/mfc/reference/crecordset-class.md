---
title: CRecordset (clase)
ms.date: 11/04/2016
f1_keywords:
- CRecordset
- AFXDB/CRecordset
- AFXDB/CRecordset::CRecordset
- AFXDB/CRecordset::AddNew
- AFXDB/CRecordset::CanAppend
- AFXDB/CRecordset::CanBookmark
- AFXDB/CRecordset::Cancel
- AFXDB/CRecordset::CancelUpdate
- AFXDB/CRecordset::CanRestart
- AFXDB/CRecordset::CanScroll
- AFXDB/CRecordset::CanTransact
- AFXDB/CRecordset::CanUpdate
- AFXDB/CRecordset::CheckRowsetError
- AFXDB/CRecordset::Close
- AFXDB/CRecordset::Delete
- AFXDB/CRecordset::DoBulkFieldExchange
- AFXDB/CRecordset::DoFieldExchange
- AFXDB/CRecordset::Edit
- AFXDB/CRecordset::FlushResultSet
- AFXDB/CRecordset::GetBookmark
- AFXDB/CRecordset::GetDefaultConnect
- AFXDB/CRecordset::GetDefaultSQL
- AFXDB/CRecordset::GetFieldValue
- AFXDB/CRecordset::GetODBCFieldCount
- AFXDB/CRecordset::GetODBCFieldInfo
- AFXDB/CRecordset::GetRecordCount
- AFXDB/CRecordset::GetRowsetSize
- AFXDB/CRecordset::GetRowsFetched
- AFXDB/CRecordset::GetRowStatus
- AFXDB/CRecordset::GetSQL
- AFXDB/CRecordset::GetStatus
- AFXDB/CRecordset::GetTableName
- AFXDB/CRecordset::IsBOF
- AFXDB/CRecordset::IsDeleted
- AFXDB/CRecordset::IsEOF
- AFXDB/CRecordset::IsFieldDirty
- AFXDB/CRecordset::IsFieldNull
- AFXDB/CRecordset::IsFieldNullable
- AFXDB/CRecordset::IsOpen
- AFXDB/CRecordset::Move
- AFXDB/CRecordset::MoveFirst
- AFXDB/CRecordset::MoveLast
- AFXDB/CRecordset::MoveNext
- AFXDB/CRecordset::MovePrev
- AFXDB/CRecordset::OnSetOptions
- AFXDB/CRecordset::OnSetUpdateOptions
- AFXDB/CRecordset::Open
- AFXDB/CRecordset::RefreshRowset
- AFXDB/CRecordset::Requery
- AFXDB/CRecordset::SetAbsolutePosition
- AFXDB/CRecordset::SetBookmark
- AFXDB/CRecordset::SetFieldDirty
- AFXDB/CRecordset::SetFieldNull
- AFXDB/CRecordset::SetLockingMode
- AFXDB/CRecordset::SetParamNull
- AFXDB/CRecordset::SetRowsetCursorPosition
- AFXDB/CRecordset::SetRowsetSize
- AFXDB/CRecordset::Update
- AFXDB/CRecordset::m_hstmt
- AFXDB/CRecordset::m_nFields
- AFXDB/CRecordset::m_nParams
- AFXDB/CRecordset::m_pDatabase
- AFXDB/CRecordset::m_strFilter
- AFXDB/CRecordset::m_strSort
helpviewer_keywords:
- CRecordset [MFC], CRecordset
- CRecordset [MFC], AddNew
- CRecordset [MFC], CanAppend
- CRecordset [MFC], CanBookmark
- CRecordset [MFC], Cancel
- CRecordset [MFC], CancelUpdate
- CRecordset [MFC], CanRestart
- CRecordset [MFC], CanScroll
- CRecordset [MFC], CanTransact
- CRecordset [MFC], CanUpdate
- CRecordset [MFC], CheckRowsetError
- CRecordset [MFC], Close
- CRecordset [MFC], Delete
- CRecordset [MFC], DoBulkFieldExchange
- CRecordset [MFC], DoFieldExchange
- CRecordset [MFC], Edit
- CRecordset [MFC], FlushResultSet
- CRecordset [MFC], GetBookmark
- CRecordset [MFC], GetDefaultConnect
- CRecordset [MFC], GetDefaultSQL
- CRecordset [MFC], GetFieldValue
- CRecordset [MFC], GetODBCFieldCount
- CRecordset [MFC], GetODBCFieldInfo
- CRecordset [MFC], GetRecordCount
- CRecordset [MFC], GetRowsetSize
- CRecordset [MFC], GetRowsFetched
- CRecordset [MFC], GetRowStatus
- CRecordset [MFC], GetSQL
- CRecordset [MFC], GetStatus
- CRecordset [MFC], GetTableName
- CRecordset [MFC], IsBOF
- CRecordset [MFC], IsDeleted
- CRecordset [MFC], IsEOF
- CRecordset [MFC], IsFieldDirty
- CRecordset [MFC], IsFieldNull
- CRecordset [MFC], IsFieldNullable
- CRecordset [MFC], IsOpen
- CRecordset [MFC], Move
- CRecordset [MFC], MoveFirst
- CRecordset [MFC], MoveLast
- CRecordset [MFC], MoveNext
- CRecordset [MFC], MovePrev
- CRecordset [MFC], OnSetOptions
- CRecordset [MFC], OnSetUpdateOptions
- CRecordset [MFC], Open
- CRecordset [MFC], RefreshRowset
- CRecordset [MFC], Requery
- CRecordset [MFC], SetAbsolutePosition
- CRecordset [MFC], SetBookmark
- CRecordset [MFC], SetFieldDirty
- CRecordset [MFC], SetFieldNull
- CRecordset [MFC], SetLockingMode
- CRecordset [MFC], SetParamNull
- CRecordset [MFC], SetRowsetCursorPosition
- CRecordset [MFC], SetRowsetSize
- CRecordset [MFC], Update
- CRecordset [MFC], m_hstmt
- CRecordset [MFC], m_nFields
- CRecordset [MFC], m_nParams
- CRecordset [MFC], m_pDatabase
- CRecordset [MFC], m_strFilter
- CRecordset [MFC], m_strSort
ms.assetid: dd89a21d-ef39-4aab-891b-1e373d67c855
ms.openlocfilehash: 1ebdb18254171d28b5d5e02367596b79142df284
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626187"
---
# <a name="crecordset-class"></a>CRecordset (clase)

Representa un conjunto de registros seleccionados de un origen de datos.

## <a name="syntax"></a>Sintaxis

```
class CRecordset : public CObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CRecordset:: CRecordset](#crecordset)|Construye un objeto `CRecordset`. La clase derivada debe proporcionar un constructor que llame a este.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CRecordset:: AddNew](#addnew)|Prepara para agregar un nuevo registro. Llame a `Update` para completar la adición.|
|[CRecordset:: CanAppend](#canappend)|Devuelve un valor distinto de cero si se pueden agregar nuevos registros al conjunto de registros a través de la función miembro `AddNew`.|
|[CRecordset:: CanBookmark](#canbookmark)|Devuelve un valor distinto de cero si el conjunto de registros admite marcadores.|
|[CRecordset:: CANCEL](#cancel)|Cancela una operación asincrónica o un proceso de un segundo subproceso.|
|[CRecordset:: CancelUpdate](#cancelupdate)|Cancela cualquier actualización pendiente debido a una operación `AddNew` o `Edit`.|
|[CRecordset:: CanRestart](#canrestart)|Devuelve un valor distinto de cero si se puede llamar a `Requery` para volver a ejecutar la consulta del conjunto de registros.|
|[CRecordset:: CanScroll](#canscroll)|Devuelve un valor distinto de cero si puede desplazarse por los registros.|
|[CRecordset:: CanTransact](#cantransact)|Devuelve un valor distinto de cero si el origen de datos admite transacciones.|
|[CRecordset:: CanUpdate](#canupdate)|Devuelve un valor distinto de cero si el conjunto de registros se puede actualizar (puede Agregar, actualizar o eliminar registros).|
|[CRecordset:: CheckRowsetError](#checkrowseterror)|Se llama para controlar los errores generados durante la captura de registros.|
|[CRecordset:: Close](#close)|Cierra el conjunto de registros y el HSTMT de ODBC asociado a él.|
|[CRecordset::D iminar](#delete)|Elimina el registro actual del conjunto de registros. Debe desplazarse explícitamente a otro registro después de la eliminación.|
|[CRecordset::D oBulkFieldExchange](#dobulkfieldexchange)|Se llama para intercambiar filas de datos masivas del origen de datos al conjunto de registros. Implementa el intercambio masivo de campos de registros (RFX masivo).|
|[CRecordset::D oFieldExchange](#dofieldexchange)|Se llama para intercambiar datos (en ambas direcciones) entre los miembros de datos de campo del conjunto de registros y el registro correspondiente en el origen de datos. Implementa el intercambio de campos de registros (RFX).|
|[CRecordset:: Edit](#edit)|Prepara los cambios en el registro actual. Llame a `Update` para completar la edición.|
|[CRecordset:: FlushResultSet](#flushresultset)|Devuelve un valor distinto de cero si hay otro conjunto de resultados que se va a recuperar, cuando se usa una consulta predefinida.|
|[CRecordset:: GetBookmark](#getbookmark)|Asigna el valor de marcador de un registro al objeto de parámetro.|
|[CRecordset:: GetDefaultConnect](#getdefaultconnect)|Se llama para obtener la cadena de conexión predeterminada.|
|[CRecordset:: GetDefaultSQL](#getdefaultsql)|Se llama para obtener la cadena SQL predeterminada que se va a ejecutar.|
|[CRecordset:: GetFieldValue](#getfieldvalue)|Devuelve el valor de un campo de un conjunto de registros.|
|[CRecordset:: GetODBCFieldCount](#getodbcfieldcount)|Devuelve el número de campos del conjunto de registros.|
|[CRecordset:: GetODBCFieldInfo](#getodbcfieldinfo)|Devuelve tipos específicos de información sobre los campos de un conjunto de registros.|
|[CRecordset:: GetRecordCount](#getrecordcount)|Devuelve el número de registros del conjunto de registros.|
|[CRecordset:: GetRowsetSize](#getrowsetsize)|Devuelve el número de registros que se van a recuperar durante una sola captura.|
|[CRecordset:: GetRowsFetched](#getrowsfetched)|Devuelve el número real de filas recuperadas durante una captura.|
|[CRecordset:: GetRowStatus](#getrowstatus)|Devuelve el estado de la fila después de una captura.|
|[CRecordset:: GetSQL](#getsql)|Obtiene la cadena de SQL utilizada para seleccionar los registros del conjunto de registros.|
|[CRecordset:: GetStatus](#getstatus)|Obtiene el estado del conjunto de registros: el índice del registro actual y si se ha obtenido un recuento final de los registros.|
|[CRecordset:: GetTableName](#gettablename)|Obtiene el nombre de la tabla en la que se basa el conjunto de registros.|
|[CRecordset:: IsBOF](#isbof)|Devuelve un valor distinto de cero si el conjunto de registros se ha colocado antes del primer registro. No hay ningún registro actual.|
|[CRecordset:: IsDeleted](#isdeleted)|Devuelve un valor distinto de cero si el conjunto de registros está colocado en un registro eliminado.|
|[CRecordset:: IsEOF](#iseof)|Devuelve un valor distinto de cero si el conjunto de registros se ha colocado después del último registro. No hay ningún registro actual.|
|[CRecordset:: IsFieldDirty](#isfielddirty)|Devuelve un valor distinto de cero si se ha cambiado el campo especificado en el registro actual.|
|[CRecordset:: IsFieldNull](#isfieldnull)|Devuelve un valor distinto de cero si el campo especificado en el registro actual es null (no tiene ningún valor).|
|[CRecordset:: IsFieldNullable](#isfieldnullable)|Devuelve un valor distinto de cero si el campo especificado del registro actual se puede establecer en null (no tiene ningún valor).|
|[CRecordset:: IsOpen](#isopen)|Devuelve un valor distinto de cero si se ha llamado previamente a `Open`.|
|[CRecordset:: Move](#move)|Coloca el conjunto de registros en un número especificado de registros del registro actual en cualquier dirección.|
|[CRecordset:: MoveFirst](#movefirst)|Coloca el registro actual en el primer registro del conjunto de registros. Pruebe `IsBOF` primero.|
|[CRecordset:: MoveLast](#movelast)|Coloca el registro actual en el último registro o en el último conjunto de filas. Pruebe `IsEOF` primero.|
|[CRecordset:: MoveNext](#movenext)|Coloca el registro actual en el siguiente registro o en el conjunto de filas siguiente. Pruebe `IsEOF` primero.|
|[CRecordset:: MovePrev](#moveprev)|Coloca el registro actual en el registro anterior o en el conjunto de filas anterior. Pruebe `IsBOF` primero.|
|[CRecordset:: OnSetOptions](#onsetoptions)|Se llama para establecer las opciones (utilizadas en la selección) para la instrucción ODBC especificada.|
|[CRecordset:: OnSetUpdateOptions](#onsetupdateoptions)|Se llama para establecer las opciones (utilizadas en la actualización) para la instrucción ODBC especificada.|
|[CRecordset:: Open](#open)|Abre el conjunto de registros recuperando la tabla o realizando la consulta que el conjunto de registros representa.|
|[CRecordset:: RefreshRowset](#refreshrowset)|Actualiza los datos y el estado de las filas especificadas.|
|[CRecordset:: Requery](#requery)|Vuelve a ejecutar la consulta del conjunto de registros para actualizar los registros seleccionados.|
|[CRecordset:: SetAbsolutePosition](#setabsoluteposition)|Coloca el conjunto de registros en el registro correspondiente al número de registro especificado.|
|[CRecordset:: SetBookmark](#setbookmark)|Coloca el conjunto de registros en el registro especificado por el marcador.|
|[CRecordset:: SetFieldDirty](#setfielddirty)|Marca el campo especificado en el registro actual como modificado.|
|[CRecordset:: SetFieldNull](#setfieldnull)|Establece el valor del campo especificado en el registro actual en null (sin valor).|
|[CRecordset:: SetLockingMode](#setlockingmode)|Establece el modo de bloqueo en bloqueo "optimista" (valor predeterminado) o "pesimista". Determina cómo se bloquean las actualizaciones de los registros.|
|[CRecordset:: SetParamNull](#setparamnull)|Establece el parámetro especificado en null (no tiene ningún valor).|
|[CRecordset:: SetRowsetCursorPosition](#setrowsetcursorposition)|Coloca el cursor en la fila especificada del conjunto de filas.|
|[CRecordset:: SetRowsetSize](#setrowsetsize)|Especifica el número de registros que se van a recuperar durante una captura.|
|[CRecordset:: Update](#update)|Completa una operación de `AddNew` o `Edit` guardando los datos nuevos o editados en el origen de datos.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[CRecordset:: m_hstmt](#m_hstmt)|Contiene el identificador de instrucción ODBC para el conjunto de registros. Escriba `HSTMT`.|
|[CRecordset:: m_nFields](#m_nfields)|Contiene el número de miembros de datos de campo en el conjunto de registros. Escriba `UINT`.|
|[CRecordset:: m_nParams](#m_nparams)|Contiene el número de miembros de datos de parámetro del conjunto de registros. Escriba `UINT`.|
|[CRecordset:: m_pDatabase](#m_pdatabase)|Contiene un puntero al objeto `CDatabase` a través del que el conjunto de registros está conectado a un origen de datos.|
|[CRecordset:: m_strFilter](#m_strfilter)|Contiene un `CString` que especifica una cláusula de `WHERE` de Lenguaje de consulta estructurado (SQL). Se usa como filtro para seleccionar solo los registros que cumplen determinados criterios.|
|[CRecordset:: m_strSort](#m_strsort)|Contiene un `CString` que especifica una cláusula de SQL `ORDER BY`. Se utiliza para controlar cómo se ordenan los registros.|

## <a name="remarks"></a> Comentarios

Se conoce como "conjuntos de registros", `CRecordset` objetos se utilizan normalmente de dos formas: dynasets e instantáneas. Un Dynaset permanece sincronizado con las actualizaciones de datos realizadas por otros usuarios. Una instantánea es una vista estática de los datos. Cada formulario representa un conjunto de registros fijos en el momento en que se abre el conjunto de registros, pero cuando se desplaza a un registro en un conjunto de registros dinámico, refleja los cambios que se realizan posteriormente en el registro, ya sea por parte de otros usuarios u otros conjuntos de registros de la aplicación.

> [!NOTE]
>  Si está trabajando con las clases de objetos de acceso a datos (DAO) en lugar de las clases de conectividad abierta de bases de datos (ODBC), utilice la clase [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) en su lugar. Para obtener más información, vea el artículo [información general sobre la programación de bases de datos](../../data/data-access-programming-mfc-atl.md).

Para trabajar con cualquier tipo de conjunto de registros, normalmente se deriva una clase de conjunto de registros específica de la aplicación a partir de `CRecordset`. Los conjuntos de registros seleccionan registros de un origen de datos y, a continuación, puede:

- Desplácese por los registros.

- Actualice los registros y especifique un modo de bloqueo.

- Filtre el conjunto de registros para restringir los registros que selecciona de los disponibles en el origen de datos.

- Ordene el conjunto de registros.

- Parametrizar el conjunto de registros para personalizar su selección con información no conocida hasta el tiempo de ejecución.

Para usar la clase, abra una base de datos y construya un objeto de conjunto de registros, pasando el constructor a un puntero al objeto de `CDatabase`. A continuación, llame a la función miembro `Open` del conjunto de registros, donde puede especificar si el objeto es un Dynaset o una instantánea. Al llamar a `Open`, se seleccionan datos del origen de datos. Una vez abierto el objeto de conjunto de registros, use sus funciones miembro y miembros de datos para desplazarse por los registros y trabajar en ellos. Las operaciones disponibles dependen de si el objeto es un conjunto de registros dinámico o una instantánea, si es actualizable o de solo lectura (esto depende de la capacidad del origen de datos ODBC) y si se ha implementado la obtención masiva de filas. Para actualizar los registros que se han cambiado o agregado desde la llamada `Open`, llame a la función miembro `Requery` del objeto. Llame a la función miembro `Close` del objeto y destruya el objeto cuando termine con él.

En una clase de `CRecordset` derivada, el intercambio de campos de registros (RFX) o el intercambio masivo de campos de registro (RFX masivo) se utiliza para admitir la lectura y actualización de campos de registro.

Para obtener más información acerca de los conjuntos de registros y el intercambio de campos de registros, vea los artículos [información general: programación de bases de datos](../../data/data-access-programming-mfc-atl.md), [conjunto de registros (ODBC)](../../data/odbc/recordset-odbc.md), [conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)y intercambio de [campos de registros (RFX)](../../data/odbc/record-field-exchange-rfx.md). Para centrarse en los conjuntos de registros dinámicos e instantáneas, vea los artículos [Dynaset](../../data/odbc/dynaset.md) e [Snapshot](../../data/odbc/snapshot.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

`CRecordset`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdb. h

##  <a name="addnew"></a>CRecordset:: AddNew

Prepara para agregar un nuevo registro a la tabla.

```
virtual void AddNew();
```

### <a name="remarks"></a>Comentarios

Debe llamar a la función miembro [Requery](#requery) para ver el registro recién agregado. Los campos del registro son inicialmente null. (En la terminología de bases de datos, null significa "sin valor" y no es igual que NULL C++en). Para completar la operación, debe llamar a la función miembro [Update](#update) . `Update` guarda los cambios realizados en el origen de datos.

> [!NOTE]
>  Si ha implementado la obtención masiva de filas, no puede llamar a `AddNew`. Esto producirá un error de aserción. Aunque la clase `CRecordset` no proporciona un mecanismo para actualizar filas de datos masivas, puede escribir sus propias funciones mediante la función de la API de ODBC `SQLSetPos`. Para obtener más información sobre la obtención masiva de filas, vea el artículo [Conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

`AddNew` prepara un nuevo registro vacío usando los miembros de datos de campo del conjunto de registros. Después de llamar a `AddNew`, establezca los valores que desee en los miembros de datos de campo del conjunto de registros. (No tiene que llamar a la función miembro [Edit](#edit) para este propósito; use `Edit` solo para los registros existentes). Cuando se llama a `Update`posteriormente, los valores modificados en los miembros de datos de campo se guardan en el origen de datos.

> [!CAUTION]
>  Si se desplaza a un nuevo registro antes de llamar a `Update`, se pierde el nuevo registro y no se proporciona ninguna advertencia.

Si el origen de datos admite transacciones, puede hacer que el `AddNew` llame a parte de una transacción. Para obtener más información sobre las transacciones, vea la clase [CDatabase](../../mfc/reference/cdatabase-class.md). Tenga en cuenta que debe llamar a [CDatabase:: BeginTrans](../../mfc/reference/cdatabase-class.md#begintrans) antes de llamar a `AddNew`.

> [!NOTE]
>  En el caso de los conjuntos de registros dinámicos, los nuevos registros se agregan al conjunto de registros como el último registro. Los registros agregados no se agregan a las instantáneas; debe llamar a `Requery` para actualizar el conjunto de registros.

No es válido llamar a `AddNew` para un conjunto de registros cuya función miembro `Open` no se haya llamado. Se produce una `CDBException` si llama a `AddNew` para un conjunto de registros que no se puede anexar a. Puede determinar si el conjunto de registros es actualizable mediante una llamada a [CanAppend](#canappend).

Para obtener más información, vea los siguientes artículos: conjunto de registros [: Cómo actualizar los registros (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md), conjunto de registros [: agregar, actualizar y eliminar registros (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)y [transacción (ODBC)](../../data/odbc/transaction-odbc.md).

### <a name="example"></a>Ejemplo

Vea el artículo [transacción: realizar una transacción en un conjunto de registros (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md).

##  <a name="canappend"></a>CRecordset:: CanAppend

Determina si el conjunto de registros abierto previamente permite agregar nuevos registros.

```
BOOL CanAppend() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el conjunto de registros permite agregar nuevos registros; de lo contrario, es 0. `CanAppend` devolverá 0 si abrió el conjunto de registros como de solo lectura.

##  <a name="canbookmark"></a>CRecordset:: CanBookmark

Determina si el conjunto de registros permite marcar registros mediante marcadores.

```
BOOL CanBookmark() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el conjunto de registros admite marcadores; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Esta función es independiente de la opción `CRecordset::useBookmarks` en el parámetro *dwOptions* de la función miembro [abierta](#open) . `CanBookmark` indica si el tipo de cursor y el controlador ODBC especificados admiten marcadores. `CRecordset::useBookmarks` indica si los marcadores estarán disponibles, siempre y cuando se admitan.

> [!NOTE]
>  No se admiten marcadores en conjuntos de registros solo hacia delante.

Para obtener más información sobre los marcadores y la navegación por conjuntos de registros, vea los artículos [conjunto de registros: marcadores y posiciones absolutas (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md) y [conjunto de registros: desplazamiento (ODBC)](../../data/odbc/recordset-scrolling-odbc.md).

##  <a name="cancel"></a>CRecordset:: CANCEL

Solicita que el origen de datos cancele una operación asincrónica en curso o un proceso de un segundo subproceso.

```
void Cancel();
```

### <a name="remarks"></a>Comentarios

Tenga en cuenta que las clases ODBC de MFC ya no utilizan el procesamiento asincrónico; para realizar una operación asincrónica, debe llamar directamente a la función de la API de ODBC `SQLSetConnectOption`. Para obtener más información, vea el tema "ejecutar funciones de forma asincrónica" en la *Guía del programador del SDK de ODBC*.

##  <a name="cancelupdate"></a>CRecordset:: CancelUpdate

Cancela cualquier actualización pendiente, causada por una operación de [edición](#edit) o de [AddNew](#addnew) , antes de llamar a [Update](#update) .

```
void CancelUpdate();
```

### <a name="remarks"></a>Comentarios

> [!NOTE]
>  Esta función miembro no es aplicable en los conjuntos de registros que usan la obtención masiva de filas, ya que estos conjuntos de registros no pueden llamar a `Edit`, `AddNew`o `Update`. Para obtener más información sobre la obtención masiva de filas, vea el artículo [Conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Si está habilitada la comprobación automática de campos modificados, `CancelUpdate` restaurará las variables de miembro a los valores que tenían antes de que se llamara a `Edit` o `AddNew`; de lo contrario, se conservarán los cambios de valor. De forma predeterminada, la comprobación automática de campos está habilitada cuando se abre el conjunto de registros. Para deshabilitarlo, debe especificar el `CRecordset::noDirtyFieldCheck` en el parámetro *dwOptions* de la función miembro [abierta](#open) .

Para obtener más información sobre la actualización de datos, vea el artículo [conjunto de registros: agregar, actualizar y eliminar registros (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md).

##  <a name="canrestart"></a>CRecordset:: CanRestart

Determina si el conjunto de registros permite reiniciar su consulta (para actualizar sus registros) mediante una llamada a la función miembro `Requery`.

```
BOOL CanRestart() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se permite la reconsulta; de lo contrario, es 0.

##  <a name="canscroll"></a>CRecordset:: CanScroll

Determina si el conjunto de registros permite el desplazamiento.

```
BOOL CanScroll() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el conjunto de registros permite el desplazamiento; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Para obtener más información sobre el desplazamiento, vea el artículo [conjunto de registros: desplazamiento (ODBC)](../../data/odbc/recordset-scrolling-odbc.md).

##  <a name="cantransact"></a>CRecordset:: CanTransact

Determina si el conjunto de registros permite transacciones.

```
BOOL CanTransact() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el conjunto de registros permite transacciones; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Para obtener más información, vea el artículo [transacción (ODBC)](../../data/odbc/transaction-odbc.md).

##  <a name="canupdate"></a>CRecordset:: CanUpdate

Determina si el conjunto de registros se puede actualizar.

```
BOOL CanUpdate() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el conjunto de registros se puede actualizar; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Un conjunto de registros podría ser de solo lectura si el origen de datos subyacente es de solo lectura o si especificó `CRecordset::readOnly` en el parámetro *dwOptions* al abrir el conjunto de registros.

##  <a name="checkrowseterror"></a>CRecordset:: CheckRowsetError

Se llama para controlar los errores generados durante la captura de registros.

```
virtual void CheckRowsetError(RETCODE nRetCode);
```

### <a name="parameters"></a>Parámetros

*nRetCode*<br/>
Código de retorno de una función de la API de ODBC. Para conocer más detalles, vea la sección Comentarios.

### <a name="remarks"></a>Comentarios

Esta función miembro virtual administra los errores que se producen cuando se capturan registros y resulta útil durante la obtención masiva de filas. Puede que desee considerar la posibilidad de invalidar `CheckRowsetError` para implementar su propio control de errores.

se llama a `CheckRowsetError` automáticamente en una operación de navegación por el cursor, como `Open`, `Requery`o cualquier operación de `Move`. Se pasa el valor devuelto de la función de la API de ODBC `SQLExtendedFetch`. En la tabla siguiente se enumeran los posibles valores para el parámetro *nRetCode* .

|nRetCode|Descripción|
|--------------|-----------------|
|SQL_SUCCESS|La función se completó correctamente; no hay información adicional disponible.|
|SQL_SUCCESS_WITH_INFO|La función se completó correctamente, posiblemente con un error no irrecuperable. Se puede obtener información adicional llamando a `SQLError`.|
|SQL_NO_DATA_FOUND|Se han capturado todas las filas del conjunto de resultados.|
|SQL_ERROR|Error de la función. Se puede obtener información adicional llamando a `SQLError`.|
|SQL_INVALID_HANDLE|Error de la función debido a un identificador de entorno no válido, un identificador de conexión o un identificador de instrucción. Esto indica un error de programación. No hay información adicional disponible en `SQLError`.|
|SQL_STILL_EXECUTING|Una función que se inició de forma asincrónica todavía se está ejecutando. Tenga en cuenta que, de forma predeterminada, MFC nunca pasará este valor a `CheckRowsetError`; MFC seguirá llamando `SQLExtendedFetch` hasta que ya no devuelva SQL_STILL_EXECUTING.|

Para obtener más información acerca de `SQLError`, vea el Windows SDK. Para obtener más información sobre la obtención masiva de filas, vea el artículo [Conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

##  <a name="close"></a>CRecordset:: Close

Cierra el conjunto de registros.

```
virtual void Close();
```

### <a name="remarks"></a>Comentarios

El HSTMT de ODBC y toda la memoria que el marco de trabajo asignado para el conjunto de registros se desasigna. Normalmente después de llamar a `Close`, se C++ elimina el objeto de conjunto de registros si se asignó con el **nuevo**.

Puede llamar a `Open` de nuevo después de llamar a `Close`. Esto le permite volver a usar el objeto de conjunto de registros. La alternativa es llamar a `Requery`.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDatabase#17](../../mfc/codesnippet/cpp/crecordset-class_1.cpp)]

##  <a name="crecordset"></a>CRecordset:: CRecordset

Construye un objeto `CRecordset`.

```
CRecordset(CDatabase* pDatabase = NULL);
```

### <a name="parameters"></a>Parámetros

*pDatabase*<br/>
Contiene un puntero a un objeto `CDatabase` o el valor NULL. Si no es NULL y no se ha llamado a la función miembro `Open` del objeto `CDatabase` para conectarlo al origen de datos, el conjunto de registros intenta abrirlo automáticamente durante su propia llamada a `Open`. Si pasa NULL, se crea un objeto de `CDatabase` y se conecta automáticamente con la información del origen de datos que especificó al derivar la clase de conjunto de registros con ClassWizard.

### <a name="remarks"></a>Comentarios

Puede usar `CRecordset` directamente o derivar una clase específica de la aplicación de `CRecordset`. Puede usar ClassWizard para derivar las clases de conjunto de registros.

> [!NOTE]
>  Una clase derivada *debe* proporcionar su propio constructor. En el constructor de la clase derivada, llame al constructor `CRecordset::CRecordset`, pasando los parámetros adecuados a él.

Pase NULL al constructor de conjunto de registros para tener un objeto `CDatabase` construido y conectado automáticamente. Se trata de una forma abreviada útil que no requiere que construya y conecte un objeto `CDatabase` antes de construir el conjunto de registros.

### <a name="example"></a>Ejemplo

Para obtener más información, vea el artículo [conjunto de registros: declarar una clase para una tabla (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md).

##  <a name="delete"></a>CRecordset::D iminar

Elimina el registro actual.

```
virtual void Delete();
```

### <a name="remarks"></a>Comentarios

Después de una eliminación correcta, los miembros de datos de campo del conjunto de registros se establecen en un valor NULL y debe llamar explícitamente a una de las funciones `Move` para salir del registro eliminado. Una vez que salga del registro eliminado, no es posible volver a él. Si el origen de datos admite transacciones, puede hacer que el `Delete` llame a parte de una transacción. Para obtener más información, vea el artículo [transacción (ODBC)](../../data/odbc/transaction-odbc.md).

> [!NOTE]
>  Si ha implementado la obtención masiva de filas, no puede llamar a `Delete`. Esto producirá un error de aserción. Aunque la clase `CRecordset` no proporciona un mecanismo para actualizar filas de datos masivas, puede escribir sus propias funciones mediante la función de la API de ODBC `SQLSetPos`. Para obtener más información sobre la obtención masiva de filas, vea el artículo [Conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

> [!CAUTION]
>  El conjunto de registros debe ser actualizable y debe haber un registro válido en el conjunto de registros cuando se llama a `Delete`; de lo contrario, se produce un error. Por ejemplo, si elimina un registro pero no se desplaza a un nuevo registro antes de volver a llamar a `Delete`, `Delete` produce una [excepción CDBException](../../mfc/reference/cdbexception-class.md).

A diferencia de [AddNew](#addnew) y [Edit](#edit), una llamada a `Delete` no va seguida de una llamada a [Update](#update). Si se produce un error en una llamada `Delete`, los miembros de datos de campo se dejan sin cambios.

### <a name="example"></a>Ejemplo

En este ejemplo se muestra un conjunto de registros creado en el marco de una función. En el ejemplo se supone la existencia de `m_dbCust`, una variable miembro de tipo `CDatabase` ya está conectada al origen de datos.

[!code-cpp[NVC_MFCDatabase#18](../../mfc/codesnippet/cpp/crecordset-class_2.cpp)]

##  <a name="dobulkfieldexchange"></a>CRecordset::D oBulkFieldExchange

Se llama para intercambiar filas de datos masivas del origen de datos al conjunto de registros. Implementa el intercambio masivo de campos de registros (RFX masivo).

```
virtual void DoBulkFieldExchange(CFieldExchange* pFX);
```

### <a name="parameters"></a>Parámetros

*pFX*<br/>
Un puntero a un objeto [CFieldExchange](../../mfc/reference/cfieldexchange-class.md) . El marco ya habrá configurado este objeto para especificar un contexto para la operación de intercambio de campos.

### <a name="remarks"></a>Comentarios

Cuando se implementa la obtención masiva de filas, el marco de trabajo llama a esta función miembro para transferir datos de forma automática desde el origen de datos al objeto de conjunto de registros. también `DoBulkFieldExchange` enlaza los miembros de datos de parámetro, si los hay, a marcadores de posición de parámetros en la cadena de instrucción SQL para la selección del conjunto de registros.

Si no se implementa la obtención masiva de filas, el marco de trabajo llama a [DoFieldExchange](#dofieldexchange). Para implementar la obtención masiva de filas, debe especificar la opción `CRecordset::useMultiRowFetch` del parámetro *dwOptions* en la función miembro [abierta](#open) .

> [!NOTE]
> `DoBulkFieldExchange` solo está disponible si se usa una clase derivada de `CRecordset`. Si ha creado un objeto de conjunto de registros directamente desde `CRecordset`, debe llamar a la función miembro [GetFieldValue](#getfieldvalue) para recuperar los datos.

El intercambio masivo de campos de registros (RFX masivo) es similar al intercambio de campos de registros (RFX). Los datos se transfieren automáticamente desde el origen de datos al objeto de conjunto de registros. Sin embargo, no puede llamar a `AddNew`, `Edit`, `Delete`o `Update` para transferir los cambios de vuelta al origen de datos. La clase `CRecordset` actualmente no proporciona un mecanismo para actualizar filas de datos masivas; sin embargo, puede escribir sus propias funciones mediante la función de la API de ODBC `SQLSetPos`.

Tenga en cuenta que ClassWizard no admite el intercambio masivo de campos de registros; por lo tanto, debe invalidar `DoBulkFieldExchange` manualmente escribiendo llamadas a las funciones de RFX masivo. Para obtener más información sobre estas funciones, vea el tema [funciones de intercambio de campos de registro](../../mfc/reference/record-field-exchange-functions.md).

Para obtener más información sobre la obtención masiva de filas, vea el artículo [Conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md). Para obtener información relacionada, vea el artículo [intercambio de campos de registros (RFX)](../../data/odbc/record-field-exchange-rfx.md).

##  <a name="dofieldexchange"></a>CRecordset::D oFieldExchange

Se llama para intercambiar datos (en ambas direcciones) entre los miembros de datos de campo del conjunto de registros y el registro correspondiente en el origen de datos. Implementa el intercambio de campos de registros (RFX).

```
virtual void DoFieldExchange(CFieldExchange* pFX);
```

### <a name="parameters"></a>Parámetros

*pFX*<br/>
Un puntero a un objeto [CFieldExchange](../../mfc/reference/cfieldexchange-class.md) . El marco ya habrá configurado este objeto para especificar un contexto para la operación de intercambio de campos.

### <a name="remarks"></a>Comentarios

Cuando no se implementa la obtención masiva de filas, el marco de trabajo llama a esta función miembro para intercambiar datos de forma automática entre los miembros de datos de campo del objeto de conjunto de registros y las columnas correspondientes del registro actual en el origen de datos. también `DoFieldExchange` enlaza los miembros de datos de parámetro, si los hay, a marcadores de posición de parámetros en la cadena de instrucción SQL para la selección del conjunto de registros.

Si se implementa la obtención masiva de filas, el marco de trabajo llama a [DoBulkFieldExchange](#dobulkfieldexchange). Para implementar la obtención masiva de filas, debe especificar la opción `CRecordset::useMultiRowFetch` del parámetro *dwOptions* en la función miembro [abierta](#open) .

> [!NOTE]
> `DoFieldExchange` solo está disponible si se usa una clase derivada de `CRecordset`. Si ha creado un objeto de conjunto de registros directamente desde `CRecordset`, debe llamar a la función miembro [GetFieldValue](#getfieldvalue) para recuperar los datos.

El intercambio de datos de campo, denominado intercambio de campos de registros (RFX), funciona en ambas direcciones: desde los miembros de datos de campo del objeto de conjunto de registros hasta los campos del registro en el origen de datos y desde el registro del origen de datos hasta el objeto de conjunto de registros.

La única acción que se debe realizar normalmente para implementar `DoFieldExchange` para la clase de conjunto de registros derivada es crear la clase con ClassWizard y especificar los nombres y los tipos de datos de los miembros de datos de campo. También puede agregar código a las escrituras de ClassWizard para especificar los miembros de datos de parámetro o para tratar con las columnas que se enlazan dinámicamente. Para obtener más información, vea el artículo [conjunto de registros: enlazar dinámicamente columnas de datos (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).

Al declarar la clase de conjunto de registros derivada con ClassWizard, el asistente escribe una invalidación de `DoFieldExchange` automáticamente, que es similar al ejemplo siguiente:

[!code-cpp[NVC_MFCDatabase#19](../../mfc/codesnippet/cpp/crecordset-class_3.cpp)]

Para obtener más información sobre las funciones de RFX, vea el tema [funciones de intercambio de campos de registro](../../mfc/reference/record-field-exchange-functions.md).

Para obtener más ejemplos y detalles sobre `DoFieldExchange`, vea el artículo [intercambio de campos de registros:](../../data/odbc/record-field-exchange-how-rfx-works.md)funcionamiento de RFX. Para obtener información general sobre RFX, consulte el artículo [intercambio de campos de registros](../../data/odbc/record-field-exchange-rfx.md).

##  <a name="edit"></a>CRecordset:: Edit

Permite realizar cambios en el registro actual.

```
virtual void Edit();
```

### <a name="remarks"></a>Comentarios

Después de llamar a `Edit`, puede cambiar los miembros de datos de campo restableciendo los valores directamente. La operación se completa cuando se llama posteriormente a la función miembro [Update](#update) para guardar los cambios en el origen de datos.

> [!NOTE]
>  Si ha implementado la obtención masiva de filas, no puede llamar a `Edit`. Esto producirá un error de aserción. Aunque la clase `CRecordset` no proporciona un mecanismo para actualizar filas de datos masivas, puede escribir sus propias funciones mediante la función de la API de ODBC `SQLSetPos`. Para obtener más información sobre la obtención masiva de filas, vea el artículo [Conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

`Edit` guarda los valores de los miembros de datos del conjunto de registros. Si llama a `Edit`, realiza cambios y llama de nuevo a `Edit`, los valores del registro se restauran a lo que estaban antes de la primera llamada a `Edit`.

En algunos casos, puede que desee actualizar una columna convirtiéndola en null (que no contiene ningún dato). Para ello, llame a [SetFieldNull](#setfieldnull) con un parámetro de true para marcar el campo como null. Esto también hace que se actualice la columna. Si desea que un campo se escriba en el origen de datos aunque su valor no haya cambiado, llame a [SetFieldDirty](#setfielddirty) con un parámetro de true. Esto funciona incluso si el campo tenía el valor null.

Si el origen de datos admite transacciones, puede hacer que el `Edit` llame a parte de una transacción. Tenga en cuenta que debe llamar a [CDatabase:: BeginTrans](../../mfc/reference/cdatabase-class.md#begintrans) antes de llamar a `Edit` y después de abrir el conjunto de registros. Tenga en cuenta también que llamar a [CDatabase:: CommitTrans](../../mfc/reference/cdatabase-class.md#committrans) no es un sustituto de la llamada a `Update` para completar la operación de `Edit`. Para obtener más información sobre las transacciones, vea la clase [CDatabase](../../mfc/reference/cdatabase-class.md).

En función del modo de bloqueo actual, el registro que se está actualizando puede bloquearse mediante `Edit` hasta que se llame a `Update` o se desplace a otro registro, o se puede bloquear solo durante la llamada a `Edit`. Puede cambiar el modo de bloqueo con [SetLockingMode](#setlockingmode).

El valor anterior del registro actual se restaura si se desplaza a un nuevo registro antes de llamar a `Update`. Se produce una `CDBException` si se llama a `Edit` para un conjunto de registros que no se puede actualizar o si no hay ningún registro actual.

Para obtener más información, vea los artículos [transacción (ODBC)](../../data/odbc/transaction-odbc.md) y conjunto de registros [: bloquear registros (ODBC)](../../data/odbc/recordset-locking-records-odbc.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDatabase#20](../../mfc/codesnippet/cpp/crecordset-class_4.cpp)]

##  <a name="flushresultset"></a>CRecordset:: FlushResultSet

Recupera el siguiente conjunto de resultados de una consulta predefinida (procedimiento almacenado), si hay varios conjuntos de resultados.

```
BOOL FlushResultSet();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si hay más conjuntos de resultados que se van a recuperar; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Solo debe llamar a `FlushResultSet` cuando haya terminado por completo con el cursor en el conjunto de resultados actual. Tenga en cuenta que al recuperar el siguiente conjunto de resultados mediante una llamada a `FlushResultSet`, el cursor no es válido en ese conjunto de resultados; debe llamar a la función miembro [MoveNext](#movenext) después de llamar a `FlushResultSet`.

Si una consulta predefinida utiliza un parámetro de salida o parámetros de entrada/salida, debe llamar a `FlushResultSet` hasta que devuelva `FALSE` (el valor 0) para obtener estos valores de parámetro.

`FlushResultSet` llama a la función de la API de ODBC `SQLMoreResults`. Si `SQLMoreResults` devuelve SQL_ERROR o SQL_INVALID_HANDLE, `FlushResultSet` producirá una excepción. Para obtener más información acerca de `SQLMoreResults`, vea el Windows SDK.

El procedimiento almacenado debe tener campos enlazados si desea llamar a `FlushResultSet`.

### <a name="example"></a>Ejemplo

En el código siguiente se supone que `COutParamRecordset` es un objeto derivado de `CRecordset`basado en una consulta predefinida con un parámetro de entrada y un parámetro de salida, y con varios conjuntos de resultados. Tenga en cuenta la estructura de la invalidación de [DoFieldExchange](#dofieldexchange) .

[!code-cpp[NVC_MFCDatabase#21](../../mfc/codesnippet/cpp/crecordset-class_5.cpp)]

[!code-cpp[NVC_MFCDatabase#22](../../mfc/codesnippet/cpp/crecordset-class_6.cpp)]

##  <a name="getbookmark"></a>CRecordset:: GetBookmark

Obtiene el valor de marcador del registro actual.

```
void GetBookmark(CDBVariant& varBookmark);
```

### <a name="parameters"></a>Parámetros

*varBookmark*<br/>
Referencia a un objeto [cdbvariant (](../../mfc/reference/cdbvariant-class.md) que representa el marcador en el registro actual.

### <a name="remarks"></a>Comentarios

Para determinar si se admiten marcadores en el conjunto de registros, llame a [CanBookmark](#canbookmark). Para que los marcadores estén disponibles si se admiten, debe establecer la opción `CRecordset::useBookmarks` en el parámetro *dwOptions* de la función miembro [abierta](#open) .

> [!NOTE]
>  Si los marcadores no se admiten o no están disponibles, al llamar a `GetBookmark` se producirá una excepción. No se admiten marcadores en conjuntos de registros solo hacia delante.

`GetBookmark` asigna el valor del marcador del registro actual a un objeto `CDBVariant`. Para volver a ese registro en cualquier momento después de desplazarse a otro registro, llame a [SetBookmark](#setbookmark) con el objeto de `CDBVariant` correspondiente.

> [!NOTE]
>  Después de ciertas operaciones de conjunto de registros, es posible que los marcadores dejen de ser válidos. Por ejemplo, si llama a `GetBookmark` seguido de `Requery`, es posible que no pueda volver al registro con `SetBookmark`. Llame a [CDatabase:: GetBookmarkPersistence](../../mfc/reference/cdatabase-class.md#getbookmarkpersistence) para comprobar si puede llamar a `SetBookmark`de forma segura.

Para obtener más información sobre los marcadores y la navegación por conjuntos de registros, vea los artículos [conjunto de registros: marcadores y posiciones absolutas (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md) y [conjunto de registros: desplazamiento (ODBC)](../../data/odbc/recordset-scrolling-odbc.md).

##  <a name="getdefaultconnect"></a>CRecordset:: GetDefaultConnect

Se llama para obtener la cadena de conexión predeterminada.

```
virtual CString GetDefaultConnect();
```

### <a name="return-value"></a>Valor devuelto

`CString` que contiene la cadena de conexión predeterminada.

### <a name="remarks"></a>Comentarios

El marco de trabajo llama a esta función miembro para obtener la cadena de conexión predeterminada para el origen de datos en el que se basa el conjunto de registros. ClassWizard implementa esta función mediante la identificación del mismo origen de datos que se usa en ClassWizard para obtener información acerca de las tablas y columnas. Lo más probable es que le resulte conveniente confiar en esta conexión predeterminada mientras desarrolla su aplicación. Pero es posible que la conexión predeterminada no sea adecuada para los usuarios de la aplicación. En ese caso, debe volver a implementar esta función y descartar la versión de ClassWizard. Para obtener más información sobre las cadenas de conexión, vea el artículo [origen de datos (ODBC)](../../data/odbc/data-source-odbc.md).

##  <a name="getdefaultsql"></a>CRecordset:: GetDefaultSQL

Se llama para obtener la cadena SQL predeterminada que se va a ejecutar.

```
virtual CString GetDefaultSQL();
```

### <a name="return-value"></a>Valor devuelto

`CString` que contiene la instrucción SQL predeterminada.

### <a name="remarks"></a>Comentarios

El marco de trabajo llama a esta función miembro para obtener la instrucción SQL predeterminada en la que se basa el conjunto de registros. Puede tratarse de un nombre de tabla o una instrucción **Select** de SQL.

La instrucción SQL predeterminada se define indirectamente declarando la clase de conjunto de registros con ClassWizard y ClassWizard realiza esta tarea por usted.

Si necesita la cadena de instrucción SQL para su propio uso, llame a `GetSQL`, que devuelve la instrucción SQL que se usa para seleccionar los registros del conjunto de registros cuando se abrió. Puede editar la cadena de SQL predeterminada en la invalidación de la clase de `GetDefaultSQL`. Por ejemplo, puede especificar una llamada a una consulta predefinida mediante una instrucción **Call** . (Sin embargo, tenga en cuenta que si edita `GetDefaultSQL`, también debe modificar `m_nFields` para que coincida con el número de columnas del origen de datos).

Para obtener más información, vea el artículo [conjunto de registros: declarar una clase para una tabla (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md).

> [!CAUTION]
>  El nombre de la tabla estará vacío si el marco no pudo identificar un nombre de tabla, si se proporcionaron varios nombres de tabla o si no se pudo interpretar una instrucción de **llamada** . Tenga en cuenta que cuando se usa una instrucción **Call** , no se debe insertar un espacio en blanco entre la llave y la palabra clave **Call** , ni se debe insertar un espacio en blanco antes de la llave o antes de la palabra clave **Select** en una instrucción **Select** .

##  <a name="getfieldvalue"></a>CRecordset:: GetFieldValue

Recupera los datos de campo del registro actual.

```
void GetFieldValue(
    LPCTSTR lpszName,
    CDBVariant& varValue,
    short nFieldType = DEFAULT_FIELD_TYPE);

void GetFieldValue(
    short nIndex,
    CDBVariant& varValue,
    short nFieldType = DEFAULT_FIELD_TYPE);

void GetFieldValue(
    short nIndex,
    CStringA& strValue);

void GetFieldValue(
    short nIndex,
    CStringW& strValue);
```

### <a name="parameters"></a>Parámetros

*lpszName*<br/>
Nombre de un campo.

*varValu*e referencia a un objeto [cdbvariant (](../../mfc/reference/cdbvariant-class.md) que almacenará el valor del campo.

*nFieldType*<br/>
El tipo de datos C de ODBC del campo. Con el valor predeterminado, DEFAULT_FIELD_TYPE, fuerza `GetFieldValue` para determinar el tipo de datos de C a partir del tipo de datos de SQL, basado en la tabla siguiente. De lo contrario, puede especificar el tipo de datos directamente o elegir un tipo de datos compatible. por ejemplo, puede almacenar cualquier tipo de datos en SQL_C_CHAR.

|C, tipo de datos|Tipo de datos SQL|
|-----------------|-------------------|
|SQL_C_BIT|SQL_BIT|
|SQL_C_UTINYINT|SQL_TINYINT|
|SQL_C_SSHORT|SQL_SMALLINT|
|SQL_C_SLONG|SQL_INTEGER|
|SQL_C_FLOAT|SQL_REAL|
|SQL_C_DOUBLE|SQL_FLOATSQL_DOUBLE|
|SQL_C_TIMESTAMP|SQL_DATESQL_TIMESQL_TIMESTAMP|
|SQL_C_CHAR|SQL_NUMERICSQL_DECIMALSQL_BIGINTSQL_CHARSQL_VARCHARSQL_LONGVARCHAR|
|SQL_C_BINARY|SQL_BINARYSQL_VARBINARYSQL_LONGVARBINARY|

Para obtener más información sobre los tipos de datos de ODBC, vea los temas "tipos de datos de SQL" y "tipos de datos de C" en el Apéndice D del Windows SDK.

*nIndex*<br/>
Índice de base cero del campo.

*strValue*<br/>
Referencia a un objeto [CString](../../atl-mfc-shared/reference/cstringt-class.md) que almacenará el valor del campo convertido en texto, independientemente del tipo de datos del campo.

### <a name="remarks"></a>Comentarios

Puede buscar un campo por nombre o por índice. Puede almacenar el valor del campo en un objeto `CDBVariant` o un objeto `CString`.

Si ha implementado la obtención masiva de filas, el registro actual siempre se coloca en el primer registro de un conjunto de filas. Para usar `GetFieldValue` en un registro dentro de un conjunto de filas determinado, primero debe llamar a la función miembro [SetRowsetCursorPosition](#setrowsetcursorposition) para que mueva el cursor a la fila deseada dentro de dicho conjunto de filas. A continuación, llame a `GetFieldValue` para esa fila. Para implementar la obtención masiva de filas, debe especificar la opción `CRecordset::useMultiRowFetch` del parámetro *dwOptions* en la función miembro [abierta](#open) .

Puede usar `GetFieldValue` para capturar dinámicamente los campos en tiempo de ejecución en lugar de enlazarlos estáticamente en tiempo de diseño. Por ejemplo, si ha declarado un objeto de conjunto de registros directamente desde `CRecordset`, debe utilizar `GetFieldValue` para recuperar los datos de campo. no se implementa el intercambio de campos de registros (RFX) o el intercambio masivo de campos de registros (RFX masivo).

> [!NOTE]
>  Si declara un objeto de conjunto de registros sin derivar de `CRecordset`, no se carga la biblioteca de cursores ODBC. La biblioteca de cursores requiere que el conjunto de registros tenga al menos una columna enlazada; sin embargo, cuando se usa `CRecordset` directamente, no se enlaza ninguna de las columnas. Las funciones miembro [CDatabase:: OpenEx](../../mfc/reference/cdatabase-class.md#openex) y [CDatabase:: Open](../../mfc/reference/cdatabase-class.md#open) controlan si se va a cargar la biblioteca de cursores.

`GetFieldValue` llama a la función de la API de ODBC `SQLGetData`. Si el controlador genera el valor SQL_NO_TOTAL para la longitud real del valor del campo, `GetFieldValue` produce una excepción. Para obtener más información acerca de `SQLGetData`, vea el Windows SDK.

### <a name="example"></a>Ejemplo

En el código de ejemplo siguiente se muestran las llamadas a `GetFieldValue` para un objeto de conjunto de registros declarado directamente desde `CRecordset`.

[!code-cpp[NVC_MFCDatabase#23](../../mfc/codesnippet/cpp/crecordset-class_7.cpp)]

> [!NOTE]
>  A diferencia de la clase DAO `CDaoRecordset`, `CRecordset` no tiene una función miembro `SetFieldValue`. Si crea un objeto directamente desde `CRecordset`, es realmente de solo lectura.

Para obtener más información sobre la obtención masiva de filas, vea el artículo [Conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

##  <a name="getodbcfieldcount"></a>CRecordset:: GetODBCFieldCount

Recupera el número total de campos del objeto de conjunto de registros.

```
short GetODBCFieldCount() const;
```

### <a name="return-value"></a>Valor devuelto

Número de campos del conjunto de registros.

### <a name="remarks"></a>Comentarios

Para obtener más información sobre cómo crear conjuntos de registros, vea el artículo conjunto de registros [: crear y cerrar conjuntos de registros (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md).

##  <a name="getodbcfieldinfo"></a>CRecordset:: GetODBCFieldInfo

Obtiene información sobre los campos del conjunto de registros.

```
void GetODBCFieldInfo(
    LPCTSTR lpszName,
    CODBCFieldInfo& fieldinfo);

void GetODBCFieldInfo(
    short nIndex,
    CODBCFieldInfo& fieldinfo);
```

### <a name="parameters"></a>Parámetros

*lpszName*<br/>
Nombre de un campo.

*FieldInfo*<br/>
Referencia a una estructura de `CODBCFieldInfo`.

*nIndex*<br/>
Índice de base cero del campo.

### <a name="remarks"></a>Comentarios

Una versión de la función permite buscar un campo por su nombre. La otra versión permite buscar un campo por índice.

Para obtener una descripción de la información devuelta, consulte la estructura [codbcfieldinfo (](../../mfc/reference/codbcfieldinfo-structure.md) .

Para obtener más información sobre cómo crear conjuntos de registros, vea el artículo conjunto de registros [: crear y cerrar conjuntos de registros (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md).

##  <a name="getrecordcount"></a>CRecordset:: GetRecordCount

Determina el tamaño del conjunto de registros.

```
long GetRecordCount() const;
```

### <a name="return-value"></a>Valor devuelto

Número de registros del conjunto de registros; 0 si el conjunto de registros no contiene registros; o-1 si no se puede determinar el número de registros.

### <a name="remarks"></a>Comentarios

> [!CAUTION]
>  El número de registros se mantiene como "límite superior", el registro con el número más alto que se ha detectado a medida que el usuario se desplaza por los registros. Solo se conoce el número total de registros después de que el usuario haya cambiado más allá del último registro. Por motivos de rendimiento, el recuento no se actualiza cuando se llama a `MoveLast`. Para contar los registros usted mismo, llame a `MoveNext` repetidamente hasta que `IsEOF` devuelva un valor distinto de cero. La adición de un registro a través de `CRecordset:AddNew` y `Update` aumenta el número; la eliminación de un registro a través de `CRecordset::Delete` disminuye el recuento.

##  <a name="getrowsetsize"></a>CRecordset:: GetRowsetSize

Obtiene el valor actual para el número de filas que desea recuperar durante una captura determinada.

```
DWORD GetRowsetSize() const;
```

### <a name="return-value"></a>Valor devuelto

Número de filas que se van a recuperar durante una captura determinada.

### <a name="remarks"></a>Comentarios

Si está utilizando la obtención masiva de filas, el tamaño predeterminado del conjunto de filas cuando se abre el conjunto de registros es 25; de lo contrario, es 1.

Para implementar la obtención masiva de filas, debe especificar la opción `CRecordset::useMultiRowFetch` en el parámetro *dwOptions* de la función miembro [abierta](#open) . Para cambiar el valor para el tamaño del conjunto de filas, llame a [SetRowsetSize](#setrowsetsize).

Para obtener más información sobre la obtención masiva de filas, vea el artículo [Conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

##  <a name="getrowsfetched"></a>CRecordset:: GetRowsFetched

Determina cuántos registros se recuperaron realmente después de una captura.

```
DWORD GetRowsFetched() const;
```

### <a name="return-value"></a>Valor devuelto

El número de filas recuperadas del origen de datos después de una captura determinada.

### <a name="remarks"></a>Comentarios

Esto resulta útil cuando se ha implementado la obtención masiva de filas. El tamaño del conjunto de filas indica normalmente el número de filas que se recuperarán de una captura; sin embargo, el número total de filas del conjunto de registros también afecta a la cantidad de filas que se recuperarán en un conjunto de filas. Por ejemplo, si el conjunto de registros tiene 10 registros con un valor de tamaño de conjunto de filas de 4, al recorrer en iteración el conjunto de registros llamando a `MoveNext` se producirá que el conjunto de filas final tenga solo 2 registros.

Para implementar la obtención masiva de filas, debe especificar la opción `CRecordset::useMultiRowFetch` en el parámetro *dwOptions* de la función miembro [abierta](#open) . Para especificar el tamaño del conjunto de filas, llame a [SetRowsetSize](#setrowsetsize).

Para obtener más información sobre la obtención masiva de filas, vea el artículo [Conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDatabase#24](../../mfc/codesnippet/cpp/crecordset-class_8.cpp)]

##  <a name="getrowstatus"></a>CRecordset:: GetRowStatus

Obtiene el estado de una fila en el conjunto de filas actual.

```
WORD GetRowStatus(WORD wRow) const;
```

### <a name="parameters"></a>Parámetros

*wRow*<br/>
La posición basada en uno de una fila en el conjunto de filas actual. Este valor puede oscilar entre 1 y el tamaño del conjunto de filas.

### <a name="return-value"></a>Valor devuelto

Valor de estado de la fila. Para conocer más detalles, vea la sección Comentarios.

### <a name="remarks"></a>Comentarios

`GetRowStatus` devuelve un valor que indica cualquier cambio en el estado de la fila desde la última vez que se recuperó del origen de datos o que no se ha capturado ninguna fila correspondiente a *wRow* . La tabla siguiente muestra los valores devueltos posibles.

|Valor de estado|Descripción|
|------------------|-----------------|
|SQL_ROW_SUCCESS|La fila no ha cambiado.|
|SQL_ROW_UPDATED|La fila se ha actualizado.|
|SQL_ROW_DELETED|La fila se ha eliminado.|
|SQL_ROW_ADDED|Se ha agregado la fila.|
|SQL_ROW_ERROR|La fila no se podrá recuperar debido a un error.|
|SQL_ROW_NOROW|No hay ninguna fila que corresponda a *wRow*.|

Para obtener más información, vea la función de la API de ODBC `SQLExtendedFetch` en el Windows SDK.

##  <a name="getstatus"></a>CRecordset:: GetStatus

Determina el índice del registro actual del conjunto de registros y si se ha encontrado el último registro.

```
void GetStatus(CRecordsetStatus& rStatus) const;
```

### <a name="parameters"></a>Parámetros

*rStatus*<br/>
Referencia a un objeto `CRecordsetStatus`. Vea la sección Comentarios para obtener más información.

### <a name="remarks"></a>Comentarios

`CRecordset` intenta realizar el seguimiento del índice pero, en algunas circunstancias, es posible que esto no sea posible. Consulte [GetRecordCount](#getrecordcount) para obtener una explicación.

La estructura `CRecordsetStatus` tiene el formato siguiente:

```cpp
struct CRecordsetStatus
{
    long m_lCurrentRecord;
    BOOL m_bRecordCountFinal;
};
```

Los dos miembros de `CRecordsetStatus` tienen los significados siguientes:

- `m_lCurrentRecord` contiene el índice de base cero del registro actual del conjunto de registros, si se conoce. Si no se puede determinar el índice, este miembro contiene AFX_CURRENT_RECORD_UNDEFINED (-2). Si `IsBOF` es TRUE (conjunto de registros vacío o se intenta desplazar antes del primer registro), `m_lCurrentRecord` se establece en AFX_CURRENT_RECORD_BOF (-1). Si se encuentra en el primer registro, se establece en 0, segundo registro 1, etc.

- `m_bRecordCountFinal` distinto de cero si se ha determinado el número total de registros del conjunto de registros. Por lo general, esto debe hacerse empezando por el principio del conjunto de registros y llamando a `MoveNext` hasta que `IsEOF` devuelva un valor distinto de cero. Si este miembro es cero, el número de registros devueltos por `GetRecordCount`, si no es-1, es solo un recuento de "marca de límite superior" de los registros.

##  <a name="getsql"></a>CRecordset:: GetSQL

Llame a esta función miembro para obtener la instrucción SQL que se usó para seleccionar los registros del conjunto de registros cuando se abrió.

```
const CString& GetSQL() const;
```

### <a name="return-value"></a>Valor devuelto

Referencia **const** a una `CString` que contiene la instrucción SQL.

### <a name="remarks"></a>Comentarios

Normalmente, será una instrucción **Select** de SQL. La cadena devuelta por `GetSQL` es de solo lectura.

La cadena devuelta por `GetSQL` es normalmente diferente de cualquier cadena que se haya pasado al conjunto de registros del parámetro *lpszSQL* a la función miembro `Open`. Esto se debe a que el conjunto de registros crea una instrucción SQL completa basada en lo que ha pasado a `Open`, lo que especificó con ClassWizard, lo que puede haber especificado en el `m_strFilter` y los miembros de datos `m_strSort` y cualquier parámetro que haya especificado. Para obtener más información sobre cómo el conjunto de registros crea esta instrucción SQL, vea el artículo conjunto de registros [: cómo se seleccionan los registros (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md).

> [!NOTE]
>  Llame a esta función miembro solo después de llamar a [Open](#open).

##  <a name="gettablename"></a>CRecordset:: GetTableName

Obtiene el nombre de la tabla SQL en la que se basa la consulta del conjunto de registros.

```
const CString& GetTableName() const;
```

### <a name="return-value"></a>Valor devuelto

Una referencia **const** a un `CString` que contiene el nombre de la tabla, si el conjunto de registros se basa en una tabla; de lo contrario, una cadena vacía.

### <a name="remarks"></a>Comentarios

`GetTableName` solo es válido si el conjunto de registros se basa en una tabla, no en una combinación de varias tablas o en una consulta predefinida (procedimiento almacenado). El nombre es de solo lectura.

> [!NOTE]
>  Llame a esta función miembro solo después de llamar a [Open](#open).

##  <a name="isbof"></a>CRecordset:: IsBOF

Devuelve un valor distinto de cero si el conjunto de registros se ha colocado antes del primer registro. No hay ningún registro actual.

```
BOOL IsBOF() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el conjunto de registros no contiene ningún registro o si se ha desplazado hacia atrás antes del primer registro; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Llame a esta función miembro antes de desplazarse de registro a registro para saber si ha pasado antes del primer registro del conjunto de registros. También puede utilizar `IsBOF` junto con `IsEOF` para determinar si el conjunto de registros contiene registros o si está vacío. Inmediatamente después de llamar a `Open`, si el conjunto de registros no contiene registros, `IsBOF` devuelve un valor distinto de cero. Al abrir un conjunto de registros que tiene al menos un registro, el primer registro es el registro actual y `IsBOF` devuelve 0.

Si el primer registro es el registro actual y llama a `MovePrev`, `IsBOF` devolverá después un valor distinto de cero. Si `IsBOF` devuelve un valor distinto de cero y llama a `MovePrev`, se produce un error. Si `IsBOF` devuelve un valor distinto de cero, el registro actual no está definido y cualquier acción que requiera un registro actual producirá un error.

### <a name="example"></a>Ejemplo

En este ejemplo se usa `IsBOF` y `IsEOF` para detectar los límites de un conjunto de registros a medida que el código se desplaza por el conjunto de registros en ambas direcciones.

[!code-cpp[NVC_MFCDatabase#25](../../mfc/codesnippet/cpp/crecordset-class_9.cpp)]

##  <a name="isdeleted"></a>CRecordset:: IsDeleted

Determina si se ha eliminado el registro actual.

```
BOOL IsDeleted() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el conjunto de registros está colocado en un registro eliminado; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Si se desplaza a un registro y `IsDeleted` devuelve TRUE (distinto de cero), debe desplazarse a otro registro antes de poder realizar cualquier otra operación de conjunto de registros.

El resultado de `IsDeleted` depende de muchos factores, como el tipo de conjunto de registros, si el conjunto de registros es actualizable, si especificó la opción `CRecordset::skipDeletedRecords` al abrir el conjunto de registros, si los paquetes de controladores eliminaron registros y si hay varios pueden.

Para obtener más información sobre `CRecordset::skipDeletedRecords` y el empaquetado de controladores, vea la función miembro [Open](#open) .

> [!NOTE]
>  Si ha implementado la obtención masiva de filas, no debe llamar a `IsDeleted`. En su lugar, llame a la función miembro [GetRowStatus](#getrowstatus) . Para obtener más información sobre la obtención masiva de filas, vea el artículo [Conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

##  <a name="iseof"></a>CRecordset:: IsEOF

Devuelve un valor distinto de cero si el conjunto de registros se ha colocado después del último registro. No hay ningún registro actual.

```
BOOL IsEOF() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el conjunto de registros no contiene registros o si se ha desplazado más allá del último registro; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Llame a esta función miembro mientras se desplaza de registro a registro para saber si ha ido más allá del último registro del conjunto de registros. También puede utilizar `IsEOF` para determinar si el conjunto de registros contiene registros o si está vacío. Inmediatamente después de llamar a `Open`, si el conjunto de registros no contiene registros, `IsEOF` devuelve un valor distinto de cero. Al abrir un conjunto de registros que tiene al menos un registro, el primer registro es el registro actual y `IsEOF` devuelve 0.

Si el último registro es el registro actual cuando se llama a `MoveNext`, `IsEOF` devolverá después un valor distinto de cero. Si `IsEOF` devuelve un valor distinto de cero y llama a `MoveNext`, se produce un error. Si `IsEOF` devuelve un valor distinto de cero, el registro actual no está definido y cualquier acción que requiera un registro actual producirá un error.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [IsBOF](#isbof).

##  <a name="isfielddirty"></a>CRecordset:: IsFieldDirty

Determina si el miembro de datos de campo especificado se ha cambiado desde que se llamó a [Edit](#edit) o [AddNew](#addnew) .

```
BOOL IsFieldDirty(void* pv);
```

### <a name="parameters"></a>Parámetros

*FV*<br/>
Puntero al miembro de datos de campo cuyo estado se desea comprobar, o NULL para determinar si alguno de los campos está sucio.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el miembro de datos de campo especificado ha cambiado desde que se llama a `AddNew` o `Edit`; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Los datos de todos los miembros de datos de campo modificados se transferirán al registro en el origen de datos cuando el registro actual se actualice mediante una llamada a la función miembro [Update](#update) de `CRecordset` (siguiendo una llamada a `Edit` o `AddNew`).

> [!NOTE]
>  Esta función miembro no es aplicable en los conjuntos de registros que usan la obtención masiva de filas. Si ha implementado la obtención masiva de filas, `IsFieldDirty` siempre devolverá FALSE y dará como resultado una aserción con errores. Para obtener más información sobre la obtención masiva de filas, vea el artículo [Conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Al llamar a `IsFieldDirty`, se restablecerán los efectos de las llamadas anteriores a [SetFieldDirty](#setfielddirty) , ya que se vuelve a evaluar el estado de modificación del campo. En el caso de `AddNew`, si el valor del campo actual difiere del valor de pseudo null, el estado del campo se establece como modificado. En el caso de `Edit`, si el valor del campo difiere del valor almacenado en caché, el estado del campo se establece como modificado.

`IsFieldDirty` se implementa a través de [DoFieldExchange](#dofieldexchange).

Para obtener más información sobre el marcador Dirty, vea el artículo conjunto de registros [: cómo se seleccionan los registros (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md).

##  <a name="isfieldnull"></a>CRecordset:: IsFieldNull

Devuelve un valor distinto de cero si el campo especificado en el registro actual es null (no tiene ningún valor).

```
BOOL IsFieldNull(void* pv);
```

### <a name="parameters"></a>Parámetros

*FV*<br/>
Puntero al miembro de datos de campo cuyo estado se desea comprobar, o NULL para determinar si alguno de los campos es NULL.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el miembro de datos de campo especificado se marca como null; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Llame a esta función miembro para determinar si el miembro de datos de campo especificado de un conjunto de registros se ha marcado como null. (En la terminología de bases de datos, null significa "sin valor" y no es igual que NULL C++en). Si un miembro de datos de campo se marca como null, se interpreta como una columna del registro actual para el que no hay ningún valor.

> [!NOTE]
>  Esta función miembro no es aplicable en los conjuntos de registros que usan la obtención masiva de filas. Si ha implementado la obtención masiva de filas, `IsFieldNull` siempre devolverá FALSE y dará como resultado una aserción con errores. Para obtener más información sobre la obtención masiva de filas, vea el artículo [Conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

`IsFieldNull` se implementa a través de [DoFieldExchange](#dofieldexchange).

##  <a name="isfieldnullable"></a>CRecordset:: IsFieldNullable

Devuelve un valor distinto de cero si el campo especificado del registro actual se puede establecer en null (no tiene ningún valor).

```
BOOL IsFieldNullable(void* pv);
```

### <a name="parameters"></a>Parámetros

*FV*<br/>
Puntero al miembro de datos de campo cuyo estado se desea comprobar, o NULL para determinar si alguno de los campos se puede establecer en un valor null.

### <a name="remarks"></a>Comentarios

Llame a esta función miembro para determinar si el miembro de datos de campo especificado tiene valores NULL (se puede establecer en un valor null; C++ NULL no es lo mismo que null, que, en la terminología de bases de datos, significa "sin valor").

> [!NOTE]
>  Si ha implementado la obtención masiva de filas, no puede llamar a `IsFieldNullable`. En su lugar, llame a la función miembro [GetODBCFieldInfo](#getodbcfieldinfo) para determinar si un campo se puede establecer en un valor null. Tenga en cuenta que siempre puede llamar a `GetODBCFieldInfo`, independientemente de si ha implementado la obtención masiva de filas. Para obtener más información sobre la obtención masiva de filas, vea el artículo [Conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Un campo que no puede ser null debe tener un valor. Si intenta establecer un campo de este tipo en NULL al agregar o actualizar un registro, el origen de datos rechaza la adición o actualización, y [Update](#update) producirá una excepción. La excepción se produce cuando se llama a `Update`, no cuando se llama a [SetFieldNull](#setfieldnull).

Si se usa NULL para el primer argumento de la función, solo se aplicará la función a los campos `outputColumn`, no `param` campos. Por ejemplo, la llamada

[!code-cpp[NVC_MFCDatabase#26](../../mfc/codesnippet/cpp/crecordset-class_10.cpp)]

establecerá solo `outputColumn` campos en NULL; `param` campos no se verán afectados.

Para trabajar en `param` campos, debe proporcionar la dirección real del `param` individual en el que desea trabajar, por ejemplo:

[!code-cpp[NVC_MFCDatabase#27](../../mfc/codesnippet/cpp/crecordset-class_11.cpp)]

Esto significa que no se pueden establecer todos los campos de `param` en NULL, como se puede hacer con los campos de `outputColumn`.

`IsFieldNullable` se implementa a través de [DoFieldExchange](#dofieldexchange).

##  <a name="isopen"></a>CRecordset:: IsOpen

Determina si el conjunto de registros ya está abierto.

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se ha llamado previamente a la función miembro [Open](#open) o [Requery](#requery) del objeto de conjunto de registros y el conjunto de registros no se ha cerrado; de lo contrario, es 0.

##  <a name="m_hstmt"></a>CRecordset:: m_hstmt

Contiene un identificador de la estructura de datos de la instrucción ODBC, de tipo HSTMT, asociada al conjunto de registros.

### <a name="remarks"></a>Comentarios

Cada consulta a un origen de datos ODBC está asociada a un HSTMT.

> [!CAUTION]
>  No utilice `m_hstmt` antes de que se haya llamado a [Open](#open) .

Normalmente no es necesario tener acceso directamente al HSTMT, pero puede que sea necesario para la ejecución directa de instrucciones SQL. La función miembro `ExecuteSQL` de la clase `CDatabase` proporciona un ejemplo del uso de `m_hstmt`.

##  <a name="m_nfields"></a>CRecordset:: m_nFields

Contiene el número de miembros de datos de campo de la clase de conjunto de registros; es decir, el número de columnas seleccionadas por el conjunto de registros del origen de datos.

### <a name="remarks"></a>Comentarios

El constructor de la clase de conjunto de registros debe inicializar `m_nFields` con el número correcto. Si no ha implementado la obtención masiva de filas, ClassWizard escribe esta inicialización cuando se usa para declarar la clase de conjunto de registros. También puede escribirlo manualmente.

El marco de trabajo utiliza este número para administrar la interacción entre los miembros de datos de campo y las columnas correspondientes del registro actual en el origen de datos.

> [!CAUTION]
>  Este número debe corresponder al número de columnas de salida registradas en `DoFieldExchange` o `DoBulkFieldExchange` después de una llamada a [SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype) con el parámetro `CFieldExchange::outputColumn`.

Puede enlazar columnas dinámicamente, como se explica en el artículo "conjunto de registros: enlazar dinámicamente columnas de datos". Si lo hace, debe aumentar el recuento en `m_nFields` para reflejar el número de llamadas de función RFX o RFX masivo en el `DoFieldExchange` o `DoBulkFieldExchange` función miembro para las columnas enlazadas dinámicamente.

Para obtener más información, vea los artículos [conjunto de registros: enlazar dinámicamente columnas de datos (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md) y [conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

### <a name="example"></a>Ejemplo

Vea el artículo [intercambio de campos de registros: utilizar RFX](../../data/odbc/record-field-exchange-using-rfx.md).

##  <a name="m_nparams"></a>CRecordset:: m_nParams

Contiene el número de miembros de datos de parámetro de la clase de conjunto de registros; es decir, el número de parámetros pasados con la consulta del conjunto de registros.

### <a name="remarks"></a>Comentarios

Si la clase de conjunto de registros tiene algún miembro de datos de parámetro, el constructor de la clase debe inicializar `m_nParams` con el número correcto. El valor de `m_nParams` tiene como valor predeterminado 0. Si agrega miembros de datos de parámetro (que debe realizar manualmente), también debe agregar manualmente una inicialización en el constructor de clase para reflejar el número de parámetros (que debe ser al menos tan grande como el número de marcadores de posición ' ' en el `m_strFilter` o `m_strSort` cadena).

El marco de trabajo utiliza este número cuando Parametriza la consulta del conjunto de registros.

> [!CAUTION]
>  Este número debe corresponder al número de "params" registrado en `DoFieldExchange` o `DoBulkFieldExchange` después de una llamada a [SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype) con un valor de parámetro de `CFieldExchange::inputParam`, `CFieldExchange::param`, `CFieldExchange::outputParam`o `CFieldExchange::inoutParam`.

### <a name="example"></a>Ejemplo

  Vea los artículos [conjunto de registros: parametrizar un conjunto de registros (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md) y [intercambio de campos de registros: utilizar RFX](../../data/odbc/record-field-exchange-using-rfx.md).

##  <a name="m_pdatabase"></a>CRecordset:: m_pDatabase

Contiene un puntero al objeto `CDatabase` a través del que el conjunto de registros está conectado a un origen de datos.

### <a name="remarks"></a>Comentarios

Esta variable se establece de dos maneras. Normalmente, se pasa un puntero a un objeto que ya está conectado `CDatabase` al construir el objeto de conjunto de registros. Si pasa NULL en su lugar, `CRecordset` crea un objeto `CDatabase` y lo conecta. En cualquier caso, `CRecordset` almacena el puntero en esta variable.

Normalmente, no necesitará usar directamente el puntero almacenado en `m_pDatabase`. Sin embargo, si escribe sus propias extensiones en `CRecordset`, es posible que tenga que usar el puntero. Por ejemplo, puede que necesite el puntero si inicia sus propios `CDBException`s. O bien, puede que necesite hacerlo si necesita hacer algo con el mismo `CDatabase` objeto, como ejecutar transacciones, establecer tiempos de espera o llamar a la función miembro `ExecuteSQL` de la clase `CDatabase` para ejecutar instrucciones SQL directamente.

##  <a name="m_strfilter"></a>CRecordset:: m_strFilter

Después de crear el objeto de conjunto de registros, pero antes de llamar a su función miembro de `Open`, utilice este miembro de datos para almacenar un `CString` que contenga una cláusula **Where** de SQL.

### <a name="remarks"></a>Comentarios

El conjunto de registros usa esta cadena para restringir (o filtrar) los registros que selecciona durante la llamada `Open` o `Requery`. Esto resulta útil para seleccionar un subconjunto de registros, como "todos los vendedores basados en California" ("State = CA"). La sintaxis SQL de ODBC para una cláusula **Where** es

`WHERE search-condition`

Tenga en cuenta que no incluye la palabra clave **Where** en la cadena. El marco de trabajo lo proporciona.

También puede parametrizar la cadena de filtro colocando los marcadores de posición ' ' en ella, declarando un miembro de datos de parámetro en la clase para cada marcador de posición y pasando parámetros al conjunto de registros en tiempo de ejecución. Esto le permite construir el filtro en tiempo de ejecución. Para obtener más información, vea el artículo [conjunto de registros: parametrizar un conjunto de registros (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).

Para obtener más información acerca de las cláusulas **Where** de SQL, vea el artículo [SQL](../../data/odbc/sql.md). Para obtener más información sobre la selección y el filtrado de registros, vea el artículo conjunto de registros [: filtrar registros (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDatabase#30](../../mfc/codesnippet/cpp/crecordset-class_12.cpp)]

##  <a name="m_strsort"></a>CRecordset:: m_strSort

Después de crear el objeto de conjunto de registros, pero antes de llamar a su función miembro de `Open`, utilice este miembro de datos para almacenar un `CString` que contenga una cláusula **order by** de SQL.

### <a name="remarks"></a>Comentarios

El conjunto de registros usa esta cadena para ordenar los registros que selecciona durante la llamada `Open` o `Requery`. Puede usar esta característica para ordenar un conjunto de registros en una o varias columnas. La sintaxis SQL de ODBC para una cláusula **order by** es

`ORDER BY sort-specification [, sort-specification]...`

donde una especificación de ordenación es un entero o un nombre de columna. También puede especificar orden ascendente o descendente (el orden es ascendente de forma predeterminada) anexando "ASC" o "DESC" a la lista de columnas en la cadena de ordenación. Los registros seleccionados se ordenan primero por la primera columna enumerada, luego por el segundo, etc. Por ejemplo, puede ordenar un conjunto de registros "Customers" por Apellido y luego por nombre. El número de columnas que puede enumerar depende del origen de datos. Para obtener más información, vea el Windows SDK.

Tenga en cuenta que no incluye la palabra clave **order by** en la cadena. El marco de trabajo lo proporciona.

Para obtener más información sobre las cláusulas SQL, vea el artículo [SQL](../../data/odbc/sql.md). Para obtener más información sobre la ordenación de registros, vea el artículo conjunto de registros [: ordenar registros (ODBC)](../../data/odbc/recordset-sorting-records-odbc.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDatabase#31](../../mfc/codesnippet/cpp/crecordset-class_13.cpp)]

##  <a name="move"></a>CRecordset:: Move

Mueve el puntero del registro actual dentro del conjunto de registros, ya sea hacia delante o hacia atrás.

```
virtual void Move(
    long nRows,
    WORD wFetchType = SQL_FETCH_RELATIVE);
```

### <a name="parameters"></a>Parámetros

*nRows*<br/>
Número de filas que se van a desplazar hacia delante o hacia atrás. Los valores positivos avanzan hacia delante, hacia el final del conjunto de registros. Los valores negativos se mueven hacia atrás, hacia el principio.

*wFetchType*<br/>
Determina el conjunto de filas que `Move` recuperará. Para conocer más detalles, vea la sección Comentarios.

### <a name="remarks"></a>Comentarios

Si pasa un valor de 0 para *nRows*, `Move` actualiza el registro actual; `Move` finalizará cualquier modo de `AddNew` o `Edit` actual y restaurará el valor del registro actual antes de que se llame a `AddNew` o `Edit`.

> [!NOTE]
>  Al desplazarse por un conjunto de registros, no se pueden omitir los registros eliminados. Vea [CRecordset:: IsDeleted](#isdeleted) para obtener más información. Al abrir un `CRecordset` con el conjunto de opciones `skipDeletedRecords`, `Move` valida si el parámetro *nRows* es 0. Este comportamiento evita la actualización de filas eliminadas por otras aplicaciones cliente que usan los mismos datos. Vea el parámetro *dwOption* en [Open](#open) para obtener una descripción de `skipDeletedRecords`.

`Move` cambia la posición del conjunto de registros por los conjuntos de filas. En función de los valores de *nRows* y *wFetchType*, `Move` captura el conjunto de filas adecuado y, a continuación, hace que el primer registro del conjunto de filas sea el registro actual. Si no ha implementado la obtención masiva de filas, el tamaño del conjunto de filas siempre es 1. Al obtener un conjunto de filas, `Move` llama directamente a la función miembro [CheckRowsetError](#checkrowseterror) para controlar los errores resultantes de la captura.

Dependiendo de los valores que se pasan, `Move` es equivalente a otras funciones miembro de `CRecordset`. En concreto, el valor de *wFetchType* puede indicar una función miembro que es más intuitiva y a menudo el método preferido para mover el registro actual.

En la tabla siguiente se enumeran los posibles valores de *wFetchType*, el conjunto de filas que `Move` capturará basándose en *wFetchType* y *nRows*, y cualquier función miembro equivalente correspondiente a *wFetchType*.

|wFetchType|Conjunto de filas recuperado|Función miembro equivalente|
|----------------|--------------------|--------------------------------|
|SQL_FETCH_RELATIVE (valor predeterminado)|El conjunto de filas que inicia *nRows* filas de la primera fila del conjunto de filas actual.||
|SQL_FETCH_NEXT|Siguiente conjunto de filas; *nRows* se omite.|[MoveNext](#movenext)|
|SQL_FETCH_PRIOR|El conjunto de filas anterior; *nRows* se omite.|[Plaza](#moveprev)|
|SQL_FETCH_FIRST|Primer conjunto de filas del conjunto de registros; *nRows* se omite.|[MoveFirst](#movefirst)|
|SQL_FETCH_LAST|El último conjunto de filas completo del conjunto de registros; *nRows* se omite.|[MoveLast](#movelast)|
|SQL_FETCH_ABSOLUTE|Si *nRows* > 0, el conjunto de filas que inicia *nRows* filas desde el principio del conjunto de registros. Si *nRows* < 0, el conjunto de filas que inicia *nRows* filas desde el final del conjunto de registros. Si *nRows* = 0, se devuelve una condición de inicio de archivo (BOF).|[SetAbsolutePosition](#setabsoluteposition)|
|SQL_FETCH_BOOKMARK|Conjunto de filas que empieza en la fila cuyo valor de marcador corresponde a *nRows*.|[SetBookmark](#setbookmark)|

> [!NOTE]
>  En el caso de los conjuntos de registros solo hacia delante, `Move` solo es válido con un valor de SQL_FETCH_NEXT para *wFetchType*.

> [!CAUTION]
>  La llamada a `Move` produce una excepción si el conjunto de registros no tiene registros. Para determinar si el conjunto de registros tiene registros, llame a [IsBOF](#isbof) y [IsEOF](#iseof).

> [!NOTE]
>  Si se ha desplazado más allá del principio o el final del conjunto de registros (`IsBOF` o `IsEOF` devuelve un valor distinto de cero), la llamada a una función de `Move` producirá una `CDBException`. Por ejemplo, si `IsEOF` devuelve un valor distinto de cero y `IsBOF` no, `MoveNext` producirá una excepción, pero `MovePrev` no.

> [!NOTE]
>  Si llama a `Move` mientras el registro actual se está actualizando o agregando, las actualizaciones se pierden sin previo aviso.

Para obtener más información sobre la navegación por conjuntos de registros, vea los artículos [conjunto de registros: desplazamiento (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) y [conjunto de registros: marcadores y posiciones absolutas (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md). Para obtener más información sobre la obtención masiva de filas, vea el artículo [Conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md). Para obtener información relacionada, vea la función de la API de ODBC `SQLExtendedFetch` en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDatabase#28](../../mfc/codesnippet/cpp/crecordset-class_14.cpp)]

##  <a name="movefirst"></a>CRecordset:: MoveFirst

Hace que el primer registro del primer conjunto de filas sea el registro actual.

```
void MoveFirst();
```

### <a name="remarks"></a>Comentarios

Independientemente de si se ha implementado la obtención masiva de filas, siempre será el primer registro del conjunto de registros.

No es necesario llamar a `MoveFirst` inmediatamente después de abrir el conjunto de registros. En ese momento, el primer registro (si existe) se convierte automáticamente en el registro actual.

> [!NOTE]
>  Esta función miembro no es válida para los conjuntos de registros solo hacia delante.

> [!NOTE]
>  Al desplazarse por un conjunto de registros, no se pueden omitir los registros eliminados. Vea la función miembro [IsDeleted](#isdeleted) para obtener más información.

> [!CAUTION]
>  Si se llama a cualquiera de las funciones de `Move`, se produce una excepción si el conjunto de registros no tiene registros. Para determinar si el conjunto de registros tiene registros, llame a `IsBOF` y `IsEOF`.

> [!NOTE]
>  Si llama a cualquiera de las funciones de `Move` mientras el registro actual se está actualizando o agregando, las actualizaciones se pierden sin previo aviso.

Para obtener más información sobre la navegación por conjuntos de registros, vea los artículos [conjunto de registros: desplazamiento (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) y [conjunto de registros: marcadores y posiciones absolutas (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md). Para obtener más información sobre la obtención masiva de filas, vea el artículo [Conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [IsBOF](#isbof).

##  <a name="movelast"></a>CRecordset:: MoveLast

Convierte el primer registro del último conjunto de filas completo en el registro actual.

```
void MoveLast();
```

### <a name="remarks"></a>Comentarios

Si no ha implementado la obtención masiva de filas, el conjunto de registros tiene un tamaño de conjunto de filas de 1, por lo que `MoveLast` simplemente se desplaza hasta el último registro del conjunto de registros.

> [!NOTE]
>  Esta función miembro no es válida para los conjuntos de registros solo hacia delante.

> [!NOTE]
>  Al desplazarse por un conjunto de registros, no se pueden omitir los registros eliminados. Vea la función miembro [IsDeleted](#isdeleted) para obtener más información.

> [!CAUTION]
>  Si se llama a cualquiera de las funciones de `Move`, se produce una excepción si el conjunto de registros no tiene registros. Para determinar si el conjunto de registros tiene registros, llame a `IsBOF` y `IsEOF`.

> [!NOTE]
>  Si llama a cualquiera de las funciones de `Move` mientras el registro actual se está actualizando o agregando, las actualizaciones se pierden sin previo aviso.

Para obtener más información sobre la navegación por conjuntos de registros, vea los artículos [conjunto de registros: desplazamiento (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) y [conjunto de registros: marcadores y posiciones absolutas (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md). Para obtener más información sobre la obtención masiva de filas, vea el artículo [Conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [IsBOF](#isbof).

##  <a name="movenext"></a>CRecordset:: MoveNext

Convierte el primer registro del conjunto de filas siguiente en el registro actual.

```
void MoveNext();
```

### <a name="remarks"></a>Comentarios

Si no ha implementado la obtención masiva de filas, el conjunto de registros tiene un tamaño de conjunto de filas de 1, por lo que `MoveNext` simplemente se mueve al siguiente registro.

> [!NOTE]
>  Al desplazarse por un conjunto de registros, no se pueden omitir los registros eliminados. Vea la función miembro [IsDeleted](#isdeleted) para obtener más información.

> [!CAUTION]
>  Si se llama a cualquiera de las funciones de `Move`, se produce una excepción si el conjunto de registros no tiene registros. Para determinar si el conjunto de registros tiene registros, llame a `IsBOF` y `IsEOF`.

> [!NOTE]
>  También se recomienda llamar a `IsEOF` antes de llamar a `MoveNext`. Por ejemplo, si se ha desplazado más allá del final del conjunto de registros, `IsEOF` devolverá un valor distinto de cero; una llamada subsiguiente a `MoveNext` produciría una excepción.

> [!NOTE]
>  Si llama a cualquiera de las funciones de `Move` mientras el registro actual se está actualizando o agregando, las actualizaciones se pierden sin previo aviso.

Para obtener más información sobre la navegación por conjuntos de registros, vea los artículos [conjunto de registros: desplazamiento (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) y [conjunto de registros: marcadores y posiciones absolutas (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md). Para obtener más información sobre la obtención masiva de filas, vea el artículo [Conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [IsBOF](#isbof).

##  <a name="moveprev"></a>CRecordset:: MovePrev

Convierte el primer registro del conjunto de filas anterior en el registro actual.

```
void MovePrev();
```

### <a name="remarks"></a>Comentarios

Si no ha implementado la obtención masiva de filas, el conjunto de registros tiene un tamaño de conjunto de filas de 1, por lo que `MovePrev` simplemente se mueve al registro anterior.

> [!NOTE]
>  Esta función miembro no es válida para los conjuntos de registros solo hacia delante.

> [!NOTE]
>  Al desplazarse por un conjunto de registros, no se pueden omitir los registros eliminados. Vea la función miembro [IsDeleted](#isdeleted) para obtener más información.

> [!CAUTION]
>  Si se llama a cualquiera de las funciones de `Move`, se produce una excepción si el conjunto de registros no tiene registros. Para determinar si el conjunto de registros tiene registros, llame a `IsBOF` y `IsEOF`.

> [!NOTE]
>  También se recomienda llamar a `IsBOF` antes de llamar a `MovePrev`. Por ejemplo, si se ha desplazado hacia delante del principio del conjunto de registros, `IsBOF` devolverá un valor distinto de cero; una llamada subsiguiente a `MovePrev` produciría una excepción.

> [!NOTE]
>  Si llama a cualquiera de las funciones de `Move` mientras el registro actual se está actualizando o agregando, las actualizaciones se pierden sin previo aviso.

Para obtener más información sobre la navegación por conjuntos de registros, vea los artículos [conjunto de registros: desplazamiento (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) y [conjunto de registros: marcadores y posiciones absolutas (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md). Para obtener más información sobre la obtención masiva de filas, vea el artículo [Conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [IsBOF](#isbof).

##  <a name="onsetoptions"></a>CRecordset:: OnSetOptions

Se llama para establecer las opciones (utilizadas en la selección) para la instrucción ODBC especificada.

```
virtual void OnSetOptions(HSTMT hstmt);
```

### <a name="parameters"></a>Parámetros

*hstmt*<br/>
HSTMT de la instrucción ODBC cuyas opciones se van a establecer.

### <a name="remarks"></a>Comentarios

Llame a `OnSetOptions` para establecer las opciones (utilizadas en la selección) para la instrucción ODBC especificada. El marco de trabajo llama a esta función miembro para establecer las opciones iniciales del conjunto de registros. `OnSetOptions` determina la compatibilidad del origen de datos con los cursores desplazables y la simultaneidad del cursor, y establece las opciones del conjunto de registros en consecuencia. (Mientras que `OnSetOptions` se utiliza para las operaciones de selección, `OnSetUpdateOptions` se utiliza para las operaciones de actualización).

Invalide `OnSetOptions` para establecer opciones específicas para el controlador o el origen de datos. Por ejemplo, si el origen de datos admite la apertura para el acceso exclusivo, podría invalidar `OnSetOptions` para beneficiarse de esa capacidad.

Para obtener más información sobre los cursores, vea el artículo [ODBC](../../data/odbc/odbc-basics.md).

##  <a name="onsetupdateoptions"></a>CRecordset:: OnSetUpdateOptions

Se llama para establecer las opciones (utilizadas en la actualización) para la instrucción ODBC especificada.

```
virtual void OnSetUpdateOptions(HSTMT hstmt);
```

### <a name="parameters"></a>Parámetros

*hstmt*<br/>
HSTMT de la instrucción ODBC cuyas opciones se van a establecer.

### <a name="remarks"></a>Comentarios

Llame a `OnSetUpdateOptions` para establecer las opciones (utilizadas en la actualización) para la instrucción ODBC especificada. El marco de trabajo llama a esta función miembro después de crear un HSTMT para actualizar los registros de un conjunto de registros. (Mientras que `OnSetOptions` se utiliza para las operaciones de selección, `OnSetUpdateOptions` se utiliza para las operaciones de actualización). `OnSetUpdateOptions` determina la compatibilidad del origen de datos con los cursores desplazables y la simultaneidad del cursor, y establece las opciones del conjunto de registros en consecuencia.

Invalide `OnSetUpdateOptions` para establecer las opciones de una instrucción ODBC antes de que dicha instrucción se utilice para tener acceso a una base de datos.

Para obtener más información sobre los cursores, vea el artículo [ODBC](../../data/odbc/odbc-basics.md).

##  <a name="open"></a>CRecordset:: Open

Abre el conjunto de registros recuperando la tabla o realizando la consulta que el conjunto de registros representa.

```
virtual BOOL Open(
    UINT nOpenType = AFX_DB_USE_DEFAULT_TYPE,
    LPCTSTR lpszSQL = NULL,
    DWORD dwOptions = none);
```

### <a name="parameters"></a>Parámetros

*nOpenType*<br/>
Acepte el valor predeterminado, AFX_DB_USE_DEFAULT_TYPE, o use uno de los siguientes valores de la `enum OpenType`:

- `CRecordset::dynaset` un conjunto de registros con desplazamiento bidireccional. La pertenencia y el orden de los registros se determinan cuando se abre el conjunto de registros, pero los cambios realizados por otros usuarios en los valores de datos son visibles después de una operación de búsqueda. Los dynasets también se conocen como conjuntos de registros conjunto controlados por conjuntos de claves.

- `CRecordset::snapshot` un conjunto de registros estático con desplazamiento bidireccional. La pertenencia y el orden de los registros se determinan cuando se abre el conjunto de registros; los valores de datos se determinan cuando se buscan los registros. Los cambios realizados por otros usuarios no son visibles hasta que no se cierra y se vuelve a abrir el conjunto de registros.

- `CRecordset::dynamic` un conjunto de registros con desplazamiento bidireccional. Los cambios realizados por otros usuarios en la pertenencia, el orden y los valores de datos son visibles después de una operación de recuperación de cambios. Tenga en cuenta que muchos controladores ODBC no admiten este tipo de conjunto de registros.

- `CRecordset::forwardOnly` un conjunto de registros de solo lectura solo con desplazamiento hacia delante.

   Por `CRecordset`, el valor predeterminado es `CRecordset::snapshot`. El mecanismo de valor predeterminado permite que los asistentes de Visual C++ interactúen con `CRecordset` de ODBC y `CDaoRecordset` de DAO, que tienen valores predeterminados diferentes.

Para obtener más información sobre estos tipos de conjunto de registros, vea el artículo [conjunto de registros (ODBC)](../../data/odbc/recordset-odbc.md). Para obtener información relacionada, vea el artículo sobre el uso de cursores de bloque y desplazables en el Windows SDK.

> [!CAUTION]
>  Si el tipo solicitado no se admite, el marco de trabajo produce una excepción.

*lpszSQL*<br/>
Puntero de cadena que contiene uno de los elementos siguientes:

- Un puntero nulo.

- Nombre de una tabla.

- Una instrucción **Select** de SQL (opcionalmente con una cláusula **Where** u **order by** de SQL).

- Una instrucción **Call** que especifica el nombre de una consulta predefinida (procedimiento almacenado). Tenga cuidado de no insertar espacios en blanco entre la llave y la palabra clave **Call** .

Para obtener más información sobre esta cadena, vea la tabla y la explicación del rol del ClassWizard en la sección [comentarios](#remarks) .

> [!NOTE]
>  El orden de las columnas del conjunto de resultados debe coincidir con el orden de las llamadas de función RFX o RFX masivo en la invalidación de la función [DoFieldExchange](#dofieldexchange) o [DoBulkFieldExchange](#dobulkfieldexchange) .

*dwOptions*<br/>
Máscara de bits que puede especificar una combinación de los valores que se muestran a continuación. Algunas de estas opciones son mutuamente excluyentes. El valor predeterminado es **None**.

- No `CRecordset::none` ningún conjunto de opciones. Este valor del parámetro es mutuamente excluyente con todos los demás valores. De forma predeterminada, el conjunto de registros se puede actualizar con [Editar](#edit) o [eliminar](#delete) y permite anexar nuevos registros con [AddNew](#addnew). La capacidad de actualización depende del origen de datos, así como de la opción *nOpenType* que especifique. La optimización para adiciones masivas no está disponible. La obtención masiva de filas no se implementará. Los registros eliminados no se omitirán al navegar por el conjunto de registros. Los marcadores no están disponibles. Se implementa la comprobación automática de campos modificados.

- `CRecordset::appendOnly` no permiten `Edit` ni `Delete` en el conjunto de registros. Solo permite `AddNew`. Esta opción es mutuamente excluyente con `CRecordset::readOnly`.

- `CRecordset::readOnly` abrir el conjunto de registros como de solo lectura. Esta opción es mutuamente excluyente con `CRecordset::appendOnly`.

- `CRecordset::optimizeBulkAdd` usar una instrucción SQL preparada para optimizar la adición de muchos registros al mismo tiempo. Solo se aplica si no se usa la función de la API de ODBC `SQLSetPos` para actualizar el conjunto de registros. La primera actualización determina qué campos se marcan como modificados. Esta opción es mutuamente excluyente con `CRecordset::useMultiRowFetch`.

- `CRecordset::useMultiRowFetch` implementar la obtención masiva de filas para permitir la recuperación de varias filas en una sola operación de recopilación. Se trata de una característica avanzada diseñada para mejorar el rendimiento; sin embargo, el Asistente para clases no admite el intercambio masivo de campos de registros. Esta opción es mutuamente excluyente con `CRecordset::optimizeBulkAdd`. Tenga en cuenta que si especifica `CRecordset::useMultiRowFetch`, la opción `CRecordset::noDirtyFieldCheck` se activará automáticamente (el almacenamiento en búfer doble no estará disponible). en los conjuntos de registros solo hacia delante, la opción `CRecordset::useExtendedFetch` se activará automáticamente. Para obtener más información sobre la obtención masiva de filas, vea el artículo [Conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

- `CRecordset::skipDeletedRecords` omitir todos los registros eliminados al navegar por el conjunto de registros. Esto ralentiza el rendimiento en ciertas búsquedas relativas. Esta opción no es válida en los conjuntos de registros solo hacia delante. Si llama a [Move](#move) con el parámetro *nRows* establecido en 0 y la opción `CRecordset::skipDeletedRecords` establecida, `Move` se validará. Tenga en cuenta que `CRecordset::skipDeletedRecords` es similar al *empaquetado de controladores*, lo que significa que las filas eliminadas se quitan del conjunto de registros. Sin embargo, si el controlador empaqueta registros, solo se omitirán los registros que elimine; no se omitirán los registros eliminados por otros usuarios mientras el conjunto de registros está abierto. `CRecordset::skipDeletedRecords` omitirá las filas eliminadas por otros usuarios.

- `CRecordset::useBookmarks` pueden utilizar marcadores en el conjunto de registros, si se admiten. Los marcadores ralentizan la recuperación de datos pero mejoran el rendimiento de la navegación de datos. No es válida en conjuntos de registros solo hacia delante. Para obtener más información, vea el artículo [conjunto de registros: marcadores y posiciones absolutas (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md).

- `CRecordset::noDirtyFieldCheck` desactivar la comprobación automática de campos modificados (almacenamiento en búfer doble). Esto mejorará el rendimiento; sin embargo, para marcar manualmente los campos como modificados se debe llamar a las funciones miembro `SetFieldDirty` y `SetFieldNull`. Tenga en cuenta que el almacenamiento en búfer doble en la clase `CRecordset` es similar al almacenamiento en búfer doble en la clase `CDaoRecordset`. Sin embargo, en `CRecordset`, no se puede habilitar el almacenamiento en búfer doble en campos individuales; hay que habilitarlo o deshabilitarlo para todos los campos. Tenga en cuenta que si especifica la opción `CRecordset::useMultiRowFetch`, `CRecordset::noDirtyFieldCheck` se activará automáticamente. sin embargo, `SetFieldDirty` y `SetFieldNull` no se pueden utilizar en conjuntos de registros que implementan la obtención masiva de filas.

- `CRecordset::executeDirect` no utilizan una instrucción SQL preparada. Para mejorar el rendimiento, especifique esta opción si nunca se llamará a la función miembro `Requery`.

- `CRecordset::useExtendedFetch` implementar `SQLExtendedFetch` en lugar de `SQLFetch`. Está diseñado para implementar la obtención masiva de filas en conjuntos de registros solo hacia delante. Si especifica la opción `CRecordset::useMultiRowFetch` en un conjunto de registros de solo avance, `CRecordset::useExtendedFetch` se activará automáticamente.

- `CRecordset::userAllocMultiRowBuffers` el usuario asignará búferes de almacenamiento para los datos. Utilice esta opción junto con `CRecordset::useMultiRowFetch` si desea asignar su propio almacenamiento; de lo contrario, el marco de trabajo asignará automáticamente el almacenamiento necesario. Para obtener más información, vea el artículo [conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md). Tenga en cuenta que si se especifica `CRecordset::userAllocMultiRowBuffers` sin especificar `CRecordset::useMultiRowFetch`, se producirá un error en la aserción.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el objeto de `CRecordset` se abrió correctamente; de lo contrario, 0 si [CDatabase:: Open](../../mfc/reference/cdatabase-class.md#open) (si se llama a) devuelve 0.

### <a name="remarks"></a>Comentarios

Se debe llamar a esta función miembro para ejecutar la consulta definida por el conjunto de registros. Antes de llamar a `Open`, debe construir el objeto de conjunto de registros.

La conexión de este conjunto de registros con el origen de datos depende de cómo construya el conjunto de registros antes de llamar a `Open`. Si pasa un objeto [CDatabase](../../mfc/reference/cdatabase-class.md) al constructor del conjunto de registros que no se ha conectado al origen de datos, esta función miembro utiliza [GetDefaultConnect](#getdefaultconnect) para intentar abrir el objeto de base de datos. Si pasa NULL al constructor del conjunto de registros, el constructor crea un `CDatabase` objeto automáticamente y `Open` intenta conectar el objeto de base de datos. Para obtener información detallada sobre cómo cerrar el conjunto de registros y la conexión en estas circunstancias variables, vea [Close](#close).

> [!NOTE]
>  El acceso a un origen de datos mediante un objeto `CRecordset` siempre es compartido. A diferencia de la clase `CDaoRecordset`, no se puede utilizar un objeto `CRecordset` para abrir un origen de datos con acceso exclusivo.

Cuando se llama a `Open`, una consulta, normalmente una instrucción **Select** de SQL, selecciona registros en función de los criterios que se muestran en la tabla siguiente.

|Valor del parámetro lpszSQL|Los registros seleccionados están determinados por|Ejemplo|
|------------------------------------|----------------------------------------|-------------|
|NULL|La cadena devuelta por `GetDefaultSQL`.||
|Nombre de tabla SQL|Todas las columnas de la lista de tablas de `DoFieldExchange` o `DoBulkFieldExchange`.|`"Customer"`|
|Nombre de la consulta (procedimiento almacenado) predefinida|Las columnas de la consulta cuya devolución se ha definido.|`"{call OverDueAccts}"`|
|**Seleccionar** columna-lista **de** tabla-lista|Las columnas especificadas de las tablas indicadas.|`"SELECT CustId, CustName FROM`<br /><br /> `Customer"`|

> [!CAUTION]
>  Tenga cuidado de no insertar espacios en blanco adicionales en la cadena SQL. Por ejemplo, si inserta un espacio en blanco entre la llave y la palabra clave **Call** , MFC interpretará la cadena de SQL como un nombre de tabla y la incorporará en una instrucción **Select** , lo que provocará que se produzca una excepción. Del mismo modo, si la consulta predefinida usa un parámetro de salida, no inserte un espacio en blanco entre la llave y el símbolo ' '. Por último, no debe insertar el espacio en blanco delante de la llave en una instrucción **Call** o antes de la palabra clave **Select** en una instrucción **Select** .

El procedimiento habitual es pasar NULL a `Open`; en este caso, `Open` llama a [GetDefaultSQL](#getdefaultsql). Si usa una clase `CRecordset` derivada, `GetDefaultSQL` proporciona los nombres de tabla especificados en ClassWizard. Se puede especificar otra información en el parámetro `lpszSQL`.

Lo que pase, `Open` crea una cadena de SQL final para la consulta (la cadena puede tener las cláusulas **Where** y **order by** de SQL anexadas a la cadena `lpszSQL` pasada) y, a continuación, ejecuta la consulta. Puede examinar la cadena construida llamando a [GetSQL](#getsql) después de llamar a `Open`. Para obtener detalles adicionales sobre cómo el conjunto de registros crea una instrucción SQL y selecciona registros, vea el artículo conjunto de registros [: cómo se seleccionan los registros (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md).

Los miembros de datos de campo de la clase de conjunto de registros están enlazados a las columnas de los datos seleccionados. Si se devuelve algún registro, el primer registro se convierte en el registro actual.

Si desea establecer las opciones del conjunto de registros, como un filtro o una ordenación, especifíquelo después de construir el objeto de conjunto de registros, pero antes de llamar a `Open`. Si desea actualizar los registros del conjunto de registros después de que el conjunto de registros ya esté abierto, llame a [Requery](#requery).

Para obtener más información, incluidos los ejemplos adicionales, vea los artículos [conjunto de registros (ODBC)](../../data/odbc/recordset-odbc.md), conjunto de registros [: cómo se seleccionan los registros (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)y conjunto de registros [: crear y cerrar conjuntos de registros (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md).

### <a name="example"></a>Ejemplo

En los ejemplos de código siguientes se muestran distintas formas de la llamada `Open`.

[!code-cpp[NVC_MFCDatabase#16](../../mfc/codesnippet/cpp/crecordset-class_15.cpp)]

##  <a name="refreshrowset"></a>CRecordset:: RefreshRowset

Actualiza los datos y el estado de una fila en el conjunto de filas actual.

```
void RefreshRowset(
    WORD wRow,
    WORD wLockType = SQL_LOCK_NO_CHANGE);
```

### <a name="parameters"></a>Parámetros

*wRow*<br/>
La posición basada en uno de una fila en el conjunto de filas actual. Este valor puede oscilar entre cero y el tamaño del conjunto de filas.

*wLockType*<br/>
Un valor que indica cómo bloquear la fila una vez que se ha actualizado. Para conocer más detalles, vea la sección Comentarios.

### <a name="remarks"></a>Comentarios

Si pasa un valor de cero para *wRow*, se actualizarán todas las filas del conjunto de filas.

Para usar `RefreshRowset`, debe haber implementado la obtención masiva de filas especificando la opción `CRecordset::useMulitRowFetch` en la función miembro [abierta](#open) .

`RefreshRowset` llama a la función de la API de ODBC `SQLSetPos`. El parámetro *wLockType* especifica el estado de bloqueo de la fila después de que se haya ejecutado `SQLSetPos`. En la tabla siguiente se describen los posibles valores para *wLockType*.

|wLockType|Descripción|
|---------------|-----------------|
|SQL_LOCK_NO_CHANGE (valor predeterminado)|El controlador o el origen de datos garantiza que la fila se encuentra en el mismo estado bloqueado o desbloqueado que tenía antes de que se llamara a `RefreshRowset`.|
|SQL_LOCK_EXCLUSIVE|El controlador o el origen de datos bloquea la fila exclusivamente. No todos los orígenes de datos admiten este tipo de bloqueo.|
|SQL_LOCK_UNLOCK|El controlador o el origen de datos desbloquea la fila. No todos los orígenes de datos admiten este tipo de bloqueo.|

Para obtener más información acerca de `SQLSetPos`, vea el Windows SDK. Para obtener más información sobre la obtención masiva de filas, vea el artículo [Conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

##  <a name="requery"></a>CRecordset:: Requery

Vuelve a generar (actualiza) un conjunto de registros.

```
virtual BOOL Requery();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el conjunto de registros se ha vuelto a generar correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Si se devuelve algún registro, el primer registro se convierte en el registro actual.

Para que el conjunto de registros refleje las adiciones y eliminaciones que usted u otros usuarios realizan en el origen de datos, debe volver a generar el conjunto de registros llamando a `Requery`. Si el conjunto de registros es un Dynaset, refleja automáticamente las actualizaciones que usted u otros usuarios realizan en sus registros existentes (pero no en las adiciones). Si el conjunto de registros es una instantánea, debe llamar a `Requery` para reflejar las modificaciones realizadas por otros usuarios, así como las adiciones y eliminaciones.

En el caso de una instantánea o de un Dynaset, llame a `Requery` en cualquier momento en el que desee volver a generar el conjunto de registros con un nuevo filtro u ordenación, o nuevos valores de parámetro. Establezca el nuevo filtro o la propiedad de ordenación asignando nuevos valores a `m_strFilter` y `m_strSort` antes de llamar a `Requery`. Establezca nuevos parámetros asignando nuevos valores a los miembros de datos de parámetro antes de llamar a `Requery`. Si las cadenas de filtro y de ordenación no cambian, puede volver a usar la consulta, lo que mejora el rendimiento.

Si se produce un error al intentar volver a generar el conjunto de registros, se cierra el conjunto de registros. Antes de llamar a `Requery`, puede determinar si el conjunto de registros se puede consultar mediante una llamada a la función miembro `CanRestart`. `CanRestart` no garantiza que `Requery` se realizará correctamente.

> [!CAUTION]
>  Llame a `Requery` solo después de haber llamado a [Open](#open).

### <a name="example"></a>Ejemplo

En este ejemplo se vuelve a generar un conjunto de registros para aplicar un criterio de ordenación diferente.

[!code-cpp[NVC_MFCDatabase#29](../../mfc/codesnippet/cpp/crecordset-class_16.cpp)]

##  <a name="setabsoluteposition"></a>CRecordset:: SetAbsolutePosition

Coloca el conjunto de registros en el registro correspondiente al número de registro especificado.

```
void SetAbsolutePosition(long nRows);
```

### <a name="parameters"></a>Parámetros

*nRows*<br/>
Posición ordinal basada en uno del registro actual del conjunto de registros.

### <a name="remarks"></a>Comentarios

`SetAbsolutePosition` mueve el puntero del registro actual basándose en esta posición ordinal.

> [!NOTE]
>  Esta función miembro no es válida en los conjuntos de registros solo hacia delante.

En el caso de los conjuntos de registros ODBC, un valor de posición absoluta de 1 hace referencia al primer registro del conjunto de registros; un valor de 0 hace referencia a la posición de inicio de archivo (BOF).

También puede pasar valores negativos a `SetAbsolutePosition`. En este caso, la posición del conjunto de registros se evalúa desde el final del conjunto de registros. Por ejemplo, `SetAbsolutePosition( -1 )` mueve el puntero de registro actual al último registro del conjunto de registros.

> [!NOTE]
>  La posición absoluta no está pensada para usarse como un número de registro suplente. Los marcadores siguen siendo la forma recomendada de conservar y volver a una posición determinada, ya que la posición de un registro cambia cuando se eliminan los registros anteriores. Además, no puede estar seguro de que un registro determinado tendrá la misma posición absoluta si el conjunto de registros se vuelve a crear porque el orden de los registros individuales dentro de un conjunto de registros no está garantizado a menos que se cree con una instrucción SQL que use un **orden by** cláusula.

Para obtener más información sobre la navegación y los marcadores de conjunto de registros, vea los artículos [conjunto de registros: desplazamiento (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) y [conjunto de registros: marcadores y posiciones absolutas (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md).

##  <a name="setbookmark"></a>CRecordset:: SetBookmark

Coloca el conjunto de registros en el registro que contiene el marcador especificado.

```
void SetBookmark(const CDBVariant& varBookmark);
```

### <a name="parameters"></a>Parámetros

*varBookmark*<br/>
Referencia a un objeto [cdbvariant (](../../mfc/reference/cdbvariant-class.md) que contiene el valor de marcador de un registro específico.

### <a name="remarks"></a>Comentarios

Para determinar si se admiten marcadores en el conjunto de registros, llame a [CanBookmark](#canbookmark). Para que los marcadores estén disponibles si se admiten, debe establecer la opción `CRecordset::useBookmarks` en el parámetro *dwOptions* de la función miembro [abierta](#open) .

> [!NOTE]
>  Si los marcadores no se admiten o no están disponibles, al llamar a `SetBookmark` se producirá una excepción. No se admiten marcadores en conjuntos de registros solo hacia delante.

Para recuperar primero el marcador del registro actual, llame a [GetBookmark](#getbookmark), que guarda el valor de marcador en un objeto `CDBVariant`. Más adelante, puede volver a ese registro llamando a `SetBookmark` mediante el valor de marcador guardado.

> [!NOTE]
>  Después de ciertas operaciones de conjunto de registros, debe comprobar la persistencia del marcador antes de llamar a `SetBookmark`. Por ejemplo, si recupera un marcador con `GetBookmark` y, a continuación, llama a `Requery`, es posible que el marcador ya no sea válido. Llame a [CDatabase:: GetBookmarkPersistence](../../mfc/reference/cdatabase-class.md#getbookmarkpersistence) para comprobar si puede llamar a `SetBookmark`de forma segura.

Para obtener más información sobre los marcadores y la navegación por conjuntos de registros, vea los artículos [conjunto de registros: marcadores y posiciones absolutas (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md) y [conjunto de registros: desplazamiento (ODBC)](../../data/odbc/recordset-scrolling-odbc.md).

##  <a name="setfielddirty"></a>CRecordset:: SetFieldDirty

Marca un miembro de datos de campo del conjunto de registros como modificado o como sin modificar.

```
void SetFieldDirty(void* pv, BOOL bDirty = TRUE);
```

### <a name="parameters"></a>Parámetros

*FV*<br/>
Contiene la dirección de un miembro de datos de campo en el conjunto de registros o NULL. Si es NULL, se marcan todos los miembros de datos de campo del conjunto de registros. (C++ NULL no es lo mismo que null en la terminología de bases de datos, lo que significa que "no tiene ningún valor").

*bDirty*<br/>
TRUE si el miembro de datos de campo se va a marcar como "sucio" (cambiado). De lo contrario, es FALSE si el miembro de datos de campo se va a marcar como "Clean" (sin cambios).

### <a name="remarks"></a>Comentarios

Marcar campos como sin cambios garantiza que el campo no se actualice y tenga como resultado un menor tráfico de SQL.

> [!NOTE]
>  Esta función miembro no es aplicable en los conjuntos de registros que usan la obtención masiva de filas. Si ha implementado la obtención masiva de filas, `SetFieldDirty` producirá un error en la aserción. Para obtener más información sobre la obtención masiva de filas, vea el artículo [Conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

El marco marca los miembros de datos de campo modificados para asegurarse de que se escribirán en el registro en el origen de datos mediante el mecanismo de intercambio de campos de registros (RFX). Al cambiar el valor de un campo, normalmente se establece el campo modificado automáticamente, por lo que rara vez tendrá que llamar a `SetFieldDirty` usted mismo, pero a veces querrá asegurarse de que las columnas se actualicen o inserten explícitamente, independientemente del valor que se encuentre en los datos de campo. miembro.

> [!CAUTION]
>  Llame a esta función miembro solo después de haber llamado a [Edit](#edit) o [AddNew](#addnew).

Si se usa NULL para el primer argumento de la función, solo se aplicará la función a los campos `outputColumn`, no `param` campos. Por ejemplo, la llamada

[!code-cpp[NVC_MFCDatabase#26](../../mfc/codesnippet/cpp/crecordset-class_10.cpp)]

establecerá solo `outputColumn` campos en NULL; `param` campos no se verán afectados.

Para trabajar en `param` campos, debe proporcionar la dirección real del `param` individual en el que desea trabajar, por ejemplo:

[!code-cpp[NVC_MFCDatabase#27](../../mfc/codesnippet/cpp/crecordset-class_11.cpp)]

Esto significa que no se pueden establecer todos los campos de `param` en NULL, como se puede hacer con los campos de `outputColumn`.

##  <a name="setfieldnull"></a>CRecordset:: SetFieldNull

Marca un miembro de datos de campo del conjunto de registros como null (específicamente sin ningún valor) o como no NULL.

```
void SetFieldNull(void* pv, BOOL bNull = TRUE);
```

### <a name="parameters"></a>Parámetros

*FV*<br/>
Contiene la dirección de un miembro de datos de campo en el conjunto de registros o NULL. Si es NULL, se marcan todos los miembros de datos de campo del conjunto de registros. (C++ NULL no es lo mismo que null en la terminología de bases de datos, lo que significa que "no tiene ningún valor").

*bNull*<br/>
Distinto de cero si el miembro de datos de campo se va a marcar como sin valor (NULL). De lo contrario, es 0 si el miembro de datos de campo se va a marcar como no NULL.

### <a name="remarks"></a>Comentarios

Al agregar un nuevo registro a un conjunto de registros, todos los miembros de datos de campo se establecen inicialmente en un valor NULL y se marcan como "sucio" (cambiado). Cuando se recupera un registro de un origen de datos, sus columnas ya tienen valores o son NULL.

> [!NOTE]
>  No llame a esta función miembro en conjuntos de registros que usan la obtención masiva de filas. Si ha implementado la obtención masiva de filas, al llamar a `SetFieldNull` se produce un error en una aserción. Para obtener más información sobre la obtención masiva de filas, vea el artículo [Conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Si desea designar específicamente un campo del registro actual sin un valor, llame a `SetFieldNull` con *bNull* establecido en true para marcarlo como null. Si un campo se marcó previamente como NULL y ahora desea darle un valor, simplemente establezca su nuevo valor. No es necesario quitar la marca nula con `SetFieldNull`. Para determinar si el campo puede ser null, llame a `IsFieldNullable`.

> [!CAUTION]
>  Llame a esta función miembro solo después de haber llamado a [Edit](#edit) o [AddNew](#addnew).

Si se usa NULL para el primer argumento de la función, solo se aplicará la función a los campos `outputColumn`, no `param` campos. Por ejemplo, la llamada

[!code-cpp[NVC_MFCDatabase#26](../../mfc/codesnippet/cpp/crecordset-class_10.cpp)]

establecerá solo `outputColumn` campos en NULL; `param` campos no se verán afectados.

Para trabajar en `param` campos, debe proporcionar la dirección real del `param` individual en el que desea trabajar, por ejemplo:

[!code-cpp[NVC_MFCDatabase#27](../../mfc/codesnippet/cpp/crecordset-class_11.cpp)]

Esto significa que no se pueden establecer todos los campos de `param` en NULL, como se puede hacer con los campos de `outputColumn`.

> [!NOTE]
>  Al establecer los parámetros en null, una llamada a `SetFieldNull` antes de que se abra el conjunto de registros genera una aserción. En este caso, llame a [SetParamNull](#setparamnull).

`SetFieldNull` se implementa a través de [DoFieldExchange](#dofieldexchange).

##  <a name="setlockingmode"></a>CRecordset:: SetLockingMode

Establece el modo de bloqueo en bloqueo "optimista" (valor predeterminado) o "pesimista". Determina cómo se bloquean las actualizaciones de los registros.

```
void SetLockingMode(UINT nMode);
```

### <a name="parameters"></a>Parámetros

*nMode*<br/>
Contiene uno de los valores siguientes de la `enum LockMode`:

- `optimistic` bloqueo optimista bloquea el registro que se está actualizando solo durante la llamada a `Update`.

- `pessimistic` el bloqueo pesimista bloquea el registro en cuanto se llama a `Edit` y lo mantiene bloqueado hasta que se completa la llamada a `Update` o se mueve a un nuevo registro.

### <a name="remarks"></a>Comentarios

Llame a esta función miembro si necesita especificar cuál de las dos estrategias de bloqueo de registros utiliza el conjunto de registros para las actualizaciones. De forma predeterminada, el modo de bloqueo de un conjunto de registros es `optimistic`. Puede cambiarlo a una estrategia de bloqueo `pessimistic` más cuidadosa. Llame a `SetLockingMode` después de construir y abrir el objeto de conjunto de registros, pero antes de llamar a `Edit`.

##  <a name="setparamnull"></a>CRecordset:: SetParamNull

Marca un parámetro como null (específicamente sin valor) o como no NULL.

```
void SetParamNull(
    int nIndex,
    BOOL bNull = TRUE);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Índice de base cero del parámetro.

*bNull*<br/>
Si es TRUE (valor predeterminado), el parámetro se marca como null. De lo contrario, el parámetro se marca como no NULL.

### <a name="remarks"></a>Comentarios

A diferencia de [SetFieldNull](#setfieldnull), puede llamar a `SetParamNull` antes de abrir el conjunto de registros.

Normalmente, `SetParamNull` se utiliza con consultas predefinidas (procedimientos almacenados).

##  <a name="setrowsetcursorposition"></a>CRecordset:: SetRowsetCursorPosition

Mueve el cursor a una fila del conjunto de filas actual.

```
void SetRowsetCursorPosition(WORD wRow, WORD wLockType = SQL_LOCK_NO_CHANGE);
```

### <a name="parameters"></a>Parámetros

*wRow*<br/>
La posición basada en uno de una fila en el conjunto de filas actual. Este valor puede oscilar entre 1 y el tamaño del conjunto de filas.

*wLockType*<br/>
Valor que indica cómo bloquear la fila una vez que se ha actualizado. Para conocer más detalles, vea la sección Comentarios.

### <a name="remarks"></a>Comentarios

Al implementar la obtención masiva de filas, los registros se recuperan mediante conjuntos de filas, donde el primer registro del conjunto de filas capturado es el registro actual. Para hacer que otro registro del conjunto de filas sea el registro actual, llame a `SetRowsetCursorPosition`. Por ejemplo, puede combinar `SetRowsetCursorPosition` con la función miembro [GetFieldValue](#getfieldvalue) para recuperar dinámicamente los datos de cualquier registro del conjunto de registros.

Para usar `SetRowsetCursorPosition`, debe haber implementado la obtención masiva de filas especificando la opción `CRecordset::useMultiRowFetch` del parámetro *dwOptions* en la función miembro [abierta](#open) .

`SetRowsetCursorPosition` llama a la función de la API de ODBC `SQLSetPos`. El parámetro *wLockType* especifica el estado de bloqueo de la fila después de que se haya ejecutado `SQLSetPos`. En la tabla siguiente se describen los posibles valores para *wLockType*.

|wLockType|Descripción|
|---------------|-----------------|
|SQL_LOCK_NO_CHANGE (valor predeterminado)|El controlador o el origen de datos garantiza que la fila se encuentra en el mismo estado bloqueado o desbloqueado que tenía antes de que se llamara a `SetRowsetCursorPosition`.|
|SQL_LOCK_EXCLUSIVE|El controlador o el origen de datos bloquea la fila exclusivamente. No todos los orígenes de datos admiten este tipo de bloqueo.|
|SQL_LOCK_UNLOCK|El controlador o el origen de datos desbloquea la fila. No todos los orígenes de datos admiten este tipo de bloqueo.|

Para obtener más información acerca de `SQLSetPos`, vea el Windows SDK. Para obtener más información sobre la obtención masiva de filas, vea el artículo [Conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

##  <a name="setrowsetsize"></a>CRecordset:: SetRowsetSize

Especifica el número de registros que se van a recuperar durante una captura.

```
virtual void SetRowsetSize(DWORD dwNewRowsetSize);
```

### <a name="parameters"></a>Parámetros

*dwNewRowsetSize*<br/>
Número de filas que se van a recuperar durante una captura determinada.

### <a name="remarks"></a>Comentarios

Esta función miembro virtual especifica el número de filas que se van a recuperar durante una captura única cuando se usa la obtención masiva de filas. Para implementar la obtención masiva de filas, debe establecer la opción `CRecordset::useMultiRowFetch` en el parámetro *dwOptions* de la función miembro [abierta](#open) .

> [!NOTE]
>  La llamada a `SetRowsetSize` sin implementar la obtención masiva de filas producirá un error de aserción.

Llame a `SetRowsetSize` antes de llamar a `Open` para establecer inicialmente el tamaño del conjunto de filas para el conjunto de registros. El tamaño del conjunto de filas predeterminado al implementar la obtención masiva de filas es 25.

> [!NOTE]
>  Tenga cuidado al llamar a `SetRowsetSize`. Si va a asignar manualmente el almacenamiento para los datos (tal y como se especifica en la opción `CRecordset::userAllocMultiRowBuffers` del parámetro dwOptions en `Open`), debe comprobar si necesita reasignar estos búferes de almacenamiento después de llamar a `SetRowsetSize`, pero antes de realizar cualquier cursor operación de navegación.

Para obtener la configuración actual del tamaño del conjunto de filas, llame a [GetRowsetSize](#getrowsetsize).

Para obtener más información sobre la obtención masiva de filas, vea el artículo [Conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

##  <a name="update"></a>CRecordset:: Update

Completa una operación de `AddNew` o `Edit` guardando los datos nuevos o editados en el origen de datos.

```
virtual BOOL Update();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si un registro se actualizó correctamente; de lo contrario, 0 si no hay ninguna columna modificada. Si no se actualizó ningún registro o si se actualizó más de un registro, se produce una excepción. También se produce una excepción para cualquier otro error en el origen de datos.

### <a name="remarks"></a>Comentarios

Llame a esta función miembro después de una llamada a la función de miembro [AddNew](#addnew) o [Edit](#edit) . Esta llamada es necesaria para completar la operación `AddNew` o `Edit`.

> [!NOTE]
>  Si ha implementado la obtención masiva de filas, no puede llamar a `Update`. Esto producirá un error de aserción. Aunque la clase `CRecordset` no proporciona un mecanismo para actualizar filas de datos masivas, puede escribir sus propias funciones mediante la función de la API de ODBC `SQLSetPos`. Para obtener más información sobre la obtención masiva de filas, vea el artículo [Conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Tanto `AddNew` como `Edit` preparan un búfer de edición en el que se colocan los datos agregados o editados para guardarlos en el origen de datos. `Update` guarda los datos. Solo se actualizan los campos marcados o detectados como modificados.

Si el origen de datos admite transacciones, puede hacer que la llamada de `Update` (y su correspondiente `AddNew` o llamada a `Edit`) forme parte de una transacción. Para obtener más información acerca de las transacciones, vea el artículo [transacción (ODBC)](../../data/odbc/transaction-odbc.md).

> [!CAUTION]
>  Si llama a `Update` sin llamar primero a `AddNew` o `Edit`, `Update` produce una `CDBException`. Si llama a `AddNew` o `Edit`, debe llamar a `Update` antes de llamar a una operación de `Move` o antes de cerrar el conjunto de registros o la conexión a un origen de datos. De lo contrario, los cambios se perderán sin notificación.

Para obtener más información sobre cómo controlar los errores de `Update`, vea el artículo conjunto de registros [: Cómo actualizar los registros (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md).

### <a name="example"></a>Ejemplo

Vea el artículo [transacción: realizar una transacción en un conjunto de registros (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md).

## <a name="see-also"></a>Vea también

[CObject (clase)](../../mfc/reference/cobject-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CDatabase (clase)](../../mfc/reference/cdatabase-class.md)<br/>
[CRecordView (clase)](../../mfc/reference/crecordview-class.md)
