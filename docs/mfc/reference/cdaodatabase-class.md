---
title: CDaoDatabase (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5b89d186701abf3b8c760e16800142e47e2872a3
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50073947"
---
# <a name="cdaodatabase-class"></a>CDaoDatabase (clase)

Representa una conexión a una base de datos, a través de la que puede trabajar con los datos.

## <a name="syntax"></a>Sintaxis

```
class CDaoDatabase : public CObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CDaoDatabase::CDaoDatabase](#cdaodatabase)|Construye un objeto `CDaoDatabase`. Llame a `Open` para conectar el objeto a una base de datos.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CDaoDatabase::CanTransact](#cantransact)|Devuelve cero si la base de datos admite transacciones.|
|[CDaoDatabase::CanUpdate](#canupdate)|Devuelve cero si el `CDaoDatabase` objeto es actualizable (no de solo lectura).|
|[CDaoDatabase::Close](#close)|Cierra la conexión de base de datos.|
|[CDaoDatabase::Create](#create)|Crea el objeto de base de datos DAO subyacente e inicializa el `CDaoDatabase` objeto.|
|[CDaoDatabase::CreateRelation](#createrelation)|Define a una nueva relación entre las tablas en la base de datos.|
|[CDaoDatabase::DeleteQueryDef](#deletequerydef)|Elimina un objeto de definición de consulta guardado en la colección de definiciones de consulta de la base de datos.|
|[CDaoDatabase::DeleteRelation](#deleterelation)|Elimina a una relación existente entre las tablas de la base de datos.|
|[CDaoDatabase::DeleteTableDef](#deletetabledef)|Elimina la definición de una tabla en la base de datos. Esto elimina la tabla real y todos sus datos.|
|[CDaoDatabase::Execute](#execute)|Ejecuta una consulta de acción. Una llamada a `Execute` para una consulta que devuelve resultados produce una excepción.|
|[CDaoDatabase::GetConnect](#getconnect)|Devuelve la cadena de conexión utilizada para conectar el `CDaoDatabase` objeto a una base de datos. Se usa para ODBC.|
|[CDaoDatabase::GetName](#getname)|Devuelve el nombre de la base de datos actualmente en uso.|
|[CDaoDatabase::GetQueryDefCount](#getquerydefcount)|Devuelve el número de consultas definidas para la base de datos.|
|[CDaoDatabase::GetQueryDefInfo](#getquerydefinfo)|Devuelve información acerca de una consulta especificada en la base de datos.|
|[CDaoDatabase::GetQueryTimeout](#getquerytimeout)|Devuelve el número de segundos después de la base de datos de operaciones de consulta agotará el tiempo. Afecta a todas las abra, agregar nuevos, actualizar y editar las operaciones y otras operaciones en los orígenes de datos ODBC (solo), como `Execute` llamadas.|
|[CDaoDatabase::GetRecordsAffected](#getrecordsaffected)|Devuelve el número de registros afectado por la última actualización, editar o agregar la operación o mediante una llamada a `Execute`.|
|[CDaoDatabase::GetRelationCount](#getrelationcount)|Devuelve el número de relaciones definidas entre las tablas de la base de datos.|
|[CDaoDatabase::GetRelationInfo](#getrelationinfo)|Devuelve información acerca de una relación especificada que se define entre las tablas en la base de datos.|
|[CDaoDatabase:: GetTableDefCount](#gettabledefcount)|Devuelve el número de tablas definidas en la base de datos.|
|[CDaoDatabase:: GetTableDefInfo](#gettabledefinfo)|Devuelve información acerca de una tabla especificada en la base de datos.|
|[CDaoDatabase::GetVersion](#getversion)|Devuelve la versión del motor de base de datos asociado con la base de datos.|
|[CDaoDatabase::IsOpen](#isopen)|Devuelve cero si el `CDaoDatabase` objeto actualmente está conectado a una base de datos.|
|[CDaoDatabase::Open](#open)|Establece una conexión a una base de datos.|
|[CDaoDatabase::SetQueryTimeout](#setquerytimeout)|Establece el número de segundos después de la base de datos de consulta operaciones (en orígenes de datos ODBC solo) agotará el tiempo. Afecta a todas las abra, agrega nuevos, actualiza y elimina operaciones.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[CDaoDatabase::m_pDAODatabase](#m_pdaodatabase)|Un puntero al objeto de base de datos DAO subyacente.|
|[CDaoDatabase::m_pWorkspace](#m_pworkspace)|Un puntero a la [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md) objeto que contiene la base de datos y define su espacio de transacción.|

## <a name="remarks"></a>Comentarios

Para obtener información acerca de los formatos de la base de datos admitidos, vea el [GetName](../../mfc/reference/cdaoworkspace-class.md#getname) función miembro. Puede tener uno o varios `CDaoDatabase` objetos activos a la vez en un "área de trabajo proporcionada," representado por un [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md) objeto. El área de trabajo mantiene una colección de objetos de base de datos abierta, llama a la colección de bases de datos.

> [!NOTE]
>  Las clases de base de datos DAO de MFC son distintas de las clases de base de datos MFC basadas en ODBC. Todos los nombres de clase de base de datos DAO tienen el prefijo "CDao". Clase `CDaoDatabase` proporciona una interfaz similar a la de la clase ODBC [CDatabase](../../mfc/reference/cdatabase-class.md). La principal diferencia es que `CDatabase` tiene acceso a la instancia de DBMS a través de Open Database Connectivity (ODBC) y un controlador ODBC para ese DBMS. `CDaoDatabase` tiene acceso a datos a través de un objeto de acceso de datos (DAO) basado en el motor de base de datos Microsoft Jet. En general, son más eficaces que las clases MFC basadas en ODBC; las clases MFC basadas en DAO las clases basadas en DAO pueden tener acceso a datos, incluidos los controladores ODBC, a través de su propio motor de base de datos. Las clases basadas en DAO también admiten las operaciones de lenguaje de definición de datos (DDL), como agregar tablas a través de las clases, sin tener que llamar a DAO directamente.

## <a name="usage"></a>Uso

Puede crear objetos de base de datos de forma implícita, cuando se crean objetos de conjunto de registros. Pero también puede crear objetos de base de datos explícitamente. Para usar una base de datos explícitamente con `CDaoDatabase`, realice una de las siguientes acciones:

- Construir un `CDaoDatabase` objeto, pasando un puntero a una apertura [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md) objeto.

- O construir una `CDaoDatabase` objeto sin especificar el área de trabajo (MFC crea un objeto de área de trabajo temporal).

Para crear una nueva Microsoft Jet (. Base de datos de Microsoft Access), construir un `CDaoDatabase` objeto y llamar a su [crear](#create) función miembro. Hacer *no* llamar `Open` después `Create`.

Para abrir una base de datos, construir un `CDaoDatabase` objeto y llamar a su [abrir](#open) función miembro.

Cualquiera de estas técnicas se anexa el objeto de base de datos DAO a la colección de bases de datos del área de trabajo y se abre una conexión a los datos. Cuando se construye a continuación, [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md), [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md), o [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md) objetos para el funcionamiento de la base de datos conectado, pase los constructores para estos objetos un puntero a su `CDaoDatabase` objeto. Cuando termine de utilizar la conexión, llame a la [cerrar](#close) miembro de función y destruir el `CDaoDatabase` objeto. `Close` cierra los conjuntos de registros que no se ha cerrado previamente.

## <a name="transactions"></a>Transacciones

Procesamiento de transacciones de base de datos se proporciona en el nivel de área de trabajo, consulte el [BeginTrans](../../mfc/reference/cdaoworkspace-class.md#begintrans), [CommitTrans](../../mfc/reference/cdaoworkspace-class.md#committrans), y [reversión](../../mfc/reference/cdaoworkspace-class.md#rollback) funciones miembro de clase `CDaoWorkspace` .

## <a name="odbc-connections"></a>Conexiones ODBC

La manera recomendada para trabajar con orígenes de datos ODBC es conectar las tablas externas a una Microsoft Jet (. Base de datos de Microsoft Access).

## <a name="collections"></a>Colecciones

Cada base de datos mantiene su propio colecciones de definición de tabla, definición de consulta, conjunto de registros y los objetos de relación. Clase `CDaoDatabase` proporciona funciones miembro para manipular estos objetos.

> [!NOTE]
>  Los objetos se almacenan en DAO, no en el objeto de base de datos MFC. MFC proporciona clases para los objetos de definición de tabla, la definición de consulta y el conjunto de registros, pero no para los objetos de relación.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

`CDaoDatabase`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdao.h

##  <a name="cantransact"></a>  CDaoDatabase::CanTransact

Llame a esta función miembro para determinar si la base de datos permite que las transacciones.

```
BOOL CanTransact();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la base de datos es compatible con las transacciones. en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Las transacciones se administran en el área de trabajo de la base de datos.

##  <a name="canupdate"></a>  CDaoDatabase::CanUpdate

Llame a esta función miembro para determinar si el `CDaoDatabase` objeto permite realizar actualizaciones.

```
BOOL CanUpdate();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el `CDaoDatabase` objeto permite actualizaciones; de lo contrario, 0, indicando que cualquiera que se pasa TRUE *bReadOnly* cuando abrió el `CDaoDatabase` objeto o que la base de datos es de solo lectura. Consulte la [abierto](#open) función miembro.

### <a name="remarks"></a>Comentarios

Para obtener información acerca de la actualización de la base de datos, vea el tema "Propiedad actualizable" en la Ayuda de DAO.

##  <a name="cdaodatabase"></a>  CDaoDatabase::CDaoDatabase

Construye un objeto `CDaoDatabase`.

```
CDaoDatabase(CDaoWorkspace* pWorkspace = NULL);
```

### <a name="parameters"></a>Parámetros

*pWorkspace*<br/>
Un puntero a la `CDaoWorkspace` objetos que contengan el nuevo objeto de base de datos. Si acepta el valor predeterminado es null, el constructor crea un archivo temporal `CDaoWorkspace` objeto que usa el área de trabajo predeterminada DAO. Puede obtener un puntero al objeto de área de trabajo mediante el [m_pWorkspace](#m_pworkspace) miembro de datos.

### <a name="remarks"></a>Comentarios

Después de crear el objeto, si va a crear una nueva Microsoft Jet (. MDB) de base de datos, llamar al objeto [crear](#create) función miembro. Si, en su lugar, abrir una base de datos existente, llame al objeto [abierto](#open) función miembro.

Cuando termine con el objeto, debe llamar a su [cerrar](#close) miembro de función y, a continuación, destruya el `CDaoDatabase` objeto.

Es posible que resulte conveniente incrustar la `CDaoDatabase` objeto en la clase de documento.

> [!NOTE]
>  Un `CDaoDatabase` objeto también se crea implícitamente si abre un [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) sin pasar un puntero a un objeto de `CDaoDatabase` objeto. Este objeto de base de datos se cierra cuando se cierra el objeto de conjunto de registros.

##  <a name="close"></a>  CDaoDatabase::Close

Llame a esta función miembro para desconectarse de una base de datos y cerrar los conjuntos de registros abiertos, definiciones de tabla y definiciones de consulta asociados con la base de datos.

```
virtual void Close();
```

### <a name="remarks"></a>Comentarios

Es recomendable cerrar estos objetos antes de llamar a esta función miembro. Cerrar un `CDaoDatabase` objeto lo quita de la colección de bases de datos en el asociado [área de trabajo](../../mfc/reference/cdaoworkspace-class.md). Dado que `Close` no destruye el `CDaoDatabase` de objeto, puede volver a usar el objeto abriendo la misma base de datos o en otra base de datos.

> [!CAUTION]
>  Llame a la [actualización](../../mfc/reference/cdaorecordset-class.md#update) función de miembro (si hay ediciones pendientes) y el `Close` la función miembro en todos los objetos de conjunto de registros abiertos antes de cerrar una base de datos. Si sale de una función que declara [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) o `CDaoDatabase` objetos en la pila, se cierra la base de datos, los cambios no guardados se perderán, todas las transacciones pendientes se revierten y las modificaciones pendientes a los datos se pierden.

> [!CAUTION]
>  Si se intenta cerrar un objeto de base de datos mientras está abierto algún objeto de conjunto de registros, o si se intenta cerrar un objeto de área de trabajo mientras está abierto algún objeto de base de datos que pertenecen a esa área de trabajo específico, se cerrarán los objetos de conjunto de registros y cualquier actualización o modificación pendiente será revierte. Si se intenta cerrar un objeto de área de trabajo mientras están abiertos los objetos de base de datos que pertenecen a ella, la operación cierra todos los objetos de base de datos que pertenecen a ese objeto de área de trabajo específica, lo que puede provocar en objetos de conjunto de registros sin cerrar se está cerrando. Si no cierra el objeto de base de datos, MFC notifica un error de aserción en las compilaciones de depuración.

Si el objeto de base de datos está definido fuera del ámbito de una función, y salir de la función sin cerrarla, permanecerá abierto hasta que cierre explícitamente el objeto de base de datos o el módulo en el que está definido fuera del ámbito.

##  <a name="create"></a>  CDaoDatabase::Create

Para crear una nueva Microsoft Jet (. MDB) de base de datos, llame a esta función miembro después de crear un `CDaoDatabase` objeto.

```
virtual void Create(
    LPCTSTR lpszName,
    LPCTSTR lpszLocale = dbLangGeneral,
    int dwOptions = 0);
```

### <a name="parameters"></a>Parámetros

*lpszName*<br/>
Una expresión de cadena que es el nombre del archivo de base de datos que va a crear. Puede ser la ruta de acceso completa y nombre de archivo, como "C:\\\MYDB. MDB". Debe proporcionar un nombre. Si no proporciona una extensión de nombre de archivo. Se anexa la MDB. Si la red es compatible con la convención de nomenclatura uniforme (UNC), también puede especificar una ruta de acceso de red, como "\\\\\\\MYSERVER\\\MYSHARE\\\MYDIR\\\MYDB". Solo Microsoft Jet (. Mediante esta función miembro, se pueden crear archivos de base de datos de Microsoft Access). (Las barras diagonales dobles son necesarias en literales de cadena porque "\\" es el carácter de escape de C++.)

*lpszLocale*<br/>
Una expresión de cadena que se usa para especificar el criterio de ordenación para la creación de la base de datos. El valor predeterminado es `dbLangGeneral`. Los valores posibles son:

- `dbLangGeneral` Inglés, alemán, francés, portugués, italiano y modernas español

- `dbLangArabic` Árabe

- `dbLangCyrillic` Ruso

- `dbLangCzech` Checo

- `dbLangDutch` Holandés

- `dbLangGreek` Griego

- `dbLangHebrew` Hebreo

- `dbLangHungarian` Húngaro

- `dbLangIcelandic` Islandés

- `dbLangNordic` Idiomas nórdicos (Microsoft Jet database engine sólo versión 1.0)

- `dbLangNorwdan` Noruego y danés

- `dbLangPolish` Polaco

- `dbLangSpanish` Español tradicional

- `dbLangSwedfin` Sueco y finés

- `dbLangTurkish` Turco

*dwOptions*<br/>
Un entero que indica una o más opciones. Los valores posibles son:

- `dbEncrypt` Crear una base de datos.

- `dbVersion10` Crear una base de datos con la versión de base de datos Microsoft Jet 1.0.

- `dbVersion11` Crear una base de datos con la versión de base de datos Microsoft Jet 1.1.

- `dbVersion20` Crear una base de datos con la versión de base de datos Microsoft Jet 2.0.

- `dbVersion30` Crear una base de datos con la versión de base de datos Microsoft Jet 3.0.

Si se omite la constante de cifrado, se crea una base de datos sin cifrar. Puede especificar solo una constante de versión. Si omite una constante de versión, se crea una base de datos que usa la versión 3.0 de la base de datos Microsoft Jet.

> [!CAUTION]
>  Si no se cifra una base de datos, es posible, incluso si decide implementar la seguridad de usuario y contraseña, para leer directamente el archivo de disco binario que constituye la base de datos.

### <a name="remarks"></a>Comentarios

`Create` crea el archivo de base de datos y el objeto de base de datos DAO subyacente e inicializa el objeto de C++. El objeto se anexa a la colección de bases de datos del área de trabajo asociado. El objeto de base de datos está en un estado abierto; No llame a `Open*` después `Create`.

> [!NOTE]
>  Con `Create`, puede crear solo Microsoft Jet (. Bases de datos de Microsoft Access). No se puede crear bases de datos ISAM o bases de datos ODBC.

##  <a name="createrelation"></a>  CDaoDatabase::CreateRelation

Llame a esta función miembro para establecer a una relación entre uno o varios campos de una tabla en la base de datos principal y uno o varios campos en una tabla externa (otra tabla en la base de datos).

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
El nombre único del objeto de relación. El nombre debe empezar por una letra y puede contener un máximo de 40 caracteres. Puede incluir números y caracteres de subrayado pero no puede incluir espacios o signos de puntuación.

*lpszTable*<br/>
El nombre de la tabla principal de la relación. Si la tabla no existe, MFC inicia una excepción de tipo [CDaoException](../../mfc/reference/cdaoexception-class.md).

*lpszForeignTable*<br/>
El nombre de la tabla externa en la relación. Si la tabla no existe, MFC inicia una excepción de tipo `CDaoException`.

*lAttributes*<br/>
Un valor long que contiene información sobre el tipo de relación. Puede usar este valor para exigir integridad referencial, entre otras cosas. Puede usar el operador OR bit a bit ( **&#124;**) para combinar cualquiera de los valores siguientes (siempre y cuando la combinación tiene sentido):

- `dbRelationUnique` La relación es uno a uno.

- `dbRelationDontEnforce` Relación no es aplicar (ninguna integridad referencial).

- `dbRelationInherited` Relación existe en una base de datos no actual que contiene las dos tablas asociadas.

- `dbRelationUpdateCascade` Las actualizaciones se realizará en cascada (para obtener más información sobre cascadas, vea la sección Comentarios).

- `dbRelationDeleteCascade` Las eliminaciones se realizará en cascada.

*lpszField*<br/>
Un puntero a una cadena terminada en null que contiene el nombre de un campo en la tabla principal (denominado por *lpszTable*).

*lpszForeignField*<br/>
Un puntero a una cadena terminada en null que contiene el nombre de un campo en la tabla externa (con el nombre *lpszForeignTable*).

*relinfo*<br/>
Una referencia a un [CDaoRelationInfo](../../mfc/reference/cdaorelationinfo-structure.md) objeto que contiene información sobre la relación que desea crear.

### <a name="remarks"></a>Comentarios

La relación no puede implicar una consulta o una tabla de una base de datos externa asociada.

Utilice la primera versión de la función cuando la relación implica un campo en cada una de las dos tablas. Use la segunda versión cuando la relación implica varios campos. El número máximo de campos en una relación es 14.

Esta acción crea un objeto de relación DAO subyacente, pero esto es un detalle de implementación de MFC, ya la encapsulación de objetos de relación de MFC está contenida dentro de la clase `CDaoDatabase`. MFC no proporciona una clase para las relaciones.

Si establece a la relación de atributos del objeto para activar las operaciones en cascada, el motor de base de datos se actualiza automáticamente o elimina los registros de una o varias tablas cuando se realizan cambios en tablas relacionadas de clave principales.

Por ejemplo, suponga que establecer una relación de eliminación en cascada entre una tabla de clientes y una tabla de pedidos. Al eliminar registros de la tabla Customers, también se eliminan los registros de la tabla de pedidos relacionados con ese cliente. Además, si establece cascade delete relaciones entre la tabla Orders y otras tablas, los registros de esas tablas se eliminan automáticamente cuando se eliminan registros de la tabla Customers.

Para obtener información relacionada, vea el tema "Método CreateRelation" en la Ayuda de DAO.

##  <a name="deletequerydef"></a>  CDaoDatabase::DeleteQueryDef

Llame a esta función miembro para eliminar la definición de consulta especificado: consulta guardada, desde el `CDaoDatabase` QueryDefs (colección) del objeto.

```
void DeleteQueryDef(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parámetros

*lpszName*<br/>
El nombre de la consulta guardada para eliminar.

### <a name="remarks"></a>Comentarios

Después, esa consulta ya no se define en la base de datos.

Para obtener información sobre cómo crear objetos de definición de consulta, vea la clase [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md). Un objeto de definición de consulta se asocia con un determinado `CDaoDatabase` objeto cuando se construye el `CDaoQueryDef` objeto, pasando un puntero al objeto de base de datos.

##  <a name="deleterelation"></a>  CDaoDatabase::DeleteRelation

Llame a esta función miembro para eliminar a una relación existente de la colección de relaciones del objeto de base de datos.

```
void DeleteRelation(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parámetros

*lpszName*<br/>
El nombre de la relación que se va a eliminar.

### <a name="remarks"></a>Comentarios

Después, la relación ya no existe.

Para obtener información relacionada, vea el tema "Método Delete" en la Ayuda de DAO.

##  <a name="deletetabledef"></a>  CDaoDatabase::DeleteTableDef

Llame a esta función miembro para eliminar la tabla especificada y todos sus datos desde el `CDaoDatabase` TableDefs (colección) del objeto.

```
void DeleteTableDef(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parámetros

*lpszName*<br/>
El nombre de la definición de tabla para eliminar.

### <a name="remarks"></a>Comentarios

Después, esta tabla ya no se define en la base de datos.

> [!NOTE]
>  Tener cuidado de no eliminar las tablas del sistema.

Para obtener información sobre cómo crear objetos de definición de tabla, vea la clase [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md). Un objeto de definición de tabla se asocia con un determinado `CDaoDatabase` objeto cuando se construye el `CDaoTableDef` objeto, pasando un puntero al objeto de base de datos.

Para obtener información relacionada, vea el tema "Método Delete" en la Ayuda de DAO.

##  <a name="execute"></a>  CDaoDatabase::Execute

Llame a esta función miembro para ejecutar una consulta de acción o ejecutar una instrucción SQL en la base de datos.

```
void Execute(
    LPCTSTR lpszSQL,
    int nOptions = dbFailOnError);
```

### <a name="parameters"></a>Parámetros

*lpszSQL*<br/>
Puntero a una cadena terminada en null que contiene un comando SQL válido.

*nOptions*<br/>
Un entero que especifica las opciones relacionadas con la integridad de la consulta. Puede usar el operador OR bit a bit ( **&#124;**) para combinar cualquiera de las siguientes constantes (siempre que la combinación tiene sentido, por ejemplo, podría combinar no `dbInconsistent` con `dbConsistent`):

- `dbDenyWrite` Denegar el permiso de escritura a otros usuarios.

- `dbInconsistent` (Valor predeterminado) Actualizaciones incoherentes.

- `dbConsistent` Actualizaciones coherentes.

- `dbSQLPassThrough` Paso a través SQL. Hace que la instrucción SQL que se pasará a un origen de datos ODBC para su procesamiento.

- `dbFailOnError` Revertir las actualizaciones si se produce un error.

- `dbSeeChanges` Generar un error en tiempo de ejecución si otro usuario está cambiando los datos que se está editando.

> [!NOTE]
>  Si ambos `dbInconsistent` y `dbConsistent` se incluyen o si ninguna de ellas se incluye, el resultado es el valor predeterminado. Para obtener una explicación de estas constantes, vea el tema "Método Execute" en la Ayuda de DAO.

### <a name="remarks"></a>Comentarios

`Execute` solo funciona para las consultas de acción o consultas de paso a través de SQL que no devuelvan resultados. No funciona para las consultas select que devuelven registros.

Para una definición e información acerca de las consultas de acción, vea los temas "Acción de consulta" y "Ejecutar método" en la Ayuda de DAO.

> [!TIP]
>  Dada una instrucción SQL sintácticamente correcta y los permisos adecuados, el `Execute` función miembro no se producirá un error incluso si no se puede modificar o eliminar una sola fila. Por lo tanto, use siempre la `dbFailOnError` opción cuando se usa el `Execute` función miembro para ejecutar una actualización o consulta de eliminación. Esta opción hace que MFC producir una excepción de tipo [CDaoException](../../mfc/reference/cdaoexception-class.md) y revierte todos los cambios correctos si cualquiera de los registros afectados se bloquean y se no puede actualizarse o eliminarse. Tenga en cuenta que pueda llamar siempre a `GetRecordsAffected` para ver el número de registros afectado.

Llame a la [GetRecordsAffected](#getrecordsaffected) función de miembro del objeto de base de datos para determinar el número de registros afectados por la más reciente `Execute` llamar. Por ejemplo, `GetRecordsAffected` devuelve información sobre el número de registros eliminados, actualizados o insertados cuando se ejecuta una consulta de acción. El recuento devuelto no se reflejará los cambios en las tablas relacionadas cuando en cascada actualiza o elimina están en vigor.

`Execute` no devuelve un conjunto de registros. Uso de `Execute` en una consulta que selecciona los registros hace que MFC producir una excepción de tipo `CDaoException`. (No hay ningún `ExecuteSQL` análogo en función de miembro `CDatabase::ExecuteSQL`.)

##  <a name="getconnect"></a>  CDaoDatabase::GetConnect

Llame a esta función miembro para recuperar la cadena de conexión utilizada para conectar el `CDaoDatabase` objeto a una base de datos ISAM u ODBC.

```
CString GetConnect();
```

### <a name="return-value"></a>Valor devuelto

La cadena de conexión si [abierto](#open) se ha llamado correctamente en un origen de datos ODBC; en caso contrario, una cadena vacía. Para un Microsoft Jet (. Base de datos de Microsoft Access), la cadena siempre está vacía a menos que establezca para su uso con el `dbSQLPassThrough` opción se utiliza con el [Execute](#execute) función miembro o usado en la apertura de un conjunto de registros.

### <a name="remarks"></a>Comentarios

La cadena proporciona información sobre el origen de una base de datos abierta o una base de datos de una consulta de paso a través. La cadena de conexión se compone de un especificador de tipo de base de datos y cero o más parámetros separados por punto y coma.

> [!NOTE]
>  Uso de las clases DAO de MFC para conectarse a un origen de datos a través de ODBC es menos eficaz que la conexión a través de una tabla asociada.

> [!NOTE]
>  La cadena de conexión se utiliza para pasar información adicional a ODBC y algunos controladores ISAM, según sea necesario. No se utiliza para. Bases de datos de Microsoft Access. Para las tablas de base de base de datos Microsoft Jet, la cadena de conexión es una cadena vacía (""), excepto cuando se utiliza para una consulta de paso a través de SQL como se describe en Return Value.

Consulte la [abierto](#open) función miembro para obtener una descripción de cómo se crea la cadena de conexión. Una vez que se ha establecido la cadena de conexión en el `Open` llamada, posteriormente sirve para comprobar la configuración para determinar el tipo, la ruta de acceso, el origen de los datos ODBC, la contraseña o Id. de usuario de la base de datos.

##  <a name="getname"></a>  CDaoDatabase::GetName

Llame a esta función miembro para recuperar el nombre de la base de datos abierto actualmente, que es el nombre de un archivo de base de datos existente o el nombre de un origen de datos ODBC registrado.

```
CString GetName();
```

### <a name="return-value"></a>Valor devuelto

La ruta de acceso completa y el nombre de la base de datos si se realiza correctamente; en caso contrario, un valor vacío [CString](../../atl-mfc-shared/reference/cstringt-class.md).

### <a name="remarks"></a>Comentarios

Si la red es compatible con la convención de nomenclatura uniforme (UNC), también puede especificar una ruta de acceso de red, por ejemplo, "\\\\\\\MYSERVER\\\MYSHARE\\\MYDIR\\\MYDB. MDB". (Las barras diagonales dobles son necesarias en literales de cadena porque "\\" es el carácter de escape de C++.)

Por ejemplo, podría mostrar este nombre en un encabezado. Si se produce un error mientras se recupera el nombre, MFC inicia una excepción de tipo [CDaoException](../../mfc/reference/cdaoexception-class.md).

> [!NOTE]
>  Para mejorar el rendimiento cuando se accede a las bases de datos externos, se recomienda adjuntar las tablas de base de datos externa a una base de datos Microsoft Jet (. MDB) en lugar de conectarse directamente al origen de datos.

El tipo de base de datos se indica mediante el archivo o directorio que la ruta de acceso apunta a, como sigue:

|Puntos de ruta de acceso a...|Tipo de base de datos|
|--------------------------|-------------------|
|. Archivo MDB|Base de datos Microsoft Jet (Microsoft Access)|
|Directorio que contiene. Archivos DBF|base de datos de dBASE|
|Directorio que contiene. Archivo XLS|Base de datos de Microsoft Excel|
|Directorio que contiene. Archivos PDX|Base de datos de Paradox|
|Directorio que contiene los archivos de base de datos de texto con el formato apropiado|Base de datos de formato de texto|

Bases de datos ODBC, como SQL Server y Oracle, la cadena de conexión de la base de datos identifica un nombre de origen de datos (DSN) que se registra por ODBC.

##  <a name="getquerydefcount"></a>  CDaoDatabase::GetQueryDefCount

Llame a esta función miembro para recuperar el número de consultas definidas en la colección de definiciones de consulta de la base de datos.

```
short GetQueryDefCount();
```

### <a name="return-value"></a>Valor devuelto

El número de consultas definidas en la base de datos.

### <a name="remarks"></a>Comentarios

`GetQueryDefCount` es útil si tiene que recorrer todas las definiciones de consulta en la colección de definiciones de consulta. Para obtener información acerca de una consulta determinada en la colección, vea [función miembro GetQueryDefInfo](#getquerydefinfo).

##  <a name="getquerydefinfo"></a>  CDaoDatabase::GetQueryDefInfo

Llame a esta función miembro para obtener diversos tipos de información acerca de una consulta definida en la base de datos.

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
El índice de la consulta predefinida en la colección de definiciones de consulta de la base de datos, para la búsqueda por índice.

*querydefinfo*<br/>
Una referencia a un [CDaoQueryDefInfo](../../mfc/reference/cdaoquerydefinfo-structure.md) objeto que devuelve la información solicitada.

*dwInfoOptions*<br/>
Opciones que especifican qué información sobre el conjunto de registros para recuperar. Las opciones disponibles se muestran aquí, junto con lo que hacen que la función devuelva sobre el conjunto de registros:

- Nombre AFX_DAO_PRIMARY_INFO (valor predeterminado), escriba

- AFX_DAO_SECONDARY_INFO principal información más: fecha de creación, fecha de última actualización, devuelve los registros, actualizable

- AFX_DAO_ALL_INFO principal y secundaria información más: SQL, Connect, ODBCTimeout

*lpszName*<br/>
Una cadena que contiene el nombre de una consulta definida en la base de datos para la búsqueda por nombre.

### <a name="remarks"></a>Comentarios

Se proporcionan dos versiones de la función para que pueda seleccionar una consulta de índice en la colección de definiciones de consulta de la base de datos o el nombre de la consulta.

Para obtener una descripción de la información devuelta en *querydefinfo*, consulte el [CDaoQueryDefInfo](../../mfc/reference/cdaoquerydefinfo-structure.md) estructura. Esta estructura no tiene miembros que corresponden a los elementos de información que aparece anteriormente en la descripción de *dwInfoOptions*. Si se solicita un nivel de información, obtenga los niveles anteriores de la información también.

##  <a name="getquerytimeout"></a>  CDaoDatabase::GetQueryTimeout

Llame a esta función miembro para recuperar el número actual de segundos que se permiten antes de que se agotó el tiempo las operaciones subsiguientes en la base de datos conectada.

```
short GetQueryTimeout();
```

### <a name="return-value"></a>Valor devuelto

Un entero corto que contiene el valor de tiempo de espera en segundos.

### <a name="remarks"></a>Comentarios

Una operación es posible que el tiempo de espera debido a problemas de acceso de red, el tiempo de procesamiento excesivo de consulta y así sucesivamente. Mientras que la configuración está en vigor, afecta a todos los abiertos, agregar nuevos, actualizar y eliminar operaciones en los conjuntos de registros asociado a este `CDaoDatabase` objeto. Puede cambiar la configuración de tiempo de espera actual mediante una llamada a [SetQueryTimeout](#setquerytimeout). Cambiar el valor de tiempo de espera de consulta para un conjunto de registros después de abrir, no cambie el valor para el conjunto de registros. Por ejemplo, posteriores [mover](../../mfc/reference/cdaorecordset-class.md#move) operaciones no usan el nuevo valor. El valor predeterminado se establece inicialmente cuando se inicializa el motor de base de datos.

El valor predeterminado para los tiempos de espera de consulta se toma del registro de Windows. Si no hay ninguna configuración del registro, el valor predeterminado es 60 segundos. No todas las bases de datos admiten la capacidad de establecer un valor de tiempo de espera de consulta. Si establece un valor de tiempo de espera de consulta de 0, se produce ningún tiempo de espera; y la comunicación con la base de datos puede dejar de responder. Este comportamiento puede ser útil durante el desarrollo. Si se produce un error en la llamada, MFC inicia una excepción de tipo [CDaoException](../../mfc/reference/cdaoexception-class.md).

Para obtener información relacionada, vea el tema "Propiedad QueryTimeout" en la Ayuda de DAO.

##  <a name="getrecordsaffected"></a>  CDaoDatabase::GetRecordsAffected

Llame a esta función miembro para determinar el número de registros afectados por la llamada más reciente de la [Execute](#execute) función miembro.

```
long GetRecordsAffected();
```

### <a name="return-value"></a>Valor devuelto

Un entero largo que contiene el número de registros afectados.

### <a name="remarks"></a>Comentarios

El valor devuelto incluye el número de registros eliminados, actualiza o inserta una consulta de acción que se ejecute con `Execute`. El recuento devuelto no se reflejará los cambios en las tablas relacionadas cuando en cascada actualiza o elimina están en vigor.

Para obtener información relacionada, vea el tema "Propiedad RecordsAffected" en la Ayuda de DAO.

##  <a name="getrelationcount"></a>  CDaoDatabase::GetRelationCount

Llame a esta función miembro para obtener el número de relaciones definidas entre las tablas de la base de datos.

```
short GetRelationCount();
```

### <a name="return-value"></a>Valor devuelto

El número de relaciones definidas entre las tablas de la base de datos.

### <a name="remarks"></a>Comentarios

`GetRelationCount` es útil si tiene que recorrer todas las relaciones definidas en la colección de relaciones de la base de datos. Para obtener información acerca de una relación determinada de la colección, consulte [GetRelationInfo](#getrelationinfo).

Para ilustrar el concepto de una relación, considere la posibilidad de una tabla de proveedores y una tabla de productos, que puede que tenga una relación uno a varios. En esta relación, un proveedor puede proporcionar más de un producto. Otras relaciones son uno a uno y varios a varios.

##  <a name="getrelationinfo"></a>  CDaoDatabase::GetRelationInfo

Llame a esta función miembro para obtener información acerca de una relación especificada en la colección de relaciones de la base de datos.

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
El índice del objeto de relación en la colección de relaciones de la base de datos, para la búsqueda por índice.

*relinfo*<br/>
Una referencia a un [CDaoRelationInfo](../../mfc/reference/cdaorelationinfo-structure.md) objeto que devuelve la información solicitada.

*dwInfoOptions*<br/>
Opciones que especifican qué información sobre la relación para recuperar. Las opciones disponibles se muestran aquí, junto con lo que hacen que la función devuelva acerca de la relación:

- Tabla externa de nombre de la tabla, AFX_DAO_PRIMARY_INFO (valor predeterminado)

- Atributos AFX_DAO_SECONDARY_INFO, información de campo

La información de campo es un [CDaoRelationFieldInfo](../../mfc/reference/cdaorelationfieldinfo-structure.md) objeto que contiene los campos de la tabla principal implicada en la relación.

*lpszName*<br/>
Una cadena que contiene el nombre del objeto relation, para la búsqueda por nombre.

### <a name="remarks"></a>Comentarios

Dos versiones de esta función proporcionan acceso por índice o por nombre. Para obtener una descripción de la información devuelta en *relinfo*, consulte el [CDaoRelationInfo](../../mfc/reference/cdaorelationinfo-structure.md) estructura. Esta estructura no tiene miembros que corresponden a los elementos de información que aparece anteriormente en la descripción de *dwInfoOptions*. Si se solicita información en un nivel, también obtendrá información en todos los niveles anteriores.

> [!NOTE]
>  Si establece la relación de atributos del objeto para activar las operaciones en cascada (`dbRelationUpdateCascades` o `dbRelationDeleteCascades`), el motor de base de datos Microsoft Jet automáticamente actualiza o elimina los registros de una o varias de las otras tablas cuando se realizan cambios en relacionados con la clave principal tablas. Por ejemplo, suponga que establecer una relación de eliminación en cascada entre una tabla de clientes y una tabla de pedidos. Al eliminar registros de la tabla Customers, también se eliminan los registros de la tabla de pedidos relacionados con ese cliente. Además, si establece cascade delete relaciones entre la tabla Orders y otras tablas, los registros de esas tablas se eliminan automáticamente cuando se eliminan registros de la tabla Customers.

##  <a name="gettabledefcount"></a>  CDaoDatabase:: GetTableDefCount

Llame a esta función miembro para recuperar el número de tablas definidas en la base de datos.

```
short GetTableDefCount();
```

### <a name="return-value"></a>Valor devuelto

El número de definiciones de tabla definidas en la base de datos.

### <a name="remarks"></a>Comentarios

`GetTableDefCount` es útil si tiene que recorrer todas las definiciones de tabla en la colección de definiciones de tabla de la base de datos. Para obtener información acerca de una tabla determinada en la colección, vea [GetTableDefInfo](#gettabledefinfo).

##  <a name="gettabledefinfo"></a>  CDaoDatabase:: GetTableDefInfo

Llame a esta función miembro para obtener diversos tipos de información sobre una tabla definida en la base de datos.

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
El índice del objeto de definición de tabla en la colección de definiciones de tabla de la base de datos, para la búsqueda por índice.

*tabledefinfo*<br/>
Una referencia a un [CDaoTableDefInfo](../../mfc/reference/cdaotabledefinfo-structure.md) objeto que devuelve la información solicitada.

*dwInfoOptions*<br/>
Opciones que especifican qué información acerca de la tabla para recuperar. Las opciones disponibles se muestran aquí, junto con lo que hacen que la función devuelva acerca de la relación:

- Atributos de nombre AFX_DAO_PRIMARY_INFO (valor predeterminado), puede actualizar,

- AFX_DAO_SECONDARY_INFO principal información más: fecha de creación, fecha de última actualización, de nombre de tabla de origen, conectar

- AFX_DAO_ALL_INFO principal y secundaria información más: número de registros de la regla de validación, el texto de validación

*lpszName*<br/>
El nombre del objeto de definición de tabla, para la búsqueda por nombre.

### <a name="remarks"></a>Comentarios

Se proporcionan dos versiones de la función para que pueda seleccionar una tabla de índice en la colección de definiciones de tabla de la base de datos o el nombre de la tabla.

Para obtener una descripción de la información devuelta en *tabledefinfo*, consulte el [CDaoTableDefInfo](../../mfc/reference/cdaotabledefinfo-structure.md) estructura. Esta estructura no tiene miembros que corresponden a los elementos de información que aparece anteriormente en la descripción de *dwInfoOptions*. Si se solicita información en un nivel, obtendrá información de los niveles anteriores también.

> [!NOTE]
>  La opción AFX_DAO_ALL_INFO proporciona información que puede ser lento a obtener. En este caso, el recuento de los registros en la tabla podría ser muy lento si hay varios registros.

##  <a name="getversion"></a>  CDaoDatabase::GetVersion

Llame a esta función miembro para determinar la versión del archivo de base de datos Microsoft Jet.

```
CString GetVersion();
```

### <a name="return-value"></a>Valor devuelto

Un [CString](../../atl-mfc-shared/reference/cstringt-class.md) que indica la versión del archivo de base de datos asociado al objeto.

### <a name="remarks"></a>Comentarios

El valor devuelto representa el número de versión en el formato "major.minor"; Por ejemplo, "3.0". El número de versión del producto (por ejemplo, 3.0) está formado por el número de versión (3), un punto y el número de versión (0). Las versiones hasta la fecha son 1.0, 1.1, 2.0 y 3.0.

Para obtener información relacionada, vea el tema "Propiedad de versión" en la Ayuda de DAO.

##  <a name="isopen"></a>  CDaoDatabase::IsOpen

Llame a esta función miembro para determinar si el `CDaoDatabase` objeto está actualmente abierto en una base de datos.

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el `CDaoDatabase` objeto está abierto actualmente; de lo contrario, 0.

### <a name="remarks"></a>Comentarios

##  <a name="m_pdaodatabase"></a>  CDaoDatabase::m_pDAODatabase

Contiene un puntero a la interfaz OLE para el objeto de base de datos DAO subyacente el `CDaoDatabase` objeto.

### <a name="remarks"></a>Comentarios

Use este puntero si necesita obtener acceso a la interfaz DAO directamente.

Para obtener información sobre cómo llamar a DAO directamente, vea [Nota técnica 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).

##  <a name="m_pworkspace"></a>  CDaoDatabase::m_pWorkspace

Contiene un puntero a la [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md) objeto que contiene el objeto de base de datos.

### <a name="remarks"></a>Comentarios

Use este puntero si necesita acceso directo del área de trabajo, por ejemplo, para obtener punteros a otros objetos de base de datos de colección de bases de datos del área de trabajo.

##  <a name="open"></a>  CDaoDatabase::Open

Debe llamar a esta función miembro para inicializar un recientemente construido `CDaoDatabase` objeto que representa una base de datos existente.

```
virtual void Open(
    LPCTSTR lpszName,
    BOOL bExclusive = FALSE,
    BOOL bReadOnly = FALSE,
    LPCTSTR lpszConnect = _T(""));
```

### <a name="parameters"></a>Parámetros

*lpszName*<br/>
Una expresión de cadena que es el nombre de una existente de Microsoft Jet (. Archivo de base de datos de Microsoft Access). Si el nombre de archivo tiene una extensión, es necesario. Si la red es compatible con la convención de nomenclatura uniforme (UNC), también puede especificar una ruta de acceso de red, como "\\\\\\\MYSERVER\\\MYSHARE\\\MYDIR\\\MYDB. MDB". (Las barras diagonales dobles son necesarias en literales de cadena porque "\\" es el carácter de escape de C++.)

Se aplican algunas consideraciones al usar *lpszName*. Si lo:

- Hace referencia a una base de datos que ya está abierto para acceso exclusivo por otro usuario, MFC inicia una excepción de tipo [CDaoException](../../mfc/reference/cdaoexception-class.md). Interceptar esta excepción para que el usuario sepa que la base de datos no está disponible.

- Es una cadena vacía ("") y *lpszConnect* es "ODBC;", se muestra un cuadro de diálogo lista de todos los nombres de origen de datos ODBC para el usuario pueda seleccionar una base de datos. Debe evitar conexiones directas a orígenes de datos ODBC; Utilice en su lugar una tabla asociada.

- En caso contrario, no hace referencia a una base de datos existente o válido datos nombre de origen ODBC, MFC inicia una excepción de tipo `CDaoException`.

> [!NOTE]
>  Para obtener más información acerca de los códigos de error DAO, vea el DAOERR. Archivo de H. Para obtener información relacionada, vea el tema "Errores interceptables de acceso de datos" en la Ayuda de DAO.

*bExclusive*<br/>
Un valor booleano que es TRUE si la base de datos que se va a abrirse para acceso exclusivo de (no compartido) y FALSE si la base de datos que se va a abrirse para el acceso compartido. Si se omite este argumento, se abre la base de datos para el acceso compartido.

*bReadOnly*<br/>
Un valor booleano que es TRUE si la base de datos que se va a abrirse para acceso de solo lectura y FALSE si es la base de datos se abre para el acceso de lectura/escritura. Si se omite este argumento, la base de datos se abre para acceso de lectura/escritura. Todos los conjuntos de registros dependientes heredan este atributo.

*lpszConnect*<br/>
Una expresión de cadena utilizada para abrir la base de datos. Esta cadena constituye ODBC conectarse argumentos. Debe proporcionar los argumentos exclusivos y de solo lectura para proporcionar una cadena de origen. Si la base de datos es una base de datos Microsoft Jet (. MDB), esta cadena está vacía (""). La sintaxis para el valor predeterminado: **_T**(""): proporciona las compilaciones de portabilidad para Unicode, así como ANSI de la aplicación.

### <a name="remarks"></a>Comentarios

`Open` la base de datos se asocia con el objeto DAO subyacente. No puede usar para construir objetos de definición de consulta, definición de tabla o conjunto de registros hasta que se inicializa el objeto de base de datos. `Open` Anexa el objeto de base de datos a la colección de bases de datos del área de trabajo asociada.

Use los parámetros de la siguiente manera:

- Si abre un Microsoft Jet (. Base de datos de Microsoft Access), use el *lpszName* parámetro y pase una cadena vacía para el *lpszConnect* parámetro o pase una cadena de contraseña del formulario "; PWD = contraseña "si la base de datos está protegido por contraseña (. MDB solo bases de datos).

- Si abre un origen de datos ODBC, pase una cadena de conexión ODBC válida en *lpszConnect* y una cadena vacía en *lpszName*.

Para obtener información relacionada, vea el tema "Método OpenDatabase" en la Ayuda de DAO.

> [!NOTE]
>  Para mejorar el rendimiento al tener acceso a bases de datos externas, incluidas las bases de datos ISAM y orígenes de datos ODBC, se recomienda que vincule tablas de base de datos externa a una base de datos de motor de Microsoft Jet (. MDB) en lugar de conectarse directamente al origen de datos.

Es posible que un intento de conexión en tiempo de espera si, por ejemplo, el host DBMS no está disponible. Si se produce un error en el intento de conexión, `Open` produce una excepción de tipo [CDaoException](../../mfc/reference/cdaoexception-class.md).

Los comentarios restantes se aplican solo a las bases de datos ODBC:

Si la base de datos es una base de datos ODBC y los parámetros en su `Open` llamada no contienen información suficiente para realizar la conexión, el controlador ODBC abre un cuadro de diálogo para obtener la información necesaria del usuario. Cuando se llama a `Open`, la cadena de conexión, *lpszConnect*, se almacena de forma privada y está disponible mediante una llamada a la [GetConnect](#getconnect) función miembro.

Si lo desea, puede abrir su propio cuadro de diálogo antes de llamar a `Open` para obtener información del usuario, como una contraseña, a continuación, agregue dicha información a la cadena de conexión se pasa a `Open`. O es posible que desee guardar la cadena de conexión pasa (por ejemplo, en el registro de Windows) por lo que se puede reutilizar la próxima vez su aplicación llama `Open` en un `CDaoDatabase` objeto.

También puede usar la cadena de conexión de varios niveles de autorización de inicio de sesión (cada uno de otro `CDaoDatabase` objeto) o transmitir otra información específica de la base de datos.

##  <a name="setquerytimeout"></a>  CDaoDatabase::SetQueryTimeout

Llame a esta función miembro para invalidar el número predeterminado de segundos que se permiten antes de las operaciones siguientes en el tiempo de espera de base de datos conectada.

```
void SetQueryTimeout(short nSeconds);
```

### <a name="parameters"></a>Parámetros

*númeroSegundos*<br/>
El número de segundos que se permiten antes de un intento de consulta agote el tiempo de espera.

### <a name="remarks"></a>Comentarios

Una operación es posible que el tiempo de espera debido a problemas de acceso de red, el tiempo de procesamiento excesivo de consulta y así sucesivamente. Llame a `SetQueryTimeout` antes de abrir el conjunto de registros o antes de llamar a la función miembro [AddNew](../../mfc/reference/cdaorecordset-class.md#addnew), [actualización](../../mfc/reference/cdaorecordset-class.md#update), o [eliminar](../../mfc/reference/cdaorecordset-class.md#delete) funciones miembro, si desea cambiar la consulta valor de tiempo de espera. La configuración afecta a todas las [abierto](../../mfc/reference/cdaorecordset-class.md#open), `AddNew`, `Update`, y `Delete` las llamadas a los conjuntos de registros asociado a este `CDaoDatabase` objeto. Cambiar el valor de tiempo de espera de consulta para un conjunto de registros después de abrir, no cambie el valor para el conjunto de registros. Por ejemplo, posteriores [mover](../../mfc/reference/cdaorecordset-class.md#move) operaciones no usan el nuevo valor.

El valor predeterminado para los tiempos de espera de consulta es 60 segundos. No todas las bases de datos admiten la capacidad de establecer un valor de tiempo de espera de consulta. Si establece un valor de tiempo de espera de consulta de 0, se produce ningún tiempo de espera; la comunicación con la base de datos puede dejar de responder. Este comportamiento puede ser útil durante el desarrollo.

Para obtener información relacionada, vea el tema "Propiedad QueryTimeout" en la Ayuda de DAO.

## <a name="see-also"></a>Vea también

[CObject (clase)](../../mfc/reference/cobject-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CDaoWorkspace (clase)](../../mfc/reference/cdaoworkspace-class.md)<br/>
[CDaoRecordset (clase)](../../mfc/reference/cdaorecordset-class.md)<br/>
[CDaoTableDef (clase)](../../mfc/reference/cdaotabledef-class.md)<br/>
[CDaoQueryDef (clase)](../../mfc/reference/cdaoquerydef-class.md)<br/>
[CDatabase (clase)](../../mfc/reference/cdatabase-class.md)<br/>
[CDaoException (clase)](../../mfc/reference/cdaoexception-class.md)
