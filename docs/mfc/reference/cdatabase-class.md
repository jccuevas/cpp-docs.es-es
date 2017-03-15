---
title: CDatabase (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDatabase
dev_langs:
- C++
helpviewer_keywords:
- database classes [C++], ODBC
- MFC [C++], ODBC
- ODBC [C++], CDatabase class
- ODBC database class
- database connections [C++], CDatabase class
- CDatabase class
ms.assetid: bd0de70a-e3c3-4441-bcaa-bbf434426ca8
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
ms.openlocfilehash: a14025d712f09bef2b6b749d46cac1b1371fd4e3
ms.lasthandoff: 02/24/2017

---
# <a name="cdatabase-class"></a>CDatabase (clase)
Representa una conexión a un origen de datos, a través de la que puede trabajar con el origen de datos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CDatabase : public CObject  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CDatabase::CDatabase](#cdatabase)|Construye un objeto `CDatabase`. Debe inicializar el objeto mediante una llamada a `OpenEx` o **abiertos**.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CDatabase::BeginTrans](#begintrans)|Inicia una transacción de"" â €"una serie de llamadas reversibles para la `AddNew`, **editar**, **eliminar**, y **actualización** funciones miembro de clase `CRecordset` â €" en el origen de datos conectado. El origen de datos debe admitir transacciones para **BeginTrans** surta efecto.|  
|[CDatabase::BindParameters](#bindparameters)|Permite enlazar parámetros antes de llamar a `CDatabase::ExecuteSQL`.|  
|[CDatabase::Cancel](#cancel)|Cancela una operación asincrónica o un proceso de un segundo subproceso.|  
|[CDatabase::CanTransact](#cantransact)|Devuelve cero si el origen de datos admite transacciones.|  
|[CDatabase::CanUpdate](#canupdate)|Devuelve cero si la `CDatabase` objeto es actualizable (no de sólo lectura).|  
|[CDatabase::Close](#close)|Cierra la conexión de origen de datos.|  
|[CDatabase::CommitTrans](#committrans)|Completa una transacción iniciada por **BeginTrans**. Comandos de la transacción que modifica el origen de datos se llevan a cabo.|  
|[CDatabase:: ExecuteSQL](#executesql)|Ejecuta una instrucción SQL. Se devuelve ningún registro de datos.|  
|[CDatabase:: GetBookmarkPersistence](#getbookmarkpersistence)|Identifica las operaciones a través del cual los marcadores son persistentes en objetos de conjunto de registros.|  
|[Getconnect](#getconnect)|Devuelve la cadena de conexión ODBC utilizada para conectar el `CDatabase` objeto a un origen de datos.|  
|[CDatabase:: GetCursorCommitBehavior](#getcursorcommitbehavior)|Identifica el efecto de confirmar una transacción en un objeto de conjunto de registros abierto.|  
|[CDatabase:: GetCursorRollbackBehavior](#getcursorrollbackbehavior)|Identifica el efecto de revertir una transacción en un objeto de conjunto de registros abierto.|  
|[CDatabase::GetDatabaseName](#getdatabasename)|Devuelve el nombre de la base de datos actualmente en uso.|  
|[CDatabase::IsOpen](#isopen)|Devuelve cero si la `CDatabase` objeto actualmente está conectado a un origen de datos.|  
|[CDatabase::OnSetOptions](#onsetoptions)|Llamado por el marco para establecer las opciones de conexión estándar. La implementación predeterminada establece el valor de tiempo de espera de consulta. Puede establecer estas opciones antes de tiempo mediante una llamada a `SetQueryTimeout`.|  
|[CDatabase:: Open](#open)|Establece una conexión a un origen de datos (a través de un controlador ODBC).|  
|[CDatabase:: OpenEx](#openex)|Establece una conexión a un origen de datos (a través de un controlador ODBC).|  
|[CDatabase::Rollback](#rollback)|Invierte los cambios realizados durante la transacción actual. Devuelve el origen de datos a su estado anterior, tal como se define en el **BeginTrans** llamada, sin modificaciones.|  
|[CDatabase::SetLoginTimeout](#setlogintimeout)|Establece el número de segundos después de que un intento de conexión del origen de datos agotará el tiempo.|  
|[CDatabase::SetQueryTimeout](#setquerytimeout)|Establece el número de segundos después de la base de datos de operaciones de consulta agotará el tiempo. Afecta a todos los registros **abiertos**, `AddNew`, **editar**, y **eliminar** llamadas.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CDatabase:: M_hdbc](#m_hdbc)|Abrir el identificador de conexión de conectividad de base de datos (ODBC) a un origen de datos. Tipo de **HDBC**.|  
  
## <a name="remarks"></a>Comentarios  
 Un origen de datos es una instancia específica de datos alojados en algún sistema de administración de base de datos (DBMS). Por ejemplo, Microsoft SQL Server, Microsoft Access, Borland dBASE y xBASE. Puede tener uno o más `CDatabase` objetos activos al mismo tiempo en la aplicación.  
  
> [!NOTE]
>  Si trabaja con las clases de objetos de acceso a datos (DAO) en lugar de las clases de Open Database Connectivity (ODBC), utilice la clase [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) en su lugar. Para obtener más información, vea el artículo [información general: programación de base de datos](../../data/data-access-programming-mfc-atl.md).  
  
 Usar `CDatabase`, construir una `CDatabase` objeto y llamar a su `OpenEx` función miembro. Esto abre una conexión. Cuando se construye a continuación, `CRecordset` objetos para operar en el origen de datos conectado, pasa al constructor de conjunto de registros de un puntero a su `CDatabase` objeto. Cuando haya terminado de utilizar la conexión, llame a la **cerrar** miembro función y destruir el `CDatabase` objeto. **Cerrar** cierra los conjuntos de registros que no se haya cerrado previamente.  
  
 Para obtener más información acerca de `CDatabase`, consulte los artículos [origen de datos (ODBC)](../../data/odbc/data-source-odbc.md) y [información general: programación de base de datos](../../data/data-access-programming-mfc-atl.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CDatabase`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdb.h  
  
##  <a name="a-namebegintransa--cdatabasebegintrans"></a><a name="begintrans"></a>CDatabase::BeginTrans  
 Llame a esta función miembro para iniciar una transacción con el origen de datos conectado.  
  
```  
BOOL BeginTrans();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si la llamada se realizó correctamente y se confirman cambios sólo manualmente. en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Una transacción se compone de uno o más llamadas a la `AddNew`, **editar**, **eliminar**, y **actualización** funciones miembro de un `CRecordset` objeto. Antes de comenzar una transacción, el `CDatabase` objeto debe ya se han conectado al origen de datos llamando a su `OpenEx` o **abiertos** función miembro. Para finalizar la transacción, llame a [CommitTrans](#committrans) para aceptar todos los cambios al origen de datos (y llevarlas a cabo) o llamar a [reversión](#rollback) anular toda la transacción. Llame a **BeginTrans** después de abrir los conjuntos de registros implicados en la transacción y como cerca de los verdaderos las operaciones de actualización como sea posible.  
  
> [!CAUTION]
>  Según el controlador ODBC, abrir un conjunto de registros antes de llamar a **BeginTrans** puede causar problemas al llamar a **reversión**. Debe comprobar el controlador específico que está utilizando. Por ejemplo, cuando se utiliza el controlador de Microsoft Access que se incluye en Microsoft ODBC Desktop Driver Pack 3.0, debe tener en cuenta para el requisito del motor de base de datos Jet que no debe iniciar una transacción en cualquier base de datos que tiene un cursor abierto. En las clases de base de datos MFC, un cursor abierto significa abrir un `CRecordset` objeto. Para obtener más información, consulte [Nota técnica 68](../../mfc/tn068-performing-transactions-with-the-microsoft-access-7-odbc-driver.md).  
  
 **BeginTrans** también se puede bloquear los registros de datos en el servidor, dependiendo de la simultaneidad solicitada y las capacidades del origen de datos. Para obtener información acerca de los datos de bloqueos, vea el artículo [conjunto de registros: bloquear registros (ODBC)](../../data/odbc/recordset-locking-records-odbc.md).  
  
 Transacciones definidas por el usuario se explican en el artículo [transacción (ODBC)](../../data/odbc/transaction-odbc.md).  
  
 **BeginTrans** establece el estado al que la secuencia de las transacciones se puede deshacer (revertir). Para establecer un nuevo estado de reversión, confirmar cualquier transacción actual, a continuación, llame a **BeginTrans** nuevo.  
  
> [!CAUTION]
>  Llamar a **BeginTrans** sin necesidad de llamar a **CommitTrans** o **reversión** es un error.  
  
 Llame a la [CanTransact](#cantransact) función miembro para determinar si el controlador admite las transacciones para una base de datos. También debe llamar a [GetCursorCommitBehavior](#getcursorcommitbehavior) y [GetCursorRollbackBehavior](#getcursorrollbackbehavior) para determinar la compatibilidad para la conservación del cursor.  
  
 Para obtener más información acerca de las transacciones, vea el artículo [transacción (ODBC)](../../data/odbc/transaction-odbc.md).  
  
### <a name="example"></a>Ejemplo  
  Consulte el artículo [transacción: realizar una transacción en un conjunto de registros (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md).  
  
##  <a name="a-namebindparametersa--cdatabasebindparameters"></a><a name="bindparameters"></a>CDatabase::BindParameters  
 Invalidar `BindParameters` cuando necesita enlazar parámetros antes de llamar a [CDatabase:: ExecuteSQL](#executesql).  
  
```  
virtual void BindParameters(HSTMT hstmt);
```  
  
### <a name="parameters"></a>Parámetros  
 `hstmt`  
 El identificador de instrucción ODBC para el que desea enlazar parámetros.  
  
### <a name="remarks"></a>Comentarios  
 Este enfoque es útil cuando no se necesita el resultado establecido desde un procedimiento almacenado.  
  
 En la invalidación, llame a **SQLBindParameters** y relacionados con las funciones ODBC para enlazar los parámetros. MFC llama a la invalidación antes de la llamada a `ExecuteSQL`. No es necesario llamar a **SQLPrepare**; `ExecuteSQL` llamadas **SQLExecDirect** y destruye el **hstmt**, que se usa sólo una vez.  
  
##  <a name="a-namecancela--cdatabasecancel"></a><a name="cancel"></a>CDatabase::Cancel  
 Llame a esta función miembro para solicitar que el origen de datos se cancela una operación asincrónica en curso o un proceso de un segundo subproceso.  
  
```  
void Cancel();
```  
  
### <a name="remarks"></a>Comentarios  
 Tenga en cuenta que las clases ODBC de MFC ya no usan procesamiento asincrónico; para realizar una operación asincrónica, se debe llamar directamente a la función API de ODBC [SQLSetConnectOption](https://msdn.microsoft.com/library/ms713564.aspx). Para obtener más información, consulte [ejecución asincrónica](https://msdn.microsoft.com/library/ms713563.aspx) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-namecantransacta--cdatabasecantransact"></a><a name="cantransact"></a>CDatabase::CanTransact  
 Llame a esta función miembro para determinar si la base de datos permite que las transacciones.  
  
```  
BOOL CanTransact() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si los conjuntos de registros con este `CDatabase` objeto permitir transacciones; de lo contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener información acerca de las transacciones, vea el artículo [transacción (ODBC)](../../data/odbc/transaction-odbc.md).  
  
##  <a name="a-namecanupdatea--cdatabasecanupdate"></a><a name="canupdate"></a>CDatabase::CanUpdate  
 Llame a esta función miembro para determinar si la `CDatabase` objeto permite actualizaciones.  
  
```  
BOOL CanUpdate() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si la `CDatabase` objeto permite actualizaciones; de lo contrario, 0, que indica a cualquiera que se pasa **TRUE** en `bReadOnly` cuando abrió el `CDatabase` objeto o que el origen de datos propio es de solo lectura. El origen de datos es de sólo lectura si una llamada a la función API de ODBC **SQLGetInfo** de **SQL_DATASOURCE_READ_ONLY** devuelve "y".  
  
### <a name="remarks"></a>Comentarios  
 Controladores que no admiten las actualizaciones.  
  
##  <a name="a-namecdatabasea--cdatabasecdatabase"></a><a name="cdatabase"></a>CDatabase::CDatabase  
 Construye un objeto `CDatabase`.  
  
```  
CDatabase();
```  
  
### <a name="remarks"></a>Comentarios  
 Después de crear el objeto, se debe llamar a su `OpenEx` o **abiertos** función miembro para establecer una conexión a un origen de datos especificado.  
  
 Quizá le resulte conveniente incrustar la `CDatabase` objeto en la clase de documento.  
  
### <a name="example"></a>Ejemplo  
 En este ejemplo se muestra cómo utilizar `CDatabase` en un `CDocument`-clase derivada.  
  
 [!code-cpp[NVC_MFCDatabase&#9;](../../mfc/codesnippet/cpp/cdatabase-class_1.h)]  
  
 [!code-cpp[NVC_MFCDatabase&#10;](../../mfc/codesnippet/cpp/cdatabase-class_2.cpp)]  
  
##  <a name="a-nameclosea--cdatabaseclose"></a><a name="close"></a>CDatabase::Close  
 Llame a esta función miembro si desea desconectarse de un origen de datos.  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>Comentarios  
 Debe cerrar los conjuntos de registros asociados con la `CDatabase` antes de llamar a esta función miembro de objeto. Porque **cerrar** no destruye el `CDatabase` de objeto, se puede reutilizar el objeto abriendo una nueva conexión con el mismo origen de datos o un origen de datos diferente.  
  
 Todas las pendientes `AddNew` o **editar** se cancelan las instrucciones de conjuntos de registros con la base de datos y se deshacen todas las transacciones pendientes. Los conjuntos de registros depende del `CDatabase` objeto quedan en un estado indefinido.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDatabase&#12;](../../mfc/codesnippet/cpp/cdatabase-class_3.cpp)]  
  
##  <a name="a-namecommittransa--cdatabasecommittrans"></a><a name="committrans"></a>CDatabase::CommitTrans  
 Llame a esta función miembro después de realizar las transacciones.  
  
```  
BOOL CommitTrans();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si las actualizaciones se han confirmado correctamente; en caso contrario, 0. Si **CommitTrans** produce un error, el estado del origen de datos no está definido. Debe comprobar los datos para determinar su estado.  
  
### <a name="remarks"></a>Comentarios  
 Una transacción se compone de una serie de llamadas a la `AddNew`, **editar**, **eliminar**, y **actualización** funciones miembro de un `CRecordset` objeto que se inició con una llamada a la [BeginTrans](#begintrans) función miembro. **CommitTrans** confirma la transacción. De forma predeterminada, las actualizaciones se confirman inmediatamente; llamar a **BeginTrans** hace el compromiso de actualizaciones se retrasa hasta **CommitTrans** se llama.  
  
 Hasta que se llama **CommitTrans** para finalizar una transacción, puede llamar a la [reversión](#rollback) función miembro para anular la transacción y dejar el origen de datos en su estado original. Para comenzar una nueva transacción, llame a **BeginTrans** nuevo.  
  
 Para obtener más información acerca de las transacciones, vea el artículo [transacción (ODBC)](../../data/odbc/transaction-odbc.md).  
  
### <a name="example"></a>Ejemplo  
  Consulte el artículo [transacción: realizar una transacción en un conjunto de registros (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md).  
  
##  <a name="a-nameexecutesqla--cdatabaseexecutesql"></a><a name="executesql"></a>CDatabase:: ExecuteSQL  
 Llame a esta función miembro cuando necesite ejecutar un comando SQL directamente.  
  
```  
void ExecuteSQL(LPCTSTR lpszSQL);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszSQL`  
 Puntero a una cadena terminada en null que contiene un comando SQL válido para ejecutarse. Puede pasar un [CString](../../atl-mfc-shared/reference/cstringt-class.md).  
  
### <a name="remarks"></a>Comentarios  
 Crear el comando como una cadena terminada en null. `ExecuteSQL`no se devuelven registros de datos. Si desea trabajar con registros, utilice un objeto de conjunto de registros.  
  
 La mayoría de los comandos de un origen de datos se emite a través de objetos de conjunto de registros, que admiten los comandos para seleccionar datos, insertar nuevos registros, eliminar registros y editar registros. Sin embargo, no todas las funciones ODBC es compatible directamente con las clases de base de datos, por lo que en ocasiones puede que necesite realizar una llamada directa de SQL con `ExecuteSQL`.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDatabase&#13;](../../mfc/codesnippet/cpp/cdatabase-class_4.cpp)]  
  
##  <a name="a-namegetbookmarkpersistencea--cdatabasegetbookmarkpersistence"></a><a name="getbookmarkpersistence"></a>CDatabase:: GetBookmarkPersistence  
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
|`SQL_BP_CLOSE`|Los marcadores son válidos tras una **Requery** operación.|  
|`SQL_BP_DELETE`|El marcador de una fila es válido tras una **eliminar** operación en esa fila.|  
|`SQL_BP_DROP`|Los marcadores son válidos tras una **cerrar** operación.|  
|`SQL_BP_SCROLL`|Los marcadores son válidos tras cualquier **mover** operación. Esto sencillamente indica si los marcadores se admiten en el conjunto de registros, tal y como devuelve `CRecordset::CanBookmark`.|  
|`SQL_BP_TRANSACTION`|Los marcadores son válidos después de que una transacción se haya confirmado o revertido.|  
|`SQL_BP_UPDATE`|El marcador de una fila es válido tras una **actualización** operación en esa fila.|  
|`SQL_BP_OTHER_HSTMT`|Los marcadores asociados con un objeto de conjunto de registros son válidos en un segundo conjunto de registros.|  
  
 Para obtener más información sobre este valor devuelto, vea la función API de ODBC **SQLGetInfo** en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]. Para obtener más información acerca de los marcadores, vea el artículo [conjunto de registros: marcadores y posiciones absolutas (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md).  
  
##  <a name="a-namegetconnecta--cdatabasegetconnect"></a><a name="getconnect"></a>Getconnect  
 Llame a esta función miembro para recuperar la cadena de conexión utilizada durante la llamada a `OpenEx` o a `Open` que conectó el objeto `CDatabase` a un origen de datos.  
  
```  
const CString GetConnect() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un `const` [CString](../../atl-mfc-shared/reference/cstringt-class.md) que contiene la cadena de conexión si `OpenEx` o `Open` se ha llamado; de lo contrario, una cadena vacía.  
  
### <a name="remarks"></a>Comentarios  
 Consulte [CDatabase:: Open](#open) para obtener una descripción de cómo se crea la cadena de conexión.  
  
##  <a name="a-namegetcursorcommitbehaviora--cdatabasegetcursorcommitbehavior"></a><a name="getcursorcommitbehavior"></a>CDatabase:: GetCursorCommitBehavior  
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
|`SQL_CB_CLOSE`|Llame a `CRecordset::Requery` inmediatamente después de la confirmación de la transacción.|  
|`SQL_CB_DELETE`|Llame a `CRecordset::Close` inmediatamente después de la confirmación de la transacción.|  
|`SQL_CB_PRESERVE`|Continúe normalmente con `CRecordset` operaciones.|  
  
 Para obtener más información sobre este valor devuelto, vea la función API de ODBC **SQLGetInfo** en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]. Para obtener más información acerca de las transacciones, vea el artículo [transacción (ODBC)](../../data/odbc/transaction-odbc.md).  
  
##  <a name="a-namegetcursorrollbackbehaviora--cdatabasegetcursorrollbackbehavior"></a><a name="getcursorrollbackbehavior"></a>CDatabase:: GetCursorRollbackBehavior  
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
|`SQL_CB_CLOSE`|Llame a `CRecordset::Requery` inmediatamente después de la reversión de la transacción.|  
|`SQL_CB_DELETE`|Llame a `CRecordset::Close` inmediatamente después de la reversión de la transacción.|  
|`SQL_CB_PRESERVE`|Continúe normalmente con `CRecordset` operaciones.|  
  
 Para obtener más información sobre este valor devuelto, vea la función API de ODBC **SQLGetInfo** en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]. Para obtener más información acerca de las transacciones, vea el artículo [transacción (ODBC)](../../data/odbc/transaction-odbc.md).  
  
##  <a name="a-namegetdatabasenamea--cdatabasegetdatabasename"></a><a name="getdatabasename"></a>CDatabase::GetDatabaseName  
 Llame a esta función miembro para recuperar el nombre de la base de datos conectada actualmente (siempre que el origen de datos define un objeto con nombre denominado "database").  
  
```  
CString GetDatabaseName() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un [CString](../../atl-mfc-shared/reference/cstringt-class.md) que contiene el nombre de la base de datos si es correcto; en caso contrario, una cadena vacía `CString`.  
  
### <a name="remarks"></a>Comentarios  
 No es el mismo que el nombre de origen de datos (DSN) especificado en el `OpenEx` o **abiertos** llamar. ¿Qué `GetDatabaseName` devuelve depende de ODBC. En general, una base de datos es una colección de tablas. Si esta entidad tiene un nombre, `GetDatabaseName` lo devuelve.  
  
 Por ejemplo, podría mostrar este nombre en un encabezado. Si se produce un error al recuperar el nombre de ODBC, `GetDatabaseName` devuelve una cadena vacía **Cstring**.  
  
##  <a name="a-nameisopena--cdatabaseisopen"></a><a name="isopen"></a>CDatabase::IsOpen  
 Llame a esta función miembro para determinar si la `CDatabase` objeto actualmente está conectado a un origen de datos.  
  
```  
BOOL IsOpen() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si la `CDatabase` objeto está conectado; en caso contrario, 0.  
  
##  <a name="a-namemhdbca--cdatabasemhdbc"></a><a name="m_hdbc"></a>CDatabase:: M_hdbc  
 Contiene un identificador público de una conexión de origen de datos ODBC â €"un"identificador de conexión".  
  
### <a name="remarks"></a>Comentarios  
 Normalmente, no tendrá necesidad de tener acceso a esta variable miembro directamente. En su lugar, asigna el identificador en el marco de trabajo al llamar a `OpenEx` o **abiertos**. El marco de trabajo desasigna el identificador cuando se llama a la **eliminar** operador en el `CDatabase` objeto. Tenga en cuenta que el **cerrar** función miembro desasignar el identificador.  
  
 En algunas circunstancias, sin embargo, debe usar el controlador directamente. Por ejemplo, si necesita llamar a funciones de la API de ODBC directamente, en lugar de a través de la clase `CDatabase`, es posible que tenga un identificador de conexión para pasar como un parámetro. Vea el ejemplo de código siguiente.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDatabase&#15;](../../mfc/codesnippet/cpp/cdatabase-class_5.cpp)]  
  
##  <a name="a-nameonsetoptionsa--cdatabaseonsetoptions"></a><a name="onsetoptions"></a>CDatabase::OnSetOptions  
 El marco de trabajo llama a esta función miembro cuando se ejecuta directamente una instrucción SQL con el `ExecuteSQL` función miembro.  
  
```  
virtual void OnSetOptions(HSTMT hstmt);
```  
  
### <a name="parameters"></a>Parámetros  
 `hstmt`  
 El identificador de instrucción ODBC para el que se están estableciendo las opciones.  
  
### <a name="remarks"></a>Comentarios  
 `CRecordset::OnSetOptions`También llama a esta función miembro.  
  
 `OnSetOptions`establece el valor de tiempo de espera de inicio de sesión. Si ha habido llamadas anteriores a la `SetQueryTimeout` y la función miembro, `OnSetOptions` refleja los valores actuales; en caso contrario, Establece los valores predeterminados.  
  
> [!NOTE]
>  Antes de MFC 4.2, `OnSetOptions` también establecer el modo de procesamiento para cualquier snychronous o asincrónica. Empezando por MFC 4.2, todas las operaciones son sincrónicas. Para realizar una operación asincrónica, debe realizar una llamada directa a la función API de ODBC **SQLSetPos**.  
  
 No es necesario reemplazar `OnSetOptions` para cambiar el valor de tiempo de espera. En su lugar, para personalizar el valor de tiempo de espera de consulta, llame a `SetQueryTimeout` antes de crear un conjunto de registros; `OnSetOptions` utilizará el nuevo valor. El conjunto de valores que se aplican a las operaciones subsiguientes en todos los conjuntos de registros o llamadas directas a SQL.  
  
 Reemplace `OnSetOptions` si desea establecer opciones adicionales. El reemplazo debe llamar a la clase base `OnSetOptions` antes o después de llamar a la función API de ODBC **SQLSetStmtOption**. Siga el método que se muestra en la implementación predeterminada del marco de trabajo de `OnSetOptions`.  
  
##  <a name="a-nameopena--cdatabaseopen"></a><a name="open"></a>CDatabase:: Open  
 Llame a esta función miembro para inicializar recientemente construido `CDatabase` objeto.  
  
```  
virtual BOOL Open(
    LPCTSTR lpszDSN,  
    BOOL bExclusive = FALSE,  
    BOOL bReadOnly = FALSE,  
    LPCTSTR lpszConnect = _T("ODBC;"),  
    BOOL bUseCursorLib = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszDSN`  
 Especifica el nombre de un origen de datos â €"registrar un nombre con ODBC mediante el programa Administrador de ODBC. Si se especifica un valor DSN en `lpszConnect` (en el formulario "DSN =\<origen de datos >"), no debe especificarse en `lpszDSN`. En este caso, `lpszDSN` debe ser **NULL**. De lo contrario, puede pasar **NULL** si desea presentar al usuario un cuadro de diálogo origen de datos en el que el usuario puede seleccionar un origen de datos. Para obtener más información, vea la sección Comentarios.  
  
 `bExclusive`  
 No se admite en esta versión de la biblioteca de clases. Actualmente, una aserción produce un error si este parámetro es **TRUE**. El origen de datos siempre se abrirá como compartido (no exclusivo).  
  
 `bReadOnly`  
 **TRUE** si piensa que la conexión sea de solo lectura y prohibir actualizaciones en el origen de datos. Todos los conjuntos de registros dependientes heredan este atributo. El valor predeterminado es **FALSE**.  
  
 `lpszConnect`  
 Especifica una cadena de conexión. La cadena de conexión concatena información, que posiblemente incluyen un nombre de origen de datos, un identificador de usuario válido en el origen de datos, una cadena de autenticación de usuario (contraseña, si el origen de datos requiere una) y otra información. La cadena de conexión completa debe ir precedida por la cadena "ODBC;" (en mayúsculas o minúsculas). "ODBC;" cadena se usa para indicar que la conexión es a un origen de datos ODBC; Esto es por la compatibilidad con versiones futuras versiones de la biblioteca de clases podrían admitir orígenes de datos ODBC no.  
  
 `bUseCursorLib`  
 **TRUE** si desea que la DLL de biblioteca de Cursor ODBC se va a cargar. La biblioteca de cursores enmascara parte de la funcionalidad del controlador ODBC subyacente, evitando así el uso de conjuntos de registros dinámicos (si el controlador los admite). Los únicos cursores admitidos si se carga la biblioteca de cursores son las instantáneas estáticas y los cursores de sólo avance. El valor predeterminado es **TRUE**. Si planea crear un objeto de conjunto de registros directamente desde `CRecordset` sin tener que derivar de ella, no debe cargar la biblioteca de cursores.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si la conexión se realiza correctamente; de lo contrario, 0 si el usuario decide cancelar cuando aparezca un cuadro de diálogo pide más información de conexión. En los demás casos, el marco de trabajo produce una excepción.  
  
### <a name="remarks"></a>Comentarios  
 El objeto de base de datos se debe inicializar antes de que puede utilizar para construir un objeto de conjunto de registros.  
  
> [!NOTE]
>  Llamar a la [OpenEx](#openex) función miembro es la forma preferida para conectarse a un origen de datos e inicializar el objeto de base de datos.  
  
 Si los parámetros de la **abiertos** llamada no contienen información suficiente para realizar la conexión, el controlador ODBC abre un cuadro de diálogo para obtener la información necesaria del usuario. Cuando se llama a **abiertos**, la cadena de conexión, `lpszConnect`, se almacena de forma privada en el `CDatabase` objeto y está disponible mediante una llamada a la [GetConnect](#getconnect) función miembro.  
  
 Si lo desea, puede abrir un cuadro de diálogo antes de llamar a **abrir** para obtener información del usuario, como una contraseña, a continuación, agregue dicha información a la cadena de conexión que se pasa a **abrir**. También puede guardar la cadena de conexión pasa por lo que se puede reutilizar la próxima vez la aplicación llama **abiertos** en un `CDatabase` objeto.  
  
 También puede utilizar la cadena de conexión para varios niveles de autorización de inicio de sesión (cada uno de otro `CDatabase` objeto) o para proporcionar otra información específica del origen de datos. Para obtener más información acerca de las cadenas de conexión, consulte el capítulo 5 en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 Es posible que un intento de conexión en tiempo de espera si, por ejemplo, el host DBMS no está disponible. Si se produce un error en el intento de conexión, **abiertos** produce una `CDBException`.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDatabase&#14;](../../mfc/codesnippet/cpp/cdatabase-class_6.cpp)]  
  
##  <a name="a-nameopenexa--cdatabaseopenex"></a><a name="openex"></a>CDatabase:: OpenEx  
 Llame a esta función miembro para inicializar recientemente construido `CDatabase` objeto.  
  
```  
virtual BOOL OpenEx(
    LPCTSTR lpszConnectString,  
    DWORD dwOptions = 0);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszConnectString`  
 Especifica una cadena de conexión ODBC. Esto incluye el nombre del origen de datos, así como otra información opcional, como un identificador de usuario y una contraseña. Por ejemplo, "DSN = SQLServer_Source; UID = SA; PWD = abc123 "es una cadena de conexión posibles. Tenga en cuenta que, si se pasa **NULL** para `lpszConnectString`, un cuadro de diálogo origen de datos le pedirá al usuario que seleccione un origen de datos.  
  
 `dwOptions`  
 Máscara de bits que especifica una combinación de los valores siguientes. El valor predeterminado es 0, lo que significa que la base de datos se abrirá como compartido con acceso de escritura, no se cargará la DLL de biblioteca de cursores de ODBC y se mostrará el cuadro de diálogo de conexión de ODBC sólo si no hay suficiente información para realizar la conexión.  
  
- **CDatabase::openExclusive** no se admite en esta versión de la biblioteca de clases. Un origen de datos siempre se abrirá como compartido (no exclusivo). Actualmente, se produce un error en una aserción si especifica esta opción.  
  
- **CDatabase::openReadOnly** abrir el origen de datos como de sólo lectura.  
  
- **CDatabase:: useCursorLib** cargar la biblioteca de cursores ODBC DLL. La biblioteca de cursores enmascara parte de la funcionalidad del controlador ODBC subyacente, evitando así el uso de conjuntos de registros dinámicos (si el controlador los admite). Los únicos cursores admitidos si se carga la biblioteca de cursores son las instantáneas estáticas y los cursores de sólo avance. Si planea crear un objeto de conjunto de registros directamente desde `CRecordset` sin tener que derivar de ella, no debe cargar la biblioteca de cursores.  
  
- **CDatabase::noOdbcDialog** no muestran el cuadro de diálogo de conexión ODBC, independientemente de si se proporciona suficiente información de conexión.  
  
- **CDatabase::forceOdbcDialog** siempre mostrará el cuadro de diálogo de conexión de ODBC.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si la conexión se realiza correctamente; de lo contrario, 0 si el usuario decide cancelar cuando aparezca un cuadro de diálogo pide más información de conexión. En los demás casos, el marco de trabajo produce una excepción.  
  
### <a name="remarks"></a>Comentarios  
 El objeto de base de datos se debe inicializar antes de que puede utilizar para construir un objeto de conjunto de registros.  
  
 Si el `lpszConnectString` parámetro en su `OpenEx` llamada no contiene suficiente información para realizar la conexión, el controlador ODBC abre un cuadro de diálogo para obtener la información necesaria del usuario, siempre que no se ha configurado **CDatabase::noOdbcDialog** o **CDatabase::forceOdbcDialog** en el `dwOptions` parámetro. Cuando se llama a `OpenEx`, la cadena de conexión, `lpszConnectString`, se almacena de forma privada en el `CDatabase` objeto y está disponible mediante una llamada a la [GetConnect](#getconnect) función miembro.  
  
 Si lo desea, puede abrir un cuadro de diálogo antes de llamar a `OpenEx` para obtener información del usuario, como una contraseña y, a continuación, agregar dicha información a la cadena de conexión que se pasa a `OpenEx`. También puede guardar la cadena de conexión pasa por lo que se puede reutilizar la próxima vez la aplicación llama `OpenEx` en un `CDatabase` objeto.  
  
 También puede utilizar la cadena de conexión para varios niveles de autorización de inicio de sesión (cada uno de otro `CDatabase` objeto) o para proporcionar otra información específica del origen de datos. Para obtener más información acerca de las cadenas de conexión, consulte el capítulo 6 de la *referencia del programador de ODBC*.  
  
 Es posible que un intento de conexión en tiempo de espera si, por ejemplo, el host DBMS no está disponible. Si se produce un error en el intento de conexión, `OpenEx` produce una `CDBException`.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDatabase&#11;](../../mfc/codesnippet/cpp/cdatabase-class_7.cpp)]  
  
##  <a name="a-namerollbacka--cdatabaserollback"></a><a name="rollback"></a>CDatabase::Rollback  
 Llame a esta función miembro para revertir los cambios realizados durante una transacción.  
  
```  
BOOL Rollback();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si se ha revertido la transacción; en caso contrario, 0. Si un **reversión** llamada produce un error, el origen de datos y transacciones estados son indefinidos. Si **reversión** devuelve 0, debe comprobar el origen de datos para determinar su estado.  
  
### <a name="remarks"></a>Comentarios  
 Todos los `CRecordset``AddNew`, **editar**, **eliminar**, y **actualización** llamadas ejecutadas desde la última [BeginTrans](#begintrans) revierte al estado que existía en el momento de esa llamada.  
  
 Después de llamar a **reversión**, la transacción está por encima y se debe llamar a **BeginTrans** nuevamente por otra transacción. El registro que era actual antes de llamar **BeginTrans** se convierte en el actual registro nuevo después de **reversión**.  
  
 Después de una reversión, el registro que era actual antes de la reversión permanece actual. Para obtener más información sobre el estado del conjunto de registros y el origen de datos después de una operación de deshacer, consulte el artículo [transacción (ODBC)](../../data/odbc/transaction-odbc.md).  
  
### <a name="example"></a>Ejemplo  
  Consulte el artículo [transacción: realizar una transacción en un conjunto de registros (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md).  
  
##  <a name="a-namesetlogintimeouta--cdatabasesetlogintimeout"></a><a name="setlogintimeout"></a>CDatabase::SetLoginTimeout  
 Llamar a este miembro de función â €"antes de llamar a `OpenEx` o **abiertos** â €" reemplazar el número predeterminado de segundos que se permiten antes de un intento de datos origen se agota.  
  
```  
void SetLoginTimeout(DWORD dwSeconds);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwSeconds`  
 Número de segundos que se permiten antes de un intento de conexión agote el tiempo de espera.  
  
### <a name="remarks"></a>Comentarios  
 Un intento de conexión podría expirar si, por ejemplo, el DBMS no está disponible. Llame a **SetLoginTimeout** después de construir el sin inicializar `CDatabase` objeto pero antes de llamar `OpenEx` o **abiertos**.  
  
 El valor predeterminado para los tiempos de espera de inicio de sesión es 15 segundos. No todos los orígenes de datos admiten la capacidad de especificar un valor de tiempo de espera de inicio de sesión. Si el origen de datos no es compatible con el tiempo de espera, obtendrá resultados de seguimiento, pero no una excepción. Un valor de 0 significa "infinito".  
  
##  <a name="a-namesetquerytimeouta--cdatabasesetquerytimeout"></a><a name="setquerytimeout"></a>CDatabase::SetQueryTimeout  
 Llame a esta función miembro para anular el número predeterminado de segundos que se permiten antes de las operaciones subsiguientes en el tiempo de espera de origen de datos conectado.  
  
```  
void SetQueryTimeout(DWORD dwSeconds);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwSeconds`  
 El número de segundos que se permiten antes de un intento de consulta agota el tiempo de espera.  
  
### <a name="remarks"></a>Comentarios  
 Una operación podría el tiempo de espera debido a problemas de acceso de red y el tiempo de procesamiento excesivo de consultas. Llame a `SetQueryTimeout` antes de abrir el conjunto de registros o antes de llamar a la función miembro `AddNew`, **actualización** o **eliminar** funciones miembro si desea cambiar el valor de tiempo de espera de consulta. La configuración afecta a todas las **abiertos**, `AddNew`, **actualización**, y **eliminar** llamadas a los conjuntos de registros asociados con este `CDatabase` objeto. Cambiar el valor de tiempo de espera de consulta para un conjunto de registros después de la apertura, no cambie el valor para el conjunto de registros. Por ejemplo, posterior **mover** operaciones no utilizan el nuevo valor.  
  
 El valor predeterminado para los tiempos de espera de consulta es 15 segundos. No todos los orígenes de datos admiten la capacidad para establecer un valor de tiempo de espera de consulta. Si establece un valor de tiempo de espera de consulta de 0, se produce ningún tiempo de espera; la comunicación con el origen de datos puede dejar de responder. Este comportamiento puede ser útil durante el desarrollo. Si el origen de datos no es compatible con el tiempo de espera, obtendrá resultados de seguimiento, pero no una excepción.  
  
## <a name="see-also"></a>Vea también  
 [CObject (clase)](../../mfc/reference/cobject-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [CRecordset (clase)](../../mfc/reference/crecordset-class.md)

