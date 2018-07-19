---
title: CRecordset (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e23b4d3521e4068d8f7cee8aa6041d57375ec1b2
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/05/2018
ms.locfileid: "37851481"
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
|[CRecordset::CRecordset](#crecordset)|Construye un objeto `CRecordset`. La clase derivada debe proporcionar un constructor que llame a este.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CRecordset::AddNew](#addnew)|Se prepara para agregar un nuevo registro. Llame a `Update` para completar la incorporación.|  
|[CRecordset::CanAppend](#canappend)|Devuelve cero si se pueden agregar nuevos registros en el conjunto de registros a través de la `AddNew` función miembro.|  
|[CRecordset:: CanBookmark](#canbookmark)|Devuelve cero si el conjunto de registros admite marcadores.|  
|[CRecordset::Cancel](#cancel)|Cancela una operación asincrónica o un proceso de un segundo subproceso.|  
|[CRecordset::CancelUpdate](#cancelupdate)|Cancela cualquier actualización pendiente debido a un `AddNew` o `Edit` operación.|  
|[CRecordset::CanRestart](#canrestart)|Devuelve cero si `Requery` puede llamarse para volver a ejecutar la consulta.|  
|[CRecordset::CanScroll](#canscroll)|Devuelve cero si puede desplazarse por los registros.|  
|[CRecordset::CanTransact](#cantransact)|Devuelve cero si el origen de datos admite transacciones.|  
|[CRecordset::CanUpdate](#canupdate)|Devuelve cero si se puede actualizar el conjunto de registros (puede agregar, actualizar o eliminar registros).|  
|[CRecordset::CheckRowsetError](#checkrowseterror)|Se llama para tratar los errores generados durante la captura de registro.|  
|[CRecordset:: Close](#close)|Cierra el conjunto de registros y la HSTMT ODBC asociado con él.|  
|[CRecordset::Delete](#delete)|Elimina el registro actual del conjunto de registros. Explícitamente, debe desplazarse a otro registro después de la eliminación.|  
|[CRecordset::DoBulkFieldExchange](#dobulkfieldexchange)|Se llama para intercambiar las filas de forma masiva de datos del origen de datos al conjunto de registros. Implementa de forma masiva el intercambio de campos de registros (RFX masivo).|  
|[CRecordset:: DoFieldExchange](#dofieldexchange)|Se llama para intercambiar datos (en ambas direcciones) entre los miembros de datos de campo del conjunto de registros y el registro correspondiente en el origen de datos. Implementa registro (RFX) de intercambio de campos.|  
|[CRecordset::Edit](#edit)|Prepara los cambios en el registro actual. Llame a `Update` para completar la edición.|  
|[CRecordset::FlushResultSet](#flushresultset)|Devuelve distinto de cero si no hay resultados de otro conjunto va a recuperar cuando se usa una consulta predefinida.|  
|[CRecordset::GetBookmark](#getbookmark)|Asigna el valor de marcador de un registro para el objeto de parámetro.|  
|[CRecordset:: GetDefaultConnect](#getdefaultconnect)|Se llama para obtener la cadena de conexión predeterminada.|  
|[CRecordset::GetDefaultSQL](#getdefaultsql)|Se llama para obtener la cadena SQL predeterminada para ejecutar.|  
|[CRecordset:: GetFieldValue](#getfieldvalue)|Devuelve el valor de un campo en un conjunto de registros.|  
|[CRecordset::GetODBCFieldCount](#getodbcfieldcount)|Devuelve el número de campos del conjunto de registros.|  
|[CRecordset::GetODBCFieldInfo](#getodbcfieldinfo)|Devuelve los tipos de información sobre los campos específicos en un conjunto de registros.|  
|[CRecordset::GetRecordCount](#getrecordcount)|Devuelve el número de registros en el conjunto de registros.|  
|[CRecordset::GetRowsetSize](#getrowsetsize)|Devuelve el número de registros que desea recuperar durante una búsqueda sencilla.|  
|[CRecordset::GetRowsFetched](#getrowsfetched)|Devuelve el número real de filas recuperado durante una búsqueda.|  
|[CRecordset::GetRowStatus](#getrowstatus)|Devuelve el estado de la fila después de una captura.|  
|[CRecordset::GetSQL](#getsql)|Obtiene la cadena SQL que se utiliza para seleccionar registros del conjunto de registros.|  
|[CRecordset::GetStatus](#getstatus)|Obtiene el estado del conjunto de registros: el índice del registro actual y si se ha obtenido un recuento final de los registros.|  
|[CRecordset::GetTableName](#gettablename)|Obtiene el nombre de la tabla en que se basa el conjunto de registros.|  
|[CRecordset::IsBOF](#isbof)|Devuelve cero si el conjunto de registros se ha posicionado antes del primer registro. No hay ningún registro actual.|  
|[CRecordset::IsDeleted](#isdeleted)|Devuelve cero si el conjunto de registros se coloca en un registro eliminado.|  
|[CRecordset::IsEOF](#iseof)|Devuelve cero si se ha colocado el conjunto de registros después del último registro. No hay ningún registro actual.|  
|[CRecordset::IsFieldDirty](#isfielddirty)|Devuelve cero si se ha cambiado el campo especificado en el registro actual.|  
|[CRecordset::IsFieldNull](#isfieldnull)|Devuelve cero si el campo especificado en el registro actual es nulo (no tiene ningún valor).|  
|[CRecordset::IsFieldNullable](#isfieldnullable)|Devuelve cero si el campo especificado en el registro actual se puede establecer en null (con ningún valor).|  
|[CRecordset::IsOpen](#isopen)|Devuelve cero si `Open` se ha llamado previamente.|  
|[CRecordset:: Move](#move)|Coloca el conjunto de registros a un número especificado de registros desde el registro actual en cualquier dirección.|  
|[CRecordset::MoveFirst](#movefirst)|Coloca el registro actual en el primer registro en el conjunto de registros. Probar `IsBOF` primero.|  
|[CRecordset::MoveLast](#movelast)|Coloca el registro actual en el último registro o en el último conjunto de filas. Probar `IsEOF` primero.|  
|[CRecordset::MoveNext](#movenext)|Coloca el registro actual en el siguiente registro o en el siguiente conjunto de filas. Probar `IsEOF` primero.|  
|[CRecordset::MovePrev](#moveprev)|Coloca el registro actual en el registro anterior o en el conjunto de filas anterior. Probar `IsBOF` primero.|  
|[CRecordset::OnSetOptions](#onsetoptions)|Se llama para establecer las opciones (que se usa en la selección) para la instrucción ODBC especificada.|  
|[CRecordset::OnSetUpdateOptions](#onsetupdateoptions)|Se llama para establecer las opciones (que se usa en la actualización) para la instrucción ODBC especificada.|  
|[CRecordset:: Open](#open)|Abre el conjunto de registros recuperando la tabla o realizando la consulta que el conjunto de registros representa.|  
|[CRecordset::RefreshRowset](#refreshrowset)|Actualiza los datos y el estado de la fila o filas especificadas.|  
|[CRecordset:: Requery](#requery)|Ejecuta la consulta del conjunto de registros nuevo para actualizar los registros seleccionados.|  
|[CRecordset:: SetAbsolutePosition](#setabsoluteposition)|Coloca el conjunto de registros en el registro correspondiente al número de registro especificado.|  
|[CRecordset::SetBookmark](#setbookmark)|Coloca el conjunto de registros en el registro especificado por el marcador.|  
|[CRecordset::SetFieldDirty](#setfielddirty)|Marca el campo especificado en el registro actual como modificada.|  
|[CRecordset::SetFieldNull](#setfieldnull)|Establece el valor del campo especificado en el registro actual en null (con ningún valor).|  
|[CRecordset::SetLockingMode](#setlockingmode)|Establece el modo de bloqueo "optimista" bloquear (predeterminado) o de bloqueo "pesimista". Determina cómo se bloquean los registros para las actualizaciones.|  
|[CRecordset::SetParamNull](#setparamnull)|El parámetro especificado se establece en null (con ningún valor).|  
|[CRecordset::SetRowsetCursorPosition](#setrowsetcursorposition)|Coloca el cursor en la fila especificada en el conjunto de filas.|  
|[CRecordset::SetRowsetSize](#setrowsetsize)|Especifica el número de registros que desea recuperar durante una búsqueda.|  
|[CRecordset:: Update](#update)|Se completa una `AddNew` o `Edit` operación guardando los datos nuevos o modificados del origen de datos.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CRecordset:: M_hstmt](#m_hstmt)|Contiene el identificador de instrucción ODBC para el conjunto de registros. Escriba `HSTMT`.|  
|[CRecordset::m_nFields](#m_nfields)|Contiene el número de miembros de datos de campo del conjunto de registros. Escriba `UINT`.|  
|[CRecordset::m_nParams](#m_nparams)|Contiene el número de miembros de datos de parámetro en el conjunto de registros. Escriba `UINT`.|  
|[CRecordset::m_pDatabase](#m_pdatabase)|Contiene un puntero a la `CDatabase` a través del cual el conjunto de registros está conectado a un origen de datos de objeto.|  
|[CRecordset:: M_strfilter](#m_strfilter)|Contiene un `CString` que especifica un lenguaje de consulta estructurado (SQL) `WHERE` cláusula. Se utiliza como filtro para seleccionar solo aquellos registros que cumplen determinados criterios.|  
|[CRecordset::m_strSort](#m_strsort)|Contiene un `CString` que especifica una instancia de SQL `ORDER BY` cláusula. Se usa para controlar cómo se ordenan los registros.|  
  
## <a name="remarks"></a>Comentarios  
 Conocida como "conjuntos de registros," `CRecordset` objetos se utilizan normalmente en dos formas: conjuntos de registros dinámicos y las instantáneas. Un conjunto de registros dinámicos permanece sincronizado con las actualizaciones de datos realizadas por otros usuarios. Una instantánea es una vista estática de los datos. Cada formulario representa un conjunto de registros que se fija en el momento en que se abre el conjunto de registros, pero cuando se desplaza a un registro en un conjunto de registros dinámicos, refleja los cambios realizados posteriormente en el registro, por otros usuarios o por otros conjuntos de registros en la aplicación.  
  
> [!NOTE]
>  Si está trabajando con las clases de objetos de acceso a datos (DAO) en lugar de las clases de Open Database Connectivity (ODBC), utilice la clase [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) en su lugar. Para obtener más información, vea el artículo [información general: programación de base de datos](../../data/data-access-programming-mfc-atl.md).  
  
 Para trabajar con cualquier tipo de conjunto de registros, normalmente se deriva una clase de conjunto de registros específicos de la aplicación de `CRecordset`. Conjuntos de registros seleccionan los registros de un origen de datos y, a continuación, puede:  
  
-   Desplazarse por los registros.  
  
-   Actualizar los registros y especificar un modo de bloqueo.  
  
-   Filtrar el conjunto de registros para limitar los registros que selecciona desde los que están disponibles en el origen de datos.  
  
-   Ordenar el conjunto de registros.  
  
-   Parametrizar el conjunto de registros para personalizar su selección con información no conocida hasta el tiempo de ejecución.  
  
 Para usar la clase, abra una base de datos y construir un objeto de conjunto de registros, pasando el constructor de un puntero a su `CDatabase` objeto. A continuación, llame el conjunto de registros `Open` función miembro, donde puede especificar si el objeto es de tipo dinámico o una instantánea. Una llamada a `Open` selecciona datos desde el origen de datos. Una vez abierto el objeto de conjunto de registros, use sus miembros de datos y funciones de miembro para desplazarse por los registros y operar con ellas. Las operaciones disponibles dependen de si el objeto es de tipo dinámico o una instantánea, ya sea actualizable o de solo lectura (Esto depende de la capacidad del origen de datos Open Database Connectivity (ODBC)), y si ha implementado la obtención masiva de filas. Para actualizar los registros que se han cambiado o agregado desde la `Open` llamada, llamar al objeto `Requery` función miembro. Llamar al objeto `Close` miembro de función y destruir el objeto cuando termine con él.  
  
 En una derivada `CRecordset` class, registre el intercambio de campos (RFX) o el intercambio masivo de campos de registros (RFX masivo) se usa para admitir la lectura y actualización de campos de registro.  
  
 Para obtener más información sobre el intercambio de campos de registros y conjuntos de registros, consulte los artículos [información general: programación de base de datos](../../data/data-access-programming-mfc-atl.md), [conjunto de registros (ODBC)](../../data/odbc/recordset-odbc.md), [conjunto de registros: obtener registros de forma masiva (ODBC) ](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md), y [(RFX) de intercambio de campos de registros](../../data/odbc/record-field-exchange-rfx.md). Para un enfoque en conjuntos de registros dinámicos y las instantáneas, consulte los artículos [Dynaset](../../data/odbc/dynaset.md) y [instantánea](../../data/odbc/snapshot.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CRecordset`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdb.h  
  
##  <a name="addnew"></a>  CRecordset::AddNew  
 Se prepara para agregar un nuevo registro a la tabla.  
  
```  
virtual void AddNew();
```  
  
### <a name="remarks"></a>Comentarios  
 Debe llamar a la [Requery](#requery) función miembro para ver el registro recién agregado. Los campos del registro son inicialmente Null. (En la terminología de base de datos, Null significa "no tener ningún valor" y no es igual a NULL en C++). Para completar la operación, debe llamar a la [actualización](#update) función miembro. `Update` guarda los cambios en el origen de datos.  
  
> [!NOTE]
>  Si ha implementado la obtención masiva de filas, no puede llamar a `AddNew`. Esto provocará un error de aserción. Aunque clase `CRecordset` no proporciona un mecanismo de actualización masiva de filas de datos, puede escribir sus propias funciones mediante la función de la API de ODBC `SQLSetPos`. Para obtener más información sobre la obtención masiva de filas, vea el artículo [Conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 `AddNew` prepara un registro nuevo y vacío con los miembros de datos de campo del conjunto de registros. Después de llamar a `AddNew`, establezca los valores que desee en los miembros de datos de campo del conjunto de registros. (No es necesario llamar a la [editar](#edit) función miembro para este fin; utilice `Edit` solo para los registros existentes.) Cuando se llama posteriormente `Update`, modificada se guardan los valores de los miembros de datos de campo del origen de datos.  
  
> [!CAUTION]
>  Si se desplaza a un nuevo registro antes de llamar a `Update`, el nuevo registro se pierden y se emite ninguna advertencia.  
  
 Si el origen de datos admite transacciones, puede hacer que su `AddNew` llame a parte de una transacción. Para obtener más información acerca de las transacciones, vea la clase [CDatabase](../../mfc/reference/cdatabase-class.md). Tenga en cuenta que debe llamar a [CDatabase::BeginTrans](../../mfc/reference/cdatabase-class.md#begintrans) antes de llamar a `AddNew`.  
  
> [!NOTE]
>  Para conjuntos de registros dinámicos, los nuevos registros se agregan al conjunto de registros como el último registro. Los registros agregados no se agregan a las instantáneas; debe llamar a `Requery` para actualizar el conjunto de registros.  
  
 No es válido llamar a `AddNew` para un conjunto de registros cuyo `Open` no se llamó la función de miembro. Un `CDBException` se produce si se llama a `AddNew` para un conjunto de registros que no se puede anexar. Puede determinar si el conjunto de registros es actualizable mediante una llamada a [CanAppend](#canappend).  
  
 Para obtener más información, consulte los artículos siguientes: [conjunto de registros: actualizar los registros (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md), [conjunto de registros: agregar, actualizar y eliminar registros (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md), y [(de transacción ODBC)](../../data/odbc/transaction-odbc.md).  
  
### <a name="example"></a>Ejemplo  
 Consulte el artículo [transacción: realizar una transacción en un conjunto de registros (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md).  
  
##  <a name="canappend"></a>  CRecordset::CanAppend  
 Determina si el conjunto de registros abierto anteriormente le permite agregar nuevos registros.  
  
```  
BOOL CanAppend() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el conjunto de registros permite agregar nuevos registros; en caso contrario, es 0. `CanAppend` Devuelve 0 si se abre el conjunto de registros como de solo lectura.  
  
##  <a name="canbookmark"></a>  CRecordset:: CanBookmark  
 Determina si el conjunto de registros permite marcar registros de uso de marcadores.  
  
```  
BOOL CanBookmark() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el conjunto de registros admite marcadores; en caso contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 Esta función es independiente de la `CRecordset::useBookmarks` opción el *dwOptions* parámetro de la [abierto](#open) función miembro. `CanBookmark` indica si el controlador ODBC determinada y el cursor de tipo de compatibilidad con marcadores. `CRecordset::useBookmarks` indica si los marcadores estarán disponibles, siempre que se admiten.  
  
> [!NOTE]
>  No se admiten marcadores en conjuntos de registros solo hacia delante.  
  
 Para obtener más información acerca de los marcadores y exploración del conjunto de registros, consulte los artículos [conjunto de registros: marcadores y posiciones absolutas (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md) y [conjunto de registros: desplazamiento (ODBC)](../../data/odbc/recordset-scrolling-odbc.md).  
  
##  <a name="cancel"></a>  CRecordset::Cancel  
 Solicitudes que el origen de datos cancela una operación asincrónica en curso o un proceso de un segundo subproceso.  
  
```  
void Cancel();
```  
  
### <a name="remarks"></a>Comentarios  
 Tenga en cuenta que las clases ODBC de MFC ya no usan el procesamiento asincrónico; para llevar a cabo una operación asincrónica, se debe llamar directamente a la función de la API de ODBC `SQLSetConnectOption`. Para obtener más información, vea el tema "Ejecutar funciones de forma asincrónica" en el *Guía del programador de ODBC SDK*.  
  
##  <a name="cancelupdate"></a>  CRecordset::CancelUpdate  
 Cancela todas las actualizaciones pendientes, causadas por un [editar](#edit) o [AddNew](#addnew) operación, antes de [actualización](#update) se llama.  
  
```  
void CancelUpdate();
```  
  
### <a name="remarks"></a>Comentarios  
  
> [!NOTE]
>  Esta función miembro no es aplicable en conjuntos de registros que se están usando la obtención masiva de filas, ya que no se pueden llamar estos conjuntos de registros `Edit`, `AddNew`, o `Update`. Para obtener más información sobre la obtención masiva de filas, vea el artículo [Conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Si está habilitada la comprobación automática de campos modificados, `CancelUpdate` restaurará las variables de miembro para los valores que tenían antes de `Edit` o `AddNew` llamado; de lo contrario, se mantendrá los cambios de valor. De forma predeterminada, la comprobación automática de campos está habilitada cuando se abre el conjunto de registros. Para deshabilitarla, debe especificar el `CRecordset::noDirtyFieldCheck` en el *dwOptions* parámetro de la [abierto](#open) función miembro.  
  
 Para obtener más información acerca de cómo actualizar datos, vea el artículo [conjunto de registros: agregar, actualizar y eliminar registros (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md).  
  
##  <a name="canrestart"></a>  CRecordset::CanRestart  
 Determina si el conjunto de registros permite reiniciar su consulta (para actualizar sus registros) mediante una llamada a la `Requery` función miembro.  
  
```  
BOOL CanRestart() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si se permite requery; en caso contrario, es 0.  
  
##  <a name="canscroll"></a>  CRecordset::CanScroll  
 Determina si el conjunto de registros permite el desplazamiento.  
  
```  
BOOL CanScroll() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el conjunto de registros permite el desplazamiento; en caso contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información acerca de desplazamiento, vea el artículo [conjunto de registros: desplazamiento (ODBC)](../../data/odbc/recordset-scrolling-odbc.md).  
  
##  <a name="cantransact"></a>  CRecordset::CanTransact  
 Determina si el conjunto de registros permite que las transacciones.  
  
```  
BOOL CanTransact() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el conjunto de registros permite que las transacciones. en caso contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, vea el artículo [transacción (ODBC)](../../data/odbc/transaction-odbc.md).  
  
##  <a name="canupdate"></a>  CRecordset::CanUpdate  
 Determina si se puede actualizar el conjunto de registros.  
  
```  
BOOL CanUpdate() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si se puede actualizar el conjunto de registros; en caso contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 Un conjunto de registros puede ser de sólo lectura si el origen de datos subyacente es de solo lectura o si especifica `CRecordset::readOnly` en el *dwOptions* parámetro cuando se abre el conjunto de registros.  
  
##  <a name="checkrowseterror"></a>  CRecordset::CheckRowsetError  
 Se llama para tratar los errores generados durante la captura de registro.  
  
```  
virtual void CheckRowsetError(RETCODE nRetCode);
```  
  
### <a name="parameters"></a>Parámetros  
 *nRetCode*  
 Código de retorno de una función API de ODBC. Para conocer más detalles, vea la sección Comentarios.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro virtual controla los errores que se producen cuando se capturan los registros, y es útil durante la obtención masiva de filas. Puede desear considerar la sobrescritura `CheckRowsetError` para implementar su propio control de errores.  
  
 `CheckRowsetError` se llama automáticamente en una operación de desplazamiento de cursor, como `Open`, `Requery`, o cualquier `Move` operación. Se pasa el valor devuelto de la función de la API de ODBC `SQLExtendedFetch`. La tabla siguiente enumeran los valores posibles para el *nRetCode* parámetro.  
  
|nRetCode|Descripción|  
|--------------|-----------------|  
|SQL_SUCCESS|Función que se ha ejecutado correctamente; No hay información adicional está disponible.|  
|SQL_SUCCESS_WITH_INFO|Función que se ha completado correctamente, posiblemente con un error recuperable. Información adicional puede obtenerse mediante una llamada a `SQLError`.|  
|SQL_NO_DATA_FOUND|Todas las filas del conjunto de resultados se han capturado.|  
|SQL_ERROR|Error de la función. Información adicional puede obtenerse mediante una llamada a `SQLError`.|  
|SQL_INVALID_HANDLE|Función falló debido a un identificador de entorno no válido, el identificador de conexión o el identificador de instrucción. Esto indica un error de programación. No hay información adicional está disponible en `SQLError`.|  
|SQL_STILL_EXECUTING|Todavía se está ejecutando una función que se inició de forma asincrónica. Tenga en cuenta que, de forma predeterminada, MFC nunca pasará este valor a `CheckRowsetError`; MFC seguirá llamada `SQLExtendedFetch` hasta que ya no devuelve SQL_STILL_EXECUTING.|  
  
 Para obtener más información sobre `SQLError`, consulte el SDK de Windows. Para obtener más información sobre la obtención masiva de filas, vea el artículo [Conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
##  <a name="close"></a>  CRecordset:: Close  
 Cierra el conjunto de registros.  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>Comentarios  
 El HSTMT ODBC y toda la memoria asignada para el conjunto de registros el marco de trabajo se desasignan. Normalmente, después de llamar a `Close`, eliminar el objeto de conjunto de registros de C++ si se ha asignado con **nuevo**.  
  
 Puede llamar a `Open` nuevamente después de llamar a `Close`. Esto permite reutilizar el objeto de conjunto de registros. La alternativa es llamar a `Requery`.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDatabase#17](../../mfc/codesnippet/cpp/crecordset-class_1.cpp)]  
  
##  <a name="crecordset"></a>  CRecordset::CRecordset  
 Construye un objeto `CRecordset`.  
  
```  
CRecordset(CDatabase* pDatabase = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 *pDatabase*  
 Contiene un puntero a un `CDatabase` objeto o el valor NULL. Si no es NULL y el `CDatabase` del objeto `Open` función miembro no se ha llamado para conectarlo al origen de datos, el objeto recordset intenta abrir automáticamente durante su propia `Open` llamar. Si se pasa NULL, un `CDatabase` objeto se construye y se conecta automáticamente con la información de origen de datos especificado al que se derivó de la clase de conjunto de registros con ClassWizard.  
  
### <a name="remarks"></a>Comentarios  
 Puede usar `CRecordset` directamente o derivar una clase específica de la aplicación de `CRecordset`. Puede usar ClassWizard para derivar las clases de conjunto de registros.  
  
> [!NOTE]
>  Una clase derivada *debe* proporcionar su propio constructor. En el constructor de la clase derivada, llame al constructor `CRecordset::CRecordset`, pasando los parámetros adecuados junto a él.  
  
 Pasar NULL para el constructor del conjunto de registros para tener un `CDatabase` objeto construido y conecta automáticamente para usted. Se trata de una forma abreviada útil que no requiere que se va a construir y conectar un `CDatabase` objeto antes de construir el conjunto de registros.  
  
### <a name="example"></a>Ejemplo  
 Para obtener más información, vea el artículo [conjunto de registros: declarar una clase para una tabla (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md).  
  
##  <a name="delete"></a>  CRecordset::Delete  
 Elimina el registro actual.  
  
```  
virtual void Delete();
```  
  
### <a name="remarks"></a>Comentarios  
 Después de una eliminación se realiza correctamente, los miembros de datos de campo del conjunto de registros se establecen en un valor Null y debe llamar explícitamente a uno de los `Move` funciones con el fin de abandonar el registro eliminado. Una vez que salga del registro eliminado, no es posible volver a él. Si el origen de datos admite transacciones, puede realizar la `Delete` llame a parte de una transacción. Para obtener más información, vea el artículo [transacción (ODBC)](../../data/odbc/transaction-odbc.md).  
  
> [!NOTE]
>  Si ha implementado la obtención masiva de filas, no puede llamar a `Delete`. Esto provocará un error de aserción. Aunque clase `CRecordset` no proporciona un mecanismo de actualización masiva de filas de datos, puede escribir sus propias funciones mediante la función de la API de ODBC `SQLSetPos`. Para obtener más información sobre la obtención masiva de filas, vea el artículo [Conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
> [!CAUTION]
>  El conjunto de registros debe ser actualizable y debe haber un registro válido actual en el conjunto de registros al llamar a `Delete`; en caso contrario, se produce un error. Por ejemplo, si elimina un registro pero no se desplazan a un nuevo registro antes de llamar a `Delete` nuevamente, `Delete` produce una [CDBException](../../mfc/reference/cdbexception-class.md).  
  
 A diferencia de [AddNew](#addnew) y [editar](#edit), una llamada a `Delete` no va seguida de una llamada a [actualización](#update). Si un `Delete` llamada produce un error, los datos del campo miembros se dejan sin cambios.  
  
### <a name="example"></a>Ejemplo  
 En este ejemplo se muestra un conjunto de registros creado en el marco de una función. En el ejemplo se presupone la existencia de `m_dbCust`, una variable de miembro de tipo `CDatabase` ya está conectado al origen de datos.  
  
 [!code-cpp[NVC_MFCDatabase#18](../../mfc/codesnippet/cpp/crecordset-class_2.cpp)]  
  
##  <a name="dobulkfieldexchange"></a>  CRecordset::DoBulkFieldExchange  
 Se llama para intercambiar las filas de forma masiva de datos del origen de datos al conjunto de registros. Implementa de forma masiva el intercambio de campos de registros (RFX masivo).  
  
```  
virtual void DoBulkFieldExchange(CFieldExchange* pFX);
```  
  
### <a name="parameters"></a>Parámetros  
 *pFX*  
 Un puntero a un [CFieldExchange](../../mfc/reference/cfieldexchange-class.md) objeto. El marco de trabajo ya habrá configurado este objeto para especificar un contexto para la operación de intercambio del campo.  
  
### <a name="remarks"></a>Comentarios  
 Cuando se implementa la obtención masiva de filas, el marco de trabajo llama a esta función miembro para transferir automáticamente datos desde el origen de datos para el objeto de conjunto de registros. `DoBulkFieldExchange` también enlaza a los miembros de datos de parámetro, si los hay, para los marcadores de posición en la cadena de instrucción SQL para la selección del conjunto de registros.  
  
 Si no se implementa la obtención masiva de filas, el marco llama a [DoFieldExchange](#dofieldexchange). Para implementar la obtención masiva de filas, debe especificar el `CRecordset::useMultiRowFetch` opción de la *dwOptions* parámetro en el [abierto](#open) función miembro.  
  
> [!NOTE]
> `DoBulkFieldExchange` solo está disponible si está utilizando una clase derivada de `CRecordset`. Si ha creado un objeto de conjunto de registros directamente desde `CRecordset`, debe llamar a la [GetFieldValue](#getfieldvalue) función miembro para recuperar los datos.  
  
 Intercambio masivo de campos de registros (RFX masivo) es similar al intercambio de campos de registros (RFX). Automáticamente, los datos se transfieren desde el origen de datos para el objeto de conjunto de registros. Sin embargo, no puede llamar a `AddNew`, `Edit`, `Delete`, o `Update` para transferir los cambios en el origen de datos. Clase `CRecordset` actualmente no proporciona un mecanismo para actualizar filas de forma masiva de datos; sin embargo, puede escribir sus propias funciones mediante la función de la API de ODBC `SQLSetPos`.  
  
 Tenga en cuenta que el Asistente para clases no admite intercambio masivo de campos de registros; por lo tanto, debe invalidar `DoBulkFieldExchange` manualmente escribiendo las llamadas a las funciones de RFX masivo. Para obtener más información acerca de estas funciones, vea el tema [funciones de intercambio de campos de registros](../../mfc/reference/record-field-exchange-functions.md).  
  
 Para obtener más información sobre la obtención masiva de filas, vea el artículo [Conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md). Para obtener información relacionada, vea el artículo [intercambio de campos de registros (RFX)](../../data/odbc/record-field-exchange-rfx.md).  
  
##  <a name="dofieldexchange"></a>  CRecordset:: DoFieldExchange  
 Se llama para intercambiar datos (en ambas direcciones) entre los miembros de datos de campo del conjunto de registros y el registro correspondiente en el origen de datos. Implementa registro (RFX) de intercambio de campos.  
  
```  
virtual void DoFieldExchange(CFieldExchange* pFX);
```  
  
### <a name="parameters"></a>Parámetros  
 *pFX*  
 Un puntero a un [CFieldExchange](../../mfc/reference/cfieldexchange-class.md) objeto. El marco de trabajo ya habrá configurado este objeto para especificar un contexto para la operación de intercambio del campo.  
  
### <a name="remarks"></a>Comentarios  
 Cuando no se implementa la obtención masiva de filas, el marco de trabajo llama a esta función miembro para automáticamente intercambiar datos entre los miembros de datos de campo del objeto de conjunto de registros y las columnas correspondientes del registro actual en el origen de datos. `DoFieldExchange` también enlaza a los miembros de datos de parámetro, si los hay, para los marcadores de posición en la cadena de instrucción SQL para la selección del conjunto de registros.  
  
 Si se implementa la obtención masiva de filas, el marco llama a [DoBulkFieldExchange](#dobulkfieldexchange). Para implementar la obtención masiva de filas, debe especificar el `CRecordset::useMultiRowFetch` opción de la *dwOptions* parámetro en el [abierto](#open) función miembro.  
  
> [!NOTE]
> `DoFieldExchange` solo está disponible si está utilizando una clase derivada de `CRecordset`. Si ha creado un objeto de conjunto de registros directamente desde `CRecordset`, debe llamar a la [GetFieldValue](#getfieldvalue) función miembro para recuperar los datos.  
  
 El intercambio de datos de campo, denominado el intercambio de campos de registros (RFX), funciona en ambas direcciones: desde los miembros de datos de campo del objeto de conjunto de registros a los campos del registro en el origen de datos y del registro en el origen de datos para el objeto de conjunto de registros.  
  
 La única acción que debe seguir normalmente para implementar `DoFieldExchange` para el conjunto de registros derivada clase consiste en crear la clase con ClassWizard y especificar los tipos de datos y los nombres de los miembros de datos de campo. También puede agregar código a lo que escribe ClassWizard para especificar a los miembros de datos de parámetro o para tratar con las columnas que enlazar dinámicamente. Para obtener más información, vea el artículo [conjunto de registros: enlazar dinámicamente columnas de datos (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).  
  
 Cuando se declara la clase derivada de conjunto de registros con ClassWizard, el asistente escribe una invalidación de `DoFieldExchange` , que es similar al siguiente:  
  
 [!code-cpp[NVC_MFCDatabase#19](../../mfc/codesnippet/cpp/crecordset-class_3.cpp)]  
  
 Para obtener más información acerca de las funciones de RFX, consulte el tema [funciones de intercambio de campos de registros](../../mfc/reference/record-field-exchange-functions.md).  
  
 Para obtener más ejemplos y detalles sobre `DoFieldExchange`, consulte el artículo [intercambio de campos de registros: funcionamiento de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md). Para obtener información general sobre RFX, consulte el artículo [intercambio de campos de registro](../../data/odbc/record-field-exchange-rfx.md).  
  
##  <a name="edit"></a>  CRecordset::Edit  
 Permite que los cambios en el registro actual.  
  
```  
virtual void Edit();
```  
  
### <a name="remarks"></a>Comentarios  
 Después de llamar a `Edit`, puede cambiar los miembros de datos de campo restableciendo directamente sus valores. La operación se completa cuando se llame posteriormente a la [actualización](#update) función miembro para guardar los cambios en el origen de datos.  
  
> [!NOTE]
>  Si ha implementado la obtención masiva de filas, no puede llamar a `Edit`. Esto provocará un error de aserción. Aunque clase `CRecordset` no proporciona un mecanismo de actualización masiva de filas de datos, puede escribir sus propias funciones mediante la función de la API de ODBC `SQLSetPos`. Para obtener más información sobre la obtención masiva de filas, vea el artículo [Conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 `Edit` guarda los valores de los miembros de datos del conjunto de registros. Si se llama a `Edit`, realizar cambios, a continuación, llame a `Edit` nuevo, se restauran los valores del registro a lo que estaban antes del primer `Edit` llamar.  
  
 En algunos casos, puede actualizar una columna, por lo que es Null (que contiene ningún dato). Para ello, llame al [SetFieldNull](#setfieldnull) con un parámetro de true para marcar el campo es Null; Esto también hace que la columna se puede actualizar. Si desea que un campo para escribirse en el origen de datos, aunque no ha cambiado su valor, llame a [SetFieldDirty](#setfielddirty) con un parámetro es true. Esto funciona incluso si el campo tenía el valor Null.  
  
 Si el origen de datos admite transacciones, puede realizar la `Edit` llame a parte de una transacción. Tenga en cuenta que debe llamar a [CDatabase::BeginTrans](../../mfc/reference/cdatabase-class.md#begintrans) antes de llamar a `Edit` y después de abrir el conjunto de registros. Tenga en cuenta también que la llamada a [CDatabase::CommitTrans](../../mfc/reference/cdatabase-class.md#committrans) no constituye un sustituto para llamar a `Update` para completar la `Edit` operación. Para obtener más información acerca de las transacciones, vea la clase [CDatabase](../../mfc/reference/cdatabase-class.md).  
  
 Según el modo de bloqueo actual, el registro que se está actualizando esté bloqueado por `Edit` hasta que llame a `Update` o desplácese a otro registro, o puede estar bloqueada solo durante el `Edit` llamar. Puede cambiar el modo de bloqueo con [SetLockingMode](#setlockingmode).  
  
 Se restaura el valor anterior del registro actual si se desplaza a un nuevo registro antes de llamar a `Update`. Un `CDBException` se produce si se llama a `Edit` para un conjunto de registros que no se puede actualizar o si no hay ningún registro actual.  
  
 Para obtener más información, consulte los artículos [transacción (ODBC)](../../data/odbc/transaction-odbc.md) y [conjunto de registros: bloquear registros (ODBC)](../../data/odbc/recordset-locking-records-odbc.md).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDatabase#20](../../mfc/codesnippet/cpp/crecordset-class_4.cpp)]  
  
##  <a name="flushresultset"></a>  CRecordset::FlushResultSet  
 Recupera el siguiente conjunto de resultados de una consulta predefinida (procedimiento almacenado), si hay varios conjuntos de resultados.  
  
```  
BOOL FlushResultSet();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si no hay más conjuntos de resultados van a recuperar; en caso contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 Debe llamar a `FlushResultSet` sólo cuando haya terminado por completo con el cursor en el conjunto de resultados actual. Tenga en cuenta que al recuperar el conjunto mediante una llamada de resultados siguiente `FlushResultSet`, el cursor no es válido en ese conjunto de resultados; debe llamar a la [MoveNext](#movenext) función miembro después de llamar a `FlushResultSet`.  
  
 Si una consulta predefinida utiliza un parámetro de salida o parámetros de entrada/salida, debe llamar a `FlushResultSet` hasta que devuelva `FALSE` (el valor 0), con el fin de obtener estos valores de parámetro.  
  
 `FlushResultSet` llama a la función de la API de ODBC `SQLMoreResults`. Si `SQLMoreResults` devuelve SQL_ERROR o SQL_INVALID_HANDLE, a continuación, `FlushResultSet` generará una excepción. Para obtener más información sobre `SQLMoreResults`, consulte el SDK de Windows.  
  
 El procedimiento almacenado debe enlazar campos si desea llamar a `FlushResultSet`.  
  
### <a name="example"></a>Ejemplo  
 El código siguiente se da por supuesto que `COutParamRecordset` es un `CRecordset`-objeto derivado en función de una consulta predefinida con un parámetro de entrada y un parámetro de salida y tener varios conjuntos de resultados. Tenga en cuenta la estructura de la [DoFieldExchange](#dofieldexchange) invalidar.  
  
 [!code-cpp[NVC_MFCDatabase#21](../../mfc/codesnippet/cpp/crecordset-class_5.cpp)]  
  
 [!code-cpp[NVC_MFCDatabase#22](../../mfc/codesnippet/cpp/crecordset-class_6.cpp)]  
  
##  <a name="getbookmark"></a>  CRecordset::GetBookmark  
 Obtiene el valor de marcador para el registro actual.  
  
```  
void GetBookmark(CDBVariant& varBookmark);
```  
  
### <a name="parameters"></a>Parámetros  
 *varBookmark*  
 Una referencia a un [CDBVariant](../../mfc/reference/cdbvariant-class.md) objeto que representa el marcador en el registro actual.  
  
### <a name="remarks"></a>Comentarios  
 Para determinar si se admiten marcadores en el conjunto de registros, llame a [CanBookmark](#canbookmark). Para que los marcadores estén disponibles si son compatibles, debe establecer el `CRecordset::useBookmarks` opción el *dwOptions* parámetro de la [abierto](#open) función miembro.  
  
> [!NOTE]
>  Si los marcadores son no compatibles o no está disponible, la llamada a `GetBookmark` dará como resultado una excepción. No se admiten marcadores en conjuntos de registros solo hacia delante.  
  
 `GetBookmark` asigna el valor de marcador para el registro actual a un `CDBVariant` objeto. Para volver a ese registro en cualquier momento después de mover a un registro diferente, llame a [SetBookmark](#setbookmark) con el correspondiente `CDBVariant` objeto.  
  
> [!NOTE]
>  Después de ciertas operaciones de conjunto de registros, los marcadores ya no pueden ser válidos. Por ejemplo, si se llama a `GetBookmark` seguido `Requery`, es posible que no pueda regresar al registro con `SetBookmark`. Llame a [CDatabase:: GetBookmarkPersistence](../../mfc/reference/cdatabase-class.md#getbookmarkpersistence) para comprobar si puede llamar con seguridad a `SetBookmark`.  
  
 Para obtener más información acerca de los marcadores y exploración del conjunto de registros, consulte los artículos [conjunto de registros: marcadores y posiciones absolutas (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md) y [conjunto de registros: desplazamiento (ODBC)](../../data/odbc/recordset-scrolling-odbc.md).  
  
##  <a name="getdefaultconnect"></a>  CRecordset:: GetDefaultConnect  
 Se llama para obtener la cadena de conexión predeterminada.  
  
```  
virtual CString GetDefaultConnect();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un `CString` que contiene la cadena de conexión predeterminada.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a esta función miembro para obtener la cadena de conexión predeterminado para el origen de datos en el que se basa el conjunto de registros. ClassWizard implementa esta función automáticamente mediante la identificación de mismo origen de datos que utilice en ClassWizard para obtener información acerca de las tablas y columnas. Probablemente le resulte conveniente confiar en esta conexión de forma predeterminada al desarrollar la aplicación. Pero la conexión predeterminada puede no ser adecuada para los usuarios de la aplicación. Si es así, se debe volver a implementar esta función, descartando la versión de ClassWizard. Para obtener más información acerca de las cadenas de conexión, vea el artículo [origen de datos (ODBC)](../../data/odbc/data-source-odbc.md).  
  
##  <a name="getdefaultsql"></a>  CRecordset::GetDefaultSQL  
 Se llama para obtener la cadena SQL predeterminada para ejecutar.  
  
```  
virtual CString GetDefaultSQL();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un `CString` que contiene la instrucción SQL predeterminada.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a esta función miembro para obtener la instrucción SQL de forma predeterminada en el que se basa el conjunto de registros. Esto podría ser un nombre de tabla o una instancia de SQL **seleccione** instrucción.  
  
 Defina la instrucción SQL predeterminada indirectamente mediante la declaración de la clase de conjunto de registros con ClassWizard y ClassWizard realiza esta tarea automáticamente.  
  
 Si tiene la cadena de instrucción SQL para su propio uso, llame a `GetSQL`, que devuelve la instrucción SQL utilizada para seleccionar registros del conjunto de registros cuando se abre. Puede editar la cadena SQL predeterminada en la invalidación de la clase de `GetDefaultSQL`. Por ejemplo, puede especificar una llamada a una consulta predefinida mediante un **llamar** instrucción. (Tenga en cuenta, sin embargo, que si edita `GetDefaultSQL`, también deberá modificar `m_nFields` para que coincida con el número de columnas del origen de datos.)  
  
 Para obtener más información, vea el artículo [conjunto de registros: declarar una clase para una tabla (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md).  
  
> [!CAUTION]
>  El nombre de la tabla estará vacío si el marco de trabajo no pudo identificar un nombre de tabla, si se han proporcionado varios nombres de tabla, o si un **llamar** instrucción no se puede interpretar. Tenga en cuenta que cuando se usa un **llamar a** instrucción, no debe insertar un espacio en blanco entre la llave y la **llamar a** palabra clave, ni debe insertar un espacio en blanco antes de la llave de apertura o el  **Seleccione** palabra clave en un **seleccione** instrucción.  
  
##  <a name="getfieldvalue"></a>  CRecordset:: GetFieldValue  
 Recupera datos del campo en el registro actual.  
  
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
 *lpszName*  
 El nombre de un campo.  
  
 *varValu*e  
 Una referencia a un [CDBVariant](../../mfc/reference/cdbvariant-class.md) objeto donde se almacenará el valor del campo.  
  
 *nFieldType*  
 El tipo de datos ODBC C del campo. Si se utiliza el valor predeterminado, DEFAULT_FIELD_TYPE, fuerza `GetFieldValue` determinar el tipo de datos C en el tipo de datos SQL, basándose en la tabla siguiente. En caso contrario, puede especificar los datos escritos directamente o elija un tipo de datos compatible; Por ejemplo, puede almacenar cualquier tipo de datos en SQL_C_CHAR.  
  
|Tipo de datos C|Tipo de datos SQL|  
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
  
 Para obtener más información sobre los tipos de datos ODBC, vea los temas "Tipos de datos de SQL" y "Tipos de datos C" en el apéndice D del SDK de Windows.  
  
 *nIndex*  
 Índice de base cero del campo.  
  
 *strValue*  
 Una referencia a un [CString](../../atl-mfc-shared/reference/cstringt-class.md) objeto donde se almacenará el valor del campo se convierte en texto, independientemente del tipo de datos del campo.  
  
### <a name="remarks"></a>Comentarios  
 Puede buscar un campo por nombre o por índice. Puede almacenar el valor del campo en ya sea un `CDBVariant` objeto o un `CString` objeto.  
  
 Si ha implementado la obtención masiva de filas, el registro actual siempre se sitúa en el primer registro en un conjunto de filas. Para usar `GetFieldValue` en un registro dentro de un conjunto de filas determinado, primero debe llamar a la [SetRowsetCursorPosition](#setrowsetcursorposition) función miembro para mover el cursor a la fila deseada dentro de ese conjunto de filas. A continuación, llame a `GetFieldValue` para esa fila. Para implementar la obtención masiva de filas, debe especificar el `CRecordset::useMultiRowFetch` opción de la *dwOptions* parámetro en el [abierto](#open) función miembro.  
  
 Puede usar `GetFieldValue` capturar campos dinámicamente en tiempo de ejecución en lugar de enlazarlos estáticamente en tiempo de diseño. Por ejemplo, si se ha declarado un objeto de conjunto de registros directamente desde `CRecordset`, debe usar `GetFieldValue` para recuperar los datos de campo; el intercambio de campos de registros (RFX) o el intercambio masivo de campos de registros (RFX masivo), no está implementada.  
  
> [!NOTE]
>  Si declara un objeto de conjunto de registros sin que derivar de `CRecordset`, es necesario cargar la biblioteca de cursores de ODBC. La biblioteca de cursores requiere que el conjunto de registros tenga al menos una columna enlazada; Sin embargo, cuando usa `CRecordset` directamente, ninguna de las columnas están enlazada. Las funciones miembro [CDatabase:: OpenEx](../../mfc/reference/cdatabase-class.md#openex) y [CDatabase:: Open](../../mfc/reference/cdatabase-class.md#open) controlar si se cargará la biblioteca de cursores.  
  
 `GetFieldValue` llama a la función de la API de ODBC `SQLGetData`. Si el controlador envía el valor SQL_NO_TOTAL para la longitud real del valor del campo, `GetFieldValue` produce una excepción. Para obtener más información sobre `SQLGetData`, consulte el SDK de Windows.  
  
### <a name="example"></a>Ejemplo  
 El código de ejemplo siguiente muestra llamadas a `GetFieldValue` para declara un objeto de conjunto de registros directamente desde `CRecordset`.  
  
 [!code-cpp[NVC_MFCDatabase#23](../../mfc/codesnippet/cpp/crecordset-class_7.cpp)]  
  
> [!NOTE]
>  A diferencia de la clase DAO `CDaoRecordset`, `CRecordset` no tiene un `SetFieldValue` función miembro. Si crea un objeto directamente desde `CRecordset`, resulta eficaz de solo lectura.  
  
 Para obtener más información sobre la obtención masiva de filas, vea el artículo [Conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
##  <a name="getodbcfieldcount"></a>  CRecordset::GetODBCFieldCount  
 Recupera el número total de campos en el objeto de conjunto de registros.  
  
```  
short GetODBCFieldCount() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de campos del conjunto de registros.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información sobre la creación de conjuntos de registros, vea el artículo [conjunto de registros: crear y cerrar conjuntos de registros (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md).  
  
##  <a name="getodbcfieldinfo"></a>  CRecordset::GetODBCFieldInfo  
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
 *lpszName*  
 El nombre de un campo.  
  
 *FieldInfo*  
 Una referencia a un `CODBCFieldInfo` estructura.  
  
 *nIndex*  
 Índice de base cero del campo.  
  
### <a name="remarks"></a>Comentarios  
 Una versión de la función le permite buscar un campo por su nombre. La otra versión le permite buscar un campo por su índice.  
  
 Para obtener una descripción acerca de la información devuelta, consulte el [CODBCFieldInfo](../../mfc/reference/codbcfieldinfo-structure.md) estructura.  
  
 Para obtener más información sobre la creación de conjuntos de registros, vea el artículo [conjunto de registros: crear y cerrar conjuntos de registros (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md).  
  
##  <a name="getrecordcount"></a>  CRecordset::GetRecordCount  
 Determina el tamaño del conjunto de registros.  
  
```  
long GetRecordCount() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de registros en el conjunto de registros; 0 si el conjunto de registros no contiene registros; o -1 si no se puede determinar el número de registros.  
  
### <a name="remarks"></a>Comentarios  
  
> [!CAUTION]
>  El número de registros se mantienen como una "marca de agua," el registro con el número mayor aún ve cuando el usuario mueve por los registros. Solo se conoce el número total de registros después de que el usuario se desplazó más allá del último registro. Por motivos de rendimiento, no se actualiza el recuento al llamar a `MoveLast`. Para contar los registros, llame a `MoveNext` repetidamente hasta que `IsEOF` devuelve cero. Adición de un registro a través de `CRecordset:AddNew` y `Update` aumenta el recuento; eliminar un registro a través de `CRecordset::Delete` disminuye el recuento.  
  
##  <a name="getrowsetsize"></a>  CRecordset::GetRowsetSize  
 Obtiene la configuración actual para el número de filas que desea recuperar durante una búsqueda determinada.  
  
```  
DWORD GetRowsetSize() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de filas que se va a recuperar durante una búsqueda determinada.  
  
### <a name="remarks"></a>Comentarios  
 Si usas la obtención masiva de filas, el tamaño del conjunto de filas de forma predeterminada cuando se abre el conjunto de registros es 25; en caso contrario, es 1.  
  
 Para implementar la obtención masiva de filas, debe especificar el `CRecordset::useMultiRowFetch` opción el *dwOptions* parámetro de la [abierto](#open) función miembro. Para cambiar la configuración para el tamaño del conjunto de filas, llame a [SetRowsetSize](#setrowsetsize).  
  
 Para obtener más información sobre la obtención masiva de filas, vea el artículo [Conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
##  <a name="getrowsfetched"></a>  CRecordset::GetRowsFetched  
 Determina cuántos registros se recuperaron realmente después de una captura.  
  
```  
DWORD GetRowsFetched() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de filas recuperadas del origen de datos después de una captura determinada.  
  
### <a name="remarks"></a>Comentarios  
 Esto es útil cuando se ha implementado la obtención masiva de filas. Normalmente, el tamaño del conjunto de filas indica cuántas filas se recuperan desde una captura; Sin embargo, el número total de filas del conjunto de registros también afecta al número de filas se recuperarán en un conjunto de filas. Por ejemplo, si el conjunto de registros tiene 10 registros con una configuración de tamaño del conjunto de filas de 4, a continuación, recorrer el conjunto de registros mediante una llamada a `MoveNext` dará como resultado el conjunto de filas final tiene sólo 2 registros.  
  
 Para implementar la obtención masiva de filas, debe especificar el `CRecordset::useMultiRowFetch` opción el *dwOptions* parámetro de la [abierto](#open) función miembro. Para especificar el tamaño del conjunto de filas, llame a [SetRowsetSize](#setrowsetsize).  
  
 Para obtener más información sobre la obtención masiva de filas, vea el artículo [Conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDatabase#24](../../mfc/codesnippet/cpp/crecordset-class_8.cpp)]  
  
##  <a name="getrowstatus"></a>  CRecordset::GetRowStatus  
 Obtiene el estado de una fila en el conjunto de filas actual.  
  
```  
WORD GetRowStatus(WORD wRow) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 *wRow*  
 La posición basada en uno de una fila en el conjunto de filas actual. Este valor puede oscilar entre 1 para el tamaño del conjunto de filas.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor de estado de la fila. Para conocer más detalles, vea la sección Comentarios.  
  
### <a name="remarks"></a>Comentarios  
 `GetRowStatus` Devuelve un valor que indica cualquier cualquier cambio en el estado de la fila porque era el último recuperados desde el origen de datos, o que no existe la fila correspondiente a *wRow* se capturó. La tabla siguiente muestra los valores devueltos posibles.  
  
|Valor de estado|Descripción|  
|------------------|-----------------|  
|SQL_ROW_SUCCESS|No se modifica la fila.|  
|SQL_ROW_UPDATED|Se ha actualizado la fila.|  
|SQL_ROW_DELETED|Se ha eliminado la fila.|  
|SQL_ROW_ADDED|Se agregó la fila.|  
|SQL_ROW_ERROR|La fila es irrecuperable debido a un error.|  
|SQL_ROW_NOROW|No hay ninguna fila que corresponde a *wRow*.|  
  
 Para obtener más información, vea la función de API de ODBC `SQLExtendedFetch` en el SDK de Windows.  
  
##  <a name="getstatus"></a>  CRecordset::GetStatus  
 Determina el índice del registro actual en el conjunto de registros y si se ha visto el último registro.  
  
```  
void GetStatus(CRecordsetStatus& rStatus) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 *rStatus*  
 Referencia a un objeto `CRecordsetStatus`. Vea la sección Comentarios para obtener más información.  
  
### <a name="remarks"></a>Comentarios  
 `CRecordset` intenta realizar un seguimiento del índice, pero en algunas circunstancias esto no sea posible. Consulte [GetRecordCount](#getrecordcount) para obtener una explicación.  
  
 El `CRecordsetStatus` estructura tiene el formato siguiente:  
  
 `struct CRecordsetStatus`  
  
 `{`  
  
 `long m_lCurrentRecord;`  
  
 `BOOL m_bRecordCountFinal;`  
  
 `};`  
  
 Los dos miembros de `CRecordsetStatus` tienen los significados siguientes:  
  
- `m_lCurrentRecord` Contiene el índice de base cero del registro actual en el conjunto de registros, si se conoce. Si no se puede determinar el índice, este miembro contiene AFX_CURRENT_RECORD_UNDEFINED-(2). Si `IsBOF` es TRUE (conjunto de registros vacío o intenta desplazarse antes del primer registro), a continuación, `m_lCurrentRecord` se establece en AFX_CURRENT_RECORD_BOF (-1). Si, a continuación, en el primer registro, se establece en 0, en segundo lugar grabar 1 y así sucesivamente.  
  
- `m_bRecordCountFinal` Distinto de cero si se ha determinado el número total de registros en el conjunto de registros. Por lo general esto debe realizarse desde el principio del conjunto de registros y llamando a `MoveNext` hasta `IsEOF` devuelve cero. Si este miembro es cero, el registro de recuento devuelto por `GetRecordCount`, si es de -1, solo un recuento de "marca de agua" de los registros.  
  
##  <a name="getsql"></a>  CRecordset::GetSQL  
 Llame a esta función miembro para obtener la instrucción SQL que se utiliza para seleccionar registros del conjunto de registros cuando se abre.  
  
```  
const CString& GetSQL() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un **const** hacen referencia a un `CString` que contiene la instrucción SQL.  
  
### <a name="remarks"></a>Comentarios  
 Esto suele ser una instancia de SQL **seleccione** instrucción. La cadena devuelta por `GetSQL` es de solo lectura.  
  
 La cadena devuelta por `GetSQL` suele ser diferente de cualquier cadena que se ha pasado al conjunto de registros en el *lpszSQL* parámetro para el `Open` función miembro. Esto es porque el conjunto de registros construye una instrucción SQL completa según lo que pasó a `Open`, especificado con el Asistente para clases, lo que puede que haya especificado en el `m_strFilter` y `m_strSort` miembros de datos y los parámetros que puede tener especificado. Para obtener información detallada acerca de cómo el conjunto de registros crea esta instrucción SQL, vea el artículo [conjunto de registros: cómo se seleccionan los registros (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md).  
  
> [!NOTE]
>  Llame a esta función miembro solo después de llamar a [abierto](#open).  
  
##  <a name="gettablename"></a>  CRecordset::GetTableName  
 Obtiene el nombre de la tabla SQL en el que se basa la consulta.  
  
```  
const CString& GetTableName() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un **const** hacen referencia a un `CString` que contiene la tabla el nombre, si el conjunto de registros se basa en una tabla; en caso contrario, una cadena vacía.  
  
### <a name="remarks"></a>Comentarios  
 `GetTableName` solo es válida si el conjunto de registros se basa en una tabla, no una combinación de varias tablas o una consulta predefinida (procedimiento almacenado). El nombre es de solo lectura.  
  
> [!NOTE]
>  Llame a esta función miembro solo después de llamar a [abierto](#open).  
  
##  <a name="isbof"></a>  CRecordset::IsBOF  
 Devuelve cero si el conjunto de registros se ha posicionado antes del primer registro. No hay ningún registro actual.  
  
```  
BOOL IsBOF() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el conjunto de registros no contiene registros o si se ha desplazado hacia atrás antes del primer registro; en caso contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función miembro antes de desplazarse de registro a registro para obtener información sobre si ha realizado antes del primer registro del conjunto de registros. También puede usar `IsBOF` junto con `IsEOF` para determinar si el conjunto de registros contiene registros o está vacío. Inmediatamente después de llamar a `Open`, si el conjunto de registros no contiene ningún registro, `IsBOF` devuelve cero. Al abrir un conjunto de registros que tiene al menos un registro, el primer registro es el registro actual y `IsBOF` devuelve 0.  
  
 Si el primer registro es el registro actual y se llama `MovePrev`, `IsBOF` posteriormente devolverá distinto de cero. Si `IsBOF` devuelve distinto de cero y se llama a `MovePrev`, se produce un error. Si `IsBOF` devuelve distinto de cero, el registro actual no está definido, y cualquier acción que requiere un registro actual se producirá un error.  
  
### <a name="example"></a>Ejemplo  
 Este ejemplo se utiliza `IsBOF` y `IsEOF` para detectar los límites de un conjunto de registros, como el código se desplaza por el conjunto de registros en ambas direcciones.  
  
 [!code-cpp[NVC_MFCDatabase#25](../../mfc/codesnippet/cpp/crecordset-class_9.cpp)]  
  
##  <a name="isdeleted"></a>  CRecordset::IsDeleted  
 Determina si se ha eliminado el registro actual.  
  
```  
BOOL IsDeleted() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el conjunto de registros está situado en un registro eliminado. en caso contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 Si se desplaza a un registro y `IsDeleted` devuelve TRUE (distinto de cero), a continuación, debe desplazarse a otro registro para poder realizar cualquier otra operación de conjunto de registros.  
  
 El resultado de `IsDeleted` depende de muchos factores, como el tipo de conjunto de registros, si el conjunto de registros es actualizable, si especificó el `CRecordset::skipDeletedRecords` opción cuando se abre el conjunto de registros, si los módulos de controlador de los registros eliminan y determinar si hay varios usuarios.  
  
 Para obtener más información acerca de `CRecordset::skipDeletedRecords` y controlador de empaquetado, consulte el [abierto](#open) función miembro.  
  
> [!NOTE]
>  Si ha implementado la obtención masiva de filas, no debe llamar `IsDeleted`. En su lugar, llame a la [GetRowStatus](#getrowstatus) función miembro. Para obtener más información sobre la obtención masiva de filas, vea el artículo [Conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
##  <a name="iseof"></a>  CRecordset::IsEOF  
 Devuelve cero si se ha colocado el conjunto de registros después del último registro. No hay ningún registro actual.  
  
```  
BOOL IsEOF() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el conjunto de registros no contiene registros o si se ha desplazado más allá del último registro; en caso contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función miembro como desplazarse de registro a registro para obtener información sobre si han ido más allá del último registro del conjunto de registros. También puede usar `IsEOF` para determinar si el conjunto de registros contiene registros o está vacío. Inmediatamente después de llamar a `Open`, si el conjunto de registros no contiene ningún registro, `IsEOF` devuelve cero. Al abrir un conjunto de registros que tiene al menos un registro, el primer registro es el registro actual y `IsEOF` devuelve 0.  
  
 Si el último registro es el registro actual cuando se llama a `MoveNext`, `IsEOF` posteriormente devolverá distinto de cero. Si `IsEOF` devuelve distinto de cero y se llama a `MoveNext`, se produce un error. Si `IsEOF` devuelve distinto de cero, el registro actual no está definido, y cualquier acción que requiere un registro actual se producirá un error.  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [IsBOF](#isbof).  
  
##  <a name="isfielddirty"></a>  CRecordset::IsFieldDirty  
 Determina si el miembro de datos del campo especificado ha cambiado desde [editar](#edit) o [AddNew](#addnew) llamó.  
  
```  
BOOL IsFieldDirty(void* pv);
```  
  
### <a name="parameters"></a>Parámetros  
 *PV*  
 Un puntero a miembro de datos del campo cuyo estado desea comprobar, o NULL para determinar si cualquiera de los campos estén modificado.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el miembro de datos del campo especificado ha cambiado desde que se llama `AddNew` o `Edit`; de lo contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Los datos en todos los miembros de datos de campos modificados se transferirá al registro en el origen de datos cuando se actualiza el registro actual mediante una llamada a la [actualización](#update) función miembro de `CRecordset` (después de una llamada a `Edit` o `AddNew`).  
  
> [!NOTE]
>  Esta función miembro no es aplicable en conjuntos de registros que se están usando la obtención masiva de filas. Si ha implementado obtención masiva de filas, a continuación, `IsFieldDirty` siempre devolverá FALSE y se producirá un error de aserción. Para obtener más información sobre la obtención masiva de filas, vea el artículo [Conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Una llamada a `IsFieldDirty` restablecerá los efectos de las anteriores llamadas a [SetFieldDirty](#setfielddirty) desde que se vuelve a evaluar el estado modificado del campo. En el `AddNew` caso, si el valor del campo actual difiere del valor null pseudo, el campo estado se establece desfasado. En el `Edit` caso, si el valor del campo difiere del valor almacenado en caché, el estado del campo se establece desfasado.  
  
 `IsFieldDirty` se implementa a través de [DoFieldExchange](#dofieldexchange).  
  
 Para obtener más información sobre la marca de modificado, consulte el artículo [conjunto de registros: cómo se seleccionan los registros (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md).  
  
##  <a name="isfieldnull"></a>  CRecordset::IsFieldNull  
 Devuelve cero si el campo especificado en el registro actual es nulo (no tiene ningún valor).  
  
```  
BOOL IsFieldNull(void* pv);
```  
  
### <a name="parameters"></a>Parámetros  
 *PV*  
 Un puntero a miembro de datos del campo cuyo estado desea comprobar o NULL para determinar si cualquiera de los campos son Null.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el miembro de datos del campo especificado se marca como Null; en caso contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función miembro para determinar si el miembro de un conjunto de registros de datos de campo especificado se ha marcado como Null. (En la terminología de base de datos, Null significa "no tener ningún valor" y no es igual a NULL en C++). Si un miembro de datos de campo se marca como Null, se interpreta como una columna del registro actual para el que no hay ningún valor.  
  
> [!NOTE]
>  Esta función miembro no es aplicable en conjuntos de registros que se están usando la obtención masiva de filas. Si ha implementado obtención masiva de filas, a continuación, `IsFieldNull` siempre devolverá FALSE y se producirá un error de aserción. Para obtener más información sobre la obtención masiva de filas, vea el artículo [Conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 `IsFieldNull` se implementa a través de [DoFieldExchange](#dofieldexchange).  
  
##  <a name="isfieldnullable"></a>  CRecordset::IsFieldNullable  
 Devuelve cero si el campo especificado en el registro actual se puede establecer en Null (con ningún valor).  
  
```  
BOOL IsFieldNullable(void* pv);
```  
  
### <a name="parameters"></a>Parámetros  
 *PV*  
 Un puntero a miembro de datos del campo cuyo estado desea comprobar, o NULL para determinar si cualquiera de los campos se pueden establecer en un valor Null.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función miembro determinar si el miembro de datos del campo especificado es "que acepta valores null" (se pueden establecer en un valor Null; C++ NULL no es igual a Null, lo que, en la terminología de base de datos, significa "no tener ningún valor").  
  
> [!NOTE]
>  Si ha implementado la obtención masiva de filas, no puede llamar a `IsFieldNullable`. En su lugar, llame a la [a GetODBCFieldInfo](#getodbcfieldinfo) función miembro para determinar si un campo se puede establecer en un valor Null. Tenga en cuenta que pueda llamar siempre a `GetODBCFieldInfo`, independientemente de si ha implementado la obtención masiva de filas. Para obtener más información sobre la obtención masiva de filas, vea el artículo [Conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Un campo que no puede ser Null debe tener un valor. Si se intenta establecer un este tipo de campo como Null al agregar o actualizar un registro, el origen de datos rechaza la adición o actualización, y [actualizar](#update) generará una excepción. La excepción se produce cuando se llama a `Update`, no cuando se llama a [SetFieldNull](#setfieldnull).  
  
 El uso de NULL para el primer argumento de la función aplicará solo a la función `outputColumn` campos, no `param` campos. Por ejemplo, la llamada  
  
 [!code-cpp[NVC_MFCDatabase#26](../../mfc/codesnippet/cpp/crecordset-class_10.cpp)]  
  
 establecerá sólo `outputColumn` campos con NULL; `param` campos no se verán afectados.  
  
 Para trabajar en `param` campos, debe proporcionar la dirección real de la persona `param` que desea trabajar, tales como:  
  
 [!code-cpp[NVC_MFCDatabase#27](../../mfc/codesnippet/cpp/crecordset-class_11.cpp)]  
  
 Esto significa que no se puede establecer en todos los `param` campos con valores NULL, se puede hacer con `outputColumn` campos.  
  
 `IsFieldNullable` se implementa a través de [DoFieldExchange](#dofieldexchange).  
  
##  <a name="isopen"></a>  CRecordset::IsOpen  
 Determina si el conjunto de registros ya está abierto.  
  
```  
BOOL IsOpen() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el objeto recordset [abierto](#open) o [Requery](#requery) función miembro se ha llamado previamente y el conjunto de registros no se ha cerrado; en caso contrario, 0.  
  
##  <a name="m_hstmt"></a>  CRecordset:: M_hstmt  
 Contiene un identificador de la estructura de datos de la instrucción de ODBC de tipo HSTMT, asociado con el conjunto de registros.  
  
### <a name="remarks"></a>Comentarios  
 Cada consulta a un origen de datos ODBC está asociado con un valor de HSTMT.  
  
> [!CAUTION]
>  No use `m_hstmt` antes [abierto](#open) se ha llamado.  
  
 Normalmente no es necesario tener acceso a la HSTMT directamente, pero es posible que necesite para la ejecución directa de instrucciones SQL. El `ExecuteSQL` función miembro de clase `CDatabase` proporciona un ejemplo del uso `m_hstmt`.  
  
##  <a name="m_nfields"></a>  CRecordset::m_nFields  
 Contiene el número de miembros de datos en la clase de conjunto de registros; es decir, el número de columnas seleccionadas por el conjunto de registros del origen de datos.  
  
### <a name="remarks"></a>Comentarios  
 Debe inicializar el constructor de la clase de conjunto de registros `m_nFields` con el número correcto. Si no ha implementado la obtención masiva de filas, ClassWizard escribe esta inicialización automáticamente cuando se usa para declarar la clase de conjunto de registros. También puede escribir manualmente.  
  
 El marco de trabajo utiliza este número para administrar la interacción entre los miembros de datos de campo y las columnas correspondientes del registro actual en el origen de datos.  
  
> [!CAUTION]
>  Este número debe coincidir con el número de "columnas de salida" registrado en `DoFieldExchange` o `DoBulkFieldExchange` después de llamar a [SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype) con el parámetro `CFieldExchange::outputColumn`.  
  
 Se pueden enlazar columnas dinámicamente, como se explica en el artículo "conjunto de registros: dinámicamente las columnas de datos de enlace." Si lo hace, debe aumentar el recuento en `m_nFields` para reflejar el número de función RFX o RFX masivo llamadas su `DoFieldExchange` o `DoBulkFieldExchange` función miembro para las columnas enlazadas dinámicamente.  
  
 Para obtener más información, consulte los artículos [conjunto de registros: enlazar dinámicamente columnas de datos (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md) y [conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
### <a name="example"></a>Ejemplo  
 Consulte el artículo [intercambio de campos de registros: Utilizar RFX](../../data/odbc/record-field-exchange-using-rfx.md).  
  
##  <a name="m_nparams"></a>  CRecordset::m_nParams  
 Contiene el número de miembros de datos de parámetro en la clase de conjunto de registros; es decir, el número de parámetros pasados con la consulta.  
  
### <a name="remarks"></a>Comentarios  
 Si la clase de conjunto de registros tiene miembros de datos de parámetro, debe inicializar el constructor de la clase `m_nParams` con el número correcto. El valor de `m_nParams` el valor predeterminado es 0. Si agrega miembros de datos de parámetro (lo que debe hacer manualmente) debe agregar manualmente una inicialización en el constructor de clase para reflejar el número de parámetros (que debe ser al menos tan grande como el número de '' marcadores de posición en su `m_strFilter` o `m_strSort`cadena).  
  
 El marco de trabajo utiliza este número cuando parametriza la consulta.  
  
> [!CAUTION]
>  Este número debe coincidir con el número de "params" registrado en `DoFieldExchange` o `DoBulkFieldExchange` después de llamar a [SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype) con un valor de parámetro `CFieldExchange::inputParam`, `CFieldExchange::param`, `CFieldExchange::outputParam`, o `CFieldExchange::inoutParam`.  
  
### <a name="example"></a>Ejemplo  
  Consulte los artículos [conjunto de registros: parametrizar un conjunto de registros (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md) y [intercambio de campos de registros: Utilizar RFX](../../data/odbc/record-field-exchange-using-rfx.md).  
  
##  <a name="m_pdatabase"></a>  CRecordset::m_pDatabase  
 Contiene un puntero a la `CDatabase` a través del cual el conjunto de registros está conectado a un origen de datos de objeto.  
  
### <a name="remarks"></a>Comentarios  
 Esta variable se establece en dos formas. Por lo general, pasar un puntero a una ya conectado `CDatabase` cuando se construye el objeto recordset de objetos. Si se pasa NULL en su lugar, `CRecordset` crea un `CDatabase` de objeto para usted y lo conecta. En cualquier caso, `CRecordset` almacena el puntero en esta variable.  
  
 Normalmente no directamente debe usar el puntero almacenado en `m_pDatabase`. Si escribe sus propias extensiones para `CRecordset`, sin embargo, es posible que deba utilizar el puntero. Por ejemplo, es posible que necesita el puntero si lanza su `CDBException`s. O tal vez necesite si tiene que hacer algo con el mismo `CDatabase` objeto, como la ejecución de transacciones, tiempos de espera de la configuración, o llamar a la `ExecuteSQL` función miembro de clase `CDatabase` para ejecutar instrucciones SQL directamente.  
  
##  <a name="m_strfilter"></a>  CRecordset:: M_strfilter  
 Después de crear el objeto de conjunto de registros, pero antes de llamar a su `Open` miembro de función, utilice este miembro de datos para almacenar un `CString` que contiene una instancia de SQL **donde** cláusula.  
  
### <a name="remarks"></a>Comentarios  
 El conjunto de registros usa esta cadena para restringir (o filtrar) en los registros selecciona durante la `Open` o `Requery` llamar. Esto es útil para seleccionar un subconjunto de registros, como "todos los vendedores con sede en California" ("estado = CA"). La sintaxis SQL de ODBC para un **donde** cláusula es  
  
 `WHERE search-condition`  
  
 Tenga en cuenta que no incluye el **donde** palabra clave en la cadena. Lo proporciona el marco de trabajo.  
  
 También se puede parametrizar la cadena de filtro mediante la colocación de '' marcadores de posición, declarar un miembro de datos de parámetro en la clase para cada marcador de posición y pasar parámetros al conjunto de registros en tiempo de ejecución. Esto le permite construir el filtro en tiempo de ejecución. Para obtener más información, vea el artículo [conjunto de registros: parametrizar un conjunto de registros (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).  
  
 Para obtener más información acerca de SQL **donde** cláusulas, vea el artículo [SQL](../../data/odbc/sql.md). Para obtener más información sobre cómo seleccionar y filtrar registros, vea el artículo [conjunto de registros: filtrar registros (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDatabase#30](../../mfc/codesnippet/cpp/crecordset-class_12.cpp)]  
  
##  <a name="m_strsort"></a>  CRecordset::m_strSort  
 Después de crear el objeto de conjunto de registros, pero antes de llamar a su `Open` miembro de función, utilice este miembro de datos para almacenar un `CString` que contiene una instancia de SQL **ORDER BY** cláusula.  
  
### <a name="remarks"></a>Comentarios  
 El conjunto de registros usa esta cadena para ordenar los registros selecciona durante la `Open` o `Requery` llamar. Puede usar esta característica para ordenar un conjunto de registros en una o varias columnas. La sintaxis SQL de ODBC para un **ORDER BY** cláusula es  
  
 `ORDER BY sort-specification [, sort-specification]...`  
  
 donde una especificación de ordenación es un entero o un nombre de columna. También puede especificar el orden ascendente o descendente (el orden es ascendente de forma predeterminada) mediante la anexión de "ASC" o "DESC" en la lista de columnas en la cadena de ordenación. Los registros seleccionados aparecen ordenados primero por la primera columna y luego por el segundo y así sucesivamente. Por ejemplo, puede ordenar un conjunto de registros "Customers" por apellido y luego por nombres. El número de columnas que puede enumerar depende del origen de datos. Para obtener más información, consulte el SDK de Windows.  
  
 Tenga en cuenta que no incluye el **ORDER BY** palabra clave en la cadena. Lo proporciona el marco de trabajo.  
  
 Para obtener más información acerca de las cláusulas SQL, vea el artículo [SQL](../../data/odbc/sql.md). Para obtener más información sobre cómo ordenar los registros, vea el artículo [conjunto de registros: ordenar registros (ODBC)](../../data/odbc/recordset-sorting-records-odbc.md).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDatabase#31](../../mfc/codesnippet/cpp/crecordset-class_13.cpp)]  
  
##  <a name="move"></a>  CRecordset:: Move  
 Mueve el puntero de registro actual en el conjunto de registros, hacia delante o hacia atrás.  
  
```  
virtual void Move(
    long nRows,  
    WORD wFetchType = SQL_FETCH_RELATIVE);
```  
  
### <a name="parameters"></a>Parámetros  
 *nRows*  
 El número de filas que debe desplazarse hacia delante o hacia atrás. Los valores positivos mueven hacia delante, hacia el final del conjunto de registros. Los valores negativos se mueven hacia atrás y hacia el principio.  
  
 *wFetchType*  
 Determina el conjunto de filas que `Move` capturará. Para conocer más detalles, vea la sección Comentarios.  
  
### <a name="remarks"></a>Comentarios  
 Si se pasa un valor de 0 para *nRows*, `Move` actualiza el registro actual; `Move` finalizará cualquier actual `AddNew` o `Edit` modo y se restaurará el valor del registro actual antes de `AddNew` o `Edit` llamó.  
  
> [!NOTE]
>  Cuando se mueve a través de un conjunto de registros, no se puede omitir los registros eliminados. Consulte [CRecordset::IsDeleted](#isdeleted) para obtener más información. Al abrir un `CRecordset` con el `skipDeletedRecords` establecida, la opción `Move` valida si el *nRows* parámetro es 0. Este comportamiento impide que la actualización de filas eliminadas por otras aplicaciones de cliente con los mismos datos. Consulte la *dwOption* parámetro [abierto](#open) para obtener una descripción de `skipDeletedRecords`.  
  
 `Move` cambia de posición el conjunto de registros por conjuntos de filas. Según los valores de *nRows* y *wFetchType*, `Move` recupera el conjunto de filas adecuado y, a continuación, convierte el primer registro en ese conjunto de filas del registro actual. Si no ha implementado la obtención masiva de filas, el tamaño del conjunto de filas es siempre 1. Al capturar un conjunto de filas, `Move` llama directamente el [CheckRowsetError](#checkrowseterror) función miembro para controlar los errores resultantes de la operación de captura.  
  
 Dependiendo de los valores pasados, `Move` es equivalente a otra `CRecordset` funciones miembro. En concreto, el valor de *wFetchType* puede indicar una función miembro que es más intuitiva y a menudo el método preferido para mover el registro actual.  
  
 La tabla siguiente enumeran los valores posibles para *wFetchType*, el conjunto de filas que `Move` capturará según *wFetchType* y *nRows*y cualquier equivalente función de miembro correspondiente a *wFetchType*.  
  
|wFetchType|Conjunto de filas capturada|Función miembro equivalente|  
|----------------|--------------------|--------------------------------|  
|SQL_FETCH_RELATIVE (el valor predeterminado)|El conjunto de filas a partir *nRows* filas de la primera fila del conjunto de filas actual.||  
|SQL_FETCH_NEXT|El siguiente conjunto de filas; *nRows* se omite.|[MoveNext](#movenext)|  
|SQL_FETCH_PRIOR|El conjunto de filas anterior; *nRows* se omite.|[MovePrev](#moveprev)|  
|SQL_FETCH_FIRST|El primer conjunto de filas del conjunto de registros; *nRows* se omite.|[MoveFirst](#movefirst)|  
|SQL_FETCH_LAST|El último conjunto de filas completo en el conjunto de registros; *nRows* se omite.|[MoveLast](#movelast)|  
|SQL_FETCH_ABSOLUTE|Si *nRows* > 0, el conjunto de filas a partir *nRows* filas desde el principio del conjunto de registros. Si *nRows* < 0, el conjunto de filas a partir *nRows* filas desde el final del conjunto de registros. Si *nRows* = 0, se devuelve una condición de inicio del archivo (BOF).|[SetAbsolutePosition](#setabsoluteposition)|  
|SQL_FETCH_BOOKMARK|Empezando por la fila cuyo valor de marcador se corresponde con el conjunto de filas *nRows*.|[SetBookmark](#setbookmark)|  
  
> [!NOTE]
>  Para conjuntos de registros solo hacia delante, `Move` sólo es válido con un valor de SQL_FETCH_NEXT para *wFetchType*.  
  
> [!CAUTION]
>  Una llamada a `Move` produce una excepción si el conjunto de registros no tiene registros. Para determinar si el conjunto de registros tiene todos los registros, llame a [IsBOF](#isbof) y [IsEOF](#iseof).  
  
> [!NOTE]
>  Si se ha desplazado más allá del principio o final del conjunto de registros (`IsBOF` o `IsEOF` devuelve distinto de cero), al llamar a un `Move` función, posiblemente, se producirá un `CDBException`. Por ejemplo, si `IsEOF` devuelve distinto de cero y `IsBOF` no es así, a continuación, `MoveNext` se iniciará una excepción, pero `MovePrev` no lo hará.  
  
> [!NOTE]
>  Si se llama a `Move` mientras que el registro actual se va a actualizar o agregar, las actualizaciones se pierden sin previo aviso.  
  
 Para obtener más información sobre la navegación del conjunto de registros, consulte los artículos [conjunto de registros: desplazamiento (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) y [conjunto de registros: marcadores y posiciones absolutas (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md). Para obtener más información sobre la obtención masiva de filas, vea el artículo [Conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md). Para obtener información relacionada, vea la función de la API de ODBC `SQLExtendedFetch` en el SDK de Windows.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDatabase#28](../../mfc/codesnippet/cpp/crecordset-class_14.cpp)]  
  
##  <a name="movefirst"></a>  CRecordset::MoveFirst  
 Convierte el primer registro en el primer conjunto de filas del registro actual.  
  
```  
void MoveFirst();
```  
  
### <a name="remarks"></a>Comentarios  
 Independientemente de si la obtención masiva de filas se ha implementado, siempre será el primer registro en el conjunto de registros.  
  
 No es necesario llamar a `MoveFirst` inmediatamente después de abrir el conjunto de registros. En ese momento, el primer registro (si existe) es automáticamente el registro actual.  
  
> [!NOTE]
>  Esta función miembro no es válida para los conjuntos de registros solo hacia delante.  
  
> [!NOTE]
>  Cuando se mueve a través de un conjunto de registros, no se puede omitir los registros eliminados. Consulte la [IsDeleted](#isdeleted) función miembro para obtener más información.  
  
> [!CAUTION]
>  Llamar a cualquiera de los `Move` funciones produce una excepción si el conjunto de registros no tiene registros. Para determinar si el conjunto de registros tiene todos los registros, llame a `IsBOF` y `IsEOF`.  
  
> [!NOTE]
>  Si se llama a cualquiera de los `Move` funciona mientras el registro actual se actualiza o agregado, las actualizaciones se pierden sin previo aviso.  
  
 Para obtener más información sobre la navegación del conjunto de registros, consulte los artículos [conjunto de registros: desplazamiento (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) y [conjunto de registros: marcadores y posiciones absolutas (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md). Para obtener más información sobre la obtención masiva de filas, vea el artículo [Conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [IsBOF](#isbof).  
  
##  <a name="movelast"></a>  CRecordset::MoveLast  
 Convierte el primer registro en el último conjunto de filas completa el registro actual.  
  
```  
void MoveLast();
```  
  
### <a name="remarks"></a>Comentarios  
 Si no ha implementado la obtención masiva de filas, el conjunto de registros tiene un tamaño de conjunto de filas de 1, por lo que `MoveLast` simplemente se desplaza al último registro del conjunto de registros.  
  
> [!NOTE]
>  Esta función miembro no es válida para los conjuntos de registros solo hacia delante.  
  
> [!NOTE]
>  Cuando se mueve a través de un conjunto de registros, no se puede omitir los registros eliminados. Consulte la [IsDeleted](#isdeleted) función miembro para obtener más información.  
  
> [!CAUTION]
>  Llamar a cualquiera de los `Move` funciones produce una excepción si el conjunto de registros no tiene registros. Para determinar si el conjunto de registros tiene todos los registros, llame a `IsBOF` y `IsEOF`.  
  
> [!NOTE]
>  Si se llama a cualquiera de los `Move` funciona mientras el registro actual se actualiza o agregado, las actualizaciones se pierden sin previo aviso.  
  
 Para obtener más información sobre la navegación del conjunto de registros, consulte los artículos [conjunto de registros: desplazamiento (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) y [conjunto de registros: marcadores y posiciones absolutas (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md). Para obtener más información sobre la obtención masiva de filas, vea el artículo [Conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [IsBOF](#isbof).  
  
##  <a name="movenext"></a>  CRecordset::MoveNext  
 Convierte el primer registro en el siguiente conjunto de filas del registro actual.  
  
```  
void MoveNext();
```  
  
### <a name="remarks"></a>Comentarios  
 Si no ha implementado la obtención masiva de filas, el conjunto de registros tiene un tamaño de conjunto de filas de 1, por lo que `MoveNext` simplemente se mueve al siguiente registro.  
  
> [!NOTE]
>  Cuando se mueve a través de un conjunto de registros, no se puede omitir los registros eliminados. Consulte la [IsDeleted](#isdeleted) función miembro para obtener más información.  
  
> [!CAUTION]
>  Llamar a cualquiera de los `Move` funciones produce una excepción si el conjunto de registros no tiene registros. Para determinar si el conjunto de registros tiene todos los registros, llame a `IsBOF` y `IsEOF`.  
  
> [!NOTE]
>  También se recomienda que llame a `IsEOF` antes de llamar a `MoveNext`. Por ejemplo, si se ha desplazado más allá del final del conjunto de registros, `IsEOF` devolverá distinto de cero; una llamada subsiguiente a `MoveNext` generaría una excepción.  
  
> [!NOTE]
>  Si se llama a cualquiera de los `Move` funciona mientras el registro actual se actualiza o agregado, las actualizaciones se pierden sin previo aviso.  
  
 Para obtener más información sobre la navegación del conjunto de registros, consulte los artículos [conjunto de registros: desplazamiento (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) y [conjunto de registros: marcadores y posiciones absolutas (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md). Para obtener más información sobre la obtención masiva de filas, vea el artículo [Conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [IsBOF](#isbof).  
  
##  <a name="moveprev"></a>  CRecordset::MovePrev  
 Convierte el primer registro en el conjunto de filas anterior del registro actual.  
  
```  
void MovePrev();
```  
  
### <a name="remarks"></a>Comentarios  
 Si no ha implementado la obtención masiva de filas, el conjunto de registros tiene un tamaño de conjunto de filas de 1, por lo que `MovePrev` simplemente se mueve al registro anterior.  
  
> [!NOTE]
>  Esta función miembro no es válida para los conjuntos de registros solo hacia delante.  
  
> [!NOTE]
>  Cuando se mueve a través de un conjunto de registros, no se puede omitir los registros eliminados. Consulte la [IsDeleted](#isdeleted) función miembro para obtener más información.  
  
> [!CAUTION]
>  Llamar a cualquiera de los `Move` funciones produce una excepción si el conjunto de registros no tiene registros. Para determinar si el conjunto de registros tiene todos los registros, llame a `IsBOF` y `IsEOF`.  
  
> [!NOTE]
>  También se recomienda que llame a `IsBOF` antes de llamar a `MovePrev`. Por ejemplo, si se ha desplazado el comienzo del conjunto de registros, `IsBOF` devolverá distinto de cero; una llamada subsiguiente a `MovePrev` generaría una excepción.  
  
> [!NOTE]
>  Si se llama a cualquiera de los `Move` funciona mientras el registro actual se actualiza o agregado, las actualizaciones se pierden sin previo aviso.  
  
 Para obtener más información sobre la navegación del conjunto de registros, consulte los artículos [conjunto de registros: desplazamiento (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) y [conjunto de registros: marcadores y posiciones absolutas (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md). Para obtener más información sobre la obtención masiva de filas, vea el artículo [Conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [IsBOF](#isbof).  
  
##  <a name="onsetoptions"></a>  CRecordset::OnSetOptions  
 Se llama para establecer las opciones (que se usa en la selección) para la instrucción ODBC especificada.  
  
```  
virtual void OnSetOptions(HSTMT hstmt);
```  
  
### <a name="parameters"></a>Parámetros  
 *HStmt*  
 HSTMT de la instrucción ODBC cuyas opciones que se van a establecer.  
  
### <a name="remarks"></a>Comentarios  
 Llame a `OnSetOptions` para establecer las opciones (que se usa en la selección) para la instrucción ODBC especificada. El marco de trabajo llama a esta función miembro para establecer las opciones iniciales para el conjunto de registros. `OnSetOptions` Determina la compatibilidad con los cursores desplazables y simultaneidad de cursor del origen de datos y establece las opciones del conjunto de registros en consecuencia. (Mientras que `OnSetOptions` se utiliza para operaciones de selección, `OnSetUpdateOptions` se usa para las operaciones de actualización.)  
  
 Invalidar `OnSetOptions` para establecer las opciones específicas para el controlador o el origen de datos. Por ejemplo, si se admite la apertura de obtener un acceso exclusivo de origen de datos, podría invalidar `OnSetOptions` aprovechar esa capacidad.  
  
 Para obtener más información acerca de los cursores, vea el artículo [ODBC](../../data/odbc/odbc-basics.md).  
  
##  <a name="onsetupdateoptions"></a>  CRecordset::OnSetUpdateOptions  
 Se llama para establecer las opciones (que se usa en la actualización) para la instrucción ODBC especificada.  
  
```  
virtual void OnSetUpdateOptions(HSTMT hstmt);
```  
  
### <a name="parameters"></a>Parámetros  
 *HStmt*  
 HSTMT de la instrucción ODBC cuyas opciones que se van a establecer.  
  
### <a name="remarks"></a>Comentarios  
 Llame a `OnSetUpdateOptions` para establecer las opciones (que se usa en la actualización) para la instrucción ODBC especificada. El marco de trabajo llama a esta función miembro después de crear un HSTMT para actualizar registros en un conjunto de registros. (Mientras que `OnSetOptions` se utiliza para operaciones de selección, `OnSetUpdateOptions` se usa para las operaciones de actualización.) `OnSetUpdateOptions` determina la compatibilidad con los cursores desplazables y simultaneidad de cursor del origen de datos y establece las opciones del conjunto de registros en consecuencia.  
  
 Invalidar `OnSetUpdateOptions` para establecer las opciones de una instrucción ODBC antes de esa instrucción se usa para tener acceso a una base de datos.  
  
 Para obtener más información acerca de los cursores, vea el artículo [ODBC](../../data/odbc/odbc-basics.md).  
  
##  <a name="open"></a>  CRecordset:: Open  
 Abre el conjunto de registros recuperando la tabla o realizando la consulta que el conjunto de registros representa.  
  
```  
virtual BOOL Open(
    UINT nOpenType = AFX_DB_USE_DEFAULT_TYPE,  
    LPCTSTR lpszSQL = NULL,  
    DWORD dwOptions = none);
```  
  
### <a name="parameters"></a>Parámetros  
 *nOpenType*  
 Acepte el valor predeterminado, AFX_DB_USE_DEFAULT_TYPE o use uno de los siguientes valores en el `enum OpenType`:  
  
- `CRecordset::dynaset` Un conjunto de registros con desplazamiento bidireccional. La pertenencia y el orden de los registros se determinan cuando se abre el conjunto de registros, pero los cambios realizados por otros usuarios en los valores de datos son visibles después de una operación de recuperación de cambios. Los dynasets también se conocen como conjuntos de registros conjunto controlados por conjuntos de claves.  
  
- `CRecordset::snapshot` Un conjunto de registros estático con desplazamiento bidireccional. La pertenencia y el orden de los registros se determinan cuando se abre el conjunto de registros; los valores de datos se determinan cuando se buscan los registros. Los cambios realizados por otros usuarios no son visibles hasta que no se cierra y se vuelve a abrir el conjunto de registros.  
  
- `CRecordset::dynamic` Un conjunto de registros con desplazamiento bidireccional. Los cambios realizados por otros usuarios en la pertenencia, el orden y los valores de datos son visibles después de una operación de recuperación de cambios. Tenga en cuenta que muchos controladores ODBC no admiten este tipo de conjunto de registros.  
  
- `CRecordset::forwardOnly` Un conjunto de registros de solo lectura con desplazamiento sólo hacia delante.  
  
     Para `CRecordset`, el valor predeterminado es `CRecordset::snapshot`. El mecanismo de valor predeterminado permite que los asistentes de Visual C++ interactúen con `CRecordset` de ODBC y `CDaoRecordset` de DAO, que tienen valores predeterminados diferentes.  
  
 Para obtener más información acerca de estos tipos de conjunto de registros, vea el artículo [conjunto de registros (ODBC)](../../data/odbc/recordset-odbc.md). Para obtener información relacionada, vea el artículo "Uso de bloque y los cursores desplazables" en el SDK de Windows.  
  
> [!CAUTION]
>  Si el tipo solicitado no se admite, el marco de trabajo produce una excepción.  
  
 *lpszSQL*  
 Puntero de cadena que contiene uno de los elementos siguientes:  
  
-   Un puntero NULL.  
  
-   Nombre de una tabla.  
  
-   Una instancia de SQL **seleccione** instrucción (opcionalmente con una instancia de SQL **donde** o **ORDER BY** cláusula).  
  
-   Un **llamar** instrucción especificando el nombre de una consulta predefinida (procedimiento almacenado). Tenga cuidado de no insertar espacios en blanco entre la llave y la **llamar** palabra clave.  
  
 Para obtener más información sobre esta cadena, vea la tabla y la descripción del rol de ClassWizard en Comentarios.  
  
> [!NOTE]
>  El orden de las columnas del conjunto de resultados debe coincidir con el orden de lo RFX o llamadas función RFX masivo en su [DoFieldExchange](#dofieldexchange) o [DoBulkFieldExchange](#dobulkfieldexchange) función invalidación.  
  
 *dwOptions*  
 Máscara de bits que puede especificar una combinación de los valores que se muestran a continuación. Algunas de estas opciones son mutuamente excluyentes. El valor predeterminado es **ninguno**.  
  
- `CRecordset::none` Ningún conjunto de opciones. Este valor del parámetro es mutuamente excluyente con todos los demás valores. De forma predeterminada, se puede actualizar el conjunto de registros con [editar](#edit) o [eliminar](#delete) y permite anexar nuevos registros con [AddNew](#addnew). Capacidad de actualización depende del origen de datos, así como en el *nOpenType* opción especificada. La optimización para adiciones masivas no está disponible. La obtención masiva de filas no se implementará. Los registros eliminados no se omitirán al navegar por el conjunto de registros. Los marcadores no están disponibles. Se implementa la comprobación automática de campos modificados.  
  
- `CRecordset::appendOnly` No permitir `Edit` o `Delete` en el conjunto de registros. Solo permite `AddNew`. Esta opción es mutuamente excluyente con `CRecordset::readOnly`.  
  
- `CRecordset::readOnly` Abra el conjunto de registros como de solo lectura. Esta opción es mutuamente excluyente con `CRecordset::appendOnly`.  
  
- `CRecordset::optimizeBulkAdd` Utilice una instrucción SQL preparada para optimizar la adición de muchos registros al mismo tiempo. Solo se aplica si no usa la función de la API de ODBC `SQLSetPos` para actualizar el conjunto de registros. La primera actualización determina qué campos se marcan como modificados. Esta opción es mutuamente excluyente con `CRecordset::useMultiRowFetch`.  
  
- `CRecordset::useMultiRowFetch` Implementar la obtención masiva de filas para permitir que varias filas que van a recuperar en una única operación de búsqueda. Se trata de una característica avanzada diseñada para mejorar el rendimiento; sin embargo, el Asistente para clases no admite el intercambio masivo de campos de registros. Esta opción es mutuamente excluyente con `CRecordset::optimizeBulkAdd`. Tenga en cuenta que si especifica `CRecordset::useMultiRowFetch`, a continuación, la opción `CRecordset::noDirtyFieldCheck` se activará automáticamente (almacenamiento en búfer doble no estará disponible); en conjuntos de solo avance, la opción `CRecordset::useExtendedFetch` se activará automáticamente. Para obtener más información sobre la obtención masiva de filas, vea el artículo [Conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
- `CRecordset::skipDeletedRecords` Omitir eliminados todos los registros cuando se navega por el conjunto de registros. Esto ralentiza el rendimiento en ciertas búsquedas relativas. Esta opción no es válida en los conjuntos de registros solo hacia delante. Si se llama a [mover](#move) con el *nRows* parámetro establecido en 0 y el `CRecordset::skipDeletedRecords` establecida, la opción `Move` se producirá una aserción. Tenga en cuenta que `CRecordset::skipDeletedRecords` es similar a *empaquetado de controladores*, lo que significa que las filas eliminadas se quita del conjunto de registros. Sin embargo, si el controlador empaqueta registros, solo se omitirán los registros que elimine; no se omitirán los registros eliminados por otros usuarios mientras el conjunto de registros está abierto. `CRecordset::skipDeletedRecords` omitirá las filas eliminadas por otros usuarios.  
  
- `CRecordset::useBookmarks` Puede utilizar marcadores en el conjunto de registros, si se admite. Los marcadores ralentizan la recuperación de datos pero mejoran el rendimiento de la navegación de datos. No es válida en conjuntos de registros solo hacia delante. Para obtener más información, vea el artículo [conjunto de registros: marcadores y posiciones absolutas (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md).  
  
- `CRecordset::noDirtyFieldCheck` Desactive la opción automática de campos modificados comprobación (almacenamiento en búfer doble). Esto mejorará el rendimiento; sin embargo, para marcar manualmente los campos como modificados se debe llamar a las funciones miembro `SetFieldDirty` y `SetFieldNull`. Tenga en cuenta que el almacenamiento en búfer doble en la clase `CRecordset` es similar al almacenamiento en búfer doble en la clase `CDaoRecordset`. Sin embargo, en `CRecordset`, no se puede habilitar el almacenamiento en búfer doble en campos individuales; hay que habilitarlo o deshabilitarlo para todos los campos. Tenga en cuenta que si especifica la opción `CRecordset::useMultiRowFetch`, a continuación, `CRecordset::noDirtyFieldCheck` se activará automáticamente; sin embargo, `SetFieldDirty` y `SetFieldNull` no se puede utilizar en conjuntos de registros que implementan la obtención masiva de filas.  
  
- `CRecordset::executeDirect` No utilice una instrucción SQL preparada. Para mejorar el rendimiento, especifique esta opción si el `Requery` nunca se llamará la función miembro.  
  
- `CRecordset::useExtendedFetch` Implemente `SQLExtendedFetch` en lugar de `SQLFetch`. Está diseñado para implementar la obtención masiva de filas en conjuntos de registros solo hacia delante. Si especifica la opción `CRecordset::useMultiRowFetch` en un recordset sólo hacia delante, a continuación, `CRecordset::useExtendedFetch` se activará automáticamente.  
  
- `CRecordset::userAllocMultiRowBuffers` El usuario asignará búferes de almacenamiento para los datos. Utilice esta opción junto con `CRecordset::useMultiRowFetch` si desea asignar su propio almacenamiento; de lo contrario, el marco de trabajo asignará automáticamente el almacenamiento necesario. Para obtener más información, vea el artículo [conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md). Tenga en cuenta que si se especifica `CRecordset::userAllocMultiRowBuffers` sin especificar `CRecordset::useMultiRowFetch` dará como resultado un error de aserción.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el `CRecordset` objeto se abrió correctamente; en caso contrario, 0 si [CDatabase:: Open](../../mfc/reference/cdatabase-class.md#open) (si se llama) devuelve 0.  
  
### <a name="remarks"></a>Comentarios  
 Se debe llamar a esta función miembro para ejecutar la consulta definida por el conjunto de registros. Antes de llamar a `Open`, debe construir el objeto de conjunto de registros.  
  
 Conexión de este conjunto de registros con el origen de datos depende de cómo se crea el conjunto de registros antes de llamar a `Open`. Si se pasa un [CDatabase](../../mfc/reference/cdatabase-class.md) objeto al constructor de conjunto de registros que no se ha conectado al origen de datos, esta función miembro utiliza [GetDefaultConnect](#getdefaultconnect) para intentar abrir el objeto de base de datos. Si se pasa NULL para el constructor del conjunto de registros, el constructor crea un `CDatabase` objeto, y `Open` intenta conectarse el objeto de base de datos. Para obtener más información al cerrar el conjunto de registros y la conexión en estas circunstancias variables, consulte [cerrar](#close).  
  
> [!NOTE]
>  El acceso a un origen de datos mediante un objeto `CRecordset` siempre es compartido. A diferencia de la clase `CDaoRecordset`, no se puede utilizar un objeto `CRecordset` para abrir un origen de datos con acceso exclusivo.  
  
 Cuando se llama a `Open`, una consulta, normalmente una instancia de SQL **seleccione** instrucción, selecciona los registros según los criterios que se muestra en la tabla siguiente.  
  
|Valor del parámetro lpszSQL|Los registros seleccionados están determinados por|Ejemplo|  
|------------------------------------|----------------------------------------|-------------|  
|NULL|La cadena devuelta por `GetDefaultSQL`.||  
|Nombre de tabla SQL|Todas las columnas de la lista de tablas de `DoFieldExchange` o `DoBulkFieldExchange`.|`"Customer"`|  
|Nombre de la consulta (procedimiento almacenado) predefinida|Las columnas de la consulta cuya devolución se ha definido.|`"{call OverDueAccts}"`|  
|**Seleccione** lista de columnas **FROM** lista de tablas|Las columnas especificadas de las tablas indicadas.|`"SELECT CustId, CustName FROM`<br /><br /> `Customer"`|  
  
> [!CAUTION]
>  Tenga cuidado de no insertar espacios en blanco adicionales en la cadena SQL. Por ejemplo, si inserta un espacio en blanco entre la llave y la **llamar a** palabra clave, MFC interpretará incorrectamente la cadena SQL como un nombre de tabla y la incorporará en un **seleccione** instrucción, lo que dará como resultado una excepción producida. De forma similar, si la consulta predefinida utiliza un parámetro de salida, no inserte un espacio en blanco entre la llave y el "símbolo. Por último, no debe insertar un espacio en blanco antes de la llave de cierre en un **llamar** instrucción o antes de la **seleccione** palabra clave en un **seleccione** instrucción.  
  
 El procedimiento habitual consiste en pasar NULL para `Open`; en este caso, `Open` llamadas [GetDefaultSQL](#getdefaultsql). Si usas una derivada `CRecordset` (clase), `GetDefaultSQL` proporciona los nombres de tabla que especificó en el Asistente para clases. Se puede especificar otra información en el parámetro `lpszSQL`.  
  
 Cualquier valor que pase `Open` construye una cadena SQL final para la consulta (la cadena puede tener SQL **donde** y **ORDER BY** anexadas cláusulas a la `lpszSQL` cadena pasó) y, a continuación, se ejecuta la consulta. Puede examinar la cadena que se crea mediante una llamada a [GetSQL](#getsql) después de llamar a *`Open`. Para obtener más detalles acerca de cómo el conjunto de registros crea una instrucción SQL y selecciona los registros, vea el artículo [conjunto de registros: cómo se seleccionan los registros (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md).  
  
 Los miembros de datos de campo de la clase de conjunto de registros están enlazados a las columnas de los datos seleccionados. Si se devuelve algún registro, el primer registro se convierte en el registro actual.  
  
 Si desea establecer las opciones para el conjunto de registros, por ejemplo, un filtro o criterio, especificarlos después de crear el objeto de conjunto de registros pero antes de llamar a `Open`. Si desea que los registros del conjunto de registros después de actualizar el conjunto de registros está abierto, llame a [Requery](#requery).  
  
 Para obtener más información, incluidos ejemplos adicionales, consulte los artículos [conjunto de registros (ODBC)](../../data/odbc/recordset-odbc.md), [conjunto de registros: cómo se seleccionan los registros (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md), y [conjunto de registros: crear y cerrar Conjuntos de registros (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md).  
  
### <a name="example"></a>Ejemplo  
 Ejemplos de código siguientes muestran distintas formas de la `Open` llamar.  
  
 [!code-cpp[NVC_MFCDatabase#16](../../mfc/codesnippet/cpp/crecordset-class_15.cpp)]  
  
##  <a name="refreshrowset"></a>  CRecordset::RefreshRowset  
 Actualiza los datos y el estado de una fila en el conjunto de filas actual.  
  
```  
void RefreshRowset(
    WORD wRow,  
    WORD wLockType = SQL_LOCK_NO_CHANGE);
```  
  
### <a name="parameters"></a>Parámetros  
 *wRow*  
 La posición basada en uno de una fila en el conjunto de filas actual. Este valor puede oscilar entre cero y el tamaño del conjunto de filas.  
  
 *wLockType*  
 Un valor que indica cómo bloquear la fila una vez que se haya actualizado. Para conocer más detalles, vea la sección Comentarios.  
  
### <a name="remarks"></a>Comentarios  
 Si se pasa un valor de cero para *wRow*, a continuación, se actualizarán todas las filas del conjunto de filas.  
  
 Para usar `RefreshRowset`, debe haber implementado la obtención masiva de filas mediante la especificación de la `CRecordset::useMulitRowFetch` opción el [abierto](#open) función miembro.  
  
 `RefreshRowset` llama a la función de la API de ODBC `SQLSetPos`. El *wLockType* parámetro especifica el estado de bloqueo de la fila después de `SQLSetPos` se ha ejecutado. La tabla siguiente describen los valores posibles para *wLockType*.  
  
|wLockType|Descripción|  
|---------------|-----------------|  
|SQL_LOCK_NO_CHANGE (el valor predeterminado)|El controlador u origen de datos garantiza que la fila en el mismo estado bloqueado o desbloqueado que estaba antes `RefreshRowset` llamó.|  
|SQL_LOCK_EXCLUSIVE|El controlador u origen de datos bloquea exclusivamente la fila. No todos los orígenes de datos admiten este tipo de bloqueo.|  
|SQL_LOCK_UNLOCK|El controlador u origen de datos desbloquea la fila. No todos los orígenes de datos admiten este tipo de bloqueo.|  
  
 Para obtener más información sobre `SQLSetPos`, consulte el SDK de Windows. Para obtener más información sobre la obtención masiva de filas, vea el artículo [Conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
##  <a name="requery"></a>  CRecordset:: Requery  
 (Actualizaciones) se vuelve a generar un conjunto de registros.  
  
```  
virtual BOOL Requery();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el conjunto de registros se recompiló correctamente; en caso contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 Si se devuelve algún registro, el primer registro se convierte en el registro actual.  
  
 En orden para el conjunto de registros reflejar las adiciones y eliminaciones que usted u otros usuarios están realizando al origen de datos, debe volver a generar el conjunto de registros mediante una llamada a `Requery`. Si el conjunto de registros es de tipo dinámico, refleja automáticamente las actualizaciones que hacen que usted u otros usuarios a sus registros existentes (pero no las adiciones). Si el conjunto de registros es una instantánea, se debe llamar a `Requery` para reflejar modificaciones realizadas por otros usuarios, así como las adiciones y eliminaciones.  
  
 Para un tipo dinámico o una instantánea, llame a `Requery` siempre que desee volver a generar el conjunto de registros mediante un nuevo filtro, ordenación o nuevos valores de parámetro. Establezca la nueva propiedad filtrar u ordenar asignando nuevos valores a `m_strFilter` y `m_strSort` antes de llamar a `Requery`. Definir nuevos parámetros asignando nuevos valores a los miembros de datos de parámetro antes de llamar a `Requery`. Si han cambiado las cadenas de filtro y ordenación, puede volver a usar la consulta, lo que mejora el rendimiento.  
  
 Si se produce un error en el intento de volver a generar el conjunto de registros, se cierra el conjunto de registros. Antes de llamar a `Requery`, puede determinar si se puede consultar el conjunto de registros mediante una llamada a la `CanRestart` función miembro. `CanRestart` no garantiza que `Requery` se realizará correctamente.  
  
> [!CAUTION]
>  Llame a `Requery` solo después de haber llamado [abierto](#open).  
  
### <a name="example"></a>Ejemplo  
 En este ejemplo se vuelve a generar un conjunto de registros para aplicar un criterio de ordenación diferente.  
  
 [!code-cpp[NVC_MFCDatabase#29](../../mfc/codesnippet/cpp/crecordset-class_16.cpp)]  
  
##  <a name="setabsoluteposition"></a>  CRecordset:: SetAbsolutePosition  
 Coloca el conjunto de registros en el registro correspondiente al número de registro especificado.  
  
```  
void SetAbsolutePosition(long nRows);
```  
  
### <a name="parameters"></a>Parámetros  
 *nRows*  
 Basado en una posición ordinal para el registro actual en el conjunto de registros.  
  
### <a name="remarks"></a>Comentarios  
 `SetAbsolutePosition` Mueve el puntero de registro actual en función de esta posición ordinal.  
  
> [!NOTE]
>  Esta función miembro no es válida en los conjuntos de registros solo hacia delante.  
  
 Conjuntos de registros ODBC, una configuración de la posición absoluta de 1 hace referencia al primer registro en el conjunto de registros; un valor de 0 hace referencia a la posición de inicio del archivo (BOF).  
  
 También puede pasar los valores negativos `SetAbsolutePosition`. En este caso se evalúa la posición del conjunto de registros desde el final del conjunto de registros. Por ejemplo, `SetAbsolutePosition( -1 )` mueve el puntero de registro actual al último registro del conjunto de registros.  
  
> [!NOTE]
>  Posición absoluta no está pensado para usarse como un número de registro suplente. Marcadores siguen siendo la forma recomendada de retener y volver a una posición determinada, desde cambios en la posición de un registro cuando se eliminan los registros anteriores. Además, no puede ser seguro de que un registro determinado tendrá la misma posición absoluta si se vuelve a crear el conjunto de registros, porque no se garantiza el orden de los registros individuales dentro de un conjunto de registros, a menos que se crea con una instrucción SQL mediante un **ORDER BY** cláusula.  
  
 Para obtener más información acerca de la exploración del conjunto de registros y los marcadores, consulte los artículos [conjunto de registros: desplazamiento (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) y [conjunto de registros: marcadores y posiciones absolutas (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md).  
  
##  <a name="setbookmark"></a>  CRecordset::SetBookmark  
 Coloca el conjunto de registros en el registro que contiene el marcador especificado.  
  
```  
void SetBookmark(const CDBVariant& varBookmark);
```  
  
### <a name="parameters"></a>Parámetros  
 *varBookmark*  
 Una referencia a un [CDBVariant](../../mfc/reference/cdbvariant-class.md) objeto que contiene el valor de marcador de un registro específico.  
  
### <a name="remarks"></a>Comentarios  
 Para determinar si se admiten marcadores en el conjunto de registros, llame a [CanBookmark](#canbookmark). Para que los marcadores estén disponibles si son compatibles, debe establecer el `CRecordset::useBookmarks` opción el *dwOptions* parámetro de la [abierto](#open) función miembro.  
  
> [!NOTE]
>  Si los marcadores son no compatibles o no está disponible, la llamada a `SetBookmark` dará como resultado una excepción. No se admiten marcadores en conjuntos de registros solo hacia delante.  
  
 Para recuperar primero el marcador para el registro actual, llame al [GetBookmark](#getbookmark), que guarda el valor de marcador a un `CDBVariant` objeto. Más adelante, puede volver a ese registro mediante una llamada a `SetBookmark` utilizando el valor de marcador guardado.  
  
> [!NOTE]
>  Después de ciertas operaciones de conjunto de registros, debe comprobar la persistencia de marcador antes de llamar a `SetBookmark`. Por ejemplo, si recupera un marcador con `GetBookmark` y, a continuación, llame a `Requery`, el marcador es posible que ya no sean válido. Llame a [CDatabase:: GetBookmarkPersistence](../../mfc/reference/cdatabase-class.md#getbookmarkpersistence) para comprobar si puede llamar con seguridad a `SetBookmark`.  
  
 Para obtener más información acerca de los marcadores y exploración del conjunto de registros, consulte los artículos [conjunto de registros: marcadores y posiciones absolutas (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md) y [conjunto de registros: desplazamiento (ODBC)](../../data/odbc/recordset-scrolling-odbc.md).  
  
##  <a name="setfielddirty"></a>  CRecordset::SetFieldDirty  
 Marca a un miembro de datos de campo del conjunto de registros según es modificado o como sin cambios.  
  
```  
void SetFieldDirty(void* pv, BOOL bDirty = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 *PV*  
 Contiene la dirección de un miembro de datos de campo en el conjunto de registros o NULL. Si es NULL, se marcan todos los miembros de datos de campo del conjunto de registros. (C++ NULL no es igual a Null en la terminología de base de datos, lo que significa "no tener ningún valor.")  
  
 *bDirty*  
 TRUE si es miembro de datos del campo se marca como "sucio" (modificado). En caso contrario, es FALSE si el miembro de datos de campo se marca como "limpiar" (sin cambios).  
  
### <a name="remarks"></a>Comentarios  
 Marcar campos como sin cambios garantiza que el campo no se actualiza y da como resultado menos tráfico SQL.  
  
> [!NOTE]
>  Esta función miembro no es aplicable en conjuntos de registros que se están usando la obtención masiva de filas. Si ha implementado obtención masiva de filas, a continuación, `SetFieldDirty` dará como resultado un error de aserción. Para obtener más información sobre la obtención masiva de filas, vea el artículo [Conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Las marcas de marco de trabajo puede cambiar los miembros de datos de campo para asegurarse de que se escribirá en el registro del origen de datos mediante el mecanismo de campos de registros (RFX) de exchange. Cambiar el valor de un campo normalmente establece el campo desfasadas automáticamente, por lo que rara vez necesitará llamar a `SetFieldDirty` usted mismo, pero a veces, conviene asegurarse de que las columnas se explícitamente actualizadas o insertadas independientemente del valor que se encuentra en los datos del campo miembro.  
  
> [!CAUTION]
>  Llame a esta función miembro después de haber llamado [editar](#edit) o [AddNew](#addnew).  
  
 El uso de NULL para el primer argumento de la función aplicará solo a la función `outputColumn` campos, no `param` campos. Por ejemplo, la llamada  
  
 [!code-cpp[NVC_MFCDatabase#26](../../mfc/codesnippet/cpp/crecordset-class_10.cpp)]  
  
 establecerá sólo `outputColumn` campos con NULL; `param` campos no se verán afectados.  
  
 Para trabajar en `param` campos, debe proporcionar la dirección real de la persona `param` que desea trabajar, tales como:  
  
 [!code-cpp[NVC_MFCDatabase#27](../../mfc/codesnippet/cpp/crecordset-class_11.cpp)]  
  
 Esto significa que no se puede establecer en todos los `param` campos con valores NULL, se puede hacer con `outputColumn` campos.  
  
##  <a name="setfieldnull"></a>  CRecordset::SetFieldNull  
 Marca a un miembro de datos de campo del conjunto de registros como Null (específicamente con ningún valor) o como no Null.  
  
```  
void SetFieldNull(void* pv, BOOL bNull = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 *PV*  
 Contiene la dirección de un miembro de datos de campo en el conjunto de registros o NULL. Si es NULL, se marcan todos los miembros de datos de campo del conjunto de registros. (C++ NULL no es igual a Null en la terminología de base de datos, lo que significa "no tener ningún valor.")  
  
 *bNull*  
 Distinto de cero si es miembro de datos del campo se marca como si tuviera ningún valor (Null). En caso contrario, 0 si el miembro de datos de campo se marca como no Null.  
  
### <a name="remarks"></a>Comentarios  
 Cuando se agrega un nuevo registro a un conjunto de registros, todos los miembros de datos de campo inicialmente son establecidos en un valor Null y marcados como "sucio" (modificado). Al recuperar un registro de un origen de datos, sus columnas ya tienen valores o son Null.  
  
> [!NOTE]
>  No llame a esta función miembro en conjuntos de registros que se están usando la obtención masiva de filas. Si ha implementado la obtención masiva de filas, una llamada a `SetFieldNull` da como resultado un error de aserción. Para obtener más información sobre la obtención masiva de filas, vea el artículo [Conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Si lo desea específicamente designar un campo del registro actual que no tiene un valor, llame a `SetFieldNull` con *bNull* establecido en TRUE para marcarlo como Null. Si previamente se marcó un campo Null y ahora desea asignarle un valor, simplemente establezca su nuevo valor. No es necesario que quitar la marca de Null con `SetFieldNull`. Para determinar si el campo puede ser Null, llame a `IsFieldNullable`.  
  
> [!CAUTION]
>  Llame a esta función miembro después de haber llamado [editar](#edit) o [AddNew](#addnew).  
  
 El uso de NULL para el primer argumento de la función aplicará solo a la función `outputColumn` campos, no `param` campos. Por ejemplo, la llamada  
  
 [!code-cpp[NVC_MFCDatabase#26](../../mfc/codesnippet/cpp/crecordset-class_10.cpp)]  
  
 establecerá sólo `outputColumn` campos con NULL; `param` campos no se verán afectados.  
  
 Para trabajar en `param` campos, debe proporcionar la dirección real de la persona `param` que desea trabajar, tales como:  
  
 [!code-cpp[NVC_MFCDatabase#27](../../mfc/codesnippet/cpp/crecordset-class_11.cpp)]  
  
 Esto significa que no se puede establecer en todos los `param` campos con valores NULL, se puede hacer con `outputColumn` campos.  
  
> [!NOTE]
>  Al establecer los parámetros con valores Null, una llamada a `SetFieldNull` antes de que el conjunto de registros está abiertos resultados en una aserción. En este caso, llame a [SetParamNull](#setparamnull).  
  
 `SetFieldNull` se implementa a través de [DoFieldExchange](#dofieldexchange).  
  
##  <a name="setlockingmode"></a>  CRecordset::SetLockingMode  
 Establece el modo de bloqueo "optimista" bloquear (predeterminado) o de bloqueo "pesimista". Determina cómo se bloquean los registros para las actualizaciones.  
  
```  
void SetLockingMode(UINT nMode);
```  
  
### <a name="parameters"></a>Parámetros  
 *nMode*  
 Contiene uno de los siguientes valores de la `enum LockMode`:  
  
- `optimistic` Bloqueo optimista bloquea el registro que se actualizan únicamente durante la llamada a `Update`.  
  
- `pessimistic` El bloqueo pesimista bloquea el registro tan pronto como `Edit` se denomina y lo mantiene bloqueado hasta que el `Update` llamada se complete o se mueve a un nuevo registro.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función miembro si tiene que especificar cuál de las dos estrategias de bloqueo de registros es usar el conjunto de registros para las actualizaciones. De forma predeterminada, el modo de bloqueo de un conjunto de registros es `optimistic`. Se puede cambiar a una más cauteloso `pessimistic` estrategia de bloqueo. Llame a `SetLockingMode` después de crear y abrir el objeto de conjunto de registros pero antes de llamar a `Edit`.  
  
##  <a name="setparamnull"></a>  CRecordset::SetParamNull  
 Marca un parámetro como Null (específicamente con ningún valor) o como no Null.  
  
```  
void SetParamNull(
    int nIndex,  
    BOOL bNull = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 *nIndex*  
 Índice de base cero del parámetro.  
  
 *bNull*  
 Si TRUE (el valor predeterminado), el parámetro se marca como Null. En caso contrario, el parámetro se marca como no Null.  
  
### <a name="remarks"></a>Comentarios  
 A diferencia de [SetFieldNull](#setfieldnull), puede llamar a `SetParamNull` antes de que ha abierto el conjunto de registros.  
  
 `SetParamNull` se utiliza normalmente con consultas predefinidas (procedimientos almacenados).  
  
##  <a name="setrowsetcursorposition"></a>  CRecordset::SetRowsetCursorPosition  
 Mueve el cursor a una fila en el conjunto de filas actual.  
  
```  
void SetRowsetCursorPosition(WORD wRow, WORD wLockType = SQL_LOCK_NO_CHANGE);
```  
  
### <a name="parameters"></a>Parámetros  
 *wRow*  
 La posición basada en uno de una fila en el conjunto de filas actual. Este valor puede oscilar entre 1 para el tamaño del conjunto de filas.  
  
 *wLockType*  
 Valor que indica cómo bloquear la fila una vez que se haya actualizado. Para conocer más detalles, vea la sección Comentarios.  
  
### <a name="remarks"></a>Comentarios  
 Al implementar la obtención masiva de filas, se recuperan los registros por conjuntos de filas, donde el primer registro en el conjunto de filas capturada es el registro actual. Para poder crear otro registro del conjunto de filas en el registro actual, llame a `SetRowsetCursorPosition`. Por ejemplo, puede combinar `SetRowsetCursorPosition` con el [GetFieldValue](#getfieldvalue) función miembro para recuperar dinámicamente los datos de todos los registros del conjunto de registros.  
  
 Para usar `SetRowsetCursorPosition`, debe haber implementado la obtención masiva de filas mediante la especificación de la `CRecordset::useMultiRowFetch` opción de la *dwOptions* parámetro en el [abierto](#open) función miembro.  
  
 `SetRowsetCursorPosition` llama a la función de la API de ODBC `SQLSetPos`. El *wLockType* parámetro especifica el estado de bloqueo de la fila después de `SQLSetPos` se ha ejecutado. La tabla siguiente describen los valores posibles para *wLockType*.  
  
|wLockType|Descripción|  
|---------------|-----------------|  
|SQL_LOCK_NO_CHANGE (el valor predeterminado)|El controlador u origen de datos garantiza que la fila en el mismo estado bloqueado o desbloqueado que estaba antes `SetRowsetCursorPosition` llamó.|  
|SQL_LOCK_EXCLUSIVE|El controlador u origen de datos bloquea exclusivamente la fila. No todos los orígenes de datos admiten este tipo de bloqueo.|  
|SQL_LOCK_UNLOCK|El controlador u origen de datos desbloquea la fila. No todos los orígenes de datos admiten este tipo de bloqueo.|  
  
 Para obtener más información sobre `SQLSetPos`, consulte el SDK de Windows. Para obtener más información sobre la obtención masiva de filas, vea el artículo [Conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
##  <a name="setrowsetsize"></a>  CRecordset::SetRowsetSize  
 Especifica el número de registros que desea recuperar durante una búsqueda.  
  
```  
virtual void SetRowsetSize(DWORD dwNewRowsetSize);
```  
  
### <a name="parameters"></a>Parámetros  
 *dwNewRowsetSize*  
 El número de filas que se va a recuperar durante una búsqueda determinada.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro virtual especifica cuántas filas desea recuperar durante una búsqueda sencilla al usar la obtención masiva de filas. Para implementar la obtención masiva de filas, debe establecer el `CRecordset::useMultiRowFetch` opción el *dwOptions* parámetro de la [abierto](#open) función miembro.  
  
> [!NOTE]
>  Una llamada a `SetRowsetSize` sin implementar de forma masiva de filas dará como resultado un error de aserción.  
  
 Llame a `SetRowsetSize` antes de llamar a `Open` establecer inicialmente el tamaño del conjunto de filas del conjunto de registros. El tamaño del conjunto de filas de forma predeterminada al implementar la obtención masiva de filas es 25.  
  
> [!NOTE]
>  Tenga cuidado al llamar a `SetRowsetSize`. Si se asigna almacenamiento para los datos manualmente (tal y como especifica la `CRecordset::userAllocMultiRowBuffers` opción del parámetro dwOptions en `Open`), debe comprobar si tiene que reasignar estos búferes de almacenamiento después de llamar a `SetRowsetSize`, pero antes de realice cualquier operación de desplazamiento de cursor.  
  
 Para obtener la configuración actual para el tamaño del conjunto de filas, llame a [GetRowsetSize](#getrowsetsize).  
  
 Para obtener más información sobre la obtención masiva de filas, vea el artículo [Conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
##  <a name="update"></a>  CRecordset:: Update  
 Se completa una `AddNew` o `Edit` operación guardando los datos nuevos o modificados del origen de datos.  
  
```  
virtual BOOL Update();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si un registro se actualizó correctamente; en caso contrario, 0 si no hay columnas han cambiado. Si se actualizó ningún registro, o si hay más de un registro se actualizó, se produce una excepción. También se produce una excepción para cualquier otro error en el origen de datos.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función miembro después de llamar a la [AddNew](#addnew) o [editar](#edit) función miembro. Esta llamada es necesario para completar la `AddNew` o `Edit` operación.  
  
> [!NOTE]
>  Si ha implementado la obtención masiva de filas, no puede llamar a `Update`. Esto provocará un error de aserción. Aunque clase `CRecordset` no proporciona un mecanismo de actualización masiva de filas de datos, puede escribir sus propias funciones mediante la función de la API de ODBC `SQLSetPos`. Para obtener más información sobre la obtención masiva de filas, vea el artículo [Conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Ambos `AddNew` y `Edit` preparar un búfer de edición en el que se colocan los datos se ha agregado o editados para guardar datos en el origen de datos. `Update` guarda los datos. Se actualizan solo los campos marcados o detecta tal como se puede cambiar.  
  
 Si el origen de datos admite transacciones, se puede hacer el `Update` llamar (y su correspondiente `AddNew` o `Edit` llamar) forma parte de una transacción. Para obtener más información acerca de las transacciones, vea el artículo [transacción (ODBC)](../../data/odbc/transaction-odbc.md).  
  
> [!CAUTION]
>  Si se llama a `Update` sin primero una llamada a `AddNew` o `Edit`, `Update` produce una `CDBException`. Si se llama a `AddNew` o `Edit`, debe llamar a `Update` antes de llamar a un `Move` operación o antes de cerrar el conjunto de registros o la conexión de origen de datos. En caso contrario, los cambios se perderán sin notificación.  
  
 Para obtener más información sobre cómo controla `Update` errores, consulte el artículo [conjunto de registros: actualizar los registros (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md).  
  
### <a name="example"></a>Ejemplo  
 Consulte el artículo [transacción: realizar una transacción en un conjunto de registros (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md).  
  
## <a name="see-also"></a>Vea también  
 [CObject (clase)](../../mfc/reference/cobject-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CDatabase (clase)](../../mfc/reference/cdatabase-class.md)   
 [CRecordView (clase)](../../mfc/reference/crecordview-class.md)
