---
title: CDaoDatabase (clase)
ms.date: 09/17/2019
f1_keywords:
- CDaoDatabase
- AFXDAO/CDaoDatabase
- AFXDAO/CDaoDatabase::CDaoDatabase
- AFXDAO/CDaoDatabase::CanTransact
- AFXDAO/CDaoDatabase::CanUpdate
- AFXDAO/CDaoDatabase::Close
- AFXDAO/CDaoDatabase::Create
- AFXDAO/CDaoDatabase::CreateRelation
- AFXDAO/CDaoDatabase::DeleteQueryDef
- AFXDAO/CDaoDatabase::DeleteRelation
- AFXDAO/CDaoDatabase::DeleteTableDef
- AFXDAO/CDaoDatabase::Execute
- AFXDAO/CDaoDatabase::GetConnect
- AFXDAO/CDaoDatabase::GetName
- AFXDAO/CDaoDatabase::GetQueryDefCount
- AFXDAO/CDaoDatabase::GetQueryDefInfo
- AFXDAO/CDaoDatabase::GetQueryTimeout
- AFXDAO/CDaoDatabase::GetRecordsAffected
- AFXDAO/CDaoDatabase::GetRelationCount
- AFXDAO/CDaoDatabase::GetRelationInfo
- AFXDAO/CDaoDatabase::GetTableDefCount
- AFXDAO/CDaoDatabase::GetTableDefInfo
- AFXDAO/CDaoDatabase::GetVersion
- AFXDAO/CDaoDatabase::IsOpen
- AFXDAO/CDaoDatabase::Open
- AFXDAO/CDaoDatabase::SetQueryTimeout
- AFXDAO/CDaoDatabase::m_pDAODatabase
- AFXDAO/CDaoDatabase::m_pWorkspace
helpviewer_keywords:
- CDaoDatabase [MFC], CDaoDatabase
- CDaoDatabase [MFC], CanTransact
- CDaoDatabase [MFC], CanUpdate
- CDaoDatabase [MFC], Close
- CDaoDatabase [MFC], Create
- CDaoDatabase [MFC], CreateRelation
- CDaoDatabase [MFC], DeleteQueryDef
- CDaoDatabase [MFC], DeleteRelation
- CDaoDatabase [MFC], DeleteTableDef
- CDaoDatabase [MFC], Execute
- CDaoDatabase [MFC], GetConnect
- CDaoDatabase [MFC], GetName
- CDaoDatabase [MFC], GetQueryDefCount
- CDaoDatabase [MFC], GetQueryDefInfo
- CDaoDatabase [MFC], GetQueryTimeout
- CDaoDatabase [MFC], GetRecordsAffected
- CDaoDatabase [MFC], GetRelationCount
- CDaoDatabase [MFC], GetRelationInfo
- CDaoDatabase [MFC], GetTableDefCount
- CDaoDatabase [MFC], GetTableDefInfo
- CDaoDatabase [MFC], GetVersion
- CDaoDatabase [MFC], IsOpen
- CDaoDatabase [MFC], Open
- CDaoDatabase [MFC], SetQueryTimeout
- CDaoDatabase [MFC], m_pDAODatabase
- CDaoDatabase [MFC], m_pWorkspace
ms.assetid: 8ff5b342-964d-449d-bef1-d0ff56aadf6d
ms.openlocfilehash: 683f3f9ebb09d69461e4f9026841363c452f4793
ms.sourcegitcommit: 2f96e2fda591d7b1b28842b2ea24e6297bcc3622
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2019
ms.locfileid: "71096170"
---
# <a name="cdaodatabase-class"></a>CDaoDatabase (clase)

Representa una conexión a una base de datos de Access mediante objetos de acceso a datos (DAO). DAO es compatible con Office 2013. DAO 3,6 es la versión final y se considera obsoleta.

## <a name="syntax"></a>Sintaxis

```
class CDaoDatabase : public CObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CDaoDatabase::CDaoDatabase](#cdaodatabase)|Construye un objeto `CDaoDatabase`. Llame `Open` a para conectar el objeto a una base de datos.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CDaoDatabase::CanTransact](#cantransact)|Devuelve un valor distinto de cero si la base de datos admite transacciones.|
|[CDaoDatabase::CanUpdate](#canupdate)|Devuelve un valor distinto de `CDaoDatabase` cero si el objeto es actualizable (no es de solo lectura).|
|[CDaoDatabase::Close](#close)|Cierra la conexión a la base de datos.|
|[CDaoDatabase::Create](#create)|Crea el objeto de base de datos DAO subyacente e `CDaoDatabase` inicializa el objeto.|
|[CDaoDatabase::CreateRelation](#createrelation)|Define una nueva relación entre las tablas de la base de datos.|
|[CDaoDatabase::DeleteQueryDef](#deletequerydef)|Elimina un objeto QueryDef guardado en la colección QueryDefs de la base de datos.|
|[CDaoDatabase::DeleteRelation](#deleterelation)|Elimina una relación existente entre las tablas de la base de datos.|
|[CDaoDatabase::DeleteTableDef](#deletetabledef)|Elimina la definición de una tabla en la base de datos. Esto elimina la tabla real y todos sus datos.|
|[CDaoDatabase::Execute](#execute)|Ejecuta una consulta de acción. La `Execute` llamada a para una consulta que devuelve resultados produce una excepción.|
|[CDaoDatabase::GetConnect](#getconnect)|Devuelve la cadena de conexión que se usa `CDaoDatabase` para conectar el objeto a una base de datos. Se usa para ODBC.|
|[CDaoDatabase::GetName](#getname)|Devuelve el nombre de la base de datos actualmente en uso.|
|[CDaoDatabase::GetQueryDefCount](#getquerydefcount)|Devuelve el número de consultas definidas para la base de datos.|
|[CDaoDatabase::GetQueryDefInfo](#getquerydefinfo)|Devuelve información sobre una consulta especificada definida en la base de datos.|
|[CDaoDatabase::GetQueryTimeout](#getquerytimeout)|Devuelve el número de segundos después del cual se agotará el tiempo de espera de las operaciones de consulta de base de datos. Afecta a todas las operaciones posteriores de apertura, de actualización y de edición, así como a otras operaciones en orígenes de datos ODBC `Execute` (solo), como las llamadas.|
|[CDaoDatabase::GetRecordsAffected](#getrecordsaffected)|Devuelve el número de registros afectados por la última operación de actualización, edición o adición, o por una llamada `Execute`a.|
|[CDaoDatabase::GetRelationCount](#getrelationcount)|Devuelve el número de relaciones definidas entre las tablas de la base de datos.|
|[CDaoDatabase::GetRelationInfo](#getrelationinfo)|Devuelve información sobre una relación especificada definida entre tablas en la base de datos.|
|[CDaoDatabase::GetTableDefCount](#gettabledefcount)|Devuelve el número de tablas definidas en la base de datos.|
|[CDaoDatabase::GetTableDefInfo](#gettabledefinfo)|Devuelve información sobre una tabla especificada en la base de datos.|
|[CDaoDatabase::GetVersion](#getversion)|Devuelve la versión del motor de base de datos asociada a la base de datos.|
|[CDaoDatabase::IsOpen](#isopen)|Devuelve un valor distinto de `CDaoDatabase` cero si el objeto está conectado actualmente a una base de datos.|
|[CDaoDatabase::Open](#open)|Establece una conexión a una base de datos.|
|[CDaoDatabase::SetQueryTimeout](#setquerytimeout)|Establece el número de segundos transcurridos los cuales se agotará el tiempo de espera de las operaciones de consulta de base de datos (solo en orígenes de datos ODBC). Afecta a todas las operaciones de apertura, actualización y eliminación posteriores.|

### <a name="public-data-members"></a>Miembros de datos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CDaoDatabase::m_pDAODatabase](#m_pdaodatabase)|Puntero al objeto de base de datos DAO subyacente.|
|[CDaoDatabase::m_pWorkspace](#m_pworkspace)|Un puntero al objeto [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md) que contiene la base de datos y define su espacio de transacciones.|

## <a name="remarks"></a>Comentarios

Para obtener información sobre los formatos de base de datos admitidos, vea la función miembro [GetName](../../mfc/reference/cdaoworkspace-class.md#getname) . Puede tener uno o más `CDaoDatabase` objetos activos a la vez en un "área de trabajo" determinada representada por un objeto [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md) . El área de trabajo mantiene una colección de objetos de base de datos abiertos, denominada colección de bases de datos.

## <a name="usage"></a>Uso

Puede crear objetos de base de datos de forma implícita al crear objetos de conjunto de registros. Pero también puede crear objetos de base de datos explícitamente. Para utilizar una base de datos existente `CDaoDatabase`explícitamente con, realice una de las siguientes acciones:

- Construya un `CDaoDatabase` objeto, pasando un puntero a un objeto [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md) abierto.

- O construir un `CDaoDatabase` objeto sin especificar el área de trabajo (MFC crea un objeto temporal de área de trabajo).

Para crear una nueva Microsoft Jet (. MDB), construya un `CDaoDatabase` objeto y llame a su función miembro [Create](#create) . *No* llame a `Open` después `Create`de.

Para abrir una base de datos existente, `CDaoDatabase` construya un objeto y llame a su función miembro [abierta](#open) .

Cualquiera de estas técnicas anexa el objeto de base de datos DAO a la colección de bases de datos del área de trabajo y abre una conexión a los datos. Cuando se construyen objetos [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md), [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)o [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md) para trabajar en la base de datos conectada, se pasan los constructores para estos `CDaoDatabase` objetos a un puntero al objeto. Cuando termine de usar la conexión, llame a la función miembro [Close](#close) y destruya `CDaoDatabase` el objeto. `Close`cierra los conjuntos de registros que no se han cerrado previamente.

## <a name="transactions"></a>Transacciones

El procesamiento de transacciones de base de datos se proporciona en el nivel de área de trabajo; vea las funciones de miembro [BeginTrans](../../mfc/reference/cdaoworkspace-class.md#begintrans), [CommitTrans](../../mfc/reference/cdaoworkspace-class.md#committrans) y [Rollback](../../mfc/reference/cdaoworkspace-class.md#rollback) de la clase `CDaoWorkspace`.

## <a name="odbc-connections"></a>Conexiones ODBC

La manera recomendada de trabajar con orígenes de datos ODBC es adjuntar tablas externas a Microsoft Jet (. MDB).

## <a name="collections"></a>Colecciones

Cada base de datos mantiene sus propias colecciones de objetos tabledef, QueryDef, Recordset y Relation. La `CDaoDatabase` clase proporciona funciones miembro para manipular estos objetos.

> [!NOTE]
>  Los objetos se almacenan en DAO, no en el objeto de base de datos MFC. MFC proporciona clases para objetos tabledef, QueryDef y Recordset, pero no para objetos Relation.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

`CDaoDatabase`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdao. h

##  <a name="cantransact"></a>  CDaoDatabase::CanTransact

Llame a esta función miembro para determinar si la base de datos permite transacciones.

```
BOOL CanTransact();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la base de datos admite transacciones; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Las transacciones se administran en el área de trabajo de la base de datos.

##  <a name="canupdate"></a>  CDaoDatabase::CanUpdate

Llame a esta función miembro para determinar si `CDaoDatabase` el objeto permite actualizaciones.

```
BOOL CanUpdate();
```

### <a name="return-value"></a>Valor devuelto

Es distinto de cero `CDaoDatabase` si el objeto permite actualizaciones; de lo contrario, es 0, lo que indica que se pasó `CDaoDatabase` true en *bReadOnly* al abrir el objeto o que la propia base de datos es de solo lectura. Vea la función miembro [Open](#open) .

### <a name="remarks"></a>Comentarios

Para obtener información sobre la actualización de bases de datos, vea el tema "propiedad actualizable" en la ayuda de DAO.

##  <a name="cdaodatabase"></a>  CDaoDatabase::CDaoDatabase

Construye un objeto `CDaoDatabase`.

```
CDaoDatabase(CDaoWorkspace* pWorkspace = NULL);
```

### <a name="parameters"></a>Parámetros

*pWorkspace*<br/>
Un puntero al `CDaoWorkspace` objeto que contendrá el nuevo objeto de base de datos. Si acepta el valor predeterminado de NULL, el constructor crea un objeto temporal `CDaoWorkspace` que usa el área de trabajo de DAO predeterminada. Puede obtener un puntero al objeto de área de trabajo a través del miembro de datos [m_pWorkspace](#m_pworkspace) .

### <a name="remarks"></a>Comentarios

Después de construir el objeto, si está creando un nuevo Microsoft Jet (. MDB), llame a la función miembro [Create](#create) del objeto. Si, en su lugar, abre una base de datos existente, llame a la función miembro [abierta](#open) del objeto.

Cuando termine con el objeto, debe llamar a la función miembro [Close](#close) y, a continuación, `CDaoDatabase` destruir el objeto.

Puede que le resulte conveniente insertar el `CDaoDatabase` objeto en la clase de documento.

> [!NOTE]
>  Un `CDaoDatabase` objeto también se crea implícitamente si se abre un objeto [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) sin pasar un puntero a un objeto `CDaoDatabase` existente. Este objeto de base de datos se cierra al cerrar el objeto de conjunto de registros.

##  <a name="close"></a>  CDaoDatabase::Close

Llame a esta función miembro para desconectarse de una base de datos y cerrar los conjuntos de registros abiertos, las definiciones de conjunto y las definiciones de base asociadas a la base de datos.

```
virtual void Close();
```

### <a name="remarks"></a>Comentarios

Es recomendable cerrar estos objetos antes de llamar a esta función miembro. Al cerrar `CDaoDatabase` un objeto se quita de la colección de bases de datos en el [área de trabajo](../../mfc/reference/cdaoworkspace-class.md)asociada. Dado `Close` que no destruye el `CDaoDatabase` objeto, puede volver a usar el objeto abriendo la misma base de datos o una base de datos diferente.

> [!CAUTION]
>  Llame a la función miembro [Update](../../mfc/reference/cdaorecordset-class.md#update) (si hay ediciones pendientes) y a la `Close` función miembro en todos los objetos de conjunto de registros abiertos antes de cerrar una base de datos. Si sale de una función que declara objetos [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) o `CDaoDatabase` en la pila, la base de datos está cerrada, se pierden los cambios no guardados, se revierten todas las transacciones pendientes y se pierden las modificaciones pendientes en los datos.

> [!CAUTION]
>  Si intenta cerrar un objeto de base de datos mientras hay objetos de conjunto de registros abiertos, o si intenta cerrar un objeto de área de trabajo mientras los objetos de base de datos que pertenecen a ese área de trabajo específica están abiertos, se cerrarán esos objetos de conjunto de registros y las actualizaciones o ediciones pendientes serán revertido. Si intenta cerrar un objeto de área de trabajo mientras los objetos de base de datos que pertenecen a él están abiertos, la operación cierra todos los objetos de base de datos que pertenecen a ese objeto de área de trabajo específico, lo que puede dar lugar a que se cierren objetos de conjunto de registros sin cerrar. Si no cierra el objeto de base de datos, MFC informa de un error de aserción en las compilaciones de depuración.

Si el objeto de base de datos se define fuera del ámbito de una función y sale de la función sin cerrarla, el objeto de base de datos permanecerá abierto hasta que se cierre explícitamente o hasta que el módulo en el que se define esté fuera del ámbito.

##  <a name="create"></a>  CDaoDatabase::Create

Para crear una nueva Microsoft Jet (. MDB), llame a esta función miembro después de construir un `CDaoDatabase` objeto.

```
virtual void Create(
    LPCTSTR lpszName,
    LPCTSTR lpszLocale = dbLangGeneral,
    int dwOptions = 0);
```

### <a name="parameters"></a>Parámetros

*lpszName*<br/>
Expresión de cadena que es el nombre del archivo de base de datos que se va a crear. Puede ser la ruta de acceso completa y el nombre de archivo, como\\"C: \MYDB. MDB ". Debe proporcionar un nombre. Si no proporciona una extensión de nombre de archivo,. Se anexa la MDB. Si la red es compatible con la Convención de nomenclatura universal (UNC), también puede especificar una ruta de acceso de\\red, como\\"\\\\\MYSERVER\\\MYSHARE\\\MYDIR \MYDB". Solo Microsoft Jet (. MDB) para crear archivos de base de datos mediante esta función miembro. (Se requieren barras diagonales inversas dobles en los literales\\de cadena porque C++ "" es el carácter de escape).

*lpszLocale*<br/>
Expresión de cadena que se usa para especificar el orden de intercalación para crear la base de datos. El valor predeterminado es `dbLangGeneral`. Los valores posibles son:

- `dbLangGeneral`Inglés, alemán, Francés, Portugués, Italiano y español moderno

- `dbLangArabic`Árabe

- `dbLangCyrillic`Ruso

- `dbLangCzech`Checo

- `dbLangDutch`Holandés

- `dbLangGreek`Griego

- `dbLangHebrew`Hebreo

- `dbLangHungarian`Húngaro

- `dbLangIcelandic`Islandés

- `dbLangNordic`Idiomas nórdicos (solo la versión 1,0 del motor de base de datos de Microsoft Jet)

- `dbLangNorwdan`Noruego y danés

- `dbLangPolish`Polaco

- `dbLangSpanish`Español tradicional

- `dbLangSwedfin`Sueco y Finés

- `dbLangTurkish`Turco

*dwOptions*<br/>
Entero que indica una o más opciones. Los valores posibles son:

- `dbEncrypt`Cree una base de datos cifrada.

- `dbVersion10`Cree una base de datos con la versión 1,0 de la base de datos Microsoft Jet.

- `dbVersion11`Cree una base de datos con la versión 1,1 de la base de datos Microsoft Jet.

- `dbVersion20`Cree una base de datos con la versión 2,0 de la base de datos Microsoft Jet.

- `dbVersion30`Cree una base de datos con la versión 3,0 de la base de datos Microsoft Jet.

Si omite la constante de cifrado, se crea una base de datos sin cifrar. Solo puede especificar una constante de versión. Si omite una constante de versión, se crea una base de datos que usa la versión 3,0 de la base de datos Microsoft Jet.

> [!CAUTION]
>  Si una base de datos no está cifrada, es posible, incluso si implementa la seguridad de usuario/contraseña, para leer directamente el archivo de disco binario que constituye la base de datos.

### <a name="remarks"></a>Comentarios

`Create`crea el archivo de base de datos y el objeto de base de datos C++ DAO subyacente e inicializa el objeto. El objeto se anexa a la colección de bases de datos del área de trabajo asociada. El objeto de base de datos está en un estado abierto; no llame a `Open*` después `Create`de.

> [!NOTE]
>  Con `Create`, solo puede crear Microsoft Jet (. MDB). No se pueden crear bases de datos ISAM o bases de datos ODBC.

##  <a name="createrelation"></a>  CDaoDatabase::CreateRelation

Llame a esta función miembro para establecer una relación entre uno o varios campos de una tabla principal de la base de datos y uno o más campos de una tabla externa (otra tabla de la base de datos).

```
void CreateRelation(
    LPCTSTR lpszName,
    LPCTSTR lpszTable,
    LPCTSTR lpszForeignTable,
    long lAttributes,
    LPCTSTR lpszField,
    LPCTSTR lpszForeignField);

void CreateRelation(CDaoRelationInfo& relinfo);
```

### <a name="parameters"></a>Parámetros

*lpszName*<br/>
Nombre único del objeto de relación. El nombre debe empezar por una letra y puede contener un máximo de 40 caracteres. Puede incluir números y caracteres de subrayado, pero no puede incluir signos de puntuación ni espacios.

*lpszTable*<br/>
Nombre de la tabla principal de la relación. Si la tabla no existe, MFC produce una excepción de tipo [CDaoException](../../mfc/reference/cdaoexception-class.md).

*lpszForeignTable*<br/>
Nombre de la tabla externa de la relación. Si la tabla no existe, MFC produce una excepción de tipo `CDaoException`.

*lAttributes*<br/>
Valor Long que contiene información sobre el tipo de relación. Puede usar este valor para exigir la integridad referencial, entre otras cosas. Puede usar el operador OR bit a bit ( **&#124;** ) para combinar cualquiera de los valores siguientes (siempre y cuando la combinación tenga sentido):

- `dbRelationUnique`La relación es de uno a uno.

- `dbRelationDontEnforce`No se aplica la relación (ninguna integridad referencial).

- `dbRelationInherited`La relación existe en una base de datos no actual que contiene las dos tablas asociadas.

- `dbRelationUpdateCascade`Las actualizaciones se realizarán en cascada (para obtener más información sobre las cascadas, vea la sección comentarios).

- `dbRelationDeleteCascade`Las eliminaciones se aplicarán en cascada.

*lpszField*<br/>
Un puntero a una cadena terminada en null que contiene el nombre de un campo en la tabla principal (denominado por *lpszTable*).

*lpszForeignField*<br/>
Un puntero a una cadena terminada en null que contiene el nombre de un campo de la tabla externa (denominado por *lpszForeignTable*).

*relinfo*<br/>
Referencia a un objeto [cdaorelationinfo (](../../mfc/reference/cdaorelationinfo-structure.md) que contiene información sobre la relación que se va a crear.

### <a name="remarks"></a>Comentarios

La relación no puede implicar una consulta o una tabla adjunta de una base de datos externa.

Use la primera versión de la función cuando la relación implique un campo en cada una de las dos tablas. Use la segunda versión cuando la relación implique varios campos. El número máximo de campos de una relación es 14.

Esta acción crea un objeto de relación DAO subyacente, pero se trata de un detalle de implementación de MFC, ya que la encapsulación de objetos `CDaoDatabase`de relación de MFC está incluida en la clase. MFC no proporciona una clase para las relaciones.

Si establece los atributos del objeto de relación para activar las operaciones en cascada, el motor de base de datos actualiza o elimina automáticamente los registros de una o varias tablas cuando se realizan cambios en las tablas de clave principal relacionadas.

Por ejemplo, supongamos que establece una relación de eliminación en cascada entre una tabla de clientes y una tabla de pedidos. Cuando se eliminan registros de la tabla Customers, también se eliminan los registros de la tabla Orders relacionados con ese cliente. Además, si establece relaciones de eliminación en cascada entre la tabla Orders y otras tablas, los registros de esas tablas se eliminarán automáticamente al eliminar los registros de la tabla customers.

Para obtener información relacionada, vea el tema sobre el método CreateRelation en la ayuda de DAO.

##  <a name="deletequerydef"></a>  CDaoDatabase::DeleteQueryDef

Llame a esta función miembro para eliminar la definición de usuario (consulta guardada `CDaoDatabase` ) especificada de la colección QueryDefs del objeto.

```
void DeleteQueryDef(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parámetros

*lpszName*<br/>
Nombre de la consulta guardada que se va a eliminar.

### <a name="remarks"></a>Comentarios

Después, esa consulta ya no se define en la base de datos.

Para obtener información sobre cómo crear objetos QueryDef, vea la clase [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md). Un objeto QueryDef se asocia a un objeto `CDaoDatabase` determinado cuando se construye el `CDaoQueryDef` objeto, pasándole un puntero al objeto de base de datos.

##  <a name="deleterelation"></a>  CDaoDatabase::DeleteRelation

Llame a esta función miembro para eliminar una relación existente de la colección de relaciones del objeto de base de datos.

```
void DeleteRelation(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parámetros

*lpszName*<br/>
Nombre de la relación que se va a eliminar.

### <a name="remarks"></a>Comentarios

Posteriormente, la relación ya no existe.

Para obtener información relacionada, vea el tema "eliminar método" en la ayuda de DAO.

##  <a name="deletetabledef"></a>  CDaoDatabase::DeleteTableDef

Llame a esta función miembro para eliminar la tabla especificada y todos sus datos de la `CDaoDatabase` colección TableDefs del objeto.

```
void DeleteTableDef(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parámetros

*lpszName*<br/>
Nombre del TableDef que se va a eliminar.

### <a name="remarks"></a>Comentarios

Después, esa tabla ya no se define en la base de datos.

> [!NOTE]
>  Tenga mucho cuidado de no eliminar las tablas del sistema.

Para obtener información sobre cómo crear objetos tabledef, vea la clase [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md). Un objeto TableDef se asocia a un objeto `CDaoDatabase` determinado cuando se construye el `CDaoTableDef` objeto, pasándole un puntero al objeto de base de datos.

Para obtener información relacionada, vea el tema "eliminar método" en la ayuda de DAO.

##  <a name="execute"></a>  CDaoDatabase::Execute

Llame a esta función miembro para ejecutar una consulta de acción o ejecutar una instrucción SQL en la base de datos.

```
void Execute(
    LPCTSTR lpszSQL,
    int nOptions = dbFailOnError);
```

### <a name="parameters"></a>Parámetros

*lpszSQL*<br/>
Puntero a una cadena terminada en null que contiene un comando SQL válido que se va a ejecutar.

*nOptions*<br/>
Un entero que especifica las opciones relacionadas con la integridad de la consulta. Puede usar el operador OR bit a bit ( **&#124;** ) para combinar cualquiera de las constantes siguientes (siempre que la combinación tenga sentido; por ejemplo, no se combina `dbInconsistent` con `dbConsistent`):

- `dbDenyWrite`Denegar el permiso de escritura a otros usuarios.

- `dbInconsistent`Predeterminada Actualizaciones incoherentes.

- `dbConsistent`Actualizaciones coherentes.

- `dbSQLPassThrough`Paso a través de SQL. Hace que la instrucción SQL se pase a un origen de datos ODBC para su procesamiento.

- `dbFailOnError`Revertir las actualizaciones si se produce un error.

- `dbSeeChanges`Generar un error en tiempo de ejecución si otro usuario está cambiando los datos que está editando.

> [!NOTE]
>  Si se incluyen `dbConsistent`y, o si no se incluye ninguno, el resultado es el valor predeterminado. `dbInconsistent` Para obtener una explicación de estas constantes, vea el tema "Execute Method" en la ayuda de DAO.

### <a name="remarks"></a>Comentarios

`Execute`solo funciona con consultas de acción o consultas de paso a través de SQL que no devuelven resultados. No funciona para las consultas select, que devuelven registros.

Para obtener una definición e información acerca de las consultas de acción, vea los temas "consulta de acción" y "ejecutar método" en la ayuda de DAO.

> [!TIP]
>  Dada una instrucción SQL sintácticamente correcta y los permisos adecuados `Execute` , no se producirá un error en la función miembro aunque no se pueda modificar o eliminar una sola fila. Por lo tanto, use `dbFailOnError` siempre la opción al `Execute` usar la función miembro para ejecutar una consulta Update o DELETE. Esta opción hace que MFC inicie una excepción de tipo [CDaoException](../../mfc/reference/cdaoexception-class.md) y revierta todos los cambios realizados correctamente si alguno de los registros afectados está bloqueado y no se puede actualizar o eliminar. Tenga en cuenta que siempre se `GetRecordsAffected` puede llamar a para ver cuántos registros se vieron afectados.

Llame a la función miembro [GetRecordsAffected](#getrecordsaffected) del objeto de base de datos para determinar el número de registros afectados por `Execute` la llamada más reciente. Por ejemplo, `GetRecordsAffected` devuelve información sobre el número de registros eliminados, actualizados o insertados al ejecutar una consulta de acción. El recuento devuelto no reflejará los cambios en las tablas relacionadas cuando las actualizaciones o eliminaciones en cascada estén en vigor.

`Execute`no devuelve un conjunto de registros. El `Execute` uso de en una consulta que selecciona registros hace que MFC produzca una excepción `CDaoException`de tipo. (No hay ninguna `ExecuteSQL` función miembro análoga a `CDatabase::ExecuteSQL`).

##  <a name="getconnect"></a>  CDaoDatabase::GetConnect

Llame a esta función miembro para recuperar la cadena de conexión que se `CDaoDatabase` usa para conectar el objeto a una base de datos de ODBC o ISAM.

```
CString GetConnect();
```

### <a name="return-value"></a>Valor devuelto

La cadena de conexión si se ha llamado correctamente a [Open](#open) en un origen de datos ODBC. de lo contrario, una cadena vacía. Para un Microsoft Jet (. MDB), la cadena siempre está vacía, a menos que se establezca para su uso `dbSQLPassThrough` con la opción usada con la función miembro [Execute](#execute) o que se usa para abrir un conjunto de registros.

### <a name="remarks"></a>Comentarios

La cadena proporciona información acerca del origen de una base de datos abierta o de una base de datos utilizada en una consulta de paso a través. La cadena de conexión se compone de un especificador de tipo de base de datos y cero o más parámetros separados por punto y coma.

> [!NOTE]
>  El uso de las clases DAO de MFC para conectarse a un origen de datos a través de ODBC es menos eficaz que la conexión a través de una tabla adjunta.

> [!NOTE]
>  La cadena de conexión se usa para pasar información adicional a ODBC y ciertos controladores ISAM según sea necesario. No se utiliza para. Bases de datos MDB. En el caso de las tablas base de base de datos de Microsoft Jet, la cadena de conexión es una cadena vacía (""), excepto cuando se usa para una consulta de paso a través de SQL, tal y como se describe en valor devuelto anterior.

Vea la función miembro [Open](#open) para obtener una descripción de cómo se crea la cadena de conexión. Una vez que se ha establecido la cadena de `Open` conexión en la llamada, puede usarla más adelante para comprobar la configuración para determinar el tipo, la ruta de acceso, el ID. de usuario, la contraseña o el origen de datos ODBC de la base de datos.

##  <a name="getname"></a>  CDaoDatabase::GetName

Llame a esta función miembro para recuperar el nombre de la base de datos abierta actualmente, que es el nombre de un archivo de base de datos existente o el nombre de un origen de datos ODBC registrado.

```
CString GetName();
```

### <a name="return-value"></a>Valor devuelto

La ruta de acceso completa y el nombre de archivo de la base de datos si se realiza correctamente; de lo contrario, un [CString](../../atl-mfc-shared/reference/cstringt-class.md)vacío.

### <a name="remarks"></a>Comentarios

Si la red es compatible con la Convención de nomenclatura universal (UNC), también puede especificar una ruta de acceso de red\\,\\por\\ejemplo\\, "\\\\\MYSERVER \MYSHARE \MYDIR \MYDB. MDB ". (Se requieren barras diagonales inversas dobles en los literales\\de cadena porque C++ "" es el carácter de escape).

Por ejemplo, puede que desee mostrar este nombre en un encabezado. Si se produce un error mientras se recupera el nombre, MFC produce una excepción de tipo [CDaoException](../../mfc/reference/cdaoexception-class.md).

> [!NOTE]
>  Para obtener un mejor rendimiento cuando se tiene acceso a las bases de datos externas, se recomienda adjuntar tablas de bases de datos externas a una base de datos de Microsoft Jet (. MDB) en lugar de conectarse directamente al origen de datos.

El tipo de base de datos se indica mediante el archivo o directorio al que apunta la ruta de acceso, como se indica a continuación:

|El directorio apunta a..|Tipo de base de datos|
|--------------------------|-------------------|
|. Archivo MDB|Base de datos de Microsoft Jet (Microsoft Access)|
|Directorio que contiene. Archivos DBF|base de datos dBASE|
|Directorio que contiene. Archivo XLS|Base de datos de Microsoft Excel|
|Directorio que contiene. Archivos PDX|Base de datos de Paradox|
|Directorio que contiene archivos de base de datos de texto con el formato adecuado|Base de datos de formato de texto|

En el caso de las bases de datos ODBC como SQL Server y Oracle, la cadena de conexión de la base de datos identifica un nombre del origen de datos (DSN) registrado por ODBC.

##  <a name="getquerydefcount"></a>  CDaoDatabase::GetQueryDefCount

Llame a esta función miembro para recuperar el número de consultas definidas en la colección QueryDefs de la base de datos.

```
short GetQueryDefCount();
```

### <a name="return-value"></a>Valor devuelto

El número de consultas definidas en la base de datos.

### <a name="remarks"></a>Comentarios

`GetQueryDefCount`resulta útil si necesita recorrer todas las definiciones de la colección QueryDefs. Para obtener información acerca de una consulta determinada en la colección, vea [GetQueryDefInfo](#getquerydefinfo).

##  <a name="getquerydefinfo"></a>  CDaoDatabase::GetQueryDefInfo

Llame a esta función miembro para obtener varios tipos de información sobre una consulta definida en la base de datos.

```
void GetQueryDefInfo(
    int nIndex,
    CDaoQueryDefInfo& querydefinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

void GetQueryDefInfo(
    LPCTSTR lpszName,
    CDaoQueryDefInfo& querydefinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Índice de la consulta predefinida en la colección QueryDefs de la base de datos, para la búsqueda por índice.

*querydefinfo*<br/>
Referencia a un objeto [cdaoquerydefinfo (](../../mfc/reference/cdaoquerydefinfo-structure.md) que devuelve la información solicitada.

*dwInfoOptions*<br/>
Opciones que especifican la información sobre el conjunto de registros que se va a recuperar. Aquí se enumeran las opciones disponibles junto con lo que hacen que la función devuelva información sobre el conjunto de registros:

- Nombre de AFX_DAO_PRIMARY_INFO (valor predeterminado), tipo

- AFX_DAO_SECONDARY_INFO información principal más: Fecha de creación, fecha de la última actualización, devuelve registros, actualizable

- AFX_DAO_ALL_INFO la información principal y secundaria más: SQL, Connect, ODBCTimeout

*lpszName*<br/>
Cadena que contiene el nombre de una consulta definida en la base de datos, para la búsqueda por nombre.

### <a name="remarks"></a>Comentarios

Se proporcionan dos versiones de la función para que pueda seleccionar una consulta por índice en la colección QueryDefs de la base de datos o por el nombre de la consulta.

Para obtener una descripción de la información que se devuelve en *querydefinfo*, consulte la estructura [cdaoquerydefinfo (](../../mfc/reference/cdaoquerydefinfo-structure.md) . Esta estructura tiene miembros que corresponden a los elementos de la información enumerados anteriormente en la descripción de *dwInfoOptions*. Si solicita un nivel de información, también obtendrá cualquier nivel de información anterior.

##  <a name="getquerytimeout"></a>  CDaoDatabase::GetQueryTimeout

Llame a esta función miembro para recuperar el número actual de segundos que se permiten antes de que se agote el tiempo de espera de las operaciones posteriores en la base de datos conectada.

```
short GetQueryTimeout();
```

### <a name="return-value"></a>Valor devuelto

Entero corto que contiene el valor de tiempo de espera en segundos.

### <a name="remarks"></a>Comentarios

Una operación puede agotar el tiempo de espera debido a problemas de acceso a la red, un tiempo de procesamiento excesivo de consultas, etc. Aunque la configuración está en vigor, afecta a todas las operaciones de apertura, adición, actualización y eliminación en cualquier conjunto de registros asociado a `CDaoDatabase` este objeto. Puede cambiar la configuración de tiempo de espera actual llamando a [SetQueryTimeout](#setquerytimeout). Cambiar el valor de tiempo de espera de consulta para un conjunto de registros después de abrir no cambia el valor del conjunto de registros. Por ejemplo, las operaciones de [movimiento](../../mfc/reference/cdaorecordset-class.md#move) posteriores no usan el nuevo valor. El valor predeterminado se establece inicialmente cuando se inicializa el motor de base de datos.

El valor predeterminado de los tiempos de espera de consulta se toma del registro de Windows. Si no hay ninguna configuración del registro, el valor predeterminado es 60 segundos. No todas las bases de datos admiten la capacidad de establecer un valor de tiempo de espera de consulta. Si establece un valor de tiempo de espera de consulta de 0, no se produce ningún tiempo de espera. y la comunicación con la base de datos puede dejar de responder. Este comportamiento puede ser útil durante el desarrollo. Si se produce un error en la llamada, MFC produce una excepción de tipo [CDaoException](../../mfc/reference/cdaoexception-class.md).

Para obtener información relacionada, vea el tema "propiedad QueryTimeout" en la ayuda de DAO.

##  <a name="getrecordsaffected"></a>  CDaoDatabase::GetRecordsAffected

Llame a esta función miembro para determinar el número de registros afectados por la llamada más reciente de la función miembro [Execute](#execute) .

```
long GetRecordsAffected();
```

### <a name="return-value"></a>Valor devuelto

Entero largo que contiene el número de registros afectados.

### <a name="remarks"></a>Comentarios

El valor devuelto incluye el número de registros eliminados, actualizados o insertados por una consulta de `Execute`acción ejecutada con. El recuento devuelto no reflejará los cambios en las tablas relacionadas cuando las actualizaciones o eliminaciones en cascada estén en vigor.

Para obtener información relacionada, vea el tema "propiedad RecordsAffected" en la ayuda de DAO.

##  <a name="getrelationcount"></a>  CDaoDatabase::GetRelationCount

Llame a esta función miembro para obtener el número de relaciones definidas entre las tablas de la base de datos.

```
short GetRelationCount();
```

### <a name="return-value"></a>Valor devuelto

El número de relaciones definidas entre tablas en la base de datos.

### <a name="remarks"></a>Comentarios

`GetRelationCount`resulta útil si necesita recorrer todas las relaciones definidas en la colección de relaciones de la base de datos. Para obtener información sobre una relación determinada en la colección, vea [GetRelationInfo](#getrelationinfo).

Para ilustrar el concepto de una relación, considere la posibilidad de una tabla Suppliers y una tabla Products, que podría tener una relación de uno a varios. En esta relación, un proveedor puede proporcionar más de un producto. Otras relaciones son uno a uno y varios a varios.

##  <a name="getrelationinfo"></a>  CDaoDatabase::GetRelationInfo

Llame a esta función miembro para obtener información sobre una relación especificada en la colección de relaciones de la base de datos.

```
void GetRelationInfo(
    int nIndex,
    CDaoRelationInfo& relinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

void GetRelationInfo(
    LPCTSTR lpszName,
    CDaoRelationInfo& relinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Índice del objeto de relación de la colección de relaciones de la base de datos, para la búsqueda por índice.

*relinfo*<br/>
Referencia a un objeto [cdaorelationinfo (](../../mfc/reference/cdaorelationinfo-structure.md) que devuelve la información solicitada.

*dwInfoOptions*<br/>
Opciones que especifican la información sobre la relación que se va a recuperar. Aquí se enumeran las opciones disponibles junto con lo que hacen que la función devuelva sobre la relación:

- AFX_DAO_PRIMARY_INFO (valor predeterminado) nombre, tabla, tabla externa

- Atributos AFX_DAO_SECONDARY_INFO, información de campo

La información del campo es un objeto [cdaorelationfieldinfo (](../../mfc/reference/cdaorelationfieldinfo-structure.md) que contiene los campos de la tabla principal implicada en la relación.

*lpszName*<br/>
Cadena que contiene el nombre del objeto de relación, para la búsqueda por nombre.

### <a name="remarks"></a>Comentarios

Dos versiones de esta función proporcionan acceso por índice o por nombre. Para obtener una descripción de la información que se devuelve en *relinfo*, consulte la estructura [cdaorelationinfo (](../../mfc/reference/cdaorelationinfo-structure.md) . Esta estructura tiene miembros que corresponden a los elementos de la información enumerados anteriormente en la descripción de *dwInfoOptions*. Si solicita información en un nivel, también obtendrá información en cualquier nivel anterior.

> [!NOTE]
>  Si establece los atributos del objeto de relación para activar las operaciones en cascada`dbRelationUpdateCascades` ( `dbRelationDeleteCascades`o), el motor de base de datos de Microsoft Jet actualiza o elimina automáticamente los registros de una o varias tablas cuando se realizan cambios en la clave principal relacionada. tablas. Por ejemplo, supongamos que establece una relación de eliminación en cascada entre una tabla de clientes y una tabla de pedidos. Cuando se eliminan registros de la tabla Customers, también se eliminan los registros de la tabla Orders relacionados con ese cliente. Además, si establece relaciones de eliminación en cascada entre la tabla Orders y otras tablas, los registros de esas tablas se eliminarán automáticamente al eliminar los registros de la tabla customers.

##  <a name="gettabledefcount"></a>  CDaoDatabase::GetTableDefCount

Llame a esta función miembro para recuperar el número de tablas definidas en la base de datos.

```
short GetTableDefCount();
```

### <a name="return-value"></a>Valor devuelto

Número de definiciones de código definidas en la base de datos.

### <a name="remarks"></a>Comentarios

`GetTableDefCount`resulta útil si necesita recorrer todas las definiciones de base de la colección TableDefs de la base de datos. Para obtener información sobre una tabla determinada de la colección, vea [GetTableDefInfo](#gettabledefinfo).

##  <a name="gettabledefinfo"></a>  CDaoDatabase::GetTableDefInfo

Llame a esta función miembro para obtener varios tipos de información acerca de una tabla definida en la base de datos.

```
void GetTableDefInfo(
    int nIndex,
    CDaoTableDefInfo& tabledefinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

void GetTableDefInfo(
    LPCTSTR lpszName,
    CDaoTableDefInfo& tabledefinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Índice del objeto TableDef de la colección TableDefs de la base de datos, para la búsqueda por índice.

*tabledefinfo*<br/>
Referencia a un objeto [cdaotabledefinfo (](../../mfc/reference/cdaotabledefinfo-structure.md) que devuelve la información solicitada.

*dwInfoOptions*<br/>
Opciones que especifican la información sobre la tabla que se va a recuperar. Aquí se enumeran las opciones disponibles junto con lo que hacen que la función devuelva sobre la relación:

- AFX_DAO_PRIMARY_INFO (predeterminado) nombre, actualizable, atributos

- AFX_DAO_SECONDARY_INFO información principal más: Fecha de creación, fecha de última actualización, nombre de la tabla de origen, conectar

- AFX_DAO_ALL_INFO la información principal y secundaria más: Regla de validación, texto de validación, número de registros

*lpszName*<br/>
Nombre del objeto TableDef, para buscar por nombre.

### <a name="remarks"></a>Comentarios

Se proporcionan dos versiones de la función para que pueda seleccionar una tabla por índice en la colección TableDefs de la base de datos o por el nombre de la tabla.

Para obtener una descripción de la información que se devuelve en *tabledefinfo*, consulte la estructura [cdaotabledefinfo (](../../mfc/reference/cdaotabledefinfo-structure.md) . Esta estructura tiene miembros que corresponden a los elementos de la información enumerados anteriormente en la descripción de *dwInfoOptions*. Si solicita información en un nivel, también obtendrá información para cualquier nivel anterior.

> [!NOTE]
>  La opción AFX_DAO_ALL_INFO proporciona información que puede ser lenta de obtener. En este caso, el recuento de los registros de la tabla podría llevar mucho tiempo si hay muchos registros.

##  <a name="getversion"></a>  CDaoDatabase::GetVersion

Llame a esta función miembro para determinar la versión del archivo de base de datos de Microsoft Jet.

```
CString GetVersion();
```

### <a name="return-value"></a>Valor devuelto

[CString](../../atl-mfc-shared/reference/cstringt-class.md) que indica la versión del archivo de base de datos asociado al objeto.

### <a name="remarks"></a>Comentarios

El valor devuelto representa el número de versión con el formato "Major. minor"; por ejemplo, "3,0". El número de versión del producto (por ejemplo, 3,0) consta del número de versión (3), un punto y el número de versión (0). Las versiones hasta la fecha son 1,0, 1,1, 2,0 y 3,0.

Para obtener información relacionada, vea el tema "propiedad version" en la ayuda de DAO.

##  <a name="isopen"></a>  CDaoDatabase::IsOpen

Llame a esta función miembro para determinar si `CDaoDatabase` el objeto está abierto actualmente en una base de datos.

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>Valor devuelto

Es distinto de cero `CDaoDatabase` si el objeto está abierto actualmente; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

##  <a name="m_pdaodatabase"></a>  CDaoDatabase::m_pDAODatabase

Contiene un puntero a la interfaz OLE para el objeto de base de datos `CDaoDatabase` DAO subyacente al objeto.

### <a name="remarks"></a>Comentarios

Utilice este puntero si necesita tener acceso a la interfaz de DAO directamente.

Para obtener información sobre cómo llamar directamente a DAO, vea la [Nota técnica 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).

##  <a name="m_pworkspace"></a>  CDaoDatabase::m_pWorkspace

Contiene un puntero al objeto [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md) que contiene el objeto de base de datos.

### <a name="remarks"></a>Comentarios

Utilice este puntero si necesita tener acceso directamente al área de trabajo; por ejemplo, para obtener punteros a otros objetos de base de datos en la colección de bases de datos del área de trabajo.

##  <a name="open"></a>  CDaoDatabase::Open

Debe llamar a esta función miembro para inicializar un objeto `CDaoDatabase` recién construido que representa una base de datos existente.

```
virtual void Open(
    LPCTSTR lpszName,
    BOOL bExclusive = FALSE,
    BOOL bReadOnly = FALSE,
    LPCTSTR lpszConnect = _T(""));
```

### <a name="parameters"></a>Parámetros

*lpszName*<br/>
Expresión de cadena que es el nombre de una existente de Microsoft Jet (. MDB). Si el nombre de archivo tiene una extensión, es obligatorio. Si la red es compatible con la Convención de nomenclatura universal (UNC), también puede especificar una ruta de acceso de\\red, como\\"\\\\\MYSERVER\\\MYSHARE\\\MYDIR \MYDB. MDB ". (Se requieren barras diagonales inversas dobles en los literales\\de cadena porque C++ "" es el carácter de escape).

Se aplican algunas consideraciones al usar *lpszName*. Si es así:

- Hace referencia a una base de datos que ya está abierta para el acceso exclusivo de otro usuario, MFC produce una excepción de tipo [CDaoException](../../mfc/reference/cdaoexception-class.md). Capture esa excepción para que el usuario sepa que la base de datos no está disponible.

- Es una cadena vacía ("") y *lpszConnect* es "ODBC;", se muestra un cuadro de diálogo que enumera todos los nombres de orígenes de datos ODBC registrados para que el usuario pueda seleccionar una base de datos. Debe evitar las conexiones directas a los orígenes de datos ODBC. en su lugar, use una tabla adjunta.

- De lo contrario, no hace referencia a una base de datos existente o a un nombre de origen de datos ODBC `CDaoException`válido, MFC produce una excepción de tipo.

> [!NOTE]
>  Para obtener más información sobre los códigos de error de DAO, vea DAOERR. H archivo. Para obtener información relacionada, vea el tema "errores de acceso a datos recapturables" en la ayuda de DAO.

*bExclusive*<br/>
Valor booleano que es TRUE si la base de datos se va a abrir para el acceso exclusivo (no compartido) y FALSE si la base de datos se va a abrir para el acceso compartido. Si omite este argumento, la base de datos se abre para el acceso compartido.

*bReadOnly*<br/>
Valor booleano que es TRUE si la base de datos se va a abrir para el acceso de solo lectura y FALSE si la base de datos se va a abrir para el acceso de lectura y escritura. Si omite este argumento, la base de datos se abre para acceso de lectura y escritura. Todos los conjuntos de registros dependientes heredan este atributo.

*lpszConnect*<br/>
Expresión de cadena utilizada para abrir la base de datos. Esta cadena constituye los argumentos de conexión ODBC. Debe proporcionar los argumentos exclusivo y de solo lectura para proporcionar una cadena de origen. Si la base de datos es una base de datos de Microsoft Jet (. MDB), esta cadena está vacía (""). La sintaxis del valor predeterminado, _ **t**(""), proporciona portabilidad para Unicode y compilaciones ANSI de la aplicación.

### <a name="remarks"></a>Comentarios

`Open`asocia la base de datos al objeto DAO subyacente. No se puede usar el objeto de base de datos para construir objetos Recordset, TableDef o QueryDef hasta que se inicialice. `Open`anexa el objeto de base de datos a la colección de bases de datos del área de trabajo asociada.

Use los parámetros de la siguiente manera:

- Si está abriendo un Microsoft Jet (. MDB), use el parámetro *lpszName* y pase una cadena vacía para el parámetro *lpszConnect* o pase una cadena de contraseña con el formato "; PWD = contraseña "si la base de datos está protegida por contraseña (. Solo bases de datos MDB).

- Si está abriendo un origen de datos ODBC, pase una cadena de conexión ODBC válida en *lpszConnect* y una cadena vacía en *lpszName*.

Para obtener información relacionada, vea el tema sobre el método OpenDatabase en la ayuda de DAO.

> [!NOTE]
>  Para mejorar el rendimiento al obtener acceso a bases de datos externas, incluidas las bases de datos ISAM y los orígenes de datos ODBC, se recomienda adjuntar tablas de bases de datos externas a una base de datos del motor de Microsoft Jet (. MDB) en lugar de conectarse directamente al origen de datos.

Es posible que se agote el tiempo de espera de un intento de conexión si, por ejemplo, el host de DBMS no está disponible. Si se produce un error en `Open` el intento de conexión, se produce una excepción de tipo [CDaoException](../../mfc/reference/cdaoexception-class.md).

Las notas restantes solo se aplican a las bases de datos ODBC:

Si la base de datos es una base de datos ODBC y `Open` los parámetros de la llamada no contienen suficiente información para realizar la conexión, el controlador ODBC abre un cuadro de diálogo para obtener la información necesaria del usuario. Cuando se llama `Open`a, la cadena de conexión, *lpszConnect*, se almacena de forma privada y está disponible mediante una llamada a la función miembro [GetConnect](#getconnect) .

Si lo desea, puede abrir su propio cuadro de diálogo antes de llamar `Open` a para obtener información del usuario, como una contraseña, y después agregar esa información a la cadena de conexión que se `Open`pasa a. O bien, puede que desee guardar la cadena de conexión que ha superado (quizás en el registro de Windows) para que pueda reutilizarla `Open` la próxima `CDaoDatabase` vez que la aplicación llame a en un objeto.

También puede usar la cadena de conexión para varios niveles de autorización de inicio de sesión (cada `CDaoDatabase` uno para un objeto diferente) o para transmitir otra información específica de la base de datos.

##  <a name="setquerytimeout"></a>  CDaoDatabase::SetQueryTimeout

Llame a esta función miembro para invalidar el número predeterminado de segundos que se va a permitir antes de que se agote el tiempo de espera de las operaciones posteriores en la base de datos conectada.

```
void SetQueryTimeout(short nSeconds);
```

### <a name="parameters"></a>Parámetros

*nSeconds*<br/>
Número de segundos que se va a permitir antes de que se agote el tiempo de espera de un intento de consulta.

### <a name="remarks"></a>Comentarios

Una operación puede agotar el tiempo de espera debido a problemas de acceso a la red, un tiempo de procesamiento excesivo de consultas, etc. Llame `SetQueryTimeout` a antes de abrir el conjunto de registros o antes de llamar a las funciones miembro [AddNew](../../mfc/reference/cdaorecordset-class.md#addnew), [Update](../../mfc/reference/cdaorecordset-class.md#update)o [Delete](../../mfc/reference/cdaorecordset-class.md#delete) del conjunto de registros si desea cambiar el valor de tiempo de espera de la consulta. La configuración afecta a todas las llamadas [Abiertas](../../mfc/reference/cdaorecordset-class.md#open), `AddNew`, `Update` y `Delete` a cualquier conjunto de registros asociado a este objeto `CDaoDatabase`. Cambiar el valor de tiempo de espera de consulta para un conjunto de registros después de abrir no cambia el valor del conjunto de registros. Por ejemplo, las operaciones de [movimiento](../../mfc/reference/cdaorecordset-class.md#move) posteriores no usan el nuevo valor.

El valor predeterminado de los tiempos de espera de la consulta es de 60 segundos. No todas las bases de datos admiten la capacidad de establecer un valor de tiempo de espera de consulta. Si establece un valor de tiempo de espera de consulta de 0, no se produce ningún tiempo de espera. la comunicación con la base de datos puede dejar de responder. Este comportamiento puede ser útil durante el desarrollo.

Para obtener información relacionada, vea el tema "propiedad QueryTimeout" en la ayuda de DAO.

## <a name="see-also"></a>Vea también

[CObject (clase)](../../mfc/reference/cobject-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CDaoWorkspace (clase)](../../mfc/reference/cdaoworkspace-class.md)<br/>
[CDaoRecordset (clase)](../../mfc/reference/cdaorecordset-class.md)<br/>
[CDaoTableDef (clase)](../../mfc/reference/cdaotabledef-class.md)<br/>
[CDaoQueryDef (clase)](../../mfc/reference/cdaoquerydef-class.md)<br/>
[CDatabase (clase)](../../mfc/reference/cdatabase-class.md)<br/>
[CDaoException (clase)](../../mfc/reference/cdaoexception-class.md)
