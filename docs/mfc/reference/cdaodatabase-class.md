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
ms.openlocfilehash: debba137878da49921df83da7630003a7d62db2f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369017"
---
# <a name="cdaodatabase-class"></a>CDaoDatabase (clase)

Representa una conexión a una base de datos de Access mediante objetos de acceso a datos (DAO). DAO se admite a través de Office 2013. DAO 3.6 es la versión final, y se considera obsoleto.

## <a name="syntax"></a>Sintaxis

```
class CDaoDatabase : public CObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CDaoDatabase::CDaoDatabase](#cdaodatabase)|Construye un objeto `CDaoDatabase`. Llame `Open` para conectar el objeto a una base de datos.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CDaoDatabase::CanTransact](#cantransact)|Devuelve distinto de cero si la base de datos admite transacciones.|
|[CDaoDatabase::CanUpdate](#canupdate)|Devuelve distinto de `CDaoDatabase` cero si el objeto es actualizable (no de solo lectura).|
|[CDaoDatabase::Close](#close)|Cierra la conexión de base de datos.|
|[CDaoDatabase::Create](#create)|Crea el objeto de base de `CDaoDatabase` datos DAO subyacente e inicializa el objeto.|
|[CDaoDatabase::CreateRelation](#createrelation)|Define una nueva relación entre las tablas de la base de datos.|
|[CDaoDatabase::DeleteQueryDef](#deletequerydef)|Elimina un objeto querydef guardado en la colección QueryDefs de la base de datos.|
|[CDaoDatabase::DeleteRelation](#deleterelation)|Elimina una relación existente entre las tablas de la base de datos.|
|[CDaoDatabase::DeleteTableDef](#deletetabledef)|Elimina la definición de una tabla en la base de datos. Esto elimina la tabla real y todos sus datos.|
|[CDaoDatabase::Execute](#execute)|Ejecuta una consulta de acción. Al `Execute` llamar a una consulta que devuelve resultados, se produce una excepción.|
|[CDaoDatabase::GetConnect](#getconnect)|Devuelve la cadena de `CDaoDatabase` conexión utilizada para conectar el objeto a una base de datos. Se utiliza para ODBC.|
|[CDaoDatabase::GetName](#getname)|Devuelve el nombre de la base de datos actualmente en uso.|
|[CDaoDatabase::GetQueryDefCount](#getquerydefcount)|Devuelve el número de consultas definidas para la base de datos.|
|[CDaoDatabase::GetQueryDefInfo](#getquerydefinfo)|Devuelve información sobre una consulta especificada definida en la base de datos.|
|[CDaoDatabase::GetQueryTimeout](#getquerytimeout)|Devuelve el número de segundos después de los cuales se agota el tiempo de espera de las operaciones de consulta de base de datos. Afecta a todas las operaciones posteriores de apertura, adición, actualización `Execute` y edición y otras operaciones en orígenes de datos ODBC (solo) como llamadas.|
|[CDaoDatabase::GetRecordsAffected](#getrecordsaffected)|Devuelve el número de registros afectados por la última operación de actualización, edición o adición o por una llamada a `Execute`.|
|[CDaoDatabase::GetRelationCount](#getrelationcount)|Devuelve el número de relaciones definidas entre las tablas de la base de datos.|
|[CDaoDatabase::GetRelationInfo](#getrelationinfo)|Devuelve información sobre una relación especificada definida entre las tablas de la base de datos.|
|[CDaoDatabase::GetTableDefCount](#gettabledefcount)|Devuelve el número de tablas definidas en la base de datos.|
|[CDaoDatabase::GetTableDefInfo](#gettabledefinfo)|Devuelve información sobre una tabla especificada en la base de datos.|
|[CDaoDatabase::GetVersion](#getversion)|Devuelve la versión del motor de base de datos asociado a la base de datos.|
|[CDaoDatabase::IsOpen](#isopen)|Devuelve distinto de `CDaoDatabase` cero si el objeto está conectado actualmente a una base de datos.|
|[CDaoDatabase::Open](#open)|Establece una conexión a una base de datos.|
|[CDaoDatabase::SetQueryTimeout](#setquerytimeout)|Establece el número de segundos después de los cuales las operaciones de consulta de base de datos (solo en orígenes de datos ODBC) agotarán el tiempo de espera. Afecta a todas las operaciones posteriores de apertura, adición, actualización y eliminación.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CDaoDatabase::m_pDAODatabase](#m_pdaodatabase)|Puntero al objeto de base de datos DAO subyacente.|
|[CDaoDatabase::m_pWorkspace](#m_pworkspace)|Puntero al objeto [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md) que contiene la base de datos y define su espacio de transacciones.|

## <a name="remarks"></a>Observaciones

Para obtener información acerca de los formatos de base de datos admitidos, vea el [GetName](../../mfc/reference/cdaoworkspace-class.md#getname) función miembro. Puede tener uno `CDaoDatabase` o varios objetos activos a la vez en un determinado "espacio de trabajo", representado por un [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md) objeto. El área de trabajo mantiene una colección de objetos de base de datos abiertos, denominada la colección Databases.

## <a name="usage"></a>Uso

Puede crear objetos de base de datos implícitamente al crear objetos de conjunto de registros. Pero también puede crear objetos de base de datos explícitamente. Para utilizar una base `CDaoDatabase`de datos existente explícitamente con , realice una de las siguientes acciones:

- Construir `CDaoDatabase` un objeto, pasando un puntero a un [abierto CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md) objeto.

- O construya `CDaoDatabase` un objeto sin especificar el área de trabajo (MFC crea un objeto de área de trabajo temporal).

Para crear un nuevo Microsoft Jet (. MDB), construya un `CDaoDatabase` objeto y llame a su [create](#create) función miembro. *No* llame `Open` `Create`después de .

Para abrir una base `CDaoDatabase` de datos existente, construya un objeto y llame a su [Open](#open) función miembro.

Cualquiera de estas técnicas anexa el objeto de base de datos DAO a la colección Databases del área de trabajo y abre una conexión a los datos. Cuando, a continuación, construya [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md), [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md), o [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md) objetos para operar `CDaoDatabase` en la base de datos conectada, pase los constructores de estos objetos un puntero al objeto. Cuando termine de usar la [Close](#close) conexión, llame `CDaoDatabase` a la Close función miembro y destruir el objeto. `Close`cierra los conjuntos de registros que no haya cerrado anteriormente.

## <a name="transactions"></a>Transacciones

El procesamiento de transacciones de base de datos se proporciona en el nivel de área de trabajo; vea las funciones de miembro [BeginTrans](../../mfc/reference/cdaoworkspace-class.md#begintrans), [CommitTrans](../../mfc/reference/cdaoworkspace-class.md#committrans) y [Rollback](../../mfc/reference/cdaoworkspace-class.md#rollback) de la clase `CDaoWorkspace`.

## <a name="odbc-connections"></a>Conexiones ODBC

La forma recomendada de trabajar con orígenes de datos ODBC es adjuntar tablas externas a un Microsoft Jet (. MDB).

## <a name="collections"></a>Colecciones

Cada base de datos mantiene sus propias colecciones de objetos tabledef, querydef, recordset y relation. Class `CDaoDatabase` proporciona funciones miembro para manipular estos objetos.

> [!NOTE]
> Los objetos se almacenan en DAO, no en el objeto de base de datos MFC. MFC proporciona clases para objetos tabledef, querydef y recordset, pero no para objetos de relación.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

`CDaoDatabase`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdao.h

## <a name="cdaodatabasecantransact"></a><a name="cantransact"></a>CDaoDatabase::CanTransact

Llame a esta función miembro para determinar si la base de datos permite transacciones.

```
BOOL CanTransact();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la base de datos admite transacciones; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Las transacciones se administran en el área de trabajo de la base de datos.

## <a name="cdaodatabasecanupdate"></a><a name="canupdate"></a>CDaoDatabase::CanUpdate

Llame a esta función `CDaoDatabase` miembro para determinar si el objeto permite actualizaciones.

```
BOOL CanUpdate();
```

### <a name="return-value"></a>Valor devuelto

Distinto de `CDaoDatabase` cero si el objeto permite actualizaciones; de lo contrario 0, lo que indica que ha `CDaoDatabase` pasado TRUE en *bReadOnly* al abrir el objeto o que la propia base de datos es de solo lectura. Consulte la función miembro [Open.](#open)

### <a name="remarks"></a>Observaciones

Para obtener información acerca de la capacidad de actualización de la base de datos, vea el tema "Propiedad actualizable" en la Ayuda de DAO.

## <a name="cdaodatabasecdaodatabase"></a><a name="cdaodatabase"></a>CDaoDatabase::CDaoDatabase

Construye un objeto `CDaoDatabase`.

```
CDaoDatabase(CDaoWorkspace* pWorkspace = NULL);
```

### <a name="parameters"></a>Parámetros

*pWorkspace*<br/>
Puntero al `CDaoWorkspace` objeto que contendrá el nuevo objeto de base de datos. Si acepta el valor predeterminado de NULL, `CDaoWorkspace` el constructor crea un objeto temporal que usa el área de trabajo DAO predeterminada. Puede obtener un puntero al objeto de área de trabajo a través [del](#m_pworkspace) m_pWorkspace miembro de datos.

### <a name="remarks"></a>Observaciones

Después de construir el objeto, si va a crear un nuevo Microsoft Jet (. MDB), llame a la función miembro [Create](#create) del objeto. Si, en su lugar, está abriendo una base de datos existente, llame a la función miembro [Open](#open) del objeto.

Cuando termine con el objeto, [Close](#close) debe llamar a su `CDaoDatabase` Close función miembro y, a continuación, destruir el objeto.

Es posible que le `CDaoDatabase` resulte conveniente incrustar el objeto en la clase de documento.

> [!NOTE]
> Un `CDaoDatabase` objeto también se crea implícitamente si se abre un [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objeto sin pasar un puntero a un objeto existente. `CDaoDatabase` Este objeto de base de datos se cierra al cerrar el objeto de conjunto de registros.

## <a name="cdaodatabaseclose"></a><a name="close"></a>CDaoDatabase::Cerrar

Llame a esta función miembro para desconectarse de una base de datos y cerrar los conjuntos de registros abiertos, tabledefs y querydefs asociados a la base de datos.

```
virtual void Close();
```

### <a name="remarks"></a>Observaciones

Es recomendable cerrar estos objetos usted mismo antes de llamar a esta función miembro. Al `CDaoDatabase` cerrar un objeto, se quita de la colección Databases del área de [trabajo](../../mfc/reference/cdaoworkspace-class.md)asociada. Dado `Close` que no `CDaoDatabase` destruye el objeto, puede reutilizar el objeto abriendo la misma base de datos o una base de datos diferente.

> [!CAUTION]
> Llame a la [Update](../../mfc/reference/cdaorecordset-class.md#update) función miembro (si `Close` hay ediciones pendientes) y la función miembro en todos los objetos de conjunto de registros abiertos antes de cerrar una base de datos. Si sale de una función que `CDaoDatabase` declara [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) u objetos en la pila, la base de datos se cierra, se pierden los cambios no guardados, se revierten todas las transacciones pendientes y se pierden las ediciones pendientes de los datos.

> [!CAUTION]
> Si intenta cerrar un objeto de base de datos mientras los objetos de conjunto de registros están abiertos, o si intenta cerrar un objeto de área de trabajo mientras están abiertos los objetos de base de datos que pertenecen a ese espacio de trabajo específico, esos objetos de conjunto de registros se cerrarán y se revertirán las actualizaciones o ediciones pendientes. Si intenta cerrar un objeto de área de trabajo mientras los objetos de base de datos que pertenecen a él están abiertos, la operación cierra todos los objetos de base de datos que pertenecen a ese objeto de área de trabajo específico, lo que puede dar lugar a que se cierren objetos de conjunto de registros no cerrados. Si no cierra el objeto de base de datos, MFC notifica un error de aserción en compilaciones de depuración.

Si el objeto de base de datos se define fuera del ámbito de una función y sale de la función sin cerrarla, el objeto de base de datos permanecerá abierto hasta que se cierre explícitamente o el módulo en el que se define esté fuera del ámbito.

## <a name="cdaodatabasecreate"></a><a name="create"></a>CDaoDatabase::Create

Para crear un nuevo Microsoft Jet (. MDB), llame a esta función `CDaoDatabase` miembro después de construir un objeto.

```
virtual void Create(
    LPCTSTR lpszName,
    LPCTSTR lpszLocale = dbLangGeneral,
    int dwOptions = 0);
```

### <a name="parameters"></a>Parámetros

*lpszName*<br/>
Expresión de cadena que es el nombre del archivo de base de datos que está creando. Puede ser la ruta de acceso completa\\y el nombre de archivo, como "C: .MYDB. MDB". Debe proporcionar un nombre. Si no proporciona una extensión de nombre de archivo, . Se anexa el BmD. Si la red es compatible con la convención de nomenclatura uniforme\\\\\\(UNC), también puede especificar una ruta de acceso de red, como por ejemplo, "MYSERVER"\\\\\\. Sólo Microsoft Jet (. MDB) archivos de base de datos se pueden crear mediante esta función miembro. (Se requieren barras diagonales inversas\\dobles en literales de cadena porque " " es el carácter de escape C++.)

*lpszLocale*<br/>
Expresión de cadena utilizada para especificar el orden de intercalación para crear la base de datos. El valor predeterminado es `dbLangGeneral`. Los valores posibles son:

- `dbLangGeneral`Inglés, alemán, francés, portugués, italiano y español moderno

- `dbLangArabic`Árabe

- `dbLangCyrillic`Ruso

- `dbLangCzech`Checo

- `dbLangDutch`Holandés

- `dbLangGreek`Griego

- `dbLangHebrew`Hebreo

- `dbLangHungarian`Húngaro

- `dbLangIcelandic`Islandés

- `dbLangNordic`Idiomas nórdicos (solo Microsoft Jet database engine versión 1.0)

- `dbLangNorwdan`Noruego y danés

- `dbLangPolish`Polaco

- `dbLangSpanish`Español Tradicional

- `dbLangSwedfin`Sueco y finlandés

- `dbLangTurkish`Turco

*dwOptions*<br/>
Entero que indica una o más opciones. Los valores posibles son:

- `dbEncrypt`Cree una base de datos cifrada.

- `dbVersion10`Cree una base de datos con la versión 1.0 de la base de datos de Microsoft Jet.

- `dbVersion11`Cree una base de datos con la versión 1.1 de la base de datos de Microsoft Jet.

- `dbVersion20`Cree una base de datos con la versión 2.0 de la base de datos de Microsoft Jet.

- `dbVersion30`Cree una base de datos con la versión 3.0 de la base de datos de Microsoft Jet.

Si omite la constante de cifrado, se crea una base de datos sin cifrar. Solo puede especificar una constante de versión. Si omite una constante de versión, se crea una base de datos que utiliza la versión 3.0 de la base de datos de Microsoft Jet.

> [!CAUTION]
> Si una base de datos no está cifrada, es posible, incluso si implementa la seguridad de usuario/contraseña, leer directamente el archivo de disco binario que constituye la base de datos.

### <a name="remarks"></a>Observaciones

`Create`crea el archivo de base de datos y el objeto de base de datos DAO subyacente e inicializa el objeto C++. El objeto se anexa a la colección Databases del área de trabajo asociada. El objeto de base de datos está en un estado abierto; no llame `Open*` `Create`después de .

> [!NOTE]
> Con `Create`, solo puede crear Microsoft Jet (. MDB). No puede crear bases de datos ISAM ni bases de datos ODBC.

## <a name="cdaodatabasecreaterelation"></a><a name="createrelation"></a>CDaoDatabase::CreateRelation

Llame a esta función miembro para establecer una relación entre uno o varios campos de una tabla principal de la base de datos y uno o varios campos de una tabla externa (otra tabla de la base de datos).

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
El nombre único del objeto de relación. El nombre debe comenzar con una letra y puede contener un máximo de 40 caracteres. Puede incluir números y caracteres de subrayado, pero no puede incluir puntuación ni espacios.

*lpszTable*<br/>
El nombre de la tabla principal de la relación. Si la tabla no existe, MFC produce una excepción de tipo [CDaoException](../../mfc/reference/cdaoexception-class.md).

*lpszForeignTable*<br/>
El nombre de la tabla externa en la relación. Si la tabla no existe, MFC produce `CDaoException`una excepción de tipo .

*lAttributes*<br/>
Valor largo que contiene información sobre el tipo de relación. Puede utilizar este valor para aplicar la integridad referencial, entre otras cosas. Puede utilizar el operador OR bit a bit ( **&#124;**) para combinar cualquiera de los siguientes valores (siempre y cuando la combinación tenga sentido):

- `dbRelationUnique`La relación es uno a uno.

- `dbRelationDontEnforce`La relación no se aplica (sin integridad referencial).

- `dbRelationInherited`La relación existe en una base de datos no actual que contiene las dos tablas adjuntas.

- `dbRelationUpdateCascade`Las actualizaciones se conectarán en cascada (para obtener más información sobre las cascadas, consulte Comentarios).

- `dbRelationDeleteCascade`Las eliminaciones se conectarán en cascada.

*lpszField*<br/>
Puntero a una cadena terminada en null que contiene el nombre de un campo de la tabla principal (denominado por *lpszTable*).

*lpszForeignField*<br/>
Puntero a una cadena terminada en null que contiene el nombre de un campo de la tabla externa (denominado por *lpszForeignTable*).

*relinfo*<br/>
Una referencia a un [CDaoRelationInfo](../../mfc/reference/cdaorelationinfo-structure.md) objeto que contiene información sobre la relación que desea crear.

### <a name="remarks"></a>Observaciones

La relación no puede implicar una consulta o una tabla adjunta de una base de datos externa.

Utilice la primera versión de la función cuando la relación implique un campo en cada una de las dos tablas. Utilice la segunda versión cuando la relación implique varios campos. El número máximo de campos en una relación es 14.

Esta acción crea un objeto de relación DAO subyacente, pero se trata de un detalle `CDaoDatabase`de implementación de MFC, ya que la encapsulación de objetos de relación de MFC está contenida en la clase . MFC no proporciona una clase para las relaciones.

Si establece los atributos del objeto de relación para activar las operaciones en cascada, el motor de base de datos actualiza o elimina automáticamente los registros de una o varias tablas cuando se realizan cambios en las tablas de claves principales relacionadas.

Por ejemplo, supongamos que establece una relación de eliminación en cascada entre una tabla Customers y una tabla Orders. Al eliminar registros de la tabla Clientes, también se eliminan los registros de la tabla Pedidos relacionados con ese cliente. Además, si establece relaciones de eliminación en cascada entre la tabla Pedidos y otras tablas, los registros de esas tablas se eliminan automáticamente al eliminar registros de la tabla Clientes.

Para obtener información relacionada, vea el tema "Método CreateRelation" en la Ayuda de DAO.

## <a name="cdaodatabasedeletequerydef"></a><a name="deletequerydef"></a>CDaoDatabase::DeleteQueryDef

Llame a esta función miembro para eliminar la definición de consulta especificada (consulta guardada) de la `CDaoDatabase` colección QueryDefs del objeto.

```
void DeleteQueryDef(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parámetros

*lpszName*<br/>
El nombre de la consulta guardada que se ha de eliminar.

### <a name="remarks"></a>Observaciones

Después, esa consulta ya no se define en la base de datos.

Para obtener información sobre la creación de objetos de definición de consulta, vea [clase CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md). Un objeto querydef se asocia `CDaoDatabase` a un `CDaoQueryDef` objeto determinado al construir el objeto, pasándole un puntero al objeto de base de datos.

## <a name="cdaodatabasedeleterelation"></a><a name="deleterelation"></a>CDaoDatabase::DeleteRelation

Llame a esta función miembro para eliminar una relación existente de la colección Relations del objeto de base de datos.

```
void DeleteRelation(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parámetros

*lpszName*<br/>
El nombre de la relación que se va a eliminar.

### <a name="remarks"></a>Observaciones

Después, la relación ya no existe.

Para obtener información relacionada, vea el tema "Método de eliminación" en la Ayuda de DAO.

## <a name="cdaodatabasedeletetabledef"></a><a name="deletetabledef"></a>CDaoDatabase::DeleteTableDef

Llame a esta función miembro para eliminar la `CDaoDatabase` tabla especificada y todos sus datos de la colección TableDefs del objeto.

```
void DeleteTableDef(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parámetros

*lpszName*<br/>
El nombre de la tabla que se ha eliminado.

### <a name="remarks"></a>Observaciones

Después, esa tabla ya no se define en la base de datos.

> [!NOTE]
> Tenga mucho cuidado de no eliminar las tablas del sistema.

Para obtener información sobre la creación de objetos de base de tabla, vea [clase CDaoTableDef](../../mfc/reference/cdaotabledef-class.md). Un objeto tabledef se asocia `CDaoDatabase` a un `CDaoTableDef` objeto determinado al construir el objeto, pasándole un puntero al objeto de base de datos.

Para obtener información relacionada, vea el tema "Método de eliminación" en la Ayuda de DAO.

## <a name="cdaodatabaseexecute"></a><a name="execute"></a>CDaoDatabase::Execute

Llame a esta función miembro para ejecutar una consulta de acción o ejecutar una instrucción SQL en la base de datos.

```
void Execute(
    LPCTSTR lpszSQL,
    int nOptions = dbFailOnError);
```

### <a name="parameters"></a>Parámetros

*lpszSQL*<br/>
Puntero a una cadena terminada en null que contiene un comando SQL válido que se va a ejecutar.

*nOpciones*<br/>
Entero que especifica opciones relacionadas con la integridad de la consulta. Puede utilizar el operador OR bit a bit ( **&#124;**) para combinar cualquiera de las siguientes `dbInconsistent` constantes (siempre que la combinación tenga sentido, por ejemplo, no se combinaría con `dbConsistent`):

- `dbDenyWrite`Denegar el permiso de escritura a otros usuarios.

- `dbInconsistent`(Predeterminado) Actualizaciones incoherentes.

- `dbConsistent`Actualizaciones coherentes.

- `dbSQLPassThrough`Paso a través de SQL. Hace que la instrucción SQL se pase a un origen de datos ODBC para su procesamiento.

- `dbFailOnError`Revierta las actualizaciones si se produce un error.

- `dbSeeChanges`Genere un error en tiempo de ejecución si otro usuario está cambiando los datos que está editando.

> [!NOTE]
> Si `dbInconsistent` ambos `dbConsistent` y se incluyen o si no se incluye ninguno, el resultado es el valor predeterminado. Para obtener una explicación de estas constantes, vea el tema "Método de ejecución" en la Ayuda de DAO.

### <a name="remarks"></a>Observaciones

`Execute`solo funciona para consultas de acción o consultas de paso a través de SQL que no devuelven resultados. No funciona para consultas seleccionadas, que devuelven registros.

Para obtener una definición e información sobre las consultas de acción, consulte los temas "Consulta de acción" y "Método de ejecución" en la Ayuda de DAO.

> [!TIP]
> Dada una instrucción SQL sintácticamente correcta `Execute` y los permisos adecuados, la función miembro no producirá un error aunque no se pueda modificar o eliminar una sola fila. Por lo tanto, utilice siempre la `dbFailOnError` opción cuando utilice la `Execute` función miembro para ejecutar una consulta de actualización o eliminación. Esta opción hace que MFC produzca una excepción de tipo [CDaoException](../../mfc/reference/cdaoexception-class.md) y revierte todos los cambios correctos si alguno de los registros afectados está bloqueado y no se puede actualizar o eliminar. Tenga en cuenta `GetRecordsAffected` que siempre puede llamar para ver cuántos registros se vieron afectados.

Llame a la [GetRecordsAffected](#getrecordsaffected) función miembro del objeto de base `Execute` de datos para determinar el número de registros afectados por la llamada más reciente. Por ejemplo, `GetRecordsAffected` devuelve información sobre el número de registros eliminados, actualizados o insertados al ejecutar una consulta de acción. El recuento devuelto no reflejará los cambios en las tablas relacionadas cuando las actualizaciones o eliminaciones en cascada estén en vigor.

`Execute`no devuelve un conjunto de registros. El `Execute` uso de una consulta que selecciona registros `CDaoException`hace que MFC produzca una excepción de tipo . (No hay `ExecuteSQL` ninguna función `CDatabase::ExecuteSQL`miembro análoga a .)

## <a name="cdaodatabasegetconnect"></a><a name="getconnect"></a>CDaoDatabase::GetConnect

Llame a esta función miembro para `CDaoDatabase` recuperar la cadena de conexión utilizada para conectar el objeto a una base de datos ODBC o ISAM.

```
CString GetConnect();
```

### <a name="return-value"></a>Valor devuelto

La cadena de conexión si [Open](#open) se ha llamado correctamente en un origen de datos ODBC; de lo contrario, una cadena vacía. Para un Microsoft Jet (. MDB), la cadena siempre está vacía a menos `dbSQLPassThrough` que se establezca para su uso con la opción utilizada con la [función](#execute) miembro Execute o utilizada para abrir un conjunto de registros.

### <a name="remarks"></a>Observaciones

La cadena proporciona información sobre el origen de una base de datos abierta o una base de datos utilizada en una consulta de paso a través. La cadena de conexión se compone de un especificador de tipo de base de datos y cero o más parámetros separados por punto y coma.

> [!NOTE]
> El uso de las clases DAO de MFC para conectarse a un origen de datos a través de ODBC es menos eficaz que conectarse a través de una tabla adjunta.

> [!NOTE]
> La cadena de conexión se utiliza para pasar información adicional a ODBC y a determinados controladores ISAM según sea necesario. No se utiliza para . Bases de datos MDB. Para las tablas base de base de base de base de base de base de Microsoft Jet, la cadena de conexión es una cadena vacía ("") excepto cuando se usa para una consulta de paso a través de SQL como se describe en Valor de devolución anterior.

Consulte el [Open](#open) función miembro para obtener una descripción de cómo se crea la cadena de conexión. Una vez establecida la cadena `Open` de conexión en la llamada, más adelante puede usarla para comprobar la configuración para determinar el tipo, la ruta de acceso, el identificador de usuario, la contraseña o el origen de datos ODBC de la base de datos.

## <a name="cdaodatabasegetname"></a><a name="getname"></a>CDaoDatabase::GetName

Llame a esta función miembro para recuperar el nombre de la base de datos abierta actualmente, que es el nombre de un archivo de base de datos existente o el nombre de un origen de datos ODBC registrado.

```
CString GetName();
```

### <a name="return-value"></a>Valor devuelto

La ruta de acceso completa y el nombre de archivo de la base de datos si se realiza correctamente; de lo contrario, un [CString](../../atl-mfc-shared/reference/cstringt-class.md)vacío .

### <a name="remarks"></a>Observaciones

Si la red es compatible con la convención de nomenclatura uniforme (UNC),\\también\\puede especificar\\una ruta de acceso de red, por ejemplo, " .\\\\\\ MDB". (Se requieren barras diagonales inversas\\dobles en literales de cadena porque " " es el carácter de escape C++.)

Por ejemplo, es posible que desee mostrar este nombre en un encabezado. Si se produce un error mientras se recupera el nombre, MFC produce una excepción de tipo [CDaoException](../../mfc/reference/cdaoexception-class.md).

> [!NOTE]
> Para obtener un mejor rendimiento cuando se tiene acceso a bases de datos externas, se recomienda adjuntar tablas de base de datos externas a una base de datos de Microsoft Jet (. MDB) en lugar de conectarse directamente al origen de datos.

El tipo de base de datos se indica mediante el archivo o directorio al que apunta la ruta de acceso, como se indica a continuación:

|Pathname apunta a..|Tipo de base de datos|
|--------------------------|-------------------|
|. Archivo MDB|Base de datos Microsoft Jet (Microsoft Access)|
|Directorio que contiene . Archivo(s) DBF (s)|base de datos dBASE|
|Directorio que contiene . Archivo XLS|Base de datos de Microsoft Excel|
|Directorio que contiene . Archivos PDX (s)|Base de datos Paradox|
|Directorio que contiene archivos de base de datos de texto con el formato adecuado|Base de datos de formato sólano de texto|

Para bases de datos ODBC como SQL Server y Oracle, la cadena de conexión de la base de datos identifica un nombre de origen de datos (DSN) registrado por ODBC.

## <a name="cdaodatabasegetquerydefcount"></a><a name="getquerydefcount"></a>CDaoDatabase::GetQueryDefCount

Llame a esta función miembro para recuperar el número de consultas definidas en la colección QueryDefs de la base de datos.

```
short GetQueryDefCount();
```

### <a name="return-value"></a>Valor devuelto

El número de consultas definidas en la base de datos.

### <a name="remarks"></a>Observaciones

`GetQueryDefCount`es útil si necesita recorrer en bucle todas las definiciones de consulta en el QueryDefs colección. Para obtener información sobre una consulta determinada de la colección, vea [GetQueryDefInfo](#getquerydefinfo).

## <a name="cdaodatabasegetquerydefinfo"></a><a name="getquerydefinfo"></a>CDaoDatabase::GetQueryDefInfo

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
El índice de la consulta predefinida en la colección QueryDefs de la base de datos, para la búsqueda por índice.

*querydefinfo*<br/>
Una referencia a un [CDaoQueryDefInfo](../../mfc/reference/cdaoquerydefinfo-structure.md) objeto que devuelve la información solicitada.

*dwInfoOptions*<br/>
Opciones que especifican qué información sobre el conjunto de registros se va a recuperar. Las opciones disponibles se enumeran aquí junto con lo que hacen que la función devuelva sobre el conjunto de registros:

- AFX_DAO_PRIMARY_INFO (predeterminado), escriba

- AFX_DAO_SECONDARY_INFO información principal más: Fecha de creación, Fecha de la última actualización, Registros de devoluciones, Actualizable

- AFX_DAO_ALL_INFO información principal y secundaria más: SQL, Connect, ODBCTimeout

*lpszName*<br/>
Cadena que contiene el nombre de una consulta definida en la base de datos, para la búsqueda por nombre.

### <a name="remarks"></a>Observaciones

Se proporcionan dos versiones de la función para que pueda seleccionar una consulta por índice en la colección QueryDefs de la base de datos o por el nombre de la consulta.

Para obtener una descripción de la información devuelta en *querydefinfo*, vea el [CDaoQueryDefInfo](../../mfc/reference/cdaoquerydefinfo-structure.md) estructura. Esta estructura tiene miembros que corresponden a los elementos de información enumerados anteriormente en la descripción de *dwInfoOptions*. Si solicita un nivel de información, también obtendrá cualquier nivel de información anterior.

## <a name="cdaodatabasegetquerytimeout"></a><a name="getquerytimeout"></a>CDaoDatabase::GetQueryTimeout

Llame a esta función miembro para recuperar el número actual de segundos para permitir antes de que se agota el tiempo de espera las operaciones posteriores en la base de datos conectada.

```
short GetQueryTimeout();
```

### <a name="return-value"></a>Valor devuelto

Entero corto que contiene el valor de tiempo de espera en segundos.

### <a name="remarks"></a>Observaciones

Es posible que se agota el tiempo de espera de una operación debido a problemas de acceso a la red, tiempo excesivo de procesamiento de consultas, etc. Mientras la configuración está en vigor, afecta a todas las operaciones open, `CDaoDatabase` add new, update y delete en cualquier conjunto de registros asociado a este objeto. Puede cambiar la configuración de tiempo de espera actual llamando a [SetQueryTimeout](#setquerytimeout). Cambiar el valor de tiempo de espera de consulta para un conjunto de registros después de la apertura no cambia el valor del conjunto de registros. Por ejemplo, las operaciones [Move](../../mfc/reference/cdaorecordset-class.md#move) posteriores no utilizan el nuevo valor. El valor predeterminado se establece inicialmente cuando se inicializa el motor de base de datos.

El valor predeterminado para los tiempos de espera de consulta se toma del registro de Windows. Si no hay ninguna configuración del Registro, el valor predeterminado es 60 segundos. No todas las bases de datos admiten la capacidad de establecer un valor de tiempo de espera de consulta. Si establece un valor de tiempo de espera de consulta de 0, no se produce ningún tiempo de espera; y la comunicación con la base de datos puede dejar de responder. Este comportamiento puede ser útil durante el desarrollo. Si se produce un error en la llamada, MFC produce una excepción de tipo [CDaoException](../../mfc/reference/cdaoexception-class.md).

Para obtener información relacionada, vea el tema "Propiedad QueryTimeout" en la Ayuda de DAO.

## <a name="cdaodatabasegetrecordsaffected"></a><a name="getrecordsaffected"></a>CDaoDatabase::GetRecordsAffected

Llame a esta función miembro para determinar el número de registros afectados por la llamada más reciente de la [Execute](#execute) función miembro.

```
long GetRecordsAffected();
```

### <a name="return-value"></a>Valor devuelto

Entero largo que contiene el número de registros afectados.

### <a name="remarks"></a>Observaciones

El valor devuelto incluye el número de registros eliminados, `Execute`actualizados o insertados por una consulta de acción que se ejecuta con . El recuento devuelto no reflejará los cambios en las tablas relacionadas cuando las actualizaciones o eliminaciones en cascada estén en vigor.

Para obtener información relacionada, vea el tema "Propiedad RecordsAffected" en la Ayuda de DAO.

## <a name="cdaodatabasegetrelationcount"></a><a name="getrelationcount"></a>CDaoDatabase::GetRelationCount

Llame a esta función miembro para obtener el número de relaciones definidas entre las tablas de la base de datos.

```
short GetRelationCount();
```

### <a name="return-value"></a>Valor devuelto

El número de relaciones definidas entre las tablas de la base de datos.

### <a name="remarks"></a>Observaciones

`GetRelationCount`es útil si necesita recorrer en bucle todas las relaciones definidas en la colección Relaciones de la base de datos. Para obtener información sobre una relación determinada de la colección, vea [GetRelationInfo](#getrelationinfo).

Para ilustrar el concepto de una relación, considere una tabla Suppliers y una tabla Products, que podrían tener una relación de uno a varios. En esta relación, un proveedor puede suministrar más de un producto. Otras relaciones son uno a uno y muchos a muchos.

## <a name="cdaodatabasegetrelationinfo"></a><a name="getrelationinfo"></a>CDaoDatabase::GetRelationInfo

Llame a esta función miembro para obtener información sobre una relación especificada en la colección Relations de la base de datos.

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
El índice del objeto de relación en la colección Relations de la base de datos, para la búsqueda por índice.

*relinfo*<br/>
Una referencia a un [CDaoRelationInfo](../../mfc/reference/cdaorelationinfo-structure.md) objeto que devuelve la información solicitada.

*dwInfoOptions*<br/>
Opciones que especifican qué información sobre la relación que se va a recuperar. Las opciones disponibles se enumeran aquí junto con lo que hacen que la función devuelva sobre la relación:

- AFX_DAO_PRIMARY_INFO (predeterminado), tabla, tabla externa

- Atributos AFX_DAO_SECONDARY_INFO, Información de campo

La información de campo es un [CDaoRelationFieldInfo](../../mfc/reference/cdaorelationfieldinfo-structure.md) objeto que contiene los campos de la tabla principal implicada en la relación.

*lpszName*<br/>
Cadena que contiene el nombre del objeto de relación, para la búsqueda por nombre.

### <a name="remarks"></a>Observaciones

Dos versiones de esta función proporcionan acceso por índice o por nombre. Para obtener una descripción de la información devuelta en *relinfo*, vea el [CDaoRelationInfo](../../mfc/reference/cdaorelationinfo-structure.md) estructura. Esta estructura tiene miembros que corresponden a los elementos de información enumerados anteriormente en la descripción de *dwInfoOptions*. Si solicita información en un nivel, también obtendrá información en cualquier nivel anterior.

> [!NOTE]
> Si establece los atributos del objeto de`dbRelationUpdateCascades` `dbRelationDeleteCascades`relación para activar operaciones en cascada ( o ), el motor de base de datos de Microsoft Jet actualiza o elimina automáticamente los registros de una o varias tablas cuando se realizan cambios en las tablas de claves principales relacionadas. Por ejemplo, supongamos que establece una relación de eliminación en cascada entre una tabla Customers y una tabla Orders. Al eliminar registros de la tabla Clientes, también se eliminan los registros de la tabla Pedidos relacionados con ese cliente. Además, si establece relaciones de eliminación en cascada entre la tabla Pedidos y otras tablas, los registros de esas tablas se eliminan automáticamente al eliminar registros de la tabla Clientes.

## <a name="cdaodatabasegettabledefcount"></a><a name="gettabledefcount"></a>CDaoDatabase::GetTableDefCount

Llame a esta función miembro para recuperar el número de tablas definidas en la base de datos.

```
short GetTableDefCount();
```

### <a name="return-value"></a>Valor devuelto

El número de definiciones de tabla definidas en la base de datos.

### <a name="remarks"></a>Observaciones

`GetTableDefCount`es útil si necesita recorrer en bucle todas las bases de datos de tablas en la colección TableDefs de la base de datos. Para obtener información sobre una tabla determinada de la colección, vea [GetTableDefInfo](#gettabledefinfo).

## <a name="cdaodatabasegettabledefinfo"></a><a name="gettabledefinfo"></a>CDaoDatabase::GetTableDefInfo

Llame a esta función miembro para obtener varios tipos de información sobre una tabla definida en la base de datos.

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
El índice del objeto tabledef de la colección TableDefs de la base de datos, para la búsqueda por índice.

*tabledefinfo*<br/>
Una referencia a un [CDaoTableDefInfo](../../mfc/reference/cdaotabledefinfo-structure.md) objeto que devuelve la información solicitada.

*dwInfoOptions*<br/>
Opciones que especifican qué información sobre la tabla se va a recuperar. Las opciones disponibles se enumeran aquí junto con lo que hacen que la función devuelva sobre la relación:

- AFX_DAO_PRIMARY_INFO (predeterminado), Actualizable, Atributos

- AFX_DAO_SECONDARY_INFO Información principal más: Fecha de creación, Fecha de la última actualización, Nombre de la tabla de origen, Conectar

- AFX_DAO_ALL_INFO información primaria y secundaria más: regla de validación, texto de validación, recuento de registros

*lpszName*<br/>
El nombre del objeto tabledef, para la búsqueda por nombre.

### <a name="remarks"></a>Observaciones

Se proporcionan dos versiones de la función para que pueda seleccionar una tabla por índice en la colección TableDefs de la base de datos o por el nombre de la tabla.

Para obtener una descripción de la información devuelta en *tabledefinfo*, vea el [CDaoTableDefInfo](../../mfc/reference/cdaotabledefinfo-structure.md) estructura. Esta estructura tiene miembros que corresponden a los elementos de información enumerados anteriormente en la descripción de *dwInfoOptions*. Si solicita información en un nivel, también obtendrá información para cualquier nivel anterior.

> [!NOTE]
> La opción AFX_DAO_ALL_INFO proporciona información que puede ser lenta de obtener. En este caso, contar los registros de la tabla podría llevar mucho tiempo si hay muchos registros.

## <a name="cdaodatabasegetversion"></a><a name="getversion"></a>CDaoDatabase::GetVersion

Llame a esta función miembro para determinar la versión del archivo de base de datos de Microsoft Jet.

```
CString GetVersion();
```

### <a name="return-value"></a>Valor devuelto

Un [CString](../../atl-mfc-shared/reference/cstringt-class.md) que indica la versión del archivo de base de datos asociado con el objeto.

### <a name="remarks"></a>Observaciones

El valor devuelto representa el número de versión con el formato "major.minor"; por ejemplo, "3.0". El número de versión del producto (por ejemplo, 3.0) consta del número de versión (3), un punto y el número de versión (0). Las versiones hasta la fecha son 1.0, 1.1, 2.0 y 3.0.

Para obtener información relacionada, vea el tema "Propiedad de versión" en la Ayuda de DAO.

## <a name="cdaodatabaseisopen"></a><a name="isopen"></a>CDaoDatabase::IsOpen

Llame a esta función `CDaoDatabase` miembro para determinar si el objeto está abierto actualmente en una base de datos.

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de `CDaoDatabase` cero si el objeto está abierto actualmente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

## <a name="cdaodatabasem_pdaodatabase"></a><a name="m_pdaodatabase"></a>CDaoDatabase::m_pDAODatabase

Contiene un puntero a la interfaz OLE `CDaoDatabase` para el objeto de base de datos DAO subyacente al objeto.

### <a name="remarks"></a>Observaciones

Utilice este puntero si necesita acceder a la interfaz DAO directamente.

Para obtener información sobre cómo llamar directamente a DAO, consulte [la Nota técnica 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).

## <a name="cdaodatabasem_pworkspace"></a><a name="m_pworkspace"></a>CDaoDatabase::m_pWorkspace

Contiene un puntero al objeto [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md) que contiene el objeto de base de datos.

### <a name="remarks"></a>Observaciones

Utilice este puntero si necesita tener acceso al área de trabajo directamente, por ejemplo, para obtener punteros a otros objetos de base de datos en la colección Databases del área de trabajo.

## <a name="cdaodatabaseopen"></a><a name="open"></a>CDaoDatabase::Open

Debe llamar a esta función miembro `CDaoDatabase` para inicializar un objeto recién construido que representa una base de datos existente.

```
virtual void Open(
    LPCTSTR lpszName,
    BOOL bExclusive = FALSE,
    BOOL bReadOnly = FALSE,
    LPCTSTR lpszConnect = _T(""));
```

### <a name="parameters"></a>Parámetros

*lpszName*<br/>
Expresión de cadena que es el nombre de un Microsoft Jet existente (. MDB). Si el nombre de archivo tiene una extensión, es necesario. Si la red es compatible con la convención de nomenclatura uniforme\\\\\\(UNC), también puede especificar una ruta de acceso de red, como por ejemplo, "MYSERVER"\\\\\\. MDB". (Se requieren barras diagonales inversas\\dobles en literales de cadena porque " " es el carácter de escape C++.)

Algunas consideraciones se aplican al usar *lpszName*. Si:

- Hace referencia a una base de datos que ya está abierta para el acceso exclusivo de otro usuario, MFC produce una excepción de tipo [CDaoException](../../mfc/reference/cdaoexception-class.md). Atrape esa excepción para que el usuario sepa que la base de datos no está disponible.

- Es una cadena vacía ("") y *lpszConnect* es "ODBC;", se muestra un cuadro de diálogo que enumera todos los nombres de origen de datos ODBC registrados para que el usuario pueda seleccionar una base de datos. Debe evitar las conexiones directas a orígenes de datos ODBC; utilizar una tabla adjunta en su lugar.

- De lo contrario, no hace referencia a una base de datos `CDaoException`existente o un nombre de origen de datos ODBC válido, MFC produce una excepción de tipo .

> [!NOTE]
> Para obtener más información acerca de los códigos de error DAO, consulte el DAOERR. Archivo H. Para obtener información relacionada, consulte el tema "Errores de acceso a datos intercambiables" en la Ayuda de DAO.

*bExclusive*<br/>
Un valor booleano que es TRUE si la base de datos se va a abrir para el acceso exclusivo (no compartido) y FALSE si la base de datos se va a abrir para el acceso compartido. Si omite este argumento, la base de datos se abre para el acceso compartido.

*bReadOnly*<br/>
Un valor booleano que es TRUE si la base de datos se va a abrir para el acceso de solo lectura y FALSE si la base de datos se va a abrir para el acceso de lectura y escritura. Si omite este argumento, la base de datos se abre para el acceso de lectura y escritura. Todos los conjuntos de registros dependientes heredan este atributo.

*lpszConnect*<br/>
Expresión de cadena utilizada para abrir la base de datos. Esta cadena constituye los argumentos de conexión ODBC. Debe proporcionar los argumentos exclusivos y de solo lectura para proporcionar una cadena de origen. Si la base de datos es una base de datos de Microsoft Jet (. MDB), esta cadena está vacía (""). La sintaxis del valor predeterminado , **_T**("") proporciona portabilidad para las compilaciones Unicode y ANSI de la aplicación.

### <a name="remarks"></a>Observaciones

`Open`asocia la base de datos con el objeto DAO subyacente. No se puede utilizar el objeto de base de datos para construir objetos recordset, tabledef o querydef hasta que se inicialice. `Open`anexa el objeto de base de datos a la colección Databases del área de trabajo asociada.

Utilice los parámetros de la siguiente manera:

- Si está abriendo un Microsoft Jet (. MDB), utilice el parámetro *lpszName* y pase una cadena vacía para el parámetro *lpszConnect* o pase una cadena de contraseña con el formato "; PWD-contraseña" si la base de datos está protegida con contraseña (. Bases de datos MDB solamente).

- Si va a abrir un origen de datos ODBC, pase una cadena de conexión ODBC válida en *lpszConnect* y una cadena vacía en *lpszName*.

Para obtener información relacionada, vea el tema "Método OpenDatabase" en la Ayuda de DAO.

> [!NOTE]
> Para obtener un mejor rendimiento al acceder a bases de datos externas, incluidas las bases de datos ISAM y los orígenes de datos ODBC, se recomienda adjuntar tablas de base de datos externas a una base de datos de motor de Microsoft Jet (. MDB) en lugar de conectarse directamente al origen de datos.

Es posible que un intento de conexión apadezca el tiempo de espera si, por ejemplo, el host DBMS no está disponible. Si se produce `Open` un error en el intento de conexión, produce una excepción de tipo [CDaoException](../../mfc/reference/cdaoexception-class.md).

Las observaciones restantes solo se aplican a las bases de datos ODBC:

Si la base de datos es `Open` una base de datos ODBC y los parámetros de la llamada no contienen suficiente información para realizar la conexión, el controlador ODBC abre un cuadro de diálogo para obtener la información necesaria del usuario. Cuando se `Open`llama a , la cadena de conexión, *lpszConnect*, se almacena de forma privada y está disponible mediante una llamada a la [GetConnect](#getconnect) función miembro.

Si lo desea, puede abrir su propio `Open` cuadro de diálogo antes de llamar para obtener información del usuario, `Open`como una contraseña, y luego agregar esa información a la cadena de conexión que pasa a . O puede que desee guardar la cadena de conexión que pasa (quizás en el `Open` registro `CDaoDatabase` de Windows) para que pueda reutilizarla la próxima vez que la aplicación llame a un objeto.

También puede utilizar la cadena de conexión para varios `CDaoDatabase` niveles de autorización de inicio de sesión (cada uno para un objeto diferente) o para transmitir otra información específica de la base de datos.

## <a name="cdaodatabasesetquerytimeout"></a><a name="setquerytimeout"></a>CDaoDatabase::SetQueryTimeout

Llame a esta función miembro para invalidar el número predeterminado de segundos para permitir antes de las operaciones posteriores en el tiempo de espera de la base de datos conectada.

```
void SetQueryTimeout(short nSeconds);
```

### <a name="parameters"></a>Parámetros

*nSeconds*<br/>
El número de segundos que se debe permitir antes de que se agota el tiempo de espera de un intento de consulta.

### <a name="remarks"></a>Observaciones

Una operación puede agotar el tiempo de espera debido a problemas de acceso a la red, tiempo excesivo de procesamiento de consultas, etc. Llame `SetQueryTimeout` antes de abrir el conjunto de registros o antes de llamar a las funciones miembro [AddNew](../../mfc/reference/cdaorecordset-class.md#addnew), [Update](../../mfc/reference/cdaorecordset-class.md#update)o [Delete](../../mfc/reference/cdaorecordset-class.md#delete) del conjunto de registros si desea cambiar el valor de tiempo de espera de consulta. La configuración afecta a `Update`todas `Delete` las llamadas [posteriores](../../mfc/reference/cdaorecordset-class.md#open) `CDaoDatabase` Open , `AddNew`, , y a los conjuntos de registros asociados a este objeto. Cambiar el valor de tiempo de espera de consulta para un conjunto de registros después de la apertura no cambia el valor del conjunto de registros. Por ejemplo, las operaciones [Move](../../mfc/reference/cdaorecordset-class.md#move) posteriores no utilizan el nuevo valor.

El valor predeterminado para los tiempos de espera de consulta es 60 segundos. No todas las bases de datos admiten la capacidad de establecer un valor de tiempo de espera de consulta. Si establece un valor de tiempo de espera de consulta de 0, no se produce ningún tiempo de espera; la comunicación con la base de datos puede dejar de responder. Este comportamiento puede ser útil durante el desarrollo.

Para obtener información relacionada, vea el tema "Propiedad QueryTimeout" en la Ayuda de DAO.

## <a name="see-also"></a>Consulte también

[Clase CObject](../../mfc/reference/cobject-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clase CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md)<br/>
[Clase CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)<br/>
[CDaoTableDef (clase)](../../mfc/reference/cdaotabledef-class.md)<br/>
[Clase CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)<br/>
[Clase CDatabase](../../mfc/reference/cdatabase-class.md)<br/>
[Clase CDaoException](../../mfc/reference/cdaoexception-class.md)
