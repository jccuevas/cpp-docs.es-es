---
title: Clase CRecordset
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
ms.openlocfilehash: ab6cde9f478dc6f2e3cb0ba5bb338a3852f083fd
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81750504"
---
# <a name="crecordset-class"></a>Clase CRecordset

Representa un conjunto de registros seleccionados de un origen de datos.

## <a name="syntax"></a>Sintaxis

```
class CRecordset : public CObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CRecordset::CRecordset](#crecordset)|Construye un objeto `CRecordset`. La clase derivada debe proporcionar un constructor que llame a este.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CRecordset::AddNew](#addnew)|Se prepara para agregar un nuevo registro. Llame `Update` para completar la adición.|
|[CRecordset::CanAppend](#canappend)|Devuelve distinto de cero si se pueden `AddNew` agregar nuevos registros al conjunto de registros a través de la función miembro.|
|[CRecordset::CanBookmark](#canbookmark)|Devuelve distinto de cero si el conjunto de registros admite marcadores.|
|[CRecordset::Cancelar](#cancel)|Cancela una operación asincrónica o un proceso desde un segundo subproceso.|
|[CRecordset::CancelUpdate](#cancelupdate)|Cancela las actualizaciones pendientes debido a una operación `AddNew` o `Edit` a una operación.|
|[CRecordset::CanRestart](#canrestart)|Devuelve distinto `Requery` de cero si se puede llamar para volver a ejecutar la consulta del conjunto de registros.|
|[CRecordset::CanScroll](#canscroll)|Devuelve distinto de cero si puede desplazarse por los registros.|
|[CRecordset::CanTransact](#cantransact)|Devuelve distinto de cero si el origen de datos admite transacciones.|
|[CRecordset::CanUpdate](#canupdate)|Devuelve distinto de cero si se puede actualizar el conjunto de registros (puede agregar, actualizar o eliminar registros).|
|[CRecordset::CheckRowsetError](#checkrowseterror)|Se llama para controlar los errores generados durante la obtención de registros.|
|[CRecordset::Cerrar](#close)|Cierra el conjunto de registros y el ODBC HSTMT asociado a él.|
|[CRecordset::Delete](#delete)|Elimina el registro actual del conjunto de registros. Debe desplazarse explícitamente a otro registro después de la eliminación.|
|[CRecordset::DoBulkFieldExchange](#dobulkfieldexchange)|Se llama para intercambiar filas masivas de datos desde el origen de datos al conjunto de registros. Implementa el intercambio de campos de registros masivos (RFX masivo).|
|[CRecordset::DoFieldExchange](#dofieldexchange)|Se llama para intercambiar datos (en ambas direcciones) entre los miembros de datos de campo del conjunto de registros y el registro correspondiente en el origen de datos. Implementa el intercambio de campos de registros (RFX).|
|[CRecordset::Editar](#edit)|Se prepara para los cambios en el registro actual. Llame `Update` para completar la edición.|
|[CRecordset::FlushResultSet](#flushresultset)|Devuelve distinto de cero si hay otro conjunto de resultados que se va a recuperar, cuando se usa una consulta predefinida.|
|[CRecordset::GetBookmark](#getbookmark)|Asigna el valor de marcador de un registro al objeto de parámetro.|
|[CRecordset::GetDefaultConnect](#getdefaultconnect)|Se llama para obtener la cadena de conexión predeterminada.|
|[CRecordset::GetDefaultSQL](#getdefaultsql)|Se llama para obtener la cadena SQL predeterminada que se va a ejecutar.|
|[CRecordset::GetFieldValue](#getfieldvalue)|Devuelve el valor de un campo de un conjunto de registros.|
|[CRecordset::GetODBCFieldCount](#getodbcfieldcount)|Devuelve el número de campos del conjunto de registros.|
|[CRecordset::GetODBCFieldInfo](#getodbcfieldinfo)|Devuelve tipos específicos de información sobre los campos de un conjunto de registros.|
|[CRecordset::GetRecordCount](#getrecordcount)|Devuelve el número de registros del conjunto de registros.|
|[CRecordset::GetRowsetSize](#getrowsetsize)|Devuelve el número de registros que desea recuperar durante una sola captura.|
|[CRecordset::GetRowsFetched](#getrowsfetched)|Devuelve el número real de filas recuperadas durante una captura.|
|[CRecordset::GetRowStatus](#getrowstatus)|Devuelve el estado de la fila después de una captura.|
|[CRecordset::GetSQL](#getsql)|Obtiene la cadena SQL utilizada para seleccionar registros para el conjunto de registros.|
|[CRecordset::GetStatus](#getstatus)|Obtiene el estado del conjunto de registros: el índice del registro actual y si se ha obtenido un recuento final de los registros.|
|[CRecordset::GetTableName](#gettablename)|Obtiene el nombre de la tabla en la que se basa el conjunto de registros.|
|[CRecordset::IsBOF](#isbof)|Devuelve distinto de cero si el conjunto de registros se ha colocado antes del primer registro. No hay ningún registro actual.|
|[CRecordset::IsDeleted](#isdeleted)|Devuelve distinto de cero si el conjunto de registros se coloca en un registro eliminado.|
|[CRecordset::IsEOF](#iseof)|Devuelve distinto de cero si el conjunto de registros se ha colocado después del último registro. No hay ningún registro actual.|
|[CRecordset::IsFieldDirty](#isfielddirty)|Devuelve distinto de cero si se ha cambiado el campo especificado en el registro actual.|
|[CRecordset::IsFieldNull](#isfieldnull)|Devuelve distinto de cero si el campo especificado en el registro actual es null (no tiene ningún valor).|
|[CRecordset::IsFieldNullable](#isfieldnullable)|Devuelve distinto de cero si el campo especificado en el registro actual se puede establecer en null (no tiene ningún valor).|
|[CRecordset::IsOpen](#isopen)|Devuelve distinto `Open` de cero si se ha llamado anteriormente.|
|[CRecordset::Move](#move)|Coloca el conjunto de registros en un número especificado de registros del registro actual en cualquier dirección.|
|[CRecordset::MoveFirst](#movefirst)|Coloca el registro actual en el primer registro del conjunto de registros. Prueba `IsBOF` para primero.|
|[CRecordset::MoveLast](#movelast)|Coloca el registro actual en el último registro o en el último conjunto de filas. Prueba `IsEOF` para primero.|
|[CRecordset::MoveNext](#movenext)|Coloca el registro actual en el siguiente registro o en el siguiente conjunto de filas. Prueba `IsEOF` para primero.|
|[CRecordset::MovePrev](#moveprev)|Coloca el registro actual en el registro anterior o en el conjunto de filas anterior. Prueba `IsBOF` para primero.|
|[CRecordset::OnSetOptions](#onsetoptions)|Se llama para establecer opciones (utilizadas en la selección) para la instrucción ODBC especificada.|
|[CRecordset::OnSetUpdateOptions](#onsetupdateoptions)|Se llama para establecer opciones (utilizadas en la actualización) para la instrucción ODBC especificada.|
|[CRecordset::Open](#open)|Abre el conjunto de registros recuperando la tabla o realizando la consulta que el conjunto de registros representa.|
|[CRecordset::RefreshRowset](#refreshrowset)|Actualiza los datos y el estado de las filas especificadas.|
|[CRecordset::Requery](#requery)|Vuelve a ejecutar la consulta del conjunto de registros para actualizar los registros seleccionados.|
|[CRecordset::SetAbsolutePosition](#setabsoluteposition)|Coloca el conjunto de registros en el registro correspondiente al número de registro especificado.|
|[CRecordset::SetBookmark](#setbookmark)|Coloca el conjunto de registros en el registro especificado por el marcador.|
|[CRecordset::SetFieldDirty](#setfielddirty)|Marca el campo especificado en el registro actual como modificado.|
|[CRecordset::SetFieldNull](#setfieldnull)|Establece el valor del campo especificado en el registro actual en null (sin valor).|
|[CRecordset::SetLockingMode](#setlockingmode)|Establece el modo de bloqueo en bloqueo "optimista" (valor predeterminado) o bloqueo "pesimista". Determina cómo se bloquean los registros para las actualizaciones.|
|[CRecordset::SetParamNull](#setparamnull)|Establece el parámetro especificado en null (sin valor).|
|[CRecordset::SetRowsetCursorPosition](#setrowsetcursorposition)|Coloca el cursor en la fila especificada dentro del conjunto de filas.|
|[CRecordset::SetRowsetSize](#setrowsetsize)|Especifica el número de registros que desea recuperar durante una captura.|
|[CRecordset::Update](#update)|Completa una `AddNew` `Edit` operación mediante la guardaguarda de los datos nuevos o editados en el origen de datos.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CRecordset::m_hstmt](#m_hstmt)|Contiene el identificador de instrucción ODBC para el conjunto de registros. Escriba `HSTMT`.|
|[CRecordset::m_nFields](#m_nfields)|Contiene el número de miembros de datos de campo en el conjunto de registros. Escriba `UINT`.|
|[CRecordset::m_nParams](#m_nparams)|Contiene el número de miembros de datos de parámetro en el conjunto de registros. Escriba `UINT`.|
|[CRecordset::m_pDatabase](#m_pdatabase)|Contiene un puntero `CDatabase` al objeto a través del cual el conjunto de registros está conectado a un origen de datos.|
|[CRecordset::m_strFilter](#m_strfilter)|Contiene `CString` a que especifica una `WHERE` cláusula de lenguaje de consulta estructurado (SQL). Se utiliza como filtro para seleccionar solo los registros que cumplen determinados criterios.|
|[CRecordset::m_strSort](#m_strsort)|Contiene `CString` a que especifica `ORDER BY` una cláusula SQL. Se utiliza para controlar cómo se ordenan los registros.|

## <a name="remarks"></a>Comentarios para <a name="remarks"></a>

Conocidos como "recordsets", `CRecordset` los objetos se usan normalmente en dos formas: conjuntos de registros dinámicos e instantáneas. Un conjunto dinámico permanece sincronizado con las actualizaciones de datos realizadas por otros usuarios. Una instantánea es una vista estática de los datos. Cada formulario representa un conjunto de registros fijos en el momento en que se abre el conjunto de registros, pero cuando se desplaza a un registro en un conjunto de registros dinámicos, refleja los cambios realizados posteriormente en el registro, ya sea por otros usuarios o por otros conjuntos de registros en la aplicación.

> [!NOTE]
> Si está trabajando con las clases de objetos de acceso a datos (DAO) en lugar de las clases de conectividad de base de datos abierta (ODBC), utilice la clase [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) en su lugar. Para obtener más información, consulte el artículo [Información general: Programación](../../data/data-access-programming-mfc-atl.md)de bases de datos .

Para trabajar con cualquier tipo de conjunto de registros, `CRecordset`normalmente se deriva una clase de conjunto de registros específica de la aplicación de . Los conjuntos de registros seleccionan registros de un origen de datos y, a continuación, puede:

- Desplácese por los registros.

- Actualice los registros y especifique un modo de bloqueo.

- Filtre el conjunto de registros para restringir los registros que selecciona de los disponibles en el origen de datos.

- Ordene el conjunto de registros.

- Parametrizar el conjunto de registros para personalizar su selección con información no conocida hasta el tiempo de ejecución.

Para usar la clase, abra una base de datos y `CDatabase` construya un objeto de conjunto de registros, pasando el constructor un puntero al objeto. A continuación, llame `Open` a la función miembro del conjunto de registros, donde puede especificar si el objeto es un conjunto de registros dinámicos o una instantánea. Al `Open` llamar, se seleccionan los datos del origen de datos. Después de abrir el objeto de conjunto de registros, utilice sus funciones miembro y miembros de datos para desplazarse por los registros y operar en ellos. Las operaciones disponibles dependen de si el objeto es un conjunto de registros dinámicos o una instantánea, si es actualizable o de solo lectura (esto depende de la capacidad del origen de datos de conectividad abierta de base de datos (ODBC)) y si ha implementado la obtención masiva de filas. Para actualizar los registros que se `Open` pueden haber cambiado `Requery` o agregado desde la llamada, llame a la función miembro del objeto. Llame a la `Close` función miembro del objeto y destruya el objeto cuando termine con él.

En una `CRecordset` clase derivada, el intercambio de campos de registros (RFX) o el intercambio masivo de campos de registros (RFX masivo) se utilizan para admitir la lectura y actualización de campos de registro.

Para obtener más información acerca de los conjuntos de registros y el intercambio de campos de registros, vea los artículos [Información general: Programación](../../data/data-access-programming-mfc-atl.md)de bases de datos , Conjunto de [registros (ODBC)](../../data/odbc/recordset-odbc.md), [Conjunto de registros: Obtención de registros en masa (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)y Intercambio de campos de registros [(RFX).](../../data/odbc/record-field-exchange-rfx.md) Para obtener un enfoque en conjuntos de registros dinámicos e instantáneas, consulte los artículos [Dynaset](../../data/odbc/dynaset.md) e [Snapshot](../../data/odbc/snapshot.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

`CRecordset`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdb.h

## <a name="crecordsetaddnew"></a><a name="addnew"></a>CRecordset::AddNew

Se prepara para agregar un nuevo registro a la tabla.

```
virtual void AddNew();
```

### <a name="remarks"></a>Observaciones

Debe llamar a la [Requery](#requery) función miembro para ver el registro recién agregado. Los campos del registro son inicialmente Null. (En terminología de base de datos, Null significa "no tener ningún valor" y no es lo mismo que NULL en C++.) Para completar la operación, debe llamar a la [Update](#update) función miembro. `Update`guarda los cambios en el origen de datos.

> [!NOTE]
> Si ha implementado la obtención masiva `AddNew`de filas, no puede llamar a . Esto dará lugar a una aserción con errores. Aunque `CRecordset` la clase no proporciona un mecanismo para actualizar filas masivas de datos, puede escribir sus propias funciones mediante la función `SQLSetPos`de API ODBC . Para obtener más información sobre la obtención masiva de filas, vea el artículo [Conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

`AddNew`prepara un nuevo registro vacío utilizando los miembros de datos de campo del conjunto de registros. Después `AddNew`de llamar , establezca los valores que desee en los miembros de datos de campo del conjunto de registros. (No es necesario llamar a la [Edit](#edit) función miembro para este propósito; uso `Edit` solo para registros existentes.) Cuando se llama `Update`posteriormente, los valores modificados en los miembros de datos de campo se guardan en el origen de datos.

> [!CAUTION]
> Si se desplaza a un `Update`nuevo registro antes de llamar , se pierde el nuevo registro y no se proporciona ninguna advertencia.

Si el origen de datos admite `AddNew` transacciones, puede hacer que la llamada forme parte de una transacción. Para obtener más información acerca de las transacciones, vea la clase [CDatabase](../../mfc/reference/cdatabase-class.md). Tenga en cuenta que debe llamar a `AddNew` [CDatabase::BeginTrans](../../mfc/reference/cdatabase-class.md#begintrans) antes de llamar a .

> [!NOTE]
> Para los conjuntos de registros dinámicos, se agregan nuevos registros al conjunto de registros como el último registro. Los registros agregados no se agregan a las instantáneas; debe llamar `Requery` para actualizar el conjunto de registros.

Es ilegal llamar `AddNew` a un `Open` conjunto de registros cuya función miembro no se ha llamado. A `CDBException` se produce si `AddNew` se llama a un conjunto de registros al que no se puede anexar. Puede determinar si el conjunto de registros es actualizable llamando a [CanAppend](#canappend).

Para obtener más información, vea los artículos siguientes: Conjunto de registros: Cómo los conjuntos de registros actualizan [registros (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md), [Conjunto de registros: agregar, actualizar y eliminar registros (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)y [transacción (ODBC)](../../data/odbc/transaction-odbc.md).

### <a name="example"></a>Ejemplo

Consulte el artículo [Transacción: realizar una transacción en un conjunto de registros (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md).

## <a name="crecordsetcanappend"></a><a name="canappend"></a>CRecordset::CanAppend

Determina si el conjunto de registros abierto anteriormente le permite agregar nuevos registros.

```
BOOL CanAppend() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el conjunto de registros permite agregar nuevos registros; de lo contrario 0. `CanAppend`devolverá 0 si abrió el conjunto de registros como de solo lectura.

## <a name="crecordsetcanbookmark"></a><a name="canbookmark"></a>CRecordset::CanBookmark

Determina si el conjunto de registros permite marcar registros mediante marcadores.

```
BOOL CanBookmark() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el conjunto de registros admite marcadores; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Esta función es `CRecordset::useBookmarks` independiente de la opción en el *dwOptions* parámetro de la [Open](#open) función miembro. `CanBookmark`indica si el controlador ODBC determinado y el tipo de cursor admiten marcadores. `CRecordset::useBookmarks`indica si los marcadores estarán disponibles, siempre que sean compatibles.

> [!NOTE]
> Los marcadores no se admiten en conjuntos de registros de solo avance.

Para obtener más información acerca de los marcadores y la navegación de conjuntos de registros, vea los artículos Conjunto de [registros: marcadores y posiciones absolutas (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md) y [Conjunto de registros: desplazamiento (ODBC)](../../data/odbc/recordset-scrolling-odbc.md).

## <a name="crecordsetcancel"></a><a name="cancel"></a>CRecordset::Cancelar

Solicita que el origen de datos cancele una operación asincrónica en curso o un proceso de un segundo subproceso.

```cpp
void Cancel();
```

### <a name="remarks"></a>Observaciones

Tenga en cuenta que las clases ODBC de MFC ya no utilizan el procesamiento asincrónico; para realizar una operación asincrona, debe `SQLSetConnectOption`llamar directamente a la función de API ODBC . Para obtener más información, consulte el tema "Ejecutar funciones de forma asincrónica" en la *Guía del programador del SDK*de ODBC .

## <a name="crecordsetcancelupdate"></a><a name="cancelupdate"></a>CRecordset::CancelUpdate

Cancela las actualizaciones pendientes, causadas por una operación [Edit](#edit) o [AddNew,](#addnew) antes de llamar a [Update.](#update)

```cpp
void CancelUpdate();
```

### <a name="remarks"></a>Observaciones

> [!NOTE]
> Esta función miembro no es aplicable en conjuntos de registros `Edit`que `AddNew`utilizan `Update`la obtención masiva de filas, ya que dichos conjuntos de registros no pueden llamar a , , o . Para obtener más información sobre la obtención masiva de filas, vea el artículo [Conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Si la comprobación automática de `CancelUpdate` campos sucios está habilitada, restaurará las variables miembro a los valores que tenían antes `Edit` o `AddNew` se llamó; de lo contrario, los cambios de valor permanecerán. De forma predeterminada, la comprobación automática de campos está habilitada cuando se abre el conjunto de registros. Para deshabilitarlo, debe `CRecordset::noDirtyFieldCheck` especificar el en el *dwOptions* parámetro de la [Open](#open) función miembro.

Para obtener más información acerca de la actualización de datos, vea el artículo [Conjunto de registros: agregar, actualizar y eliminar registros (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md).

## <a name="crecordsetcanrestart"></a><a name="canrestart"></a>CRecordset::CanRestart

Determina si el conjunto de registros permite reiniciar su `Requery` consulta (para actualizar sus registros) mediante una llamada a la función miembro.

```
BOOL CanRestart() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se permite la reconsulta; de lo contrario 0.

## <a name="crecordsetcanscroll"></a><a name="canscroll"></a>CRecordset::CanScroll

Determina si el conjunto de registros permite el desplazamiento.

```
BOOL CanScroll() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el conjunto de registros permite el desplazamiento; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Para obtener más información sobre el desplazamiento, vea el artículo [Conjunto de registros: desplazamiento (ODBC)](../../data/odbc/recordset-scrolling-odbc.md).

## <a name="crecordsetcantransact"></a><a name="cantransact"></a>CRecordset::CanTransact

Determina si el conjunto de registros permite transacciones.

```
BOOL CanTransact() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el conjunto de registros permite transacciones; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Para obtener más información, vea el artículo [Transacción (ODBC)](../../data/odbc/transaction-odbc.md).

## <a name="crecordsetcanupdate"></a><a name="canupdate"></a>CRecordset::CanUpdate

Determina si se puede actualizar el conjunto de registros.

```
BOOL CanUpdate() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el conjunto de registros se puede actualizar; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Un conjunto de registros puede ser de solo lectura si el `CRecordset::readOnly` origen de datos subyacente es de solo lectura o si especificó en el parámetro *dwOptions* al abrir el conjunto de registros.

## <a name="crecordsetcheckrowseterror"></a><a name="checkrowseterror"></a>CRecordset::CheckRowsetError

Se llama para controlar los errores generados durante la obtención de registros.

```
virtual void CheckRowsetError(RETCODE nRetCode);
```

### <a name="parameters"></a>Parámetros

*nRetCode*<br/>
Una función de API ODBC código de retorno. Para conocer más detalles, vea la sección Comentarios.

### <a name="remarks"></a>Observaciones

Esta función miembro virtual controla los errores que se producen cuando se recuperan registros y es útil durante la obtención masiva de filas. Es posible que desee considerar la invalidación `CheckRowsetError` para implementar su propio control de errores.

`CheckRowsetError`se llama automáticamente en una operación `Requery`de `Move` navegación del cursor, como `Open`, , o cualquier operación. Se pasa el valor devuelto de `SQLExtendedFetch`la función de API ODBC. En la tabla siguiente se enumeran los valores posibles para el *nRetCode* parámetro.

|nRetCode|Descripción|
|--------------|-----------------|
|SQL_SUCCESS|Función completada con éxito; no hay información adicional disponible.|
|SQL_SUCCESS_WITH_INFO|Función completada correctamente, posiblemente con un error no fatal. Se puede obtener información `SQLError`adicional llamando a .|
|SQL_NO_DATA_FOUND|Se han capturado todas las filas del conjunto de resultados.|
|SQL_ERROR|Error en la función. Se puede obtener información `SQLError`adicional llamando a .|
|SQL_INVALID_HANDLE|Error en la función debido a un identificador de entorno no válido, identificador de conexión o identificador de instrucción. Esto indica un error de programación. No hay información `SQLError`adicional disponible en .|
|SQL_STILL_EXECUTING|Una función que se inició de forma asincrónica todavía se está ejecutando. Tenga en cuenta que, de forma `CheckRowsetError`predeterminada, MFC nunca pasará este valor a ; MFC seguirá `SQLExtendedFetch` llamando hasta que ya no vuelva SQL_STILL_EXECUTING.|

Para obtener `SQLError`más información acerca de , consulte el Windows SDK. Para obtener más información sobre la obtención masiva de filas, vea el artículo [Conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

## <a name="crecordsetclose"></a><a name="close"></a>CRecordset::Cerrar

Cierra el conjunto de registros.

```
virtual void Close();
```

### <a name="remarks"></a>Observaciones

El ODBC HSTMT y toda la memoria del marco asignado para el conjunto de registros se desasignan. Normalmente, `Close`después de llamar , se elimina el objeto de conjunto de registros C++ si se asignó con **new**.

Puede volver `Open` a `Close`llamar después de llamar. Esto le permite reutilizar el objeto de conjunto de registros. La alternativa es `Requery`llamar a .

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDatabase#17](../../mfc/codesnippet/cpp/crecordset-class_1.cpp)]

## <a name="crecordsetcrecordset"></a><a name="crecordset"></a>CRecordset::CRecordset

Construye un objeto `CRecordset`.

```
CRecordset(CDatabase* pDatabase = NULL);
```

### <a name="parameters"></a>Parámetros

*pBase de datos*<br/>
Contiene un puntero `CDatabase` a un objeto o el valor NULL. Si no NULL `CDatabase` y `Open` la función miembro del objeto no se ha llamado para conectarlo al `Open` origen de datos, el conjunto de registros intenta abrirlo durante su propia llamada. Si pasa NULL, `CDatabase` se construye y se conecta un objeto mediante la información del origen de datos que especificó al derivar la clase de conjunto de registros con ClassWizard.

### <a name="remarks"></a>Observaciones

Puede utilizar `CRecordset` directamente o derivar una `CRecordset`clase específica de la aplicación de . Puede usar ClassWizard para derivar las clases de conjunto de registros.

> [!NOTE]
> Una clase derivada *debe* proporcionar su propio constructor. En el constructor de la clase `CRecordset::CRecordset`derivada, llame al constructor , pasándole los parámetros adecuados.

Pase NULL al constructor del `CDatabase` conjunto de registros para que un objeto se construya y se conecte automáticamente. Se trata de una abreviatura útil que no `CDatabase` requiere que se construya y conecte un objeto antes de construir el conjunto de registros.

### <a name="example"></a>Ejemplo

Para obtener más información, vea el artículo [Conjunto de registros: declarar una clase para una tabla (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md).

## <a name="crecordsetdelete"></a><a name="delete"></a>CRecordset::Delete

Elimina el registro actual.

```
virtual void Delete();
```

### <a name="remarks"></a>Observaciones

Después de una eliminación correcta, los miembros de datos de campo del `Move` conjunto de registros se establecen en un valor Null y debe llamar explícitamente a una de las funciones para salir del registro eliminado. Una vez que se mueve fuera del registro eliminado, no es posible volver a él. Si el origen de datos admite `Delete` transacciones, puede hacer que la llamada forme parte de una transacción. Para obtener más información, vea el artículo [Transacción (ODBC)](../../data/odbc/transaction-odbc.md).

> [!NOTE]
> Si ha implementado la obtención masiva `Delete`de filas, no puede llamar a . Esto dará lugar a una aserción con errores. Aunque `CRecordset` la clase no proporciona un mecanismo para actualizar filas masivas de datos, puede escribir sus propias funciones mediante la función `SQLSetPos`de API ODBC . Para obtener más información sobre la obtención masiva de filas, vea el artículo [Conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

> [!CAUTION]
> El conjunto de registros debe ser actualizable y debe haber `Delete`un registro válido actual en el conjunto de registros cuando se llama a ; de lo contrario, se produce un error. Por ejemplo, si elimina un registro pero no se `Delete` desplaza `Delete` a un nuevo registro antes de llamar de nuevo, inicia una [excepción CDBException](../../mfc/reference/cdbexception-class.md).

A diferencia de [AddNew](#addnew) `Delete` y [Edit](#edit), una llamada no va seguida de una llamada a [Update](#update). Si `Delete` se produce un error en una llamada, los miembros de datos de campo se quedan sin cambios.

### <a name="example"></a>Ejemplo

En este ejemplo se muestra un conjunto de registros creado en el marco de una función. En el ejemplo se `m_dbCust`supone la existencia `CDatabase` de , una variable miembro de tipo ya conectada al origen de datos.

[!code-cpp[NVC_MFCDatabase#18](../../mfc/codesnippet/cpp/crecordset-class_2.cpp)]

## <a name="crecordsetdobulkfieldexchange"></a><a name="dobulkfieldexchange"></a>CRecordset::DoBulkFieldExchange

Se llama para intercambiar filas masivas de datos desde el origen de datos al conjunto de registros. Implementa el intercambio de campos de registros masivos (RFX masivo).

```
virtual void DoBulkFieldExchange(CFieldExchange* pFX);
```

### <a name="parameters"></a>Parámetros

*Pfx*<br/>
Un puntero a un [CFieldExchange](../../mfc/reference/cfieldexchange-class.md) objeto. El marco de trabajo ya habrá configurado este objeto para especificar un contexto para la operación de intercambio de campos.

### <a name="remarks"></a>Observaciones

Cuando se implementa la obtención masiva de filas, el marco de trabajo llama a esta función miembro para transferir automáticamente datos desde el origen de datos al objeto de conjunto de registros. `DoBulkFieldExchange`También enlaza los miembros de datos de parámetro, si los hay, a marcadores de posición de parámetro en la cadena de instrucción SQL para la selección del conjunto de registros.

Si no se implementa la obtención masiva de filas, el marco de trabajo llama a [DoFieldExchange](#dofieldexchange). Para implementar la obtención masiva `CRecordset::useMultiRowFetch` de filas, debe especificar la opción del parámetro *dwOptions* en la función miembro [Open.](#open)

> [!NOTE]
> `DoBulkFieldExchange`solo está disponible si está utilizando `CRecordset`una clase derivada de . Si ha creado un objeto `CRecordset`de conjunto de registros directamente desde , debe llamar a la [GetFieldValue](#getfieldvalue) función miembro para recuperar datos.

El intercambio masivo de campos de registros (RFX masivo) es similar al intercambio de campos de registros (RFX). Los datos se transfieren automáticamente desde el origen de datos al objeto de conjunto de registros. Sin embargo, `AddNew` `Edit`no `Delete`puede `Update` llamar a , , , o para transferir los cambios al origen de datos. La `CRecordset` clase actualmente no proporciona un mecanismo para actualizar filas masivas de datos; sin embargo, puede escribir sus propias `SQLSetPos`funciones mediante la función de API ODBC.

Tenga en cuenta que ClassWizard no admite el intercambio de campos de registros masivos; por lo tanto, debe invalidar `DoBulkFieldExchange` manualmente escribiendo llamadas a las funciones RFX masivas. Para obtener más información acerca de estas funciones, vea el tema [Funciones](../../mfc/reference/record-field-exchange-functions.md)de intercambio de campos de registro .

Para obtener más información sobre la obtención masiva de filas, vea el artículo [Conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md). Para obtener información relacionada, vea el artículo Intercambio de campos de [registros (RFX)](../../data/odbc/record-field-exchange-rfx.md).

## <a name="crecordsetdofieldexchange"></a><a name="dofieldexchange"></a>CRecordset::DoFieldExchange

Se llama para intercambiar datos (en ambas direcciones) entre los miembros de datos de campo del conjunto de registros y el registro correspondiente en el origen de datos. Implementa el intercambio de campos de registros (RFX).

```
virtual void DoFieldExchange(CFieldExchange* pFX);
```

### <a name="parameters"></a>Parámetros

*Pfx*<br/>
Un puntero a un [CFieldExchange](../../mfc/reference/cfieldexchange-class.md) objeto. El marco de trabajo ya habrá configurado este objeto para especificar un contexto para la operación de intercambio de campos.

### <a name="remarks"></a>Observaciones

Cuando no se implementa la obtención masiva de filas, el marco de trabajo llama a esta función miembro para intercambiar automáticamente datos entre los miembros de datos de campo del objeto de conjunto de registros y las columnas correspondientes del registro actual en el origen de datos. `DoFieldExchange`También enlaza los miembros de datos de parámetro, si los hay, a marcadores de posición de parámetro en la cadena de instrucción SQL para la selección del conjunto de registros.

Si se implementa la obtención masiva de filas, el marco de trabajo llama a [DoBulkFieldExchange](#dobulkfieldexchange). Para implementar la obtención masiva `CRecordset::useMultiRowFetch` de filas, debe especificar la opción del parámetro *dwOptions* en la función miembro [Open.](#open)

> [!NOTE]
> `DoFieldExchange`solo está disponible si está utilizando `CRecordset`una clase derivada de . Si ha creado un objeto `CRecordset`de conjunto de registros directamente desde , debe llamar a la [GetFieldValue](#getfieldvalue) función miembro para recuperar datos.

El intercambio de datos de campo, denominado intercambio de campos de registros (RFX), funciona en ambas direcciones: desde los miembros de datos de campo del objeto de conjunto de registros hasta los campos del registro en el origen de datos y desde el registro del origen de datos al objeto de conjunto de registros.

La única acción que normalmente debe realizar para implementar `DoFieldExchange` para la clase de conjunto de registros derivada es crear la clase con ClassWizard y especificar los nombres y tipos de datos de los miembros de datos de campo. También puede agregar código a lo que ClassWizard escribe para especificar miembros de datos de parámetro o para tratar con las columnas que se enlazan dinámicamente. Para obtener más información, vea el artículo [Conjunto de registros: Enlazar dinámicamente columnas de datos (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).

Cuando se declara la clase de conjunto de registros `DoFieldExchange` derivada con ClassWizard, el asistente escribe una invalidación de usted, que se asemeja al ejemplo siguiente:

[!code-cpp[NVC_MFCDatabase#19](../../mfc/codesnippet/cpp/crecordset-class_3.cpp)]

Para obtener más información acerca de las funciones RFX, vea el tema [Funciones](../../mfc/reference/record-field-exchange-functions.md)de intercambio de campos de registro .

Para obtener más ejemplos y detalles sobre `DoFieldExchange`, vea el artículo Intercambio de campos de registros: Cómo funciona [RFX](../../data/odbc/record-field-exchange-how-rfx-works.md). Para obtener información general acerca de RFX, vea el artículo Intercambio de campos de [registros](../../data/odbc/record-field-exchange-rfx.md).

## <a name="crecordsetedit"></a><a name="edit"></a>CRecordset::Editar

Permite realizar cambios en el registro actual.

```
virtual void Edit();
```

### <a name="remarks"></a>Observaciones

Después `Edit`de llamar a , puede cambiar los miembros de datos de campo restableciendo directamente sus valores. La operación se completa cuando se llama posteriormente a la [Update](#update) función miembro para guardar los cambios en el origen de datos.

> [!NOTE]
> Si ha implementado la obtención masiva `Edit`de filas, no puede llamar a . Esto dará lugar a una aserción con errores. Aunque `CRecordset` la clase no proporciona un mecanismo para actualizar filas masivas de datos, puede escribir sus propias funciones mediante la función `SQLSetPos`de API ODBC . Para obtener más información sobre la obtención masiva de filas, vea el artículo [Conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

`Edit`guarda los valores de los miembros de datos del conjunto de registros. Si llama `Edit`a , realiza `Edit` cambios y, a continuación, vuelve a `Edit` llamar, los valores del registro se restauran en lo que eran antes de la primera llamada.

En algunos casos, es posible que desee actualizar una columna convirtiéndola en Null (que no contiene datos). Para ello, llame a [SetFieldNull](#setfieldnull) con un parámetro de TRUE para marcar el campo Null; esto también hace que la columna se actualice. Si desea que un campo se escriba en el origen de datos aunque su valor no haya cambiado, llame a [SetFieldDirty](#setfielddirty) con un parámetro de TRUE. Esto funciona incluso si el campo tenía el valor Null.

Si el origen de datos admite `Edit` transacciones, puede hacer que la llamada forme parte de una transacción. Tenga en cuenta que debe llamar a `Edit` [CDatabase::BeginTrans](../../mfc/reference/cdatabase-class.md#begintrans) antes de llamar y después de que se ha abierto el conjunto de registros. Tenga en cuenta también que llamar a [CDatabase::CommitTrans](../../mfc/reference/cdatabase-class.md#committrans) no es un sustituto para llamar `Update` para completar la `Edit` operación. Para obtener más información acerca de las transacciones, vea la clase [CDatabase](../../mfc/reference/cdatabase-class.md).

Dependiendo del modo de bloqueo actual, el `Edit` registro que `Update` se está actualizando puede bloquearse hasta `Edit` que llame o desplácese a otro registro, o puede bloquearse solo durante la llamada. Puede cambiar el modo de bloqueo con [SetLockingMode](#setlockingmode).

El valor anterior del registro actual se restaura si `Update`se desplaza a un nuevo registro antes de llamar a . A `CDBException` se produce si `Edit` se llama a un conjunto de registros que no se puede actualizar o si no hay ningún registro actual.

Para obtener más información, vea los artículos [Transacción (ODBC)](../../data/odbc/transaction-odbc.md) y [Conjunto de registros: bloqueo de registros (ODBC)](../../data/odbc/recordset-locking-records-odbc.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDatabase#20](../../mfc/codesnippet/cpp/crecordset-class_4.cpp)]

## <a name="crecordsetflushresultset"></a><a name="flushresultset"></a>CRecordset::FlushResultSet

Recupera el siguiente conjunto de resultados de una consulta predefinida (procedimiento almacenado), si hay varios conjuntos de resultados.

```
BOOL FlushResultSet();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si hay más conjuntos de resultados que se recuperarán; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Solo debe `FlushResultSet` llamar cuando haya terminado completamente con el cursor en el conjunto de resultados actual. Tenga en cuenta que cuando se `FlushResultSet`recupera el siguiente conjunto de resultados mediante una llamada , el cursor no es válido en ese conjunto de resultados; debe llamar a la [MoveNext](#movenext) función miembro después de llamar a `FlushResultSet`.

Si una consulta predefinida utiliza un parámetro de salida `FlushResultSet` o `FALSE` parámetros de entrada/salida, debe llamar hasta que vuelva (el valor 0), para obtener estos valores de parámetro.

`FlushResultSet`llama a la `SQLMoreResults`función de API ODBC . Si `SQLMoreResults` devuelve SQL_ERROR o `FlushResultSet` SQL_INVALID_HANDLE, se producirá una excepción. Para obtener `SQLMoreResults`más información acerca de , consulte el Windows SDK.

El procedimiento almacenado debe tener campos enlazados si desea llamar `FlushResultSet`a .

### <a name="example"></a>Ejemplo

En el código `COutParamRecordset` siguiente `CRecordset`se supone que es un objeto derivado basado en una consulta predefinida con un parámetro de entrada y un parámetro de salida, y que tiene varios conjuntos de resultados. Tenga en cuenta la estructura de la invalidación [DoFieldExchange.](#dofieldexchange)

[!code-cpp[NVC_MFCDatabase#21](../../mfc/codesnippet/cpp/crecordset-class_5.cpp)]

[!code-cpp[NVC_MFCDatabase#22](../../mfc/codesnippet/cpp/crecordset-class_6.cpp)]

## <a name="crecordsetgetbookmark"></a><a name="getbookmark"></a>CRecordset::GetBookmark

Obtiene el valor del marcador para el registro actual.

```cpp
void GetBookmark(CDBVariant& varBookmark);
```

### <a name="parameters"></a>Parámetros

*varBookmark*<br/>
Una referencia a un [CDBVariant](../../mfc/reference/cdbvariant-class.md) objeto que representa el marcador en el registro actual.

### <a name="remarks"></a>Observaciones

Para determinar si los marcadores son compatibles con el conjunto de registros, llame a [CanBookmark](#canbookmark). Para que los marcadores estén disponibles `CRecordset::useBookmarks` si son compatibles, debe establecer la opción en el parámetro *dwOptions* de [la](#open) open función miembro.

> [!NOTE]
> Si los marcadores no son `GetBookmark` compatibles o no están disponibles, la llamada dará lugar a una excepción que se produce. Los marcadores no se admiten en conjuntos de registros de solo avance.

`GetBookmark`asigna el valor del marcador para el `CDBVariant` registro actual a un objeto. Para volver a ese registro en cualquier momento después de `CDBVariant` pasar a un registro diferente, llame a [SetBookmark](#setbookmark) con el objeto correspondiente.

> [!NOTE]
> Después de ciertas operaciones de conjunto de registros, es posible que los marcadores ya no sean válidos. Por ejemplo, si `GetBookmark` llama `Requery`seguido de , es posible que `SetBookmark`no pueda volver al registro con . Llame a [CDatabase::GetBookmarkPersistence](../../mfc/reference/cdatabase-class.md#getbookmarkpersistence) para comprobar `SetBookmark`si puede llamar de forma segura .

Para obtener más información acerca de los marcadores y la navegación de conjuntos de registros, vea los artículos Conjunto de [registros: marcadores y posiciones absolutas (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md) y [Conjunto de registros: desplazamiento (ODBC)](../../data/odbc/recordset-scrolling-odbc.md).

## <a name="crecordsetgetdefaultconnect"></a><a name="getdefaultconnect"></a>CRecordset::GetDefaultConnect

Se llama para obtener la cadena de conexión predeterminada.

```
virtual CString GetDefaultConnect();
```

### <a name="return-value"></a>Valor devuelto

A `CString` que contiene la cadena de conexión predeterminada.

### <a name="remarks"></a>Observaciones

El marco de trabajo llama a esta función miembro para obtener la cadena de conexión predeterminada para el origen de datos en el que se basa el conjunto de registros. ClassWizard implementa esta función por usted mediante la identificación del mismo origen de datos que se usa en ClassWizard para obtener información sobre tablas y columnas. Probablemente le resulte conveniente confiar en esta conexión predeterminada mientras desarrolla la aplicación. Pero la conexión predeterminada puede no ser adecuada para los usuarios de la aplicación. Si ese es el caso, debe volver a implementar esta función, descartando la versión de ClassWizard. Para obtener más información acerca de las cadenas de conexión, vea el artículo Origen de datos [(ODBC)](../../data/odbc/data-source-odbc.md).

## <a name="crecordsetgetdefaultsql"></a><a name="getdefaultsql"></a>CRecordset::GetDefaultSQL

Se llama para obtener la cadena SQL predeterminada que se va a ejecutar.

```
virtual CString GetDefaultSQL();
```

### <a name="return-value"></a>Valor devuelto

A `CString` que contiene la instrucción SQL predeterminada.

### <a name="remarks"></a>Observaciones

El marco de trabajo llama a esta función miembro para obtener la instrucción SQL predeterminada en la que se basa el conjunto de registros. Puede ser un nombre de tabla o una instrucción **SELECT** de SQL.

Defina indirectamente la instrucción SQL predeterminada declarando la clase de conjunto de registros con ClassWizard y ClassWizard realiza esta tarea por usted.

Si necesita la cadena de instrucción `GetSQL`SQL para su propio uso, llame a , que devuelve la instrucción SQL utilizada para seleccionar los registros del conjunto de registros cuando se abrió. Puede editar la cadena SQL predeterminada en `GetDefaultSQL`la invalidación de la clase de . Por ejemplo, puede especificar una llamada a una consulta predefinida mediante una instrucción **CALL.** (Tenga en cuenta, sin embargo, que si edita `GetDefaultSQL`, también debe modificar para que `m_nFields` coincida con el número de columnas en el origen de datos.)

Para obtener más información, vea el artículo [Conjunto de registros: declarar una clase para una tabla (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md).

> [!CAUTION]
> El nombre de la tabla estará vacío si el marco de trabajo no pudo identificar un nombre de tabla, si se proporcionaron varios nombres de tabla o si no se pudo interpretar una instrucción **CALL.** Tenga en cuenta que al utilizar una instrucción **CALL,** no debe insertar espacios en blanco entre la llave y la palabra clave **CALL,** ni debe insertar espacios en blanco antes de la llave o antes de la palabra clave **SELECT** en una instrucción **SELECT.**

## <a name="crecordsetgetfieldvalue"></a><a name="getfieldvalue"></a>CRecordset::GetFieldValue

Recupera datos de campo en el registro actual.

```cpp
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
El nombre de un campo.

*varValu*e Una referencia a un [CDBVariant](../../mfc/reference/cdbvariant-class.md) objeto que almacenará el valor del campo.

*nFieldType*<br/>
El tipo de datos ODBC C del campo. El uso del valor `GetFieldValue` predeterminado, DEFAULT_FIELD_TYPE, obliga a determinar el tipo de datos C del tipo de datos SQL, en función de la tabla siguiente. De lo contrario, puede especificar el tipo de datos directamente o elegir un tipo de datos compatible; por ejemplo, puede almacenar cualquier tipo de datos en SQL_C_CHAR.

|Tipo de datos C|Tipo de datos de SQL|
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

Para obtener más información acerca de los tipos de datos ODBC, vea los temas "Tipos de datos SQL" y "Tipos de datos C" en el Apéndice D del Windows SDK.

*nIndex*<br/>
El índice de base cero del campo.

*strValue*<br/>
Una referencia a un [CString](../../atl-mfc-shared/reference/cstringt-class.md) objeto que almacenará el valor del campo convertido en texto, independientemente del tipo de datos del campo.

### <a name="remarks"></a>Observaciones

Puede buscar un campo por nombre o por índice. Puede almacenar el valor del `CDBVariant` campo `CString` en un objeto o en un objeto.

Si ha implementado la obtención masiva de filas, el registro actual siempre se coloca en el primer registro de un conjunto de filas. Para `GetFieldValue` usar en un registro dentro de un conjunto de filas determinado, primero debe llamar a la [SetRowsetCursorPosition](#setrowsetcursorposition) función miembro para mover el cursor a la fila deseada dentro de ese conjunto de filas. Entonces `GetFieldValue` llama a esa fila. Para implementar la obtención masiva `CRecordset::useMultiRowFetch` de filas, debe especificar la opción del parámetro *dwOptions* en la función miembro [Open.](#open)

Puede usar `GetFieldValue` para capturar campos dinámicamente en tiempo de ejecución en lugar de enlazarlos estáticamente en tiempo de diseño. Por ejemplo, si ha declarado un `CRecordset`objeto de `GetFieldValue` conjunto de registros directamente desde , debe utilizar para recuperar los datos de campo; no se implementa el intercambio de campos de registros (RFX) o el intercambio de campos de registros masivos (RFX masivo).

> [!NOTE]
> Si declara un objeto de `CRecordset`conjunto de registros sin derivar de , no tiene cargada la biblioteca de cursores ODBC. La biblioteca de cursores requiere que el conjunto de registros tenga al menos una columna enlazada; sin embargo, `CRecordset` cuando se utiliza directamente, ninguna de las columnas está enlazada. Las funciones miembro [CDatabase::OpenEx](../../mfc/reference/cdatabase-class.md#openex) y [CDatabase::Open](../../mfc/reference/cdatabase-class.md#open) controlan si se cargará la biblioteca de cursores.

`GetFieldValue`llama a la `SQLGetData`función de API ODBC . Si el controlador genera el valor SQL_NO_TOTAL para la `GetFieldValue` longitud real del valor de campo, produce una excepción. Para obtener `SQLGetData`más información acerca de , consulte el Windows SDK.

### <a name="example"></a>Ejemplo

El siguiente código de `GetFieldValue` ejemplo ilustra las llamadas a un objeto de conjunto de registros declarado directamente desde `CRecordset`.

[!code-cpp[NVC_MFCDatabase#23](../../mfc/codesnippet/cpp/crecordset-class_7.cpp)]

> [!NOTE]
> A diferencia `CDaoRecordset`de `CRecordset` la clase `SetFieldValue` DAO , no tiene una función miembro. Si crea un objeto `CRecordset`directamente desde , es de forma efectiva de solo lectura.

Para obtener más información sobre la obtención masiva de filas, vea el artículo [Conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

## <a name="crecordsetgetodbcfieldcount"></a><a name="getodbcfieldcount"></a>CRecordset::GetODBCFieldCount

Recupera el número total de campos del objeto de conjunto de registros.

```
short GetODBCFieldCount() const;
```

### <a name="return-value"></a>Valor devuelto

El número de campos del conjunto de registros.

### <a name="remarks"></a>Observaciones

Para obtener más información acerca de la creación de conjuntos de registros, vea el artículo Conjunto de [registros: crear y cerrar conjuntos de registros (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md).

## <a name="crecordsetgetodbcfieldinfo"></a><a name="getodbcfieldinfo"></a>CRecordset::GetODBCFieldInfo

Obtiene información sobre los campos del conjunto de registros.

```cpp
void GetODBCFieldInfo(
    LPCTSTR lpszName,
    CODBCFieldInfo& fieldinfo);

void GetODBCFieldInfo(
    short nIndex,
    CODBCFieldInfo& fieldinfo);
```

### <a name="parameters"></a>Parámetros

*lpszName*<br/>
El nombre de un campo.

*fieldinfo*<br/>
Una referencia `CODBCFieldInfo` a una estructura.

*nIndex*<br/>
El índice de base cero del campo.

### <a name="remarks"></a>Observaciones

Una versión de la función le permite buscar un campo por nombre. La otra versión le permite buscar un campo por índice.

Para obtener una descripción sobre la información devuelta, vea el [CODBCFieldInfo](../../mfc/reference/codbcfieldinfo-structure.md) estructura.

Para obtener más información acerca de la creación de conjuntos de registros, vea el artículo Conjunto de [registros: crear y cerrar conjuntos de registros (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md).

## <a name="crecordsetgetrecordcount"></a><a name="getrecordcount"></a>CRecordset::GetRecordCount

Determina el tamaño del conjunto de registros.

```
long GetRecordCount() const;
```

### <a name="return-value"></a>Valor devuelto

El número de registros en el conjunto de registros; 0 si el conjunto de registros no contiene registros; o -1 si no se puede determinar el recuento de registros.

### <a name="remarks"></a>Observaciones

> [!CAUTION]
> El recuento de registros se mantiene como una "marca de agua alta", el registro con el número más alto que se ve hasta la fecha a medida que el usuario se mueve a través de los registros. El número total de registros solo se conoce después de que el usuario se haya movido más allá del último registro. Por motivos de rendimiento, el `MoveLast`recuento no se actualiza cuando se llama a . Para contar los registros usted mismo, llame `MoveNext` repetidamente hasta que `IsEOF` se devuelva distinto de cero. Agregar un `CRecordset:AddNew` registro `Update` a través y aumenta el recuento; eliminar un registro `CRecordset::Delete` a través disminuye el recuento.

## <a name="crecordsetgetrowsetsize"></a><a name="getrowsetsize"></a>CRecordset::GetRowsetSize

Obtiene la configuración actual para el número de filas que desea recuperar durante una captura determinada.

```
DWORD GetRowsetSize() const;
```

### <a name="return-value"></a>Valor devuelto

El número de filas que se van a recuperar durante una captura determinada.

### <a name="remarks"></a>Observaciones

Si utiliza la obtención masiva de filas, el tamaño predeterminado del conjunto de filas cuando se abre el conjunto de registros es 25; de lo contrario, es 1.

Para implementar la obtención masiva `CRecordset::useMultiRowFetch` de filas, debe especificar la opción en el *dwOptions* parámetro de la [Open](#open) función miembro. Para cambiar la configuración del tamaño del conjunto de filas, llame a [SetRowsetSize](#setrowsetsize).

Para obtener más información sobre la obtención masiva de filas, vea el artículo [Conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

## <a name="crecordsetgetrowsfetched"></a><a name="getrowsfetched"></a>CRecordset::GetRowsFetched

Determina cuántos registros se recuperaron realmente después de una captura.

```
DWORD GetRowsFetched() const;
```

### <a name="return-value"></a>Valor devuelto

El número de filas recuperadas del origen de datos después de una captura determinada.

### <a name="remarks"></a>Observaciones

Esto es útil cuando se ha implementado la obtención masiva de filas. El tamaño del conjunto de filas normalmente indica cuántas filas se recuperarán de una captura; sin embargo, el número total de filas del conjunto de registros también afecta a cuántas filas se recuperarán en un conjunto de filas. Por ejemplo, si el conjunto de registros tiene 10 registros con `MoveNext` un valor de tamaño de conjunto de filas de 4, el bucle a través del conjunto de registros mediante una llamada dará como resultado que el conjunto de filas final tenga solo 2 registros.

Para implementar la obtención masiva `CRecordset::useMultiRowFetch` de filas, debe especificar la opción en el *dwOptions* parámetro de la [Open](#open) función miembro. Para especificar el tamaño del conjunto de filas, llame a [SetRowsetSize](#setrowsetsize).

Para obtener más información sobre la obtención masiva de filas, vea el artículo [Conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDatabase#24](../../mfc/codesnippet/cpp/crecordset-class_8.cpp)]

## <a name="crecordsetgetrowstatus"></a><a name="getrowstatus"></a>CRecordset::GetRowStatus

Obtiene el estado de una fila del conjunto de filas actual.

```
WORD GetRowStatus(WORD wRow) const;
```

### <a name="parameters"></a>Parámetros

*wRow*<br/>
Posición basada en uno de una fila en el conjunto de filas actual. Este valor puede oscilar entre 1 y el tamaño del conjunto de filas.

### <a name="return-value"></a>Valor devuelto

Un valor de estado para la fila. Para conocer más detalles, vea la sección Comentarios.

### <a name="remarks"></a>Observaciones

`GetRowStatus`devuelve un valor que indica cualquier cambio en el estado de la fila desde la última vez que se recuperó del origen de datos o que no se recuperó ninguna fila correspondiente a *wRow.* La tabla siguiente muestra los valores devueltos posibles.

|Valor de estado|Descripción|
|------------------|-----------------|
|SQL_ROW_SUCCESS|La fila no cambia.|
|SQL_ROW_UPDATED|La fila se ha actualizado.|
|SQL_ROW_DELETED|La fila se ha eliminado.|
|SQL_ROW_ADDED|Se ha agregado la fila.|
|SQL_ROW_ERROR|La fila no se puede recuperar debido a un error.|
|SQL_ROW_NOROW|No hay ninguna fila que corresponda a *wRow*.|

Para obtener más información, `SQLExtendedFetch` consulte la función de API ODBC en el Windows SDK.

## <a name="crecordsetgetstatus"></a><a name="getstatus"></a>CRecordset::GetStatus

Determina el índice del registro actual en el conjunto de registros y si se ha visto el último registro.

```cpp
void GetStatus(CRecordsetStatus& rStatus) const;
```

### <a name="parameters"></a>Parámetros

*rStatus*<br/>
Referencia a un objeto `CRecordsetStatus`. Para obtener más información, vea la sección Comentarios.

### <a name="remarks"></a>Observaciones

`CRecordset`intenta realizar un seguimiento del índice, pero en algunas circunstancias esto puede no ser posible. Consulte [GetRecordCount](#getrecordcount) para obtener una explicación.

La `CRecordsetStatus` estructura tiene la siguiente forma:

```cpp
struct CRecordsetStatus
{
    long m_lCurrentRecord;
    BOOL m_bRecordCountFinal;
};
```

Los dos `CRecordsetStatus` miembros tienen los siguientes significados:

- `m_lCurrentRecord`Contiene el índice de base cero del registro actual en el conjunto de registros, si se conoce. Si no se puede determinar el índice, este miembro contiene AFX_CURRENT_RECORD_UNDEFINED (-2). Si `IsBOF` es TRUE (conjunto de registros vacío `m_lCurrentRecord` o intento de desplazarse antes del primer registro), se establece en AFX_CURRENT_RECORD_BOF (-1). Si está en el primer registro, se establece en 0, segundo registro 1, y así sucesivamente.

- `m_bRecordCountFinal`Distinto de cero si se ha determinado el número total de registros del conjunto de registros. Por lo general, esto debe lograrse comenzando `MoveNext` `IsEOF` al principio del conjunto de registros y llamando hasta que se devuelve distinto de cero. Si este miembro es cero, el `GetRecordCount`recuento de registros devuelto por , si no -1, es sólo un recuento de "marca de agua alta" de los registros.

## <a name="crecordsetgetsql"></a><a name="getsql"></a>CRecordset::GetSQL

Llame a esta función miembro para obtener la instrucción SQL que se usó para seleccionar los registros del conjunto de registros cuando se abrió.

```
const CString& GetSQL() const;
```

### <a name="return-value"></a>Valor devuelto

Una referencia **const** a una `CString` que contiene la instrucción SQL.

### <a name="remarks"></a>Observaciones

Por lo general, se trata de una instrucción **SELECT** de SQL. La cadena `GetSQL` devuelta por es de solo lectura.

La cadena `GetSQL` devuelta por es normalmente diferente de cualquier cadena que haya pasado `Open` al conjunto de registros en el *lpszSQL* parámetro a la función miembro. Esto se debe a que el conjunto de registros construye una instrucción SQL completa basada en lo que ha pasado , `Open`lo que especificó con ClassWizard, lo que puede haber especificado en los `m_strFilter` miembros de datos y `m_strSort` y los parámetros que haya especificado. Para obtener más información sobre cómo el conjunto de registros construye esta instrucción SQL, vea el artículo Conjunto de registros: cómo los conjuntos de [registros seleccionan registros (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md).

> [!NOTE]
> Llame a esta función miembro solo después de llamar a [Open](#open).

## <a name="crecordsetgettablename"></a><a name="gettablename"></a>CRecordset::GetTableName

Obtiene el nombre de la tabla SQL en la que se basa la consulta del conjunto de registros.

```
const CString& GetTableName() const;
```

### <a name="return-value"></a>Valor devuelto

Una referencia **const** a a `CString` que contiene el nombre de la tabla, si el conjunto de registros se basa en una tabla; de lo contrario, una cadena vacía.

### <a name="remarks"></a>Observaciones

`GetTableName`solo es válido si el conjunto de registros se basa en una tabla, no en una combinación de varias tablas o en una consulta predefinida (procedimiento almacenado). El nombre es de solo lectura.

> [!NOTE]
> Llame a esta función miembro solo después de llamar a [Open](#open).

## <a name="crecordsetisbof"></a><a name="isbof"></a>CRecordset::IsBOF

Devuelve distinto de cero si el conjunto de registros se ha colocado antes del primer registro. No hay ningún registro actual.

```
BOOL IsBOF() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el conjunto de registros no contiene registros o si se ha desplazado hacia atrás antes del primer registro; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Llame a esta función miembro antes de desplazarse de registro a registro para saber si ha ido antes del primer registro del conjunto de registros. También puede `IsBOF` usar `IsEOF` junto con para determinar si el conjunto de registros contiene registros o está vacío. Inmediatamente después `Open`de llamar a , `IsBOF` si el conjunto de registros no contiene registros, devuelve distinto de cero. Al abrir un conjunto de registros que tiene al menos `IsBOF` un registro, el primer registro es el registro actual y devuelve 0.

Si el primer registro es el `MovePrev` `IsBOF` registro actual y se llama a , devolverá posteriormente distinto de cero. Si `IsBOF` devuelve distinto de `MovePrev`cero y se llama a , se produce un error. Si `IsBOF` devuelve distinto de cero, el registro actual es indefinido y cualquier acción que requiera un registro actual dará lugar a un error.

### <a name="example"></a>Ejemplo

En este `IsBOF` `IsEOF` ejemplo se usan y para detectar los límites de un conjunto de registros a medida que el código se desplaza por el conjunto de registros en ambas direcciones.

[!code-cpp[NVC_MFCDatabase#25](../../mfc/codesnippet/cpp/crecordset-class_9.cpp)]

## <a name="crecordsetisdeleted"></a><a name="isdeleted"></a>CRecordset::IsDeleted

Determina si se ha eliminado el registro actual.

```
BOOL IsDeleted() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el conjunto de registros se coloca en un registro eliminado; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Si se desplaza a `IsDeleted` un registro y devuelve TRUE (distinto de cero), debe desplazarse a otro registro antes de poder realizar cualquier otra operación de conjunto de registros.

El resultado `IsDeleted` de depende de muchos factores, como el tipo de conjunto de `CRecordset::skipDeletedRecords` registros, si el conjunto de registros es actualizable, si especificó la opción al abrir el conjunto de registros, si el controlador empaqueta registros eliminados y si hay varios usuarios.

Para obtener `CRecordset::skipDeletedRecords` más información acerca y el empaquetado del controlador, vea el [Open](#open) función miembro.

> [!NOTE]
> Si ha implementado la obtención masiva de `IsDeleted`filas, no debe llamar a . En su lugar, llame a la [GetRowStatus](#getrowstatus) función miembro. Para obtener más información sobre la obtención masiva de filas, vea el artículo [Conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

## <a name="crecordsetiseof"></a><a name="iseof"></a>CRecordset::IsEOF

Devuelve distinto de cero si el conjunto de registros se ha colocado después del último registro. No hay ningún registro actual.

```
BOOL IsEOF() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el conjunto de registros no contiene registros o si se ha desplazado más allá del último registro; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Llame a esta función miembro a medida que se desplaza de registro a registro para saber si ha ido más allá del último registro del conjunto de registros. También puede `IsEOF` utilizar para determinar si el conjunto de registros contiene registros o está vacío. Inmediatamente después `Open`de llamar a , `IsEOF` si el conjunto de registros no contiene registros, devuelve distinto de cero. Al abrir un conjunto de registros que tiene al menos `IsEOF` un registro, el primer registro es el registro actual y devuelve 0.

Si el último registro es el `MoveNext` `IsEOF` registro actual cuando se llama , devolverá posteriormente distinto de cero. Si `IsEOF` devuelve distinto de `MoveNext`cero y se llama a , se produce un error. Si `IsEOF` devuelve distinto de cero, el registro actual es indefinido y cualquier acción que requiera un registro actual dará lugar a un error.

### <a name="example"></a>Ejemplo

Vea el ejemplo [de IsBOF](#isbof).

## <a name="crecordsetisfielddirty"></a><a name="isfielddirty"></a>CRecordset::IsFieldDirty

Determina si el miembro de datos de campo especificado se ha cambiado desde que se llamó a [Edit](#edit) o [AddNew.](#addnew)

```
BOOL IsFieldDirty(void* pv);
```

### <a name="parameters"></a>Parámetros

*Pv*<br/>
Un puntero al miembro de datos de campo cuyo estado desea comprobar, o NULL para determinar si alguno de los campos está sucio.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el miembro de `AddNew` `Edit`datos de campo especificado ha cambiado desde que llamó o ; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Los datos de todos los miembros de datos de campo sucios se transferirán al registro del origen de `Edit` `AddNew`datos cuando se actualice el registro actual mediante una llamada a la función miembro [Update](#update) de `CRecordset` (después de una llamada a o ).

> [!NOTE]
> Esta función miembro no es aplicable en conjuntos de registros que usan la obtención masiva de filas. Si ha implementado la obtención `IsFieldDirty` masiva de filas, siempre devolverá FALSE y dará como resultado una aserción con errores. Para obtener más información sobre la obtención masiva de filas, vea el artículo [Conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

La `IsFieldDirty` llamada restablecerá los efectos de las llamadas anteriores a [SetFieldDirty,](#setfielddirty) ya que se vuelve a evaluar el estado sucio del campo. En `AddNew` el caso, si el valor del campo actual difiere del valor pseudo nulo, el estado del campo se establece sucio. En `Edit` el caso, si el valor del campo difiere del valor almacenado en caché, el estado del campo se establece sucio.

`IsFieldDirty`se implementa a través de [DoFieldExchange](#dofieldexchange).

Para obtener más información sobre la marca desfasado, vea el artículo Conjunto de registros: cómo los conjuntos de [registros seleccionan registros (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md).

## <a name="crecordsetisfieldnull"></a><a name="isfieldnull"></a>CRecordset::IsFieldNull

Devuelve distinto de cero si el campo especificado en el registro actual es Null (no tiene ningún valor).

```
BOOL IsFieldNull(void* pv);
```

### <a name="parameters"></a>Parámetros

*Pv*<br/>
Un puntero al miembro de datos de campo cuyo estado desea comprobar, o NULL para determinar si alguno de los campos es Null.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el miembro de datos de campo especificado se marca como Null; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Llame a esta función miembro para determinar si el miembro de datos de campo especificado de un conjunto de registros se ha marcado como Null. (En terminología de base de datos, Null significa "no tener ningún valor" y no es lo mismo que NULL en C++.) Si un miembro de datos de campo se marca como Null, se interpreta como una columna del registro actual para la que no hay ningún valor.

> [!NOTE]
> Esta función miembro no es aplicable en conjuntos de registros que usan la obtención masiva de filas. Si ha implementado la obtención `IsFieldNull` masiva de filas, siempre devolverá FALSE y dará como resultado una aserción con errores. Para obtener más información sobre la obtención masiva de filas, vea el artículo [Conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

`IsFieldNull`se implementa a través de [DoFieldExchange](#dofieldexchange).

## <a name="crecordsetisfieldnullable"></a><a name="isfieldnullable"></a>CRecordset::IsFieldNullable

Devuelve distinto de cero si el campo especificado en el registro actual se puede establecer en Null (sin valor).

```
BOOL IsFieldNullable(void* pv);
```

### <a name="parameters"></a>Parámetros

*Pv*<br/>
Puntero al miembro de datos de campo cuyo estado desea comprobar, o NULL para determinar si alguno de los campos se puede establecer en un valor Null.

### <a name="remarks"></a>Observaciones

Llame a esta función miembro para determinar si el miembro de datos de campo especificado es "nullable" (se puede establecer en un Null valor; C++ NULL no es lo mismo que Null, que, en terminología de base de datos, significa "no tener ningún valor").

> [!NOTE]
> Si ha implementado la obtención masiva `IsFieldNullable`de filas, no puede llamar a . En su lugar, llame a la [GetODBCFieldInfo](#getodbcfieldinfo) función miembro para determinar si un campo se puede establecer en un Null valor. Tenga en cuenta `GetODBCFieldInfo`que siempre puede llamar a , independientemente de si ha implementado la obtención masiva de filas. Para obtener más información sobre la obtención masiva de filas, vea el artículo [Conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Un campo que no puede ser Null debe tener un valor. Si intenta establecer un campo de este tipo en Null al agregar o actualizar un registro, el origen de datos rechaza la adición o actualización y [Update](#update) producirá una excepción. La excepción se `Update`produce cuando se llama a , no cuando se llama a [SetFieldNull](#setfieldnull).

El uso de NULL para el primer argumento `outputColumn` de `param` la función aplicará la función solo a los campos, no a los campos. Por ejemplo, la llamada

[!code-cpp[NVC_MFCDatabase#26](../../mfc/codesnippet/cpp/crecordset-class_10.cpp)]

establecerá solo `outputColumn` los campos en NULL; `param` los campos no se verán afectados.

Para trabajar `param` en campos, debe proporcionar la `param` dirección real de la persona en la que desea trabajar, como:

[!code-cpp[NVC_MFCDatabase#27](../../mfc/codesnippet/cpp/crecordset-class_11.cpp)]

Esto significa que `param` no puede establecer todos `outputColumn` los campos en NULL, como puede hacer con los campos.

`IsFieldNullable`se implementa a través de [DoFieldExchange](#dofieldexchange).

## <a name="crecordsetisopen"></a><a name="isopen"></a>CRecordset::IsOpen

Determina si el conjunto de registros ya está abierto.

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se ha llamado previamente a la función miembro [Open](#open) o [Requery](#requery) del objeto de conjunto de registros y no se ha cerrado el conjunto de registros; de lo contrario 0.

## <a name="crecordsetm_hstmt"></a><a name="m_hstmt"></a>CRecordset::m_hstmt

Contiene un identificador de la estructura de datos de la instrucción ODBC, de tipo HSTMT, asociada al conjunto de registros.

### <a name="remarks"></a>Observaciones

Cada consulta a un origen de datos ODBC está asociada a un HSTMT.

> [!CAUTION]
> No usar `m_hstmt` antes de que se haya llamado a [Open.](#open)

Normalmente no es necesario tener acceso al HSTMT directamente, pero es posible que lo necesite para la ejecución directa de instrucciones SQL. La `ExecuteSQL` función `CDatabase` miembro de la `m_hstmt`clase proporciona un ejemplo de uso de .

## <a name="crecordsetm_nfields"></a><a name="m_nfields"></a>CRecordset::m_nFields

Contiene el número de miembros de datos de campo en la clase de conjunto de registros; es decir, el número de columnas seleccionadas por el conjunto de registros del origen de datos.

### <a name="remarks"></a>Observaciones

El constructor de la `m_nFields` clase de conjunto de registros debe inicializarse con el número correcto. Si no ha implementado la obtención masiva de filas, ClassWizard escribe esta inicialización automáticamente cuando se usa para declarar la clase de conjunto de registros. También puede escribirlo manualmente.

El marco de trabajo usa este número para administrar la interacción entre los miembros de datos de campo y las columnas correspondientes del registro actual en el origen de datos.

> [!CAUTION]
> Este número debe corresponder al número de `DoFieldExchange` `DoBulkFieldExchange` "columnas de salida" registradas `CFieldExchange::outputColumn`en o después de una llamada a [SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype) con el parámetro .

Puede enlazar columnas dinámicamente, como se explica en el artículo "Recordset: Dynamically Binding Data Columns." Si lo hace, debe aumentar `m_nFields` el recuento para reflejar el número de llamadas de función RFX o RFX masivas en la función `DoFieldExchange` miembro o para `DoBulkFieldExchange` las columnas enlazadas dinámicamente.

Para obtener más información, vea los artículos [Recordset: Dynamically Binding Data Columns (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md) y [Recordset: Fetching Records in Bulk (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

### <a name="example"></a>Ejemplo

Consulte el artículo Intercambio de campos de [registros: Uso](../../data/odbc/record-field-exchange-using-rfx.md)de RFX .

## <a name="crecordsetm_nparams"></a><a name="m_nparams"></a>CRecordset::m_nParams

Contiene el número de miembros de datos de parámetro en la clase de conjunto de registros; es decir, el número de parámetros pasados con la consulta del conjunto de registros.

### <a name="remarks"></a>Observaciones

Si la clase de conjunto de registros tiene `m_nParams` algún miembro de datos de parámetro, el constructor de la clase debe inicializarse con el número correcto. El valor `m_nParams` predeterminado es 0. Si agrega miembros de datos de parámetro (que debe hacer manualmente), también debe agregar manualmente una inicialización en el constructor de clase para `m_strFilter` reflejar `m_strSort` el número de parámetros (que debe ser al menos tan grande como el número de marcadores de posición '' en su o cadena).

El marco de trabajo usa este número cuando parametriza la consulta del conjunto de registros.

> [!CAUTION]
> Este número debe corresponder al número de `DoFieldExchange` "params" registrados en `DoBulkFieldExchange` o después de una llamada a [SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype) con un valor de parámetro de `CFieldExchange::inputParam`, `CFieldExchange::param`, `CFieldExchange::outputParam`, o `CFieldExchange::inoutParam`.

### <a name="example"></a>Ejemplo

  Consulte los artículos [Conjunto de registros: Parametrizar un conjunto de registros (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md) y Intercambio de campos de registros: Uso de [RFX](../../data/odbc/record-field-exchange-using-rfx.md).

## <a name="crecordsetm_pdatabase"></a><a name="m_pdatabase"></a>CRecordset::m_pDatabase

Contiene un puntero `CDatabase` al objeto a través del cual el conjunto de registros está conectado a un origen de datos.

### <a name="remarks"></a>Observaciones

Esta variable se establece de dos maneras. Normalmente, se pasa un puntero `CDatabase` a un objeto ya conectado al construir el objeto de conjunto de registros. Si pasa NULL `CRecordset` en `CDatabase` su lugar, crea un objeto automáticamente y lo conecta. En cualquier `CRecordset` caso, almacena el puntero en esta variable.

Normalmente no necesitará utilizar directamente `m_pDatabase`el puntero almacenado en . Sin embargo, si `CRecordset`escribe sus propias extensiones en , es posible que deba usar el puntero. Por ejemplo, es posible que necesite `CDBException`el puntero si lanza su propia s. O puede que lo necesite si necesita `CDatabase` hacer algo con el mismo objeto, como `ExecuteSQL` ejecutar transacciones, establecer tiempos de espera o llamar a la función miembro de la clase `CDatabase` para ejecutar instrucciones SQL directamente.

## <a name="crecordsetm_strfilter"></a><a name="m_strfilter"></a>CRecordset::m_strFilter

Después de construir el objeto de `Open` conjunto de registros, pero `CString` antes de llamar a su función miembro, use este miembro de datos para almacenar un contenido de un SQL **WHERE** cláusula.

### <a name="remarks"></a>Observaciones

El conjunto de registros utiliza esta cadena para restringir `Open` `Requery` (o filtrar) los registros que selecciona durante la llamada o. Esto es útil para seleccionar un subconjunto de registros, como "todos los vendedores con sede en California" ("estado de CA"). La sintaxis SQL ODBC para una cláusula **WHERE** es

`WHERE search-condition`

Tenga en cuenta que no incluye la palabra clave **WHERE** en la cadena. El marco lo suministra.

También puede parametrizar la cadena de filtro colocando marcadores de posición '' en ella, declarando un miembro de datos de parámetro en la clase para cada marcador de posición y pasando parámetros al conjunto de registros en tiempo de ejecución. Esto le permite construir el filtro en tiempo de ejecución. Para obtener más información, vea el artículo [Conjunto de registros: parametrizar un conjunto de registros (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).

Para obtener más información acerca de las cláusulas **WHERE** de SQL, vea el artículo [SQL](../../data/odbc/sql.md). Para obtener más información acerca de la selección y el filtrado de registros, vea el artículo [Conjunto de registros: filtrar registros (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDatabase#30](../../mfc/codesnippet/cpp/crecordset-class_12.cpp)]

## <a name="crecordsetm_strsort"></a><a name="m_strsort"></a>CRecordset::m_strSort

Después de construir el objeto de `Open` conjunto de registros, pero `CString` antes de llamar a su función miembro, utilice este miembro de datos para almacenar un contenedor de un SQL **ORDER BY** cláusula.

### <a name="remarks"></a>Observaciones

El conjunto de registros utiliza esta cadena `Open` `Requery` para ordenar los registros que selecciona durante la llamada o. Puede usar esta característica para ordenar un conjunto de registros en una o varias columnas. La sintaxis SQL ODBC para una cláusula **ORDER BY** es

`ORDER BY sort-specification [, sort-specification]...`

donde una especificación de ordenación es un entero o un nombre de columna. También puede especificar el orden ascendente o descendente (el orden es ascendente de forma predeterminada) anexando "ASC" o "DESC" a la lista de columnas de la cadena de ordenación. Los registros seleccionados se ordenan primero por la primera columna de la lista, luego por la segunda, etc. Por ejemplo, puede pedir un conjunto de registros "Clientes" por apellido y, a continuación, nombre. El número de columnas que puede enumerar depende del origen de datos. Para obtener más información, consulte el Windows SDK.

Tenga en cuenta que no incluye la palabra clave **ORDER BY** en la cadena. El marco lo suministra.

Para obtener más información acerca de las cláusulas SQL, vea el artículo [SQL](../../data/odbc/sql.md). Para obtener más información acerca de la ordenación de registros, vea el artículo [Conjunto de registros: ordenar registros (ODBC)](../../data/odbc/recordset-sorting-records-odbc.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDatabase#31](../../mfc/codesnippet/cpp/crecordset-class_13.cpp)]

## <a name="crecordsetmove"></a><a name="move"></a>CRecordset::Move

Mueve el puntero de registro actual dentro del conjunto de registros, ya sea hacia delante o hacia atrás.

```
virtual void Move(
    long nRows,
    WORD wFetchType = SQL_FETCH_RELATIVE);
```

### <a name="parameters"></a>Parámetros

*nRows*<br/>
El número de filas que se moverán hacia delante o hacia atrás. Los valores positivos avanzan hacia el final del conjunto de registros. Los valores negativos se mueven hacia atrás, hacia el principio.

*wFetchType*<br/>
Determina el conjunto `Move` de filas que se recuperará. Para conocer más detalles, vea la sección Comentarios.

### <a name="remarks"></a>Observaciones

Si pasa un valor de 0 `Move` para *nRows*, actualiza el registro actual; `Move` terminará cualquier `AddNew` modo `Edit` o corriente, y restaurará el `AddNew` `Edit` valor del registro actual antes o se llamó.

> [!NOTE]
> Cuando se mueve a través de un conjunto de registros, no se pueden omitir los registros eliminados. Consulte [CRecordset::IsDeleted](#isdeleted) para obtener más información. Al abrir `CRecordset` un `skipDeletedRecords` con la `Move` opción establecida, afirma si el *nRows* parámetro es 0. Este comportamiento impide la actualización de las filas eliminadas por otras aplicaciones cliente con los mismos datos. Consulte el parámetro *dwOption* en `skipDeletedRecords` [Abrir](#open) para obtener una descripción de .

`Move`reposiciona el conjunto de registros por conjuntos de filas. En función de los valores de `Move` *nRows* y *wFetchType*, recupera el conjunto de filas adecuado y, a continuación, convierte el primer registro de ese conjunto de filas en el registro actual. Si no ha implementado la obtención masiva de filas, el tamaño del conjunto de filas siempre es 1. Al capturar un `Move` conjunto de filas, llama directamente a la [CheckRowsetError](#checkrowseterror) función miembro para controlar los errores resultantes de la captura.

Dependiendo de los valores `Move` que pase, es equivalente a otras `CRecordset` funciones miembro. En particular, el valor de *wFetchType* puede indicar una función miembro que es más intuitiva y a menudo el método preferido para mover el registro actual.

En la tabla siguiente se enumeran los valores `Move` posibles para *wFetchType*, el conjunto de filas que se recuperará en función de *wFetchType* y *nRows*, y cualquier función miembro equivalente correspondiente a *wFetchType*.

|wFetchType|Conjunto de filas capturado|Función miembro equivalente|
|----------------|--------------------|--------------------------------|
|SQL_FETCH_RELATIVE (el valor predeterminado)|El conjunto de filas que inicia *nRows* row(s) de la primera fila del conjunto de filas actual.||
|SQL_FETCH_NEXT|El siguiente conjunto de filas; *nRows* se omite.|[MoveNext](#movenext)|
|SQL_FETCH_PRIOR|El conjunto de filas anterior; *nRows* se omite.|[MovePrev](#moveprev)|
|SQL_FETCH_FIRST|El primer conjunto de filas del conjunto de registros; *nRows* se omite.|[Movefirst](#movefirst)|
|SQL_FETCH_LAST|El último conjunto de filas completo del conjunto de registros; *nRows* se omite.|[Movelast](#movelast)|
|SQL_FETCH_ABSOLUTE|Si *nRows* > 0, el conjunto de filas nRows que inicia *nRows* desde el principio del conjunto de registros. Si *nRows* < 0, el conjunto de filas nRows que inicia *nRows* desde el final del conjunto de registros. Si *nRows* es 0, se devuelve una condición de inicio de archivo (BOF).|[SetAbsolutePosition](#setabsoluteposition)|
|SQL_FETCH_BOOKMARK|El conjunto de filas que comienza en la fila cuyo valor de marcador corresponde a *nRows*.|[SetBookmark](#setbookmark)|

> [!NOTE]
> Para conjuntos de `Move` registros de solo avance, solo es válido con un valor de SQL_FETCH_NEXT para *wFetchType*.

> [!CAUTION]
> Al `Move` llamar se produce una excepción si el conjunto de registros no tiene registros. Para determinar si el conjunto de registros tiene registros, llame a [IsBOF](#isbof) e [IsEOF](#iseof).

> [!NOTE]
> Si se ha desplazado más allá del`IsBOF` principio `IsEOF` o al final `Move` del conjunto `CDBException`de registros ( o devuelve distinto de cero), llamar a una función posiblemente producirá un archivo . Por ejemplo, `IsEOF` si devuelve `IsBOF` distinto de `MoveNext` cero y no `MovePrev` lo hace, se producirá una excepción, pero no lo hará.

> [!NOTE]
> Si llama `Move` mientras se actualiza o agrega el registro actual, las actualizaciones se pierden sin previo aviso.

Para obtener más información acerca de la navegación de conjuntos de registros, vea los artículos [Recordset: Scrolling (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) y [Recordset: Bookmarks and Absolute Positions (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md). Para obtener más información sobre la obtención masiva de filas, vea el artículo [Conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md). Para obtener información relacionada, `SQLExtendedFetch` consulte la función de API ODBC en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDatabase#28](../../mfc/codesnippet/cpp/crecordset-class_14.cpp)]

## <a name="crecordsetmovefirst"></a><a name="movefirst"></a>CRecordset::MoveFirst

Convierte el primer registro del primer conjunto de filas en el registro actual.

```cpp
void MoveFirst();
```

### <a name="remarks"></a>Observaciones

Independientemente de si se ha implementado la obtención masiva de filas, este siempre será el primer registro del conjunto de registros.

No es necesario `MoveFirst` llamar inmediatamente después de abrir el conjunto de registros. En ese momento, el primer registro (si existe) es automáticamente el registro actual.

> [!NOTE]
> Esta función miembro no es válida para conjuntos de registros de solo avance.

> [!NOTE]
> Cuando se mueve a través de un conjunto de registros, no se pueden omitir los registros eliminados. Consulte el [IsDeleted](#isdeleted) función miembro para obtener más información.

> [!CAUTION]
> Al llamar `Move` a cualquiera de las funciones se produce una excepción si el conjunto de registros no tiene registros. Para determinar si el conjunto `IsBOF` de `IsEOF`registros tiene registros, llame y .

> [!NOTE]
> Si llama a `Move` cualquiera de las funciones mientras se actualiza o agrega el registro actual, las actualizaciones se pierden sin previo aviso.

Para obtener más información acerca de la navegación de conjuntos de registros, vea los artículos [Recordset: Scrolling (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) y [Recordset: Bookmarks and Absolute Positions (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md). Para obtener más información sobre la obtención masiva de filas, vea el artículo [Conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

### <a name="example"></a>Ejemplo

  Vea el ejemplo [de IsBOF](#isbof).

## <a name="crecordsetmovelast"></a><a name="movelast"></a>CRecordset::MoveLast

Convierte el primer registro del último conjunto de filas completo en el registro actual.

```cpp
void MoveLast();
```

### <a name="remarks"></a>Observaciones

Si no ha implementado la obtención masiva de filas, el `MoveLast` conjunto de registros tiene un tamaño de conjunto de filas de 1, por lo que simplemente se mueve al último registro del conjunto de registros.

> [!NOTE]
> Esta función miembro no es válida para conjuntos de registros de solo avance.

> [!NOTE]
> Cuando se mueve a través de un conjunto de registros, no se pueden omitir los registros eliminados. Consulte el [IsDeleted](#isdeleted) función miembro para obtener más información.

> [!CAUTION]
> Al llamar `Move` a cualquiera de las funciones se produce una excepción si el conjunto de registros no tiene registros. Para determinar si el conjunto `IsBOF` de `IsEOF`registros tiene registros, llame y .

> [!NOTE]
> Si llama a `Move` cualquiera de las funciones mientras se actualiza o agrega el registro actual, las actualizaciones se pierden sin previo aviso.

Para obtener más información acerca de la navegación de conjuntos de registros, vea los artículos [Recordset: Scrolling (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) y [Recordset: Bookmarks and Absolute Positions (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md). Para obtener más información sobre la obtención masiva de filas, vea el artículo [Conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

### <a name="example"></a>Ejemplo

  Vea el ejemplo [de IsBOF](#isbof).

## <a name="crecordsetmovenext"></a><a name="movenext"></a>CRecordset::MoveNext

Convierte el primer registro del siguiente conjunto de filas en el registro actual.

```cpp
void MoveNext();
```

### <a name="remarks"></a>Observaciones

Si no ha implementado la obtención masiva de filas, el `MoveNext` conjunto de registros tiene un tamaño de conjunto de filas de 1, por lo que simplemente se mueve al siguiente registro.

> [!NOTE]
> Cuando se mueve a través de un conjunto de registros, no se pueden omitir los registros eliminados. Consulte el [IsDeleted](#isdeleted) función miembro para obtener más información.

> [!CAUTION]
> Al llamar `Move` a cualquiera de las funciones se produce una excepción si el conjunto de registros no tiene registros. Para determinar si el conjunto `IsBOF` de `IsEOF`registros tiene registros, llame y .

> [!NOTE]
> También se recomienda que `IsEOF` llame `MoveNext`antes de llamar a . Por ejemplo, si se ha desplazado más `IsEOF` allá del final del conjunto de registros, devolverá distinto de cero; una llamada `MoveNext` posterior a produciría una excepción.

> [!NOTE]
> Si llama a `Move` cualquiera de las funciones mientras se actualiza o agrega el registro actual, las actualizaciones se pierden sin previo aviso.

Para obtener más información acerca de la navegación de conjuntos de registros, vea los artículos [Recordset: Scrolling (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) y [Recordset: Bookmarks and Absolute Positions (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md). Para obtener más información sobre la obtención masiva de filas, vea el artículo [Conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

### <a name="example"></a>Ejemplo

  Vea el ejemplo [de IsBOF](#isbof).

## <a name="crecordsetmoveprev"></a><a name="moveprev"></a>CRecordset::MovePrev

Convierte el primer registro del conjunto de filas anterior en el registro actual.

```cpp
void MovePrev();
```

### <a name="remarks"></a>Observaciones

Si no ha implementado la obtención masiva de filas, el `MovePrev` conjunto de registros tiene un tamaño de conjunto de filas de 1, por lo que simplemente se mueve al registro anterior.

> [!NOTE]
> Esta función miembro no es válida para conjuntos de registros de solo avance.

> [!NOTE]
> Cuando se mueve a través de un conjunto de registros, no se pueden omitir los registros eliminados. Consulte el [IsDeleted](#isdeleted) función miembro para obtener más información.

> [!CAUTION]
> Al llamar `Move` a cualquiera de las funciones se produce una excepción si el conjunto de registros no tiene registros. Para determinar si el conjunto `IsBOF` de `IsEOF`registros tiene registros, llame y .

> [!NOTE]
> También se recomienda que `IsBOF` llame `MovePrev`antes de llamar a . Por ejemplo, si se ha desplazado antes del `IsBOF` principio del conjunto de registros, devolverá distinto de cero; una llamada `MovePrev` posterior a produciría una excepción.

> [!NOTE]
> Si llama a `Move` cualquiera de las funciones mientras se actualiza o agrega el registro actual, las actualizaciones se pierden sin previo aviso.

Para obtener más información acerca de la navegación de conjuntos de registros, vea los artículos [Recordset: Scrolling (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) y [Recordset: Bookmarks and Absolute Positions (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md). Para obtener más información sobre la obtención masiva de filas, vea el artículo [Conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

### <a name="example"></a>Ejemplo

  Vea el ejemplo [de IsBOF](#isbof).

## <a name="crecordsetonsetoptions"></a><a name="onsetoptions"></a>CRecordset::OnSetOptions

Se llama para establecer opciones (utilizadas en la selección) para la instrucción ODBC especificada.

```
virtual void OnSetOptions(HSTMT hstmt);
```

### <a name="parameters"></a>Parámetros

*hstmt*<br/>
El HSTMT de la instrucción ODBC cuyas opciones se deben establecer.

### <a name="remarks"></a>Observaciones

Llame `OnSetOptions` para establecer opciones (utilizadas en la selección) para la instrucción ODBC especificada. El marco de trabajo llama a esta función miembro para establecer las opciones iniciales para el conjunto de registros. `OnSetOptions`determina la compatibilidad del origen de datos para cursores desplazables y para la simultaneidad de cursores y establece las opciones del conjunto de registros en consecuencia. (Mientras `OnSetOptions` que se utiliza `OnSetUpdateOptions` para las operaciones de selección, se utiliza para las operaciones de actualización.)

Reemplazar `OnSetOptions` para establecer opciones específicas para el controlador o el origen de datos. Por ejemplo, si el origen de datos admite `OnSetOptions` la apertura para el acceso exclusivo, puede invalidar para aprovechar esa capacidad.

Para obtener más información acerca de los cursores, vea el artículo [ODBC](../../data/odbc/odbc-basics.md).

## <a name="crecordsetonsetupdateoptions"></a><a name="onsetupdateoptions"></a>CRecordset::OnSetUpdateOptions

Se llama para establecer opciones (utilizadas en la actualización) para la instrucción ODBC especificada.

```
virtual void OnSetUpdateOptions(HSTMT hstmt);
```

### <a name="parameters"></a>Parámetros

*hstmt*<br/>
El HSTMT de la instrucción ODBC cuyas opciones se deben establecer.

### <a name="remarks"></a>Observaciones

Llame `OnSetUpdateOptions` para establecer opciones (utilizadas en la actualización) para la instrucción ODBC especificada. El marco de trabajo llama a esta función miembro después de crear un HSTMT para actualizar los registros en un conjunto de registros. (Mientras `OnSetOptions` que se utiliza `OnSetUpdateOptions` para las operaciones de selección, se utiliza para las operaciones de actualización.) `OnSetUpdateOptions` determina la compatibilidad del origen de datos para cursores desplazables y para la simultaneidad de cursores y establece las opciones del conjunto de registros en consecuencia.

Reemplazar `OnSetUpdateOptions` para establecer opciones de una instrucción ODBC antes de que esa instrucción se use para tener acceso a una base de datos.

Para obtener más información acerca de los cursores, vea el artículo [ODBC](../../data/odbc/odbc-basics.md).

## <a name="crecordsetopen"></a><a name="open"></a>CRecordset::Open

Abre el conjunto de registros recuperando la tabla o realizando la consulta que el conjunto de registros representa.

```
virtual BOOL Open(
    UINT nOpenType = AFX_DB_USE_DEFAULT_TYPE,
    LPCTSTR lpszSQL = NULL,
    DWORD dwOptions = none);
```

### <a name="parameters"></a>Parámetros

*nOpenType*<br/>
Acepte el valor predeterminado, AFX_DB_USE_DEFAULT_TYPE o utilice uno `enum OpenType`de los siguientes valores de:

- `CRecordset::dynaset`Un conjunto de registros con desplazamiento bidireccional. La pertenencia y el orden de los registros se determinan cuando se abre el conjunto de registros, pero los cambios realizados por otros usuarios en los valores de datos son visibles después de una operación de búsqueda. Los dynasets también se conocen como conjuntos de registros conjunto controlados por conjuntos de claves.

- `CRecordset::snapshot`Un conjunto de registros estático con desplazamiento bidireccional. La pertenencia y el orden de los registros se determinan cuando se abre el conjunto de registros; los valores de datos se determinan cuando se buscan los registros. Los cambios realizados por otros usuarios no son visibles hasta que no se cierra y se vuelve a abrir el conjunto de registros.

- `CRecordset::dynamic`Un conjunto de registros con desplazamiento bidireccional. Los cambios realizados por otros usuarios en la pertenencia, el orden y los valores de datos son visibles después de una operación de recuperación de cambios. Tenga en cuenta que muchos controladores ODBC no admiten este tipo de conjunto de registros.

- `CRecordset::forwardOnly`Un conjunto de registros de solo lectura con solo desplazamiento hacia delante.

   Para `CRecordset`, el `CRecordset::snapshot`valor predeterminado es . El mecanismo de valor predeterminado permite que los asistentes de Visual C++ interactúen con `CRecordset` de ODBC y `CDaoRecordset` de DAO, que tienen valores predeterminados diferentes.

Para obtener más información acerca de estos tipos de conjunto de registros, vea el artículo [Conjunto de registros (ODBC)](../../data/odbc/recordset-odbc.md). Para obtener información relacionada, vea el artículo "Uso de cursores de bloque y desplazables" en el Windows SDK.

> [!CAUTION]
> Si el tipo solicitado no se admite, el marco de trabajo produce una excepción.

*lpszSQL*<br/>
Puntero de cadena que contiene uno de los elementos siguientes:

- Un puntero NULL.

- Nombre de una tabla.

- Una instrucción **SELECT** de SQL (opcionalmente con una cláusula **WHERE** u **ORDER BY** de SQL).

- Una instrucción **CALL** que especifica el nombre de una consulta predefinida (procedimiento almacenado). Tenga cuidado de no insertar espacios en blanco entre la llave y la palabra clave **CALL.**

Para obtener más información acerca de esta cadena, vea la tabla y la explicación del rol de ClassWizard en la sección [Comentarios.](#remarks)

> [!NOTE]
> El orden de las columnas del conjunto de resultados debe coincidir con el orden de las llamadas de función RFX o RFX masivas en la invalidación de la función [DoFieldExchange](#dofieldexchange) o [DoBulkFieldExchange.](#dobulkfieldexchange)

*dwOptions*<br/>
Máscara de bits que puede especificar una combinación de los valores que se muestran a continuación. Algunas de estas opciones son mutuamente excluyentes. El valor predeterminado es **none**.

- `CRecordset::none`No hay opciones establecidas. Este valor del parámetro es mutuamente excluyente con todos los demás valores. De forma predeterminada, el conjunto de registros se puede actualizar con [Editar](#edit) o [Eliminar](#delete) y permite anexar nuevos registros con [AddNew](#addnew). La capacidad de actualización depende del origen de datos, así como de la opción *nOpenType* que especifique. La optimización para adiciones masivas no está disponible. La obtención masiva de filas no se implementará. Los registros eliminados no se omitirán al navegar por el conjunto de registros. Los marcadores no están disponibles. Se implementa la comprobación automática de campos modificados.

- `CRecordset::appendOnly`No permitir `Edit` `Delete` o en el conjunto de registros. Solo permite `AddNew`. Esta opción es mutuamente excluyente con `CRecordset::readOnly`.

- `CRecordset::readOnly`Abra el conjunto de registros como de solo lectura. Esta opción es mutuamente excluyente con `CRecordset::appendOnly`.

- `CRecordset::optimizeBulkAdd`Use una instrucción SQL preparada para optimizar la adición de muchos registros a la vez. Solo se aplica si no utiliza `SQLSetPos` la función de API ODBC para actualizar el conjunto de registros. La primera actualización determina qué campos se marcan como modificados. Esta opción es mutuamente excluyente con `CRecordset::useMultiRowFetch`.

- `CRecordset::useMultiRowFetch`Implemente la obtención masiva de filas para permitir que se recuperen varias filas en una sola operación de obtención. Se trata de una característica avanzada diseñada para mejorar el rendimiento; sin embargo, el Asistente para clases no admite el intercambio masivo de campos de registros. Esta opción es mutuamente excluyente con `CRecordset::optimizeBulkAdd`. Tenga en cuenta `CRecordset::useMultiRowFetch`que si `CRecordset::noDirtyFieldCheck` especifica , la opción se encenderá automáticamente (el almacenamiento en búfer doble no estará disponible); en conjuntos de registros `CRecordset::useExtendedFetch` de solo avance, la opción se encenderá automáticamente. Para obtener más información sobre la obtención masiva de filas, vea el artículo [Conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

- `CRecordset::skipDeletedRecords`Omita todos los registros eliminados al navegar por el conjunto de registros. Esto ralentiza el rendimiento en ciertas búsquedas relativas. Esta opción no es válida en los conjuntos de registros solo hacia delante. Si llama a [Move](#move) con el parámetro *nRows* establecido en 0 y el `CRecordset::skipDeletedRecords` conjunto de opciones, `Move` afirmará. Tenga `CRecordset::skipDeletedRecords` en cuenta que es similar al empaquetado del *controlador,* lo que significa que las filas eliminadas se quitan del conjunto de registros. Sin embargo, si el controlador empaqueta registros, solo se omitirán los registros que elimine; no se omitirán los registros eliminados por otros usuarios mientras el conjunto de registros está abierto. `CRecordset::skipDeletedRecords`omitirá las filas eliminadas por otros usuarios.

- `CRecordset::useBookmarks`Puede usar marcadores en el conjunto de registros, si se admite. Los marcadores ralentizan la recuperación de datos pero mejoran el rendimiento de la navegación de datos. No es válida en conjuntos de registros solo hacia delante. Para obtener más información, vea el artículo [Conjunto de registros: marcadores y posiciones absolutas (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md).

- `CRecordset::noDirtyFieldCheck`Desactive la comprobación automática de campos sucios (doble almacenamiento en búfer). Esto mejorará el rendimiento; sin embargo, para marcar manualmente los campos como modificados se debe llamar a las funciones miembro `SetFieldDirty` y `SetFieldNull`. Tenga en cuenta que el almacenamiento en búfer doble en la clase `CRecordset` es similar al almacenamiento en búfer doble en la clase `CDaoRecordset`. Sin embargo, en `CRecordset`, no se puede habilitar el almacenamiento en búfer doble en campos individuales; hay que habilitarlo o deshabilitarlo para todos los campos. Tenga en cuenta que `CRecordset::useMultiRowFetch`si `CRecordset::noDirtyFieldCheck` especifica la opción , se encenderá automáticamente; sin `SetFieldDirty` `SetFieldNull` embargo, y no se puede usar en conjuntos de registros que implementan la obtención masiva de filas.

- `CRecordset::executeDirect`No utilice una instrucción SQL preparada. Para mejorar el rendimiento, `Requery` especifique esta opción si nunca se llamará a la función miembro.

- `CRecordset::useExtendedFetch`Implementar `SQLExtendedFetch` en `SQLFetch`lugar de . Está diseñado para implementar la obtención masiva de filas en conjuntos de registros solo hacia delante. Si especifica la `CRecordset::useMultiRowFetch` opción en un conjunto `CRecordset::useExtendedFetch` de registros de solo avance, se encenderá automáticamente.

- `CRecordset::userAllocMultiRowBuffers`El usuario asignará búferes de almacenamiento para los datos. Utilice esta opción junto con `CRecordset::useMultiRowFetch` si desea asignar su propio almacenamiento; de lo contrario, el marco de trabajo asignará automáticamente el almacenamiento necesario. Para obtener más información, vea el artículo [Conjunto de registros: obtención de registros en masa (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md). Tenga en `CRecordset::userAllocMultiRowBuffers` cuenta que `CRecordset::useMultiRowFetch` especificar sin especificar dará lugar a una aserción con errores.

### <a name="return-value"></a>Valor devuelto

Distinto de `CRecordset` cero si el objeto se abrió correctamente; de lo contrario 0 si [CDatabase::Open](../../mfc/reference/cdatabase-class.md#open) (si se llama) devuelve 0.

### <a name="remarks"></a>Observaciones

Se debe llamar a esta función miembro para ejecutar la consulta definida por el conjunto de registros. Antes `Open`de llamar a , debe construir el objeto de conjunto de registros.

La conexión de este conjunto de registros con el `Open`origen de datos depende de cómo se construye el conjunto de registros antes de llamar a . Si pasa un [CDatabase](../../mfc/reference/cdatabase-class.md) objeto al constructor de conjunto de registros que no se ha conectado al origen de datos, esta función miembro utiliza [GetDefaultConnect](#getdefaultconnect) para intentar abrir el objeto de base de datos. Si pasa NULL al constructor del conjunto `CDatabase` de registros, `Open` el constructor construye un objeto automáticamente e intenta conectar el objeto de base de datos. Para obtener más información sobre cómo cerrar el conjunto de registros y la conexión en estas circunstancias variables, consulte [Cerrar](#close).

> [!NOTE]
> El acceso a un origen de datos mediante un objeto `CRecordset` siempre es compartido. A diferencia de la clase `CDaoRecordset`, no se puede utilizar un objeto `CRecordset` para abrir un origen de datos con acceso exclusivo.

Cuando se `Open`llama a , una consulta, normalmente una instrucción **SELECT** de SQL, selecciona registros en función de los criterios que se muestran en la tabla siguiente.

|Valor del parámetro lpszSQL|Los registros seleccionados están determinados por|Ejemplo|
|------------------------------------|----------------------------------------|-------------|
|NULL|La cadena devuelta por `GetDefaultSQL`.||
|Nombre de tabla SQL|Todas las columnas de la lista de tablas de `DoFieldExchange` o `DoBulkFieldExchange`.|`"Customer"`|
|Nombre de la consulta (procedimiento almacenado) predefinida|Las columnas de la consulta cuya devolución se ha definido.|`"{call OverDueAccts}"`|
|**SELECT** column-list **FROM** table-list|Las columnas especificadas de las tablas indicadas.|`"SELECT CustId, CustName FROM`<br /><br /> `Customer"`|

> [!CAUTION]
> Tenga cuidado de no insertar espacios en blanco adicionales en la cadena SQL. Por ejemplo, si inserta espacios en blanco entre la llave y la palabra clave **CALL,** MFC malinterpretará la cadena SQL como un nombre de tabla e incorporará en una instrucción **SELECT,** lo que dará lugar a una excepción que se produce. Del mismo modo, si la consulta predefinida utiliza un parámetro de salida, no inserte espacios en blanco entre la llave y el símbolo ''. Por último, no debe insertar espacios en blanco antes de la llave en una instrucción **CALL** o antes de la palabra clave **SELECT** en una instrucción **SELECT.**

El procedimiento habitual es `Open`pasar NULL a ; en este `Open` caso, llama a [GetDefaultSQL](#getdefaultsql). Si utiliza una clase `CRecordset` derivada, `GetDefaultSQL` proporciona los nombres de tabla especificados en ClassWizard. Se puede especificar otra información en el parámetro `lpszSQL`.

Pase lo `Open` que pase, construye una cadena SQL final para la consulta (la cadena `lpszSQL` puede tener cláusulas SQL **WHERE** y ORDER **BY** anexadas a la cadena que ha pasado) y, a continuación, ejecuta la consulta. Puede examinar la cadena construida llamando a `Open` [GetSQL](#getsql) después de llamar a . Para obtener más información sobre cómo el conjunto de registros construye una instrucción SQL y selecciona registros, vea el artículo Conjunto de registros: cómo los conjuntos de [registros seleccionan registros (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md).

Los miembros de datos de campo de la clase de conjunto de registros están enlazados a las columnas de los datos seleccionados. Si se devuelve algún registro, el primer registro se convierte en el registro actual.

Si desea establecer opciones para el conjunto de registros, como un filtro u ordenación, estibrérelas después de construir el objeto de conjunto de registros pero antes de llamar a `Open`. Si desea actualizar los registros del conjunto de registros después de que el conjunto de registros ya esté abierto, llame a [Requery](#requery).

Para obtener más información, incluidos ejemplos adicionales, vea los artículos [Recordset (ODBC)](../../data/odbc/recordset-odbc.md), [Recordset: How Recordsets Select Records (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)y [Recordset: Creating and Closing Recordsets (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md).

### <a name="example"></a>Ejemplo

Los siguientes ejemplos de código `Open` muestran diferentes formas de la llamada.

[!code-cpp[NVC_MFCDatabase#16](../../mfc/codesnippet/cpp/crecordset-class_15.cpp)]

## <a name="crecordsetrefreshrowset"></a><a name="refreshrowset"></a>CRecordset::RefreshRowset

Actualiza los datos y el estado de una fila del conjunto de filas actual.

```cpp
void RefreshRowset(
    WORD wRow,
    WORD wLockType = SQL_LOCK_NO_CHANGE);
```

### <a name="parameters"></a>Parámetros

*wRow*<br/>
Posición basada en uno de una fila en el conjunto de filas actual. Este valor puede variar de cero al tamaño del conjunto de filas.

*wLockType*<br/>
Valor que indica cómo bloquear la fila después de que se haya actualizado. Para conocer más detalles, vea la sección Comentarios.

### <a name="remarks"></a>Observaciones

Si pasa un valor de cero para *wRow*, se actualizará cada fila del conjunto de filas.

Para `RefreshRowset`usar , debe haber implementado la obtención `CRecordset::useMulitRowFetch` masiva de filas especificando la opción en el [Open](#open) función miembro.

`RefreshRowset`llama a la `SQLSetPos`función de API ODBC . El parámetro *wLockType* especifica el estado `SQLSetPos` de bloqueo de la fila después de que se haya ejecutado. En la tabla siguiente se describen los valores posibles para *wLockType*.

|wLockType|Descripción|
|---------------|-----------------|
|SQL_LOCK_NO_CHANGE (el valor predeterminado)|El controlador o el origen de datos garantiza que la fila `RefreshRowset` está en el mismo estado bloqueado o desbloqueado que antes se llamó.|
|SQL_LOCK_EXCLUSIVE|El controlador o el origen de datos bloquea la fila exclusivamente. No todos los orígenes de datos admiten este tipo de bloqueo.|
|SQL_LOCK_UNLOCK|El controlador o el origen de datos desbloquea la fila. No todos los orígenes de datos admiten este tipo de bloqueo.|

Para obtener `SQLSetPos`más información acerca de , consulte el Windows SDK. Para obtener más información sobre la obtención masiva de filas, vea el artículo [Conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

## <a name="crecordsetrequery"></a><a name="requery"></a>CRecordset::Requery

Reconstruye (actualiza) un conjunto de registros.

```
virtual BOOL Requery();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el conjunto de registros se reconstruyó correctamente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Si se devuelve algún registro, el primer registro se convierte en el registro actual.

Para que el conjunto de registros refleje las adiciones y eliminaciones que usted u `Requery`otros usuarios están realizando en el origen de datos, debe volver a generar el conjunto de registros llamando a . Si el conjunto de registros es un conjunto de registros dinámicos, refleja automáticamente las actualizaciones que usted u otros usuarios realizan en sus registros existentes (pero no en las adiciones). Si el conjunto de registros `Requery` es una instantánea, debe llamar para reflejar las ediciones de otros usuarios, así como las adiciones y eliminaciones.

Para un conjunto de registros `Requery` dinámicos o una instantánea, llame a cualquier momento que desee volver a generar el conjunto de registros mediante un nuevo filtro u ordenación, o nuevos valores de parámetro. Establezca la nueva propiedad filter u `m_strFilter` sort `m_strSort` asignando nuevos valores a y antes de llamar a `Requery`. Establezca nuevos parámetros asignando nuevos valores `Requery`a los miembros de datos de parámetro antes de llamar a . Si las cadenas de filtro y ordenación no cambian, puede reutilizar la consulta, lo que mejora el rendimiento.

Si se produce un error en el intento de volver a generar el conjunto de registros, el conjunto de registros se cierra. Antes de `Requery`llamar a , puede determinar si se `CanRestart` puede volver a consultar el conjunto de registros llamando a la función miembro. `CanRestart`no garantiza `Requery` que tendrá éxito.

> [!CAUTION]
> Llame `Requery` sólo después de haber llamado [a Abrir](#open).

### <a name="example"></a>Ejemplo

En este ejemplo se vuelve a generar un conjunto de registros para aplicar un criterio de ordenación diferente.

[!code-cpp[NVC_MFCDatabase#29](../../mfc/codesnippet/cpp/crecordset-class_16.cpp)]

## <a name="crecordsetsetabsoluteposition"></a><a name="setabsoluteposition"></a>CRecordset::SetAbsolutePosition

Coloca el conjunto de registros en el registro correspondiente al número de registro especificado.

```cpp
void SetAbsolutePosition(long nRows);
```

### <a name="parameters"></a>Parámetros

*nRows*<br/>
Posición ordinal basada en uno para el registro actual en el conjunto de registros.

### <a name="remarks"></a>Observaciones

`SetAbsolutePosition`mueve el puntero de registro actual en función de esta posición ordinal.

> [!NOTE]
> Esta función miembro no es válida en conjuntos de registros de solo avance.

Para los conjuntos de registros ODBC, un valor de posición absoluta de 1 hace referencia al primer registro del conjunto de registros; un valor de 0 se refiere a la posición de inicio de archivo (BOF).

También puede pasar valores `SetAbsolutePosition`negativos a . En este caso, la posición del conjunto de registros se evalúa desde el final del conjunto de registros. Por ejemplo, `SetAbsolutePosition( -1 )` mueve el puntero de registro actual al último registro del conjunto de registros.

> [!NOTE]
> La posición absoluta no está diseñada para utilizarse como un número de registro suplente. Los marcadores siguen siendo la forma recomendada de conservar y volver a una posición determinada, ya que la posición de un registro cambia cuando se eliminan los registros anteriores. Además, no puede estar seguro de que un registro determinado tendrá la misma posición absoluta si el conjunto de registros se vuelve a crear porque el orden de los registros individuales dentro de un conjunto de registros no está garantizado a menos que se cree con una instrucción SQL mediante una cláusula **ORDER BY.**

Para obtener más información acerca de la navegación de conjuntos de registros y marcadores, vea los artículos [Recordset: Scrolling (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) y [Recordset: Bookmarks and Absolute Positions (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md).

## <a name="crecordsetsetbookmark"></a><a name="setbookmark"></a>CRecordset::SetBookmark

Coloca el conjunto de registros en el registro que contiene el marcador especificado.

```cpp
void SetBookmark(const CDBVariant& varBookmark);
```

### <a name="parameters"></a>Parámetros

*varBookmark*<br/>
Una referencia a un [CDBVariant](../../mfc/reference/cdbvariant-class.md) objeto que contiene el valor de marcador para un registro específico.

### <a name="remarks"></a>Observaciones

Para determinar si los marcadores son compatibles con el conjunto de registros, llame a [CanBookmark](#canbookmark). Para que los marcadores estén disponibles `CRecordset::useBookmarks` si son compatibles, debe establecer la opción en el parámetro *dwOptions* de [la](#open) open función miembro.

> [!NOTE]
> Si los marcadores no son `SetBookmark` compatibles o no están disponibles, la llamada dará lugar a una excepción que se produce. Los marcadores no se admiten en conjuntos de registros de solo avance.

Para recuperar primero el marcador para el registro actual, llame a `CDBVariant` [GetBookmark](#getbookmark), que guarda el valor del marcador en un objeto. Más adelante, puede volver a `SetBookmark` ese registro llamando al valor de marcador guardado.

> [!NOTE]
> Después de ciertas operaciones de conjunto `SetBookmark`de registros, debe comprobar la persistencia del marcador antes de llamar a . Por ejemplo, si recupera `GetBookmark` un marcador `Requery`con y, a continuación, llama a , es posible que el marcador ya no sea válido. Llame a [CDatabase::GetBookmarkPersistence](../../mfc/reference/cdatabase-class.md#getbookmarkpersistence) para comprobar `SetBookmark`si puede llamar de forma segura .

Para obtener más información acerca de los marcadores y la navegación de conjuntos de registros, vea los artículos Conjunto de [registros: marcadores y posiciones absolutas (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md) y [Conjunto de registros: desplazamiento (ODBC)](../../data/odbc/recordset-scrolling-odbc.md).

## <a name="crecordsetsetfielddirty"></a><a name="setfielddirty"></a>CRecordset::SetFieldDirty

Marca un miembro de datos de campo del conjunto de registros como modificado o como sin cambios.

```cpp
void SetFieldDirty(void* pv, BOOL bDirty = TRUE);
```

### <a name="parameters"></a>Parámetros

*Pv*<br/>
Contiene la dirección de un miembro de datos de campo en el conjunto de registros o NULL. Si NULL, se marcan todos los miembros de datos de campo del conjunto de registros. (C++ NULL no es lo mismo que Null en la terminología de la base de datos, lo que significa "no tener ningún valor.")

*bDirty*<br/>
TRUESi el miembro de datos de campo debe marcarse como "sucio" (cambiado). De lo contrario, FALSE si el miembro de datos de campo debe marcarse como "limpio" (sin cambios).

### <a name="remarks"></a>Observaciones

Marcar los campos como sin cambios garantiza que el campo no se actualiza y da como resultado menos tráfico SQL.

> [!NOTE]
> Esta función miembro no es aplicable en conjuntos de registros que usan la obtención masiva de filas. Si ha implementado la obtención `SetFieldDirty` masiva de filas, se producirá un error en la aserción. Para obtener más información sobre la obtención masiva de filas, vea el artículo [Conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Las marcas de marco cambiaron los miembros de datos de campo para asegurarse de que se escribirán en el registro en el origen de datos mediante el mecanismo de intercambio de campos de registros (RFX). Cambiar el valor de un campo generalmente establece el campo sucio `SetFieldDirty` automáticamente, por lo que rara vez tendrá que llamarse a sí mismo, pero a veces es posible que desee asegurarse de que las columnas se actualizarán o insertarán explícitamente independientemente de qué valor se encuentre en el miembro de datos de campo.

> [!CAUTION]
> Llame a esta función miembro solo después de haber llamado a [Edit](#edit) o [AddNew](#addnew).

El uso de NULL para el primer argumento `outputColumn` de `param` la función aplicará la función solo a los campos, no a los campos. Por ejemplo, la llamada

[!code-cpp[NVC_MFCDatabase#26](../../mfc/codesnippet/cpp/crecordset-class_10.cpp)]

establecerá solo `outputColumn` los campos en NULL; `param` los campos no se verán afectados.

Para trabajar `param` en campos, debe proporcionar la `param` dirección real de la persona en la que desea trabajar, como:

[!code-cpp[NVC_MFCDatabase#27](../../mfc/codesnippet/cpp/crecordset-class_11.cpp)]

Esto significa que `param` no puede establecer todos `outputColumn` los campos en NULL, como puede hacer con los campos.

## <a name="crecordsetsetfieldnull"></a><a name="setfieldnull"></a>CRecordset::SetFieldNull

Marca un miembro de datos de campo del conjunto de registros como Null (específicamente sin valor) o como no nulo.

```cpp
void SetFieldNull(void* pv, BOOL bNull = TRUE);
```

### <a name="parameters"></a>Parámetros

*Pv*<br/>
Contiene la dirección de un miembro de datos de campo en el conjunto de registros o NULL. Si NULL, se marcan todos los miembros de datos de campo del conjunto de registros. (C++ NULL no es lo mismo que Null en la terminología de la base de datos, lo que significa "no tener ningún valor.")

*bNull*<br/>
Distinto de cero si el miembro de datos de campo se marca como que no tiene ningún valor (Null). De lo contrario, 0 si el miembro de datos de campo se va a marcar como no nulo.

### <a name="remarks"></a>Observaciones

Cuando se agrega un nuevo registro a un conjunto de registros, todos los miembros de datos de campo se establecen inicialmente en un valor Null y se marcan como "sucio" (cambiado). Cuando se recupera un registro de un origen de datos, sus columnas ya tienen valores o son Null.

> [!NOTE]
> No llame a esta función miembro en conjuntos de registros que usan la obtención masiva de filas. Si ha implementado la obtención `SetFieldNull` masiva de filas, la llamada da como resultado una aserción con errores. Para obtener más información sobre la obtención masiva de filas, vea el artículo [Conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Si desea designar específicamente un campo del registro actual como `SetFieldNull` que no tiene un valor, llame con *bNull* establecido en TRUE para marcarlo como Null. Si un campo se marcó anteriormente como Null y ahora desea darle un valor, simplemente establezca su nuevo valor. No es necesario quitar la `SetFieldNull`marca Null con . Para determinar si el campo puede `IsFieldNullable`ser Null, llame a .

> [!CAUTION]
> Llame a esta función miembro solo después de haber llamado a [Edit](#edit) o [AddNew](#addnew).

El uso de NULL para el primer argumento `outputColumn` de `param` la función aplicará la función solo a los campos, no a los campos. Por ejemplo, la llamada

[!code-cpp[NVC_MFCDatabase#26](../../mfc/codesnippet/cpp/crecordset-class_10.cpp)]

establecerá solo `outputColumn` los campos en NULL; `param` los campos no se verán afectados.

Para trabajar `param` en campos, debe proporcionar la `param` dirección real de la persona en la que desea trabajar, como:

[!code-cpp[NVC_MFCDatabase#27](../../mfc/codesnippet/cpp/crecordset-class_11.cpp)]

Esto significa que `param` no puede establecer todos `outputColumn` los campos en NULL, como puede hacer con los campos.

> [!NOTE]
> Al establecer parámetros en `SetFieldNull` Null, una llamada a antes de abrir el conjunto de registros da como resultado una aserción. En este caso, llame a [SetParamNull](#setparamnull).

`SetFieldNull`se implementa a través de [DoFieldExchange](#dofieldexchange).

## <a name="crecordsetsetlockingmode"></a><a name="setlockingmode"></a>CRecordset::SetLockingMode

Establece el modo de bloqueo en bloqueo "optimista" (valor predeterminado) o bloqueo "pesimista". Determina cómo se bloquean los registros para las actualizaciones.

```cpp
void SetLockingMode(UINT nMode);
```

### <a name="parameters"></a>Parámetros

*nMode*<br/>
Contiene uno de los `enum LockMode`siguientes valores de:

- `optimistic`El bloqueo optimista bloquea el registro `Update`que se actualiza solo durante la llamada a .

- `pessimistic`El bloqueo pesimista bloquea el `Edit` registro tan pronto como `Update` se llama y lo mantiene bloqueado hasta que se completa la llamada o se mueve a un nuevo registro.

### <a name="remarks"></a>Observaciones

Llame a esta función miembro si necesita especificar cuál de las dos estrategias de bloqueo de registros que usa el conjunto de registros para las actualizaciones. De forma predeterminada, el modo `optimistic`de bloqueo de un conjunto de registros es . Puede cambiarlo a una `pessimistic` estrategia de bloqueo más cautelosa. Llame `SetLockingMode` después de construir y abrir `Edit`el objeto de conjunto de registros, pero antes de llamar a .

## <a name="crecordsetsetparamnull"></a><a name="setparamnull"></a>CRecordset::SetParamNull

Marca un parámetro como Null (específicamente sin valor) o como no Null.

```cpp
void SetParamNull(
    int nIndex,
    BOOL bNull = TRUE);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Índice de base cero del parámetro.

*bNull*<br/>
Si TRUE (el valor predeterminado), el parámetro se marca como Null. De lo contrario, el parámetro se marca como no Null.

### <a name="remarks"></a>Observaciones

A diferencia de [SetFieldNull](#setfieldnull), puede llamar `SetParamNull` antes de abrir el conjunto de registros.

`SetParamNull`normalmente se utiliza con consultas predefinidas (procedimientos almacenados).

## <a name="crecordsetsetrowsetcursorposition"></a><a name="setrowsetcursorposition"></a>CRecordset::SetRowsetCursorPosition

Mueve el cursor a una fila dentro del conjunto de filas actual.

```cpp
void SetRowsetCursorPosition(WORD wRow, WORD wLockType = SQL_LOCK_NO_CHANGE);
```

### <a name="parameters"></a>Parámetros

*wRow*<br/>
Posición basada en uno de una fila en el conjunto de filas actual. Este valor puede oscilar entre 1 y el tamaño del conjunto de filas.

*wLockType*<br/>
Valor que indica cómo bloquear la fila después de que se haya actualizado. Para conocer más detalles, vea la sección Comentarios.

### <a name="remarks"></a>Observaciones

Al implementar la obtención masiva de filas, los conjuntos de filas recuperan los registros, donde el primer registro del conjunto de filas capturado es el registro actual. Para convertir otro registro dentro del conjunto `SetRowsetCursorPosition`de filas en el registro actual, llame a . Por ejemplo, puede `SetRowsetCursorPosition` combinar con el [GetFieldValue](#getfieldvalue) función miembro para recuperar dinámicamente los datos de cualquier registro del conjunto de registros.

Para `SetRowsetCursorPosition`usar , debe haber implementado la obtención `CRecordset::useMultiRowFetch` masiva de filas especificando la opción del parámetro *dwOptions* en la función miembro [Open.](#open)

`SetRowsetCursorPosition`llama a la `SQLSetPos`función de API ODBC . El parámetro *wLockType* especifica el estado `SQLSetPos` de bloqueo de la fila después de que se haya ejecutado. En la tabla siguiente se describen los valores posibles para *wLockType*.

|wLockType|Descripción|
|---------------|-----------------|
|SQL_LOCK_NO_CHANGE (el valor predeterminado)|El controlador o el origen de datos garantiza que la fila `SetRowsetCursorPosition` está en el mismo estado bloqueado o desbloqueado que antes se llamó.|
|SQL_LOCK_EXCLUSIVE|El controlador o el origen de datos bloquea la fila exclusivamente. No todos los orígenes de datos admiten este tipo de bloqueo.|
|SQL_LOCK_UNLOCK|El controlador o el origen de datos desbloquea la fila. No todos los orígenes de datos admiten este tipo de bloqueo.|

Para obtener `SQLSetPos`más información acerca de , consulte el Windows SDK. Para obtener más información sobre la obtención masiva de filas, vea el artículo [Conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

## <a name="crecordsetsetrowsetsize"></a><a name="setrowsetsize"></a>CRecordset::SetRowsetSize

Especifica el número de registros que desea recuperar durante una captura.

```
virtual void SetRowsetSize(DWORD dwNewRowsetSize);
```

### <a name="parameters"></a>Parámetros

*dwNewRowsetSize*<br/>
El número de filas que se van a recuperar durante una captura determinada.

### <a name="remarks"></a>Observaciones

Esta función miembro virtual especifica cuántas filas desea recuperar durante una sola captura cuando se usa la obtención masiva de filas. Para implementar la obtención masiva `CRecordset::useMultiRowFetch` de filas, debe establecer la opción en el *dwOptions* parámetro de la [Open](#open) función miembro.

> [!NOTE]
> Llamar `SetRowsetSize` sin implementar la obtención masiva de filas dará lugar a una aserción con errores.

Llame `SetRowsetSize` antes `Open` de llamar para establecer inicialmente el tamaño del conjunto de filas para el conjunto de registros. El tamaño predeterminado del conjunto de filas al implementar la obtención masiva de filas es 25.

> [!NOTE]
> Tenga cuidado `SetRowsetSize`al llamar . Si va a asignar manualmente el almacenamiento para los `CRecordset::userAllocMultiRowBuffers` datos (según `Open`lo especificado por la opción del parámetro dwOptions `SetRowsetSize`en ), debe comprobar si necesita volver a asignar estos búferes de almacenamiento después de llamar a , pero antes de realizar cualquier operación de navegación del cursor.

Para obtener la configuración actual del tamaño del conjunto de filas, llame a [GetRowsetSize](#getrowsetsize).

Para obtener más información sobre la obtención masiva de filas, vea el artículo [Conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

## <a name="crecordsetupdate"></a><a name="update"></a>CRecordset::Update

Completa una `AddNew` `Edit` operación mediante la guardaguarda de los datos nuevos o editados en el origen de datos.

```
virtual BOOL Update();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si un registro se actualizó correctamente; 0 si no ha cambiado ninguna columna. Si no se actualizó ningún registro, o si se actualizó más de un registro, se produce una excepción. También se produce una excepción para cualquier otro error en el origen de datos.

### <a name="remarks"></a>Observaciones

Llame a esta función miembro después de una llamada a la [AddNew](#addnew) o [Edit](#edit) función miembro. Esta llamada es necesaria `AddNew` `Edit` para completar la operación.

> [!NOTE]
> Si ha implementado la obtención masiva `Update`de filas, no puede llamar a . Esto dará lugar a una aserción con errores. Aunque `CRecordset` la clase no proporciona un mecanismo para actualizar filas masivas de datos, puede escribir sus propias funciones mediante la función `SQLSetPos`de API ODBC . Para obtener más información sobre la obtención masiva de filas, vea el artículo [Conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

`Edit` Preparar `AddNew` un búfer de edición en el que se colocan los datos agregados o editados para guardarlos en el origen de datos. `Update`guarda los datos. Solo se actualizan los campos marcados o detectados como modificados.

Si el origen de datos admite `Update` transacciones, puede `AddNew` `Edit` hacer que la llamada (y su correspondiente o llamada) forme parte de una transacción. Para obtener más información acerca de las transacciones, vea el artículo [Transacción (ODBC)](../../data/odbc/transaction-odbc.md).

> [!CAUTION]
> Si llama `Update` sin `AddNew` llamar `Edit` `Update` primero a `CDBException`cualquiera o , lanza un archivo . Si llama `AddNew` `Edit`o , `Update` debe llamar `Move` antes de llamar a una operación o antes de cerrar el conjunto de registros o la conexión del origen de datos. De lo contrario, los cambios se pierden sin notificación.

Para obtener `Update` más información sobre el control de errores, vea el artículo Conjunto de registros: cómo los conjuntos de [registros actualizan registros (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md).

### <a name="example"></a>Ejemplo

Consulte el artículo [Transacción: realizar una transacción en un conjunto de registros (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md).

## <a name="see-also"></a>Vea también

[Clase CObject](../../mfc/reference/cobject-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clase CDatabase](../../mfc/reference/cdatabase-class.md)<br/>
[CRecordView (clase)](../../mfc/reference/crecordview-class.md)
