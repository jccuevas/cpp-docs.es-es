---
title: Clase CDaoQueryDef | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDaoQueryDef
dev_langs:
- C++
helpviewer_keywords:
- QueryDef objects
- CDaoQueryDef class
- queries [Visual Studio], defining
ms.assetid: 9676a4a3-c712-44d4-8c5d-d1cc78288d3a
caps.latest.revision: 24
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
ms.openlocfilehash: 0bf06c68bb7072aa1907e4c730848cca9ff5e7d0
ms.lasthandoff: 02/24/2017

---
# <a name="cdaoquerydef-class"></a>CDaoQueryDef (clase)
Representa una definición de consulta o "querydef", normalmente guardada en una base de datos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CDaoQueryDef : public CObject  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CDaoQueryDef::CDaoQueryDef](#cdaoquerydef)|Construye un **CDaoQueryDef** objeto. A continuación llama a **abiertos** o **crear**, en función de sus necesidades.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CDaoQueryDef:: Append](#append)|Anexa la definición de consulta a la colección de definiciones de consulta de la base de datos como una consulta guardada.|  
|[CDaoQueryDef::CanUpdate](#canupdate)|Devuelve cero si la consulta puede actualizar la base de datos.|  
|[CDaoQueryDef::Close](#close)|Cierra el objeto de definición de consulta. Destruye el objeto de C++ cuando haya terminado con él.|  
|[CDaoQueryDef:: Create](#create)|Crea el objeto de definición de consulta DAO subyacente. Usar la definición de consulta como una consulta temporal o llamada **anexado** para guardar en la base de datos.|  
|[CDaoQueryDef:: Execute](#execute)|Ejecuta la consulta definida por el objeto de definición de consulta.|  
|[CDaoQueryDef::GetConnect](#getconnect)|Devuelve la cadena de conexión asociada con la definición de consulta. La cadena de conexión identifica el origen de datos. (Para SQL acceso directo consulta solamente; de lo contrario, una cadena vacía.)|  
|[CDaoQueryDef::GetDateCreated](#getdatecreated)|Devuelve la fecha en que se creó la consulta guardada.|  
|[CDaoQueryDef::GetDateLastUpdated](#getdatelastupdated)|Devuelve la fecha en que se actualizó por última vez la consulta guardada.|  
|[CDaoQueryDef::GetFieldCount](#getfieldcount)|Devuelve el número de campos definidos por la definición de consulta.|  
|[CDaoQueryDef::GetFieldInfo](#getfieldinfo)|Devuelve información acerca de un campo especificado definido en la consulta.|  
|[CDaoQueryDef::GetName](#getname)|Devuelve el nombre de la definición de consulta.|  
|[CDaoQueryDef::GetODBCTimeout](#getodbctimeout)|Devuelve el valor de tiempo de espera utilizado por ODBC (para una consulta ODBC) cuando se ejecuta la definición de consulta. Determina cuánto tiempo permitir que se complete la acción de la consulta.|  
|[CDaoQueryDef::GetParameterCount](#getparametercount)|Devuelve el número de parámetros definidos para la consulta.|  
|[CDaoQueryDef::GetParameterInfo](#getparameterinfo)|Devuelve información sobre un parámetro especificado en la consulta.|  
|[CDaoQueryDef:: GetParamValue](#getparamvalue)|Devuelve el valor del parámetro especificado en la consulta.|  
|[CDaoQueryDef::GetRecordsAffected](#getrecordsaffected)|Devuelve el número de registros afectados por una consulta de acción.|  
|[CDaoQueryDef::GetReturnsRecords](#getreturnsrecords)|Devuelve cero si la consulta definida por la definición de consulta devuelve registros.|  
|[CDaoQueryDef::GetSQL](#getsql)|Devuelve la cadena SQL que especifica la consulta definida por la definición de consulta.|  
|[CDaoQueryDef::GetType](#gettype)|Devuelve el tipo de consulta: eliminar, actualizar, anexar, creación de tabla y así sucesivamente.|  
|[CDaoQueryDef::IsOpen](#isopen)|Devuelve cero si la definición de consulta está abierta y se puede ejecutar.|  
|[CDaoQueryDef::Open](#open)|Se abre una definición de consulta existente almacenado en la colección de definiciones de consulta de la base de datos.|  
|[CDaoQueryDef::SetConnect](#setconnect)|Establece la cadena de conexión para una consulta de paso a través de SQL en un origen de datos ODBC.|  
|[CDaoQueryDef::SetName](#setname)|Establece el nombre de la consulta guardada, reemplazando el nombre en uso cuando se creó la definición de consulta.|  
|[CDaoQueryDef::SetODBCTimeout](#setodbctimeout)|Establece el valor de tiempo de espera utilizado por ODBC (para una consulta ODBC) cuando se ejecuta la definición de consulta.|  
|[CDaoQueryDef:: SetParamValue](#setparamvalue)|Establece el valor del parámetro especificado en la consulta.|  
|[CDaoQueryDef::SetReturnsRecords](#setreturnsrecords)|Especifica si la definición de consulta devuelve registros. Establecer este atributo en **TRUE** sólo es válido para consultas de paso a través de SQL.|  
|[CDaoQueryDef::SetSQL](#setsql)|Establece la cadena SQL que especifica la consulta definida por la definición de consulta.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CDaoQueryDef::m_pDAOQueryDef](#m_pdaoquerydef)|Puntero a la interfaz OLE para el objeto de definición de consulta DAO subyacente.|  
|[CDaoQueryDef::m_pDatabase](#m_pdatabase)|Un puntero a la `CDaoDatabase` objeto al que está asociada la definición de consulta. La definición de consulta puede guardarse en la base de datos o no.|  
  
## <a name="remarks"></a>Comentarios  
 Una definición de consulta es un objeto de acceso a datos que contiene la instrucción SQL que describe una consulta y sus propiedades, como "Fecha de creación" y "Tiempo de espera ODBC". También puede crear objetos de definición de consulta temporal sin guardarlos, pero es conveniente y mucho más eficaz, para guardar habitualmente reutiliza consultas en una base de datos. Un [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) objeto mantiene una colección, denominada el QueryDefs (colección), que contiene sus definiciones de consulta guardadas.  
  
> [!NOTE]
>  Las clases de base de datos DAO son distintas de las clases de base de datos MFC basadas en Open Database Connectivity (ODBC). Todos los nombres de clase de base de datos DAO tienen el prefijo "CDao". Aún puede acceso a orígenes de datos ODBC con las clases DAO. En general, son más eficaces que las clases MFC basadas en ODBC, las clases MFC basadas en DAO las clases basadas en DAO pueden tener acceso a datos, incluidos los controladores ODBC, mediante su propio motor de base de datos. Las clases de DAO también admiten operaciones de lenguaje de definición de datos (DDL), como agregar tablas a través de las clases, sin tener que llamar a DAO directamente.  
  
## <a name="usage"></a>Uso  
 Usar objetos de definición de consulta para que funcione con una consulta guardada existente o para crear un nuevo Guardar consulta o temporal:  
  
1.  En todos los casos, construir una `CDaoQueryDef` objeto, proporcionando un puntero a la [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) del objeto al que pertenece la consulta.  
  
2.  A continuación, haga lo siguiente, según lo que desee:  
  
    -   Para utilizar una consulta guardada existente, llame al objeto de definición de consulta [abiertos](#open) función miembro, proporcionando el nombre de la consulta guardada.  
  
    -   Para crear una nueva consulta guardada, llame al objeto de definición de consulta [crear](#create) función miembro, proporcionando el nombre de la consulta. A continuación, llame a [anexado](#append) para guardar la consulta, ésta se agrega a la colección de definiciones de consulta de la base de datos. **Crear** coloca la definición de consulta en este estado, es así después de llamar a **crear** no se llama **abrir**.  
  
    -   Para crear una definición de consulta temporal, llame a **crear**. Pasar una cadena vacía para el nombre de la consulta. No llame a **anexado**.  
  
 Cuando termine de utilizar un objeto de definición de consulta, llame a su [cerrar](#close) miembro de función; a continuación, destruya el objeto de definición de consulta.  
  
> [!TIP]
>  Es la manera más fácil de crear consultas guardadas crearlos y almacenarlos en la base de datos mediante Microsoft Access. A continuación, puede abrir y utilizarlos en el código MFC.  
  
## <a name="purposes"></a>Efectos  
 Puede utilizar un objeto querydef para cualquiera de los siguientes fines:  
  
-   Para crear un `CDaoRecordset` objeto  
  
-   Para llamar al objeto **Execute** función miembro para ejecutar directamente una consulta de acción o una consulta de paso a través de SQL  
  
 Puede usar un objeto querydef para cualquier tipo de consulta, incluyendo select, acción, referencias cruzadas, delete, update, anexar, creación de tabla, definición de datos, paso a través SQL, union y consultas masivas. Tipo de consulta está determinado por el contenido de la instrucción SQL que proporcione. Para obtener información acerca de los tipos de consulta, vea el **Execute** y [GetType](#gettype) funciones miembro. Conjuntos de registros se utilizan normalmente para devolver filas consultas, normalmente los usuarios que utilicen el **seleccione... DESDE** palabras clave. **Ejecutar** se utiliza habitualmente para operaciones masivas. Para obtener más información, consulte [Execute](#execute) y [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md).  
  
## <a name="querydefs-and-recordsets"></a>Definiciones de consulta y conjuntos de registros  
 Utilizar un objeto querydef para crear un `CDaoRecordset` objeto suelen crear o abrir una definición de consulta, como se describió anteriormente. A continuación, construya un objeto de conjunto de registros, pasando un puntero al objeto de definición de consulta cuando se llama a [CDaoRecordset:: Open](../../mfc/reference/cdaorecordset-class.md#open). La definición de consulta que se pasa debe estar en un estado abierto. Para obtener más información, vea la clase [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md).  
  
 No puede usar una definición de consulta para crear un conjunto de registros (es decir, el uso más común para una definición de consulta) a menos que esté en estado abierto. Poner la definición de consulta en un estado abierto llamando **abrir** o **crear**.  
  
## <a name="external-databases"></a>Bases de datos externas  
 Objetos QueryDef son la mejor manera de usar el dialecto SQL nativo de un motor de base de datos externa. Por ejemplo, puede crear una consulta de Transact SQL (como se utiliza en Microsoft SQL Server) y almacenarlo en un objeto de definición de consulta. Cuando necesite utilizar una consulta SQL no se basa en el motor de base de datos Microsoft Jet, debe proporcionar una cadena de conexión que apunta al origen de datos externo. Consultas con cadenas de conexión válidas omiten el motor de base de datos y pasan la consulta directamente al servidor de base de datos externo para procesarla.  
  
> [!TIP]
>  Es la manera preferida de trabajar con tablas ODBC adjuntarlos a un Microsoft Jet (. Base de datos de Microsoft Access).  
  
 Para obtener información relacionada, vea los temas "Objeto QueryDef", "QueryDefs (colección)" y "Objeto CdbDatabase" en el SDK de DAO.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CDaoQueryDef`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdao.h  
  
##  <a name="a-nameappenda--cdaoquerydefappend"></a><a name="append"></a>CDaoQueryDef:: Append  
 Llame a esta función miembro después de llamar a [crear](#create) para crear un nuevo objeto de definición de consulta.  
  
```  
virtual void Append();
```  
  
### <a name="remarks"></a>Comentarios  
 **Anexar** guarda la definición de consulta en la base de datos agregando el objeto a la colección de definiciones de consulta de la base de datos. Puede usar la definición de consulta como objeto temporal sin agregarlo, pero si desea conservar, debe llamar a **anexado**.  
  
 Si intenta agregar un objeto de definición de consulta temporal, MFC inicia una excepción de tipo [CDaoException](../../mfc/reference/cdaoexception-class.md).  
  
##  <a name="a-namecanupdatea--cdaoquerydefcanupdate"></a><a name="canupdate"></a>CDaoQueryDef::CanUpdate  
 Llame a esta función miembro para determinar si se puede modificar la definición de consulta, como cambiar su nombre o la cadena SQL.  
  
```  
BOOL CanUpdate();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si se le permite modificar la definición de consulta; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Si se puede modificar la definición de consulta:  
  
-   No se basa en una base de datos está abierta en modo de sólo lectura.  
  
-   Tener permisos de actualización para la base de datos.  
  
     Esto depende de si se han implementado las características de seguridad. MFC no ofrece soporte para la seguridad; debe implementarlo usted mismo al llamar a DAO directamente o mediante el uso de Microsoft Access. Consulte el tema "Propiedad permisos" en la Ayuda de DAO.  
  
##  <a name="a-namecdaoquerydefa--cdaoquerydefcdaoquerydef"></a><a name="cdaoquerydef"></a>CDaoQueryDef::CDaoQueryDef  
 Construye un **CDaoQueryDef** objeto.  
  
```  
CDaoQueryDef(CDaoDatabase* pDatabase);
```  
  
### <a name="parameters"></a>Parámetros  
 `pDatabase`  
 Un puntero a un formato de archivo [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) objeto.  
  
### <a name="remarks"></a>Comentarios  
 El objeto puede representar una querydef existente almacenada en QueryDefs (colección) de la base de datos, una consulta nueva que se almacenará en la colección o una consulta temporal, no para almacenarse. El siguiente paso depende del tipo de definición de consulta:  
  
-   Si el objeto representa una definición de consulta existente, llame al objeto de la [abiertos](#open) función miembro para inicializarlo.  
  
-   Si el objeto representa una definición de consulta nueva que se guarde, llame al objeto de la [crear](#create) función miembro. Esto agrega el objeto a la colección de definiciones de consulta de la base de datos. A continuación, llame a `CDaoQueryDef` funciones miembro para establecer los atributos del objeto. Por último, llame a [anexado](#append).  
  
-   Si el objeto representa una definición de consulta temporal (no se guardan en la base de datos), llame a **crear**, pasando una cadena vacía para el nombre de la consulta. Después de llamar a **crear**, inicializar el objeto querydef estableciendo directamente sus atributos. No llame a **anexado**.  
  
 Para establecer los atributos de la definición de consulta, puede usar el [SetName](#setname), [SetSQL](#setsql), [SetConnect](#setconnect), [SetODBCTimeout](#setodbctimeout), y [la función SetReturnsRecords](#setreturnsrecords) funciones miembro.  
  
 Cuando termine con el objeto de definición de consulta, llame a su [cerrar](#close) función miembro. Si tiene un puntero a la definición de consulta, utilice la **eliminar** operador para destruir el objeto de C++.  
  
##  <a name="a-nameclosea--cdaoquerydefclose"></a><a name="close"></a>CDaoQueryDef::Close  
 Llame a esta función miembro cuando haya terminado de utilizar el objeto de definición de consulta.  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>Comentarios  
 Cierre la definición de consulta libera el objeto DAO subyacente pero no destruye el objeto de definición de consulta DAO guardado o C++ `CDaoQueryDef` objeto. No es igual a [CDaoDatabase::DeleteQueryDef](../../mfc/reference/cdaodatabase-class.md#deletequerydef), que elimina la definición de consulta en la colección de definiciones de consulta de la base de datos de DAO (si no es una definición de consulta temporal).  
  
##  <a name="a-namecreatea--cdaoquerydefcreate"></a><a name="create"></a>CDaoQueryDef:: Create  
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
 La cadena SQL que define la consulta. Si acepta el valor predeterminado de **NULL**, más adelante se debe llamar a [SetSQL](#setsql) para establecer la cadena. Hasta entonces, la consulta es indefinida. Sin embargo, puede utilizar la consulta definida para abrir un conjunto de registros; Para obtener más información, vea la sección Comentarios. La instrucción SQL debe definirse antes de anexar la definición de consulta a la colección de definiciones de consulta.  
  
### <a name="remarks"></a>Comentarios  
 Si se pasa un nombre de `lpszName`, a continuación, puede llamar a [anexado](#append) para guardar la definición de consulta en la colección de definiciones de consulta de la base de datos. De lo contrario, el objeto es un objeto querydef temporal y no se guarda. En cualquier caso, la definición de consulta está en un estado abierto y puede usarlo para crear un [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) de objeto o llamar a la definición de consulta [Execute](#execute) función miembro.  
  
 Si no se proporciona una instrucción SQL en `lpszSQL`, no se puede ejecutar la consulta con **Execute** pero se puede utilizar para crear un conjunto de registros. En ese caso, MFC utiliza la instrucción de SQL predeterminada del conjunto de registros.  
  
##  <a name="a-nameexecutea--cdaoquerydefexecute"></a><a name="execute"></a>CDaoQueryDef:: Execute  
 Llame a esta función miembro para ejecutar la consulta definida por el objeto de definición de consulta.  
  
```  
virtual void Execute(int nOptions = dbFailOnError);
```  
  
### <a name="parameters"></a>Parámetros  
 `nOptions`  
 Un entero que determina las características de la consulta. Para obtener información relacionada, vea el tema "Ejecutar el método" en la Ayuda de DAO. Puede utilizar el operador OR bit a bit ( **|**) para combinar las constantes siguientes para este argumento:  
  
- **dbDenyWrite** denegar el permiso de escritura a otros usuarios.  
  
- **dbInconsistent** actualizaciones incoherentes.  
  
- **dbConsistent** actualizaciones coherentes.  
  
- **dbSQLPassThrough** paso a través SQL. Hace que la instrucción SQL que se pasan a una base de datos ODBC para su procesamiento.  
  
- **dbFailOnError** valor predeterminado. Revertir las actualizaciones si se produce un error y el informe el error al usuario.  
  
- **dbSeeChanges** generará un error de tiempo de ejecución si otro usuario cambia datos que está modificando.  
  
> [!NOTE]
>  Para obtener una explicación de los términos "incoherente" y "coherente", vea el tema "Ejecutar el método" en la Ayuda de DAO.  
  
### <a name="remarks"></a>Comentarios  
 Objetos QueryDef utilizados para la ejecución de esta manera sólo pueden representar uno de los siguientes tipos de consulta:  
  
-   Consultas de acción  
  
-   Consultas de paso a través de SQL  
  
 **Ejecutar** no funciona para las consultas que devuelven registros, como las consultas de selección. **Ejecutar** se utiliza normalmente para las consultas de operación masiva, como **actualización**, **insertar**, o **SELECT INTO**, o para operaciones de DDL (lenguaje) de definición de datos.  
  
> [!TIP]
>  La manera preferida de trabajar con orígenes de datos ODBC es asociar tablas a un Microsoft Jet (. Base de datos de Microsoft Access). Para obtener más información, vea el tema "Acceso a bases de datos externas con DAO" en la Ayuda de DAO.  
  
 Llame a la [GetRecordsAffected](#getrecordsaffected) función miembro del objeto de definición de consulta para determinar el número de registros afectados por la más reciente de **Execute** llamar. Por ejemplo, `GetRecordsAffected` devuelve información sobre el número de registros eliminados, actualizados o insertados cuando se ejecuta una consulta de acción. El recuento devuelto no se reflejará los cambios en las tablas relacionadas cuando en cascada actualiza o elimina entran en vigor.  
  
 Si incluye tanto **dbInconsistent** y **dbConsistent** o si incluye ninguna de ellas, el resultado es el valor predeterminado, **dbInconsistent**.  
  
 **Ejecutar** no devuelve un conjunto de registros. Usando **Execute** en una consulta que selecciona los registros hace MFC producir una excepción de tipo [CDaoException](../../mfc/reference/cdaoexception-class.md).  
  
##  <a name="a-namegetconnecta--cdaoquerydefgetconnect"></a><a name="getconnect"></a>CDaoQueryDef::GetConnect  
 Llame a esta función miembro para obtener la cadena de conexión asociada con el origen de datos de la definición de la consulta.  
  
```  
CString GetConnect();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un [CString](../../atl-mfc-shared/reference/cstringt-class.md) que contiene la cadena de conexión para la definición de consulta.  
  
### <a name="remarks"></a>Comentarios  
 Esta función sólo se utiliza con orígenes de datos ODBC y algunos controladores ISAM. No se utiliza con Microsoft Jet (. Bases de datos de Microsoft Access); en este caso, `GetConnect` devuelve una cadena vacía. Para obtener más información, consulte [SetConnect](#setconnect).  
  
> [!TIP]
>  Es la manera preferida de trabajar con tablas ODBC adjuntar a una. Base de datos de Microsoft Access. Para obtener más información, vea el tema "Acceso a bases de datos externas con DAO" en la Ayuda de DAO.  
  
 Para obtener información acerca de las cadenas de conexión, vea el tema "Propiedad conectarse" en la Ayuda de DAO.  
  
##  <a name="a-namegetdatecreateda--cdaoquerydefgetdatecreated"></a><a name="getdatecreated"></a>CDaoQueryDef::GetDateCreated  
 Llame a esta función miembro para obtener la fecha en que se creó el objeto de definición de consulta.  
  
```  
COleDateTime GetDateCreated();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objeto que contiene la fecha y hora de creación de la definición de consulta.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener información relacionada, vea el tema "DateCreated y LastUpdated propiedades" en la Ayuda de DAO.  
  
##  <a name="a-namegetdatelastupdateda--cdaoquerydefgetdatelastupdated"></a><a name="getdatelastupdated"></a>CDaoQueryDef::GetDateLastUpdated  
 Llamada a esta función miembro para obtener el objeto de definición de consulta de la fecha en que se actualizó por última vez, cuando cualquiera de sus propiedades se han cambiado, como su nombre, su cadena SQL o la cadena de conexión.  
  
```  
COleDateTime GetDateLastUpdated();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objeto que contiene la fecha y hora que se actualizó por última vez la definición de consulta.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener información relacionada, vea el tema "DateCreated y LastUpdated propiedades" en la Ayuda de DAO.  
  
##  <a name="a-namegetfieldcounta--cdaoquerydefgetfieldcount"></a><a name="getfieldcount"></a>CDaoQueryDef::GetFieldCount  
 Llame a esta función miembro para recuperar el número de campos de la consulta.  
  
```  
short GetFieldCount();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de campos definidos en la consulta.  
  
### <a name="remarks"></a>Comentarios  
 `GetFieldCount`es útil para recorrer en iteración todos los campos de la definición de consulta. Para ello, utilice `GetFieldCount` junto con [GetFieldInfo](#getfieldinfo).  
  
##  <a name="a-namegetfieldinfoa--cdaoquerydefgetfieldinfo"></a><a name="getfieldinfo"></a>CDaoQueryDef::GetFieldInfo  
 Llame a esta función miembro para obtener información acerca de un campo definido en la definición de consulta de diferentes tipos.  
  
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
 Índice de base cero del campo que desea en la colección de campos de la definición de la consulta, para la búsqueda por índice.  
  
 `fieldinfo`  
 Una referencia a un `CDaoFieldInfo` objeto que devuelve la información solicitada.  
  
 `dwInfoOptions`  
 Opciones que especifican qué información sobre el campo que desea recuperar. Las opciones disponibles se muestran aquí junto con lo que hacen que la función devuelva:  
  
- `AFX_DAO_PRIMARY_INFO`(Valor predeterminado) Nombre, tipo, tamaño, atributos  
  
- `AFX_DAO_SECONDARY_INFO`Además de información principal: posición Ordinal, necesaria, Permitir longitud cero, el campo de origen, nombre externa, tabla de origen, orden de intercalación  
  
- `AFX_DAO_ALL_INFO`Más información primaria y secundaria: regla de validación del valor predeterminado, el texto de validación,  
  
 `lpszName`  
 Una cadena que contiene el nombre del campo deseado, para la búsqueda por nombre. Puede usar un [CString](../../atl-mfc-shared/reference/cstringt-class.md).  
  
### <a name="remarks"></a>Comentarios  
 Para obtener una descripción de la información devuelta en `fieldinfo`, consulte el [CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md) estructura. Esta estructura no tiene miembros que corresponden a la información descriptiva en `dwInfoOptions` anteriormente. Si se solicita un nivel de información, obtendrá los niveles anteriores de información.  
  
##  <a name="a-namegetnamea--cdaoquerydefgetname"></a><a name="getname"></a>CDaoQueryDef::GetName  
 Llame a esta función miembro para recuperar el nombre de la consulta representada por la definición de consulta.  
  
```  
CString GetName();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Nombre de la consulta.  
  
### <a name="remarks"></a>Comentarios  
 Los nombres de definición de consulta son nombres únicos definidos por el usuario. Para obtener más información acerca de los nombres de definición de consulta, vea el tema "Nombre de propiedad" en la Ayuda de DAO.  
  
##  <a name="a-namegetodbctimeouta--cdaoquerydefgetodbctimeout"></a><a name="getodbctimeout"></a>CDaoQueryDef::GetODBCTimeout  
 Llame a esta función miembro para recuperar el límite de tiempo actual antes de que el tiempo de espera de una consulta a un origen de datos ODBC.  
  
```  
short GetODBCTimeout();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Número de segundos antes de que una consulta agote el tiempo de espera.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener información acerca de este límite de tiempo, vea el tema "Propiedad ODBCTimeout" en la Ayuda de DAO.  
  
> [!TIP]
>  Es la manera preferida de trabajar con tablas ODBC adjuntarlos a un Microsoft Jet (. Base de datos de Microsoft Access). Para obtener más información, vea el tema "Acceso a bases de datos externas con DAO" en la Ayuda de DAO.  
  
##  <a name="a-namegetparametercounta--cdaoquerydefgetparametercount"></a><a name="getparametercount"></a>CDaoQueryDef::GetParameterCount  
 Llame a esta función miembro para recuperar el número de parámetros de la consulta guardada.  
  
```  
short GetParameterCount();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de parámetros definidos en la consulta.  
  
### <a name="remarks"></a>Comentarios  
 `GetParameterCount`es útil para recorrer en iteración todos los parámetros en la definición de consulta. Para ello, utilice `GetParameterCount` junto con [GetParameterInfo](#getparameterinfo).  
  
 Para obtener información relacionada, vea los temas "Objeto de parámetro", "Parámetros de colección" y "declaración de parámetros (SQL)" en la Ayuda de DAO.  
  
##  <a name="a-namegetparameterinfoa--cdaoquerydefgetparameterinfo"></a><a name="getparameterinfo"></a>CDaoQueryDef::GetParameterInfo  
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
 Índice de base cero del parámetro en la colección de parámetros de la definición de la consulta, para la búsqueda por índice deseado.  
  
 `paraminfo`  
 Una referencia a un [CDaoParameterInfo](../../mfc/reference/cdaoparameterinfo-structure.md) objeto que devuelve la información solicitada.  
  
 `dwInfoOptions`  
 Opciones que especifican qué información sobre el parámetro para recuperar. La opción disponible aparece aquí junto con lo que hace que la función devuelva:  
  
- `AFX_DAO_PRIMARY_INFO`(Valor predeterminado) Nombre de tipo  
  
 `lpszName`  
 Una cadena que contiene el nombre del parámetro deseado, para la búsqueda por nombre. Puede usar un [CString](../../atl-mfc-shared/reference/cstringt-class.md).  
  
### <a name="remarks"></a>Comentarios  
 Para obtener una descripción de la información devuelta en `paraminfo`, consulte el [CDaoParameterInfo](../../mfc/reference/cdaoparameterinfo-structure.md) estructura. Esta estructura no tiene miembros que corresponden a la información descriptiva en `dwInfoOptions` anteriormente.  
  
 Para obtener información relacionada, vea el tema "declaración de parámetros (SQL)" en la Ayuda de DAO.  
  
##  <a name="a-namegetparamvaluea--cdaoquerydefgetparamvalue"></a><a name="getparamvalue"></a>CDaoQueryDef:: GetParamValue  
 Llame a esta función miembro para recuperar el valor actual del parámetro especificado que se almacenan en la colección de parámetros de la definición de la consulta.  
  
```  
virtual COleVariant GetParamValue(LPCTSTR lpszName);  
virtual COleVariant GetParamValue(int nIndex);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszName`  
 El nombre del parámetro cuyo valor desee para la búsqueda por nombre.  
  
 `nIndex`  
 Índice de base cero del parámetro en la colección de parámetros de la definición de la consulta, para la búsqueda por índice. Puede obtener este valor con llamadas a [GetParameterCount](#getparametercount) y [GetParameterInfo](#getparameterinfo).  
  
### <a name="return-value"></a>Valor devuelto  
 Un objeto de clase [COleVariant](../../mfc/reference/colevariant-class.md) que contiene el valor del parámetro.  
  
### <a name="remarks"></a>Comentarios  
 El parámetro puede tener acceso por nombre o por su posición ordinal en la colección.  
  
 Para obtener información relacionada, vea el tema "declaración de parámetros (SQL)" en la Ayuda de DAO.  
  
##  <a name="a-namegetrecordsaffecteda--cdaoquerydefgetrecordsaffected"></a><a name="getrecordsaffected"></a>CDaoQueryDef::GetRecordsAffected  
 Llame a esta función miembro para determinar el número de registros afectado por la última llamada de [Execute](#execute).  
  
```  
long GetRecordsAffected();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de registros afectados.  
  
### <a name="remarks"></a>Comentarios  
 El recuento devuelto no se reflejará los cambios en las tablas relacionadas cuando en cascada actualiza o elimina entran en vigor.  
  
 Para obtener información relacionada, vea el tema "Propiedad RecordsAffected" en la Ayuda de DAO.  
  
##  <a name="a-namegetreturnsrecordsa--cdaoquerydefgetreturnsrecords"></a><a name="getreturnsrecords"></a>CDaoQueryDef::GetReturnsRecords  
 Llame a esta función miembro para determinar si la definición de consulta se basa en una consulta que devuelve los registros.  
  
```  
BOOL GetReturnsRecords();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la definición de consulta se basa en una consulta que devuelve los registros; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro sólo se utiliza para las consultas de paso a través de SQL. Para obtener más información acerca de las consultas SQL, consulte la [Execute](#execute) función miembro. Para obtener más información acerca de cómo trabajar con consultas de paso a través de SQL, consulte la [la función SetReturnsRecords](#setreturnsrecords) función miembro.  
  
 Para obtener información relacionada, vea el tema "Propiedad ReturnsRecords" en la Ayuda de DAO.  
  
##  <a name="a-namegetsqla--cdaoquerydefgetsql"></a><a name="getsql"></a>CDaoQueryDef::GetSQL  
 Llame a esta función miembro para recuperar la instrucción SQL que define la consulta en la que se basa la definición de consulta.  
  
```  
CString GetSQL();
```  
  
### <a name="return-value"></a>Valor devuelto  
 La instrucción SQL que define la consulta en la que se basa la definición de consulta.  
  
### <a name="remarks"></a>Comentarios  
 A continuación, probablemente analizará la cadena de palabras clave, nombres de tabla y así sucesivamente.  
  
 Para obtener información relacionada, vea los temas "SQL Property", "Comparación de Microsoft Jet base de datos del motor y ANSI SQL" y "Consultar una base de datos con SQL en código" en la Ayuda de DAO.  
  
##  <a name="a-namegettypea--cdaoquerydefgettype"></a><a name="gettype"></a>CDaoQueryDef::GetType  
 Llame a esta función miembro para determinar el tipo de consulta de la definición de consulta.  
  
```  
short GetType();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El tipo de la consulta definida por la definición de consulta. Para los valores, vea la sección Comentarios.  
  
### <a name="remarks"></a>Comentarios  
 Se establece el tipo de consulta por lo que especifique en la cadena de la definición de la consulta SQL al crear la definición de consulta o llamar a una definición de consulta existente [SetSQL](#setsql) función miembro. El tipo de consulta devuelto por esta función puede ser uno de los siguientes valores:  
  
- **dbQSelect** seleccionar  
  
- **dbQAction** acción  
  
- **dbQCrosstab** general  
  
- **dbQDelete** eliminar  
  
- **dbQUpdate** actualización  
  
- **dbQAppend** anexar  
  
- **dbQMakeTable** creación de tabla  
  
- **dbQDDL** definición de datos  
  
- **dbQSQLPassThrough** acceso directo  
  
- **dbQSetOperation** Union  
  
- **dbQSPTBulk** utilizar con **dbQSQLPassThrough** para especificar una consulta que no devuelve ningún registro.  
  
> [!NOTE]
>  Para crear una consulta de paso a través de SQL, no establezca la **dbSQLPassThrough** constante. Esto se establece automáticamente el motor de base de datos Microsoft Jet cuando se crea un objeto de definición de consulta y establece la cadena de conexión.  
  
 Para obtener información acerca de las cadenas SQL, consulte [GetSQL](#getsql). Para obtener información acerca de los tipos de consulta, vea [Execute](#execute).  
  
##  <a name="a-nameisopena--cdaoquerydefisopen"></a><a name="isopen"></a>CDaoQueryDef::IsOpen  
 Llame a esta función miembro para determinar si la `CDaoQueryDef` objeto está abierto.  
  
```  
BOOL IsOpen() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si la `CDaoQueryDef` objeto está actualmente abierto; de lo contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Debe ser una definición de consulta en este estado antes de utilizarla para llamar a [Execute](#execute) o para crear un [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objeto. Para poner una definición de consulta en una llamada de estado abierto o [crear](#create) (para una nueva definición de consulta) o [abrir](#open) (para una definición de consulta existente).  
  
##  <a name="a-namempdatabasea--cdaoquerydefmpdatabase"></a><a name="m_pdatabase"></a>CDaoQueryDef::m_pDatabase  
 Contiene un puntero a la [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) objeto asociado con el objeto de definición de consulta.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este puntero si necesita tener acceso directamente a la base de datos, por ejemplo, para obtener punteros a otros querydef o el conjunto de registros de objetos en colecciones de la base de datos.  
  
##  <a name="a-namempdaoquerydefa--cdaoquerydefmpdaoquerydef"></a><a name="m_pdaoquerydef"></a>CDaoQueryDef::m_pDAOQueryDef  
 Contiene un puntero a la interfaz OLE para el objeto de definición de consulta DAO subyacente.  
  
### <a name="remarks"></a>Comentarios  
 Este puntero se proporciona integridad y coherencia con las otras clases. Sin embargo, porque MFC encapsula completamente en su lugar las definiciones de consulta DAO, es probable que la necesite. Si desea usarla, hacerlo con precaución, en particular, no cambie el valor del puntero a menos que sepa lo que está haciendo.  
  
##  <a name="a-nameopena--cdaoquerydefopen"></a><a name="open"></a>CDaoQueryDef::Open  
 Llame a esta función miembro para abrir una definición de consulta guardado previamente en la colección de definiciones de consulta de la base de datos.  
  
```  
virtual void Open(LPCTSTR lpszName = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszName`  
 Una cadena que contiene el nombre de la definición de consulta guardada para abrir. Puede usar un [CString](../../atl-mfc-shared/reference/cstringt-class.md).  
  
### <a name="remarks"></a>Comentarios  
 Una vez abierta la definición de consulta, puede llamar a su [Execute](#execute) función miembro o utilice la definición de consulta para crear una [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objeto.  
  
##  <a name="a-namesetconnecta--cdaoquerydefsetconnect"></a><a name="setconnect"></a>CDaoQueryDef::SetConnect  
 Llame a esta función miembro para establecer la cadena de conexión del objeto de definición de consulta.  
  
```  
void SetConnect(LPCTSTR lpszConnect);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszConnect`  
 Una cadena que contiene una cadena de conexión asociado [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) objeto.  
  
### <a name="remarks"></a>Comentarios  
 La cadena de conexión se utiliza para pasar información adicional a controladores ODBC y algunos controladores ISAM, según sea necesario. No se utiliza para Microsoft Jet (. Bases de datos de Microsoft Access).  
  
> [!TIP]
>  Es la manera preferida de trabajar con tablas ODBC adjuntar a una. Base de datos de Microsoft Access.  
  
 Antes de ejecutar una definición de consulta que representa una consulta de paso a través de SQL a un origen de datos ODBC, establezca la cadena de conexión con `SetConnect` y llame a [la función SetReturnsRecords](#setreturnsrecords) para especificar si la consulta devuelve registros.  
  
 Para obtener más información acerca de la estructura y los ejemplos de componentes de la cadena de conexión de la cadena de conexión, vea el tema "Propiedad conectarse" en la Ayuda de DAO.  
  
##  <a name="a-namesetnamea--cdaoquerydefsetname"></a><a name="setname"></a>CDaoQueryDef::SetName  
 Llame a esta función miembro si desea cambiar el nombre de una definición de consulta no es temporal.  
  
```  
void SetName(LPCTSTR lpszName);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszName`  
 Una cadena que contiene el nuevo nombre para una consulta en el asociado producen [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) objeto.  
  
### <a name="remarks"></a>Comentarios  
 Los nombres de definición de consulta son nombres únicos y definidos por el usuario. Puede llamar a `SetName` antes de la definición de consulta el objeto se anexa a la colección de definiciones de consulta.  
  
##  <a name="a-namesetodbctimeouta--cdaoquerydefsetodbctimeout"></a><a name="setodbctimeout"></a>CDaoQueryDef::SetODBCTimeout  
 Llame a esta función miembro para establecer el límite de tiempo antes de que agota el tiempo de espera de una consulta a un origen de datos ODBC.  
  
```  
void SetODBCTimeout(short nODBCTimeout);
```  
  
### <a name="parameters"></a>Parámetros  
 *nODBCTimeout*  
 Número de segundos antes de que una consulta agote el tiempo de espera.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro le permite reemplazar el número predeterminado de segundos antes de que las operaciones subsiguientes en el origen de datos conectado "tiempo de espera". Una operación podría el tiempo de espera debido a problemas de acceso de red y el tiempo de procesamiento excesivo de consultas. Llame a `SetODBCTimeout` antes de ejecutar una consulta con esta definición de consulta si desea cambiar el valor de tiempo de espera de consulta. (Como ODBC reutiliza las conexiones, el valor de tiempo de espera es el mismo para todos los clientes en la misma conexión.)  
  
 El valor predeterminado para los tiempos de espera de consulta es 60 segundos.  
  
##  <a name="a-namesetparamvaluea--cdaoquerydefsetparamvalue"></a><a name="setparamvalue"></a>CDaoQueryDef:: SetParamValue  
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
 El nombre del parámetro cuyo valor va a establecer.  
  
 `varValue`  
 El valor que se va a establecer; vea la sección Comentarios.  
  
 `nIndex`  
 La posición ordinal del parámetro en la colección de parámetros de la definición de la consulta. Puede obtener este valor con llamadas a [GetParameterCount](#getparametercount) y [GetParameterInfo](#getparameterinfo).  
  
### <a name="remarks"></a>Comentarios  
 El parámetro ya se debe haber establecido como parte de la cadena de la definición de la consulta SQL. El parámetro puede tener acceso por nombre o por su posición ordinal en la colección.  
  
 Especifique el valor que se establecerá como un `COleVariant` objeto. Para obtener información acerca de cómo establecer el valor deseado y el tipo en su `COleVariant` de objetos, vea la clase [COleVariant](../../mfc/reference/colevariant-class.md).  
  
##  <a name="a-namesetreturnsrecordsa--cdaoquerydefsetreturnsrecords"></a><a name="setreturnsrecords"></a>CDaoQueryDef::SetReturnsRecords  
 Llame a esta función miembro como parte del proceso de configuración de una consulta de paso a través de SQL a una base de datos externo.  
  
```  
void SetReturnsRecords(BOOL bReturnsRecords);
```  
  
### <a name="parameters"></a>Parámetros  
 *bReturnsRecords*  
 Pasar **TRUE** si la consulta en una base de datos externa devuelve registros; en caso contrario, **FALSE**.  
  
### <a name="remarks"></a>Comentarios  
 En tal caso, debe crear la definición de consulta y establezca sus propiedades mediante otros `CDaoQueryDef` funciones miembro. Para obtener una descripción de las bases de datos externas, consulte [SetConnect](#setconnect).  
  
##  <a name="a-namesetsqla--cdaoquerydefsetsql"></a><a name="setsql"></a>CDaoQueryDef::SetSQL  
 Llame a esta función miembro para establecer la instrucción SQL que ejecuta la definición de consulta.  
  
```  
void SetSQL(LPCTSTR lpszSQL);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszSQL`  
 Una cadena que contiene una instrucción SQL completa, adecuada para la ejecución. La sintaxis de esta cadena depende del DBMS que el destino de la consulta. Para obtener una explicación de la sintaxis utilizada en el motor de base de datos Microsoft Jet, vea el tema "Crear instrucciones en código SQL" en la Ayuda de DAO.  
  
### <a name="remarks"></a>Comentarios  
 Un uso típico de `SetSQL` es configurar un objeto de definición de consulta para su uso en una consulta de paso a través de SQL. (Para la sintaxis de consultas de paso a través de SQL en el DBMS de destino, consulte la documentación del DBMS).  
  
## <a name="see-also"></a>Vea también  
 [CObject (clase)](../../mfc/reference/cobject-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [CDaoRecordset (clase)](../../mfc/reference/cdaorecordset-class.md)   
 [CDaoDatabase (clase)](../../mfc/reference/cdaodatabase-class.md)   
 [Clase CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)   
 [Clase CDaoException](../../mfc/reference/cdaoexception-class.md)

