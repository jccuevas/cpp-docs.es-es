---
title: CDaoRecordset (clase) | Microsoft Docs
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d31e61dcddeca7e27370dd293056ebcf990d9ef7
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50068370"
---
# <a name="cdaorecordset-class"></a>CDaoRecordset (clase)

Representa un conjunto de registros seleccionados de un origen de datos.

## <a name="syntax"></a>Sintaxis

```
class CDaoRecordset : public CObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CDaoRecordset::CDaoRecordset](#cdaorecordset)|Construye un objeto `CDaoRecordset`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CDaoRecordset:: AddNew](#addnew)|Se prepara para agregar un nuevo registro. Llame a [actualización](#update) para completar la incorporación.|
|[CDaoRecordset::CanAppend](#canappend)|Devuelve cero si se pueden agregar nuevos registros en el conjunto de registros a través de la [AddNew](#addnew) función miembro.|
|[CDaoRecordset:: CanBookmark](#canbookmark)|Devuelve cero si el conjunto de registros admite marcadores.|
|[CDaoRecordset::CancelUpdate](#cancelupdate)|Cancela cualquier actualización pendiente debido a un [editar](#edit) o [AddNew](#addnew) operación.|
|[CDaoRecordset::CanRestart](#canrestart)|Devuelve cero si [Requery](#requery) puede llamarse para volver a ejecutar la consulta.|
|[CDaoRecordset::CanScroll](#canscroll)|Devuelve cero si puede desplazarse por los registros.|
|[CDaoRecordset::CanTransact](#cantransact)|Devuelve cero si el origen de datos admite transacciones.|
|[CDaoRecordset::CanUpdate](#canupdate)|Devuelve cero si se puede actualizar el conjunto de registros (puede agregar, actualizar o eliminar registros).|
|[CDaoRecordset::Close](#close)|Cierra el conjunto de registros.|
|[CDaoRecordset::Delete](#delete)|Elimina el registro actual del conjunto de registros. Explícitamente, debe desplazarse a otro registro después de la eliminación.|
|[CDaoRecordset](#dofieldexchange)|Se llama para intercambiar datos (en ambas direcciones) entre los miembros de datos de campo del conjunto de registros y el registro correspondiente en el origen de datos. Implementa DAO campo intercambio registros (DFX).|
|[CDaoRecordset:: Edit](#edit)|Prepara los cambios en el registro actual. Llame a `Update` para completar la edición.|
|[CDaoRecordset:: FillCache](#fillcache)|Llena todo o parte de una caché local para un objeto de conjunto de registros que contiene los datos de un origen de datos ODBC.|
|[CDaoRecordset::Find](#find)|Busca la primera, siguiente, anterior, o la última ubicación de una cadena concreta en un conjunto de registros de tipo dinámico que satisface los criterios especificados y hace que el registro en el registro actual.|
|[CDaoRecordset::FindFirst](#findfirst)|Busca el primer registro en un tipo dinámico o un conjunto de registros de tipo de instantánea que satisface los criterios especificados y hace que el registro en el registro actual.|
|[CDaoRecordset::FindLast](#findlast)|Busca el último registro en un tipo dinámico o un conjunto de registros de tipo de instantánea que satisface los criterios especificados y hace que el registro en el registro actual.|
|[CDaoRecordset::FindNext](#findnext)|Busca el siguiente registro en un tipo dinámico o un conjunto de registros de tipo de instantánea que satisface los criterios especificados y hace que el registro en el registro actual.|
|[CDaoRecordset::FindPrev](#findprev)|Busca el registro anterior en un tipo dinámico o un conjunto de registros de tipo de instantánea que satisface los criterios especificados y hace que el registro en el registro actual.|
|[CDaoRecordset:: GetAbsolutePosition](#getabsoluteposition)|Devuelve el número de registro del registro actual del objeto de un conjunto de registros.|
|[CDaoRecordset:: GetBookmark](#getbookmark)|Devuelve un valor que representa el marcador en un registro.|
|[CDaoRecordset::GetCacheSize](#getcachesize)|Devuelve un valor que especifica el número de registros en un conjunto de registros de tipo dinámico que contiene datos para almacenar en caché localmente desde un origen de datos ODBC.|
|[CDaoRecordset::GetCacheStart](#getcachestart)|Devuelve un valor que especifica el marcador del primer registro en el conjunto de registros en la memoria caché.|
|[CDaoRecordset::GetCurrentIndex](#getcurrentindex)|Devuelve un `CString` que contiene el nombre del índice más recientemente usa un tipo de tabla indizada, `CDaoRecordset`.|
|[CDaoRecordset::GetDateCreated](#getdatecreated)|Devuelve la fecha y hora de la tabla base subyacente un `CDaoRecordset` se creó el objeto|
|[CDaoRecordset::GetDateLastUpdated](#getdatelastupdated)|Devuelve la fecha y hora de los cambios más recientes realizados en el diseño de una tabla base subyacente un `CDaoRecordset` objeto.|
|[CDaoRecordset::GetDefaultDBName](#getdefaultdbname)|Devuelve el nombre del origen de datos de forma predeterminada.|
|[CDaoRecordset::GetDefaultSQL](#getdefaultsql)|Se llama para obtener la cadena SQL predeterminada para ejecutar.|
|[CDaoRecordset::GetEditMode](#geteditmode)|Devuelve un valor que indica el estado de edición para el registro actual.|
|[CDaoRecordset::GetFieldCount](#getfieldcount)|Devuelve un valor que representa el número de campos de un conjunto de registros.|
|[CDaoRecordset::GetFieldInfo](#getfieldinfo)|Devuelve los tipos concretos de información sobre los campos del conjunto de registros.|
|[CDaoRecordset:: GetFieldValue](#getfieldvalue)|Devuelve el valor de un campo en un conjunto de registros.|
|[CDaoRecordset::GetIndexCount](#getindexcount)|Recupera el número de índices en una tabla subyacente de un conjunto de registros.|
|[CDaoRecordset::GetIndexInfo](#getindexinfo)|Devuelve diversos tipos de información acerca de un índice.|
|[CDaoRecordset::GetLastModifiedBookmark](#getlastmodifiedbookmark)|Se usa para determinar el último agrega o actualiza el registro.|
|[CDaoRecordset::GetLockingMode](#getlockingmode)|Devuelve un valor que indica el tipo de bloqueo que está vigente durante la edición.|
|[CDaoRecordset::GetName](#getname)|Devuelve un `CString` que contiene el nombre del conjunto de registros.|
|[CDaoRecordset::GetParamValue](#getparamvalue)|Recupera el valor actual del parámetro especificado almacenado en el objeto DAOParameter subyacente.|
|[CDaoRecordset:: GetPercentPosition](#getpercentposition)|Devuelve la posición del registro actual como un porcentaje del número total de registros.|
|[CDaoRecordset::GetRecordCount](#getrecordcount)|Devuelve el número de registros que se obtiene acceso en un objeto de conjunto de registros.|
|[CDaoRecordset::GetSQL](#getsql)|Obtiene la cadena SQL que se utiliza para seleccionar registros del conjunto de registros.|
|[CDaoRecordset::GetType](#gettype)|Se llama para determinar el tipo de un conjunto de registros: tipo de tabla, tipo dinámico o tipo de instantánea.|
|[CDaoRecordset::GetValidationRule](#getvalidationrule)|Devuelve un `CString` que contiene el valor que valida los datos mientras se escribe en un campo.|
|[CDaoRecordset::GetValidationText](#getvalidationtext)|Recupera el texto que se muestra cuando no se cumple una regla de validación.|
|[CDaoRecordset::IsBOF](#isbof)|Devuelve cero si el conjunto de registros se ha posicionado antes del primer registro. No hay ningún registro actual.|
|[CDaoRecordset::IsDeleted](#isdeleted)|Devuelve cero si el conjunto de registros se coloca en un registro eliminado.|
|[CDaoRecordset::IsEOF](#iseof)|Devuelve cero si se ha colocado el conjunto de registros después del último registro. No hay ningún registro actual.|
|[CDaoRecordset::IsFieldDirty](#isfielddirty)|Devuelve cero si se ha cambiado el campo especificado en el registro actual.|
|[CDaoRecordset::IsFieldNull](#isfieldnull)|Devuelve cero si el campo especificado en el registro actual es Null (con ningún valor).|
|[CDaoRecordset::IsFieldNullable](#isfieldnullable)|Devuelve cero si el campo especificado en el registro actual se puede establecer en Null (con ningún valor).|
|[CDaoRecordset::IsOpen](#isopen)|Devuelve cero si [abierto](#open) se ha llamado previamente.|
|[CDaoRecordset:: Move](#move)|Coloca el conjunto de registros a un número especificado de registros desde el registro actual en cualquier dirección.|
|[CDaoRecordset::MoveFirst](#movefirst)|Coloca el registro actual en el primer registro en el conjunto de registros.|
|[CDaoRecordset::MoveLast](#movelast)|Coloca el registro actual en el último registro del conjunto de registros.|
|[CDaoRecordset::MoveNext](#movenext)|Coloca el registro actual en el registro siguiente en el conjunto de registros.|
|[CDaoRecordset::MovePrev](#moveprev)|Coloca el registro actual en el registro anterior en el conjunto de registros.|
|[CDaoRecordset:: Open](#open)|Crea un nuevo conjunto de registros de una tabla, un tipo dinámico o una instantánea.|
|[CDaoRecordset::Requery](#requery)|Ejecuta la consulta del conjunto de registros nuevo para actualizar los registros seleccionados.|
|[CDaoRecordset::Seek](#seek)|Localiza el registro de un objeto de conjunto de registros de tipo tabla indizada que satisface los criterios especificados para el índice actual y hace que el registro en el registro actual.|
|[CDaoRecordset:: SetAbsolutePosition](#setabsoluteposition)|Establece el número de registro del registro actual del objeto de un conjunto de registros.|
|[CDaoRecordset:: SetBookmark](#setbookmark)|Coloca el conjunto de registros en un registro que contiene el marcador especificado.|
|[CDaoRecordset:: SetCacheSize](#setcachesize)|Establece un valor que especifica el número de registros en un conjunto de registros de tipo dinámico que contiene datos para almacenar en caché localmente desde un origen de datos ODBC.|
|[CDaoRecordset:: SetCacheStart](#setcachestart)|Establece un valor que especifica el marcador del primer registro en el conjunto de registros en la memoria caché.|
|[CDaoRecordset:: SetCurrentIndex](#setcurrentindex)|Se llama para establecer un índice en un conjunto de registros de tipo de tabla.|
|[CDaoRecordset:: SetFieldDirty](#setfielddirty)|Marca el campo especificado en el registro actual como modificada.|
|[CDaoRecordset::SetFieldNull](#setfieldnull)|Establece el valor del campo especificado en el registro actual en Null (con ningún valor).|
|[CDaoRecordset::SetFieldValue](#setfieldvalue)|Establece el valor de un campo en un conjunto de registros.|
|[CDaoRecordset::SetFieldValueNull](#setfieldvaluenull)|Establece el valor de un campo en un conjunto de registros en Null. (con ningún valor).|
|[CDaoRecordset::SetLockingMode](#setlockingmode)|Establece un valor que indica el tipo de bloqueo para poner en efecto durante la edición.|
|[CDaoRecordset::SetParamValue](#setparamvalue)|Establece el valor actual del parámetro especificado almacenado en el objeto subyacente de DAOParameter|
|[CDaoRecordset::SetParamValueNull](#setparamvaluenull)|El valor actual del parámetro especificado se establece en Null (con ningún valor).|
|[CDaoRecordset:: SetPercentPosition](#setpercentposition)|Establece la posición del registro actual en una ubicación correspondiente a un porcentaje del número total de registros en un conjunto de registros.|
|[CDaoRecordset::Update](#update)|Se completa una `AddNew` o `Edit` operación guardando los datos nuevos o modificados del origen de datos.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[CDaoRecordset:: M_bcheckcachefordirtyfields](#m_bcheckcachefordirtyfields)|Contiene una marca que indica si los campos se marcan automáticamente como modificado.|
|[CDaoRecordset::m_nFields](#m_nfields)|Contiene el número de miembros de datos en la clase de conjunto de registros y el número de columnas seleccionadas por el conjunto de registros del origen de datos.|
|[CDaoRecordset::m_nParams](#m_nparams)|Contiene el número de miembros de datos de parámetro en la clase de conjunto de registros: el número de parámetros pasados con la consulta del conjunto de registros|
|[CDaoRecordset::m_pDAORecordset](#m_pdaorecordset)|Un puntero a la interfaz DAO subyacente al objeto de conjunto de registros.|
|[CDaoRecordset::m_pDatabase](#m_pdatabase)|Base de datos de origen para este conjunto de resultados. Contiene un puntero a un [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) objeto.|
|[CDaoRecordset:: M_strfilter](#m_strfilter)|Contiene una cadena utilizada para construir una instancia de SQL **donde** instrucción.|
|[CDaoRecordset::m_strSort](#m_strsort)|Contiene una cadena utilizada para construir una instancia de SQL **ORDER BY** instrucción.|

## <a name="remarks"></a>Comentarios

Conocida como "conjuntos de registros," `CDaoRecordset` objetos están disponibles en las tres formas siguientes:

- Conjuntos de registros de tipo de tabla representan una tabla base que puede usar para examinar, agregar, cambiar o eliminar registros de una tabla de base de datos única.

- Conjuntos de registros de tipo dinámico son el resultado de una consulta que puede tener registros actualizables. Estos conjuntos de registros son un conjunto de registros que puede usar para examinar, agregar, cambiar o eliminar registros de una tabla de base de datos subyacente o tablas. Conjuntos de registros de tipo dinámico pueden contener campos de una o varias tablas en una base de datos.

- Conjuntos de registros de tipo de instantánea son una copia estática de un conjunto de registros que puede usar para buscar datos o generar informes. Estos conjuntos de registros pueden contener campos de una o varias tablas en una base de datos, pero no se puede actualizar.

Cada formulario de conjunto de registros representa un conjunto de registros que se fija en el momento en que se abre el conjunto de registros. Cuando se desplaza a un registro en un conjunto de registros de tipo de tabla o un conjunto de registros de tipo dinámico, refleja los cambios realizados en el registro después de abre el conjunto de registros, por otros usuarios o por otros conjuntos de registros en la aplicación. (No se puede actualizar un conjunto de registros de tipo de instantánea). Puede usar `CDaoRecordset` directamente o derivar una clase de conjunto de registros específicos de la aplicación de `CDaoRecordset`. A continuación, puede:

- Desplazarse por los registros.

- Establecer un índice y buscar rápidamente los registros mediante [Seek](#seek) (sólo para conjuntos de registros de tipo de tabla).

- Buscar registros según una comparación de cadenas: "<","\<=", "=", "> =", o ">" (tipo de conjunto de registros dinámicos y conjuntos de registros de tipo de instantánea).

- Actualizar los registros y especificar un modo de bloqueo (excepto los conjuntos de registros de tipo de instantánea).

- Filtrar el conjunto de registros para limitar los registros que selecciona desde los que están disponibles en el origen de datos.

- Ordenar el conjunto de registros.

- Parametrizar el conjunto de registros para personalizar su selección con información no conocida hasta el tiempo de ejecución.

Clase `CDaoRecordset` proporciona una interfaz similar a la de la clase `CRecordset`. La principal diferencia es que esa clase `CDaoRecordset` tiene acceso a datos a través de un objeto de acceso de datos (DAO) en función de OLE. Clase `CRecordset` tiene acceso a la instancia de DBMS a través de Open Database Connectivity (ODBC) y un controlador ODBC para ese DBMS.

> [!NOTE]
> Las clases de base de datos DAO son distintas de las clases de base de datos MFC basadas en Open Database Connectivity (ODBC). Todos los nombres de clase de base de datos DAO tienen el prefijo "CDao". También puede seguir acceso a orígenes de datos ODBC con las clases DAO; las clases DAO normalmente ofrecen capacidades superior porque son específicas para el motor de base de datos Microsoft Jet.

Puede usar `CDaoRecordset` directamente o derivar una clase de `CDaoRecordset`. Para usar una clase de conjunto de registros en cualquier caso, abrir una base de datos y construir un objeto de conjunto de registros, pasando el constructor de un puntero a su `CDaoDatabase` objeto. También se puede construir un `CDaoRecordset` objeto y dejar que MFC crea un archivo temporal `CDaoDatabase` objeto automáticamente. A continuación, llame el conjunto de registros [abierto](#open) función miembro, especificando si el objeto es un conjunto de registros de tipo de tabla, un conjunto de registros de tipo dinámico o un conjunto de registros de tipo de instantánea. Una llamada a `Open` selecciona datos de la base de datos y recupera el primer registro.

Usar a miembros de datos y funciones de miembro del objeto para desplazarse por los registros y operar con ellas. Las operaciones disponibles dependen de si el objeto es un conjunto de registros de tipo de tabla, un conjunto de registros de tipo dinámico o un conjunto de registros de tipo de instantánea y, si es actualizable o de solo lectura, esto depende de la capacidad de la base de datos o Open Database Connectivity (ODBC) origen de datos. Para actualizar los registros que se han cambiado o agregado desde la `Open` llamada, llamar al objeto [Requery](#requery) función miembro. Llamar al objeto `Close` miembro de función y destruir el objeto cuando termine con él.

`CDaoRecordset` intercambio de campos de registros DAO (DFX) se utiliza para admitir la lectura y actualización de campos de registro a través de los miembros de C++ con seguridad de tipos de su `CDaoRecordset` o `CDaoRecordset`-clase derivada. También puede implementar el enlace dinámico de columnas en una base de datos sin usar el mecanismo de uso DFX [GetFieldValue](#getfieldvalue) y [SetFieldValue](#setfieldvalue).

Para obtener información relacionada, vea el tema "Objeto de conjunto de registros" en la Ayuda de DAO.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

`CDaoRecordset`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdao.h

##  <a name="addnew"></a>  CDaoRecordset:: AddNew

Llame a esta función miembro para agregar un nuevo registro a un conjunto de registros de tipo de tabla o de tipo dinámico.

```
virtual void AddNew();
```

### <a name="remarks"></a>Comentarios

Los campos del registro son inicialmente Null. (En la terminología de base de datos, Null significa "no tener ningún valor" y no es igual a NULL en C++). Para completar la operación, debe llamar a la [actualización](#update) función miembro. `Update` guarda los cambios en el origen de datos.

> [!CAUTION]
>  Si edita un registro y, a continuación, desplácese a otro registro sin llamar a `Update`, los cambios se perderán sin previo aviso.

Si agregar un registro a un conjunto de registros de tipo dinámico mediante una llamada a [AddNew](#addnew), el registro es visible en el conjunto de registros y se incluye en la tabla subyacente donde estará visible para cualquier nuevo `CDaoRecordset` objetos.

La posición del nuevo registro depende del tipo de conjunto de registros:

- En un tipo de conjunto de registros dinámicos no se garantiza el conjunto de registros, donde se insertó el nuevo registro. Este comportamiento puede cambiado con Microsoft Jet 3.0 por motivos de rendimiento y simultaneidad. Si su objetivo es convertir el registro actual en el registro recién agregado, obtenga el marcador del último registro modificado y mover a ese marcador:

[!code-cpp[NVC_MFCDatabase#1](../../mfc/codesnippet/cpp/cdaorecordset-class_1.cpp)]

- En un conjunto de registros de tipo de tabla para la que se ha especificado un índice, se devuelven registros en su lugar adecuado en el criterio de ordenación. Si no se ha especificado ningún índice, se devuelven registros nuevos al final del conjunto de registros.

El registro que era actual antes de utilizar `AddNew` sigue siendo el actual. Si desea que el nuevo registro actual y el conjunto de registros admite marcadores, llamada [SetBookmark](#setbookmark) en el marcador identificado por el valor de propiedad LastModified del objeto de conjunto de registros DAO subyacente. Si lo hace, es útil para determinar el valor de los campos de contador (incremento automático) en un registro se ha agregado. Para obtener más información, consulte [GetLastModifiedBookmark](#getlastmodifiedbookmark).

Si la base de datos admite transacciones, puede hacer que su `AddNew` llame a parte de una transacción. Para obtener más información acerca de las transacciones, vea la clase [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md). Tenga en cuenta que debe llamar a [CDaoWorkspace::BeginTrans](../../mfc/reference/cdaoworkspace-class.md#begintrans) antes de llamar a `AddNew`.

No es válido llamar a `AddNew` para un conjunto de registros cuyo [abierto](#open) no se llamó la función de miembro. Un `CDaoException` se produce si se llama a `AddNew` para un conjunto de registros que no se puede anexar. Puede determinar si el conjunto de registros es actualizable llamando [CanAppend](#canappend).

Las marcas de marco de trabajo puede cambiar los miembros de datos de campo para asegurarse de que se escribirá en el registro del origen de datos mediante el mecanismo de intercambio (DFX) de campos de registros DAO. Cambiar el valor de un campo normalmente establece el campo desfasadas automáticamente, por lo que rara vez necesitará llamar a [SetFieldDirty](#setfielddirty) usted mismo, pero a veces, conviene asegurarse de que las columnas se explícitamente actualizadas o insertadas en cualquier caso de qué valor está en el miembro de datos de campo. El mecanismo DFX también emplea el uso de **PSEUDO NULL**. Para obtener más información, consulte [CDaoFieldExchange:: M_noperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation).

Si no se utiliza el mecanismo de almacenamiento en búfer doble, a continuación, cambiar el valor del campo no establece automáticamente el campo como modificado. En este caso, será necesario establecer explícitamente el campo de datos sucios. La marca contenida en [m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields) controla la comprobación automática de campos.

> [!NOTE]
> Si hay registros doble búfer (es decir, la comprobación automática de campos está habilitada), una llamada a `CancelUpdate` restaurará las variables de miembro para los valores que tenían antes de `AddNew` o `Edit` llamó.

Para obtener información relacionada, vea los temas "Método AddNew", "Método CancelUpdate", "Propiedad LastModified" y "Propiedad EditMode" en la Ayuda de DAO.

##  <a name="canappend"></a>  CDaoRecordset::CanAppend

Llame a esta función miembro para determinar si el conjunto de registros abierto anteriormente le permite agregar nuevos registros mediante una llamada a la [AddNew](#addnew) función miembro.

```
BOOL CanAppend() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el conjunto de registros permite agregar nuevos registros; en caso contrario, es 0. `CanAppend` Devuelve 0 si se abre el conjunto de registros como de solo lectura.

### <a name="remarks"></a>Comentarios

Para obtener información relacionada, vea el tema "Método Append" en la Ayuda de DAO.

##  <a name="canbookmark"></a>  CDaoRecordset:: CanBookmark

Llame a esta función miembro para determinar si el conjunto de registros abierto anteriormente le permite marcar individualmente los registros de uso de marcadores.

```
BOOL CanBookmark();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el conjunto de registros admite marcadores, de lo contrario, 0.

### <a name="remarks"></a>Comentarios

Si usa conjuntos de registros que se basa íntegramente en tablas del motor de base de datos Microsoft Jet, pueden utilizar marcadores, excepto en conjuntos de registros de tipo de instantánea marcados como conjuntos de registros de desplazamiento solo hacia delante. Otros productos de base de datos (orígenes de datos ODBC externos) pueden no admitir marcadores.

Para obtener información relacionada, vea el tema "Propiedad es" en la Ayuda de DAO.

##  <a name="cancelupdate"></a>  CDaoRecordset::CancelUpdate

El `CancelUpdate` función miembro cancela cualquier actualización pendiente debido a un [editar](#edit) o [AddNew](#addnew) operación.

```
virtual void CancelUpdate();
```

### <a name="remarks"></a>Comentarios

Por ejemplo, si una aplicación llama a la `Edit` o `AddNew` función miembro y no ha llamado a [actualización](#update), `CancelUpdate` cancela los cambios efectuados después `Edit` o `AddNew` llamó.

> [!NOTE]
>  Si hay registros doble búfer (es decir, la comprobación automática de campos está habilitada), una llamada a `CancelUpdate` restaurará las variables de miembro para los valores que tenían antes de `AddNew` o `Edit` llamó.

Si no hay ningún `Edit` o `AddNew` operación pendiente, `CancelUpdate` hace que MFC producir una excepción. Llame a la [GetEditMode](#geteditmode) función miembro para determinar si hay una operación pendiente que puede cancelarse.

Para obtener información relacionada, vea el tema "Método CancelUpdate" en la Ayuda de DAO.

##  <a name="canrestart"></a>  CDaoRecordset::CanRestart

Llame a esta función miembro para determinar si el conjunto de registros permite reiniciar su consulta (para actualizar sus registros) mediante una llamada a la `Requery` función miembro.

```
BOOL CanRestart();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si `Requery` se puede llamar para ejecutar la consulta de nuevo, en caso contrario, 0.

### <a name="remarks"></a>Comentarios

No se admiten conjuntos de registros de tipo de tabla `Requery`.

Si `Requery` no es se admite llamar a [cerrar](#close) , a continuación, [abierto](#open) para actualizar los datos. Puede llamar a `Requery` actualizar un objeto de conjunto de registros subyacente de la consulta de parámetros después de que se han cambiado los valores de parámetro.

Para obtener información relacionada, vea el tema "Propiedad reiniciable" en la Ayuda de DAO.

##  <a name="canscroll"></a>  CDaoRecordset::CanScroll

Llame a esta función miembro para determinar si el conjunto de registros permite el desplazamiento.

```
BOOL CanScroll() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si puede desplazarse por los registros, de lo contrario, 0.

### <a name="remarks"></a>Comentarios

Si se llama a [abierto](#open) con `dbForwardOnly`, puede que el conjunto de registros solo hacia delante.

Para obtener información relacionada, vea el tema "Colocar el puntero de registro actual con DAO" en la Ayuda de DAO.

##  <a name="cantransact"></a>  CDaoRecordset::CanTransact

Llame a esta función miembro para determinar si el conjunto de registros permite que las transacciones.

```
BOOL CanTransact();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el origen de datos subyacente admite transacciones, de lo contrario, 0.

### <a name="remarks"></a>Comentarios

Para obtener información relacionada, vea el tema "Propiedad de transacciones" en la Ayuda de DAO.

##  <a name="canupdate"></a>  CDaoRecordset::CanUpdate

Llame a esta función miembro para determinar si se puede actualizar el conjunto de registros.

```
BOOL CanUpdate() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se puede actualizar el conjunto de registros (agregar, actualizar y eliminar registros), en caso contrario, 0.

### <a name="remarks"></a>Comentarios

Un conjunto de registros puede ser de sólo lectura si el origen de datos subyacente es de solo lectura o si especifica `dbReadOnly` para *nOptions* cuando llama a [abierto](#open) para el conjunto de registros.

Para obtener información relacionada, vea los temas "Método AddNew", "Editar método", "Método Delete", "Método de actualización" y "Propiedad actualizable" en la Ayuda de DAO.

##  <a name="cdaorecordset"></a>  CDaoRecordset::CDaoRecordset

Construye un objeto `CDaoRecordset`.

```
CDaoRecordset(CDaoDatabase* pDatabase = NULL);
```

### <a name="parameters"></a>Parámetros

*pDatabase*<br/>
Contiene un puntero a un [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) objeto o el valor NULL. Si no es NULL y el `CDaoDatabase` del objeto `Open` función miembro no se ha llamado para conectarlo al origen de datos, el objeto recordset intenta abrir automáticamente durante su propia [abrir](#open) llamar. Si se pasa NULL, un `CDaoDatabase` objeto se construye y se conecta automáticamente con la información de origen de datos especificado si deriva de la clase de conjunto de registros de `CDaoRecordset`.

### <a name="remarks"></a>Comentarios

Puede usar `CDaoRecordset` directamente o derivar una clase específica de la aplicación de `CDaoRecordset`. Puede usar ClassWizard para derivar las clases de conjunto de registros.

> [!NOTE]
>  Si deriva una `CDaoRecordset` clase, la derivada clase debe proporcionar su propio constructor. En el constructor de la clase derivada, llame al constructor `CDaoRecordset::CDaoRecordset`, pasando los parámetros adecuados junto a él.

Pasar NULL para el constructor del conjunto de registros para tener un `CDaoDatabase` objeto construido y conecta automáticamente para usted. Se trata de un acceso directo que no requiere que se va a construir y conectar un `CDaoDatabase` objeto antes de construir el conjunto de registros. Si el `CDaoDatabase` objeto no está abierto, un [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md) también se creará el objeto que usa el área de trabajo predeterminada. Para obtener más información, consulte [CDaoDatabase::CDaoDatabase](../../mfc/reference/cdaodatabase-class.md#cdaodatabase).

##  <a name="close"></a>  CDaoRecordset::Close

Cerrar un `CDaoRecordset` objeto lo quita de la colección de conjuntos de registros abiertos en la base de datos asociada.

```
virtual void Close();
```

### <a name="remarks"></a>Comentarios

Dado que `Close` no destruye el `CDaoRecordset` objeto, puede volver a usar el objeto mediante una llamada a `Open` en el mismo origen de datos o un origen de datos diferente.

Todas las pendientes [AddNew](#addnew) o [editar](#edit) se cancelan las instrucciones y todas las transacciones pendientes se revierten. Si desea conservar adiciones o ediciones pendientes, llame a [actualización](#update) antes de llamar a `Close` para cada conjunto de registros.

Puede llamar a `Open` nuevamente después de llamar a `Close`. Esto permite reutilizar el objeto de conjunto de registros. Una mejor alternativa es llamar a [Requery](#requery), si es posible.

Para obtener información relacionada, vea el tema "Método Close" en la Ayuda de DAO.

##  <a name="delete"></a>  CDaoRecordset::Delete

Llame a esta función miembro para eliminar el registro actual en un objeto de conjunto de registros abierto de tipo dinámico o tipo de tabla.

```
virtual void Delete();
```

### <a name="remarks"></a>Comentarios

Después de una eliminación se realiza correctamente, los miembros de datos de campo del conjunto de registros se establecen en un valor Null y debe llamar explícitamente a una de las funciones miembro de navegación de conjunto de registros ( [mover](#move), [Seek](#seek), [ SetBookmark](#setbookmark), y así sucesivamente) con el fin de abandonar el registro eliminado. Cuando se eliminan los registros de un conjunto de registros, debe haber un registro actual en el conjunto de registros antes de llamar a `Delete`; en caso contrario, MFC inicia una excepción.

`Delete` Quita el registro actual y hace que sea inaccesible. Aunque no se puede editar o utilizar el registro eliminado, sigue estando activo. Cuando se mueva a otro registro, sin embargo, no puede realizar el registro eliminado actual a intentarlo.

> [!CAUTION]
>  El conjunto de registros debe ser actualizable y debe haber un registro válido actual en el conjunto de registros al llamar a `Delete`. Por ejemplo, si elimina un registro pero no se desplazan a un nuevo registro antes de llamar a `Delete` nuevamente, `Delete` produce una [CDaoException](../../mfc/reference/cdaoexception-class.md).

Puede recuperar un registro si se utilizan transacciones y se llama el [CDaoWorkspace::Rollback](../../mfc/reference/cdaoworkspace-class.md#rollback) función miembro. Si la tabla base es la tabla principal en cascada Eliminar relación, también puede eliminar uno o más registros en una tabla externa al eliminar el registro actual. Para obtener más información, vea la definición "en cascada" eliminar en la Ayuda de DAO.

A diferencia de `AddNew` y `Edit`, una llamada a `Delete` no va seguida de una llamada a `Update`.

Para obtener información relacionada, vea los temas "Método AddNew", "Editar método", "Método Delete", "Método de actualización" y "Propiedad actualizable" en la Ayuda de DAO.

##  <a name="dofieldexchange"></a>  CDaoRecordset

El marco de trabajo llama a esta función miembro para automáticamente intercambiar datos entre los miembros de datos de campo del objeto de conjunto de registros y las columnas correspondientes del registro actual en el origen de datos.

```
virtual void DoFieldExchange(CDaoFieldExchange* pFX);
```

### <a name="parameters"></a>Parámetros

*pFX*<br/>
Contiene un puntero a un `CDaoFieldExchange` objeto. El marco de trabajo ya habrá configurado este objeto para especificar un contexto para la operación de intercambio del campo.

### <a name="remarks"></a>Comentarios

También enlaza a los miembros de datos de parámetro, si los hay, para los marcadores de posición en la cadena de instrucción SQL para la selección del conjunto de registros. El intercambio de datos de campo, denominado intercambio de campos de registros DAO (DFX), funciona en ambas direcciones: desde los miembros de datos de campo del objeto de conjunto de registros a los campos del registro en el origen de datos y del registro en el origen de datos para el objeto de conjunto de registros. Si va a enlazar columnas dinámicamente, no son necesarios para implementar `DoFieldExchange`.

La única acción que debe seguir normalmente para implementar `DoFieldExchange` para el conjunto de registros derivada clase consiste en crear la clase con ClassWizard y especificar los tipos de datos y los nombres de los miembros de datos de campo. También puede agregar código a lo que escribe ClassWizard especificar a los miembros de datos de parámetro. Si todos los campos que se van a enlazarse dinámicamente, esta función estará inactiva a menos que especifique a los miembros de datos de parámetro.

Cuando se declara la clase derivada de conjunto de registros con ClassWizard, el asistente escribe una invalidación de `DoFieldExchange` , que es similar al siguiente:

[!code-cpp[NVC_MFCDatabase#2](../../mfc/codesnippet/cpp/cdaorecordset-class_2.cpp)]

##  <a name="edit"></a>  CDaoRecordset:: Edit

Llame a esta función miembro para permitir cambios en el registro actual.

```
virtual void Edit();
```

### <a name="remarks"></a>Comentarios

Una vez que llamamos el `Edit` función miembro, los cambios realizados en los campos del registro actual se copian en el búfer de copia. Después de realizar los cambios deseados en el registro, llame a `Update` para guardar los cambios. `Edit` guarda los valores de los miembros de datos del conjunto de registros. Si se llama a `Edit`, realizar cambios, a continuación, llame a `Edit` nuevo, se restauran los valores del registro a lo que estaban antes del primer `Edit` llamar.

> [!CAUTION]
>  Si edita un registro y, a continuación, realizar cualquier operación que se mueve a otro registro sin llamar primero a `Update`, los cambios se perderán sin previo aviso. Además, si cierra el conjunto de registros o la base de datos principal, se descarta el registro editado sin previo aviso.

En algunos casos, puede actualizar una columna, por lo que es Null (que contiene ningún dato). Para ello, llame al `SetFieldNull` con un parámetro de true para marcar el campo es Null; Esto también hace que la columna se puede actualizar. Si desea que un campo para escribirse en el origen de datos, aunque no ha cambiado su valor, llame a `SetFieldDirty` con un parámetro es true. Esto funciona incluso si el campo tenía el valor Null.

Las marcas de marco de trabajo puede cambiar los miembros de datos de campo para asegurarse de que se escribirá en el registro del origen de datos mediante el mecanismo de intercambio (DFX) de campos de registros DAO. Cambiar el valor de un campo normalmente establece el campo desfasadas automáticamente, por lo que rara vez necesitará llamar a [SetFieldDirty](#setfielddirty) usted mismo, pero a veces, conviene asegurarse de que las columnas se explícitamente actualizadas o insertadas en cualquier caso de qué valor está en el miembro de datos de campo. El mecanismo DFX también emplea el uso de **PSEUDO NULL**. Para obtener más información, consulte [CDaoFieldExchange:: M_noperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation).

Si no se utiliza el mecanismo de almacenamiento en búfer doble, a continuación, cambiar el valor del campo no establece automáticamente el campo como modificado. En este caso, será necesario establecer explícitamente el campo de datos sucios. La marca contenida en [m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields) controla la comprobación automática de campos.

Cuando el objeto recordset forma pesimista está bloqueado en un entorno multiusuario, el registro permanece bloqueado desde el momento `Edit` se usa hasta que finalice la actualización. Si el conjunto de registros está bloqueado de forma optimista, el registro se bloquea y se compara con el registro justo antes de se actualiza en la base de datos. Si el registro ha cambiado desde que llamó a `Edit`, el `Update` se produce un error de operación y MFC produce una excepción. Puede cambiar el modo de bloqueo con `SetLockingMode`.

> [!NOTE]
>  Bloqueo optimista siempre se usa en formatos de base de datos externo, como ODBC y ISAM instalable.

El registro actual permanece actual después de llamar a `Edit`. Para llamar a `Edit`, debe haber un registro actual. Si no hay ningún registro actual, o si el conjunto de registros no hace referencia a un tipo de tabla abierto u objeto de conjunto de registros de tipo dinámico, se produce una excepción. Una llamada a `Edit` hace que un `CDaoException` que se produzca en las siguientes condiciones:

- No hay ningún registro actual.

- La base de datos o un conjunto de registros es de solo lectura.

- No hay campos en el registro son actualizables.

- La base de datos o un conjunto de registros se abrió para su uso exclusivo por otro usuario.

- Otro usuario ha bloqueado la página que contiene el registro.

Si el origen de datos admite transacciones, puede realizar la `Edit` llame a parte de una transacción. Tenga en cuenta que debe llamar a `CDaoWorkspace::BeginTrans` antes de llamar a `Edit` y después de abrir el conjunto de registros. Tenga en cuenta también que la llamada a `CDaoWorkspace::CommitTrans` no constituye un sustituto para llamar a `Update` para completar la `Edit` operación. Para obtener más información acerca de las transacciones, vea la clase `CDaoWorkspace`.

Para obtener información relacionada, vea los temas "Método AddNew", "Editar método", "Método Delete", "Método de actualización" y "Propiedad actualizable" en la Ayuda de DAO.

##  <a name="fillcache"></a>  CDaoRecordset:: FillCache

Llame a esta función miembro para almacenar en caché un número especificado de registros desde el conjunto de registros.

```
void FillCache(
    long* pSize = NULL,
    COleVariant* pBookmark = NULL);
```

### <a name="parameters"></a>Parámetros

*pSize*<br/>
Especifica el número de filas que se va a rellenar la memoria caché. Si se omite este parámetro, el valor viene determinada por la configuración de la propiedad CacheSize del objeto DAO subyacente.

*pBookmark*<br/>
Un [COleVariant](../../mfc/reference/colevariant-class.md) especificación de un marcador. La memoria caché se llena a partir del registro indicado por este marcador. Si se omite este parámetro, la memoria caché se llena a partir del registro indicado por la propiedad CacheStart del objeto DAO subyacente.

### <a name="remarks"></a>Comentarios

Almacenamiento en caché mejora el rendimiento de una aplicación que recupera o captura de datos desde un servidor remoto. Una memoria caché es el espacio en la memoria local que contiene los datos que se han capturado recientemente desde el servidor en la suposición de que los datos probablemente se solicitarán nuevo mientras se ejecuta la aplicación. Cuando se solicitan datos, el motor de base de datos Microsoft Jet comprueba primero la memoria caché para los datos en lugar de captura del servidor, que tarda más tiempo. Usar datos de almacenamiento en caché en orígenes de datos ODBC no tiene ningún efecto como los datos no se guardan en la memoria caché.

En lugar de esperar a que la memoria caché va a rellenar con registros se capturan, se puede llenar la memoria caché en cualquier momento mediante una llamada a la `FillCache` función miembro. Se trata de una manera más rápida para llenar la caché porque `FillCache` recupera varios registros a la vez en lugar de uno en uno. Por ejemplo, mientras se está mostrando cada pantalla de registros, puede tener la llamada de la aplicación `FillCache` para capturar la siguiente pantalla de registros.

Cualquier base de datos ODBC que se obtiene acceso con los objetos de conjunto de registros puede tener una caché local. Para crear la memoria caché, abra un objeto de conjunto de registros desde el origen de datos remoto y, a continuación, llame a la `SetCacheSize` y `SetCacheStart` funciones miembro del conjunto de registros. Si *lSize* y *lBookmark* crear un intervalo que se desplacen parcial o totalmente fuera del intervalo especificado por `SetCacheSize` y `SetCacheStart`, la parte del conjunto de registros fuera de este intervalo se omite y no es carga en la memoria caché. Si `FillCache` solicita más registros que permanecen en el origen de datos remoto, sólo los registros restantes se capturan y se produce ninguna excepción.

Registros recuperados de la memoria caché no reflejan los cambios realizados al mismo tiempo al origen de datos por otros usuarios.

`FillCache` captura solo los registros que ya no almacenado en caché. Para forzar una actualización de todos los datos almacenados en caché, llame a la `SetCacheSize` función miembro con un *lSize* parámetro igual a 0, llamada `SetCacheSize` nuevo con el *lSize* parámetro igual que el tamaño de la memoria caché se solicitó originalmente y, a continuación, llamar a `FillCache`.

Para obtener información relacionada, vea el tema "Método FillCache" en la Ayuda de DAO.

##  <a name="find"></a>  CDaoRecordset::Find

Llame a esta función miembro para buscar una cadena concreta en un conjunto de registros de tipo dinámico o instantánea mediante un operador de comparación.

```
virtual BOOL Find(
    long lFindType,
    LPCTSTR lpszFilter);
```

### <a name="parameters"></a>Parámetros

*lFindType*<br/>
Un valor que indica el tipo de operación de búsqueda deseado. Los valores posibles son:

- AFX_DAO_NEXT encontrar la ubicación siguiente de una cadena coincidente.

- AFX_DAO_PREV encontrar la ubicación anterior de una cadena coincidente.

- AFX_DAO_FIRST buscar la primera ubicación de una cadena coincidente.

- Bien AFX_DAO_LAST buscar la última ubicación de una cadena coincidente.

*lpszFilter*<br/>
Una expresión de cadena (como el **donde** cláusula en una instrucción SQL sin la palabra **donde**) usado para buscar el registro. Por ejemplo:

[!code-cpp[NVC_MFCDatabase#3](../../mfc/codesnippet/cpp/cdaorecordset-class_3.cpp)]

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se encuentran los registros coincidentes, en caso contrario, 0.

### <a name="remarks"></a>Comentarios

Puede encontrar la primera, siguiente, anterior, o en última instancia de la cadena. `Find` es una función virtual, por lo que puede invalidarlo y agregar su propia implementación. El `FindFirst`, `FindLast`, `FindNext`, y `FindPrev` funciones miembro llaman a la `Find` función miembro, por lo que puede usar `Find` para controlar el comportamiento de todas las operaciones de búsqueda.

Para buscar un registro en un conjunto de registros de tipo de tabla, llame a la [Seek](#seek) función miembro.

> [!TIP]
>  Cuanto menor sea el conjunto de registros que tiene, más eficaces `Find` será. En general y especialmente con los datos ODBC, es mejor crear una nueva consulta que recupera solo los registros que desee.

Para obtener información relacionada, vea el tema "FindFirst, FindLast, FindNext, FindPrevious métodos" en la Ayuda de DAO.

##  <a name="findfirst"></a>  CDaoRecordset::FindFirst

Llame a esta función miembro para encontrar el primer registro que coincide con una condición especificada.

```
BOOL FindFirst(LPCTSTR lpszFilter);
```

### <a name="parameters"></a>Parámetros

*lpszFilter*<br/>
Una expresión de cadena (como el **donde** cláusula en una instrucción SQL sin la palabra **donde**) usado para buscar el registro.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se encuentran los registros coincidentes, en caso contrario, 0.

### <a name="remarks"></a>Comentarios

El `FindFirst` función miembro comienza la búsqueda desde el principio del conjunto de registros y busca hasta el final del conjunto de registros.

Si desea incluir todos los registros en la búsqueda (no solo aquellos que satisfacen una condición específica) usan una de las operaciones de movimiento para desplazarse por los registros. Para buscar un registro en un conjunto de registros de tipo de tabla, llame a la `Seek` función miembro.

Si no se encuentra un registro que coincida con los criterios, el puntero de registro actual es indeterminado, y `FindFirst` devuelve cero. Si el conjunto de registros contiene más de un registro que satisface los criterios, `FindFirst` localiza la primera aparición, `FindNext` busca la siguiente repetición y así sucesivamente.

> [!CAUTION]
>  Si edita el registro actual, asegúrese de guardar los cambios mediante una llamada a la `Update` función de miembro antes de pasar a otro registro. Si mueve a otro registro sin actualizar, los cambios se perderán sin previo aviso.

El `Find` funciones miembro de búsqueda desde la ubicación y en la dirección especificada en la tabla siguiente:

|Operaciones de búsqueda|comenzar|Dirección de búsqueda|
|---------------------|-----------|----------------------|
|`FindFirst`|A partir del conjunto de registros|Final del conjunto de registros|
|`FindLast`|Final del conjunto de registros|A partir del conjunto de registros|
|`FindNext`|Registro actual|Final del conjunto de registros|
|`FindPrevious`|Registro actual|A partir del conjunto de registros|

> [!NOTE]
>  Cuando se llama a `FindLast`, el motor de base de datos Microsoft Jet rellena totalmente el conjunto de registros antes de comenzar la búsqueda, si no lo ha hecho ya. La primera búsqueda puede tardar más que las búsquedas posteriores.

Utilizando una de las operaciones de búsqueda no es igual que llamar a `MoveFirst` o `MoveNext`, sin embargo, que simplemente hace que el registro de la primero o siguiente actual sin especificar una condición. Puede seguir una operación de búsqueda con una operación de movimiento.

Al usar las operaciones de búsqueda, tenga en cuenta lo siguiente:

- Si `Find` devuelve distinto de cero, el registro actual no está definido. En este caso, debe colocar el puntero de registro actual a un registro válido.

- No se puede usar una operación de búsqueda con un recordset de tipo snapshot desplazamiento sólo hacia delante.

- Debe usar el formato de fecha (mes-año) de EE. UU. al realizar una búsqueda para campos que contienen fechas, incluso si no usa la versión de Estados Unidos del motor de base de datos Microsoft Jet; en caso contrario, los registros coincidentes pueden no encontrarse.

- Cuando se trabaja con grandes conjuntos de registros dinámicos y de bases de datos ODBC, es posible que descubra que el uso de las operaciones de búsqueda es lento, especialmente cuando se trabaja con grandes conjuntos de registros. Puede mejorar el rendimiento mediante consultas SQL con personalizar **ORDERBY** o **donde** cláusulas, consultas con parámetros, o `CDaoQuerydef` objetos que recuperan registros indizados específicos.

Para obtener información relacionada, vea el tema "FindFirst, FindLast, FindNext, FindPrevious métodos" en la Ayuda de DAO.

##  <a name="findlast"></a>  CDaoRecordset::FindLast

Llame a esta función miembro para encontrar el último registro que coincida con una condición especificada.

```
BOOL FindLast(LPCTSTR lpszFilter);
```

### <a name="parameters"></a>Parámetros

*lpszFilter*<br/>
Una expresión de cadena (como el **donde** cláusula en una instrucción SQL sin la palabra **donde**) usado para buscar el registro.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se encuentran los registros coincidentes, en caso contrario, 0.

### <a name="remarks"></a>Comentarios

El `FindLast` función miembro comienza la búsqueda al final del conjunto de registros y las búsquedas hacia atrás hacia el principio del conjunto de registros.

Si desea incluir todos los registros en la búsqueda (no solo aquellos que satisfacen una condición específica) usan una de las operaciones de movimiento para desplazarse por los registros. Para buscar un registro en un conjunto de registros de tipo de tabla, llame a la `Seek` función miembro.

Si no se encuentra un registro que coincida con los criterios, el puntero de registro actual es indeterminado, y `FindLast` devuelve cero. Si el conjunto de registros contiene más de un registro que satisface los criterios, `FindFirst` localiza la primera aparición, `FindNext` busca la siguiente aparición después de la primera aparición y así sucesivamente.

> [!CAUTION]
>  Si edita el registro actual, asegúrese de guardar los cambios mediante una llamada a la `Update` función de miembro antes de pasar a otro registro. Si mueve a otro registro sin actualizar, los cambios se perderán sin previo aviso.

Utilizando una de las operaciones de búsqueda no es igual que llamar a `MoveFirst` o `MoveNext`, sin embargo, que simplemente hace que el registro de la primero o siguiente actual sin especificar una condición. Puede seguir una operación de búsqueda con una operación de movimiento.

Al usar las operaciones de búsqueda, tenga en cuenta lo siguiente:

- Si `Find` devuelve distinto de cero, el registro actual no está definido. En este caso, debe colocar el puntero de registro actual a un registro válido.

- No se puede usar una operación de búsqueda con un recordset de tipo snapshot desplazamiento sólo hacia delante.

- Debe usar el formato de fecha (mes-año) de EE. UU. al realizar una búsqueda para campos que contienen fechas, incluso si no usa la versión de Estados Unidos del motor de base de datos Microsoft Jet; en caso contrario, los registros coincidentes pueden no encontrarse.

- Cuando se trabaja con grandes conjuntos de registros dinámicos y de bases de datos ODBC, es posible que descubra que el uso de las operaciones de búsqueda es lento, especialmente cuando se trabaja con grandes conjuntos de registros. Puede mejorar el rendimiento mediante consultas SQL con personalizar **ORDERBY** o **donde** cláusulas, consultas con parámetros, o `CDaoQuerydef` objetos que recuperan registros indizados específicos.

Para obtener información relacionada, vea el tema "FindFirst, FindLast, FindNext, FindPrevious métodos" en la Ayuda de DAO.

##  <a name="findnext"></a>  CDaoRecordset::FindNext

Llame a esta función miembro para encontrar el registro siguiente que coincida con una condición especificada.

```
BOOL FindNext(LPCTSTR lpszFilter);
```

### <a name="parameters"></a>Parámetros

*lpszFilter*<br/>
Una expresión de cadena (como el **donde** cláusula en una instrucción SQL sin la palabra **donde**) usado para buscar el registro.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se encuentran los registros coincidentes, en caso contrario, 0.

### <a name="remarks"></a>Comentarios

El `FindNext` función miembro inicia su búsqueda en el registro actual y busca hasta el final del conjunto de registros.

Si desea incluir todos los registros en la búsqueda (no solo aquellos que satisfacen una condición específica) usan una de las operaciones de movimiento para desplazarse por los registros. Para buscar un registro en un conjunto de registros de tipo de tabla, llame a la `Seek` función miembro.

Si no se encuentra un registro que coincida con los criterios, el puntero de registro actual es indeterminado, y `FindNext` devuelve cero. Si el conjunto de registros contiene más de un registro que satisface los criterios, `FindFirst` localiza la primera aparición, `FindNext` busca la siguiente repetición y así sucesivamente.

> [!CAUTION]
>  Si edita el registro actual, asegúrese de guardar los cambios mediante una llamada a la `Update` función de miembro antes de pasar a otro registro. Si mueve a otro registro sin actualizar, los cambios se perderán sin previo aviso.

Utilizando una de las operaciones de búsqueda no es igual que llamar a `MoveFirst` o `MoveNext`, sin embargo, que simplemente hace que el registro de la primero o siguiente actual sin especificar una condición. Puede seguir una operación de búsqueda con una operación de movimiento.

Al usar las operaciones de búsqueda, tenga en cuenta lo siguiente:

- Si `Find` devuelve distinto de cero, el registro actual no está definido. En este caso, debe colocar el puntero de registro actual a un registro válido.

- No se puede usar una operación de búsqueda con un recordset de tipo snapshot desplazamiento sólo hacia delante.

- Debe usar el formato de fecha (mes-año) de EE. UU. al realizar una búsqueda para campos que contienen fechas, incluso si no usa la versión de Estados Unidos del motor de base de datos Microsoft Jet; en caso contrario, los registros coincidentes pueden no encontrarse.

- Cuando se trabaja con grandes conjuntos de registros dinámicos y de bases de datos ODBC, es posible que descubra que el uso de las operaciones de búsqueda es lento, especialmente cuando se trabaja con grandes conjuntos de registros. Puede mejorar el rendimiento mediante consultas SQL con personalizar **ORDERBY** o **donde** cláusulas, consultas con parámetros, o `CDaoQuerydef` objetos que recuperan registros indizados específicos.

Para obtener información relacionada, vea el tema "FindFirst, FindLast, FindNext, FindPrevious métodos" en la Ayuda de DAO.

##  <a name="findprev"></a>  CDaoRecordset::FindPrev

Llame a esta función miembro para encontrar el registro anterior que coincida con una condición especificada.

```
BOOL FindPrev(LPCTSTR lpszFilter);
```

### <a name="parameters"></a>Parámetros

*lpszFilter*<br/>
Una expresión de cadena (como el **donde** cláusula en una instrucción SQL sin la palabra **donde**) usado para buscar el registro.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se encuentran los registros coincidentes, en caso contrario, 0.

### <a name="remarks"></a>Comentarios

El `FindPrev` función miembro inicia su búsqueda en el registro actual y realiza búsquedas hacia atrás hacia el principio del conjunto de registros.

Si desea incluir todos los registros en la búsqueda (no solo aquellos que satisfacen una condición específica) usan una de las operaciones de movimiento para desplazarse por los registros. Para buscar un registro en un conjunto de registros de tipo de tabla, llame a la `Seek` función miembro.

Si no se encuentra un registro que coincida con los criterios, el puntero de registro actual es indeterminado, y `FindPrev` devuelve cero. Si el conjunto de registros contiene más de un registro que satisface los criterios, `FindFirst` localiza la primera aparición, `FindNext` busca la siguiente repetición y así sucesivamente.

> [!CAUTION]
>  Si edita el registro actual, asegúrese de guardar los cambios mediante una llamada a la `Update` función de miembro antes de pasar a otro registro. Si mueve a otro registro sin actualizar, los cambios se perderán sin previo aviso.

Utilizando una de las operaciones de búsqueda no es igual que llamar a `MoveFirst` o `MoveNext`, sin embargo, que simplemente hace que el registro de la primero o siguiente actual sin especificar una condición. Puede seguir una operación de búsqueda con una operación de movimiento.

Al usar las operaciones de búsqueda, tenga en cuenta lo siguiente:

- Si `Find` devuelve distinto de cero, el registro actual no está definido. En este caso, debe colocar el puntero de registro actual a un registro válido.

- No se puede usar una operación de búsqueda con un recordset de tipo snapshot desplazamiento sólo hacia delante.

- Debe usar el formato de fecha (mes-año) de EE. UU. al realizar una búsqueda para campos que contienen fechas, incluso si no usa la versión de Estados Unidos del motor de base de datos Microsoft Jet; en caso contrario, los registros coincidentes pueden no encontrarse.

- Cuando se trabaja con grandes conjuntos de registros dinámicos y de bases de datos ODBC, es posible que descubra que el uso de las operaciones de búsqueda es lento, especialmente cuando se trabaja con grandes conjuntos de registros. Puede mejorar el rendimiento mediante consultas SQL con personalizar **ORDERBY** o **donde** cláusulas, consultas con parámetros, o `CDaoQuerydef` objetos que recuperan registros indizados específicos.

Para obtener información relacionada, vea el tema "FindFirst, FindLast, FindNext, FindPrevious métodos" en la Ayuda de DAO.

##  <a name="getabsoluteposition"></a>  CDaoRecordset:: GetAbsolutePosition

Devuelve el número de registro del registro actual del objeto de un conjunto de registros.

```
long GetAbsolutePosition();
```

### <a name="return-value"></a>Valor devuelto

Entero del 0 al número de registros en el conjunto de registros. Corresponde a la posición ordinal del registro actual en el conjunto de registros.

### <a name="remarks"></a>Comentarios

El valor de propiedad AbsolutePosition del objeto DAO subyacente está basado en cero; un valor de 0 hace referencia al primer registro en el conjunto de registros. Puede determinar el número de registros rellenados en el conjunto de registros mediante una llamada a [GetRecordCount](#getrecordcount). Una llamada a `GetRecordCount` puede tardar algún tiempo porque debe acceder a todos los registros para determinar el recuento.

Si hay ningún registro actual, como cuando no hay ningún registro en el conjunto de registros, se devuelve 1. Si se elimina el registro actual, no está definido el valor de propiedad AbsolutePosition y MFC produce una excepción si se hace referencia. Para conjuntos de registros de tipo dinámico, nuevos registros se agregan al final de la secuencia.

> [!NOTE]
>  Esta propiedad no pretende utilizarse como un número de registro suplente. Los marcadores siguen siendo la forma recomendada de retener y volver a una posición determinada y son la única forma de colocar el registro actual en todos los tipos de objetos de conjunto de registros. En concreto, la posición de un registro determinado cambia cuando se eliminan los registros que le precede. También no hay ninguna garantía de que un registro determinado tendrá la misma posición absoluta si se vuelve a crear el conjunto de registros, porque no se garantiza el orden de los registros individuales dentro de un conjunto de registros, a menos que se crea con una instrucción SQL mediante un  **ORDERBY** cláusula.

> [!NOTE]
>  Esta función miembro es válida únicamente para el tipo de conjunto de registros dinámicos y los conjuntos de registros de tipo de instantánea.

Para obtener información relacionada, vea el tema "Propiedad AbsolutePosition" en la Ayuda de DAO.

##  <a name="getbookmark"></a>  CDaoRecordset:: GetBookmark

Llame a esta función miembro para obtener el valor de marcador en un registro concreto.

```
COleVariant GetBookmark();
```

### <a name="return-value"></a>Valor devuelto

Devuelve un valor que representa el marcador en el registro actual.

### <a name="remarks"></a>Comentarios

Cuando se crea o se abre un objeto de conjunto de registros, cada uno de sus registros tiene ya un marcador único si admite. Llame a `CanBookmark` para determinar si un conjunto de registros admite marcadores.

Puede guardar el marcador para el registro actual, asigne el valor del marcador a un `COleVariant` objeto. Para volver rápidamente a ese registro en cualquier momento después de mover a un registro diferente, llame a `SetBookmark` con un parámetro corresponde al valor de ese `COleVariant` objeto.

> [!NOTE]
>  Una llamada a [Requery](#requery) cambia los marcadores DAO.

Para obtener información relacionada, vea el tema "Propiedades de marcador" en la Ayuda de DAO.

##  <a name="getcachesize"></a>  CDaoRecordset::GetCacheSize

Llame a esta función miembro para obtener el número de registros que se almacenan en caché.

```
long GetCacheSize();
```

### <a name="return-value"></a>Valor devuelto

Un valor que especifica el número de registros en un conjunto de registros de tipo dinámico que contiene datos para almacenar en caché localmente desde un origen de datos ODBC.

### <a name="remarks"></a>Comentarios

Datos en caché mejoran el rendimiento de una aplicación que recupera datos de un servidor remoto a través de objetos de conjunto de registros de tipo dinámico. Una memoria caché es un espacio en la memoria local que contiene los datos recientemente recuperados del servidor en caso de que los datos volverá a solicitarse mientras se ejecuta la aplicación. Cuando se solicitan datos, el motor de base de datos Microsoft Jet comprueba primero la caché de los datos solicitados en lugar de recuperarlos desde el servidor, lo que requiere más tiempo. Datos que no proceden de un origen de datos ODBC no se guardan en la memoria caché.

Cualquier origen de datos ODBC, como una tabla asociada, puede tener una caché local.

Para obtener información relacionada, vea el tema "CacheSize, CacheStart propiedades" en la Ayuda de DAO.

##  <a name="getcachestart"></a>  CDaoRecordset::GetCacheStart

Llame a esta función miembro para obtener el valor de marcador del primer registro en el conjunto de registros en la memoria caché.

```
COleVariant GetCacheStart();
```

### <a name="return-value"></a>Valor devuelto

Un `COleVariant` que especifica el marcador del primer registro en el conjunto de registros en la memoria caché.

### <a name="remarks"></a>Comentarios

El motor de base de datos Microsoft Jet solicita registros dentro del intervalo de memoria caché de la memoria caché y solicita registros fuera del intervalo de memoria caché del servidor.

> [!NOTE]
>  Los registros recuperados de la memoria caché no reflejan los cambios realizados al mismo tiempo al origen de datos por otros usuarios.

Para obtener información relacionada, vea el tema "CacheSize, CacheStart propiedades" en la Ayuda de DAO.

##  <a name="getcurrentindex"></a>  CDaoRecordset::GetCurrentIndex

Llame a esta función miembro para determinar el índice actualmente en uso en un tipo de tabla indizado `CDaoRecordset` objeto.

```
CString GetCurrentIndex();
```

### <a name="return-value"></a>Valor devuelto

Un `CString` que contiene el nombre del índice actualmente en uso con un conjunto de registros de tipo de tabla. Devuelve una cadena vacía si no se ha establecido ningún índice.

### <a name="remarks"></a>Comentarios

Este índice es la base para ordenar los registros en un conjunto de registros de tipo de tabla y está usando el [Seek](#seek) función miembro para localizar los registros.

Un `CDaoRecordset` objeto puede tener más de un índice, pero puede utilizar solo un índice a la vez (aunque un [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md) objeto puede tener varios índices definidos en él).

Para obtener información relacionada, vea el tema "Objeto Index" y la definición de "índice actual" en la Ayuda de DAO.

##  <a name="getdatecreated"></a>  CDaoRecordset::GetDateCreated

Llame a esta función miembro para recuperar la fecha y hora de que creación de una tabla base.

```
COleDateTime GetDateCreated();
```

### <a name="return-value"></a>Valor devuelto

Un [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objeto que contiene la fecha y hora de creación de la tabla base.

### <a name="remarks"></a>Comentarios

Configuración de fecha y hora se deriva del equipo en el que se creó la tabla base.

Para obtener información relacionada, vea el tema "DateCreated y LastUpdated propiedades" en la Ayuda de DAO.

##  <a name="getdatelastupdated"></a>  CDaoRecordset::GetDateLastUpdated

Llame a esta función miembro para recuperar la fecha y hora que se actualizó por última vez el esquema.

```
COleDateTime GetDateLastUpdated();
```

### <a name="return-value"></a>Valor devuelto

Un [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objeto que contiene la fecha y hora que se actualizó por última vez la estructura de tabla base (esquema).

### <a name="remarks"></a>Comentarios

Configuración de fecha y hora se deriva del equipo en el que se actualizó por última vez la estructura de tabla base (esquema).

Para obtener información relacionada, vea el tema "DateCreated y LastUpdated propiedades" en la Ayuda de DAO.

##  <a name="getdefaultdbname"></a>  CDaoRecordset::GetDefaultDBName

Llame a esta función miembro para determinar el nombre de la base de datos para este conjunto de registros.

```
virtual CString GetDefaultDBName();
```

### <a name="return-value"></a>Valor devuelto

Un `CString` que contiene la ruta de acceso y el nombre de la base de datos que se deriva este conjunto de registros.

### <a name="remarks"></a>Comentarios

Si se crea un conjunto de registros sin un puntero a un [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md), a continuación, se usa esta ruta de acceso por el conjunto de registros para abrir la base de datos de forma predeterminada. De forma predeterminada, esta función devuelve una cadena vacía. Cuando se ClassWizard deriva un nuevo conjunto de registros desde `CDaoRecordset`, creará esta función para usted.

El ejemplo siguiente muestra el uso de la doble barra diagonal inversa (\\\\) en la cadena, según sea necesario para la cadena se interpreta correctamente.

[!code-cpp[NVC_MFCDatabase#4](../../mfc/codesnippet/cpp/cdaorecordset-class_4.cpp)]

##  <a name="getdefaultsql"></a>  CDaoRecordset::GetDefaultSQL

El marco de trabajo llama a esta función miembro para obtener la instrucción SQL de forma predeterminada en el que se basa el conjunto de registros.

```
virtual CString GetDefaultSQL();
```

### <a name="return-value"></a>Valor devuelto

Un `CString` que contiene la instrucción SQL predeterminada.

### <a name="remarks"></a>Comentarios

Esto podría ser un nombre de tabla o una instancia de SQL **seleccione** instrucción.

Defina la instrucción SQL predeterminada indirectamente mediante la declaración de la clase de conjunto de registros con ClassWizard y ClassWizard realiza esta tarea automáticamente.

Si se pasa una cadena SQL null a [abierto](#open), a continuación, se llama a esta función para determinar el nombre de la tabla o SQL para el conjunto de registros.

##  <a name="geteditmode"></a>  CDaoRecordset::GetEditMode

Llame a esta función miembro para determinar el estado de edición, que es uno de los siguientes valores:

```
short GetEditMode();
```

### <a name="return-value"></a>Valor devuelto

Devuelve un valor que indica el estado de edición para el registro actual.

### <a name="remarks"></a>Comentarios

|Valor|Descripción|
|-----------|-----------------|
|`dbEditNone`|No hay ninguna operación de edición está en curso.|
|`dbEditInProgress`|`Edit` se ha llamado.|
|`dbEditAdd`|`AddNew` se ha llamado.|

Para obtener información relacionada, vea el tema "Propiedad EditMode" en la Ayuda de DAO.

##  <a name="getfieldcount"></a>  CDaoRecordset::GetFieldCount

Llame a esta función miembro para recuperar el número de campos (columnas) definidos en el conjunto de registros.

```
short GetFieldCount();
```

### <a name="return-value"></a>Valor devuelto

El número de campos del conjunto de registros.

### <a name="remarks"></a>Comentarios

Para obtener información relacionada, vea el tema "Propiedad Count" en la Ayuda de DAO.

##  <a name="getfieldinfo"></a>  CDaoRecordset::GetFieldInfo

Llame a esta función miembro para obtener información acerca de los campos de un conjunto de registros.

```
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
Índice de base cero del campo predefinido en la colección de campos del conjunto de registros, para la búsqueda por índice.

*FieldInfo*<br/>
Una referencia a un [CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md) estructura.

*dwInfoOptions*<br/>
Opciones que especifican qué información sobre el conjunto de registros para recuperar. Las opciones disponibles se muestran aquí, junto con lo que hacen que la función devolver. Para obtener el mejor rendimiento, recuperar solo el nivel de información que necesita:

- `AFX_DAO_PRIMARY_INFO` (Valor predeterminado) Nombre, tipo, tamaño, atributos

- `AFX_DAO_SECONDARY_INFO` La información principal, además de: Permitir cero tabla de origen de longitud, orden de intercalación, nombre de la externa, el campo de origen, la posición Ordinal, es necesario,

- `AFX_DAO_ALL_INFO` La información principal y secundaria, además de: texto del valor predeterminado, la regla de validación, validación

*lpszName*<br/>
Nombre del campo.

### <a name="remarks"></a>Comentarios

Una versión de la función le permite buscar un campo por su índice. La otra versión le permite buscar un campo por su nombre.

Para obtener una descripción de la información devuelta, consulte el [CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md) estructura. Esta estructura no tiene miembros que corresponden a los elementos de información que aparece anteriormente en la descripción de *dwInfoOptions*. Cuando se solicita información en un nivel, obtendrá información de los niveles anteriores también.

Para obtener información relacionada, vea el tema "Atributos de propiedad" en la Ayuda de DAO.

##  <a name="getfieldvalue"></a>  CDaoRecordset:: GetFieldValue

Llame a esta función miembro para recuperar los datos en un conjunto de registros.

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
Un puntero a una cadena que contiene el nombre de un campo.

*varValue*<br/>
Una referencia a un `COleVariant` objeto donde se almacenará el valor de un campo.

*nIndex*<br/>
Un índice de base cero del campo en la colección de campos del conjunto de registros, para la búsqueda por índice.

### <a name="return-value"></a>Valor devuelto

Las dos versiones de `GetFieldValue` que devuelven un valor devuelto una [COleVariant](../../mfc/reference/colevariant-class.md) objeto que contiene el valor de un campo.

### <a name="remarks"></a>Comentarios

Puede buscar un campo por nombre o por posición ordinal.

> [!NOTE]
>  Resulta más eficaz para llamar a una de las versiones de esta función miembro que toma un `COleVariant` referencia de objeto como un parámetro, en lugar de llamar a una versión que devuelve un `COleVariant` objeto. Las versiones más recientes de esta función se conservan por compatibilidad con versiones anteriores.

Use `GetFieldValue` y [SetFieldValue](#setfieldvalue) para enlazar campos dinámicamente en tiempo de ejecución en lugar de estáticamente columnas de enlace mediante la [DoFieldExchange](#dofieldexchange) mecanismo.

`GetFieldValue` y el `DoFieldExchange` mecanismo se puede combinar para mejorar el rendimiento. Por ejemplo, use `GetFieldValue` para recuperar un valor que necesite únicamente a petición y asignar esa llamada a un botón "Más información" en la interfaz.

Para obtener información relacionada, vea los temas "Objeto de campo" y "Valor de propiedad" en la Ayuda de DAO.

##  <a name="getindexcount"></a>  CDaoRecordset::GetIndexCount

Llame a esta función miembro para determinar el número de índices disponibles en el conjunto de registros de tipo de tabla.

```
short GetIndexCount();
```

### <a name="return-value"></a>Valor devuelto

El número de índices en el conjunto de registros de tipo de tabla.

### <a name="remarks"></a>Comentarios

`GetIndexCount` es útil para recorrer en iteración todos los índices del conjunto de registros. Para ello, utilice `GetIndexCount` junto con [GetIndexInfo](#getindexinfo). Si se llama a esta función miembro de tipo dinámico o conjuntos de registros de tipo de instantánea, MFC inicia una excepción.

Para obtener información relacionada, vea el tema "Atributos de propiedad" en la Ayuda de DAO.

##  <a name="getindexinfo"></a>  CDaoRecordset::GetIndexInfo

Llame a esta función miembro para obtener diversos tipos de información acerca de un índice definido en la tabla base subyacente de un conjunto de registros.

```
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
Índice de base cero en la colección de índices de la tabla, para la búsqueda por posición numérica.

*indexinfo*<br/>
Una referencia a un [CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md) estructura.

*dwInfoOptions*<br/>
Opciones que especifican qué información sobre el índice para recuperar. Las opciones disponibles se muestran aquí, junto con lo que hacen que la función devolver. Para obtener el mejor rendimiento, recuperar solo el nivel de información que necesita:

- `AFX_DAO_PRIMARY_INFO` (Valor predeterminado) Campos de nombre, información de campo

- `AFX_DAO_SECONDARY_INFO` La información principal, además de: principal, Unique, Clustered, IgnoreNulls, es necesario, externa

- `AFX_DAO_ALL_INFO` La información principal y secundaria, además de: recuento distinto

*lpszName*<br/>
Un puntero al nombre del objeto de índice, para la búsqueda por nombre.

### <a name="remarks"></a>Comentarios

Una versión de la función le permite buscar un índice por su posición en la colección. La otra versión le permite buscar un índice por nombre.

Para obtener una descripción de la información devuelta, consulte el [CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md) estructura. Esta estructura no tiene miembros que corresponden a los elementos de información que aparece anteriormente en la descripción de *dwInfoOptions*. Cuando se solicita información en un nivel, obtendrá información de los niveles anteriores también.

Para obtener información relacionada, vea el tema "Atributos de propiedad" en la Ayuda de DAO.

##  <a name="getlastmodifiedbookmark"></a>  CDaoRecordset::GetLastModifiedBookmark

Llame a esta función miembro para recuperar el marcador del registro más recientemente se ha agregado o actualizado.

```
COleVariant GetLastModifiedBookmark();
```

### <a name="return-value"></a>Valor devuelto

Un `COleVariant` que contiene un marcador que indica el último registro agregado o modificado.

### <a name="remarks"></a>Comentarios

Cuando se crea o se abre un objeto de conjunto de registros, cada uno de sus registros tiene ya un marcador único si admite. Llame a [GetBookmark](#getbookmark) para determinar si el conjunto de registros admite marcadores. Si el conjunto de registros no es compatible con los marcadores, un `CDaoException` se produce.

Cuando se agrega un registro, aparece al final del conjunto de registros y no es el registro actual. Para que el nuevo registro actual, llame a `GetLastModifiedBookmark` y, a continuación, llame a `SetBookmark` para devolver el registro recién agregado.

Para obtener información relacionada, vea el tema "Propiedad LastModified" en la Ayuda de DAO.

##  <a name="getlockingmode"></a>  CDaoRecordset::GetLockingMode

Llame a esta función miembro para determinar el tipo de bloqueo en vigor para el conjunto de registros.

```
BOOL GetLockingMode();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el tipo de bloqueo es pesimista, en caso contrario, 0 para el bloqueo optimista registro.

### <a name="remarks"></a>Comentarios

Cuando el bloqueo pesimista está activada, la página de datos que contiene el registro que está modificando está bloqueada en cuanto llame a la [editar](#edit) función miembro. La página se desbloquea cuando se llama a la [actualización](#update) o [cerrar](#close) función miembro o cualquiera de las operaciones de mover o encontrar.

Cuando está activado un bloqueo optimista, se bloquea la página de datos que contiene el registro solo mientras se actualiza el registro con el `Update` función miembro.

Cuando se trabaja con orígenes de datos ODBC, el modo de bloqueo siempre es optimista.

Para obtener información relacionada, vea los temas "Propiedad LockEdits" y "Comportamiento de bloqueo en multiusuario Applications" en la Ayuda de DAO.

##  <a name="getname"></a>  CDaoRecordset::GetName

Llame a esta función miembro para recuperar el nombre del conjunto de registros.

```
CString GetName();
```

### <a name="return-value"></a>Valor devuelto

Un `CString` que contiene el nombre del conjunto de registros.

### <a name="remarks"></a>Comentarios

El nombre del conjunto de registros debe comenzar con una letra y puede contener un máximo de 40 caracteres. Puede incluir números y caracteres de subrayado pero no puede incluir espacios o signos de puntuación.

Para obtener información relacionada, vea el tema "Nombre de la propiedad" en la Ayuda de DAO.

##  <a name="getparamvalue"></a>  CDaoRecordset::GetParamValue

Llame a esta función miembro para recuperar el valor actual del parámetro especificado almacenado en el objeto DAOParameter subyacente.

```
virtual COleVariant GetParamValue(int nIndex);
virtual COleVariant GetParamValue(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
La posición numérica del parámetro en el objeto DAOParameter subyacente.

*lpszName*<br/>
El nombre del parámetro cuyo valor desee.

### <a name="return-value"></a>Valor devuelto

Un objeto de clase [COleVariant](../../mfc/reference/colevariant-class.md) que contiene el valor del parámetro.

### <a name="remarks"></a>Comentarios

El parámetro puede tener acceso por nombre o por su posición numérica de la colección.

Para obtener información relacionada, vea el tema "Objeto de parámetro" en la Ayuda de DAO.

##  <a name="getpercentposition"></a>  CDaoRecordset:: GetPercentPosition

Cuando se trabaja con un tipo dinámico o un conjunto de registros de tipo de instantánea, si se llama a `GetPercentPosition` antes de rellenar completamente el conjunto de registros, la cantidad de movimiento es relativo al número de registros de acceso tal como se indica mediante una llamada a [GetRecordCount](#getrecordcount).

```
float GetPercentPosition();
```

### <a name="return-value"></a>Valor devuelto

Un número entre 0 y 100 que indica la ubicación aproximada del registro actual en el objeto de conjunto de registros basándose en un porcentaje de los registros del conjunto de registros.

### <a name="remarks"></a>Comentarios

Puede mover al último registro mediante una llamada a [MoveLast](#movelast) para completar la población de todos los conjuntos de registros, pero esto puede tardar una cantidad considerable de tiempo.

Puede llamar a `GetPercentPosition` en los tres tipos de objetos de conjunto de registros, incluidas las tablas sin índices. Sin embargo, no puede llamar a `GetPercentPosition` en instantáneas de desplazamiento solo hacia delante o en un conjunto de registros abierto desde una consulta de paso a través en una base de datos externo. Si no hay ningún registro actual, o se ha eliminado el registro actual, un `CDaoException` se produce.

Para obtener información relacionada, vea el tema "PercentPosition Property" en la Ayuda de DAO.

##  <a name="getrecordcount"></a>  CDaoRecordset::GetRecordCount

Llame a esta función miembro para averiguar cuántos registros en un conjunto de registros se ha tenido acceso.

```
long GetRecordCount();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el número de registros que se obtiene acceso en un objeto de conjunto de registros.

### <a name="remarks"></a>Comentarios

`GetRecordCount` no indica cuántos registros se encuentran en un tipo dinámico o un conjunto de registros de tipo de instantánea hasta que todos los registros se ha tenido acceso. Esta llamada de función miembro puede tardar una cantidad considerable de tiempo en completarse.

Una vez que se ha accedido el último registro, el valor devuelto indica el número total de registros se han recuperado en el conjunto de registros. Para forzar el último registro de acceso, llame a la `MoveLast` o `FindLast` función miembro para el conjunto de registros. También puede usar un recuento de SQL para determinar el número aproximado de registros que devolverá la consulta.

Como la aplicación elimina registros en un conjunto de registros de tipo dinámico, el valor devuelto de `GetRecordCount` disminuye. Sin embargo, los registros eliminados por otros usuarios no se reflejan en `GetRecordCount` hasta que el registro actual se coloca en un registro eliminado. Si ejecuta una transacción que afecta el número de registros y posteriormente deshace la transacción, `GetRecordCount` no reflejará el número real de los registros restantes.

El valor de `GetRecordCount` desde un conjunto de registros de tipo de instantánea no se ve afectado por los cambios en las tablas subyacentes.

El valor de `GetRecordCount` desde un tipo de tabla refleja el número aproximado de registros en la tabla de conjunto de registros y se verá afectado inmediatamente se agregan y eliminan registros de la tabla.

Un conjunto de registros sin registros devuelve un valor de 0. Al trabajar con tablas asociadas o bases de datos ODBC, `GetRecordCount` siempre devuelve - 1. Una llamada a la `Requery` función miembro en un conjunto de registros restablece el valor de `GetRecordCount` como si se vuelve a ejecutar la consulta.

Para obtener información relacionada, vea el tema "Propiedad RecordCount" en la Ayuda de DAO.

##  <a name="getsql"></a>  CDaoRecordset::GetSQL

Llame a esta función miembro para obtener la instrucción SQL que se utiliza para seleccionar registros del conjunto de registros cuando se abre.

```
CString GetSQL() const;
```

### <a name="return-value"></a>Valor devuelto

Un `CString` que contiene la instrucción SQL.

### <a name="remarks"></a>Comentarios

Esto suele ser una instancia de SQL **seleccione** instrucción.

La cadena devuelta por `GetSQL` suele ser diferente de cualquier cadena que se ha pasado al conjunto de registros en el *lpszSQL* parámetro para el [abierto](#open) función miembro. Esto es porque el conjunto de registros construye una instrucción SQL completa según lo que pasó a `Open`, lo que especifique con ClassWizard y que pueda haber especificado en el [m_strFilter](#m_strfilter) y [m_strSort](#m_strsort) los miembros de datos.

> [!NOTE]
>  Llame a esta función miembro solo después de llamar a `Open`.

Para obtener información relacionada, vea el tema "Propiedades de SQL" en la Ayuda de DAO.

##  <a name="gettype"></a>  CDaoRecordset::GetType

Llame a esta función miembro después de abrir el conjunto de registros para determinar el tipo del objeto de conjunto de registros.

```
short GetType();
```

### <a name="return-value"></a>Valor devuelto

Uno de los siguientes valores que indica el tipo de un conjunto de registros:

- `dbOpenTable` Conjunto de registros de tipo de tabla

- `dbOpenDynaset` Registros de tipo dinámico

- `dbOpenSnapshot` Conjunto de registros de tipo de instantánea

### <a name="remarks"></a>Comentarios

Para obtener información relacionada, vea el tema "Propiedad de tipo" en la Ayuda de DAO.

##  <a name="getvalidationrule"></a>  CDaoRecordset::GetValidationRule

Llame a esta función miembro para determinar la regla utilizada para validar los datos.

```
CString GetValidationRule();
```

### <a name="return-value"></a>Valor devuelto

Un `CString` objeto que contiene un valor que valida los datos de un registro cuando se cambia o se agregan a una tabla.

### <a name="remarks"></a>Comentarios

Esta regla está basado en texto y se aplica cada vez que cambia la tabla subyacente. Si los datos no están legales, MFC inicia una excepción. El mensaje de error devuelto es el texto de la propiedad de texto de validación del objeto de campo subyacente, si se especifica, o el texto de la expresión especificada por la propiedad ValidationRule del objeto de campo subyacente. Puede llamar a [GetValidationText](#getvalidationtext) para obtener el texto del mensaje de error.

Por ejemplo, un campo en un registro que requiere el día del mes podría tener una regla de validación, como "día entre 1 y 31."

Para obtener información relacionada, vea el tema "Propiedad ValidationRule" en la Ayuda de DAO.

##  <a name="getvalidationtext"></a>  CDaoRecordset::GetValidationText

Llame a esta función miembro para recuperar el texto de la propiedad de texto de validación del objeto de campo subyacente.

```
CString GetValidationText();
```

### <a name="return-value"></a>Valor devuelto

Un `CString` que contiene el texto del mensaje que se muestra si el valor de un campo no cumple la regla de validación del objeto de campo subyacente del objeto.

### <a name="remarks"></a>Comentarios

Para obtener información relacionada, vea el tema "Propiedad de texto de validación" en la Ayuda de DAO.

##  <a name="isbof"></a>  CDaoRecordset::IsBOF

Llame a esta función miembro antes de desplazarse de registro a registro para obtener información sobre si ha realizado antes del primer registro del conjunto de registros.

```
BOOL IsBOF() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el conjunto de registros no contiene registros o si se ha desplazado hacia atrás antes del primer registro; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

También puede llamar a `IsBOF` junto con `IsEOF` para determinar si el conjunto de registros contiene registros o está vacío. Inmediatamente después de llamar a `Open`, si el conjunto de registros no contiene ningún registro, `IsBOF` devuelve cero. Al abrir un conjunto de registros que tiene al menos un registro, el primer registro es el registro actual y `IsBOF` devuelve 0.

Si el primer registro es el registro actual y se llama `MovePrev`, `IsBOF` posteriormente devolverá distinto de cero. Si `IsBOF` devuelve distinto de cero y se llama a `MovePrev`, se produce una excepción. Si `IsBOF` devuelve distinto de cero, el registro actual no está definido, y cualquier acción que requiere un registro actual se producirá una excepción.

Efecto de los métodos específicos en `IsBOF` y `IsEOF` configuración:

- Una llamada a `Open*` internamente hace que el primer registro en el conjunto de registros del registro actual mediante una llamada a `MoveFirst`. Por lo tanto, una llamada a `Open` en un conjunto de causas de registros vacío `IsBOF` y `IsEOF` para devolver distinto de cero. (Consulte la tabla siguiente para el comportamiento de un error `MoveFirst` o `MoveLast` llamar a.)

- Hacer que todas las operaciones de movimiento que puede encontrar un registro ambos `IsBOF` y `IsEOF` devuelva 0.

- Un `AddNew` llamada seguido por un `Update` hará que la llamada que se inserta correctamente un nuevo registro `IsBOF` para devolver 0, pero solo si `IsEOF` ya es distinto de cero. El estado de `IsEOF` siempre permanecerá sin cambios. Tal como se define por el motor de base de datos Microsoft Jet, el puntero de registro actual de un conjunto de registros vacío es al final de un archivo, por lo que se inserta cualquier nuevo registro después del registro actual.

- Cualquier `Delete` llamada, incluso si quita el único registro de un conjunto de registros, no cambiará el valor de `IsBOF` o `IsEOF`.

Esta tabla muestra qué operaciones de movimiento están permitidas con diferentes combinaciones de `IsBOF` /  `IsEOF`.

||Métodos MoveFirst, MoveLast|MovePrev,<br /><br /> Mover < 0|Mover 0|MoveNext,<br /><br /> Mover > 0|
|------|-------------------------|-----------------------------|------------|-----------------------------|
|`IsBOF`= distinto de cero,<br /><br /> `IsEOF`=0|Permitido|Excepción|Excepción|Permitido|
|`IsBOF`=0,<br /><br /> `IsEOF`= distinto de cero|Permitido|Permitido|Excepción|Excepción|
|Ambos distinto de cero|Excepción|Excepción|Excepción|Excepción|
|Ambos 0|Permitido|Permitido|Permitido|Permitido|

Lo que permite una operación de movimiento no significa que la operación busque correctamente un registro. Simplemente indica que ha intentado realizar la operación de desplazamiento especificada se permite y no generará una excepción. El valor de la `IsBOF` y `IsEOF` funciones miembro pueden cambiar como resultado del intento de move.

El efecto de las operaciones de movimiento que no se encontró un registro en el valor de `IsBOF` y `IsEOF` configuración se muestra en la tabla siguiente.

||IsBOF|IsEOF|
|------|-----------|-----------|
|`MoveFirst`, `MoveLast`|Distinto de cero|Distinto de cero|
|`Move` 0|Sin cambios|Sin cambios|
|`MovePrev`, `Move` < 0|Distinto de cero|Sin cambios|
|`MoveNext`, `Move` > 0|Sin cambios|Distinto de cero|

Para obtener información relacionada, vea el tema "BOF, EOF (propiedades)" en la Ayuda de DAO.

##  <a name="isdeleted"></a>  CDaoRecordset::IsDeleted

Llame a esta función miembro para determinar si se ha eliminado el registro actual.

```
BOOL IsDeleted() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el conjunto de registros está situado en un registro eliminado. en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Si se desplaza a un registro y `IsDeleted` devuelve TRUE (distinto de cero), a continuación, debe desplazarse a otro registro para poder realizar cualquier otra operación de conjunto de registros.

> [!NOTE]
>  No es necesario comprobar el estado eliminado de registros en un conjunto de registros de tipo de tabla o de instantáneas. Dado que no se puede eliminar registros desde una instantánea, no hay ninguna necesidad de llamar a `IsDeleted`. Para conjuntos de registros de tipo de tabla, los registros eliminados se quitarán realmente el conjunto de registros. Una vez que se ha eliminado un registro, por el usuario, otro usuario, o en otro conjunto de registros no podrá volver a ese registro. Por lo tanto, no hay ninguna necesidad de llamar a `IsDeleted`.

Cuando se elimina un registro de un conjunto de registros dinámicos, se quita del conjunto de registros y no podrá volver a ese registro. Sin embargo, si un registro en un conjunto de registros dinámicos se elimina por otro usuario o en otro conjunto de registros basándose en la misma tabla, `IsDeleted` devolverá TRUE cuando se desplaza más adelante para ese registro.

Para obtener información relacionada, vea los temas "Método Delete", "Propiedad LastModified" y "Propiedad EditMode" en la Ayuda de DAO.

##  <a name="iseof"></a>  CDaoRecordset::IsEOF

Llame a esta función miembro como desplazarse de registro a registro para obtener información sobre si han ido más allá del último registro del conjunto de registros.

```
BOOL IsEOF() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el conjunto de registros no contiene registros o si se ha desplazado más allá del último registro; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

También puede llamar a `IsEOF` para determinar si el conjunto de registros contiene registros o está vacío. Inmediatamente después de llamar a `Open`, si el conjunto de registros no contiene ningún registro, `IsEOF` devuelve cero. Al abrir un conjunto de registros que tiene al menos un registro, el primer registro es el registro actual y `IsEOF` devuelve 0.

Si el último registro es el registro actual cuando se llama a `MoveNext`, `IsEOF` posteriormente devolverá distinto de cero. Si `IsEOF` devuelve distinto de cero y se llama a `MoveNext`, se produce una excepción. Si `IsEOF` devuelve distinto de cero, el registro actual no está definido, y cualquier acción que requiere un registro actual se producirá una excepción.

Efecto de los métodos específicos en `IsBOF` y `IsEOF` configuración:

- Una llamada a `Open` internamente hace que el primer registro en el conjunto de registros del registro actual mediante una llamada a `MoveFirst`. Por lo tanto, una llamada a `Open` en un conjunto de causas de registros vacío `IsBOF` y `IsEOF` para devolver distinto de cero. (Consulte la tabla siguiente para el comportamiento de un error `MoveFirst` llamar a.)

- Hacer que todas las operaciones de movimiento que puede encontrar un registro ambos `IsBOF` y `IsEOF` devuelva 0.

- Un `AddNew` llamada seguido por un `Update` hará que la llamada que se inserta correctamente un nuevo registro `IsBOF` para devolver 0, pero solo si `IsEOF` ya es distinto de cero. El estado de `IsEOF` siempre permanecerá sin cambios. Tal como se define por el motor de base de datos Microsoft Jet, el puntero de registro actual de un conjunto de registros vacío es al final de un archivo, por lo que se inserta cualquier nuevo registro después del registro actual.

- Cualquier `Delete` llamada, incluso si quita el único registro de un conjunto de registros, no cambiará el valor de `IsBOF` o `IsEOF`.

Esta tabla muestra qué operaciones de movimiento están permitidas con diferentes combinaciones de `IsBOF` /  `IsEOF`.

||Métodos MoveFirst, MoveLast|MovePrev,<br /><br /> Mover < 0|Mover 0|MoveNext,<br /><br /> Mover > 0|
|------|-------------------------|-----------------------------|------------|-----------------------------|
|`IsBOF`= distinto de cero,<br /><br /> `IsEOF`=0|Permitido|Excepción|Excepción|Permitido|
|`IsBOF`=0,<br /><br /> `IsEOF`= distinto de cero|Permitido|Permitido|Excepción|Excepción|
|Ambos distinto de cero|Excepción|Excepción|Excepción|Excepción|
|Ambos 0|Permitido|Permitido|Permitido|Permitido|

Lo que permite una operación de movimiento no significa que la operación busque correctamente un registro. Simplemente indica que ha intentado realizar la operación de desplazamiento especificada se permite y no generará una excepción. El valor de la `IsBOF` y `IsEOF` funciones miembro pueden cambiar como resultado del intento de Move.

El efecto de las operaciones de movimiento que no se encontró un registro en el valor de `IsBOF` y `IsEOF` configuración se muestra en la tabla siguiente.

||IsBOF|IsEOF|
|------|-----------|-----------|
|`MoveFirst`, `MoveLast`|Distinto de cero|Distinto de cero|
|`Move` 0|Sin cambios|Sin cambios|
|`MovePrev`, `Move` < 0|Distinto de cero|Sin cambios|
|`MoveNext`, `Move` > 0|Sin cambios|Distinto de cero|

Para obtener información relacionada, vea el tema "BOF, EOF (propiedades)" en la Ayuda de DAO.

##  <a name="isfielddirty"></a>  CDaoRecordset::IsFieldDirty

Llame a esta función miembro determinar si el miembro de datos del campo especificado del tipo dinámico se ha marcado como "sucio" (cambia).

```
BOOL IsFieldDirty(void* pv);
```

### <a name="parameters"></a>Parámetros

*PV*<br/>
Un puntero a miembro de datos del campo cuyo estado desea comprobar, o NULL para determinar si cualquiera de los campos estén modificado.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el miembro de datos del campo especificado se marca como modificado; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Los datos en todos los miembros de datos de campos modificados se transferirá al registro en el origen de datos cuando se actualiza el registro actual mediante una llamada a la `Update` función miembro de `CDaoRecordset` (después de una llamada a `Edit` o `AddNew`). Con este conocimiento, puede realizar más pasos, como quitar marcadores el miembro de datos de campo para marcar la columna, por lo que no se escribirán en el origen de datos.

`IsFieldDirty` se implementa a través de `DoFieldExchange`.

##  <a name="isfieldnull"></a>  CDaoRecordset::IsFieldNull

Llame a esta función miembro para determinar si el miembro de un conjunto de registros de datos de campo especificado se ha marcado como Null.

```
BOOL IsFieldNull(void* pv);
```

### <a name="parameters"></a>Parámetros

*PV*<br/>
Un puntero a miembro de datos del campo cuyo estado desea comprobar o NULL para determinar si cualquiera de los campos son Null.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el miembro de datos del campo especificado se marca como Null; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

(En la terminología de base de datos, Null significa "no tener ningún valor" y no es igual a NULL en C++). Si un miembro de datos de campo se marca como Null, se interpreta como una columna del registro actual para el que no hay ningún valor.

> [!NOTE]
>  En determinadas situaciones, mediante `IsFieldNull` puede ser ineficaz, como se muestra en el ejemplo de código siguiente:

[!code-cpp[NVC_MFCDatabase#5](../../mfc/codesnippet/cpp/cdaorecordset-class_5.cpp)]

> [!NOTE]
>  Si se utiliza un enlace de registros dinámico, sin que derivar de `CDaoRecordset`, procure usar VT_NULL tal como se muestra en el ejemplo.

##  <a name="isfieldnullable"></a>  CDaoRecordset::IsFieldNullable

Llame a esta función miembro determinar si el miembro de datos del campo especificado es "que acepta valores null" (se pueden establecer en un valor Null; C++ NULL no es igual a Null, lo que, en la terminología de base de datos, significa "no tener ningún valor").

```
BOOL IsFieldNullable(void* pv);
```

### <a name="parameters"></a>Parámetros

*PV*<br/>
Un puntero a miembro de datos del campo cuyo estado desea comprobar o NULL para determinar si cualquiera de los campos son Null.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se puede establecer el miembro de datos del campo especificado es Null; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Un campo que no puede ser Null debe tener un valor. Si se intenta establecer este campo como Null al agregar o actualizar un registro, el origen de datos rechaza la adición o actualización, y `Update` se iniciará una excepción. La excepción se produce cuando se llama a `Update`, no cuando se llama a `SetFieldNull`.

##  <a name="isopen"></a>  CDaoRecordset::IsOpen

Llame a esta función miembro para determinar si el conjunto de registros está abierto.

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el objeto recordset `Open` o `Requery` función miembro se ha llamado previamente y el conjunto de registros no se ha cerrado; en caso contrario, 0.

### <a name="remarks"></a>Comentarios

##  <a name="m_bcheckcachefordirtyfields"></a>  CDaoRecordset:: M_bcheckcachefordirtyfields

Contiene una marca que indica si los campos almacenados en caché se marcan automáticamente como desfasadas (modificados) y Null.

### <a name="remarks"></a>Comentarios

El valor predeterminado de la marca es TRUE. La configuración de este miembro de datos controla todo el mecanismo de almacenamiento en búfer doble. Si establece la marca en TRUE, puede desactivar el almacenamiento en caché según el campo por campo mediante el mecanismo de DFX. Si la marca se establece en FALSE, debe llamar a `SetFieldDirty` y `SetFieldNull` usted mismo.

Establecer este miembro de datos antes de llamar a `Open`. Este mecanismo es principalmente para su facilidad de uso. Rendimiento puede ser más lento debido a que el búfer doble de campos cuando se realizan cambios.

##  <a name="m_nfields"></a>  CDaoRecordset::m_nFields

Contiene el número de miembros de datos en la clase de conjunto de registros y el número de columnas seleccionadas por el conjunto de registros del origen de datos.

### <a name="remarks"></a>Comentarios

Debe inicializar el constructor de la clase de conjunto de registros `m_nFields` con el número correcto de los campos enlazados estáticamente. ClassWizard escribe esta inicialización automáticamente cuando se usa para declarar la clase de conjunto de registros. También puede escribir manualmente.

El marco de trabajo utiliza este número para administrar la interacción entre los miembros de datos de campo y las columnas correspondientes del registro actual en el origen de datos.

> [!NOTE]
>  Este número debe coincidir con el número de columnas de salida registrada en `DoFieldExchange` después de llamar a `SetFieldType` con el parámetro `CDaoFieldExchange::outputColumn`.

Puede enlazar columnas dinámicamente por medio de `CDaoRecordset::GetFieldValue` y `CDaoRecordset::SetFieldValue`. Si lo hace, no es necesario incrementar el recuento en `m_nFields` para reflejar el número de función DFX llamadas su `DoFieldExchange` función miembro.

##  <a name="m_nparams"></a>  CDaoRecordset::m_nParams

Contiene el número de miembros de datos de parámetro en la clase de conjunto de registros: el número de parámetros pasados con la consulta.

### <a name="remarks"></a>Comentarios

Si la clase de conjunto de registros tiene miembros de datos de parámetro, debe inicializar el constructor de la clase *m_nParams* con el número correcto. El valor de *m_nParams* el valor predeterminado es 0. Si agrega miembros de datos de parámetro, lo que debe hacer manualmente, debe agregar manualmente una inicialización en el constructor de clase para reflejar el número de parámetros (que debe ser al menos tan grande como el número de '' marcadores de posición en su *m_strFilter*  o *m_strSort* cadena).

El marco de trabajo utiliza este número cuando parametriza la consulta.

> [!NOTE]
>  Este número debe coincidir con el número de "params" registrado en `DoFieldExchange` después de llamar a `SetFieldType` con el parámetro `CFieldExchange::param`.

Para obtener información relacionada, vea el tema "Objeto de parámetro" en la Ayuda de DAO.

##  <a name="m_pdaorecordset"></a>  CDaoRecordset::m_pDAORecordset

Contiene un puntero a la interfaz OLE para el objeto de conjunto de registros DAO subyacente el `CDaoRecordset` objeto.

### <a name="remarks"></a>Comentarios

Use este puntero si necesita obtener acceso a la interfaz DAO directamente.

Para obtener información relacionada, vea el tema "Objeto de conjunto de registros" en la Ayuda de DAO.

##  <a name="m_pdatabase"></a>  CDaoRecordset::m_pDatabase

Contiene un puntero a la `CDaoDatabase` a través del cual el conjunto de registros está conectado a un origen de datos de objeto.

### <a name="remarks"></a>Comentarios

Esta variable se establece en dos formas. Por lo general, pasar un puntero a una ya está abierta `CDaoDatabase` cuando se construye el objeto recordset de objetos. Si se pasa NULL en su lugar, `CDaoRecordset` crea un `CDaoDatabase` objeto y lo abre. En cualquier caso, `CDaoRecordset` almacena el puntero en esta variable.

Normalmente no directamente debe usar el puntero almacenado en `m_pDatabase`. Si escribe sus propias extensiones para `CDaoRecordset`, sin embargo, es posible que deba utilizar el puntero. Por ejemplo, es posible que necesita el puntero si lanza su `CDaoException`(s).

Para obtener información relacionada, vea el tema "Objeto de base de datos" en la Ayuda de DAO.

##  <a name="m_strfilter"></a>  CDaoRecordset:: M_strfilter

Contiene una cadena que se utiliza para construir el **donde** cláusula de una instrucción SQL.

### <a name="remarks"></a>Comentarios

No incluye la palabra reservada **donde** para filtrar el conjunto de registros. El uso de este miembro de datos no es aplicable a los conjuntos de registros de tipo de tabla. El uso de `m_strFilter` no tiene ningún efecto al abrir un conjunto de registros utilizando un `CDaoQueryDef` puntero.

Use el formato de fecha (mes-año) de EE. UU. al filtrar los campos que contienen fechas, incluso si no usa la versión de Estados Unidos del motor de base de datos Microsoft Jet; en caso contrario, es posible que no se filtran los datos según lo esperado.

Para obtener información relacionada, vea el tema "Propiedad de filtro" en la Ayuda de DAO.

##  <a name="m_strsort"></a>  CDaoRecordset::m_strSort

Contiene una cadena que contiene el **ORDERBY** cláusula de una instrucción SQL sin las palabras reservadas **ORDERBY**.

### <a name="remarks"></a>Comentarios

Se puede ordenar los objetos de conjunto de registros de tipo de conjunto de registros dinámicos y de instantánea.

No se puede ordenar los objetos de conjunto de registros de tipo de tabla. Para determinar el criterio de ordenación de un conjunto de registros de tipo de tabla, llame a [SetCurrentIndex](#setcurrentindex).

El uso de *m_strSort* no tiene ningún efecto al abrir un conjunto de registros utilizando un `CDaoQueryDef` puntero.

Para obtener información relacionada, vea el tema "Propiedad de ordenación" en la Ayuda de DAO.

##  <a name="move"></a>  CDaoRecordset:: Move

Llame a esta función miembro para colocar el conjunto de registros *lRows* registros desde el registro actual.

```
virtual void Move(long lRows);
```

### <a name="parameters"></a>Parámetros

*lRows*<br/>
El número de registros para avanzar o retroceder. Los valores positivos mueven hacia delante, hacia el final del conjunto de registros. Los valores negativos se mueven hacia atrás y hacia el principio.

### <a name="remarks"></a>Comentarios

Puede mover hacia delante o hacia atrás. `Move( 1 )` es equivalente a `MoveNext`, y `Move( -1 )` es equivalente a `MovePrev`.

> [!CAUTION]
>  Llamar a cualquiera de los `Move` funciones produce una excepción si el conjunto de registros no tiene registros. En general, llame a ambos `IsBOF` y `IsEOF` antes de una operación de movimiento para determinar si el conjunto de registros tiene todos los registros. Después de llamar a `Open` o `Requery`, llamar a `IsBOF` o `IsEOF`.

> [!NOTE]
>  Si se ha desplazado más allá del principio o final del conjunto de registros ( `IsBOF` o `IsEOF` devuelve distinto de cero), una llamada a `Move` produce una `CDaoException`.

> [!NOTE]
>  Si se llama a cualquiera de los `Move` funciona mientras el registro actual se actualiza o agregado, las actualizaciones se pierden sin previo aviso.

Cuando se llama a `Move` en una instantánea de desplazamiento solo hacia delante, el *lRows* parámetro debe ser un entero positivo y no se permiten marcadores, por lo que puede mover hacia delante solo.

Para realizar la primera, última, siguiente o anterior grabar en un conjunto de registros de la llamada actual de registros, la `MoveFirst`, `MoveLast`, `MoveNext`, o `MovePrev` función miembro.

Para obtener información relacionada, vea los temas "Método Move" y "MoveFirst, MoveLast, MoveNext y MovePrevious" en la Ayuda de DAO.

##  <a name="movefirst"></a>  CDaoRecordset::MoveFirst

Llame a esta función miembro para realizar el primer registro en el conjunto de registros (si existe) del registro actual.

```
void MoveFirst();
```

### <a name="remarks"></a>Comentarios

No es necesario llamar a `MoveFirst` inmediatamente después de abrir el conjunto de registros. En ese momento, el primer registro (si existe) es automáticamente el registro actual.

> [!CAUTION]
>  Llamar a cualquiera de los `Move` funciones produce una excepción si el conjunto de registros no tiene registros. En general, llame a ambos `IsBOF` y `IsEOF` antes de una operación de movimiento para determinar si el conjunto de registros tiene todos los registros. Después de llamar a `Open` o `Requery`, llamar a `IsBOF` o `IsEOF`.

> [!NOTE]
>  Si se llama a cualquiera de los `Move` funciona mientras el registro actual se actualiza o agregado, las actualizaciones se pierden sin previo aviso.

Use el `Move` funciones para desplazarse por los registros sin aplicar una condición. Utilice las operaciones de búsqueda para localizar los registros en un tipo dinámico o un objeto de conjunto de registros de tipo de instantánea que satisfacen una condición determinada. Para buscar un registro en un objeto de conjunto de registros de tipo de tabla, llame a `Seek`.

Si el conjunto de registros se refiere a un conjunto de registros de tipo de tabla, el desplazamiento sigue índice actual de la tabla. Puede establecer el índice actual mediante la propiedad de índice del objeto DAO subyacente. Si no establece el índice actual, el orden de los registros devueltos es indefinido.

Si se llama a `MoveLast` en un objeto de conjunto de registros basado en una consulta SQL o la definición de consulta, la consulta se ve obligada a finalizar y el objeto de conjunto de registros esté completa.

No se puede llamar a la `MoveFirst` o `MovePrev` función miembro con una instantánea de desplazamiento solo hacia delante.

Para mover la posición del elemento actual registro de un objeto de conjunto de registros de un determinado número de registros hacia delante o hacia atrás, llame a `Move`.

Para obtener información relacionada, vea los temas "Método Move" y "MoveFirst, MoveLast, MoveNext y MovePrevious" en la Ayuda de DAO.

##  <a name="movelast"></a>  CDaoRecordset::MoveLast

Llame a esta función miembro para realizar el último registro (si existe) en el conjunto de registros del registro actual.

```
void MoveLast();
```

### <a name="remarks"></a>Comentarios

> [!CAUTION]
>  Llamar a cualquiera de los `Move` funciones produce una excepción si el conjunto de registros no tiene registros. En general, llame a ambos `IsBOF` y `IsEOF` antes de una operación de movimiento para determinar si el conjunto de registros tiene todos los registros. Después de llamar a `Open` o `Requery`, llamar a `IsBOF` o `IsEOF`.

> [!NOTE]
>  Si se llama a cualquiera de los `Move` funciona mientras el registro actual se actualiza o agregado, las actualizaciones se pierden sin previo aviso.

Use el `Move` funciones para desplazarse por los registros sin aplicar una condición. Utilice las operaciones de búsqueda para localizar los registros en un tipo dinámico o un objeto de conjunto de registros de tipo de instantánea que satisfacen una condición determinada. Para buscar un registro en un objeto de conjunto de registros de tipo de tabla, llame a `Seek`.

Si el conjunto de registros se refiere a un conjunto de registros de tipo de tabla, el desplazamiento sigue índice actual de la tabla. Puede establecer el índice actual mediante la propiedad de índice del objeto DAO subyacente. Si no establece el índice actual, el orden de los registros devueltos es indefinido.

Si se llama a `MoveLast` en un objeto de conjunto de registros basado en una consulta SQL o la definición de consulta, la consulta se ve obligada a finalizar y el objeto de conjunto de registros esté completa.

Para mover la posición del elemento actual registro de un objeto de conjunto de registros de un determinado número de registros hacia delante o hacia atrás, llame a `Move`.

Para obtener información relacionada, vea los temas "Método Move" y "MoveFirst, MoveLast, MoveNext y MovePrevious" en la Ayuda de DAO.

##  <a name="movenext"></a>  CDaoRecordset::MoveNext

Llame a esta función miembro para realizar el registro siguiente en el conjunto de registros del registro actual.

```
void MoveNext();
```

### <a name="remarks"></a>Comentarios

Se recomienda que llame a `IsBOF` antes de intentar mover al registro anterior. Una llamada a `MovePrev` producirá un `CDaoException` si `IsBOF` devuelve distinto de cero, que indica que ya se haya desplazado antes del primer registro o que no hay registros seleccionados por el conjunto de registros.

> [!CAUTION]
>  Llamar a cualquiera de los `Move` funciones produce una excepción si el conjunto de registros no tiene registros. En general, llame a ambos `IsBOF` y `IsEOF` antes de una operación de movimiento para determinar si el conjunto de registros tiene todos los registros. Después de llamar a `Open` o `Requery`, llamar a `IsBOF` o `IsEOF`.

> [!NOTE]
>  Si se llama a cualquiera de los `Move` funciona mientras el registro actual se actualiza o agregado, las actualizaciones se pierden sin previo aviso.

Use el `Move` funciones para desplazarse por los registros sin aplicar una condición. Utilice las operaciones de búsqueda para localizar los registros en un tipo dinámico o un objeto de conjunto de registros de tipo de instantánea que satisfacen una condición determinada. Para buscar un registro en un objeto de conjunto de registros de tipo de tabla, llame a `Seek`.

Si el conjunto de registros se refiere a un conjunto de registros de tipo de tabla, el desplazamiento sigue índice actual de la tabla. Puede establecer el índice actual mediante la propiedad de índice del objeto DAO subyacente. Si no establece el índice actual, el orden de los registros devueltos es indefinido.

Para mover la posición del elemento actual registro de un objeto de conjunto de registros de un determinado número de registros hacia delante o hacia atrás, llame a `Move`.

Para obtener información relacionada, vea los temas "Método Move" y "MoveFirst, MoveLast, MoveNext y MovePrevious" en la Ayuda de DAO.

##  <a name="moveprev"></a>  CDaoRecordset::MovePrev

Llame a esta función miembro para realizar el registro anterior en el conjunto de registros del registro actual.

```
void MovePrev();
```

### <a name="remarks"></a>Comentarios

Se recomienda que llame a `IsBOF` antes de intentar mover al registro anterior. Una llamada a `MovePrev` producirá un `CDaoException` si `IsBOF` devuelve distinto de cero, que indica que ya se haya desplazado antes del primer registro o que no hay registros seleccionados por el conjunto de registros.

> [!CAUTION]
>  Llamar a cualquiera de los `Move` funciones produce una excepción si el conjunto de registros no tiene registros. En general, llame a ambos `IsBOF` y `IsEOF` antes de una operación de movimiento para determinar si el conjunto de registros tiene todos los registros. Después de llamar a `Open` o `Requery`, llamar a `IsBOF` o `IsEOF`.

> [!NOTE]
>  Si se llama a cualquiera de los `Move` funciona mientras el registro actual se actualiza o agregado, las actualizaciones se pierden sin previo aviso.

Use el `Move` funciones para desplazarse por los registros sin aplicar una condición. Utilice las operaciones de búsqueda para localizar los registros en un tipo dinámico o un objeto de conjunto de registros de tipo de instantánea que satisfacen una condición determinada. Para buscar un registro en un objeto de conjunto de registros de tipo de tabla, llame a `Seek`.

Si el conjunto de registros se refiere a un conjunto de registros de tipo de tabla, el desplazamiento sigue índice actual de la tabla. Puede establecer el índice actual mediante la propiedad de índice del objeto DAO subyacente. Si no establece el índice actual, el orden de los registros devueltos es indefinido.

No se puede llamar a la `MoveFirst` o `MovePrev` función miembro con una instantánea de desplazamiento solo hacia delante.

Para mover la posición del elemento actual registro de un objeto de conjunto de registros de un determinado número de registros hacia delante o hacia atrás, llame a `Move`.

Para obtener información relacionada, vea los temas "Método Move" y "MoveFirst, MoveLast, MoveNext y MovePrevious" en la Ayuda de DAO.

##  <a name="open"></a>  CDaoRecordset:: Open

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
Uno de los siguientes valores:

- `dbOpenDynaset` Un conjunto de registros de tipo dinámico con desplazamiento bidireccional. Este es el valor predeterminado.

- `dbOpenTable` Un conjunto de registros de tipo de tabla con desplazamiento bidireccional.

- `dbOpenSnapshot` Un conjunto de registros de tipo de instantánea con desplazamiento bidireccional.

*lpszSQL*<br/>
Puntero de cadena que contiene uno de los elementos siguientes:

- Un puntero NULL.

- El nombre de una o varias definiciones de tabla o definiciones de consulta (separados por comas).

- Una instancia de SQL **seleccione** instrucción (opcionalmente con una instancia de SQL **donde** o **ORDERBY** cláusula).

- Una consulta de paso a través.

*nOptions*<br/>
Uno o más de las siguientes opciones. El valor predeterminado es 0. Los valores posibles son los siguientes:

- `dbAppendOnly` Sólo se pueden anexar nuevos registros (registros de tipo dinámico solo). Esta opción literalmente significa que solo se pueden anexar los registros. Las clases de base de datos ODBC de MFC tienen una opción de solo anexión que permite que los registros que recuperan y anexar.

- `dbForwardOnly` El conjunto de registros es una instantánea de desplazamiento solo hacia delante.

- `dbSeeChanges` Generar una excepción si otro usuario está cambiando los datos que se está editando.

- `dbDenyWrite` Otros usuarios no pueden modificar o agregar registros.

- `dbDenyRead` Otros usuarios no pueden ver los registros (solo conjunto de registros de tipo de tabla).

- `dbReadOnly` Solo se pueden ver registros; otros usuarios pueden modificarlas.

- `dbInconsistent` Las actualizaciones incoherentes se permiten (solo registros de tipo dinámico).

- `dbConsistent` Actualizaciones coherentes solo se permiten (solo registros de tipo dinámico).

> [!NOTE]
>  Las constantes `dbConsistent` y `dbInconsistent` son mutuamente excluyentes. Puede usar uno o el otro, pero no ambos en una instancia determinada de `Open`.

*pTableDef*<br/>
Un puntero a un [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md) objeto. Esta versión es válida sólo para conjuntos de registros de tipo de tabla. Cuando se usa esta opción, el `CDaoDatabase` puntero usado para construir el `CDaoRecordset` no se utiliza; en su lugar, se usa la base de datos en el que reside la definición de tabla.

*pQueryDef*<br/>
Un puntero a un [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md) objeto. Esta versión es válida únicamente para el tipo de conjunto de registros dinámicos y los conjuntos de registros de tipo de instantánea. Cuando se usa esta opción, el `CDaoDatabase` puntero usado para construir el `CDaoRecordset` no se utiliza; en su lugar, se usa la base de datos en el que reside la definición de consulta.

### <a name="remarks"></a>Comentarios

Antes de llamar a `Open`, debe construir el objeto de conjunto de registros. Existen varias formas de hacerlo:

- Cuando se construye el objeto de conjunto de registros, pasar un puntero a un `CDaoDatabase` objeto que ya está abierto.

- Cuando se construye el objeto de conjunto de registros, pasar un puntero a un `CDaoDatabase` objeto que no está abierto. El conjunto de registros se abre un `CDaoDatabase` de objeto, pero no la cerrará cuando se cierra el objeto de conjunto de registros.

- Cuando se construye el objeto de conjunto de registros, pasar un puntero NULL. Las llamadas de objeto de conjunto de registros `GetDefaultDBName` para obtener el nombre de Microsoft Access. Archivo MDB va a abrir. El conjunto de registros, a continuación, se abre un `CDaoDatabase` objeto y mantiene, se abre siempre que el conjunto de registros está abierto. Cuando se llama a `Close` en el conjunto de registros, la `CDaoDatabase` también se cierra el objeto.

    > [!NOTE]
    >  Cuando se abre el conjunto de registros el `CDaoDatabase` de objeto, se abre el origen de datos con acceso no exclusivo.

Para la versión de `Open` que usa el *lpszSQL* parámetro, una vez abierto el conjunto de registros puede recuperar registros de varias maneras. La primera opción es que las funciones DFX su `DoFieldExchange`. La segunda opción consiste en usar el enlace dinámico mediante una llamada a la `GetFieldValue` función miembro. Estas opciones se pueden implementar por separado o combinados. Si se combinan, tendrá que pasar en la instrucción SQL usted mismo en la llamada a `Open`.

Cuando se usa la segunda versión de `Open` donde se pasa en un `CDaoTableDef` de objetos, las columnas resultantes estará disponibles para enlazar a través de `DoFieldExchange` y el mecanismo DFX o enlazar dinámicamente mediante `GetFieldValue`.

> [!NOTE]
>  Solo puede llamar a `Open` mediante un `CDaoTableDef` objeto para conjuntos de registros de tipo de tabla.

Cuando se usa la tercera versión de `Open` donde se pasa en un `CDaoQueryDef` de objeto, que se ejecutará la consulta y las columnas resultantes estará disponibles para enlazar a través de `DoFieldExchange` y el mecanismo DFX o enlazar dinámicamente mediante `GetFieldValue`.

> [!NOTE]
>  Solo puede llamar a `Open` mediante un `CDaoQueryDef` objeto de tipo dinámico y los conjuntos de registros de tipo de instantánea.

Para la primera versión de `Open` que usa el `lpszSQL` parámetro, los registros están seleccionados según los criterios que se muestra en la tabla siguiente.

|Valor del parámetro `lpszSQL`|Los registros seleccionados están determinados por|Ejemplo|
|--------------------------------------|----------------------------------------|-------------|
|NULL|La cadena devuelta por `GetDefaultSQL`.||
|Una lista separada por comas de uno o más definiciones de tabla o nombres de definición de consulta.|Todas las columnas se representan en el `DoFieldExchange`.|`"Customer"`|
|**Seleccione** lista de columnas **FROM** lista de tablas|Las columnas especificadas del querydef(s) y/o tabledef(s) especificado.|`"SELECT CustId, CustName`<br /><br /> `FROM Customer"`|

El procedimiento habitual consiste en pasar NULL para `Open`; en ese caso, `Open` llamadas `GetDefaultSQL`, una función miembro reemplazables que ClassWizard genera al crear un `CDaoRecordset`-clase derivada. Este valor proporciona los nombres tabledef(s) o definición de consulta que especificó en el Asistente para clases. En su lugar, puede especificar otra información en el *lpszSQL* parámetro.

Cualquier valor que pase `Open` construye una cadena SQL final para la consulta (la cadena puede tener SQL **donde** y **ORDERBY** anexadas cláusulas a la *lpszSQL* cadena se pasó) y, a continuación, ejecuta la consulta. Puede examinar la cadena que se crea mediante una llamada a `GetSQL` después de llamar a `Open`.

Los miembros de datos de campo de la clase de conjunto de registros están enlazados a las columnas de los datos seleccionados. Si se devuelve algún registro, el primer registro se convierte en el registro actual.

Si desea establecer opciones para el conjunto de registros, por ejemplo, un filtro o criterio, establezca `m_strSort` o `m_strFilter` después de crear el objeto de conjunto de registros pero antes de llamar a `Open`. Si desea que los registros del conjunto de registros después de actualizar el conjunto de registros está abierto, llame a `Requery`.

Si se llama a `Open` en un tipo dinámico o un conjunto de registros de tipo de instantánea, o si el origen de datos hace referencia a una instrucción SQL o una definición de tabla que representa una tabla asociada, no se puede usar `dbOpenTable` para el argumento de tipo; si lo hace, MFC inicia una excepción. Para determinar si un objeto de definición de tabla representa una tabla asociada, cree un [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md) objeto y llamar a su [GetConnect](../../mfc/reference/cdaotabledef-class.md#getconnect) función miembro.

Use el `dbSeeChanges` marca si quiere capturar los cambios realizados por otro usuario u otro programa en el equipo cuando está modificando o eliminando el mismo registro. Por ejemplo, si dos usuarios empiezan a editar el mismo registro, el primer usuario que llame a la `Update` función miembro se realiza correctamente. Cuando `Update` es llamado por el segundo usuario, un `CDaoException` se produce. De forma similar, si el segundo usuario intenta llamar a `Delete` eliminar el registro y ya ha cambiado el primer usuario, un `CDaoException` se produce.

Normalmente, si el usuario obtiene este `CDaoException` durante la actualización, el código debe actualizar el contenido de los campos y recuperar los valores modificados recientemente. Si se produce la excepción en el proceso de eliminación, el código puede mostrar los datos de registro nuevo para el usuario y un mensaje que indica que los datos han cambiado recientemente. En este momento, el código puede solicitar una confirmación de que el usuario aún desea eliminar el registro.

> [!TIP]
>  Utilice la opción de desplazamiento solo hacia delante (`dbForwardOnly`) mejorar el rendimiento cuando la aplicación realiza un único paso a través de un conjunto de registros abierto desde un origen de datos ODBC.

Para obtener información relacionada, vea el tema "Método OpenRecordset" en la Ayuda de DAO.

##  <a name="requery"></a>  CDaoRecordset::Requery

Llame a esta función miembro para volver a generar (actualizar) un conjunto de registros.

```
virtual void Requery();
```

### <a name="remarks"></a>Comentarios

Si se devuelve algún registro, el primer registro se convierte en el registro actual.

En orden para el conjunto de registros reflejar las adiciones y eliminaciones que usted u otros usuarios están realizando al origen de datos, debe volver a generar el conjunto de registros mediante una llamada a `Requery`. Si el conjunto de registros es de tipo dinámico, refleja automáticamente las actualizaciones que hacen que usted u otros usuarios a sus registros existentes (pero no las adiciones). Si el conjunto de registros es una instantánea, se debe llamar a `Requery` para reflejar modificaciones realizadas por otros usuarios, así como las adiciones y eliminaciones.

Para un tipo dinámico o una instantánea, llame a `Requery` siempre que desee volver a generar el conjunto de registros con valores de parámetros. Establezca el nuevo filtro u ordenar estableciendo [m_strFilter](#m_strfilter) y [m_strSort](#m_strsort) antes de llamar a `Requery`. Definir nuevos parámetros asignando nuevos valores a los miembros de datos de parámetro antes de llamar a `Requery`.

Si se produce un error en el intento de volver a generar el conjunto de registros, se cierra el conjunto de registros. Antes de llamar a `Requery`, puede determinar si se puede consultar el conjunto de registros mediante una llamada a la [CanRestart](#canrestart) función miembro. `CanRestart` no garantiza que `Requery` se realizará correctamente.

> [!CAUTION]
>  Llame a `Requery` solo después de haber llamado `Open`.

> [!NOTE]
>  Una llamada a [Requery](#requery) cambia los marcadores DAO.

No se puede llamar a `Requery` en un tipo dinámico o un conjunto de registros de tipo de instantánea si una llamada a `CanRestart` devuelve 0, ni puede usarla en un conjunto de registros de tipo de tabla.

Si ambos `IsBOF` y `IsEOF` devolver distinto de cero después de llamar a `Requery`, la consulta no devolvió ningún registro y el conjunto de registros no contendrán ningún dato.

Para obtener información relacionada, vea el tema "Método Requery" en la Ayuda de DAO.

##  <a name="seek"></a>  CDaoRecordset::Seek

Llame a esta función miembro para encontrar el registro en un objeto de conjunto de registros de tipo tabla indizada que satisface los criterios especificados para el actual de índice y convierte ese registro en el registro actual.

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
Una de las expresiones de cadena siguientes: "<","\<=", "=", "> =", o ">".

*pKey1*<br/>
Un puntero a un [COleVariant](../../mfc/reference/colevariant-class.md) cuyo valor corresponde al primer campo en el índice. Requerido.

*pKey2*<br/>
Un puntero a un `COleVariant` cuyo valor corresponde al segundo campo del índice, si existe. El valor predeterminado es NULL.

*pKey3*<br/>
Un puntero a un `COleVariant` cuyo valor corresponde al tercer campo en el índice, si existe. El valor predeterminado es NULL.

*pKeyArray*<br/>
Un puntero a una matriz de variantes. El tamaño de matriz corresponde al número de campos en el índice.

*nKeys*<br/>
Un entero correspondiente al tamaño de la matriz, que es el número de campos en el índice.

> [!NOTE]
>  No se especifican caracteres comodín en las claves. Hará que los caracteres comodín `Seek` para no devolver ningún registro coincidente.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se encuentran los registros coincidentes, en caso contrario, 0.

### <a name="remarks"></a>Comentarios

Use la segunda versión (matriz) de `Seek` para administrar los índices de campos de cuatro o más.

`Seek` permite buscar en conjuntos de registros de tipo de tabla de índice de alto rendimiento. Debe establecer el índice actual mediante una llamada a `SetCurrentIndex` antes de llamar a `Seek`. Si el índice que identifica un único campo o campos clave, `Seek` localiza el primer registro que satisface los criterios. Si no establece un índice, se produce una excepción.

Tenga en cuenta que si no va a crear un conjunto de registros UNICODE, el `COleVariant` objetos se deben declarar explícitamente ANSI. Esto puede hacerse mediante el uso de la [COleVariant::COleVariant](../../mfc/reference/colevariant-class.md#colevariant)**(** *lpszSrc* **,** *vtSrc* **)**  formulario del constructor con *vtSrc* establecido en `VT_BSTRT` (ANSI) o mediante el `COleVariant` función [SetString](../../mfc/reference/colevariant-class.md#setstring)**(** *lpszSrc* **,** *vtSrc* **)** con *vtSrc* establecido en `VT_BSTRT`.

Cuando se llama a `Seek`, pasar uno o más valores de clave y un operador de comparación ("<","\<=", "=", "> =", o ">"). `Seek` busca en los campos de clave especificados y localiza el primer registro que satisface los criterios especificados por *lpszComparison* y *pKey1*. Una vez encontrado, `Seek` devuelve distinto de cero y hace que dicho registro actual. Si `Seek` no encuentra una coincidencia, `Seek` devuelve cero y el registro actual es indefinido. Al usar DAO directamente, debe comprobar explícitamente la propiedad NoMatch.

Si `lpszComparison` es "=", "> =", o ">", `Seek` comienza al principio del índice. Si *lpszComparison* es "<" o "< =", `Seek` se inicia al final del índice y busca hacia atrás a menos que haya entradas de índice duplicados al final. En este caso, `Seek` comienza en una entrada arbitraria entre las entradas de índice duplicados al final del índice.

Allí no tiene que ser un registro actual cuando se usa `Seek`.

Para buscar un registro en un tipo dinámico o un conjunto de registros de tipo de instantánea que satisface una condición específica, utilice las operaciones de búsqueda. Para incluir todos los registros, no solo aquellos que satisfacen una condición específica, utilice las operaciones de movimiento para desplazarse por los registros.

No se puede llamar a `Seek` en una tabla asociada de cualquier tipo porque las tablas asociadas deben estar abiertas como tipo dinámico o conjuntos de registros de tipo de instantánea. Sin embargo, si se llama a `CDaoDatabase::Open` para abrir directamente una base de datos ISAM instalable, puede llamar a `Seek` en las tablas de base de datos, aunque el rendimiento puede ser lenta.

Para obtener información relacionada, vea el tema "Método Seek" en la Ayuda de DAO.

##  <a name="setabsoluteposition"></a>  CDaoRecordset:: SetAbsolutePosition

Establece el número de registro relativo del registro actual del objeto de un conjunto de registros.

```
void SetAbsolutePosition(long lPosition);
```

### <a name="parameters"></a>Parámetros

*lPosition*<br/>
Corresponde a la posición ordinal del registro actual en el conjunto de registros.

### <a name="remarks"></a>Comentarios

Una llamada a `SetAbsolutePosition` permite colocar el puntero de registro actual a un registro concreto según su posición ordinal en un tipo dinámico o un conjunto de registros de tipo de instantánea. También puede determinar el número de registros actual mediante una llamada a [GetAbsolutePosition](#getabsoluteposition).

> [!NOTE]
>  Esta función miembro es válida únicamente para el tipo de conjunto de registros dinámicos y los conjuntos de registros de tipo de instantánea.

El valor de propiedad AbsolutePosition del objeto DAO subyacente está basado en cero; un valor de 0 hace referencia al primer registro en el conjunto de registros. Establecer un valor mayor que el número de registros llenados, MFC para producir una excepción. Puede determinar el número de registros rellenados en el conjunto de registros mediante una llamada a la `GetRecordCount` función miembro.

Si se elimina el registro actual, no está definido el valor de propiedad AbsolutePosition y MFC produce una excepción si se hace referencia. Nuevos registros se agregan al final de la secuencia.

> [!NOTE]
>  Esta propiedad no pretende utilizarse como un número de registro suplente. Los marcadores siguen siendo la forma recomendada de retener y volver a una posición determinada y son la única forma de colocar el registro actual en todos los tipos de objetos de conjunto de registros que admiten marcadores. En concreto, la posición de un registro determinado cambia cuando se eliminan los registros que le precede. También no hay ninguna garantía de que un registro determinado tendrá la misma posición absoluta si se vuelve a crear el conjunto de registros, porque no se garantiza el orden de los registros individuales dentro de un conjunto de registros, a menos que se crea con una instrucción SQL mediante un  **ORDERBY** cláusula.

Para obtener información relacionada, vea el tema "Propiedad AbsolutePosition" en la Ayuda de DAO.

##  <a name="setbookmark"></a>  CDaoRecordset:: SetBookmark

Llame a esta función miembro para colocar el conjunto de registros en el registro que contiene el marcador especificado.

```
void SetBookmark(COleVariant varBookmark);
```

### <a name="parameters"></a>Parámetros

*varBookmark*<br/>
Un [COleVariant](../../mfc/reference/colevariant-class.md) objeto que contiene el valor de marcador de un registro específico.

### <a name="remarks"></a>Comentarios

Cuando se crea o se abre un objeto de conjunto de registros, cada uno de sus registros ya tiene un marcador único. Puede recuperar el marcador para el registro actual mediante una llamada a `GetBookmark` y guardar el valor a un `COleVariant` objeto. Más adelante puede volver a ese registro mediante una llamada a `SetBookmark` utilizando el valor de marcador guardado.

> [!NOTE]
>  Una llamada a [Requery](#requery) cambia los marcadores DAO.

Tenga en cuenta que si no va a crear un conjunto de registros UNICODE, el `COleVariant` objeto se debe declarar explícitamente ANSI. Esto puede hacerse mediante el uso de la [COleVariant::COleVariant](../../mfc/reference/colevariant-class.md#colevariant)**(** *lpszSrc* **,** *vtSrc* **)**  formulario del constructor con *vtSrc* establecido en `VT_BSTRT` (ANSI) o mediante el `COleVariant` función [SetString](../../mfc/reference/colevariant-class.md#setstring)**(** *lpszSrc* **,** *vtSrc* **)** con *vtSrc* establecido en `VT_BSTRT`.

Para obtener información relacionada, vea los temas "Marcador de propiedad" y la propiedad es"en la Ayuda de DAO.

##  <a name="setcachesize"></a>  CDaoRecordset:: SetCacheSize

Llame a esta función miembro para establecer el número de registros en la memoria caché.

```
void SetCacheSize(long lSize);
```

### <a name="parameters"></a>Parámetros

*lSize*<br/>
Especifica el número de registros. Un valor típico es 100. Un valor de 0 desactiva la caché. El valor debe estar entre 5 y 1200 registros. La memoria caché puede utilizar una considerable cantidad de memoria.

### <a name="remarks"></a>Comentarios

Una memoria caché es un espacio en la memoria local que contiene los datos recientemente recuperados del servidor en caso de que los datos volverá a solicitarse mientras se ejecuta la aplicación. Datos en caché mejoran el rendimiento de una aplicación que recupera datos de un servidor remoto a través de objetos de conjunto de registros de tipo dinámico. Cuando se solicitan datos, el motor de base de datos Microsoft Jet comprueba primero la caché de los datos solicitados en lugar de recuperarlos desde el servidor, lo que requiere más tiempo. Datos que no proceden de un origen de datos ODBC no se guardan en la memoria caché.

Cualquier origen de datos ODBC, como una tabla asociada, puede tener una caché local. Para crear la memoria caché, abra un objeto de conjunto de registros desde el origen de datos remoto, llamada la `SetCacheSize` y `SetCacheStart` funciones miembro y, a continuación, llame el `FillCache` paso a través de los registros mediante una de las operaciones de movimiento o función miembro. El *lSize* parámetro de la `SetCacheSize` función miembro puede basarse en el número de registros de la aplicación puede funcionar al mismo tiempo. Por ejemplo, si utiliza un conjunto de registros como origen de los datos que se mostrará en la pantalla, podría pasar el `SetCacheSize` *lSize* parámetro como 20 para mostrar 20 registros al mismo tiempo.

Para obtener información relacionada, vea el tema "CacheSize, CacheStart propiedades" en la Ayuda de DAO.

##  <a name="setcachestart"></a>  CDaoRecordset:: SetCacheStart

Llame a esta función miembro para especificar el marcador del primer registro en el conjunto de registros en la memoria caché.

```
void SetCacheStart(COleVariant varBookmark);
```

### <a name="parameters"></a>Parámetros

*varBookmark*<br/>
Un [COleVariant](../../mfc/reference/colevariant-class.md) que especifica el marcador del primer registro en el conjunto de registros en la memoria caché.

### <a name="remarks"></a>Comentarios

Puede usar el valor de marcador de todos los registros para el *varBookmark* parámetro de la `SetCacheStart` función miembro. Realizar el registro que desea iniciar la memoria caché con el registro actual, establecer un marcador para ese registro mediante [SetBookmark](#setbookmark)y pase el valor de marcador como parámetro para el `SetCacheStart` función miembro.

El motor de base de datos Microsoft Jet solicita registros dentro del intervalo de memoria caché de la memoria caché y solicita registros fuera del intervalo de memoria caché del servidor.

Los registros recuperados de la memoria caché no reflejan los cambios realizados al mismo tiempo al origen de datos por otros usuarios.

Para forzar una actualización de todos los datos almacenados en caché, pase el *lSize* parámetro de `SetCacheSize` como 0, llame a `SetCacheSize` nuevo con el tamaño de la memoria caché que solicitó originalmente y, a continuación, llame a la `FillCache` función miembro.

Tenga en cuenta que si no va a crear un conjunto de registros UNICODE, el `COleVariant` objeto se debe declarar explícitamente ANSI. Esto puede hacerse mediante el uso de la [COleVariant::COleVariant](../../mfc/reference/colevariant-class.md#colevariant)**(** *lpszSrc* **,** *vtSrc* **)**  formulario del constructor con *vtSrc* establecido en `VT_BSTRT` (ANSI) o mediante el `COleVariant` función [SetString](../../mfc/reference/colevariant-class.md#setstring)**(** *lpszSrc* **,** *vtSrc* **)** con *vtSrc* establecido en `VT_BSTRT`.

Para obtener información relacionada, vea el tema CacheSize, CacheStart propiedades"en la Ayuda de DAO.

##  <a name="setcurrentindex"></a>  CDaoRecordset:: SetCurrentIndex

Llame a esta función miembro para establecer un índice en un conjunto de registros de tipo de tabla.

```
void SetCurrentIndex(LPCTSTR lpszIndex);
```

### <a name="parameters"></a>Parámetros

*lpszIndex*<br/>
Un puntero que contiene el nombre del índice debe establecerse.

### <a name="remarks"></a>Comentarios

Registros de las tablas bases no se almacenan en ningún orden concreto. Un índice de configuración cambia el orden de los registros devueltos desde la base de datos, pero no afecta el orden en que se almacenan los registros. Ya se debe definir el índice especificado. Si intenta usar un objeto de índice que no existe, o si el índice no se establece cuando se llama a [Seek](#seek), MFC inicia una excepción.

Puede crear un nuevo índice para la tabla mediante una llamada a [CDaoTableDef::CreateIndex](../../mfc/reference/cdaotabledef-class.md#createindex) y anexar el nuevo índice a la colección de índices de la definición de tabla subyacente mediante una llamada a [CDaoTableDef:: Append](../../mfc/reference/cdaotabledef-class.md#append), y a continuación, volver a abrir el conjunto de registros.

Los registros devueltos desde un conjunto de registros de tipo de tabla se pueden ordenar solo por los índices definidos para la definición de tabla subyacente. Para ordenar los registros en otro orden, puede abrir un tipo dinámico o un conjunto de registros de tipo de instantánea mediante una instancia de SQL **ORDERBY** cláusula almacenados en [CDaoRecordset::m_strSort](#m_strsort).

Para obtener información relacionada, vea el tema "Objeto Index" y la definición de "índice actual" en la Ayuda de DAO.

##  <a name="setfielddirty"></a>  CDaoRecordset:: SetFieldDirty

Llame a esta función miembro para marcar a un miembro de datos de campo del conjunto de registros como modificado o no como modificado.

```
void SetFieldDirty(
    void* pv,
    BOOL bDirty = TRUE);
```

### <a name="parameters"></a>Parámetros

*PV*<br/>
Contiene la dirección de un miembro de datos de campo en el conjunto de registros o NULL. Si es NULL, se marcan todos los miembros de datos de campo del conjunto de registros. (C++ NULL no es igual a Null en la terminología de base de datos, lo que significa "no tener ningún valor.")

*bDirty*<br/>
TRUE si es miembro de datos del campo se marca como "sucio" (modificado). En caso contrario, es FALSE si el miembro de datos de campo se marca como "limpiar" (sin cambios).

### <a name="remarks"></a>Comentarios

Marcar campos como sin cambios garantiza que no se actualiza el campo.

Las marcas de marco de trabajo puede cambiar los miembros de datos de campo para asegurarse de que se escribirá en el registro del origen de datos mediante el mecanismo de intercambio (DFX) de campos de registros DAO. Cambiar el valor de un campo normalmente establece el campo desfasadas automáticamente, por lo que rara vez necesitará llamar a `SetFieldDirty` usted mismo, pero a veces, conviene asegurarse de que las columnas se explícitamente actualizadas o insertadas independientemente del valor que se encuentra en los datos del campo miembro. El mecanismo DFX también emplea el uso de PSEUDONULL. Para obtener más información, consulte [CDaoFieldExchange:: M_noperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation).

Si no se utiliza el mecanismo de almacenamiento en búfer doble, a continuación, cambiar el valor del campo no establece automáticamente el campo como modificado. En este caso, será necesario establecer explícitamente el campo como modificado. La marca contenida en [m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields) controla la comprobación automática de campos.

> [!NOTE]
>  Llame a esta función miembro después de haber llamado [editar](#edit) o [AddNew](#addnew).

El uso de NULL para el primer argumento de la función aplicará la función a todos los `outputColumn` campos, no **param** campos `CDaoFieldExchange`. Por ejemplo, la llamada

[!code-cpp[NVC_MFCDatabase#6](../../mfc/codesnippet/cpp/cdaorecordset-class_6.cpp)]

establecerá sólo `outputColumn` campos con NULL; **param** campos no se verán afectados.

Para trabajar en un **param**, debe proporcionar la dirección real de la persona **param** que desea trabajar, tales como:

[!code-cpp[NVC_MFCDatabase#7](../../mfc/codesnippet/cpp/cdaorecordset-class_7.cpp)]

Esto significa que no se puede establecer en todos los **param** campos con valores NULL, se puede hacer con `outputColumn` campos.

`SetFieldDirty` se implementa a través de `DoFieldExchange`.

##  <a name="setfieldnull"></a>  CDaoRecordset::SetFieldNull

Llame a esta función miembro para marcar a un miembro de datos de campo del conjunto de registros como Null (específicamente con ningún valor) o como no Null.

```
void SetFieldNull(
    void* pv,
    BOOL bNull = TRUE);
```

### <a name="parameters"></a>Parámetros

*PV*<br/>
Contiene la dirección de un miembro de datos de campo en el conjunto de registros o NULL. Si es NULL, se marcan todos los miembros de datos de campo del conjunto de registros. (C++ NULL no es igual a Null en la terminología de base de datos, lo que significa "no tener ningún valor.")

*bNull*<br/>
Distinto de cero si es miembro de datos del campo se marca como si tuviera ningún valor (Null). En caso contrario, 0 si el miembro de datos de campo se marca como no Null.

### <a name="remarks"></a>Comentarios

`SetFieldNull` se utiliza para campos enlazados en el `DoFieldExchange` mecanismo.

Cuando se agrega un nuevo registro a un conjunto de registros, todos los miembros de datos de campo inicialmente son establecidos en un valor Null y marcados como "sucio" (modificado). Al recuperar un registro de un origen de datos, sus columnas ya tienen valores o son Null. Si no es adecuado para un campo Null, un [CDaoException](../../mfc/reference/cdaoexception-class.md) se produce.

Si usa el mecanismo de almacenamiento en búfer doble, por ejemplo, si lo desea específicamente designar un campo del registro actual que no tiene un valor, llame a `SetFieldNull` con *bNull* establecido en TRUE para marcarlo como Null. Si previamente se marcó un campo Null y ahora desea asignarle un valor, simplemente establezca su nuevo valor. No es necesario que quitar la marca de Null con `SetFieldNull`. Para determinar si el campo puede ser Null, llame a [IsFieldNullable](#isfieldnullable).

Si no utiliza el mecanismo de almacenamiento en búfer doble, a continuación, cambiar el valor del campo no establece automáticamente el campo como modificado y no es Null. Debe establecer específicamente los campos de datos sucios y no Null. La marca contenida en [m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields) controla la comprobación automática de campos.

El mecanismo DFX emplea el uso de PSEUDONULL. Para obtener más información, consulte [CDaoFieldExchange:: M_noperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation).

> [!NOTE]
>  Llame a esta función miembro después de haber llamado [editar](#edit) o [AddNew](#addnew).

El uso de NULL para el primer argumento de la función aplicará solo a la función `outputColumn` campos, no **param** campos `CDaoFieldExchange`. Por ejemplo, la llamada

[!code-cpp[NVC_MFCDatabase#8](../../mfc/codesnippet/cpp/cdaorecordset-class_8.cpp)]

establecerá sólo `outputColumn` campos con NULL; **param** campos no se verán afectados.

##  <a name="setfieldvalue"></a>  CDaoRecordset::SetFieldValue

Llame a esta función miembro para establecer el valor de un campo, según su posición ordinal o cambiando el valor de la cadena.

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
Un puntero a una cadena que contiene el nombre de un campo.

*varValue*<br/>
Una referencia a un [COleVariant](../../mfc/reference/colevariant-class.md) objeto que contiene el valor del contenido del campo.

*nIndex*<br/>
Un entero que representa la posición ordinal del campo en la colección de campos del conjunto de registros (basado en cero).

*lpszValue*<br/>
Un puntero a una cadena que contiene el valor del contenido del campo.

### <a name="remarks"></a>Comentarios

Use `SetFieldValue` y [GetFieldValue](#getfieldvalue) para enlazar campos dinámicamente en tiempo de ejecución en lugar de estáticamente columnas de enlace mediante la [DoFieldExchange](#dofieldexchange) mecanismo.

Tenga en cuenta que si no va a crear un conjunto de registros UNICODE, se debe usar un formulario de `SetFieldValue` que no contiene un `COleVariant` parámetro, o la `COleVariant` objeto se debe declarar explícitamente ANSI. Esto puede hacerse mediante el uso de la [COleVariant::COleVariant](../../mfc/reference/colevariant-class.md#colevariant)**(** *lpszSrc* **,** *vtSrc* **)**  formulario del constructor con *vtSrc* establecido en `VT_BSTRT` (ANSI) o mediante el `COleVariant` función [SetString](../../mfc/reference/colevariant-class.md#setstring)**(** *lpszSrc* **,** *vtSrc* **)** con *vtSrc* establecido en `VT_BSTRT`.

Para obtener información relacionada, vea los temas "Objeto de campo" y "Valor de propiedad" en la Ayuda de DAO.

##  <a name="setfieldvaluenull"></a>  CDaoRecordset::SetFieldValueNull

Llame a esta función miembro para establecer el campo en un valor Null.

```
void SetFieldValueNull(int nIndex);
void SetFieldValueNull(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
El índice del campo en el conjunto de registros para la búsqueda de índice de base cero.

*lpszName*<br/>
El nombre del campo en el conjunto de registros para la búsqueda por nombre.

### <a name="remarks"></a>Comentarios

C++ NULL no es igual a Null, lo que, en la terminología de base de datos, significa "no tener ningún valor."

Para obtener información relacionada, vea los temas "Objeto de campo" y "Valor de propiedad" en la Ayuda de DAO.

##  <a name="setlockingmode"></a>  CDaoRecordset::SetLockingMode

Llame a esta función miembro para establecer el tipo de bloqueo para el conjunto de registros.

```
void SetLockingMode(BOOL bPessimistic);
```

### <a name="parameters"></a>Parámetros

*bPessimistic*<br/>
Una marca que indica el tipo de bloqueo.

### <a name="remarks"></a>Comentarios

Cuando el bloqueo pesimista en vigor, es la página de 2K que contiene el registro que está modificando está bloqueada en cuanto llame a la `Edit` función miembro. La página se desbloquea cuando se llama a la `Update` o `Close` función miembro o cualquiera de las operaciones de mover o encontrar.

Cuando está activado un bloqueo optimista, la página de 2K que contiene el registro se bloquea mientras se está actualizando el registro con el `Update` función miembro.

Si se bloquea una página, ningún otro usuario puede editar los registros en la misma página. Si se llama a `SetLockingMode` y pasar un valor distinto de cero y otro usuario ya ha bloqueado la página, se produce una excepción al llamar a `Edit`. Otros usuarios pueden leer datos de páginas bloqueadas.

Si se llama a `SetLockingMode` llamar con un valor de cero y versiones posteriores `Update` mientras la página está bloqueada por otro usuario, se produce una excepción. Para ver los cambios realizados por otro usuario en el registro (y perder los cambios), llame a la `SetBookmark` función miembro con el valor de marcador del registro actual.

Cuando se trabaja con orígenes de datos ODBC, el modo de bloqueo siempre es optimista.

##  <a name="setparamvalue"></a>  CDaoRecordset::SetParamValue

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
La posición numérica del parámetro en la colección de parámetros de la definición de la consulta.

*var*<br/>
El valor que se va a establecer; vea la sección Comentarios.

*lpszName*<br/>
El nombre del parámetro cuyo valor va a establecer.

### <a name="remarks"></a>Comentarios

El parámetro debe ya ha establecido como parte de la cadena SQL del conjunto de registros. El parámetro puede tener acceso por nombre o por su posición de índice en la colección.

Especifique el valor que se establece como un `COleVariant` objeto. Para obtener información acerca de cómo establecer el valor deseado y escriba su `COleVariant` de objetos, vea la clase [COleVariant](../../mfc/reference/colevariant-class.md). Tenga en cuenta que si no va a crear un conjunto de registros UNICODE, el `COleVariant` objeto se debe declarar explícitamente ANSI. Esto puede hacerse mediante el uso de la [COleVariant::COleVariant](../../mfc/reference/colevariant-class.md#colevariant)**(** *lpszSrc* **,** *vtSrc* **)**  formulario del constructor con *vtSrc* establecido en `VT_BSTRT` (ANSI) o mediante el `COleVariant` función [SetString](../../mfc/reference/colevariant-class.md#setstring)**(** *lpszSrc* **,** *vtSrc* **)** con *vtSrc* establecido en `VT_BSTRT`.

##  <a name="setparamvaluenull"></a>  CDaoRecordset::SetParamValueNull

Llame a esta función miembro para establecer el parámetro en un valor Null.

```
void SetParamValueNull(int nIndex);
void SetParamValueNull(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
El índice del campo en el conjunto de registros para la búsqueda de índice de base cero.

*lpszName*<br/>
El nombre del campo en el conjunto de registros para la búsqueda por nombre.

### <a name="remarks"></a>Comentarios

C++ NULL no es igual a Null, lo que, en la terminología de base de datos, significa "no tener ningún valor."

##  <a name="setpercentposition"></a>  CDaoRecordset:: SetPercentPosition

Llame a esta función miembro para establecer un valor que cambia la ubicación aproximada del registro actual en el objeto de conjunto de registros basándose en un porcentaje de los registros del conjunto de registros.

```
void SetPercentPosition(float fPosition);
```

### <a name="parameters"></a>Parámetros

*fPosition*<br/>
Número comprendido entre 0 y 100.

### <a name="remarks"></a>Comentarios

Cuando se trabaja con un tipo dinámico o un conjunto de registros de tipo de instantánea, en primer lugar rellenar el conjunto de registros moviendo al último registro antes de llamar a `SetPercentPosition`. Si se llama a `SetPercentPosition` antes de rellenar completamente el conjunto de registros, la cantidad de movimiento es relativo al número de registros de acceso tal y como indica el valor de [GetRecordCount](#getrecordcount). Puede mover al último registro mediante una llamada a `MoveLast`.

Una vez que llamamos `SetPercentPosition`, el registro en la posición aproximado correspondiente a ese valor se convierte en actual.

> [!NOTE]
>  Una llamada a `SetPercentPosition` para mover el registro actual a un registro específico en un conjunto de registros no se recomienda. Llame a la [SetBookmark](#setbookmark) función miembro en su lugar.

Para obtener información relacionada, vea el tema "PercentPosition Property" en la Ayuda de DAO.

##  <a name="update"></a>  CDaoRecordset::Update

Llame a esta función miembro después de llamar a la `AddNew` o `Edit` función miembro.

```
virtual void Update();
```

### <a name="remarks"></a>Comentarios

Esta llamada es necesario para completar la `AddNew` o `Edit` operación.

Ambos `AddNew` y `Edit` preparar un búfer de edición en el que se colocan los datos se ha agregado o editados para guardar datos en el origen de datos. `Update` guarda los datos. Se actualizan solo los campos marcados o detecta tal como se puede cambiar.

Si el origen de datos admite transacciones, se puede hacer el `Update` llamar (y su correspondiente `AddNew` o `Edit` llamar) forma parte de una transacción.

> [!CAUTION]
> Si se llama a `Update` sin primero una llamada a `AddNew` o `Edit`, `Update` produce una `CDaoException`. Si se llama a `AddNew` o `Edit`, debe llamar a `Update` antes de llamar a [MoveNext](#movenext) o cerrar la conexión de origen de datos o el conjunto de registros. En caso contrario, los cambios se perderán sin notificación.

Cuando el objeto recordset forma pesimista está bloqueado en un entorno multiusuario, el registro permanece bloqueado desde el momento `Edit` se usa hasta que finalice la actualización. Si el conjunto de registros está bloqueado de forma optimista, el registro se bloquea y se compara con el registro justo antes de se actualiza en la base de datos. Si el registro ha cambiado desde que llamó a `Edit`, el `Update` se produce un error de operación y MFC produce una excepción. Puede cambiar el modo de bloqueo con `SetLockingMode`.

> [!NOTE]
> Bloqueo optimista siempre se usa en formatos de base de datos externo, como ODBC y ISAM instalable.

Para obtener información relacionada, vea los temas "Método AddNew", "Método CancelUpdate", "Método Delete", "LastModified Property", "Método de actualización" y "Propiedad EditMode" en la Ayuda de DAO.

## <a name="see-also"></a>Vea también

[CObject (clase)](../../mfc/reference/cobject-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CDaoTableDef (clase)](../../mfc/reference/cdaotabledef-class.md)<br/>
[CDaoWorkspace (clase)](../../mfc/reference/cdaoworkspace-class.md)<br/>
[CDaoDatabase (clase)](../../mfc/reference/cdaodatabase-class.md)<br/>
[CDaoQueryDef (clase)](../../mfc/reference/cdaoquerydef-class.md)<br/>
