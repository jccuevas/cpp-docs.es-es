---
title: CDaoQueryDef (clase) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDaoQueryDef
- AFXDAO/CDaoQueryDef
- AFXDAO/CDaoQueryDef::CDaoQueryDef
- AFXDAO/CDaoQueryDef::Append
- AFXDAO/CDaoQueryDef::CanUpdate
- AFXDAO/CDaoQueryDef::Close
- AFXDAO/CDaoQueryDef::Create
- AFXDAO/CDaoQueryDef::Execute
- AFXDAO/CDaoQueryDef::GetConnect
- AFXDAO/CDaoQueryDef::GetDateCreated
- AFXDAO/CDaoQueryDef::GetDateLastUpdated
- AFXDAO/CDaoQueryDef::GetFieldCount
- AFXDAO/CDaoQueryDef::GetFieldInfo
- AFXDAO/CDaoQueryDef::GetName
- AFXDAO/CDaoQueryDef::GetODBCTimeout
- AFXDAO/CDaoQueryDef::GetParameterCount
- AFXDAO/CDaoQueryDef::GetParameterInfo
- AFXDAO/CDaoQueryDef::GetParamValue
- AFXDAO/CDaoQueryDef::GetRecordsAffected
- AFXDAO/CDaoQueryDef::GetReturnsRecords
- AFXDAO/CDaoQueryDef::GetSQL
- AFXDAO/CDaoQueryDef::GetType
- AFXDAO/CDaoQueryDef::IsOpen
- AFXDAO/CDaoQueryDef::Open
- AFXDAO/CDaoQueryDef::SetConnect
- AFXDAO/CDaoQueryDef::SetName
- AFXDAO/CDaoQueryDef::SetODBCTimeout
- AFXDAO/CDaoQueryDef::SetParamValue
- AFXDAO/CDaoQueryDef::SetReturnsRecords
- AFXDAO/CDaoQueryDef::SetSQL
- AFXDAO/CDaoQueryDef::m_pDAOQueryDef
- AFXDAO/CDaoQueryDef::m_pDatabase
dev_langs:
- C++
helpviewer_keywords:
- CDaoQueryDef [MFC], CDaoQueryDef
- CDaoQueryDef [MFC], Append
- CDaoQueryDef [MFC], CanUpdate
- CDaoQueryDef [MFC], Close
- CDaoQueryDef [MFC], Create
- CDaoQueryDef [MFC], Execute
- CDaoQueryDef [MFC], GetConnect
- CDaoQueryDef [MFC], GetDateCreated
- CDaoQueryDef [MFC], GetDateLastUpdated
- CDaoQueryDef [MFC], GetFieldCount
- CDaoQueryDef [MFC], GetFieldInfo
- CDaoQueryDef [MFC], GetName
- CDaoQueryDef [MFC], GetODBCTimeout
- CDaoQueryDef [MFC], GetParameterCount
- CDaoQueryDef [MFC], GetParameterInfo
- CDaoQueryDef [MFC], GetParamValue
- CDaoQueryDef [MFC], GetRecordsAffected
- CDaoQueryDef [MFC], GetReturnsRecords
- CDaoQueryDef [MFC], GetSQL
- CDaoQueryDef [MFC], GetType
- CDaoQueryDef [MFC], IsOpen
- CDaoQueryDef [MFC], Open
- CDaoQueryDef [MFC], SetConnect
- CDaoQueryDef [MFC], SetName
- CDaoQueryDef [MFC], SetODBCTimeout
- CDaoQueryDef [MFC], SetParamValue
- CDaoQueryDef [MFC], SetReturnsRecords
- CDaoQueryDef [MFC], SetSQL
- CDaoQueryDef [MFC], m_pDAOQueryDef
- CDaoQueryDef [MFC], m_pDatabase
ms.assetid: 9676a4a3-c712-44d4-8c5d-d1cc78288d3a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 81e7d3b093da8127887878b2ac5f2af652f549c3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="cdaoquerydef-class"></a>CDaoQueryDef (clase)
Representa una definición de consulta o "querydef", normalmente guardada en una base de datos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CDaoQueryDef : public CObject  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDaoQueryDef::CDaoQueryDef](#cdaoquerydef)|Construye un **CDaoQueryDef** objeto. A continuación llama a **abiertos** o **crear**, en función de sus necesidades.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDaoQueryDef:: Append](#append)|Anexa la definición de consulta a la colección de definiciones de consulta de la base de datos como una consulta guardada.|  
|[CDaoQueryDef::CanUpdate](#canupdate)|Devuelve un valor distinto de cero si la consulta puede actualizar la base de datos.|  
|[CDaoQueryDef::Close](#close)|Cierra el objeto de definición de consulta. Destruye el objeto de C++ cuando haya terminado con él.|  
|[CDaoQueryDef:: Create](#create)|Crea el objeto de definición de consulta DAO subyacente. Usar la definición de consulta como consulta temporal o llamada **anexado** para guardarlo en la base de datos.|  
|[CDaoQueryDef:: Execute](#execute)|Ejecuta la consulta definida por el objeto de definición de consulta.|  
|[CDaoQueryDef::GetConnect](#getconnect)|Devuelve la cadena de conexión asociada con la definición de consulta. La cadena de conexión identifica el origen de datos. (Para SQL acceso directo consulta solamente; en caso contrario, una cadena vacía.)|  
|[CDaoQueryDef::GetDateCreated](#getdatecreated)|Devuelve la fecha de que creación de la consulta guardada.|  
|[CDaoQueryDef::GetDateLastUpdated](#getdatelastupdated)|Devuelve la fecha en que se actualizó por última vez la consulta guardada.|  
|[CDaoQueryDef::GetFieldCount](#getfieldcount)|Devuelve el número de campos definidos por la definición de consulta.|  
|[CDaoQueryDef::GetFieldInfo](#getfieldinfo)|Devuelve información acerca de un campo especificado definido en la consulta.|  
|[CDaoQueryDef::GetName](#getname)|Devuelve el nombre de la definición de consulta.|  
|[CDaoQueryDef::GetODBCTimeout](#getodbctimeout)|Devuelve el valor de tiempo de espera utilizado por ODBC (para una consulta ODBC) cuando se ejecuta la definición de consulta. Esto determina cuánto tiempo permitir que se complete la acción de la consulta.|  
|[CDaoQueryDef::GetParameterCount](#getparametercount)|Devuelve el número de parámetros definidos para la consulta.|  
|[CDaoQueryDef::GetParameterInfo](#getparameterinfo)|Devuelve información sobre un parámetro especificado para la consulta.|  
|[CDaoQueryDef:: GetParamValue](#getparamvalue)|Devuelve el valor de un parámetro especificado para la consulta.|  
|[CDaoQueryDef::GetRecordsAffected](#getrecordsaffected)|Devuelve el número de registros afectados por una consulta de acción.|  
|[CDaoQueryDef::GetReturnsRecords](#getreturnsrecords)|Devuelve un valor distinto de cero si la consulta definida por la definición de consulta devuelve los registros.|  
|[CDaoQueryDef::GetSQL](#getsql)|Devuelve la cadena SQL que especifica la consulta definida por la definición de consulta.|  
|[CDaoQueryDef::GetType](#gettype)|Devuelve el tipo de consulta: eliminar, actualizar, anexar, creación de tabla y así sucesivamente.|  
|[CDaoQueryDef::IsOpen](#isopen)|Devuelve el valor distinto de cero si la definición de consulta está abierta y se puede ejecutar.|  
|[CDaoQueryDef::Open](#open)|Se abre una definición de consulta existente almacenado en la colección de definiciones de consulta de la base de datos.|  
|[CDaoQueryDef::SetConnect](#setconnect)|Establece la cadena de conexión para una consulta de paso a través de SQL en un origen de datos ODBC.|  
|[CDaoQueryDef::SetName](#setname)|Establece el nombre de la consulta guardada, reemplazando el nombre en uso cuando se creó la definición de consulta.|  
|[CDaoQueryDef::SetODBCTimeout](#setodbctimeout)|Establece el valor de tiempo de espera utilizado por ODBC (para una consulta ODBC) cuando se ejecuta la definición de consulta.|  
|[CDaoQueryDef:: SetParamValue](#setparamvalue)|Establece el valor de un parámetro especificado en la consulta.|  
|[CDaoQueryDef::SetReturnsRecords](#setreturnsrecords)|Especifica si la definición de consulta devuelve los registros. Establecer este atributo en **TRUE** solo es válida para las consultas de paso a través de SQL.|  
|[CDaoQueryDef::SetSQL](#setsql)|Establece la cadena SQL que especifica la consulta definida por la definición de consulta.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDaoQueryDef::m_pDAOQueryDef](#m_pdaoquerydef)|Un puntero a la interfaz OLE para el objeto de definición de consulta DAO subyacente.|  
|[CDaoQueryDef::m_pDatabase](#m_pdatabase)|Un puntero a la `CDaoDatabase` objeto con el que está asociada la definición de consulta. La definición de consulta podría estar guardado en la base de datos o no.|  
  
## <a name="remarks"></a>Comentarios  
 Una definición de consulta es un objeto de acceso de datos que contiene la instrucción SQL que describe una consulta y sus propiedades, como "Fecha de creación" y "Tiempo de espera ODBC". También puede crear objetos de definición de consulta temporal sin guardarlos, pero es conveniente y mucho más eficaz, para guardar normalmente reutiliza las consultas en una base de datos. A [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) objeto mantiene una colección, llamada a la colección de definiciones de consulta, que contiene sus definiciones de consulta guardadas.  
  
> [!NOTE]
>  Las clases de base de datos DAO son distintas de las clases de base de datos MFC basadas en Open Database Connectivity (ODBC). Todos los nombres de clase de base de datos DAO tienen el prefijo "CDao". Todavía puede acceso a orígenes de datos ODBC con las clases DAO. En general, son más eficaces que las clases MFC basadas en ODBC, las clases MFC basadas en DAO las clases basadas en DAO pueden tener acceso a datos, incluidos los controladores ODBC, a través de su propio motor de base de datos. Las clases basadas en DAO también admiten operaciones de lenguaje de definición de datos (DDL), como agregar tablas a través de las clases, sin tener que llamar a DAO directamente.  
  
## <a name="usage"></a>Uso  
 Utilizan objetos querydef ya sea para que funcione con una consulta guardada existente o para crear un nuevo guardar consultas o consulta temporal:  
  
1.  En todos los casos, crear un `CDaoQueryDef` objeto, proporcionando un puntero a la [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) del objeto al que pertenece la consulta.  
  
2.  A continuación, realice los siguientes, según lo que desee:  
  
    -   Para utilizar una consulta guardada existente, llame al objeto de definición de consulta [abiertos](#open) función miembro, proporcionando el nombre de la consulta guardada.  
  
    -   Para crear una nueva consulta guardada, llaman al objeto de definición de consulta [crear](#create) función miembro, proporcionando el nombre de la consulta. A continuación, llame a [anexado](#append) para guardar la consulta mediante la anexión a QueryDefs (colección) de la base de datos. **Crear** coloca la definición de consulta en un estado abierto, por lo que después de llamar a **crear** no llame a **abrir**.  
  
    -   Para crear una definición de consulta temporal, llame a **crear**. Pasar una cadena vacía para el nombre de la consulta. No llame a **anexado**.  
  
 Cuando haya terminado de utilizar un objeto de definición de consulta, llame a su [cerrar](#close) miembro de la función; a continuación, destruya el objeto de definición de consulta.  
  
> [!TIP]
>  Es la manera más fácil de crear las consultas guardadas crearlos y almacenarlos en la base de datos mediante Microsoft Access. A continuación, puede abrir y utilizarlos en el código MFC.  
  
## <a name="purposes"></a>Con fines de  
 Puede usar un objeto de definición de consulta para cualquiera de los siguientes fines:  
  
-   Para crear un `CDaoRecordset` objeto  
  
-   Para llamar al objeto **Execute** función de miembro para ejecutar directamente una consulta de acción o una consulta de paso a través de SQL  
  
 Puede usar un objeto de definición de consulta para cualquier tipo de consulta, incluidas select, acción, tabla de referencias cruzadas, delete, update, anexar, creación de tabla, definición de datos, paso a través SQL, union y las consultas de forma masiva. Tipo de la consulta está determinado por el contenido de la instrucción SQL que suministre. Para obtener información acerca de los tipos de consulta, vea el **Execute** y [GetType](#gettype) funciones miembro. Conjuntos de registros se suelen usar para devolver filas realiza una consulta, normalmente los usuarios que utilicen el **seleccione... DESDE** palabras clave. **Ejecutar** normalmente se utiliza para operaciones masivas. Para obtener más información, consulte [Execute](#execute) y [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md).  
  
## <a name="querydefs-and-recordsets"></a>Definiciones de consulta y conjuntos de registros  
 Usar un objeto de definición de consulta para crear un `CDaoRecordset` de objeto, normalmente crea o abre una definición de consulta como se describió anteriormente. A continuación, construya un objeto de conjunto de registros, pasando un puntero al objeto querydef cuando se llama a [CDaoRecordset:: Open](../../mfc/reference/cdaorecordset-class.md#open). La definición de consulta que se pasa debe estar en un estado abierto. Para obtener más información, vea la clase [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md).  
  
 No se puede usar una definición de consulta para crear un conjunto de registros (el uso más común de una definición de consulta), a menos que se encuentra en un estado abierto. Poner la definición de consulta en un estado abierto por una llamada a **abrir** o **crear**.  
  
## <a name="external-databases"></a>Bases de datos externas  
 Objetos QueryDef son la mejor manera de usar el dialecto SQL nativo de un motor de base de datos externa. Por ejemplo, puede crear una consulta de Transact SQL (que se utiliza en Microsoft SQL Server) y almacena en un objeto de definición de consulta. Si necesita usar una consulta SQL no se basa en el motor de base de datos de Microsoft Jet, debe proporcionar una cadena de conexión que señala al origen de datos externo. Las consultas con cadenas de conexión válidas omiten el motor de base de datos y pasan la consulta directamente en el servidor de base de datos externo para procesarla.  
  
> [!TIP]
>  Es la mejor manera de trabajar con tablas ODBC adjuntarlos a un Microsoft Jet (. Base de datos de Microsoft Access).  
  
 Para obtener información relacionada, vea los temas "Objeto QueryDef", "QueryDefs (colección)" y "Objeto CdbDatabase" en el SDK de DAO.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CDaoQueryDef`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdao.h  
  
##  <a name="append"></a>  CDaoQueryDef:: Append  
 Llame a esta función miembro después de llamar a [crear](#create) para crear un nuevo objeto de definición de consulta.  
  
```  
virtual void Append();
```  
  
### <a name="remarks"></a>Comentarios  
 **Anexar** guarda la definición de consulta en la base de datos agregando el objeto a la colección de definiciones de consulta de la base de datos. Puede usar la definición de consulta como un objeto temporal sin anexarlo, pero si desea conservar, se debe llamar a **anexado**.  
  
 Si intenta agregar un objeto de definición de consulta temporal, MFC inicia una excepción de tipo [CDaoException](../../mfc/reference/cdaoexception-class.md).  
  
##  <a name="canupdate"></a>  CDaoQueryDef::CanUpdate  
 Llame a esta función miembro para determinar si se puede modificar la definición de consulta, por ejemplo, cambiar su nombre o la cadena de SQL.  
  
```  
BOOL CanUpdate();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si se permiten modificar la definición de consulta; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 Si se puede modificar la definición de consulta:  
  
-   No se basa en una base de datos que se abrió como solo lectura.  
  
-   Tiene permisos de actualización para la base de datos.  
  
     Esto depende de si se han implementado las características de seguridad. MFC no ofrece soporte para la seguridad; debe implementarla usted mismo mediante una llamada a DAO directamente o mediante el uso de Microsoft Access. Vea el tema "Propiedad permisos" en la Ayuda de DAO.  
  
##  <a name="cdaoquerydef"></a>  CDaoQueryDef::CDaoQueryDef  
 Construye un **CDaoQueryDef** objeto.  
  
```  
CDaoQueryDef(CDaoDatabase* pDatabase);
```  
  
### <a name="parameters"></a>Parámetros  
 `pDatabase`  
 Un puntero a un formato de archivo [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) objeto.  
  
### <a name="remarks"></a>Comentarios  
 El objeto puede representar una querydef existente almacenada en QueryDefs (colección) de la base de datos, una consulta nueva que se almacenará en la colección o una consulta temporal, no va a almacenar. El paso siguiente depende del tipo de definición de consulta:  
  
-   Si el objeto representa una definición de consulta existente, llame al objeto de la [abiertos](#open) función de miembro para inicializarlo.  
  
-   Si el objeto representa una definición de consulta nueva que se guarde, llaman al objeto de la [crear](#create) función miembro. Esto agrega el objeto a la colección de definiciones de consulta de la base de datos. A continuación, llame a `CDaoQueryDef` funciones de miembro para establecer los atributos del objeto. Por último, llame a [anexado](#append).  
  
-   Si el objeto representa una definición de consulta temporal (no se guardan en la base de datos), llame a **crear**, pasando una cadena vacía para el nombre de la consulta. Después de llamar a **crear**, inicializar el objeto querydef estableciendo directamente sus atributos. No llame a **anexado**.  
  
 Para establecer los atributos de la definición de consulta, puede usar el [SetName](#setname), [SetSQL](#setsql), [SetConnect](#setconnect), [SetODBCTimeout](#setodbctimeout)y [La función SetReturnsRecords](#setreturnsrecords) funciones miembro.  
  
 Cuando termine con el objeto de definición de consulta, llame a su [cerrar](#close) función miembro. Si tiene un puntero a la definición de consulta, use la **eliminar** operador que se va a destruir el objeto de C++.  
  
##  <a name="close"></a>  CDaoQueryDef::Close  
 Llame a esta función miembro cuando haya terminado de utilizar el objeto de definición de consulta.  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>Comentarios  
 Cierre la definición de consulta libera el objeto DAO subyacente pero no destruirá el objeto de definición de consulta DAO guardado o C++ `CDaoQueryDef` objeto. Esto no es igual a [CDaoDatabase::DeleteQueryDef](../../mfc/reference/cdaodatabase-class.md#deletequerydef), que elimina la definición de consulta en la colección de definiciones de consulta de la base de datos de DAO (si no es una definición de consulta temporal).  
  
##  <a name="create"></a>  CDaoQueryDef:: Create  
 Llame a esta función miembro para crear una nueva consulta guardada o una nueva consulta temporal.  
  
```  
virtual void Create(
    LPCTSTR lpszName = NULL,  
    LPCTSTR lpszSQL = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszName`  
 El nombre único de la consulta guardada en la base de datos. Para obtener más información acerca de la cadena, vea el tema "Método CreateQueryDef" en la Ayuda de DAO. Si acepta el valor predeterminado, una cadena vacía, se crea una definición de consulta temporal. Este tipo de consulta no se guarda en la colección de definiciones de consulta.  
  
 `lpszSQL`  
 La cadena de SQL que define la consulta. Si acepta el valor predeterminado de **NULL**, posteriormente, debe llamar [SetSQL](#setsql) para establecer la cadena. Hasta entonces, la consulta es indefinida. Sin embargo, puede utilizar la consulta definida para abrir un conjunto de registros; Para obtener más información, vea la sección Comentarios. La instrucción SQL debe definirse antes de anexar la definición de consulta a la colección de definiciones de consulta.  
  
### <a name="remarks"></a>Comentarios  
 Si se pasa un nombre en `lpszName`, a continuación, puede llamar a [anexado](#append) para guardar la definición de consulta en la colección de definiciones de consulta de la base de datos. En caso contrario, el objeto es una definición de consulta temporal y no se guarda. En cualquier caso, la definición de consulta está en un estado abierto, y puede usarlo para crear un [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objeto o llamar a la definición de consulta [Execute](#execute) función miembro.  
  
 Si no proporciona una instrucción SQL en `lpszSQL`, no se puede ejecutar la consulta con **Execute** pero se puede usar para crear un conjunto de registros. En ese caso, MFC utiliza la instrucción de SQL predeterminada del conjunto de registros.  
  
##  <a name="execute"></a>  CDaoQueryDef:: Execute  
 Llame a esta función miembro para ejecutar la consulta definida por el objeto de definición de consulta.  
  
```  
virtual void Execute(int nOptions = dbFailOnError);
```  
  
### <a name="parameters"></a>Parámetros  
 `nOptions`  
 Un entero que determina las características de la consulta. Para obtener información relacionada, vea el tema "Execute Method" en la Ayuda de DAO. Puede utilizar el operador OR bit a bit ( **&#124;**) para combinar las constantes siguientes para este argumento:  
  
- **dbDenyWrite** denegar el permiso de escritura a otros usuarios.  
  
- **dbInconsistent** las actualizaciones incoherentes.  
  
- **dbConsistent** coherencia de las actualizaciones.  
  
- **dbSQLPassThrough** paso a través SQL. Hace que la instrucción SQL que se pasan a una base de datos ODBC para su procesamiento.  
  
- **dbFailOnError** valor predeterminado. Revertir las actualizaciones si se produce un error y el informe del error para el usuario.  
  
- **dbSeeChanges** generar un error de tiempo de ejecución si otro usuario está cambiando los datos que se va a editar.  
  
> [!NOTE]
>  Para obtener una explicación de los términos "incoherente" y "coherente", vea el tema "Execute Method" en la Ayuda de DAO.  
  
### <a name="remarks"></a>Comentarios  
 QueryDef (objetos) utilizados para la ejecución de esta manera solo pueden representar uno de los siguientes tipos de consulta:  
  
-   Consultas de acción  
  
-   Consultas de paso a través de SQL  
  
 **Ejecutar** no funciona para las consultas que devuelven registros, como las consultas de selección. **Ejecutar** se utiliza normalmente para las consultas de operación masiva, como **actualización**, **insertar**, o **SELECT INTO**, o para las operaciones de DDL (lenguaje) de definición de datos.  
  
> [!TIP]
>  La mejor manera de trabajar con orígenes de datos ODBC consiste en asociar las tablas a un Microsoft Jet (. Base de datos de Microsoft Access). Para obtener más información, vea el tema "Acceso a bases de datos externas con DAO" en la Ayuda de DAO.  
  
 Llame a la [GetRecordsAffected](#getrecordsaffected) función de miembro del objeto de definición de consulta para determinar el número de registros afectados por la última **Execute** llamar. Por ejemplo, `GetRecordsAffected` devuelve información sobre el número de registros eliminados, actualizados o insertados cuando se ejecuta una consulta de acción. El recuento devuelto no reflejará los cambios en las tablas relacionadas cuando cascade actualiza o elimina entran en vigor.  
  
 Si incluye ambas **dbInconsistent** y **dbConsistent** o si incluye ninguna de ellas, el resultado es el valor predeterminado, **dbInconsistent**.  
  
 **Ejecutar** no devuelve un conjunto de registros. Usar **Execute** en una consulta que selecciona los registros hace MFC producir una excepción de tipo [CDaoException](../../mfc/reference/cdaoexception-class.md).  
  
##  <a name="getconnect"></a>  CDaoQueryDef::GetConnect  
 Llame a esta función miembro para obtener la cadena de conexión asociada con el origen de datos de la definición de la consulta.  
  
```  
CString GetConnect();
```  
  
### <a name="return-value"></a>Valor devuelto  
 A [CString](../../atl-mfc-shared/reference/cstringt-class.md) que contiene la cadena de conexión para la definición de consulta.  
  
### <a name="remarks"></a>Comentarios  
 Esta función se utiliza únicamente con orígenes de datos ODBC y algunos controladores ISAM. No se utiliza con Microsoft Jet (. En el caso de las bases de datos de Microsoft Access); en este caso, `GetConnect` devuelve una cadena vacía. Para obtener más información, consulte [SetConnect](#setconnect).  
  
> [!TIP]
>  La mejor manera de trabajar con tablas ODBC consiste en asociar a una. Base de datos de Microsoft Access. Para obtener más información, vea el tema "Acceso a bases de datos externas con DAO" en la Ayuda de DAO.  
  
 Para obtener información acerca de las cadenas de conexión, vea el tema "Conectarse Property" en la Ayuda de DAO.  
  
##  <a name="getdatecreated"></a>  CDaoQueryDef::GetDateCreated  
 Llame a esta función miembro para obtener la fecha en que se creó el objeto de definición de consulta.  
  
```  
COleDateTime GetDateCreated();
```  
  
### <a name="return-value"></a>Valor devuelto  
 A [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objeto que contiene la fecha y hora en que se creó la definición de consulta.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener información relacionada, vea el tema "DateCreated y LastUpdated propiedades" en la Ayuda de DAO.  
  
##  <a name="getdatelastupdated"></a>  CDaoQueryDef::GetDateLastUpdated  
 Llamada a esta función miembro para obtener el objeto de definición de consulta de la fecha en que se actualizó por última vez, cuando cualquiera de sus propiedades se han cambiado, por ejemplo, su nombre, su cadena SQL y su cadena de conexión.  
  
```  
COleDateTime GetDateLastUpdated();
```  
  
### <a name="return-value"></a>Valor devuelto  
 A [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objeto que contiene la fecha y hora que se actualizó por última vez la definición de consulta.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener información relacionada, vea el tema "DateCreated y LastUpdated propiedades" en la Ayuda de DAO.  
  
##  <a name="getfieldcount"></a>  CDaoQueryDef::GetFieldCount  
 Llame a esta función miembro para recuperar el número de campos de la consulta.  
  
```  
short GetFieldCount();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de campos definidos en la consulta.  
  
### <a name="remarks"></a>Comentarios  
 `GetFieldCount` es útil para recorrer en iteración todos los campos de la definición de consulta. Para ello, use `GetFieldCount` junto con [GetFieldInfo](#getfieldinfo).  
  
##  <a name="getfieldinfo"></a>  CDaoQueryDef::GetFieldInfo  
 Llame a esta función miembro para obtener diversos tipos de información acerca de un campo definido en la definición de consulta.  
  
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
 Índice de base cero del campo deseado en la colección de campos de la definición de la consulta, para la búsqueda por su índice.  
  
 `fieldinfo`  
 Una referencia a un `CDaoFieldInfo` objeto que devuelve la información solicitada.  
  
 `dwInfoOptions`  
 Opciones que especifican qué información sobre el campo que desea recuperar. Las opciones disponibles son las siguientes junto con lo que hacen que la función devolver:  
  
- `AFX_DAO_PRIMARY_INFO` (Valor predeterminado) Nombre, tipo, tamaño, atributos  
  
- `AFX_DAO_SECONDARY_INFO` Signo más de información principal: posición Ordinal, necesario, Permitir longitud cero, el campo de origen, nombre externa, tabla de origen, orden de intercalación  
  
- `AFX_DAO_ALL_INFO` Más información primaria y secundaria: regla de validación de valor predeterminado, el texto de validación,  
  
 `lpszName`  
 Una cadena que contiene el nombre del campo deseado, para la búsqueda por nombre. Puede usar un [CString](../../atl-mfc-shared/reference/cstringt-class.md).  
  
### <a name="remarks"></a>Comentarios  
 Para obtener una descripción de la información devuelta en `fieldinfo`, consulte el [CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md) estructura. Esta estructura no tiene miembros que se corresponden con la información descriptiva en `dwInfoOptions` anteriormente. Si se solicita un nivel de información, obtendrá los niveles anteriores de información también.  
  
##  <a name="getname"></a>  CDaoQueryDef::GetName  
 Llame a esta función miembro para recuperar el nombre de la consulta representada por la definición de consulta.  
  
```  
CString GetName();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Nombre de la consulta.  
  
### <a name="remarks"></a>Comentarios  
 Los nombres de definición de consulta son nombres únicos definidos por el usuario. Para obtener más información acerca de los nombres de definición de consulta, vea el tema "Nombre de propiedad" en la Ayuda de DAO.  
  
##  <a name="getodbctimeout"></a>  CDaoQueryDef::GetODBCTimeout  
 Llame a esta función miembro para recuperar el límite de tiempo actual antes agote el tiempo de espera de una consulta a un origen de datos ODBC.  
  
```  
short GetODBCTimeout();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de segundos antes de que una consulta agote el tiempo de espera.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener información acerca de este límite de tiempo, vea el tema "Propiedad ODBCTimeout" en la Ayuda de DAO.  
  
> [!TIP]
>  Es la mejor manera de trabajar con tablas ODBC adjuntarlos a un Microsoft Jet (. Base de datos de Microsoft Access). Para obtener más información, vea el tema "Acceso a bases de datos externas con DAO" en la Ayuda de DAO.  
  
##  <a name="getparametercount"></a>  CDaoQueryDef::GetParameterCount  
 Llame a esta función miembro para recuperar el número de parámetros en la consulta guardada.  
  
```  
short GetParameterCount();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de parámetros definidos en la consulta.  
  
### <a name="remarks"></a>Comentarios  
 `GetParameterCount` es útil para recorrer en iteración todos los parámetros en la definición de consulta. Para ello, use `GetParameterCount` junto con [GetParameterInfo](#getparameterinfo).  
  
 Para obtener información relacionada, vea los temas "Objeto Parameter", "Colección de parámetros" y "declaración de parámetros (SQL)" en la Ayuda de DAO.  
  
##  <a name="getparameterinfo"></a>  CDaoQueryDef::GetParameterInfo  
 Llame a esta función miembro para obtener información sobre un parámetro definido en la definición de consulta.  
  
```  
void GetParameterInfo(
    int nIndex,  
    CDaoParameterInfo& paraminfo,  
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

 
void GetParameterInfo(
    LPCTSTR lpszName,  
    CDaoParameterInfo& paraminfo,  
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 Índice de base cero del parámetro deseado en la colección de parámetros de la definición de la consulta, para la búsqueda por su índice.  
  
 `paraminfo`  
 Una referencia a un [CDaoParameterInfo](../../mfc/reference/cdaoparameterinfo-structure.md) objeto que devuelve la información solicitada.  
  
 `dwInfoOptions`  
 Opciones que especifican qué información sobre el parámetro para recuperar. La opción disponible aparece aquí junto con lo que hace la función devolver:  
  
- `AFX_DAO_PRIMARY_INFO` (Valor predeterminado) Nombre de tipo  
  
 `lpszName`  
 Una cadena que contiene el nombre del parámetro deseado, para la búsqueda por nombre. Puede usar un [CString](../../atl-mfc-shared/reference/cstringt-class.md).  
  
### <a name="remarks"></a>Comentarios  
 Para obtener una descripción de la información devuelta en `paraminfo`, consulte el [CDaoParameterInfo](../../mfc/reference/cdaoparameterinfo-structure.md) estructura. Esta estructura no tiene miembros que se corresponden con la información descriptiva en `dwInfoOptions` anteriormente.  
  
 Para obtener información relacionada, vea el tema "declaración de parámetros (SQL)" en la Ayuda de DAO.  
  
##  <a name="getparamvalue"></a>  CDaoQueryDef:: GetParamValue  
 Llame a esta función miembro para recuperar el valor actual del parámetro especificado almacenado en la colección de parámetros de la definición de la consulta.  
  
```  
virtual COleVariant GetParamValue(LPCTSTR lpszName);  
virtual COleVariant GetParamValue(int nIndex);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszName`  
 El nombre del parámetro cuyo valor desee, para la búsqueda por nombre.  
  
 `nIndex`  
 Índice de base cero del parámetro en la colección de parámetros de la definición de la consulta, para la búsqueda por su índice. Puede obtener este valor con llamadas a [GetParameterCount](#getparametercount) y [GetParameterInfo](#getparameterinfo).  
  
### <a name="return-value"></a>Valor devuelto  
 Un objeto de clase [COleVariant](../../mfc/reference/colevariant-class.md) que contiene el valor del parámetro.  
  
### <a name="remarks"></a>Comentarios  
 El parámetro puede tener acceso por nombre o por su posición ordinal en la colección.  
  
 Para obtener información relacionada, vea el tema "declaración de parámetros (SQL)" en la Ayuda de DAO.  
  
##  <a name="getrecordsaffected"></a>  CDaoQueryDef::GetRecordsAffected  
 Llame a esta función miembro para determinar el número de registros afectado por la última llamada de [Execute](#execute).  
  
```  
long GetRecordsAffected();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de registros afectados.  
  
### <a name="remarks"></a>Comentarios  
 El recuento devuelto no reflejará los cambios en las tablas relacionadas cuando cascade actualiza o elimina entran en vigor.  
  
 Para obtener información relacionada, vea el tema "RecordsAffected (propiedad)" en la Ayuda de DAO.  
  
##  <a name="getreturnsrecords"></a>  CDaoQueryDef::GetReturnsRecords  
 Llame a esta función miembro para determinar si la definición de consulta se basa en una consulta que devuelve los registros.  
  
```  
BOOL GetReturnsRecords();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la definición de consulta se basa en una consulta que devuelve los registros; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro solo se utiliza para las consultas de paso a través de SQL. Para obtener más información acerca de las consultas SQL, vea el [Execute](#execute) función miembro. Para obtener más información sobre cómo trabajar con consultas de paso a través de SQL, vea el [la función SetReturnsRecords](#setreturnsrecords) función miembro.  
  
 Para obtener información relacionada, vea el tema "Propiedad ReturnsRecords" en la Ayuda de DAO.  
  
##  <a name="getsql"></a>  CDaoQueryDef::GetSQL  
 Llame a esta función miembro para recuperar la instrucción SQL que define la consulta en el que se basa la definición de consulta.  
  
```  
CString GetSQL();
```  
  
### <a name="return-value"></a>Valor devuelto  
 La instrucción SQL que define la consulta en el que se basa la definición de consulta.  
  
### <a name="remarks"></a>Comentarios  
 A continuación, probablemente analizará la cadena de palabras clave, los nombres de tabla y así sucesivamente.  
  
 Para obtener información relacionada, vea los temas "SQL Property", "Comparación de Microsoft Jet base de datos del motor y ANSI SQL" y "Consultar una base de datos con SQL en código" en la Ayuda de DAO.  
  
##  <a name="gettype"></a>  CDaoQueryDef::GetType  
 Llame a esta función miembro para determinar el tipo de consulta de la definición de consulta.  
  
```  
short GetType();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El tipo de la consulta definida por la definición de consulta. Para los valores, vea la sección Comentarios.  
  
### <a name="remarks"></a>Comentarios  
 El tipo de consulta se establece por lo que especifique en la cadena de la definición de la consulta SQL al crear la definición de consulta o llamar a una definición de consulta existente [SetSQL](#setsql) función miembro. El tipo de consulta devuelto por esta función puede ser uno de los valores siguientes:  
  
- **dbQSelect** seleccionar  
  
- **dbQAction** acción  
  
- **dbQCrosstab** tabla de referencias cruzadas  
  
- **dbQDelete** eliminar  
  
- **dbQUpdate** actualización  
  
- **dbQAppend** anexado  
  
- **dbQMakeTable** creación de tabla  
  
- **dbQDDL** definición de datos  
  
- **dbQSQLPassThrough** paso a través  
  
- **dbQSetOperation** Union  
  
- **dbQSPTBulk** utilizar con **dbQSQLPassThrough** para especificar una consulta que no devuelve ningún registro.  
  
> [!NOTE]
>  Para crear una consulta de paso a través de SQL, no establezca la **dbSQLPassThrough** constante. Esto se establece automáticamente el motor de base de datos de Microsoft Jet cuando se crea un objeto de definición de consulta y establece la cadena de conexión.  
  
 Para obtener información acerca de las cadenas SQL, consulte [GetSQL](#getsql). Para obtener información acerca de los tipos de consulta, vea [Execute](#execute).  
  
##  <a name="isopen"></a>  CDaoQueryDef::IsOpen  
 Llame a esta función miembro para determinar si la `CDaoQueryDef` objeto está abierto actualmente.  
  
```  
BOOL IsOpen() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si la `CDaoQueryDef` objeto está actualmente abierto; de lo contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Una definición de consulta debe estar en un estado abierto antes de utilizarla para llamar a [Execute](#execute) o para crear un [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objeto. Para poner una definición de consulta en una llamada de estado abierto o [crear](#create) (para un nuevo objeto querydef) o [abrir](#open) (para una definición de consulta existente).  
  
##  <a name="m_pdatabase"></a>  CDaoQueryDef::m_pDatabase  
 Contiene un puntero a la [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) objeto asociado con el objeto de definición de consulta.  
  
### <a name="remarks"></a>Comentarios  
 Use este puntero si necesita acceso directo a la base de datos: por ejemplo obtener punteros a otra definición de consulta o conjunto de registros objetos en colecciones de la base de datos.  
  
##  <a name="m_pdaoquerydef"></a>  CDaoQueryDef::m_pDAOQueryDef  
 Contiene un puntero a la interfaz OLE para el objeto de definición de consulta DAO subyacente.  
  
### <a name="remarks"></a>Comentarios  
 This (puntero) se proporciona para la integridad y la coherencia con las otras clases. Sin embargo, puesto que MFC encapsula totalmente en su lugar las definiciones de consulta DAO, es poco probable que necesite. Si usa, hacerlo con precaución, en particular, no cambie el valor del puntero a menos que sepa lo que está haciendo.  
  
##  <a name="open"></a>  CDaoQueryDef::Open  
 Llame a esta función miembro para abrir una definición de consulta previamente guardado en la colección de definiciones de consulta de la base de datos.  
  
```  
virtual void Open(LPCTSTR lpszName = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszName`  
 Una cadena que contiene el nombre de la definición de consulta guardada para abrir. Puede usar un [CString](../../atl-mfc-shared/reference/cstringt-class.md).  
  
### <a name="remarks"></a>Comentarios  
 Una vez que la definición de consulta está abierta, puede llamar a su [Execute](#execute) función miembro o el uso de la definición de consulta para crear un [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objeto.  
  
##  <a name="setconnect"></a>  CDaoQueryDef::SetConnect  
 Llame a esta función miembro para establecer la cadena de conexión del objeto de definición de consulta.  
  
```  
void SetConnect(LPCTSTR lpszConnect);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszConnect`  
 Una cadena que contiene una cadena de conexión para el asociado [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) objeto.  
  
### <a name="remarks"></a>Comentarios  
 La cadena de conexión se utiliza para pasar información adicional a controladores ODBC y algunos controladores ISAM, según sea necesario. No se utiliza para Microsoft Jet (. En el caso de las bases de datos de Microsoft Access).  
  
> [!TIP]
>  La mejor manera de trabajar con tablas ODBC consiste en asociar a una. Base de datos de Microsoft Access.  
  
 Antes de ejecutar una definición de consulta que representa una consulta de paso a través de SQL a un origen de datos ODBC, establezca la cadena de conexión con `SetConnect` y llame a [la función SetReturnsRecords](#setreturnsrecords) para especificar si la consulta devuelve registros.  
  
 Para obtener más información acerca de la estructura y los ejemplos de componentes de la cadena de conexión de la cadena de conexión, vea el tema "Conectarse Property" en la Ayuda de DAO.  
  
##  <a name="setname"></a>  CDaoQueryDef::SetName  
 Llame a esta función miembro si desea cambiar el nombre de una definición de consulta que no es temporal.  
  
```  
void SetName(LPCTSTR lpszName);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszName`  
 Una cadena que contiene el nuevo nombre para una consulta en el asociado producen [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) objeto.  
  
### <a name="remarks"></a>Comentarios  
 Los nombres de definición de consulta son nombres únicos y definidos por el usuario. Puede llamar a `SetName` antes de la definición de consulta el objeto se anexa a la colección de definiciones de consulta.  
  
##  <a name="setodbctimeout"></a>  CDaoQueryDef::SetODBCTimeout  
 Llame a esta función miembro para establecer el límite de tiempo antes agote el tiempo de espera de una consulta a un origen de datos ODBC.  
  
```  
void SetODBCTimeout(short nODBCTimeout);
```  
  
### <a name="parameters"></a>Parámetros  
 *nODBCTimeout*  
 El número de segundos antes de que una consulta agote el tiempo de espera.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro le permite invalidar el número predeterminado de segundos antes de que las operaciones subsiguientes en el origen de datos conectado "tiempo de espera". Una operación podría tiempo de espera debido a problemas de acceso de red, el tiempo de procesamiento de consulta excesivo y así sucesivamente. Llame a `SetODBCTimeout` antes de ejecutar una consulta con esta definición de consulta si desea cambiar el valor de tiempo de espera de consulta. (Como ODBC reutiliza las conexiones, el valor de tiempo de espera es el mismo para todos los clientes en la misma conexión.)  
  
 El valor predeterminado para los tiempos de espera de consulta es 60 segundos.  
  
##  <a name="setparamvalue"></a>  CDaoQueryDef:: SetParamValue  
 Llame a esta función miembro para establecer el valor de un parámetro en la definición de consulta en tiempo de ejecución.  
  
```  
virtual void SetParamValue(
    LPCTSTR lpszName,  
    const COleVariant& varValue);

 
virtual void SetParamValue(
    int nIndex,  
    const COleVariant& varValue);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszName`  
 El nombre del parámetro cuyo valor desea establecer.  
  
 `varValue`  
 El valor que se va a establecer; vea la sección Comentarios.  
  
 `nIndex`  
 La posición ordinal del parámetro en la colección de parámetros de la definición de la consulta. Puede obtener este valor con llamadas a [GetParameterCount](#getparametercount) y [GetParameterInfo](#getparameterinfo).  
  
### <a name="remarks"></a>Comentarios  
 El parámetro ya se debe haber establecido como parte de la cadena de la definición de la consulta SQL. El parámetro puede tener acceso por nombre o por su posición ordinal en la colección.  
  
 Especifique el valor que se establecerá como un `COleVariant` objeto. Para obtener información acerca de cómo establecer el valor deseado y el tipo en su `COleVariant` de objetos, vea la clase [COleVariant](../../mfc/reference/colevariant-class.md).  
  
##  <a name="setreturnsrecords"></a>  CDaoQueryDef::SetReturnsRecords  
 Llame a esta función miembro como parte del proceso de configuración de una consulta de paso a través de SQL a una base de datos externo.  
  
```  
void SetReturnsRecords(BOOL bReturnsRecords);
```  
  
### <a name="parameters"></a>Parámetros  
 *bReturnsRecords*  
 Pasar **TRUE** si la consulta en una base de datos externa devuelve registros; en caso contrario, **FALSE**.  
  
### <a name="remarks"></a>Comentarios  
 En tal caso, debe crear la definición de consulta y establezca sus propiedades mediante otro `CDaoQueryDef` funciones miembro. Para obtener una descripción de las bases de datos externos, vea [SetConnect](#setconnect).  
  
##  <a name="setsql"></a>  CDaoQueryDef::SetSQL  
 Llame a esta función miembro para establecer la instrucción SQL que se ejecuta la definición de consulta.  
  
```  
void SetSQL(LPCTSTR lpszSQL);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszSQL`  
 Una cadena que contiene una instrucción SQL completa, adecuada para la ejecución. La sintaxis de esta cadena depende del DBMS que el destino de la consulta. Para obtener una explicación de la sintaxis utilizada en el motor de base de datos de Microsoft Jet, vea el tema "Generar instrucciones en código SQL" en la Ayuda de DAO.  
  
### <a name="remarks"></a>Comentarios  
 Un uso típico de `SetSQL` es configurar un objeto de definición de consulta para su uso en una consulta de paso a través de SQL. (Para obtener la sintaxis de consultas de paso a través de SQL en el DBMS de destino, vea la documentación para el sistema DBMS).  
  
## <a name="see-also"></a>Vea también  
 [CObject (clase)](../../mfc/reference/cobject-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CDaoRecordset (clase)](../../mfc/reference/cdaorecordset-class.md)   
 [CDaoDatabase (clase)](../../mfc/reference/cdaodatabase-class.md)   
 [Clase CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)   
 [CDaoException (clase)](../../mfc/reference/cdaoexception-class.md)
