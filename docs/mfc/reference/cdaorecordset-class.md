---
title: CDaoRecordset (clase) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 603cd1658af417dfbb7f2d8aa8022275e866a706
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33378909"
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
|[CDaoRecordset:: AddNew](#addnew)|Se prepara para agregar un nuevo registro. Llame a [actualización](#update) para completar la adición.|  
|[CDaoRecordset::CanAppend](#canappend)|Devuelve un valor distinto de cero si se pueden agregar nuevos registros en el conjunto de registros a través de la [AddNew](#addnew) función miembro.|  
|[CDaoRecordset:: CanBookmark](#canbookmark)|Devuelve un valor distinto de cero si el conjunto de registros admite marcadores.|  
|[CDaoRecordset::CancelUpdate](#cancelupdate)|Cancela cualquier actualización pendiente debido a un [editar](#edit) o [AddNew](#addnew) operación.|  
|[CDaoRecordset::CanRestart](#canrestart)|Devuelve un valor distinto de cero si [Requery](#requery) puede llamarse para volver a ejecutar la consulta del conjunto de registros.|  
|[CDaoRecordset::CanScroll](#canscroll)|Devuelve un valor distinto de cero si puede desplazarse por los registros.|  
|[CDaoRecordset::CanTransact](#cantransact)|Devuelve un valor distinto de cero si el origen de datos admite transacciones.|  
|[CDaoRecordset::CanUpdate](#canupdate)|Devuelve un valor distinto de cero si se puede actualizar el conjunto de registros (puede agregar, actualizar o eliminar registros).|  
|[CDaoRecordset::Close](#close)|Cierra el conjunto de registros.|  
|[CDaoRecordset::Delete](#delete)|Elimina el registro actual del conjunto de registros. Explícitamente, debe desplazarse a otro registro después de la eliminación.|  
|[CDaoRecordset](#dofieldexchange)|Se llama para intercambiar datos (en ambas direcciones) entre los miembros de datos de campo del conjunto de registros y el registro correspondiente en el origen de datos. Implementa DAO campo intercambio registros (DFX).|  
|[CDaoRecordset:: Edit](#edit)|Se prepara para que los cambios en el registro actual. Llame a **actualización** para completar la edición.|  
|[CDaoRecordset:: FillCache](#fillcache)|Llena todo o parte de una caché local para un objeto de conjunto de registros que contiene los datos de un origen de datos ODBC.|  
|[CDaoRecordset::Find](#find)|Busca la primera, siguiente, anterior, o última ubicación de una cadena concreta en un conjunto de registros de tipo dinámico que satisface los criterios especificados y hace que el registro en el registro actual.|  
|[CDaoRecordset::FindFirst](#findfirst)|Busca el primer registro de un tipo de conjunto de registros dinámicos o un conjunto de registros de tipo snapshot que satisface los criterios especificados y hace que el registro en el registro actual.|  
|[CDaoRecordset::FindLast](#findlast)|Localiza el último registro en un tipo de conjunto de registros dinámicos o un conjunto de registros de tipo snapshot que satisface los criterios especificados y hace que el registro en el registro actual.|  
|[CDaoRecordset::FindNext](#findnext)|Localiza el registro siguiente en un tipo de conjunto de registros dinámicos o un conjunto de registros de tipo snapshot que satisface los criterios especificados y hace que el registro en el registro actual.|  
|[CDaoRecordset::FindPrev](#findprev)|Localiza el registro anterior de un tipo de conjunto de registros dinámicos o un conjunto de registros de tipo snapshot que satisface los criterios especificados y hace que el registro en el registro actual.|  
|[CDaoRecordset:: GetAbsolutePosition](#getabsoluteposition)|Devuelve el número de registro del registro actual del objeto de conjunto de registros.|  
|[CDaoRecordset:: GetBookmark](#getbookmark)|Devuelve un valor que representa el marcador de un registro.|  
|[CDaoRecordset::GetCacheSize](#getcachesize)|Devuelve un valor que especifica el número de registros en un conjunto de registros de tipo dinámico que contiene datos que se va a almacenar en caché localmente desde un origen de datos ODBC.|  
|[CDaoRecordset::GetCacheStart](#getcachestart)|Devuelve un valor que especifica el marcador del primer registro en el conjunto de registros en la memoria caché.|  
|[CDaoRecordset::GetCurrentIndex](#getcurrentindex)|Devuelve un `CString` que contiene el nombre del índice más recientemente usa un tipo de tabla indizada, `CDaoRecordset`.|  
|[CDaoRecordset::GetDateCreated](#getdatecreated)|Devuelve la fecha y hora de la tabla base subyacente un `CDaoRecordset` se creó el objeto|  
|[CDaoRecordset::GetDateLastUpdated](#getdatelastupdated)|Devuelve la fecha y hora del cambio más reciente realizado en el diseño de una tabla base subyacente un `CDaoRecordset` objeto.|  
|[CDaoRecordset::GetDefaultDBName](#getdefaultdbname)|Devuelve el nombre del origen de datos predeterminado.|  
|[CDaoRecordset::GetDefaultSQL](#getdefaultsql)|Se llama para obtener la cadena SQL predeterminada para ejecutar.|  
|[CDaoRecordset::GetEditMode](#geteditmode)|Devuelve un valor que indica el estado de edición para el registro actual.|  
|[CDaoRecordset::GetFieldCount](#getfieldcount)|Devuelve un valor que representa el número de campos de un conjunto de registros.|  
|[CDaoRecordset::GetFieldInfo](#getfieldinfo)|Devuelve determinados tipos de información sobre los campos del conjunto de registros.|  
|[CDaoRecordset:: GetFieldValue](#getfieldvalue)|Devuelve el valor de un campo en un conjunto de registros.|  
|[CDaoRecordset::GetIndexCount](#getindexcount)|Recupera el número de índices en una tabla que subyace a un conjunto de registros.|  
|[CDaoRecordset::GetIndexInfo](#getindexinfo)|Devuelve diversos tipos de información acerca de los índices.|  
|[CDaoRecordset::GetLastModifiedBookmark](#getlastmodifiedbookmark)|Se utiliza para determinar el último agrega o actualiza el registro.|  
|[CDaoRecordset::GetLockingMode](#getlockingmode)|Devuelve un valor que indica el tipo de bloqueo que esté en vigor durante la edición.|  
|[CDaoRecordset::GetName](#getname)|Devuelve un `CString` que contiene el nombre del conjunto de registros.|  
|[CDaoRecordset::GetParamValue](#getparamvalue)|Recupera el valor actual del parámetro especificado almacenado en el objeto DAOParameter subyacente.|  
|[CDaoRecordset:: GetPercentPosition](#getpercentposition)|Devuelve la posición del registro actual como un porcentaje del número total de registros.|  
|[CDaoRecordset::GetRecordCount](#getrecordcount)|Devuelve el número de registros que se obtiene acceso en un objeto de conjunto de registros.|  
|[CDaoRecordset::GetSQL](#getsql)|Obtiene la cadena SQL que se utiliza para seleccionar los registros para el conjunto de registros.|  
|[CDaoRecordset::GetType](#gettype)|Se llama para determinar el tipo de un conjunto de registros: tipo de tabla, tipo de conjunto de registros dinámicos o tipo de instantánea.|  
|[CDaoRecordset::GetValidationRule](#getvalidationrule)|Devuelve un `CString` que contiene el valor que valida los datos de medida que se escribe en un campo.|  
|[CDaoRecordset::GetValidationText](#getvalidationtext)|Recupera el texto que se muestra cuando no se cumple una regla de validación.|  
|[CDaoRecordset::IsBOF](#isbof)|Devuelve un valor distinto de cero si el conjunto de registros se ha colocado antes del primer registro. No hay ningún registro actual.|  
|[CDaoRecordset::IsDeleted](#isdeleted)|Devuelve un valor distinto de cero si el conjunto de registros está situado en un registro eliminado.|  
|[CDaoRecordset::IsEOF](#iseof)|Devuelve un valor distinto de cero si el conjunto de registros se ha colocado después del último registro. No hay ningún registro actual.|  
|[CDaoRecordset::IsFieldDirty](#isfielddirty)|Devuelve un valor distinto de cero si se ha cambiado el campo especificado en el registro actual.|  
|[CDaoRecordset::IsFieldNull](#isfieldnull)|Devuelve un valor distinto de cero si el campo especificado en el registro actual es Null (no tener ningún valor).|  
|[CDaoRecordset::IsFieldNullable](#isfieldnullable)|Devuelve un valor distinto de cero si el campo especificado en el registro actual se puede establecer en Null (no tener ningún valor).|  
|[CDaoRecordset::IsOpen](#isopen)|Devuelve un valor distinto de cero si [abiertos](#open) se ha llamado anteriormente.|  
|[CDaoRecordset:: Move](#move)|Coloca el conjunto de registros a un número especificado de entradas del registro actual en cualquier dirección.|  
|[CDaoRecordset::MoveFirst](#movefirst)|El registro actual se coloca en el primer registro del conjunto de registros.|  
|[CDaoRecordset::MoveLast](#movelast)|Coloca el registro actual en el último registro en el conjunto de registros.|  
|[CDaoRecordset::MoveNext](#movenext)|El registro actual se coloca en el registro siguiente en el conjunto de registros.|  
|[CDaoRecordset::MovePrev](#moveprev)|El registro actual se coloca en el registro anterior en el conjunto de registros.|  
|[CDaoRecordset:: Open](#open)|Crea un nuevo conjunto de registros de una tabla, un conjunto de registros dinámicos o una instantánea.|  
|[CDaoRecordset::Requery](#requery)|Ejecuta la consulta del conjunto de registros para actualizar los registros seleccionados.|  
|[CDaoRecordset::Seek](#seek)|Localiza el registro en un objeto de conjunto de registros de tipo tabla indizada que satisface los criterios especificados para el índice actual y hace que el registro en el registro actual.|  
|[CDaoRecordset:: SetAbsolutePosition](#setabsoluteposition)|Establece el número de registro del registro actual del objeto de conjunto de registros.|  
|[CDaoRecordset:: SetBookmark](#setbookmark)|El conjunto de registros se coloca en un registro que contiene el marcador especificado.|  
|[CDaoRecordset:: SetCacheSize](#setcachesize)|Establece un valor que especifica el número de registros en un conjunto de registros de tipo dinámico que contiene datos que se va a almacenar en caché localmente desde un origen de datos ODBC.|  
|[CDaoRecordset:: SetCacheStart](#setcachestart)|Establece un valor que especifica el marcador del primer registro en el conjunto de registros en la memoria caché.|  
|[CDaoRecordset:: SetCurrentIndex](#setcurrentindex)|Se llama para establecer un índice en un conjunto de registros de tipo de tabla.|  
|[CDaoRecordset:: SetFieldDirty](#setfielddirty)|Marca el campo especificado en el registro actual como modificada.|  
|[CDaoRecordset::SetFieldNull](#setfieldnull)|Establece el valor del campo especificado en el registro actual en Null (no tener ningún valor).|  
|[CDaoRecordset::SetFieldValue](#setfieldvalue)|Establece el valor de un campo en un conjunto de registros.|  
|[CDaoRecordset::SetFieldValueNull](#setfieldvaluenull)|Establece el valor de un campo en un conjunto de registros en Null. (no tener ningún valor).|  
|[CDaoRecordset::SetLockingMode](#setlockingmode)|Establece un valor que indica el tipo de bloqueo para poner en efecto durante la edición.|  
|[CDaoRecordset::SetParamValue](#setparamvalue)|Establece el valor actual del parámetro especificado almacenado en el objeto subyacente de DAOParameter|  
|[CDaoRecordset::SetParamValueNull](#setparamvaluenull)|Establece el valor actual del parámetro especificado en Null (no tener ningún valor).|  
|[CDaoRecordset:: SetPercentPosition](#setpercentposition)|Establece la posición del registro actual en una ubicación correspondiente a un porcentaje del número total de registros en un conjunto de registros.|  
|[CDaoRecordset::Update](#update)|Completa una `AddNew` o **editar** operación guardando los datos nuevos o modificados del origen de datos.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDaoRecordset:: M_bcheckcachefordirtyfields](#m_bcheckcachefordirtyfields)|Contiene una marca que indica si los campos se marcan automáticamente como modificada.|  
|[CDaoRecordset::m_nFields](#m_nfields)|Contiene el número de miembros de datos de campo en la clase de conjunto de registros y el número de columnas seleccionadas por el conjunto de registros desde el origen de datos.|  
|[CDaoRecordset::m_nParams](#m_nparams)|Contiene el número de miembros de datos de parámetro en la clase de conjunto de registros: el número de parámetros pasados con la consulta del conjunto de registros|  
|[CDaoRecordset::m_pDAORecordset](#m_pdaorecordset)|Un puntero a la interfaz DAO subyacente al objeto de conjunto de registros.|  
|[CDaoRecordset::m_pDatabase](#m_pdatabase)|Base de datos de origen para este conjunto de resultados. Contiene un puntero a un [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) objeto.|  
|[CDaoRecordset:: M_strfilter](#m_strfilter)|Contiene una cadena utilizada para construir una instancia de SQL **donde** instrucción.|  
|[CDaoRecordset::m_strSort](#m_strsort)|Contiene una cadena utilizada para construir una instancia de SQL **ORDER BY** instrucción.|  
  
## <a name="remarks"></a>Comentarios  
 Conocida como "conjuntos de registros," `CDaoRecordset` objetos están disponibles en las tres formas siguientes:  
  
-   Conjuntos de registros de tipo de tabla representan una tabla base que puede usar para examinar, agregar, cambiar o eliminar registros de una tabla de base de datos único.  
  
-   Conjuntos de registros de tipo de conjunto de registros dinámicos son el resultado de una consulta que puede tener registros actualizables. Estos conjuntos de registros son un conjunto de registros que puede usar para examinar, agregar, cambiar o eliminar registros de una tabla de base de datos subyacente o tablas. Conjuntos de registros de tipo Dynaset pueden contener campos de una o más tablas en una base de datos.  
  
-   Conjuntos de registros de tipo de instantánea son una copia estática de un conjunto de registros que puede usar para buscar datos o generar informes. Estos conjuntos de registros pueden contener campos de una o más tablas en una base de datos, pero no se puede actualizar.  
  
 Cada forma de conjunto de registros representa un conjunto de registros que se fija en el momento en que se abre el conjunto de registros. Cuando se desplaza a un registro en un conjunto de registros de tipo de tabla o un conjunto de registros de tipo dynaset, refleja los cambios realizados en el registro cuando se abre el conjunto de registros, por otros usuarios o por otros conjuntos de registros en la aplicación. (No se puede actualizar un conjunto de registros de tipo de instantánea). Puede usar `CDaoRecordset` directamente o derivar una clase de conjunto de registros específicos de la aplicación de `CDaoRecordset`. A continuación, puede:  
  
-   Desplazarse por los registros.  
  
-   Establecer un índice y buscar rápidamente los registros mediante [búsqueda](#seek) (sólo para conjuntos de registros de tipo de tabla).  
  
-   Buscar registros basándose en una comparación de cadenas: "<","\<=", "=", "> =", o ">" (tipo de conjunto de registros dinámicos y conjuntos de registros de tipo de instantánea).  
  
-   Actualizar los registros y especificar un modo de bloqueo (excepto los conjuntos de registros de tipo de instantánea).  
  
-   Filtrar el conjunto de registros para restringir qué registros selecciona de los que están disponibles en el origen de datos.  
  
-   Ordenar el conjunto de registros.  
  
-   Parametrice el conjunto de registros para personalizar su selección con información no conocida hasta el tiempo de ejecución.  
  
 Clase `CDaoRecordset` proporciona una interfaz similar a la de la clase `CRecordset`. La diferencia principal es esa clase `CDaoRecordset` tiene acceso a datos a través de un objeto de acceso de datos (DAO) en función de OLE. Clase `CRecordset` accede a DBMS a través de Open Database Connectivity (ODBC) y un controlador ODBC para ese DBMS.  
  
> [!NOTE]
>  Las clases de base de datos DAO son distintas de las clases de base de datos MFC basadas en Open Database Connectivity (ODBC). Todos los nombres de clase de base de datos DAO tienen el prefijo "CDao". Todavía podrá acceso a orígenes de datos ODBC con las clases DAO; por lo general, las clases DAO ofrecen capacidades de superior porque son específicas para el motor de base de datos de Microsoft Jet.  
  
 Puede usar `CDaoRecordset` directamente o derivar una clase de `CDaoRecordset`. Para utilizar una clase de conjunto de registros en cualquier caso, abrir una base de datos y crear un objeto de conjunto de registros, el constructor se pasa un puntero a su `CDaoDatabase` objeto. También se puede construir un `CDaoRecordset` objeto y deje que MFC crear un archivo temporal `CDaoDatabase` objeto automáticamente. A continuación, llame el conjunto de registros [abiertos](#open) función de miembro, que especifica si el objeto es un conjunto de registros de tipo de tabla, un conjunto de registros de tipo dinámico o un conjunto de registros de tipo de instantánea. Al llamar a **abiertos** selecciona datos de la base de datos y recupera el primer registro.  
  
 Usar a miembros de datos y funciones de miembro del objeto para desplazarse por los registros y operar con ellas. Las operaciones disponibles dependen de si el objeto es un conjunto de registros de tipo de tabla, un conjunto de registros de tipo dinámico o un conjunto de registros de tipo de instantánea y, si es actualizable o de solo lectura, esto depende de la capacidad de la base de datos o Open Database Connectivity (ODBC) origen de datos. Para actualizar los registros que se han cambiado o agregado desde el **abiertos** llamada, llamar al objeto [Requery](#requery) función miembro. Llamar al objeto **cerrar** miembro de función y destruir el objeto cuando haya terminado con él.  
  
 `CDaoRecordset` intercambio de campos de registros DAO (DFX) se utiliza para permitir la lectura y actualización de los campos de registro a través de los miembros de C++ con seguridad de tipos de su `CDaoRecordset` o `CDaoRecordset`-clase derivada. También puede implementar el enlace dinámico de columnas en una base de datos sin usar el mecanismo DFX utilizando [GetFieldValue](#getfieldvalue) y [SetFieldValue](#setfieldvalue).  
  
 Para obtener información relacionada, vea el tema "Recordset (objeto)" en la Ayuda de DAO.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CDaoRecordset`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdao.h  
  
##  <a name="addnew"></a>  CDaoRecordset:: AddNew  
 Llame a esta función miembro para agregar un nuevo registro a un conjunto de registros de tipo de tabla o tipo de conjunto de registros dinámicos.  
  
```  
virtual void AddNew();
```  
  
### <a name="remarks"></a>Comentarios  
 Los campos del registro son inicialmente Null. (En la terminología de base de datos, Null significa "no having ningún valor" y no es igual a **NULL** en C++.) Para completar la operación, se debe llamar a la [actualización](#update) función miembro. **Actualización** guarda los cambios en el origen de datos.  
  
> [!CAUTION]
>  Si edita un registro y, a continuación, desplácese a otro registro sin llamar a **actualización**, los cambios se pierden sin previo aviso.  
  
 Si agrega un registro a un conjunto de registros de tipo dinámico mediante una llamada a [AddNew](#addnew), el registro es visible en el conjunto de registros y se incluye en la tabla subyacente donde estará visible para cualquier nuevo `CDaoRecordset` objetos.  
  
 La posición del nuevo registro depende del tipo de conjunto de registros:  
  
-   En un tipo de conjunto de registros dinámicos no se garantiza el conjunto de registros, donde se insertó el nuevo registro. Este comportamiento en el que se ha cambiado con Microsoft Jet 3.0 por motivos de rendimiento y la simultaneidad. Si su objetivo es hacer el registro recién agregado en el registro actual, obtener el marcador del último registro modificado y mover a ese marcador:  
  
 [!code-cpp[NVC_MFCDatabase#1](../../mfc/codesnippet/cpp/cdaorecordset-class_1.cpp)]  
  
-   En un conjunto de registros de tipo de tabla para la que se ha especificado un índice, los registros se devuelven en su posición correcta en el criterio de ordenación. Si no se ha especificado ningún índice, los nuevos registros se devuelven al final del conjunto de registros.  
  
 El registro que era el actual antes de utilizar `AddNew` sigue estando activo. Si desea que el nuevo registro actual y el conjunto de registros admite marcadores, llamada [SetBookmark](#setbookmark) en el marcador identificado por el valor de propiedad LastModified del objeto de conjunto de registros DAO subyacente. Esto es útil para determinar el valor de contador (incremento automático) los campos en un registro agregado. Para obtener más información, consulte [GetLastModifiedBookmark](#getlastmodifiedbookmark).  
  
 Si la base de datos admite transacciones, puede realizar su `AddNew` llame a parte de una transacción. Para obtener más información acerca de las transacciones, vea la clase [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md). Tenga en cuenta que debe llamar a [CDaoWorkspace::BeginTrans](../../mfc/reference/cdaoworkspace-class.md#begintrans) antes de llamar a `AddNew`.  
  
 No es válido para llamar a `AddNew` para un conjunto de registros cuyo [abiertos](#open) función miembro no se ha llamado. A `CDaoException` se produce si se llama a `AddNew` para un conjunto de registros que no se puede anexar. Puede determinar si el conjunto de registros es actualizable mediante una llamada a [CanAppend](#canappend).  
  
 Las marcas de framework cambiar los miembros de datos de campo para asegurarse de que se escribirán en el registro en el origen de datos mediante el mecanismo de intercambio (DFX) de campos de registros DAO. Cambiar el valor de un campo normalmente establece el campo desfasadas automáticamente, por lo que rara vez deberá llamar a [SetFieldDirty](#setfielddirty) usted mismo, pero a veces, conviene asegurarse de que las columnas se explícitamente actualiza o inserta independientemente de qué valor está en el miembro de datos de campo. El mecanismo DFX también emplea el uso de **PSEUDO NULL**. Para obtener más información, consulte [CDaoFieldExchange:: M_noperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation).  
  
 Si no se utiliza el mecanismo de almacenamiento en búfer doble, a continuación, cambiar el valor del campo no establece automáticamente el campo como modificados. En este caso, será necesario establecer explícitamente el campo de datos sucios. La marca contenida en [m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields) controla la comprobación automática de campos.  
  
> [!NOTE]
>  Si los registros son doble búfer (es decir, la comprobación automática de campos está habilitada), una llamada a `CancelUpdate` restaurará las variables de miembro para los valores que tenían antes de `AddNew` o **editar** se llamó.  
  
 Para obtener información relacionada, vea los temas "AddNew (método)", "Método CancelUpdate", "Propiedad LastModified" y "Propiedad EditMode" en la Ayuda de DAO.  
  
##  <a name="canappend"></a>  CDaoRecordset::CanAppend  
 Llame a esta función miembro para determinar si el conjunto de registros abierto anteriormente le permite agregar nuevos registros mediante una llamada a la [AddNew](#addnew) función miembro.  
  
```  
BOOL CanAppend() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el conjunto de registros permite agregar nuevos registros; en caso contrario es 0. `CanAppend` devolverá 0 si se abre el conjunto de registros como de solo lectura.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener información relacionada, vea el tema "Método Append" en la Ayuda de DAO.  
  
##  <a name="canbookmark"></a>  CDaoRecordset:: CanBookmark  
 Llame a esta función miembro para determinar si el conjunto de registros abierto anteriormente le permite marcar individualmente los registros mediante marcadores.  
  
```  
BOOL CanBookmark();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el conjunto de registros admite marcadores, de lo contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Si usa conjuntos de registros que se basa completamente en tablas del motor de base de datos de Microsoft Jet, se pueden utilizar marcadores excepto en conjuntos de registros de tipo instantánea marcados como conjuntos de registros de desplazamiento solo hacia delante. Pueden que otros productos de base de datos (orígenes de datos ODBC externos) no admite marcadores.  
  
 Para obtener información relacionada, vea el tema "Propiedad admite marcadores" en la Ayuda de DAO.  
  
##  <a name="cancelupdate"></a>  CDaoRecordset::CancelUpdate  
 El `CancelUpdate` función miembro cancela cualquier actualización pendiente debido a un [editar](#edit) o [AddNew](#addnew) operación.  
  
```  
virtual void CancelUpdate();
```  
  
### <a name="remarks"></a>Comentarios  
 Por ejemplo, si una aplicación llama a la **editar** o `AddNew` función miembro y no se ha llamado [actualización](#update), `CancelUpdate` cancela los cambios efectuados después **editar**o `AddNew` se llamó.  
  
> [!NOTE]
>  Si los registros son doble búfer (es decir, la comprobación automática de campos está habilitada), una llamada a `CancelUpdate` restaurará las variables de miembro para los valores que tenían antes de `AddNew` o **editar** se llamó.  
  
 Si no hay ningún **editar** o `AddNew` operación pendiente, `CancelUpdate` hace MFC producir una excepción. Llame a la [GetEditMode](#geteditmode) función de miembro para determinar si hay una operación pendiente que se puede cancelar.  
  
 Para obtener información relacionada, vea el tema "Método CancelUpdate" en la Ayuda de DAO.  
  
##  <a name="canrestart"></a>  CDaoRecordset::CanRestart  
 Llame a esta función miembro para determinar si el conjunto de registros permite reiniciar su consulta (para actualizar sus registros) mediante una llamada a la **Requery** función miembro.  
  
```  
BOOL CanRestart();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si **Requery** puede llamarse para ejecutar la consulta de nuevo, en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Conjuntos de registros de tipo de tabla no admiten **Requery**.  
  
 Si **Requery** no es compatible, llame a [cerrar](#close) , a continuación, [abiertos](#open) para actualizar los datos. Puede llamar a **Requery** actualizar un objeto de conjunto de registros subyacente de la consulta de parámetros después de que se cambiaron los valores de parámetro.  
  
 Para obtener información relacionada, vea el tema "Propiedad reiniciables" en la Ayuda de DAO.  
  
##  <a name="canscroll"></a>  CDaoRecordset::CanScroll  
 Llame a esta función miembro para determinar si el conjunto de registros permite el desplazamiento.  
  
```  
BOOL CanScroll() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si puede desplazarse por los registros, de lo contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Si se llama a [abiertos](#open) con **dbForwardOnly**, el conjunto de registros solo se puede desplazar hacia delante.  
  
 Para obtener información relacionada, vea el tema "Colocar el puntero de registro actual con DAO" en la Ayuda de DAO.  
  
##  <a name="cantransact"></a>  CDaoRecordset::CanTransact  
 Llame a esta función miembro para determinar si el conjunto de registros permite que las transacciones.  
  
```  
BOOL CanTransact();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el origen de datos subyacente admite transacciones, de lo contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener información relacionada, vea el tema "Propiedad de transacciones" en la Ayuda de DAO.  
  
##  <a name="canupdate"></a>  CDaoRecordset::CanUpdate  
 Llame a esta función miembro para determinar si se puede actualizar el conjunto de registros.  
  
```  
BOOL CanUpdate() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si se puede actualizar el conjunto de registros (agregar, actualizar y eliminar registros), en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Un conjunto de registros puede ser de solo lectura si el origen de datos subyacente es de solo lectura o si especifica **dbReadOnly** para `nOptions` cuando llama a [abiertos](#open) para el conjunto de registros.  
  
 Para obtener información relacionada, vea los temas "AddNew (método)", "Editar método", "Método Delete", "Método de actualización" y "Propiedad actualizable" en la Ayuda de DAO.  
  
##  <a name="cdaorecordset"></a>  CDaoRecordset::CDaoRecordset  
 Construye un objeto `CDaoRecordset`.  
  
```  
CDaoRecordset(CDaoDatabase* pDatabase = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `pDatabase`  
 Contiene un puntero a un [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) objeto o el valor **NULL**. Si no **NULL** y `CDaoDatabase` del objeto **abrir** función miembro no se ha llamado para conectarse al origen de datos, el conjunto de registros intenta abrir automáticamente durante su propio [abrir ](#open) llamar. Si se pasa **NULL**, `CDaoDatabase` objeto se construye y se conecta automáticamente con la información de origen de datos que especificó si deriva de la clase de conjunto de registros de `CDaoRecordset`.  
  
### <a name="remarks"></a>Comentarios  
 Puede usar `CDaoRecordset` directamente o derivar una clase específica de la aplicación de `CDaoRecordset`. Puede utilizar ClassWizard para derivar las clases de conjunto de registros.  
  
> [!NOTE]
>  Si deriva un `CDaoRecordset` de la clase, la derivada clase debe proporcionar su propio constructor. En el constructor de la clase derivada, llame al constructor `CDaoRecordset::CDaoRecordset`, pasando los parámetros adecuados junto a él.  
  
 Pasar **NULL** a su constructor de conjunto de registros para tener un `CDaoDatabase` objeto construido y conecte automáticamente para usted. Se trata de un acceso directo útil que no es necesario crear y conectar un `CDaoDatabase` objeto antes de construir el conjunto de registros. Si el `CDaoDatabase` objeto no está abierto, un [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md) objeto también se creará para usted que usa el área de trabajo de forma predeterminada. Para obtener más información, consulte [CDaoDatabase::CDaoDatabase](../../mfc/reference/cdaodatabase-class.md#cdaodatabase).  
  
##  <a name="close"></a>  CDaoRecordset::Close  
 Cerrar un `CDaoRecordset` objeto quita de la colección de conjuntos de registros abiertos en la base de datos asociada.  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>Comentarios  
 Porque **cerrar** no destruye el `CDaoRecordset` objeto, puede volver a usar el objeto mediante una llamada a **abiertos** en el mismo origen de datos o un origen de datos diferente.  
  
 Todas las pendientes [AddNew](#addnew) o [editar](#edit) instrucciones se cancelan y se revierten todas las transacciones pendientes. Si desea conservar las adiciones o modificaciones pendientes, llame a [actualización](#update) antes de llamar a **cerrar** para cada conjunto de registros.  
  
 Puede llamar a **abiertos** nuevo después de llamar a **cerrar**. Esto le permite volver a usar el objeto de conjunto de registros. Una alternativa mejor es llamar a [Requery](#requery), si es posible.  
  
 Para obtener información relacionada, vea el tema "Close (método)" en la Ayuda de DAO.  
  
##  <a name="delete"></a>  CDaoRecordset::Delete  
 Llame a esta función miembro para eliminar el registro actual en un objeto de conjunto de registros abierto de tipo dynaset o tipo de tabla.  
  
```  
virtual void Delete();
```  
  
### <a name="remarks"></a>Comentarios  
 Después de una eliminación se realiza correctamente, se establecen los miembros de datos de campo del conjunto de registros en un valor Null, y debe llamar explícitamente a una de las funciones de miembro de navegación de conjunto de registros ( [mover](#move), [Seek](#seek), [ SetBookmark](#setbookmark), y así sucesivamente) con el fin de abandonar el registro eliminado. Cuando se eliminan registros de un conjunto de registros, debe haber un registro actual en el conjunto de registros antes de llamar a **eliminar**; en caso contrario, MFC inicia una excepción.  
  
 **Eliminar** quita el registro actual y lo convierte en inaccesible. Aunque no se puede editar o utilizar el registro eliminado, sigue estando activo. Cuando se mueva a otro registro, sin embargo, no puede realizar el registro eliminado actual nuevo.  
  
> [!CAUTION]
>  El conjunto de registros debe ser actualizable y debe haber un registro válido actual en el conjunto de registros cuando se llama a **eliminar**. Por ejemplo, si elimina un registro pero se desplaza a un nuevo registro antes de llamar a **eliminar** nuevo, **eliminar** produce una [CDaoException](../../mfc/reference/cdaoexception-class.md).  
  
 Puede restaurar un registro si se utilizan transacciones y se llama el [CDaoWorkspace::Rollback](../../mfc/reference/cdaoworkspace-class.md#rollback) función miembro. Si la tabla base es la tabla principal en cascada Eliminar relación, eliminando el registro actual, también puede eliminar uno o más registros de una tabla externa. Para obtener más información, consulte la definición "en cascada" eliminar en la Ayuda de DAO.  
  
 A diferencia de `AddNew` y **editar**, una llamada a **eliminar** no va seguida de una llamada a **actualización**.  
  
 Para obtener información relacionada, vea los temas "AddNew (método)", "Editar método", "Método Delete", "Método de actualización" y "Propiedad actualizable" en la Ayuda de DAO.  
  
##  <a name="dofieldexchange"></a>  CDaoRecordset  
 El marco de trabajo llama a esta función miembro para automáticamente intercambiar datos entre los miembros de datos de campo del objeto de conjunto de registros y las columnas correspondientes del registro actual en el origen de datos.  
  
```  
virtual void DoFieldExchange(CDaoFieldExchange* pFX);
```  
  
### <a name="parameters"></a>Parámetros  
 `pFX`  
 Contiene un puntero a un `CDaoFieldExchange` objeto. El marco de trabajo ya habrá configurado este objeto para especificar un contexto para la operación de intercambio de campos.  
  
### <a name="remarks"></a>Comentarios  
 También enlaza a los miembros de datos de parámetro, si los hay, para los marcadores de posición de parámetro en la cadena de la instrucción SQL para la selección del conjunto de registros. El intercambio de datos de campo, denominado intercambio de campos de registros DAO (DFX), funciona en ambas direcciones: desde miembros de datos de campo del objeto de conjunto de registros a los campos del registro en el origen de datos y del registro en el origen de datos para el objeto de conjunto de registros. Si va a enlazar columnas dinámicamente, no se debe implementar `DoFieldExchange`.  
  
 La única acción que normalmente debe seguir para implementar `DoFieldExchange` para el conjunto de registros derivada clase consiste en crear la clase con ClassWizard y especificar los nombres y tipos de datos de los miembros de datos de campo. También puede agregar código a lo que escribe ClassWizard especificar a los miembros de datos de parámetro. Si todos los campos que se van a enlazarse dinámicamente, esta función estará inactiva a menos que especifique a los miembros de datos de parámetro.  
  
 Cuando se declara la clase derivada de conjunto de registros con ClassWizard, el asistente escribe una invalidación de `DoFieldExchange` para usted, que es similar al siguiente:  
  
 [!code-cpp[NVC_MFCDatabase#2](../../mfc/codesnippet/cpp/cdaorecordset-class_2.cpp)]  
  
##  <a name="edit"></a>  CDaoRecordset:: Edit  
 Llame a esta función miembro para permitir cambios en el registro actual.  
  
```  
virtual void Edit();
```  
  
### <a name="remarks"></a>Comentarios  
 Una vez que se llama a la **editar** función de miembro, los cambios realizados en los campos del registro actual se copian en el búfer de copia. Después de realizar los cambios deseados en el registro, llame a **actualización** para guardar los cambios. **Editar** guarda los valores de los miembros de datos del conjunto de registros. Si se llama a **editar**, realizar cambios, a continuación, llame a **editar** nuevo, los valores del registro se restauran a su estado original antes de la primera **editar** llamar.  
  
> [!CAUTION]
>  Si edita un registro y, a continuación, realizar cualquier operación que se mueve a otro registro sin antes de llamar a **actualización**, los cambios se pierden sin previo aviso. Además, si cierra el conjunto de registros o la base de datos primaria, el registro editado se descarta sin previo aviso.  
  
 En algunos casos, puede que desee actualizar una columna por lo que es Null (que contiene ningún dato). Para ello, llame a `SetFieldNull` con un parámetro de **TRUE** para marcar el campo es Null; Esto también hace que la columna que se va a actualizar. Si desea que un campo se escriben en el origen de datos incluso si no ha cambiado su valor, llame a `SetFieldDirty` con un parámetro de **TRUE**. Esto funciona incluso si el campo tiene el valor Null.  
  
 Las marcas de framework cambiar los miembros de datos de campo para asegurarse de que se escribirán en el registro en el origen de datos mediante el mecanismo de intercambio (DFX) de campos de registros DAO. Cambiar el valor de un campo normalmente establece el campo desfasadas automáticamente, por lo que rara vez deberá llamar a [SetFieldDirty](#setfielddirty) usted mismo, pero a veces, conviene asegurarse de que las columnas se explícitamente actualiza o inserta independientemente de qué valor está en el miembro de datos de campo. El mecanismo DFX también emplea el uso de **PSEUDO NULL**. Para obtener más información, consulte [CDaoFieldExchange:: M_noperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation).  
  
 Si no se utiliza el mecanismo de almacenamiento en búfer doble, a continuación, cambiar el valor del campo no establece automáticamente el campo como modificados. En este caso, será necesario establecer explícitamente el campo de datos sucios. La marca contenida en [m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields) controla la comprobación automática de campos.  
  
 Cuando el objeto de conjunto de registros está bloqueado de forma pesimista en un entorno multiusuario, el registro permanece bloqueado desde el momento en que **editar** se usa hasta que finalice la actualización. Si el conjunto de registros está bloqueado de forma optimista, el registro está bloqueado y se compara con el registro antes de ser modificado justo antes de que se actualiza en la base de datos. Si el registro ha cambiado desde que se llamó a **editar**, **actualización** operación provocará un error y MFC produce una excepción. Puede cambiar el modo de bloqueo con `SetLockingMode`.  
  
> [!NOTE]
>  Bloqueo optimista siempre se utiliza en los formatos de base de datos externa, como ODBC y ISAM instalable.  
  
 El registro actual se mantiene actual después de llamar a **editar**. Para llamar a **editar**, debe haber un registro actual. Si no hay ningún registro actual, o si el conjunto de registros no hace referencia a un tipo de tabla abierta o el objeto de conjunto de registros de tipo de conjunto de registros dinámicos, se produce una excepción. Al llamar a **editar** hace un `CDaoException` que se produzca en las siguientes condiciones:  
  
-   No hay ningún registro actual.  
  
-   La base de datos o el conjunto de registros es de solo lectura.  
  
-   No hay campos en el registro son actualizables.  
  
-   La base de datos o el conjunto de registros se abrió para uso exclusivo por otro usuario.  
  
-   Otro usuario ha bloqueado la página que contiene el registro.  
  
 Si el origen de datos admite transacciones, puede realizar la **editar** llame a parte de una transacción. Tenga en cuenta que debe llamar a `CDaoWorkspace::BeginTrans` antes de llamar a **editar** y después de que se ha abierto el conjunto de registros. Tenga en cuenta también que la llamada a `CDaoWorkspace::CommitTrans` no constituye un sustituto para llamar a **actualización** para completar la **editar** operación. Para obtener más información acerca de las transacciones, vea la clase `CDaoWorkspace`.  
  
 Para obtener información relacionada, vea los temas "AddNew (método)", "Editar método", "Método Delete", "Método de actualización" y "Propiedad actualizable" en la Ayuda de DAO.  
  
##  <a name="fillcache"></a>  CDaoRecordset:: FillCache  
 Llame a esta función miembro para almacenar en caché un número especificado de registros desde el conjunto de registros.  
  
```  
void FillCache(
    long* pSize = NULL,  
    COleVariant* pBookmark = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `pSize`  
 Especifica el número de filas en blanco para igualar la memoria caché. Si se omite este parámetro, el valor está determinado por el valor de la propiedad CacheSize del objeto DAO subyacente.  
  
 `pBookmark`  
 A [COleVariant](../../mfc/reference/colevariant-class.md) especificar un marcador. La memoria caché se llena a partir del registro indicado por este marcador. Si se omite este parámetro, la memoria caché se llena a partir del registro indicado por la propiedad CacheStart del objeto DAO subyacente.  
  
### <a name="remarks"></a>Comentarios  
 Almacenamiento en caché mejora el rendimiento de una aplicación que recupera o captura, los datos desde un servidor remoto. Una memoria caché es el espacio en la memoria local que contiene los datos que se han capturado recientemente desde el servidor en la suposición de que los datos probablemente se solicitará nuevo mientras se ejecuta la aplicación. Cuando se solicitan datos, el motor de base de datos de Microsoft Jet comprueba la memoria caché para los datos en primer lugar, en lugar de captura desde el servidor, que requiere más tiempo. Utilizando los datos de almacenamiento en caché en orígenes de datos ODBC no tiene ningún efecto como los datos no se guardan en la memoria caché.  
  
 En lugar de esperar la memoria caché se llena con registros, tal y como se han capturado, se puede llenar la memoria caché en cualquier momento mediante una llamada a la `FillCache` función miembro. Se trata de una manera más rápida de llenar la caché porque `FillCache` captura varios registros a la vez en lugar de uno en uno. Por ejemplo, mientras se está mostrando cada pantalla de registros, puede tener la llamada de la aplicación `FillCache` para capturar la siguiente pantalla de registros.  
  
 Cualquier base de datos ODBC que se obtiene acceso con objetos de conjunto de registros puede tener una caché local. Para crear la memoria caché, abra un objeto de conjunto de registros desde el origen de datos remoto y, a continuación, llame a la `SetCacheSize` y `SetCacheStart` funciones de miembro del conjunto de registros. Si `lSize` y *lBookmark* crear un rango que está parcial o totalmente fuera del intervalo especificado por `SetCacheSize` y `SetCacheStart`, la parte del conjunto de registros fuera de este intervalo se omite y no se ha cargado en la memoria caché. Si `FillCache` solicita más registros que permanecen en el origen de datos remoto, sólo los registros restantes se capturan y se inicia ninguna excepción.  
  
 Registros obtenidos de la memoria caché no reflejan los cambios realizados al mismo tiempo al origen de datos por otros usuarios.  
  
 `FillCache` captura solo los registros ya no almacenado en caché. Para forzar una actualización de todos los datos almacenados en caché, llame a la `SetCacheSize` función miembro con un `lSize` parámetro igual a 0, llamada `SetCacheSize` nuevo con el `lSize` parámetro igual que el tamaño de la memoria caché solicitada originalmente y, a continuación, llamar a `FillCache`.  
  
 Para obtener información relacionada, vea el tema "Método FillCache" en la Ayuda de DAO.  
  
##  <a name="find"></a>  CDaoRecordset::Find  
 Llame a esta función miembro para buscar una cadena concreta en un conjunto de registros de tipo dynaset o snapshot utilizando un operador de comparación.  
  
```  
virtual BOOL Find(
    long lFindType,  
    LPCTSTR lpszFilter);
```  
  
### <a name="parameters"></a>Parámetros  
 *lFindType*  
 Un valor que indica el tipo de operación de búsqueda deseado. Los valores posibles son:  
  
- **AFX_DAO_NEXT** encontrar la ubicación siguiente de una cadena coincidente.  
  
- **AFX_DAO_PREV** encontrar la ubicación anterior de una cadena coincidente.  
  
- **AFX_DAO_FIRST** buscar la primera ubicación de una cadena coincidente.  
  
- **Bien AFX_DAO_LAST** buscar la última ubicación de una cadena coincidente.  
  
 `lpszFilter`  
 Una expresión de cadena (como el **donde** cláusula en una instrucción SQL sin la palabra **donde**) utilizado para buscar el registro. Por ejemplo:  
  
 [!code-cpp[NVC_MFCDatabase#3](../../mfc/codesnippet/cpp/cdaorecordset-class_3.cpp)]  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si no se encuentra registros coincidentes, 0 en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 Puede encontrar el primer, siguiente, anterior, o última instancia de la cadena. **Buscar** es una función virtual, por lo que puede invalidarlo y agregar su propia implementación. El `FindFirst`, `FindLast`, `FindNext`, y `FindPrev` funciones miembro llaman a la **buscar** función de miembro, por lo que puede usar **buscar** para controlar el comportamiento de todas las operaciones de búsqueda .  
  
 Para buscar un registro en un conjunto de registros de tipo de tabla, llame a la [Seek](#seek) función miembro.  
  
> [!TIP]
>  Cuanto menor sea el conjunto de registros tiene, aumentará la eficacia **buscar** será. En general y especialmente con datos ODBC, es mejor crear una nueva consulta que recupera solo los registros que desee.  
  
 Para obtener información relacionada, vea el tema "FindFirst, FindLast, FindNext, FindPrevious métodos" en la Ayuda de DAO.  
  
##  <a name="findfirst"></a>  CDaoRecordset::FindFirst  
 Llame a esta función miembro para encontrar el primer registro que coincide con una condición especificada.  
  
```  
BOOL FindFirst(LPCTSTR lpszFilter);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszFilter`  
 Una expresión de cadena (como el **donde** cláusula en una instrucción SQL sin la palabra **donde**) utilizado para buscar el registro.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si no se encuentra registros coincidentes, 0 en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 El `FindFirst` función miembro comienza la búsqueda desde el principio del conjunto de registros y busque hacia el final del conjunto de registros.  
  
 Si desea incluir todos los registros en la búsqueda (no solo los que cumplen una condición específica) usan una de las operaciones de desplazamiento para desplazarse por los registros. Para buscar un registro en un conjunto de registros de tipo de tabla, llame a la `Seek` función miembro.  
  
 Si no se encuentra un registro que cumpla los criterios, el puntero de registro actual es indeterminado, y `FindFirst` devuelve cero. Si el conjunto de registros contiene más de un registro que satisface los criterios, `FindFirst` localiza la primera aparición, `FindNext` busca la siguiente repetición y así sucesivamente.  
  
> [!CAUTION]
>  Si edita el registro actual, asegúrese de guardar los cambios mediante una llamada a la **actualización** función de miembro antes de continuar con otro registro. Si mueve a otro registro sin actualizar, los cambios se pierden sin previo aviso.  
  
 El **buscar** funciones miembro buscar desde la ubicación y en la dirección especificada en la tabla siguiente:  
  
|Las operaciones de búsqueda|BEGIN|Dirección de búsqueda|  
|---------------------|-----------|----------------------|  
|`FindFirst`|Principio del conjunto de registros|Final del conjunto de registros|  
|`FindLast`|Final del conjunto de registros|Principio del conjunto de registros|  
|`FindNext`|Registro actual|Final del conjunto de registros|  
|**FindPrevious**|Registro actual|Principio del conjunto de registros|  
  
> [!NOTE]
>  Cuando se llama a `FindLast`, el motor de base de datos de Microsoft Jet rellena totalmente el conjunto de registros antes de comenzar la búsqueda, si esto ya no se ha hecho. La primera búsqueda puede tardar más que búsquedas subsiguientes.  
  
 Utilizando una de las operaciones de búsqueda no es el mismo que llamar al método **MoveFirst** o `MoveNext`, sin embargo, que simplemente hace que el primer o siguiente registro actual sin especificar una condición. Puede seguir una operación de búsqueda con una operación de movimiento.  
  
 Al usar las operaciones de búsqueda, tenga en cuenta lo siguiente:  
  
-   Si **buscar** devuelve distinto de cero, el registro actual no está definido. En este caso, debe colocar el puntero de registro actual hacia un registro válido.  
  
-   No se puede usar una operación de búsqueda con un recordset de tipo snapshot desplazamiento solo hacia delante.  
  
-   Debe tener el formato de fecha de Estados Unidos (mes-año) cuando busca campos que contienen fechas, incluso si no usa la versión de Estados Unidos del motor de base de datos de Microsoft Jet; en caso contrario, registros coincidentes no se pueden encontrar.  
  
-   Cuando se trabaja con grandes conjuntos de registros dinámicos y de bases de datos ODBC, puede detectar que utiliza las operaciones de búsqueda es muy lento, especialmente cuando se trabaja con grandes conjuntos de registros. Puede mejorar el rendimiento mediante consultas SQL con personalizarse **ORDERBY** o **donde** cláusulas, consultas de parámetros, o **CDaoQuerydef** objetos que recuperan específico registros indizados.  
  
 Para obtener información relacionada, vea el tema "FindFirst, FindLast, FindNext, FindPrevious métodos" en la Ayuda de DAO.  
  
##  <a name="findlast"></a>  CDaoRecordset::FindLast  
 Llame a esta función miembro para encontrar el último registro que coincide con una condición especificada.  
  
```  
BOOL FindLast(LPCTSTR lpszFilter);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszFilter`  
 Una expresión de cadena (como el **donde** cláusula en una instrucción SQL sin la palabra **donde**) utilizado para buscar el registro.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si no se encuentra registros coincidentes, 0 en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 El `FindLast` función miembro comienza la búsqueda al final del conjunto de registros y las búsquedas hacia atrás hacia el principio del conjunto de registros.  
  
 Si desea incluir todos los registros en la búsqueda (no solo los que cumplen una condición específica) usan una de las operaciones de desplazamiento para desplazarse por los registros. Para buscar un registro en un conjunto de registros de tipo de tabla, llame a la `Seek` función miembro.  
  
 Si no se encuentra un registro que cumpla los criterios, el puntero de registro actual es indeterminado, y `FindLast` devuelve cero. Si el conjunto de registros contiene más de un registro que satisface los criterios, `FindFirst` localiza la primera aparición, `FindNext` busca la siguiente aparición después de la primera aparición y así sucesivamente.  
  
> [!CAUTION]
>  Si edita el registro actual, asegúrese de guardar los cambios mediante una llamada a la **actualización** función de miembro antes de continuar con otro registro. Si mueve a otro registro sin actualizar, los cambios se pierden sin previo aviso.  
  
 Utilizando una de las operaciones de búsqueda no es el mismo que llamar al método **MoveFirst** o `MoveNext`, sin embargo, que simplemente hace que el primer o siguiente registro actual sin especificar una condición. Puede seguir una operación de búsqueda con una operación de movimiento.  
  
 Al usar las operaciones de búsqueda, tenga en cuenta lo siguiente:  
  
-   Si **buscar** devuelve distinto de cero, el registro actual no está definido. En este caso, debe colocar el puntero de registro actual hacia un registro válido.  
  
-   No se puede usar una operación de búsqueda con un recordset de tipo snapshot desplazamiento solo hacia delante.  
  
-   Debe tener el formato de fecha de Estados Unidos (mes-año) cuando busca campos que contienen fechas, incluso si no usa la versión de Estados Unidos del motor de base de datos de Microsoft Jet; en caso contrario, registros coincidentes no se pueden encontrar.  
  
-   Cuando se trabaja con grandes conjuntos de registros dinámicos y de bases de datos ODBC, puede detectar que utiliza las operaciones de búsqueda es muy lento, especialmente cuando se trabaja con grandes conjuntos de registros. Puede mejorar el rendimiento mediante consultas SQL con personalizarse **ORDERBY** o **donde** cláusulas, consultas de parámetros, o **CDaoQuerydef** objetos que recuperan específico registros indizados.  
  
 Para obtener información relacionada, vea el tema "FindFirst, FindLast, FindNext, FindPrevious métodos" en la Ayuda de DAO.  
  
##  <a name="findnext"></a>  CDaoRecordset::FindNext  
 Llame a esta función miembro para encontrar el registro siguiente que coincida con una condición especificada.  
  
```  
BOOL FindNext(LPCTSTR lpszFilter);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszFilter`  
 Una expresión de cadena (como el **donde** cláusula en una instrucción SQL sin la palabra **donde**) utilizado para buscar el registro.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si no se encuentra registros coincidentes, 0 en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 El `FindNext` función miembro comienza la búsqueda en el registro actual y busca al final del conjunto de registros.  
  
 Si desea incluir todos los registros en la búsqueda (no solo los que cumplen una condición específica) usan una de las operaciones de desplazamiento para desplazarse por los registros. Para buscar un registro en un conjunto de registros de tipo de tabla, llame a la `Seek` función miembro.  
  
 Si no se encuentra un registro que cumpla los criterios, el puntero de registro actual es indeterminado, y `FindNext` devuelve cero. Si el conjunto de registros contiene más de un registro que satisface los criterios, `FindFirst` localiza la primera aparición, `FindNext` busca la siguiente repetición y así sucesivamente.  
  
> [!CAUTION]
>  Si edita el registro actual, asegúrese de guardar los cambios mediante una llamada a la **actualización** función de miembro antes de continuar con otro registro. Si mueve a otro registro sin actualizar, los cambios se pierden sin previo aviso.  
  
 Utilizando una de las operaciones de búsqueda no es el mismo que llamar al método **MoveFirst** o `MoveNext`, sin embargo, que simplemente hace que el primer o siguiente registro actual sin especificar una condición. Puede seguir una operación de búsqueda con una operación de movimiento.  
  
 Al usar las operaciones de búsqueda, tenga en cuenta lo siguiente:  
  
-   Si **buscar** devuelve distinto de cero, el registro actual no está definido. En este caso, debe colocar el puntero de registro actual hacia un registro válido.  
  
-   No se puede usar una operación de búsqueda con un recordset de tipo snapshot desplazamiento solo hacia delante.  
  
-   Debe tener el formato de fecha de Estados Unidos (mes-año) cuando busca campos que contienen fechas, incluso si no usa la versión de Estados Unidos del motor de base de datos de Microsoft Jet; en caso contrario, registros coincidentes no se pueden encontrar.  
  
-   Cuando se trabaja con grandes conjuntos de registros dinámicos y de bases de datos ODBC, puede detectar que utiliza las operaciones de búsqueda es muy lento, especialmente cuando se trabaja con grandes conjuntos de registros. Puede mejorar el rendimiento mediante consultas SQL con personalizarse **ORDERBY** o **donde** cláusulas, consultas de parámetros, o **CDaoQuerydef** objetos que recuperan específico registros indizados.  
  
 Para obtener información relacionada, vea el tema "FindFirst, FindLast, FindNext, FindPrevious métodos" en la Ayuda de DAO.  
  
##  <a name="findprev"></a>  CDaoRecordset::FindPrev  
 Llame a esta función miembro para encontrar el registro anterior que cumple una condición especificada.  
  
```  
BOOL FindPrev(LPCTSTR lpszFilter);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszFilter`  
 Una expresión de cadena (como el **donde** cláusula en una instrucción SQL sin la palabra **donde**) utilizado para buscar el registro.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si no se encuentra registros coincidentes, 0 en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 El `FindPrev` función miembro comienza la búsqueda en el registro actual y busca hacia atrás hacia el principio del conjunto de registros.  
  
 Si desea incluir todos los registros en la búsqueda (no solo los que cumplen una condición específica) usan una de las operaciones de desplazamiento para desplazarse por los registros. Para buscar un registro en un conjunto de registros de tipo de tabla, llame a la `Seek` función miembro.  
  
 Si no se encuentra un registro que cumpla los criterios, el puntero de registro actual es indeterminado, y `FindPrev` devuelve cero. Si el conjunto de registros contiene más de un registro que satisface los criterios, `FindFirst` localiza la primera aparición, `FindNext` busca la siguiente repetición y así sucesivamente.  
  
> [!CAUTION]
>  Si edita el registro actual, asegúrese de guardar los cambios mediante una llamada a la **actualización** función de miembro antes de continuar con otro registro. Si mueve a otro registro sin actualizar, los cambios se pierden sin previo aviso.  
  
 Utilizando una de las operaciones de búsqueda no es el mismo que llamar al método **MoveFirst** o `MoveNext`, sin embargo, que simplemente hace que el primer o siguiente registro actual sin especificar una condición. Puede seguir una operación de búsqueda con una operación de movimiento.  
  
 Al usar las operaciones de búsqueda, tenga en cuenta lo siguiente:  
  
-   Si **buscar** devuelve distinto de cero, el registro actual no está definido. En este caso, debe colocar el puntero de registro actual hacia un registro válido.  
  
-   No se puede usar una operación de búsqueda con un recordset de tipo snapshot desplazamiento solo hacia delante.  
  
-   Debe tener el formato de fecha de Estados Unidos (mes-año) cuando busca campos que contienen fechas, incluso si no usa la versión de Estados Unidos del motor de base de datos de Microsoft Jet; en caso contrario, registros coincidentes no se pueden encontrar.  
  
-   Cuando se trabaja con grandes conjuntos de registros dinámicos y de bases de datos ODBC, puede detectar que utiliza las operaciones de búsqueda es muy lento, especialmente cuando se trabaja con grandes conjuntos de registros. Puede mejorar el rendimiento mediante consultas SQL con personalizarse **ORDERBY** o **donde** cláusulas, consultas de parámetros, o **CDaoQuerydef** objetos que recuperan específico registros indizados.  
  
 Para obtener información relacionada, vea el tema "FindFirst, FindLast, FindNext, FindPrevious métodos" en la Ayuda de DAO.  
  
##  <a name="getabsoluteposition"></a>  CDaoRecordset:: GetAbsolutePosition  
 Devuelve el número de registro del registro actual del objeto de conjunto de registros.  
  
```  
long GetAbsolutePosition();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Entero del 0 al número de registros en el conjunto de registros. Corresponde a la posición ordinal del registro actual en el conjunto de registros.  
  
### <a name="remarks"></a>Comentarios  
 El valor de propiedad AbsolutePosition del objeto DAO subyacente está basado en cero; un valor de 0 hace referencia al primer registro del conjunto de registros. Puede determinar el número de registros rellenados en el conjunto de registros mediante una llamada a [GetRecordCount](#getrecordcount). Al llamar a `GetRecordCount` puede tardar algún tiempo porque se deben tener acceso a todos los registros para determinar el recuento.  
  
 Si no hay ningún registro actual, como cuando no hay ningún registro en el conjunto de registros, se devuelve 1. Si se elimina el registro actual, el valor de la propiedad AbsolutePosition no está definido y MFC inicia una excepción si se hace referencia. Para conjuntos de registros de tipo de conjunto de registros dinámicos, se agregan nuevos registros al final de la secuencia.  
  
> [!NOTE]
>  Esta propiedad no está diseñada para usarse como un número de registro suplente. Los marcadores siguen siendo la forma recomendada de conservar y volver a una posición determinada y son la única forma de colocar el registro actual en todos los tipos de objetos de conjunto de registros. En concreto, la posición de un registro determinado cambia cuando se eliminan registros anteriores a ésta. También no hay ninguna garantía de que un determinado registro tendrá la misma posición absoluta si se vuelve a crear el conjunto de registros, porque no se garantiza el orden de los registros individuales dentro de un conjunto de registros, a menos que se crea con una instrucción SQL que usa un  **ORDERBY** cláusula.  
  
> [!NOTE]
>  Esta función miembro es válida únicamente para el tipo de conjunto de registros dinámicos y conjuntos de registros de tipo de instantánea.  
  
 Para obtener información relacionada, vea el tema "AbsolutePosition (propiedad)" en la Ayuda de DAO.  
  
##  <a name="getbookmark"></a>  CDaoRecordset:: GetBookmark  
 Llame a esta función miembro para obtener el valor de marcador en un registro concreto.  
  
```  
COleVariant GetBookmark();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un valor que representa el marcador en el registro actual.  
  
### <a name="remarks"></a>Comentarios  
 Cuando se crea o abre un objeto de conjunto de registros, cada uno de sus registros tiene ya un marcador único si admite. Llame a `CanBookmark` para determinar si un conjunto de registros admite marcadores.  
  
 Puede guardar el marcador para el registro actual asignando el valor del marcador a un `COleVariant` objeto. Para volver rápidamente a ese registro en cualquier momento después de moverse a un registro diferente, llame a `SetBookmark` con un parámetro que corresponde al valor de ese `COleVariant` objeto.  
  
> [!NOTE]
>  Al llamar a [Requery](#requery) cambia marcadores DAO.  
  
 Para obtener información relacionada, vea el tema "Propiedades de marcador" en la Ayuda de DAO.  
  
##  <a name="getcachesize"></a>  CDaoRecordset::GetCacheSize  
 Llame a esta función miembro para obtener el número de registros almacenados en memoria caché.  
  
```  
long GetCacheSize();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor que especifica el número de registros en un conjunto de registros de tipo dinámico que contiene datos que se va a almacenar en caché localmente desde un origen de datos ODBC.  
  
### <a name="remarks"></a>Comentarios  
 Almacenamiento en caché de datos mejora el rendimiento de una aplicación que recupera datos de un servidor remoto a través de objetos de conjunto de registros de tipo de conjunto de registros dinámicos. Una caché es un espacio en la memoria local que contiene los datos recuperados más recientemente desde el servidor en caso de que los datos volverá a solicitarse mientras se ejecuta la aplicación. Cuando se solicitan datos, el motor de base de datos de Microsoft Jet comprueba la memoria caché para los datos solicitados en primer lugar, en lugar de recuperar desde el servidor, que requiere más tiempo. Datos que no proceden de un origen de datos ODBC no se guardan en la memoria caché.  
  
 Cualquier origen de datos ODBC, como una tabla asociada, puede tener una caché local.  
  
 Para obtener información relacionada, vea el tema "CacheSize, CacheStart (propiedades)" en la Ayuda de DAO.  
  
##  <a name="getcachestart"></a>  CDaoRecordset::GetCacheStart  
 Llame a esta función miembro para obtener el valor de marcador del primer registro en el conjunto de registros en la memoria caché.  
  
```  
COleVariant GetCacheStart();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un `COleVariant` que especifica el marcador del primer registro en el conjunto de registros en la memoria caché.  
  
### <a name="remarks"></a>Comentarios  
 El motor de base de datos de Microsoft Jet solicita registros dentro del intervalo de memoria caché de la memoria caché y solicita registros fuera del intervalo de memoria caché del servidor.  
  
> [!NOTE]
>  Los registros recuperados de la memoria caché no reflejan los cambios realizados al mismo tiempo al origen de datos por otros usuarios.  
  
 Para obtener información relacionada, vea el tema "CacheSize, CacheStart (propiedades)" en la Ayuda de DAO.  
  
##  <a name="getcurrentindex"></a>  CDaoRecordset::GetCurrentIndex  
 Llame a esta función miembro para determinar el índice actualmente en uso en un tipo de tabla indizado `CDaoRecordset` objeto.  
  
```  
CString GetCurrentIndex();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un `CString` que contiene el nombre del índice actualmente en uso con un conjunto de registros de tipo de tabla. Devuelve una cadena vacía si no se ha establecido ningún índice.  
  
### <a name="remarks"></a>Comentarios  
 Este índice es la base para ordenar los registros en un conjunto de registros de tipo de tabla y se usa por la [Seek](#seek) función de miembro para localizar los registros.  
  
 A `CDaoRecordset` objeto puede tener más de un índice, pero puede utilizar solo un índice a la vez (aunque un [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md) objeto puede tener varios índices definidos en él).  
  
 Para obtener información relacionada, vea el tema "Objeto Index" y la definición de "índice actual" en la Ayuda de DAO.  
  
##  <a name="getdatecreated"></a>  CDaoRecordset::GetDateCreated  
 Llame a esta función miembro para recuperar la fecha y hora de que creación de una tabla base.  
  
```  
COleDateTime GetDateCreated();
```  
  
### <a name="return-value"></a>Valor devuelto  
 A [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objeto que contiene la fecha y hora de creación de la tabla base.  
  
### <a name="remarks"></a>Comentarios  
 Configuración de fecha y hora se deriva del equipo en el que se creó la tabla base.  
  
 Para obtener información relacionada, vea el tema "DateCreated y LastUpdated propiedades" en la Ayuda de DAO.  
  
##  <a name="getdatelastupdated"></a>  CDaoRecordset::GetDateLastUpdated  
 Llame a esta función miembro para recuperar la fecha y hora que se actualizó por última vez el esquema.  
  
```  
COleDateTime GetDateLastUpdated();
```  
  
### <a name="return-value"></a>Valor devuelto  
 A [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objeto que contiene la fecha y hora que se actualizó por última vez la estructura de la tabla base (esquema).  
  
### <a name="remarks"></a>Comentarios  
 Configuración de fecha y hora se deriva del equipo en el que se actualizó por última vez la estructura de la tabla base (esquema).  
  
 Para obtener información relacionada, vea el tema "DateCreated y LastUpdated propiedades" en la Ayuda de DAO.  
  
##  <a name="getdefaultdbname"></a>  CDaoRecordset::GetDefaultDBName  
 Llame a esta función miembro para determinar el nombre de la base de datos para este conjunto de registros.  
  
```  
virtual CString GetDefaultDBName();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un `CString` que contiene la ruta de acceso y el nombre de la base de datos que se deriva este conjunto de registros.  
  
### <a name="remarks"></a>Comentarios  
 Si se crea un conjunto de registros sin un puntero a un [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md), a continuación, esta ruta de acceso es utilizado por el conjunto de registros para abrir la base de datos de forma predeterminada. De forma predeterminada, esta función devuelve una cadena vacía. Cuando ClassWizard deriva un nuevo conjunto de registros de `CDaoRecordset`, va a crear esta función para usted.  
  
 En el ejemplo siguiente se muestra el uso de la barra diagonal inversa doble (\\\\) en la cadena, según sea necesario para la cadena para que se interpreten correctamente.  
  
 [!code-cpp[NVC_MFCDatabase#4](../../mfc/codesnippet/cpp/cdaorecordset-class_4.cpp)]  
  
##  <a name="getdefaultsql"></a>  CDaoRecordset::GetDefaultSQL  
 El marco de trabajo llama a esta función miembro para obtener la instrucción SQL de forma predeterminada en la que se basa el conjunto de registros.  
  
```  
virtual CString GetDefaultSQL();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un `CString` que contiene la instrucción SQL predeterminada.  
  
### <a name="remarks"></a>Comentarios  
 Podría tratarse de un nombre de tabla o una instancia de SQL **seleccione** instrucción.  
  
 Puede definir indirectamente la instrucción SQL predeterminada mediante la declaración de la clase de conjunto de registros con ClassWizard; ClassWizard realiza esta tarea automáticamente.  
  
 Si se pasa una cadena SQL null a [abiertos](#open), a continuación, llama a esta función para determinar el nombre de la tabla o SQL para el conjunto de registros.  
  
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
|**dbEditNone**|No hay ninguna operación de edición está en curso.|  
|**dbEditInProgress**|**Editar** se ha llamado.|  
|**dbEditAdd**|`AddNew` se ha llamado.|  
  
 Para obtener información relacionada, vea el tema "Propiedad EditMode" en la Ayuda de DAO.  
  
##  <a name="getfieldcount"></a>  CDaoRecordset::GetFieldCount  
 Llame a esta función miembro para recuperar el número de campos (columnas) definidos en el conjunto de registros.  
  
```  
short GetFieldCount();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de campos del conjunto de registros.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener información relacionada, vea el tema "Recuento de propiedad" en la Ayuda de DAO.  
  
##  <a name="getfieldinfo"></a>  CDaoRecordset::GetFieldInfo  
 Llame a esta función miembro para obtener información acerca de los campos en un conjunto de registros.  
  
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
 `nIndex`  
 Índice de base cero del campo predefinido en la colección de campos del conjunto de registros, para la búsqueda por su índice.  
  
 `fieldinfo`  
 Una referencia a un [CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md) estructura.  
  
 `dwInfoOptions`  
 Opciones que especifican qué información acerca de los registros que se va a recuperar. A continuación se enumeran las opciones disponibles junto con lo que hacen que la función devuelva. Para obtener el mejor rendimiento, recuperar solo el nivel de información que necesita:  
  
- `AFX_DAO_PRIMARY_INFO` (Valor predeterminado) Nombre, tipo, tamaño, atributos  
  
- `AFX_DAO_SECONDARY_INFO` La información principal, además de: posición Ordinal, necesario, permitir cero tabla de origen de longitud, orden de intercalación, nombre de la externa, el campo de origen,  
  
- `AFX_DAO_ALL_INFO` Información primaria y secundaria, además de: valor predeterminado, regla de validación, texto de validación  
  
 `lpszName`  
 Nombre del campo.  
  
### <a name="remarks"></a>Comentarios  
 Una versión de la función le permite buscar un campo por su índice. La otra versión le permite buscar un campo por su nombre.  
  
 Para obtener una descripción de la información devuelta, consulte el [CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md) estructura. Esta estructura no tiene miembros que se corresponden con los elementos de información enumerados anteriormente en la descripción de `dwInfoOptions`. Cuando se solicita información en un nivel, obtendrá información para todos los niveles anteriores.  
  
 Para obtener información relacionada, vea el tema "Atributos de propiedad" en la Ayuda de DAO.  
  
##  <a name="getfieldvalue"></a>  CDaoRecordset:: GetFieldValue  
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
 `lpszName`  
 Un puntero a una cadena que contiene el nombre de un campo.  
  
 `varValue`  
 Una referencia a un `COleVariant` objeto que se va a almacenar el valor de un campo.  
  
 `nIndex`  
 Índice de base cero del campo en la colección de campos del conjunto de registros, para la búsqueda por su índice.  
  
### <a name="return-value"></a>Valor devuelto  
 Las dos versiones de `GetFieldValue` que devuelven un valor devuelto una [COleVariant](../../mfc/reference/colevariant-class.md) objeto que contiene el valor de un campo.  
  
### <a name="remarks"></a>Comentarios  
 Puede buscar un campo por nombre o por posición ordinal.  
  
> [!NOTE]
>  Resulta más eficaz para llamar a una de las versiones de esta función miembro que toma un `COleVariant` referencia de objeto como un parámetro, en lugar de llamar a una versión que devuelve un `COleVariant` objeto. Las versiones más recientes de esta función se mantienen por compatibilidad con versiones anteriores.  
  
 Use `GetFieldValue` y [SetFieldValue](#setfieldvalue) enlazar campos dinámicamente en tiempo de ejecución en lugar de estáticamente columnas de enlace mediante la [DoFieldExchange](#dofieldexchange) mecanismo.  
  
 `GetFieldValue` y el `DoFieldExchange` mecanismo se puede combinar para mejorar el rendimiento. Por ejemplo, utilice `GetFieldValue` para recuperar un valor que debe sólo a petición y asignar esa llamada para un botón de "Más información" en la interfaz.  
  
 Para obtener información relacionada, vea los temas "Objeto Field" y "Valor de propiedad" en la Ayuda de DAO.  
  
##  <a name="getindexcount"></a>  CDaoRecordset::GetIndexCount  
 Llame a esta función miembro para determinar el número de índice disponibles en el conjunto de registros de tipo de tabla.  
  
```  
short GetIndexCount();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de índices en el conjunto de registros de tipo de tabla.  
  
### <a name="remarks"></a>Comentarios  
 `GetIndexCount` es útil para recorrer en iteración todos los índices en el conjunto de registros. Para ello, use `GetIndexCount` junto con [GetIndexInfo](#getindexinfo). Si se llama a esta función miembro en tipo de conjunto de registros dinámicos o los conjuntos de registros de tipo de instantánea, MFC inicia una excepción.  
  
 Para obtener información relacionada, vea el tema "Atributos de propiedad" en la Ayuda de DAO.  
  
##  <a name="getindexinfo"></a>  CDaoRecordset::GetIndexInfo  
 Llame a esta función miembro para obtener información acerca de los índices definidos en la tabla base subyacente de un conjunto de registros de diferentes tipos.  
  
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
 `nIndex`  
 Índice de base cero en la colección de índices de la tabla, para la búsqueda por posición numérica.  
  
 `indexinfo`  
 Una referencia a un [CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md) estructura.  
  
 `dwInfoOptions`  
 Opciones que especifican qué información sobre el índice para recuperar. A continuación se enumeran las opciones disponibles junto con lo que hacen que la función devuelva. Para obtener el mejor rendimiento, recuperar solo el nivel de información que necesita:  
  
- `AFX_DAO_PRIMARY_INFO` (Valor predeterminado) Campos de nombre, información de campo  
  
- `AFX_DAO_SECONDARY_INFO` La información principal, además de: principal, Unique, Clustered, IgnoreNulls, necesario, externo  
  
- `AFX_DAO_ALL_INFO` Información primaria y secundaria, además de: Distinct Count  
  
 `lpszName`  
 Un puntero al nombre del objeto de índice, para la búsqueda por nombre.  
  
### <a name="remarks"></a>Comentarios  
 Una versión de la función le permite buscar un índice por su posición en la colección. La otra versión le permite buscar un índice por su nombre.  
  
 Para obtener una descripción de la información devuelta, consulte el [CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md) estructura. Esta estructura no tiene miembros que se corresponden con los elementos de información enumerados anteriormente en la descripción de `dwInfoOptions`. Cuando se solicita información en un nivel, obtendrá información para todos los niveles anteriores.  
  
 Para obtener información relacionada, vea el tema "Atributos de propiedad" en la Ayuda de DAO.  
  
##  <a name="getlastmodifiedbookmark"></a>  CDaoRecordset::GetLastModifiedBookmark  
 Llame a esta función miembro para recuperar el marcador del registro más recientemente agregado o actualizado.  
  
```  
COleVariant GetLastModifiedBookmark();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un `COleVariant` que contiene un marcador que indica el último registro agregado o modificado.  
  
### <a name="remarks"></a>Comentarios  
 Cuando se crea o abre un objeto de conjunto de registros, cada uno de sus registros tiene ya un marcador único si admite. Llame a [GetBookmark](#getbookmark) para determinar si el conjunto de registros admite marcadores. Si el conjunto de registros no es compatible con los marcadores, un `CDaoException` se produce.  
  
 Cuando se agrega un registro, aparece al final del conjunto de registros y no es el registro actual. Para que el nuevo registro actual, llame a `GetLastModifiedBookmark` y, a continuación, llame a `SetBookmark` para devolver el registro recién agregado.  
  
 Para obtener información relacionada, vea el tema "LastModified de la propiedad" en la Ayuda de DAO.  
  
##  <a name="getlockingmode"></a>  CDaoRecordset::GetLockingMode  
 Llame a esta función miembro para determinar el tipo de bloqueo en vigor para el conjunto de registros.  
  
```  
BOOL GetLockingMode();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el tipo de bloqueo es pesimista, en caso contrario 0 para el bloqueo de registro optimista.  
  
### <a name="remarks"></a>Comentarios  
 Cuando el bloqueo pesimista está activada, la página de datos que contiene el registro que está modificando está bloqueada en cuanto se llama a la [editar](#edit) función miembro. La página se desbloquea cuando se llama a la [actualización](#update) o [cerrar](#close) función miembro o cualquiera de las operaciones de movimiento o búsqueda.  
  
 Cuando está activado un bloqueo optimista, la página de datos que contiene el registro está bloqueada solo mientras se actualiza el registro con el **actualización** función miembro.  
  
 Al trabajar con orígenes de datos ODBC, el modo de bloqueo siempre es optimista.  
  
 Para obtener información relacionada, vea los temas "Propiedad LockEdits" y "Comportamiento de bloqueo en Multiuser Applications" en la Ayuda de DAO.  
  
##  <a name="getname"></a>  CDaoRecordset::GetName  
 Llame a esta función miembro para recuperar el nombre del conjunto de registros.  
  
```  
CString GetName();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un `CString` que contiene el nombre del conjunto de registros.  
  
### <a name="remarks"></a>Comentarios  
 El nombre del conjunto de registros debe comenzar con una letra y puede contener un máximo de 40 caracteres. Puede incluir números y caracteres de subrayado pero no puede incluir espacios o signos de puntuación.  
  
 Para obtener información relacionada, vea el tema "Nombre de propiedad" en la Ayuda de DAO.  
  
##  <a name="getparamvalue"></a>  CDaoRecordset::GetParamValue  
 Llame a esta función miembro para recuperar el valor actual del parámetro especificado almacenado en el objeto DAOParameter subyacente.  
  
```  
virtual COleVariant GetParamValue(int nIndex);  
virtual COleVariant GetParamValue(LPCTSTR lpszName);
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 La posición numérica del parámetro en el objeto DAOParameter subyacente.  
  
 `lpszName`  
 El nombre del parámetro cuyo valor desee.  
  
### <a name="return-value"></a>Valor devuelto  
 Un objeto de clase [COleVariant](../../mfc/reference/colevariant-class.md) que contiene el valor del parámetro.  
  
### <a name="remarks"></a>Comentarios  
 El parámetro puede tener acceso por nombre o por su posición numérica en la colección.  
  
 Para obtener información relacionada, vea el tema "Objeto de parámetro" en la Ayuda de DAO.  
  
##  <a name="getpercentposition"></a>  CDaoRecordset:: GetPercentPosition  
 Cuando se trabaja con un tipo de conjunto de registros dinámicos o un conjunto de registros de tipo de instantánea, si se llama a `GetPercentPosition` antes de rellenar completamente el conjunto de registros, es la cantidad de movimiento en relación con el número de registros que se tiene acceso a como se indica mediante una llamada a [GetRecordCount](#getrecordcount).  
  
```  
float GetPercentPosition();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un número entre 0 y 100 que indica la ubicación aproximada del registro actual en el objeto de conjunto de registros basándose en un porcentaje de los registros del conjunto de registros.  
  
### <a name="remarks"></a>Comentarios  
 Puede mover al último registro mediante una llamada a [MoveLast](#movelast) para completar la población de todos los conjuntos de registros, pero esto puede tardar una cantidad considerable de tiempo.  
  
 Puede llamar a `GetPercentPosition` en los tres tipos de objetos de conjunto de registros, incluidas las tablas sin índices. Sin embargo, no se puede llamar a `GetPercentPosition` en instantáneas de desplazamiento solo hacia delante, o en un conjunto de registros que se abre desde una consulta de paso a través en una base de datos externo. Si no hay ningún registro actual, o se ha eliminado el registro actual de, un `CDaoException` se produce.  
  
 Para obtener información relacionada, vea el tema "PercentPosition (propiedad)" en la Ayuda de DAO.  
  
##  <a name="getrecordcount"></a>  CDaoRecordset::GetRecordCount  
 Llame a esta función miembro para averiguar el número de registros en un conjunto de registros se ha tenido acceso.  
  
```  
long GetRecordCount();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el número de registros que se obtiene acceso en un objeto de conjunto de registros.  
  
### <a name="remarks"></a>Comentarios  
 `GetRecordCount` no indica el número de registros se encuentran en un tipo de conjunto de registros dinámicos o un conjunto de registros de tipo de instantánea hasta que todos los registros se ha tenido acceso. Esta llamada de función miembro puede tardar una cantidad significativa de tiempo en completarse.  
  
 Una vez que se ha accedido al último registro, el valor devuelto indica el número total de registros sin eliminarse en el conjunto de registros. Para obligar al tener acceso el último registro, llame a la `MoveLast` o `FindLast` función de miembro para el conjunto de registros. También puede usar un recuento de SQL para determinar el número aproximado de registros que devolverá la consulta.  
  
 Como la aplicación elimina registros en un conjunto de registros de tipo dynaset, el valor devuelto de `GetRecordCount` disminuye. Sin embargo, los registros eliminados por otros usuarios no se reflejan en `GetRecordCount` hasta que el registro actual se coloca en un registro eliminado. Si ejecuta una transacción que afecta al número de registros y posteriormente deshace la transacción, `GetRecordCount` no reflejará el número real de los registros restantes.  
  
 El valor de `GetRecordCount` de un conjunto de registros de tipo de instantánea no se ve afectada por los cambios en las tablas subyacentes.  
  
 El valor de `GetRecordCount` de un tipo de tabla refleja el número aproximado de entradas en la tabla de conjunto de registros y se ve afectada inmediatamente cuando se agregan o eliminan registros de la tabla.  
  
 Un conjunto de registros no tienen registros devuelve un valor de 0. Al trabajar con tablas adjuntas o bases de datos ODBC, `GetRecordCount` siempre devuelve - 1. Llamar a la **Requery** función miembro en un conjunto de registros restablece el valor de `GetRecordCount` como si se volverá a ejecutar la consulta.  
  
 Para obtener información relacionada, vea el tema "Propiedad RecordCount" en la Ayuda de DAO.  
  
##  <a name="getsql"></a>  CDaoRecordset::GetSQL  
 Llame a esta función miembro para obtener la instrucción SQL que se usa para seleccionar los registros del conjunto de registros al que se abrió.  
  
```  
CString GetSQL() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un `CString` que contiene la instrucción SQL.  
  
### <a name="remarks"></a>Comentarios  
 Esto suele ser una instancia de SQL **seleccione** instrucción.  
  
 La cadena devuelta por `GetSQL` suele ser distinto de cualquier cadena que se ha pasado para el conjunto de registros en la `lpszSQL` parámetro a la [abiertos](#open) función miembro. Esto es porque el conjunto de registros construye una instrucción SQL completa en función de lo que pasa a **abiertos**, lo que hayas especificado con ClassWizard y lo que puede que haya especificado en el [m_strFilter](#m_strfilter) y [m_strSort](#m_strsort) miembros de datos.  
  
> [!NOTE]
>  Llame a esta función miembro solo después de llamar a **abiertos**.  
  
 Para obtener información relacionada, vea el tema "Propiedad de SQL" en la Ayuda de DAO.  
  
##  <a name="gettype"></a>  CDaoRecordset::GetType  
 Llame a esta función miembro después de abrir el conjunto de registros para determinar el tipo del objeto de conjunto de registros.  
  
```  
short GetType();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Uno de los siguientes valores que indica el tipo de un conjunto de registros:  
  
- **dbOpenTable** conjunto de registros de tipo de tabla  
  
- **dbOpenDynaset** registros de tipo dinámico  
  
- **dbOpenSnapshot** conjunto de registros de tipo de instantánea  
  
### <a name="remarks"></a>Comentarios  
 Para obtener información relacionada, vea el tema "Tipo de propiedad" en la Ayuda de DAO.  
  
##  <a name="getvalidationrule"></a>  CDaoRecordset::GetValidationRule  
 Llame a esta función miembro para determinar la regla usada para validar los datos.  
  
```  
CString GetValidationRule();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un `CString` objeto que contiene un valor que valida los datos en un registro cuando se cambia o se agrega a una tabla.  
  
### <a name="remarks"></a>Comentarios  
 Esta regla está basado en texto y se aplica cada vez que cambia la tabla subyacente. Si los datos no son válidos, MFC inicia una excepción. El mensaje de error devuelto es el texto de la propiedad de texto de validación del objeto campo subyacente, si se especifica, o el texto de la expresión especificada por la propiedad ValidationRule del objeto campo subyacente. Puede llamar a [GetValidationText](#getvalidationtext) para obtener el texto del mensaje de error.  
  
 Por ejemplo, un campo de un registro que requiera el día del mes podría tener una regla de validación como "día entre 1 y 31."  
  
 Para obtener información relacionada, vea el tema "Propiedad ValidationRule" en la Ayuda de DAO.  
  
##  <a name="getvalidationtext"></a>  CDaoRecordset::GetValidationText  
 Llame a esta función miembro para recuperar el texto de la propiedad de texto de validación del objeto de campo subyacente.  
  
```  
CString GetValidationText();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un `CString` objeto que contiene el texto del mensaje que se muestra si el valor de un campo no satisface la regla de validación del objeto de campo subyacente.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener información relacionada, vea el tema "Propiedad texto de validación" en la Ayuda de DAO.  
  
##  <a name="isbof"></a>  CDaoRecordset::IsBOF  
 Llame a esta función miembro antes de que se desplaza de registro a registro para obtener información sobre si ha realizado antes del primer registro del conjunto de registros.  
  
```  
BOOL IsBOF() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el conjunto de registros no contiene registros o si se ha desplazado hacia atrás delante del primer registro; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 También puede llamar a `IsBOF` junto con `IsEOF` para determinar si el conjunto de registros contiene todos los registros o está vacío. Inmediatamente después de llamar a **abiertos**, si el conjunto de registros no contiene registros, `IsBOF` devuelve es distinto de cero. Al abrir un conjunto de registros que tiene al menos un registro, el primer registro es el registro actual y `IsBOF` devuelve 0.  
  
 Si el primer registro es el registro actual y se llama `MovePrev`, `IsBOF` posteriormente devolverá es distinto de cero. Si `IsBOF` devuelve es distinto de cero y se llama a `MovePrev`, se produce una excepción. Si `IsBOF` devuelve es distinto de cero, el registro actual no está definido, y cualquier acción que requiere un registro actual se producirá una excepción.  
  
 Efecto de los métodos específicos en `IsBOF` y `IsEOF` configuración:  
  
-   Al llamar a **abiertos** internamente hace que el primer registro en el conjunto de registros el registro actual mediante una llamada a **MoveFirst**. Por lo tanto, al llamar a **abiertos** en un conjunto vacío de causas de registros `IsBOF` y `IsEOF` para devolver un valor distinto de cero. (Consulte la siguiente tabla para el comportamiento de un error **MoveFirst** o `MoveLast` llamar a.)  
  
-   Todas las operaciones de movimiento que se puede encontrar un registro hacen ambos `IsBOF` y `IsEOF` para devolver 0.  
  
-   Un `AddNew` llamada seguido por un **actualización** hará que la llamada que inserta correctamente un nuevo registro `IsBOF` para devolver 0, pero solo si `IsEOF` ya es distinto de cero. El estado de `IsEOF` siempre permanecerá sin cambios. Tal como se define por el motor de base de datos de Microsoft Jet, el puntero del registro actual de un conjunto de registros vacío es al final de un archivo, por lo que se inserta cualquier nuevo registro después del registro actual.  
  
-   Cualquier **eliminar** llamada, incluso si quita el registro restante solo de un conjunto de registros, no cambiará el valor de `IsBOF` o `IsEOF`.  
  
 Esta tabla muestra las operaciones de movimiento permitidas con diferentes combinaciones de `IsBOF` /  `IsEOF`.  
  
||MoveFirst, MoveLast|MovePrev,<br /><br /> Mover < 0|Mover 0|MoveNext,<br /><br /> Mover > 0|  
|------|-------------------------|-----------------------------|------------|-----------------------------|  
|`IsBOF`= distinto de cero,<br /><br /> `IsEOF`=0|Permitido|Excepción|Excepción|Permitido|  
|`IsBOF`=0,<br /><br /> `IsEOF`= es distinto de cero|Permitido|Permitido|Excepción|Excepción|  
|Ambos es distinto de cero|Excepción|Excepción|Excepción|Excepción|  
|0|Permitido|Permitido|Permitido|Permitido|  
  
 Permitir que una operación de movimiento no significa que la operación busque correctamente un registro. Simplemente indica que un intento de realizar la operación de desplazamiento especificada se puede y no generará una excepción. El valor de la `IsBOF` y `IsEOF` funciones miembro pueden cambiar como resultado del intento de move.  
  
 El efecto de las operaciones de movimiento que no se ubican en un registro en el valor de `IsBOF` y `IsEOF` configuración se muestra en la tabla siguiente.  
  
||IsBOF|IsEOF|  
|------|-----------|-----------|  
|**MoveFirst**, `MoveLast`|Es distinto de cero|Es distinto de cero|  
|**Mover** 0|No hay ningún cambio|No hay ningún cambio|  
|`MovePrev`, **Mover** < 0|Es distinto de cero|No hay ningún cambio|  
|`MoveNext`, **Mover** > 0|No hay ningún cambio|Es distinto de cero|  
  
 Para obtener información relacionada, vea el tema "BOF, EOF (propiedades)" en la Ayuda de DAO.  
  
##  <a name="isdeleted"></a>  CDaoRecordset::IsDeleted  
 Llame a esta función miembro para determinar si se ha eliminado el registro actual.  
  
```  
BOOL IsDeleted() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el conjunto de registros está situado en un registro eliminado; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 Si se desplaza a un registro y `IsDeleted` devuelve **TRUE** (distinto de cero,), a continuación, debe desplazar a otro registro para poder realizar otras operaciones de conjunto de registros.  
  
> [!NOTE]
>  No es necesario comprobar el estado eliminado de registros en un conjunto de registros de tipo de tabla o de instantáneas. Dado que no se puede eliminar registros de una instantánea, no es necesario llamar a `IsDeleted`. Para conjuntos de registros de tipo de tabla, los registros eliminados se quitan realmente del conjunto de registros. Una vez que se ha eliminado un registro, ya sea por parte del usuario, otro usuario, o en otro conjunto de registros, no es posible desplazarse hacia ese registro. Por lo tanto, no es necesario llamar a `IsDeleted`.  
  
 Cuando se elimina un registro de un conjunto de registros dinámicos, se quita del conjunto de registros y no se puede desplazar hacia ese registro. Sin embargo, si un registro en un conjunto de registros dinámicos se elimina por otro usuario o en otro conjunto de registros en función de la misma tabla, `IsDeleted` devolverá **TRUE** cuando más adelante desplazarse a ese registro.  
  
 Para obtener información relacionada, vea los temas "Método Delete", "Propiedad LastModified" y "Propiedad EditMode" en la Ayuda de DAO.  
  
##  <a name="iseof"></a>  CDaoRecordset::IsEOF  
 Llame a esta función miembro mientras se desplaza de registro a registro para obtener información sobre si ha ido más allá del último registro del conjunto de registros.  
  
```  
BOOL IsEOF() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el conjunto de registros no contiene registros o si se ha desplazado más allá del último registro; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 También puede llamar a `IsEOF` para determinar si el conjunto de registros contiene todos los registros o está vacío. Inmediatamente después de llamar a **abiertos**, si el conjunto de registros no contiene registros, `IsEOF` devuelve es distinto de cero. Al abrir un conjunto de registros que tiene al menos un registro, el primer registro es el registro actual y `IsEOF` devuelve 0.  
  
 Si el último registro es el registro actual cuando se llama a `MoveNext`, `IsEOF` posteriormente devolverá es distinto de cero. Si `IsEOF` devuelve es distinto de cero y se llama a `MoveNext`, se produce una excepción. Si `IsEOF` devuelve es distinto de cero, el registro actual no está definido, y cualquier acción que requiere un registro actual se producirá una excepción.  
  
 Efecto de los métodos específicos en `IsBOF` y `IsEOF` configuración:  
  
-   Al llamar a **abiertos** internamente hace que el primer registro en el conjunto de registros el registro actual mediante una llamada a **MoveFirst**. Por lo tanto, al llamar a **abiertos** en un conjunto vacío de causas de registros `IsBOF` y `IsEOF` para devolver un valor distinto de cero. (Consulte la siguiente tabla para el comportamiento de un error **MoveFirst** llamar a.)  
  
-   Todas las operaciones de movimiento que se puede encontrar un registro hacen ambos `IsBOF` y `IsEOF` para devolver 0.  
  
-   Un `AddNew` llamada seguido por un **actualización** hará que la llamada que inserta correctamente un nuevo registro `IsBOF` para devolver 0, pero solo si `IsEOF` ya es distinto de cero. El estado de `IsEOF` siempre permanecerá sin cambios. Tal como se define por el motor de base de datos de Microsoft Jet, el puntero del registro actual de un conjunto de registros vacío es al final de un archivo, por lo que se inserta cualquier nuevo registro después del registro actual.  
  
-   Cualquier **eliminar** llamada, incluso si quita el registro restante solo de un conjunto de registros, no cambiará el valor de `IsBOF` o `IsEOF`.  
  
 Esta tabla muestra las operaciones de movimiento permitidas con diferentes combinaciones de `IsBOF` /  `IsEOF`.  
  
||MoveFirst, MoveLast|MovePrev,<br /><br /> Mover < 0|Mover 0|MoveNext,<br /><br /> Mover > 0|  
|------|-------------------------|-----------------------------|------------|-----------------------------|  
|`IsBOF`= distinto de cero,<br /><br /> `IsEOF`=0|Permitido|Excepción|Excepción|Permitido|  
|`IsBOF`=0,<br /><br /> `IsEOF`= es distinto de cero|Permitido|Permitido|Excepción|Excepción|  
|Ambos es distinto de cero|Excepción|Excepción|Excepción|Excepción|  
|0|Permitido|Permitido|Permitido|Permitido|  
  
 Permitir que una operación de movimiento no significa que la operación busque correctamente un registro. Simplemente indica que un intento de realizar la operación de desplazamiento especificada se puede y no generará una excepción. El valor de la `IsBOF` y `IsEOF` funciones miembro pueden cambiar como resultado del intento de Move.  
  
 El efecto de las operaciones de movimiento que no se ubican en un registro en el valor de `IsBOF` y `IsEOF` configuración se muestra en la tabla siguiente.  
  
||IsBOF|IsEOF|  
|------|-----------|-----------|  
|**MoveFirst**, `MoveLast`|Es distinto de cero|Es distinto de cero|  
|**Mover** 0|No hay ningún cambio|No hay ningún cambio|  
|`MovePrev`, **Mover** < 0|Es distinto de cero|No hay ningún cambio|  
|`MoveNext`, **Mover** > 0|No hay ningún cambio|Es distinto de cero|  
  
 Para obtener información relacionada, vea el tema "BOF, EOF (propiedades)" en la Ayuda de DAO.  
  
##  <a name="isfielddirty"></a>  CDaoRecordset::IsFieldDirty  
 Llame a esta función miembro determinar si el miembro de datos del campo especificado de un conjunto de registros dinámicos se ha marcado como "modificados" (cambia).  
  
```  
BOOL IsFieldDirty(void* pv);
```  
  
### <a name="parameters"></a>Parámetros  
 `pv`  
 Un puntero a miembro de datos del campo cuyo estado desea comprobar, o **NULL** para determinar si cualquiera de los campos están desfasada.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el miembro de datos del campo especificado se marca como modificado; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 Los datos de todos los miembros de datos de campo modificados se transferirán al registro en el origen de datos cuando se actualiza el registro actual mediante una llamada a la **actualización** función miembro de `CDaoRecordset` (después de una llamada a **editar**o `AddNew`). Con este conocimiento, puede realizar más pasos, como quitar marcadores el miembro de datos de campo para marcar la columna, por lo que no se escribirán en el origen de datos.  
  
 `IsFieldDirty` se implementa a través de `DoFieldExchange`.  
  
##  <a name="isfieldnull"></a>  CDaoRecordset::IsFieldNull  
 Llame a esta función miembro para determinar si el miembro de datos del campo especificado de un conjunto de registros se ha marcado como Null.  
  
```  
BOOL IsFieldNull(void* pv);
```  
  
### <a name="parameters"></a>Parámetros  
 `pv`  
 Un puntero a miembro de datos del campo cuyo estado desea comprobar, o **NULL** para determinar si cualquiera de los campos son Null.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el miembro de datos del campo especificado se marca como Null; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 (En la terminología de base de datos, Null significa "no having ningún valor" y no es igual a **NULL** en C++.) Si un miembro de datos de campo se marca como Null, se interpreta como una columna del registro actual para el que no hay ningún valor.  
  
> [!NOTE]
>  En determinadas situaciones, mediante `IsFieldNull` puede ser ineficaz, como se muestra en el ejemplo de código siguiente:  
  
 [!code-cpp[NVC_MFCDatabase#5](../../mfc/codesnippet/cpp/cdaorecordset-class_5.cpp)]  
  
> [!NOTE]
>  Si se utiliza un enlace de registro dinámico, sin tener que derivar de `CDaoRecordset`, asegúrese de usar **VT_NULL** tal como se muestra en el ejemplo.  
  
##  <a name="isfieldnullable"></a>  CDaoRecordset::IsFieldNullable  
 Llame a esta función miembro determinar si el miembro de datos del campo especificado es "que aceptan valores null" (se pueden establecer en un valor Null; C++ **NULL** no es igual a Null, lo que, en la terminología de base de datos, significa "no having ningún valor").  
  
```  
BOOL IsFieldNullable(void* pv);
```  
  
### <a name="parameters"></a>Parámetros  
 `pv`  
 Un puntero a miembro de datos del campo cuyo estado desea comprobar, o **NULL** para determinar si cualquiera de los campos son Null.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el miembro de datos del campo especificado se puede establecer es Null; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 Un campo que no puede ser Null debe tener un valor. Si se intenta establecer este tipo de campo como Null al agregar o actualizar un registro, el origen de datos rechaza la adición o la actualización, y **actualizar** se iniciará una excepción. La excepción se produce cuando se llama a **actualización**, no cuando se llama a `SetFieldNull`.  
  
##  <a name="isopen"></a>  CDaoRecordset::IsOpen  
 Llame a esta función miembro para determinar si el conjunto de registros está abierto.  
  
```  
BOOL IsOpen() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el objeto de conjunto de registros **abiertos** o **Requery** función miembro se ha llamado anteriormente y el conjunto de registros no se ha cerrado; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="m_bcheckcachefordirtyfields"></a>  CDaoRecordset:: M_bcheckcachefordirtyfields  
 Contiene una marca que indica si los campos almacenados en memoria caché se marcan automáticamente como desfasadas (modificados) y Null.  
  
### <a name="remarks"></a>Comentarios  
 Tiene como valor predeterminado de la marca a **TRUE**. La configuración de este miembro de datos controla todo el mecanismo de almacenamiento en búfer doble. Si la marca se establece en **TRUE**, puede desactivar el almacenamiento en caché en forma de campo a campo mediante el mecanismo DFX. Si la marca se establece en **FALSE**, debe llamar a `SetFieldDirty` y `SetFieldNull` usted mismo.  
  
 Establecer este miembro de datos antes de llamar a **abiertos**. Este mecanismo es principalmente para la facilidad de uso. Rendimiento puede ser más lento debido a que el búfer doble de los campos cuando se realizan cambios.  
  
##  <a name="m_nfields"></a>  CDaoRecordset::m_nFields  
 Contiene el número de miembros de datos de campo en la clase de conjunto de registros y el número de columnas seleccionadas por el conjunto de registros desde el origen de datos.  
  
### <a name="remarks"></a>Comentarios  
 Debe inicializar el constructor de la clase de conjunto de registros `m_nFields` con el número correcto de campos enlazados estáticamente. ClassWizard escribe esta inicialización cuando se usa para declarar la clase de conjunto de registros. También puede escribir manualmente.  
  
 El marco de trabajo utiliza este número para administrar la interacción entre los miembros de datos de campo y las columnas correspondientes del registro actual en el origen de datos.  
  
> [!NOTE]
>  Este número debe coincidir con el número de columnas de salida registrado en `DoFieldExchange` después de llamar a `SetFieldType` con el parámetro **CDaoFieldExchange:: outputColumn**.  
  
 Puede enlazar columnas dinámicamente por medio de `CDaoRecordset::GetFieldValue` y `CDaoRecordset::SetFieldValue`. Si lo hace, no es necesario incrementar el recuento de `m_nFields` para reflejar el número de función DFX llama su `DoFieldExchange` función miembro.  
  
##  <a name="m_nparams"></a>  CDaoRecordset::m_nParams  
 Contiene el número de miembros de datos de parámetro en la clase de conjunto de registros: el número de parámetros pasados con la consulta del conjunto de registros.  
  
### <a name="remarks"></a>Comentarios  
 Si la clase de conjunto de registros tiene los miembros de datos de parámetro, debe inicializar el constructor de la clase `m_nParams` con el número correcto. El valor de `m_nParams` el valor predeterminado es 0. Si agrega miembros de datos de parámetro, lo que debe realizar manualmente, también debe agregar manualmente una inicialización en el constructor de clase para reflejar el número de parámetros (que debe ser al menos tan grande como el número de '' marcadores de posición en su **m_strFilter**  o `m_strSort` cadena).  
  
 El marco de trabajo utiliza este número cuando parametriza la consulta del conjunto de registros.  
  
> [!NOTE]
>  Este número debe coincidir con el número de "parámetros" registrados en `DoFieldExchange` después de llamar a `SetFieldType` con el parámetro **CFieldExchange::param**.  
  
 Para obtener información relacionada, vea el tema "Objeto de parámetro" en la Ayuda de DAO.  
  
##  <a name="m_pdaorecordset"></a>  CDaoRecordset::m_pDAORecordset  
 Contiene un puntero a la interfaz OLE para el objeto de conjunto de registros DAO subyacente la `CDaoRecordset` objeto.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este puntero si necesita acceso directo a la interfaz DAO.  
  
 Para obtener información relacionada, vea el tema "Recordset (objeto)" en la Ayuda de DAO.  
  
##  <a name="m_pdatabase"></a>  CDaoRecordset::m_pDatabase  
 Contiene un puntero a la `CDaoDatabase` objeto a través del cual el conjunto de registros está conectado a un origen de datos.  
  
### <a name="remarks"></a>Comentarios  
 Esta variable se establece de dos maneras. Por lo general, pasar un puntero a una ya está abierto `CDaoDatabase` objeto cuando se construya el objeto de conjunto de registros. Si se pasa **NULL** en su lugar, **CDaoRecordset** crea un `CDaoDatabase` objeto automáticamente y lo abre. En cualquier caso, `CDaoRecordset` almacena el puntero en esta variable.  
  
 Normalmente no directamente debe usar el puntero almacenado en **m_pDatabase**. Si escribe sus propias extensiones al `CDaoRecordset`, sin embargo, deberá utilizar el puntero. Por ejemplo, podría necesitar el puntero si se produce su propio `CDaoException`(s).  
  
 Para obtener información relacionada, vea el tema "Objeto de base de datos" en la Ayuda de DAO.  
  
##  <a name="m_strfilter"></a>  CDaoRecordset:: M_strfilter  
 Contiene una cadena que se usa para construir la **donde** cláusula de una instrucción SQL.  
  
### <a name="remarks"></a>Comentarios  
 No incluye la palabra reservada **donde** para filtrar el conjunto de registros. El uso de este miembro de datos no es aplicable a los conjuntos de registros de tipo de tabla. El uso de **m_strFilter** no tiene ningún efecto al abrir un conjunto de registros utilizando un `CDaoQueryDef` puntero.  
  
 Utilice el formato de fecha de Estados Unidos (mes-año) cuando se filtran los campos que contienen fechas, incluso si no usa la versión de Estados Unidos del motor de base de datos de Microsoft Jet; en caso contrario, no se pueden filtrar los datos tal y como esperaba.  
  
 Para obtener información relacionada, vea el tema "Propiedad de filtro" en la Ayuda de DAO.  
  
##  <a name="m_strsort"></a>  CDaoRecordset::m_strSort  
 Contiene una cadena que contiene el **ORDERBY** cláusula de una instrucción SQL sin las palabras reservadas **ORDERBY**.  
  
### <a name="remarks"></a>Comentarios  
 Puede ordenar en objetos de conjunto de registros de tipo dynaset y snapshot.  
  
 No se puede ordenar los objetos de conjunto de registros de tipo de tabla. Para determinar el criterio de ordenación de un conjunto de registros de tipo de tabla, llame a [SetCurrentIndex](#setcurrentindex).  
  
 El uso de `m_strSort` no tiene ningún efecto al abrir un conjunto de registros utilizando un `CDaoQueryDef` puntero.  
  
 Para obtener información relacionada, vea el tema "Propiedad de ordenación" en la Ayuda de DAO.  
  
##  <a name="move"></a>  CDaoRecordset:: Move  
 Llame a esta función miembro para colocar el conjunto de registros `lRows` registros desde el registro actual.  
  
```  
virtual void Move(long lRows);
```  
  
### <a name="parameters"></a>Parámetros  
 `lRows`  
 El número de registros para desplazarse hacia delante o hacia atrás. Los valores positivos desplazarse hacia delante, hacia el final del conjunto de registros. Los valores negativos hacia atrás, mover hacia el principio.  
  
### <a name="remarks"></a>Comentarios  
 Puede mover hacia delante o hacia atrás. `Move( 1 )` es equivalente a `MoveNext`, y `Move( -1 )` es equivalente a `MovePrev`.  
  
> [!CAUTION]
>  Llamar a cualquiera de los **mover** funciones produce una excepción si el conjunto de registros no tiene registros. En general, llamar a `IsBOF` y `IsEOF` antes de una operación de movimiento para determinar si el conjunto de registros tiene los registros. Después de llamar a **abiertos** o **Requery**, llame a `IsBOF` o `IsEOF`.  
  
> [!NOTE]
>  Si se ha desplazado más allá del principio o al final del conjunto de registros ( `IsBOF` o `IsEOF` devuelve un valor distinto de cero), una llamada a **mover** produce una `CDaoException`.  
  
> [!NOTE]
>  Si se llama a cualquiera de los **mover** funciona mientras el registro actual se actualiza o agregado, las actualizaciones se pierden sin previo aviso.  
  
 Cuando se llama a **mover** en una instantánea con desplazamiento solo hacia delante, la `lRows` parámetro debe ser un entero positivo y no se permiten marcadores, por lo que puede desplazarse hacia delante solo.  
  
 Para hacer que el primero, último, siguiente o anterior grabar en un conjunto de registros de la llamada actual de registros, la **MoveFirst**, `MoveLast`, `MoveNext`, o `MovePrev` función miembro.  
  
 Para obtener información relacionada, vea los temas "Método Move" y "MoveFirst, MoveLast, MoveNext, MovePrevious métodos" en la Ayuda de DAO.  
  
##  <a name="movefirst"></a>  CDaoRecordset::MoveFirst  
 Llame a esta función miembro para realizar el primer registro en el conjunto de registros (si existe) del registro actual.  
  
```  
void MoveFirst();
```  
  
### <a name="remarks"></a>Comentarios  
 No es necesario llamar a **MoveFirst** inmediatamente después de abrir el conjunto de registros. En ese momento, el primer registro (si existe) es automáticamente el registro actual.  
  
> [!CAUTION]
>  Llamar a cualquiera de los **mover** funciones produce una excepción si el conjunto de registros no tiene registros. En general, llamar a `IsBOF` y `IsEOF` antes de una operación de movimiento para determinar si el conjunto de registros tiene los registros. Después de llamar a **abiertos** o **Requery**, llame a `IsBOF` o `IsEOF`.  
  
> [!NOTE]
>  Si se llama a cualquiera de los **mover** funciona mientras el registro actual se actualiza o agregado, las actualizaciones se pierden sin previo aviso.  
  
 Use la **mover** funciones para desplazarse de un registro a otro sin aplicar una condición. Utilice las operaciones de búsqueda para localizar los registros en un tipo de conjunto de registros dinámicos u objeto de conjunto de registros de tipo de instantánea que cumplen una condición determinada. Para buscar un registro en un objeto de conjunto de registros de tipo de tabla, llame a `Seek`.  
  
 Si el conjunto de registros hace referencia a un conjunto de registros de tipo de tabla, el desplazamiento sigue índice actual de la tabla. Puede establecer el índice actual mediante la propiedad de índice del objeto DAO subyacente. Si no establece el índice actual, el orden de los registros devueltos es indefinido.  
  
 Si se llama a `MoveLast` en un objeto de conjunto de registros basado en una consulta SQL o la definición de consulta, la consulta se ve obligada a finalizar y el objeto de conjunto de registros esté completa.  
  
 No se puede llamar el **MoveFirst** o `MovePrev` función miembro con una instantánea de desplazamiento solo hacia delante.  
  
 Para mover la posición del elemento actual registro de un objeto de conjunto de registros de un determinado número de registros hacia delante o hacia atrás, llame a **mover**.  
  
 Para obtener información relacionada, vea los temas "Método Move" y "MoveFirst, MoveLast, MoveNext, MovePrevious métodos" en la Ayuda de DAO.  
  
##  <a name="movelast"></a>  CDaoRecordset::MoveLast  
 Llame a esta función miembro para realizar el último registro (si existe) en el conjunto de registros, el registro actual.  
  
```  
void MoveLast();
```  
  
### <a name="remarks"></a>Comentarios  
  
> [!CAUTION]
>  Llamar a cualquiera de los **mover** funciones produce una excepción si el conjunto de registros no tiene registros. En general, llamar a `IsBOF` y `IsEOF` antes de una operación de movimiento para determinar si el conjunto de registros tiene los registros. Después de llamar a **abiertos** o **Requery**, llame a `IsBOF` o `IsEOF`.  
  
> [!NOTE]
>  Si se llama a cualquiera de los **mover** funciona mientras el registro actual se actualiza o agregado, las actualizaciones se pierden sin previo aviso.  
  
 Use la **mover** funciones para desplazarse de un registro a otro sin aplicar una condición. Utilice las operaciones de búsqueda para localizar los registros en un tipo de conjunto de registros dinámicos u objeto de conjunto de registros de tipo de instantánea que cumplen una condición determinada. Para buscar un registro en un objeto de conjunto de registros de tipo de tabla, llame a `Seek`.  
  
 Si el conjunto de registros hace referencia a un conjunto de registros de tipo de tabla, el desplazamiento sigue índice actual de la tabla. Puede establecer el índice actual mediante la propiedad de índice del objeto DAO subyacente. Si no establece el índice actual, el orden de los registros devueltos es indefinido.  
  
 Si se llama a `MoveLast` en un objeto de conjunto de registros basado en una consulta SQL o la definición de consulta, la consulta se ve obligada a finalizar y el objeto de conjunto de registros esté completa.  
  
 Para mover la posición del elemento actual registro de un objeto de conjunto de registros de un determinado número de registros hacia delante o hacia atrás, llame a **mover**.  
  
 Para obtener información relacionada, vea los temas "Método Move" y "MoveFirst, MoveLast, MoveNext, MovePrevious métodos" en la Ayuda de DAO.  
  
##  <a name="movenext"></a>  CDaoRecordset::MoveNext  
 Llame a esta función miembro para realizar el registro siguiente en el registro actual del conjunto de registros.  
  
```  
void MoveNext();
```  
  
### <a name="remarks"></a>Comentarios  
 Se recomienda llamar a `IsBOF` antes de intentar mover al registro anterior. Una llamada a `MovePrev` producirá un `CDaoException` si `IsBOF` devuelve distinto de cero, que indica que ya se haya desplazado delante del primer registro o que no se seleccionaron registros por el conjunto de registros.  
  
> [!CAUTION]
>  Llamar a cualquiera de los **mover** funciones produce una excepción si el conjunto de registros no tiene registros. En general, llamar a `IsBOF` y `IsEOF` antes de una operación de movimiento para determinar si el conjunto de registros tiene los registros. Después de llamar a **abiertos** o **Requery**, llame a `IsBOF` o `IsEOF`.  
  
> [!NOTE]
>  Si se llama a cualquiera de los **mover** funciona mientras el registro actual se actualiza o agregado, las actualizaciones se pierden sin previo aviso.  
  
 Use la **mover** funciones para desplazarse de un registro a otro sin aplicar una condición. Utilice las operaciones de búsqueda para localizar los registros en un tipo de conjunto de registros dinámicos u objeto de conjunto de registros de tipo de instantánea que cumplen una condición determinada. Para buscar un registro en un objeto de conjunto de registros de tipo de tabla, llame a `Seek`.  
  
 Si el conjunto de registros hace referencia a un conjunto de registros de tipo de tabla, el desplazamiento sigue índice actual de la tabla. Puede establecer el índice actual mediante la propiedad de índice del objeto DAO subyacente. Si no establece el índice actual, el orden de los registros devueltos es indefinido.  
  
 Para mover la posición del elemento actual registro de un objeto de conjunto de registros de un determinado número de registros hacia delante o hacia atrás, llame a **mover**.  
  
 Para obtener información relacionada, vea los temas "Método Move" y "MoveFirst, MoveLast, MoveNext, MovePrevious métodos" en la Ayuda de DAO.  
  
##  <a name="moveprev"></a>  CDaoRecordset::MovePrev  
 Llame a esta función miembro para realizar el registro anterior en el conjunto de registros, el registro actual.  
  
```  
void MovePrev();
```  
  
### <a name="remarks"></a>Comentarios  
 Se recomienda llamar a `IsBOF` antes de intentar mover al registro anterior. Una llamada a `MovePrev` producirá un `CDaoException` si `IsBOF` devuelve distinto de cero, que indica que ya se haya desplazado delante del primer registro o que no se seleccionaron registros por el conjunto de registros.  
  
> [!CAUTION]
>  Llamar a cualquiera de los **mover** funciones produce una excepción si el conjunto de registros no tiene registros. En general, llamar a `IsBOF` y `IsEOF` antes de una operación de movimiento para determinar si el conjunto de registros tiene los registros. Después de llamar a **abiertos** o **Requery**, llame a `IsBOF` o `IsEOF`.  
  
> [!NOTE]
>  Si se llama a cualquiera de los **mover** funciona mientras el registro actual se actualiza o agregado, las actualizaciones se pierden sin previo aviso.  
  
 Use la **mover** funciones para desplazarse de un registro a otro sin aplicar una condición. Utilice las operaciones de búsqueda para localizar los registros en un tipo de conjunto de registros dinámicos u objeto de conjunto de registros de tipo de instantánea que cumplen una condición determinada. Para buscar un registro en un objeto de conjunto de registros de tipo de tabla, llame a `Seek`.  
  
 Si el conjunto de registros hace referencia a un conjunto de registros de tipo de tabla, el desplazamiento sigue índice actual de la tabla. Puede establecer el índice actual mediante la propiedad de índice del objeto DAO subyacente. Si no establece el índice actual, el orden de los registros devueltos es indefinido.  
  
 No se puede llamar el **MoveFirst** o `MovePrev` función miembro con una instantánea de desplazamiento solo hacia delante.  
  
 Para mover la posición del elemento actual registro de un objeto de conjunto de registros de un determinado número de registros hacia delante o hacia atrás, llame a **mover**.  
  
 Para obtener información relacionada, vea los temas "Método Move" y "MoveFirst, MoveLast, MoveNext, MovePrevious métodos" en la Ayuda de DAO.  
  
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
 `nOpenType`  
 Uno de los siguientes valores:  
  
- **dbOpenDynaset** un conjunto de registros de tipo dynaset con desplazamiento bidireccional. Este es el valor predeterminado.  
  
- **dbOpenTable** un conjunto de registros de tipo de tabla con desplazamiento bidireccional.  
  
- **dbOpenSnapshot** un conjunto de registros de tipo instantánea con desplazamiento bidireccional.  
  
 `lpszSQL`  
 Puntero de cadena que contiene uno de los elementos siguientes:  
  
-   A **NULL** puntero.  
  
-   El nombre de una o más definiciones de tabla y/o querydefs (separados por comas).  
  
-   Una instancia de SQL **seleccione** instrucción (opcionalmente con una instancia de SQL **donde** o **ORDERBY** cláusula).  
  
-   Una consulta de paso.  
  
 `nOptions`  
 Uno o más de las siguientes opciones. El valor predeterminado es 0. Los valores posibles son los siguientes:  
  
- **dbAppendOnly** sólo se pueden anexar nuevos registros (solo registros de tipo dinámico). Esta opción significa literalmente que solo se pueden anexar los registros. Las clases de base de datos ODBC de MFC tienen una opción de sólo anexar que permite que los registros que recuperan y anexar.  
  
- **dbForwardOnly** el conjunto de registros es una instantánea de desplazamiento solo hacia delante.  
  
- **dbSeeChanges** generará una excepción si otro usuario está cambiando los datos que se va a editar.  
  
- **dbDenyWrite** no se pueden modificar o agregar registros de otros usuarios.  
  
- **dbDenyRead** otros usuarios no pueden ver los registros (solo conjunto de registros de tipo de tabla).  
  
- **dbReadOnly** sólo puede ver los registros; otros usuarios pueden modificarlos.  
  
- **dbInconsistent** se permiten actualizaciones incoherentes (solo registros de tipo dinámico).  
  
- **dbConsistent** solo se permiten actualizaciones coherentes (solo registros de tipo dinámico).  
  
> [!NOTE]
>  Las constantes **dbConsistent** y **dbInconsistent** son mutuamente excluyentes. Puede usar uno o el otro, pero no ambas en una instancia determinada de **abiertos**.  
  
 *pTableDef*  
 Un puntero a un [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md) objeto. Esta versión es válida únicamente para los conjuntos de registros de tipo de tabla. Cuando se usa esta opción, el `CDaoDatabase` puntero utilizado para construir el `CDaoRecordset` no se utiliza; en su lugar, se utiliza la base de datos en el que reside la definición de tabla.  
  
 *pQueryDef*  
 Un puntero a un [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md) objeto. Esta versión es válida únicamente para el tipo de conjunto de registros dinámicos y conjuntos de registros de tipo de instantánea. Cuando se usa esta opción, el `CDaoDatabase` puntero utilizado para construir el `CDaoRecordset` no se utiliza; en su lugar, se utiliza la base de datos en el que reside la definición de consulta.  
  
### <a name="remarks"></a>Comentarios  
 Antes de llamar a **abiertos**, debe crear el objeto de conjunto de registros. Existen varias formas de hacerlo:  
  
-   Cuando se crea el objeto de conjunto de registros, puede pasar un puntero a un `CDaoDatabase` objeto que ya está abierto.  
  
-   Cuando se crea el objeto de conjunto de registros, puede pasar un puntero a un `CDaoDatabase` objeto que no está abierto. El conjunto de registros se abre un `CDaoDatabase` de objeto, pero no se cierre cuando se cierra el objeto de conjunto de registros.  
  
-   Cuando se crea el objeto de conjunto de registros, pasar un **NULL** puntero. Las llamadas del objeto de conjunto de registros `GetDefaultDBName` para obtener el nombre de Microsoft Access. Archivo de Microsoft Access que se abre. El conjunto de registros, a continuación, se abre un `CDaoDatabase` objeto y mantiene y abrirlo siempre que el conjunto de registros está abierto. Cuando se llama a **cerrar** en el conjunto de registros, la `CDaoDatabase` también se cierra el objeto.  
  
    > [!NOTE]
    >  Cuando se abre el conjunto de registros el `CDaoDatabase` de objeto, se abre el origen de datos con acceso no exclusivo.  
  
 Para la versión de **abrir** que usa el `lpszSQL` parámetro, una vez abierto el conjunto de registros puede recuperar registros de varias maneras. La primera opción es que las funciones DFX su `DoFieldExchange`. La segunda opción consiste en usar el enlace dinámico mediante una llamada a la `GetFieldValue` función miembro. Estas opciones se pueden implementar por separado o en combinación. Si se combinan, tendrá que pasar en la instrucción SQL por sí mismo en la llamada a **abiertos**.  
  
 Cuando se usa la segunda versión de **abiertos** donde se pasa un `CDaoTableDef` de objetos, las columnas resultantes estará disponibles para enlazar a través de `DoFieldExchange` y el mecanismo DFX, o enlace dinámicamente mediante `GetFieldValue`.  
  
> [!NOTE]
>  Solo se puede llamar a **abiertos** mediante un `CDaoTableDef` objeto para conjuntos de registros de tipo de tabla.  
  
 Cuando se usa la tercera versión de **abiertos** donde se pasa un `CDaoQueryDef` de objeto, que se ejecutará la consulta y las columnas resultantes estará disponibles para enlazar a través de `DoFieldExchange` y el mecanismo DFX, o enlazar dinámicamente a través de `GetFieldValue`.  
  
> [!NOTE]
>  Solo se puede llamar a **abiertos** mediante un `CDaoQueryDef` objeto para el tipo de conjunto de registros dinámicos y conjuntos de registros de tipo de instantánea.  
  
 Para la primera versión de **abiertos** que usa el `lpszSQL` parámetro, los registros son los criterios seleccionados según se muestra en la tabla siguiente.  
  
|Valor del parámetro `lpszSQL`|Los registros seleccionados están determinados por|Ejemplo|  
|--------------------------------------|----------------------------------------|-------------|  
|**NULL**|La cadena devuelta por `GetDefaultSQL`.||  
|Una lista separada por comas de uno o más definiciones de tabla o nombres de definición de consulta.|Todas las columnas se representan en el `DoFieldExchange`.|`"Customer"`|  
|**Seleccione** lista de columnas **FROM** lista de tablas|Las columnas especificadas del querydef(s) y/o tabledef(s) especificado.|`"SELECT CustId, CustName`<br /><br /> `FROM Customer"`|  
  
 El procedimiento habitual consiste en pasar **NULL** a **abiertos**; en ese caso, **abiertos** llamadas `GetDefaultSQL`, una función de miembro reemplazables que genera el asistente al crear un `CDaoRecordset`-clase derivada. Este valor proporciona los nombres de tabledef(s) o definición de consulta que especificó en el Asistente para. Se puede especificar otra información en el parámetro `lpszSQL`.  
  
 Cualquier valor que pase, **abrir** construye una cadena SQL final para la consulta (la cadena puede tener SQL **donde** y **ORDERBY** anexadas cláusulas a la `lpszSQL` cadena que se pasa) y, a continuación, ejecuta la consulta. Puede examinar la cadena construida mediante una llamada a `GetSQL` después de llamar a **abiertos**.  
  
 Los miembros de datos de campo de la clase de conjunto de registros están enlazados a las columnas de los datos seleccionados. Si se devuelve algún registro, el primer registro se convierte en el registro actual.  
  
 Si desea establecer opciones para el conjunto de registros, por ejemplo, un filtro o una ordenación, establezca `m_strSort` o **m_strFilter** después de crear el objeto de conjunto de registros, pero antes de llamar a **abiertos**. Si desea que los registros del conjunto de registros después de actualizar el conjunto de registros está abierto, llame a **Requery**.  
  
 Si se llama a **abiertos** en un tipo de conjunto de registros dinámicos o un conjunto de registros de tipo de instantánea, o si el origen de datos hace referencia a una instrucción SQL o una definición de tabla que representa una tabla asociada, no se puede usar **dbOpenTable** para el tipo argumento; Si lo hace, MFC inicia una excepción. Para determinar si un objeto de definición de tabla representa una tabla asociada, cree una [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md) objeto y llame a su [GetConnect](../../mfc/reference/cdaotabledef-class.md#getconnect) función miembro.  
  
 Use la **dbSeeChanges** marcar si desea volver a capturar los cambios realizados por otro usuario u otro programa en su equipo cuando está modificando o eliminando el registro de la mismo. Por ejemplo, si dos usuarios comenzar a editar el mismo registro, el primer usuario que llame a la **actualización** función miembro se realiza correctamente. Cuando **actualización** llama el segundo usuario, un `CDaoException` se produce. De forma similar, si el segundo usuario intenta llamar a **eliminar** eliminar el registro y ya ha cambiado el primer usuario, un `CDaoException` se produce.  
  
 Por lo general, si el usuario obtiene este `CDaoException` durante la actualización, el código debe actualizar el contenido de los campos y recuperar los valores recién modificados. Si se produce la excepción en el proceso de eliminación, el código puede mostrar los datos de registro nuevo para el usuario y un mensaje que indica que los datos han cambiado recientemente. En este momento, el código puede solicitar una confirmación de que el usuario aún desea eliminar el registro.  
  
> [!TIP]
>  Utilice la opción de desplazamiento solo hacia delante ( **dbForwardOnly**) mejorar el rendimiento cuando la aplicación realiza un único paso a través de un conjunto de registros abierto de un origen de datos ODBC.  
  
 Para obtener información relacionada, vea el tema "Método OpenRecordset" en la Ayuda de DAO.  
  
##  <a name="requery"></a>  CDaoRecordset::Requery  
 Llame a esta función miembro para volver a generar (actualizar) un conjunto de registros.  
  
```  
virtual void Requery();
```  
  
### <a name="remarks"></a>Comentarios  
 Si se devuelve algún registro, el primer registro se convierte en el registro actual.  
  
 En orden para el conjunto de registros reflejar las adiciones y eliminaciones realizados por usted u otros usuarios en el origen de datos, debe volver a crear el conjunto de registros mediante una llamada a **Requery**. Si el conjunto de registros es un conjunto de registros dinámicos, refleja automáticamente las actualizaciones que usted u otros usuarios realicen en sus registros existentes (pero no las adiciones). Si el conjunto de registros es una instantánea, debe llamar a **Requery** para reflejar modificaciones realizadas por otros usuarios, así como las adiciones y eliminaciones.  
  
 Para un conjunto de registros dinámicos o en una instantánea, llame a **Requery** siempre que desee volver a generar el conjunto de registros con valores de parámetros. Establezca el filtro o una ordenación estableciendo [m_strFilter](#m_strfilter) y [m_strSort](#m_strsort) antes de llamar a **Requery**. Definir nuevos parámetros asignando nuevos valores a los miembros de datos de parámetro antes de llamar a **Requery**.  
  
 Si se produce un error en el intento de volver a generar el conjunto de registros, se cierra el conjunto de registros. Antes de llamar a **Requery**, puede determinar si el conjunto de registros puede realizar una nueva consulta mediante una llamada a la [CanRestart](#canrestart) función miembro. `CanRestart` no garantiza que **Requery** se realizará correctamente.  
  
> [!CAUTION]
>  Llame a **Requery** sólo después de haber llamado **abiertos**.  
  
> [!NOTE]
>  Al llamar a [Requery](#requery) cambia marcadores DAO.  
  
 No se puede llamar **Requery** en un tipo de conjunto de registros dinámicos o un conjunto de registros de tipo snapshot si una llamada a `CanRestart` devuelve 0, ni puede usarla en un conjunto de registros de tipo de tabla.  
  
 Si ambos `IsBOF` y `IsEOF` devolver es distinto de cero después de llamar a **Requery**, la consulta no devolvió ningún registro y el conjunto de registros no contendrá ningún dato.  
  
 Para obtener información relacionada, vea el tema "Requery (método)" en la Ayuda de DAO.  
  
##  <a name="seek"></a>  CDaoRecordset::Seek  
 Llame a esta función miembro para ubicar el registro de un objeto de conjunto de registros de tipo tabla indizada que satisface los criterios especificados para el actual de índice y convierte ese registro en el registro actual.  
  
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
 `lpszComparison`  
 Una de las siguientes expresiones de cadena: "<","\<=", "=", "> =", o ">".  
  
 `pKey1`  
 Un puntero a un [COleVariant](../../mfc/reference/colevariant-class.md) cuyo valor corresponde al primer campo en el índice. Requerido.  
  
 *pKey2*  
 Un puntero a un `COleVariant` cuyo valor se corresponde con el segundo campo en el índice, si existe. Valor predeterminado es **NULL**.  
  
 *pKey3*  
 Un puntero a un `COleVariant` cuyo valor corresponde al tercer campo en el índice, si existe. Valor predeterminado es **NULL**.  
  
 *pKeyArray*  
 Un puntero a una matriz de variantes. El tamaño de la matriz corresponde al número de campos en el índice.  
  
 *nKeys*  
 Un entero correspondiente al tamaño de la matriz, que es el número de campos en el índice.  
  
> [!NOTE]
>  No se especifican caracteres comodín en las claves. Hará que los caracteres comodín `Seek` para no devolver tienen registros coincidentes.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si no se encuentra registros coincidentes, 0 en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 Use la segunda versión (matriz) de `Seek` administrar índices de cuatro campos o más.  
  
 `Seek` permite buscar en conjuntos de registros de tipo de tabla de índice de alto rendimiento. Debe establecer el índice actual mediante una llamada a `SetCurrentIndex` antes de llamar a `Seek`. Si el índice identifica un único campo o campos clave, `Seek` localiza el primer registro que satisface los criterios. Si no establece un índice, se produce una excepción.  
  
 Tenga en cuenta que si no va a crear un conjunto de registros UNICODE, el `COleVariant` objetos se deben declarar explícitamente ANSI. Esto puede hacerse mediante el uso de la [COleVariant::COleVariant](../../mfc/reference/colevariant-class.md#colevariant)**(** `lpszSrc` **,** `vtSrc` **)** forma de constructor con `vtSrc` establecido en `VT_BSTRT` (ANSI) o mediante el **COleVariant** función [SetString](../../mfc/reference/colevariant-class.md#setstring)**(** `lpszSrc` **,** `vtSrc` **)** con `vtSrc` establecido en `VT_BSTRT`.  
  
 Cuando se llama a `Seek`, pasar uno o más valores de clave y un operador de comparación ("<","\<=", "=", "> =", o ">"). `Seek` busca en los campos de clave especificados y localiza el primer registro que satisface los criterios especificados por `lpszComparison` y `pKey1`. Una vez encontrado, `Seek` devuelve es distinto de cero y hace que dicho registro actual. Si `Seek` se produce un error al intentar buscar una coincidencia, `Seek` devuelve cero y el registro actual es indefinido. Al utilizar DAO directamente, debe comprobar explícitamente la propiedad NoMatch.  
  
 Si `lpszComparison` es "=", "> =", o ">", `Seek` comienza al principio del índice. Si `lpszComparison` es "<" o "< =", `Seek` se inicia al final del índice y busca hacia atrás a menos que haya entradas de índice duplicadas al final. En este caso, `Seek` comienza en una entrada arbitraria entre las entradas de índice duplicadas al final del índice.  
  
 No existe no tiene que ser un registro actual cuando se utiliza `Seek`.  
  
 Para buscar un registro en un tipo de conjunto de registros dinámicos o un conjunto de registros de tipo snapshot que satisface una condición específica, utilice las operaciones de búsqueda. Para incluir todos los registros, no solo aquéllos que cumplen una condición específica, utilice las operaciones de desplazamiento para desplazarse por los registros.  
  
 No se puede llamar a `Seek` en una tabla asociada de cualquier tipo porque tablas asociadas deben abrirse como conjuntos de registros de tipo de instantánea o un tipo de conjunto de registros dinámicos. Sin embargo, si se llama a `CDaoDatabase::Open` para abrir directamente una base de datos ISAM instalable, puede llamar a `Seek` en las tablas de esa base de datos, aunque el rendimiento puede ser lenta.  
  
 Para obtener información relacionada, vea el tema "Método Seek" en la Ayuda de DAO.  
  
##  <a name="setabsoluteposition"></a>  CDaoRecordset:: SetAbsolutePosition  
 Establece el número de registro relativo del registro actual del objeto de conjunto de registros.  
  
```  
void SetAbsolutePosition(long lPosition);
```  
  
### <a name="parameters"></a>Parámetros  
 *lPosition*  
 Corresponde a la posición ordinal del registro actual en el conjunto de registros.  
  
### <a name="remarks"></a>Comentarios  
 Al llamar a `SetAbsolutePosition` le permite colocar el puntero de registro actual en un registro específico en función de su posición ordinal en un tipo de conjunto de registros dinámicos o un conjunto de registros de tipo de instantánea. También puede determinar el número de registro actual mediante una llamada a [GetAbsolutePosition](#getabsoluteposition).  
  
> [!NOTE]
>  Esta función miembro es válida únicamente para el tipo de conjunto de registros dinámicos y conjuntos de registros de tipo de instantánea.  
  
 El valor de propiedad AbsolutePosition del objeto DAO subyacente está basado en cero; un valor de 0 hace referencia al primer registro del conjunto de registros. Establecer un valor mayor que el número de registros llenados, MFC inicia una excepción. Puede determinar el número de registros rellenados en el conjunto de registros mediante una llamada a la `GetRecordCount` función miembro.  
  
 Si se elimina el registro actual, el valor de la propiedad AbsolutePosition no está definido y MFC inicia una excepción si se hace referencia. Nuevos registros se agregan al final de la secuencia.  
  
> [!NOTE]
>  Esta propiedad no está diseñada para usarse como un número de registro suplente. Los marcadores siguen siendo la forma recomendada de conservar y volver a una posición determinada y son la única forma de colocar el registro actual en todos los tipos de objetos de conjunto de registros que admiten marcadores. En concreto, la posición de un registro determinado cambia cuando se eliminan registros anteriores a ésta. También no hay ninguna garantía de que un determinado registro tendrá la misma posición absoluta si se vuelve a crear el conjunto de registros, porque no se garantiza el orden de los registros individuales dentro de un conjunto de registros, a menos que se crea con una instrucción SQL que usa un  **ORDERBY** cláusula.  
  
 Para obtener información relacionada, vea el tema "AbsolutePosition (propiedad)" en la Ayuda de DAO.  
  
##  <a name="setbookmark"></a>  CDaoRecordset:: SetBookmark  
 Llame a esta función miembro para colocar el conjunto de registros en el registro que contiene el marcador especificado.  
  
```  
void SetBookmark(COleVariant varBookmark);
```  
  
### <a name="parameters"></a>Parámetros  
 `varBookmark`  
 A [COleVariant](../../mfc/reference/colevariant-class.md) objeto que contiene el valor de marcador para un registro específico.  
  
### <a name="remarks"></a>Comentarios  
 Cuando se crea o abre un objeto de conjunto de registros, cada uno de sus registros ya tiene un marcador único. Puede recuperar el marcador para el registro actual mediante una llamada a `GetBookmark` y guardar el valor para un `COleVariant` objeto. Más adelante puede volver a ese registro mediante una llamada a `SetBookmark` con el valor de marcador guardado.  
  
> [!NOTE]
>  Al llamar a [Requery](#requery) cambia marcadores DAO.  
  
 Tenga en cuenta que si no va a crear un conjunto de registros UNICODE, la `COleVariant` objeto se debe declarar explícitamente ANSI. Esto puede hacerse mediante el uso de la [COleVariant::COleVariant](../../mfc/reference/colevariant-class.md#colevariant)**(** `lpszSrc` **,** `vtSrc` **)** forma de constructor con `vtSrc` establecido en `VT_BSTRT` (ANSI) o mediante el **COleVariant** función [SetString](../../mfc/reference/colevariant-class.md#setstring)**(** `lpszSrc` **,** `vtSrc` **)** con `vtSrc` establecido en `VT_BSTRT`.  
  
 Para obtener información relacionada, vea los temas "Propiedades de marcador" y admite marcadores"en la Ayuda de DAO.  
  
##  <a name="setcachesize"></a>  CDaoRecordset:: SetCacheSize  
 Llame a esta función miembro para establecer el número de registros en la memoria caché.  
  
```  
void SetCacheSize(long lSize);
```  
  
### <a name="parameters"></a>Parámetros  
 `lSize`  
 Especifica el número de registros. Un valor típico es 100. Un valor de 0 desactiva la caché. El valor debe estar entre 5 y 1200 registros. La memoria caché puede utilizar una cantidad considerable de memoria.  
  
### <a name="remarks"></a>Comentarios  
 Una caché es un espacio en la memoria local que contiene los datos recuperados más recientemente desde el servidor en caso de que los datos volverá a solicitarse mientras se ejecuta la aplicación. Almacenamiento en caché de datos mejora el rendimiento de una aplicación que recupera datos de un servidor remoto a través de objetos de conjunto de registros de tipo de conjunto de registros dinámicos. Cuando se solicitan datos, el motor de base de datos de Microsoft Jet comprueba la memoria caché para los datos solicitados en primer lugar, en lugar de recuperar desde el servidor, que requiere más tiempo. Datos que no proceden de un origen de datos ODBC no se guardan en la memoria caché.  
  
 Cualquier origen de datos ODBC, como una tabla asociada, puede tener una caché local. Para crear la memoria caché, abra un objeto de conjunto de registros desde el origen de datos remoto, llamada la `SetCacheSize` y `SetCacheStart` funciones miembro y, después, llame el `FillCache` función miembro o paso a paso por los registros mediante el uso de una de las operaciones de movimiento. El `lSize` parámetro de la `SetCacheSize` función miembro puede basarse en el número de registros de la aplicación puede funcionar al mismo tiempo. Por ejemplo, si usas un conjunto de registros como el origen de los datos que se muestre en pantalla, podría pasar la `SetCacheSize` `lSize` parámetro como 20 para mostrar 20 registros a la vez.  
  
 Para obtener información relacionada, vea el tema "CacheSize, CacheStart (propiedades)" en la Ayuda de DAO.  
  
##  <a name="setcachestart"></a>  CDaoRecordset:: SetCacheStart  
 Llame a esta función miembro para especificar el marcador del primer registro en el conjunto de registros en la memoria caché.  
  
```  
void SetCacheStart(COleVariant varBookmark);
```  
  
### <a name="parameters"></a>Parámetros  
 `varBookmark`  
 A [COleVariant](../../mfc/reference/colevariant-class.md) que especifica el marcador del primer registro en el conjunto de registros en la memoria caché.  
  
### <a name="remarks"></a>Comentarios  
 Puede utilizar el valor de marcador de todos los registros para el `varBookmark` parámetro de la `SetCacheStart` función miembro. Hacer que el registro que desee comenzar el almacenamiento en caché con el registro actual, establecer un marcador para ese registro mediante [SetBookmark](#setbookmark)y pase el valor de marcador como parámetro para el `SetCacheStart` función miembro.  
  
 El motor de base de datos de Microsoft Jet solicita registros dentro del intervalo de memoria caché de la memoria caché y solicita registros fuera del intervalo de memoria caché del servidor.  
  
 Los registros recuperados de la memoria caché no reflejan los cambios realizados al mismo tiempo al origen de datos por otros usuarios.  
  
 Para forzar una actualización de todos los datos almacenados en caché, pasar la `lSize` parámetro de `SetCacheSize` como 0, llame a `SetCacheSize` nuevo con el tamaño de la memoria caché que solicitó originalmente y, a continuación, llame a la `FillCache` función miembro.  
  
 Tenga en cuenta que si no va a crear un conjunto de registros UNICODE, la `COleVariant` objeto se debe declarar explícitamente ANSI. Esto puede hacerse mediante el uso de la [COleVariant::COleVariant](../../mfc/reference/colevariant-class.md#colevariant)**(** `lpszSrc` **,** `vtSrc` **)** forma de constructor con `vtSrc` establecido en `VT_BSTRT` (ANSI) o mediante el **COleVariant** función [SetString](../../mfc/reference/colevariant-class.md#setstring)**(** `lpszSrc` **,** `vtSrc` **)** con `vtSrc` establecido en `VT_BSTRT`.  
  
 Para obtener información relacionada, vea el tema CacheSize, CacheStart (propiedades)"en la Ayuda de DAO.  
  
##  <a name="setcurrentindex"></a>  CDaoRecordset:: SetCurrentIndex  
 Llame a esta función miembro para definir un índice en un conjunto de registros de tipo de tabla.  
  
```  
void SetCurrentIndex(LPCTSTR lpszIndex);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszIndex`  
 Un puntero que contiene el nombre del índice que se puede establecer.  
  
### <a name="remarks"></a>Comentarios  
 Registros de las tablas base no se almacenan en ningún orden concreto. Un índice de configuración cambia el orden de los registros devueltos desde la base de datos, pero no afecta el orden en que se almacenan los registros. Ya debe estar definido el índice especificado. Si intenta usar un objeto de índice que no existe, o si el índice no se establece cuando se llama a [Seek](#seek), MFC inicia una excepción.  
  
 Puede crear un nuevo índice de la tabla mediante una llamada a [CDaoTableDef::CreateIndex](../../mfc/reference/cdaotabledef-class.md#createindex) y agregar el nuevo índice de la colección de índices de la definición de tabla subyacente mediante una llamada a [CDaoTableDef:: Append](../../mfc/reference/cdaotabledef-class.md#append), y a continuación, volver a abrir el conjunto de registros.  
  
 Los registros devueltos desde un conjunto de registros de tipo de tabla pueden ordenarse sólo por los índices definidos para la definición de tabla subyacente. Para ordenar los registros en otro orden, puede abrir un tipo de conjunto de registros dinámicos o un conjunto de registros de tipo de instantánea con una instancia de SQL **ORDERBY** cláusula almacenados en [CDaoRecordset::m_strSort](#m_strsort).  
  
 Para obtener información relacionada, vea el tema "Objeto Index" y la definición de "índice actual" en la Ayuda de DAO.  
  
##  <a name="setfielddirty"></a>  CDaoRecordset:: SetFieldDirty  
 Llame a esta función miembro para marcar a un miembro de datos de campo del conjunto de registros como modificado o no como modificado.  
  
```  
void SetFieldDirty(
    void* pv,  
    BOOL bDirty = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 `pv`  
 Contiene la dirección de un miembro de datos de campo del conjunto de registros o **NULL**. Si **NULL**, se marcan todos los miembros de datos de campo del conjunto de registros. (C++ **NULL** no es igual a Null en la terminología de base de datos, lo que significa "no tener ningún valor.")  
  
 `bDirty`  
 **TRUE** si es miembro de datos del campo se marca como "dirty" (modificado). En caso contrario, **FALSE** si es miembro de datos del campo se marca como "limpiar" (sin cambios).  
  
### <a name="remarks"></a>Comentarios  
 Marcar campos como sin cambios garantiza que no se actualiza el campo.  
  
 Las marcas de framework cambiar los miembros de datos de campo para asegurarse de que se escribirán en el registro en el origen de datos mediante el mecanismo de intercambio (DFX) de campos de registros DAO. Cambiar el valor de un campo normalmente establece el campo desfasadas automáticamente, por lo que rara vez deberá llamar a `SetFieldDirty` usted mismo, pero a veces, conviene asegurarse de que las columnas se explícitamente actualiza o inserta independientemente de qué valor está en los datos del campo miembro. El mecanismo DFX también emplea el uso de **PSEUDONULL**. Para obtener más información, consulte [CDaoFieldExchange:: M_noperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation).  
  
 Si no se utiliza el mecanismo de almacenamiento en búfer doble, a continuación, cambiar el valor del campo no establece automáticamente el campo como modificados. En este caso, será necesario establecer explícitamente el campo como modificados. La marca contenida en [m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields) controla la comprobación automática de campos.  
  
> [!NOTE]
>  Llame a esta función miembro solo después de haber llamado [editar](#edit) o [AddNew](#addnew).  
  
 Usar **NULL** para el primer argumento de la función aplicará la función a todos los **outputColumn** campos, no **param** campos en `CDaoFieldExchange`. Por ejemplo, la llamada  
  
 [!code-cpp[NVC_MFCDatabase#6](../../mfc/codesnippet/cpp/cdaorecordset-class_6.cpp)]  
  
 establecerá solo **outputColumn** campos a **NULL**; **param** campos no se verá afectados.  
  
 Para que funcione en un **param**, debe proporcionar la dirección real de la persona **param** que desea trabajar en ella, como:  
  
 [!code-cpp[NVC_MFCDatabase#7](../../mfc/codesnippet/cpp/cdaorecordset-class_7.cpp)]  
  
 Esto significa que no se puede establecer todos los **param** campos a **NULL**, tal y como se haría con **outputColumn** campos.  
  
 `SetFieldDirty` se implementa a través de `DoFieldExchange`.  
  
##  <a name="setfieldnull"></a>  CDaoRecordset::SetFieldNull  
 Llame a esta función miembro para marcar a un miembro de datos de campo del conjunto de registros como Null (específicamente no tener ningún valor) o como no Null.  
  
```  
void SetFieldNull(
    void* pv,  
    BOOL bNull = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 `pv`  
 Contiene la dirección de un miembro de datos de campo del conjunto de registros o **NULL**. Si **NULL**, se marcan todos los miembros de datos de campo del conjunto de registros. (C++ **NULL** no es igual a Null en la terminología de base de datos, lo que significa "no tener ningún valor.")  
  
 `bNull`  
 Es distinto de cero si el miembro de datos de campo está marcado como si tuviera ningún valor (Null). 0 en caso contrario, si el miembro de datos de campo está marcado como no Null.  
  
### <a name="remarks"></a>Comentarios  
 `SetFieldNull` se usa para campos enlazados en el `DoFieldExchange` mecanismo.  
  
 Cuando se agrega un nuevo registro a un conjunto de registros, todos los miembros de datos de campo se establecen en un valor Null inicialmente y se marca como "dirty" (modificado). Cuando recupera un registro de un origen de datos, sus columnas ya tienen valores o son Null. Si no es adecuado convertir un campo Null, un [CDaoException](../../mfc/reference/cdaoexception-class.md) se produce.  
  
 Si está utilizando el mecanismo de almacenamiento en búfer doble, por ejemplo, si desea específicamente designar un campo del registro actual que no tiene un valor, llame a `SetFieldNull` con `bNull` establecido en **TRUE** para marcar como Null. Si previamente se marcó un campo Null y ahora desea asignarle un valor, basta con establecer su nuevo valor. No tiene que quitar la marca de Null con `SetFieldNull`. Para determinar si el campo puede ser Null, llame a [IsFieldNullable](#isfieldnullable).  
  
 Si no se utiliza el mecanismo de almacenamiento en búfer doble, a continuación, cambiar el valor del campo no establece automáticamente el campo como desfasadas y distinto de Null. Específicamente, debe establecer los campos desfasadas y distinto de Null. La marca contenida en [m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields) controla la comprobación automática de campos.  
  
 El mecanismo DFX emplea el uso de **PSEUDONULL**. Para obtener más información, consulte [CDaoFieldExchange:: M_noperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation).  
  
> [!NOTE]
>  Llame a esta función miembro solo después de haber llamado [editar](#edit) o [AddNew](#addnew).  
  
 Usar **NULL** para el primer argumento de la función aplicará únicamente a la función **outputColumn** campos, no **param** campos en `CDaoFieldExchange`. Por ejemplo, la llamada  
  
 [!code-cpp[NVC_MFCDatabase#8](../../mfc/codesnippet/cpp/cdaorecordset-class_8.cpp)]  
  
 establecerá solo **outputColumn** campos a **NULL**; **param** campos no se verá afectados.  
  
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
 `lpszName`  
 Un puntero a una cadena que contiene el nombre de un campo.  
  
 `varValue`  
 Una referencia a un [COleVariant](../../mfc/reference/colevariant-class.md) objeto que contiene el valor del contenido del campo.  
  
 `nIndex`  
 Un entero que representa la posición ordinal del campo en la colección de campos del conjunto de registros (basado en cero).  
  
 `lpszValue`  
 Un puntero a una cadena que contiene el valor del contenido del campo.  
  
### <a name="remarks"></a>Comentarios  
 Use `SetFieldValue` y [GetFieldValue](#getfieldvalue) enlazar campos dinámicamente en tiempo de ejecución en lugar de estáticamente columnas de enlace mediante la [DoFieldExchange](#dofieldexchange) mecanismo.  
  
 Tenga en cuenta que si no va a crear un conjunto de registros UNICODE, se debe usar una forma de `SetFieldValue` que no contiene un `COleVariant` parámetro, o la `COleVariant` objeto se debe declarar explícitamente ANSI. Esto puede hacerse mediante el uso de la [COleVariant::COleVariant](../../mfc/reference/colevariant-class.md#colevariant)**(** `lpszSrc` **,** `vtSrc` **)** forma de constructor con `vtSrc` establecido en `VT_BSTRT` (ANSI) o mediante el **COleVariant** función [SetString](../../mfc/reference/colevariant-class.md#setstring)**(** `lpszSrc` **,** `vtSrc` **)** con `vtSrc` establecido en `VT_BSTRT`.  
  
 Para obtener información relacionada, vea los temas "Objeto Field" y "Valor de propiedad" en la Ayuda de DAO.  
  
##  <a name="setfieldvaluenull"></a>  CDaoRecordset::SetFieldValueNull  
 Llame a esta función miembro para establecer el campo en un valor Null.  
  
```  
void SetFieldValueNull(int nIndex);  
void SetFieldValueNull(LPCTSTR lpszName);
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 El índice del campo en el conjunto de registros, para la búsqueda por su índice basado en cero.  
  
 `lpszName`  
 El nombre del campo en el conjunto de registros para la búsqueda por nombre.  
  
### <a name="remarks"></a>Comentarios  
 C++ **NULL** no es igual a Null, lo que, en la terminología de base de datos, significa "no having ningún valor".  
  
 Para obtener información relacionada, vea los temas "Objeto Field" y "Valor de propiedad" en la Ayuda de DAO.  
  
##  <a name="setlockingmode"></a>  CDaoRecordset::SetLockingMode  
 Llame a esta función miembro para establecer el tipo de bloqueo para el conjunto de registros.  
  
```  
void SetLockingMode(BOOL bPessimistic);
```  
  
### <a name="parameters"></a>Parámetros  
 *bPessimistic*  
 Una marca que indica el tipo de bloqueo.  
  
### <a name="remarks"></a>Comentarios  
 Cuando el bloqueo pesimista está activada, la página de 2K que contiene el registro que está modificando se bloquea en cuanto se llama a la **editar** función miembro. La página se desbloquea cuando se llama a la **actualización** o **cerrar** función miembro o cualquiera de las operaciones de movimiento o búsqueda.  
  
 Cuando está activado un bloqueo optimista, la página de 2K que contiene el registro está bloqueada solo mientras se actualiza el registro con el **actualización** función miembro.  
  
 Si se bloquea una página, ningún otro usuario puede editar registros en la misma página. Si se llama a `SetLockingMode` y pasar un valor distinto de cero y otro usuario ya ha bloqueado la página, se produce una excepción cuando se llama a **editar**. Otros usuarios pueden leer datos de páginas bloqueadas.  
  
 Si se llama a `SetLockingMode` con un valor de cero y versiones posteriores llamadas **actualización** mientras la página está bloqueada por otro usuario, se produce una excepción. Para ver los cambios realizados por otro usuario en el registro (y perder los cambios), llame a la `SetBookmark` función miembro con el valor de marcador del registro actual.  
  
 Al trabajar con orígenes de datos ODBC, el modo de bloqueo siempre es optimista.  
  
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
 `nIndex`  
 La posición numérica del parámetro en la colección de parámetros de la definición de la consulta.  
  
 `var`  
 El valor que se va a establecer; vea la sección Comentarios.  
  
 `lpszName`  
 El nombre del parámetro cuyo valor desea establecer.  
  
### <a name="remarks"></a>Comentarios  
 El parámetro ya se debe haber establecido como parte de la cadena de SQL del conjunto de registros. El parámetro puede tener acceso por nombre o por su posición de índice en la colección.  
  
 Especifique el valor que se establecerá como un `COleVariant` objeto. Para obtener información acerca de cómo establecer el valor deseado y el tipo en su `COleVariant` de objetos, vea la clase [COleVariant](../../mfc/reference/colevariant-class.md). Tenga en cuenta que si no va a crear un conjunto de registros UNICODE, la `COleVariant` objeto se debe declarar explícitamente ANSI. Esto puede hacerse mediante el uso de la [COleVariant::COleVariant](../../mfc/reference/colevariant-class.md#colevariant)**(** `lpszSrc` **,** `vtSrc` **)** forma de constructor con `vtSrc` establecido en `VT_BSTRT` (ANSI) o mediante el **COleVariant** función [SetString](../../mfc/reference/colevariant-class.md#setstring)**(** `lpszSrc` **,** `vtSrc` **)** con `vtSrc` establecido en `VT_BSTRT`.  
  
##  <a name="setparamvaluenull"></a>  CDaoRecordset::SetParamValueNull  
 Llame a esta función miembro para establecer el parámetro en un valor Null.  
  
```  
void SetParamValueNull(int nIndex);  
void SetParamValueNull(LPCTSTR lpszName);
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 El índice del campo en el conjunto de registros, para la búsqueda por su índice basado en cero.  
  
 `lpszName`  
 El nombre del campo en el conjunto de registros para la búsqueda por nombre.  
  
### <a name="remarks"></a>Comentarios  
 C++ **NULL** no es igual a Null, lo que, en la terminología de base de datos, significa "no having ningún valor".  
  
##  <a name="setpercentposition"></a>  CDaoRecordset:: SetPercentPosition  
 Llame a esta función miembro para establecer un valor que cambia la ubicación aproximada del registro actual en el objeto de conjunto de registros basándose en un porcentaje de los registros del conjunto de registros.  
  
```  
void SetPercentPosition(float fPosition);
```  
  
### <a name="parameters"></a>Parámetros  
 *fPosition*  
 Número comprendido entre 0 y 100.  
  
### <a name="remarks"></a>Comentarios  
 Cuando se trabaja con un tipo de conjunto de registros dinámicos o el conjunto de registros de tipo de instantánea, rellenar el conjunto de registros, mueva hasta el último registro antes de llamar a `SetPercentPosition`. Si se llama a `SetPercentPosition` antes de rellenar completamente el conjunto de registros, es la cantidad de movimiento en relación con el número de registros que se tiene acceso a tal y como indica el valor de [GetRecordCount](#getrecordcount). Puede mover al último registro mediante una llamada a `MoveLast`.  
  
 Una vez que se llama a `SetPercentPosition`, el registro en la ubicación aproximada correspondiente a ese valor se convierte en actual.  
  
> [!NOTE]
>  Al llamar a `SetPercentPosition` para mover el registro actual a un registro específico en un conjunto de registros no se recomienda. Llame a la [SetBookmark](#setbookmark) función miembro en su lugar.  
  
 Para obtener información relacionada, vea el tema "PercentPosition (propiedad)" en la Ayuda de DAO.  
  
##  <a name="update"></a>  CDaoRecordset::Update  
 Llame a esta función miembro después de llamar a la `AddNew` o **editar** función miembro.  
  
```  
virtual void Update();
```  
  
### <a name="remarks"></a>Comentarios  
 Esta llamada es necesario para completar la `AddNew` o **editar** operación.  
  
 Ambos `AddNew` y **editar** preparar un búfer de edición en la que se colocan los datos agregados o editados para guardar datos en el origen de datos. **Actualización** guarda los datos. Se actualizan solo esos campos marcados o detectado como modificada.  
  
 Si el origen de datos admite transacciones, puede realizar la **actualización** llamar a (y su correspondiente `AddNew` o **editar** llamar) forma parte de una transacción.  
  
> [!CAUTION]
>  Si se llama a **actualización** sin primero una llamada a `AddNew` o **editar**, **actualización** produce una `CDaoException`. Si se llama a `AddNew` o **editar**, debe llamar a **actualización** antes de llamar a [MoveNext](#movenext) o cerrar el conjunto de registros o la conexión de origen de datos. En caso contrario, los cambios se pierden sin notificación.  
  
 Cuando el objeto de conjunto de registros está bloqueado de forma pesimista en un entorno multiusuario, el registro permanece bloqueado desde el momento en que **editar** se usa hasta que finalice la actualización. Si el conjunto de registros está bloqueado de forma optimista, el registro está bloqueado y se compara con el registro antes de ser modificado justo antes de que se actualiza en la base de datos. Si el registro ha cambiado desde que se llamó a **editar**, **actualización** operación provocará un error y MFC produce una excepción. Puede cambiar el modo de bloqueo con `SetLockingMode`.  
  
> [!NOTE]
>  Bloqueo optimista siempre se utiliza en los formatos de base de datos externa, como ODBC y ISAM instalable.  
  
 Para obtener información relacionada, vea los temas "AddNew (método)", "Método CancelUpdate", "Método Delete", "Propiedad LastModified", "Método de actualización" y "Propiedad EditMode" en la Ayuda de DAO.  
  
## <a name="see-also"></a>Vea también  
 [CObject (clase)](../../mfc/reference/cobject-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clase CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)   
 [CDaoWorkspace (clase)](../../mfc/reference/cdaoworkspace-class.md)   
 [CDaoDatabase (clase)](../../mfc/reference/cdaodatabase-class.md)   
 [CDaoQueryDef (clase)](../../mfc/reference/cdaoquerydef-class.md)
