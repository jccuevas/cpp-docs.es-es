---
title: Clase CDaoRecordset
ms.date: 08/27/2018
f1_keywords:
- CDaoRecordset
- AFXDAO/CDaoRecordset
- AFXDAO/CDaoRecordset::CDaoRecordset
- AFXDAO/CDaoRecordset::AddNew
- AFXDAO/CDaoRecordset::CanAppend
- AFXDAO/CDaoRecordset::CanBookmark
- AFXDAO/CDaoRecordset::CancelUpdate
- AFXDAO/CDaoRecordset::CanRestart
- AFXDAO/CDaoRecordset::CanScroll
- AFXDAO/CDaoRecordset::CanTransact
- AFXDAO/CDaoRecordset::CanUpdate
- AFXDAO/CDaoRecordset::Close
- AFXDAO/CDaoRecordset::Delete
- AFXDAO/CDaoRecordset::DoFieldExchange
- AFXDAO/CDaoRecordset::Edit
- AFXDAO/CDaoRecordset::FillCache
- AFXDAO/CDaoRecordset::Find
- AFXDAO/CDaoRecordset::FindFirst
- AFXDAO/CDaoRecordset::FindLast
- AFXDAO/CDaoRecordset::FindNext
- AFXDAO/CDaoRecordset::FindPrev
- AFXDAO/CDaoRecordset::GetAbsolutePosition
- AFXDAO/CDaoRecordset::GetBookmark
- AFXDAO/CDaoRecordset::GetCacheSize
- AFXDAO/CDaoRecordset::GetCacheStart
- AFXDAO/CDaoRecordset::GetCurrentIndex
- AFXDAO/CDaoRecordset::GetDateCreated
- AFXDAO/CDaoRecordset::GetDateLastUpdated
- AFXDAO/CDaoRecordset::GetDefaultDBName
- AFXDAO/CDaoRecordset::GetDefaultSQL
- AFXDAO/CDaoRecordset::GetEditMode
- AFXDAO/CDaoRecordset::GetFieldCount
- AFXDAO/CDaoRecordset::GetFieldInfo
- AFXDAO/CDaoRecordset::GetFieldValue
- AFXDAO/CDaoRecordset::GetIndexCount
- AFXDAO/CDaoRecordset::GetIndexInfo
- AFXDAO/CDaoRecordset::GetLastModifiedBookmark
- AFXDAO/CDaoRecordset::GetLockingMode
- AFXDAO/CDaoRecordset::GetName
- AFXDAO/CDaoRecordset::GetParamValue
- AFXDAO/CDaoRecordset::GetPercentPosition
- AFXDAO/CDaoRecordset::GetRecordCount
- AFXDAO/CDaoRecordset::GetSQL
- AFXDAO/CDaoRecordset::GetType
- AFXDAO/CDaoRecordset::GetValidationRule
- AFXDAO/CDaoRecordset::GetValidationText
- AFXDAO/CDaoRecordset::IsBOF
- AFXDAO/CDaoRecordset::IsDeleted
- AFXDAO/CDaoRecordset::IsEOF
- AFXDAO/CDaoRecordset::IsFieldDirty
- AFXDAO/CDaoRecordset::IsFieldNull
- AFXDAO/CDaoRecordset::IsFieldNullable
- AFXDAO/CDaoRecordset::IsOpen
- AFXDAO/CDaoRecordset::Move
- AFXDAO/CDaoRecordset::MoveFirst
- AFXDAO/CDaoRecordset::MoveLast
- AFXDAO/CDaoRecordset::MoveNext
- AFXDAO/CDaoRecordset::MovePrev
- AFXDAO/CDaoRecordset::Open
- AFXDAO/CDaoRecordset::Requery
- AFXDAO/CDaoRecordset::Seek
- AFXDAO/CDaoRecordset::SetAbsolutePosition
- AFXDAO/CDaoRecordset::SetBookmark
- AFXDAO/CDaoRecordset::SetCacheSize
- AFXDAO/CDaoRecordset::SetCacheStart
- AFXDAO/CDaoRecordset::SetCurrentIndex
- AFXDAO/CDaoRecordset::SetFieldDirty
- AFXDAO/CDaoRecordset::SetFieldNull
- AFXDAO/CDaoRecordset::SetFieldValue
- AFXDAO/CDaoRecordset::SetFieldValueNull
- AFXDAO/CDaoRecordset::SetLockingMode
- AFXDAO/CDaoRecordset::SetParamValue
- AFXDAO/CDaoRecordset::SetParamValueNull
- AFXDAO/CDaoRecordset::SetPercentPosition
- AFXDAO/CDaoRecordset::Update
- AFXDAO/CDaoRecordset::m_bCheckCacheForDirtyFields
- AFXDAO/CDaoRecordset::m_nFields
- AFXDAO/CDaoRecordset::m_nParams
- AFXDAO/CDaoRecordset::m_pDAORecordset
- AFXDAO/CDaoRecordset::m_pDatabase
- AFXDAO/CDaoRecordset::m_strFilter
- AFXDAO/CDaoRecordset::m_strSort
helpviewer_keywords:
- CDaoRecordset [MFC], CDaoRecordset
- CDaoRecordset [MFC], AddNew
- CDaoRecordset [MFC], CanAppend
- CDaoRecordset [MFC], CanBookmark
- CDaoRecordset [MFC], CancelUpdate
- CDaoRecordset [MFC], CanRestart
- CDaoRecordset [MFC], CanScroll
- CDaoRecordset [MFC], CanTransact
- CDaoRecordset [MFC], CanUpdate
- CDaoRecordset [MFC], Close
- CDaoRecordset [MFC], Delete
- CDaoRecordset [MFC], DoFieldExchange
- CDaoRecordset [MFC], Edit
- CDaoRecordset [MFC], FillCache
- CDaoRecordset [MFC], Find
- CDaoRecordset [MFC], FindFirst
- CDaoRecordset [MFC], FindLast
- CDaoRecordset [MFC], FindNext
- CDaoRecordset [MFC], FindPrev
- CDaoRecordset [MFC], GetAbsolutePosition
- CDaoRecordset [MFC], GetBookmark
- CDaoRecordset [MFC], GetCacheSize
- CDaoRecordset [MFC], GetCacheStart
- CDaoRecordset [MFC], GetCurrentIndex
- CDaoRecordset [MFC], GetDateCreated
- CDaoRecordset [MFC], GetDateLastUpdated
- CDaoRecordset [MFC], GetDefaultDBName
- CDaoRecordset [MFC], GetDefaultSQL
- CDaoRecordset [MFC], GetEditMode
- CDaoRecordset [MFC], GetFieldCount
- CDaoRecordset [MFC], GetFieldInfo
- CDaoRecordset [MFC], GetFieldValue
- CDaoRecordset [MFC], GetIndexCount
- CDaoRecordset [MFC], GetIndexInfo
- CDaoRecordset [MFC], GetLastModifiedBookmark
- CDaoRecordset [MFC], GetLockingMode
- CDaoRecordset [MFC], GetName
- CDaoRecordset [MFC], GetParamValue
- CDaoRecordset [MFC], GetPercentPosition
- CDaoRecordset [MFC], GetRecordCount
- CDaoRecordset [MFC], GetSQL
- CDaoRecordset [MFC], GetType
- CDaoRecordset [MFC], GetValidationRule
- CDaoRecordset [MFC], GetValidationText
- CDaoRecordset [MFC], IsBOF
- CDaoRecordset [MFC], IsDeleted
- CDaoRecordset [MFC], IsEOF
- CDaoRecordset [MFC], IsFieldDirty
- CDaoRecordset [MFC], IsFieldNull
- CDaoRecordset [MFC], IsFieldNullable
- CDaoRecordset [MFC], IsOpen
- CDaoRecordset [MFC], Move
- CDaoRecordset [MFC], MoveFirst
- CDaoRecordset [MFC], MoveLast
- CDaoRecordset [MFC], MoveNext
- CDaoRecordset [MFC], MovePrev
- CDaoRecordset [MFC], Open
- CDaoRecordset [MFC], Requery
- CDaoRecordset [MFC], Seek
- CDaoRecordset [MFC], SetAbsolutePosition
- CDaoRecordset [MFC], SetBookmark
- CDaoRecordset [MFC], SetCacheSize
- CDaoRecordset [MFC], SetCacheStart
- CDaoRecordset [MFC], SetCurrentIndex
- CDaoRecordset [MFC], SetFieldDirty
- CDaoRecordset [MFC], SetFieldNull
- CDaoRecordset [MFC], SetFieldValue
- CDaoRecordset [MFC], SetFieldValueNull
- CDaoRecordset [MFC], SetLockingMode
- CDaoRecordset [MFC], SetParamValue
- CDaoRecordset [MFC], SetParamValueNull
- CDaoRecordset [MFC], SetPercentPosition
- CDaoRecordset [MFC], Update
- CDaoRecordset [MFC], m_bCheckCacheForDirtyFields
- CDaoRecordset [MFC], m_nFields
- CDaoRecordset [MFC], m_nParams
- CDaoRecordset [MFC], m_pDAORecordset
- CDaoRecordset [MFC], m_pDatabase
- CDaoRecordset [MFC], m_strFilter
- CDaoRecordset [MFC], m_strSort
ms.assetid: 2322067f-1027-4662-a5d7-aa2fc7488630
ms.openlocfilehash: 6a1475d1b0bc083cfd180ea5a211e752c973e2f8
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754683"
---
# <a name="cdaorecordset-class"></a>Clase CDaoRecordset

Representa un conjunto de registros seleccionados de un origen de datos.

## <a name="syntax"></a>Sintaxis

```
class CDaoRecordset : public CObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CDaoRecordset::CDaoRecordset](#cdaorecordset)|Construye un objeto `CDaoRecordset`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CDaoRecordset::AddNew](#addnew)|Se prepara para agregar un nuevo registro. Llame a [Update](#update) para completar la adición.|
|[CDaoRecordset::CanAppend](#canappend)|Devuelve distinto de cero si se pueden agregar nuevos registros al conjunto de registros a través de la [AddNew](#addnew) función miembro.|
|[CDaoRecordset::CanBookmark](#canbookmark)|Devuelve distinto de cero si el conjunto de registros admite marcadores.|
|[CDaoRecordset::CancelUpdate](#cancelupdate)|Cancela las actualizaciones pendientes debido a una operación [Editar](#edit) o [AddNew.](#addnew)|
|[CDaoRecordset::CanRestart](#canrestart)|Devuelve distinto de cero si se puede llamar a [Requery](#requery) para volver a ejecutar la consulta del conjunto de registros.|
|[CDaoRecordset::CanScroll](#canscroll)|Devuelve distinto de cero si puede desplazarse por los registros.|
|[CDaoRecordset::CanTransact](#cantransact)|Devuelve distinto de cero si el origen de datos admite transacciones.|
|[CDaoRecordset::CanUpdate](#canupdate)|Devuelve distinto de cero si se puede actualizar el conjunto de registros (puede agregar, actualizar o eliminar registros).|
|[CDaoRecordset::Cerrar](#close)|Cierra el conjunto de registros.|
|[CDaoRecordset::Delete](#delete)|Elimina el registro actual del conjunto de registros. Debe desplazarse explícitamente a otro registro después de la eliminación.|
|[CDaoRecordset::DoFieldExchange](#dofieldexchange)|Se llama para intercambiar datos (en ambas direcciones) entre los miembros de datos de campo del conjunto de registros y el registro correspondiente en el origen de datos. Implementa el intercambio de campos de registros DAO (DFX).|
|[CDaoRecordset::Editar](#edit)|Se prepara para los cambios en el registro actual. Llame `Update` para completar la edición.|
|[CDaoRecordset::FillCache](#fillcache)|Rellena todo o parte de una memoria caché local para un objeto de conjunto de registros que contiene datos de un origen de datos ODBC.|
|[CDaoRecordset::Buscar](#find)|Busca la primera, siguiente, anterior o última ubicación de una cadena determinada en un conjunto de registros de tipo dinámico que satisface los criterios especificados y hace que ese registro el registro actual.|
|[CDaoRecordset::FindFirst](#findfirst)|Busca el primer registro en un conjunto de registros de tipo dinámico o de tipo instantánea que cumple los criterios especificados y hace que registre el registro actual.|
|[CDaoRecordset::FindLast](#findlast)|Busca el último registro en un conjunto de registros de tipo dinámico o de tipo instantánea que cumple los criterios especificados y hace que registre el registro actual.|
|[CDaoRecordset::FindNext](#findnext)|Busca el siguiente registro en un conjunto de registros de tipo dinámico o de tipo instantánea que cumple los criterios especificados y hace que registre el registro actual.|
|[CDaoRecordset::FindPrev](#findprev)|Busca el registro anterior en un conjunto de registros de tipo dinámico o de tipo instantánea que cumple los criterios especificados y hace que registre el registro actual.|
|[CDaoRecordset::GetAbsolutePosition](#getabsoluteposition)|Devuelve el número de registro del registro actual de un objeto de conjunto de registros.|
|[CDaoRecordset::GetBookmark](#getbookmark)|Devuelve un valor que representa el marcador de un registro.|
|[CDaoRecordset::GetCacheSize](#getcachesize)|Devuelve un valor que especifica el número de registros de un conjunto de registros de tipo dinámico que contiene datos que se almacenarán localmente en caché desde un origen de datos ODBC.|
|[CDaoRecordset::GetCacheStart](#getcachestart)|Devuelve un valor que especifica el marcador del primer registro del conjunto de registros que se va a almacenar en caché.|
|[CDaoRecordset::GetCurrentIndex](#getcurrentindex)|Devuelve `CString` un que contiene el nombre del índice utilizado más `CDaoRecordset`recientemente en un tipo de tabla indizado.|
|[CDaoRecordset::GetDateCreated](#getdatecreated)|Devuelve la fecha y hora en `CDaoRecordset` que se creó la tabla base subyacente a un objeto|
|[CDaoRecordset::GetDateLastUpdated](#getdatelastupdated)|Devuelve la fecha y hora del cambio más reciente realizado en `CDaoRecordset` el diseño de una tabla base subyacente a un objeto.|
|[CDaoRecordset::GetDefaultDBName](#getdefaultdbname)|Devuelve el nombre del origen de datos predeterminado.|
|[CDaoRecordset::GetDefaultSQL](#getdefaultsql)|Se llama para obtener la cadena SQL predeterminada que se va a ejecutar.|
|[CDaoRecordset::GetEditMode](#geteditmode)|Devuelve un valor que indica el estado de edición del registro actual.|
|[CDaoRecordset::GetFieldCount](#getfieldcount)|Devuelve un valor que representa el número de campos de un conjunto de registros.|
|[CDaoRecordset::GetFieldInfo](#getfieldinfo)|Devuelve tipos específicos de información sobre los campos del conjunto de registros.|
|[CDaoRecordset::GetFieldValue](#getfieldvalue)|Devuelve el valor de un campo de un conjunto de registros.|
|[CDaoRecordset::GetIndexCount](#getindexcount)|Recupera el número de índices de una tabla subyacente a un conjunto de registros.|
|[CDaoRecordset::GetIndexInfo](#getindexinfo)|Devuelve varios tipos de información sobre un índice.|
|[CDaoRecordset::GetLastModifiedBookmark](#getlastmodifiedbookmark)|Se utiliza para determinar el registro agregado o actualizado más recientemente.|
|[CDaoRecordset::GetLockingMode](#getlockingmode)|Devuelve un valor que indica el tipo de bloqueo que está en vigor durante la edición.|
|[CDaoRecordset::GetName](#getname)|Devuelve `CString` un que contiene el nombre del conjunto de registros.|
|[CDaoRecordset::GetParamValue](#getparamvalue)|Recupera el valor actual del parámetro especificado almacenado en el objeto DAOParameter subyacente.|
|[CDaoRecordset::GetPercentPosition](#getpercentposition)|Devuelve la posición del registro actual como porcentaje del número total de registros.|
|[CDaoRecordset::GetRecordCount](#getrecordcount)|Devuelve el número de registros a los que se tiene acceso en un objeto de conjunto de registros.|
|[CDaoRecordset::GetSQL](#getsql)|Obtiene la cadena SQL utilizada para seleccionar registros para el conjunto de registros.|
|[CDaoRecordset::GetType](#gettype)|Se llama para determinar el tipo de conjunto de registros: tipo de tabla, tipo de conjunto de registros dinámicos o tipo de instantánea.|
|[CDaoRecordset::GetValidationRule](#getvalidationrule)|Devuelve `CString` un valor que contiene el valor que valida los datos a medida que se introducen en un campo.|
|[CDaoRecordset::GetValidationText](#getvalidationtext)|Recupera el texto que se muestra cuando no se cumple una regla de validación.|
|[CDaoRecordset::IsBOF](#isbof)|Devuelve distinto de cero si el conjunto de registros se ha colocado antes del primer registro. No hay ningún registro actual.|
|[CDaoRecordset::IsDeleted](#isdeleted)|Devuelve distinto de cero si el conjunto de registros se coloca en un registro eliminado.|
|[CDaoRecordset::IsEOF](#iseof)|Devuelve distinto de cero si el conjunto de registros se ha colocado después del último registro. No hay ningún registro actual.|
|[CDaoRecordset::IsFieldDirty](#isfielddirty)|Devuelve distinto de cero si se ha cambiado el campo especificado en el registro actual.|
|[CDaoRecordset::IsFieldNull](#isfieldnull)|Devuelve distinto de cero si el campo especificado en el registro actual es Null (no tiene ningún valor).|
|[CDaoRecordset::IsFieldNullable](#isfieldnullable)|Devuelve distinto de cero si el campo especificado en el registro actual se puede establecer en Null (sin valor).|
|[CDaoRecordset::IsOpen](#isopen)|Devuelve distinto de cero si se ha llamado anteriormente a [Open.](#open)|
|[CDaoRecordset::Move](#move)|Coloca el conjunto de registros en un número especificado de registros del registro actual en cualquier dirección.|
|[CDaoRecordset::MoveFirst](#movefirst)|Coloca el registro actual en el primer registro del conjunto de registros.|
|[CDaoRecordset::MoveLast](#movelast)|Coloca el registro actual en el último registro del conjunto de registros.|
|[CDaoRecordset::MoveNext](#movenext)|Coloca el registro actual en el siguiente registro del conjunto de registros.|
|[CDaoRecordset::MovePrev](#moveprev)|Coloca el registro actual en el registro anterior en el conjunto de registros.|
|[CDaoRecordset::Open](#open)|Crea un nuevo conjunto de registros a partir de una tabla, un conjunto de registros dinámicos o una instantánea.|
|[CDaoRecordset::Requery](#requery)|Vuelve a ejecutar la consulta del conjunto de registros para actualizar los registros seleccionados.|
|[CDaoRecordset::Buscar](#seek)|Busca el registro en un objeto de conjunto de registros de tipo de tabla indizado que cumple los criterios especificados para el índice actual y hace que registre el registro actual.|
|[CDaoRecordset::SetAbsolutePosition](#setabsoluteposition)|Establece el número de registro del registro actual de un objeto de conjunto de registros.|
|[CDaoRecordset::SetBookmark](#setbookmark)|Coloca el conjunto de registros en un registro que contiene el marcador especificado.|
|[CDaoRecordset::SetCacheSize](#setcachesize)|Establece un valor que especifica el número de registros de un conjunto de registros de tipo dinámico que contiene datos que se almacenarán localmente en caché desde un origen de datos ODBC.|
|[CDaoRecordset::SetCacheStart](#setcachestart)|Establece un valor que especifica el marcador del primer registro del conjunto de registros que se va a almacenar en caché.|
|[CDaoRecordset::SetCurrentIndex](#setcurrentindex)|Se llama para establecer un índice en un conjunto de registros de tipo de tabla.|
|[CDaoRecordset::SetFieldDirty](#setfielddirty)|Marca el campo especificado en el registro actual como modificado.|
|[CDaoRecordset::SetFieldNull](#setfieldnull)|Establece el valor del campo especificado en el registro actual en Null (sin valor).|
|[CDaoRecordset::SetFieldValue](#setfieldvalue)|Establece el valor de un campo en un conjunto de registros.|
|[CDaoRecordset::SetFieldValueNull](#setfieldvaluenull)|Establece el valor de un campo de un conjunto de registros en Null. (sin valor).|
|[CDaoRecordset::SetLockingMode](#setlockingmode)|Establece un valor que indica el tipo de bloqueo que se va a poner en vigor durante la edición.|
|[CDaoRecordset::SetParamValue](#setparamvalue)|Establece el valor actual del parámetro especificado almacenado en el objeto DAOParameter subyacente|
|[CDaoRecordset::SetParamValueNull](#setparamvaluenull)|Establece el valor actual del parámetro especificado en Null (sin valor).|
|[CDaoRecordset::SetPercentPosition](#setpercentposition)|Establece la posición del registro actual en una ubicación correspondiente a un porcentaje del número total de registros de un conjunto de registros.|
|[CDaoRecordset::Update](#update)|Completa una `AddNew` `Edit` operación mediante la guardaguarda de los datos nuevos o editados en el origen de datos.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CDaoRecordset::m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields)|Contiene una marca que indica si los campos se marcan automáticamente como modificados.|
|[CDaoRecordset::m_nFields](#m_nfields)|Contiene el número de miembros de datos de campo en la clase de conjunto de registros y el número de columnas seleccionadas por el conjunto de registros del origen de datos.|
|[CDaoRecordset::m_nParams](#m_nparams)|Contiene el número de miembros de datos de parámetro en la clase de conjunto de registros: el número de parámetros pasados con la consulta del conjunto de registros|
|[CDaoRecordset::m_pDAORecordset](#m_pdaorecordset)|Puntero a la interfaz DAO subyacente al objeto de conjunto de registros.|
|[CDaoRecordset::m_pDatabase](#m_pdatabase)|Base de datos de origen para este conjunto de resultados. Contiene un puntero a un [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) objeto.|
|[CDaoRecordset::m_strFilter](#m_strfilter)|Contiene una cadena utilizada para construir una instrucción **WHERE** de SQL.|
|[CDaoRecordset::m_strSort](#m_strsort)|Contiene una cadena utilizada para construir una instrucción **SQL ORDER BY.**|

## <a name="remarks"></a>Observaciones

Los objetos conocidos `CDaoRecordset` como "recordsets", están disponibles en las tres formas siguientes:

- Los conjuntos de registros de tipo de tabla representan una tabla base que puede usar para examinar, agregar, cambiar o eliminar registros de una sola tabla de base de datos.

- Los conjuntos de registros de tipo Dynaset son el resultado de una consulta que puede tener registros actualizables. Estos conjuntos de registros son un conjunto de registros que puede usar para examinar, agregar, cambiar o eliminar registros de una tabla o tablas de base de datos subyacentes. Los conjuntos de registros de tipo Dynaset pueden contener campos de una o varias tablas de una base de datos.

- Los conjuntos de registros de tipo instantánea son una copia estática de un conjunto de registros que puede usar para buscar datos o generar informes. Estos conjuntos de registros pueden contener campos de una o varias tablas de una base de datos, pero no se pueden actualizar.

Cada forma de conjunto de registros representa un conjunto de registros fijos en el momento en que se abre el conjunto de registros. Cuando se desplaza a un registro en un conjunto de registros de tipo tabla o un conjunto de registros de tipo dinámico, refleja los cambios realizados en el registro después de abrir el conjunto de registros, ya sea por otros usuarios o por otros conjuntos de registros de la aplicación. (No se puede actualizar un conjunto de registros de tipo instantánea.) Puede utilizar `CDaoRecordset` directamente o derivar una `CDaoRecordset`clase de conjunto de registros específica de la aplicación de . Seguidamente, puede:

- Desplácese por los registros.

- Establezca un índice y busque rápidamente registros mediante [Seek](#seek) (solo conjuntos de registros de tipo de tabla).

- Buscar registros basados en una comparación de cadenas: "<", "",\<"", ">" o ">" (conjuntos de registros de tipo dinámico y tipo de instantánea).

- Actualice los registros y especifique un modo de bloqueo (excepto conjuntos de registros de tipo instantánea).

- Filtre el conjunto de registros para restringir los registros que selecciona de los disponibles en el origen de datos.

- Ordene el conjunto de registros.

- Parametrizar el conjunto de registros para personalizar su selección con información no conocida hasta el tiempo de ejecución.

La `CDaoRecordset` clase proporciona una interfaz `CRecordset`similar a la de la clase . La principal diferencia `CDaoRecordset` es que la clase tiene acceso a los datos a través de un objeto de acceso a datos (DAO) basado en OLE. Clase `CRecordset` tiene acceso al DBMS a través de Open Database Connectivity (ODBC) y un controlador ODBC para ese DBMS.

> [!NOTE]
> Las clases de base de datos DAO son distintas de las clases de base de datos MFC basadas en Open Database Connectivity (ODBC). Todos los nombres de clase de base de datos DAO tienen el prefijo "CDao". Todavía puede tener acceso a orígenes de datos ODBC con las clases DAO; las clases DAO generalmente ofrecen capacidades superiores porque son específicas del motor de base de datos Microsoft Jet.

Puede utilizar `CDaoRecordset` directamente o derivar `CDaoRecordset`una clase de . Para utilizar una clase de conjunto de registros en cualquier caso, abra `CDaoDatabase` una base de datos y construya un objeto de conjunto de registros, pasando el constructor un puntero al objeto. También puede construir `CDaoRecordset` un objeto y `CDaoDatabase` dejar que MFC cree un objeto temporal para usted. A continuación, llame a la función miembro [Open](#open) del conjunto de registros, especificando si el objeto es un conjunto de registros de tipo tabla, un conjunto de registros de tipo dinámico o un conjunto de registros de tipo instantánea. Al `Open` llamar, se seleccionan los datos de la base de datos y se recupera el primer registro.

Utilice las funciones miembro del objeto y los miembros de datos para desplazarse por los registros y operar en ellos. Las operaciones disponibles dependen de si el objeto es un conjunto de registros de tipo tabla, un conjunto de registros de tipo dinámico o un conjunto de registros de tipo instantánea, y si es actualizable o de solo lectura, esto depende de la capacidad de la base de datos o del origen de datos de Open Database Connectivity (ODBC). Para actualizar los registros que se `Open` pueden haber cambiado o agregado desde la llamada, llame a la función miembro [Requery](#requery) del objeto. Llame a la `Close` función miembro del objeto y destruya el objeto cuando termine con él.

`CDaoRecordset`utiliza el intercambio de campos de registros DAO (DFX) para admitir la `CDaoRecordset` `CDaoRecordset`lectura y actualización de campos de registro a través de miembros C++ seguros para tipos de la clase o derivada. También puede implementar el enlace dinámico de columnas en una base de datos sin usar el mecanismo DFX mediante [GetFieldValue](#getfieldvalue) y [SetFieldValue](#setfieldvalue).

Para obtener información relacionada, vea el tema "Objeto de conjunto de registros" en la Ayuda de DAO.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

`CDaoRecordset`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdao.h

## <a name="cdaorecordsetaddnew"></a><a name="addnew"></a>CDaoRecordset::AddNew

Llame a esta función miembro para agregar un nuevo registro a un conjunto de registros de tipo tabla o de tipo dinámico.

```
virtual void AddNew();
```

### <a name="remarks"></a>Observaciones

Los campos del registro son inicialmente Null. (En terminología de base de datos, Null significa "no tener ningún valor" y no es lo mismo que NULL en C++.) Para completar la operación, debe llamar a la [Update](#update) función miembro. `Update`guarda los cambios en el origen de datos.

> [!CAUTION]
> Si edita un registro y, a `Update`continuación, se desplaza a otro registro sin llamar, los cambios se pierden sin previo aviso.

Si agrega un registro a un conjunto de registros de tipo dinámico mediante una llamada a [AddNew](#addnew), el `CDaoRecordset` registro es visible en el conjunto de registros y se incluye en la tabla subyacente donde se vuelve visible para los objetos nuevos.

La posición del nuevo registro depende del tipo de conjunto de registros:

- En un conjunto de registros de tipo dinámico, donde se inserta el nuevo registro no está garantizado. Este comportamiento cambió con Microsoft Jet 3.0 por motivos de rendimiento y simultaneidad. Si su objetivo es hacer que el registro recién agregado sea el registro actual, obtenga el marcador del último registro modificado y vaya a ese marcador:

[!code-cpp[NVC_MFCDatabase#1](../../mfc/codesnippet/cpp/cdaorecordset-class_1.cpp)]

- En un conjunto de registros de tipo de tabla para el que se ha especificado un índice, los registros se devuelven en su lugar adecuado en el criterio de ordenación. Si no se ha especificado ningún índice, se devuelven nuevos registros al final del conjunto de registros.

El registro que era `AddNew` actual antes de usar sigue siendo actual. Si desea que el nuevo registro sea actual y el conjunto de registros admita marcadores, llame a [SetBookmark](#setbookmark) al marcador identificado por el valor de la propiedad LastModified del objeto de conjunto de registros DAO subyacente. Hacerlo es útil para determinar el valor de los campos de contador (incremento automático) en un registro agregado. Para obtener más información, vea [GetLastModifiedBookmark](#getlastmodifiedbookmark).

Si la base de datos admite `AddNew` transacciones, puede hacer que la llamada forme parte de una transacción. Para obtener más información acerca de las transacciones, vea la clase [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md). Tenga en cuenta que debe llamar a `AddNew` [CDaoWorkspace::BeginTrans](../../mfc/reference/cdaoworkspace-class.md#begintrans) antes de llamar a .

Es ilegal llamar `AddNew` a un conjunto de registros cuya función miembro [Open](#open) no se ha llamado. A `CDaoException` se produce si `AddNew` se llama a un conjunto de registros que no se puede anexar. Puede determinar si el conjunto de registros se puede actualizar llamando a [CanAppend](#canappend).

Las marcas de marco cambiaron los miembros de datos de campo para asegurarse de que se escribirán en el registro en el origen de datos mediante el mecanismo de intercambio de campos de registros DAO (DFX). Cambiar el valor de un campo generalmente establece el campo sucio automáticamente, por lo que rara vez tendrá que llamar a [SetFieldDirty](#setfielddirty) usted mismo, pero a veces es posible que desee asegurarse de que las columnas se actualizarán o insertarán explícitamente independientemente de qué valor se encuentre en el miembro de datos de campo. El mecanismo DFX también emplea el uso de **PSEUDO NULL**. Para obtener más información, vea [CDaoFieldExchange::m_nOperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation).

Si no se utiliza el mecanismo de doble búfer, cambiar el valor del campo no establece automáticamente el campo como sucio. En este caso, será necesario establecer explícitamente el campo sucio. La marca contenida en [m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields) controla esta comprobación automática de campos.

> [!NOTE]
> Si los registros tienen doble búfer (es decir, `CancelUpdate` la comprobación automática de campos está `AddNew` habilitada), la llamada restaurará las variables miembro a los valores que tenían antes o `Edit` se llamó.

Para obtener información relacionada, vea los temas "AddNew Method", "CancelUpdate Method", "LastModified Property" y "EditMode Property" en la Ayuda de DAO.

## <a name="cdaorecordsetcanappend"></a><a name="canappend"></a>CDaoRecordset::CanAppend

Llame a esta función miembro para determinar si el conjunto de registros abierto anteriormente le permite agregar nuevos registros mediante una llamada a la [AddNew](#addnew) función miembro.

```
BOOL CanAppend() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el conjunto de registros permite agregar nuevos registros; de lo contrario 0. `CanAppend`devolverá 0 si abrió el conjunto de registros como de solo lectura.

### <a name="remarks"></a>Observaciones

Para obtener información relacionada, vea el tema "Método de anexar" en la Ayuda de DAO.

## <a name="cdaorecordsetcanbookmark"></a><a name="canbookmark"></a>CDaoRecordset::CanBookmark

Llame a esta función miembro para determinar si el conjunto de registros abierto anteriormente le permite marcar registros individualmente mediante marcadores.

```
BOOL CanBookmark();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el conjunto de registros admite marcadores, de lo contrario 0.

### <a name="remarks"></a>Observaciones

Si utiliza conjuntos de registros basados enteramente en tablas de motor de base de datos de Microsoft Jet, se pueden usar marcadores excepto en conjuntos de registros de tipo instantánea marcados como conjuntos de registros de desplazamiento de solo avance. Es posible que otros productos de base de datos (orígenes de datos ODBC externos) no admitan marcadores.

Para obtener información relacionada, vea el tema "Propiedad bookmarkable" en la Ayuda de DAO.

## <a name="cdaorecordsetcancelupdate"></a><a name="cancelupdate"></a>CDaoRecordset::CancelUpdate

La `CancelUpdate` función miembro cancela las actualizaciones pendientes debido a una operación [Edit](#edit) o [AddNew.](#addnew)

```
virtual void CancelUpdate();
```

### <a name="remarks"></a>Observaciones

Por ejemplo, si una `Edit` `AddNew` aplicación llama a la `CancelUpdate` función miembro o `Edit` `AddNew` y no ha llamado a [Update](#update), cancela los cambios realizados después o se llamó.

> [!NOTE]
> Si los registros tienen doble búfer (es decir, `CancelUpdate` la comprobación automática de campos está `AddNew` habilitada), la llamada restaurará las variables miembro a los valores que tenían antes o `Edit` se llamó.

Si no `Edit` hay `AddNew` ninguna `CancelUpdate` operación o operación pendiente, hace que MFC produzca una excepción. Llame a la [GetEditMode](#geteditmode) función miembro para determinar si hay una operación pendiente que se puede cancelar.

Para obtener información relacionada, vea el tema "Método CancelUpdate" en la Ayuda de DAO.

## <a name="cdaorecordsetcanrestart"></a><a name="canrestart"></a>CDaoRecordset::CanRestart

Llame a esta función miembro para determinar si el conjunto de `Requery` registros permite reiniciar su consulta (para actualizar sus registros) mediante una llamada a la función miembro.

```
BOOL CanRestart();
```

### <a name="return-value"></a>Valor devuelto

Distinto de `Requery` cero si se puede llamar para ejecutar la consulta del conjunto de registros de nuevo, de lo contrario 0.

### <a name="remarks"></a>Observaciones

Los conjuntos de registros de tipo de tabla no admiten `Requery`archivos .

Si `Requery` no se admite, llame a [Close](#close) y luego a [Open](#open) para actualizar los datos. Puede llamar `Requery` para actualizar la consulta de parámetros subyacente de un objeto de conjunto de registros después de que se hayan cambiado los valores de parámetro.

Para obtener información relacionada, vea el tema "Propiedad reiniciable" en la Ayuda de DAO.

## <a name="cdaorecordsetcanscroll"></a><a name="canscroll"></a>CDaoRecordset::CanScroll

Llame a esta función miembro para determinar si el conjunto de registros permite el desplazamiento.

```
BOOL CanScroll() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si puede desplazarse por los registros, de lo contrario 0.

### <a name="remarks"></a>Observaciones

Si llama [Open](#open) a `dbForwardOnly`Open with , el conjunto de registros solo puede desplazarse hacia delante.

Para obtener información relacionada, vea el tema "Colocación del puntero de registro actual con DAO" en la Ayuda de DAO.

## <a name="cdaorecordsetcantransact"></a><a name="cantransact"></a>CDaoRecordset::CanTransact

Llame a esta función miembro para determinar si el conjunto de registros permite transacciones.

```
BOOL CanTransact();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el origen de datos subyacente admite transacciones, en caso contrario 0.

### <a name="remarks"></a>Observaciones

Para obtener información relacionada, vea el tema "Propiedad de transacciones" en la Ayuda de DAO.

## <a name="cdaorecordsetcanupdate"></a><a name="canupdate"></a>CDaoRecordset::CanUpdate

Llame a esta función miembro para determinar si se puede actualizar el conjunto de registros.

```
BOOL CanUpdate() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el conjunto de registros se puede actualizar (agregar, actualizar y eliminar registros), en caso contrario 0.

### <a name="remarks"></a>Observaciones

Un conjunto de registros puede ser de solo lectura si el `dbReadOnly` origen de datos subyacente es de solo lectura o si especificó para *nOptions* cuando llamó a [Open](#open) para el conjunto de registros.

Para obtener información relacionada, vea los temas "AddNew Method", "Edit Method", "Delete Method", "Update Method" y "Updatable Property" en la Ayuda de DAO.

## <a name="cdaorecordsetcdaorecordset"></a><a name="cdaorecordset"></a>CDaoRecordset::CDaoRecordset

Construye un objeto `CDaoRecordset`.

```
CDaoRecordset(CDaoDatabase* pDatabase = NULL);
```

### <a name="parameters"></a>Parámetros

*pBase de datos*<br/>
Contiene un puntero a un [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) objeto o el valor NULL. Si no NULL `CDaoDatabase` y `Open` la función miembro del objeto no se ha llamado para conectarlo al origen de datos, el conjunto de registros intenta abrirlo durante su propia llamada [abierta.](#open) Si se pasa `CDaoDatabase` NULL, se construye y se conecta un objeto mediante la información del `CDaoRecordset`origen de datos que especificó si derivó la clase de conjunto de registros de .

### <a name="remarks"></a>Observaciones

Puede utilizar `CDaoRecordset` directamente o derivar una `CDaoRecordset`clase específica de la aplicación de . Puede usar ClassWizard para derivar las clases de conjunto de registros.

> [!NOTE]
> Si deriva `CDaoRecordset` una clase, la clase derivada debe proporcionar su propio constructor. En el constructor de la clase `CDaoRecordset::CDaoRecordset`derivada, llame al constructor , pasándole los parámetros adecuados.

Pase NULL al constructor del `CDaoDatabase` conjunto de registros para que un objeto se construya y se conecte automáticamente. Se trata de un método abreviado útil que `CDaoDatabase` no requiere que se construya y conecte un objeto antes de construir el conjunto de registros. Si `CDaoDatabase` el objeto no está abierto, también se creará un [cDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md) objeto que utiliza el espacio de trabajo predeterminado. Para obtener más información, vea [CDaoDatabase::CDaoDatabase](../../mfc/reference/cdaodatabase-class.md#cdaodatabase).

## <a name="cdaorecordsetclose"></a><a name="close"></a>CDaoRecordset::Cerrar

Al `CDaoRecordset` cerrar un objeto, se quita de la colección de conjuntos de registros abiertos de la base de datos asociada.

```
virtual void Close();
```

### <a name="remarks"></a>Observaciones

Dado `Close` que no `CDaoRecordset` destruye el objeto, puede `Open` reutilizar el objeto llamando al mismo origen de datos o a un origen de datos diferente.

Se cancelan todas las instrucciones [AddNew](#addnew) o [Edit](#edit) pendientes y se revierten todas las transacciones pendientes. Si desea conservar las adiciones o ediciones pendientes, llame a [Update](#update) antes de llamar a `Close` cada conjunto de registros.

Puede volver `Open` a `Close`llamar después de llamar. Esto le permite reutilizar el objeto de conjunto de registros. Una mejor alternativa es llamar a [Requery](#requery), si es posible.

Para obtener información relacionada, vea el tema "Método de cierre" en la Ayuda de DAO.

## <a name="cdaorecordsetdelete"></a><a name="delete"></a>CDaoRecordset::Delete

Llame a esta función miembro para eliminar el registro actual en un objeto de conjunto de registros de tipo dinámico abierto o de tipo de tabla.

```
virtual void Delete();
```

### <a name="remarks"></a>Observaciones

Después de una eliminación correcta, los miembros de datos de campo del conjunto de registros se establecen en un valor Null y debe llamar explícitamente a una de las funciones miembro de navegación del conjunto de registros ( [Move](#move), [Seek](#seek), [SetBookmark](#setbookmark), etc.) para mover fuera del registro eliminado. Al eliminar registros de un conjunto de registros, debe `Delete`haber un registro actual en el conjunto de registros antes de llamar a ; de lo contrario, MFC produce una excepción.

`Delete`elimina el registro actual y lo hace inaccesible. Aunque no puede editar ni utilizar el registro eliminado, permanece actualizado. Una vez que se mueve a otro registro, sin embargo, no se puede hacer que el registro eliminado actual de nuevo.

> [!CAUTION]
> El conjunto de registros debe ser actualizable y debe haber `Delete`un registro válido actual en el conjunto de registros cuando se llama a . Por ejemplo, si elimina un registro pero no se `Delete` desplaza `Delete` a un nuevo registro antes de llamar de nuevo, inicia una [excepción CDaoException](../../mfc/reference/cdaoexception-class.md).

Puede recuperar un registro si utiliza transacciones y llama a la [CDaoWorkspace::Rollback](../../mfc/reference/cdaoworkspace-class.md#rollback) función miembro. Si la tabla base es la tabla principal de una relación de eliminación en cascada, la eliminación del registro actual también puede eliminar uno o varios registros de una tabla externa. Para obtener más información, consulte la definición "eliminación en cascada" en la Ayuda de DAO.

A `AddNew` `Edit`diferencia de `Delete` y , una llamada `Update`a no va seguida de una llamada a .

Para obtener información relacionada, vea los temas "AddNew Method", "Edit Method", "Delete Method", "Update Method" y "Updatable Property" en la Ayuda de DAO.

## <a name="cdaorecordsetdofieldexchange"></a><a name="dofieldexchange"></a>CDaoRecordset::DoFieldExchange

El marco de trabajo llama a esta función miembro para intercambiar automáticamente datos entre los miembros de datos de campo del objeto de conjunto de registros y las columnas correspondientes del registro actual en el origen de datos.

```
virtual void DoFieldExchange(CDaoFieldExchange* pFX);
```

### <a name="parameters"></a>Parámetros

*Pfx*<br/>
Contiene un puntero `CDaoFieldExchange` a un objeto. El marco de trabajo ya habrá configurado este objeto para especificar un contexto para la operación de intercambio de campos.

### <a name="remarks"></a>Observaciones

También enlaza los miembros de datos de parámetro, si los hay, a marcadores de posición de parámetro en la cadena de instrucción SQL para la selección del conjunto de registros. El intercambio de datos de campo, denominado intercambio de campos de registros DAO (DFX), funciona en ambas direcciones: desde los miembros de datos de campo del objeto de conjunto de registros a los campos del registro en el origen de datos y desde el registro del origen de datos al objeto de conjunto de registros. Si va a enlazar columnas dinámicamente, no `DoFieldExchange`es necesario implementar .

La única acción que normalmente debe realizar para implementar `DoFieldExchange` para la clase de conjunto de registros derivada es crear la clase con ClassWizard y especificar los nombres y tipos de datos de los miembros de datos de campo. También puede agregar código a lo que ClassWizard escribe para especificar miembros de datos de parámetro. Si todos los campos se van a enlazar dinámicamente, esta función estará inactiva a menos que especifique miembros de datos de parámetro.

Cuando se declara la clase de conjunto de registros `DoFieldExchange` derivada con ClassWizard, el asistente escribe una invalidación de usted, que se asemeja al ejemplo siguiente:

[!code-cpp[NVC_MFCDatabase#2](../../mfc/codesnippet/cpp/cdaorecordset-class_2.cpp)]

## <a name="cdaorecordsetedit"></a><a name="edit"></a>CDaoRecordset::Editar

Llame a esta función miembro para permitir cambios en el registro actual.

```
virtual void Edit();
```

### <a name="remarks"></a>Observaciones

Una vez `Edit` que se llama a la función miembro, los cambios realizados en los campos del registro actual se copian en el búfer de copia. Después de realizar los cambios `Update` deseados en el registro, llame para guardar los cambios. `Edit`guarda los valores de los miembros de datos del conjunto de registros. Si llama `Edit`a , realiza `Edit` cambios y, a continuación, vuelve a `Edit` llamar, los valores del registro se restauran en lo que eran antes de la primera llamada.

> [!CAUTION]
> Si edita un registro y, a continuación, realiza `Update`cualquier operación que se mueve a otro registro sin llamar primero, los cambios se pierden sin previo aviso. Además, si cierra el conjunto de registros o la base de datos principal, el registro editado se descarta sin previo aviso.

En algunos casos, es posible que desee actualizar una columna convirtiéndola en Null (que no contiene datos). Para ello, `SetFieldNull` llame con un parámetro de TRUE para marcar el campo Null; esto también hace que la columna se actualice. Si desea que un campo se escriba en el origen de `SetFieldDirty` datos aunque su valor no haya cambiado, llame con un parámetro de TRUE. Esto funciona incluso si el campo tenía el valor Null.

Las marcas de marco cambiaron los miembros de datos de campo para asegurarse de que se escribirán en el registro en el origen de datos mediante el mecanismo de intercambio de campos de registros DAO (DFX). Cambiar el valor de un campo generalmente establece el campo sucio automáticamente, por lo que rara vez tendrá que llamar a [SetFieldDirty](#setfielddirty) usted mismo, pero a veces es posible que desee asegurarse de que las columnas se actualizarán o insertarán explícitamente independientemente de qué valor se encuentre en el miembro de datos de campo. El mecanismo DFX también emplea el uso de **PSEUDO NULL**. Para obtener más información, vea [CDaoFieldExchange::m_nOperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation).

Si no se utiliza el mecanismo de doble búfer, cambiar el valor del campo no establece automáticamente el campo como sucio. En este caso, será necesario establecer explícitamente el campo sucio. La marca contenida en [m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields) controla esta comprobación automática de campos.

Cuando el objeto de conjunto de registros se bloquea de forma pesimista en un entorno multiusuario, el registro permanece bloqueado desde el momento `Edit` en que se completa la actualización. Si el conjunto de registros está bloqueado de forma optimista, el registro se bloquea y se compara con el registro preeditado justo antes de que se actualice en la base de datos. Si el registro ha `Edit`cambiado `Update` desde que llamó , se produce un error en la operación y MFC produce una excepción. Puede cambiar el modo `SetLockingMode`de bloqueo con .

> [!NOTE]
> El bloqueo optimista siempre se utiliza en formatos de base de datos externos, como ODBC e ISAM instalable.

El registro actual permanece `Edit`actualizado después de llamar a . Para `Edit`llamar , debe haber un registro actual. Si no hay ningún registro actual o si el conjunto de registros no hace referencia a un objeto de conjunto de registros de tipo de tabla o de tipo dinámico abierto, se produce una excepción. La `Edit` llamada `CDaoException` hace que se lance un valor bajo las siguientes condiciones:

- No hay ningún registro actual.

- La base de datos o el conjunto de registros es de solo lectura.

- No hay campos en el registro que se puede registrar.

- La base de datos o conjunto de registros se abrió para uso exclusivo de otro usuario.

- Otro usuario ha bloqueado la página que contiene el registro.

Si el origen de datos admite `Edit` transacciones, puede hacer que la llamada forme parte de una transacción. Tenga en cuenta `CDaoWorkspace::BeginTrans` que `Edit` debe llamar antes de llamar y después de que se ha abierto el conjunto de registros. Tenga en `CDaoWorkspace::CommitTrans` cuenta también que `Update` llamar no `Edit` es un sustituto para llamar para completar la operación. Para obtener más información acerca `CDaoWorkspace`de las transacciones, vea clase .

Para obtener información relacionada, vea los temas "AddNew Method", "Edit Method", "Delete Method", "Update Method" y "Updatable Property" en la Ayuda de DAO.

## <a name="cdaorecordsetfillcache"></a><a name="fillcache"></a>CDaoRecordset::FillCache

Llame a esta función miembro para almacenar en caché un número especificado de registros del conjunto de registros.

```cpp
void FillCache(
    long* pSize = NULL,
    COleVariant* pBookmark = NULL);
```

### <a name="parameters"></a>Parámetros

*pSize*<br/>
Especifica el número de filas que se rellenará en la memoria caché. Si omite este parámetro, el valor viene determinado por el valor de la propiedad CacheSize del objeto DAO subyacente.

*pBookmark*<br/>
Un [COleVariant](../../mfc/reference/colevariant-class.md) que especifica un marcador. La memoria caché se rellena a partir del registro indicado por este marcador. Si omite este parámetro, la memoria caché se rellena a partir del registro indicado por la propiedad CacheStart del objeto DAO subyacente.

### <a name="remarks"></a>Observaciones

El almacenamiento en caché mejora el rendimiento de una aplicación que recupera o recupera datos de un servidor remoto. Una memoria caché es espacio en la memoria local que contiene los datos obtenidos más recientemente del servidor en el supuesto de que los datos probablemente se solicitarán de nuevo mientras se ejecuta la aplicación. Cuando se solicitan datos, el motor de base de datos Microsoft Jet comprueba primero la memoria caché de los datos en lugar de recuperarlos del servidor, lo que lleva más tiempo. El uso del almacenamiento en caché de datos en orígenes de datos que no son ODBC no tiene ningún efecto, ya que los datos no se guardan en la memoria caché.

En lugar de esperar a que la memoria caché se llene con registros a medida `FillCache` que se recuperan, puede rellenar explícitamente la memoria caché en cualquier momento llamando a la función miembro. Esta es una forma más `FillCache` rápida de rellenar la memoria caché porque recupera varios registros a la vez en lugar de uno a la vez. Por ejemplo, mientras se muestra cada pantalla llena de `FillCache` registros, puede hacer que la aplicación llame para capturar la siguiente pantalla llena de registros.

Cualquier base de datos ODBC a la que se tenga acceso con objetos de conjunto de registros puede tener una memoria caché local. Para crear la memoria caché, abra un objeto de `SetCacheSize` conjunto `SetCacheStart` de registros desde el origen de datos remoto y, a continuación, llame a las funciones miembro y del conjunto de registros. Si *lSize* y *lBookmark* crean un intervalo que está parcial o `SetCacheSize` `SetCacheStart`totalmente fuera del intervalo especificado por y , la parte del conjunto de registros fuera de este intervalo se omite y no se carga en la memoria caché. Si `FillCache` solicita más registros que permanecen en el origen de datos remoto, solo se recuperan los registros restantes y no se produce ninguna excepción.

Los registros obtenidos de la memoria caché no reflejan los cambios realizados simultáneamente en los datos de origen por otros usuarios.

`FillCache`recupera solo los registros que aún no se almacenan en caché. Para forzar una actualización de todos `SetCacheSize` los datos almacenados en caché, `SetCacheSize` llame a la función miembro con un parámetro *lSize* igual a 0, vuelva a llamar con el parámetro *lSize* igual al tamaño de la memoria caché que solicitó originalmente y, a continuación, llame a `FillCache`.

Para obtener información relacionada, vea el tema "Método FillCache" en la Ayuda de DAO.

## <a name="cdaorecordsetfind"></a><a name="find"></a>CDaoRecordset::Buscar

Llame a esta función miembro para buscar una cadena determinada en un conjunto de registros de tipo dynaset o snapshot mediante un operador de comparación.

```
virtual BOOL Find(
    long lFindType,
    LPCTSTR lpszFilter);
```

### <a name="parameters"></a>Parámetros

*lFindType*<br/>
Valor que indica el tipo de operación Buscar deseada. Los valores posibles son:

- AFX_DAO_NEXT Busque la siguiente ubicación de una cadena coincidente.

- AFX_DAO_PREV Buscar la ubicación anterior de una cadena coincidente.

- AFX_DAO_FIRST Buscar la primera ubicación de una cadena coincidente.

- AFX_DAO_LAST Buscar la última ubicación de una cadena coincidente.

*lpszFilter*<br/>
Expresión de cadena (como la cláusula **WHERE** en una instrucción SQL sin la palabra **WHERE**) utilizada para localizar el registro. Por ejemplo:

[!code-cpp[NVC_MFCDatabase#3](../../mfc/codesnippet/cpp/cdaorecordset-class_3.cpp)]

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se encuentran registros coincidentes, de lo contrario 0.

### <a name="remarks"></a>Observaciones

Puede encontrar la primera, siguiente, anterior o última instancia de la cadena. `Find`es una función virtual, por lo que puede invalidarla y agregar su propia implementación. Las `FindFirst` `FindLast`funciones , `FindNext`, y `FindPrev` miembro llaman a la `Find` función miembro, por lo que puede usar `Find` para controlar el comportamiento de todas las operaciones Find.

Para buscar un registro en un conjunto de registros de tipo de tabla, llame a la [Seek](#seek) función miembro.

> [!TIP]
> Cuanto menor sea el conjunto de `Find` registros que tenga, más eficaz será. En general, y especialmente con datos ODBC, es mejor crear una nueva consulta que recupere solo los registros que desee.

Para obtener información relacionada, consulte el tema "FindFirst, FindLast, FindNext, FindPrevious Methods" en la Ayuda de DAO.

## <a name="cdaorecordsetfindfirst"></a><a name="findfirst"></a>CDaoRecordset::FindFirst

Llame a esta función miembro para buscar el primer registro que coincide con una condición especificada.

```
BOOL FindFirst(LPCTSTR lpszFilter);
```

### <a name="parameters"></a>Parámetros

*lpszFilter*<br/>
Expresión de cadena (como la cláusula **WHERE** en una instrucción SQL sin la palabra **WHERE**) utilizada para localizar el registro.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se encuentran registros coincidentes, de lo contrario 0.

### <a name="remarks"></a>Observaciones

La `FindFirst` función miembro comienza su búsqueda desde el principio del conjunto de registros y busca hasta el final del conjunto de registros.

Si desea incluir todos los registros en la búsqueda (no solo aquellos que cumplen una condición específica), utilice una de las operaciones Mover para pasar de un registro a otro. Para buscar un registro en un conjunto `Seek` de registros de tipo tabla, llame a la función miembro.

Si no se encuentra un registro que coincida con los `FindFirst` criterios, el puntero de registro actual es indeterminado y devuelve cero. Si el conjunto de registros contiene más `FindFirst` de un registro `FindNext` que cumple los criterios, localiza la primera aparición, localiza la siguiente aparición, etc.

> [!CAUTION]
> Si edita el registro actual, asegúrese de `Update` guardar los cambios llamando a la función miembro antes de pasar a otro registro. Si se mueve a otro registro sin actualizar, los cambios se pierden sin previo aviso.

Las `Find` funciones miembro buscan desde la ubicación y en la dirección especificada en la tabla siguiente:

|Buscar operaciones|Begin|Dirección de búsqueda|
|---------------------|-----------|----------------------|
|`FindFirst`|Inicio del conjunto de registros|Fin del conjunto de registros|
|`FindLast`|Fin del conjunto de registros|Inicio del conjunto de registros|
|`FindNext`|Registro actual|Fin del conjunto de registros|
|`FindPrevious`|Registro actual|Inicio del conjunto de registros|

> [!NOTE]
> Cuando se `FindLast`llama a , el motor de base de datos de Microsoft Jet rellena completamente el conjunto de registros antes de iniciar la búsqueda, si esto no se ha hecho ya. La primera búsqueda puede tardar más que las búsquedas posteriores.

Sin embargo, el uso de `MoveFirst` una `MoveNext`de las operaciones De búsqueda no es lo mismo que llamar o , lo que simplemente hace que el primer o siguiente registro sea actual sin especificar una condición. Puede seguir una operación Buscar con una operación Mover.

Tenga en cuenta lo siguiente al utilizar las operaciones Buscar:

- Si `Find` devuelve distinto de cero, el registro actual no está definido. En este caso, debe volver a colocar el puntero de registro actual en un registro válido.

- No se puede utilizar una operación de búsqueda con un conjunto de registros de tipo de instantánea de desplazamiento de solo avance.

- Debe usar el formato de fecha de EE. UU. (mes-día-año) al buscar campos que contengan fechas, incluso si no está utilizando la versión de EE. UU. del motor de base de datos Microsoft Jet; de lo contrario, es posible que no se encuentren registros coincidentes.

- Al trabajar con bases de datos ODBC y conjuntos de registros dinámicos grandes, puede descubrir que el uso de las operaciones de búsqueda es lento, especialmente cuando se trabaja con conjuntos de registros grandes. Puede mejorar el rendimiento mediante consultas SQL con cláusulas **ORDERBY** `CDaoQuerydef` o **WHERE** personalizadas, consultas de parámetros u objetos que recuperan registros indexados específicos.

Para obtener información relacionada, consulte el tema "FindFirst, FindLast, FindNext, FindPrevious Methods" en la Ayuda de DAO.

## <a name="cdaorecordsetfindlast"></a><a name="findlast"></a>CDaoRecordset::FindLast

Llame a esta función miembro para buscar el último registro que coincide con una condición especificada.

```
BOOL FindLast(LPCTSTR lpszFilter);
```

### <a name="parameters"></a>Parámetros

*lpszFilter*<br/>
Expresión de cadena (como la cláusula **WHERE** en una instrucción SQL sin la palabra **WHERE**) utilizada para localizar el registro.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se encuentran registros coincidentes, de lo contrario 0.

### <a name="remarks"></a>Observaciones

La `FindLast` función miembro comienza su búsqueda al final del conjunto de registros y busca hacia atrás hacia el principio del conjunto de registros.

Si desea incluir todos los registros en la búsqueda (no solo aquellos que cumplen una condición específica), utilice una de las operaciones Mover para pasar de un registro a otro. Para buscar un registro en un conjunto `Seek` de registros de tipo tabla, llame a la función miembro.

Si no se encuentra un registro que coincida con los `FindLast` criterios, el puntero de registro actual es indeterminado y devuelve cero. Si el conjunto de registros contiene más `FindFirst` de un registro `FindNext` que cumple los criterios, localiza la primera aparición, localiza la siguiente aparición después de la primera aparición, etc.

> [!CAUTION]
> Si edita el registro actual, asegúrese de `Update` guardar los cambios llamando a la función miembro antes de pasar a otro registro. Si se mueve a otro registro sin actualizar, los cambios se pierden sin previo aviso.

Sin embargo, el uso de `MoveFirst` una `MoveNext`de las operaciones De búsqueda no es lo mismo que llamar o , lo que simplemente hace que el primer o siguiente registro sea actual sin especificar una condición. Puede seguir una operación Buscar con una operación Mover.

Tenga en cuenta lo siguiente al utilizar las operaciones Buscar:

- Si `Find` devuelve distinto de cero, el registro actual no está definido. En este caso, debe volver a colocar el puntero de registro actual en un registro válido.

- No se puede utilizar una operación de búsqueda con un conjunto de registros de tipo de instantánea de desplazamiento de solo avance.

- Debe usar el formato de fecha de EE. UU. (mes-día-año) al buscar campos que contengan fechas, incluso si no está utilizando la versión de EE. UU. del motor de base de datos Microsoft Jet; de lo contrario, es posible que no se encuentren registros coincidentes.

- Al trabajar con bases de datos ODBC y conjuntos de registros dinámicos grandes, puede descubrir que el uso de las operaciones de búsqueda es lento, especialmente cuando se trabaja con conjuntos de registros grandes. Puede mejorar el rendimiento mediante consultas SQL con cláusulas **ORDERBY** `CDaoQuerydef` o **WHERE** personalizadas, consultas de parámetros u objetos que recuperan registros indexados específicos.

Para obtener información relacionada, consulte el tema "FindFirst, FindLast, FindNext, FindPrevious Methods" en la Ayuda de DAO.

## <a name="cdaorecordsetfindnext"></a><a name="findnext"></a>CDaoRecordset::FindNext

Llame a esta función miembro para buscar el siguiente registro que coincide con una condición especificada.

```
BOOL FindNext(LPCTSTR lpszFilter);
```

### <a name="parameters"></a>Parámetros

*lpszFilter*<br/>
Expresión de cadena (como la cláusula **WHERE** en una instrucción SQL sin la palabra **WHERE**) utilizada para localizar el registro.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se encuentran registros coincidentes, de lo contrario 0.

### <a name="remarks"></a>Observaciones

La `FindNext` función miembro comienza su búsqueda en el registro actual y busca al final del conjunto de registros.

Si desea incluir todos los registros en la búsqueda (no solo aquellos que cumplen una condición específica), utilice una de las operaciones Mover para pasar de un registro a otro. Para buscar un registro en un conjunto `Seek` de registros de tipo tabla, llame a la función miembro.

Si no se encuentra un registro que coincida con los `FindNext` criterios, el puntero de registro actual es indeterminado y devuelve cero. Si el conjunto de registros contiene más `FindFirst` de un registro `FindNext` que cumple los criterios, localiza la primera aparición, localiza la siguiente aparición, etc.

> [!CAUTION]
> Si edita el registro actual, asegúrese de `Update` guardar los cambios llamando a la función miembro antes de pasar a otro registro. Si se mueve a otro registro sin actualizar, los cambios se pierden sin previo aviso.

Sin embargo, el uso de `MoveFirst` una `MoveNext`de las operaciones De búsqueda no es lo mismo que llamar o , lo que simplemente hace que el primer o siguiente registro sea actual sin especificar una condición. Puede seguir una operación Buscar con una operación Mover.

Tenga en cuenta lo siguiente al utilizar las operaciones Buscar:

- Si `Find` devuelve distinto de cero, el registro actual no está definido. En este caso, debe volver a colocar el puntero de registro actual en un registro válido.

- No se puede utilizar una operación de búsqueda con un conjunto de registros de tipo de instantánea de desplazamiento de solo avance.

- Debe usar el formato de fecha de EE. UU. (mes-día-año) al buscar campos que contengan fechas, incluso si no está utilizando la versión de EE. UU. del motor de base de datos Microsoft Jet; de lo contrario, es posible que no se encuentren registros coincidentes.

- Al trabajar con bases de datos ODBC y conjuntos de registros dinámicos grandes, puede descubrir que el uso de las operaciones de búsqueda es lento, especialmente cuando se trabaja con conjuntos de registros grandes. Puede mejorar el rendimiento mediante consultas SQL con cláusulas **ORDERBY** `CDaoQuerydef` o **WHERE** personalizadas, consultas de parámetros u objetos que recuperan registros indexados específicos.

Para obtener información relacionada, consulte el tema "FindFirst, FindLast, FindNext, FindPrevious Methods" en la Ayuda de DAO.

## <a name="cdaorecordsetfindprev"></a><a name="findprev"></a>CDaoRecordset::FindPrev

Llame a esta función miembro para buscar el registro anterior que coincide con una condición especificada.

```
BOOL FindPrev(LPCTSTR lpszFilter);
```

### <a name="parameters"></a>Parámetros

*lpszFilter*<br/>
Expresión de cadena (como la cláusula **WHERE** en una instrucción SQL sin la palabra **WHERE**) utilizada para localizar el registro.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se encuentran registros coincidentes, de lo contrario 0.

### <a name="remarks"></a>Observaciones

La `FindPrev` función miembro comienza su búsqueda en el registro actual y busca hacia atrás hacia el principio del conjunto de registros.

Si desea incluir todos los registros en la búsqueda (no solo aquellos que cumplen una condición específica), utilice una de las operaciones Mover para pasar de un registro a otro. Para buscar un registro en un conjunto `Seek` de registros de tipo tabla, llame a la función miembro.

Si no se encuentra un registro que coincida con los `FindPrev` criterios, el puntero de registro actual es indeterminado y devuelve cero. Si el conjunto de registros contiene más `FindFirst` de un registro `FindNext` que cumple los criterios, localiza la primera aparición, localiza la siguiente aparición, etc.

> [!CAUTION]
> Si edita el registro actual, asegúrese de `Update` guardar los cambios llamando a la función miembro antes de pasar a otro registro. Si se mueve a otro registro sin actualizar, los cambios se pierden sin previo aviso.

Sin embargo, el uso de `MoveFirst` una `MoveNext`de las operaciones De búsqueda no es lo mismo que llamar o , lo que simplemente hace que el primer o siguiente registro sea actual sin especificar una condición. Puede seguir una operación Buscar con una operación Mover.

Tenga en cuenta lo siguiente al utilizar las operaciones Buscar:

- Si `Find` devuelve distinto de cero, el registro actual no está definido. En este caso, debe volver a colocar el puntero de registro actual en un registro válido.

- No se puede utilizar una operación de búsqueda con un conjunto de registros de tipo de instantánea de desplazamiento de solo avance.

- Debe usar el formato de fecha de EE. UU. (mes-día-año) al buscar campos que contengan fechas, incluso si no está utilizando la versión de EE. UU. del motor de base de datos Microsoft Jet; de lo contrario, es posible que no se encuentren registros coincidentes.

- Al trabajar con bases de datos ODBC y conjuntos de registros dinámicos grandes, puede descubrir que el uso de las operaciones de búsqueda es lento, especialmente cuando se trabaja con conjuntos de registros grandes. Puede mejorar el rendimiento mediante consultas SQL con cláusulas **ORDERBY** `CDaoQuerydef` o **WHERE** personalizadas, consultas de parámetros u objetos que recuperan registros indexados específicos.

Para obtener información relacionada, consulte el tema "FindFirst, FindLast, FindNext, FindPrevious Methods" en la Ayuda de DAO.

## <a name="cdaorecordsetgetabsoluteposition"></a><a name="getabsoluteposition"></a>CDaoRecordset::GetAbsolutePosition

Devuelve el número de registro del registro actual de un objeto de conjunto de registros.

```
long GetAbsolutePosition();
```

### <a name="return-value"></a>Valor devuelto

Un entero de 0 al número de registros del conjunto de registros. Corresponde a la posición ordinal del registro actual en el conjunto de registros.

### <a name="remarks"></a>Observaciones

El valor de la propiedad AbsolutePosition del objeto DAO subyacente se basa en cero; un valor de 0 hace referencia al primer registro del conjunto de registros. Puede determinar el número de registros rellenados en el conjunto de registros llamando a [GetRecordCount](#getrecordcount). Las `GetRecordCount` llamadas pueden tardar algún tiempo porque deben tener acceso a todos los registros para determinar el recuento.

Si no hay ningún registro actual, como cuando no hay registros en el conjunto de registros, se devuelve - 1. Si se elimina el registro actual, el AbsolutePosition valor de propiedad no está definido y MFC produce una excepción si se hace referencia a él. Para conjuntos de registros de tipo dinámico, se agregan nuevos registros al final de la secuencia.

> [!NOTE]
> Esta propiedad no está diseñada para usarse como un número de registro suplente. Los marcadores siguen siendo la forma recomendada de conservar y volver a una posición determinada y son la única manera de colocar el registro actual en todos los tipos de objetos de conjunto de registros. En particular, la posición de un registro determinado cambia cuando se eliminan los registros que lo preceden. Tampoco hay ninguna garantía de que un registro determinado tendrá la misma posición absoluta si el conjunto de registros se vuelve a crear porque el orden de los registros individuales dentro de un conjunto de registros no está garantizado a menos que se cree con una instrucción SQL mediante una cláusula **ORDERBY.**

> [!NOTE]
> Esta función miembro solo es válida para conjuntos de registros de tipo dinámico y de tipo instantánea.

Para obtener información relacionada, vea el tema "Propiedad AbsolutePosition" en la Ayuda de DAO.

## <a name="cdaorecordsetgetbookmark"></a><a name="getbookmark"></a>CDaoRecordset::GetBookmark

Llame a esta función miembro para obtener el valor de marcador en un registro determinado.

```
COleVariant GetBookmark();
```

### <a name="return-value"></a>Valor devuelto

Devuelve un valor que representa el marcador en el registro actual.

### <a name="remarks"></a>Observaciones

Cuando se crea o abre un objeto de conjunto de registros, cada uno de sus registros ya tiene un marcador único si los admite. Llame `CanBookmark` para determinar si un conjunto de registros admite marcadores.

Puede guardar el marcador para el registro actual asignando `COleVariant` el valor del marcador a un objeto. Para volver rápidamente a ese registro en cualquier momento `SetBookmark` después de pasar a `COleVariant` un registro diferente, llame con un parámetro correspondiente al valor de ese objeto.

> [!NOTE]
> Llamar a [Requery](#requery) cambia los marcadores DAO.

Para obtener información relacionada, vea el tema "Propiedad de marcador" en la Ayuda de DAO.

## <a name="cdaorecordsetgetcachesize"></a><a name="getcachesize"></a>CDaoRecordset::GetCacheSize

Llame a esta función miembro para obtener el número de registros almacenados en caché.

```
long GetCacheSize();
```

### <a name="return-value"></a>Valor devuelto

Valor que especifica el número de registros de un conjunto de registros de tipo dinámico que contiene datos que se almacenarán localmente en caché desde un origen de datos ODBC.

### <a name="remarks"></a>Observaciones

El almacenamiento en caché de datos mejora el rendimiento de una aplicación que recupera datos de un servidor remoto a través de objetos de conjunto de registros de tipo dinámico. Una memoria caché es un espacio en la memoria local que contiene los datos recuperados más recientemente del servidor en caso de que los datos se soliciten de nuevo mientras se ejecuta la aplicación. Cuando se solicitan datos, el motor de base de datos Microsoft Jet comprueba primero la memoria caché de los datos solicitados en lugar de recuperarlos del servidor, lo que lleva más tiempo. Los datos que no proceden de un origen de datos ODBC no se guardan en la memoria caché.

Cualquier origen de datos ODBC, como una tabla adjunta, puede tener una memoria caché local.

Para obtener información relacionada, vea el tema "CacheSize, CacheStart Properties" en la Ayuda de DAO.

## <a name="cdaorecordsetgetcachestart"></a><a name="getcachestart"></a>CDaoRecordset::GetCacheStart

Llame a esta función miembro para obtener el valor de marcador del primer registro del conjunto de registros que se va a almacenar en caché.

```
COleVariant GetCacheStart();
```

### <a name="return-value"></a>Valor devuelto

A `COleVariant` que especifica el marcador del primer registro del conjunto de registros que se va a almacenar en caché.

### <a name="remarks"></a>Observaciones

El motor de base de datos microsoft Jet solicita registros dentro del intervalo de caché de la memoria caché y solicita registros fuera del intervalo de caché desde el servidor.

> [!NOTE]
> Los registros recuperados de la memoria caché no reflejan los cambios realizados simultáneamente en los datos de origen por otros usuarios.

Para obtener información relacionada, vea el tema "CacheSize, CacheStart Properties" en la Ayuda de DAO.

## <a name="cdaorecordsetgetcurrentindex"></a><a name="getcurrentindex"></a>CDaoRecordset::GetCurrentIndex

Llame a esta función miembro para determinar el índice `CDaoRecordset` actualmente en uso en un objeto de tipo de tabla indizado.

```
CString GetCurrentIndex();
```

### <a name="return-value"></a>Valor devuelto

Un `CString` contenedor del nombre del índice actualmente en uso con un conjunto de registros de tipo de tabla. Devuelve una cadena vacía si no se ha establecido ningún índice.

### <a name="remarks"></a>Observaciones

Este índice es la base para ordenar registros en un conjunto de registros de tipo tabla y lo usa la función miembro [Seek](#seek) para buscar registros.

Un `CDaoRecordset` objeto puede tener más de un índice, pero solo puede usar un índice a la vez (aunque un [cDaoTableDef](../../mfc/reference/cdaotabledef-class.md) objeto puede tener varios índices definidos en él).

Para obtener información relacionada, vea el tema "Objeto de índice" y la definición "índice actual" en la Ayuda de DAO.

## <a name="cdaorecordsetgetdatecreated"></a><a name="getdatecreated"></a>CDaoRecordset::GetDateCreated

Llame a esta función miembro para recuperar la fecha y hora en que se creó una tabla base.

```
COleDateTime GetDateCreated();
```

### <a name="return-value"></a>Valor devuelto

Un [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objeto que contiene la fecha y hora en que se creó la tabla base.

### <a name="remarks"></a>Observaciones

La configuración de fecha y hora se deriva del equipo en el que se creó la tabla base.

Para obtener información relacionada, vea el tema "DateCreated, LastUpdated Properties" en la Ayuda de DAO.

## <a name="cdaorecordsetgetdatelastupdated"></a><a name="getdatelastupdated"></a>CDaoRecordset::GetDateLastUpdated

Llame a esta función miembro para recuperar la fecha y hora en que se actualizó por última vez el esquema.

```
COleDateTime GetDateLastUpdated();
```

### <a name="return-value"></a>Valor devuelto

Un [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objeto que contiene la fecha y hora de la estructura de tabla base (esquema) se actualizó por última vez.

### <a name="remarks"></a>Observaciones

La configuración de fecha y hora se deriva del equipo en el que se actualizó por última vez la estructura de la tabla base (esquema).

Para obtener información relacionada, vea el tema "DateCreated, LastUpdated Properties" en la Ayuda de DAO.

## <a name="cdaorecordsetgetdefaultdbname"></a><a name="getdefaultdbname"></a>CDaoRecordset::GetDefaultDBName

Llame a esta función miembro para determinar el nombre de la base de datos para este conjunto de registros.

```
virtual CString GetDefaultDBName();
```

### <a name="return-value"></a>Valor devuelto

A `CString` que contiene la ruta de acceso y el nombre de la base de datos de la que se deriva este conjunto de registros.

### <a name="remarks"></a>Observaciones

Si se crea un conjunto de registros sin un puntero a un [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md), el conjunto de registros utiliza esta ruta de acceso para abrir la base de datos predeterminada. De forma predeterminada, esta función devuelve una cadena vacía. Cuando ClassWizard deriva un `CDaoRecordset`nuevo conjunto de registros de , creará esta función para usted.

En el ejemplo siguiente se muestra el\\\\uso de la barra diagonal inversa doble ( ) en la cadena, como es necesario para que la cadena se interprete correctamente.

[!code-cpp[NVC_MFCDatabase#4](../../mfc/codesnippet/cpp/cdaorecordset-class_4.cpp)]

## <a name="cdaorecordsetgetdefaultsql"></a><a name="getdefaultsql"></a>CDaoRecordset::GetDefaultSQL

El marco de trabajo llama a esta función miembro para obtener la instrucción SQL predeterminada en la que se basa el conjunto de registros.

```
virtual CString GetDefaultSQL();
```

### <a name="return-value"></a>Valor devuelto

A `CString` que contiene la instrucción SQL predeterminada.

### <a name="remarks"></a>Observaciones

Puede ser un nombre de tabla o una instrucción **SELECT** de SQL.

Defina indirectamente la instrucción SQL predeterminada declarando la clase de conjunto de registros con ClassWizard y ClassWizard realiza esta tarea por usted.

Si pasa una cadena SQL nula a [Open](#open), se llama a esta función para determinar el nombre de tabla o SQL para el conjunto de registros.

## <a name="cdaorecordsetgeteditmode"></a><a name="geteditmode"></a>CDaoRecordset::GetEditMode

Llame a esta función miembro para determinar el estado de edición, que es uno de los siguientes valores:

```
short GetEditMode();
```

### <a name="return-value"></a>Valor devuelto

Devuelve un valor que indica el estado de edición del registro actual.

### <a name="remarks"></a>Observaciones

|Value|Descripción|
|-----------|-----------------|
|`dbEditNone`|No hay ninguna operación de edición en curso.|
|`dbEditInProgress`|Se ha llamado previamente a `Edit`.|
|`dbEditAdd`|Se ha llamado previamente a `AddNew`.|

Para obtener información relacionada, vea el tema "Propiedad EditMode" en la Ayuda de DAO.

## <a name="cdaorecordsetgetfieldcount"></a><a name="getfieldcount"></a>CDaoRecordset::GetFieldCount

Llame a esta función miembro para recuperar el número de campos (columnas) definidos en el conjunto de registros.

```
short GetFieldCount();
```

### <a name="return-value"></a>Valor devuelto

El número de campos del conjunto de registros.

### <a name="remarks"></a>Observaciones

Para obtener información relacionada, vea el tema "Count Property" en la Ayuda de DAO.

## <a name="cdaorecordsetgetfieldinfo"></a><a name="getfieldinfo"></a>CDaoRecordset::GetFieldInfo

Llame a esta función miembro para obtener información sobre los campos de un conjunto de registros.

```cpp
void GetFieldInfo(
    int nIndex,
    CDaoFieldInfo& fieldinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

void GetFieldInfo(
    LPCTSTR lpszName,
    CDaoFieldInfo& fieldinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
El índice de base cero del campo predefinido de la colección Fields del conjunto de registros, para la búsqueda por índice.

*fieldinfo*<br/>
Una referencia a un [CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md) estructura.

*dwInfoOptions*<br/>
Opciones que especifican qué información sobre el conjunto de registros se va a recuperar. Las opciones disponibles se enumeran aquí junto con lo que hacen que la función vuelva. Para obtener el mejor rendimiento, recupere solo el nivel de información que necesita:

- `AFX_DAO_PRIMARY_INFO`(Predeterminado) Nombre, Tipo, Tamaño, Atributos

- `AFX_DAO_SECONDARY_INFO`Información principal, además de: Posición ordinal, Requerido, Permitir longitud cero, Orden de intercalación, Nombre externo, Campo de origen, Tabla de origen

- `AFX_DAO_ALL_INFO`Información primaria y secundaria, además de: Valor predeterminado, Regla de validación, Texto de validación

*lpszName*<br/>
Nombre del campo.

### <a name="remarks"></a>Observaciones

Una versión de la función le permite buscar un campo por índice. La otra versión le permite buscar un campo por nombre.

Para obtener una descripción de la información devuelta, vea el [CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md) estructura. Esta estructura tiene miembros que corresponden a los elementos de información enumerados anteriormente en la descripción de *dwInfoOptions*. Cuando solicita información en un nivel, también obtiene información para cualquier nivel anterior.

Para obtener información relacionada, vea el tema "Propiedad de atributos" en la Ayuda de DAO.

## <a name="cdaorecordsetgetfieldvalue"></a><a name="getfieldvalue"></a>CDaoRecordset::GetFieldValue

Llame a esta función miembro para recuperar datos en un conjunto de registros.

```
virtual void GetFieldValue(
    LPCTSTR lpszName,
    COleVariant& varValue);

virtual void GetFieldValue(
    int nIndex,
    COleVariant& varValue);

virtual COleVariant GetFieldValue(LPCTSTR lpszName);
virtual COleVariant GetFieldValue(int nIndex);
```

### <a name="parameters"></a>Parámetros

*lpszName*<br/>
Puntero a una cadena que contiene el nombre de un campo.

*varValue*<br/>
Una referencia `COleVariant` a un objeto que almacenará el valor de un campo.

*nIndex*<br/>
Un índice de base cero del campo de la colección Fields del conjunto de registros, para la búsqueda por índice.

### <a name="return-value"></a>Valor devuelto

Las dos `GetFieldValue` versiones de ese devuelven un valor devuelven un [COleVariant](../../mfc/reference/colevariant-class.md) objeto que contiene el valor de un campo.

### <a name="remarks"></a>Observaciones

Puede buscar un campo por nombre o por posición ordinal.

> [!NOTE]
> Es más eficaz llamar a una de las versiones de esta función miembro que toma una `COleVariant` referencia de objeto como parámetro, en lugar de llamar a una versión que devuelve un `COleVariant` objeto. Las últimas versiones de esta función se mantienen por compatibilidad con versiones anteriores.

Use `GetFieldValue` y [SetFieldValue](#setfieldvalue) para enlazar campos dinámicamente en tiempo de ejecución en lugar de enlazar columnas estáticamente mediante el mecanismo [DoFieldExchange.](#dofieldexchange)

`GetFieldValue`y `DoFieldExchange` el mecanismo se puede combinar para mejorar el rendimiento. Por ejemplo, `GetFieldValue` utilice para recuperar un valor que solo necesita a petición y asigne esa llamada a un botón "Más información" en la interfaz.

Para obtener información relacionada, vea los temas "Objeto de campo" y "Propiedad de valor" en la Ayuda de DAO.

## <a name="cdaorecordsetgetindexcount"></a><a name="getindexcount"></a>CDaoRecordset::GetIndexCount

Llame a esta función miembro para determinar el número de índices disponibles en el conjunto de registros de tipo de tabla.

```
short GetIndexCount();
```

### <a name="return-value"></a>Valor devuelto

El número de índices en el conjunto de registros de tipo tabla.

### <a name="remarks"></a>Observaciones

`GetIndexCount`es útil para recorrer en bucle todos los índices del conjunto de registros. Para ello, `GetIndexCount` utilícelo junto con [GetIndexInfo](#getindexinfo). Si se llama a esta función miembro en conjuntos de registros de tipo dinámico o de tipo instantánea, MFC produce una excepción.

Para obtener información relacionada, vea el tema "Propiedad de atributos" en la Ayuda de DAO.

## <a name="cdaorecordsetgetindexinfo"></a><a name="getindexinfo"></a>CDaoRecordset::GetIndexInfo

Llame a esta función miembro para obtener varios tipos de información sobre un índice definido en la tabla base subyacente a un conjunto de registros.

```cpp
void GetIndexInfo(
    int nIndex,
    CDaoIndexInfo& indexinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

void GetIndexInfo(
    LPCTSTR lpszName,
    CDaoIndexInfo& indexinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
El índice de base cero de la colección Indexes de la tabla, para la búsqueda por posición numérica.

*indexinfo*<br/>
Una referencia a un [CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md) estructura.

*dwInfoOptions*<br/>
Opciones que especifican qué información sobre el índice se va a recuperar. Las opciones disponibles se enumeran aquí junto con lo que hacen que la función vuelva. Para obtener el mejor rendimiento, recupere solo el nivel de información que necesita:

- `AFX_DAO_PRIMARY_INFO`(Predeterminado) Nombre, Información de campo, Campos

- `AFX_DAO_SECONDARY_INFO`Información primaria, además de: Primaria, Única, Agrupada, IgnoreNulls, Obligatoria, Extranjera

- `AFX_DAO_ALL_INFO`Información primaria y secundaria, además: Recuento diferenciado

*lpszName*<br/>
Un puntero al nombre del objeto de índice, para la búsqueda por nombre.

### <a name="remarks"></a>Observaciones

Una versión de la función permite buscar un índice por su posición en la colección. La otra versión le permite buscar un índice por nombre.

Para obtener una descripción de la información devuelta, vea el [CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md) estructura. Esta estructura tiene miembros que corresponden a los elementos de información enumerados anteriormente en la descripción de *dwInfoOptions*. Cuando solicita información en un nivel, también obtiene información para cualquier nivel anterior.

Para obtener información relacionada, vea el tema "Propiedad de atributos" en la Ayuda de DAO.

## <a name="cdaorecordsetgetlastmodifiedbookmark"></a><a name="getlastmodifiedbookmark"></a>CDaoRecordset::GetLastModifiedBookmark

Llame a esta función miembro para recuperar el marcador del registro agregado o actualizado más recientemente.

```
COleVariant GetLastModifiedBookmark();
```

### <a name="return-value"></a>Valor devuelto

Un `COleVariant` marcador que contiene el registro agregado o modificado más recientemente.

### <a name="remarks"></a>Observaciones

Cuando se crea o abre un objeto de conjunto de registros, cada uno de sus registros ya tiene un marcador único si los admite. Llame a [GetBookmark](#getbookmark) para determinar si el conjunto de registros admite marcadores. Si el conjunto de registros `CDaoException` no admite marcadores, se produce un objeto.

Cuando se agrega un registro, aparece al final del conjunto de registros y no es el registro actual. Para que el nuevo `GetLastModifiedBookmark` registro sea `SetBookmark` actual, llame y, a continuación, llame para volver al registro recién agregado.

Para obtener información relacionada, vea el tema "Propiedad LastModified" en la Ayuda de DAO.

## <a name="cdaorecordsetgetlockingmode"></a><a name="getlockingmode"></a>CDaoRecordset::GetLockingMode

Llame a esta función miembro para determinar el tipo de bloqueo en vigor para el conjunto de registros.

```
BOOL GetLockingMode();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el tipo de bloqueo es pesimista, de lo contrario 0 para el bloqueo de registros optimista.

### <a name="remarks"></a>Observaciones

Cuando el bloqueo pesimista está en vigor, la página de datos que contiene el registro que está editando se bloquea tan pronto como se llama a la [Edit](#edit) función miembro. La página se desbloquea cuando se llama a la [Update](#update) o [Close](#close) función miembro o cualquiera de las operaciones Move o Find.

Cuando el bloqueo optimista está en vigor, la página de datos que `Update` contiene el registro se bloquea solo mientras se actualiza el registro con la función miembro.

Cuando se trabaja con orígenes de datos ODBC, el modo de bloqueo siempre es optimista.

Para obtener información relacionada, vea los temas "LockEdits Property" y "Locking Behavior in Multiuser Applications" en la Ayuda de DAO.

## <a name="cdaorecordsetgetname"></a><a name="getname"></a>CDaoRecordset::GetName

Llame a esta función miembro para recuperar el nombre del conjunto de registros.

```
CString GetName();
```

### <a name="return-value"></a>Valor devuelto

A `CString` que contiene el nombre del conjunto de registros.

### <a name="remarks"></a>Observaciones

El nombre del conjunto de registros debe comenzar con una letra y puede contener un máximo de 40 caracteres. Puede incluir números y caracteres de subrayado, pero no puede incluir puntuación ni espacios.

Para obtener información relacionada, vea el tema "Propiedad de nombre" en la Ayuda de DAO.

## <a name="cdaorecordsetgetparamvalue"></a><a name="getparamvalue"></a>CDaoRecordset::GetParamValue

Llame a esta función miembro para recuperar el valor actual del parámetro especificado almacenado en el objeto DAOParameter subyacente.

```
virtual COleVariant GetParamValue(int nIndex);
virtual COleVariant GetParamValue(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
La posición numérica del parámetro en el objeto DAOParameter subyacente.

*lpszName*<br/>
El nombre del parámetro cuyo valor desea.

### <a name="return-value"></a>Valor devuelto

Objeto de la clase [COleVariant](../../mfc/reference/colevariant-class.md) que contiene el valor del parámetro.

### <a name="remarks"></a>Observaciones

Puede acceder al parámetro por nombre o por su posición numérica en la colección.

Para obtener información relacionada, vea el tema "Objeto de parámetro" en la Ayuda de DAO.

## <a name="cdaorecordsetgetpercentposition"></a><a name="getpercentposition"></a>CDaoRecordset::GetPercentPosition

Cuando se trabaja con un conjunto de registros `GetPercentPosition` de tipo dinámico o de tipo instantánea, si se llama antes de rellenar completamente el conjunto de registros, la cantidad de movimiento es relativa al número de registros a los que se tiene acceso como se indica mediante una llamada a [GetRecordCount](#getrecordcount).

```
float GetPercentPosition();
```

### <a name="return-value"></a>Valor devuelto

Número entre 0 y 100 que indica la ubicación aproximada del registro actual en el objeto de conjunto de registros en función de un porcentaje de los registros del conjunto de registros.

### <a name="remarks"></a>Observaciones

Puede pasar al último registro llamando a [MoveLast](#movelast) para completar la población de todos los conjuntos de registros, pero esto puede tardar una cantidad significativa de tiempo.

Puede llamar `GetPercentPosition` a los tres tipos de objetos de conjunto de registros, incluidas las tablas sin índices. Sin embargo, `GetPercentPosition` no se puede llamar a instantáneas de desplazamiento de solo avance o en un conjunto de registros abierto desde una consulta de paso a través en una base de datos externa. Si no hay ningún registro actual o se `CDaoException` ha eliminado el registro actual, se produce un valor.

Para obtener información relacionada, vea el tema "Propiedad PercentPosition" en la Ayuda de DAO.

## <a name="cdaorecordsetgetrecordcount"></a><a name="getrecordcount"></a>CDaoRecordset::GetRecordCount

Llame a esta función miembro para averiguar cuántos registros de un conjunto de registros se han tenido acceso.

```
long GetRecordCount();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el número de registros a los que se tiene acceso en un objeto de conjunto de registros.

### <a name="remarks"></a>Observaciones

`GetRecordCount`no indica cuántos registros están contenidos en un conjunto de registros de tipo dinámico o de tipo instantánea hasta que se ha tenido acceso a todos los registros. Esta llamada a la función miembro puede tardar una cantidad significativa de tiempo en completarse.

Una vez que se ha tenido acceso al último registro, el valor devuelto indica el número total de registros no eliminados en el conjunto de registros. Para forzar el acceso al último `MoveLast` `FindLast` registro, llame a la función o miembro del conjunto de registros. También puede usar un recuento de SQL para determinar el número aproximado de registros que devolverá la consulta.

A medida que la aplicación elimina registros en un `GetRecordCount` conjunto de registros de tipo dinámico, el valor devuelto disminuye. Sin embargo, los registros eliminados por otros usuarios no se reflejan `GetRecordCount` hasta que el registro actual se coloca en un registro eliminado. Si ejecuta una transacción que afecta al recuento de `GetRecordCount` registros y posteriormente revierte la transacción, no reflejará el número real de registros restantes.

El valor `GetRecordCount` de un conjunto de registros de tipo de instantánea no se ve afectado por los cambios en las tablas subyacentes.

El valor `GetRecordCount` de un conjunto de registros de tipo tabla refleja el número aproximado de registros de la tabla y se ve afectado inmediatamente a medida que se agregan y eliminan registros de tabla.

Un conjunto de registros sin registros devuelve un valor de 0. Cuando se trabaja con tablas adjuntas o bases de datos ODBC, `GetRecordCount` siempre devuelve - 1. Llamar `Requery` a la función miembro en `GetRecordCount` un conjunto de registros restablece el valor de como si la consulta se volvió a ejecutar.

Para obtener información relacionada, vea el tema "Propiedad RecordCount" en la Ayuda de DAO.

## <a name="cdaorecordsetgetsql"></a><a name="getsql"></a>CDaoRecordset::GetSQL

Llame a esta función miembro para obtener la instrucción SQL que se usó para seleccionar los registros del conjunto de registros cuando se abrió.

```
CString GetSQL() const;
```

### <a name="return-value"></a>Valor devuelto

A `CString` que contiene la instrucción SQL.

### <a name="remarks"></a>Observaciones

Por lo general, se trata de una instrucción **SELECT** de SQL.

La cadena `GetSQL` devuelta por es normalmente diferente de cualquier cadena que haya pasado al conjunto de registros en el *lpszSQL* parámetro a la [Open](#open) función miembro. Esto se debe a que el conjunto de registros construye una instrucción SQL completa en función de lo que pasó , `Open`lo que especificó con ClassWizard y lo que puede haber especificado en el [m_strFilter](#m_strfilter) y [m_strSort](#m_strsort) miembros de datos.

> [!NOTE]
> Llame a esta función miembro solo después de llamar a `Open`.

Para obtener información relacionada, vea el tema "Propiedad SQL" en la Ayuda de DAO.

## <a name="cdaorecordsetgettype"></a><a name="gettype"></a>CDaoRecordset::GetType

Llame a esta función miembro después de abrir el conjunto de registros para determinar el tipo del objeto de conjunto de registros.

```
short GetType();
```

### <a name="return-value"></a>Valor devuelto

Uno de los siguientes valores que indica el tipo de conjunto de registros:

- `dbOpenTable`Conjunto de registros de tipo tabla

- `dbOpenDynaset`Conjunto de registros de tipo Dynaset

- `dbOpenSnapshot`Conjunto de registros de tipo instantánea

### <a name="remarks"></a>Observaciones

Para obtener información relacionada, vea el tema "Propiedad de tipo" en la Ayuda de DAO.

## <a name="cdaorecordsetgetvalidationrule"></a><a name="getvalidationrule"></a>CDaoRecordset::GetValidationRule

Llame a esta función miembro para determinar la regla utilizada para validar los datos.

```
CString GetValidationRule();
```

### <a name="return-value"></a>Valor devuelto

Objeto `CString` que contiene un valor que valida los datos de un registro a medida que se cambian o se agregan a una tabla.

### <a name="remarks"></a>Observaciones

Esta regla se basa en texto y se aplica cada vez que se cambia la tabla subyacente. Si los datos no son legales, MFC produce una excepción. El mensaje de error devuelto es el texto de la propiedad ValidationText del objeto de campo subyacente, si se especifica, o el texto de la expresión especificada por la propiedad ValidationRule del objeto de campo subyacente. Puede llamar a [GetValidationText](#getvalidationtext) para obtener el texto del mensaje de error.

Por ejemplo, un campo de un registro que requiere el día del mes podría tener una regla de validación como "DAY BETWEEN 1 AND 31."

Para obtener información relacionada, vea el tema "Propiedad ValidationRule" en la Ayuda de DAO.

## <a name="cdaorecordsetgetvalidationtext"></a><a name="getvalidationtext"></a>CDaoRecordset::GetValidationText

Llame a esta función miembro para recuperar el texto de la Propiedad ValidationText del objeto de campo subyacente.

```
CString GetValidationText();
```

### <a name="return-value"></a>Valor devuelto

Objeto `CString` que contiene el texto del mensaje que se muestra si el valor de un campo no satisface la regla de validación del objeto de campo subyacente.

### <a name="remarks"></a>Observaciones

Para obtener información relacionada, vea el tema "Propiedad ValidationText" en la Ayuda de DAO.

## <a name="cdaorecordsetisbof"></a><a name="isbof"></a>CDaoRecordset::IsBOF

Llame a esta función miembro antes de desplazarse de registro a registro para saber si ha ido antes del primer registro del conjunto de registros.

```
BOOL IsBOF() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el conjunto de registros no contiene registros o si se ha desplazado hacia atrás antes del primer registro; de lo contrario 0.

### <a name="remarks"></a>Observaciones

También puede `IsBOF` llamar `IsEOF` junto con para determinar si el conjunto de registros contiene registros o está vacío. Inmediatamente después `Open`de llamar a , `IsBOF` si el conjunto de registros no contiene registros, devuelve distinto de cero. Al abrir un conjunto de registros que tiene al menos `IsBOF` un registro, el primer registro es el registro actual y devuelve 0.

Si el primer registro es el `MovePrev` `IsBOF` registro actual y se llama a , devolverá posteriormente distinto de cero. Si `IsBOF` devuelve distinto de `MovePrev`cero y se llama a , se produce una excepción. Si `IsBOF` devuelve distinto de cero, el registro actual es indefinido y cualquier acción que requiera un registro actual dará lugar a una excepción.

Efecto de `IsBOF` métodos `IsEOF` y ajustes específicos:

- Al `Open*` llamar internamente, el primer registro `MoveFirst`del conjunto de registros es el registro actual llamando a . Por lo `Open` tanto, llamar a `IsBOF` `IsEOF` un conjunto vacío de registros provoca y devuelve distinto de cero. (Consulte la tabla siguiente para `MoveFirst` ver `MoveLast` el comportamiento de un error o una llamada.)

- Todas las operaciones Move que `IsBOF` localizan correctamente un registro provocan tanto como `IsEOF` devuelva0.

- Una `AddNew` llamada seguida `Update` de una llamada que inserta `IsBOF` correctamente un nuevo registro `IsEOF` hará que se devuelva 0, pero solo si ya es distinto de cero. El estado `IsEOF` de voluntad siempre permanece inalterado. Según lo definido por el motor de base de datos Microsoft Jet, el puntero de registro actual de un conjunto de registros vacío se encuentra al final de un archivo, por lo que cualquier registro nuevo se inserta después del registro actual.

- Cualquier `Delete` llamada, incluso si quita el único registro restante de un `IsBOF` conjunto `IsEOF`de registros, no cambiará el valor de o .

Esta tabla muestra qué operaciones Mover `IsBOF` /  `IsEOF`se permiten con diferentes combinaciones de .

||MoveFirst, MoveLast|MovePrev,<br /><br /> Mover < 0|Mover 0|Movenext<br /><br /> Mover > 0|
|------|-------------------------|-----------------------------|------------|-----------------------------|
|`IsBOF`•nonzero,<br /><br /> `IsEOF`=0|Permitida|Excepción|Excepción|Permitida|
|`IsBOF`=0,<br /><br /> `IsEOF`•nonzero|Permitida|Permitida|Excepción|Excepción|
|Ambos distintos de cero|Excepción|Excepción|Excepción|Excepción|
|Ambos 0|Permitida|Permitida|Permitida|Permitida|

Permitir una operación Move no significa que la operación localice correctamente un registro. Simplemente indica que se permite un intento de realizar la operación Move especificada y no generará una excepción. El valor `IsBOF` de `IsEOF` las funciones miembro y puede cambiar como resultado del intento de movimiento.

El efecto de las operaciones Move que `IsBOF` no `IsEOF` localizan un registro en el valor y la configuración se muestra en la tabla siguiente.

||IsBOF|IsEOF|
|------|-----------|-----------|
|`MoveFirst`, `MoveLast`|Distinto|Distinto|
|`Move` 0|Sin cambios|Sin cambios|
|`MovePrev`, `Move` < 0|Distinto|Sin cambios|
|`MoveNext`, `Move` > 0|Sin cambios|Distinto|

Para obtener información relacionada, vea el tema "BOF, Propiedades de EOF" en la Ayuda de DAO.

## <a name="cdaorecordsetisdeleted"></a><a name="isdeleted"></a>CDaoRecordset::IsDeleted

Llame a esta función miembro para determinar si se ha eliminado el registro actual.

```
BOOL IsDeleted() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el conjunto de registros se coloca en un registro eliminado; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Si se desplaza a `IsDeleted` un registro y devuelve TRUE (distinto de cero), debe desplazarse a otro registro antes de poder realizar cualquier otra operación de conjunto de registros.

> [!NOTE]
> No es necesario comprobar el estado eliminado de los registros de una instantánea o conjunto de registros de tipo tabla. Dado que los registros no se pueden `IsDeleted`eliminar de una instantánea, no es necesario llamar a . Para los conjuntos de registros de tipo de tabla, los registros eliminados se quitan realmente del conjunto de registros. Una vez que se ha eliminado un registro, ya sea por usted, otro usuario o en otro conjunto de registros, no se puede volver a ese registro. Por lo tanto, no `IsDeleted`hay necesidad de llamar .

Cuando se elimina un registro de un conjunto de registros dinámicos, se quita del conjunto de registros y no se puede volver a ese registro. Sin embargo, si un registro de un conjunto de registros dinámicos `IsDeleted` es eliminado por otro usuario o en otro conjunto de registros basado en la misma tabla, devolverá TRUE cuando más adelante se desplazará a ese registro.

Para obtener información relacionada, vea los temas "Método de eliminación", "Propiedad LastModified" y "Propiedad EditMode" en la Ayuda de DAO.

## <a name="cdaorecordsetiseof"></a><a name="iseof"></a>CDaoRecordset::IsEOF

Llame a esta función miembro a medida que se desplaza de registro a registro para saber si ha ido más allá del último registro del conjunto de registros.

```
BOOL IsEOF() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el conjunto de registros no contiene registros o si se ha desplazado más allá del último registro; de lo contrario 0.

### <a name="remarks"></a>Observaciones

También puede `IsEOF` llamar para determinar si el conjunto de registros contiene registros o está vacío. Inmediatamente después `Open`de llamar a , `IsEOF` si el conjunto de registros no contiene registros, devuelve distinto de cero. Al abrir un conjunto de registros que tiene al menos `IsEOF` un registro, el primer registro es el registro actual y devuelve 0.

Si el último registro es el `MoveNext` `IsEOF` registro actual cuando se llama , devolverá posteriormente distinto de cero. Si `IsEOF` devuelve distinto de `MoveNext`cero y se llama a , se produce una excepción. Si `IsEOF` devuelve distinto de cero, el registro actual es indefinido y cualquier acción que requiera un registro actual dará lugar a una excepción.

Efecto de `IsBOF` métodos `IsEOF` y ajustes específicos:

- Al `Open` llamar internamente, el primer registro `MoveFirst`del conjunto de registros es el registro actual llamando a . Por lo `Open` tanto, llamar a `IsBOF` `IsEOF` un conjunto vacío de registros provoca y devuelve distinto de cero. (Consulte la tabla siguiente para `MoveFirst` ver el comportamiento de una llamada con error.)

- Todas las operaciones Move que `IsBOF` localizan correctamente un registro provocan tanto como `IsEOF` devuelva0.

- Una `AddNew` llamada seguida `Update` de una llamada que inserta `IsBOF` correctamente un nuevo registro `IsEOF` hará que se devuelva 0, pero solo si ya es distinto de cero. El estado `IsEOF` de voluntad siempre permanece inalterado. Según lo definido por el motor de base de datos Microsoft Jet, el puntero de registro actual de un conjunto de registros vacío se encuentra al final de un archivo, por lo que cualquier registro nuevo se inserta después del registro actual.

- Cualquier `Delete` llamada, incluso si quita el único registro restante de un `IsBOF` conjunto `IsEOF`de registros, no cambiará el valor de o .

Esta tabla muestra qué operaciones Mover `IsBOF` /  `IsEOF`se permiten con diferentes combinaciones de .

||MoveFirst, MoveLast|MovePrev,<br /><br /> Mover < 0|Mover 0|Movenext<br /><br /> Mover > 0|
|------|-------------------------|-----------------------------|------------|-----------------------------|
|`IsBOF`•nonzero,<br /><br /> `IsEOF`=0|Permitida|Excepción|Excepción|Permitida|
|`IsBOF`=0,<br /><br /> `IsEOF`•nonzero|Permitida|Permitida|Excepción|Excepción|
|Ambos distintos de cero|Excepción|Excepción|Excepción|Excepción|
|Ambos 0|Permitida|Permitida|Permitida|Permitida|

Permitir una operación Move no significa que la operación localice correctamente un registro. Simplemente indica que se permite un intento de realizar la operación Move especificada y no generará una excepción. El valor `IsBOF` de `IsEOF` las funciones miembro y puede cambiar como resultado del intento de mover.

El efecto de las operaciones Move que `IsBOF` no `IsEOF` localizan un registro en el valor y la configuración se muestra en la tabla siguiente.

||IsBOF|IsEOF|
|------|-----------|-----------|
|`MoveFirst`, `MoveLast`|Distinto|Distinto|
|`Move` 0|Sin cambios|Sin cambios|
|`MovePrev`, `Move` < 0|Distinto|Sin cambios|
|`MoveNext`, `Move` > 0|Sin cambios|Distinto|

Para obtener información relacionada, vea el tema "BOF, Propiedades de EOF" en la Ayuda de DAO.

## <a name="cdaorecordsetisfielddirty"></a><a name="isfielddirty"></a>CDaoRecordset::IsFieldDirty

Llame a esta función miembro para determinar si el miembro de datos de campo especificado de un conjunto de registros dinámicos se ha marcado como "sucio" (cambiado).

```
BOOL IsFieldDirty(void* pv);
```

### <a name="parameters"></a>Parámetros

*Pv*<br/>
Un puntero al miembro de datos de campo cuyo estado desea comprobar, o NULL para determinar si alguno de los campos está sucio.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el miembro de datos de campo especificado se marca como sucio; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Los datos de todos los miembros de datos de campo sucios se transferirán `Update` al registro `CDaoRecordset` del origen `Edit` de `AddNew`datos cuando se actualice el registro actual mediante una llamada a la función miembro de (después de una llamada a o ). Con este conocimiento, puede realizar más pasos, como desmarcar el miembro de datos de campo para marcar la columna para que no se escriba en el origen de datos.

`IsFieldDirty`se implementa `DoFieldExchange`a través de .

## <a name="cdaorecordsetisfieldnull"></a><a name="isfieldnull"></a>CDaoRecordset::IsFieldNull

Llame a esta función miembro para determinar si el miembro de datos de campo especificado de un conjunto de registros se ha marcado como Null.

```
BOOL IsFieldNull(void* pv);
```

### <a name="parameters"></a>Parámetros

*Pv*<br/>
Un puntero al miembro de datos de campo cuyo estado desea comprobar, o NULL para determinar si alguno de los campos es Null.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el miembro de datos de campo especificado se marca como Null; de lo contrario 0.

### <a name="remarks"></a>Observaciones

(En terminología de base de datos, Null significa "no tener ningún valor" y no es lo mismo que NULL en C++.) Si un miembro de datos de campo se marca como Null, se interpreta como una columna del registro actual para la que no hay ningún valor.

> [!NOTE]
> En determinadas `IsFieldNull` situaciones, el uso puede ser ineficiente, como se muestra en el ejemplo de código siguiente:

[!code-cpp[NVC_MFCDatabase#5](../../mfc/codesnippet/cpp/cdaorecordset-class_5.cpp)]

> [!NOTE]
> Si utiliza el enlace de registros `CDaoRecordset`dinámicos, sin derivar de , asegúrese de usar VT_NULL como se muestra en el ejemplo.

## <a name="cdaorecordsetisfieldnullable"></a><a name="isfieldnullable"></a>CDaoRecordset::IsFieldNullable

Llame a esta función miembro para determinar si el miembro de datos de campo especificado es "nullable" (se puede establecer en un Null valor; C++ NULL no es lo mismo que Null, que, en terminología de base de datos, significa "no tener ningún valor").

```
BOOL IsFieldNullable(void* pv);
```

### <a name="parameters"></a>Parámetros

*Pv*<br/>
Un puntero al miembro de datos de campo cuyo estado desea comprobar, o NULL para determinar si alguno de los campos es Null.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el miembro de datos de campo especificado se puede hacer Null; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Un campo que no puede ser Null debe tener un valor. Si intenta establecer un campo de este tipo en Null al agregar o actualizar `Update` un registro, el origen de datos rechaza la adición o actualización y producirá una excepción. La excepción se `Update`produce cuando `SetFieldNull`se llama , no cuando se llama a .

## <a name="cdaorecordsetisopen"></a><a name="isopen"></a>CDaoRecordset::IsOpen

Llame a esta función miembro para determinar si el conjunto de registros está abierto.

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si `Open` se `Requery` ha llamado previamente a la función miembro o del objeto de conjunto de registros y no se ha cerrado el conjunto de registros; de lo contrario 0.

### <a name="remarks"></a>Observaciones

## <a name="cdaorecordsetm_bcheckcachefordirtyfields"></a><a name="m_bcheckcachefordirtyfields"></a>CDaoRecordset::m_bCheckCacheForDirtyFields

Contiene una marca que indica si los campos almacenados en caché se marcan automáticamente como sucios (cambiados) y Null.

### <a name="remarks"></a>Observaciones

El valor predeterminado de la marca es TRUE. La configuración de este miembro de datos controla todo el mecanismo de almacenamiento en búfer doble. Si establece la marca en TRUE, puede desactivar el almacenamiento en caché campo por campo mediante el mecanismo DFX. Si establece la marca en FALSE, debe llamar `SetFieldDirty` y `SetFieldNull` a sí mismo.

Establezca este miembro `Open`de datos antes de llamar a . Este mecanismo es principalmente para facilitar su uso. El rendimiento puede ser más lento debido al almacenamiento en búfer doble de los campos a medida que se realizan cambios.

## <a name="cdaorecordsetm_nfields"></a><a name="m_nfields"></a>CDaoRecordset::m_nFields

Contiene el número de miembros de datos de campo en la clase de conjunto de registros y el número de columnas seleccionadas por el conjunto de registros del origen de datos.

### <a name="remarks"></a>Observaciones

El constructor de la `m_nFields` clase de conjunto de registros debe inicializarse con el número correcto de campos enlazados estáticamente. ClassWizard escribe esta inicialización automáticamente cuando se usa para declarar la clase de conjunto de registros. También puede escribirlo manualmente.

El marco de trabajo usa este número para administrar la interacción entre los miembros de datos de campo y las columnas correspondientes del registro actual en el origen de datos.

> [!NOTE]
> Este número debe corresponder al número `DoFieldExchange` de columnas `SetFieldType` de `CDaoFieldExchange::outputColumn`salida registradas después de una llamada con el parámetro .

Puede enlazar columnas dinámicamente a `CDaoRecordset::GetFieldValue` `CDaoRecordset::SetFieldValue`través de y . Si lo hace, no es necesario incrementar `m_nFields` el recuento para reflejar el `DoFieldExchange` número de llamadas de función DFX en la función miembro.

## <a name="cdaorecordsetm_nparams"></a><a name="m_nparams"></a>CDaoRecordset::m_nParams

Contiene el número de miembros de datos de parámetro en la clase de conjunto de registros: el número de parámetros pasados con la consulta del conjunto de registros.

### <a name="remarks"></a>Observaciones

Si la clase de conjunto de registros tiene algún miembro de datos de parámetro, el constructor de la clase debe inicializar *m_nParams* con el número correcto. El valor predeterminado de *m_nParams* es 0. Si agrega miembros de datos de parámetro, que debe hacer manualmente, también debe agregar manualmente una inicialización en el constructor de clase para reflejar el número de parámetros (que debe ser al menos tan grande como el número de marcadores de posición '' en la *cadena m_strFilter* o *m_strSort).*

El marco de trabajo usa este número cuando parametriza la consulta del conjunto de registros.

> [!NOTE]
> Este número debe corresponder al número de `DoFieldExchange` "params" registrados después de una llamada con `SetFieldType` el parámetro `CFieldExchange::param`.

Para obtener información relacionada, vea el tema "Objeto de parámetro" en la Ayuda de DAO.

## <a name="cdaorecordsetm_pdaorecordset"></a><a name="m_pdaorecordset"></a>CDaoRecordset::m_pDAORecordset

Contiene un puntero a la interfaz OLE `CDaoRecordset` para el objeto de conjunto de registros DAO subyacente al objeto.

### <a name="remarks"></a>Observaciones

Utilice este puntero si necesita acceder a la interfaz DAO directamente.

Para obtener información relacionada, vea el tema "Objeto de conjunto de registros" en la Ayuda de DAO.

## <a name="cdaorecordsetm_pdatabase"></a><a name="m_pdatabase"></a>CDaoRecordset::m_pDatabase

Contiene un puntero `CDaoDatabase` al objeto a través del cual el conjunto de registros está conectado a un origen de datos.

### <a name="remarks"></a>Observaciones

Esta variable se establece de dos maneras. Normalmente, se pasa un puntero `CDaoDatabase` a un objeto ya abierto al construir el objeto de conjunto de registros. Si pasa NULL `CDaoRecordset` en `CDaoDatabase` su lugar, crea un objeto automáticamente y lo abre. En cualquier `CDaoRecordset` caso, almacena el puntero en esta variable.

Normalmente no necesitará utilizar directamente `m_pDatabase`el puntero almacenado en . Sin embargo, si `CDaoRecordset`escribe sus propias extensiones en , es posible que deba usar el puntero. Por ejemplo, es posible que necesite `CDaoException`el puntero si lanza los suyos propios.

Para obtener información relacionada, vea el tema "Objeto de base de datos" en la Ayuda de DAO.

## <a name="cdaorecordsetm_strfilter"></a><a name="m_strfilter"></a>CDaoRecordset::m_strFilter

Contiene una cadena que se utiliza para construir la cláusula **WHERE** de una instrucción SQL.

### <a name="remarks"></a>Observaciones

No incluye la palabra reservada **WHERE** para filtrar el conjunto de registros. El uso de este miembro de datos no es aplicable a conjuntos de registros de tipo tabla. El uso `m_strFilter` de no tiene ningún `CDaoQueryDef` efecto al abrir un conjunto de registros mediante un puntero.

Utilice el formato de fecha de EE. UU. (mes-día-año) al filtrar campos que contienen fechas, incluso si no está utilizando la versión de EE. UU. del motor de base de datos Microsoft Jet; de lo contrario, es posible que los datos no se filtren como espera.

Para obtener información relacionada, vea el tema "Propiedad de filtro" en la Ayuda de DAO.

## <a name="cdaorecordsetm_strsort"></a><a name="m_strsort"></a>CDaoRecordset::m_strSort

Contiene una cadena que contiene la cláusula **ORDERBY** de una instrucción SQL sin las palabras reservadas **ORDERBY**.

### <a name="remarks"></a>Observaciones

Puede ordenar en objetos de conjunto de registros de tipo dinámico e instantánea.

No se pueden ordenar objetos de conjunto de registros de tipo tabla. Para determinar el criterio de ordenación de un conjunto de registros de tipo tabla, llame a [SetCurrentIndex](#setcurrentindex).

El uso de *m_strSort* no tiene ningún `CDaoQueryDef` efecto al abrir un conjunto de registros mediante un puntero.

Para obtener información relacionada, vea el tema "Ordenar propiedad" en la Ayuda de DAO.

## <a name="cdaorecordsetmove"></a><a name="move"></a>CDaoRecordset::Move

Llame a esta función miembro para colocar el conjunto de registros *lRows* registros desde el registro actual.

```
virtual void Move(long lRows);
```

### <a name="parameters"></a>Parámetros

*lRows*<br/>
El número de registros que se moverán hacia delante o hacia atrás. Los valores positivos avanzan hacia el final del conjunto de registros. Los valores negativos se mueven hacia atrás, hacia el principio.

### <a name="remarks"></a>Observaciones

Puede avanzar o retroceder. `Move( 1 )`es equivalente `MoveNext`a `Move( -1 )` , `MovePrev`y es equivalente a .

> [!CAUTION]
> Al llamar `Move` a cualquiera de las funciones se produce una excepción si el conjunto de registros no tiene registros. En general, `IsBOF` llame `IsEOF` a ambos y antes de una operación Move para determinar si el conjunto de registros tiene registros. Después `Open` de `Requery`llamar `IsBOF` o `IsEOF`, llame a cualquiera o .

> [!NOTE]
> Si se ha desplazado más allá del `IsBOF` principio `IsEOF` o al final `Move` del conjunto `CDaoException`de registros ( o devuelve distinto de cero), una llamada para lanzar un archivo .

> [!NOTE]
> Si llama a `Move` cualquiera de las funciones mientras se actualiza o agrega el registro actual, las actualizaciones se pierden sin previo aviso.

Cuando se `Move` llama a una instantánea de desplazamiento de solo avance, el parámetro *lRows* debe ser un entero positivo y no se permiten marcadores, por lo que solo puede avanzar.

Para convertir el primer, último, siguiente o anterior registro de `MoveFirst` `MoveLast`un `MoveNext`conjunto `MovePrev` de registros en el registro actual, llame a la función , , o miembro .

Para obtener información relacionada, consulte los temas "Método de movimiento" y "MoveFirst, MoveLast, MoveNext, MovePrevious Methods" en la Ayuda de DAO.

## <a name="cdaorecordsetmovefirst"></a><a name="movefirst"></a>CDaoRecordset::MoveFirst

Llame a esta función miembro para que el primer registro del conjunto de registros (si existe) sea el registro actual.

```cpp
void MoveFirst();
```

### <a name="remarks"></a>Observaciones

No es necesario `MoveFirst` llamar inmediatamente después de abrir el conjunto de registros. En ese momento, el primer registro (si existe) es automáticamente el registro actual.

> [!CAUTION]
> Al llamar `Move` a cualquiera de las funciones se produce una excepción si el conjunto de registros no tiene registros. En general, `IsBOF` llame `IsEOF` a ambos y antes de una operación Move para determinar si el conjunto de registros tiene registros. Después `Open` de `Requery`llamar `IsBOF` o `IsEOF`, llame a cualquiera o .

> [!NOTE]
> Si llama a `Move` cualquiera de las funciones mientras se actualiza o agrega el registro actual, las actualizaciones se pierden sin previo aviso.

Utilice `Move` las funciones para pasar de un registro a otro sin aplicar una condición. Utilice las operaciones Buscar para buscar registros en un objeto de conjunto de registros de tipo dinámico o de tipo instantánea que satisfagan una determinada condición. Para buscar un registro en un objeto `Seek`de conjunto de registros de tipo tabla, llame a .

Si el conjunto de registros hace referencia a un conjunto de registros de tipo de tabla, el movimiento sigue el índice actual de la tabla. Puede establecer el índice actual mediante la propiedad Index del objeto DAO subyacente. Si no establece el índice actual, el orden de los registros devueltos es indefinido.

Si se `MoveLast` llama a un objeto de conjunto de registros basado en una consulta SQL o una definición de consulta, la consulta se fuerza a completarse y el objeto de conjunto de registros se rellena por completo.

No se `MoveFirst` puede `MovePrev` llamar a la o función miembro con una instantánea de desplazamiento de solo avance.

Para mover la posición del registro actual en un objeto de `Move`conjunto de registros un número específico de registros hacia delante o hacia atrás, llame a .

Para obtener información relacionada, consulte los temas "Método de movimiento" y "MoveFirst, MoveLast, MoveNext, MovePrevious Methods" en la Ayuda de DAO.

## <a name="cdaorecordsetmovelast"></a><a name="movelast"></a>CDaoRecordset::MoveLast

Llame a esta función miembro para que el último registro (si existe) en el conjunto de registros el registro actual.

```cpp
void MoveLast();
```

### <a name="remarks"></a>Observaciones

> [!CAUTION]
> Al llamar `Move` a cualquiera de las funciones se produce una excepción si el conjunto de registros no tiene registros. En general, `IsBOF` llame `IsEOF` a ambos y antes de una operación Move para determinar si el conjunto de registros tiene registros. Después `Open` de `Requery`llamar `IsBOF` o `IsEOF`, llame a cualquiera o .

> [!NOTE]
> Si llama a `Move` cualquiera de las funciones mientras se actualiza o agrega el registro actual, las actualizaciones se pierden sin previo aviso.

Utilice `Move` las funciones para pasar de un registro a otro sin aplicar una condición. Utilice las operaciones Buscar para buscar registros en un objeto de conjunto de registros de tipo dinámico o de tipo instantánea que satisfagan una determinada condición. Para buscar un registro en un objeto `Seek`de conjunto de registros de tipo tabla, llame a .

Si el conjunto de registros hace referencia a un conjunto de registros de tipo de tabla, el movimiento sigue el índice actual de la tabla. Puede establecer el índice actual mediante la propiedad Index del objeto DAO subyacente. Si no establece el índice actual, el orden de los registros devueltos es indefinido.

Si se `MoveLast` llama a un objeto de conjunto de registros basado en una consulta SQL o una definición de consulta, la consulta se fuerza a completarse y el objeto de conjunto de registros se rellena por completo.

Para mover la posición del registro actual en un objeto de `Move`conjunto de registros un número específico de registros hacia delante o hacia atrás, llame a .

Para obtener información relacionada, consulte los temas "Método de movimiento" y "MoveFirst, MoveLast, MoveNext, MovePrevious Methods" en la Ayuda de DAO.

## <a name="cdaorecordsetmovenext"></a><a name="movenext"></a>CDaoRecordset::MoveNext

Llame a esta función miembro para que el siguiente registro en el conjunto de registros el registro actual.

```cpp
void MoveNext();
```

### <a name="remarks"></a>Observaciones

Se recomienda que `IsBOF` llame antes de intentar mover al registro anterior. Una llamada `MovePrev` a `CDaoException` producirá `IsBOF` un if devuelve distinto de cero, lo que indica que ya se ha desplazado antes del primer registro o que el conjunto de registros no seleccionó ningún registro.

> [!CAUTION]
> Al llamar `Move` a cualquiera de las funciones se produce una excepción si el conjunto de registros no tiene registros. En general, `IsBOF` llame `IsEOF` a ambos y antes de una operación Move para determinar si el conjunto de registros tiene registros. Después `Open` de `Requery`llamar `IsBOF` o `IsEOF`, llame a cualquiera o .

> [!NOTE]
> Si llama a `Move` cualquiera de las funciones mientras se actualiza o agrega el registro actual, las actualizaciones se pierden sin previo aviso.

Utilice `Move` las funciones para pasar de un registro a otro sin aplicar una condición. Utilice las operaciones Buscar para buscar registros en un objeto de conjunto de registros de tipo dinámico o de tipo instantánea que satisfagan una determinada condición. Para buscar un registro en un objeto `Seek`de conjunto de registros de tipo tabla, llame a .

Si el conjunto de registros hace referencia a un conjunto de registros de tipo de tabla, el movimiento sigue el índice actual de la tabla. Puede establecer el índice actual mediante la propiedad Index del objeto DAO subyacente. Si no establece el índice actual, el orden de los registros devueltos es indefinido.

Para mover la posición del registro actual en un objeto de `Move`conjunto de registros un número específico de registros hacia delante o hacia atrás, llame a .

Para obtener información relacionada, consulte los temas "Método de movimiento" y "MoveFirst, MoveLast, MoveNext, MovePrevious Methods" en la Ayuda de DAO.

## <a name="cdaorecordsetmoveprev"></a><a name="moveprev"></a>CDaoRecordset::MovePrev

Llame a esta función miembro para que el registro anterior en el conjunto de registros el registro actual.

```cpp
void MovePrev();
```

### <a name="remarks"></a>Observaciones

Se recomienda que `IsBOF` llame antes de intentar mover al registro anterior. Una llamada `MovePrev` a `CDaoException` producirá `IsBOF` un if devuelve distinto de cero, lo que indica que ya se ha desplazado antes del primer registro o que el conjunto de registros no seleccionó ningún registro.

> [!CAUTION]
> Al llamar `Move` a cualquiera de las funciones se produce una excepción si el conjunto de registros no tiene registros. En general, `IsBOF` llame `IsEOF` a ambos y antes de una operación Move para determinar si el conjunto de registros tiene registros. Después `Open` de `Requery`llamar `IsBOF` o `IsEOF`, llame a cualquiera o .

> [!NOTE]
> Si llama a `Move` cualquiera de las funciones mientras se actualiza o agrega el registro actual, las actualizaciones se pierden sin previo aviso.

Utilice `Move` las funciones para pasar de un registro a otro sin aplicar una condición. Utilice las operaciones Buscar para buscar registros en un objeto de conjunto de registros de tipo dinámico o de tipo instantánea que satisfagan una determinada condición. Para buscar un registro en un objeto `Seek`de conjunto de registros de tipo tabla, llame a .

Si el conjunto de registros hace referencia a un conjunto de registros de tipo de tabla, el movimiento sigue el índice actual de la tabla. Puede establecer el índice actual mediante la propiedad Index del objeto DAO subyacente. Si no establece el índice actual, el orden de los registros devueltos es indefinido.

No se `MoveFirst` puede `MovePrev` llamar a la o función miembro con una instantánea de desplazamiento de solo avance.

Para mover la posición del registro actual en un objeto de `Move`conjunto de registros un número específico de registros hacia delante o hacia atrás, llame a .

Para obtener información relacionada, consulte los temas "Método de movimiento" y "MoveFirst, MoveLast, MoveNext, MovePrevious Methods" en la Ayuda de DAO.

## <a name="cdaorecordsetopen"></a><a name="open"></a>CDaoRecordset::Open

Debe llamar a esta función miembro para recuperar los registros para el conjunto de registros.

```
virtual void Open(
    int nOpenType = AFX_DAO_USE_DEFAULT_TYPE,
    LPCTSTR lpszSQL = NULL,
    int nOptions = 0);

virtual void Open(
    CDaoTableDef* pTableDef,
    int nOpenType = dbOpenTable,
    int nOptions = 0);

virtual void Open(
    CDaoQueryDef* pQueryDef,
    int nOpenType = dbOpenDynaset,
    int nOptions = 0);
```

### <a name="parameters"></a>Parámetros

*nOpenType*<br/>
Uno de los valores siguientes:

- `dbOpenDynaset`Un conjunto de registros de tipo dinámico con desplazamiento bidireccional. Este es el valor predeterminado.

- `dbOpenTable`Un conjunto de registros de tipo de tabla con desplazamiento bidireccional.

- `dbOpenSnapshot`Un conjunto de registros de tipo instantánea con desplazamiento bidireccional.

*lpszSQL*<br/>
Puntero de cadena que contiene uno de los elementos siguientes:

- Un puntero NULL.

- El nombre de una o más definiciones de tabla y/o defs de consulta (separadas por comas).

- Una instrucción **SELECT** de SQL (opcionalmente con una cláusula **WHERE** o **ORDERBY** de SQL).

- Una consulta de paso a través.

*nOpciones*<br/>
Una o más de las opciones enumeradas a continuación. El valor predeterminado es 0. Los valores posibles son los siguientes:

- `dbAppendOnly`Solo puede anexar nuevos registros (solo conjunto de registros de tipo dinámico). Esta opción significa literalmente que los registros solo se pueden anexar. Las clases de base de datos ODBC de MFC tienen una opción de solo anexar que permite recuperar y anexar registros.

- `dbForwardOnly`El conjunto de registros es una instantánea de desplazamiento de solo avance.

- `dbSeeChanges`Genere una excepción si otro usuario está cambiando los datos que está editando.

- `dbDenyWrite`Otros usuarios no pueden modificar ni agregar registros.

- `dbDenyRead`Otros usuarios no pueden ver registros (solo conjunto de registros de tipo tabla).

- `dbReadOnly`Solo puede ver registros; otros usuarios pueden modificarlos.

- `dbInconsistent`Se permiten actualizaciones incoherentes (solo conjunto de registros de tipo dinámico).

- `dbConsistent`Solo se permiten actualizaciones coherentes (solo conjunto de registros de tipo dinámico).

> [!NOTE]
> Las `dbConsistent` constantes `dbInconsistent` y son mutuamente excluyentes. Puede utilizar uno u otro, pero no ambos `Open`en una instancia determinada de .

*pTableDef*<br/>
Un puntero a un [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md) objeto. Esta versión solo es válida para conjuntos de registros de tipo tabla. Cuando se utiliza `CDaoDatabase` esta opción, `CDaoRecordset` el puntero utilizado para construir el no se utiliza; más bien, se utiliza la base de datos en la que reside la base de datos.

*pQueryDef*<br/>
Un puntero a un [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md) objeto. Esta versión solo es válida para conjuntos de registros de tipo dinámico y de tipo instantánea. Cuando se utiliza `CDaoDatabase` esta opción, `CDaoRecordset` el puntero utilizado para construir el no se utiliza; más bien, se utiliza la base de datos en la que reside querydef.

### <a name="remarks"></a>Observaciones

Antes `Open`de llamar a , debe construir el objeto de conjunto de registros. Existen varias formas de hacerlo:

- Al construir el objeto de conjunto `CDaoDatabase` de registros, pase un puntero a un objeto que ya esté abierto.

- Al construir el objeto de conjunto `CDaoDatabase` de registros, pase un puntero a un objeto que no esté abierto. El conjunto `CDaoDatabase` de registros abre un objeto, pero no lo cerrará cuando se cierre el objeto de conjunto de registros.

- Al construir el objeto de conjunto de registros, pase un puntero NULL. El objeto `GetDefaultDBName` de conjunto de registros llama para obtener el nombre de Microsoft Access . MDB para abrir. A continuación, `CDaoDatabase` el conjunto de registros abre un objeto y lo mantiene abierto mientras el conjunto de registros esté abierto. Cuando se `Close` llama al `CDaoDatabase` conjunto de registros, el objeto también se cierra.

    > [!NOTE]
    >  Cuando el conjunto `CDaoDatabase` de registros abre el objeto, abre el origen de datos con acceso no exclusivo.

Para la `Open` versión que utiliza el parámetro *lpszSQL,* una vez que el conjunto de registros está abierto, puede recuperar registros de una de varias maneras. La primera opción es tener funciones DFX en su `DoFieldExchange`archivo . La segunda opción es usar el `GetFieldValue` enlace dinámico mediante una llamada a la función miembro. Estas opciones se pueden implementar por separado o en combinación. Si se combinan, tendrá que pasar la instrucción SQL `Open`usted mismo en la llamada a .

Cuando utilice la segunda `Open` versión de `CDaoTableDef` donde se pasa un objeto, las `DoFieldExchange` columnas resultantes estarán disponibles para `GetFieldValue`enlazar a través de y el mecanismo DFX, y / o enlazar dinámicamente a través de .

> [!NOTE]
> Solo se `Open` puede `CDaoTableDef` llamar mediante un objeto para conjuntos de registros de tipo tabla.

Cuando utilice la tercera `Open` versión de `CDaoQueryDef` donde pase un objeto, esa consulta se ejecutará y `DoFieldExchange` las columnas resultantes estarán disponibles `GetFieldValue`para enlazar a través de y el mecanismo DFX, y/ o enlazar dinámicamente a través de .

> [!NOTE]
> Solo se `Open` puede `CDaoQueryDef` llamar mediante un objeto para conjuntos de registros de tipo dinámico y de tipo instantánea.

Para la primera `Open` versión `lpszSQL` que utiliza el parámetro, los registros se seleccionan en función de los criterios que se muestran en la tabla siguiente.

|Valor del parámetro `lpszSQL`|Los registros seleccionados están determinados por|Ejemplo|
|--------------------------------------|----------------------------------------|-------------|
|NULL|La cadena devuelta por `GetDefaultSQL`.||
|Una lista separada por comas de uno o más nombres de definición de tabla y/o definición de consulta.|Todas las columnas `DoFieldExchange`representadas en el archivo .|`"Customer"`|
|**SELECT** column-list **FROM** table-list|Las columnas especificadas de las definiciones de tabla y/o querydef(s) especificadas.|`"SELECT CustId, CustName`<br /><br /> `FROM Customer"`|

El procedimiento habitual es `Open`pasar NULL a ; en ese `Open` caso, llama `GetDefaultSQL`a , una función miembro `CDaoRecordset`reemplazable que ClassWizard genera al crear una clase derivada. Este valor proporciona los nombres de definición de tabla y/o de definición de consulta que especificó en ClassWizard. En su lugar, puede especificar otra información en el parámetro *lpszSQL.*

Pase lo `Open` que pase, construye una cadena SQL final para la consulta (la cadena puede tener cláusulas SQL **WHERE** y **ORDERBY** anexadas a la cadena *lpszSQL* que ha pasado) y, a continuación, ejecuta la consulta. Puede examinar la cadena construida `GetSQL` llamando `Open`a una llamada después de llamar a .

Los miembros de datos de campo de la clase de conjunto de registros están enlazados a las columnas de los datos seleccionados. Si se devuelve algún registro, el primer registro se convierte en el registro actual.

Si desea establecer opciones para el conjunto de registros, como un filtro u ordenación, establezca `m_strSort` o `m_strFilter` después de construir el objeto de conjunto de registros, pero antes de llamar a `Open`. Si desea actualizar los registros del conjunto de registros después de que el conjunto de registros ya esté abierto, llame a `Requery`.

Si llama `Open` a un conjunto de registros de tipo dinámico o de tipo instantánea, o si el origen de `dbOpenTable` datos hace referencia a una instrucción SQL o a una propiedad de tabla que representa una tabla adjunta, no puede usar para el argumento type; si lo hace, MFC produce una excepción. Para determinar si un objeto tabledef representa una tabla adjunta, cree un [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md) objeto y llame a su [GetConnect](../../mfc/reference/cdaotabledef-class.md#getconnect) función miembro.

Utilice `dbSeeChanges` la marca si desea capturar los cambios realizados por otro usuario u otro programa en su equipo cuando esté editando o eliminando el mismo registro. Por ejemplo, si dos usuarios comienzan a editar `Update` el mismo registro, el primer usuario que llama a la función miembro se realiza correctamente. Cuando `Update` es llamado por el `CDaoException` segundo usuario, se produce un. De forma similar, si `Delete` el segundo usuario intenta llamar para eliminar el registro `CDaoException` y ya ha sido cambiado por el primer usuario, se produce un.

Normalmente, si el usuario `CDaoException` obtiene esto durante la actualización, el código debe actualizar el contenido de los campos y recuperar los valores recién modificados. Si la excepción se produce en el proceso de eliminación, el código podría mostrar los nuevos datos de registro al usuario y un mensaje que indica que los datos han cambiado recientemente. En este punto, el código puede solicitar una confirmación de que el usuario todavía desea eliminar el registro.

> [!TIP]
> Utilice la opción de desplazamiento`dbForwardOnly`de solo avance ( ) para mejorar el rendimiento cuando la aplicación realiza un único paso a través de un conjunto de registros abierto desde un origen de datos ODBC.

Para obtener información relacionada, vea el tema "Método OpenRecordset" en la Ayuda de DAO.

## <a name="cdaorecordsetrequery"></a><a name="requery"></a>CDaoRecordset::Requery

Llame a esta función miembro para volver a generar (actualizar) un conjunto de registros.

```
virtual void Requery();
```

### <a name="remarks"></a>Observaciones

Si se devuelve algún registro, el primer registro se convierte en el registro actual.

Para que el conjunto de registros refleje las adiciones y eliminaciones que usted u `Requery`otros usuarios están realizando en el origen de datos, debe volver a generar el conjunto de registros llamando a . Si el conjunto de registros es un conjunto de registros dinámicos, refleja automáticamente las actualizaciones que usted u otros usuarios realizan en sus registros existentes (pero no en las adiciones). Si el conjunto de registros `Requery` es una instantánea, debe llamar para reflejar las ediciones de otros usuarios, así como las adiciones y eliminaciones.

Para un conjunto de registros `Requery` dinámicos o una instantánea, llame a cualquier momento que desee volver a generar el conjunto de registros mediante valores de parámetro. Establezca el nuevo filtro u ordene `Requery`estableciendo [m_strFilter](#m_strfilter) y [m_strSort](#m_strsort) antes de llamar a . Establezca nuevos parámetros asignando nuevos valores `Requery`a los miembros de datos de parámetro antes de llamar a .

Si se produce un error en el intento de volver a generar el conjunto de registros, el conjunto de registros se cierra. Antes de `Requery`llamar a , puede determinar si se puede volver a consultar el conjunto de registros mediante una llamada a la [CanRestart](#canrestart) función miembro. `CanRestart`no garantiza `Requery` que tendrá éxito.

> [!CAUTION]
> Llame `Requery` sólo después `Open`de haber llamado .

> [!NOTE]
> Llamar a [Requery](#requery) cambia los marcadores DAO.

No se puede `Requery` llamar a un conjunto de registros `CanRestart` de tipo dinámico o de tipo instantánea si se devuelve una llamada devuelve 0, ni se puede usar en un conjunto de registros de tipo de tabla.

Si `IsBOF` ambos `IsEOF` y devuelven `Requery`distinto de cero después de llamar a , la consulta no devuelve ningún registro y el conjunto de registros no contendrá datos.

Para obtener información relacionada, vea el tema "Método de consulta" en la Ayuda de DAO.

## <a name="cdaorecordsetseek"></a><a name="seek"></a>CDaoRecordset::Buscar

Llame a esta función miembro para buscar el registro en un objeto de conjunto de registros de tipo de tabla indizado que cumple los criterios especificados para el índice actual y hacer que registre el registro actual.

```
BOOL Seek(
    LPCTSTR lpszComparison,
    COleVariant* pKey1,
    COleVariant* pKey2 = NULL,
    COleVariant* pKey3 = NULL);

BOOL Seek(
    LPCTSTR lpszComparison,
    COleVariant* pKeyArray,
    WORD nKeys);
```

### <a name="parameters"></a>Parámetros

*lpszComparison*<br/>
Una de las siguientes expresiones de\<cadena: "<", "", "", ">", o ">".

*pKey1*<br/>
Un puntero a un [COleVariant](../../mfc/reference/colevariant-class.md) cuyo valor corresponde al primer campo del índice. Necesario.

*pKey2*<br/>
Puntero a `COleVariant` un cuyo valor corresponde al segundo campo del índice, si existe. El valor predeterminado es NULL.

*pKey3*<br/>
Puntero a `COleVariant` un cuyo valor corresponde al tercer campo del índice, si existe. El valor predeterminado es NULL.

*pKeyArray*<br/>
Un puntero a una matriz de variantes. El tamaño de la matriz corresponde al número de campos del índice.

*nKeys*<br/>
Entero correspondiente al tamaño de la matriz, que es el número de campos del índice.

> [!NOTE]
> No especifique comodines en las claves. Los comodines harán `Seek` que no devuelva ningún registro coincidente.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se encuentran registros coincidentes, de lo contrario 0.

### <a name="remarks"></a>Observaciones

Utilice la segunda versión `Seek` (matriz) de para controlar índices de cuatro campos o más.

`Seek`permite la búsqueda de índices de alto rendimiento en conjuntos de registros de tipo tabla. Debe establecer el índice `SetCurrentIndex` actual `Seek`llamando a . Si el índice identifica un campo o `Seek` campos de clave no únicos, busca el primer registro que cumple los criterios. Si no establece un índice, se produce una excepción.

Tenga en cuenta que si no `COleVariant` está creando un conjunto de registros UNICODE, los objetos deben declararse explícitamente ANSI. Esto se puede hacer mediante la forma [COleVariant::COleVariant](../../mfc/reference/colevariant-class.md#colevariant)**(** *lpszSrc* **,** *vtSrc* **)** de constructor con *vtSrc* establecido en `VT_BSTRT` (ANSI) o mediante la `COleVariant` función [SetString](../../mfc/reference/colevariant-class.md#setstring)**(** *lpszSrc* **,** *vtSrc* **)** con *vtSrc* establecido en . `VT_BSTRT`

Cuando se `Seek`llama a , se pasan uno o más\<valores de clave y un operador de comparación ("<", " " , "", ">" o ">"). `Seek`busca a través de los campos clave especificados y localiza el primer registro que cumple los criterios especificados por *lpszComparison* y *pKey1*. Una vez `Seek` encontrado, devuelve distinto de cero y hace que el registro sea actual. Si `Seek` no encuentra una `Seek` coincidencia, devuelve cero y el registro actual es indefinido. Al usar DAO directamente, debe comprobar explícitamente la propiedad NoMatch.

Si `lpszComparison` es "-", ">", o `Seek` ">", comienza al principio del índice. Si *lpszComparison* es "<" o `Seek` "<", comienza al final del índice y busca hacia atrás a menos que haya entradas de índice duplicadas al final. En este `Seek` caso, comienza con una entrada arbitraria entre las entradas de índice duplicadas al final del índice.

No tiene que haber un registro `Seek`actual cuando se utiliza .

Para buscar un registro en un conjunto de registros de tipo dinámico o de tipo instantánea que satisfaga una condición específica, utilice las operaciones Buscar. Para incluir todos los registros, no solo los que cumplen una condición específica, utilice las operaciones Mover para pasar de un registro a otro.

No se `Seek` puede llamar a una tabla adjunta de ningún tipo porque las tablas adjuntas deben abrirse como conjuntos de registros de tipo dinámico o de tipo de instantánea. Sin embargo, `CDaoDatabase::Open` si llama para abrir directamente una `Seek` base de datos ISAM instalable, puede llamar a tablas en esa base de datos, aunque el rendimiento puede ser lento.

Para obtener información relacionada, consulte el tema "Método de búsqueda" en la Ayuda de DAO.

## <a name="cdaorecordsetsetabsoluteposition"></a><a name="setabsoluteposition"></a>CDaoRecordset::SetAbsolutePosition

Establece el número de registro relativo del registro actual de un objeto de conjunto de registros.

```cpp
void SetAbsolutePosition(long lPosition);
```

### <a name="parameters"></a>Parámetros

*lPosición*<br/>
Corresponde a la posición ordinal del registro actual en el conjunto de registros.

### <a name="remarks"></a>Observaciones

La `SetAbsolutePosition` llamada le permite colocar el puntero de registro actual en un registro específico en función de su posición ordinal en un conjunto de registros de tipo dinámico o de tipo instantánea. También puede determinar el número de registro actual llamando a [GetAbsolutePosition](#getabsoluteposition).

> [!NOTE]
> Esta función miembro solo es válida para conjuntos de registros de tipo dinámico y de tipo instantánea.

El valor de la propiedad AbsolutePosition del objeto DAO subyacente se basa en cero; un valor de 0 hace referencia al primer registro del conjunto de registros. Establecer un valor mayor que el número de registros rellenados hace que MFC produzca una excepción. Puede determinar el número de registros rellenados `GetRecordCount` en el conjunto de registros mediante una llamada a la función miembro.

Si se elimina el registro actual, el AbsolutePosition valor de propiedad no está definido y MFC produce una excepción si se hace referencia a él. Se agregan nuevos registros al final de la secuencia.

> [!NOTE]
> Esta propiedad no está diseñada para usarse como un número de registro suplente. Los marcadores siguen siendo la forma recomendada de conservar y volver a una posición determinada y son la única manera de colocar el registro actual en todos los tipos de objetos de conjunto de registros que admiten marcadores. En particular, la posición de un registro determinado cambia cuando se eliminan los registros que lo preceden. Tampoco hay ninguna garantía de que un registro determinado tendrá la misma posición absoluta si el conjunto de registros se vuelve a crear porque el orden de los registros individuales dentro de un conjunto de registros no está garantizado a menos que se cree con una instrucción SQL mediante una cláusula **ORDERBY.**

Para obtener información relacionada, vea el tema "Propiedad AbsolutePosition" en la Ayuda de DAO.

## <a name="cdaorecordsetsetbookmark"></a><a name="setbookmark"></a>CDaoRecordset::SetBookmark

Llame a esta función miembro para colocar el conjunto de registros en el registro que contiene el marcador especificado.

```cpp
void SetBookmark(COleVariant varBookmark);
```

### <a name="parameters"></a>Parámetros

*varBookmark*<br/>
Un [COleVariant](../../mfc/reference/colevariant-class.md) objeto que contiene el valor de marcador para un registro específico.

### <a name="remarks"></a>Observaciones

Cuando se crea o abre un objeto de conjunto de registros, cada uno de sus registros ya tiene un marcador único. Puede recuperar el marcador para el `GetBookmark` registro actual llamando `COleVariant` y guardando el valor en un objeto. Más adelante puede volver a `SetBookmark` ese registro llamando al valor de marcador guardado.

> [!NOTE]
> Llamar a [Requery](#requery) cambia los marcadores DAO.

Tenga en cuenta que si no `COleVariant` está creando un conjunto de registros UNICODE, el objeto debe declararse explícitamente ANSI. Esto se puede hacer mediante la forma [COleVariant::COleVariant](../../mfc/reference/colevariant-class.md#colevariant)**(** *lpszSrc* **,** *vtSrc* **)** de constructor con *vtSrc* establecido en `VT_BSTRT` (ANSI) o mediante la `COleVariant` función [SetString](../../mfc/reference/colevariant-class.md#setstring)**(** *lpszSrc* **,** *vtSrc* **)** con *vtSrc* establecido en . `VT_BSTRT`

Para obtener información relacionada, vea los temas "Propiedad de marcador" y Propiedad bookmarkable" en la Ayuda de DAO.

## <a name="cdaorecordsetsetcachesize"></a><a name="setcachesize"></a>CDaoRecordset::SetCacheSize

Llame a esta función miembro para establecer el número de registros que se almacenarán en caché.

```cpp
void SetCacheSize(long lSize);
```

### <a name="parameters"></a>Parámetros

*lSize*<br/>
Especifica el número de registros. Un valor típico es 100. Un valor de 0 desactiva el almacenamiento en caché. La configuración debe estar entre 5 y 1200 registros. La memoria caché puede utilizar una cantidad considerable de memoria.

### <a name="remarks"></a>Observaciones

Una memoria caché es un espacio en la memoria local que contiene los datos recuperados más recientemente del servidor en caso de que los datos se soliciten de nuevo mientras se ejecuta la aplicación. El almacenamiento en caché de datos mejora el rendimiento de una aplicación que recupera datos de un servidor remoto a través de objetos de conjunto de registros de tipo dinámico. Cuando se solicitan datos, el motor de base de datos Microsoft Jet comprueba primero la memoria caché de los datos solicitados en lugar de recuperarlos del servidor, lo que lleva más tiempo. Los datos que no proceden de un origen de datos ODBC no se guardan en la memoria caché.

Cualquier origen de datos ODBC, como una tabla adjunta, puede tener una memoria caché local. Para crear la memoria caché, abra un objeto `SetCacheSize` de `SetCacheStart` conjunto de registros `FillCache` desde el origen de datos remoto, llame a las funciones miembro y, a continuación, llame a la función miembro o paso a través de los registros mediante una de las operaciones Move. El *lSize* parámetro `SetCacheSize` de la función miembro se puede basar en el número de registros que la aplicación puede trabajar a la vez. Por ejemplo, si utiliza un conjunto de registros como origen de los `SetCacheSize` datos que se mostrarán en pantalla, podría pasar el parámetro *lSize* como 20 para mostrar 20 registros a la vez.

Para obtener información relacionada, vea el tema "CacheSize, CacheStart Properties" en la Ayuda de DAO.

## <a name="cdaorecordsetsetcachestart"></a><a name="setcachestart"></a>CDaoRecordset::SetCacheStart

Llame a esta función miembro para especificar el marcador del primer registro en el conjunto de registros que se va a almacenar en caché.

```cpp
void SetCacheStart(COleVariant varBookmark);
```

### <a name="parameters"></a>Parámetros

*varBookmark*<br/>
Un [COleVariant](../../mfc/reference/colevariant-class.md) que especifica el marcador del primer registro del conjunto de registros que se va a almacenar en caché.

### <a name="remarks"></a>Observaciones

Puede utilizar el valor de marcador de cualquier `SetCacheStart` registro para el parámetro *varBookmark* de la función miembro. Cree el registro que desea iniciar la memoria caché con el registro actual, establezca un marcador para `SetCacheStart` ese registro mediante [SetBookmark](#setbookmark)y pase el valor del marcador como parámetro para la función miembro.

El motor de base de datos microsoft Jet solicita registros dentro del intervalo de caché de la memoria caché y solicita registros fuera del intervalo de caché desde el servidor.

Los registros recuperados de la memoria caché no reflejan los cambios realizados simultáneamente en los datos de origen por otros usuarios.

Para forzar una actualización de todos los datos `SetCacheSize` almacenados en `SetCacheSize` caché, pase el parámetro *lSize* de 0, vuelva a llamar con el tamaño de la memoria caché que solicitó originalmente y, a continuación, llame a la `FillCache` función miembro.

Tenga en cuenta que si no `COleVariant` está creando un conjunto de registros UNICODE, el objeto debe declararse explícitamente ANSI. Esto se puede hacer mediante la forma [COleVariant::COleVariant](../../mfc/reference/colevariant-class.md#colevariant)**(** *lpszSrc* **,** *vtSrc* **)** de constructor con *vtSrc* establecido en `VT_BSTRT` (ANSI) o mediante la `COleVariant` función [SetString](../../mfc/reference/colevariant-class.md#setstring)**(** *lpszSrc* **,** *vtSrc* **)** con *vtSrc* establecido en . `VT_BSTRT`

Para obtener información relacionada, vea el tema CacheSize, CacheStart Properties" en la Ayuda de DAO.

## <a name="cdaorecordsetsetcurrentindex"></a><a name="setcurrentindex"></a>CDaoRecordset::SetCurrentIndex

Llame a esta función miembro para establecer un índice en un conjunto de registros de tipo de tabla.

```cpp
void SetCurrentIndex(LPCTSTR lpszIndex);
```

### <a name="parameters"></a>Parámetros

*lpszIndex*<br/>
Puntero que contiene el nombre del índice que se va a establecer.

### <a name="remarks"></a>Observaciones

Los registros de las tablas base no se almacenan en un orden determinado. Establecer un índice cambia el orden de los registros devueltos desde la base de datos, pero no afecta al orden en que se almacenan los registros. El índice especificado ya debe estar definido. Si intenta utilizar un objeto de índice que no existe, o si el índice no se establece al llamar a [Seek](#seek), MFC produce una excepción.

Puede crear un nuevo índice para la tabla llamando a [CDaoTableDef::CreateIndex](../../mfc/reference/cdaotabledef-class.md#createindex) y anexando el nuevo índice a la colección Indexes de la tabladef subyacente llamando a [CDaoTableDef::Append](../../mfc/reference/cdaotabledef-class.md#append)y, a continuación, volviendo a abrir el conjunto de registros.

Los registros devueltos desde un conjunto de registros de tipo de tabla solo se pueden ordenar por los índices definidos para la definición de tabla subyacente. Para ordenar los registros en otro orden, puede abrir un conjunto de registros de tipo dinámico o de tipo instantánea mediante una cláusula **ORDERBY** de SQL almacenada en [CDaoRecordset::m_strSort](#m_strsort).

Para obtener información relacionada, vea el tema "Objeto de índice" y la definición "índice actual" en la Ayuda de DAO.

## <a name="cdaorecordsetsetfielddirty"></a><a name="setfielddirty"></a>CDaoRecordset::SetFieldDirty

Llame a esta función miembro para marcar un miembro de datos de campo del conjunto de registros como modificado o como sin cambios.

```cpp
void SetFieldDirty(
    void* pv,
    BOOL bDirty = TRUE);
```

### <a name="parameters"></a>Parámetros

*Pv*<br/>
Contiene la dirección de un miembro de datos de campo en el conjunto de registros o NULL. Si NULL, se marcan todos los miembros de datos de campo del conjunto de registros. (C++ NULL no es lo mismo que Null en la terminología de la base de datos, lo que significa "no tener ningún valor.")

*bDirty*<br/>
TRUESi el miembro de datos de campo debe marcarse como "sucio" (cambiado). De lo contrario, FALSE si el miembro de datos de campo debe marcarse como "limpio" (sin cambios).

### <a name="remarks"></a>Observaciones

Marcar campos como sin cambios garantiza que el campo no se actualice.

Las marcas de marco cambiaron los miembros de datos de campo para asegurarse de que se escribirán en el registro en el origen de datos mediante el mecanismo de intercambio de campos de registros DAO (DFX). Cambiar el valor de un campo generalmente establece el campo sucio `SetFieldDirty` automáticamente, por lo que rara vez tendrá que llamarse a sí mismo, pero a veces es posible que desee asegurarse de que las columnas se actualizarán o insertarán explícitamente independientemente de qué valor se encuentre en el miembro de datos de campo. El mecanismo DFX también emplea el uso de PSEUDONULL. Para obtener más información, vea [CDaoFieldExchange::m_nOperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation).

Si no se utiliza el mecanismo de doble búfer, cambiar el valor del campo no establece automáticamente el campo como sucio. En este caso, será necesario establecer explícitamente el campo como sucio. La marca contenida en [m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields) controla esta comprobación automática de campos.

> [!NOTE]
> Llame a esta función miembro solo después de haber llamado a [Edit](#edit) o [AddNew](#addnew).

El uso de NULL para el primer argumento `outputColumn` de la función `CDaoFieldExchange`aplicará la función a todos los campos, no a los campos **param** de . Por ejemplo, la llamada

[!code-cpp[NVC_MFCDatabase#6](../../mfc/codesnippet/cpp/cdaorecordset-class_6.cpp)]

establecerá solo `outputColumn` los campos en NULL; los campos **de parámetros** no se verán afectados.

Para trabajar en un **parámetro,** debe proporcionar la dirección real del **parámetro** individual en el que desea trabajar, como:

[!code-cpp[NVC_MFCDatabase#7](../../mfc/codesnippet/cpp/cdaorecordset-class_7.cpp)]

Esto significa que no puede establecer todos los `outputColumn` campos **param en** NULL, como puede hacer con los campos.

`SetFieldDirty`se implementa `DoFieldExchange`a través de .

## <a name="cdaorecordsetsetfieldnull"></a><a name="setfieldnull"></a>CDaoRecordset::SetFieldNull

Llame a esta función miembro para marcar un miembro de datos de campo del conjunto de registros como Null (específicamente no tiene ningún valor) o como no Null.

```cpp
void SetFieldNull(
    void* pv,
    BOOL bNull = TRUE);
```

### <a name="parameters"></a>Parámetros

*Pv*<br/>
Contiene la dirección de un miembro de datos de campo en el conjunto de registros o NULL. Si NULL, se marcan todos los miembros de datos de campo del conjunto de registros. (C++ NULL no es lo mismo que Null en la terminología de la base de datos, lo que significa "no tener ningún valor.")

*bNull*<br/>
Distinto de cero si el miembro de datos de campo se marca como que no tiene ningún valor (Null). De lo contrario, 0 si el miembro de datos de campo se va a marcar como no nulo.

### <a name="remarks"></a>Observaciones

`SetFieldNull`se utiliza para los `DoFieldExchange` campos enlazados en el mecanismo.

Cuando se agrega un nuevo registro a un conjunto de registros, todos los miembros de datos de campo se establecen inicialmente en un valor Null y se marcan como "sucio" (cambiado). Cuando se recupera un registro de un origen de datos, sus columnas ya tienen valores o son Null. Si no es adecuado convertir un campo Null, se produce una [excepción CDaoException.](../../mfc/reference/cdaoexception-class.md)

Si está utilizando el mecanismo de almacenamiento en búfer doble, por ejemplo, si desea designar específicamente un campo del registro actual como que no tiene un valor, llame `SetFieldNull` con *bNull* establecido en TRUE para marcarlo como Null. Si un campo se marcó anteriormente como Null y ahora desea darle un valor, simplemente establezca su nuevo valor. No es necesario quitar la `SetFieldNull`marca Null con . Para determinar si el campo puede ser Null, llame a [IsFieldNullable](#isfieldnullable).

Si no está utilizando el mecanismo de doble búfer, cambiar el valor del campo no establece automáticamente el campo como sucio y no nulo. Debe establecer específicamente los campos dirty y non-Null. La marca contenida en [m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields) controla esta comprobación automática de campos.

El mecanismo DFX emplea el uso de PSEUDONULL. Para obtener más información, vea [CDaoFieldExchange::m_nOperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation).

> [!NOTE]
> Llame a esta función miembro solo después de haber llamado a [Edit](#edit) o [AddNew](#addnew).

El uso de NULL para el primer argumento `outputColumn` de la función `CDaoFieldExchange`aplicará la función solo a los campos, no a los campos **param** de . Por ejemplo, la llamada

[!code-cpp[NVC_MFCDatabase#8](../../mfc/codesnippet/cpp/cdaorecordset-class_8.cpp)]

establecerá solo `outputColumn` los campos en NULL; los campos **de parámetros** no se verán afectados.

## <a name="cdaorecordsetsetfieldvalue"></a><a name="setfieldvalue"></a>CDaoRecordset::SetFieldValue

Llame a esta función miembro para establecer el valor de un campo, ya sea por posición ordinal o cambiando el valor de la cadena.

```
virtual void SetFieldValue(
    LPCTSTR lpszName,
    const COleVariant& varValue);

virtual void SetFieldValue(
    int nIndex,
    const COleVariant& varValue);

void SetFieldValue(
    LPCTSTR lpszName,
    LPCTSTR lpszValue);

void SetFieldValue(
    int nIndex,
    LPCTSTR lpszValue);
```

### <a name="parameters"></a>Parámetros

*lpszName*<br/>
Puntero a una cadena que contiene el nombre de un campo.

*varValue*<br/>
Una referencia a un [COleVariant](../../mfc/reference/colevariant-class.md) objeto que contiene el valor del contenido del campo.

*nIndex*<br/>
Entero que representa la posición ordinal del campo en la colección Fields del conjunto de registros (basada en cero).

*lpszValue*<br/>
Puntero a una cadena que contiene el valor del contenido del campo.

### <a name="remarks"></a>Observaciones

Use `SetFieldValue` y [GetFieldValue](#getfieldvalue) para enlazar campos dinámicamente en tiempo de ejecución en lugar de enlazar columnas estáticamente mediante el mecanismo [DoFieldExchange.](#dofieldexchange)

Tenga en cuenta que si no va a crear `SetFieldValue` un conjunto de `COleVariant` registros `COleVariant` UNICODE, debe usar una forma que no contenga un parámetro o el objeto debe declararse explícitamente ANSI. Esto se puede hacer mediante la forma [COleVariant::COleVariant](../../mfc/reference/colevariant-class.md#colevariant)**(** *lpszSrc* **,** *vtSrc* **)** de constructor con *vtSrc* establecido en `VT_BSTRT` (ANSI) o mediante la `COleVariant` función [SetString](../../mfc/reference/colevariant-class.md#setstring)**(** *lpszSrc* **,** *vtSrc* **)** con *vtSrc* establecido en . `VT_BSTRT`

Para obtener información relacionada, vea los temas "Objeto de campo" y "Propiedad de valor" en la Ayuda de DAO.

## <a name="cdaorecordsetsetfieldvaluenull"></a><a name="setfieldvaluenull"></a>CDaoRecordset::SetFieldValueNull

Llame a esta función miembro para establecer el campo en un Null valor.

```cpp
void SetFieldValueNull(int nIndex);
void SetFieldValueNull(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
El índice del campo en el conjunto de registros, para la búsqueda por índice de base cero.

*lpszName*<br/>
El nombre del campo en el conjunto de registros, para la búsqueda por nombre.

### <a name="remarks"></a>Observaciones

C++ NULL no es lo mismo que Null, que, en terminología de base de datos, significa "no tener ningún valor."

Para obtener información relacionada, vea los temas "Objeto de campo" y "Propiedad de valor" en la Ayuda de DAO.

## <a name="cdaorecordsetsetlockingmode"></a><a name="setlockingmode"></a>CDaoRecordset::SetLockingMode

Llame a esta función miembro para establecer el tipo de bloqueo para el conjunto de registros.

```cpp
void SetLockingMode(BOOL bPessimistic);
```

### <a name="parameters"></a>Parámetros

*bPessimistic*<br/>
Marca que indica el tipo de bloqueo.

### <a name="remarks"></a>Observaciones

Cuando el bloqueo pesimista está en vigor, la página 2K que contiene `Edit` el registro que está editando se bloquea tan pronto como se llama a la función miembro. La página se desbloquea cuando `Update` `Close` se llama a la o función miembro o cualquiera de las operaciones Mover o Buscar.

Cuando el bloqueo optimista está en vigor, la página 2K que contiene `Update` el registro se bloquea solo mientras se actualiza el registro con la función miembro.

Si una página está bloqueada, ningún otro usuario puede editar registros en la misma página. Si llama `SetLockingMode` y pasa un valor distinto de cero y otro usuario ya `Edit`tiene la página bloqueada, se produce una excepción al llamar a . Otros usuarios pueden leer datos de páginas bloqueadas.

Si llama `SetLockingMode` con un valor `Update` cero y más tarde llama mientras la página está bloqueada por otro usuario, se produce una excepción. Para ver los cambios realizados en el registro por `SetBookmark` otro usuario (y perder los cambios), llame a la función miembro con el valor de marcador del registro actual.

Cuando se trabaja con orígenes de datos ODBC, el modo de bloqueo siempre es optimista.

## <a name="cdaorecordsetsetparamvalue"></a><a name="setparamvalue"></a>CDaoRecordset::SetParamValue

Llame a esta función miembro para establecer el valor de un parámetro en el conjunto de registros en tiempo de ejecución.

```
virtual void SetParamValue(
    int nIndex,
    const COleVariant& varValue);

virtual void SetParamValue(
    LPCTSTR lpszName,
    const COleVariant& varValue);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
La posición numérica del parámetro en la colección Parameters de la definición de consulta.

*var*<br/>
El valor que se va a establecer; ver Comentarios.

*lpszName*<br/>
El nombre del parámetro cuyo valor desea establecer.

### <a name="remarks"></a>Observaciones

El parámetro ya debe haberse establecido como parte de la cadena SQL del conjunto de registros. Puede tener acceso al parámetro por nombre o por su posición de índice en la colección.

Especifique el valor que `COleVariant` se va a establecer como un objeto. Para obtener información sobre cómo establecer `COleVariant` el valor y el tipo deseados en el objeto, vea la clase [COleVariant](../../mfc/reference/colevariant-class.md). Tenga en cuenta que si no `COleVariant` está creando un conjunto de registros UNICODE, el objeto debe declararse explícitamente ANSI. Esto se puede hacer mediante la forma [COleVariant::COleVariant](../../mfc/reference/colevariant-class.md#colevariant)**(** *lpszSrc* **,** *vtSrc* **)** de constructor con *vtSrc* establecido en `VT_BSTRT` (ANSI) o mediante la `COleVariant` función [SetString](../../mfc/reference/colevariant-class.md#setstring)**(** *lpszSrc* **,** *vtSrc* **)** con *vtSrc* establecido en . `VT_BSTRT`

## <a name="cdaorecordsetsetparamvaluenull"></a><a name="setparamvaluenull"></a>CDaoRecordset::SetParamValueNull

Llame a esta función miembro para establecer el parámetro en un Null valor.

```cpp
void SetParamValueNull(int nIndex);
void SetParamValueNull(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
El índice del campo en el conjunto de registros, para la búsqueda por índice de base cero.

*lpszName*<br/>
El nombre del campo en el conjunto de registros, para la búsqueda por nombre.

### <a name="remarks"></a>Observaciones

C++ NULL no es lo mismo que Null, que, en terminología de base de datos, significa "no tener ningún valor."

## <a name="cdaorecordsetsetpercentposition"></a><a name="setpercentposition"></a>CDaoRecordset::SetPercentPosition

Llame a esta función miembro para establecer un valor que cambia la ubicación aproximada del registro actual en el objeto de conjunto de registros en función de un porcentaje de los registros en el conjunto de registros.

```cpp
void SetPercentPosition(float fPosition);
```

### <a name="parameters"></a>Parámetros

*fPosición*<br/>
Número comprendido entre 0 y 100.

### <a name="remarks"></a>Observaciones

Al trabajar con un conjunto de registros de tipo dinámico o de tipo `SetPercentPosition`instantánea, rellene primero el conjunto de registros pasando al último registro antes de llamar a . Si llama `SetPercentPosition` antes de rellenar completamente el conjunto de registros, la cantidad de movimiento es relativa al número de registros a los que se tiene acceso según lo indicado por el valor de [GetRecordCount](#getrecordcount). Puede pasar al último registro `MoveLast`llamando a .

Una vez `SetPercentPosition`que se llama , el registro en la posición aproximada correspondiente a ese valor se convierte en actual.

> [!NOTE]
> No `SetPercentPosition` se recomienda llamar para mover el registro actual a un registro específico de un conjunto de registros. Llame a la [SetBookmark](#setbookmark) función miembro en su lugar.

Para obtener información relacionada, vea el tema "Propiedad PercentPosition" en la Ayuda de DAO.

## <a name="cdaorecordsetupdate"></a><a name="update"></a>CDaoRecordset::Update

Llame a esta función `AddNew` miembro `Edit` después de una llamada a la o función miembro.

```
virtual void Update();
```

### <a name="remarks"></a>Observaciones

Esta llamada es necesaria `AddNew` `Edit` para completar la operación.

`Edit` Preparar `AddNew` un búfer de edición en el que se colocan los datos agregados o editados para guardarlos en el origen de datos. `Update`guarda los datos. Solo se actualizan los campos marcados o detectados como modificados.

Si el origen de datos admite `Update` transacciones, puede `AddNew` `Edit` hacer que la llamada (y su correspondiente o llamada) forme parte de una transacción.

> [!CAUTION]
> Si llama `Update` sin `AddNew` llamar `Edit` `Update` primero a `CDaoException`cualquiera o , lanza un archivo . Si llama `AddNew` `Edit`o , `Update` debe llamar antes de llamar a [MoveNext](#movenext) o cerrar el conjunto de registros o la conexión de origen de datos. De lo contrario, los cambios se pierden sin notificación.

Cuando el objeto de conjunto de registros se bloquea de forma pesimista en un entorno multiusuario, el registro permanece bloqueado desde el momento `Edit` en que se completa la actualización. Si el conjunto de registros está bloqueado de forma optimista, el registro se bloquea y se compara con el registro preeditado justo antes de que se actualice en la base de datos. Si el registro ha `Edit`cambiado `Update` desde que llamó , se produce un error en la operación y MFC produce una excepción. Puede cambiar el modo `SetLockingMode`de bloqueo con .

> [!NOTE]
> El bloqueo optimista siempre se utiliza en formatos de base de datos externos, como ODBC e ISAM instalable.

Para obtener información relacionada, vea los temas "AddNew Method", "CancelUpdate Method", "Delete Method", "LastModified Property", "Update Method" y "EditMode Property" en la Ayuda de DAO.

## <a name="see-also"></a>Vea también

[Clase CObject](../../mfc/reference/cobject-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CDaoTableDef (clase)](../../mfc/reference/cdaotabledef-class.md)<br/>
[Clase CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md)<br/>
[CDaoDatabase (clase)](../../mfc/reference/cdaodatabase-class.md)<br/>
[Clase CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)<br/>
