---
title: Clase CRecordset | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
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
- database records [C++]
- CRecordset class
- ODBC recordsets [C++], CRecordset objects
- sets of records [C++]
ms.assetid: dd89a21d-ef39-4aab-891b-1e373d67c855
caps.latest.revision: 23
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a82768750e6a7837bb81edd8a51847f83c294c20
ms.openlocfilehash: 9271608528699e93fa7b8315f8ef2fdd5ae1e54d
ms.lasthandoff: 04/04/2017

---
# <a name="crecordset-class"></a>CRecordset (clase)
Representa un conjunto de registros seleccionados de un origen de datos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CRecordset : public CObject  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CRecordset::CRecordset](#crecordset)|Construye un objeto `CRecordset`. La clase derivada debe proporcionar un constructor que llama a este.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CRecordset::AddNew](#addnew)|Se prepara para agregar un nuevo registro. Llame a `Update` para completar la adición.|  
|[CRecordset::CanAppend](#canappend)|Devuelve un valor distinto de cero si se pueden agregar nuevos registros en el conjunto de registros a través de la `AddNew` función miembro.|  
|[CRecordset:: CanBookmark](#canbookmark)|Devuelve un valor distinto de cero si el conjunto de registros admite marcadores.|  
|[CRecordset::Cancel](#cancel)|Cancela una operación asincrónica o en un proceso de un segundo subproceso.|  
|[CRecordset::CancelUpdate](#cancelupdate)|Cancela cualquier actualización pendiente debido a un `AddNew` o `Edit` operación.|  
|[CRecordset::CanRestart](#canrestart)|Devuelve un valor distinto de cero si `Requery` puede llamarse para volver a ejecutar la consulta del conjunto de registros.|  
|[CRecordset::CanScroll](#canscroll)|Devuelve un valor distinto de cero si puede desplazarse por los registros.|  
|[CRecordset::CanTransact](#cantransact)|Devuelve un valor distinto de cero si el origen de datos admite transacciones.|  
|[CRecordset::CanUpdate](#canupdate)|Devuelve un valor distinto de cero si se puede actualizar el conjunto de registros (puede agregar, actualizar o eliminar registros).|  
|[CRecordset::CheckRowsetError](#checkrowseterror)|Se llama para controlar los errores generados durante la captura de registro.|  
|[CRecordset:: Close](#close)|Cierra el conjunto de registros y ODBC **HSTMT** asociados a él.|  
|[CRecordset::Delete](#delete)|Elimina el registro actual del conjunto de registros. Explícitamente, debe desplazarse a otro registro después de la eliminación.|  
|[CRecordset::DoBulkFieldExchange](#dobulkfieldexchange)|Se llama para intercambiar masiva de filas de datos del origen de datos para el conjunto de registros. Implementa de forma masiva el intercambio de campos de registros (RFX masivo).|  
|[CRecordset:: DoFieldExchange](#dofieldexchange)|Se llama para intercambiar datos (en ambas direcciones) entre los miembros de datos de campo del conjunto de registros y el registro correspondiente en el origen de datos. Implementa registro (RFX) de intercambio de campos.|  
|[CRecordset::Edit](#edit)|Se prepara para que los cambios en el registro actual. Llame a `Update` para completar la edición.|  
|[CRecordset::FlushResultSet](#flushresultset)|Devuelve es distinto de cero si no hay resultados de otro conjunto va a recuperar, cuando se usa una consulta predefinida.|  
|[CRecordset::GetBookmark](#getbookmark)|Asigna el valor de marcador de un registro para el objeto de parámetro.|  
|[CRecordset:: GetDefaultConnect](#getdefaultconnect)|Se llama para obtener la cadena de conexión predeterminada.|  
|[CRecordset::GetDefaultSQL](#getdefaultsql)|Se llama para obtener la cadena SQL predeterminada para ejecutar.|  
|[CRecordset:: GetFieldValue](#getfieldvalue)|Devuelve el valor de un campo en un conjunto de registros.|  
|[CRecordset::GetODBCFieldCount](#getodbcfieldcount)|Devuelve el número de campos del conjunto de registros.|  
|[CRecordset::GetODBCFieldInfo](#getodbcfieldinfo)|Devuelve determinados tipos de información sobre los campos de un conjunto de registros.|  
|[CRecordset::GetRecordCount](#getrecordcount)|Devuelve el número de registros en el conjunto de registros.|  
|[CRecordset::GetRowsetSize](#getrowsetsize)|Devuelve el número de registros que se va a recuperar durante una sola operación de obtención.|  
|[CRecordset::GetRowsFetched](#getrowsfetched)|Devuelve el número real de filas recuperado durante una búsqueda.|  
|[CRecordset::GetRowStatus](#getrowstatus)|Devuelve el estado de la fila después de una captura.|  
|[CRecordset::GetSQL](#getsql)|Obtiene la cadena SQL que se utiliza para seleccionar los registros para el conjunto de registros.|  
|[CRecordset::GetStatus](#getstatus)|Obtiene el estado del conjunto de registros: el índice del registro actual y si se ha obtenido un recuento final de los registros.|  
|[CRecordset::GetTableName](#gettablename)|Obtiene el nombre de la tabla en la que se basa el conjunto de registros.|  
|[CRecordset::IsBOF](#isbof)|Devuelve un valor distinto de cero si el conjunto de registros se ha colocado antes del primer registro. No hay ningún registro actual.|  
|[CRecordset::IsDeleted](#isdeleted)|Devuelve un valor distinto de cero si el conjunto de registros está situado en un registro eliminado.|  
|[CRecordset::IsEOF](#iseof)|Devuelve un valor distinto de cero si el conjunto de registros se ha colocado después del último registro. No hay ningún registro actual.|  
|[CRecordset::IsFieldDirty](#isfielddirty)|Devuelve un valor distinto de cero si se ha cambiado el campo especificado en el registro actual.|  
|[CRecordset::IsFieldNull](#isfieldnull)|Devuelve un valor distinto de cero si el campo especificado en el registro actual es nulo (no tiene ningún valor).|  
|[CRecordset::IsFieldNullable](#isfieldnullable)|Devuelve un valor distinto de cero si el campo especificado en el registro actual se puede establecer en null (no tener ningún valor).|  
|[CRecordset::IsOpen](#isopen)|Devuelve un valor distinto de cero si `Open` se ha llamado anteriormente.|  
|[CRecordset:: Move](#move)|Coloca el conjunto de registros a un número especificado de entradas del registro actual en cualquier dirección.|  
|[CRecordset::MoveFirst](#movefirst)|El registro actual se coloca en el primer registro del conjunto de registros. Comprobar `IsBOF` primero.|  
|[CRecordset::MoveLast](#movelast)|Coloca el registro actual en el último registro o en el último conjunto de filas. Comprobar `IsEOF` primero.|  
|[CRecordset::MoveNext](#movenext)|El registro actual se coloca en el siguiente registro o en el siguiente conjunto de filas. Comprobar `IsEOF` primero.|  
|[CRecordset::MovePrev](#moveprev)|El registro actual se coloca en el registro anterior o en el conjunto de filas anterior. Comprobar `IsBOF` primero.|  
|[CRecordset::OnSetOptions](#onsetoptions)|Se llama para establecer las opciones de (utilizados en la selección) para la instrucción ODBC especificada.|  
|[CRecordset::OnSetUpdateOptions](#onsetupdateoptions)|Se llama para establecer opciones de (que se usa en la actualización) de la instrucción ODBC especificada.|  
|[CRecordset:: Open](#open)|Abre el conjunto de registros recuperando la tabla o realizando la consulta que el conjunto de registros representa.|  
|[CRecordset::RefreshRowset](#refreshrowset)|Actualiza los datos y el estado de las filas especificadas.|  
|[CRecordset:: Requery](#requery)|Ejecuta la consulta del conjunto de registros para actualizar los registros seleccionados.|  
|[CRecordset:: SetAbsolutePosition](#setabsoluteposition)|El conjunto de registros se coloca en el registro correspondiente al número de registro especificado.|  
|[CRecordset::SetBookmark](#setbookmark)|El conjunto de registros se coloca en el registro especificado por el marcador.|  
|[CRecordset::SetFieldDirty](#setfielddirty)|Marca el campo especificado en el registro actual como modificada.|  
|[CRecordset::SetFieldNull](#setfieldnull)|Establece el valor del campo especificado en el registro actual en null (no tener ningún valor).|  
|[CRecordset::SetLockingMode](#setlockingmode)|Establece el modo de bloqueo "optimista" bloquear (predeterminado) o de bloqueo "pesimista". Determina cómo se bloquean los registros para las actualizaciones.|  
|[CRecordset::SetParamNull](#setparamnull)|El parámetro especificado se establece en null (no tener ningún valor).|  
|[CRecordset::SetRowsetCursorPosition](#setrowsetcursorposition)|Coloca el cursor en la fila especificada en el conjunto de filas.|  
|[CRecordset::SetRowsetSize](#setrowsetsize)|Especifica el número de registros que se va a recuperar durante una búsqueda.|  
|[CRecordset:: Update](#update)|Completa una `AddNew` o `Edit` operación guardando los datos nuevos o modificados del origen de datos.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CRecordset:: M_hstmt](#m_hstmt)|Contiene el identificador de instrucción ODBC para el conjunto de registros. Escriba `HSTMT`.|  
|[CRecordset::m_nFields](#m_nfields)|Contiene el número de miembros de datos de campo del conjunto de registros. Escriba `UINT`.|  
|[CRecordset::m_nParams](#m_nparams)|Contiene el número de miembros de datos de parámetro en el conjunto de registros. Escriba `UINT`.|  
|[CRecordset::m_pDatabase](#m_pdatabase)|Contiene un puntero a la `CDatabase` objeto a través del cual el conjunto de registros está conectado a un origen de datos.|  
|[CRecordset:: M_strfilter](#m_strfilter)|Contiene un `CString` que especifica un lenguaje de consulta estructurado (SQL) `WHERE` cláusula. Se usa como filtro para seleccionar solo los registros que cumplen determinados criterios.|  
|[CRecordset::m_strSort](#m_strsort)|Contiene un `CString` que especifica una instancia de SQL `ORDER BY` cláusula. Se utiliza para controlar cómo se ordenan los registros.|  
  
## <a name="remarks"></a>Comentarios  
 Conocida como "conjuntos de registros," `CRecordset` objetos utilizan normalmente de dos formas: conjuntos de registros dinámicos y las instantáneas. Un conjunto de registros dinámicos permanece sincronizado con las actualizaciones de datos realizadas por otros usuarios. Una instantánea es una vista estática de los datos. Cada formulario representa un conjunto de registros que se fija en el momento en que se abre el conjunto de registros, pero cuando se desplaza a un registro en un conjunto de registros dinámicos, refleja los cambios realizados posteriormente en el registro, por otros usuarios o por otros conjuntos de registros en la aplicación.  
  
> [!NOTE]
>  Si está trabajando con las clases de Data Access Objects (DAO) en lugar de las clases de Open Database Connectivity (ODBC), utilice la clase [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) en su lugar. Para obtener más información, vea el artículo [información general: programación de base de datos](../../data/data-access-programming-mfc-atl.md).  
  
 Para trabajar con cualquier tipo de conjunto de registros, normalmente se deriva una clase de conjunto de registros específicos de la aplicación de `CRecordset`. Conjuntos de registros seleccionan registros de un origen de datos y, a continuación, puede:  
  
-   Desplazarse por los registros.  
  
-   Actualizar los registros y especificar un modo de bloqueo.  
  
-   Filtrar el conjunto de registros para restringir qué registros selecciona de los que están disponibles en el origen de datos.  
  
-   Ordenar el conjunto de registros.  
  
-   Parametrice el conjunto de registros para personalizar su selección con información no conocida hasta el tiempo de ejecución.  
  
 Para utilizar la clase, abra una base de datos y crear un objeto de conjunto de registros, el constructor se pasa un puntero a su `CDatabase` objeto. A continuación, llame el conjunto de registros **abiertos** función miembro, donde puede especificar si el objeto es un conjunto de registros dinámicos o una instantánea. Al llamar a **abiertos** selecciona datos desde el origen de datos. Después de que el objeto de conjunto de registros está abierto, utilice a sus miembros de datos y funciones de miembro para desplazarse por los registros y operar con ellas. Las operaciones disponibles dependen de si el objeto es un conjunto de registros dinámicos o una instantánea, ya sea actualizable o de solo lectura (Esto depende de la capacidad del origen de datos Open Database Connectivity (ODBC)), y si ha implementado la obtención masiva de filas. Para actualizar los registros que se han cambiado o agregado desde el **abiertos** llamada, llamar al objeto **Requery** función miembro. Llamar al objeto **cerrar** miembro de función y destruir el objeto cuando haya terminado con él.  
  
 En un derivada `CRecordset` clase, registre el intercambio de campos (RFX) o el intercambio masivo de campos de registros (RFX masivo) se utiliza para permitir la lectura y actualización de los campos de registro.  
  
 Para obtener más información acerca de intercambio de campos de registro y conjuntos de registros, vea los artículos [información general: programación de base de datos](../../data/data-access-programming-mfc-atl.md), [conjunto de registros (ODBC)](../../data/odbc/recordset-odbc.md), [conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md), y [intercambio de campos de registros (RFX)](../../data/odbc/record-field-exchange-rfx.md). Para un enfoque en conjuntos de registros dinámicos y las instantáneas, vea los artículos [Dynaset](../../data/odbc/dynaset.md) y [instantánea](../../data/odbc/snapshot.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CRecordset`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdb.h  
  
##  <a name="addnew"></a>CRecordset::AddNew  
 Se prepara para agregar un nuevo registro a la tabla.  
  
```  
virtual void AddNew();
```  
  
### <a name="remarks"></a>Comentarios  
 Debe llamar a la [Requery](#requery) función miembro para ver el registro recién agregado. Los campos del registro son inicialmente Null. (En la terminología de base de datos, Null significa "no having ningún valor" y no es igual a **NULL** en C++.) Para completar la operación, se debe llamar a la [actualización](#update) función miembro. **Actualización** guarda los cambios en el origen de datos.  
  
> [!NOTE]
>  Si ha implementado la obtención masiva de filas, no se puede llamar `AddNew`. Esto producirá un error de aserción. Aunque clase `CRecordset` no proporciona un mecanismo para actualizar filas masivas de datos, puede escribir sus propias funciones mediante la función API de ODBC **SQLSetPos**. Para obtener más información sobre la obtención masiva de filas, vea el artículo [conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 `AddNew`prepara un registro nuevo y vacío con miembros de datos de campo del conjunto de registros. Después de llamar a `AddNew`, establezca los valores que desee en miembros de datos de campo del conjunto de registros. (No es necesario llamar a la [editar](#edit) función de miembro para este fin; utilice **editar** solo para los registros existentes.) Cuando vuelve a llamar a **actualización**, cambiado los valores de los miembros de datos de campo se guardan en el origen de datos.  
  
> [!CAUTION]
>  Si se desplaza a un nuevo registro antes de llamar a **actualización**, el nuevo registro se pierde y se emite ninguna advertencia.  
  
 Si el origen de datos admite transacciones, puede realizar su `AddNew` llame a parte de una transacción. Para obtener más información acerca de las transacciones, vea la clase [CDatabase](../../mfc/reference/cdatabase-class.md). Tenga en cuenta que debe llamar a [CDatabase::BeginTrans](../../mfc/reference/cdatabase-class.md#begintrans) antes de llamar a `AddNew`.  
  
> [!NOTE]
>  Para conjuntos de registros dinámicos, los nuevos registros se agregan al conjunto de registros como el último registro. Los registros agregados no se agregan a instantáneas; debe llamar a **Requery** para actualizar el conjunto de registros.  
  
 No es válido para llamar a `AddNew` para un conjunto de registros cuyo **abiertos** función miembro no se ha llamado. A `CDBException` se produce si se llama a `AddNew` para un conjunto de registros que no se pueden anexar a. Puede determinar si el conjunto de registros es actualizable mediante una llamada a [CanAppend](#canappend).  
  
 Para obtener más información, vea los siguientes artículos: [conjunto de registros: actualizar los registros (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md), [conjunto de registros: agregar, actualizar y eliminar registros (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md), y [transacción (ODBC)](../../data/odbc/transaction-odbc.md).  
  
### <a name="example"></a>Ejemplo  
 Vea el artículo [transacción: realizar una transacción en un conjunto de registros (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md).  
  
##  <a name="canappend"></a>CRecordset::CanAppend  
 Determina si el conjunto de registros abierto anteriormente le permite agregar nuevos registros.  
  
```  
BOOL CanAppend() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el conjunto de registros permite agregar nuevos registros; en caso contrario es 0. `CanAppend`devolverá 0 si se abre el conjunto de registros como de solo lectura.  
  
##  <a name="canbookmark"></a>CRecordset:: CanBookmark  
 Determina si el conjunto de registros permite marcar los registros mediante marcadores.  
  
```  
BOOL CanBookmark() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el conjunto de registros admite marcadores; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 Esta función es independiente de la **CRecordset:: useBookmarks** opción en el `dwOptions` parámetro de la [abiertos](#open) función miembro. `CanBookmark`indica si el controlador ODBC determinado y el cursor de tipo de compatibilidad con marcadores. **CRecordset:: useBookmarks** indica si los marcadores dejará de estar disponibles, siempre se admiten.  
  
> [!NOTE]
>  No se admiten marcadores en conjuntos de registros solo hacia delante.  
  
 Para obtener más información acerca de los marcadores y la navegación de conjunto de registros, vea los artículos [conjunto de registros: marcadores y posiciones absolutas (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md) y [conjunto de registros: desplazamiento (ODBC)](../../data/odbc/recordset-scrolling-odbc.md).  
  
##  <a name="cancel"></a>CRecordset::Cancel  
 Solicitudes que el origen de datos cancela una operación asincrónica en curso o un proceso de un segundo subproceso.  
  
```  
void Cancel();
```  
  
### <a name="remarks"></a>Comentarios  
 Tenga en cuenta que las clases ODBC de MFC ya no usan el procesamiento asincrónico; para llevar a cabo una operación asincrónica, se debe llamar directamente a la función API de ODBC **SQLSetConnectOption**. Para obtener más información, vea el tema "Ejecutar funciones de forma asincrónica" en la *Guía del programador del SDK de ODBC*.  
  
##  <a name="cancelupdate"></a>CRecordset::CancelUpdate  
 Cancela todas las actualizaciones pendientes, causadas por una [editar](#edit) o [AddNew](#addnew) operación, antes de [actualización](#update) se llama.  
  
```  
void CancelUpdate();
```  
  
### <a name="remarks"></a>Comentarios  
  
> [!NOTE]
>  Esta función miembro no es aplicable en conjuntos de registros que están usando la obtención masiva de filas, ya que no se pueden llamar estos conjuntos de registros **editar**, `AddNew`, o **actualización**. Para obtener más información sobre la obtención masiva de filas, vea el artículo [conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Si está habilitada la comprobación automática de campos modificados, `CancelUpdate` restaurará las variables de miembro para los valores que tenían antes de **editar** o `AddNew` llamado; en caso contrario, se mantendrá los cambios de valor. De forma predeterminada, la comprobación automática de campos está habilitada cuando se abre el conjunto de registros. Para deshabilitarla, debe especificar el **CRecordset:: noDirtyFieldCheck** en el `dwOptions` parámetro de la [abiertos](#open) función miembro.  
  
 Para obtener más información acerca de cómo actualizar datos, vea el artículo [conjunto de registros: agregar, actualizar y eliminar registros (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md).  
  
##  <a name="canrestart"></a>CRecordset::CanRestart  
 Determina si el conjunto de registros permite reiniciar su consulta (para actualizar sus registros) mediante una llamada a la **Requery** función miembro.  
  
```  
BOOL CanRestart() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si se permite requery; en caso contrario es 0.  
  
##  <a name="canscroll"></a>CRecordset::CanScroll  
 Determina si el conjunto de registros permite el desplazamiento.  
  
```  
BOOL CanScroll() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el conjunto de registros permite el desplazamiento; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información sobre el desplazamiento, vea el artículo [conjunto de registros: desplazamiento (ODBC)](../../data/odbc/recordset-scrolling-odbc.md).  
  
##  <a name="cantransact"></a>CRecordset::CanTransact  
 Determina si el conjunto de registros permite que las transacciones.  
  
```  
BOOL CanTransact() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el conjunto de registros permite que las transacciones; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, vea el artículo [transacción (ODBC)](../../data/odbc/transaction-odbc.md).  
  
##  <a name="canupdate"></a>CRecordset::CanUpdate  
 Determina si se puede actualizar el conjunto de registros.  
  
```  
BOOL CanUpdate() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el conjunto de registros se puede actualizar; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 Un conjunto de registros puede ser de solo lectura si el origen de datos subyacente es de solo lectura o si especifica **CRecordset:: ReadOnly** en el `dwOptions` parámetro cuando se abre el conjunto de registros.  
  
##  <a name="checkrowseterror"></a>CRecordset::CheckRowsetError  
 Se llama para controlar los errores generados durante la captura de registro.  
  
```  
virtual void CheckRowsetError(RETCODE nRetCode);
```  
  
### <a name="parameters"></a>Parámetros  
 `nRetCode`  
 Código de retorno de una función de la API de ODBC. Para conocer más detalles, vea la sección Comentarios.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro virtual controla los errores que se producen cuando se buscan los registros, y es útil durante la obtención masiva de filas. Puede que desee considerar reemplazar `CheckRowsetError` para implementar su propio control de errores.  
  
 `CheckRowsetError`se llama automáticamente en una operación de desplazamiento de cursor, como **abiertos**, **Requery**, o cualquier **mover** operación. Se pasa el valor devuelto de la función API de ODBC **SQLExtendedFetch**. En la tabla siguiente se enumera los posibles valores para el `nRetCode` parámetro.  
  
|nRetCode|Descripción|  
|--------------|-----------------|  
|**SQL_SUCCESS**|Función se completó correctamente; No hay información adicional está disponible.|  
|**SQL_SUCCESS_WITH_INFO**|Función que se completó correctamente, posiblemente con un error recuperable. Información adicional se puede obtener mediante una llamada a **SQLError**.|  
|**SQL_NO_DATA_FOUND**|Todas las filas del conjunto de resultados se han capturado.|  
|**SQL_ERROR**|Error de la función. Información adicional se puede obtener mediante una llamada a **SQLError**.|  
|**SQL_INVALID_HANDLE**|Error en la función debido a un identificador de entorno no válido, el identificador de conexión o el identificador de instrucción. Esto indica un error de programación. No hay información adicional está disponible en **SQLError**.|  
|`SQL_STILL_EXECUTING`|Todavía se está ejecutando una función que se inicia de forma asincrónica. Tenga en cuenta que, de forma predeterminada, MFC nunca pasará este valor a `CheckRowsetError`; MFC continuará llamada **SQLExtendedFetch** hasta que ya no devuelve `SQL_STILL_EXECUTING`.|  
  
 Para obtener más información acerca de **SQLError**, consulte el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]. Para obtener más información sobre la obtención masiva de filas, vea el artículo [conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
##  <a name="close"></a>CRecordset:: Close  
 Cierra el conjunto de registros.  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>Comentarios  
 ODBC **HSTMT** y toda la memoria de trabajo se desasignan el marco de trabajo asignado para el conjunto de registros. Normalmente después de llamar a **cerrar**, eliminar el objeto de conjunto de registros de C++, si se asignó con **nueva**.  
  
 Puede llamar a **abiertos** nuevo después de llamar a **cerrar**. Esto le permite volver a usar el objeto de conjunto de registros. La alternativa consiste en llamar a **Requery**.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDatabase #17](../../mfc/codesnippet/cpp/crecordset-class_1.cpp)]  
  
##  <a name="crecordset"></a>CRecordset::CRecordset  
 Construye un objeto `CRecordset`.  
  
```  
CRecordset(CDatabase* pDatabase = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `pDatabase`  
 Contiene un puntero a un `CDatabase` objeto o el valor **NULL**. Si no **NULL** y `CDatabase` del objeto **abrir** función miembro no se ha llamado para conectarse al origen de datos, el conjunto de registros intenta abrir automáticamente durante su propio **abrir** llamar. Si se pasa **NULL**, un `CDatabase` objeto se construye y se conecta automáticamente con la información de origen de datos que especificó cuando se deriva la clase de conjunto de registros con ClassWizard.  
  
### <a name="remarks"></a>Comentarios  
 Puede usar `CRecordset` directamente o derivar una clase específica de la aplicación de `CRecordset`. Puede utilizar ClassWizard para derivar las clases de conjunto de registros.  
  
> [!NOTE]
>  Una clase derivada *debe* proporcionar su propio constructor. En el constructor de la clase derivada, llame al constructor `CRecordset::CRecordset`, pasando los parámetros adecuados junto a él.  
  
 Pasar **NULL** a su constructor de conjunto de registros para tener un `CDatabase` objeto construido y conecte automáticamente para usted. Se trata de un método abreviado útil que no es necesario crear y conectar un `CDatabase` objeto antes de construir el conjunto de registros.  
  
### <a name="example"></a>Ejemplo  
 Para obtener más información, vea el artículo [conjunto de registros: declarar una clase para una tabla (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md).  
  
##  <a name="delete"></a>CRecordset::Delete  
 Elimina el registro actual.  
  
```  
virtual void Delete();
```  
  
### <a name="remarks"></a>Comentarios  
 Después de una eliminación se realiza correctamente, se establecen los miembros de datos de campo del conjunto de registros en un valor Null, y debe llamar explícitamente a uno de los **mover** funciones con el fin de abandonar el registro eliminado. Una vez que abandonar el registro eliminado, no es posible volver a él. Si el origen de datos admite transacciones, puede realizar la **eliminar** llame a parte de una transacción. Para obtener más información, vea el artículo [transacción (ODBC)](../../data/odbc/transaction-odbc.md).  
  
> [!NOTE]
>  Si ha implementado la obtención masiva de filas, no se puede llamar **eliminar**. Esto producirá un error de aserción. Aunque clase `CRecordset` no proporciona un mecanismo para actualizar filas masivas de datos, puede escribir sus propias funciones mediante la función API de ODBC **SQLSetPos**. Para obtener más información sobre la obtención masiva de filas, vea el artículo [conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
> [!CAUTION]
>  El conjunto de registros debe ser actualizable y debe haber un registro válido actual en el conjunto de registros cuando se llama a **eliminar**; en caso contrario, se produce un error. Por ejemplo, si elimina un registro pero se desplaza a un nuevo registro antes de llamar a **eliminar** nuevo, **eliminar** produce una [CDBException](../../mfc/reference/cdbexception-class.md).  
  
 A diferencia de [AddNew](#addnew) y [editar](#edit), una llamada a **eliminar** no va seguida de una llamada a [actualización](#update). Si un **eliminar** llamada produce un error, los datos del campo miembros se dejan sin cambios.  
  
### <a name="example"></a>Ejemplo  
 En este ejemplo se muestra un conjunto de registros creado en el marco de una función. El ejemplo supone la existencia de `m_dbCust`, una variable miembro de tipo `CDatabase` ya está conectado al origen de datos.  
  
 [!code-cpp[NVC_MFCDatabase #18](../../mfc/codesnippet/cpp/crecordset-class_2.cpp)]  
  
##  <a name="dobulkfieldexchange"></a>CRecordset::DoBulkFieldExchange  
 Se llama para intercambiar masiva de filas de datos del origen de datos para el conjunto de registros. Implementa de forma masiva el intercambio de campos de registros (RFX masivo).  
  
```  
virtual void DoBulkFieldExchange(CFieldExchange* pFX);
```  
  
### <a name="parameters"></a>Parámetros  
 `pFX`  
 Un puntero a un [CFieldExchange](../../mfc/reference/cfieldexchange-class.md) objeto. El marco de trabajo ya habrá configurado este objeto para especificar un contexto para la operación de intercambio de campos.  
  
### <a name="remarks"></a>Comentarios  
 Cuando se implementa la obtención masiva de filas, el marco de trabajo llama a esta función miembro para transferir automáticamente los datos del origen de datos para el objeto de conjunto de registros. `DoBulkFieldExchange`también enlaza a los miembros de datos de parámetro, si los hay, para los marcadores de posición de parámetro en la cadena de la instrucción SQL para la selección del conjunto de registros.  
  
 Si no se implementa la obtención masiva de filas, el marco llama a [DoFieldExchange](#dofieldexchange). Para implementar la obtención masiva de filas, debe especificar el `CRecordset::useMultiRowFetch` opción de la `dwOptions` parámetro en el [abiertos](#open) función miembro.  
  
> [!NOTE]
> `DoBulkFieldExchange`solo está disponible si está utilizando una clase derivada de `CRecordset`. Si ha creado un objeto de conjunto de registros directamente desde `CRecordset`, debe llamar a la [GetFieldValue](#getfieldvalue) función miembro para recuperar los datos.  
  
 Intercambio masivo de campos de registros (RFX masivo) es similar al intercambio de campos de registros (RFX). Automáticamente, los datos se transfieren desde el origen de datos para el objeto de conjunto de registros. Sin embargo, no se puede llamar a `AddNew`, **editar**, **eliminar**, o **actualización** para transferir los cambios en el origen de datos. Clase `CRecordset` actualmente no proporciona un mecanismo para actualizar filas masivas de datos; sin embargo, puede escribir sus propias funciones mediante la función API de ODBC **SQLSetPos**.  
  
 Tenga en cuenta que ClassWizard no admite intercambio masivo de campos de registros; por lo tanto, es necesario reemplazar `DoBulkFieldExchange` manualmente mediante la escritura de llamadas a las funciones de RFX masivo. Para obtener más información acerca de estas funciones, vea el tema [funciones de intercambio de campos de registros](../../mfc/reference/record-field-exchange-functions.md).  
  
 Para obtener más información sobre la obtención masiva de filas, vea el artículo [conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md). Para obtener información relacionada, vea el artículo [intercambio de campos de registros (RFX)](../../data/odbc/record-field-exchange-rfx.md).  
  
##  <a name="dofieldexchange"></a>CRecordset:: DoFieldExchange  
 Se llama para intercambiar datos (en ambas direcciones) entre los miembros de datos de campo del conjunto de registros y el registro correspondiente en el origen de datos. Implementa registro (RFX) de intercambio de campos.  
  
```  
virtual void DoFieldExchange(CFieldExchange* pFX);
```  
  
### <a name="parameters"></a>Parámetros  
 `pFX`  
 Un puntero a un [CFieldExchange](../../mfc/reference/cfieldexchange-class.md) objeto. El marco de trabajo ya habrá configurado este objeto para especificar un contexto para la operación de intercambio de campos.  
  
### <a name="remarks"></a>Comentarios  
 Cuando no se ha implementado la obtención masiva de filas, el marco de trabajo llama a esta función miembro para automáticamente intercambiar datos entre los miembros de datos de campo del objeto de conjunto de registros y las columnas correspondientes del registro actual en el origen de datos. `DoFieldExchange`también enlaza a los miembros de datos de parámetro, si los hay, para los marcadores de posición de parámetro en la cadena de la instrucción SQL para la selección del conjunto de registros.  
  
 Si se implementa la obtención masiva de filas, el marco llama a [DoBulkFieldExchange](#dobulkfieldexchange). Para implementar la obtención masiva de filas, debe especificar el `CRecordset::useMultiRowFetch` opción de la `dwOptions` parámetro en el [abiertos](#open) función miembro.  
  
> [!NOTE]
> `DoFieldExchange`solo está disponible si está utilizando una clase derivada de `CRecordset`. Si ha creado un objeto de conjunto de registros directamente desde `CRecordset`, debe llamar a la [GetFieldValue](#getfieldvalue) función miembro para recuperar los datos.  
  
 El intercambio de datos de campo, denominado el intercambio de campos de registros (RFX), funciona en ambas direcciones: desde miembros de datos de campo del objeto de conjunto de registros a los campos del registro en el origen de datos y del registro en el origen de datos para el objeto de conjunto de registros.  
  
 La única acción que normalmente debe seguir para implementar `DoFieldExchange` para el conjunto de registros derivada clase consiste en crear la clase con ClassWizard y especificar los nombres y tipos de datos de los miembros de datos de campo. También puede agregar código a lo que escribe ClassWizard para especificar a los miembros de datos de parámetro o para ocuparse de las columnas que enlaza dinámicamente. Para obtener más información, vea el artículo [conjunto de registros: enlazar dinámicamente columnas de datos (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).  
  
 Cuando se declara la clase derivada de conjunto de registros con ClassWizard, el asistente escribe una invalidación de `DoFieldExchange` para usted, que es similar al siguiente:  
  
 [!code-cpp[NVC_MFCDatabase #19](../../mfc/codesnippet/cpp/crecordset-class_3.cpp)]  
  
 Para obtener más información acerca de las funciones de RFX, vea el tema [funciones de intercambio de campos de registros](../../mfc/reference/record-field-exchange-functions.md).  
  
 Para obtener más ejemplos y detalles acerca de `DoFieldExchange`, vea el artículo [intercambio de campos de registros: funcionamiento de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md). Para obtener información general sobre RFX, vea el artículo [intercambio de campos de registro](../../data/odbc/record-field-exchange-rfx.md).  
  
##  <a name="edit"></a>CRecordset::Edit  
 Permite que los cambios en el registro actual.  
  
```  
virtual void Edit();
```  
  
### <a name="remarks"></a>Comentarios  
 Después de llamar a **editar**, puede cambiar los miembros de datos de campo restableciendo directamente sus valores. La operación se completa cuando vuelve a llamar a la [actualización](#update) función de miembro para guardar los cambios en el origen de datos.  
  
> [!NOTE]
>  Si ha implementado la obtención masiva de filas, no se puede llamar **editar**. Esto producirá un error de aserción. Aunque clase `CRecordset` no proporciona un mecanismo para actualizar filas masivas de datos, puede escribir sus propias funciones mediante la función API de ODBC **SQLSetPos**. Para obtener más información sobre la obtención masiva de filas, vea el artículo [conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 **Editar** guarda los valores de los miembros de datos del conjunto de registros. Si se llama a **editar**, realizar cambios, a continuación, llame a **editar** nuevo, los valores del registro se restauran a su estado original antes de la primera **editar** llamar.  
  
 En algunos casos, puede que desee actualizar una columna por lo que es Null (que contiene ningún dato). Para ello, llame a [SetFieldNull](#setfieldnull) con un parámetro de **TRUE** para marcar el campo es Null; Esto también hace que la columna que se va a actualizar. Si desea que un campo se escriben en el origen de datos incluso si no ha cambiado su valor, llame a [SetFieldDirty](#setfielddirty) con un parámetro de **TRUE**. Esto funciona incluso si el campo tiene el valor Null.  
  
 Si el origen de datos admite transacciones, puede realizar la **editar** llame a parte de una transacción. Tenga en cuenta que debe llamar a [CDatabase::BeginTrans](../../mfc/reference/cdatabase-class.md#begintrans) antes de llamar a **editar** y después de que se ha abierto el conjunto de registros. Tenga en cuenta también que la llamada a [CDatabase::CommitTrans](../../mfc/reference/cdatabase-class.md#committrans) no constituye un sustituto para llamar a **actualización** para completar la **editar** operación. Para obtener más información acerca de las transacciones, vea la clase [CDatabase](../../mfc/reference/cdatabase-class.md).  
  
 Según el modo de bloqueo actual, el registro que se está actualizando esté bloqueado por **editar** hasta que llame a **actualización** o desplácese a otro registro, o puede que esté bloqueado solo durante la **editar** llamar. Puede cambiar el modo de bloqueo con [SetLockingMode](#setlockingmode).  
  
 Se restaura el valor anterior del registro actual si se desplaza a un nuevo registro antes de llamar a **actualización**. A `CDBException` se produce si se llama a **editar** para un conjunto de registros que no se puede actualizar o si no hay ningún registro actual.  
  
 Para obtener más información, vea los artículos [transacción (ODBC)](../../data/odbc/transaction-odbc.md) y [conjunto de registros: bloquear registros (ODBC)](../../data/odbc/recordset-locking-records-odbc.md).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDatabase Nº 20](../../mfc/codesnippet/cpp/crecordset-class_4.cpp)]  
  
##  <a name="flushresultset"></a>CRecordset::FlushResultSet  
 Recupera el siguiente conjunto de resultados de una consulta predefinida (procedimiento almacenado), si hay varios conjuntos de resultados.  
  
```  
BOOL FlushResultSet();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si no hay más conjuntos de resultados van a recuperar; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 Debe llamar a `FlushResultSet` sólo cuando se finalice completamente con el cursor en el conjunto de resultados actual. Tenga en cuenta que cuando se recupera el resultado siguiente establece mediante una llamada `FlushResultSet`, el cursor no es válido en ese conjunto de resultados; debe llamar a la [MoveNext](#movenext) función miembro después de llamar a `FlushResultSet`.  
  
 Si una consulta predefinida utiliza un parámetro de salida o parámetros de entrada/salida, debe llamar a `FlushResultSet` hasta que devuelve `FALSE` (el valor 0), con el fin de obtener estos valores de parámetro.  
  
 `FlushResultSet`llama a la función API de ODBC `SQLMoreResults`. Si `SQLMoreResults` devuelve `SQL_ERROR` o `SQL_INVALID_HANDLE`, a continuación, `FlushResultSet` se iniciará una excepción. Para obtener más información acerca de `SQLMoreResults`, consulte el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 El procedimiento almacenado debe enlazar los campos si desea llamar a `FlushResultSet`.  
  
### <a name="example"></a>Ejemplo  
 El código siguiente se da por supuesto que `COutParamRecordset` es un `CRecordset`-objeto derivado en función de una consulta predefinida con un parámetro de entrada y un parámetro de salida y tener varios conjuntos de resultados. Tenga en cuenta la estructura de la [DoFieldExchange](#dofieldexchange) invalidar.  
  
 [!code-cpp[NVC_MFCDatabase #21](../../mfc/codesnippet/cpp/crecordset-class_5.cpp)]  
  
 [!code-cpp[NVC_MFCDatabase #22](../../mfc/codesnippet/cpp/crecordset-class_6.cpp)]  
  
##  <a name="getbookmark"></a>CRecordset::GetBookmark  
 Obtiene el valor de marcador para el registro actual.  
  
```  
void GetBookmark(CDBVariant& varBookmark);
```  
  
### <a name="parameters"></a>Parámetros  
 `varBookmark`  
 Una referencia a un [CDBVariant](../../mfc/reference/cdbvariant-class.md) objeto que representa el marcador en el registro actual.  
  
### <a name="remarks"></a>Comentarios  
 Para determinar si se admiten marcadores en el conjunto de registros, llame a [CanBookmark](#canbookmark). Para disponer de marcadores si son compatibles, debe establecer el **CRecordset:: useBookmarks** opción en el `dwOptions` parámetro de la [abiertos](#open) función miembro.  
  
> [!NOTE]
>  Si los marcadores son no compatible o no está disponible, la llamada a `GetBookmark` se producirá una excepción. No se admiten marcadores en conjuntos de registros solo hacia delante.  
  
 `GetBookmark`asigna el valor de marcador para el registro actual a un `CDBVariant` objeto. Para devolver a ese registro en cualquier momento después de moverse a un registro diferente, llame a [SetBookmark](#setbookmark) con la correspondiente `CDBVariant` objeto.  
  
> [!NOTE]
>  Después de ciertas operaciones de conjunto de registros, los marcadores ya no estén válidos. Por ejemplo, si se llama a `GetBookmark` seguido **Requery**, es podrán que no pueda regresar al registro con `SetBookmark`. Llame a [CDatabase:: GetBookmarkPersistence](../../mfc/reference/cdatabase-class.md#getbookmarkpersistence) para comprobar si puede llamar con seguridad a `SetBookmark`.  
  
 Para obtener más información acerca de los marcadores y la navegación de conjunto de registros, vea los artículos [conjunto de registros: marcadores y posiciones absolutas (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md) y [conjunto de registros: desplazamiento (ODBC)](../../data/odbc/recordset-scrolling-odbc.md).  
  
##  <a name="getdefaultconnect"></a>CRecordset:: GetDefaultConnect  
 Se llama para obtener la cadena de conexión predeterminada.  
  
```  
virtual CString GetDefaultConnect();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un `CString` que contiene la cadena de conexión predeterminada.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a esta función miembro para obtener la cadena de conexión predeterminada para el origen de datos en el que se basa el conjunto de registros. ClassWizard implementa esta función automáticamente mediante la identificación del mismo origen de datos que se use en el Asistente para obtener información sobre las tablas y columnas. Probablemente les resultará conveniente confiar en esta conexión de manera predeterminada al desarrollar la aplicación. Pero la conexión predeterminada puede no ser adecuada para los usuarios de la aplicación. Si es así, se debe volver a implementar esta función, descartando versión de ClassWizard. Para obtener más información acerca de las cadenas de conexión, vea el artículo [origen de datos (ODBC)](../../data/odbc/data-source-odbc.md).  
  
##  <a name="getdefaultsql"></a>CRecordset::GetDefaultSQL  
 Se llama para obtener la cadena SQL predeterminada para ejecutar.  
  
```  
virtual CString GetDefaultSQL();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un `CString` que contiene la instrucción SQL predeterminada.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a esta función miembro para obtener la instrucción SQL de forma predeterminada en la que se basa el conjunto de registros. Podría tratarse de un nombre de tabla o una instancia de SQL **seleccione** instrucción.  
  
 Puede definir indirectamente la instrucción SQL predeterminada mediante la declaración de la clase de conjunto de registros con ClassWizard; ClassWizard realiza esta tarea automáticamente.  
  
 Si necesita la cadena de la instrucción SQL para su propio uso, llame a `GetSQL`, que devuelve la instrucción SQL utilizada para seleccionar registros del conjunto de registros cuando se abre. Puede editar la cadena SQL predeterminada en la invalidación de la clase de `GetDefaultSQL`. Por ejemplo, puede especificar una llamada a una consulta predefinida mediante un **llamar** instrucción. (Tenga en cuenta, sin embargo, que si edita `GetDefaultSQL`, también debe modificar `m_nFields` para que coincida con el número de columnas del origen de datos.)  
  
 Para obtener más información, vea el artículo [conjunto de registros: declarar una clase para una tabla (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md).  
  
> [!CAUTION]
>  El nombre de la tabla estará vacío si el marco de trabajo no pudo identificar un nombre de tabla, si se proporcionaron varios nombres de tabla, o si un **llamar** instrucción no se pudo interpretar. Tenga en cuenta que, cuando se usa un **llamar a** (instrucción), no debe insertar un espacio en blanco entre la llave y el **llamar a** (palabra clave), ni debe insertar espacio en blanco antes de la llave de apertura o el **seleccione** palabra clave en un **seleccione** instrucción.  
  
##  <a name="getfieldvalue"></a>CRecordset:: GetFieldValue  
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
 `lpszName`  
 El nombre de un campo.  
  
 *varValu*e  
 Una referencia a un [CDBVariant](../../mfc/reference/cdbvariant-class.md) objeto que se va a almacenar el valor del campo.  
  
 `nFieldType`  
 El tipo de datos ODBC C del campo. Con el valor predeterminado, **DEFAULT_FIELD_TYPE**, fuerza `GetFieldValue` determinar el tipo de datos de C desde el tipo de datos SQL, basándose en la tabla siguiente. En caso contrario, puede especificar los datos escribir directamente o puede elegir un tipo de datos compatible; Por ejemplo, puede almacenar cualquier tipo de datos en **SQL_C_CHAR**.  
  
|Tipo de datos C|Tipo de datos SQL|  
|-----------------|-------------------|  
|**SQL_C_BIT**|**SQL_BIT**|  
|**SQL_C_UTINYINT**|**SQL_TINYINT**|  
|**SQL_C_SSHORT**|**SQL_SMALLINT**|  
|**SQL_C_SLONG**|**SQL_INTEGER**|  
|**SQL_C_FLOAT**|**SQL_REAL**|  
|**SQL_C_DOUBLE**|**SQL_FLOATSQL_DOUBLE**|  
|**SQL_C_TIMESTAMP**|**SQL_DATESQL_TIMESQL_TIMESTAMP**|  
|**SQL_C_CHAR**|**SQL_NUMERICSQL_DECIMALSQL_BIGINTSQL_CHARSQL_VARCHARSQL_LONGVARCHAR**|  
|**SQL_C_BINARY**|**SQL_BINARYSQL_VARBINARYSQL_LONGVARBINARY**|  
  
 Para obtener más información sobre los tipos de datos ODBC, vea los temas "Tipos de datos de SQL" y "Tipos de datos de C" en el apéndice D de la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 `nIndex`  
 Índice de base cero del campo.  
  
 `strValue`  
 Una referencia a un [CString](../../atl-mfc-shared/reference/cstringt-class.md) objeto que se va a almacenar el valor del campo se convierte en texto, independientemente del tipo de datos del campo.  
  
### <a name="remarks"></a>Comentarios  
 Puede buscar un campo por su nombre o por índice. Puede almacenar el valor del campo en la vista una `CDBVariant` objeto o un `CString` objeto.  
  
 Si ha implementado la obtención masiva de filas, el registro actual siempre se sitúa en el primer registro de un conjunto de filas. Usar `GetFieldValue` en un registro en un conjunto de filas determinado, primero debe llamar a la [SetRowsetCursorPosition](#setrowsetcursorposition) función de miembro para mover el cursor a la fila deseada dentro de ese conjunto de filas. A continuación, llame a `GetFieldValue` para esa fila. Para implementar la obtención masiva de filas, debe especificar el `CRecordset::useMultiRowFetch` opción de la `dwOptions` parámetro en el [abiertos](#open) función miembro.  
  
 Puede usar `GetFieldValue` para capturar campos dinámicamente en tiempo de ejecución, en lugar de enlazarlos estáticamente en tiempo de diseño. Por ejemplo, si se ha declarado un objeto de conjunto de registros directamente desde `CRecordset`, debe usar `GetFieldValue` para recuperar los datos de campo; el intercambio de campos de registros (RFX) o el intercambio masivo de campos de registros (RFX masivo), no está implementada.  
  
> [!NOTE]
>  Si se declara un objeto de conjunto de registros sin tener que derivar de `CRecordset`, es necesario cargar la biblioteca de cursores de ODBC. La biblioteca de cursores requiere que el conjunto de registros tiene al menos una columna enlazada; Sin embargo, cuando usa `CRecordset` directamente, ninguna de las columnas están enlazada. Las funciones miembro [CDatabase:: OpenEx](../../mfc/reference/cdatabase-class.md#openex) y [CDatabase:: Open](../../mfc/reference/cdatabase-class.md#open) controlar si se puede cargar la biblioteca de cursores.  
  
 `GetFieldValue`llama a la función API de ODBC **SQLGetData**. Si el controlador envía el valor **SQL_NO_TOTAL** para la longitud real del valor del campo, `GetFieldValue` produce una excepción. Para obtener más información acerca de **SQLGetData**, consulte el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
 El código de ejemplo siguiente muestra las llamadas a `GetFieldValue` para declara un objeto de conjunto de registros directamente desde `CRecordset`.  
  
 [!code-cpp[NVC_MFCDatabase #23](../../mfc/codesnippet/cpp/crecordset-class_7.cpp)]  
  
> [!NOTE]
>  A diferencia de la clase DAO `CDaoRecordset`, `CRecordset` no tiene un `SetFieldValue` función miembro. Si crea un objeto directamente desde `CRecordset`, resulta eficaz de solo lectura.  
  
 Para obtener más información sobre la obtención masiva de filas, vea el artículo [conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
##  <a name="getodbcfieldcount"></a>CRecordset::GetODBCFieldCount  
 Recupera el número total de campos en el objeto de conjunto de registros.  
  
```  
short GetODBCFieldCount() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de campos del conjunto de registros.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información acerca de cómo crear conjuntos de registros, vea el artículo [conjunto de registros: crear y cerrar conjuntos de registros (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md).  
  
##  <a name="getodbcfieldinfo"></a>CRecordset::GetODBCFieldInfo  
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
 `lpszName`  
 El nombre de un campo.  
  
 `fieldinfo`  
 Una referencia a un `CODBCFieldInfo` estructura.  
  
 `nIndex`  
 Índice de base cero del campo.  
  
### <a name="remarks"></a>Comentarios  
 Una versión de la función le permite buscar un campo por su nombre. La otra versión le permite buscar un campo por su índice.  
  
 Para obtener una descripción acerca de la información devuelta, consulte el [CODBCFieldInfo](../../mfc/reference/codbcfieldinfo-structure.md) estructura.  
  
 Para obtener más información acerca de cómo crear conjuntos de registros, vea el artículo [conjunto de registros: crear y cerrar conjuntos de registros (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md).  
  
##  <a name="getrecordcount"></a>CRecordset::GetRecordCount  
 Determina el tamaño del conjunto de registros.  
  
```  
long GetRecordCount() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de registros en el conjunto de registros; 0 si el conjunto de registros no contiene registros; o -1 si no se puede determinar el número de registros.  
  
### <a name="remarks"></a>Comentarios  
  
> [!CAUTION]
>  El número de registros se mantiene como una "marca de agua," el registro con el número mayor aún aparece cuando el usuario mueve por los registros. Solo se conoce el número total de registros después de que el usuario ha movido más allá del último registro. Por motivos de rendimiento, el recuento no se actualiza cuando se llama a `MoveLast`. Para contar los registros, llame a `MoveNext` repetidamente hasta que `IsEOF` devuelve es distinto de cero. Agregar un registro a través de **CRecordset:AddNew** y **actualización** aumenta el recuento; eliminar un registro a través de `CRecordset::Delete` disminuye el recuento.  
  
##  <a name="getrowsetsize"></a>CRecordset::GetRowsetSize  
 Obtiene la configuración actual para el número de filas que se va a recuperar durante una operación de obtención determinada.  
  
```  
DWORD GetRowsetSize() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de filas que desea recuperar durante una operación de obtención determinada.  
  
### <a name="remarks"></a>Comentarios  
 Si está usando la obtención masiva de filas, el tamaño del conjunto de filas de forma predeterminada cuando se abre el conjunto de registros es 25; en caso contrario, es 1.  
  
 Para implementar la obtención masiva de filas, debe especificar el `CRecordset::useMultiRowFetch` opción en el `dwOptions` parámetro de la [abiertos](#open) función miembro. Para cambiar la configuración para el tamaño del conjunto de filas, llame a [SetRowsetSize](#setrowsetsize).  
  
 Para obtener más información sobre la obtención masiva de filas, vea el artículo [conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
##  <a name="getrowsfetched"></a>CRecordset::GetRowsFetched  
 Determina el número de registros se recuperaron realmente después de una captura.  
  
```  
DWORD GetRowsFetched() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de filas se recupera del origen de datos después de una operación de obtención determinada.  
  
### <a name="remarks"></a>Comentarios  
 Esto es útil cuando se ha implementado la obtención masiva de filas. Normalmente, el tamaño del conjunto de filas indica cuántas filas se recuperan desde una captura; Sin embargo, el número total de filas del conjunto de registros también afecta al número de filas se recuperarán en un conjunto de filas. Por ejemplo, si el conjunto de registros tiene 10 registros con un valor de tamaño de conjunto de filas de 4, a continuación, recorrer en bucle el conjunto de registros mediante una llamada a `MoveNext` dará como resultado el conjunto de filas final contenedoras de registros solo 2.  
  
 Para implementar la obtención masiva de filas, debe especificar el `CRecordset::useMultiRowFetch` opción en el `dwOptions` parámetro de la [abiertos](#open) función miembro. Para especificar el tamaño del conjunto de filas, llame a [SetRowsetSize](#setrowsetsize).  
  
 Para obtener más información sobre la obtención masiva de filas, vea el artículo [conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDatabase #24](../../mfc/codesnippet/cpp/crecordset-class_8.cpp)]  
  
##  <a name="getrowstatus"></a>CRecordset::GetRowStatus  
 Obtiene el estado de una fila en el conjunto de filas actual.  
  
```  
WORD GetRowStatus(WORD wRow) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `wRow`  
 La posición basada en uno de una fila en el conjunto de filas actual. Este valor puede oscilar entre 1 y el tamaño del conjunto de filas.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor de estado de la fila. Para conocer más detalles, vea la sección Comentarios.  
  
### <a name="remarks"></a>Comentarios  
 `GetRowStatus`Devuelve un valor que indica cualquier cualquier cambio en el estado a la fila porque era el último recuperados desde el origen de datos, o que no existe la fila correspondiente a `wRow` se capturó. La tabla siguiente muestra los valores devueltos posibles.  
  
|Valor de estado|Descripción|  
|------------------|-----------------|  
|`SQL_ROW_SUCCESS`|La fila se modifica.|  
|`SQL_ROW_UPDATED`|Se ha actualizado la fila.|  
|`SQL_ROW_DELETED`|Se ha eliminado la fila.|  
|`SQL_ROW_ADDED`|Se ha agregado la fila.|  
|`SQL_ROW_ERROR`|La fila es no se puede recuperar debido a un error.|  
|`SQL_ROW_NOROW`|No hay ninguna fila que corresponde a `wRow`.|  
  
 Para obtener más información, vea la función API de ODBC **SQLExtendedFetch** en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="getstatus"></a>CRecordset::GetStatus  
 Determina el índice del registro actual en el conjunto de registros y si se ha visto el último registro.  
  
```  
void GetStatus(CRecordsetStatus& rStatus) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `rStatus`  
 Una referencia a un **CRecordsetStatus** objeto. Vea la sección Comentarios para obtener más información.  
  
### <a name="remarks"></a>Comentarios  
 `CRecordset`Si se intenta realizar un seguimiento del índice, pero en algunos casos esto puede no ser posible. Vea [GetRecordCount](#getrecordcount) para obtener una explicación.  
  
 El **CRecordsetStatus** estructura tiene el formato siguiente:  
  
 `struct CRecordsetStatus`  
  
 `{`  
  
 `long m_lCurrentRecord;`  
  
 `BOOL m_bRecordCountFinal;`  
  
 `};`  
  
 Los dos miembros de **CRecordsetStatus** tienen los significados siguientes:  
  
- **m_lCurrentRecord** contiene el índice de base cero del registro actual en el conjunto de registros, si se conoce. Si no se puede determinar el índice, este miembro contiene **AFX_CURRENT_RECORD_UNDEFINED** (-2). Si `IsBOF` es **TRUE** (vaciar registros o se intentó desplazar anterior al primer registro), a continuación, **m_lCurrentRecord** está establecido en **AFX_CURRENT_RECORD_BOF** (-1). Si, a continuación, en el primer registro, se establece en 0, en segundo lugar grabar 1 y así sucesivamente.  
  
- **m_bRecordCountFinal** Nonzero si se ha determinado el número total de registros en el conjunto de registros. Por lo general esto debe realizarse empezando en el principio del conjunto de registros y llamando a `MoveNext` hasta que `IsEOF` devuelve es distinto de cero. Si este miembro es cero, el registro de recuento devuelto por `GetRecordCount`, si es de -1, solo un recuento de "marca de agua" de los registros.  
  
##  <a name="getsql"></a>CRecordset::GetSQL  
 Llame a esta función miembro para obtener la instrucción SQL que se usa para seleccionar los registros del conjunto de registros al que se abrió.  
  
```  
const CString& GetSQL() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 A **const** hacen referencia a un `CString` que contiene la instrucción SQL.  
  
### <a name="remarks"></a>Comentarios  
 Esto suele ser una instancia de SQL **seleccione** instrucción. La cadena devuelta por `GetSQL` es de solo lectura.  
  
 La cadena devuelta por `GetSQL` suele ser distinto de cualquier cadena que se ha pasado para el conjunto de registros en la `lpszSQL` parámetro a la **abiertos** función miembro. Esto es porque el conjunto de registros construye una instrucción SQL completa en función de lo que pasa a **abiertos**, lo que hayas especificado con ClassWizard, lo que puede que haya especificado en el **m_strFilter** y `m_strSort` miembros de datos y los parámetros que haya especificado. Para obtener más información acerca de cómo el conjunto de registros crea esta instrucción SQL, vea el artículo [conjunto de registros: cómo se seleccionan los registros (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md).  
  
> [!NOTE]
>  Llame a esta función miembro solo después de llamar a [abiertos](#open).  
  
##  <a name="gettablename"></a>CRecordset::GetTableName  
 Obtiene el nombre de la tabla SQL en el que se basa la consulta del conjunto de registros.  
  
```  
const CString& GetTableName() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 A **const** hacen referencia a un `CString` que contiene la tabla el nombre, si el conjunto de registros está basado en una tabla; en caso contrario, una cadena vacía.  
  
### <a name="remarks"></a>Comentarios  
 `GetTableName`solo es válida si el conjunto de registros se basa en una tabla, no una combinación de varias tablas o una consulta predefinida (procedimiento almacenado). El nombre es de sólo lectura.  
  
> [!NOTE]
>  Llame a esta función miembro solo después de llamar a [abiertos](#open).  
  
##  <a name="isbof"></a>CRecordset::IsBOF  
 Devuelve un valor distinto de cero si el conjunto de registros se ha colocado antes del primer registro. No hay ningún registro actual.  
  
```  
BOOL IsBOF() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el conjunto de registros no contiene registros o si se ha desplazado hacia atrás delante del primer registro; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función miembro antes de que se desplaza de registro a registro para obtener información sobre si ha realizado antes del primer registro del conjunto de registros. También puede usar `IsBOF` junto con `IsEOF` para determinar si el conjunto de registros contiene todos los registros o está vacío. Inmediatamente después de llamar a **abiertos**, si el conjunto de registros no contiene registros, `IsBOF` devuelve es distinto de cero. Al abrir un conjunto de registros que tiene al menos un registro, el primer registro es el registro actual y `IsBOF` devuelve 0.  
  
 Si el primer registro es el registro actual y se llama `MovePrev`, `IsBOF` posteriormente devolverá es distinto de cero. Si `IsBOF` devuelve es distinto de cero y se llama a `MovePrev`, se produce un error. Si `IsBOF` devuelve es distinto de cero, el registro actual no está definido, y cualquier acción que requiere un registro actual se producirá un error.  
  
### <a name="example"></a>Ejemplo  
 Este ejemplo se utiliza `IsBOF` y `IsEOF` para detectar los límites de un conjunto de registros, como el código se desplaza por el conjunto de registros en ambas direcciones.  
  
 [!code-cpp[NVC_MFCDatabase #25](../../mfc/codesnippet/cpp/crecordset-class_9.cpp)]  
  
##  <a name="isdeleted"></a>CRecordset::IsDeleted  
 Determina si se ha eliminado el registro actual.  
  
```  
BOOL IsDeleted() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el conjunto de registros está situado en un registro eliminado; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 Si se desplaza a un registro y `IsDeleted` devuelve **TRUE** (distinto de cero,), a continuación, debe desplazar a otro registro para poder realizar otras operaciones de conjunto de registros.  
  
 El resultado de `IsDeleted` depende de muchos factores, como el tipo de conjunto de registros, si el conjunto de registros es actualizable, que indica si especifica la **skipDeletedRecords** opción cuando se abre el conjunto de registros, si los módulos de controlador eliminan los registros y determinar si hay varios usuarios.  
  
 Para obtener más información acerca de **skipDeletedRecords** y controlador de empaquetado, vea el [abrir](#open) función miembro.  
  
> [!NOTE]
>  Si ha implementado la obtención masiva de filas, no debe llamar `IsDeleted`. En su lugar, llame a la [GetRowStatus](#getrowstatus) función miembro. Para obtener más información sobre la obtención masiva de filas, vea el artículo [conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
##  <a name="iseof"></a>CRecordset::IsEOF  
 Devuelve un valor distinto de cero si el conjunto de registros se ha colocado después del último registro. No hay ningún registro actual.  
  
```  
BOOL IsEOF() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el conjunto de registros no contiene registros o si se ha desplazado más allá del último registro; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función miembro mientras se desplaza de registro a registro para obtener información sobre si ha ido más allá del último registro del conjunto de registros. También puede utilizar `IsEOF` para determinar si el conjunto de registros contiene todos los registros o está vacío. Inmediatamente después de llamar a **abiertos**, si el conjunto de registros no contiene registros, `IsEOF` devuelve es distinto de cero. Al abrir un conjunto de registros que tiene al menos un registro, el primer registro es el registro actual y `IsEOF` devuelve 0.  
  
 Si el último registro es el registro actual cuando se llama a `MoveNext`, `IsEOF` posteriormente devolverá es distinto de cero. Si `IsEOF` devuelve es distinto de cero y se llama a `MoveNext`, se produce un error. Si `IsEOF` devuelve es distinto de cero, el registro actual no está definido, y cualquier acción que requiere un registro actual se producirá un error.  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [IsBOF](#isbof).  
  
##  <a name="isfielddirty"></a>CRecordset::IsFieldDirty  
 Determina si el miembro de datos del campo especificado ha cambiado desde [editar](#edit) o [AddNew](#addnew) se llamó.  
  
```  
BOOL IsFieldDirty(void* pv);
```  
  
### <a name="parameters"></a>Parámetros  
 `pv`  
 Un puntero a miembro de datos del campo cuyo estado desea comprobar, o **NULL** para determinar si cualquiera de los campos están desfasada.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el miembro de datos del campo especificado ha cambiado desde que realiza la llamada `AddNew` o **editar**; de lo contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Los datos de todos los miembros de datos de campo modificados se transferirán al registro en el origen de datos cuando se actualiza el registro actual mediante una llamada a la [actualización](#update) función miembro de `CRecordset` (después de una llamada a **editar** o `AddNew`).  
  
> [!NOTE]
>  Esta función miembro no es aplicable en conjuntos de registros que están usando la obtención masiva de filas. Si ha implementado obtención masiva de filas, a continuación, `IsFieldDirty` siempre devolverá **FALSE** y se producirá un error de aserción. Para obtener más información sobre la obtención masiva de filas, vea el artículo [conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Al llamar a `IsFieldDirty` restablecerá los efectos de las anteriores llamadas a [SetFieldDirty](#setfielddirty) desde que se vuelve a evaluar el estado modificado del campo. En el `AddNew` caso, si el valor del campo actual difiere del valor de null de seudoprueba, el campo estado se establece desfasado. En el **editar** caso, si el valor del campo difiere del valor almacenado en caché, el estado del campo se establece desfasado.  
  
 `IsFieldDirty`se implementa a través de [DoFieldExchange](#dofieldexchange).  
  
 Para obtener más información sobre la marca de modificado, consulte el artículo [conjunto de registros: cómo se seleccionan los registros (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md).  
  
##  <a name="isfieldnull"></a>CRecordset::IsFieldNull  
 Devuelve un valor distinto de cero si el campo especificado en el registro actual es Null (no tiene ningún valor).  
  
```  
BOOL IsFieldNull(void* pv);
```  
  
### <a name="parameters"></a>Parámetros  
 `pv`  
 Un puntero a miembro de datos del campo cuyo estado desea comprobar, o **NULL** para determinar si cualquiera de los campos son Null.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el miembro de datos del campo especificado se marca como Null; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función miembro para determinar si el miembro de datos del campo especificado de un conjunto de registros se ha marcado como Null. (En la terminología de base de datos, Null significa "no having ningún valor" y no es igual a **NULL** en C++.) Si un miembro de datos de campo se marca como Null, se interpreta como una columna del registro actual para el que no hay ningún valor.  
  
> [!NOTE]
>  Esta función miembro no es aplicable en conjuntos de registros que están usando la obtención masiva de filas. Si ha implementado obtención masiva de filas, a continuación, `IsFieldNull` siempre devolverá **FALSE** y se producirá un error de aserción. Para obtener más información sobre la obtención masiva de filas, vea el artículo [conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 `IsFieldNull`se implementa a través de [DoFieldExchange](#dofieldexchange).  
  
##  <a name="isfieldnullable"></a>CRecordset::IsFieldNullable  
 Devuelve un valor distinto de cero si el campo especificado en el registro actual se puede establecer en Null (no tener ningún valor).  
  
```  
BOOL IsFieldNullable(void* pv);
```  
  
### <a name="parameters"></a>Parámetros  
 `pv`  
 Un puntero a miembro de datos del campo cuyo estado desea comprobar, o **NULL** para determinar si cualquiera de los campos puede establecerse en un valor Null.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función miembro determinar si el miembro de datos del campo especificado es "que aceptan valores null" (se pueden establecer en un valor Null; C++ **NULL** no es igual a Null, lo que, en la terminología de base de datos, significa "no having ningún valor").  
  
> [!NOTE]
>  Si ha implementado la obtención masiva de filas, no se puede llamar `IsFieldNullable`. En su lugar, llame a la [a GetODBCFieldInfo](#getodbcfieldinfo) función de miembro para determinar si se puede establecer un campo como un valor Null. Tenga en cuenta que siempre se puede llamar `GetODBCFieldInfo`, independientemente de si ha implementado la obtención masiva de filas. Para obtener más información sobre la obtención masiva de filas, vea el artículo [conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Un campo que no puede ser Null debe tener un valor. Si se intenta establecer un este tipo de campo como Null al agregar o actualizar un registro, el origen de datos rechaza la adición o la actualización, y [actualizar](#update) se iniciará una excepción. La excepción se produce cuando se llama a **actualización**, no cuando se llama a [SetFieldNull](#setfieldnull).  
  
 Usar **NULL** para el primer argumento de la función aplicará únicamente a la función **outputColumn** campos, no **param** campos. Por ejemplo, la llamada  
  
 [!code-cpp[26 de # NVC_MFCDatabase](../../mfc/codesnippet/cpp/crecordset-class_10.cpp)]  
  
 establecerá solo **outputColumn** campos a **NULL**; **param** campos no se verá afectados.  
  
 Para que funcione en **param** campos, debe proporcionar la dirección real de la persona **param** que desea trabajar en ella, como:  
  
 [!code-cpp[NVC_MFCDatabase #27](../../mfc/codesnippet/cpp/crecordset-class_11.cpp)]  
  
 Esto significa que no se puede establecer todos los **param** campos a **NULL**, tal y como se haría con **outputColumn** campos.  
  
 `IsFieldNullable`se implementa a través de [DoFieldExchange](#dofieldexchange).  
  
##  <a name="isopen"></a>CRecordset::IsOpen  
 Determina si el conjunto de registros ya está abierto.  
  
```  
BOOL IsOpen() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el objeto de conjunto de registros [abiertos](#open) o [Requery](#requery) función miembro se ha llamado anteriormente y el conjunto de registros no se ha cerrado; en caso contrario, 0.  
  
##  <a name="m_hstmt"></a>CRecordset:: M_hstmt  
 Contiene un identificador de la estructura de datos de la instrucción de ODBC de tipo **HSTMT**, asociado con el conjunto de registros.  
  
### <a name="remarks"></a>Comentarios  
 Cada consulta a un origen de datos ODBC está asociado con un **HSTMT**.  
  
> [!CAUTION]
>  No utilice **m_hstmt** antes de [abiertos](#open) se ha llamado.  
  
 Normalmente no es necesario tener acceso a la **HSTMT** directamente, pero puede que tenga para la ejecución directa de instrucciones SQL. El `ExecuteSQL` función miembro de clase `CDatabase` proporciona un ejemplo del uso **m_hstmt**.  
  
##  <a name="m_nfields"></a>CRecordset::m_nFields  
 Contiene el número de miembros de datos de campo en la clase de conjunto de registros; es decir, el número de columnas seleccionadas por el conjunto de registros desde el origen de datos.  
  
### <a name="remarks"></a>Comentarios  
 Debe inicializar el constructor de la clase de conjunto de registros `m_nFields` con el número correcto. Si no ha implementado la obtención masiva de filas, ClassWizard escribe esta inicialización cuando se usa para declarar la clase de conjunto de registros. También puede escribir manualmente.  
  
 El marco de trabajo utiliza este número para administrar la interacción entre los miembros de datos de campo y las columnas correspondientes del registro actual en el origen de datos.  
  
> [!CAUTION]
>  Este número debe coincidir con el número de "columnas de salida" registrado en `DoFieldExchange` o `DoBulkFieldExchange` después de llamar a [SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype) con el parámetro **CFieldExchange::outputColumn**.  
  
 Puede enlazar columnas dinámicamente, como se explica en el artículo "conjunto de registros: dinámicamente columnas de datos de enlace." Si lo hace, debe aumentar el número de `m_nFields` para reflejar el número de función RFX o RFX masivo llama su `DoFieldExchange` o `DoBulkFieldExchange` función de miembro para las columnas enlazadas dinámicamente.  
  
 Para obtener más información, vea los artículos [conjunto de registros: enlazar dinámicamente columnas de datos (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md) y [conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
### <a name="example"></a>Ejemplo  
 Vea el artículo [intercambio de campos de registros: Utilizar RFX](../../data/odbc/record-field-exchange-using-rfx.md).  
  
##  <a name="m_nparams"></a>CRecordset::m_nParams  
 Contiene el número de miembros de datos de parámetro en la clase de conjunto de registros; es decir, el número de parámetros pasados con la consulta del conjunto de registros.  
  
### <a name="remarks"></a>Comentarios  
 Si la clase de conjunto de registros tiene los miembros de datos de parámetro, debe inicializar el constructor de la clase `m_nParams` con el número correcto. El valor de `m_nParams` el valor predeterminado es 0. Si agrega miembros de datos de parámetro (lo que debe hacer manualmente) también debe agregar manualmente una inicialización en el constructor de clase para reflejar el número de parámetros (que debe ser al menos tan grande como el número de "marcadores de posición en la **m_strFilter** o `m_strSort` cadena).  
  
 El marco de trabajo utiliza este número cuando parametriza la consulta del conjunto de registros.  
  
> [!CAUTION]
>  Este número debe coincidir con el número de "parámetros" registrados en `DoFieldExchange` o `DoBulkFieldExchange` después de llamar a [SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype) con un valor de parámetro de **CFieldExchange::inputParam**, **CFieldExchange::param**, **CFieldExchange::outputParam**, o **CFieldExchange::inoutParam**.  
  
### <a name="example"></a>Ejemplo  
  Consulte los artículos [conjunto de registros: parametrizar un conjunto de registros (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md) y [intercambio de campos de registros: Utilizar RFX](../../data/odbc/record-field-exchange-using-rfx.md).  
  
##  <a name="m_pdatabase"></a>CRecordset::m_pDatabase  
 Contiene un puntero a la `CDatabase` objeto a través del cual el conjunto de registros está conectado a un origen de datos.  
  
### <a name="remarks"></a>Comentarios  
 Esta variable se establece de dos maneras. Por lo general, pasar un puntero a una ya estaba conectado `CDatabase` objeto cuando se construya el objeto de conjunto de registros. Si se pasa **NULL** en su lugar, `CRecordset` crea un `CDatabase` objeto automáticamente y lo conecta. En cualquier caso, `CRecordset` almacena el puntero en esta variable.  
  
 Normalmente no directamente debe usar el puntero almacenado en **m_pDatabase**. Si escribe sus propias extensiones al `CRecordset`, sin embargo, deberá utilizar el puntero. Por ejemplo, podría necesitar el puntero si se produce su propio `CDBException`s. O tal vez necesite si necesita hacer algo con el mismo `CDatabase` objeto, como la ejecución de transacciones, tiempos de espera de la configuración, o llamar a la `ExecuteSQL` función miembro de clase `CDatabase` para ejecutar instrucciones SQL directamente.  
  
##  <a name="m_strfilter"></a>CRecordset:: M_strfilter  
 Después de crear el objeto de conjunto de registros, pero antes de llamar a su **abiertos** miembro funcione, use este miembro de datos para almacenar una `CString` que contiene una instancia de SQL **donde** cláusula.  
  
### <a name="remarks"></a>Comentarios  
 El conjunto de registros usa esta cadena para restringir (o filtrar) los registros selecciona durante la **abiertos** o **Requery** llamar. Esto es útil para seleccionar un subconjunto de registros, como "todos los vendedores con sede en California" ("estado = CA"). La sintaxis SQL de ODBC para una **donde** cláusula es  
  
 `WHERE search-condition`  
  
 Tenga en cuenta que no incluye el **donde** palabra clave de la cadena. El marco de trabajo lo proporciona.  
  
 También se puede parametrizar la cadena de filtro mediante la colocación de '' marcadores de posición, declarar un miembro de datos de parámetro en la clase para cada marcador de posición y pasar los parámetros que el conjunto de registros en tiempo de ejecución. Esto le permite construir el filtro en tiempo de ejecución. Para obtener más información, vea el artículo [conjunto de registros: parametrizar un conjunto de registros (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).  
  
 Para obtener más información acerca de SQL **donde** cláusulas, vea el artículo [SQL](../../data/odbc/sql.md). Para obtener más información sobre cómo seleccionar y filtrar registros, vea el artículo [conjunto de registros: filtrar registros (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDatabase #30](../../mfc/codesnippet/cpp/crecordset-class_12.cpp)]  
  
##  <a name="m_strsort"></a>CRecordset::m_strSort  
 Después de crear el objeto de conjunto de registros, pero antes de llamar a su **abiertos** miembro funcione, use este miembro de datos para almacenar una `CString` que contiene una instancia de SQL **ORDER BY** cláusula.  
  
### <a name="remarks"></a>Comentarios  
 El conjunto de registros usa esta cadena para ordenar los registros selecciona durante la **abiertos** o **Requery** llamar. Puede usar esta característica para ordenar un conjunto de registros en una o más columnas. La sintaxis SQL de ODBC para una **ORDER BY** cláusula es  
  
 `ORDER BY sort-specification [, sort-specification]...`  
  
 donde una especificación de ordenación es un entero o un nombre de columna. También puede especificar el orden ascendente o descendente (el orden es ascendente de forma predeterminada) mediante la anexión de "ASC" o "DESC" a la lista de columnas en la cadena de ordenación. Los registros seleccionados aparecen ordenados primero por la primera columna y luego por el segundo y así sucesivamente. Por ejemplo, puede ordenar un conjunto de registros "Customers" por apellido y luego por nombres. El número de columnas, puede obtener una lista depende del origen de datos. Para obtener más información, vea [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 Tenga en cuenta que no incluye el **ORDER BY** palabra clave de la cadena. El marco de trabajo lo proporciona.  
  
 Para obtener más información acerca de las cláusulas SQL, vea el artículo [SQL](../../data/odbc/sql.md). Para obtener más información acerca de cómo ordenar registros, vea el artículo [conjunto de registros: ordenar registros (ODBC)](../../data/odbc/recordset-sorting-records-odbc.md).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDatabase #31](../../mfc/codesnippet/cpp/crecordset-class_13.cpp)]  
  
##  <a name="move"></a>CRecordset:: Move  
 Mueve el puntero de registro actual en el conjunto de registros, hacia delante o hacia atrás.  
  
```  
virtual void Move(
    long nRows,  
    WORD wFetchType = SQL_FETCH_RELATIVE);
```  
  
### <a name="parameters"></a>Parámetros  
 `nRows`  
 El número de filas que debe desplazarse hacia delante o hacia atrás. Los valores positivos desplazarse hacia delante, hacia el final del conjunto de registros. Los valores negativos hacia atrás, mover hacia el principio.  
  
 `wFetchType`  
 Determina el conjunto de filas que **mover** capturará. Para conocer más detalles, vea la sección Comentarios.  
  
### <a name="remarks"></a>Comentarios  
 Si se pasa un valor de 0 para `nRows`, **mover** actualiza el registro actual; **Mover** finalizará cualquier actual `AddNew` o **editar** modo y se restaurará el valor del registro actual antes de `AddNew` o **editar** se llamó.  
  
> [!NOTE]
>  Cuando se mueve a través de un conjunto de registros, no se puede omitir los registros eliminados. Vea [CRecordset::IsDeleted](#isdeleted) para obtener más información. Cuando se abre un `CRecordset` con el **skipDeletedRecords** establecida, la opción **mover** valida si el `nRows` parámetro es 0. Este comportamiento impide que la actualización de filas eliminadas por otras aplicaciones de cliente utilizando los mismos datos. Consulte la `dwOption` parámetro en [abiertos](#open) para obtener una descripción de **skipDeletedRecords**.  
  
 **Mover** cambia de posición el conjunto de registros por conjuntos de filas. En función de los valores de `nRows` y `wFetchType`, **mover** recupera el conjunto de filas adecuado y, a continuación, hace que el primer registro de ese conjunto de filas del registro actual. Si no ha implementado la obtención masiva de filas, el tamaño del conjunto de filas es siempre 1. Al capturar un conjunto de filas, **mover** llama directamente el [CheckRowsetError](#checkrowseterror) función de miembro para controlar los errores resultantes de la operación de captura.  
  
 Según los valores se pasan, **mover** es equivalente a otro `CRecordset` funciones miembro. En concreto, el valor de `wFetchType` puede indicar una función miembro que es más intuitiva y a menudo el método preferido para mover el registro actual.  
  
 En la tabla siguiente se enumera los posibles valores para `wFetchType`, el conjunto de filas que **mover** capturará basado en `wFetchType` y `nRows`y de cualquier función miembro equivalente correspondiente a `wFetchType`.  
  
|wFetchType|Conjunto de filas capturada|Función miembro equivalente|  
|----------------|--------------------|--------------------------------|  
|`SQL_FETCH_RELATIVE`(el valor predeterminado)|El conjunto de filas a partir `nRows` filas de la primera fila del conjunto de filas actual.||  
|`SQL_FETCH_NEXT`|El siguiente conjunto de filas; `nRows` se omite.|[MoveNext](#movenext)|  
|`SQL_FETCH_PRIOR`|El conjunto de filas anterior; `nRows` se omite.|[MovePrev](#moveprev)|  
|`SQL_FETCH_FIRST`|El primer conjunto de filas del conjunto de registros; `nRows` se omite.|[MoveFirst](#movefirst)|  
|`SQL_FETCH_LAST`|El último conjunto de filas completo en el conjunto de registros; `nRows` se omite.|[MoveLast](#movelast)|  
|`SQL_FETCH_ABSOLUTE`|Si `nRows` > 0, el conjunto de filas a partir de `nRows` filas desde el principio del conjunto de registros. Si `nRows` < 0,="" the="" rowset="" starting=""> `nRows` filas desde el final del conjunto de registros. Si `nRows` = 0, se devuelve una condición de inicio del archivo (BOF).|[SetAbsolutePosition](#setabsoluteposition)|  
|`SQL_FETCH_BOOKMARK`|El conjunto de filas a partir de la fila cuyo valor de marcador corresponde a `nRows`.|[SetBookmark](#setbookmark)|  
  
> [!NOTE]
>  Para conjuntos de registros solo hacia delante, **mover** sólo es válido con un valor de `SQL_FETCH_NEXT` para `wFetchType`.  
  
> [!CAUTION]
>  Al llamar a **mover** produce una excepción si el conjunto de registros no tiene registros. Para determinar si el conjunto de registros tiene los registros, llame a [IsBOF](#isbof) y [IsEOF](#iseof).  
  
> [!NOTE]
>  Si se ha desplazado más allá del principio o al final del conjunto de registros ( `IsBOF` o `IsEOF` devuelve un valor distinto de cero), la llamada a un **mover** función posiblemente generará un `CDBException`. Por ejemplo, si `IsEOF` devuelve un valor distinto de cero y `IsBOF` no es así, a continuación, `MoveNext` se iniciará una excepción, pero `MovePrev` no lo hará.  
  
> [!NOTE]
>  Si se llama a **mover** mientras el registro actual se actualiza o agregado, las actualizaciones se pierden sin previo aviso.  
  
 Para obtener más información sobre la navegación de conjunto de registros, vea los artículos [conjunto de registros: desplazamiento (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) y [conjunto de registros: marcadores y posiciones absolutas (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md). Para obtener más información sobre la obtención masiva de filas, vea el artículo [conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md). Para obtener información relacionada, vea la función API de ODBC **SQLExtendedFetch** en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDatabase #28](../../mfc/codesnippet/cpp/crecordset-class_14.cpp)]  
  
##  <a name="movefirst"></a>CRecordset::MoveFirst  
 Convierte el primer registro en el primer conjunto de filas del registro actual.  
  
```  
void MoveFirst();
```  
  
### <a name="remarks"></a>Comentarios  
 Independientemente de si se ha implementado el obtención masiva de filas, siempre será el primer registro del conjunto de registros.  
  
 No es necesario llamar a **MoveFirst** inmediatamente después de abrir el conjunto de registros. En ese momento, el primer registro (si existe) es automáticamente el registro actual.  
  
> [!NOTE]
>  Esta función miembro no es válida para conjuntos de registros solo hacia delante.  
  
> [!NOTE]
>  Cuando se mueve a través de un conjunto de registros, no se puede omitir los registros eliminados. Consulte la [IsDeleted](#isdeleted) función de miembro para obtener más información.  
  
> [!CAUTION]
>  Llamar a cualquiera de los **mover** funciones produce una excepción si el conjunto de registros no tiene registros. Para determinar si el conjunto de registros tiene los registros, llame a `IsBOF` y `IsEOF`.  
  
> [!NOTE]
>  Si se llama a cualquiera de los **mover** funciona mientras el registro actual se actualiza o agregado, las actualizaciones se pierden sin previo aviso.  
  
 Para obtener más información sobre la navegación de conjunto de registros, vea los artículos [conjunto de registros: desplazamiento (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) y [conjunto de registros: marcadores y posiciones absolutas (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md). Para obtener más información sobre la obtención masiva de filas, vea el artículo [conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [IsBOF](#isbof).  
  
##  <a name="movelast"></a>CRecordset::MoveLast  
 Convierte el primer registro en el último conjunto de filas completa el registro actual.  
  
```  
void MoveLast();
```  
  
### <a name="remarks"></a>Comentarios  
 Si no ha implementado la obtención masiva de filas, el conjunto de registros tiene un tamaño de conjunto de filas de 1, por lo que `MoveLast` simplemente se desplaza hasta el último registro en el conjunto de registros.  
  
> [!NOTE]
>  Esta función miembro no es válida para conjuntos de registros solo hacia delante.  
  
> [!NOTE]
>  Cuando se mueve a través de un conjunto de registros, no se puede omitir los registros eliminados. Consulte la [IsDeleted](#isdeleted) función de miembro para obtener más información.  
  
> [!CAUTION]
>  Llamar a cualquiera de los **mover** funciones produce una excepción si el conjunto de registros no tiene registros. Para determinar si el conjunto de registros tiene los registros, llame a `IsBOF` y `IsEOF`.  
  
> [!NOTE]
>  Si se llama a cualquiera de los **mover** funciona mientras el registro actual se actualiza o agregado, las actualizaciones se pierden sin previo aviso.  
  
 Para obtener más información sobre la navegación de conjunto de registros, vea los artículos [conjunto de registros: desplazamiento (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) y [conjunto de registros: marcadores y posiciones absolutas (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md). Para obtener más información sobre la obtención masiva de filas, vea el artículo [conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [IsBOF](#isbof).  
  
##  <a name="movenext"></a>CRecordset::MoveNext  
 Convierte el primer registro en el siguiente conjunto de filas del registro actual.  
  
```  
void MoveNext();
```  
  
### <a name="remarks"></a>Comentarios  
 Si no ha implementado la obtención masiva de filas, el conjunto de registros tiene un tamaño de conjunto de filas de 1, por lo que `MoveNext` simplemente se mueve al siguiente registro.  
  
> [!NOTE]
>  Cuando se mueve a través de un conjunto de registros, no se puede omitir los registros eliminados. Consulte la [IsDeleted](#isdeleted) función de miembro para obtener más información.  
  
> [!CAUTION]
>  Llamar a cualquiera de los **mover** funciones produce una excepción si el conjunto de registros no tiene registros. Para determinar si el conjunto de registros tiene los registros, llame a `IsBOF` y `IsEOF`.  
  
> [!NOTE]
>  También se recomienda llamar a `IsEOF` antes de llamar a `MoveNext`. Por ejemplo, si se ha desplazado más allá del final del conjunto de registros, `IsEOF` devolverá es distinto de cero; una llamada subsiguiente a `MoveNext` produciría una excepción.  
  
> [!NOTE]
>  Si se llama a cualquiera de los **mover** funciona mientras el registro actual se actualiza o agregado, las actualizaciones se pierden sin previo aviso.  
  
 Para obtener más información sobre la navegación de conjunto de registros, vea los artículos [conjunto de registros: desplazamiento (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) y [conjunto de registros: marcadores y posiciones absolutas (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md). Para obtener más información sobre la obtención masiva de filas, vea el artículo [conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [IsBOF](#isbof).  
  
##  <a name="moveprev"></a>CRecordset::MovePrev  
 Convierte el primer registro en el conjunto de filas anterior del registro actual.  
  
```  
void MovePrev();
```  
  
### <a name="remarks"></a>Comentarios  
 Si no ha implementado la obtención masiva de filas, el conjunto de registros tiene un tamaño de conjunto de filas de 1, por lo que `MovePrev` simplemente se mueve al registro anterior.  
  
> [!NOTE]
>  Esta función miembro no es válida para conjuntos de registros solo hacia delante.  
  
> [!NOTE]
>  Cuando se mueve a través de un conjunto de registros, no se puede omitir los registros eliminados. Consulte la [IsDeleted](#isdeleted) función de miembro para obtener más información.  
  
> [!CAUTION]
>  Llamar a cualquiera de los **mover** funciones produce una excepción si el conjunto de registros no tiene registros. Para determinar si el conjunto de registros tiene los registros, llame a `IsBOF` y `IsEOF`.  
  
> [!NOTE]
>  También se recomienda llamar a `IsBOF` antes de llamar a `MovePrev`. Por ejemplo, si se ha desplazado el comienzo del conjunto de registros, `IsBOF` devolverá es distinto de cero; una llamada subsiguiente a `MovePrev` produciría una excepción.  
  
> [!NOTE]
>  Si se llama a cualquiera de los **mover** funciona mientras el registro actual se actualiza o agregado, las actualizaciones se pierden sin previo aviso.  
  
 Para obtener más información sobre la navegación de conjunto de registros, vea los artículos [conjunto de registros: desplazamiento (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) y [conjunto de registros: marcadores y posiciones absolutas (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md). Para obtener más información sobre la obtención masiva de filas, vea el artículo [conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [IsBOF](#isbof).  
  
##  <a name="onsetoptions"></a>CRecordset::OnSetOptions  
 Se llama para establecer las opciones de (utilizados en la selección) para la instrucción ODBC especificada.  
  
```  
virtual void OnSetOptions(HSTMT hstmt);
```  
  
### <a name="parameters"></a>Parámetros  
 `hstmt`  
 El **HSTMT** de la instrucción ODBC cuyas opciones que se van a establecer.  
  
### <a name="remarks"></a>Comentarios  
 Llame a `OnSetOptions` para establecer las opciones (utilizados en la selección) de la instrucción ODBC especificada. El marco de trabajo llama a esta función miembro para establecer opciones iniciales para el conjunto de registros. `OnSetOptions`Determina la compatibilidad del origen de datos para los cursores desplazables y para la simultaneidad de cursor y establece opciones del conjunto de registros en consecuencia. (Mientras que `OnSetOptions` se utiliza para operaciones de selección, `OnSetUpdateOptions` se usa para las operaciones de actualización.)  
  
 Invalidar `OnSetOptions` para establecer las opciones específicas para el controlador o el origen de datos. Por ejemplo, si su origen de datos admite la apertura de obtener un acceso exclusivo, se podría invalidar `OnSetOptions` para aprovechar las ventajas de esa capacidad.  
  
 Para obtener más información acerca de los cursores, vea el artículo [ODBC](../../data/odbc/odbc-basics.md).  
  
##  <a name="onsetupdateoptions"></a>CRecordset::OnSetUpdateOptions  
 Se llama para establecer opciones de (que se usa en la actualización) de la instrucción ODBC especificada.  
  
```  
virtual void OnSetUpdateOptions(HSTMT hstmt);
```  
  
### <a name="parameters"></a>Parámetros  
 `hstmt`  
 El **HSTMT** de la instrucción ODBC cuyas opciones que se van a establecer.  
  
### <a name="remarks"></a>Comentarios  
 Llame a `OnSetUpdateOptions` para establecer las opciones (que se usa en la actualización) de la instrucción ODBC especificada. El marco de trabajo llama a esta función miembro después de crear un valor de HSTMT para actualizar los registros en un conjunto de registros. (Mientras que `OnSetOptions` se utiliza para operaciones de selección, `OnSetUpdateOptions` se usa para las operaciones de actualización.) `OnSetUpdateOptions` determina la compatibilidad del origen de datos para los cursores desplazables y para la simultaneidad de cursor y establece opciones del conjunto de registros en consecuencia.  
  
 Invalidar `OnSetUpdateOptions` para establecer las opciones de una instrucción ODBC antes de esa instrucción se utiliza para tener acceso a una base de datos.  
  
 Para obtener más información acerca de los cursores, vea el artículo [ODBC](../../data/odbc/odbc-basics.md).  
  
##  <a name="open"></a>CRecordset:: Open  
 Abre el conjunto de registros recuperando la tabla o realizando la consulta que el conjunto de registros representa.  
  
```  
virtual BOOL Open(
    UINT nOpenType = AFX_DB_USE_DEFAULT_TYPE,  
    LPCTSTR lpszSQL = NULL,  
    DWORD dwOptions = none);
```  
  
### <a name="parameters"></a>Parámetros  
 `nOpenType`  
 Acepte el valor predeterminado, **AFX_DB_USE_DEFAULT_TYPE**, o utilice uno de los siguientes valores en el **enumeración OpenType**:  
  
- **CRecordset:: dynaset** un conjunto de registros con desplazamiento bidireccional. La pertenencia y el orden de los registros se determinan cuando se abre el conjunto de registros, pero los cambios realizados por otros usuarios en los valores de datos son visibles después de una operación de recuperación de cambios. Los dynasets también se conocen como conjuntos de registros conjunto controlados por conjuntos de claves.  
  
- **CRecordset:: Snapshot** un conjunto de registros estático con desplazamiento bidireccional. La pertenencia y el orden de los registros se determinan cuando se abre el conjunto de registros; los valores de datos se determinan cuando se buscan los registros. Los cambios realizados por otros usuarios no son visibles hasta que no se cierra y se vuelve a abrir el conjunto de registros.  
  
- **CRecordset:: Dynamic** un conjunto de registros con desplazamiento bidireccional. Los cambios realizados por otros usuarios en la pertenencia, el orden y los valores de datos son visibles después de una operación de recuperación de cambios. Tenga en cuenta que muchos controladores ODBC no admiten este tipo de conjunto de registros.  
  
- **CRecordset:: forwardOnly** un conjunto de registros de solo lectura con desplazamiento solo hacia delante.  
  
     Para `CRecordset`, el valor predeterminado es **CRecordset:: Snapshot**. El mecanismo de valor predeterminado permite que los asistentes de Visual C++ interactúen con `CRecordset` de ODBC y `CDaoRecordset` de DAO, que tienen valores predeterminados diferentes.  
  
 Para obtener más información acerca de estos tipos de conjunto de registros, vea el artículo [conjunto de registros (ODBC)](../../data/odbc/recordset-odbc.md). Para obtener información relacionada, vea el artículo sobre el uso de cursores de bloque y desplazables en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
> [!CAUTION]
>  Si el tipo solicitado no se admite, el marco de trabajo produce una excepción.  
  
 `lpszSQL`  
 Puntero de cadena que contiene uno de los elementos siguientes:  
  
-   A **NULL** puntero.  
  
-   Nombre de una tabla.  
  
-   Una instancia de SQL **seleccione** instrucción (opcionalmente con una instancia de SQL **donde** o **ORDER BY** cláusula).  
  
-   A **llamar** instrucción especificando el nombre de una consulta predefinida (procedimiento almacenado). Tenga cuidado de no insertar espacios en blanco entre la llave y el **llamar a** (palabra clave).  
  
 Para obtener más información sobre esta cadena, vea la tabla y la descripción del rol de ClassWizard en Comentarios.  
  
> [!NOTE]
>  El orden de las columnas en el conjunto de resultados debe coincidir con el orden de lo RFX o RFX masivo función llama de su [DoFieldExchange](#dofieldexchange) o [DoBulkFieldExchange](#dobulkfieldexchange) función invalidación.  
  
 `dwOptions`  
 Máscara de bits que puede especificar una combinación de los valores que se muestran a continuación. Algunas de estas opciones son mutuamente excluyentes. El valor predeterminado es **ninguno**.  
  
- **CRecordset:: None** ningún conjunto de opciones. Este valor del parámetro es mutuamente excluyente con todos los demás valores. De forma predeterminada, se puede actualizar el conjunto de registros con [editar](#edit) o [eliminar](#delete) y permite anexar nuevos registros con [AddNew](#addnew). La capacidad de actualización depende del origen de datos y de la opción de `nOpenType` que se especifique. La optimización para adiciones masivas no está disponible. La obtención masiva de filas no se implementará. Los registros eliminados no se omitirán al navegar por el conjunto de registros. Los marcadores no están disponibles. Se implementa la comprobación automática de campos modificados.  
  
- **CRecordset:: AppendOnly** no permiten **editar** o **eliminar** en el conjunto de registros. Solo permite `AddNew`. Esta opción es mutuamente excluyente con **CRecordset:: ReadOnly**.  
  
- **CRecordset:: ReadOnly** abrir el conjunto de registros como de solo lectura. Esta opción es mutuamente excluyente con **CRecordset:: AppendOnly**.  
  
- **CRecordset:: optimizeBulkAdd** usar una instrucción SQL preparada para optimizar la adición de muchos registros al mismo tiempo. Solo se aplica si no se usa la función de API de ODBC **SQLSetPos** para actualizar el conjunto de registros. La primera actualización determina qué campos se marcan como modificados. Esta opción es mutuamente excluyente con `CRecordset::useMultiRowFetch`.  
  
- `CRecordset::useMultiRowFetch`Implementar la obtención masiva de filas para permitir que varias filas en una única operación de búsqueda. Se trata de una característica avanzada diseñada para mejorar el rendimiento; sin embargo, el Asistente para clases no admite el intercambio masivo de campos de registros. Esta opción es mutuamente excluyente con **CRecordset:: optimizeBulkAdd**. Tenga en cuenta que si especifica `CRecordset::useMultiRowFetch`, a continuación, la opción **CRecordset:: noDirtyFieldCheck** se activará automáticamente (almacenamiento en búfer doble no estará disponible); de solo avance conjuntos de registros, la opción **CRecordset:: useExtendedFetch** se activará automáticamente. Para obtener más información sobre la obtención masiva de filas, vea el artículo [conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
- **CRecordset:: skipDeletedRecords** omitir todos los registros eliminados al navegar por el conjunto de registros. Esto ralentiza el rendimiento en ciertas búsquedas relativas. Esta opción no es válida en los conjuntos de registros solo hacia delante. Si se llama a [mover](#move) con el `nRows` parámetro establecido en 0 y el **skipDeletedRecords** establecida, la opción **mover** producirá una aserción. Tenga en cuenta que **skipDeletedRecords** es similar a *empaquetado de controladores*, lo que significa que las filas eliminadas se quita del conjunto de registros. Sin embargo, si el controlador empaqueta registros, solo se omitirán los registros que elimine; no se omitirán los registros eliminados por otros usuarios mientras el conjunto de registros está abierto. **CRecordset:: skipDeletedRecords** omitirá las filas eliminadas por otros usuarios.  
  
- **CRecordset:: useBookmarks** puede utilizar marcadores en el conjunto de registros, si se admite. Los marcadores ralentizan la recuperación de datos pero mejoran el rendimiento de la navegación de datos. No es válida en conjuntos de registros solo hacia delante. Para obtener más información, vea el artículo [conjunto de registros: marcadores y posiciones absolutas (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md).  
  
- **CRecordset:: noDirtyFieldCheck** desactive la opción automática de campos modificados comprobación (almacenamiento en búfer doble). Esto mejorará el rendimiento; sin embargo, para marcar manualmente los campos como modificados se debe llamar a las funciones miembro `SetFieldDirty` y `SetFieldNull`. Tenga en cuenta que el almacenamiento en búfer doble en la clase `CRecordset` es similar al almacenamiento en búfer doble en la clase `CDaoRecordset`. Sin embargo, en `CRecordset`, no se puede habilitar el almacenamiento en búfer doble en campos individuales; hay que habilitarlo o deshabilitarlo para todos los campos. Tenga en cuenta que si especifica la opción `CRecordset::useMultiRowFetch`, a continuación, **CRecordset:: noDirtyFieldCheck** se activará automáticamente; sin embargo, `SetFieldDirty` y `SetFieldNull` no se puede utilizar en conjuntos de registros que implementan la obtención masiva de filas.  
  
- **CRecordset:: Executedirect** no utiliza una instrucción SQL preparada. Para mejorar el rendimiento, especifique esta opción si la **Requery** nunca se llamará a función miembro.  
  
- **CRecordset:: useExtendedFetch** implemente **SQLExtendedFetch** en lugar de **SQLFetch**. Está diseñado para implementar la obtención masiva de filas en conjuntos de registros solo hacia delante. Si especifica la opción `CRecordset::useMultiRowFetch` en un solo avance y solo conjunto de registros, a continuación, **CRecordset:: useExtendedFetch** se activará automáticamente.  
  
- **CRecordset:: userAllocMultiRowBuffers** el usuario asignará búferes de almacenamiento para los datos. Utilice esta opción junto con `CRecordset::useMultiRowFetch` si desea asignar su propio almacenamiento; de lo contrario, el marco de trabajo asignará automáticamente el almacenamiento necesario. Para obtener más información, vea el artículo [conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md). Tenga en cuenta que si se especifica **CRecordset:: userAllocMultiRowBuffers** sin especificar `CRecordset::useMultiRowFetch` dará como resultado un error de aserción.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si la `CRecordset` objeto se abrió correctamente; en caso contrario 0 si [CDatabase:: Open](../../mfc/reference/cdatabase-class.md#open) (si se llama) devuelve 0.  
  
### <a name="remarks"></a>Comentarios  
 Se debe llamar a esta función miembro para ejecutar la consulta definida por el conjunto de registros. Antes de llamar a **abiertos**, debe crear el objeto de conjunto de registros.  
  
 Conexión de este conjunto de registros al origen de datos depende de cómo se crea el conjunto de registros antes de llamar a **abiertos**. Si se pasa un [CDatabase](../../mfc/reference/cdatabase-class.md) de objeto para el constructor de conjunto de registros que no se ha conectado al origen de datos, esta función miembro utiliza [GetDefaultConnect](#getdefaultconnect) para intentar abrir el objeto de base de datos. Si se pasa **NULL** al constructor del conjunto de registros, el constructor crea un `CDatabase` objeto automáticamente, y **abiertos** intenta conectar el objeto de base de datos. Para obtener más información sobre cómo cerrar el conjunto de registros y la conexión en estas circunstancias variables, consulte [cerrar](#close).  
  
> [!NOTE]
>  El acceso a un origen de datos mediante un objeto `CRecordset` siempre es compartido. A diferencia de la clase `CDaoRecordset`, no se puede utilizar un objeto `CRecordset` para abrir un origen de datos con acceso exclusivo.  
  
 Cuando se llama a **abiertos**, una consulta, normalmente una instancia de SQL **seleccione** (instrucción), selecciona los registros en función de criterios que se muestran en la tabla siguiente.  
  
|Valor del parámetro lpszSQL|Los registros seleccionados están determinados por|Ejemplo|  
|------------------------------------|----------------------------------------|-------------|  
|**ES NULL**|La cadena devuelta por `GetDefaultSQL`.||  
|Nombre de tabla SQL|Todas las columnas de la lista de tablas de `DoFieldExchange` o `DoBulkFieldExchange`.|`"Customer"`|  
|Nombre de la consulta (procedimiento almacenado) predefinida|Las columnas de la consulta cuya devolución se ha definido.|`"{call OverDueAccts}"`|  
|**Seleccione** lista de columnas **FROM** lista de tablas|Las columnas especificadas de las tablas indicadas.|`"SELECT CustId, CustName FROM`<br /><br /> `Customer"`|  
  
> [!CAUTION]
>  Tenga cuidado de no insertar espacios en blanco adicionales en la cadena SQL. Por ejemplo, si inserta un espacio en blanco entre la llave y el **llamar a** (palabra clave), MFC se incorrectamente la cadena SQL como un nombre de tabla y se incorporará a una **seleccione** instrucción, lo que dará lugar a que se produzca una excepción. De forma similar, si la consulta predefinida utiliza un parámetro de salida, no inserte un espacio en blanco entre la llave y el "símbolo. Por último, no se debe insertar un espacio en blanco antes de la llave en un **llamar a** instrucción o antes de la **seleccione** palabra clave en un **seleccione** instrucción.  
  
 El procedimiento habitual consiste en pasar **NULL** a **abiertos**; en este caso, **abiertos** llamadas [GetDefaultSQL](#getdefaultsql). Si utilizas un derivada `CRecordset` (clase), **GetDefaultSQL** proporciona los nombres de tabla que especificó en el Asistente para. Se puede especificar otra información en el parámetro `lpszSQL`.  
  
 Cualquier valor que pase, **abiertos** construye una cadena SQL final para la consulta (la cadena puede tener SQL **donde** y **ORDER BY** anexadas cláusulas para el `lpszSQL` cadena pasó) y, a continuación, ejecuta la consulta. Puede examinar la cadena construida mediante una llamada a [GetSQL](#getsql) después de llamar a **abiertos**. Para obtener más detalles acerca de cómo el conjunto de registros crea una instrucción SQL y selecciona los registros, vea el artículo [conjunto de registros: cómo se seleccionan los registros (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md).  
  
 Los miembros de datos de campo de la clase de conjunto de registros están enlazados a las columnas de los datos seleccionados. Si se devuelve algún registro, el primer registro se convierte en el registro actual.  
  
 Si desea establecer opciones para el conjunto de registros, por ejemplo, un filtro o una ordenación, especificarlos después de crear el objeto de conjunto de registros, pero antes de llamar a **abiertos**. Si desea que los registros del conjunto de registros después de actualizar el conjunto de registros está abierto, llame a [Requery](#requery).  
  
 Para obtener más información, incluidos ejemplos adicionales, vea los artículos [conjunto de registros (ODBC)](../../data/odbc/recordset-odbc.md), [conjunto de registros: cómo se seleccionan los registros (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md), y [conjunto de registros: crear y cerrar conjuntos de registros (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md).  
  
### <a name="example"></a>Ejemplo  
 Ejemplos de código siguientes muestran distintas formas de la **abiertos** llamar.  
  
 [!code-cpp[NVC_MFCDatabase Nº 16](../../mfc/codesnippet/cpp/crecordset-class_15.cpp)]  
  
##  <a name="refreshrowset"></a>CRecordset::RefreshRowset  
 Actualiza los datos y el estado de una fila en el conjunto de filas actual.  
  
```  
void RefreshRowset(
    WORD wRow,  
    WORD wLockType = SQL_LOCK_NO_CHANGE);
```  
  
### <a name="parameters"></a>Parámetros  
 `wRow`  
 La posición basada en uno de una fila en el conjunto de filas actual. Este valor puede estar comprendido entre cero y el tamaño del conjunto de filas.  
  
 `wLockType`  
 Un valor que indica cómo bloquear la fila una vez que se haya actualizado. Para conocer más detalles, vea la sección Comentarios.  
  
### <a name="remarks"></a>Comentarios  
 Si se pasa un valor de cero para `wRow`, a continuación, se actualizarán todas las filas del conjunto de filas.  
  
 Usar `RefreshRowset`, debe ha implementado la obtención masiva de filas mediante la especificación de la **CRecordset::useMulitRowFetch** opción en el [abiertos](#open) función miembro.  
  
 `RefreshRowset`llama a la función API de ODBC **SQLSetPos**. El `wLockType` parámetro especifica el estado de bloqueo de la fila después de **SQLSetPos** se ha ejecutado. La tabla siguiente describen los posibles valores para `wLockType`.  
  
|wLockType|Descripción|  
|---------------|-----------------|  
|`SQL_LOCK_NO_CHANGE`(el valor predeterminado)|El controlador u origen de datos se asegura de que la fila está en el mismo estado bloqueado o desbloqueado tal como estaba antes de `RefreshRowset` se llamó.|  
|`SQL_LOCK_EXCLUSIVE`|El controlador u origen de datos bloquea la fila de forma exclusiva. No todos los orígenes de datos admiten este tipo de bloqueo.|  
|`SQL_LOCK_UNLOCK`|El controlador u origen de datos desbloquea la fila. No todos los orígenes de datos admiten este tipo de bloqueo.|  
  
 Para obtener más información acerca de **SQLSetPos**, consulte el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]. Para obtener más información sobre la obtención masiva de filas, vea el artículo [conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
##  <a name="requery"></a>CRecordset:: Requery  
 (Las actualizaciones) se vuelve a generar un conjunto de registros.  
  
```  
virtual BOOL Requery();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el conjunto de registros se ha vuelto a generar correctamente; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 Si se devuelve algún registro, el primer registro se convierte en el registro actual.  
  
 En orden para el conjunto de registros reflejar las adiciones y eliminaciones realizados por usted u otros usuarios en el origen de datos, debe volver a crear el conjunto de registros mediante una llamada a **Requery**. Si el conjunto de registros es un conjunto de registros dinámicos, refleja automáticamente las actualizaciones que usted u otros usuarios realicen en sus registros existentes (pero no las adiciones). Si el conjunto de registros es una instantánea, debe llamar a **Requery** para reflejar modificaciones realizadas por otros usuarios, así como las adiciones y eliminaciones.  
  
 Para un conjunto de registros dinámicos o en una instantánea, llame a **Requery** siempre que desee volver a generar el conjunto de registros con un nuevo filtro o de ordenación o de nuevos valores de parámetro. Establezca la nueva propiedad filtrar u ordenar asignando nuevos valores a **m_strFilter** y `m_strSort` antes de llamar a **Requery**. Definir nuevos parámetros asignando nuevos valores a los miembros de datos de parámetro antes de llamar a **Requery**. Si se modifican las cadenas de filtro y ordenación, puede volver a la consulta, lo que mejora el rendimiento.  
  
 Si se produce un error en el intento de volver a generar el conjunto de registros, se cierra el conjunto de registros. Antes de llamar a **Requery**, puede determinar si el conjunto de registros puede realizar una nueva consulta mediante una llamada a la `CanRestart` función miembro. `CanRestart`no garantiza que **Requery** se realizará correctamente.  
  
> [!CAUTION]
>  Llame a **Requery** sólo después de haber llamado [abiertos](#open).  
  
### <a name="example"></a>Ejemplo  
 En este ejemplo se vuelve a generar un conjunto de registros para aplicar un criterio de ordenación diferente.  
  
 [!code-cpp[NVC_MFCDatabase #29](../../mfc/codesnippet/cpp/crecordset-class_16.cpp)]  
  
##  <a name="setabsoluteposition"></a>CRecordset:: SetAbsolutePosition  
 El conjunto de registros se coloca en el registro correspondiente al número de registro especificado.  
  
```  
void SetAbsolutePosition(long nRows);
```  
  
### <a name="parameters"></a>Parámetros  
 `nRows`  
 Basado en una posición ordinal para el registro actual en el conjunto de registros.  
  
### <a name="remarks"></a>Comentarios  
 `SetAbsolutePosition`Mueve el puntero de registro actual basándose en esta posición ordinal.  
  
> [!NOTE]
>  Esta función miembro no es válida en conjuntos de registros solo hacia delante.  
  
 Conjuntos de registros ODBC, una configuración de la posición absoluta de 1 hace referencia al primer registro en el conjunto de registros; un valor de 0 hace referencia a la posición de inicio del archivo (BOF).  
  
 También puede pasar valores negativos para `SetAbsolutePosition`. En este caso se evalúa la posición del conjunto de registros desde el final del conjunto de registros. Por ejemplo, `SetAbsolutePosition( -1 )` mueve el puntero de registro actual al último registro en el conjunto de registros.  
  
> [!NOTE]
>  Posición absoluta no está pensada para usarse como un número de registro suplente. Marcadores siguen siendo la forma recomendada de retener y volver a una posición determinada, desde que se cambia de posición de un registro cuando se eliminan registros anteriores. Además, usted no puede estar seguro que un determinado registro tendrá la misma posición absoluta si se vuelve a crear el conjunto de registros, porque no se garantiza el orden de los registros individuales dentro de un conjunto de registros, a menos que se crea con una instrucción SQL que usa un **ORDER BY** cláusula.  
  
 Para obtener más información acerca de la navegación de conjunto de registros y los marcadores, vea los artículos [conjunto de registros: desplazamiento (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) y [conjunto de registros: marcadores y posiciones absolutas (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md).  
  
##  <a name="setbookmark"></a>CRecordset::SetBookmark  
 El conjunto de registros se coloca en el registro que contiene el marcador especificado.  
  
```  
void SetBookmark(const CDBVariant& varBookmark);
```  
  
### <a name="parameters"></a>Parámetros  
 `varBookmark`  
 Una referencia a un [CDBVariant](../../mfc/reference/cdbvariant-class.md) objeto que contiene el valor de marcador para un registro específico.  
  
### <a name="remarks"></a>Comentarios  
 Para determinar si se admiten marcadores en el conjunto de registros, llame a [CanBookmark](#canbookmark). Para disponer de marcadores si son compatibles, debe establecer el **CRecordset:: useBookmarks** opción en el `dwOptions` parámetro de la [abiertos](#open) función miembro.  
  
> [!NOTE]
>  Si los marcadores son no compatible o no está disponible, la llamada a `SetBookmark` se producirá una excepción. No se admiten marcadores en conjuntos de registros solo hacia delante.  
  
 Para recuperar primero el marcador para el registro actual, llame a [GetBookmark](#getbookmark), que guarda el valor de marcador a un `CDBVariant` objeto. Más adelante, puede volver a ese registro mediante una llamada a `SetBookmark` con el valor de marcador guardado.  
  
> [!NOTE]
>  Después de ciertas operaciones de conjunto de registros, debe comprobar la persistencia de marcador antes de llamar a `SetBookmark`. Por ejemplo, si recupera un marcador con `GetBookmark` y, a continuación, llame a **Requery**, el marcador puede no ser válido. Llame a [CDatabase:: GetBookmarkPersistence](../../mfc/reference/cdatabase-class.md#getbookmarkpersistence) para comprobar si puede llamar con seguridad a `SetBookmark`.  
  
 Para obtener más información acerca de los marcadores y la navegación de conjunto de registros, vea los artículos [conjunto de registros: marcadores y posiciones absolutas (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md) y [conjunto de registros: desplazamiento (ODBC)](../../data/odbc/recordset-scrolling-odbc.md).  
  
##  <a name="setfielddirty"></a>CRecordset::SetFieldDirty  
 Marca a un miembro de datos de campo del conjunto de registros como modificada o como sin cambios.  
  
```  
void SetFieldDirty(void* pv, BOOL bDirty = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 `pv`  
 Contiene la dirección de un miembro de datos de campo del conjunto de registros o **NULL**. Si **NULL**, se marcan todos los miembros de datos de campo del conjunto de registros. (C++ **NULL** no es igual a Null en la terminología de base de datos, lo que significa "no tener ningún valor.")  
  
 `bDirty`  
 **TRUE** si es miembro de datos del campo se marca como "dirty" (modificado). En caso contrario, **FALSE** si es miembro de datos del campo se marca como "limpiar" (sin cambios).  
  
### <a name="remarks"></a>Comentarios  
 Marcar campos como sin cambios, se garantiza el campo no se actualiza y da como resultado menos tráfico SQL.  
  
> [!NOTE]
>  Esta función miembro no es aplicable en conjuntos de registros que están usando la obtención masiva de filas. Si ha implementado obtención masiva de filas, a continuación, `SetFieldDirty` dará como resultado un error de aserción. Para obtener más información sobre la obtención masiva de filas, vea el artículo [conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Las marcas de framework cambiar los miembros de datos de campo para asegurarse de que se escribirán en el registro en el origen de datos mediante el mecanismo de campos de registros (RFX) de exchange. Cambiar el valor de un campo normalmente establece el campo desfasadas automáticamente, por lo que rara vez deberá llamar a `SetFieldDirty` usted mismo, pero a veces, conviene asegurarse de que las columnas se explícitamente actualiza o inserta independientemente de qué valor se encuentra en el miembro de datos de campo.  
  
> [!CAUTION]
>  Llame a esta función miembro solo después de haber llamado [editar](#edit) o [AddNew](#addnew).  
  
 Usar **NULL** para el primer argumento de la función aplicará únicamente a la función **outputColumn** campos, no **param** campos. Por ejemplo, la llamada  
  
 [!code-cpp[26 de # NVC_MFCDatabase](../../mfc/codesnippet/cpp/crecordset-class_10.cpp)]  
  
 establecerá solo **outputColumn** campos a **NULL**; **param** campos no se verá afectados.  
  
 Para que funcione en **param** campos, debe proporcionar la dirección real de la persona **param** que desea trabajar en ella, como:  
  
 [!code-cpp[NVC_MFCDatabase #27](../../mfc/codesnippet/cpp/crecordset-class_11.cpp)]  
  
 Esto significa que no se puede establecer todos los **param** campos a **NULL**, tal y como se haría con **outputColumn** campos.  
  
##  <a name="setfieldnull"></a>CRecordset::SetFieldNull  
 Marca a un miembro de datos de campo del conjunto de registros como Null (específicamente no tener ningún valor) o como no Null.  
  
```  
void SetFieldNull(void* pv, BOOL bNull = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 `pv`  
 Contiene la dirección de un miembro de datos de campo del conjunto de registros o **NULL**. Si **NULL**, se marcan todos los miembros de datos de campo del conjunto de registros. (C++ **NULL** no es igual a Null en la terminología de base de datos, lo que significa "no tener ningún valor.")  
  
 `bNull`  
 Es distinto de cero si el miembro de datos de campo está marcado como si tuviera ningún valor (Null). 0 en caso contrario, si el miembro de datos de campo está marcado como no Null.  
  
### <a name="remarks"></a>Comentarios  
 Cuando se agrega un nuevo registro a un conjunto de registros, todos los miembros de datos de campo se establecen en un valor Null inicialmente y se marca como "dirty" (modificado). Cuando recupera un registro de un origen de datos, sus columnas ya tienen valores o son Null.  
  
> [!NOTE]
>  No llame a esta función miembro en conjuntos de registros que están usando la obtención masiva de filas. Si ha implementado la obtención masiva de filas, una llamada a `SetFieldNull` da como resultado un error de aserción. Para obtener más información sobre la obtención masiva de filas, vea el artículo [conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Si desea específicamente designar un campo del registro actual que no tiene un valor, llame a `SetFieldNull` con `bNull` establecido en **TRUE** para marcar como Null. Si previamente se marcó un campo Null y ahora desea asignarle un valor, basta con establecer su nuevo valor. No tiene que quitar la marca de Null con `SetFieldNull`. Para determinar si el campo puede ser Null, llame a `IsFieldNullable`.  
  
> [!CAUTION]
>  Llame a esta función miembro solo después de haber llamado [editar](#edit) o [AddNew](#addnew).  
  
 Usar **NULL** para el primer argumento de la función aplicará únicamente a la función **outputColumn** campos, no **param** campos. Por ejemplo, la llamada  
  
 [!code-cpp[26 de # NVC_MFCDatabase](../../mfc/codesnippet/cpp/crecordset-class_10.cpp)]  
  
 establecerá solo **outputColumn** campos a **NULL**; **param** campos no se verá afectados.  
  
 Para que funcione en **param** campos, debe proporcionar la dirección real de la persona **param** que desea trabajar en ella, como:  
  
 [!code-cpp[NVC_MFCDatabase #27](../../mfc/codesnippet/cpp/crecordset-class_11.cpp)]  
  
 Esto significa que no se puede establecer todos los **param** campos a **NULL**, tal y como se haría con **outputColumn** campos.  
  
> [!NOTE]
>  Al establecer los parámetros con valores Null, una llamada a `SetFieldNull` antes de que el conjunto de registros está abiertos resultados en una aserción. En este caso, llame a [SetParamNull](#setparamnull).  
  
 `SetFieldNull`se implementa a través de [DoFieldExchange](#dofieldexchange).  
  
##  <a name="setlockingmode"></a>CRecordset::SetLockingMode  
 Establece el modo de bloqueo "optimista" bloquear (predeterminado) o de bloqueo "pesimista". Determina cómo se bloquean los registros para las actualizaciones.  
  
```  
void SetLockingMode(UINT nMode);
```  
  
### <a name="parameters"></a>Parámetros  
 `nMode`  
 Contiene uno de los siguientes valores de la **enum LockMode**:  
  
- **optimista** bloqueo optimista bloquea el registro que se actualiza solo durante la llamada a **actualización**.  
  
- **pesimista** el bloqueo pesimista bloquea el registro en cuanto **editar** se llama y los mantiene bloqueada hasta que el **actualización** llamada completa o se mueve a un nuevo registro.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función miembro si tiene que especificar cuál de las dos estrategias de bloqueo de registros es usar el conjunto de registros para las actualizaciones. De forma predeterminada, el modo de bloqueo de un conjunto de registros es **optimista**. Se puede cambiar a una más cuidado **pesimista** estrategia de bloqueo. Llame a `SetLockingMode` después de crear y abrir el objeto de conjunto de registros, pero antes de llamar a **editar**.  
  
##  <a name="setparamnull"></a>CRecordset::SetParamNull  
 Marca un parámetro como Null (específicamente no tener ningún valor) o como no Null.  
  
```  
void SetParamNull(
    int nIndex,  
    BOOL bNull = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 Índice de base cero del parámetro.  
  
 `bNull`  
 Si **TRUE** (el valor predeterminado), el parámetro se marca como Null. En caso contrario, el parámetro se marca como no Null.  
  
### <a name="remarks"></a>Comentarios  
 A diferencia de [SetFieldNull](#setfieldnull), puede llamar a `SetParamNull` antes de que ha abierto el conjunto de registros.  
  
 `SetParamNull`se suele utilizar con consultas predefinidas (procedimientos almacenados).  
  
##  <a name="setrowsetcursorposition"></a>CRecordset::SetRowsetCursorPosition  
 Mueve el cursor a una fila en el conjunto de filas actual.  
  
```  
void SetRowsetCursorPosition(WORD wRow, WORD wLockType = SQL_LOCK_NO_CHANGE);
```  
  
### <a name="parameters"></a>Parámetros  
 `wRow`  
 La posición basada en uno de una fila en el conjunto de filas actual. Este valor puede oscilar entre 1 y el tamaño del conjunto de filas.  
  
 `wLockType`  
 Valor que indica cómo bloquear la fila una vez que se haya actualizado. Para conocer más detalles, vea la sección Comentarios.  
  
### <a name="remarks"></a>Comentarios  
 Al implementar la obtención masiva de filas, los registros se recuperan mediante conjuntos de filas, donde el primer registro en el conjunto de filas capturada es el registro actual. Para realizar otro registro en el conjunto de filas en el registro actual, llame a `SetRowsetCursorPosition`. Por ejemplo, puede combinar `SetRowsetCursorPosition` con el [GetFieldValue](#getfieldvalue) función miembro para recuperar dinámicamente los datos de todos los registros del conjunto de registros.  
  
 Usar `SetRowsetCursorPosition`, debe ha implementado la obtención masiva de filas mediante la especificación de la `CRecordset::useMultiRowFetch` opción de la `dwOptions` parámetro en el [abiertos](#open) función miembro.  
  
 `SetRowsetCursorPosition`llama a la función API de ODBC **SQLSetPos**. El `wLockType` parámetro especifica el estado de bloqueo de la fila después de **SQLSetPos** se ha ejecutado. La tabla siguiente describen los posibles valores para `wLockType`.  
  
|wLockType|Descripción|  
|---------------|-----------------|  
|`SQL_LOCK_NO_CHANGE`(el valor predeterminado)|El controlador u origen de datos se asegura de que la fila está en el mismo estado bloqueado o desbloqueado tal como estaba antes de `SetRowsetCursorPosition` se llamó.|  
|`SQL_LOCK_EXCLUSIVE`|El controlador u origen de datos bloquea la fila de forma exclusiva. No todos los orígenes de datos admiten este tipo de bloqueo.|  
|`SQL_LOCK_UNLOCK`|El controlador u origen de datos desbloquea la fila. No todos los orígenes de datos admiten este tipo de bloqueo.|  
  
 Para obtener más información acerca de **SQLSetPos**, consulte el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]. Para obtener más información sobre la obtención masiva de filas, vea el artículo [conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
##  <a name="setrowsetsize"></a>CRecordset::SetRowsetSize  
 Especifica el número de registros que se va a recuperar durante una búsqueda.  
  
```  
virtual void SetRowsetSize(DWORD dwNewRowsetSize);
```  
  
### <a name="parameters"></a>Parámetros  
 *dwNewRowsetSize*  
 El número de filas que desea recuperar durante una operación de obtención determinada.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro virtual especifica el número de filas que se va a recuperar durante una sola operación de obtención al utilizar la obtención masiva de filas. Para implementar la obtención masiva de filas, debe establecer el `CRecordset::useMultiRowFetch` opción en el `dwOptions` parámetro de la [abiertos](#open) función miembro.  
  
> [!NOTE]
>  Al llamar a `SetRowsetSize` sin necesidad de implementar de forma masiva la obtención de filas dará como resultado un error de aserción.  
  
 Llame a `SetRowsetSize` antes de llamar a **abiertos** establecer inicialmente el tamaño del conjunto de filas para el conjunto de registros. El tamaño del conjunto de filas de forma predeterminada al implementar la obtención masiva de filas es 25.  
  
> [!NOTE]
>  Tenga cuidado al llamar a `SetRowsetSize`. Si está asignando manualmente almacenamiento para los datos (según lo especificado por el **CRecordset:: userAllocMultiRowBuffers** opción del parámetro dwOptions en **abiertos**), debe comprobar si debe reasignar estos búferes de almacenamiento después de llamar a `SetRowsetSize`, pero antes de realizar cualquier operación de desplazamiento de cursor.  
  
 Para obtener la configuración actual para el tamaño del conjunto de filas, llame a [GetRowsetSize](#getrowsetsize).  
  
 Para obtener más información sobre la obtención masiva de filas, vea el artículo [conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
##  <a name="update"></a>CRecordset:: Update  
 Completa una `AddNew` o **editar** operación guardando los datos nuevos o modificados del origen de datos.  
  
```  
virtual BOOL Update();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si se actualizó correctamente un registro; en caso contrario es 0 si no hay columnas han cambiado. Si se actualizó ningún registro, o si hay más de un registro se actualizó, se produce una excepción. También se produce una excepción para cualquier otro error en el origen de datos.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función miembro después de llamar a la [AddNew](#addnew) o [editar](#edit) función miembro. Esta llamada es necesario para completar la `AddNew` o **editar** operación.  
  
> [!NOTE]
>  Si ha implementado la obtención masiva de filas, no se puede llamar **actualización**. Esto producirá un error de aserción. Aunque clase `CRecordset` no proporciona un mecanismo para actualizar filas masivas de datos, puede escribir sus propias funciones mediante la función API de ODBC **SQLSetPos**. Para obtener más información sobre la obtención masiva de filas, vea el artículo [conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Ambos `AddNew` y **editar** preparar un búfer de edición en la que se colocan los datos agregados o editados para guardar datos en el origen de datos. **Actualización** guarda los datos. Se actualizan solo esos campos marcados o detectado como modificada.  
  
 Si el origen de datos admite transacciones, puede realizar la **actualización** llamar a (y su correspondiente `AddNew` o **editar** llamar) forma parte de una transacción. Para obtener más información acerca de las transacciones, vea el artículo [transacción (ODBC)](../../data/odbc/transaction-odbc.md).  
  
> [!CAUTION]
>  Si se llama a **actualización** sin primero una llamada a `AddNew` o **editar**, **actualización** produce una `CDBException`. Si se llama a `AddNew` o **editar**, debe llamar a **actualización** antes de llamar a un **mover** operación o antes de cerrar el conjunto de registros o la conexión de origen de datos. En caso contrario, los cambios se pierden sin notificación.  
  
 Para obtener más información sobre el control de **actualización** errores, vea el artículo [conjunto de registros: actualizar los registros (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md).  
  
### <a name="example"></a>Ejemplo  
 Vea el artículo [transacción: realizar una transacción en un conjunto de registros (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md).  
  
## <a name="see-also"></a>Vea también  
 [CObject (clase)](../../mfc/reference/cobject-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CDatabase (clase)](../../mfc/reference/cdatabase-class.md)   
 [CRecordView (clase)](../../mfc/reference/crecordview-class.md)

