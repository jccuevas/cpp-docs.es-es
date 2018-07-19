---
title: CDatabase (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b28dc721b3131fc413248f6ba4a0b0612176cb67
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2018
ms.locfileid: "37337585"
---
# <a name="cdatabase-class"></a>CDatabase (clase)
Representa una conexión a un origen de datos, a través de la que puede trabajar con el origen de datos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CDatabase : public CObject  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDatabase::CDatabase](#cdatabase)|Construye un objeto `CDatabase`. Debe inicializar el objeto mediante una llamada a `OpenEx` o `Open`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDatabase::BeginTrans](#begintrans)|Inicia una transacción de"", una serie de llamadas reversibles en la `AddNew`, `Edit`, `Delete`, y `Update` funciones miembro de clase `CRecordset` : en el origen de datos conectado. El origen de datos debe admitir transacciones para `BeginTrans` surta efecto.|  
|[CDatabase::BindParameters](#bindparameters)|Le permite enlazar parámetros antes de llamar a `CDatabase::ExecuteSQL`.|  
|[CDatabase::Cancel](#cancel)|Cancela una operación asincrónica o un proceso de un segundo subproceso.|  
|[CDatabase::CanTransact](#cantransact)|Devuelve cero si el origen de datos admite transacciones.|  
|[CDatabase::CanUpdate](#canupdate)|Devuelve cero si el `CDatabase` objeto es actualizable (no de solo lectura).|  
|[CDatabase::Close](#close)|Cierra la conexión de origen de datos.|  
|[CDatabase::CommitTrans](#committrans)|Se completa una transacción iniciada por `BeginTrans`. Los comandos de la transacción que modifica el origen de datos se llevan a cabo.|  
|[CDatabase:: ExecuteSQL](#executesql)|Ejecuta una instrucción SQL. Se devuelve ningún registro de datos.|  
|[CDatabase:: GetBookmarkPersistence](#getbookmarkpersistence)|Identifica las operaciones a través del cual los marcadores son persistentes en los objetos de conjunto de registros.|  
|[CDatabase:: Getconnect](#getconnect)|Devuelve la cadena de conexión ODBC utilizada para conectar el `CDatabase` objeto a un origen de datos.|  
|[CDatabase:: GetCursorCommitBehavior](#getcursorcommitbehavior)|Identifica el efecto de confirmar una transacción en un objeto de conjunto de registros abierto.|  
|[CDatabase:: GetCursorRollbackBehavior](#getcursorrollbackbehavior)|Identifica el efecto de revertir una transacción en un objeto de conjunto de registros abierto.|  
|[CDatabase::GetDatabaseName](#getdatabasename)|Devuelve el nombre de la base de datos actualmente en uso.|  
|[CDatabase::IsOpen](#isopen)|Devuelve cero si el `CDatabase` objeto actualmente está conectado a un origen de datos.|  
|[CDatabase::OnSetOptions](#onsetoptions)|Lo llama el marco de trabajo para establecer las opciones de conexión estándar. La implementación predeterminada establece el valor de tiempo de espera de consulta. Puede establecer estas opciones antes de tiempo mediante una llamada a `SetQueryTimeout`.|  
|[CDatabase:: Open](#open)|Establece una conexión a un origen de datos (a través de un controlador ODBC).|  
|[CDatabase:: OpenEx](#openex)|Establece una conexión a un origen de datos (a través de un controlador ODBC).|  
|[CDatabase::Rollback](#rollback)|Invierte los cambios realizados durante la transacción actual. Devuelve el origen de datos a su estado anterior, tal como se define en el `BeginTrans` llamada, sin modificaciones.|  
|[CDatabase::SetLoginTimeout](#setlogintimeout)|Establece el número de segundos tras el cual un intento de conexión del origen de datos agotará el tiempo.|  
|[CDatabase::SetQueryTimeout](#setquerytimeout)|Establece el número de segundos después de la base de datos de operaciones de consulta agotará el tiempo. Afecta al conjunto de registros posterior `Open`, `AddNew`, `Edit`, y `Delete` llamadas.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDatabase:: M_hdbc](#m_hdbc)|Identificador de conexión de Open Database Connectivity (ODBC) para un origen de datos. Tipo *HDBC*.|  
  
## <a name="remarks"></a>Comentarios  
 Un origen de datos es una instancia específica de datos hospedados por algún sistema de administración de base de datos (DBMS). Algunos ejemplos son Microsoft SQL Server, Microsoft Access, Borland dBASE y xBASE. Puede tener uno o varios `CDatabase` objetos activos a la vez en la aplicación.  
  
> [!NOTE]
>  Si está trabajando con las clases de objetos de acceso a datos (DAO) en lugar de las clases de Open Database Connectivity (ODBC), utilice la clase [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) en su lugar. Para obtener más información, vea el artículo [información general: programación de base de datos](../../data/data-access-programming-mfc-atl.md).  
  
 Para usar `CDatabase`, construir un `CDatabase` objeto y llamar a su `OpenEx` función miembro. Esto abre una conexión. Cuando se construye a continuación, `CRecordset` objetos para operar en el origen de datos conectado, pase al constructor de conjunto de registros de un puntero a su `CDatabase` objeto. Cuando termine de utilizar la conexión, llame a la `Close` miembro de función y destruir el `CDatabase` objeto. `Close` cierra los conjuntos de registros que no se ha cerrado previamente.  
  
 Para obtener más información acerca de `CDatabase`, consulte los artículos [origen de datos (ODBC)](../../data/odbc/data-source-odbc.md) y [información general: programación de base de datos](../../data/data-access-programming-mfc-atl.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CDatabase`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdb.h  
  
##  <a name="begintrans"></a>  CDatabase::BeginTrans  
 Llame a esta función miembro para iniciar una transacción con el origen de datos conectado.  
  
```  
BOOL BeginTrans();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si la llamada se realizó correctamente y se confirman cambios solo manualmente. en caso contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 Una transacción consta de uno o más llamadas a la `AddNew`, `Edit`, `Delete`, y `Update` funciones miembro de un `CRecordset` objeto. Antes de comenzar una transacción, el `CDatabase` objeto debe ya se han conectado al origen de datos mediante una llamada a su `OpenEx` o `Open` función miembro. Para finalizar la transacción, llame a [CommitTrans](#committrans) para aceptar todos los cambios en el origen de datos (y llevarlas a cabo) o llamar a [reversión](#rollback) anular toda la transacción. Llamar a `BeginTrans` después de abrir los conjuntos de registros de la transacción y como real cerca de las operaciones de actualización como sea posible.  
  
> [!CAUTION]
>  Según el controlador ODBC, abrir un conjunto de registros antes de llamar a `BeginTrans` puede causar problemas al llamar a `Rollback`. Debe comprobar el controlador específico que está utilizando. Por ejemplo, cuando se usa el controlador de Microsoft Access que se incluye en el módulo de controlador de Microsoft ODBC Desktop 3.0, debe tener en cuenta para el requisito del motor de base de datos Jet que no debería comenzar una transacción en cualquier base de datos con un cursor abierto. En las clases de base de datos MFC, un cursor abierto significa una apertura `CRecordset` objeto. Para obtener más información, consulte [Nota técnica 68](../../mfc/tn068-performing-transactions-with-the-microsoft-access-7-odbc-driver.md).  
  
 `BeginTrans` También se pueden bloquear los registros de datos en el servidor, dependiendo de la simultaneidad solicitada y las capacidades del origen de datos. Para obtener información acerca de los datos de bloqueos, consulte el artículo [conjunto de registros: bloquear registros (ODBC)](../../data/odbc/recordset-locking-records-odbc.md).  
  
 Las transacciones definidas por el usuario se explican en el artículo [transacción (ODBC)](../../data/odbc/transaction-odbc.md).  
  
 `BeginTrans` establece el estado al que la secuencia de transacciones se puede deshacer (revertir). Para establecer un nuevo estado de reversión, confirmar cualquier transacción actual, a continuación, llame a `BeginTrans` nuevo.  
  
> [!CAUTION]
>  Una llamada a `BeginTrans` nuevo sin llamar a `CommitTrans` o `Rollback` es un error.  
  
 Llame a la [CanTransact](#cantransact) función miembro para determinar si el controlador admite las transacciones para una base de datos. También se debe llamar a [GetCursorCommitBehavior](#getcursorcommitbehavior) y [GetCursorRollbackBehavior](#getcursorrollbackbehavior) para determinar la compatibilidad para conservar el cursor.  
  
 Para obtener más información acerca de las transacciones, vea el artículo [transacción (ODBC)](../../data/odbc/transaction-odbc.md).  
  
### <a name="example"></a>Ejemplo  
  Consulte el artículo [transacción: realizar una transacción en un conjunto de registros (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md).  
  
##  <a name="bindparameters"></a>  CDatabase::BindParameters  
 Invalidar `BindParameters` cuando necesita enlazar parámetros antes de llamar a [CDatabase:: ExecuteSQL](#executesql).  
  
```  
virtual void BindParameters(HSTMT hstmt);
```  
  
### <a name="parameters"></a>Parámetros  
 *HStmt*  
 El identificador de instrucción ODBC para el que desea enlazar parámetros.  
  
### <a name="remarks"></a>Comentarios  
 Este enfoque es útil cuando el resultado no es necesario establecer desde un procedimiento almacenado.  
  
 En la invalidación, llame a `SQLBindParameters` y relacionados con las funciones ODBC para enlazar los parámetros. MFC llama a la invalidación antes de la llamada a `ExecuteSQL`. No es necesario llamar a `SQLPrepare`; `ExecuteSQL` llamadas `SQLExecDirect` y destruye el *hstmt*, que se usa una sola vez.  
  
##  <a name="cancel"></a>  CDatabase::Cancel  
 Llame a esta función miembro para solicitar que el origen de datos se cancela una operación asincrónica en curso o un proceso de un segundo subproceso.  
  
```  
void Cancel();
```  
  
### <a name="remarks"></a>Comentarios  
 Tenga en cuenta que las clases ODBC de MFC ya no usan el procesamiento asincrónico; para llevar a cabo una operación asincrónica, se debe llamar directamente a la función de la API de ODBC [SQLSetConnectOption](https://msdn.microsoft.com/library/ms713564.aspx). Para obtener más información, consulte [ejecución asincrónica](https://msdn.microsoft.com/library/ms713563.aspx) en el SDK de Windows.  
  
##  <a name="cantransact"></a>  CDatabase::CanTransact  
 Llame a esta función miembro para determinar si la base de datos permite que las transacciones.  
  
```  
BOOL CanTransact() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si los conjuntos de registros mediante este `CDatabase` objeto permitir transacciones; de lo contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener información acerca de las transacciones, vea el artículo [transacción (ODBC)](../../data/odbc/transaction-odbc.md).  
  
##  <a name="canupdate"></a>  CDatabase::CanUpdate  
 Llame a esta función miembro para determinar si el `CDatabase` objeto permite realizar actualizaciones.  
  
```  
BOOL CanUpdate() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el `CDatabase` objeto permite actualizaciones; de lo contrario, 0, indicando que cualquiera que se pasa TRUE *bReadOnly* cuando abrió el `CDatabase` objeto o que el origen de datos propio es de solo lectura. El origen de datos es de solo lectura si una llamada a la función de la API de ODBC `SQLGetInfo` para SQL_DATASOURCE_READ_ONLY devuelve "s".  
  
### <a name="remarks"></a>Comentarios  
 No todos los controladores admiten las actualizaciones.  
  
##  <a name="cdatabase"></a>  CDatabase::CDatabase  
 Construye un objeto `CDatabase`.  
  
```  
CDatabase();
```  
  
### <a name="remarks"></a>Comentarios  
 Después de crear el objeto, se debe llamar a su `OpenEx` o `Open` función miembro para establecer una conexión a un origen de datos especificado.  
  
 Quizá le resulte conveniente incrustar la `CDatabase` objeto en la clase de documento.  
  
### <a name="example"></a>Ejemplo  
 En este ejemplo se muestra cómo utilizar `CDatabase` en un `CDocument`-clase derivada.  
  
 [!code-cpp[NVC_MFCDatabase#9](../../mfc/codesnippet/cpp/cdatabase-class_1.h)]  
  
 [!code-cpp[NVC_MFCDatabase#10](../../mfc/codesnippet/cpp/cdatabase-class_2.cpp)]  
  
##  <a name="close"></a>  CDatabase::Close  
 Llame a esta función miembro si desea desconectarse de un origen de datos.  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>Comentarios  
 Debe cerrar los conjuntos de registros asociados con la `CDatabase` antes de llamar a esta función miembro de objeto. Dado que `Close` no destruye el `CDatabase` de objeto, puede volver a usar el objeto abriendo una nueva conexión con el mismo origen de datos o un origen de datos diferente.  
  
 Todas las pendientes `AddNew` o `Edit` se cancelan las instrucciones de uso de la base de datos de conjuntos de registros y se revierten todas las transacciones pendientes. Los conjuntos de registros depende de la `CDatabase` objeto quedan en un estado indefinido.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDatabase#12](../../mfc/codesnippet/cpp/cdatabase-class_3.cpp)]  
  
##  <a name="committrans"></a>  CDatabase::CommitTrans  
 Llame a esta función de miembro al completarse las transacciones.  
  
```  
BOOL CommitTrans();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si las actualizaciones se confirmaron correctamente; en caso contrario, es 0. Si `CommitTrans` se produce un error, el estado del origen de datos no está definido. Debe comprobar los datos para determinar su estado.  
  
### <a name="remarks"></a>Comentarios  
 Una transacción consta de una serie de llamadas a la `AddNew`, `Edit`, `Delete`, y `Update` funciones miembro de un `CRecordset` objeto que se inició con una llamada a la [BeginTrans](#begintrans) función miembro. `CommitTrans` Confirma la transacción. De forma predeterminada, las actualizaciones se confirman inmediatamente; una llamada a `BeginTrans` hace que se retrasa hasta el compromiso de actualizaciones `CommitTrans` se llama.  
  
 Hasta que llame a `CommitTrans` para finalizar una transacción, puede llamar a la [reversión](#rollback) función miembro para anular la transacción y dejar el origen de datos en su estado original. Para comenzar una nueva transacción, llame a `BeginTrans` nuevo.  
  
 Para obtener más información acerca de las transacciones, vea el artículo [transacción (ODBC)](../../data/odbc/transaction-odbc.md).  
  
### <a name="example"></a>Ejemplo  
  Consulte el artículo [transacción: realizar una transacción en un conjunto de registros (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md).  
  
##  <a name="executesql"></a>  CDatabase:: ExecuteSQL  
 Llame a esta función miembro cuando se necesita ejecutar un comando SQL directamente.  
  
```  
void ExecuteSQL(LPCTSTR lpszSQL);
```  
  
### <a name="parameters"></a>Parámetros  
 *lpszSQL*  
 Puntero a una cadena terminada en null que contiene un comando SQL válido. Puede pasar un [CString](../../atl-mfc-shared/reference/cstringt-class.md).  
  
### <a name="remarks"></a>Comentarios  
 Crear el comando como una cadena terminada en null. `ExecuteSQL` no devuelve los registros de datos. Si desea operar en los registros, use un objeto de conjunto de registros en su lugar.  
  
 La mayoría de los comandos para un origen de datos se emite a través de los objetos de conjunto de registros, que son compatibles con los comandos para seleccionar datos, insertar nuevos registros, la eliminación de registros y editar registros. Sin embargo, no toda la funcionalidad ODBC es directamente compatible con las clases de base de datos, por lo que a veces es posible que deba realizar una llamada directa de SQL con `ExecuteSQL`.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDatabase#13](../../mfc/codesnippet/cpp/cdatabase-class_4.cpp)]  
  
##  <a name="getbookmarkpersistence"></a>  CDatabase:: GetBookmarkPersistence  
 Llame a esta función miembro para averiguar la persistencia de los marcadores en un objeto de conjunto de registros tras determinadas operaciones.  
  
```  
DWORD GetBookmarkPersistence() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Máscara de bits que identifica las operaciones en las que los marcadores son persistentes en un objeto de conjunto de registros. Para conocer más detalles, vea la sección Comentarios.  
  
### <a name="remarks"></a>Comentarios  
 Por ejemplo, si llama a `CRecordset::GetBookmark` y, luego, a `CRecordset::Requery`, es posible que el marcador obtenido de `GetBookmark` ya no sea válido. Debe llamar a `GetBookmarkPersistence` antes de llamar a `CRecordset::SetBookmark`.  
  
 En la siguiente tabla se enumeran los valores de máscara de bits que se pueden combinar para el valor devuelto de `GetBookmarkPersistence`.  
  
|Valor de máscara de bits|Persistencia de marcador|  
|-------------------|--------------------------|  
|SQL_BP_CLOSE|Los marcadores son válidos tras una `Requery` operación.|  
|SQL_BP_DELETE|El marcador de una fila es válido tras una `Delete` operación en esa fila.|  
|SQL_BP_DROP|Los marcadores son válidos tras una `Close` operación.|  
|SQL_BP_SCROLL|Los marcadores son válidos después de cualquier `Move` operación. Esto sencillamente indica si los marcadores se admiten en el conjunto de registros, tal y como devuelve `CRecordset::CanBookmark`.|  
|SQL_BP_TRANSACTION|Los marcadores son válidos después de que una transacción se haya confirmado o revertido.|  
|SQL_BP_UPDATE|El marcador de una fila es válido tras una `Update` operación en esa fila.|  
|SQL_BP_OTHER_HSTMT|Los marcadores asociados con un objeto de conjunto de registros son válidos en un segundo conjunto de registros.|  
  
 Para obtener más información acerca de este valor devuelto, vea la función de API de ODBC `SQLGetInfo` en el SDK de Windows. Para obtener más información acerca de los marcadores, vea el artículo [conjunto de registros: marcadores y posiciones absolutas (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md).  
  
##  <a name="getconnect"></a>  CDatabase:: Getconnect  
 Llame a esta función miembro para recuperar la cadena de conexión utilizada durante la llamada a `OpenEx` o a `Open` que conectó el objeto `CDatabase` a un origen de datos.  
  
```  
const CString GetConnect() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un **const**[CString](../../atl-mfc-shared/reference/cstringt-class.md) que contiene la cadena de conexión si `OpenEx` o `Open` se ha llamado; de lo contrario, una cadena vacía.  
  
### <a name="remarks"></a>Comentarios  
 Consulte [CDatabase:: Open](#open) para obtener una descripción de cómo se crea la cadena de conexión.  
  
##  <a name="getcursorcommitbehavior"></a>  CDatabase:: GetCursorCommitBehavior  
 Llame a esta función miembro para determinar cómo un [CommitTrans](#committrans) operación afecta a los cursores en los objetos de conjunto de registros abierto.  
  
```  
int GetCursorCommitBehavior() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor que indica el efecto de las transacciones en los objetos de conjunto de registros abierto. Para conocer más detalles, vea la sección Comentarios.  
  
### <a name="remarks"></a>Comentarios  
 La tabla siguiente enumeran los posibles valores devueltos para `GetCursorCommitBehavior` y el efecto correspondiente en el conjunto de registros abierto.  
  
|Valor devuelto|Efecto en CRecordset (objetos)|  
|------------------|----------------------------------|  
|SQL_CB_CLOSE|Llamar a `CRecordset::Requery` inmediatamente después de la confirmación de transacción.|  
|SQL_CB_DELETE|Llamar a `CRecordset::Close` inmediatamente después de la confirmación de transacción.|  
|SQL_CB_PRESERVE|Continúe normalmente con `CRecordset` operaciones.|  
  
 Para obtener más información acerca de este valor devuelto, vea la función de API de ODBC `SQLGetInfo` en el SDK de Windows. Para obtener más información acerca de las transacciones, vea el artículo [transacción (ODBC)](../../data/odbc/transaction-odbc.md).  
  
##  <a name="getcursorrollbackbehavior"></a>  CDatabase:: GetCursorRollbackBehavior  
 Llame a esta función miembro para determinar cómo un [reversión](#rollback) operación afecta a los cursores en los objetos de conjunto de registros abierto.  
  
```  
int GetCursorRollbackBehavior() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor que indica el efecto de las transacciones en los objetos de conjunto de registros abierto. Para conocer más detalles, vea la sección Comentarios.  
  
### <a name="remarks"></a>Comentarios  
 La tabla siguiente enumeran los posibles valores devueltos para `GetCursorRollbackBehavior` y el efecto correspondiente en el conjunto de registros abierto.  
  
|Valor devuelto|Efecto en CRecordset (objetos)|  
|------------------|----------------------------------|  
|SQL_CB_CLOSE|Llamar a `CRecordset::Requery` inmediatamente después de la reversión de transacciones.|  
|SQL_CB_DELETE|Llamar a `CRecordset::Close` inmediatamente después de la reversión de transacciones.|  
|SQL_CB_PRESERVE|Continúe normalmente con `CRecordset` operaciones.|  
  
 Para obtener más información acerca de este valor devuelto, vea la función de API de ODBC `SQLGetInfo` en el SDK de Windows. Para obtener más información acerca de las transacciones, vea el artículo [transacción (ODBC)](../../data/odbc/transaction-odbc.md).  
  
##  <a name="getdatabasename"></a>  CDatabase::GetDatabaseName  
 Llame a esta función miembro para recuperar el nombre de la base de datos conectada (siempre que el origen de datos define un objeto con nombre denominado "base de datos").  
  
```  
CString GetDatabaseName() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un [CString](../../atl-mfc-shared/reference/cstringt-class.md) que contiene el nombre de la base de datos si es correcto; en caso contrario, un valor vacío `CString`.  
  
### <a name="remarks"></a>Comentarios  
 Esto no es el mismo que el nombre de origen de datos (DSN) especificado en el `OpenEx` o `Open` llamar. ¿Qué `GetDatabaseName` devuelve depende de ODBC. En general, una base de datos es una colección de tablas. Si esta entidad tiene un nombre, `GetDatabaseName` lo devuelve.  
  
 Por ejemplo, podría mostrar este nombre en un encabezado. Si se produce un error al recuperar el nombre de ODBC, `GetDatabaseName` devuelve un valor vacío `CString`.  
  
##  <a name="isopen"></a>  CDatabase::IsOpen  
 Llame a esta función miembro para determinar si el `CDatabase` objeto actualmente está conectado a un origen de datos.  
  
```  
BOOL IsOpen() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el `CDatabase` objeto actualmente está conectado; en caso contrario, 0.  
  
##  <a name="m_hdbc"></a>  CDatabase:: M_hdbc  
 Contiene un identificador público de una conexión de origen de datos ODBC, un "identificador de conexión".  
  
### <a name="remarks"></a>Comentarios  
 Normalmente, no tendrá acceso directamente a esta variable de miembro es necesario. En su lugar, el marco de trabajo asigna el identificador cuando se llama a `OpenEx` o `Open`. El marco de trabajo desasigna el identificador cuando se llama a la **eliminar** operador en la `CDatabase` objeto. Tenga en cuenta que el `Close` función miembro desasignar el identificador.  
  
 Sin embargo, en algunas circunstancias, es posible que debe usar directamente el identificador. Por ejemplo, si tiene que llamar a funciones API de ODBC directamente en lugar de a través de la clase `CDatabase`, necesita un identificador de conexión para pasar como parámetro. Vea el ejemplo de código siguiente.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDatabase#15](../../mfc/codesnippet/cpp/cdatabase-class_5.cpp)]  
  
##  <a name="onsetoptions"></a>  CDatabase::OnSetOptions  
 El marco llama a esta función miembro cuando se ejecuta directamente una instrucción SQL con el `ExecuteSQL` función miembro.  
  
```  
virtual void OnSetOptions(HSTMT hstmt);
```  
  
### <a name="parameters"></a>Parámetros  
 *HStmt*  
 El identificador de instrucción ODBC para el que se establecen las opciones.  
  
### <a name="remarks"></a>Comentarios  
 `CRecordset::OnSetOptions` También se llama a esta función miembro.  
  
 `OnSetOptions` establece el valor de tiempo de espera de inicio de sesión. Si ha habido las llamadas anteriores a la `SetQueryTimeout` y la función miembro, `OnSetOptions` refleja los valores actuales; de lo contrario, Establece los valores predeterminados.  
  
> [!NOTE]
>  Antes de MFC 4.2, `OnSetOptions` también establece el modo de procesamiento para cualquier snychronous o asincrónicas. A partir de MFC 4.2, todas las operaciones son sincrónicas. Para llevar a cabo una operación asincrónica, debe realizar una llamada directa a la función de la API de ODBC `SQLSetPos`.  
  
 No es necesario invalidar `OnSetOptions` para cambiar el valor de tiempo de espera. En su lugar, para personalizar el valor de tiempo de espera de consulta, llame a `SetQueryTimeout` antes de crear un conjunto de registros; `OnSetOptions` usarán el nuevo valor. Los valores establecidos se aplican a las operaciones siguientes en todos los conjuntos de registros o llamadas directas a SQL.  
  
 Invalidar `OnSetOptions` si desea establecer opciones adicionales. La invalidación debe llamar a la clase base `OnSetOptions` antes o después de llamar a la función de la API de ODBC `SQLSetStmtOption`. Siga el método que se muestra en la implementación de predeterminada de .NET framework de `OnSetOptions`.  
  
##  <a name="open"></a>  CDatabase:: Open  
 Llame a esta función miembro para inicializar un recientemente construido `CDatabase` objeto.  
  
```  
virtual BOOL Open(
    LPCTSTR lpszDSN,  
    BOOL bExclusive = FALSE,  
    BOOL bReadOnly = FALSE,  
    LPCTSTR lpszConnect = _T("ODBC;"),  
    BOOL bUseCursorLib = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 *lpszDSN*  
 Especifica un nombre de origen de datos, registrado un nombre con ODBC a través del programa de administrador de ODBC. Si se especifica un valor DSN en *lpszConnect* (en el formulario "DSN =\<origen de datos >"), no debe especificarse en *lpszDSN*. En este caso, *lpszDSN* debe ser NULL. En caso contrario, puede pasar NULL si desea presentar al usuario un cuadro de diálogo origen de datos en el que el usuario puede seleccionar un origen de datos. Para obtener más información, vea la sección Comentarios.  
  
 *bExclusive*  
 No se admite en esta versión de la biblioteca de clases. Actualmente, se produce un error en una aserción si este parámetro es TRUE. El origen de datos siempre se abre como compartido (no exclusivo).  
  
 *bReadOnly*  
 TRUE si desea que la conexión sea de solo lectura y se va a prohibir las actualizaciones al origen de datos. Todos los conjuntos de registros dependientes heredan este atributo. El valor predeterminado es FALSE.  
  
 *lpszConnect*  
 Especifica una cadena de conexión. La cadena de conexión concatena información, posiblemente con un nombre de origen de datos, un identificador de usuario válido en el origen de datos, una cadena de autenticación de usuario (la contraseña, si el origen de datos requiere uno) y otra información. La cadena de conexión completo debe ir precedida por la cadena "ODBC;" (en mayúsculas o minúsculas). "ODBC;" cadena se usa para indicar que la conexión es a un origen de datos ODBC; Esto es para la compatibilidad con versiones futuras versiones de la biblioteca de clases podrían admite orígenes de datos que no son ODBC.  
  
 *bUseCursorLib*  
 TRUE si desea que la DLL de biblioteca de Cursor ODBC que se cargue. La biblioteca de cursores enmascara alguna funcionalidad del controlador ODBC subyacente, evitando así el uso de conjuntos de registros dinámicos (si el controlador es compatible con ellos). Los cursores solo admitidos si se carga la biblioteca de cursores son instantáneas estáticas y cursores de solo avance. El valor predeterminado es TRUE. Si va a crear un objeto de conjunto de registros directamente desde `CRecordset` sin derivados de él, no debe cargar la biblioteca de cursores.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si la conexión se realiza correctamente; en caso contrario, 0 si el usuario elige Cancelar cuando aparezca un cuadro de diálogo que pregunta para obtener más información de conexión. En todos los demás casos, el marco de trabajo produce una excepción.  
  
### <a name="remarks"></a>Comentarios  
 El objeto de base de datos debe inicializarse antes de que se puede usar para construir un objeto de conjunto de registros.  
  
> [!NOTE]
>  Una llamada a la [OpenEx](#openex) función miembro es la mejor manera de conectarse a un origen de datos e inicializar el objeto de base de datos.  
  
 Si los parámetros en su `Open` llamada no contienen información suficiente para realizar la conexión, el controlador ODBC abre un cuadro de diálogo para obtener la información necesaria del usuario. Cuando se llama a `Open`, la cadena de conexión, *lpszConnect*, se almacena de forma privada en el `CDatabase` de objetos y está disponible mediante una llamada a la [GetConnect](#getconnect) función miembro.  
  
 Si lo desea, puede abrir su propio cuadro de diálogo antes de llamar a `Open` para obtener información del usuario, como una contraseña, a continuación, agregue dicha información a la cadena de conexión se pasa a `Open`. O es posible que desee guardar la cadena de conexión que pase por lo que se puede reutilizar la próxima vez su aplicación llama `Open` en un `CDatabase` objeto.  
  
 También puede usar la cadena de conexión de varios niveles de autorización de inicio de sesión (cada uno de otro `CDatabase` objeto) o transmitir otra información específica del origen de datos. Para obtener más información acerca de las cadenas de conexión, consulte el capítulo 5 en el SDK de Windows.  
  
 Es posible que un intento de conexión en tiempo de espera si, por ejemplo, el host DBMS no está disponible. Si se produce un error en el intento de conexión, `Open` produce una `CDBException`.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDatabase#14](../../mfc/codesnippet/cpp/cdatabase-class_6.cpp)]  
  
##  <a name="openex"></a>  CDatabase:: OpenEx  
 Llame a esta función miembro para inicializar un recientemente construido `CDatabase` objeto.  
  
```  
virtual BOOL OpenEx(
    LPCTSTR lpszConnectString,  
    DWORD dwOptions = 0);
```  
  
### <a name="parameters"></a>Parámetros  
 *lpszConnectString*  
 Especifica una cadena de conexión ODBC. Esto incluye el nombre del origen de datos, así como otra información opcional, como un Id. de usuario y una contraseña. Por ejemplo, "DSN = SQLServer_Source; UID = SA; PWD = abc123 "es una cadena de conexión posible. Tenga en cuenta que si se pasa NULL para *lpszConnectString*, un cuadro de diálogo origen de datos le pedirá al usuario seleccionar un origen de datos.  
  
 *dwOptions*  
 Máscara de bits que especifica una combinación de los siguientes valores. El valor predeterminado es 0, lo que significa que la base de datos se abrirá como compartido con acceso de escritura, no se cargará la DLL de biblioteca de cursores ODBC y se mostrará el cuadro de diálogo de conexión de ODBC solo si no hay suficiente información para realizar la conexión.  
  
- `CDatabase::openExclusive` No se admite en esta versión de la biblioteca de clases. Un origen de datos siempre se abre como compartido (no exclusivo). Actualmente, se produce un error en una aserción si especifica esta opción.  
  
- `CDatabase::openReadOnly` Abra el origen de datos como de solo lectura.  
  
- `CDatabase::useCursorLib` Cargar la biblioteca de cursores ODBC DLL. La biblioteca de cursores enmascara alguna funcionalidad del controlador ODBC subyacente, evitando así el uso de conjuntos de registros dinámicos (si el controlador es compatible con ellos). Los cursores solo admitidos si se carga la biblioteca de cursores son instantáneas estáticas y cursores de solo avance. Si va a crear un objeto de conjunto de registros directamente desde `CRecordset` sin derivados de él, no debe cargar la biblioteca de cursores.  
  
- `CDatabase::noOdbcDialog` No mostrar el cuadro de diálogo de conexión ODBC, independientemente de si se proporciona suficiente información de conexión.  
  
- `CDatabase::forceOdbcDialog` Mostrar siempre el cuadro de diálogo de conexión de ODBC.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si la conexión se realiza correctamente; en caso contrario, 0 si el usuario elige Cancelar cuando aparezca un cuadro de diálogo que pregunta para obtener más información de conexión. En todos los demás casos, el marco de trabajo produce una excepción.  
  
### <a name="remarks"></a>Comentarios  
 El objeto de base de datos debe inicializarse antes de que se puede usar para construir un objeto de conjunto de registros.  
  
 Si el *lpszConnectString* parámetro en su `OpenEx` llamada no contiene información suficiente para realizar la conexión, el controlador ODBC abre un cuadro de diálogo para obtener la información necesaria del usuario, siempre que no disponga de establecer `CDatabase::noOdbcDialog` o `CDatabase::forceOdbcDialog` en el *dwOptions* parámetro. Cuando se llama a `OpenEx`, la cadena de conexión, *lpszConnectString*, se almacena de forma privada en el `CDatabase` de objetos y está disponible mediante una llamada a la [GetConnect](#getconnect) función miembro.  
  
 Si lo desea, puede abrir su propio cuadro de diálogo antes de llamar a `OpenEx` para obtener información del usuario, como una contraseña y, a continuación, agregar esa información a la cadena de conexión se pasa a `OpenEx`. O es posible que desee guardar la cadena de conexión que pase por lo que se puede reutilizar la próxima vez su aplicación llama `OpenEx` en un `CDatabase` objeto.  
  
 También puede usar la cadena de conexión de varios niveles de autorización de inicio de sesión (cada uno de otro `CDatabase` objeto) o transmitir otra información específica del origen de datos. Para obtener más información acerca de las cadenas de conexión, consulte el capítulo 6 en el *referencia del programador de ODBC*.  
  
 Es posible que un intento de conexión en tiempo de espera si, por ejemplo, el host DBMS no está disponible. Si se produce un error en el intento de conexión, `OpenEx` produce una `CDBException`.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDatabase#11](../../mfc/codesnippet/cpp/cdatabase-class_7.cpp)]  
  
##  <a name="rollback"></a>  CDatabase::Rollback  
 Llame a esta función miembro para revertir los cambios realizados durante una transacción.  
  
```  
BOOL Rollback();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si se ha revertido la transacción; en caso contrario, es 0. Si un `Rollback` llamada produce un error, el origen de datos y transacciones estados son indefinidos. Si `Rollback` devuelve 0, debe comprobar el origen de datos para determinar su estado.  
  
### <a name="remarks"></a>Comentarios  
 Todos los `CRecordset` `AddNew`, `Edit`, `Delete`, y `Update` llamadas ejecutadas desde la última [BeginTrans](#begintrans) se revierten al estado que existía en el momento de esa llamada.  
  
 Después de llamar a `Rollback`, la transacción está por encima y se debe llamar a `BeginTrans` nuevamente por otra transacción. El registro que era el actual antes de llamar `BeginTrans` se convierte en el registro actual a intentarlo después de `Rollback`.  
  
 Después de una operación de reversión, el registro que era el actual antes de la reversión permanece actual. Para obtener más información sobre el estado del conjunto de registros y el origen de datos después de una operación de reversión, consulte el artículo [transacción (ODBC)](../../data/odbc/transaction-odbc.md).  
  
### <a name="example"></a>Ejemplo  
  Consulte el artículo [transacción: realizar una transacción en un conjunto de registros (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md).  
  
##  <a name="setlogintimeout"></a>  CDatabase::SetLoginTimeout  
 Llame a esta función miembro, antes de llamar a `OpenEx` o `Open` : reemplazar el número predeterminado de segundos que se permiten antes de un intento de datos origen conexión agote el tiempo.  
  
```  
void SetLoginTimeout(DWORD dwSeconds);
```  
  
### <a name="parameters"></a>Parámetros  
 *dwSeconds*  
 El número de segundos que se permiten antes de un intento de conexión agote el tiempo de espera.  
  
### <a name="remarks"></a>Comentarios  
 Un intento de conexión es posible que el tiempo de espera si, por ejemplo, el DBMS no está disponible. Llame a `SetLoginTimeout` después de crear el sin inicializar `CDatabase` objeto pero antes de llamar `OpenEx` o `Open`.  
  
 El valor predeterminado para los tiempos de espera de inicio de sesión es 15 segundos. No todos los orígenes de datos admiten la posibilidad de especificar un valor de tiempo de espera de inicio de sesión. Si el origen de datos no es compatible con el tiempo de espera, obtendrá resultados de seguimiento, pero no una excepción. Un valor de 0 significa "infinito".  
  
##  <a name="setquerytimeout"></a>  CDatabase::SetQueryTimeout  
 Llame a esta función miembro para invalidar el número predeterminado de segundos que se permiten antes de las operaciones siguientes en el tiempo de espera de origen de datos conectado.  
  
```  
void SetQueryTimeout(DWORD dwSeconds);
```  
  
### <a name="parameters"></a>Parámetros  
 *dwSeconds*  
 El número de segundos que se permiten antes de un intento de consulta agote el tiempo de espera.  
  
### <a name="remarks"></a>Comentarios  
 Una operación es posible que el tiempo de espera debido a problemas de acceso de red, el tiempo de procesamiento excesivo de consulta y así sucesivamente. Llame a `SetQueryTimeout` antes de abrir el conjunto de registros o antes de llamar a la función miembro `AddNew`, `Update` o `Delete` funciones miembro, si desea cambiar el valor de tiempo de espera de consulta. La configuración afecta a todas las `Open`, `AddNew`, `Update`, y `Delete` las llamadas a los conjuntos de registros asociado a este `CDatabase` objeto. Cambiar el valor de tiempo de espera de consulta para un conjunto de registros después de abrir, no cambie el valor para el conjunto de registros. Por ejemplo, posteriores `Move` operaciones no usan el nuevo valor.  
  
 El valor predeterminado para los tiempos de espera de consulta es 15 segundos. No todos los orígenes de datos admiten la capacidad de establecer un valor de tiempo de espera de consulta. Si establece un valor de tiempo de espera de consulta de 0, se produce ningún tiempo de espera; la comunicación con el origen de datos puede dejar de responder. Este comportamiento puede ser útil durante el desarrollo. Si el origen de datos no es compatible con el tiempo de espera, obtendrá resultados de seguimiento, pero no una excepción.  
  
## <a name="see-also"></a>Vea también  
 [CObject (clase)](../../mfc/reference/cobject-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CRecordset (clase)](../../mfc/reference/crecordset-class.md)
