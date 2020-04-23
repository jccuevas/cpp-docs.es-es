---
title: Clase CDaoQueryDef
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
ms.openlocfilehash: ed298c40daa9485683d0b989e47b97fdce9f6562
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754700"
---
# <a name="cdaoquerydef-class"></a>Clase CDaoQueryDef

Representa una definición de consulta o "querydef", normalmente guardada en una base de datos.

## <a name="syntax"></a>Sintaxis

```
class CDaoQueryDef : public CObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CDaoQueryDef::CDaoQueryDef](#cdaoquerydef)|Construye un objeto `CDaoQueryDef`. Próxima `Open` llamada `Create`o , dependiendo de sus necesidades.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CDaoQueryDef::Append](#append)|Anexa la definición de consulta a la colección QueryDefs de la base de datos como una consulta guardada.|
|[CDaoQueryDef::CanUpdate](#canupdate)|Devuelve distinto de cero si la consulta puede actualizar la base de datos.|
|[CDaoQueryDef::Cerrar](#close)|Cierra el objeto querydef. Destruye el objeto C++ cuando termines con él.|
|[CDaoQueryDef::Crear](#create)|Crea el objeto de definición de consulta DAO subyacente. Use la definición de consulta como `Append` una consulta temporal o llame para guardarla en la base de datos.|
|[CDaoQueryDef::Execute](#execute)|Ejecuta la consulta definida por el objeto querydef.|
|[CDaoQueryDef::GetConnect](#getconnect)|Devuelve la cadena de conexión asociada a la definición de consulta. La cadena de conexión identifica el origen de datos. (Solo para consultas de paso a través de SQL; de lo contrario una cadena vacía.)|
|[CDaoQueryDef::GetDateCreated](#getdatecreated)|Devuelve la fecha en que se creó la consulta guardada.|
|[CDaoQueryDef::GetDateLastUpdated](#getdatelastupdated)|Devuelve la fecha en que se actualizó por última vez la consulta guardada.|
|[CDaoQueryDef::GetFieldCount](#getfieldcount)|Devuelve el número de campos definidos por la definición de consulta.|
|[CDaoQueryDef::GetFieldInfo](#getfieldinfo)|Devuelve información sobre un campo especificado definido en la consulta.|
|[CDaoQueryDef::GetName](#getname)|Devuelve el nombre de la definición de consulta.|
|[CDaoQueryDef::GetODBCTimeout](#getodbctimeout)|Devuelve el valor de tiempo de espera utilizado por ODBC (para una consulta ODBC) cuando se ejecuta la definición de consulta. Esto determina cuánto tiempo se debe permitir que se complete la acción de la consulta.|
|[CDaoQueryDef::GetParameterCount](#getparametercount)|Devuelve el número de parámetros definidos para la consulta.|
|[CDaoQueryDef::GetParameterInfo](#getparameterinfo)|Devuelve información sobre un parámetro especificado a la consulta.|
|[CDaoQueryDef::GetParamValue](#getparamvalue)|Devuelve el valor de un parámetro especificado a la consulta.|
|[CDaoQueryDef::GetRecordsAffected](#getrecordsaffected)|Devuelve el número de registros afectados por una consulta de acción.|
|[CDaoQueryDef::GetReturnsRecords](#getreturnsrecords)|Devuelve distinto de cero si la consulta definida por la definición de consulta devuelve registros.|
|[CDaoQueryDef::GetSQL](#getsql)|Devuelve la cadena SQL que especifica la consulta definida por la definición de consulta.|
|[CDaoQueryDef::GetType](#gettype)|Devuelve el tipo de consulta: delete, update, append, make-table, etc.|
|[CDaoQueryDef::IsOpen](#isopen)|Devuelve distinto de cero si la definición de consulta está abierta y se puede ejecutar.|
|[CDaoQueryDef::Open](#open)|Abre una definición de consulta existente almacenada en la colección QueryDefs de la base de datos.|
|[CDaoQueryDef::SetConnect](#setconnect)|Establece la cadena de conexión para una consulta de paso a través de SQL en un origen de datos ODBC.|
|[CDaoQueryDef::SetName](#setname)|Establece el nombre de la consulta guardada, reemplazando el nombre en uso cuando se creó la definición de consulta.|
|[CDaoQueryDef::SetODBCTimeout](#setodbctimeout)|Establece el valor de tiempo de espera utilizado por ODBC (para una consulta ODBC) cuando se ejecuta la definición de consulta.|
|[CDaoQueryDef::SetParamValue](#setparamvalue)|Establece el valor de un parámetro especificado en la consulta.|
|[CDaoQueryDef::SetReturnsRecords](#setreturnsrecords)|Especifica si la definición de consulta devuelve registros. Establecer este atributo en TRUE solo es válido para consultas de paso a través de SQL.|
|[CDaoQueryDef::SetSQL](#setsql)|Establece la cadena SQL que especifica la consulta definida por la definición de consulta.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CDaoQueryDef::m_pDAOQueryDef](#m_pdaoquerydef)|Puntero a la interfaz OLE para el objeto de definición de consulta DAO subyacente.|
|[CDaoQueryDef::m_pDatabase](#m_pdatabase)|Puntero al `CDaoDatabase` objeto con el que está asociada la definición de consulta. La definición de consulta podría guardarse en la base de datos o no.|

## <a name="remarks"></a>Observaciones

Una definición de consulta es un objeto de acceso a datos que contiene la instrucción SQL que describe una consulta y sus propiedades, como "Fecha de creación" y "Tiempo de espera ODBC." También puede crear objetos de definición de consulta temporales sin guardarlos, pero es conveniente,y mucho más eficaz, guardar las consultas reutilizadas en una base de datos. Un [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) objeto mantiene una colección, denominada el QueryDefs colección, que contiene sus definiciones de consulta guardadas.

> [!NOTE]
> Las clases de base de datos DAO son distintas de las clases de base de datos MFC basadas en Open Database Connectivity (ODBC). Todos los nombres de clase de base de datos DAO tienen el prefijo "CDao". Todavía puede tener acceso a orígenes de datos ODBC con las clases DAO. En general, las clases MFC basadas en DAO son más capaces que las clases MFC basadas en ODBC; las clases basadas en DAO pueden tener acceso a los datos, incluso a través de controladores ODBC, a través de su propio motor de base de datos. Las clases basadas en DAO también admiten operaciones de lenguaje de definición de datos (DDL), como agregar tablas a través de las clases, sin tener que llamar a DAO directamente.

## <a name="usage"></a>Uso

Utilice objetos querydef para trabajar con una consulta guardada existente o para crear una nueva consulta guardada o una consulta temporal:

1. En todos los casos, primero construir un `CDaoQueryDef` objeto, proporcionando un puntero a la [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) objeto al que pertenece la consulta.

1. A continuación, haga lo siguiente, dependiendo de lo que desee:

   - Para usar una consulta guardada existente, llame a la función miembro [Open](#open) del objeto querydef, proporcionando el nombre de la consulta guardada.

   - Para crear una nueva consulta guardada, llame a la función miembro [Create](#create) del objeto querydef, proporcionando el nombre de la consulta. A continuación, llame a [Append](#append) para guardar la consulta anexándola a la colección QueryDefs de la base de datos. `Create`pone la definición de consulta en un `Create` estado abierto, por lo que después de llamar no se llama a `Open`.

   - Para crear una definición `Create`de consulta temporal, llame a . Pase una cadena vacía para el nombre de la consulta. No llame a `Append`.

Cuando termine de usar un objeto querydef, llame a su [Close](#close) función miembro; a continuación, destruya el objeto querydef.

> [!TIP]
> La forma más fácil de crear consultas guardadas es crearlas y almacenarlas en la base de datos mediante Microsoft Access. A continuación, puede abrirlos y usarlos en el código MFC.

## <a name="purposes"></a>Propósitos

Puede utilizar un objeto querydef para cualquiera de los siguientes propósitos:

- Para crear `CDaoRecordset` un objeto

- Para llamar a `Execute` la función miembro del objeto para ejecutar directamente una consulta de acción o una consulta de paso a través de SQL

Puede usar un objeto querydef para cualquier tipo de consulta, incluidas las consultas select, action, crosstab, delete, update, append, make-table, data definition, SQL pass-through, union y bulk. El tipo de la consulta viene determinado por el contenido de la instrucción SQL que proporcione. Para obtener información acerca `Execute` de los tipos de consulta, vea el y [GetType](#gettype) funciones miembro. Los conjuntos de registros se usan normalmente para las consultas de devolución de filas, normalmente las que usan **SELECT ... FROM** palabras clave. `Execute`se utiliza más comúnmente para operaciones masivas. Para obtener más información, vea [Ejecutar](#execute) y [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md).

## <a name="querydefs-and-recordsets"></a>Querydefs y Conjuntos de registros

Para utilizar un objeto querydef para crear un `CDaoRecordset` objeto, normalmente se crea o se abre una definición de consulta como se ha descrito anteriormente. A continuación, construya un objeto de conjunto de registros, pasando un puntero al objeto querydef cuando llame a [CDaoRecordset::Open](../../mfc/reference/cdaorecordset-class.md#open). La definición de consulta que pase debe estar en un estado abierto. Para obtener más información, vea la clase [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md).

No puede usar una definición de consulta para crear un conjunto de registros (el uso más común para una definición de consulta) a menos que esté en un estado abierto. Coloque la definición de consulta en `Open` `Create`un estado abierto llamando a cualquiera o .

## <a name="external-databases"></a>Bases de datos externas

Los objetos Querydef son la forma preferida de usar el dialecto SQL nativo de un motor de base de datos externo. Por ejemplo, puede crear una consulta SQL de Transact (como se usa en Microsoft SQL Server) y almacenarla en un objeto querydef. Cuando necesite usar una consulta SQL no basada en el motor de base de datos Microsoft Jet, debe proporcionar una cadena de conexión que apunte al origen de datos externo. Las consultas con cadenas de conexión válidas omiten el motor de base de datos y pasan la consulta directamente al servidor de base de datos externo para su procesamiento.

> [!TIP]
> La forma preferida de trabajar con tablas ODBC es adjuntarlas a un Microsoft Jet (. MDB).

Para obtener información relacionada, vea los temas "Objeto QueryDef", "Colección QueryDefs" y "Objeto CdbDatabase" en el SDK de DAO.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

`CDaoQueryDef`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdao.h

## <a name="cdaoquerydefappend"></a><a name="append"></a>CDaoQueryDef::Append

Llame a esta función miembro después de llamar a [crear](#create) para crear un nuevo objeto querydef.

```
virtual void Append();
```

### <a name="remarks"></a>Observaciones

`Append`guarda la definición de consulta en la base de datos anexando el objeto a la colección QueryDefs de la base de datos. Puede usar la definición de consulta como un objeto temporal sin anexarla, pero si desea que persista, debe llamar a `Append`.

Si intenta anexar un objeto querydef temporal, MFC produce una excepción de tipo [CDaoException](../../mfc/reference/cdaoexception-class.md).

## <a name="cdaoquerydefcanupdate"></a><a name="canupdate"></a>CDaoQueryDef::CanUpdate

Llame a esta función miembro para determinar si puede modificar la definición de consulta, como cambiar su nombre o cadena SQL.

```
BOOL CanUpdate();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se le permite modificar la definición de consulta; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Puede modificar la definición de consulta si:

- No se basa en una base de datos que está abierta de solo lectura.

- Tiene permisos de actualización para la base de datos.

   Esto depende de si ha implementado características de seguridad. MFC no proporciona compatibilidad con la seguridad; debe implementarlo usted mismo llamando a DAO directamente o mediante Microsoft Access. Consulte el tema "Propiedad de permisos" en la Ayuda de DAO.

## <a name="cdaoquerydefcdaoquerydef"></a><a name="cdaoquerydef"></a>CDaoQueryDef::CDaoQueryDef

Construye un objeto `CDaoQueryDef`.

```
CDaoQueryDef(CDaoDatabase* pDatabase);
```

### <a name="parameters"></a>Parámetros

*pBase de datos*<br/>
Puntero a un objeto [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) abierto.

### <a name="remarks"></a>Observaciones

El objeto puede representar una definición de consulta existente almacenada en la colección QueryDefs de la base de datos, una nueva consulta que se va a almacenar en la colección o una consulta temporal, que no se va a almacenar. El siguiente paso depende del tipo de definición de consulta:

- Si el objeto representa una definición de consulta existente, llame a la función miembro [Open](#open) del objeto para inicializarlo.

- Si el objeto representa una nueva definición de consulta que se va a guardar, llame a la función miembro [Create](#create) del objeto. Esto agrega el objeto a la colección QueryDefs de la base de datos. A `CDaoQueryDef` continuación, llame a las funciones miembro para establecer los atributos del objeto. Por último, llame a [Anexar](#append).

- Si el objeto representa una definición de consulta temporal (no que se guardará en la base de datos), llame a , pasando `Create`una cadena vacía para el nombre de la consulta. Después `Create`de llamar a , inicialice la definición de consulta estableciendo directamente sus atributos. No llame a `Append`.

Para establecer los atributos de la definición de consulta, puede utilizar las funciones miembro [SetName](#setname), [SetSQL](#setsql), [SetConnect](#setconnect), [SetODBCTimeout](#setodbctimeout)y [SetReturnsRecords](#setreturnsrecords) .

Cuando termine con el objeto querydef, llame a su [Close](#close) función miembro. Si tiene un puntero a la definición de consulta, utilice el operador **delete** para destruir el objeto C++.

## <a name="cdaoquerydefclose"></a><a name="close"></a>CDaoQueryDef::Cerrar

Llame a esta función miembro cuando termine de usar el objeto querydef.

```
virtual void Close();
```

### <a name="remarks"></a>Observaciones

Al cerrar la definición de consulta, se libera el objeto DAO subyacente, `CDaoQueryDef` pero no se destruye el objeto de definición de consulta DAO guardado ni el objeto C++. Esto no es lo mismo que [CDaoDatabase::DeleteQueryDef](../../mfc/reference/cdaodatabase-class.md#deletequerydef), que elimina el definición de consulta de la colección QueryDefs de la base de datos en DAO (si no es una definición de consulta temporal).

## <a name="cdaoquerydefcreate"></a><a name="create"></a>CDaoQueryDef::Crear

Llame a esta función miembro para crear una nueva consulta guardada o una nueva consulta temporal.

```
virtual void Create(
    LPCTSTR lpszName = NULL,
    LPCTSTR lpszSQL = NULL);
```

### <a name="parameters"></a>Parámetros

*lpszName*<br/>
El nombre único de la consulta guardada en la base de datos. Para obtener más información acerca de la cadena, vea el tema "Método CreateQueryDef" en la Ayuda de DAO. Si acepta el valor predeterminado, una cadena vacía, se crea una definición de consulta temporal. Dicha consulta no se guarda en la colección QueryDefs.

*lpszSQL*<br/>
La cadena SQL que define la consulta. Si acepta el valor predeterminado de NULL, debe llamar más adelante a [SetSQL](#setsql) para establecer la cadena. Hasta entonces, la consulta no está definida. Sin embargo, puede utilizar la consulta indefinida para abrir un conjunto de registros; ver Comentarios para más detalles. La instrucción SQL debe definirse antes de poder anexar la definición de consulta a la colección QueryDefs.

### <a name="remarks"></a>Observaciones

Si pasa un nombre en *lpszName*, puede llamar a [Append](#append) para guardar la definición de consulta en la colección QueryDefs de la base de datos. De lo contrario, el objeto es una definición de consulta temporal y no se guarda. En cualquier caso, la definición de consulta está en un estado abierto y puede usarla para crear un [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objeto o llamar a la definición de consulta [Execute](#execute) función miembro.

Si no proporciona una instrucción SQL en *lpszSQL* `Execute` , no puede ejecutar la consulta con pero puede usarla para crear un conjunto de registros. En ese caso, MFC utiliza la instrucción SQL predeterminada del conjunto de registros.

## <a name="cdaoquerydefexecute"></a><a name="execute"></a>CDaoQueryDef::Execute

Llame a esta función miembro para ejecutar la consulta definida por el objeto querydef.

```
virtual void Execute(int nOptions = dbFailOnError);
```

### <a name="parameters"></a>Parámetros

*nOpciones*<br/>
Entero que determina las características de la consulta. Para obtener información relacionada, vea el tema "Método de ejecución" en la Ayuda de DAO. Puede utilizar el operador OR bit a bit ( **&#124;**) para combinar las siguientes constantes para este argumento:

- `dbDenyWrite`Denegar el permiso de escritura a otros usuarios.

- `dbInconsistent`Actualizaciones incoherentes.

- `dbConsistent`Actualizaciones coherentes.

- `dbSQLPassThrough`Paso a través de SQL. Hace que la instrucción SQL se pase a una base de datos ODBC para su procesamiento.

- `dbFailOnError`Valor predeterminado. Revierta las actualizaciones si se produce un error e informe del error al usuario.

- `dbSeeChanges`Genere un error en tiempo de ejecución si otro usuario está cambiando los datos que está editando.

> [!NOTE]
> Para obtener una explicación de los términos "incoherente" y "coherente", consulte el tema "Ejecutar método" en la Ayuda de DAO.

### <a name="remarks"></a>Observaciones

Los objetos Querydef utilizados para la ejecución de esta manera solo pueden representar uno de los siguientes tipos de consulta:

- Consultas de acción

- Consultas de paso a través de SQL

`Execute`no funciona para las consultas que devuelven registros, como las consultas de selección. `Execute`se utiliza normalmente para consultas de operaciones masivas, como **UPDATE**, **INSERT**o **SELECT INTO,** o para operaciones de lenguaje de definición de datos (DDL).

> [!TIP]
> La forma preferida de trabajar con orígenes de datos ODBC es adjuntar tablas a microsoft Jet (. MDB). Para obtener más información, vea el tema "Acceso a bases de datos externas con DAO" en la Ayuda de DAO.

Llame a la [GetRecordsAffected](#getrecordsaffected) función miembro del objeto querydef para `Execute` determinar el número de registros afectados por la llamada más reciente. Por ejemplo, `GetRecordsAffected` devuelve información sobre el número de registros eliminados, actualizados o insertados al ejecutar una consulta de acción. El recuento devuelto no reflejará los cambios en las tablas relacionadas cuando las actualizaciones o eliminaciones en cascada estén en vigor.

Si incluye `dbInconsistent` ambos `dbConsistent` y o si no incluye ninguno, el resultado es el valor predeterminado, `dbInconsistent`.

`Execute`no devuelve un conjunto de registros. El `Execute` uso de una consulta que selecciona registros hace que MFC produzca una excepción de tipo [CDaoException](../../mfc/reference/cdaoexception-class.md).

## <a name="cdaoquerydefgetconnect"></a><a name="getconnect"></a>CDaoQueryDef::GetConnect

Llame a esta función miembro para obtener la cadena de conexión asociada con el origen de datos de la definición de consulta.

```
CString GetConnect();
```

### <a name="return-value"></a>Valor devuelto

Un [CString](../../atl-mfc-shared/reference/cstringt-class.md) que contiene la cadena de conexión para la definición de consulta.

### <a name="remarks"></a>Observaciones

Esta función solo se utiliza con orígenes de datos ODBC y determinados controladores ISAM. No se utiliza con Microsoft Jet (. MDB); en este `GetConnect` caso, devuelve una cadena vacía. Para obtener más información, consulte [SetConnect](#setconnect).

> [!TIP]
> La forma preferida de trabajar con tablas ODBC es adjuntarlas a un archivo . Base de datos MDB. Para obtener más información, vea el tema "Acceso a bases de datos externas con DAO" en la Ayuda de DAO.

Para obtener información acerca de las cadenas de conexión, vea el tema "Conectar propiedad" en la Ayuda de DAO.

## <a name="cdaoquerydefgetdatecreated"></a><a name="getdatecreated"></a>CDaoQueryDef::GetDateCreated

Llame a esta función miembro para obtener la fecha en que se creó el objeto querydef.

```
COleDateTime GetDateCreated();
```

### <a name="return-value"></a>Valor devuelto

Un [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objeto que contiene la fecha y hora de la definición de consulta se creó.

### <a name="remarks"></a>Observaciones

Para obtener información relacionada, vea el tema "DateCreated, LastUpdated Properties" en la Ayuda de DAO.

## <a name="cdaoquerydefgetdatelastupdated"></a><a name="getdatelastupdated"></a>CDaoQueryDef::GetDateLastUpdated

Llame a esta función miembro para obtener la fecha en que se actualizó por última vez el objeto querydef, cuando se cambió cualquiera de sus propiedades, como su nombre, su cadena SQL o su cadena de conexión.

```
COleDateTime GetDateLastUpdated();
```

### <a name="return-value"></a>Valor devuelto

Un [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objeto que contiene la fecha y hora de la definición de consulta se actualizó por última vez.

### <a name="remarks"></a>Observaciones

Para obtener información relacionada, vea el tema "DateCreated, LastUpdated Properties" en la Ayuda de DAO.

## <a name="cdaoquerydefgetfieldcount"></a><a name="getfieldcount"></a>CDaoQueryDef::GetFieldCount

Llame a esta función miembro para recuperar el número de campos de la consulta.

```
short GetFieldCount();
```

### <a name="return-value"></a>Valor devuelto

El número de campos definidos en la consulta.

### <a name="remarks"></a>Observaciones

`GetFieldCount`es útil para recorrer en bucle todos los campos de la definición de consulta. Para ello, `GetFieldCount` utilícelo junto con [GetFieldInfo](#getfieldinfo).

## <a name="cdaoquerydefgetfieldinfo"></a><a name="getfieldinfo"></a>CDaoQueryDef::GetFieldInfo

Llame a esta función miembro para obtener varios tipos de información sobre un campo definido en la definición de consulta.

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
El índice de base cero del campo deseado en la colección Fields de la definición de consulta, para la búsqueda por índice.

*fieldinfo*<br/>
Una referencia `CDaoFieldInfo` a un objeto que devuelve la información solicitada.

*dwInfoOptions*<br/>
Opciones que especifican qué información sobre el campo se va a recuperar. Las opciones disponibles se enumeran aquí junto con lo que hacen que la función devuelva:

- AFX_DAO_PRIMARY_INFO (predeterminado) Nombre, Tipo, Tamaño, Atributos

- AFX_DAO_SECONDARY_INFO información principal más: Posición ordinal, Requerido, Permitir longitud cero, Campo de origen, Nombre extranjero, Tabla de origen, Orden de intercalación

- AFX_DAO_ALL_INFO información primaria y secundaria más: valor predeterminado, texto de validación, regla de validación

*lpszName*<br/>
Cadena que contiene el nombre del campo deseado para la búsqueda por nombre. Puede usar un [CString](../../atl-mfc-shared/reference/cstringt-class.md).

### <a name="remarks"></a>Observaciones

Para obtener una descripción de la información devuelta en *fieldinfo*, vea el [CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md) estructura. Esta estructura tiene miembros que corresponden a la información descriptiva en *dwInfoOptions* anterior. Si solicita un nivel de información, también obtendrá cualquier nivel de información anterior.

## <a name="cdaoquerydefgetname"></a><a name="getname"></a>CDaoQueryDef::GetName

Llame a esta función miembro para recuperar el nombre de la consulta representada por la definición de consulta.

```
CString GetName();
```

### <a name="return-value"></a>Valor devuelto

Nombre de la consulta.

### <a name="remarks"></a>Observaciones

Los nombres de definición de consulta son nombres únicos definidos por el usuario. Para obtener más información acerca de los nombres de definición de consulta, vea el tema "Propiedad de nombre" en la Ayuda de DAO.

## <a name="cdaoquerydefgetodbctimeout"></a><a name="getodbctimeout"></a>CDaoQueryDef::GetODBCTimeout

Llame a esta función miembro para recuperar el límite de tiempo actual antes de que se agota el tiempo de espera de una consulta a un origen de datos ODBC.

```
short GetODBCTimeout();
```

### <a name="return-value"></a>Valor devuelto

El número de segundos antes de que una consulta exceda el tiempo de espera.

### <a name="remarks"></a>Observaciones

Para obtener información acerca de este límite de tiempo, vea el tema "Propiedad ODBCTimeout" en la Ayuda de DAO.

> [!TIP]
> La forma preferida de trabajar con tablas ODBC es adjuntarlas a un Microsoft Jet (. MDB). Para obtener más información, vea el tema "Acceso a bases de datos externas con DAO" en la Ayuda de DAO.

## <a name="cdaoquerydefgetparametercount"></a><a name="getparametercount"></a>CDaoQueryDef::GetParameterCount

Llame a esta función miembro para recuperar el número de parámetros en la consulta guardada.

```
short GetParameterCount();
```

### <a name="return-value"></a>Valor devuelto

El número de parámetros definidos en la consulta.

### <a name="remarks"></a>Observaciones

`GetParameterCount`es útil para recorrer en bucle todos los parámetros de la definición de consulta. Para ello, `GetParameterCount` utilícelo junto con [GetParameterInfo](#getparameterinfo).

Para obtener información relacionada, vea los temas "Objeto de parámetro", "Colección de parámetros" y "Declaración de parámetros (SQL)" en la Ayuda de DAO.

## <a name="cdaoquerydefgetparameterinfo"></a><a name="getparameterinfo"></a>CDaoQueryDef::GetParameterInfo

Llame a esta función miembro para obtener información sobre un parámetro definido en la definición de consulta.

```cpp
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
El índice de base cero del parámetro deseado en la colección Parameters de la definición de consulta, para la búsqueda por índice.

*paraminfo*<br/>
Una referencia a un [CDaoParameterInfo](../../mfc/reference/cdaoparameterinfo-structure.md) objeto que devuelve la información solicitada.

*dwInfoOptions*<br/>
Opciones que especifican qué información sobre el parámetro se va a recuperar. La opción disponible se enumera aquí junto con lo que hace que la función devuelva:

- AFX_DAO_PRIMARY_INFO (predeterminado), escriba

*lpszName*<br/>
Cadena que contiene el nombre del parámetro deseado para buscar por nombre. Puede usar un [CString](../../atl-mfc-shared/reference/cstringt-class.md).

### <a name="remarks"></a>Observaciones

Para obtener una descripción de la información devuelta en *paraminfo*, vea el [CDaoParameterInfo](../../mfc/reference/cdaoparameterinfo-structure.md) estructura. Esta estructura tiene miembros que corresponden a la información descriptiva en *dwInfoOptions* anterior.

Para obtener información relacionada, vea el tema "Declaración de parameters (SQL)" en la Ayuda de DAO.

## <a name="cdaoquerydefgetparamvalue"></a><a name="getparamvalue"></a>CDaoQueryDef::GetParamValue

Llame a esta función miembro para recuperar el valor actual del parámetro especificado almacenado en la colección Parameters de la definición de consulta.

```
virtual COleVariant GetParamValue(LPCTSTR lpszName);
virtual COleVariant GetParamValue(int nIndex);
```

### <a name="parameters"></a>Parámetros

*lpszName*<br/>
El nombre del parámetro cuyo valor desea, para la búsqueda por nombre.

*nIndex*<br/>
El índice de base cero del parámetro en la colección Parameters de la definición de consulta, para la búsqueda por índice. Puede obtener este valor con llamadas a [GetParameterCount](#getparametercount) y [GetParameterInfo](#getparameterinfo).

### <a name="return-value"></a>Valor devuelto

Objeto de la clase [COleVariant](../../mfc/reference/colevariant-class.md) que contiene el valor del parámetro.

### <a name="remarks"></a>Observaciones

Puede acceder al parámetro por nombre o por su posición ordinal en la colección.

Para obtener información relacionada, vea el tema "Declaración de parameters (SQL)" en la Ayuda de DAO.

## <a name="cdaoquerydefgetrecordsaffected"></a><a name="getrecordsaffected"></a>CDaoQueryDef::GetRecordsAffected

Llame a esta función miembro para determinar cuántos registros se vieron afectados por la última llamada de [Execute](#execute).

```
long GetRecordsAffected();
```

### <a name="return-value"></a>Valor devuelto

El número de registros afectados.

### <a name="remarks"></a>Observaciones

El recuento devuelto no reflejará los cambios en las tablas relacionadas cuando las actualizaciones o eliminaciones en cascada estén en vigor.

Para obtener información relacionada, consulte el tema "Propiedad RecordsAffected" en la Ayuda de DAO.

## <a name="cdaoquerydefgetreturnsrecords"></a><a name="getreturnsrecords"></a>CDaoQueryDef::GetReturnsRecords

Llame a esta función miembro para determinar si la definición de consulta se basa en una consulta que devuelve registros.

```
BOOL GetReturnsRecords();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la definición de consulta se basa en una consulta que devuelve registros; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Esta función miembro solo se utiliza para consultas de paso a través de SQL. Para obtener más información acerca de las consultas SQL, vea el [Execute](#execute) función miembro. Para obtener más información acerca de cómo trabajar con consultas de paso a través de SQL, vea el [SetReturnsRecords](#setreturnsrecords) función miembro.

Para obtener información relacionada, vea el tema "ReturnsRecords Property" en la Ayuda de DAO.

## <a name="cdaoquerydefgetsql"></a><a name="getsql"></a>CDaoQueryDef::GetSQL

Llame a esta función miembro para recuperar la instrucción SQL que define la consulta en la que se basa la definición de consulta.

```
CString GetSQL();
```

### <a name="return-value"></a>Valor devuelto

La instrucción SQL que define la consulta en la que se basa la definición de consulta.

### <a name="remarks"></a>Observaciones

A continuación, probablemente analizará la cadena de palabras clave, nombres de tabla, etc.

Para obtener información relacionada, vea los temas "Sql Property", "Comparison of Microsoft Jet Database Engine SQL and ANSI SQL" y "Querying a Database with SQL in Code" en la Ayuda de DAO.

## <a name="cdaoquerydefgettype"></a><a name="gettype"></a>CDaoQueryDef::GetType

Llame a esta función miembro para determinar el tipo de consulta de la definición de consulta.

```
short GetType();
```

### <a name="return-value"></a>Valor devuelto

El tipo de la consulta definida por la definición de consulta. Para obtener valores, consulte Comentarios.

### <a name="remarks"></a>Observaciones

El tipo de consulta se establece mediante lo que se especifica en la cadena SQL de la definición de consulta al crear la definición de consulta o llamar a una definición de consulta existente [SetSQL](#setsql) función miembro. El tipo de consulta devuelto por esta función puede ser uno de los siguientes valores:

- `dbQSelect`Seleccione

- Acción de `dbQAction`

- `dbQCrosstab`Referencias cruzadas

- `dbQDelete`Eliminar

- `dbQUpdate` Update

- `dbQAppend`Anexar

- `dbQMakeTable`Make-table

- `dbQDDL`Definición de datos

- `dbQSQLPassThrough`Paso a través

- `dbQSetOperation`Unión

- `dbQSPTBulk`Se `dbQSQLPassThrough` utiliza con para especificar una consulta que no devuelve registros.

> [!NOTE]
> Para crear una consulta de paso a `dbSQLPassThrough` través de SQL, no establezca la constante. Esto lo establece automáticamente el motor de base de datos Microsoft Jet al crear un objeto querydef y establecer la cadena de conexión.

Para obtener información acerca de las cadenas SQL, vea [GetSQL](#getsql). Para obtener información acerca de los tipos de consulta, vea [Ejecutar](#execute).

## <a name="cdaoquerydefisopen"></a><a name="isopen"></a>CDaoQueryDef::IsOpen

Llame a esta función `CDaoQueryDef` miembro para determinar si el objeto está abierto actualmente.

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de `CDaoQueryDef` cero si el objeto está abierto actualmente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Una definición de consulta debe estar en un estado abierto antes de usarla para llamar a [Execute](#execute) o para crear un [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objeto. Para colocar una definición de consulta en una llamada de estado [abierto,](#create) ya sea Crear (para una nueva definición de consulta) o [Abrir](#open) (para una definición de consulta existente).

## <a name="cdaoquerydefm_pdatabase"></a><a name="m_pdatabase"></a>CDaoQueryDef::m_pDatabase

Contiene un puntero a la [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) objeto asociado con el objeto querydef.

### <a name="remarks"></a>Observaciones

Utilice este puntero si necesita tener acceso a la base de datos directamente, por ejemplo, para obtener punteros a otros objetos de definición de consulta o conjunto de registros en las colecciones de la base de datos.

## <a name="cdaoquerydefm_pdaoquerydef"></a><a name="m_pdaoquerydef"></a>CDaoQueryDef::m_pDAOQueryDef

Contiene un puntero a la interfaz OLE para el objeto de definición de consulta DAO subyacente.

### <a name="remarks"></a>Observaciones

Este puntero se proporciona para la integridad y coherencia con las otras clases. Sin embargo, dado que MFC encapsula completamente las definiciones de consulta DAO, es poco probable que lo necesite. Si lo usa, hágalo con precaución, en particular, no cambie el valor del puntero a menos que sepa lo que está haciendo.

## <a name="cdaoquerydefopen"></a><a name="open"></a>CDaoQueryDef::Open

Llame a esta función miembro para abrir una definición de consulta guardada previamente en la colección QueryDefs de la base de datos.

```
virtual void Open(LPCTSTR lpszName = NULL);
```

### <a name="parameters"></a>Parámetros

*lpszName*<br/>
Cadena que contiene el nombre de la definición de consulta guardada que se va a abrir. Puede usar un [CString](../../atl-mfc-shared/reference/cstringt-class.md).

### <a name="remarks"></a>Observaciones

Una vez que la definición de consulta está abierta, puede llamar a su [Execute](#execute) función miembro o usar el querydef para crear un [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objeto.

## <a name="cdaoquerydefsetconnect"></a><a name="setconnect"></a>CDaoQueryDef::SetConnect

Llame a esta función miembro para establecer la cadena de conexión del objeto querydef.

```cpp
void SetConnect(LPCTSTR lpszConnect);
```

### <a name="parameters"></a>Parámetros

*lpszConnect*<br/>
Cadena que contiene una cadena de conexión para el objeto [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) asociado.

### <a name="remarks"></a>Observaciones

La cadena de conexión se utiliza para pasar información adicional a ODBC y a determinados controladores ISAM según sea necesario. No se utiliza para Microsoft Jet (. MDB).

> [!TIP]
> La forma preferida de trabajar con tablas ODBC es adjuntarlas a un archivo . Base de datos MDB.

Antes de ejecutar una definición de consulta que representa una consulta de paso `SetConnect` a través de SQL en un origen de datos ODBC, establezca la cadena de conexión con y llame a [SetReturnsRecords](#setreturnsrecords) para especificar si la consulta devuelve registros.

Para obtener más información acerca de la estructura de la cadena de conexión y ejemplos de componentes de cadena de conexión, vea el tema "Connect Property" en la Ayuda de DAO.

## <a name="cdaoquerydefsetname"></a><a name="setname"></a>CDaoQueryDef::SetName

Llame a esta función miembro si desea cambiar el nombre de una definición de consulta que no es temporal.

```cpp
void SetName(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parámetros

*lpszName*<br/>
Cadena que contiene el nuevo nombre de una consulta no temporal en el objeto [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) asociado.

### <a name="remarks"></a>Observaciones

Los nombres de definición de consulta son nombres únicos definidos por el usuario. Puede llamar `SetName` antes de que el objeto querydef se anexe a la colección QueryDefs.

## <a name="cdaoquerydefsetodbctimeout"></a><a name="setodbctimeout"></a>CDaoQueryDef::SetODBCTimeout

Llame a esta función miembro para establecer el límite de tiempo antes de que se agota el tiempo de espera de una consulta en un origen de datos ODBC.

```cpp
void SetODBCTimeout(short nODBCTimeout);
```

### <a name="parameters"></a>Parámetros

*nODBCTimeout*<br/>
El número de segundos antes de que una consulta exceda el tiempo de espera.

### <a name="remarks"></a>Observaciones

Esta función miembro le permite invalidar el número predeterminado de segundos antes de las operaciones posteriores en el origen de datos conectado "tiempo de espera." Es posible que se agota el tiempo de espera de una operación debido a problemas de acceso a la red, tiempo excesivo de procesamiento de consultas, etc. Llame `SetODBCTimeout` antes de ejecutar una consulta con esta definición de consulta si desea cambiar el valor de tiempo de espera de la consulta. (A medida que ODBC reutiliza las conexiones, el valor de tiempo de espera es el mismo para todos los clientes en la misma conexión.)

El valor predeterminado para los tiempos de espera de consulta es 60 segundos.

## <a name="cdaoquerydefsetparamvalue"></a><a name="setparamvalue"></a>CDaoQueryDef::SetParamValue

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

*lpszName*<br/>
El nombre del parámetro cuyo valor desea establecer.

*varValue*<br/>
El valor que se va a establecer; ver Comentarios.

*nIndex*<br/>
La posición ordinal del parámetro en la colección Parameters de la definición de consulta. Puede obtener este valor con llamadas a [GetParameterCount](#getparametercount) y [GetParameterInfo](#getparameterinfo).

### <a name="remarks"></a>Observaciones

El parámetro ya debe haberse establecido como parte de la cadena SQL de la definición de consulta. Puede acceder al parámetro por nombre o por su posición ordinal en la colección.

Especifique el valor que `COleVariant` se va a establecer como un objeto. Para obtener información sobre cómo establecer `COleVariant` el valor y el tipo deseados en el objeto, vea la clase [COleVariant](../../mfc/reference/colevariant-class.md).

## <a name="cdaoquerydefsetreturnsrecords"></a><a name="setreturnsrecords"></a>CDaoQueryDef::SetReturnsRecords

Llame a esta función miembro como parte del proceso de configuración de una consulta de paso a través de SQL a una base de datos externa.

```cpp
void SetReturnsRecords(BOOL bReturnsRecords);
```

### <a name="parameters"></a>Parámetros

*bReturnsRecords*<br/>
Pasar TRUE si la consulta en una base de datos externa devuelve registros; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

En tal caso, debe crear la definición de `CDaoQueryDef` consulta y establecer sus propiedades mediante otras funciones miembro. Para obtener una descripción de las bases de datos externas, consulte [SetConnect](#setconnect).

## <a name="cdaoquerydefsetsql"></a><a name="setsql"></a>CDaoQueryDef::SetSQL

Llame a esta función miembro para establecer la instrucción SQL que ejecuta querydef.

```cpp
void SetSQL(LPCTSTR lpszSQL);
```

### <a name="parameters"></a>Parámetros

*lpszSQL*<br/>
Cadena que contiene una instrucción SQL completa, adecuada para su ejecución. La sintaxis de esta cadena depende del DBMS al que se dirige la consulta. Para obtener una explicación de la sintaxis utilizada en el motor de base de datos Microsoft Jet, vea el tema "Creación de instrucciones SQL en código" en la Ayuda de DAO.

### <a name="remarks"></a>Observaciones

Un uso `SetSQL` típico de es la configuración de un objeto querydef para su uso en una consulta de paso a través de SQL. (Para ver la sintaxis de las consultas de paso a través de SQL en el DBMS de destino, consulte la documentación del DBMS.)

## <a name="see-also"></a>Vea también

[Clase CObject](../../mfc/reference/cobject-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clase CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)<br/>
[CDaoDatabase (clase)](../../mfc/reference/cdaodatabase-class.md)<br/>
[CDaoTableDef (clase)](../../mfc/reference/cdaotabledef-class.md)<br/>
[Clase CDaoException](../../mfc/reference/cdaoexception-class.md)
