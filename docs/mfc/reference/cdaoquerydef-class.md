---
title: CDaoQueryDef (clase)
ms.date: 11/04/2016
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
ms.openlocfilehash: 08fb2909a4fd2e5bda3dfc63d19224a515c7c699
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78883894"
---
# <a name="cdaoquerydef-class"></a>CDaoQueryDef (clase)

Representa una definición de consulta o "querydef", normalmente guardada en una base de datos.

## <a name="syntax"></a>Sintaxis

```
class CDaoQueryDef : public CObject
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CDaoQueryDef:: CDaoQueryDef](#cdaoquerydef)|Construye un objeto `CDaoQueryDef`. A continuación, llame a `Open` o `Create`, en función de sus necesidades.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CDaoQueryDef:: Append](#append)|Anexa el QueryDef a la colección QueryDefs de la base de datos como una consulta guardada.|
|[CDaoQueryDef:: CanUpdate](#canupdate)|Devuelve un valor distinto de cero si la consulta puede actualizar la base de datos.|
|[CDaoQueryDef:: Close](#close)|Cierra el objeto QueryDef. Destruya el C++ objeto cuando termine de usarlo.|
|[CDaoQueryDef:: Create](#create)|Crea el objeto DAO QueryDef subyacente. Use el QueryDef como una consulta temporal o llame a `Append` para guardarlo en la base de datos.|
|[CDaoQueryDef:: Execute](#execute)|Ejecuta la consulta definida por el objeto QueryDef.|
|[CDaoQueryDef:: GetConnect](#getconnect)|Devuelve la cadena de conexión asociada a la definición de tipo. La cadena de conexión identifica el origen de datos. (Solo para las consultas de paso a través de SQL; de lo contrario, una cadena vacía).|
|[CDaoQueryDef:: GetDateCreated](#getdatecreated)|Devuelve la fecha en que se creó la consulta guardada.|
|[CDaoQueryDef:: GetDateLastUpdated](#getdatelastupdated)|Devuelve la fecha en que se actualizó por última vez la consulta guardada.|
|[CDaoQueryDef:: GetFieldCount](#getfieldcount)|Devuelve el número de campos definido por la definición de código.|
|[CDaoQueryDef:: GetFieldInfo](#getfieldinfo)|Devuelve información sobre un campo especificado definido en la consulta.|
|[CDaoQueryDef:: GetName](#getname)|Devuelve el nombre de la definición de la definición.|
|[CDaoQueryDef:: GetODBCTimeout](#getodbctimeout)|Devuelve el valor de tiempo de espera utilizado por ODBC (para una consulta ODBC) cuando se ejecuta la definición de consulta. Esto determina cuánto tiempo se permite que se complete la acción de la consulta.|
|[CDaoQueryDef:: GetParameterCount](#getparametercount)|Devuelve el número de parámetros definidos para la consulta.|
|[CDaoQueryDef:: GetParameterInfo](#getparameterinfo)|Devuelve información sobre un parámetro especificado a la consulta.|
|[CDaoQueryDef:: GetParamValue](#getparamvalue)|Devuelve el valor de un parámetro especificado a la consulta.|
|[CDaoQueryDef:: GetRecordsAffected](#getrecordsaffected)|Devuelve el número de registros afectados por una consulta de acción.|
|[CDaoQueryDef:: GetReturnsRecords](#getreturnsrecords)|Devuelve un valor distinto de cero si la consulta definida por QueryDef devuelve registros.|
|[CDaoQueryDef:: GetSQL](#getsql)|Devuelve la cadena de SQL que especifica la consulta definida por la definición de tipo.|
|[CDaoQueryDef:: GetType](#gettype)|Devuelve el tipo de consulta: Delete, Update, append, make-Table, etc.|
|[CDaoQueryDef:: IsOpen](#isopen)|Devuelve un valor distinto de cero si QueryDef está abierto y se puede ejecutar.|
|[CDaoQueryDef:: Open](#open)|Abre un QueryDef existente almacenado en la colección QueryDefs de la base de datos.|
|[CDaoQueryDef:: SetConnect](#setconnect)|Establece la cadena de conexión para una consulta de paso a través de SQL en un origen de datos ODBC.|
|[CDaoQueryDef:: SetName](#setname)|Establece el nombre de la consulta guardada, reemplazando el nombre que se utiliza cuando se creó la definición de consulta.|
|[CDaoQueryDef:: SetODBCTimeout](#setodbctimeout)|Establece el valor de tiempo de espera utilizado por ODBC (para una consulta ODBC) cuando se ejecuta la definición de consulta.|
|[CDaoQueryDef:: SetParamValue](#setparamvalue)|Establece el valor de un parámetro especificado en la consulta.|
|[CDaoQueryDef:: SetReturnsRecords](#setreturnsrecords)|Especifica si QueryDef devuelve registros. Establecer este atributo en TRUE solo es válido para las consultas de paso a través de SQL.|
|[CDaoQueryDef:: SetSQL](#setsql)|Establece la cadena de SQL que especifica la consulta definida por la definición de tipo.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CDaoQueryDef:: m_pDAOQueryDef](#m_pdaoquerydef)|Puntero a la interfaz OLE para el objeto DAO QueryDef subyacente.|
|[CDaoQueryDef:: m_pDatabase](#m_pdatabase)|Puntero al objeto de `CDaoDatabase` con el que está asociada la definición de objetos. Es posible que la definición de la base de datos se guarde en la base de datos o no.|

## <a name="remarks"></a>Observaciones

Una definición de tipo es un objeto de acceso a datos que contiene la instrucción SQL que describe una consulta y sus propiedades, como "fecha de creación" y "tiempo de espera de ODBC". También puede crear objetos de definición de usuario temporales sin guardarlos, pero es conveniente, y mucho más eficaz, para guardar las consultas que se reutilizan con frecuencia en una base de datos. Un objeto [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) mantiene una colección, denominada colección QueryDefs, que contiene las definiciones de conjunto guardadas.

> [!NOTE]
>  Las clases de base de datos DAO son distintas de las clases de base de datos MFC basadas en Conectividad abierta de bases de datos (ODBC). Todos los nombres de clase de base de datos DAO tienen el prefijo "CDao". Todavía puede obtener acceso a los orígenes de datos ODBC con las clases DAO. En general, las clases MFC basadas en DAO son más capaces que las clases MFC basadas en ODBC. las clases basadas en DAO pueden tener acceso a los datos, incluidos los controladores ODBC, a través de su propio motor de base de datos. Las clases basadas en DAO también admiten operaciones de lenguaje de definición de datos (DDL), como agregar tablas a través de las clases, sin tener que llamar a DAO directamente.

## <a name="usage"></a>Uso

Utilice los objetos QueryDef para trabajar con una consulta guardada existente o para crear una consulta guardada o una consulta temporal:

1. En todos los casos, primero construya un objeto `CDaoQueryDef`, proporcionando un puntero al objeto [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) al que pertenece la consulta.

1. A continuación, haga lo siguiente, en función de lo que desee:

   - Para utilizar una consulta guardada existente, llame a la función miembro [Open](#open) del objeto QueryDef y proporcione el nombre de la consulta guardada.

   - Para crear una nueva consulta guardada, llame a la función miembro [Create](#create) del objeto QueryDef y proporcione el nombre de la consulta. A continuación, llame a [Append](#append) para guardar la consulta anexando a la colección QueryDefs de la base de datos. `Create` coloca la definición de usuario en un estado abierto, por lo que después de llamar a `Create` no se llama a `Open`.

   - Para crear una definición de método temporal, llame a `Create`. Pase una cadena vacía para el nombre de la consulta. No llame a `Append`.

Cuando termine de usar un objeto QueryDef, llame a la función miembro [Close](#close) ; a continuación, destruya el objeto QueryDef.

> [!TIP]
>  La forma más fácil de crear consultas guardadas es crearlas y almacenarlas en la base de datos mediante Microsoft Access. Después, puede abrirlos y usarlos en el código MFC.

## <a name="purposes"></a>Fiere

Puede usar un objeto QueryDef para cualquiera de los siguientes propósitos:

- Para crear un objeto `CDaoRecordset`

- Para llamar a la función miembro `Execute` del objeto para ejecutar directamente una consulta de acción o una consulta de paso a través de SQL

Puede usar un objeto QueryDef para cualquier tipo de consulta, como SELECT, Action, crosstab, Delete, Update, append, make-Table, Data Definition, paso a través de SQL, Unión y consultas masivas. El tipo de la consulta viene determinado por el contenido de la instrucción SQL que proporcione. Para obtener información sobre los tipos de consulta, vea las funciones miembro `Execute` y [GetType](#gettype) . Los conjuntos de registros se utilizan normalmente para las consultas que devuelven filas, normalmente las que usan la  **DE** palabras clave. `Execute` se usa normalmente para operaciones masivas. Para obtener más información, vea [Execute](#execute) y [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md).

## <a name="querydefs-and-recordsets"></a>Definiciones de conjunto y conjuntos de registros

Para usar un objeto QueryDef con el fin de crear un objeto `CDaoRecordset`, normalmente se crea o se abre una definición de usuario, como se ha descrito anteriormente. A continuación, construya un objeto de conjunto de registros, pasando un puntero al objeto QueryDef cuando llame a [CDaoRecordset:: Open](../../mfc/reference/cdaorecordset-class.md#open). La definición de acceso que se pasa debe estar en un estado abierto. Para obtener más información, vea la clase [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md).

No se puede usar una definición de usuario para crear un conjunto de registros (el uso más común de una definición de usuario) a menos que esté en un estado abierto. Coloque la definición de tipo en un estado abierto llamando a `Open` o `Create`.

## <a name="external-databases"></a>Bases de datos externas

Los objetos QueryDef son la manera preferida de usar el dialecto SQL nativo de un motor de base de datos externo. Por ejemplo, puede crear una consulta de Transact-SQL (como se usa en Microsoft SQL Server) y almacenarla en un objeto QueryDef. Cuando necesite usar una consulta SQL que no esté basada en el motor de base de datos de Microsoft Jet, debe proporcionar una cadena de conexión que señale al origen de datos externo. Las consultas con cadenas de conexión válidas omiten el motor de base de datos y pasan la consulta directamente al servidor de bases de datos externo para su procesamiento.

> [!TIP]
>  La mejor manera de trabajar con tablas ODBC es asociarlas a Microsoft Jet (. MDB).

Para obtener información relacionada, vea los temas "QueryDef Object", "QueryDefs Collection" y "CdbDatabase Object" en el SDK de DAO.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

`CDaoQueryDef`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdao. h

##  <a name="append"></a>CDaoQueryDef:: Append

Llame a esta función miembro después de llamar a [Create](#create) para crear un nuevo objeto QueryDef.

```
virtual void Append();
```

### <a name="remarks"></a>Observaciones

`Append` guarda el objeto QueryDef en la base de datos anexando el objeto a la colección QueryDefs de la base de datos. Puede usar la definición de usuario como un objeto temporal sin anexarlo, pero si desea que persista, debe llamar a `Append`.

Si intenta anexar un objeto de definición de tipos temporal, MFC produce una excepción de tipo [CDaoException](../../mfc/reference/cdaoexception-class.md).

##  <a name="canupdate"></a>CDaoQueryDef:: CanUpdate

Llame a esta función miembro para determinar si se puede modificar la definición de tipo, por ejemplo, si se cambia el nombre o la cadena SQL.

```
BOOL CanUpdate();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se permite modificar la definición de usuario; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

Puede modificar la definición de usuario si:

- No se basa en una base de datos que está abierta en modo de solo lectura.

- Tiene permisos de actualización para la base de datos.

   Esto depende de si ha implementado características de seguridad. MFC no proporciona compatibilidad con la seguridad; debe implementarla usted mismo llamando a DAO directamente o mediante Microsoft Access. Vea el tema "propiedad Permissions" en la ayuda de DAO.

##  <a name="cdaoquerydef"></a>CDaoQueryDef:: CDaoQueryDef

Construye un objeto `CDaoQueryDef`.

```
CDaoQueryDef(CDaoDatabase* pDatabase);
```

### <a name="parameters"></a>Parámetros

*pDatabase*<br/>
Un puntero a un objeto [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) abierto.

### <a name="remarks"></a>Observaciones

El objeto puede representar un objeto QueryDef existente almacenado en la colección QueryDefs de la base de datos, una nueva consulta que se va a almacenar en la colección o una consulta temporal, y que no se debe almacenar. El siguiente paso depende del tipo de definición de tipos:

- Si el objeto representa una definición de usuario existente, llame a la función miembro [abierta](#open) del objeto para inicializarla.

- Si el objeto representa una nueva definición de usuario que se va a guardar, llame a la función miembro [Create](#create) del objeto. Esto agrega el objeto a la colección QueryDefs de la base de datos. A continuación, llame a `CDaoQueryDef` funciones miembro para establecer los atributos del objeto. Por último, llame a [Append](#append).

- Si el objeto representa una definición de tipo temporal (no se debe guardar en la base de datos), llame a `Create`, pasando una cadena vacía para el nombre de la consulta. Después de llamar a `Create`, inicialice el QueryDef estableciendo directamente sus atributos. No llame a `Append`.

Para establecer los atributos de la definición de usuario, puede usar las funciones miembro [setName](#setname), [SetSQL](#setsql), [SetConnect](#setconnect), [SetODBCTimeout](#setodbctimeout)y [SetReturnsRecords](#setreturnsrecords) .

Cuando termine con el objeto QueryDef, llame a la función miembro [Close](#close) . Si tiene un puntero a la definición de usuario, use el operador **Delete** para destruir C++ el objeto.

##  <a name="close"></a>CDaoQueryDef:: Close

Llame a esta función miembro cuando termine de utilizar el objeto QueryDef.

```
virtual void Close();
```

### <a name="remarks"></a>Observaciones

Al cerrar la QueryDef, se libera el objeto DAO subyacente, pero no se destruye el objeto DAO C++ QueryDef guardado ni el objeto `CDaoQueryDef`. Esto no es lo mismo que [CDaoDatabase::D eletequerydef](../../mfc/reference/cdaodatabase-class.md#deletequerydef), que elimina la QueryDef de la colección QueryDefs de la base de datos en Dao (si no es una definición de biblioteca temporal).

##  <a name="create"></a>CDaoQueryDef:: Create

Llame a esta función miembro para crear una nueva consulta guardada o una nueva consulta temporal.

```
virtual void Create(
    LPCTSTR lpszName = NULL,
    LPCTSTR lpszSQL = NULL);
```

### <a name="parameters"></a>Parámetros

*lpszName*<br/>
Nombre único de la consulta guardada en la base de datos. Para obtener más información acerca de la cadena, vea el tema "método CreateQueryDef" en la ayuda de DAO. Si acepta el valor predeterminado, una cadena vacía, se crea una definición de tipo temporal. Este tipo de consulta no se guarda en la colección QueryDefs.

*lpszSQL*<br/>
Cadena de SQL que define la consulta. Si acepta el valor predeterminado de NULL, debe llamar a [SetSQL](#setsql) más adelante para establecer la cadena. Hasta entonces, la consulta no está definida. Sin embargo, puede utilizar la consulta no definida para abrir un conjunto de registros; Vea la sección Comentarios para obtener más información. La instrucción SQL debe definirse antes de poder anexar la definición de usuario a la colección QueryDefs.

### <a name="remarks"></a>Observaciones

Si pasa un nombre en *lpszName*, puede llamar a [Append](#append) para guardar la definición de acceso en la colección QueryDefs de la base de datos. De lo contrario, el objeto es una definición de tipo temporal y no se guarda. En cualquier caso, la definición de tipo está en un estado abierto y se puede usar para crear un objeto [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) o para llamar a la función miembro [Execute](#execute) de la definición de tipo.

Si no proporciona una instrucción SQL en *lpszSQL*, no puede ejecutar la consulta con `Execute` pero puede utilizarla para crear un conjunto de registros. En ese caso, MFC utiliza la instrucción SQL predeterminada del conjunto de registros.

##  <a name="execute"></a>CDaoQueryDef:: Execute

Llame a esta función miembro para ejecutar la consulta definida por el objeto QueryDef.

```
virtual void Execute(int nOptions = dbFailOnError);
```

### <a name="parameters"></a>Parámetros

*nOptions*<br/>
Entero que determina las características de la consulta. Para obtener información relacionada, vea el tema sobre el método Execute en la ayuda de DAO. Puede usar el operador OR bit a bit ( **&#124;** ) para combinar las constantes siguientes para este argumento:

- `dbDenyWrite` denegar el permiso de escritura a otros usuarios.

- `dbInconsistent` actualizaciones incoherentes.

- `dbConsistent` actualizaciones coherentes.

- `dbSQLPassThrough` paso a través de SQL. Hace que la instrucción SQL se pase a una base de datos ODBC para su procesamiento.

- `dbFailOnError` valor predeterminado. Revertir las actualizaciones si se produce un error y notificar el error al usuario.

- `dbSeeChanges` generar un error en tiempo de ejecución si otro usuario está cambiando los datos que está editando.

> [!NOTE]
>  Para obtener una explicación de los términos "incoherentes" y "coherentes", vea el tema "ejecutar método" en la ayuda de DAO.

### <a name="remarks"></a>Observaciones

Los objetos QueryDef usados para la ejecución de esta manera solo pueden representar uno de los siguientes tipos de consulta:

- Consultas de acción

- Consultas de paso a través de SQL

`Execute` no funciona para las consultas que devuelven registros, como consultas Select. `Execute` se usa normalmente para las consultas de operaciones masivas, como **Update**, **Insert**o **SELECT INTO**, o para operaciones de lenguaje de definición de datos (DDL).

> [!TIP]
>  La mejor manera de trabajar con orígenes de datos ODBC es adjuntar tablas a Microsoft Jet (. MDB). Para obtener más información, vea el tema "obtener acceso a bases de datos externas con DAO" en la ayuda de DAO.

Llame a la función miembro [GetRecordsAffected](#getrecordsaffected) del objeto QueryDef para determinar el número de registros afectados por la llamada a `Execute` más reciente. Por ejemplo, `GetRecordsAffected` devuelve información sobre el número de registros eliminados, actualizados o insertados al ejecutar una consulta de acción. El recuento devuelto no reflejará los cambios en las tablas relacionadas cuando las actualizaciones o eliminaciones en cascada estén en vigor.

Si incluye `dbInconsistent` y `dbConsistent` o si no incluye ninguno, el resultado es el valor predeterminado, `dbInconsistent`.

`Execute` no devuelve un conjunto de registros. El uso de `Execute` en una consulta que selecciona registros hace que MFC produzca una excepción de tipo [CDaoException](../../mfc/reference/cdaoexception-class.md).

##  <a name="getconnect"></a>CDaoQueryDef:: GetConnect

Llame a esta función miembro para obtener la cadena de conexión asociada al origen de datos de la definición de acceso.

```
CString GetConnect();
```

### <a name="return-value"></a>Valor devuelto

Objeto [CString](../../atl-mfc-shared/reference/cstringt-class.md) que contiene la cadena de conexión para la definición de tipo.

### <a name="remarks"></a>Observaciones

Esta función solo se utiliza con orígenes de datos ODBC y ciertos controladores ISAM. No se utiliza con Microsoft Jet (. MDB); en este caso, `GetConnect` devuelve una cadena vacía. Para obtener más información, vea [SetConnect](#setconnect).

> [!TIP]
>  La mejor manera de trabajar con tablas ODBC es asociarlas a un. Base de datos MDB. Para obtener más información, vea el tema "obtener acceso a bases de datos externas con DAO" en la ayuda de DAO.

Para obtener información acerca de las cadenas de conexión, vea el tema "propiedad de conexión" en la ayuda de DAO.

##  <a name="getdatecreated"></a>CDaoQueryDef:: GetDateCreated

Llame a esta función miembro para obtener la fecha en que se creó el objeto QueryDef.

```
COleDateTime GetDateCreated();
```

### <a name="return-value"></a>Valor devuelto

Objeto [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) que contiene la fecha y hora en que se creó la definición de tipo.

### <a name="remarks"></a>Observaciones

Para obtener información relacionada, vea el tema "DateCreated, propiedades de LastUpdated" en la ayuda de DAO.

##  <a name="getdatelastupdated"></a>CDaoQueryDef:: GetDateLastUpdated

Llame a esta función miembro para obtener la fecha en que se actualizó por última vez el objeto QueryDef, cuando se cambió alguna de sus propiedades, como su nombre, su cadena SQL o su cadena de conexión.

```
COleDateTime GetDateLastUpdated();
```

### <a name="return-value"></a>Valor devuelto

Objeto [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) que contiene la fecha y la hora en que se actualizó por última vez la definición de tipo.

### <a name="remarks"></a>Observaciones

Para obtener información relacionada, vea el tema "DateCreated, propiedades de LastUpdated" en la ayuda de DAO.

##  <a name="getfieldcount"></a>CDaoQueryDef:: GetFieldCount

Llame a esta función miembro para recuperar el número de campos de la consulta.

```
short GetFieldCount();
```

### <a name="return-value"></a>Valor devuelto

El número de campos definidos en la consulta.

### <a name="remarks"></a>Observaciones

`GetFieldCount` es útil para recorrer todos los campos de la definición de acceso. Para ello, use `GetFieldCount` junto con [GetFieldInfo](#getfieldinfo).

##  <a name="getfieldinfo"></a>CDaoQueryDef:: GetFieldInfo

Llame a esta función miembro para obtener varios tipos de información sobre un campo definido en la definición de tipo.

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
Índice de base cero del campo deseado en la colección de campos de la definición de consulta, para la búsqueda por índice.

*FieldInfo*<br/>
Referencia a un objeto `CDaoFieldInfo` que devuelve la información solicitada.

*dwInfoOptions*<br/>
Opciones que especifican la información sobre el campo que se va a recuperar. Aquí se enumeran las opciones disponibles junto con lo que hacen que la función devuelva:

- AFX_DAO_PRIMARY_INFO (valor predeterminado) Name, Type, size, Attributes

- AFX_DAO_SECONDARY_INFO información principal más: posición ordinal, requerida, Permitir longitud cero, campo de origen, nombre externo, tabla de origen, orden de intercalación

- AFX_DAO_ALL_INFO información principal y secundaria más: valor predeterminado, texto de validación, regla de validación

*lpszName*<br/>
Cadena que contiene el nombre del campo deseado, para la búsqueda por nombre. Puede usar un [CString](../../atl-mfc-shared/reference/cstringt-class.md).

### <a name="remarks"></a>Observaciones

Para obtener una descripción de la información que se devuelve en *FieldInfo*, vea la estructura [cdaofieldinfo (](../../mfc/reference/cdaofieldinfo-structure.md) . Esta estructura tiene miembros que corresponden a la información descriptiva en *dwInfoOptions* anterior. Si solicita un nivel de información, también obtendrá cualquier nivel de información anterior.

##  <a name="getname"></a>CDaoQueryDef:: GetName

Llame a esta función miembro para recuperar el nombre de la consulta representada por la definición de usuario.

```
CString GetName();
```

### <a name="return-value"></a>Valor devuelto

Nombre de la consulta.

### <a name="remarks"></a>Observaciones

Los nombres de QueryDef son nombres únicos definidos por el usuario. Para obtener más información sobre los nombres de QueryDef, vea el tema "propiedad Name" en la ayuda de DAO.

##  <a name="getodbctimeout"></a>CDaoQueryDef:: GetODBCTimeout

Llame a esta función miembro para recuperar el límite de tiempo actual antes de que se agote el tiempo de espera de una consulta a un origen de datos ODBC.

```
short GetODBCTimeout();
```

### <a name="return-value"></a>Valor devuelto

El número de segundos antes de que una consulta exceda el tiempo de espera.

### <a name="remarks"></a>Observaciones

Para obtener información acerca de este límite de tiempo, vea el tema "propiedad ODBCTimeout" en la ayuda de DAO.

> [!TIP]
>  La mejor manera de trabajar con tablas ODBC es asociarlas a Microsoft Jet (. MDB). Para obtener más información, vea el tema "obtener acceso a bases de datos externas con DAO" en la ayuda de DAO.

##  <a name="getparametercount"></a>CDaoQueryDef:: GetParameterCount

Llame a esta función miembro para recuperar el número de parámetros de la consulta guardada.

```
short GetParameterCount();
```

### <a name="return-value"></a>Valor devuelto

El número de parámetros definidos en la consulta.

### <a name="remarks"></a>Observaciones

`GetParameterCount` es útil para recorrer todos los parámetros de la definición de acceso. Para ello, use `GetParameterCount` junto con [GetParameterInfo](#getparameterinfo).

Para obtener información relacionada, vea los temas "objeto de parámetro", "colección de parámetros" y "Declaración de parámetros (SQL)" en la ayuda de DAO.

##  <a name="getparameterinfo"></a>CDaoQueryDef:: GetParameterInfo

Llame a esta función miembro para obtener información sobre un parámetro definido en la definición de datos.

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

*nIndex*<br/>
Índice de base cero del parámetro deseado en la colección de parámetros de la definición de la consulta, para la búsqueda por índice.

*paraminfo*<br/>
Referencia a un objeto [cdaoparameterinfo (](../../mfc/reference/cdaoparameterinfo-structure.md) que devuelve la información solicitada.

*dwInfoOptions*<br/>
Opciones que especifican la información sobre el parámetro que se va a recuperar. La opción disponible se muestra aquí junto con lo que hace que la función devuelva:

- AFX_DAO_PRIMARY_INFO (valor predeterminado), escriba

*lpszName*<br/>
Cadena que contiene el nombre del parámetro deseado, para la búsqueda por nombre. Puede usar un [CString](../../atl-mfc-shared/reference/cstringt-class.md).

### <a name="remarks"></a>Observaciones

Para obtener una descripción de la información que se devuelve en *paraminfo*, consulte la estructura [cdaoparameterinfo (](../../mfc/reference/cdaoparameterinfo-structure.md) . Esta estructura tiene miembros que corresponden a la información descriptiva en *dwInfoOptions* anterior.

Para obtener información relacionada, vea el tema "Parameters declaration (SQL)" en la ayuda de DAO.

##  <a name="getparamvalue"></a>CDaoQueryDef:: GetParamValue

Llame a esta función miembro para recuperar el valor actual del parámetro especificado almacenado en la colección de parámetros de la definición de la definición.

```
virtual COleVariant GetParamValue(LPCTSTR lpszName);
virtual COleVariant GetParamValue(int nIndex);
```

### <a name="parameters"></a>Parámetros

*lpszName*<br/>
Nombre del parámetro cuyo valor se desea, para la búsqueda por nombre.

*nIndex*<br/>
Índice de base cero del parámetro en la colección de parámetros de la definición de la consulta, para la búsqueda por índice. Puede obtener este valor con llamadas a [GetParameterCount](#getparametercount) y [GetParameterInfo](#getparameterinfo).

### <a name="return-value"></a>Valor devuelto

Objeto de la clase [COleVariant](../../mfc/reference/colevariant-class.md) que contiene el valor del parámetro.

### <a name="remarks"></a>Observaciones

Puede tener acceso al parámetro por el nombre o por su posición ordinal en la colección.

Para obtener información relacionada, vea el tema "Parameters declaration (SQL)" en la ayuda de DAO.

##  <a name="getrecordsaffected"></a>CDaoQueryDef:: GetRecordsAffected

Llame a esta función miembro para determinar el número de registros afectados por la última llamada de [Execute](#execute).

```
long GetRecordsAffected();
```

### <a name="return-value"></a>Valor devuelto

El número de registros afectados.

### <a name="remarks"></a>Observaciones

El recuento devuelto no reflejará los cambios en las tablas relacionadas cuando las actualizaciones o eliminaciones en cascada estén en vigor.

Para obtener información relacionada, vea el tema "propiedad RecordsAffected" en la ayuda de DAO.

##  <a name="getreturnsrecords"></a>CDaoQueryDef:: GetReturnsRecords

Llame a esta función miembro para determinar si la definición de usuario se basa en una consulta que devuelve registros.

```
BOOL GetReturnsRecords();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si QueryDef se basa en una consulta que devuelve registros; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

Esta función miembro solo se utiliza para las consultas de paso a través de SQL. Para obtener más información sobre las consultas SQL, vea la función miembro [Execute](#execute) . Para obtener más información sobre cómo trabajar con consultas de paso a través de SQL, vea la función miembro [SetReturnsRecords](#setreturnsrecords) .

Para obtener información relacionada, vea el tema "propiedad ReturnsRecords" en la ayuda de DAO.

##  <a name="getsql"></a>CDaoQueryDef:: GetSQL

Llame a esta función miembro para recuperar la instrucción SQL que define la consulta en la que se basa la definición de usuario.

```
CString GetSQL();
```

### <a name="return-value"></a>Valor devuelto

Instrucción SQL que define la consulta en la que se basa la definición de consulta.

### <a name="remarks"></a>Observaciones

Probablemente analizará la cadena para palabras clave, nombres de tabla, etc.

Para obtener información relacionada, vea los temas "propiedad SQL", "comparación de Microsoft Jet Motor de base de datos SQL y ANSI SQL" y "consultar una base de datos con SQL en el código" en la ayuda de DAO.

##  <a name="gettype"></a>CDaoQueryDef:: GetType

Llame a esta función miembro para determinar el tipo de consulta de la definición de tipo.

```
short GetType();
```

### <a name="return-value"></a>Valor devuelto

Tipo de la consulta definida por la definición de tipo. Para ver los valores, vea la sección Comentarios.

### <a name="remarks"></a>Observaciones

El tipo de consulta lo establece lo que se especifica en la cadena de SQL de la definición de tipos al crear la definición de tipo o llamar a una función miembro [SetSQL](#setsql) de una QueryDef existente. El tipo de consulta devuelto por esta función puede ser uno de los valores siguientes:

- `dbQSelect` seleccionar

- Acción de `dbQAction`

- `dbQCrosstab` general

- `dbQDelete` eliminar

- `dbQUpdate` Update

- `dbQAppend` anexar

- `dbQMakeTable` make-Table

- `dbQDDL` de definición de datos

- `dbQSQLPassThrough` paso a través

- Unión `dbQSetOperation`

- `dbQSPTBulk` usa con `dbQSQLPassThrough` para especificar una consulta que no devuelve registros.

> [!NOTE]
>  Para crear una consulta de paso a través de SQL, no establezca la constante `dbSQLPassThrough`. El motor de base de datos de Microsoft Jet lo establece automáticamente cuando se crea un objeto QueryDef y se establece la cadena de conexión.

Para obtener información sobre las cadenas SQL, vea [GetSQL](#getsql). Para obtener información sobre los tipos de consulta, consulte [Execute](#execute).

##  <a name="isopen"></a>CDaoQueryDef:: IsOpen

Llame a esta función miembro para determinar si el objeto `CDaoQueryDef` está abierto actualmente.

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el objeto de `CDaoQueryDef` está abierto actualmente; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

Una definición de usuario debe estar en un estado abierto antes de usarla para llamar a [Execute](#execute) o para crear un objeto [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) . Para colocar una definición de tipo en una llamada de estado abierto, [cree](#create) (para una nueva definición de tipo) o [abra](#open) (para una definición de tipo existente).

##  <a name="m_pdatabase"></a>CDaoQueryDef:: m_pDatabase

Contiene un puntero al objeto [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) asociado al objeto QueryDef.

### <a name="remarks"></a>Observaciones

Utilice este puntero si necesita tener acceso a la base de datos directamente, por ejemplo, para obtener punteros a otros objetos QueryDef o Recordset de las colecciones de la base de datos.

##  <a name="m_pdaoquerydef"></a>CDaoQueryDef:: m_pDAOQueryDef

Contiene un puntero a la interfaz OLE para el objeto DAO QueryDef subyacente.

### <a name="remarks"></a>Observaciones

Este puntero se proporciona por integridad y coherencia con las otras clases. Sin embargo, dado que MFC en lugar de encapsular totalmente definiciones de usuario DAO, es poco probable que la necesite. Si lo usa, hágalo con precaución, en particular, no cambie el valor del puntero a menos que sepa lo que está haciendo.

##  <a name="open"></a>CDaoQueryDef:: Open

Llame a esta función miembro para abrir una definición de usuario previamente guardada en la colección QueryDefs de la base de datos.

```
virtual void Open(LPCTSTR lpszName = NULL);
```

### <a name="parameters"></a>Parámetros

*lpszName*<br/>
Cadena que contiene el nombre de la definición de tipo guardada que se va a abrir. Puede usar un [CString](../../atl-mfc-shared/reference/cstringt-class.md).

### <a name="remarks"></a>Observaciones

Una vez abierta la definición de usuario, se puede llamar a la función miembro [Execute](#execute) o usar la definición de método para crear un objeto [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) .

##  <a name="setconnect"></a>CDaoQueryDef:: SetConnect

Llame a esta función miembro para establecer la cadena de conexión del objeto QueryDef.

```
void SetConnect(LPCTSTR lpszConnect);
```

### <a name="parameters"></a>Parámetros

*lpszConnect*<br/>
Cadena que contiene una cadena de conexión para el objeto [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) asociado.

### <a name="remarks"></a>Observaciones

La cadena de conexión se usa para pasar información adicional a ODBC y ciertos controladores ISAM según sea necesario. No se utiliza para Microsoft Jet (. MDB).

> [!TIP]
>  La mejor manera de trabajar con tablas ODBC es asociarlas a un. Base de datos MDB.

Antes de ejecutar una definición de tipo que representa una consulta de paso a través de SQL a un origen de datos ODBC, establezca la cadena de conexión con `SetConnect` y llame a [SetReturnsRecords](#setreturnsrecords) para especificar si la consulta devuelve registros.

Para obtener más información sobre la estructura de la cadena de conexión y ejemplos de componentes de la cadena de conexión, vea el tema "propiedad de conexión" en la ayuda de DAO.

##  <a name="setname"></a>CDaoQueryDef:: SetName

Llame a esta función miembro si desea cambiar el nombre de una definición de usuario que no es temporal.

```
void SetName(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parámetros

*lpszName*<br/>
Cadena que contiene el nuevo nombre de una consulta no temporal en el objeto [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) asociado.

### <a name="remarks"></a>Observaciones

Los nombres de QueryDef son nombres únicos definidos por el usuario. Puede llamar a `SetName` antes de que el objeto QueryDef se anexe a la colección QueryDefs.

##  <a name="setodbctimeout"></a>CDaoQueryDef:: SetODBCTimeout

Llame a esta función miembro para establecer el límite de tiempo antes de que una consulta a un origen de datos ODBC agote el tiempo de espera.

```
void SetODBCTimeout(short nODBCTimeout);
```

### <a name="parameters"></a>Parámetros

*nODBCTimeout*<br/>
El número de segundos antes de que una consulta exceda el tiempo de espera.

### <a name="remarks"></a>Observaciones

Esta función miembro permite reemplazar el número predeterminado de segundos antes de que se agote el tiempo de espera de las operaciones posteriores en el origen de datos conectado. Una operación puede agotar el tiempo de espera debido a problemas de acceso a la red, un tiempo de procesamiento excesivo de consultas, etc. Llame a `SetODBCTimeout` antes de ejecutar una consulta con este QueryDef si desea cambiar el valor de tiempo de espera de la consulta. (Cuando ODBC reutiliza las conexiones, el valor de tiempo de espera es el mismo para todos los clientes en la misma conexión).

El valor predeterminado de los tiempos de espera de la consulta es de 60 segundos.

##  <a name="setparamvalue"></a>CDaoQueryDef:: SetParamValue

Llame a esta función miembro para establecer el valor de un parámetro en la definición de usuario en tiempo de ejecución.

```
virtual void SetParamValue(
    LPCTSTR lpszName,
    const COleVariant& varValue);

virtual void SetParamValue(
    int nIndex,
    const COleVariant& varValue);
```

### <a name="parameters"></a>Parámetros

*lpszName*<br/>
Nombre del parámetro cuyo valor se va a establecer.

*varValue*<br/>
Valor que se va a establecer. Vea la sección Comentarios.

*nIndex*<br/>
Posición ordinal del parámetro en la colección de parámetros de la definición de la definición. Puede obtener este valor con llamadas a [GetParameterCount](#getparametercount) y [GetParameterInfo](#getparameterinfo).

### <a name="remarks"></a>Observaciones

El parámetro ya se debe haber establecido como parte de la cadena SQL de la definición de tipo. Puede tener acceso al parámetro por el nombre o por su posición ordinal en la colección.

Especifique el valor que se va a establecer como un objeto de `COleVariant`. Para obtener información sobre cómo establecer el valor y el tipo deseado en el objeto `COleVariant`, vea la clase [COleVariant](../../mfc/reference/colevariant-class.md).

##  <a name="setreturnsrecords"></a>CDaoQueryDef:: SetReturnsRecords

Llame a esta función miembro como parte del proceso de configuración de una consulta de paso a través de SQL en una base de datos externa.

```
void SetReturnsRecords(BOOL bReturnsRecords);
```

### <a name="parameters"></a>Parámetros

*bReturnsRecords*<br/>
Pass TRUE si la consulta en una base de datos externa devuelve registros; en caso contrario, FALSE.

### <a name="remarks"></a>Observaciones

En tal caso, debe crear la definición de tipo y establecer sus propiedades utilizando otras funciones miembro de `CDaoQueryDef`. Para obtener una descripción de las bases de datos externas, vea [SetConnect](#setconnect).

##  <a name="setsql"></a>CDaoQueryDef:: SetSQL

Llame a esta función miembro para establecer la instrucción SQL que ejecuta la QueryDef.

```
void SetSQL(LPCTSTR lpszSQL);
```

### <a name="parameters"></a>Parámetros

*lpszSQL*<br/>
Una cadena que contiene una instrucción SQL completa, adecuada para su ejecución. La sintaxis de esta cadena depende del DBMS de destino de la consulta. Para obtener una explicación de la sintaxis utilizada en el motor de base de datos de Microsoft Jet, vea el tema "Building SQL statements in Code" en la ayuda de DAO.

### <a name="remarks"></a>Observaciones

Un uso típico de `SetSQL` es configurar un objeto QueryDef para su uso en una consulta de paso a través de SQL. (Para ver la sintaxis de las consultas de paso a través de SQL en el DBMS de destino, consulte la documentación de su DBMS).

## <a name="see-also"></a>Consulte también

[CObject (clase)](../../mfc/reference/cobject-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CDaoRecordset (clase)](../../mfc/reference/cdaorecordset-class.md)<br/>
[CDaoDatabase (clase)](../../mfc/reference/cdaodatabase-class.md)<br/>
[CDaoTableDef (clase)](../../mfc/reference/cdaotabledef-class.md)<br/>
[CDaoException (clase)](../../mfc/reference/cdaoexception-class.md)
