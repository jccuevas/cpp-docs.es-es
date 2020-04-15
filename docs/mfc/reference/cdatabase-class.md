---
title: Clase CDatabase
ms.date: 11/04/2016
f1_keywords:
- CDatabase
- AFXDB/CDatabase
- AFXDB/CDatabase::CDatabase
- AFXDB/CDatabase::BeginTrans
- AFXDB/CDatabase::BindParameters
- AFXDB/CDatabase::Cancel
- AFXDB/CDatabase::CanTransact
- AFXDB/CDatabase::CanUpdate
- AFXDB/CDatabase::Close
- AFXDB/CDatabase::CommitTrans
- AFXDB/CDatabase::ExecuteSQL
- AFXDB/CDatabase::GetBookmarkPersistence
- AFXDB/CDatabase::GetConnect
- AFXDB/CDatabase::GetCursorCommitBehavior
- AFXDB/CDatabase::GetCursorRollbackBehavior
- AFXDB/CDatabase::GetDatabaseName
- AFXDB/CDatabase::IsOpen
- AFXDB/CDatabase::OnSetOptions
- AFXDB/CDatabase::Open
- AFXDB/CDatabase::OpenEx
- AFXDB/CDatabase::Rollback
- AFXDB/CDatabase::SetLoginTimeout
- AFXDB/CDatabase::SetQueryTimeout
- AFXDB/CDatabase::m_hdbc
helpviewer_keywords:
- CDatabase [MFC], CDatabase
- CDatabase [MFC], BeginTrans
- CDatabase [MFC], BindParameters
- CDatabase [MFC], Cancel
- CDatabase [MFC], CanTransact
- CDatabase [MFC], CanUpdate
- CDatabase [MFC], Close
- CDatabase [MFC], CommitTrans
- CDatabase [MFC], ExecuteSQL
- CDatabase [MFC], GetBookmarkPersistence
- CDatabase [MFC], GetConnect
- CDatabase [MFC], GetCursorCommitBehavior
- CDatabase [MFC], GetCursorRollbackBehavior
- CDatabase [MFC], GetDatabaseName
- CDatabase [MFC], IsOpen
- CDatabase [MFC], OnSetOptions
- CDatabase [MFC], Open
- CDatabase [MFC], OpenEx
- CDatabase [MFC], Rollback
- CDatabase [MFC], SetLoginTimeout
- CDatabase [MFC], SetQueryTimeout
- CDatabase [MFC], m_hdbc
ms.assetid: bd0de70a-e3c3-4441-bcaa-bbf434426ca8
ms.openlocfilehash: 260a4a38fcee8994d804267709c11279266d393c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376478"
---
# <a name="cdatabase-class"></a>Clase CDatabase

Representa una conexión a un origen de datos, a través de la que puede trabajar con el origen de datos.

## <a name="syntax"></a>Sintaxis

```
class CDatabase : public CObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CDatabase::CDatabase](#cdatabase)|Construye un objeto `CDatabase`. Debe inicializar el objeto `OpenEx` `Open`llamando o .|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CDatabase::BeginTrans](#begintrans)|Inicia una "transacción" (una serie `AddNew` `Edit`de `Delete`llamadas reversibles a las funciones , , , y `Update` miembro de la clase) `CRecordset` en el origen de datos conectado. El origen de datos `BeginTrans` debe admitir transacciones para que tengan algún efecto.|
|[CDatabase::BindParameters](#bindparameters)|Le permite enlazar parámetros antes de llamar a `CDatabase::ExecuteSQL`.|
|[CDatabase::Cancelar](#cancel)|Cancela una operación asincrónica o un proceso desde un segundo subproceso.|
|[CDatabase::CanTransact](#cantransact)|Devuelve distinto de cero si el origen de datos admite transacciones.|
|[CDatabase::CanUpdate](#canupdate)|Devuelve distinto de `CDatabase` cero si el objeto es actualizable (no de solo lectura).|
|[CDatabase::Cerrar](#close)|Cierra la conexión del origen de datos.|
|[CDatabase::CommitTrans](#committrans)|Completa una transacción `BeginTrans`iniciada por . Se llevan a cabo los comandos de la transacción que modifican el origen de datos.|
|[CDatabase::ExecuteSQL](#executesql)|Ejecuta una instrucción SQL. No se devuelve ningún registro de datos.|
|[CDatabase::GetBookmarkPersistence](#getbookmarkpersistence)|Identifica las operaciones a través de las cuales los marcadores persisten en los objetos de conjunto de registros.|
|[CDatabase::GetConnect](#getconnect)|Devuelve la cadena de conexión `CDatabase` ODBC utilizada para conectar el objeto a un origen de datos.|
|[CDatabase::GetCursorCommitBehavior](#getcursorcommitbehavior)|Identifica el efecto de confirmar una transacción en un objeto de conjunto de registros abierto.|
|[CDatabase::GetCursorRollbackBehavior](#getcursorrollbackbehavior)|Identifica el efecto de revertir una transacción en un objeto de conjunto de registros abierto.|
|[CDatabase::GetDatabaseName](#getdatabasename)|Devuelve el nombre de la base de datos actualmente en uso.|
|[CDatabase::IsOpen](#isopen)|Devuelve distinto de `CDatabase` cero si el objeto está conectado actualmente a un origen de datos.|
|[CDatabase::OnSetOptions](#onsetoptions)|Llamado por el marco de trabajo para establecer opciones de conexión estándar. La implementación predeterminada establece el valor de tiempo de espera de consulta. Puede establecer estas opciones con `SetQueryTimeout`antelación llamando a .|
|[CDatabase::Abierto](#open)|Establece una conexión a un origen de datos (a través de un controlador ODBC).|
|[CDatabase::OpenEx](#openex)|Establece una conexión a un origen de datos (a través de un controlador ODBC).|
|[CDatabase::Rollback](#rollback)|Invierte los cambios realizados durante la transacción actual. El origen de datos vuelve a su `BeginTrans` estado anterior, tal como se define en la llamada, sin cambios.|
|[CDatabase::SetLoginTimeout](#setlogintimeout)|Establece el número de segundos después de los cuales se agota el tiempo de espera de un intento de conexión de origen de datos.|
|[CDatabase::SetQueryTimeout](#setquerytimeout)|Establece el número de segundos después de los cuales se agota el tiempo de espera de las operaciones de consulta de base de datos. Afecta a `Open`todos `AddNew` `Edit`los `Delete` conjuntos de registros subsiguientes, , , y las llamadas.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CDatabase::m_hdbc](#m_hdbc)|Abra el identificador de conexión de conectividad a la base de datos (ODBC) a un origen de datos. Escriba *HDBC*.|

## <a name="remarks"></a>Observaciones

Un origen de datos es una instancia específica de datos hospedada por algún sistema de administración de bases de datos (DBMS). Algunos ejemplos son Microsoft SQL Server, Microsoft Access, Borland dBASE y xBASE. Puede tener uno `CDatabase` o más objetos activos a la vez en la aplicación.

> [!NOTE]
> Si está trabajando con las clases de objetos de acceso a datos (DAO) en lugar de las clases de conectividad de base de datos abierta (ODBC), utilice la clase [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) en su lugar. Para obtener más información, consulte el artículo [Información general: Programación](../../data/data-access-programming-mfc-atl.md)de bases de datos .

Para `CDatabase`usar , `CDatabase` construir un `OpenEx` objeto y llamar a su función miembro. Esto abre una conexión. A continuación, `CRecordset` cuando construya objetos para operar en el origen `CDatabase` de datos conectado, pase el constructor del conjunto de registros un puntero al objeto. Cuando termine de usar la `Close` conexión, llame `CDatabase` a la función miembro y destruya el objeto. `Close`cierra los conjuntos de registros que no haya cerrado anteriormente.

Para obtener `CDatabase`más información acerca de , vea los artículos Origen de datos [(ODBC)](../../data/odbc/data-source-odbc.md) y [Información general: Programación](../../data/data-access-programming-mfc-atl.md)de bases de datos .

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

`CDatabase`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdb.h

## <a name="cdatabasebegintrans"></a><a name="begintrans"></a>CDatabase::BeginTrans

Llame a esta función miembro para iniciar una transacción con el origen de datos conectado.

```
BOOL BeginTrans();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la llamada se realizó correctamente y los cambios se confirman solo manualmente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Una transacción consta de una `AddNew` `Edit`o `Delete`varias `Update` llamadas `CRecordset` a las funciones , , y miembro de un objeto. Antes de iniciar `CDatabase` una transacción, el objeto ya `OpenEx` debe `Open` haberse conectado al origen de datos llamando a su función miembro. Para finalizar la transacción, llame a [CommitTrans](#committrans) para aceptar todos los cambios en el origen de datos (y llevarlos a cabo) o llame a [Rollback](#rollback) para anular toda la transacción. Llame `BeginTrans` después de abrir los conjuntos de registros implicados en la transacción y lo más cerca posible de las operaciones de actualización reales.

> [!CAUTION]
> Según el controlador ODBC, abrir `BeginTrans` un conjunto de `Rollback`registros antes de llamar puede causar problemas al llamar a . Debe comprobar el controlador específico que está utilizando. Por ejemplo, al usar el controlador de Microsoft Access incluido en Microsoft ODBC Desktop Driver Pack 3.0, debe tener en cuenta el requisito del motor de base de datos Jet de que no debe iniciar una transacción en ninguna base de datos que tenga un cursor abierto. En las clases de base de `CRecordset` datos MFC, un cursor abierto significa un objeto abierto. Para obtener más información, consulte [la Nota técnica 68](../../mfc/tn068-performing-transactions-with-the-microsoft-access-7-odbc-driver.md).

`BeginTrans`También puede bloquear registros de datos en el servidor, dependiendo de la simultaneidad solicitada y las capacidades del origen de datos. Para obtener información sobre el bloqueo de datos, vea el artículo [Conjunto de registros: bloqueo de registros (ODBC)](../../data/odbc/recordset-locking-records-odbc.md).

Las transacciones definidas por el usuario se explican en el artículo [Transacción (ODBC)](../../data/odbc/transaction-odbc.md).

`BeginTrans`establece el estado al que se puede revertir la secuencia de transacciones (invertida). Para establecer un nuevo estado para las reversiones, confirme cualquier transacción actual y, a continuación, vuelva a llamar. `BeginTrans`

> [!CAUTION]
> Llamar `BeginTrans` de `CommitTrans` nuevo `Rollback` sin llamar o es un error.

Llame a la [CanTransact](#cantransact) función miembro para determinar si el controlador admite transacciones para una base de datos determinada. También debe llamar a [GetCursorCommitBehavior](#getcursorcommitbehavior) y [GetCursorRollbackBehavior](#getcursorrollbackbehavior) para determinar la compatibilidad con la conservación del cursor.

Para obtener más información acerca de las transacciones, vea el artículo [Transacción (ODBC)](../../data/odbc/transaction-odbc.md).

### <a name="example"></a>Ejemplo

  Consulte el artículo [Transacción: realizar una transacción en un conjunto de registros (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md).

## <a name="cdatabasebindparameters"></a><a name="bindparameters"></a>CDatabase::BindParameters

Invalidar `BindParameters` cuando necesite enlazar parámetros antes de llamar a [CDatabase::ExecuteSQL](#executesql).

```
virtual void BindParameters(HSTMT hstmt);
```

### <a name="parameters"></a>Parámetros

*hstmt*<br/>
El identificador de instrucción ODBC para el que desea enlazar parámetros.

### <a name="remarks"></a>Observaciones

Este enfoque es útil cuando no necesita el conjunto de resultados de un procedimiento almacenado.

En la invalidación, llame `SQLBindParameters` a las funciones ODBC relacionadas y para enlazar los parámetros. MFC llama a la `ExecuteSQL`invalidación antes de la llamada a . No es necesario `SQLPrepare`llamar; `ExecuteSQL` llama `SQLExecDirect` y destruye el *hstmt,* que se utiliza una sola vez.

## <a name="cdatabasecancel"></a><a name="cancel"></a>CDatabase::Cancelar

Llame a esta función miembro para solicitar que el origen de datos cancele una operación asincrónica en curso o un proceso de un segundo subproceso.

```
void Cancel();
```

### <a name="remarks"></a>Observaciones

Tenga en cuenta que las clases ODBC de MFC ya no utilizan el procesamiento asincrónico; para realizar una operación asincrónica, debe llamar directamente a la función de API ODBC [SQLSetConnectOption](/sql/odbc/reference/syntax/sqlsetconnectoption-function). Para obtener más información, vea el tema que trata sobre [ejecución asincrónica](/sql/odbc/reference/develop-app/asynchronous-execution).

## <a name="cdatabasecantransact"></a><a name="cantransact"></a>CDatabase::CanTransact

Llame a esta función miembro para determinar si la base de datos permite transacciones.

```
BOOL CanTransact() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si `CDatabase` los conjuntos de registros que utilizan este objeto permiten transacciones; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Para obtener información acerca de las transacciones, vea el artículo [Transacción (ODBC)](../../data/odbc/transaction-odbc.md).

## <a name="cdatabasecanupdate"></a><a name="canupdate"></a>CDatabase::CanUpdate

Llame a esta función `CDatabase` miembro para determinar si el objeto permite actualizaciones.

```
BOOL CanUpdate() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de `CDatabase` cero si el objeto permite actualizaciones; de lo contrario 0, lo que indica que ha `CDatabase` pasado TRUE en *bReadOnly* al abrir el objeto o que el propio origen de datos es de solo lectura. El origen de datos es de solo lectura `SQLGetInfo` si una llamada a la función de API ODBC para SQL_DATASOURCE_READ_ONLY devuelve "y".

### <a name="remarks"></a>Observaciones

No todos los controladores admiten actualizaciones.

## <a name="cdatabasecdatabase"></a><a name="cdatabase"></a>CDatabase::CDatabase

Construye un objeto `CDatabase`.

```
CDatabase();
```

### <a name="remarks"></a>Observaciones

Después de construir el objeto, debe llamar a su `OpenEx` o `Open` función miembro para establecer una conexión a un origen de datos especificado.

Es posible que le `CDatabase` resulte conveniente incrustar el objeto en la clase de documento.

### <a name="example"></a>Ejemplo

En este ejemplo `CDatabase` se `CDocument`muestra el uso en una clase derivada.

[!code-cpp[NVC_MFCDatabase#9](../../mfc/codesnippet/cpp/cdatabase-class_1.h)]

[!code-cpp[NVC_MFCDatabase#10](../../mfc/codesnippet/cpp/cdatabase-class_2.cpp)]

## <a name="cdatabaseclose"></a><a name="close"></a>CDatabase::Cerrar

Llame a esta función miembro si desea desconectarse de un origen de datos.

```
virtual void Close();
```

### <a name="remarks"></a>Observaciones

Debe cerrar los conjuntos `CDatabase` de registros asociados con el objeto antes de llamar a esta función miembro. Dado `Close` que no `CDatabase` destruye el objeto, puede reutilizar el objeto abriendo una nueva conexión al mismo origen de datos o a un origen de datos diferente.

Se `AddNew` cancelan todas las instrucciones pendientes o `Edit` de conjuntos de registros que utilizan la base de datos y se revierten todas las transacciones pendientes. Los conjuntos de `CDatabase` registros que dependen del objeto se dejan en un estado indefinido.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDatabase#12](../../mfc/codesnippet/cpp/cdatabase-class_3.cpp)]

## <a name="cdatabasecommittrans"></a><a name="committrans"></a>CDatabase::CommitTrans

Llame a esta función miembro al completar transacciones.

```
BOOL CommitTrans();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si las actualizaciones se confirmaron correctamente; de lo contrario 0. Si `CommitTrans` se produce un error, el estado del origen de datos es indefinido. Debe comprobar los datos para determinar su estado.

### <a name="remarks"></a>Observaciones

Una transacción consta de una `AddNew` `Edit`serie `Delete`de `Update` llamadas `CRecordset` a las funciones miembro , , y de un objeto que comenzó con una llamada a la [BeginTrans](#begintrans) función miembro. `CommitTrans`confirma la transacción. De forma predeterminada, las actualizaciones se confirman inmediatamente; llamar `BeginTrans` hace que el compromiso `CommitTrans` de las actualizaciones se retrase hasta que se llame.

Hasta que `CommitTrans` llame para finalizar una transacción, puede llamar a la [Rollback](#rollback) función miembro para anular la transacción y dejar el origen de datos en su estado original. Para comenzar una nueva `BeginTrans` transacción, vuelva a llamar.

Para obtener más información acerca de las transacciones, vea el artículo [Transacción (ODBC)](../../data/odbc/transaction-odbc.md).

### <a name="example"></a>Ejemplo

  Consulte el artículo [Transacción: realizar una transacción en un conjunto de registros (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md).

## <a name="cdatabaseexecutesql"></a><a name="executesql"></a>CDatabase::ExecuteSQL

Llame a esta función miembro cuando necesite ejecutar un comando SQL directamente.

```
void ExecuteSQL(LPCTSTR lpszSQL);
```

### <a name="parameters"></a>Parámetros

*lpszSQL*<br/>
Puntero a una cadena terminada en null que contiene un comando SQL válido que se va a ejecutar. Puede pasar un [CString](../../atl-mfc-shared/reference/cstringt-class.md).

### <a name="remarks"></a>Observaciones

Cree el comando como una cadena terminada en null. `ExecuteSQL`no devuelve registros de datos. Si desea operar en registros, utilice un objeto de conjunto de registros en su lugar.

La mayoría de los comandos de un origen de datos se emiten a través de objetos de conjunto de registros, que admiten comandos para seleccionar datos, insertar nuevos registros, eliminar registros y editar registros. Sin embargo, no todas las funciones ODBC son compatibles directamente con las `ExecuteSQL`clases de base de datos, por lo que a veces es posible que necesite realizar una llamada SQL directa con .

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDatabase#13](../../mfc/codesnippet/cpp/cdatabase-class_4.cpp)]

## <a name="cdatabasegetbookmarkpersistence"></a><a name="getbookmarkpersistence"></a>CDatabase::GetBookmarkPersistence

Llame a esta función miembro para averiguar la persistencia de los marcadores en un objeto de conjunto de registros tras determinadas operaciones.

```
DWORD GetBookmarkPersistence() const;
```

### <a name="return-value"></a>Valor devuelto

Máscara de bits que identifica las operaciones en las que los marcadores son persistentes en un objeto de conjunto de registros. Para conocer más detalles, vea la sección Comentarios.

### <a name="remarks"></a>Observaciones

Por ejemplo, si llama a `CRecordset::GetBookmark` y, luego, a `CRecordset::Requery`, es posible que el marcador obtenido de `GetBookmark` ya no sea válido. Debe llamar a `GetBookmarkPersistence` antes de llamar a `CRecordset::SetBookmark`.

En la siguiente tabla se enumeran los valores de máscara de bits que se pueden combinar para el valor devuelto de `GetBookmarkPersistence`.

|Valor de máscara de bits|Persistencia de marcador|
|-------------------|--------------------------|
|SQL_BP_CLOSE|Los marcadores son `Requery` válidos después de una operación.|
|SQL_BP_DELETE|El marcador de una fila `Delete` es válido después de una operación en esa fila.|
|SQL_BP_DROP|Los marcadores son `Close` válidos después de una operación.|
|SQL_BP_SCROLL|Los marcadores son `Move` válidos después de cualquier operación. Esto sencillamente indica si los marcadores se admiten en el conjunto de registros, tal y como devuelve `CRecordset::CanBookmark`.|
|SQL_BP_TRANSACTION|Los marcadores son válidos después de que una transacción se haya confirmado o revertido.|
|SQL_BP_UPDATE|El marcador de una fila `Update` es válido después de una operación en esa fila.|
|SQL_BP_OTHER_HSTMT|Los marcadores asociados con un objeto de conjunto de registros son válidos en un segundo conjunto de registros.|

Para obtener más información acerca de este `SQLGetInfo` valor devuelto, vea la función de API ODBC en el Windows SDK. Para obtener más información acerca de los marcadores, vea el artículo [Conjunto de registros: marcadores y posiciones absolutas (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md).

## <a name="cdatabasegetconnect"></a><a name="getconnect"></a>CDatabase::GetConnect

Llame a esta función miembro para recuperar la cadena de conexión utilizada durante la llamada a `OpenEx` o a `Open` que conectó el objeto `CDatabase` a un origen de datos.

```
const CString GetConnect() const;
```

### <a name="return-value"></a>Valor devuelto

Un **const**[CString](../../atl-mfc-shared/reference/cstringt-class.md) que `OpenEx` contiene `Open` la cadena de conexión si o se ha llamado; de lo contrario, una cadena vacía.

### <a name="remarks"></a>Observaciones

Consulte [CDatabase::Open](#open) para obtener una descripción de cómo se crea la cadena de conexión.

## <a name="cdatabasegetcursorcommitbehavior"></a><a name="getcursorcommitbehavior"></a>CDatabase::GetCursorCommitBehavior

Llame a esta función miembro para determinar cómo una [operación CommitTrans](#committrans) afecta a los cursores en objetos de conjunto de registros abiertos.

```
int GetCursorCommitBehavior() const;
```

### <a name="return-value"></a>Valor devuelto

Valor que indica el efecto de las transacciones en objetos de conjunto de registros abiertos. Para conocer más detalles, vea la sección Comentarios.

### <a name="remarks"></a>Observaciones

En la tabla siguiente se `GetCursorCommitBehavior` enumeran los posibles valores devueltos para y el efecto correspondiente en el conjunto de registros abierto.

|Valor devuelto|Efecto en los objetos CRecordset|
|------------------|----------------------------------|
|SQL_CB_CLOSE|Llame `CRecordset::Requery` inmediatamente después de la confirmación de la transacción.|
|SQL_CB_DELETE|Llame `CRecordset::Close` inmediatamente después de la confirmación de la transacción.|
|SQL_CB_PRESERVE|Proceda normalmente con `CRecordset` las operaciones.|

Para obtener más información acerca de este `SQLGetInfo` valor devuelto, vea la función de API ODBC en el Windows SDK. Para obtener más información acerca de las transacciones, vea el artículo [Transacción (ODBC)](../../data/odbc/transaction-odbc.md).

## <a name="cdatabasegetcursorrollbackbehavior"></a><a name="getcursorrollbackbehavior"></a>CDatabase::GetCursorRollbackBehavior

Llame a esta función miembro para determinar cómo una operación [de reversión](#rollback) afecta a los cursores en objetos de conjunto de registros abiertos.

```
int GetCursorRollbackBehavior() const;
```

### <a name="return-value"></a>Valor devuelto

Valor que indica el efecto de las transacciones en objetos de conjunto de registros abiertos. Para conocer más detalles, vea la sección Comentarios.

### <a name="remarks"></a>Observaciones

En la tabla siguiente se `GetCursorRollbackBehavior` enumeran los posibles valores devueltos para y el efecto correspondiente en el conjunto de registros abierto.

|Valor devuelto|Efecto en los objetos CRecordset|
|------------------|----------------------------------|
|SQL_CB_CLOSE|Llame `CRecordset::Requery` inmediatamente después de la reversión de la transacción.|
|SQL_CB_DELETE|Llame `CRecordset::Close` inmediatamente después de la reversión de la transacción.|
|SQL_CB_PRESERVE|Proceda normalmente con `CRecordset` las operaciones.|

Para obtener más información acerca de este `SQLGetInfo` valor devuelto, vea la función de API ODBC en el Windows SDK. Para obtener más información acerca de las transacciones, vea el artículo [Transacción (ODBC)](../../data/odbc/transaction-odbc.md).

## <a name="cdatabasegetdatabasename"></a><a name="getdatabasename"></a>CDatabase::GetDatabaseName

Llame a esta función miembro para recuperar el nombre de la base de datos conectada actualmente (siempre que el origen de datos define un objeto con nombre denominado "base de datos").

```
CString GetDatabaseName() const;
```

### <a name="return-value"></a>Valor devuelto

Un [CString](../../atl-mfc-shared/reference/cstringt-class.md) que contiene el nombre de la base de datos si se realiza correctamente; de lo `CString`contrario, un . vacío

### <a name="remarks"></a>Observaciones

Esto no es lo mismo que el nombre del origen `OpenEx` `Open` de datos (DSN) especificado en la llamada o. Lo `GetDatabaseName` que devuelve depende de ODBC. En general, una base de datos es una colección de tablas. Si esta entidad tiene `GetDatabaseName` un nombre, lo devuelve.

Por ejemplo, es posible que desee mostrar este nombre en un encabezado. Si se produce un error al `GetDatabaseName` recuperar el `CString`nombre de ODBC, devuelve un archivo .

## <a name="cdatabaseisopen"></a><a name="isopen"></a>CDatabase::IsOpen

Llame a esta función `CDatabase` miembro para determinar si el objeto está conectado actualmente a un origen de datos.

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de `CDatabase` cero si el objeto está conectado actualmente; de lo contrario 0.

## <a name="cdatabasem_hdbc"></a><a name="m_hdbc"></a>CDatabase::m_hdbc

Contiene un identificador público para una conexión de origen de datos ODBC: un "identificador de conexión."

### <a name="remarks"></a>Observaciones

Normalmente, no tendrá necesidad de tener acceso a esta variable miembro directamente. En su lugar, el marco `OpenEx` de `Open`trabajo asigna el identificador cuando se llama o . El marco de trabajo desasigna **delete** el identificador `CDatabase` cuando se llama al operador delete en el objeto. Tenga en `Close` cuenta que la función miembro no desasigna el identificador.

En algunas circunstancias, sin embargo, es posible que deba usar el identificador directamente. Por ejemplo, si necesita llamar a funciones `CDatabase`de la API ODBC directamente en lugar de a través de la clase, es posible que necesite un identificador de conexión para pasar como parámetro. Consulte el ejemplo de código siguiente.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDatabase#15](../../mfc/codesnippet/cpp/cdatabase-class_5.cpp)]

## <a name="cdatabaseonsetoptions"></a><a name="onsetoptions"></a>CDatabase::OnSetOptions

El marco de trabajo llama a esta función miembro al ejecutar directamente una instrucción SQL con la `ExecuteSQL` función miembro.

```
virtual void OnSetOptions(HSTMT hstmt);
```

### <a name="parameters"></a>Parámetros

*hstmt*<br/>
El identificador de instrucción ODBC para el que se establecen las opciones.

### <a name="remarks"></a>Observaciones

`CRecordset::OnSetOptions`también llama a esta función miembro.

`OnSetOptions`establece el valor de tiempo de espera de inicio de sesión. Si ha habido llamadas `SetQueryTimeout` anteriores `OnSetOptions` a la y función miembro, refleja los valores actuales; de lo contrario, establece los valores predeterminados.

> [!NOTE]
> Antes de MFC 4.2, `OnSetOptions` también establezca el modo de procesamiento en snychronous o asincrónico. A partir de MFC 4.2, todas las operaciones son sincrónicas. Para realizar una operación asincrónica, debe realizar una `SQLSetPos`llamada directa a la función de API ODBC.

No es necesario `OnSetOptions` reemplazar para cambiar el valor de tiempo de espera. En su lugar, para personalizar `SetQueryTimeout` el valor de tiempo de espera de consulta, llame antes de crear un conjunto de registros; `OnSetOptions` utilizará el nuevo valor. Los valores establecidos se aplican a las operaciones posteriores en todos los conjuntos de registros o llamadas SQL directas.

Reemplazar `OnSetOptions` si desea establecer opciones adicionales. La invalidación debe `OnSetOptions` llamar a la clase base `SQLSetStmtOption`antes o después de llamar a la función de API ODBC . Siga el método que se muestra en `OnSetOptions`la implementación predeterminada del marco de trabajo de .

## <a name="cdatabaseopen"></a><a name="open"></a>CDatabase::Abierto

Llame a esta función miembro `CDatabase` para inicializar un objeto recién construido.

```
virtual BOOL Open(
    LPCTSTR lpszDSN,
    BOOL bExclusive = FALSE,
    BOOL bReadOnly = FALSE,
    LPCTSTR lpszConnect = _T("ODBC;"),
    BOOL bUseCursorLib = TRUE);
```

### <a name="parameters"></a>Parámetros

*lpszDSN*<br/>
Especifica un nombre de origen de datos: un nombre registrado con ODBC a través del programa Administrador ODBC. Si se especifica un valor DSN en *lpszConnect* (con\<el formato "> de origen de datos DSN"), no se debe especificar de nuevo en *lpszDSN*. En este caso, *lpszDSN* debe ser NULL. De lo contrario, puede pasar NULL si desea presentar al usuario un cuadro de diálogo Origen de datos en el que el usuario puede seleccionar un origen de datos. Para obtener más información, consulte Comentarios.

*bExclusive*<br/>
No se admite en esta versión de la biblioteca de clases. Actualmente, se produce un error en una aserción si este parámetro es TRUE. El origen de datos siempre se abre como compartido (no exclusivo).

*bReadOnly*<br/>
TRUESi desea que la conexión sea de solo lectura y prohíba las actualizaciones del origen de datos. Todos los conjuntos de registros dependientes heredan este atributo. El valor predeterminado es FALSE.

*lpszConnect*<br/>
Especifica una cadena de conexión. La cadena de conexión concatena información, posiblemente incluyendo un nombre de origen de datos, un identificador de usuario válido en el origen de datos, una cadena de autenticación de usuario (contraseña, si el origen de datos requiere uno) y otra información. Toda la cadena de conexión debe ir precedida por la cadena "ODBC;" (mayúsculas o minúsculas). La cadena "ODBC;" se utiliza para indicar que la conexión es a un origen de datos ODBC; esto es para la compatibilidad ascendente cuando las versiones futuras de la biblioteca de clases podrían admitir orígenes de datos que no sean ODBC.

*bUseCursorLib*<br/>
TRUESi desea que se cargue el archivo DLL de la biblioteca de cursores ODBC. La biblioteca de cursores enmascara algunas funciones del controlador ODBC subyacente, lo que impide eficazmente el uso de conjuntos de registros dinámicos (si el controlador los admite). Los únicos cursores admitidos si se carga la biblioteca de cursores son instantáneas estáticas y cursores de solo avance. El valor predeterminado es TRUE. Si tiene previsto crear un `CRecordset` objeto de conjunto de registros directamente desde sin derivar de él, no debe cargar la biblioteca de cursores.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la conexión se realiza correctamente; de lo contrario 0 si el usuario elige Cancelar cuando se presenta un cuadro de diálogo que solicita más información de conexión. En todos los demás casos, el marco de trabajo produce una excepción.

### <a name="remarks"></a>Observaciones

El objeto de base de datos debe inicializarse antes de poder usarlo para construir un objeto de conjunto de registros.

> [!NOTE]
> Llamar a la [OpenEx](#openex) función miembro es la forma preferida de conectarse a un origen de datos e inicializar el objeto de base de datos.

Si los parámetros de la `Open` llamada no contienen suficiente información para realizar la conexión, el controlador ODBC abre un cuadro de diálogo para obtener la información necesaria del usuario. Cuando se `Open`llama a , la cadena de conexión, `CDatabase` *lpszConnect*, se almacena de forma privada en el objeto y está disponible mediante una llamada a la [GetConnect](#getconnect) función miembro.

Si lo desea, puede abrir su propio `Open` cuadro de diálogo antes de llamar para obtener información del usuario, `Open`como una contraseña, y luego agregar esa información a la cadena de conexión que pasa a . O puede que desee guardar la cadena de conexión que pase `Open` para `CDatabase` que pueda reutilizarla la próxima vez que la aplicación llame a un objeto.

También puede utilizar la cadena de conexión para varios `CDatabase` niveles de autorización de inicio de sesión (cada uno para un objeto diferente) o para transmitir otra información específica del origen de datos. Para obtener más información acerca de las cadenas de conexión, consulte el capítulo 5 en el Windows SDK.

Es posible que un intento de conexión apadezca el tiempo de espera si, por ejemplo, el host DBMS no está disponible. Si se produce `Open` un error `CDBException`en el intento de conexión, se produce un archivo .

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDatabase#14](../../mfc/codesnippet/cpp/cdatabase-class_6.cpp)]

## <a name="cdatabaseopenex"></a><a name="openex"></a>CDatabase::OpenEx

Llame a esta función miembro `CDatabase` para inicializar un objeto recién construido.

```
virtual BOOL OpenEx(
    LPCTSTR lpszConnectString,
    DWORD dwOptions = 0);
```

### <a name="parameters"></a>Parámetros

*lpszConnectString*<br/>
Especifica una cadena de conexión ODBC. Esto incluye el nombre del origen de datos, así como otra información opcional, como un ID de usuario y una contraseña. Por ejemplo, "DSN-SQLServer_Source; UID-SA; PWD-abc123" es una cadena de conexión posible. Tenga en cuenta que si pasa NULL para *lpszConnectString*, un cuadro de diálogo Origen de datos pedirá al usuario que seleccione un origen de datos.

*dwOptions*<br/>
Una máscara de bits que especifica una combinación de los siguientes valores. El valor predeterminado es 0, lo que significa que la base de datos se abrirá como compartida con acceso de escritura, el archivo DLL de la biblioteca de cursores ODBC no se cargará y el cuadro de diálogo de conexión ODBC solo se mostrará si no hay suficiente información para realizar la conexión.

- `CDatabase::openExclusive`No se admite en esta versión de la biblioteca de clases. Un origen de datos siempre se abre como compartido (no exclusivo). Actualmente, se produce un error en una aserción si especifica esta opción.

- `CDatabase::openReadOnly`Abra el origen de datos como de solo lectura.

- `CDatabase::useCursorLib`Cargue el archivo DLL de la biblioteca de cursores ODBC. La biblioteca de cursores enmascara algunas funciones del controlador ODBC subyacente, lo que impide eficazmente el uso de conjuntos de registros dinámicos (si el controlador los admite). Los únicos cursores admitidos si se carga la biblioteca de cursores son instantáneas estáticas y cursores de solo avance. Si tiene previsto crear un `CRecordset` objeto de conjunto de registros directamente desde sin derivar de él, no debe cargar la biblioteca de cursores.

- `CDatabase::noOdbcDialog`No muestre el cuadro de diálogo Conexión ODBC, independientemente de si se proporciona suficiente información de conexión.

- `CDatabase::forceOdbcDialog`Mostrar siempre el cuadro de diálogo Conexión ODBC.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la conexión se realiza correctamente; de lo contrario 0 si el usuario elige Cancelar cuando se presenta un cuadro de diálogo que solicita más información de conexión. En todos los demás casos, el marco de trabajo produce una excepción.

### <a name="remarks"></a>Observaciones

El objeto de base de datos debe inicializarse antes de poder usarlo para construir un objeto de conjunto de registros.

Si el parámetro *lpszConnectString* de `OpenEx` la llamada no contiene suficiente información para realizar la conexión, el controlador ODBC abre `CDatabase::noOdbcDialog` `CDatabase::forceOdbcDialog` un cuadro de diálogo para obtener la información necesaria del usuario, siempre que no haya establecido o en el parámetro *dwOptions.* Cuando se `OpenEx`llama a , la cadena de conexión, *lpszConnectString*, se almacena de forma privada en el `CDatabase` objeto y está disponible mediante una llamada a la [GetConnect](#getconnect) función miembro.

Si lo desea, puede abrir su propio `OpenEx` cuadro de diálogo antes de llamar para obtener información del usuario, `OpenEx`como una contraseña, y, a continuación, agregar esa información a la cadena de conexión que pasa a . O puede que desee guardar la cadena de conexión que pase `OpenEx` para `CDatabase` que pueda reutilizarla la próxima vez que la aplicación llame a un objeto.

También puede utilizar la cadena de conexión para varios `CDatabase` niveles de autorización de inicio de sesión (cada uno para un objeto diferente) o para transmitir otra información específica del origen de datos. Para obtener más información acerca de las cadenas de conexión, consulte el capítulo 6 en la *referencia del programador ODBC*.

Es posible que un intento de conexión apadezca el tiempo de espera si, por ejemplo, el host DBMS no está disponible. Si se produce `OpenEx` un error `CDBException`en el intento de conexión, se produce un archivo .

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDatabase#11](../../mfc/codesnippet/cpp/cdatabase-class_7.cpp)]

## <a name="cdatabaserollback"></a><a name="rollback"></a>CDatabase::Rollback

Llame a esta función miembro para invertir los cambios realizados durante una transacción.

```
BOOL Rollback();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la transacción se ha invertido correctamente; de lo contrario 0. Si `Rollback` se produce un error en una llamada, el origen de datos y los estados de transacción son indefinidos. Si `Rollback` devuelve 0, debe comprobar el origen de datos para determinar su estado.

### <a name="remarks"></a>Observaciones

Todas `CRecordset` `AddNew` `Edit`las `Delete`llamadas , , y `Update` ejecutadas desde el último [BeginTrans](#begintrans) se revierten al estado que existía en el momento de esa llamada.

Después de `Rollback`una llamada a , la `BeginTrans` transacción ha terminado y debe llamar de nuevo para otra transacción. El registro que era `BeginTrans` actual antes de llamar `Rollback`se convierte en el registro actual de nuevo después de .

Después de una reversión, el registro que era actual antes de la reversión sigue siendo actual. Para obtener más información sobre el estado del conjunto de registros y el origen de datos después de una reversión, vea el artículo [Transacción (ODBC)](../../data/odbc/transaction-odbc.md).

### <a name="example"></a>Ejemplo

  Consulte el artículo [Transacción: realizar una transacción en un conjunto de registros (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md).

## <a name="cdatabasesetlogintimeout"></a><a name="setlogintimeout"></a>CDatabase::SetLoginTimeout

Llame a esta función `OpenEx` `Open` miembro , antes de llamar o — para invalidar el número predeterminado de segundos permitidos antes de que se agota el tiempo de espera de una conexión de origen de datos intentada.

```
void SetLoginTimeout(DWORD dwSeconds);
```

### <a name="parameters"></a>Parámetros

*dwSeconds*<br/>
El número de segundos que se debe permitir antes de que se agota el tiempo de espera de un intento de conexión.

### <a name="remarks"></a>Observaciones

Un intento de conexión podría agotar el tiempo de espera si, por ejemplo, el DBMS no está disponible. Llame `SetLoginTimeout` después de construir `CDatabase` el objeto `OpenEx` no `Open`inicializado, pero antes de llamar o .

El valor predeterminado para los tiempos de espera de inicio de sesión es 15 segundos. No todos los orígenes de datos admiten la capacidad de especificar un valor de tiempo de espera de inicio de sesión. Si el origen de datos no admite el tiempo de espera, obtendrá la salida de seguimiento, pero no una excepción. Un valor de 0 significa "infinito."

## <a name="cdatabasesetquerytimeout"></a><a name="setquerytimeout"></a>CDatabase::SetQueryTimeout

Llame a esta función miembro para invalidar el número predeterminado de segundos para permitir antes de las operaciones posteriores en el tiempo de espera del origen de datos conectado.

```
void SetQueryTimeout(DWORD dwSeconds);
```

### <a name="parameters"></a>Parámetros

*dwSeconds*<br/>
El número de segundos que se debe permitir antes de que se agota el tiempo de espera de un intento de consulta.

### <a name="remarks"></a>Observaciones

Es posible que se agota el tiempo de espera de una operación debido a problemas de acceso a la red, tiempo excesivo de procesamiento de consultas, etc. Llame `SetQueryTimeout` antes de abrir el conjunto de `AddNew`registros o antes de llamar a las funciones miembro `Update` o `Delete` del conjunto de registros si desea cambiar el valor de tiempo de espera de consulta. La configuración afecta `Open` `AddNew`a `Update`todas `Delete` las llamadas posteriores `CDatabase` , , y a los conjuntos de registros asociados a este objeto. Cambiar el valor de tiempo de espera de consulta para un conjunto de registros después de la apertura no cambia el valor del conjunto de registros. Por ejemplo, `Move` las operaciones posteriores no utilizan el nuevo valor.

El valor predeterminado para los tiempos de espera de consulta es 15 segundos. No todos los orígenes de datos admiten la capacidad de establecer un valor de tiempo de espera de consulta. Si establece un valor de tiempo de espera de consulta de 0, no se produce ningún tiempo de espera; la comunicación con el origen de datos puede dejar de responder. Este comportamiento puede ser útil durante el desarrollo. Si el origen de datos no admite el tiempo de espera, obtendrá la salida de seguimiento, pero no una excepción.

## <a name="see-also"></a>Consulte también

[Clase CObject](../../mfc/reference/cobject-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clase CRecordset](../../mfc/reference/crecordset-class.md)
