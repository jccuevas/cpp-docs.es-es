---
title: CDatabase (clase)
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
ms.openlocfilehash: ebc36d82af9bfe12ab30a86214e58610b5eaab95
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78876302"
---
# <a name="cdatabase-class"></a>CDatabase (clase)

Representa una conexión a un origen de datos, a través de la que puede trabajar con el origen de datos.

## <a name="syntax"></a>Sintaxis

```
class CDatabase : public CObject
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CDatabase:: CDatabase](#cdatabase)|Construye un objeto `CDatabase`. Debe inicializar el objeto llamando a `OpenEx` o `Open`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CDatabase:: BeginTrans](#begintrans)|Inicia una "transacción", una serie de llamadas reversibles a las funciones miembro `AddNew`, `Edit`, `Delete`y `Update` de la clase `CRecordset`, en el origen de datos conectado. El origen de datos debe admitir transacciones para que `BeginTrans` surtan efecto.|
|[CDatabase:: BindParameters](#bindparameters)|Permite enlazar parámetros antes de llamar a `CDatabase::ExecuteSQL`.|
|[CDatabase:: CANCEL](#cancel)|Cancela una operación asincrónica o un proceso de un segundo subproceso.|
|[CDatabase:: CanTransact](#cantransact)|Devuelve un valor distinto de cero si el origen de datos admite transacciones.|
|[CDatabase:: CanUpdate](#canupdate)|Devuelve un valor distinto de cero si el objeto `CDatabase` es actualizable (no es de solo lectura).|
|[CDatabase:: Close](#close)|Cierra la conexión del origen de datos.|
|[CDatabase:: CommitTrans](#committrans)|Completa una transacción iniciada por `BeginTrans`. Los comandos de la transacción que modifican el origen de datos se llevan a cabo.|
|[CDatabase:: ExecuteSQL](#executesql)|Ejecuta una instrucción SQL. No se devuelve ningún registro de datos.|
|[CDatabase:: GetBookmarkPersistence](#getbookmarkpersistence)|Identifica las operaciones a través de las que los marcadores persisten en objetos de conjunto de registros.|
|[CDatabase:: GetConnect](#getconnect)|Devuelve la cadena de conexión ODBC utilizada para conectar el objeto de `CDatabase` a un origen de datos.|
|[CDatabase:: GetCursorCommitBehavior](#getcursorcommitbehavior)|Identifica el efecto de confirmar una transacción en un objeto de conjunto de registros abierto.|
|[CDatabase:: GetCursorRollbackBehavior](#getcursorrollbackbehavior)|Identifica el efecto de revertir una transacción en un objeto de conjunto de registros abierto.|
|[CDatabase:: GetDatabaseName](#getdatabasename)|Devuelve el nombre de la base de datos actualmente en uso.|
|[CDatabase:: IsOpen](#isopen)|Devuelve un valor distinto de cero si el objeto `CDatabase` está conectado actualmente a un origen de datos.|
|[CDatabase:: OnSetOptions](#onsetoptions)|Lo llama el marco de trabajo para establecer las opciones de conexión estándar. La implementación predeterminada establece el valor de tiempo de espera de la consulta. Puede establecer estas opciones con anterioridad llamando a `SetQueryTimeout`.|
|[CDatabase:: Open](#open)|Establece una conexión a un origen de datos (a través de un controlador ODBC).|
|[CDatabase:: OpenEx](#openex)|Establece una conexión a un origen de datos (a través de un controlador ODBC).|
|[CDatabase:: Rollback](#rollback)|Invierte los cambios realizados durante la transacción actual. El origen de datos vuelve a su estado anterior, tal y como se define en la llamada `BeginTrans`, sin modificar.|
|[CDatabase:: SetLoginTimeout](#setlogintimeout)|Establece el número de segundos después del cual se agotará el tiempo de espera de un intento de conexión de origen de datos.|
|[CDatabase:: SetQueryTimeout](#setquerytimeout)|Establece el número de segundos después del cual se agotará el tiempo de espera de las operaciones de consulta de base de datos. Afecta a todas las llamadas subsiguientes `Open`, `AddNew`, `Edit`y `Delete` del conjunto de registros.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CDatabase:: m_hdbc](#m_hdbc)|Identificador de conexión Open Database Connectivity (ODBC) a un origen de datos. Escriba *HDBC*.|

## <a name="remarks"></a>Observaciones

Un origen de datos es una instancia específica de datos hospedada por algún sistema de administración de bases de datos (DBMS). Algunos ejemplos son Microsoft SQL Server, Microsoft Access, Borland dBASE y xBASE. Puede tener uno o más objetos `CDatabase` activos a la vez en la aplicación.

> [!NOTE]
>  Si está trabajando con las clases de objetos de acceso a datos (DAO) en lugar de las clases de conectividad abierta de bases de datos (ODBC), utilice la clase [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) en su lugar. Para obtener más información, vea el artículo [información general sobre la programación de bases de datos](../../data/data-access-programming-mfc-atl.md).

Para usar `CDatabase`, construya un objeto `CDatabase` y llame a su función miembro `OpenEx`. Se abrirá una conexión. Cuando se construyen objetos `CRecordset` para trabajar en el origen de datos conectado, se pasa al constructor de conjunto de registros un puntero al objeto `CDatabase`. Cuando termine de usar la conexión, llame a la función miembro `Close` y destruya el objeto `CDatabase`. `Close` cierra los conjuntos de registros que no se han cerrado previamente.

Para obtener más información acerca de `CDatabase`, vea los artículos [origen de datos (ODBC)](../../data/odbc/data-source-odbc.md) e [información general: programación de bases](../../data/data-access-programming-mfc-atl.md)de datos.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

`CDatabase`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdb. h

##  <a name="begintrans"></a>CDatabase:: BeginTrans

Llame a esta función miembro para iniciar una transacción con el origen de datos conectado.

```
BOOL BeginTrans();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la llamada se realizó correctamente y los cambios se confirman solo manualmente; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

Una transacción se compone de una o más llamadas a las funciones miembro `AddNew`, `Edit`, `Delete`y `Update` de un objeto `CRecordset`. Antes de comenzar una transacción, el objeto de `CDatabase` debe haberse conectado al origen de datos llamando a su función miembro `OpenEx` o `Open`. Para finalizar la transacción, llame a [CommitTrans](#committrans) para aceptar todos los cambios en el origen de datos (y exportarlos) o llame a [Rollback](#rollback) para anular toda la transacción. Llame a `BeginTrans` después de abrir cualquier conjunto de registros implicado en la transacción y lo más cerca posible de las operaciones de actualización reales.

> [!CAUTION]
>  Dependiendo del controlador ODBC, abrir un conjunto de registros antes de llamar a `BeginTrans` puede producir problemas al llamar a `Rollback`. Debe comprobar el controlador específico que está usando. Por ejemplo, al usar el controlador de Microsoft Access incluido en Microsoft ODBC Desktop driver Pack 3,0, debe tener en cuenta el requisito del motor de base de datos Jet de que no debe iniciar una transacción en ninguna base de datos que tenga un cursor abierto. En las clases de base de datos MFC, un cursor abierto significa un objeto de `CRecordset` abierto. Para obtener más información, vea la [Nota técnica 68](../../mfc/tn068-performing-transactions-with-the-microsoft-access-7-odbc-driver.md).

`BeginTrans` también puede bloquear registros de datos en el servidor, en función de la simultaneidad solicitada y las capacidades del origen de datos. Para obtener información sobre el bloqueo de datos, vea el artículo conjunto de registros [: bloquear registros (ODBC)](../../data/odbc/recordset-locking-records-odbc.md).

Las transacciones definidas por el usuario se explican en el artículo [transacción (ODBC)](../../data/odbc/transaction-odbc.md).

`BeginTrans` establece el estado al que se puede revertir (invertir) la secuencia de transacciones. Para establecer un nuevo estado de reversión, confirme cualquier transacción actual y, a continuación, vuelva a llamar a `BeginTrans`.

> [!CAUTION]
>  Llamar a `BeginTrans` de nuevo sin llamar a `CommitTrans` o `Rollback` es un error.

Llame a la función miembro [CanTransact](#cantransact) para determinar si el controlador admite transacciones para una base de datos determinada. También debe llamar a [GetCursorCommitBehavior](#getcursorcommitbehavior) y [GetCursorRollbackBehavior](#getcursorrollbackbehavior) para determinar la compatibilidad con la preservación del cursor.

Para obtener más información acerca de las transacciones, vea el artículo [transacción (ODBC)](../../data/odbc/transaction-odbc.md).

### <a name="example"></a>Ejemplo

  Vea el artículo [transacción: realizar una transacción en un conjunto de registros (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md).

##  <a name="bindparameters"></a>CDatabase:: BindParameters

Invalide `BindParameters` cuando necesite enlazar parámetros antes de llamar a [CDatabase:: ExecuteSQL](#executesql).

```
virtual void BindParameters(HSTMT hstmt);
```

### <a name="parameters"></a>Parámetros

*hstmt*<br/>
Identificador de instrucción ODBC para el que se van a enlazar parámetros.

### <a name="remarks"></a>Observaciones

Este enfoque es útil cuando no se necesita el conjunto de resultados de un procedimiento almacenado.

En la invalidación, llame a `SQLBindParameters` y a las funciones ODBC relacionadas para enlazar los parámetros. MFC llama a la invalidación antes de la llamada a `ExecuteSQL`. No es necesario llamar a `SQLPrepare`; `ExecuteSQL` llama a `SQLExecDirect` y destruye el *hstmt*, que solo se usa una vez.

##  <a name="cancel"></a>CDatabase:: CANCEL

Llame a esta función miembro para solicitar que el origen de datos cancele una operación asincrónica en curso o un proceso de un segundo subproceso.

```
void Cancel();
```

### <a name="remarks"></a>Observaciones

Tenga en cuenta que las clases ODBC de MFC ya no utilizan el procesamiento asincrónico; para realizar una operación asincrónica, debe llamar directamente a la función de la API de ODBC [SQLSetConnectOption](/sql/odbc/reference/syntax/sqlsetconnectoption-function). Para obtener más información, vea el tema que trata sobre [ejecución asincrónica](/sql/odbc/reference/develop-app/asynchronous-execution).

##  <a name="cantransact"></a>CDatabase:: CanTransact

Llame a esta función miembro para determinar si la base de datos permite transacciones.

```
BOOL CanTransact() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si los conjuntos de registros que usan este objeto `CDatabase` permiten transacciones; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

Para obtener información acerca de las transacciones, vea el artículo [transacción (ODBC)](../../data/odbc/transaction-odbc.md).

##  <a name="canupdate"></a>CDatabase:: CanUpdate

Llame a esta función miembro para determinar si el objeto de `CDatabase` permite actualizaciones.

```
BOOL CanUpdate() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el objeto de `CDatabase` permite actualizaciones; de lo contrario, es 0, lo que indica que se pasó TRUE en *bReadOnly* al abrir el objeto `CDatabase` o que el propio origen de datos es de solo lectura. El origen de datos es de solo lectura si una llamada a la función de la API de ODBC `SQLGetInfo` para SQL_DATASOURCE_READ_ONLY devuelve "y".

### <a name="remarks"></a>Observaciones

No todos los controladores admiten actualizaciones.

##  <a name="cdatabase"></a>CDatabase:: CDatabase

Construye un objeto `CDatabase`.

```
CDatabase();
```

### <a name="remarks"></a>Observaciones

Después de construir el objeto, debe llamar a su función miembro `OpenEx` o `Open` para establecer una conexión a un origen de datos especificado.

Puede que le resulte conveniente insertar el objeto de `CDatabase` en la clase de documento.

### <a name="example"></a>Ejemplo

En este ejemplo se muestra el uso de `CDatabase` en una clase derivada de `CDocument`.

[!code-cpp[NVC_MFCDatabase#9](../../mfc/codesnippet/cpp/cdatabase-class_1.h)]

[!code-cpp[NVC_MFCDatabase#10](../../mfc/codesnippet/cpp/cdatabase-class_2.cpp)]

##  <a name="close"></a>CDatabase:: Close

Llame a esta función miembro si desea desconectarse de un origen de datos.

```
virtual void Close();
```

### <a name="remarks"></a>Observaciones

Debe cerrar todos los conjuntos de registros asociados al objeto `CDatabase` antes de llamar a esta función miembro. Dado que `Close` no destruye el objeto `CDatabase`, puede volver a usar el objeto abriendo una nueva conexión al mismo origen de datos o a un origen de datos diferente.

Todas las instrucciones pendientes `AddNew` o `Edit` de conjuntos de registros que usan la base de datos se cancelan y se revierten todas las transacciones pendientes. Los conjuntos de registros que dependan del objeto `CDatabase` quedan en un estado indefinido.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDatabase#12](../../mfc/codesnippet/cpp/cdatabase-class_3.cpp)]

##  <a name="committrans"></a>CDatabase:: CommitTrans

Llame a esta función miembro al completar las transacciones.

```
BOOL CommitTrans();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si las actualizaciones se confirmaron correctamente; de lo contrario, es 0. Si `CommitTrans` produce un error, el estado del origen de datos es indefinido. Debe comprobar los datos para determinar su estado.

### <a name="remarks"></a>Observaciones

Una transacción se compone de una serie de llamadas a las funciones miembro `AddNew`, `Edit`, `Delete`y `Update` de un objeto `CRecordset` que comenzó con una llamada a la función miembro [BeginTrans](#begintrans) . `CommitTrans` confirma la transacción. De forma predeterminada, las actualizaciones se confirman inmediatamente. la llamada a `BeginTrans` provoca que se retrase el compromiso de las actualizaciones hasta que se llame a `CommitTrans`.

Hasta que llame a `CommitTrans` para finalizar una transacción, puede llamar a la función miembro [Rollback](#rollback) para anular la transacción y dejar el origen de datos en su estado original. Para iniciar una nueva transacción, llame de nuevo a `BeginTrans`.

Para obtener más información acerca de las transacciones, vea el artículo [transacción (ODBC)](../../data/odbc/transaction-odbc.md).

### <a name="example"></a>Ejemplo

  Vea el artículo [transacción: realizar una transacción en un conjunto de registros (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md).

##  <a name="executesql"></a>CDatabase:: ExecuteSQL

Llame a esta función miembro cuando necesite ejecutar directamente un comando SQL.

```
void ExecuteSQL(LPCTSTR lpszSQL);
```

### <a name="parameters"></a>Parámetros

*lpszSQL*<br/>
Puntero a una cadena terminada en null que contiene un comando SQL válido que se va a ejecutar. Puede pasar un [CString](../../atl-mfc-shared/reference/cstringt-class.md).

### <a name="remarks"></a>Observaciones

Cree el comando como una cadena terminada en NULL. `ExecuteSQL` no devuelve registros de datos. Si desea trabajar en registros, utilice en su lugar un objeto de conjunto de registros.

La mayoría de los comandos para un origen de datos se emiten a través de objetos de conjunto de registros, que admiten comandos para seleccionar datos, insertar nuevos registros, eliminar registros y editar registros. Sin embargo, no todas las funciones de ODBC son compatibles directamente con las clases de base de datos, por lo que en ocasiones es necesario realizar una llamada SQL directa con `ExecuteSQL`.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDatabase#13](../../mfc/codesnippet/cpp/cdatabase-class_4.cpp)]

##  <a name="getbookmarkpersistence"></a>CDatabase:: GetBookmarkPersistence

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
|SQL_BP_CLOSE|Los marcadores son válidos después de una operación de `Requery`.|
|SQL_BP_DELETE|El marcador de una fila es válido después de una operación de `Delete` en esa fila.|
|SQL_BP_DROP|Los marcadores son válidos después de una operación de `Close`.|
|SQL_BP_SCROLL|Los marcadores son válidos después de cualquier operación de `Move`. Esto sencillamente indica si los marcadores se admiten en el conjunto de registros, tal y como devuelve `CRecordset::CanBookmark`.|
|SQL_BP_TRANSACTION|Los marcadores son válidos después de que una transacción se haya confirmado o revertido.|
|SQL_BP_UPDATE|El marcador de una fila es válido después de una operación de `Update` en esa fila.|
|SQL_BP_OTHER_HSTMT|Los marcadores asociados con un objeto de conjunto de registros son válidos en un segundo conjunto de registros.|

Para obtener más información acerca de este valor devuelto, vea la función de la API de ODBC `SQLGetInfo` en el Windows SDK. Para obtener más información sobre los marcadores, vea el artículo [conjunto de registros: marcadores y posiciones absolutas (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md).

##  <a name="getconnect"></a>CDatabase:: GetConnect

Llame a esta función miembro para recuperar la cadena de conexión utilizada durante la llamada a `OpenEx` o a `Open` que conectó el objeto `CDatabase` a un origen de datos.

```
const CString GetConnect() const;
```

### <a name="return-value"></a>Valor devuelto

Un[CString](../../atl-mfc-shared/reference/cstringt-class.md) const que contiene la cadena de conexión si se ha llamado a `OpenEx` o `Open`; de lo contrario, una cadena vacía.

### <a name="remarks"></a>Observaciones

Vea [CDatabase:: Open](#open) para obtener una descripción de cómo se crea la cadena de conexión.

##  <a name="getcursorcommitbehavior"></a>CDatabase:: GetCursorCommitBehavior

Llame a esta función miembro para determinar cómo afecta una operación de [CommitTrans](#committrans) a los cursores de los objetos de conjunto de registros abiertos.

```
int GetCursorCommitBehavior() const;
```

### <a name="return-value"></a>Valor devuelto

Valor que indica el efecto de las transacciones en los objetos de conjunto de registros abiertos. Para conocer más detalles, vea la sección Comentarios.

### <a name="remarks"></a>Observaciones

En la tabla siguiente se enumeran los posibles valores devueltos para `GetCursorCommitBehavior` y el efecto correspondiente en el conjunto de registros abierto.

|Valor devuelto|Efecto en objetos CRecordset|
|------------------|----------------------------------|
|SQL_CB_CLOSE|Llame a `CRecordset::Requery` inmediatamente después de la confirmación de la transacción.|
|SQL_CB_DELETE|Llame a `CRecordset::Close` inmediatamente después de la confirmación de la transacción.|
|SQL_CB_PRESERVE|Continúe normalmente con las operaciones de `CRecordset`.|

Para obtener más información acerca de este valor devuelto, vea la función de la API de ODBC `SQLGetInfo` en el Windows SDK. Para obtener más información acerca de las transacciones, vea el artículo [transacción (ODBC)](../../data/odbc/transaction-odbc.md).

##  <a name="getcursorrollbackbehavior"></a>CDatabase:: GetCursorRollbackBehavior

Llame a esta función miembro para determinar cómo afecta una operación de [reversión](#rollback) a los cursores de los objetos de conjunto de registros abiertos.

```
int GetCursorRollbackBehavior() const;
```

### <a name="return-value"></a>Valor devuelto

Valor que indica el efecto de las transacciones en los objetos de conjunto de registros abiertos. Para conocer más detalles, vea la sección Comentarios.

### <a name="remarks"></a>Observaciones

En la tabla siguiente se enumeran los posibles valores devueltos para `GetCursorRollbackBehavior` y el efecto correspondiente en el conjunto de registros abierto.

|Valor devuelto|Efecto en objetos CRecordset|
|------------------|----------------------------------|
|SQL_CB_CLOSE|Llame a `CRecordset::Requery` inmediatamente después de la reversión de la transacción.|
|SQL_CB_DELETE|Llame a `CRecordset::Close` inmediatamente después de la reversión de la transacción.|
|SQL_CB_PRESERVE|Continúe normalmente con las operaciones de `CRecordset`.|

Para obtener más información acerca de este valor devuelto, vea la función de la API de ODBC `SQLGetInfo` en el Windows SDK. Para obtener más información acerca de las transacciones, vea el artículo [transacción (ODBC)](../../data/odbc/transaction-odbc.md).

##  <a name="getdatabasename"></a>CDatabase:: GetDatabaseName

Llame a esta función miembro para recuperar el nombre de la base de datos conectada actualmente (siempre que el origen de datos defina un objeto con nombre denominado "Database").

```
CString GetDatabaseName() const;
```

### <a name="return-value"></a>Valor devuelto

Un objeto [CString](../../atl-mfc-shared/reference/cstringt-class.md) que contiene el nombre de la base de datos si se realiza correctamente; de lo contrario, un `CString`vacío.

### <a name="remarks"></a>Observaciones

No es lo mismo que el nombre del origen de datos (DSN) especificado en la llamada `OpenEx` o `Open`. Qué `GetDatabaseName` devuelve depende de ODBC. En general, una base de datos es una colección de tablas. Si esta entidad tiene un nombre, `GetDatabaseName` lo devuelve.

Por ejemplo, puede que desee mostrar este nombre en un encabezado. Si se produce un error al recuperar el nombre de ODBC, `GetDatabaseName` devuelve un `CString`vacío.

##  <a name="isopen"></a>CDatabase:: IsOpen

Llame a esta función miembro para determinar si el objeto `CDatabase` está conectado actualmente a un origen de datos.

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el objeto de `CDatabase` está conectado actualmente; de lo contrario, es 0.

##  <a name="m_hdbc"></a>CDatabase:: m_hdbc

Contiene un identificador público para una conexión de origen de datos ODBC, un "identificador de conexión".

### <a name="remarks"></a>Observaciones

Normalmente, no tendrá que acceder directamente a esta variable miembro. En su lugar, el marco de trabajo asigna el identificador cuando se llama a `OpenEx` o `Open`. El marco de trabajo desasigna el identificador cuando se llama al operador **Delete** en el objeto `CDatabase`. Tenga en cuenta que la función miembro `Close` no cancela la asignación del identificador.

Sin embargo, en algunas circunstancias, puede que tenga que usar el identificador directamente. Por ejemplo, si necesita llamar a funciones de la API de ODBC directamente en lugar de a través de la clase `CDatabase`, puede que necesite un identificador de conexión para pasarlo como parámetro. Vea el ejemplo de código siguiente.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDatabase#15](../../mfc/codesnippet/cpp/cdatabase-class_5.cpp)]

##  <a name="onsetoptions"></a>CDatabase:: OnSetOptions

El marco de trabajo llama a esta función miembro al ejecutar directamente una instrucción SQL con la función miembro `ExecuteSQL`.

```
virtual void OnSetOptions(HSTMT hstmt);
```

### <a name="parameters"></a>Parámetros

*hstmt*<br/>
Identificador de instrucción ODBC para el que se establecen opciones.

### <a name="remarks"></a>Observaciones

`CRecordset::OnSetOptions` también llama a esta función miembro.

`OnSetOptions` establece el valor de tiempo de espera de inicio de sesión. Si ha habido llamadas anteriores a la función miembro `SetQueryTimeout` y, `OnSetOptions` refleja los valores actuales; de lo contrario, establece los valores predeterminados.

> [!NOTE]
>  Antes de MFC 4,2, `OnSetOptions` establecer también el modo de procesamiento en snychronous o Asynchronous. A partir de MFC 4,2, todas las operaciones son sincrónicas. Para realizar una operación asincrónica, debe realizar una llamada directa a la función de la API de ODBC `SQLSetPos`.

No es necesario invalidar `OnSetOptions` para cambiar el valor de tiempo de espera. En su lugar, para personalizar el valor de tiempo de espera de consulta, llame a `SetQueryTimeout` antes de crear un conjunto de registros; `OnSetOptions` usará el nuevo valor. Los valores establecidos se aplican a las operaciones posteriores en todos los conjuntos de registros o llamadas SQL directas.

Invalide `OnSetOptions` si desea establecer opciones adicionales. La invalidación debe llamar a la clase base `OnSetOptions` antes o después de llamar a la función de la API de ODBC `SQLSetStmtOption`. Siga el método que se muestra en la implementación predeterminada del marco de `OnSetOptions`.

##  <a name="open"></a>CDatabase:: Open

Llame a esta función miembro para inicializar un objeto `CDatabase` recién construido.

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
Especifica un nombre de origen de datos, un nombre registrado con ODBC a través del programa de administrador de ODBC. Si se especifica un valor DSN en *lpszConnect* (con el formato "DSN =\<Data-Source >"), no se debe especificar de nuevo en *lpszDSN*. En este caso, *lpszDSN* debe ser null. De lo contrario, puede pasar NULL si desea presentar al usuario un cuadro de diálogo de origen de datos en el que el usuario pueda seleccionar un origen de datos. Para obtener más información, vea la sección Comentarios.

*bExclusive*<br/>
No se admite en esta versión de la biblioteca de clases. Actualmente, se produce un error en una aserción si este parámetro es TRUE. El origen de datos siempre se abre como compartido (no es exclusivo).

*bReadOnly*<br/>
TRUE si desea que la conexión sea de solo lectura y para prohibir las actualizaciones en el origen de datos. Todos los conjuntos de registros dependientes heredan este atributo. El valor predeterminado es FALSE.

*lpszConnect*<br/>
Especifica una cadena de conexión. La cadena de conexión concatena información, que posiblemente incluye un nombre de origen de datos, un identificador de usuario válido en el origen de datos, una cadena de autenticación de usuario (contraseña, si el origen de datos requiere uno) y otra información. La cadena de conexión completa debe ir precedida de la cadena "ODBC;" (en mayúsculas o minúsculas). La cadena "ODBC;" se utiliza para indicar que la conexión es a un origen de datos ODBC; Esto es para la compatibilidad ascendente cuando las versiones futuras de la biblioteca de clases pueden admitir orígenes de datos que no sean de ODBC.

*bUseCursorLib*<br/>
TRUE si desea que se cargue la DLL de la biblioteca de cursores ODBC. La biblioteca de cursores enmascara algunas funciones del controlador ODBC subyacente, lo que impide realmente el uso de dynasets (si el controlador los admite). Los únicos cursores admitidos si se carga la biblioteca de cursores son instantáneas estáticas y cursores de solo avance. El valor predeterminado es TRUE. Si tiene previsto crear un objeto de conjunto de registros directamente desde `CRecordset` sin derivar de él, no debe cargar la biblioteca de cursores.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la conexión se realiza correctamente; de lo contrario, 0 si el usuario elige cancelar cuando se le presenta un cuadro de diálogo que solicita más información de conexión. En todos los demás casos, el marco de trabajo produce una excepción.

### <a name="remarks"></a>Observaciones

El objeto de base de datos debe inicializarse antes de poder usarlo para construir un objeto de conjunto de registros.

> [!NOTE]
>  Llamar a la función miembro [OpenEx](#openex) es el método preferido para conectarse a un origen de datos e inicializar el objeto de base de datos.

Si los parámetros de la llamada de `Open` no contienen suficiente información para realizar la conexión, el controlador ODBC abre un cuadro de diálogo para obtener la información necesaria del usuario. Cuando se llama a `Open`, la cadena de conexión, *lpszConnect*, se almacena de forma privada en el objeto `CDatabase` y está disponible mediante una llamada a la función miembro [GetConnect](#getconnect) .

Si lo desea, puede abrir su propio cuadro de diálogo antes de llamar a `Open` para obtener información del usuario, como una contraseña, y después agregar esa información a la cadena de conexión que pasa a `Open`. O bien, puede que desee guardar la cadena de conexión que se pasa para poder reutilizarla la próxima vez que la aplicación llame a `Open` en un objeto `CDatabase`.

También puede usar la cadena de conexión para varios niveles de autorización de inicio de sesión (cada uno para un objeto de `CDatabase` diferente) o para transmitir otra información específica del origen de datos. Para obtener más información acerca de las cadenas de conexión, vea el capítulo 5 del Windows SDK.

Es posible que se agote el tiempo de espera de un intento de conexión si, por ejemplo, el host de DBMS no está disponible. Si se produce un error en el intento de conexión, `Open` produce una `CDBException`.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDatabase#14](../../mfc/codesnippet/cpp/cdatabase-class_6.cpp)]

##  <a name="openex"></a>CDatabase:: OpenEx

Llame a esta función miembro para inicializar un objeto `CDatabase` recién construido.

```
virtual BOOL OpenEx(
    LPCTSTR lpszConnectString,
    DWORD dwOptions = 0);
```

### <a name="parameters"></a>Parámetros

*lpszConnectString*<br/>
Especifica una cadena de conexión ODBC. Esto incluye el nombre del origen de datos así como otra información opcional, como un identificador de usuario y una contraseña. Por ejemplo, "DSN = SQLServer_Source; UID = SA; PWD = ABC123 "es una cadena de conexión posible. Tenga en cuenta que si pasa NULL para *lpszConnectString*, aparecerá un cuadro de diálogo de origen de datos que le pedirá al usuario que seleccione un origen de datos.

*dwOptions*<br/>
Máscara de máscara que especifica una combinación de los valores siguientes. El valor predeterminado es 0, lo que significa que la base de datos se abrirá como compartida con acceso de escritura, no se cargará la DLL de la biblioteca de cursores ODBC y el cuadro de diálogo conexión ODBC solo se mostrará si no hay suficiente información para realizar la conexión.

- `CDatabase::openExclusive` no se admite en esta versión de la biblioteca de clases. Un origen de datos siempre se abre como compartido (no es exclusivo). Actualmente, se produce un error en una aserción si se especifica esta opción.

- `CDatabase::openReadOnly` abrir el origen de datos como de solo lectura.

- `CDatabase::useCursorLib` cargar el archivo DLL de la biblioteca de cursores ODBC. La biblioteca de cursores enmascara algunas funciones del controlador ODBC subyacente, lo que impide realmente el uso de dynasets (si el controlador los admite). Los únicos cursores admitidos si se carga la biblioteca de cursores son instantáneas estáticas y cursores de solo avance. Si tiene previsto crear un objeto de conjunto de registros directamente desde `CRecordset` sin derivar de él, no debe cargar la biblioteca de cursores.

- `CDatabase::noOdbcDialog` no muestran el cuadro de diálogo conexión ODBC, independientemente de si se proporciona información de conexión suficiente.

- `CDatabase::forceOdbcDialog` Mostrar siempre el cuadro de diálogo de conexión ODBC.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la conexión se realiza correctamente; de lo contrario, 0 si el usuario elige cancelar cuando se le presenta un cuadro de diálogo que solicita más información de conexión. En todos los demás casos, el marco de trabajo produce una excepción.

### <a name="remarks"></a>Observaciones

El objeto de base de datos debe inicializarse antes de poder usarlo para construir un objeto de conjunto de registros.

Si el parámetro *lpszConnectString* de la llamada a `OpenEx` no contiene suficiente información para realizar la conexión, el controlador ODBC abre un cuadro de diálogo para obtener la información necesaria del usuario, siempre que no haya establecido `CDatabase::noOdbcDialog` o `CDatabase::forceOdbcDialog` en el parámetro *dwOptions* . Cuando se llama a `OpenEx`, la cadena de conexión, *lpszConnectString*, se almacena de forma privada en el objeto `CDatabase` y está disponible mediante una llamada a la función miembro [GetConnect](#getconnect) .

Si lo desea, puede abrir su propio cuadro de diálogo antes de llamar a `OpenEx` para obtener información del usuario, como una contraseña, y, a continuación, agregar esa información a la cadena de conexión que pasa a `OpenEx`. O bien, puede que desee guardar la cadena de conexión que se pasa para poder reutilizarla la próxima vez que la aplicación llame a `OpenEx` en un objeto `CDatabase`.

También puede usar la cadena de conexión para varios niveles de autorización de inicio de sesión (cada uno para un objeto de `CDatabase` diferente) o para transmitir otra información específica del origen de datos. Para obtener más información acerca de las cadenas de conexión, vea el capítulo 6 de la *Referencia del programador de ODBC*.

Es posible que se agote el tiempo de espera de un intento de conexión si, por ejemplo, el host de DBMS no está disponible. Si se produce un error en el intento de conexión, `OpenEx` produce una `CDBException`.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDatabase#11](../../mfc/codesnippet/cpp/cdatabase-class_7.cpp)]

##  <a name="rollback"></a>CDatabase:: Rollback

Llame a esta función miembro para invertir los cambios realizados durante una transacción.

```
BOOL Rollback();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la transacción se revirtió correctamente; de lo contrario, es 0. Si se produce un error en una llamada `Rollback`, los Estados de la transacción y el origen de datos son indefinidos. Si `Rollback` devuelve 0, debe comprobar el origen de datos para determinar su estado.

### <a name="remarks"></a>Observaciones

Todas las llamadas `CRecordset` `AddNew`, `Edit`, `Delete`y `Update` ejecutadas desde la última [BeginTrans](#begintrans) se revierten al estado que existía en el momento de la llamada.

Después de una llamada a `Rollback`, la transacción ha finalizado y debe llamar de nuevo a `BeginTrans` para otra transacción. El registro que era actual antes de llamar a `BeginTrans` vuelve a convertirse en el registro actual después de `Rollback`.

Después de una reversión, el registro que era actual antes de la reversión sigue siendo actual. Para obtener más información sobre el estado del conjunto de registros y el origen de datos después de una reversión, vea el artículo [transacción (ODBC)](../../data/odbc/transaction-odbc.md).

### <a name="example"></a>Ejemplo

  Vea el artículo [transacción: realizar una transacción en un conjunto de registros (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md).

##  <a name="setlogintimeout"></a>CDatabase:: SetLoginTimeout

Llame a esta función miembro, antes de llamar a `OpenEx` o `Open`, para invalidar el número predeterminado de segundos permitidos antes de que se agote el tiempo de espera de la conexión de origen de datos.

```
void SetLoginTimeout(DWORD dwSeconds);
```

### <a name="parameters"></a>Parámetros

*dwSeconds*<br/>
Número de segundos que se va a permitir antes de que se agote el tiempo de espera de un intento de conexión.

### <a name="remarks"></a>Observaciones

Un intento de conexión puede agotar el tiempo de espera si, por ejemplo, el DBMS no está disponible. Llame a `SetLoginTimeout` después de construir el objeto de `CDatabase` no inicializado, pero antes de llamar a `OpenEx` o `Open`.

El valor predeterminado de los tiempos de espera de inicio de sesión es de 15 segundos. No todos los orígenes de datos admiten la capacidad de especificar un valor de tiempo de espera de inicio de sesión. Si el origen de datos no admite el tiempo de espera, se obtiene la salida del seguimiento pero no una excepción. Un valor de 0 significa "infinito".

##  <a name="setquerytimeout"></a>CDatabase:: SetQueryTimeout

Llame a esta función miembro para invalidar el número predeterminado de segundos que se va a permitir antes de que se agote el tiempo de espera de las operaciones posteriores en el origen de datos conectado.

```
void SetQueryTimeout(DWORD dwSeconds);
```

### <a name="parameters"></a>Parámetros

*dwSeconds*<br/>
Número de segundos que se va a permitir antes de que se agote el tiempo de espera de un intento de consulta.

### <a name="remarks"></a>Observaciones

Una operación puede agotar el tiempo de espera debido a problemas de acceso a la red, un tiempo de procesamiento excesivo de consultas, etc. Llame a `SetQueryTimeout` antes de abrir el conjunto de registros o antes de llamar a las funciones miembro `AddNew`, `Update` o `Delete` del conjunto de registros si desea cambiar el valor de tiempo de espera de la consulta. La configuración afecta a todas las llamadas subsiguientes `Open`, `AddNew`, `Update`y `Delete` a cualquier conjunto de registros asociado a este objeto `CDatabase`. Cambiar el valor de tiempo de espera de consulta para un conjunto de registros después de abrir no cambia el valor del conjunto de registros. Por ejemplo, las operaciones de `Move` subsiguientes no usan el nuevo valor.

El valor predeterminado de los tiempos de espera de consulta es de 15 segundos. No todos los orígenes de datos admiten la capacidad de establecer un valor de tiempo de espera de consulta. Si establece un valor de tiempo de espera de consulta de 0, no se produce ningún tiempo de espera. la comunicación con el origen de datos puede dejar de responder. Este comportamiento puede ser útil durante el desarrollo. Si el origen de datos no admite el tiempo de espera, se obtiene la salida del seguimiento pero no una excepción.

## <a name="see-also"></a>Consulte también

[CObject (clase)](../../mfc/reference/cobject-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CRecordset (clase)](../../mfc/reference/crecordset-class.md)
