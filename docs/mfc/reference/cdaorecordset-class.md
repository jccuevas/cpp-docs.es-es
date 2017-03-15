---
title: CDaoRecordset (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDaoRecordset
dev_langs:
- C++
helpviewer_keywords:
- recordsets, types
- CDaoRecordset class
- records, CDaoRecordSet
ms.assetid: 2322067f-1027-4662-a5d7-aa2fc7488630
caps.latest.revision: 26
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 3d3d830a7d423a2653819e9cbf160538e486cfb0
ms.lasthandoff: 02/24/2017

---
# <a name="cdaorecordset-class"></a>CDaoRecordset (clase)
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
|[CDaoRecordset:: AddNew](#addnew)|Se prepara para agregar un nuevo registro. Llame a [actualización](#update) para completar la adición.|  
|[CDaoRecordset::CanAppend](#canappend)|Devuelve cero si se pueden agregar nuevos registros al conjunto de registros a través de la [AddNew](#addnew) función miembro.|  
|[CDaoRecordset:: CanBookmark](#canbookmark)|Devuelve cero si el conjunto de registros admite marcadores.|  
|[CDaoRecordset::CancelUpdate](#cancelupdate)|Cancela cualquier actualización pendiente debido a una [editar](#edit) o [AddNew](#addnew) operación.|  
|[CDaoRecordset::CanRestart](#canrestart)|Devuelve cero si [Requery](#requery) puede llamar para volver a ejecutar la consulta.|  
|[CDaoRecordset::CanScroll](#canscroll)|Devuelve cero si puede desplazarse por los registros.|  
|[CDaoRecordset::CanTransact](#cantransact)|Devuelve cero si el origen de datos admite transacciones.|  
|[CDaoRecordset::CanUpdate](#canupdate)|Devuelve distinto de cero si se puede actualizar el conjunto de registros (puede agregar, actualizar o eliminar registros).|  
|[CDaoRecordset::Close](#close)|Cierra el conjunto de registros.|  
|[CDaoRecordset::Delete](#delete)|Elimina el registro actual del conjunto de registros. Explícitamente, debe desplazarse a otro registro después de la eliminación.|  
|[CDaoRecordset](#dofieldexchange)|Se llama para intercambiar datos (en ambas direcciones) entre los miembros de datos de campo del conjunto de registros y el registro correspondiente en el origen de datos. Implementa DAO campo intercambio de registros (DFX).|  
|[CDaoRecordset:: Edit](#edit)|Se prepara para cambios en el registro actual. Llame a **actualización** para completar la edición.|  
|[CDaoRecordset:: FillCache](#fillcache)|Llena todo o parte de una caché local para un objeto de conjunto de registros que contiene los datos de un origen de datos ODBC.|  
|[CDaoRecordset::Find](#find)|Busca la primera, siguiente, anterior o última ubicación de una cadena concreta en un conjunto de registros de tipo dinámico que satisface los criterios especificados y hace que el registro del registro actual.|  
|[CDaoRecordset::FindFirst](#findfirst)|Localiza el primer registro en un tipo dinámico o el conjunto de registros de tipo snapshot que satisface los criterios especificados y hace que el registro del registro actual.|  
|[CDaoRecordset::FindLast](#findlast)|Localiza el último registro en un tipo dinámico o el conjunto de registros de tipo snapshot que satisface los criterios especificados y hace que el registro del registro actual.|  
|[CDaoRecordset::FindNext](#findnext)|Busca el siguiente registro de un tipo dinámico o el conjunto de registros de tipo snapshot que satisface los criterios especificados y hace que el registro en el registro actual.|  
|[CDaoRecordset::FindPrev](#findprev)|Localiza el registro anterior en un tipo dinámico o el conjunto de registros de tipo snapshot que satisface los criterios especificados y hace que el registro del registro actual.|  
|[CDaoRecordset:: GetAbsolutePosition](#getabsoluteposition)|Devuelve el número de registro del registro actual de un objeto recordset.|  
|[CDaoRecordset:: GetBookmark](#getbookmark)|Devuelve un valor que representa el marcador de un registro.|  
|[CDaoRecordset::GetCacheSize](#getcachesize)|Devuelve un valor que especifica el número de registros en un conjunto de registros de tipo dinámico que contiene datos para almacenar en caché localmente desde un origen de datos ODBC.|  
|[CDaoRecordset::GetCacheStart](#getcachestart)|Devuelve un valor que especifica el marcador del primer registro del conjunto de registros en la caché.|  
|[CDaoRecordset::GetCurrentIndex](#getcurrentindex)|Devuelve un `CString` que contiene el nombre del índice más recientemente utilizado en un tipo de tabla indizado, `CDaoRecordset`.|  
|[CDaoRecordset::GetDateCreated](#getdatecreated)|Devuelve la fecha y hora de la tabla base subyacente un `CDaoRecordset` se creó el objeto|  
|[CDaoRecordset::GetDateLastUpdated](#getdatelastupdated)|Devuelve la fecha y hora del cambio más reciente realizado en el diseño de una tabla base subyacente un `CDaoRecordset` objeto.|  
|[CDaoRecordset::GetDefaultDBName](#getdefaultdbname)|Devuelve el nombre del origen de datos predeterminado.|  
|[CDaoRecordset::GetDefaultSQL](#getdefaultsql)|Se llama para obtener la cadena SQL predeterminada para ejecutar.|  
|[CDaoRecordset::GetEditMode](#geteditmode)|Devuelve un valor que indica el estado de edición para el registro actual.|  
|[CDaoRecordset::GetFieldCount](#getfieldcount)|Devuelve un valor que representa el número de campos de un conjunto de registros.|  
|[CDaoRecordset::GetFieldInfo](#getfieldinfo)|Devuelve los tipos específicos de información sobre los campos del conjunto de registros.|  
|[CDaoRecordset:: GetFieldValue](#getfieldvalue)|Devuelve el valor de un campo en un conjunto de registros.|  
|[CDaoRecordset::GetIndexCount](#getindexcount)|Recupera el número de índices en una tabla subyacente de un conjunto de registros.|  
|[CDaoRecordset::GetIndexInfo](#getindexinfo)|Devuelve información acerca de un índice de diferentes tipos.|  
|[CDaoRecordset::GetLastModifiedBookmark](#getlastmodifiedbookmark)|Se utiliza para determinar el último agregado o actualizado el registro.|  
|[CDaoRecordset::GetLockingMode](#getlockingmode)|Devuelve un valor que indica el tipo de bloqueo que se aplica durante la edición.|  
|[CDaoRecordset::GetName](#getname)|Devuelve un `CString` que contiene el nombre del conjunto de registros.|  
|[CDaoRecordset::GetParamValue](#getparamvalue)|Recupera el valor actual del parámetro especificado almacenado en el objeto DAOParameter subyacente.|  
|[CDaoRecordset:: GetPercentPosition](#getpercentposition)|Devuelve la posición del registro actual como un porcentaje del número total de registros.|  
|[CDaoRecordset::GetRecordCount](#getrecordcount)|Devuelve el número de registros que se obtiene acceso en un objeto recordset.|  
|[CDaoRecordset::GetSQL](#getsql)|Obtiene la cadena SQL que se utiliza para seleccionar registros del conjunto de registros.|  
|[CDaoRecordset::GetType](#gettype)|Se llama para determinar el tipo de un conjunto de registros: tipo de tabla, tipo dinámico o tipo de instantánea.|  
|[CDaoRecordset::GetValidationRule](#getvalidationrule)|Devuelve un `CString` que contiene el valor que valida los datos a medida que se escribe en un campo.|  
|[CDaoRecordset::GetValidationText](#getvalidationtext)|Recupera el texto que se muestra cuando no se cumpla una regla de validación.|  
|[CDaoRecordset::IsBOF](#isbof)|Devuelve cero si el conjunto de registros se ha colocado antes del primer registro. No hay ningún registro actual.|  
|[CDaoRecordset::IsDeleted](#isdeleted)|Devuelve cero si el conjunto de registros está situado en un registro eliminado.|  
|[CDaoRecordset::IsEOF](#iseof)|Devuelve cero si el conjunto de registros se ha colocado después del último registro. No hay ningún registro actual.|  
|[CDaoRecordset::IsFieldDirty](#isfielddirty)|Devuelve cero si se ha cambiado el campo especificado en el registro actual.|  
|[CDaoRecordset::IsFieldNull](#isfieldnull)|Devuelve cero si el campo especificado en el registro actual es Null (no tener ningún valor).|  
|[CDaoRecordset::IsFieldNullable](#isfieldnullable)|Devuelve cero si el campo especificado en el registro actual se puede establecer en Null (no tener ningún valor).|  
|[CDaoRecordset::IsOpen](#isopen)|Devuelve cero si [abiertos](#open) se ha llamado anteriormente.|  
|[CDaoRecordset:: Move](#move)|Coloca el conjunto de registros a un número especificado de registros desde el registro actual en cualquier dirección.|  
|[CDaoRecordset::MoveFirst](#movefirst)|El registro actual se coloca en el primer registro del conjunto de registros.|  
|[CDaoRecordset::MoveLast](#movelast)|Coloca el registro actual en el último registro del conjunto de registros.|  
|[CDaoRecordset::MoveNext](#movenext)|Coloca el registro actual en el siguiente registro del conjunto de registros.|  
|[CDaoRecordset::MovePrev](#moveprev)|Coloca el registro actual en el registro anterior del conjunto de registros.|  
|[CDaoRecordset:: Open](#open)|Crea un nuevo conjunto de registros de una tabla, dynaset o instantánea.|  
|[CDaoRecordset::Requery](#requery)|Ejecuta la consulta para actualizar los registros seleccionados.|  
|[CDaoRecordset::Seek](#seek)|Localiza el registro en un objeto de conjunto de registros de tipo tabla indizada que satisface los criterios especificados para el índice actual y hace que el registro del registro actual.|  
|[CDaoRecordset:: SetAbsolutePosition](#setabsoluteposition)|Establece el número de registro del registro actual de un objeto recordset.|  
|[CDaoRecordset:: SetBookmark](#setbookmark)|Coloca el conjunto de registros en un registro que contiene el marcador especificado.|  
|[CDaoRecordset:: SetCacheSize](#setcachesize)|Establece un valor que especifica el número de registros en un conjunto de registros de tipo dinámico que contiene datos para almacenar en caché localmente desde un origen de datos ODBC.|  
|[CDaoRecordset:: SetCacheStart](#setcachestart)|Establece un valor que especifica el marcador del primer registro del conjunto de registros en la caché.|  
|[CDaoRecordset:: SetCurrentIndex](#setcurrentindex)|Llamado para establecer un índice en un conjunto de registros de tipo de tabla.|  
|[CDaoRecordset:: SetFieldDirty](#setfielddirty)|Marca el campo especificado en el registro actual ha cambiado.|  
|[CDaoRecordset::SetFieldNull](#setfieldnull)|Establece el valor del campo especificado en el registro actual en Null (no tener ningún valor).|  
|[CDaoRecordset::SetFieldValue](#setfieldvalue)|Establece el valor de un campo en un conjunto de registros.|  
|[CDaoRecordset::SetFieldValueNull](#setfieldvaluenull)|Establece el valor de un campo en un conjunto de registros en Null. (con ningún valor).|  
|[CDaoRecordset::SetLockingMode](#setlockingmode)|Establece un valor que indica el tipo de bloqueo para poner en efecto durante la edición.|  
|[CDaoRecordset::SetParamValue](#setparamvalue)|Establece el valor actual del parámetro especificado almacenado en el objeto subyacente de DAOParameter|  
|[CDaoRecordset::SetParamValueNull](#setparamvaluenull)|El valor actual del parámetro especificado se establece en Null (no tener ningún valor).|  
|[CDaoRecordset:: SetPercentPosition](#setpercentposition)|Establece la posición del registro actual en una ubicación correspondiente a un porcentaje del número total de registros en un conjunto de registros.|  
|[CDaoRecordset::Update](#update)|Completa una `AddNew` o **editar** operación guardando los datos nuevos o modificados del origen de datos.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CDaoRecordset:: M_bcheckcachefordirtyfields](#m_bcheckcachefordirtyfields)|Contiene una marca que indica si los campos se marcan automáticamente como modificada.|  
|[CDaoRecordset::m_nFields](#m_nfields)|Contiene el número de miembros de datos de campo en la clase de conjunto de registros y el número de columnas seleccionadas por el conjunto de registros del origen de datos.|  
|[CDaoRecordset::m_nParams](#m_nparams)|Contiene el número de miembros de datos de parámetro en la clase de conjunto de registros: el número de parámetros pasado con la consulta|  
|[CDaoRecordset::m_pDAORecordset](#m_pdaorecordset)|Puntero a la interfaz DAO subyacente al objeto recordset.|  
|[CDaoRecordset::m_pDatabase](#m_pdatabase)|Base de datos de origen para este conjunto de resultados. Contiene un puntero a un [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) objeto.|  
|[CDaoRecordset:: M_strfilter](#m_strfilter)|Contiene una cadena utilizada para construir una instancia de SQL **donde** instrucción.|  
|[CDaoRecordset::m_strSort](#m_strsort)|Contiene una cadena utilizada para construir una instancia de SQL **ORDER BY** instrucción.|  
  
## <a name="remarks"></a>Comentarios  
 Conocido como "conjuntos de registros," `CDaoRecordset` objetos están disponibles en las tres formas siguientes:  
  
-   Conjuntos de registros de tipo de tabla representan una tabla base que se puede utilizar para examinar, agregar, cambiar o eliminar registros de una tabla de base de datos única.  
  
-   Conjuntos de registros de tipo dinámico son el resultado de una consulta que puede tener registros actualizables. Estos conjuntos de registros son un conjunto de registros que puede utilizar para examinar, agregar, cambiar o eliminar registros de una tabla de base de datos subyacente o tablas. Conjuntos de registros de tipo Dynaset pueden contener campos de una o más tablas en una base de datos.  
  
-   Conjuntos de registros de tipo instantánea son una copia estática de un conjunto de registros que puede usar para buscar datos o generar informes. Estos conjuntos de registros pueden contener campos de una o más tablas en una base de datos, pero no se puede actualizar.  
  
 Cada formato de conjunto de registros representa un conjunto de registros que se fija en el momento en que se abre el conjunto de registros. Cuando se desplaza a un registro de un conjunto de registros de tipo de tabla o un conjunto de registros de tipo dinámico, refleja los cambios realizados en el registro cuando se abre el conjunto de registros, por otros usuarios o por otros conjuntos de registros en la aplicación. (No se puede actualizar un conjunto de registros de tipo instantánea). Puede usar `CDaoRecordset` directamente o derivar una clase de conjunto de registros específicos de la aplicación de `CDaoRecordset`. A continuación, se puede:  
  
-   Desplazarse por los registros.  
  
-   Establecer un índice y buscar rápidamente registros mediante [Seek](#seek) (sólo para conjuntos de registros de tipo de tabla).  
  
-   Buscar registros basándose en una comparación de cadenas: "<",></",>\<=", "=", "> =", o ">" (tipo de conjunto de registros dinámicos y registros de tipo instantánea).  
  
-   Actualizar los registros y especificar un modo de bloqueo (excepto los conjuntos de registros de tipo instantánea).  
  
-   Filtrar el conjunto de registros para restringir qué registros selecciona de los que están disponibles en el origen de datos.  
  
-   Ordenar el conjunto de registros.  
  
-   Parametrice el conjunto de registros para personalizar su selección con información que no conocida hasta el tiempo de ejecución.  
  
 Clase `CDaoRecordset` proporciona una interfaz similar a la de la clase `CRecordset`. La diferencia principal es esa clase `CDaoRecordset` tiene acceso a datos a través de un objeto de acceso de datos (DAO) basado en OLE. Clase `CRecordset` tiene acceso el DBMS a través de Open Database Connectivity (ODBC) y un controlador ODBC para ese DBMS.  
  
> [!NOTE]
>  Las clases de base de datos DAO son distintas de las clases de base de datos MFC basadas en Open Database Connectivity (ODBC). Todos los nombres de clase de base de datos DAO tienen el prefijo "CDao". Puede seguir acceso a orígenes de datos ODBC con las clases DAO; Generalmente, las clases DAO ofrecen capacidades de superior porque son específicas para el motor de base de datos Microsoft Jet.  
  
 Puede usar `CDaoRecordset` directamente o derivar una clase de `CDaoRecordset`. Para utilizar una clase de conjunto de registros en cualquier caso, abrir una base de datos y construir un objeto de conjunto de registros, pasando al constructor un puntero a su `CDaoDatabase` objeto. También se puede construir un `CDaoRecordset` de objetos y dejar que MFC crea un archivo temporal `CDaoDatabase` objeto. A continuación, llame el conjunto de registros [abiertos](#open) función de miembro, que especifica si el objeto es un conjunto de registros de tipo de tabla, un conjunto de registros de tipo dinámico o un conjunto de registros de tipo snapshot. Llamar a **abiertos** selecciona datos de la base de datos y recupera el primer registro.  
  
 Utilice los miembros de datos y funciones de miembro del objeto para desplazarse por los registros y trabajar en ellos. Las operaciones disponibles dependen de si el objeto es un conjunto de registros de tipo de tabla, un conjunto de registros de tipo dinámico o un conjunto de registros de tipo snapshot y, si es actualizable o de solo lectura: Esto depende de la capacidad de la base de datos o un origen de datos de Open Database Connectivity (ODBC). Para actualizar los registros que se han cambiado o agregado desde el **abiertos** llamada, llame al objeto [Requery](#requery) función miembro. Llame al objeto **cerrar** miembro de función y destruir el objeto cuando haya terminado con él.  
  
 `CDaoRecordset`intercambio de campos de registros DAO (DFX) se utiliza para admitir la lectura y actualización de campos de registro a través de los miembros de C++ con seguridad de tipos de su `CDaoRecordset` o `CDaoRecordset`-clase derivada. También puede implementar el enlace dinámico de columnas en una base de datos sin mediante el uso del mecanismo DFX [GetFieldValue](#getfieldvalue) y [SetFieldValue](#setfieldvalue).  
  
 Para obtener información relacionada, vea el tema "Objeto Recordset" en la Ayuda de DAO.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CDaoRecordset`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdao.h  
  
##  <a name="a-nameaddnewa--cdaorecordsetaddnew"></a><a name="addnew"></a>CDaoRecordset:: AddNew  
 Llame a esta función miembro para agregar un nuevo registro a un conjunto de registros de tipo dinámico o tabla.  
  
```  
virtual void AddNew();
```  
  
### <a name="remarks"></a>Comentarios  
 Los campos del registro son Null inicialmente. (En la terminología de base de datos, Null significa "no tener ningún valor" y no es igual a **NULL** en C++.) Para completar la operación, se debe llamar a la [actualización](#update) función miembro. **Actualización** guarda los cambios en el origen de datos.  
  
> [!CAUTION]
>  Si edita un registro y, a continuación, desplácese a otro registro sin llamar a **actualización**, los cambios se pierden sin advertencia.  
  
 Si agregar un registro a un conjunto de registros de tipo dinámico mediante una llamada a [AddNew](#addnew), el registro está visible en el conjunto de registros y se incluye en la tabla subyacente donde estará visible para cualquier nuevo `CDaoRecordset` objetos.  
  
 La posición del nuevo registro depende del tipo de conjunto de registros:  
  
-   En un tipo de conjunto de registros dinámicos no se garantiza el conjunto de registros, donde se insertó el nuevo registro. Este comportamiento se cambió con Microsoft Jet 3.0 por motivos de rendimiento y simultaneidad. Si su objetivo es hacer el registro recién agregado en el registro actual, obtener el marcador del último registro modificado y moverse al marcador:  
  
 [!code-cpp[1 NVC_MFCDatabase](../../mfc/codesnippet/cpp/cdaorecordset-class_1.cpp)]  
  
-   En un conjunto de registros de tipo de tabla para la que se ha especificado un índice, los registros se devuelven en su posición correcta en el criterio de ordenación. Si no se ha especificado ningún índice, los nuevos registros se devuelven al final del conjunto de registros.  
  
 El registro que era actual antes de utilizar `AddNew` sigue estando activo. Si desea que el nuevo registro actual y el conjunto de registros admite marcadores, llamada [SetBookmark](#setbookmark) en el marcador identificado por el valor de la propiedad LastModified del objeto de conjunto de registros DAO subyacente. Esto es útil para determinar el valor de los campos de contador (incremento automático) en un registro agregado. Para obtener más información, consulte [GetLastModifiedBookmark](#getlastmodifiedbookmark).  
  
 Si la base de datos admite transacciones, puede hacer que su `AddNew` llame a parte de una transacción. Para obtener más información acerca de las transacciones, vea la clase [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md). Tenga en cuenta que debe llamar a [CDaoWorkspace::BeginTrans](../../mfc/reference/cdaoworkspace-class.md#begintrans) antes de llamar a `AddNew`.  
  
 No es válido para llamar a `AddNew` para un conjunto de registros cuyo [abiertos](#open) no se llamó a la función miembro. Un `CDaoException` se produce si se llama a `AddNew` para un conjunto de registros que no se puede anexar. Puede determinar si el conjunto de registros es actualizable llamando [CanAppend](#canappend).  
  
 Las marcas de framework cambiar los miembros de datos de campo para asegurarse de que se escribirán en el registro en el origen de datos mediante el mecanismo de intercambio (DFX) de campos de registros DAO. Cambiar el valor de un campo normalmente establece el campo desfasadas automáticamente, por lo que rara vez necesitará llamar a [SetFieldDirty](#setfielddirty) usted mismo, pero a veces, conviene asegurarse de que las columnas se explícitamente actualizadas o insertadas, independientemente de qué valor se encuentra en el miembro de datos de campo. El mecanismo DFX también emplea el uso de **PSEUDO NULL**. Para obtener más información, consulte [CDaoFieldExchange:: M_noperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation).  
  
 Si no se utiliza el mecanismo de doble búfer, a continuación, cambiar el valor del campo no establece automáticamente el campo como modificada. En este caso, será necesario establecer explícitamente el campo modificado. La marca contenida en [m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields) controla esta comprobación automática de campos.  
  
> [!NOTE]
>  Si hay registros de doble búfer (es decir, comprobación automática de campos está habilitada), una llamada a `CancelUpdate` restaurará las variables miembro para los valores que tenían antes de `AddNew` o **editar** se llamó.  
  
 Para obtener información relacionada, vea los temas "Método AddNew", "Método CancelUpdate", "Propiedad LastModified" y "Propiedad EditMode" en la Ayuda de DAO.  
  
##  <a name="a-namecanappenda--cdaorecordsetcanappend"></a><a name="canappend"></a>CDaoRecordset::CanAppend  
 Llame a esta función miembro para determinar si el conjunto de registros abierto anteriormente le permite agregar nuevos registros mediante una llamada a la [AddNew](#addnew) función miembro.  
  
```  
BOOL CanAppend() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el conjunto de registros permite agregar nuevos registros; en caso contrario, 0. `CanAppend`Devuelve 0 si se abre el conjunto de registros como de solo lectura.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener información relacionada, vea el tema "Método Append" en la Ayuda de DAO.  
  
##  <a name="a-namecanbookmarka--cdaorecordsetcanbookmark"></a><a name="canbookmark"></a>CDaoRecordset:: CanBookmark  
 Llame a esta función miembro para determinar si el conjunto de registros abierto anteriormente le permite marcar individualmente los registros mediante marcadores.  
  
```  
BOOL CanBookmark();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el conjunto de registros admite marcadores, de lo contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Si está utilizando conjuntos de registros que se basa completamente en tablas del motor de base de datos Microsoft Jet, pueden utilizar marcadores excepto en conjuntos de registros de tipo snapshot que se marca como conjuntos de registros de desplazamiento sólo hacia delante. Otros productos de base de datos (orígenes de datos ODBC externos) pueden no admitir marcadores.  
  
 Para obtener información relacionada, vea el tema "Propiedad admite marcadores" en la Ayuda de DAO.  
  
##  <a name="a-namecancelupdatea--cdaorecordsetcancelupdate"></a><a name="cancelupdate"></a>CDaoRecordset::CancelUpdate  
 El `CancelUpdate` función miembro cancela cualquier actualización pendiente debido a una [editar](#edit) o [AddNew](#addnew) operación.  
  
```  
virtual void CancelUpdate();
```  
  
### <a name="remarks"></a>Comentarios  
 Por ejemplo, si una aplicación llama a la **editar** o `AddNew` función miembro y no se ha llamado [actualización](#update), `CancelUpdate` cancela los cambios realizados después de **editar** o `AddNew` se llamó.  
  
> [!NOTE]
>  Si hay registros de doble búfer (es decir, comprobación automática de campos está habilitada), una llamada a `CancelUpdate` restaurará las variables miembro para los valores que tenían antes de `AddNew` o **editar** se llamó.  
  
 Si no hay ningún **editar** o `AddNew` operación pendiente, `CancelUpdate` hace MFC producir una excepción. Llame a la [GetEditMode](#geteditmode) función miembro para determinar si hay una operación pendiente que se puede cancelar.  
  
 Para obtener información relacionada, vea el tema "Método CancelUpdate" en la Ayuda de DAO.  
  
##  <a name="a-namecanrestarta--cdaorecordsetcanrestart"></a><a name="canrestart"></a>CDaoRecordset::CanRestart  
 Llame a esta función miembro para determinar si el conjunto de registros permite reiniciar su consulta (para actualizar sus registros) llamando a la **Requery** función miembro.  
  
```  
BOOL CanRestart();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si **Requery** se puede llamar para ejecutar la consulta de nuevo, de lo contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 No se admiten conjuntos de registros de tipo de tabla **Requery**.  
  
 Si **Requery** no es compatible, llame a [cerrar](#close) , a continuación, [abiertos](#open) para actualizar los datos. Puede llamar a **Requery** actualizar un objeto de conjunto de registros subyacente de la consulta de parámetros después de cambiar los valores de parámetro.  
  
 Para obtener información relacionada, vea el tema "Propiedad reiniciable" en la Ayuda de DAO.  
  
##  <a name="a-namecanscrolla--cdaorecordsetcanscroll"></a><a name="canscroll"></a>CDaoRecordset::CanScroll  
 Llame a esta función miembro para determinar si el conjunto de registros permite el desplazamiento.  
  
```  
BOOL CanScroll() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si puede desplazarse por los registros, de lo contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Si se llama a [abiertos](#open) con **dbForwardOnly**, el conjunto de registros sólo puede desplazarse hacia delante.  
  
 Para obtener información relacionada, vea el tema "Dirigir el puntero de registro actual con DAO" en la Ayuda de DAO.  
  
##  <a name="a-namecantransacta--cdaorecordsetcantransact"></a><a name="cantransact"></a>CDaoRecordset::CanTransact  
 Llame a esta función miembro para determinar si el conjunto de registros permite que las transacciones.  
  
```  
BOOL CanTransact();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el origen de datos subyacente admite las transacciones, de lo contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener información relacionada, vea el tema "Propiedad de transacciones" en la Ayuda de DAO.  
  
##  <a name="a-namecanupdatea--cdaorecordsetcanupdate"></a><a name="canupdate"></a>CDaoRecordset::CanUpdate  
 Llame a esta función miembro para determinar si se puede actualizar el conjunto de registros.  
  
```  
BOOL CanUpdate() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si se puede actualizar el conjunto de registros (agregar, actualizar y eliminar registros), de lo contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Un conjunto de registros puede ser de sólo lectura si el origen de datos subyacente es de solo lectura o si ha especificado **dbReadOnly** de `nOptions` cuando llama a [abiertos](#open) para el conjunto de registros.  
  
 Para obtener información relacionada, vea los temas "Método AddNew", "Editar método", "Método Delete", "Método de actualización" y "Propiedad actualizable" en la Ayuda de DAO.  
  
##  <a name="a-namecdaorecordseta--cdaorecordsetcdaorecordset"></a><a name="cdaorecordset"></a>CDaoRecordset::CDaoRecordset  
 Construye un objeto `CDaoRecordset`.  
  
```  
CDaoRecordset(CDaoDatabase* pDatabase = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `pDatabase`  
 Contiene un puntero a un [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) objeto o el valor **NULL**. Si no **NULL** y `CDaoDatabase` del objeto **abrir** función miembro no se llamó para conectarse al origen de datos, el objeto recordset intenta abrir automáticamente durante su propio [abrir](#open) llamar. Si se pasa **NULL**, `CDaoDatabase` objeto se crea y se conecta utilizando la información de origen de datos especificado si deriva de la clase de conjunto de registros de `CDaoRecordset`.  
  
### <a name="remarks"></a>Comentarios  
 Puede usar `CDaoRecordset` directamente o derivar una clase específica de la aplicación de `CDaoRecordset`. Puede usar ClassWizard para derivar las clases de conjunto de registros.  
  
> [!NOTE]
>  Si deriva una `CDaoRecordset` clase su derivada clase debe proporcionar su propio constructor. En el constructor de la clase derivada, llame al constructor `CDaoRecordset::CDaoRecordset`, pasando los parámetros adecuados junto a él.  
  
 Pasar **NULL** a su constructor de conjunto de registros que tienen un `CDaoDatabase` objeto construido y conectado por usted automáticamente. Se trata de un método abreviado útiles que no requiere crear y conectar un `CDaoDatabase` objeto antes de construir el conjunto de registros. Si el `CDaoDatabase` objeto no está abierto, un [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md) también se creará el objeto que utiliza el área de trabajo predeterminada. Para obtener más información, consulte [CDaoDatabase::CDaoDatabase](../../mfc/reference/cdaodatabase-class.md#cdaodatabase).  
  
##  <a name="a-nameclosea--cdaorecordsetclose"></a><a name="close"></a>CDaoRecordset::Close  
 Cerrar un `CDaoRecordset` objeto quita de la colección de conjuntos de registros abiertos en la base de datos asociada.  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>Comentarios  
 Porque **cerrar** no destruye el `CDaoRecordset` de objeto, se puede reutilizar el objeto mediante una llamada a **abiertos** en el mismo origen de datos o un origen de datos diferente.  
  
 Todas las pendientes [AddNew](#addnew) o [editar](#edit) instrucciones se cancelan y se revierten todas las transacciones pendientes. Si desea conservar adiciones o modificaciones pendientes, llame a [actualización](#update) antes de llamar a **cerrar** para cada conjunto de registros.  
  
 Puede llamar a **abiertos** nuevo después de llamar a **cerrar**. Esto permite reutilizar el objeto recordset. Una alternativa mejor es llamar a [Requery](#requery), si es posible.  
  
 Para obtener información relacionada, vea el tema "Método Close" en la Ayuda de DAO.  
  
##  <a name="a-namedeletea--cdaorecordsetdelete"></a><a name="delete"></a>CDaoRecordset::Delete  
 Llame a esta función miembro para eliminar el registro actual en un objeto de conjunto de registros abierto de tipo dinámico o tipo de tabla.  
  
```  
virtual void Delete();
```  
  
### <a name="remarks"></a>Comentarios  
 Después de una eliminación se realiza correctamente, los miembros de datos de campo del conjunto de registros se establecen en un valor Null, y debe llamar explícitamente a una de las funciones de miembro de navegación de conjunto de registros ( [mover](#move), [Seek](#seek), [SetBookmark](#setbookmark), etc.) para abandonar el registro eliminado. Cuando se eliminan registros de un conjunto de registros, debe haber un registro actual en el conjunto de registros antes de llamar a **eliminar**; en caso contrario, produce una excepción de MFC.  
  
 **Eliminar** quita el registro actual y lo convierte en inaccesible. Aunque no puede editar o utilizar el registro eliminado, éste permanece actual. Cuando se mueva a otro registro, sin embargo, no puede realizar el registro eliminado actual nuevo.  
  
> [!CAUTION]
>  El conjunto de registros debe ser actualizable y debe haber un registro válido actual en el conjunto de registros al llamar a **eliminar**. Por ejemplo, si elimina un registro pero no desplazarse a un nuevo registro antes de llamar a **eliminar** nuevamente, **eliminar** produce una [CDaoException](../../mfc/reference/cdaoexception-class.md).  
  
 Puede recuperar un registro si se utilizan transacciones y se llama el [CDaoWorkspace::Rollback](../../mfc/reference/cdaoworkspace-class.md#rollback) función miembro. Si la tabla base es la tabla principal en cascada Eliminar relación, también puede eliminar uno o más registros en una tabla externa al eliminar el registro actual. Para obtener más información, vea la definición "en cascada" eliminar en la Ayuda de DAO.  
  
 A diferencia de `AddNew` y **editar**, una llamada a **eliminar** no va seguida de una llamada a **actualización**.  
  
 Para obtener información relacionada, vea los temas "Método AddNew", "Editar método", "Método Delete", "Método de actualización" y "Propiedad actualizable" en la Ayuda de DAO.  
  
##  <a name="a-namedofieldexchangea--cdaorecordsetdofieldexchange"></a><a name="dofieldexchange"></a>CDaoRecordset  
 El marco de trabajo llama a esta función miembro para automáticamente intercambiar datos entre los miembros de datos de campo del objeto de conjunto de registros y las columnas correspondientes del registro actual en el origen de datos.  
  
```  
virtual void DoFieldExchange(CDaoFieldExchange* pFX);
```  
  
### <a name="parameters"></a>Parámetros  
 `pFX`  
 Contiene un puntero a un `CDaoFieldExchange` objeto. El marco de trabajo ya habrá configurado este objeto para especificar un contexto para la operación de intercambio de campos.  
  
### <a name="remarks"></a>Comentarios  
 También enlaza a los miembros de datos de parámetro, si los hay, los marcadores de posición en la cadena de la instrucción SQL para la selección del conjunto de registros. El intercambio de datos de campo, denominado intercambio de campos de registros DAO (DFX) funciona en ambas direcciones: desde miembros de datos de campo del objeto de conjunto de registros a los campos del registro en el origen de datos y del registro en el origen de datos para el objeto de conjunto de registros. Si va a enlazar columnas dinámicamente, no debe implementar `DoFieldExchange`.  
  
 La única acción que debe realizar normalmente para implementar `DoFieldExchange` el conjunto de registros derivada de la clase es crear la clase con ClassWizard y especificar los nombres y tipos de datos de los miembros de datos de campo. También puede agregar código a lo que escribe ClassWizard especificar a los miembros de datos de parámetro. Si todos los campos que se enlazarán dinámicamente, esta función estará inactiva a menos que especifique a los miembros de datos de parámetro.  
  
 Cuando se declara la clase de conjunto de registros derivada con ClassWizard, el asistente escribe una invalidación de `DoFieldExchange` , que es similar al siguiente:  
  
 [!code-cpp[NVC_MFCDatabase&#2;](../../mfc/codesnippet/cpp/cdaorecordset-class_2.cpp)]  
  
##  <a name="a-nameedita--cdaorecordsetedit"></a><a name="edit"></a>CDaoRecordset:: Edit  
 Llame a esta función miembro para permitir cambios en el registro actual.  
  
```  
virtual void Edit();
```  
  
### <a name="remarks"></a>Comentarios  
 Una vez que se llama a la **editar** función miembro, los cambios realizados en los campos del registro activo se copian en el búfer de copia. Después de realizar los cambios deseados en el registro, llamada **actualización** para guardar los cambios. **Editar** guarda los valores de los miembros de datos del conjunto de registros. Si se llama a **editar**, realice cambios y, a continuación, llame a **editar** de nuevo, los valores del registro se restauran a su estado original antes de la primera **editar** llamar.  
  
> [!CAUTION]
>  Si edita un registro y, a continuación, realizar cualquier operación que se desplace a otro registro sin llamar primero a **actualización**, los cambios se pierden sin advertencia. Además, si cierra el conjunto de registros o base de datos primaria, el registro editado se descarta sin advertencia.  
  
 En algunos casos, puede actualizar una columna por lo que es Null (que contiene datos no). Para ello, llame a `SetFieldNull` con un parámetro de **TRUE** para marcar el campo Null; Esto también hace que la columna que se va a actualizar. Si desea que un campo para escribir en el origen de datos aunque no ha cambiado su valor, llame a `SetFieldDirty` con un parámetro de **TRUE**. Esto funciona incluso si el campo tiene el valor Null.  
  
 Las marcas de framework cambiar los miembros de datos de campo para asegurarse de que se escribirán en el registro en el origen de datos mediante el mecanismo de intercambio (DFX) de campos de registros DAO. Cambiar el valor de un campo normalmente establece el campo desfasadas automáticamente, por lo que rara vez necesitará llamar a [SetFieldDirty](#setfielddirty) usted mismo, pero a veces, conviene asegurarse de que las columnas se explícitamente actualizadas o insertadas, independientemente de qué valor se encuentra en el miembro de datos de campo. El mecanismo DFX también emplea el uso de **PSEUDO NULL**. Para obtener más información, consulte [CDaoFieldExchange:: M_noperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation).  
  
 Si no se utiliza el mecanismo de doble búfer, a continuación, cambiar el valor del campo no establece automáticamente el campo como modificada. En este caso, será necesario establecer explícitamente el campo modificado. La marca contenida en [m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields) controla esta comprobación automática de campos.  
  
 Cuando el objeto recordset está bloqueado de forma pesimista en un entorno multiusuario, el registro permanece bloqueado desde **editar** se usa hasta que finalice la actualización. Si el conjunto de registros está bloqueado de forma optimista, el registro está bloqueado y se compara con el registro justo antes de actualizar la base de datos. Si el registro ha cambiado desde que llamó a **editar**, **actualización** error de la operación y MFC produce una excepción. Puede cambiar el modo de bloqueo con `SetLockingMode`.  
  
> [!NOTE]
>  Siempre se utiliza el bloqueo optimista en formatos de base de datos externa, como ODBC e ISAM instalable.  
  
 El registro actual se mantiene actual después de llamar a **editar**. Llamar a **editar**, debe haber un registro actual. Si no hay ningún registro actual, o si el conjunto de registros no hace referencia a un tipo de tabla abierto o el objeto recordset de tipo dynaset, se produce una excepción. Llamar a **editar** hace un `CDaoException` que se produzca en las siguientes condiciones:  
  
-   No hay ningún registro actual.  
  
-   La base de datos o un conjunto de registros es de sólo lectura.  
  
-   No hay campos en el registro son actualizables.  
  
-   La base de datos o un conjunto de registros se abrió para uso exclusivo por otro usuario.  
  
-   Otro usuario ha bloqueado la página que contiene el registro.  
  
 Si el origen de datos admite transacciones, puede hacer que el **editar** llame a parte de una transacción. Tenga en cuenta que debe llamar a `CDaoWorkspace::BeginTrans` antes de llamar a **editar** y después de abrir el conjunto de registros. Tenga en cuenta también que la llamada a `CDaoWorkspace::CommitTrans` no es un sustituto para llamar a **actualización** para completar la **editar** operación. Para obtener más información acerca de las transacciones, vea la clase `CDaoWorkspace`.  
  
 Para obtener información relacionada, vea los temas "Método AddNew", "Editar método", "Método Delete", "Método de actualización" y "Propiedad actualizable" en la Ayuda de DAO.  
  
##  <a name="a-namefillcachea--cdaorecordsetfillcache"></a><a name="fillcache"></a>CDaoRecordset:: FillCache  
 Llame a esta función miembro para almacenar en caché un número de registros del conjunto de registros especificado.  
  
```  
void FillCache(
    long* pSize = NULL,  
    COleVariant* pBookmark = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `pSize`  
 Especifica el número de filas que se va a rellenar la memoria caché. Si omite este parámetro, el valor se determina por el valor de la propiedad CacheSize del objeto DAO subyacente.  
  
 `pBookmark`  
 Un [COleVariant](../../mfc/reference/colevariant-class.md) especificación de un marcador. La caché se llena a partir del registro indicado por este marcador. Si omite este parámetro, la caché se llena a partir del registro indicado por la propiedad CacheStart del objeto DAO subyacente.  
  
### <a name="remarks"></a>Comentarios  
 Almacenamiento en caché mejora el rendimiento de una aplicación que recupera o la captura de datos desde un servidor remoto. Una caché es un espacio en memoria local que contiene los datos que se han capturado recientemente desde el servidor en la suposición de que los datos probablemente se solicitarán nuevo mientras se ejecuta la aplicación. Cuando se soliciten datos, el motor de base de datos Microsoft Jet comprueba primero la caché para los datos en lugar de recuperar desde el servidor, que tarda más tiempo. Utilizando los datos de almacenamiento en caché de orígenes de datos ODBC no tiene ningún efecto como los datos no se guardan en la memoria caché.  
  
 En lugar de esperar a que la memoria caché se llena con registros se capturan, se puede llenar la caché en cualquier momento llamando a la `FillCache` función miembro. Se trata de una manera más rápida de llenar la caché porque `FillCache` recupera varios registros a la vez en lugar de uno en uno. Por ejemplo, mientras se está mostrando cada pantalla de registros, puede tener la llamada de la aplicación `FillCache` para capturar la siguiente pantalla de registros.  
  
 Cualquier base de datos ODBC que se tiene acceso con objetos recordset puede tener una caché local. Para crear una caché, abra un objeto recordset desde el origen de datos remoto y, a continuación, llame a la `SetCacheSize` y `SetCacheStart` funciones miembro del conjunto de registros. Si `lSize` y *lBookmark* crear un rango que está parcial o totalmente fuera del intervalo especificado por `SetCacheSize` y `SetCacheStart`, la parte del conjunto de registros fuera de este intervalo se omite y no se ha cargado en la memoria caché. Si `FillCache` solicita más registros que permanecen en el origen de datos remoto, sólo los registros restantes se capturan y se inicia ninguna excepción.  
  
 Registros obtenidos de la memoria caché no reflejan los cambios realizados al origen de datos por otros usuarios.  
  
 `FillCache`captura solo los registros ya no almacenado en caché. Para forzar una actualización de todos los datos almacenados en caché, llame a la `SetCacheSize` función miembro con un `lSize` parámetro igual a 0, llamada `SetCacheSize` nuevo con el `lSize` parámetro igual al tamaño de la memoria caché que solicitó originalmente y, a continuación, llame `FillCache`.  
  
 Para obtener información relacionada, vea el tema "Método FillCache" en la Ayuda de DAO.  
  
##  <a name="a-namefinda--cdaorecordsetfind"></a><a name="find"></a>CDaoRecordset::Find  
 Llame a esta función miembro para buscar una cadena concreta en un conjunto de registros de tipo dynaset o snapshot mediante un operador de comparación.  
  
```  
virtual BOOL Find(
    long lFindType,  
    LPCTSTR lpszFilter);
```  
  
### <a name="parameters"></a>Parámetros  
 *lFindType*  
 Un valor que indica el tipo de operación de búsqueda deseada. Los valores posibles son:  
  
- **AFX_DAO_NEXT** encontrar la ubicación siguiente de la cadena coincidente.  
  
- **AFX_DAO_PREV** encontrar la ubicación anterior de una cadena coincidente.  
  
- **AFX_DAO_FIRST** buscar la primera ubicación de una cadena coincidente.  
  
- **Bien AFX_DAO_LAST** encontrar la última ubicación de una cadena coincidente.  
  
 `lpszFilter`  
 Una expresión de cadena (como el **donde** cláusula en una instrucción SQL sin la palabra **donde**) utilizado para buscar el registro. Por ejemplo:  
  
 [!code-cpp[NVC_MFCDatabase&3;](../../mfc/codesnippet/cpp/cdaorecordset-class_3.cpp)]  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si se encuentran registros coincidentes, en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Puede encontrar el primer, siguiente, anterior o en última instancia de la cadena. **Buscar** es una función virtual, por lo que puede invalidarlo y agregar su propia implementación. El `FindFirst`, `FindLast`, `FindNext`, y `FindPrev` llamada de funciones miembro de la **buscar** función miembro, por lo que puede usar **buscar** para controlar el comportamiento de todas las operaciones de búsqueda.  
  
 Para localizar un registro en un conjunto de registros de tipo de tabla, llame a la [Seek](#seek) función miembro.  
  
> [!TIP]
>  Cuanto menor sea el conjunto de registros tiene, más eficaces **buscar** será. En general y especialmente con los datos ODBC, es mejor crear una nueva consulta que recupera sólo los registros que desee.  
  
 Para obtener información relacionada, vea el tema "FindFirst, FindLast, FindNext, FindPrevious métodos" en la Ayuda de DAO.  
  
##  <a name="a-namefindfirsta--cdaorecordsetfindfirst"></a><a name="findfirst"></a>CDaoRecordset::FindFirst  
 Llame a esta función miembro para buscar el primer registro que coincide con una condición especificada.  
  
```  
BOOL FindFirst(LPCTSTR lpszFilter);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszFilter`  
 Una expresión de cadena (como el **donde** cláusula en una instrucción SQL sin la palabra **donde**) utilizado para buscar el registro.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si se encuentran registros coincidentes, en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 El `FindFirst` función miembro comienza su búsqueda desde el principio del conjunto de registros y busca hasta el final del conjunto de registros.  
  
 Si desea incluir todos los registros en la búsqueda (no sólo los que cumplen una condición específica) usan una de las operaciones de desplazamiento para desplazarse por los registros. Para localizar un registro en un conjunto de registros de tipo de tabla, llame a la `Seek` función miembro.  
  
 Si no se encuentra ningún registro que cumpla los criterios, el puntero del registro actual es indeterminado, y `FindFirst` devuelve cero. Si el conjunto de registros contiene más de un registro que satisface los criterios `FindFirst` localiza la primera aparición, `FindNext` busca la siguiente aparición y así sucesivamente.  
  
> [!CAUTION]
>  Si edita el registro actual, asegúrese de guardar los cambios mediante una llamada a la **actualización** función de miembro antes de pasar a otro registro. Si se mueve a otro registro sin actualizar, los cambios se pierden sin advertencia.  
  
 El **buscar** funciones miembro de búsqueda desde la ubicación y en la dirección especificada en la tabla siguiente:  
  
|Operaciones de búsqueda|BEGIN|Dirección de búsqueda|  
|---------------------|-----------|----------------------|  
|`FindFirst`|Principio del conjunto de registros|Final del conjunto de registros|  
|`FindLast`|Final del conjunto de registros|Principio del conjunto de registros|  
|`FindNext`|Registro actual|Final del conjunto de registros|  
|**FindPrevious**|Registro actual|Principio del conjunto de registros|  
  
> [!NOTE]
>  Cuando se llama a `FindLast`, el motor de base de datos Microsoft Jet rellena totalmente el conjunto de registros antes de comenzar la búsqueda, si no se ha hecho ya. La primera búsqueda puede tardar más que las búsquedas posteriores.  
  
 Utilizando una de las operaciones de búsqueda no es el mismo que llamar a **MoveFirst** o `MoveNext`, sin embargo, que simplemente hace que el primer o siguiente registro actual sin especificar una condición. Puede seguir una operación de búsqueda con una operación de movimiento.  
  
 Tenga en cuenta lo siguiente al utilizar las operaciones de búsqueda:  
  
-   Si **buscar** devuelve distinto de cero, el registro actual no está definido. En este caso, debe colocar el puntero de registro actual hacia un registro válido.  
  
-   No puede utilizar una operación de búsqueda con un recordset de tipo snapshot de desplazamiento sólo hacia delante.  
  
-   Debe usar el formato de fecha de Estados Unidos (mes-año) cuando busca campos que contienen fechas, incluso si no está utilizando la versión de Estados Unidos del motor de base de datos de Microsoft Jet; de lo contrario, registros coincidentes pueden no encontrarse.  
  
-   Cuando se trabaja con grandes conjuntos de registros dinámicos y de bases de datos ODBC, puede descubrir que utilizan las operaciones de búsqueda es lento, especialmente cuando se trabaja con grandes conjuntos de registros. Puede mejorar el rendimiento mediante consultas SQL con personalizar **ORDERBY** o **donde** cláusulas, consultas de parámetros, o **CDaoQuerydef** objetos que recuperan registros indizados específicos.  
  
 Para obtener información relacionada, vea el tema "FindFirst, FindLast, FindNext, FindPrevious métodos" en la Ayuda de DAO.  
  
##  <a name="a-namefindlasta--cdaorecordsetfindlast"></a><a name="findlast"></a>CDaoRecordset::FindLast  
 Llame a esta función miembro para buscar el último registro que coincide con una condición especificada.  
  
```  
BOOL FindLast(LPCTSTR lpszFilter);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszFilter`  
 Una expresión de cadena (como el **donde** cláusula en una instrucción SQL sin la palabra **donde**) utilizado para buscar el registro.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si se encuentran registros coincidentes, en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 El `FindLast` función miembro comienza su búsqueda al final del conjunto de registros y busca hacia atrás hacia el principio del conjunto de registros.  
  
 Si desea incluir todos los registros en la búsqueda (no sólo los que cumplen una condición específica) usan una de las operaciones de desplazamiento para desplazarse por los registros. Para localizar un registro en un conjunto de registros de tipo de tabla, llame a la `Seek` función miembro.  
  
 Si no se encuentra ningún registro que cumpla los criterios, el puntero del registro actual es indeterminado, y `FindLast` devuelve cero. Si el conjunto de registros contiene más de un registro que satisface los criterios `FindFirst` localiza la primera aparición, `FindNext` busca la siguiente aparición después de la primera aparición y así sucesivamente.  
  
> [!CAUTION]
>  Si edita el registro actual, asegúrese de guardar los cambios mediante una llamada a la **actualización** función de miembro antes de pasar a otro registro. Si se mueve a otro registro sin actualizar, los cambios se pierden sin advertencia.  
  
 Utilizando una de las operaciones de búsqueda no es el mismo que llamar a **MoveFirst** o `MoveNext`, sin embargo, que simplemente hace que el primer o siguiente registro actual sin especificar una condición. Puede seguir una operación de búsqueda con una operación de movimiento.  
  
 Tenga en cuenta lo siguiente al utilizar las operaciones de búsqueda:  
  
-   Si **buscar** devuelve distinto de cero, el registro actual no está definido. En este caso, debe colocar el puntero de registro actual hacia un registro válido.  
  
-   No puede utilizar una operación de búsqueda con un recordset de tipo snapshot de desplazamiento sólo hacia delante.  
  
-   Debe usar el formato de fecha de Estados Unidos (mes-año) cuando busca campos que contienen fechas, incluso si no está utilizando la versión de Estados Unidos del motor de base de datos de Microsoft Jet; de lo contrario, registros coincidentes pueden no encontrarse.  
  
-   Cuando se trabaja con grandes conjuntos de registros dinámicos y de bases de datos ODBC, puede descubrir que utilizan las operaciones de búsqueda es lento, especialmente cuando se trabaja con grandes conjuntos de registros. Puede mejorar el rendimiento mediante consultas SQL con personalizar **ORDERBY** o **donde** cláusulas, consultas de parámetros, o **CDaoQuerydef** objetos que recuperan registros indizados específicos.  
  
 Para obtener información relacionada, vea el tema "FindFirst, FindLast, FindNext, FindPrevious métodos" en la Ayuda de DAO.  
  
##  <a name="a-namefindnexta--cdaorecordsetfindnext"></a><a name="findnext"></a>CDaoRecordset::FindNext  
 Llame a esta función miembro para buscar el siguiente registro que coincide con una condición especificada.  
  
```  
BOOL FindNext(LPCTSTR lpszFilter);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszFilter`  
 Una expresión de cadena (como el **donde** cláusula en una instrucción SQL sin la palabra **donde**) utilizado para buscar el registro.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si se encuentran registros coincidentes, en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 El `FindNext` función miembro comienza su búsqueda en el registro actual y busca hasta el final del conjunto de registros.  
  
 Si desea incluir todos los registros en la búsqueda (no sólo los que cumplen una condición específica) usan una de las operaciones de desplazamiento para desplazarse por los registros. Para localizar un registro en un conjunto de registros de tipo de tabla, llame a la `Seek` función miembro.  
  
 Si no se encuentra ningún registro que cumpla los criterios, el puntero del registro actual es indeterminado, y `FindNext` devuelve cero. Si el conjunto de registros contiene más de un registro que satisface los criterios `FindFirst` localiza la primera aparición, `FindNext` busca la siguiente aparición y así sucesivamente.  
  
> [!CAUTION]
>  Si edita el registro actual, asegúrese de guardar los cambios mediante una llamada a la **actualización** función de miembro antes de pasar a otro registro. Si se mueve a otro registro sin actualizar, los cambios se pierden sin advertencia.  
  
 Utilizando una de las operaciones de búsqueda no es el mismo que llamar a **MoveFirst** o `MoveNext`, sin embargo, que simplemente hace que el primer o siguiente registro actual sin especificar una condición. Puede seguir una operación de búsqueda con una operación de movimiento.  
  
 Tenga en cuenta lo siguiente al utilizar las operaciones de búsqueda:  
  
-   Si **buscar** devuelve distinto de cero, el registro actual no está definido. En este caso, debe colocar el puntero de registro actual hacia un registro válido.  
  
-   No puede utilizar una operación de búsqueda con un recordset de tipo snapshot de desplazamiento sólo hacia delante.  
  
-   Debe usar el formato de fecha de Estados Unidos (mes-año) cuando busca campos que contienen fechas, incluso si no está utilizando la versión de Estados Unidos del motor de base de datos de Microsoft Jet; de lo contrario, registros coincidentes pueden no encontrarse.  
  
-   Cuando se trabaja con grandes conjuntos de registros dinámicos y de bases de datos ODBC, puede descubrir que utilizan las operaciones de búsqueda es lento, especialmente cuando se trabaja con grandes conjuntos de registros. Puede mejorar el rendimiento mediante consultas SQL con personalizar **ORDERBY** o **donde** cláusulas, consultas de parámetros, o **CDaoQuerydef** objetos que recuperan registros indizados específicos.  
  
 Para obtener información relacionada, vea el tema "FindFirst, FindLast, FindNext, FindPrevious métodos" en la Ayuda de DAO.  
  
##  <a name="a-namefindpreva--cdaorecordsetfindprev"></a><a name="findprev"></a>CDaoRecordset::FindPrev  
 Llame a esta función miembro para buscar el registro anterior que coincide con una condición especificada.  
  
```  
BOOL FindPrev(LPCTSTR lpszFilter);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszFilter`  
 Una expresión de cadena (como el **donde** cláusula en una instrucción SQL sin la palabra **donde**) utilizado para buscar el registro.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si se encuentran registros coincidentes, en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 El `FindPrev` función miembro comienza su búsqueda en el registro actual y busca hacia atrás hacia el principio del conjunto de registros.  
  
 Si desea incluir todos los registros en la búsqueda (no sólo los que cumplen una condición específica) usan una de las operaciones de desplazamiento para desplazarse por los registros. Para localizar un registro en un conjunto de registros de tipo de tabla, llame a la `Seek` función miembro.  
  
 Si no se encuentra ningún registro que cumpla los criterios, el puntero del registro actual es indeterminado, y `FindPrev` devuelve cero. Si el conjunto de registros contiene más de un registro que satisface los criterios `FindFirst` localiza la primera aparición, `FindNext` busca la siguiente aparición y así sucesivamente.  
  
> [!CAUTION]
>  Si edita el registro actual, asegúrese de guardar los cambios mediante una llamada a la **actualización** función de miembro antes de pasar a otro registro. Si se mueve a otro registro sin actualizar, los cambios se pierden sin advertencia.  
  
 Utilizando una de las operaciones de búsqueda no es el mismo que llamar a **MoveFirst** o `MoveNext`, sin embargo, que simplemente hace que el primer o siguiente registro actual sin especificar una condición. Puede seguir una operación de búsqueda con una operación de movimiento.  
  
 Tenga en cuenta lo siguiente al utilizar las operaciones de búsqueda:  
  
-   Si **buscar** devuelve distinto de cero, el registro actual no está definido. En este caso, debe colocar el puntero de registro actual hacia un registro válido.  
  
-   No puede utilizar una operación de búsqueda con un recordset de tipo snapshot de desplazamiento sólo hacia delante.  
  
-   Debe usar el formato de fecha de Estados Unidos (mes-año) cuando busca campos que contienen fechas, incluso si no está utilizando la versión de Estados Unidos del motor de base de datos de Microsoft Jet; de lo contrario, registros coincidentes pueden no encontrarse.  
  
-   Cuando se trabaja con grandes conjuntos de registros dinámicos y de bases de datos ODBC, puede descubrir que utilizan las operaciones de búsqueda es lento, especialmente cuando se trabaja con grandes conjuntos de registros. Puede mejorar el rendimiento mediante consultas SQL con personalizar **ORDERBY** o **donde** cláusulas, consultas de parámetros, o **CDaoQuerydef** objetos que recuperan registros indizados específicos.  
  
 Para obtener información relacionada, vea el tema "FindFirst, FindLast, FindNext, FindPrevious métodos" en la Ayuda de DAO.  
  
##  <a name="a-namegetabsolutepositiona--cdaorecordsetgetabsoluteposition"></a><a name="getabsoluteposition"></a>CDaoRecordset:: GetAbsolutePosition  
 Devuelve el número de registro del registro actual de un objeto recordset.  
  
```  
long GetAbsolutePosition();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Entero del 0 al número de registros en el conjunto de registros. Corresponde a la posición ordinal del registro actual en el conjunto de registros.  
  
### <a name="remarks"></a>Comentarios  
 El valor de la propiedad AbsolutePosition del objeto DAO subyacente está basado en cero; un valor de 0 hace referencia al primer registro del conjunto de registros. Puede determinar el número de registros rellenados en el conjunto de registros llamando a [GetRecordCount](#getrecordcount). Llamar a `GetRecordCount` puede tardar algún tiempo porque se deben tener acceso a todos los registros para determinar el recuento.  
  
 Si hay ningún registro actual, como cuando no hay ningún registro en el conjunto de registros, se devuelve 1. Si se elimina el registro actual, el valor de la propiedad AbsolutePosition no se define y MFC produce una excepción si se hace referencia. Para conjuntos de registros de tipo dinámico, se agregan nuevos registros al final de la secuencia.  
  
> [!NOTE]
>  Esta propiedad no pretende utilizar como un número de registro suplente. Los marcadores siguen siendo la forma recomendada de conservar y volver a una posición determinada y son la única manera de colocar el registro actual en todos los tipos de objetos de conjunto de registros. En particular, la posición de un registro determinado cambia cuando se eliminan registros anterior. También no hay ninguna garantía de que un determinado registro tendrá la misma posición absoluta si se vuelve a crear el conjunto de registros, porque no se garantiza el orden de los registros individuales dentro de un conjunto de registros, a menos que se cree con una instrucción SQL mediante un **ORDERBY** cláusula.  
  
> [!NOTE]
>  Esta función miembro es válida sólo para el tipo de conjunto de registros dinámicos y registros de tipo instantánea.  
  
 Para obtener información relacionada, vea el tema "AbsolutePosition (propiedad)" en la Ayuda de DAO.  
  
##  <a name="a-namegetbookmarka--cdaorecordsetgetbookmark"></a><a name="getbookmark"></a>CDaoRecordset:: GetBookmark  
 Llame a esta función miembro para obtener el valor de marcador en un registro concreto.  
  
```  
COleVariant GetBookmark();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un valor que representa el marcador en el registro actual.  
  
### <a name="remarks"></a>Comentarios  
 Cuando se crea o se abre un objeto recordset, cada uno de sus registros tiene ya un marcador único si es compatible con ellos. Llame a `CanBookmark` para determinar si un conjunto de registros admite marcadores.  
  
 Puede guardar el marcador del registro actual asignando el valor del marcador a un `COleVariant` objeto. Para poder volver rápidamente a ese registro después de moverse a otro registro, llamada `SetBookmark` con un parámetro que corresponde al valor de ese `COleVariant` objeto.  
  
> [!NOTE]
>  Llamar a [Requery](#requery) cambia marcadores DAO.  
  
 Para obtener información relacionada, vea el tema "Propiedades de marcador" en la Ayuda de DAO.  
  
##  <a name="a-namegetcachesizea--cdaorecordsetgetcachesize"></a><a name="getcachesize"></a>CDaoRecordset::GetCacheSize  
 Llame a esta función miembro para obtener el número de registros en caché.  
  
```  
long GetCacheSize();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor que especifica el número de registros en un conjunto de registros de tipo dinámico que contiene datos para almacenar en caché localmente desde un origen de datos ODBC.  
  
### <a name="remarks"></a>Comentarios  
 Datos en caché mejora el rendimiento de una aplicación que recupera datos de un servidor remoto a través de objetos de conjunto de registros de tipo dinámico. Una caché es un espacio en la memoria local que contiene los datos recuperados más recientemente desde el servidor en caso de que los datos volverá a solicitarse mientras se ejecuta la aplicación. Cuando se soliciten datos, el motor de base de datos Microsoft Jet comprueba primero la caché de los datos solicitados en lugar de recuperar desde el servidor, que tarda más tiempo. Datos que no proceden de un origen de datos no se guardan en la memoria caché.  
  
 Cualquier origen de datos ODBC, como una tabla asociada, puede tener una caché local.  
  
 Para obtener información relacionada, vea el tema "CacheSize, CacheStart (propiedades)" en la Ayuda de DAO.  
  
##  <a name="a-namegetcachestarta--cdaorecordsetgetcachestart"></a><a name="getcachestart"></a>CDaoRecordset::GetCacheStart  
 Llame a esta función miembro para obtener el valor de marcador del primer registro del conjunto de registros en la caché.  
  
```  
COleVariant GetCacheStart();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un `COleVariant` que especifica el marcador del primer registro en el conjunto de registros en la caché.  
  
### <a name="remarks"></a>Comentarios  
 El motor de base de datos Microsoft Jet solicita registros dentro del intervalo de la memoria caché de la memoria caché y solicita registros fuera del intervalo de la memoria caché del servidor.  
  
> [!NOTE]
>  Los registros recuperados de la caché no reflejan los cambios realizados al origen de datos por otros usuarios.  
  
 Para obtener información relacionada, vea el tema "CacheSize, CacheStart (propiedades)" en la Ayuda de DAO.  
  
##  <a name="a-namegetcurrentindexa--cdaorecordsetgetcurrentindex"></a><a name="getcurrentindex"></a>CDaoRecordset::GetCurrentIndex  
 Llame a esta función miembro para determinar el índice actualmente en uso en un tipo de tabla indizado `CDaoRecordset` objeto.  
  
```  
CString GetCurrentIndex();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un `CString` que contiene el nombre del índice actualmente en uso con un conjunto de registros de tipo de tabla. Devuelve una cadena vacía si no se ha establecido ningún índice.  
  
### <a name="remarks"></a>Comentarios  
 Este índice es la base para ordenar los registros en un conjunto de registros de tipo de tabla y usa el [Seek](#seek) función miembro para localizar los registros.  
  
 Un `CDaoRecordset` objeto puede tener más de un índice, pero puede utilizar un índice a la vez (aunque un [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md) objeto puede tener varios índices definidos en él).  
  
 Para obtener información relacionada, vea el tema "Objeto Index" y la definición de "índice actual" en la Ayuda de DAO.  
  
##  <a name="a-namegetdatecreateda--cdaorecordsetgetdatecreated"></a><a name="getdatecreated"></a>CDaoRecordset::GetDateCreated  
 Llame a esta función miembro para recuperar la fecha y hora de que creación de una tabla base.  
  
```  
COleDateTime GetDateCreated();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objeto que contiene la fecha y hora de creación de la tabla base.  
  
### <a name="remarks"></a>Comentarios  
 Configuración de fecha y hora se deriva del equipo en el que se creó la tabla base.  
  
 Para obtener información relacionada, vea el tema "DateCreated y LastUpdated propiedades" en la Ayuda de DAO.  
  
##  <a name="a-namegetdatelastupdateda--cdaorecordsetgetdatelastupdated"></a><a name="getdatelastupdated"></a>CDaoRecordset::GetDateLastUpdated  
 Llame a esta función miembro para recuperar la fecha y hora que se actualizó por última vez el esquema.  
  
```  
COleDateTime GetDateLastUpdated();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objeto que contiene la fecha y hora que se actualizó por última vez la estructura de la tabla base (esquema).  
  
### <a name="remarks"></a>Comentarios  
 Configuración de fecha y hora se deriva del equipo en el que se actualizó por última vez la estructura de la tabla base (esquema).  
  
 Para obtener información relacionada, vea el tema "DateCreated y LastUpdated propiedades" en la Ayuda de DAO.  
  
##  <a name="a-namegetdefaultdbnamea--cdaorecordsetgetdefaultdbname"></a><a name="getdefaultdbname"></a>CDaoRecordset::GetDefaultDBName  
 Llame a esta función miembro para determinar el nombre de la base de datos para este conjunto de registros.  
  
```  
virtual CString GetDefaultDBName();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un `CString` que contiene la ruta de acceso y el nombre de la base de datos que se deriva este conjunto de registros.  
  
### <a name="remarks"></a>Comentarios  
 Si se crea un conjunto de registros sin un puntero a un [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md), esta ruta de acceso se utiliza el conjunto de registros para abrir la base de datos predeterminada. De forma predeterminada, esta función devuelve una cadena vacía. Cuando ClassWizard deriva un nuevo conjunto de registros de `CDaoRecordset`, creará esta función por usted.  
  
 En el ejemplo siguiente se muestra el uso de la barra diagonal inversa doble (\\\\) en la cadena, según sea necesario interpretar correctamente la cadena.  
  
 [!code-cpp[NVC_MFCDatabase Nº&4;](../../mfc/codesnippet/cpp/cdaorecordset-class_4.cpp)]  
  
##  <a name="a-namegetdefaultsqla--cdaorecordsetgetdefaultsql"></a><a name="getdefaultsql"></a>CDaoRecordset::GetDefaultSQL  
 El marco de trabajo llama a esta función miembro para obtener la instrucción SQL de forma predeterminada en que se basa el conjunto de registros.  
  
```  
virtual CString GetDefaultSQL();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un `CString` que contiene la instrucción SQL predeterminada.  
  
### <a name="remarks"></a>Comentarios  
 Puede ser un nombre de tabla o una instancia de SQL **seleccione** instrucción.  
  
 Puede definir indirectamente la instrucción SQL predeterminada mediante la declaración de la clase de conjunto de registros con ClassWizard; ClassWizard realiza esta tarea por usted.  
  
 Si se pasa una cadena SQL null a [abiertos](#open), a continuación, llama a esta función para determinar el nombre de tabla o SQL para el conjunto de registros.  
  
##  <a name="a-namegeteditmodea--cdaorecordsetgeteditmode"></a><a name="geteditmode"></a>CDaoRecordset::GetEditMode  
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
|**dbEditAdd**|`AddNew`se ha llamado.|  
  
 Para obtener información relacionada, vea el tema "Propiedad EditMode" en la Ayuda de DAO.  
  
##  <a name="a-namegetfieldcounta--cdaorecordsetgetfieldcount"></a><a name="getfieldcount"></a>CDaoRecordset::GetFieldCount  
 Llame a esta función miembro para recuperar el número de campos (columnas) definido en el conjunto de registros.  
  
```  
short GetFieldCount();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de campos del conjunto de registros.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener información relacionada, vea el tema "Propiedad Count" en la Ayuda de DAO.  
  
##  <a name="a-namegetfieldinfoa--cdaorecordsetgetfieldinfo"></a><a name="getfieldinfo"></a>CDaoRecordset::GetFieldInfo  
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
 `nIndex`  
 Índice de base cero del campo predefinido en la colección de campos del conjunto de registros, para la búsqueda por índice.  
  
 `fieldinfo`  
 Una referencia a un [CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md) estructura.  
  
 `dwInfoOptions`  
 Opciones que especifican qué información sobre el conjunto de registros para recuperar. Las opciones disponibles se muestran aquí junto con lo que hacen que la función devuelva. Para obtener el mejor rendimiento, recuperar sólo el nivel de información que necesita:  
  
- `AFX_DAO_PRIMARY_INFO`(Valor predeterminado) Nombre, tipo, tamaño, atributos  
  
- `AFX_DAO_SECONDARY_INFO`La información principal, además de: posición Ordinal, necesaria, permitir cero tabla de origen de longitud, orden de intercalación, nombre externa, el campo de origen  
  
- `AFX_DAO_ALL_INFO`Información primaria y secundaria, además de: valor predeterminado, regla de validación, validación de texto  
  
 `lpszName`  
 Nombre del campo.  
  
### <a name="remarks"></a>Comentarios  
 Una versión de la función le permite buscar un campo por su índice. La otra versión le permite buscar un campo por su nombre.  
  
 Para obtener una descripción de la información devuelta, consulte el [CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md) estructura. Esta estructura no tiene miembros que corresponden a los elementos de información enumerados anteriormente en la descripción de `dwInfoOptions`. Cuando se solicita información de un nivel, obtendrá información de los niveles anteriores también.  
  
 Para obtener información relacionada, vea el tema "Propiedad Attributes" en la Ayuda de DAO.  
  
##  <a name="a-namegetfieldvaluea--cdaorecordsetgetfieldvalue"></a><a name="getfieldvalue"></a>CDaoRecordset:: GetFieldValue  
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
 Índice de base cero del campo en la colección de campos del conjunto de registros, para la búsqueda por índice.  
  
### <a name="return-value"></a>Valor devuelto  
 Las dos versiones de `GetFieldValue` que devuelven un valor devuelto una [COleVariant](../../mfc/reference/colevariant-class.md) objeto que contiene el valor de un campo.  
  
### <a name="remarks"></a>Comentarios  
 Puede buscar un campo por nombre o por posición ordinal.  
  
> [!NOTE]
>  Resulta más eficaz para llamar a una de las versiones de esta función miembro que toma un `COleVariant` referencia de objeto como un parámetro en lugar de llamar a una versión que devuelve un `COleVariant` objeto. Las versiones más recientes de esta función se conservan por compatibilidad con versiones anteriores.  
  
 Utilice `GetFieldValue` y [SetFieldValue](#setfieldvalue) para enlazar campos de forma dinámica en tiempo de ejecución en lugar de estáticamente columnas de enlace mediante la [DoFieldExchange](#dofieldexchange) mecanismo.  
  
 `GetFieldValue`y el `DoFieldExchange` mecanismo se puede combinar para mejorar el rendimiento. Por ejemplo, utilice `GetFieldValue` para recuperar un valor que necesita sólo a petición y asignar esa llamada a un botón "Más información" en la interfaz.  
  
 Para obtener información relacionada, vea los temas "Objeto Field" y "Valor de propiedad" en la Ayuda de DAO.  
  
##  <a name="a-namegetindexcounta--cdaorecordsetgetindexcount"></a><a name="getindexcount"></a>CDaoRecordset::GetIndexCount  
 Llame a esta función miembro para determinar el número de índices disponibles en el conjunto de registros de tipo de tabla.  
  
```  
short GetIndexCount();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de índices en el conjunto de registros de tipo de tabla.  
  
### <a name="remarks"></a>Comentarios  
 `GetIndexCount`es útil para recorrer en iteración todos los índices del conjunto de registros. Para ello, utilice `GetIndexCount` junto con [GetIndexInfo](#getindexinfo). Si se llama a esta función miembro de tipo dinámico o conjuntos de registros de tipo snapshot, MFC inicia una excepción.  
  
 Para obtener información relacionada, vea el tema "Propiedad Attributes" en la Ayuda de DAO.  
  
##  <a name="a-namegetindexinfoa--cdaorecordsetgetindexinfo"></a><a name="getindexinfo"></a>CDaoRecordset::GetIndexInfo  
 Llame a esta función miembro para obtener información acerca de un índice definido en la tabla base subyacente de un conjunto de registros de diferentes tipos.  
  
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
 Opciones que especifican qué información sobre el índice para recuperar. Las opciones disponibles se muestran aquí junto con lo que hacen que la función devuelva. Para obtener el mejor rendimiento, recuperar sólo el nivel de información que necesita:  
  
- `AFX_DAO_PRIMARY_INFO`(Valor predeterminado) Campos de nombre, información de campo  
  
- `AFX_DAO_SECONDARY_INFO`La información principal, además de: principal, Unique, Clustered, IgnoreNulls y necesario, externa  
  
- `AFX_DAO_ALL_INFO`Información primaria y secundaria, además de: Distinct Count  
  
 `lpszName`  
 Puntero al nombre del objeto de índice para la búsqueda por nombre.  
  
### <a name="remarks"></a>Comentarios  
 Una versión de la función le permite buscar un índice por su posición en la colección. La otra versión le permite buscar un índice por nombre.  
  
 Para obtener una descripción de la información devuelta, consulte el [CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md) estructura. Esta estructura no tiene miembros que corresponden a los elementos de información enumerados anteriormente en la descripción de `dwInfoOptions`. Cuando se solicita información de un nivel, obtendrá información de los niveles anteriores también.  
  
 Para obtener información relacionada, vea el tema "Propiedad Attributes" en la Ayuda de DAO.  
  
##  <a name="a-namegetlastmodifiedbookmarka--cdaorecordsetgetlastmodifiedbookmark"></a><a name="getlastmodifiedbookmark"></a>CDaoRecordset::GetLastModifiedBookmark  
 Llame a esta función miembro para recuperar el marcador del registro más recientemente agregado o actualizado.  
  
```  
COleVariant GetLastModifiedBookmark();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un `COleVariant` que contiene un marcador que indica el último registro agregado o modificado.  
  
### <a name="remarks"></a>Comentarios  
 Cuando se crea o se abre un objeto recordset, cada uno de sus registros tiene ya un marcador único si es compatible con ellos. Llame a [GetBookmark](#getbookmark) para determinar si el objeto recordset admite marcadores. Si el objeto recordset no admite marcadores, una `CDaoException` se inicia.  
  
 Cuando se agrega un registro, aparece al final del conjunto de registros y no es el registro actual. Para que el nuevo registro actual, llame a `GetLastModifiedBookmark` y, a continuación, llame a `SetBookmark` para regresar al registro recién agregado.  
  
 Para obtener información relacionada, vea el tema "Propiedad LastModified" en la Ayuda de DAO.  
  
##  <a name="a-namegetlockingmodea--cdaorecordsetgetlockingmode"></a><a name="getlockingmode"></a>CDaoRecordset::GetLockingMode  
 Llame a esta función miembro para determinar el tipo de bloqueo en vigor para el conjunto de registros.  
  
```  
BOOL GetLockingMode();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el tipo de bloqueo es pesimista, en caso contrario, 0 para bloqueo optimista registros.  
  
### <a name="remarks"></a>Comentarios  
 Cuando el bloqueo pesimista está activada, la página de datos que contiene el registro que está modificando está bloqueada en cuanto se llama a la [editar](#edit) función miembro. La página se desbloquea cuando se llama a la [actualización](#update) o [cerrar](#close) función miembro o cualquiera de las operaciones de mover o buscar.  
  
 Cuando está activado un bloqueo optimista, la página de datos que contiene el registro está bloqueada mientras se actualiza el registro con el **actualización** función miembro.  
  
 Al trabajar con orígenes de datos ODBC, el modo de bloqueo siempre es optimista.  
  
 Para obtener información relacionada, vea los temas "Propiedad LockEdits" y "Comportamiento de bloqueo en Multiuser Applications" en la Ayuda de DAO.  
  
##  <a name="a-namegetnamea--cdaorecordsetgetname"></a><a name="getname"></a>CDaoRecordset::GetName  
 Llame a esta función miembro para recuperar el nombre del conjunto de registros.  
  
```  
CString GetName();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un `CString` que contiene el nombre del conjunto de registros.  
  
### <a name="remarks"></a>Comentarios  
 El nombre del conjunto de registros debe comenzar con una letra y puede contener un máximo de 40 caracteres. Puede incluir números y caracteres de subrayado, pero no puede incluir signos de puntuación o espacios.  
  
 Para obtener información relacionada, vea el tema "Nombre de propiedad" en la Ayuda de DAO.  
  
##  <a name="a-namegetparamvaluea--cdaorecordsetgetparamvalue"></a><a name="getparamvalue"></a>CDaoRecordset::GetParamValue  
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
  
##  <a name="a-namegetpercentpositiona--cdaorecordsetgetpercentposition"></a><a name="getpercentposition"></a>CDaoRecordset:: GetPercentPosition  
 Cuando se trabaja con un tipo dinámico o un objeto recordset de instantánea, si se llama a `GetPercentPosition` antes de rellenar completamente el conjunto de registros, la cantidad de movimiento es relativo al número de registros que se tiene acceso como se indica mediante una llamada a [GetRecordCount](#getrecordcount).  
  
```  
float GetPercentPosition();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un número entre 0 y 100 que indica la ubicación aproximada del registro actual en el objeto de conjunto de registros basándose en un porcentaje de los registros del conjunto de registros.  
  
### <a name="remarks"></a>Comentarios  
 Puede mover al último registro mediante una llamada a [MoveLast](#movelast) para completar la población de todos los conjuntos de registros, pero esto puede tardar una cantidad considerable de tiempo.  
  
 Puede llamar a `GetPercentPosition` en los tres tipos de objetos de conjunto de registros, incluidas las tablas sin índices. Sin embargo, no puede llamar a `GetPercentPosition` en instantáneas de desplazamiento sólo hacia delante, o en un conjunto de registros abierto desde una consulta de paso a través en una base de datos externa. Si no hay ningún registro actual o se ha eliminado el registro actual de, un `CDaoException` se produce.  
  
 Para obtener información relacionada, vea el tema "PercentPosition (propiedad)" en la Ayuda de DAO.  
  
##  <a name="a-namegetrecordcounta--cdaorecordsetgetrecordcount"></a><a name="getrecordcount"></a>CDaoRecordset::GetRecordCount  
 Llame a esta función miembro para averiguar cuántos registros en un conjunto de registros se ha tenido acceso.  
  
```  
long GetRecordCount();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el número de registros que se obtiene acceso en un objeto recordset.  
  
### <a name="remarks"></a>Comentarios  
 `GetRecordCount`no indica el número de registros contenido en un tipo dinámico o el conjunto de registros de tipo snapshot hasta que todos los registros se ha tenido acceso. Esta llamada de función miembro puede tardar bastante tiempo en completarse.  
  
 Una vez que se ha accedido al último registro, el valor devuelto indica el número total de registros sin eliminar en el conjunto de registros. Para forzar el último registro que se tenga acceso, llame a la `MoveLast` o `FindLast` función de miembro para el conjunto de registros. También puede utilizar un recuento de SQL para determinar el número aproximado de registros que devolverá la consulta.  
  
 Como la aplicación elimina registros en un conjunto de registros de tipo dinámico, el valor devuelto de `GetRecordCount` disminuye. Sin embargo, los registros eliminados por otros usuarios no se reflejan en `GetRecordCount` hasta que el registro actual se coloca en un registro eliminado. Si ejecuta una transacción que afecta al número de registros y posteriormente deshace la transacción, `GetRecordCount` no reflejará el número real de los registros restantes.  
  
 El valor de `GetRecordCount` de un conjunto de registros de tipo snapshot no se ve afectado por los cambios en las tablas subyacentes.  
  
 El valor de `GetRecordCount` de un tipo de tabla recordset refleja el número aproximado de registros de la tabla y se ve afectada inmediatamente cuando se agregan o eliminan registros de la tabla.  
  
 Un conjunto de registros sin registros devuelve un valor de 0. Al trabajar con tablas adjuntas o bases de datos ODBC, `GetRecordCount` siempre devuelve – 1. Llamar a la **Requery** función miembro en un conjunto de registros restablece el valor de `GetRecordCount` como si se volviera a ejecutar la consulta.  
  
 Para obtener información relacionada, vea el tema "Propiedad RecordCount" en la Ayuda de DAO.  
  
##  <a name="a-namegetsqla--cdaorecordsetgetsql"></a><a name="getsql"></a>CDaoRecordset::GetSQL  
 Llame a esta función miembro para obtener la instrucción SQL que se utiliza para seleccionar registros del conjunto de registros cuando se abrió.  
  
```  
CString GetSQL() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un `CString` que contiene la instrucción SQL.  
  
### <a name="remarks"></a>Comentarios  
 Esto suele ser una instancia de SQL **seleccione** instrucción.  
  
 La cadena devuelta por `GetSQL` suele ser diferente de cualquier cadena que se pasó al conjunto de registros en la `lpszSQL` parámetro para la [abiertos](#open) función miembro. Esto es porque el conjunto de registros crea una instrucción de SQL completa basada en lo que pasó a **abiertos**, lo que se especificó con ClassWizard y que pueda haber especificado en el [m_strFilter](#m_strfilter) y [m_strSort](#m_strsort) miembros de datos.  
  
> [!NOTE]
>  Llame a esta función miembro sólo después de llamar a **abiertos**.  
  
 Para obtener información relacionada, vea el tema "Propiedad de SQL" en la Ayuda de DAO.  
  
##  <a name="a-namegettypea--cdaorecordsetgettype"></a><a name="gettype"></a>CDaoRecordset::GetType  
 Llame a esta función miembro después de abrir el conjunto de registros para determinar el tipo del objeto recordset.  
  
```  
short GetType();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Uno de los siguientes valores que indica el tipo de un conjunto de registros:  
  
- **dbOpenTable** recordset de tipo de tabla  
  
- **dbOpenDynaset** registros de tipo dinámico  
  
- **dbOpenSnapshot** recordset de tipo Snapshot  
  
### <a name="remarks"></a>Comentarios  
 Para obtener información relacionada, vea el tema "Tipo de propiedad" en la Ayuda de DAO.  
  
##  <a name="a-namegetvalidationrulea--cdaorecordsetgetvalidationrule"></a><a name="getvalidationrule"></a>CDaoRecordset::GetValidationRule  
 Llame a esta función miembro para determinar la regla utilizada para validar los datos.  
  
```  
CString GetValidationRule();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un `CString` objeto que contiene un valor que valida los datos de un registro cuando se cambia o se agrega a una tabla.  
  
### <a name="remarks"></a>Comentarios  
 Esta regla está basado en texto y se aplica cada vez que cambia la tabla subyacente. Si los datos no están legales, MFC inicia una excepción. El mensaje de error devuelto es el texto de la propiedad texto de validación del objeto campo subyacente, si se especifica, o el texto de la expresión especificada por la propiedad ValidationRule del objeto campo subyacente. Puede llamar a [GetValidationText](#getvalidationtext) para obtener el texto del mensaje de error.  
  
 Por ejemplo, un campo de un registro que requiere el día del mes podría tener una regla de validación como "día entre 1 y 31."  
  
 Para obtener información relacionada, vea el tema "Propiedad ValidationRule" en la Ayuda de DAO.  
  
##  <a name="a-namegetvalidationtexta--cdaorecordsetgetvalidationtext"></a><a name="getvalidationtext"></a>CDaoRecordset::GetValidationText  
 Llame a esta función miembro para recuperar el texto de la propiedad texto de validación del objeto campo subyacente.  
  
```  
CString GetValidationText();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un `CString` que contiene el texto del mensaje que se muestra si el valor de un campo no cumplen la regla de validación del objeto campo subyacente del objeto.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener información relacionada, vea el tema "Propiedad texto de validación" en la Ayuda de DAO.  
  
##  <a name="a-nameisbofa--cdaorecordsetisbof"></a><a name="isbof"></a>CDaoRecordset::IsBOF  
 Llame a esta función miembro antes de desplazarse de registro a registro para saber si han pasado antes del primer registro del conjunto de registros.  
  
```  
BOOL IsBOF() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el conjunto de registros no contiene registros o si se ha desplazado hacia atrás antes del primer registro; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 También puede llamar a `IsBOF` junto con `IsEOF` para determinar si el conjunto de registros contiene registros o está vacío. Inmediatamente después de llamar a **abiertos**, si el objeto recordset no contiene registros, `IsBOF` devuelve distinto de cero. Al abrir un conjunto de registros que tiene al menos un registro, el primer registro es el registro actual y `IsBOF` devuelve 0.  
  
 Si el primer registro es el registro actual y se llama `MovePrev`, `IsBOF` posteriormente devolverá distinto de cero. Si `IsBOF` devuelve distinto de cero y se llama a `MovePrev`, se produce una excepción. Si `IsBOF` devuelve distinto de cero, el registro actual está indefinido y cualquier acción que requiere un registro actual se producirá una excepción.  
  
 Efecto de los métodos específicos de `IsBOF` y `IsEOF` configuración:  
  
-   Llamar a **abiertos** internamente establece el primer registro del conjunto de registros del registro actual mediante una llamada a **MoveFirst**. Por consiguiente, llamar **abiertos** en un conjunto vacío de causas de registros `IsBOF` y `IsEOF` para devolver distinto de cero. (Consulte la siguiente tabla para el comportamiento de un error **MoveFirst** o `MoveLast` llamada.)  
  
-   Todas las operaciones de movimiento que busque correctamente un registro hacen ambos `IsBOF` y `IsEOF` para devolver 0.  
  
-   Un `AddNew` llamada seguida de un **actualización** hará que la llamada que inserta correctamente un nuevo registro `IsBOF` para devolver 0, pero solo si `IsEOF` ya es distinto de cero. El estado de `IsEOF` siempre permanecerá sin cambios. Tal como se define por el motor de base de datos Microsoft Jet, el puntero de registro actual de un objeto recordset vacío es al final de un archivo, por lo que se inserta cualquier nuevo registro después del registro actual.  
  
-   Cualquier **eliminar** llamada, incluso si se quita el único registro de un conjunto de registros, no cambiará el valor de `IsBOF` o `IsEOF`.  
  
 Esta tabla muestra las operaciones de movimiento permitidas con diferentes combinaciones de `IsBOF` /  `IsEOF`.  
  
||MoveFirst, MoveLast|MovePrev,<br /><br /> Mover< 0></ 0>|Mover 0|MoveNext,<br /><br /> Mover > 0|  
|------|-------------------------|-----------------------------|------------|-----------------------------|  
|`IsBOF`= distinto de cero,<br /><br /> `IsEOF`=0|Permitido|Excepción|Excepción|Permitido|  
|`IsBOF`=0,<br /><br /> `IsEOF`= distinto de cero|Permitido|Permitido|Excepción|Excepción|  
|Ambos es distinto de cero|Excepción|Excepción|Excepción|Excepción|  
|0|Permitido|Permitido|Permitido|Permitido|  
  
 Permitir que una operación de movimiento no significa que la operación busque correctamente un registro. Simplemente indica que un intento de realizar la operación de desplazamiento especificada se permite y no se generará una excepción. El valor de la `IsBOF` y `IsEOF` funciones miembro pueden cambiar como resultado del intento de move.  
  
 El efecto de las operaciones de desplazamiento que no encuentra un registro en el valor de `IsBOF` y `IsEOF` en la tabla siguiente se muestra la configuración.  
  
||IsBOF|IsEOF|  
|------|-----------|-----------|  
|**MoveFirst**,`MoveLast`|Es distinto de cero|Es distinto de cero|  
|**Mover** 0|Sin cambios|Sin cambios|  
|`MovePrev`, **Move**< 0></ 0>|Es distinto de cero|Sin cambios|  
|`MoveNext`, **Move** > 0|Sin cambios|Es distinto de cero|  
  
 Para obtener información relacionada, vea el tema "Propiedades BOF y EOF" en la Ayuda de DAO.  
  
##  <a name="a-nameisdeleteda--cdaorecordsetisdeleted"></a><a name="isdeleted"></a>CDaoRecordset::IsDeleted  
 Llame a esta función miembro para determinar si se ha eliminado el registro actual.  
  
```  
BOOL IsDeleted() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el conjunto de registros está situado en un registro eliminado. en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Si se desplaza a un registro y `IsDeleted` devuelve **TRUE** (cero), a continuación, se debe desplazar a otro registro para poder realizar otras operaciones de conjunto de registros.  
  
> [!NOTE]
>  No es necesario comprobar el estado eliminado de registros en un conjunto de registros de tipo de tabla o de instantáneas. Porque no se puede eliminar registros de una instantánea, no hay ninguna necesidad de llamar a `IsDeleted`. Para conjuntos de registros de tipo de tabla, los registros eliminados se quitan realmente del conjunto de registros. Una vez eliminado un registro, por otro usuario, o en otro conjunto de registros, no puede desplazarse a ese registro. Por lo tanto, no es necesario llamar a `IsDeleted`.  
  
 Cuando se elimina un registro de un conjunto de registros dinámicos, se quita del conjunto de registros y no podrá volver a ese registro. Sin embargo, si un registro en un conjunto de registros dinámicos se elimina por otro usuario o en otro conjunto de registros basándose en la misma tabla, `IsDeleted` devolverá **TRUE** al más adelante desplazarse a ese registro.  
  
 Para obtener información relacionada, vea los temas "Método Delete", "Propiedad LastModified" y "Propiedad EditMode" en la Ayuda de DAO.  
  
##  <a name="a-nameiseofa--cdaorecordsetiseof"></a><a name="iseof"></a>CDaoRecordset::IsEOF  
 Llame a esta función miembro mientras se desplaza de registro a registro para saber si se fue más allá del último registro del conjunto de registros.  
  
```  
BOOL IsEOF() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el conjunto de registros no contiene registros o si se ha desplazado más allá del último registro; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 También puede llamar a `IsEOF` para determinar si el conjunto de registros contiene registros o está vacío. Inmediatamente después de llamar a **abiertos**, si el objeto recordset no contiene registros, `IsEOF` devuelve distinto de cero. Al abrir un conjunto de registros que tiene al menos un registro, el primer registro es el registro actual y `IsEOF` devuelve 0.  
  
 Si el último registro es el registro actual cuando se llama a `MoveNext`, `IsEOF` posteriormente devolverá distinto de cero. Si `IsEOF` devuelve distinto de cero y se llama a `MoveNext`, se produce una excepción. Si `IsEOF` devuelve distinto de cero, el registro actual está indefinido y cualquier acción que requiere un registro actual se producirá una excepción.  
  
 Efecto de los métodos específicos de `IsBOF` y `IsEOF` configuración:  
  
-   Llamar a **abiertos** internamente establece el primer registro del conjunto de registros del registro actual mediante una llamada a **MoveFirst**. Por consiguiente, llamar **abiertos** en un conjunto vacío de causas de registros `IsBOF` y `IsEOF` para devolver distinto de cero. (Consulte la siguiente tabla para el comportamiento de un error **MoveFirst** llamada.)  
  
-   Todas las operaciones de movimiento que busque correctamente un registro hacen ambos `IsBOF` y `IsEOF` para devolver 0.  
  
-   Un `AddNew` llamada seguida de un **actualización** hará que la llamada que inserta correctamente un nuevo registro `IsBOF` para devolver 0, pero solo si `IsEOF` ya es distinto de cero. El estado de `IsEOF` siempre permanecerá sin cambios. Tal como se define por el motor de base de datos Microsoft Jet, el puntero de registro actual de un objeto recordset vacío es al final de un archivo, por lo que se inserta cualquier nuevo registro después del registro actual.  
  
-   Cualquier **eliminar** llamada, incluso si se quita el único registro de un conjunto de registros, no cambiará el valor de `IsBOF` o `IsEOF`.  
  
 Esta tabla muestra las operaciones de movimiento permitidas con diferentes combinaciones de `IsBOF` /  `IsEOF`.  
  
||MoveFirst, MoveLast|MovePrev,<br /><br /> Mover< 0></ 0>|Mover 0|MoveNext,<br /><br /> Mover > 0|  
|------|-------------------------|-----------------------------|------------|-----------------------------|  
|`IsBOF`= distinto de cero,<br /><br /> `IsEOF`=0|Permitido|Excepción|Excepción|Permitido|  
|`IsBOF`=0,<br /><br /> `IsEOF`= distinto de cero|Permitido|Permitido|Excepción|Excepción|  
|Ambos es distinto de cero|Excepción|Excepción|Excepción|Excepción|  
|0|Permitido|Permitido|Permitido|Permitido|  
  
 Permitir que una operación de movimiento no significa que la operación busque correctamente un registro. Simplemente indica que un intento de realizar la operación de desplazamiento especificada se permite y no se generará una excepción. El valor de la `IsBOF` y `IsEOF` funciones miembro pueden cambiar como resultado del intento de Move.  
  
 El efecto de las operaciones de desplazamiento que no encuentra un registro en el valor de `IsBOF` y `IsEOF` en la tabla siguiente se muestra la configuración.  
  
||IsBOF|IsEOF|  
|------|-----------|-----------|  
|**MoveFirst**,`MoveLast`|Es distinto de cero|Es distinto de cero|  
|**Mover** 0|Sin cambios|Sin cambios|  
|`MovePrev`, **Move**< 0></ 0>|Es distinto de cero|Sin cambios|  
|`MoveNext`, **Move** > 0|Sin cambios|Es distinto de cero|  
  
 Para obtener información relacionada, vea el tema "Propiedades BOF y EOF" en la Ayuda de DAO.  
  
##  <a name="a-nameisfielddirtya--cdaorecordsetisfielddirty"></a><a name="isfielddirty"></a>CDaoRecordset::IsFieldDirty  
 Llame a esta función miembro determinar si el miembro de datos del campo especificado de un conjunto de registros dinámicos se ha marcado como "dirty" (modificado).  
  
```  
BOOL IsFieldDirty(void* pv);
```  
  
### <a name="parameters"></a>Parámetros  
 `pv`  
 Un puntero a miembro de datos del campo cuyo estado desea comprobar, o **NULL** para determinar si cualquiera de los campos modificado.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el miembro de datos del campo especificado está marcado como modificado; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Los datos de todos los miembros de datos de campo modificados se transferirá al registro en el origen de datos cuando se actualiza el registro actual mediante una llamada a la **actualización** función miembro de `CDaoRecordset` (después de una llamada a **editar** o `AddNew`). Con este conocimiento, puede realizar más pasos, como quitar marcadores el miembro de datos de campo para marcar la columna, por lo que no se escribirán en el origen de datos.  
  
 `IsFieldDirty`se implementa a través de `DoFieldExchange`.  
  
##  <a name="a-nameisfieldnulla--cdaorecordsetisfieldnull"></a><a name="isfieldnull"></a>CDaoRecordset::IsFieldNull  
 Llame a esta función miembro para determinar si el miembro de datos del campo especificado de un conjunto de registros se ha marcado como Null.  
  
```  
BOOL IsFieldNull(void* pv);
```  
  
### <a name="parameters"></a>Parámetros  
 `pv`  
 Un puntero a miembro de datos del campo cuyo estado desea comprobar, o **NULL** para determinar si cualquiera de los campos son Null.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el miembro de datos del campo especificado está marcado como Null; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 (En la terminología de base de datos, Null significa "no tener ningún valor" y no es igual a **NULL** en C++.) Si un miembro de datos de campo se marca como Null, se interpreta como una columna del registro actual para el que no hay ningún valor.  
  
> [!NOTE]
>  En determinadas situaciones, con `IsFieldNull` puede ser ineficaz, como se muestra en el ejemplo de código siguiente:  
  
 [!code-cpp[NVC_MFCDatabase&#5;](../../mfc/codesnippet/cpp/cdaorecordset-class_5.cpp)]  
  
> [!NOTE]
>  Si se utiliza un enlace de registro dinámico, sin derivar de `CDaoRecordset`, procure usar **VT_NULL** tal como se muestra en el ejemplo.  
  
##  <a name="a-nameisfieldnullablea--cdaorecordsetisfieldnullable"></a><a name="isfieldnullable"></a>CDaoRecordset::IsFieldNullable  
 Llame a esta función miembro determinar si el miembro de datos del campo especificado es "que aceptan valores null" (se puede establecer en un valor Null; C++ **NULL** no es igual a Null, lo que, en la terminología de base de datos, significa "no having ningún valor").  
  
```  
BOOL IsFieldNullable(void* pv);
```  
  
### <a name="parameters"></a>Parámetros  
 `pv`  
 Un puntero a miembro de datos del campo cuyo estado desea comprobar, o **NULL** para determinar si cualquiera de los campos son Null.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el miembro de datos del campo especificado puede ser Null; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Un campo que no puede ser Null debe tener un valor. Si se intenta establecer este campo en Null cuando se agrega o actualiza un registro, el origen de datos rechaza la adición o la actualización, y **actualizar** generará una excepción. La excepción se produce cuando se llama a **actualización**, no cuando se llama a `SetFieldNull`.  
  
##  <a name="a-nameisopena--cdaorecordsetisopen"></a><a name="isopen"></a>CDaoRecordset::IsOpen  
 Llame a esta función miembro para determinar si el conjunto de registros está abierto.  
  
```  
BOOL IsOpen() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el objeto recordset **abiertos** o **Requery** función miembro se ha llamado anteriormente y no se ha cerrado el conjunto de registros; de lo contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namembcheckcachefordirtyfieldsa--cdaorecordsetmbcheckcachefordirtyfields"></a><a name="m_bcheckcachefordirtyfields"></a>CDaoRecordset:: M_bcheckcachefordirtyfields  
 Contiene una marca que indica si los campos almacenados en caché se marcan automáticamente como desfasada (modificados) y Null.  
  
### <a name="remarks"></a>Comentarios  
 La marca de forma predeterminada es **TRUE**. El valor de este miembro de datos controla todo el mecanismo de doble búfer. Si se establece la marca en **TRUE**, puede desactivar el almacenamiento en caché en función de campo por campo mediante el mecanismo DFX. Si se establece la marca en **FALSE**, debe llamar a `SetFieldDirty` y `SetFieldNull` usted mismo.  
  
 Establecer este miembro de datos antes de llamar a **abiertos**. Este mecanismo es principalmente para facilidad de uso. Rendimiento puede ser menor debido a que el búfer doble de campos cuando se realizan cambios.  
  
##  <a name="a-namemnfieldsa--cdaorecordsetmnfields"></a><a name="m_nfields"></a>CDaoRecordset::m_nFields  
 Contiene el número de miembros de datos de campo en la clase de conjunto de registros y el número de columnas seleccionadas por el conjunto de registros del origen de datos.  
  
### <a name="remarks"></a>Comentarios  
 Debe inicializar el constructor de la clase de conjunto de registros `m_nFields` con el número correcto de campos enlazados estáticamente. ClassWizard escribe esta inicialización cuando se utiliza para declarar la clase de conjunto de registros. También puede escribir manualmente.  
  
 El marco de trabajo utiliza este número para administrar la interacción entre los miembros de datos de campo y las columnas correspondientes del registro actual en el origen de datos.  
  
> [!NOTE]
>  Este número debe corresponder al número de columnas de salida registrado en `DoFieldExchange` después de llamar a `SetFieldType` con el parámetro **CDaoFieldExchange:: outputColumn**.  
  
 Puede enlazar columnas dinámicamente por medio de `CDaoRecordset::GetFieldValue` y `CDaoRecordset::SetFieldValue`. Si lo hace, no es necesario incrementar el recuento de `m_nFields` para reflejar el número de función DFX llamadas su `DoFieldExchange` función miembro.  
  
##  <a name="a-namemnparamsa--cdaorecordsetmnparams"></a><a name="m_nparams"></a>CDaoRecordset::m_nParams  
 Contiene el número de miembros de datos de parámetro en la clase de conjunto de registros: el número de parámetros pasado con la consulta.  
  
### <a name="remarks"></a>Comentarios  
 Si la clase de conjunto de registros tiene miembros de datos de parámetro, debe inicializar el constructor de la clase `m_nParams` con el número correcto. El valor de `m_nParams` el valor predeterminado es 0. Si agrega miembros de datos de parámetro, lo que debe hacer manualmente, debe agregar manualmente una inicialización en el constructor de clase para reflejar el número de parámetros (que debe ser al menos tan grande como el número de '' marcadores de posición en su **m_strFilter** o `m_strSort` cadena).  
  
 El marco de trabajo utiliza este número cuando parametriza la consulta.  
  
> [!NOTE]
>  Este número debe corresponder al número de "params" registrado en `DoFieldExchange` después de llamar a `SetFieldType` con el parámetro **CFieldExchange::param**.  
  
 Para obtener información relacionada, vea el tema "Objeto de parámetro" en la Ayuda de DAO.  
  
##  <a name="a-namempdaorecordseta--cdaorecordsetmpdaorecordset"></a><a name="m_pdaorecordset"></a>CDaoRecordset::m_pDAORecordset  
 Contiene un puntero a la interfaz OLE para el objeto de conjunto de registros DAO subyacente la `CDaoRecordset` objeto.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este puntero si necesita tener acceso directamente a la interfaz DAO.  
  
 Para obtener información relacionada, vea el tema "Objeto Recordset" en la Ayuda de DAO.  
  
##  <a name="a-namempdatabasea--cdaorecordsetmpdatabase"></a><a name="m_pdatabase"></a>CDaoRecordset::m_pDatabase  
 Contiene un puntero a la `CDaoDatabase` a través del cual el conjunto de registros está conectado a un origen de datos del objeto.  
  
### <a name="remarks"></a>Comentarios  
 Esta variable se establece en dos formas. Normalmente, debe pasar un puntero a ya estaba abierto `CDaoDatabase` cuando se construye el objeto recordset de objetos. Si se pasa **NULL** en su lugar, **CDaoRecordset** crea un `CDaoDatabase` objeto y lo abre. En cualquier caso, `CDaoRecordset` almacena el puntero en esta variable.  
  
 Normalmente, no directamente necesitará utilizar el puntero almacenado en **m_pDatabase**. Si escribe sus propias extensiones al `CDaoRecordset`, sin embargo, debe utilizar el puntero. Por ejemplo, tendrá que el puntero si produce su propio `CDaoException`(s).  
  
 Para obtener información relacionada, vea el tema "Objeto de base de datos" en la Ayuda de DAO.  
  
##  <a name="a-namemstrfiltera--cdaorecordsetmstrfilter"></a><a name="m_strfilter"></a>CDaoRecordset:: M_strfilter  
 Contiene una cadena que se utiliza para construir el **donde** cláusula de una instrucción SQL.  
  
### <a name="remarks"></a>Comentarios  
 No incluye la palabra reservada **donde** para filtrar el conjunto de registros. El uso de este miembro de datos no es aplicable a los conjuntos de registros de tipo de tabla. El uso de **m_strFilter** no tiene ningún efecto cuando se abre un conjunto de registros utilizando un `CDaoQueryDef` puntero.  
  
 Utilice el formato de fecha de Estados Unidos (mes-año) cuando filtre campos que contienen fechas, incluso si no está utilizando la versión de Estados Unidos del motor de base de datos de Microsoft Jet; de lo contrario, no se pueden filtrar los datos como se espera.  
  
 Para obtener información relacionada, vea el tema "Propiedad Filter" en la Ayuda de DAO.  
  
##  <a name="a-namemstrsorta--cdaorecordsetmstrsort"></a><a name="m_strsort"></a>CDaoRecordset::m_strSort  
 Contiene una cadena que contiene el **ORDERBY** cláusula de una instrucción SQL sin las palabras reservadas **ORDERBY**.  
  
### <a name="remarks"></a>Comentarios  
 Puede ordenar en objetos de conjunto de registros de tipo dynaset y snapshot.  
  
 No se puede ordenar los objetos de conjunto de registros de tipo de tabla. Para determinar el criterio de ordenación de un conjunto de registros de tipo de tabla, llame a [SetCurrentIndex](#setcurrentindex).  
  
 El uso de `m_strSort` no tiene ningún efecto cuando se abre un conjunto de registros utilizando un `CDaoQueryDef` puntero.  
  
 Para obtener información relacionada, vea el tema "Propiedad de ordenación" en la Ayuda de DAO.  
  
##  <a name="a-namemovea--cdaorecordsetmove"></a><a name="move"></a>CDaoRecordset:: Move  
 Llame a esta función miembro para colocar el conjunto de registros `lRows` registros del registro actual.  
  
```  
virtual void Move(long lRows);
```  
  
### <a name="parameters"></a>Parámetros  
 `lRows`  
 El número de registros hacia adelante o hacia atrás. Los valores positivos mueven hacia delante, hacia el final del conjunto de registros. Valores negativos la mueven hacia atrás y hacia el principio.  
  
### <a name="remarks"></a>Comentarios  
 Puede mover hacia delante o hacia atrás. `Move( 1 )`es equivalente a `MoveNext`, y `Move( -1 )` es equivalente a `MovePrev`.  
  
> [!CAUTION]
>  Llamar a cualquiera de los **mover** funciones produce una excepción si el objeto recordset no tiene registros. En general, llame a ambos `IsBOF` y `IsEOF` antes de una operación de movimiento para determinar si el conjunto de registros tiene todos los registros. Después de llamar a **abiertos** o **Requery**, llame a `IsBOF` o `IsEOF`.  
  
> [!NOTE]
>  Si se ha desplazado más allá del principio o al final del conjunto de registros ( `IsBOF` o `IsEOF` devuelve distinto de cero), una llamada a **mover** produce una `CDaoException`.  
  
> [!NOTE]
>  Si se llama a cualquiera de los **mover** funciona mientras el registro actual se actualiza o agregado, las actualizaciones se pierden sin advertencia.  
  
 Cuando se llama a **mover** en una instantánea con desplazamiento sólo hacia delante, la `lRows` parámetro debe ser un entero positivo y no se permiten marcadores para poder avanzar solo.  
  
 Para hacer que la primera, última, siguiente o anterior registro en un conjunto de registros la llamada actual de registros, el **MoveFirst**, `MoveLast`, `MoveNext`, o `MovePrev` función miembro.  
  
 Para obtener información relacionada, vea los temas "Método Move" y "MoveFirst, MoveLast, MoveNext, MovePrevious métodos" en la Ayuda de DAO.  
  
##  <a name="a-namemovefirsta--cdaorecordsetmovefirst"></a><a name="movefirst"></a>CDaoRecordset::MoveFirst  
 Llame a esta función miembro para realizar el primer registro del conjunto de registros (si existe) del registro actual.  
  
```  
void MoveFirst();
```  
  
### <a name="remarks"></a>Comentarios  
 No es necesario llamar a **MoveFirst** inmediatamente después de abrir el conjunto de registros. En ese momento, el primer registro (si existe) es automáticamente el registro actual.  
  
> [!CAUTION]
>  Llamar a cualquiera de los **mover** funciones produce una excepción si el objeto recordset no tiene registros. En general, llame a ambos `IsBOF` y `IsEOF` antes de una operación de movimiento para determinar si el conjunto de registros tiene todos los registros. Después de llamar a **abiertos** o **Requery**, llame a `IsBOF` o `IsEOF`.  
  
> [!NOTE]
>  Si se llama a cualquiera de los **mover** funciona mientras el registro actual se actualiza o agregado, las actualizaciones se pierden sin advertencia.  
  
 Utilice la **mover** funciones para desplazarse por los registros sin aplicar una condición. Utilice las operaciones de búsqueda para localizar los registros en un tipo dinámico o un objeto recordset de tipo snapshot que satisface una condición determinada. Para localizar un registro en un objeto de conjunto de registros de tipo de tabla, llame a `Seek`.  
  
 Si el conjunto de registros hace referencia a un conjunto de registros de tipo de tabla, desplazamiento sigue el índice actual de la tabla. Puede establecer el índice actual mediante la propiedad de índice del objeto DAO subyacente. Si no establece el índice actual, el orden de los registros devueltos es indefinido.  
  
 Si se llama a `MoveLast` en un objeto recordset basado en una consulta SQL o la definición de consulta, la consulta se forzará la finalización y el objeto recordset está completamente lleno.  
  
 No se puede llamar el **MoveFirst** o `MovePrev` función miembro con una instantánea con desplazamiento sólo hacia delante.  
  
 Para mover la posición del actual registro de un objeto de conjunto de registros un determinado número de registros hacia delante o hacia atrás, llame a **mover**.  
  
 Para obtener información relacionada, vea los temas "Método Move" y "MoveFirst, MoveLast, MoveNext, MovePrevious métodos" en la Ayuda de DAO.  
  
##  <a name="a-namemovelasta--cdaorecordsetmovelast"></a><a name="movelast"></a>CDaoRecordset::MoveLast  
 Llame a esta función miembro para hacer del último registro (si existe) en el registro actual del conjunto de registros.  
  
```  
void MoveLast();
```  
  
### <a name="remarks"></a>Comentarios  
  
> [!CAUTION]
>  Llamar a cualquiera de los **mover** funciones produce una excepción si el objeto recordset no tiene registros. En general, llame a ambos `IsBOF` y `IsEOF` antes de una operación de movimiento para determinar si el conjunto de registros tiene todos los registros. Después de llamar a **abiertos** o **Requery**, llame a `IsBOF` o `IsEOF`.  
  
> [!NOTE]
>  Si se llama a cualquiera de los **mover** funciona mientras el registro actual se actualiza o agregado, las actualizaciones se pierden sin advertencia.  
  
 Utilice la **mover** funciones para desplazarse por los registros sin aplicar una condición. Utilice las operaciones de búsqueda para localizar los registros en un tipo dinámico o un objeto recordset de tipo snapshot que satisface una condición determinada. Para localizar un registro en un objeto de conjunto de registros de tipo de tabla, llame a `Seek`.  
  
 Si el conjunto de registros hace referencia a un conjunto de registros de tipo de tabla, desplazamiento sigue el índice actual de la tabla. Puede establecer el índice actual mediante la propiedad de índice del objeto DAO subyacente. Si no establece el índice actual, el orden de los registros devueltos es indefinido.  
  
 Si se llama a `MoveLast` en un objeto recordset basado en una consulta SQL o la definición de consulta, la consulta se forzará la finalización y el objeto recordset está completamente lleno.  
  
 Para mover la posición del actual registro de un objeto de conjunto de registros un determinado número de registros hacia delante o hacia atrás, llame a **mover**.  
  
 Para obtener información relacionada, vea los temas "Método Move" y "MoveFirst, MoveLast, MoveNext, MovePrevious métodos" en la Ayuda de DAO.  
  
##  <a name="a-namemovenexta--cdaorecordsetmovenext"></a><a name="movenext"></a>CDaoRecordset::MoveNext  
 Llame a esta función miembro para realizar el registro siguiente en el registro actual del conjunto de registros.  
  
```  
void MoveNext();
```  
  
### <a name="remarks"></a>Comentarios  
 Se recomienda que llame a `IsBOF` antes de intentar mover al registro anterior. Una llamada a `MovePrev` producirá un `CDaoException` si `IsBOF` devuelve distinto de cero, que indica que ya se haya desplazado antes del primer registro o que no se seleccionaron registros por el conjunto de registros.  
  
> [!CAUTION]
>  Llamar a cualquiera de los **mover** funciones produce una excepción si el objeto recordset no tiene registros. En general, llame a ambos `IsBOF` y `IsEOF` antes de una operación de movimiento para determinar si el conjunto de registros tiene todos los registros. Después de llamar a **abiertos** o **Requery**, llame a `IsBOF` o `IsEOF`.  
  
> [!NOTE]
>  Si se llama a cualquiera de los **mover** funciona mientras el registro actual se actualiza o agregado, las actualizaciones se pierden sin advertencia.  
  
 Utilice la **mover** funciones para desplazarse por los registros sin aplicar una condición. Utilice las operaciones de búsqueda para localizar los registros en un tipo dinámico o un objeto recordset de tipo snapshot que satisface una condición determinada. Para localizar un registro en un objeto de conjunto de registros de tipo de tabla, llame a `Seek`.  
  
 Si el conjunto de registros hace referencia a un conjunto de registros de tipo de tabla, desplazamiento sigue el índice actual de la tabla. Puede establecer el índice actual mediante la propiedad de índice del objeto DAO subyacente. Si no establece el índice actual, el orden de los registros devueltos es indefinido.  
  
 Para mover la posición del actual registro de un objeto de conjunto de registros un determinado número de registros hacia delante o hacia atrás, llame a **mover**.  
  
 Para obtener información relacionada, vea los temas "Método Move" y "MoveFirst, MoveLast, MoveNext, MovePrevious métodos" en la Ayuda de DAO.  
  
##  <a name="a-namemovepreva--cdaorecordsetmoveprev"></a><a name="moveprev"></a>CDaoRecordset::MovePrev  
 Llame a esta función miembro para realizar el registro anterior del conjunto de registros del registro actual.  
  
```  
void MovePrev();
```  
  
### <a name="remarks"></a>Comentarios  
 Se recomienda que llame a `IsBOF` antes de intentar mover al registro anterior. Una llamada a `MovePrev` producirá un `CDaoException` si `IsBOF` devuelve distinto de cero, que indica que ya se haya desplazado antes del primer registro o que no se seleccionaron registros por el conjunto de registros.  
  
> [!CAUTION]
>  Llamar a cualquiera de los **mover** funciones produce una excepción si el objeto recordset no tiene registros. En general, llame a ambos `IsBOF` y `IsEOF` antes de una operación de movimiento para determinar si el conjunto de registros tiene todos los registros. Después de llamar a **abiertos** o **Requery**, llame a `IsBOF` o `IsEOF`.  
  
> [!NOTE]
>  Si se llama a cualquiera de los **mover** funciona mientras el registro actual se actualiza o agregado, las actualizaciones se pierden sin advertencia.  
  
 Utilice la **mover** funciones para desplazarse por los registros sin aplicar una condición. Utilice las operaciones de búsqueda para localizar los registros en un tipo dinámico o un objeto recordset de tipo snapshot que satisface una condición determinada. Para localizar un registro en un objeto de conjunto de registros de tipo de tabla, llame a `Seek`.  
  
 Si el conjunto de registros hace referencia a un conjunto de registros de tipo de tabla, desplazamiento sigue el índice actual de la tabla. Puede establecer el índice actual mediante la propiedad de índice del objeto DAO subyacente. Si no establece el índice actual, el orden de los registros devueltos es indefinido.  
  
 No se puede llamar el **MoveFirst** o `MovePrev` función miembro con una instantánea con desplazamiento sólo hacia delante.  
  
 Para mover la posición del actual registro de un objeto de conjunto de registros un determinado número de registros hacia delante o hacia atrás, llame a **mover**.  
  
 Para obtener información relacionada, vea los temas "Método Move" y "MoveFirst, MoveLast, MoveNext, MovePrevious métodos" en la Ayuda de DAO.  
  
##  <a name="a-nameopena--cdaorecordsetopen"></a><a name="open"></a>CDaoRecordset:: Open  
 Debe llamar a esta función miembro para recuperar los registros del conjunto de registros.  
  
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
  
- **dbOpenTable** un conjunto de registros de tipo tabla con desplazamiento bidireccional.  
  
- **dbOpenSnapshot** un conjunto de registros de tipo instantánea con desplazamiento bidireccional.  
  
 `lpszSQL`  
 Puntero de cadena que contiene uno de los elementos siguientes:  
  
-   Un **NULL** puntero.  
  
-   El nombre de uno o más definiciones de tabla y/o querydefs (separados por comas).  
  
-   Una instancia de SQL **seleccione** instrucción (opcionalmente con una instancia de SQL **donde** o **ORDERBY** cláusula).  
  
-   Una consulta de paso.  
  
 `nOptions`  
 Uno o más de las siguientes opciones. El valor predeterminado es 0. Los valores posibles son los siguientes:  
  
- **dbAppendOnly** sólo se pueden anexar nuevos registros (sólo registros de tipo dinámico). Esta opción significa literalmente que sólo se pueden anexar los registros. Las clases de base de datos ODBC de MFC tienen una opción de sólo anexar que permite recuperar y anexa los registros.  
  
- **dbForwardOnly** el conjunto de registros es una instantánea de desplazamiento sólo hacia delante.  
  
- **dbSeeChanges** generará una excepción si otro usuario cambia datos que está modificando.  
  
- **dbDenyWrite** no se pueden modificar o agregar registros de otros usuarios.  
  
- **dbDenyRead** otros usuarios no pueden ver los registros (sólo conjunto de registros de tipo de tabla).  
  
- **dbReadOnly** sólo puede ver los registros; otros usuarios pueden modificarlas.  
  
- **dbInconsistent** actualizaciones incoherentes se permiten (solo registros de tipo dinámico).  
  
- **dbConsistent** sólo pueden actualizaciones coherentes (sólo registros de tipo dinámico).  
  
> [!NOTE]
>  Las constantes **dbConsistent** y **dbInconsistent** son mutuamente excluyentes. Puede usar uno o el otro, pero no ambas en una instancia determinada de **abiertos**.  
  
 *pTableDef*  
 Un puntero a un [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md) objeto. Esta versión es válida sólo para conjuntos de registros de tipo de tabla. Al utilizar esta opción, el `CDaoDatabase` puntero utilizado para construir el `CDaoRecordset` no se utiliza; en su lugar, se utiliza la base de datos en el que reside la definición de tabla.  
  
 *pQueryDef*  
 Un puntero a un [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md) objeto. Esta versión es válida únicamente para el tipo de conjunto de registros dinámicos y registros de tipo instantánea. Al utilizar esta opción, el `CDaoDatabase` puntero utilizado para construir el `CDaoRecordset` no se utiliza; en su lugar, se utiliza la base de datos en el que reside la definición de consulta.  
  
### <a name="remarks"></a>Comentarios  
 Antes de llamar a **abiertos**, debe crear el objeto de conjunto de registros. Existen varias formas de hacerlo:  
  
-   Cuando se construye el objeto recordset, pase un puntero a un `CDaoDatabase` objeto que ya está abierto.  
  
-   Cuando se construye el objeto recordset, pase un puntero a un `CDaoDatabase` objeto que no está abierto. El conjunto de registros se abre un `CDaoDatabase` el objeto, pero no la cerrará cuando se cierra el objeto recordset.  
  
-   Cuando se construye el objeto recordset, pasa una **NULL** puntero. Las llamadas del objeto de conjunto de registros `GetDefaultDBName` para obtener el nombre de Microsoft Access. Archivo de Microsoft Access para abrir. El conjunto de registros, a continuación, se abre un `CDaoDatabase` objeto y mantiene abra siempre que el conjunto de registros está abierto. Cuando se llama a **cerrar** en el conjunto de registros, la `CDaoDatabase` también se cierra el objeto.  
  
    > [!NOTE]
    >  Cuando se abre el conjunto de registros el `CDaoDatabase` de objeto, se abre el origen de datos con acceso no exclusivo.  
  
 Para la versión de **abrir** que usa el `lpszSQL` parámetro, una vez abierto el conjunto de registros puede recuperar registros de varias maneras. La primera opción es tener funciones DFX en su `DoFieldExchange`. La segunda opción es usar el enlace dinámico llamando a la `GetFieldValue` función miembro. Estas opciones se pueden implementar por separado o combinados. Si se combinan, tendrá que pasar en la instrucción SQL usted mismo en la llamada a **abiertos**.  
  
 Cuando se usa la segunda versión de **abiertos** donde se pasa en un `CDaoTableDef` objeto, estarán disponibles para enlazar a través de las columnas resultantes `DoFieldExchange` y el mecanismo DFX o enlazar dinámicamente mediante `GetFieldValue`.  
  
> [!NOTE]
>  Solo se puede llamar a **abiertos** mediante un `CDaoTableDef` objeto para conjuntos de registros de tipo de tabla.  
  
 Cuando se usa la tercera versión de **abiertos** donde se pasa en un `CDaoQueryDef` de objeto, que se ejecutará la consulta y las columnas resultantes estarán disponibles para enlazar a través de `DoFieldExchange` y el mecanismo DFX o enlazar dinámicamente mediante `GetFieldValue`.  
  
> [!NOTE]
>  Solo se puede llamar a **abiertos** mediante un `CDaoQueryDef` objeto de tipo dynaset y conjuntos de registros de tipo snapshot.  
  
 Para la primera versión de **abiertos** que usa el `lpszSQL` parámetro, los registros son seleccionados según los criterios que se muestra en la tabla siguiente.  
  
|Valor del parámetro `lpszSQL`|Los registros seleccionados están determinados por|Ejemplo|  
|--------------------------------------|----------------------------------------|-------------|  
|**NULL**|La cadena devuelta por `GetDefaultSQL`.||  
|Una lista separada por comas de uno o más definiciones de tabla o a los nombres de definición de consulta.|Todas las columnas se representan en el `DoFieldExchange`.|`"Customer"`|  
|**Seleccione** lista de columnas **FROM** lista de tablas|Las columnas especificadas de la tabledef(s) especificado o querydef(s).|`"SELECT CustId, CustName`<br /><br /> `FROM Customer"`|  
  
 El procedimiento habitual consiste en pasar **NULL** a **abiertos**; en ese caso, **abiertos** llamadas `GetDefaultSQL`, una función de miembro reemplazables ClassWizard genera al crear un `CDaoRecordset`-clase derivada. Este valor proporciona los nombres tabledef(s) o definición de consulta especificada en el Asistente para. Se puede especificar otra información en el parámetro `lpszSQL`.  
  
 Cualquier valor que pase **abiertos** construye una cadena SQL final para la consulta (la cadena puede tener **donde** y **ORDERBY** cláusulas se anexan a la `lpszSQL` cadena pasó) y, a continuación, ejecuta la consulta. Puede examinar la cadena construida mediante una llamada a `GetSQL` después de llamar a **abiertos**.  
  
 Los miembros de datos de campo de la clase de conjunto de registros están enlazados a las columnas de los datos seleccionados. Si se devuelve algún registro, el primer registro se convierte en el registro actual.  
  
 Si desea establecer opciones para el conjunto de registros, como un filtro o una ordenación, establezca `m_strSort` o **m_strFilter** después de crear el objeto de conjunto de registros, pero antes de llamar a **abiertos**. Si desea actualizar los registros del conjunto de registros después del conjunto de registros está abierto, llame a **Requery**.  
  
 Si se llama a **abiertos** en un tipo dinámico o un objeto recordset de instantánea, o si el origen de datos hace referencia a una instrucción SQL o una definición de tabla que representa una tabla asociada, no puede usar **dbOpenTable** para el argumento de tipo; si lo hace, MFC produce una excepción. Para determinar si un objeto tabledef representa una tabla asociada, cree una [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md) objeto y llamar a su [GetConnect](../../mfc/reference/cdaotabledef-class.md#getconnect) función miembro.  
  
 Utilice la **dbSeeChanges** marca si desea capturar los cambios realizados por otro usuario u otro programa en su equipo cuando está modificando o eliminando el mismo registro. Por ejemplo, si dos usuarios comenzar a editar el mismo registro, el primer usuario que llame a la **actualización** función miembro se realiza correctamente. Cuando **actualización** llama al segundo usuario, un `CDaoException` se produce. De forma similar, si el segundo usuario intenta llamar a **eliminar** eliminar el registro y se ha cambiado ya por el primer usuario, un `CDaoException` se produce.  
  
 Normalmente, si el usuario obtiene este `CDaoException` durante la actualización, el código debe actualizar el contenido de los campos y recuperar los valores recién modificados. Si la excepción se produce en el proceso de eliminación, el código puede mostrar los datos de registro de nuevo al usuario y un mensaje que indica que los datos han cambiado recientemente. En este punto, el código puede solicitar una confirmación de que el usuario aún desea eliminar el registro.  
  
> [!TIP]
>  Utilice la opción de desplazamiento sólo hacia delante ( **dbForwardOnly**) mejorar el rendimiento cuando la aplicación realiza una sola pasada a través de un conjunto de registros abierto de un origen de datos ODBC.  
  
 Para obtener información relacionada, vea el tema "Método OpenRecordset" en la Ayuda de DAO.  
  
##  <a name="a-namerequerya--cdaorecordsetrequery"></a><a name="requery"></a>CDaoRecordset::Requery  
 Llame a esta función miembro para volver a generar (actualizar) un conjunto de registros.  
  
```  
virtual void Requery();
```  
  
### <a name="remarks"></a>Comentarios  
 Si se devuelve algún registro, el primer registro se convierte en el registro actual.  
  
 En orden para el conjunto de registros reflejar las adiciones y eliminaciones realizados por usted u otros usuarios en el origen de datos, debe volver a generar el conjunto de registros llamando a **Requery**. Si el conjunto de registros es de tipo dinámico, refleja automáticamente las actualizaciones que usted u otros usuarios realicen en sus registros existentes (pero no las adiciones). Si el conjunto de registros es una instantánea, debe llamar a **Requery** para reflejar modificaciones realizadas por otros usuarios, así como las adiciones y eliminaciones.  
  
 Para el tipo dinámico o una instantánea, llame a **Requery** siempre que desee volver a generar el conjunto de registros con los valores de parámetro. Establecer el nuevo filtro u ordenar estableciendo [m_strFilter](#m_strfilter) y [m_strSort](#m_strsort) antes de llamar a **Requery**. Definir nuevos parámetros si asigna nuevos valores a los miembros de datos de parámetro antes de llamar a **Requery**.  
  
 Si se produce un error en el intento de volver a generar el conjunto de registros, se cierra el conjunto de registros. Antes de llamar a **Requery**, puede determinar si se puede consultar el conjunto de registros llamando a la [CanRestart](#canrestart) función miembro. `CanRestart`no garantiza que **Requery** se realizará correctamente.  
  
> [!CAUTION]
>  Llame a **Requery** sólo después de haber llamado **abiertos**.  
  
> [!NOTE]
>  Llamar a [Requery](#requery) cambia marcadores DAO.  
  
 No se puede llamar **Requery** en un tipo dinámico o el conjunto de registros de tipo instantánea si una llamada a `CanRestart` devuelve 0, ni se puede utilizar, en un conjunto de registros de tipo de tabla.  
  
 Si ambos `IsBOF` y `IsEOF` devolver cero después de llamar a **Requery**, la consulta no devuelve todos los registros y el conjunto de registros no contendrá ningún dato.  
  
 Para obtener información relacionada, vea el tema "Requery (método)" en la Ayuda de DAO.  
  
##  <a name="a-nameseeka--cdaorecordsetseek"></a><a name="seek"></a>CDaoRecordset::Seek  
 Llame a esta función miembro para encontrar el registro en un objeto de conjunto de registros de tipo tabla indizada que satisface los criterios especificados para la actual de índice y convierte ese registro en el registro actual.  
  
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
 Una de las siguientes expresiones de cadena: "<",></",>\<=", "=", "> =", o ">".  
  
 `pKey1`  
 Un puntero a un [COleVariant](../../mfc/reference/colevariant-class.md) cuyo valor se corresponde con el primer campo en el índice. Obligatorio.  
  
 *pKey2*  
 Un puntero a un `COleVariant` cuyo valor corresponde al segundo campo del índice, si existe. Valor predeterminado es **NULL**.  
  
 *pKey3*  
 Un puntero a un `COleVariant` cuyo valor corresponde al tercer campo en el índice, si existe. Valor predeterminado es **NULL**.  
  
 *pKeyArray*  
 Un puntero a una matriz de variantes. El tamaño de la matriz se corresponde con el número de campos en el índice.  
  
 *nKeys*  
 Un entero correspondiente al tamaño de la matriz, que es el número de campos en el índice.  
  
> [!NOTE]
>  No especifique caracteres comodín en las claves. Hará que los caracteres comodín `Seek` para no devolver ningún registro coincidente.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si se encuentran registros coincidentes, en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Utilice la segunda versión (matriz) de `Seek` para administrar índices de cuatro campos o más.  
  
 `Seek`permite buscar en conjuntos de registros de tipo de tabla de índice de alto rendimiento. Debe establecer el índice actual mediante una llamada a `SetCurrentIndex` antes de llamar a `Seek`. Si el índice identifica un único campo o campos clave, `Seek` localiza el primer registro que satisface los criterios. Si no establece un índice, se produce una excepción.  
  
 Tenga en cuenta que si no se está creando un conjunto de registros UNICODE, la `COleVariant` objetos se deben declarar explícitamente ANSI. Esto puede hacerse mediante el uso de la [COleVariant::COleVariant](../../mfc/reference/colevariant-class.md#colevariant)**(** `lpszSrc` **,** `vtSrc` **)** formulario del constructor con `vtSrc` establecido en `VT_BSTRT` (ANSI) o mediante el **COleVariant** función [SetString](../../mfc/reference/colevariant-class.md#setstring)**(** `lpszSrc` **,** `vtSrc` **)** con `vtSrc` establecido en `VT_BSTRT`.  
  
 Cuando se llama a `Seek`, pasar uno o más valores de clave y un operador de comparación ("<",></",>\<=", "=", "> =", o ">"). `Seek`busca en los campos clave especificados y localiza el primer registro que satisface los criterios especificados por `lpszComparison` y `pKey1`. Una vez encontrado, `Seek` devuelve distinto de cero y que el registro actual. Si `Seek` no encuentra una coincidencia, `Seek` devuelve cero y el registro actual no está definido. Cuando utiliza DAO directamente, debe comprobar explícitamente la propiedad NoMatch.  
  
 Si `lpszComparison` es "=", "> =", o ">", `Seek` comienza al principio del índice. Si `lpszComparison` es "<" or=""> </"> <=",> </=",> `Seek` se inicia al final del índice y busca hacia atrás a menos que haya entradas de índice duplicadas al final. En este caso, `Seek` comienza en una entrada arbitraria entre las entradas de índice duplicadas al final del índice.  
  
 No existen que ser un registro actual cuando utiliza `Seek`.  
  
 Para buscar un registro en un tipo dinámico o un conjunto de registros de tipo snapshot que satisface una condición específica, utilice las operaciones de búsqueda. Para incluir todos los registros, no sólo los que cumplen una condición específica, utilice las operaciones de desplazamiento para desplazarse por los registros.  
  
 No se puede llamar `Seek` en una tabla asociada de cualquier tipo porque se deben abrir tablas asociadas como conjuntos de registros de tipo snapshot o un tipo de conjunto de registros dinámicos. Sin embargo, si se llama a `CDaoDatabase::Open` para abrir directamente una base de datos ISAM instalable, puede llamar a `Seek` en las tablas de esa base de datos, aunque el rendimiento puede ser lento.  
  
 Para obtener información relacionada, vea el tema "Método Seek" en la Ayuda de DAO.  
  
##  <a name="a-namesetabsolutepositiona--cdaorecordsetsetabsoluteposition"></a><a name="setabsoluteposition"></a>CDaoRecordset:: SetAbsolutePosition  
 Establece el número de registro relativo del registro actual de un objeto recordset.  
  
```  
void SetAbsolutePosition(long lPosition);
```  
  
### <a name="parameters"></a>Parámetros  
 *lPosition*  
 Corresponde a la posición ordinal del registro actual en el conjunto de registros.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a `SetAbsolutePosition` le permite colocar el puntero de registro actual en un registro específico basado en su posición ordinal en un tipo dinámico o el conjunto de registros de tipo snapshot. También puede determinar el número de registro actual mediante una llamada a [GetAbsolutePosition](#getabsoluteposition).  
  
> [!NOTE]
>  Esta función miembro es válida sólo para el tipo de conjunto de registros dinámicos y registros de tipo instantánea.  
  
 El valor de la propiedad AbsolutePosition del objeto DAO subyacente está basado en cero; un valor de 0 hace referencia al primer registro del conjunto de registros. Establecer un valor mayor que el número de registros llenados, MFC inicia una excepción. Puede determinar el número de registros rellenados en el conjunto de registros llamando a la `GetRecordCount` función miembro.  
  
 Si se elimina el registro actual, el valor de la propiedad AbsolutePosition no se define y MFC produce una excepción si se hace referencia. Registros nuevos se agregan al final de la secuencia.  
  
> [!NOTE]
>  Esta propiedad no pretende utilizar como un número de registro suplente. Los marcadores siguen siendo la forma recomendada de conservar y volver a una posición determinada y son la única manera de colocar el registro actual en todos los tipos de objetos recordset que admiten marcadores. En particular, la posición de un registro determinado cambia cuando se eliminan registros anterior. También no hay ninguna garantía de que un determinado registro tendrá la misma posición absoluta si se vuelve a crear el conjunto de registros, porque no se garantiza el orden de los registros individuales dentro de un conjunto de registros, a menos que se cree con una instrucción SQL mediante un **ORDERBY** cláusula.  
  
 Para obtener información relacionada, vea el tema "AbsolutePosition (propiedad)" en la Ayuda de DAO.  
  
##  <a name="a-namesetbookmarka--cdaorecordsetsetbookmark"></a><a name="setbookmark"></a>CDaoRecordset:: SetBookmark  
 Llame a esta función miembro para colocar el conjunto de registros en el registro que contiene el marcador especificado.  
  
```  
void SetBookmark(COleVariant varBookmark);
```  
  
### <a name="parameters"></a>Parámetros  
 `varBookmark`  
 Un [COleVariant](../../mfc/reference/colevariant-class.md) objeto que contiene el valor de marcador para un registro específico.  
  
### <a name="remarks"></a>Comentarios  
 Cuando se crea o se abre un objeto recordset, cada uno de sus registros ya tiene un marcador único. Puede recuperar el marcador del registro actual mediante una llamada a `GetBookmark` y guardar el valor para un `COleVariant` objeto. Más adelante puede volver a ese registro mediante una llamada a `SetBookmark` con el valor de marcador guardado.  
  
> [!NOTE]
>  Llamar a [Requery](#requery) cambia marcadores DAO.  
  
 Tenga en cuenta que si no se está creando un conjunto de registros UNICODE, la `COleVariant` objeto debe declararse explícitamente ANSI. Esto puede hacerse mediante el uso de la [COleVariant::COleVariant](../../mfc/reference/colevariant-class.md#colevariant)**(** `lpszSrc` **,** `vtSrc` **)** formulario del constructor con `vtSrc` establecido en `VT_BSTRT` (ANSI) o mediante el **COleVariant** función [SetString](../../mfc/reference/colevariant-class.md#setstring)**(** `lpszSrc` **,** `vtSrc` **)** con `vtSrc` establecido en `VT_BSTRT`.  
  
 Para obtener información relacionada, vea los temas "Propiedades de marcador" y admite marcadores"en la Ayuda de DAO.  
  
##  <a name="a-namesetcachesizea--cdaorecordsetsetcachesize"></a><a name="setcachesize"></a>CDaoRecordset:: SetCacheSize  
 Llame a esta función miembro para establecer el número de registros que se van a almacenar en caché.  
  
```  
void SetCacheSize(long lSize);
```  
  
### <a name="parameters"></a>Parámetros  
 `lSize`  
 Especifica el número de registros. Un valor típico es 100. Un valor de 0 desactiva la caché. El valor debe estar entre 5 y 1200 registros. La memoria caché puede utilizar una cantidad considerable de memoria.  
  
### <a name="remarks"></a>Comentarios  
 Una caché es un espacio en la memoria local que contiene los datos recuperados más recientemente desde el servidor en caso de que los datos volverá a solicitarse mientras se ejecuta la aplicación. Datos en caché mejora el rendimiento de una aplicación que recupera datos de un servidor remoto a través de objetos de conjunto de registros de tipo dinámico. Cuando se soliciten datos, el motor de base de datos Microsoft Jet comprueba primero la caché de los datos solicitados en lugar de recuperar desde el servidor, que tarda más tiempo. Datos que no proceden de un origen de datos no se guardan en la memoria caché.  
  
 Cualquier origen de datos ODBC, como una tabla asociada, puede tener una caché local. Para crear una caché, abra un objeto recordset desde el origen de datos remoto, llamada la `SetCacheSize` y `SetCacheStart` funciones miembro y, a continuación, llame el `FillCache` función miembro o desplazarse por los registros mediante una de las operaciones de movimiento. El `lSize` parámetro de la `SetCacheSize` función miembro puede basarse en el número de registros que su aplicación puede funcionar con a la vez. Por ejemplo, si utiliza un conjunto de registros como el origen de datos que se mostrará en la pantalla, podría pasar la `SetCacheSize``lSize` parámetro como 20 para mostrar 20 registros a la vez.  
  
 Para obtener información relacionada, vea el tema "CacheSize, CacheStart (propiedades)" en la Ayuda de DAO.  
  
##  <a name="a-namesetcachestarta--cdaorecordsetsetcachestart"></a><a name="setcachestart"></a>CDaoRecordset:: SetCacheStart  
 Llame a esta función miembro para especificar el marcador del primer registro del conjunto de registros en la caché.  
  
```  
void SetCacheStart(COleVariant varBookmark);
```  
  
### <a name="parameters"></a>Parámetros  
 `varBookmark`  
 Un [COleVariant](../../mfc/reference/colevariant-class.md) que especifica el marcador del primer registro en el conjunto de registros en la caché.  
  
### <a name="remarks"></a>Comentarios  
 Puede usar el valor de marcador de cualquier registro para la `varBookmark` parámetro de la `SetCacheStart` función miembro. Hacer que el registro que desea iniciar la memoria caché con el registro actual, establecer un marcador para ese registro con [SetBookmark](#setbookmark)y pase el valor de marcador como parámetro para el `SetCacheStart` función miembro.  
  
 El motor de base de datos Microsoft Jet solicita registros dentro del intervalo de la memoria caché de la memoria caché y solicita registros fuera del intervalo de la memoria caché del servidor.  
  
 Los registros recuperados de la caché no reflejan los cambios realizados al origen de datos por otros usuarios.  
  
 Para forzar una actualización de todos los datos almacenados en caché, pasar la `lSize` parámetro de `SetCacheSize` como 0, llame a `SetCacheSize` nuevo con el tamaño de la caché que solicitó originalmente y, a continuación, llame a la `FillCache` función miembro.  
  
 Tenga en cuenta que si no se está creando un conjunto de registros UNICODE, la `COleVariant` objeto debe declararse explícitamente ANSI. Esto puede hacerse mediante el uso de la [COleVariant::COleVariant](../../mfc/reference/colevariant-class.md#colevariant)**(** `lpszSrc` **,** `vtSrc` **)** formulario del constructor con `vtSrc` establecido en `VT_BSTRT` (ANSI) o mediante el **COleVariant** función [SetString](../../mfc/reference/colevariant-class.md#setstring)**(** `lpszSrc` **,** `vtSrc` **)** con `vtSrc` establecido en `VT_BSTRT`.  
  
 Para obtener información relacionada, vea el tema CacheSize, CacheStart (propiedades)"en la Ayuda de DAO.  
  
##  <a name="a-namesetcurrentindexa--cdaorecordsetsetcurrentindex"></a><a name="setcurrentindex"></a>CDaoRecordset:: SetCurrentIndex  
 Llame a esta función miembro para establecer un índice en un conjunto de registros de tipo de tabla.  
  
```  
void SetCurrentIndex(LPCTSTR lpszIndex);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszIndex`  
 Un puntero que contiene el nombre del índice que se puede establecer.  
  
### <a name="remarks"></a>Comentarios  
 Registros en tablas base no se almacenan en un orden determinado. Establecer un índice cambia el orden de los registros devueltos desde la base de datos, pero no afecta el orden en que se almacenan los registros. Ya debe estar definido el índice especificado. Si intenta utilizar un objeto de índice que no existe, o si el índice no se establece cuando se llama a [Seek](#seek), MFC produce una excepción.  
  
 Puede crear un nuevo índice para la tabla mediante una llamada a [CDaoTableDef::CreateIndex](../../mfc/reference/cdaotabledef-class.md#createindex) y anexar el nuevo índice a la colección de índices de la definición de tabla subyacente mediante una llamada a [CDaoTableDef:: Append](../../mfc/reference/cdaotabledef-class.md#append)y, a continuación, volver a abrir el conjunto de registros.  
  
 Los registros devueltos desde un conjunto de registros de tipo de tabla pueden ordenarse sólo por los índices definidos para la definición de tabla subyacente. Para ordenar los registros en otro orden, puede abrir un tipo dinámico o conjunto de registros de tipo instantánea mediante SQL **ORDERBY** cláusula almacenados en [CDaoRecordset::m_strSort](#m_strsort).  
  
 Para obtener información relacionada, vea el tema "Objeto Index" y la definición de "índice actual" en la Ayuda de DAO.  
  
##  <a name="a-namesetfielddirtya--cdaorecordsetsetfielddirty"></a><a name="setfielddirty"></a>CDaoRecordset:: SetFieldDirty  
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
 **TRUE** si el miembro de datos del campo es se marcará como "dirty" (modificado). De lo contrario, **FALSE** si el miembro de datos del campo es se marcará como "limpiar" (sin cambios).  
  
### <a name="remarks"></a>Comentarios  
 Marcar campos como sin cambios garantiza que no se actualiza el campo.  
  
 Las marcas de framework cambiar los miembros de datos de campo para asegurarse de que se escribirán en el registro en el origen de datos mediante el mecanismo de intercambio (DFX) de campos de registros DAO. Cambiar el valor de un campo normalmente establece el campo desfasadas automáticamente, por lo que rara vez necesitará llamar `SetFieldDirty` usted mismo, pero a veces, conviene asegurarse de que las columnas se explícitamente actualizadas o insertadas, independientemente de qué valor se encuentra en el miembro de datos de campo. El mecanismo DFX también emplea el uso de **PSEUDONULL**. Para obtener más información, consulte [CDaoFieldExchange:: M_noperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation).  
  
 Si no se utiliza el mecanismo de doble búfer, a continuación, cambiar el valor del campo no establece automáticamente el campo como modificada. En este caso, será necesario establecer explícitamente el campo como modificada. La marca contenida en [m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields) controla esta comprobación automática de campos.  
  
> [!NOTE]
>  Llame a esta función miembro después de haber llamado [editar](#edit) o [AddNew](#addnew).  
  
 Usando **NULL** para el primer argumento de la función aplicará la función a todos los **outputColumn** campos, no **param** campos de `CDaoFieldExchange`. Por ejemplo, la llamada  
  
 [!code-cpp[NVC_MFCDatabase Nº&6;](../../mfc/codesnippet/cpp/cdaorecordset-class_6.cpp)]  
  
 establecerá sólo **outputColumn** campos **NULL**; **param** campos no se verán afectados.  
  
 Para trabajar en un **param**, debe proporcionar la dirección real de la persona **param** que desea trabajar, como:  
  
 [!code-cpp[NVC_MFCDatabase&#7;](../../mfc/codesnippet/cpp/cdaorecordset-class_7.cpp)]  
  
 Esto significa que no se puede establecer en todos los **param** campos **NULL**, como ocurre con **outputColumn** campos.  
  
 `SetFieldDirty`se implementa a través de `DoFieldExchange`.  
  
##  <a name="a-namesetfieldnulla--cdaorecordsetsetfieldnull"></a><a name="setfieldnull"></a>CDaoRecordset::SetFieldNull  
 Llame a esta función miembro para marcar a un miembro de datos de campo del conjunto de registros como Null (específicamente con ningún valor) o como no Null.  
  
```  
void SetFieldNull(
    void* pv,  
    BOOL bNull = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 `pv`  
 Contiene la dirección de un miembro de datos de campo del conjunto de registros o **NULL**. Si **NULL**, se marcan todos los miembros de datos de campo del conjunto de registros. (C++ **NULL** no es igual a Null en la terminología de base de datos, lo que significa "no tener ningún valor.")  
  
 `bNull`  
 Es distinto de cero si es miembro de datos del campo se marca como no tener ningún valor (Null). En caso contrario, 0 si el miembro de datos de campo se marca como no Null.  
  
### <a name="remarks"></a>Comentarios  
 `SetFieldNull`se usa para campos enlazados en el `DoFieldExchange` mecanismo.  
  
 Al agregar un nuevo registro a un conjunto de registros, todos los miembros de datos de campo se establecen en un valor Null inicialmente y se marca como "dirty" (modificado). Cuando recupera un registro de un origen de datos, sus columnas ya tienen valores o son Null. Si no es adecuado convertir un campo Null, un [CDaoException](../../mfc/reference/cdaoexception-class.md) se produce.  
  
 Si utiliza el mecanismo de doble búfer, por ejemplo, si desea específicamente designar un campo del registro actual que no tiene un valor, llame a `SetFieldNull` con `bNull` establecido en **TRUE** para marcar como Null. Si previamente se ha marcado un campo Null y ahora desea asignarle un valor, simplemente establezca su nuevo valor. No es necesario quitar la marca Null con `SetFieldNull`. Para determinar si el campo puede ser Null, llame a [IsFieldNullable](#isfieldnullable).  
  
 Si no utiliza el mecanismo de doble búfer, a continuación, cambiar el valor del campo no establece automáticamente el campo como desfasadas y distinto de Null. Específicamente, debe establecer los campos modificados y no Null. La marca contenida en [m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields) controla esta comprobación automática de campos.  
  
 El mecanismo DFX emplea el uso de **PSEUDONULL**. Para obtener más información, consulte [CDaoFieldExchange:: M_noperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation).  
  
> [!NOTE]
>  Llame a esta función miembro después de haber llamado [editar](#edit) o [AddNew](#addnew).  
  
 Usando **NULL** para el primer argumento de la función aplicará únicamente a la función **outputColumn** campos, no **param** campos de `CDaoFieldExchange`. Por ejemplo, la llamada  
  
 [!code-cpp[NVC_MFCDatabase Nº&8;](../../mfc/codesnippet/cpp/cdaorecordset-class_8.cpp)]  
  
 establecerá sólo **outputColumn** campos **NULL**; **param** campos no se verán afectados.  
  
##  <a name="a-namesetfieldvaluea--cdaorecordsetsetfieldvalue"></a><a name="setfieldvalue"></a>CDaoRecordset::SetFieldValue  
 Llame a esta función miembro para establecer el valor de un campo por posición ordinal o cambiando el valor de la cadena.  
  
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
 Puntero a una cadena que contiene el valor del contenido del campo.  
  
### <a name="remarks"></a>Comentarios  
 Utilice `SetFieldValue` y [GetFieldValue](#getfieldvalue) para enlazar campos de forma dinámica en tiempo de ejecución en lugar de estáticamente columnas de enlace mediante la [DoFieldExchange](#dofieldexchange) mecanismo.  
  
 Tenga en cuenta que si no está creando un conjunto de registros UNICODE, hay que usar un formulario de `SetFieldValue` que no contiene un `COleVariant` parámetro, o la `COleVariant` objeto debe declararse explícitamente ANSI. Esto puede hacerse mediante el uso de la [COleVariant::COleVariant](../../mfc/reference/colevariant-class.md#colevariant)**(** `lpszSrc` **,** `vtSrc` **)** formulario del constructor con `vtSrc` establecido en `VT_BSTRT` (ANSI) o mediante el **COleVariant** función [SetString](../../mfc/reference/colevariant-class.md#setstring)**(** `lpszSrc` **,** `vtSrc` **)** con `vtSrc` establecido en `VT_BSTRT`.  
  
 Para obtener información relacionada, vea los temas "Objeto Field" y "Valor de propiedad" en la Ayuda de DAO.  
  
##  <a name="a-namesetfieldvaluenulla--cdaorecordsetsetfieldvaluenull"></a><a name="setfieldvaluenull"></a>CDaoRecordset::SetFieldValueNull  
 Llame a esta función miembro para configurar el campo como un valor Null.  
  
```  
void SetFieldValueNull(int nIndex);  
void SetFieldValueNull(LPCTSTR lpszName);
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 El índice del campo en el conjunto de registros para la búsqueda por índice de base cero.  
  
 `lpszName`  
 El nombre del campo en el conjunto de registros para la búsqueda por nombre.  
  
### <a name="remarks"></a>Comentarios  
 C++ **NULL** no es igual a Null, lo que significa que en la terminología de base de datos, "no tener ningún valor."  
  
 Para obtener información relacionada, vea los temas "Objeto Field" y "Valor de propiedad" en la Ayuda de DAO.  
  
##  <a name="a-namesetlockingmodea--cdaorecordsetsetlockingmode"></a><a name="setlockingmode"></a>CDaoRecordset::SetLockingMode  
 Llame a esta función miembro para establecer el tipo de bloqueo para el conjunto de registros.  
  
```  
void SetLockingMode(BOOL bPessimistic);
```  
  
### <a name="parameters"></a>Parámetros  
 *bPessimistic*  
 Marca que indica el tipo de bloqueo.  
  
### <a name="remarks"></a>Comentarios  
 Cuando el bloqueo pesimista está activada, la página de 2K que contiene el registro que está modificando está bloqueada en cuanto se llama a la **editar** función miembro. La página se desbloquea cuando se llama a la **actualización** o **cerrar** función miembro o cualquiera de las operaciones de mover o buscar.  
  
 Cuando está activado un bloqueo optimista, la página de 2K que contiene el registro está bloqueada mientras se actualiza el registro con el **actualización** función miembro.  
  
 Si una página está bloqueada, ningún otro usuario puede editar registros en la misma página. Si se llama a `SetLockingMode` y pasar un valor distinto de cero y otro usuario ya ha bloqueado la página, se produce una excepción cuando se llama a **editar**. Otros usuarios pueden leer datos de páginas bloqueadas.  
  
 Si se llama a `SetLockingMode` con un valor de cero y posterior llamada **actualización** mientras la página está bloqueada por otro usuario, se produce una excepción. Para ver los cambios realizados por otro usuario en el registro y perder los cambios, llame a la `SetBookmark` función miembro con el valor de marcador del registro actual.  
  
 Al trabajar con orígenes de datos ODBC, el modo de bloqueo siempre es optimista.  
  
##  <a name="a-namesetparamvaluea--cdaorecordsetsetparamvalue"></a><a name="setparamvalue"></a>CDaoRecordset::SetParamValue  
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
 El nombre del parámetro cuyo valor va a establecer.  
  
### <a name="remarks"></a>Comentarios  
 El parámetro ya se debe haber establecido como parte de la cadena SQL del conjunto de registros. El parámetro puede tener acceso por nombre o por su posición de índice en la colección.  
  
 Especifique el valor que se establecerá como un `COleVariant` objeto. Para obtener información acerca de cómo establecer el valor deseado y el tipo en su `COleVariant` de objetos, vea la clase [COleVariant](../../mfc/reference/colevariant-class.md). Tenga en cuenta que si no se está creando un conjunto de registros UNICODE, la `COleVariant` objeto debe declararse explícitamente ANSI. Esto puede hacerse mediante el uso de la [COleVariant::COleVariant](../../mfc/reference/colevariant-class.md#colevariant)**(** `lpszSrc` **,** `vtSrc` **)** formulario del constructor con `vtSrc` establecido en `VT_BSTRT` (ANSI) o mediante el **COleVariant** función [SetString](../../mfc/reference/colevariant-class.md#setstring)**(** `lpszSrc` **,** `vtSrc` **)** con `vtSrc` establecido en `VT_BSTRT`.  
  
##  <a name="a-namesetparamvaluenulla--cdaorecordsetsetparamvaluenull"></a><a name="setparamvaluenull"></a>CDaoRecordset::SetParamValueNull  
 Llame a esta función miembro para establecer el parámetro en un valor Null.  
  
```  
void SetParamValueNull(int nIndex);  
void SetParamValueNull(LPCTSTR lpszName);
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 El índice del campo en el conjunto de registros para la búsqueda por índice de base cero.  
  
 `lpszName`  
 El nombre del campo en el conjunto de registros para la búsqueda por nombre.  
  
### <a name="remarks"></a>Comentarios  
 C++ **NULL** no es igual a Null, lo que significa que en la terminología de base de datos, "no tener ningún valor."  
  
##  <a name="a-namesetpercentpositiona--cdaorecordsetsetpercentposition"></a><a name="setpercentposition"></a>CDaoRecordset:: SetPercentPosition  
 Llame a esta función miembro para establecer un valor que cambia la ubicación aproximada del registro actual en el objeto de conjunto de registros basándose en un porcentaje de los registros del conjunto de registros.  
  
```  
void SetPercentPosition(float fPosition);
```  
  
### <a name="parameters"></a>Parámetros  
 *fPosition*  
 Número comprendido entre 0 y 100.  
  
### <a name="remarks"></a>Comentarios  
 Cuando se trabaja con un tipo de conjunto de registros dinámicos o el conjunto de registros de tipo snapshot, rellenar el objeto recordset moviendo el último registro antes de llamar a `SetPercentPosition`. Si se llama a `SetPercentPosition` antes de rellenar completamente el conjunto de registros, la cantidad de movimiento es relativo al número de registros que se tiene acceso como indica el valor de [GetRecordCount](#getrecordcount). Puede mover al último registro mediante una llamada a `MoveLast`.  
  
 Una vez que se llama a `SetPercentPosition`, el registro en la ubicación aproximada correspondiente a ese valor se convierte en actual.  
  
> [!NOTE]
>  Llamar a `SetPercentPosition` para mover el registro actual a un registro específico en un conjunto de registros no se recomienda. Llame a la [SetBookmark](#setbookmark) función miembro en su lugar.  
  
 Para obtener información relacionada, vea el tema "PercentPosition (propiedad)" en la Ayuda de DAO.  
  
##  <a name="a-nameupdatea--cdaorecordsetupdate"></a><a name="update"></a>CDaoRecordset::Update  
 Llame a esta función miembro después de llamar a la `AddNew` o **editar** función miembro.  
  
```  
virtual void Update();
```  
  
### <a name="remarks"></a>Comentarios  
 Esta llamada es necesario para completar la `AddNew` o **editar** operación.  
  
 Ambos `AddNew` y **editar** preparar un búfer de edición en el que se colocan los datos agregados o editados para guardar en el origen de datos. **Actualización** guarda los datos. Solo los campos marcados o detectado como cambiado se actualizan.  
  
 Si el origen de datos admite transacciones, puede hacer que el **actualización** llamar (y su correspondiente `AddNew` o **editar** llamar) forma parte de una transacción.  
  
> [!CAUTION]
>  Si se llama a **actualización** sin antes una llamada a `AddNew` o **editar**, **actualización** produce una `CDaoException`. Si se llama a `AddNew` o **editar**, debe llamar a **actualización** antes de llamar a [MoveNext](#movenext) cerrar el conjunto de registros o la conexión de origen de datos. De lo contrario, los cambios se pierden sin notificación.  
  
 Cuando el objeto recordset está bloqueado de forma pesimista en un entorno multiusuario, el registro permanece bloqueado desde **editar** se usa hasta que finalice la actualización. Si el conjunto de registros está bloqueado de forma optimista, el registro está bloqueado y se compara con el registro justo antes de actualizar la base de datos. Si el registro ha cambiado desde que llamó a **editar**, **actualización** error de la operación y MFC produce una excepción. Puede cambiar el modo de bloqueo con `SetLockingMode`.  
  
> [!NOTE]
>  Siempre se utiliza el bloqueo optimista en formatos de base de datos externa, como ODBC e ISAM instalable.  
  
 Para obtener información relacionada, vea los temas "Método AddNew", "Método CancelUpdate", "Método Delete", "Propiedad LastModified", "Método de actualización" y "Propiedad EditMode" en la Ayuda de DAO.  
  
## <a name="see-also"></a>Vea también  
 [CObject (clase)](../../mfc/reference/cobject-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clase CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)   
 [CDaoWorkspace (clase)](../../mfc/reference/cdaoworkspace-class.md)   
 [CDaoDatabase (clase)](../../mfc/reference/cdaodatabase-class.md)   
 [CDaoQueryDef (clase)](../../mfc/reference/cdaoquerydef-class.md)

