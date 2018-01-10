---
title: CDaoDatabase (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
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
dev_langs: C++
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
caps.latest.revision: "23"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 48646e0635098aceea957f93015a5de93515096d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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
|[CDaoDatabase::CDaoDatabase](#cdaodatabase)|Construye un objeto `CDaoDatabase`. Llame a **abiertos** para conectar el objeto a una base de datos.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDaoDatabase::CanTransact](#cantransact)|Devuelve un valor distinto de cero si la base de datos admite transacciones.|  
|[CDaoDatabase::CanUpdate](#canupdate)|Devuelve un valor distinto de cero si la `CDaoDatabase` objeto es actualizable (no de solo lectura).|  
|[CDaoDatabase::Close](#close)|Cierra la conexión de base de datos.|  
|[CDaoDatabase::Create](#create)|Crea el objeto de base de datos DAO subyacente e inicializa la `CDaoDatabase` objeto.|  
|[CDaoDatabase::CreateRelation](#createrelation)|Define a una nueva relación entre las tablas en la base de datos.|  
|[CDaoDatabase::DeleteQueryDef](#deletequerydef)|Elimina un objeto de definición de consulta guardado en QueryDefs (colección) de la base de datos.|  
|[CDaoDatabase::DeleteRelation](#deleterelation)|Elimina a una relación existente entre las tablas de la base de datos.|  
|[CDaoDatabase::DeleteTableDef](#deletetabledef)|Elimina la definición de una tabla en la base de datos. Esto elimina la tabla real y todos sus datos.|  
|[CDaoDatabase::Execute](#execute)|Ejecuta una consulta de acción. Al llamar a **Execute** para una consulta que devuelve resultados produce una excepción.|  
|[CDaoDatabase::GetConnect](#getconnect)|Devuelve la cadena de conexión utilizada para conectar el `CDaoDatabase` objeto a una base de datos. Se utiliza para ODBC.|  
|[CDaoDatabase::GetName](#getname)|Devuelve el nombre de la base de datos actualmente en uso.|  
|[CDaoDatabase::GetQueryDefCount](#getquerydefcount)|Devuelve el número de las consultas definidas para la base de datos.|  
|[CDaoDatabase::GetQueryDefInfo](#getquerydefinfo)|Devuelve información sobre una consulta específica definida en la base de datos.|  
|[CDaoDatabase::GetQueryTimeout](#getquerytimeout)|Devuelve el número de segundos después de la base de datos de operaciones de consulta agotará el tiempo. Afecta a todas las posterior abrir, agregar nuevas, actualizar y editar las operaciones y realizar otras operaciones en orígenes de datos ODBC (sólo) como **Execute** llamadas.|  
|[CDaoDatabase::GetRecordsAffected](#getrecordsaffected)|Devuelve el número de registros afectado por la actualización más reciente, editar o agregar la operación o mediante una llamada a **Execute**.|  
|[CDaoDatabase::GetRelationCount](#getrelationcount)|Devuelve el número de relaciones definidas entre las tablas de la base de datos.|  
|[CDaoDatabase::GetRelationInfo](#getrelationinfo)|Devuelve información acerca de una relación especificada definida entre las tablas de la base de datos.|  
|[CDaoDatabase:: GetTableDefCount](#gettabledefcount)|Devuelve el número de tablas definidas en la base de datos.|  
|[CDaoDatabase:: GetTableDefInfo](#gettabledefinfo)|Devuelve información acerca de una tabla especificada en la base de datos.|  
|[CDaoDatabase::GetVersion](#getversion)|Devuelve la versión del motor de base de datos asociada a la base de datos.|  
|[CDaoDatabase::IsOpen](#isopen)|Devuelve un valor distinto de cero si la `CDaoDatabase` objeto actualmente está conectado a una base de datos.|  
|[CDaoDatabase::Open](#open)|Establece una conexión a una base de datos.|  
|[CDaoDatabase::SetQueryTimeout](#setquerytimeout)|Establece el número de segundos después de la base de datos de consulta operaciones (en orígenes de datos ODBC solo) agotará el tiempo. Afecta a todas las posterior abre, agrega nuevas, actualiza y elimina operaciones.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDaoDatabase::m_pDAODatabase](#m_pdaodatabase)|Un puntero al objeto de base de datos DAO subyacente.|  
|[CDaoDatabase::m_pWorkspace](#m_pworkspace)|Un puntero a la [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md) objeto que contiene la base de datos y define su espacio de transacciones.|  
  
## <a name="remarks"></a>Comentarios  
 Para obtener información acerca de los formatos de base de datos compatibles, vea el [GetName](../../mfc/reference/cdaoworkspace-class.md#getname) función miembro. Puede tener uno o más `CDaoDatabase` objetos activos a la vez en un "área de trabajo proporcionada," representado por un [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md) objeto. El área de trabajo mantiene una colección de objetos de base de datos abierto, llamado a la colección de bases de datos.  
  
> [!NOTE]
>  Las clases de base de datos DAO de MFC son distintas de las clases de base de datos MFC basadas en ODBC. Todos los nombres de clase de base de datos DAO tienen el prefijo "CDao". Clase `CDaoDatabase` proporciona una interfaz similar a la de la clase ODBC [CDatabase](../../mfc/reference/cdatabase-class.md). La principal diferencia es que `CDatabase` accede a DBMS a través de Open Database Connectivity (ODBC) y un controlador ODBC para ese DBMS. `CDaoDatabase`tiene acceso a datos a través de un objeto de acceso de datos (DAO) basado en el motor de base de datos de Microsoft Jet. En general, son más eficaces que las clases MFC basadas en ODBC, las clases MFC basadas en DAO las clases basadas en DAO pueden tener acceso a datos, incluidos los controladores ODBC, a través de su propio motor de base de datos. Las clases basadas en DAO también admiten operaciones de lenguaje de definición de datos (DDL), como agregar tablas a través de las clases, sin tener que llamar a DAO directamente.  
  
## <a name="usage"></a>Uso  
 Puede crear objetos de base de datos de forma implícita, cuando se crean objetos de conjunto de registros. Pero también puede crear objetos de base de datos explícitamente. Para usar una base de datos explícitamente con `CDaoDatabase`, realice una de las siguientes acciones:  
  
-   Construir un `CDaoDatabase` objeto, pasando un puntero a un formato de archivo [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md) objeto.  
  
-   O construir una `CDaoDatabase` objeto sin especificar el área de trabajo (MFC crea un objeto de área de trabajo temporal).  
  
 Para crear una nueva Microsoft Jet (. Base de datos de Microsoft Access), construir un `CDaoDatabase` objeto y llame a su [crear](#create) función miembro. Hacer *no* llamar a **abiertos** después **crear**.  
  
 Para abrir una base de datos, construir un `CDaoDatabase` objeto y llame a su [abrir](#open) función miembro.  
  
 Cualquiera de estas técnicas se anexa el objeto de base de datos DAO a la colección de bases de datos del área de trabajo y se abre una conexión a los datos. Cuando se construyen a continuación, [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md), [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md), o [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md) objetos para el funcionamiento de la base de datos conectado, pasar los constructores para estos objetos un puntero a la `CDaoDatabase` objeto. Cuando haya terminado de utilizar la conexión, llame a la [cerrar](#close) miembro funcione y destruir el `CDaoDatabase` objeto. **Cerrar** cierra los conjuntos de registros no ha cerrado previamente.  
  
## <a name="transactions"></a>Transacciones  
 Procesamiento de transacciones de base de datos se proporciona en el nivel de área de trabajo, consulte la [BeginTrans](../../mfc/reference/cdaoworkspace-class.md#begintrans), [CommitTrans](../../mfc/reference/cdaoworkspace-class.md#committrans), y [reversión](../../mfc/reference/cdaoworkspace-class.md#rollback) funciones miembro de clase `CDaoWorkspace` .  
  
## <a name="odbc-connections"></a>Conexiones ODBC  
 El método recomendado para trabajar con orígenes de datos ODBC consiste en asociar tablas externas a una Microsoft Jet (. Base de datos de Microsoft Access).  
  
## <a name="collections"></a>Colecciones  
 Cada base de datos mantiene sus propio colecciones de tabledef, querydef, conjunto de registros y los objetos de relación. Clase `CDaoDatabase` proporciona funciones miembro para manipular estos objetos.  
  
> [!NOTE]
>  Los objetos se almacenan en DAO, no está en el objeto de base de datos MFC. MFC proporciona clases para objetos tabledef y querydef, conjunto de registros, pero no para los objetos de relación.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CDaoDatabase`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdao.h  
  
##  <a name="cantransact"></a>CDaoDatabase::CanTransact  
 Llame a esta función miembro para determinar si la base de datos permite que las transacciones.  
  
```  
BOOL CanTransact();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la base de datos admite transacciones; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 Las transacciones se administran en el área de trabajo de la base de datos.  
  
##  <a name="canupdate"></a>CDaoDatabase::CanUpdate  
 Llame a esta función miembro para determinar si la `CDaoDatabase` objeto permite realizar actualizaciones.  
  
```  
BOOL CanUpdate();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si la `CDaoDatabase` objeto permite realizar actualizaciones; de lo contrario, 0, que indica cualquier que se pasa **TRUE** en `bReadOnly` cuando abrió el `CDaoDatabase` objeto o que la base de datos es de solo lectura. Consulte la [abiertos](#open) función miembro.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener información acerca de la actualización de la base de datos, vea el tema "Propiedad actualizable" en la Ayuda de DAO.  
  
##  <a name="cdaodatabase"></a>CDaoDatabase::CDaoDatabase  
 Construye un objeto `CDaoDatabase`.  
  
```  
CDaoDatabase(CDaoWorkspace* pWorkspace = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 *pWorkspace*  
 Un puntero a la `CDaoWorkspace` objeto que va a contener el nuevo objeto de base de datos. Si acepta el valor predeterminado de **NULL**, el constructor crea un archivo temporal `CDaoWorkspace` objeto que usa el área de trabajo DAO predeterminada. Puede obtener un puntero al objeto de área de trabajo a través de la [m_pWorkspace](#m_pworkspace) miembro de datos.  
  
### <a name="remarks"></a>Comentarios  
 Después de crear el objeto, si está creando una nueva Microsoft Jet (. MDB) de base de datos, llame al objeto [crear](#create) función miembro. Si es, en su lugar, abrir una base de datos existente, llame al objeto de la [abiertos](#open) función miembro.  
  
 Cuando termine con el objeto, debe llamar a su [cerrar](#close) miembro funcione y, luego, destruya el `CDaoDatabase` objeto.  
  
 Le resultará conveniente incrustar la `CDaoDatabase` objeto en la clase de documento.  
  
> [!NOTE]
>  A `CDaoDatabase` objeto también se crea implícitamente si abre un [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objeto sin pasar un puntero a un archivo `CDaoDatabase` objeto. Este objeto de base de datos se cierra cuando se cierra el objeto de conjunto de registros.  
  
##  <a name="close"></a>CDaoDatabase::Close  
 Llame a esta función miembro para desconectarse de una base de datos y cerrar cualquier abrir conjuntos de registros, definiciones de tabla y las definiciones de consulta asociadas con la base de datos.  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>Comentarios  
 Es recomendable cerrar estos objetos antes de llamar a esta función miembro. Cerrar un `CDaoDatabase` objeto quita de la colección de bases de datos en el asociado [área de trabajo](../../mfc/reference/cdaoworkspace-class.md). Porque **cerrar** no destruirá los `CDaoDatabase` de objeto, puede volver a usar el objeto abriendo la misma base de datos o una base de datos diferente.  
  
> [!CAUTION]
>  Llame a la [actualización](../../mfc/reference/cdaorecordset-class.md#update) función de miembro (si hay ediciones pendientes) y la **cerrar** función de miembro en todos los objetos de conjunto de registros abierto antes de cerrar una base de datos. Si sale de una función que declara [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) o `CDaoDatabase` objetos en la pila, se cierra la base de datos, se perderán los cambios no guardados, todas las transacciones pendientes se revierten y todas las ediciones pendientes a los datos se pierden.  
  
> [!CAUTION]
>  Si intenta cerrar un objeto de base de datos mientras está abierto algún objeto de conjunto de registros, o si se intenta cerrar un objeto de área de trabajo mientras está abierto algún objeto de base de datos que pertenecen a esa área de trabajo concreto, los objetos de conjunto de registros se cerrarán y cualquier actualización o modificación pendiente será revierte. Si intenta cerrar un objeto de área de trabajo mientras está abierto algún objeto de base de datos que pertenecen a ella, la operación cierra todos los objetos de base de datos que pertenecen a ese objeto de área de trabajo específicos, lo que podría producir en objetos de conjunto de registros sin cerrar se cierra. Si no cierra el objeto de base de datos, MFC notifica un error de aserción en compilaciones de depuración.  
  
 Si el objeto de base de datos se define fuera del ámbito de una función y salir de la función pero no lo cierre, permanecerá abierto hasta que cierre explícitamente el objeto de base de datos o el módulo en el que se define fuera del ámbito.  
  
##  <a name="create"></a>CDaoDatabase::Create  
 Para crear una nueva Microsoft Jet (. MDB) de base de datos, llame a esta función miembro después de crear un `CDaoDatabase` objeto.  
  
```  
virtual void Create(
    LPCTSTR lpszName,  
    LPCTSTR lpszLocale = dbLangGeneral,  
    int dwOptions = 0);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszName`  
 Una expresión de cadena que es el nombre del archivo de base de datos que va a crear. Puede ser la ruta de acceso completa y nombre de archivo, como "C:\\\MYDB. MDB". Debe proporcionar un nombre. Si no proporciona una extensión de nombre de archivo. Se anexa el archivo MDB. Si la red es compatible con la convención de nomenclatura uniforme (UNC), también puede especificar una ruta de acceso de red, como "\\\\\\\MYSERVER\\\MYSHARE\\\MYDIR\\\MYDB". Sólo Microsoft Jet (. Archivos de base de datos de Microsoft Access) pueden crearse con esta función miembro. (Barras diagonales inversas dobles son necesarias en literales de cadena como "\\" es el carácter de escape de C++.)  
  
 `lpszLocale`  
 Una expresión de cadena que se utiliza para especificar el criterio de ordenación para la creación de la base de datos. El valor predeterminado es **dbLangGeneral**. Los valores posibles son:  
  
- **dbLangGeneral** inglés, alemán, francés, portugués, italiano y español moderno  
  
- **dbLangArabic** árabe  
  
- **dbLangCyrillic** ruso  
  
- **dbLangCzech** checo  
  
- **dbLangDutch** neerlandés  
  
- **dbLangGreek** griego  
  
- **dbLangHebrew** hebreo  
  
- **dbLangHungarian** húngaro  
  
- **dbLangIcelandic** islandés  
  
- **dbLangNordic** idioma nórdico (Microsoft base de datos motor Jet versión 1.0 solo)  
  
- **dbLangNorwdan** noruego y danés  
  
- **dbLangPolish** polaco  
  
- **dbLangSpanish** Español tradicional  
  
- **dbLangSwedfin** sueco y finés  
  
- **dbLangTurkish** turco  
  
 `dwOptions`  
 Un entero que indica una o varias opciones. Los valores posibles son:  
  
- **dbEncrypt** crear una base de datos.  
  
- **dbVersion10** crear una base de datos con la versión de base de datos de Microsoft Jet 1.0.  
  
- **dbVersion11** crear una base de datos con la versión de base de datos de Microsoft Jet 1.1.  
  
- **dbVersion20** crear una base de datos con la versión de base de datos de Microsoft Jet 2.0.  
  
- **dbVersion30** crear una base de datos con la versión de base de datos de Microsoft Jet 3.0.  
  
 Si se omite la constante de cifrado, se crea una base de datos sin cifrar. Puede especificar sólo una constante de versión. Si omite una constante de versión, se crea una base de datos que usa la versión de base de datos de Microsoft Jet 3.0.  
  
> [!CAUTION]
>  Si no se cifra una base de datos, es posible, incluso si implementar la seguridad de usuario/contraseña, para leer directamente el archivo de disco binario que constituye la base de datos.  
  
### <a name="remarks"></a>Comentarios  
 **Crear** crea el archivo de base de datos y el objeto de base de datos DAO subyacente e inicializa el objeto de C++. El objeto se anexa a la colección de bases de datos del área de trabajo asociada. El objeto de base de datos está en un estado abierto; No llame a **abiertos** después **crear**.  
  
> [!NOTE]
>  Con **crear**, puede crear solo Microsoft Jet (. En el caso de las bases de datos de Microsoft Access). No se puede crear bases de datos ISAM o bases de datos ODBC.  
  
##  <a name="createrelation"></a>CDaoDatabase::CreateRelation  
 Llame a esta función miembro para establecer a una relación entre uno o más campos de una tabla en la base de datos principal y uno o más campos de una tabla externa (otra tabla en la base de datos).  
  
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
 `lpszName`  
 El nombre único del objeto relation. El nombre debe empezar por una letra y puede contener un máximo de 40 caracteres. Puede incluir números y caracteres de subrayado pero no puede incluir espacios o signos de puntuación.  
  
 `lpszTable`  
 El nombre de la tabla principal de la relación. Si la tabla no existe, MFC inicia una excepción de tipo [CDaoException](../../mfc/reference/cdaoexception-class.md).  
  
 `lpszForeignTable`  
 El nombre de la tabla externa en la relación. Si la tabla no existe, MFC inicia una excepción de tipo `CDaoException`.  
  
 `lAttributes`  
 Un valor long que contiene información sobre el tipo de relación. Puede usar este valor para exigir la integridad referencial, entre otras cosas. Puede utilizar el operador OR bit a bit ( **&#124;**) para combinar cualquiera de los siguientes valores (siempre que la combinación tiene sentido):  
  
- **dbRelationUnique** relación es de uno a uno.  
  
- **dbRelationDontEnforce** relación no es aplica (sin integridad referencial).  
  
- **dbRelationInherited** relación existe en una base de datos contiene las dos tablas asociadas.  
  
- **dbRelationUpdateCascade** actualizaciones se producirán en cascada (para obtener más información sobre cascadas, vea la sección Comentarios).  
  
- **dbRelationDeleteCascade** eliminaciones se producirán en cascada.  
  
 *lpszField*  
 Un puntero a una cadena terminada en null que contiene el nombre de un campo de la tabla principal (con el nombre por `lpszTable`).  
  
 *lpszForeignField*  
 Un puntero a una cadena terminada en null que contiene el nombre de un campo en la tabla externa (denominado por `lpszForeignTable`).  
  
 *relinfo*  
 Una referencia a un [CDaoRelationInfo](../../mfc/reference/cdaorelationinfo-structure.md) objeto que contiene información acerca de la relación que desea crear.  
  
### <a name="remarks"></a>Comentarios  
 La relación no puede implicar una consulta o una tabla asociada desde una base de datos externo.  
  
 Utilice la primera versión de la función cuando la relación implica un campo en cada una de las dos tablas. Use la segunda versión cuando la relación implica varios campos. El número máximo de campos en una relación es 14.  
  
 Esta acción crea un objeto de relación de DAO subyacente, pero esto es un detalle de implementación de MFC, ya que la encapsulación de MFC de objetos de la relación está dentro de una clase `CDaoDatabase`. MFC no proporciona una clase para las relaciones.  
  
 Si establece a la relación de atributos del objeto para activar operaciones en cascada, el motor de base de datos se actualiza automáticamente o elimina los registros de una o varias tablas cuando se realizan cambios en tablas relacionadas de clave principales.  
  
 Por ejemplo, supongamos que establece una relación de eliminación en cascada entre una tabla Customers y una tabla Orders. Al eliminar registros de la tabla Customers, también se eliminan registros de la tabla de pedidos relacionados con ese cliente. Además, si establece cascade delete relaciones entre la tabla Orders y otras tablas, registros de esas tablas se eliminan automáticamente cuando se eliminan registros de la tabla Customers.  
  
 Para obtener información relacionada, vea el tema "Método CreateRelation" en la Ayuda de DAO.  
  
##  <a name="deletequerydef"></a>CDaoDatabase::DeleteQueryDef  
 Llame a esta función miembro para eliminar la definición de consulta especificado: consulta guardada, desde el `CDaoDatabase` QueryDefs (colección) del objeto.  
  
```  
void DeleteQueryDef(LPCTSTR lpszName);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszName`  
 El nombre de la consulta guardada para eliminar.  
  
### <a name="remarks"></a>Comentarios  
 Después, esa consulta ya no se define en la base de datos.  
  
 Para obtener información acerca de cómo crear objetos de definición de consulta, vea la clase [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md). Un objeto querydef queda asociado con un determinado `CDaoDatabase` objeto cuando se construye el `CDaoQueryDef` objeto, pasando un puntero al objeto de base de datos.  
  
##  <a name="deleterelation"></a>CDaoDatabase::DeleteRelation  
 Llame a esta función miembro para eliminar a una relación existente de la colección de relaciones del objeto de base de datos.  
  
```  
void DeleteRelation(LPCTSTR lpszName);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszName`  
 El nombre de la relación para eliminar.  
  
### <a name="remarks"></a>Comentarios  
 Después, la relación ya no existe.  
  
 Para obtener información relacionada, vea el tema "Método Delete" en la Ayuda de DAO.  
  
##  <a name="deletetabledef"></a>CDaoDatabase::DeleteTableDef  
 Llame a esta función miembro para eliminar la tabla especificada y todos sus datos de la `CDaoDatabase` TableDefs (colección) del objeto.  
  
```  
void DeleteTableDef(LPCTSTR lpszName);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszName`  
 El nombre de la definición de tabla para eliminar.  
  
### <a name="remarks"></a>Comentarios  
 Después, esta tabla ya no se define en la base de datos.  
  
> [!NOTE]
>  Tener cuidado de no eliminar tablas del sistema.  
  
 Para obtener información acerca de cómo crear objetos de definición de tabla, vea la clase [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md). Un objeto tabledef queda asociado con un determinado `CDaoDatabase` objeto cuando se construye el `CDaoTableDef` objeto, pasando un puntero al objeto de base de datos.  
  
 Para obtener información relacionada, vea el tema "Método Delete" en la Ayuda de DAO.  
  
##  <a name="execute"></a>CDaoDatabase::Execute  
 Llame a esta función miembro para ejecutar una consulta de acción o ejecutar una instrucción SQL en la base de datos.  
  
```  
void Execute(
    LPCTSTR lpszSQL,  
    int nOptions = dbFailOnError);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszSQL`  
 Puntero a una cadena terminada en null que contiene un comando SQL válido para ejecutar.  
  
 `nOptions`  
 Un entero que especifica las opciones relativas a la integridad de la consulta. Puede utilizar el operador OR bit a bit ( **&#124;**) para combinar cualquiera de las siguientes constantes (proporcionado por la combinación tiene sentido, por ejemplo, podría combinar no **dbInconsistent** con **dbConsistent**):  
  
- **dbDenyWrite** denegar el permiso de escritura a otros usuarios.  
  
- **dbInconsistent** actualizaciones incoherentes (valor predeterminado).  
  
- **dbConsistent** coherencia de las actualizaciones.  
  
- **dbSQLPassThrough** paso a través SQL. Hace que la instrucción SQL que se pasan a un origen de datos ODBC para su procesamiento.  
  
- **dbFailOnError** revertir actualizaciones si se produce un error.  
  
- **dbSeeChanges** generar un error de tiempo de ejecución si otro usuario está cambiando los datos que se va a editar.  
  
> [!NOTE]
>  Si ambos **dbInconsistent** y **dbConsistent** se incluyen o si ninguna de ellas se incluye, el resultado es el valor predeterminado. Para obtener una explicación de estas constantes, vea el tema "Execute Method" en la Ayuda de DAO.  
  
### <a name="remarks"></a>Comentarios  
 **Ejecutar** solo funciona para las consultas de acción o las consultas de paso a través de SQL que no devuelvan resultados. No funciona para las consultas select que devuelven registros.  
  
 Para una definición e información acerca de las consultas de acción, vea los temas "Consulta de acción" y "Execute Method" en la Ayuda de DAO.  
  
> [!TIP]
>  Dada una instrucción SQL sintácticamente correcta y los permisos adecuados, el **Execute** función miembro no se producirá un error incluso si no se puede modificar o eliminar una sola fila. Por tanto, use siempre la **dbFailOnError** opción cuando se usa el **Execute** función de miembro para ejecutar una actualización o consulta de eliminación. Esta opción hace MFC producir una excepción de tipo [CDaoException](../../mfc/reference/cdaoexception-class.md) y revierte todos los cambios correctos si cualquiera de los registros afectados se bloquean y no se actualiza o elimina. Tenga en cuenta que siempre se puede llamar a `GetRecordsAffected` para ver el número de registros se vieron afectado.  
  
 Llame a la [GetRecordsAffected](#getrecordsaffected) función de miembro del objeto de base de datos para determinar el número de registros afectados por la última **Execute** llamar. Por ejemplo, `GetRecordsAffected` devuelve información sobre el número de registros eliminados, actualizados o insertados cuando se ejecuta una consulta de acción. El recuento devuelto no reflejará los cambios en las tablas relacionadas cuando cascade actualiza o elimina entran en vigor.  
  
 **Ejecutar** no devuelve un conjunto de registros. Usar **Execute** en una consulta que selecciona los registros hace MFC producir una excepción de tipo `CDaoException`. (No hay ningún `ExecuteSQL` análogo en función de miembro `CDatabase::ExecuteSQL`.)  
  
##  <a name="getconnect"></a>CDaoDatabase::GetConnect  
 Llame a esta función miembro para recuperar la cadena de conexión utilizada para conectar el `CDaoDatabase` objeto a una base de datos ODBC o ISAM.  
  
```  
CString GetConnect();
```  
  
### <a name="return-value"></a>Valor devuelto  
 La cadena de conexión si [abiertos](#open) se ha llamado correctamente en un origen de datos ODBC; en caso contrario, una cadena vacía. Para un Microsoft Jet (. Base de datos de Microsoft Access), la cadena siempre está vacía a menos que establezca para su uso con el **dbSQLPassThrough** opción utilizada con el [Execute](#execute) función miembro o utilizado en la apertura de un conjunto de registros.  
  
### <a name="remarks"></a>Comentarios  
 La cadena proporciona información sobre el origen de una base de datos abierta o una base de datos utilizada en una consulta de paso. La cadena de conexión se compone de un especificador de tipo de base de datos y cero o más parámetros separados por punto y coma.  
  
> [!NOTE]
>  Usar las clases DAO de MFC para conectarse a un origen de datos a través de ODBC es menos eficaz que la conexión a través de una tabla asociada.  
  
> [!NOTE]
>  La cadena de conexión se utiliza para pasar información adicional a controladores ODBC y algunos controladores ISAM, según sea necesario. No se utiliza para. En el caso de las bases de datos de Microsoft Access. Para las tablas de base de base de datos de Microsoft Jet, la cadena de conexión es una cadena vacía ("") excepto cuando se utiliza para una consulta de paso a través de SQL como se describe en Return Value.  
  
 Consulte la [abiertos](#open) función de miembro para obtener una descripción de cómo se crea la cadena de conexión. Una vez que se ha establecido la cadena de conexión en el **abiertos** llamada, más adelante utilizarla para comprobar la configuración para determinar el tipo, la ruta de acceso, el origen de los datos ODBC, la contraseña o el Id. de usuario de la base de datos.  
  
##  <a name="getname"></a>CDaoDatabase::GetName  
 Llame a esta función miembro para recuperar el nombre de la base de datos abierto actualmente, que es el nombre de un archivo de base de datos existente o el nombre de un origen de datos ODBC registrado.  
  
```  
CString GetName();
```  
  
### <a name="return-value"></a>Valor devuelto  
 La ruta de acceso completa y el nombre de archivo de la base de datos si se realiza correctamente; en caso contrario, vacío [CString](../../atl-mfc-shared/reference/cstringt-class.md).  
  
### <a name="remarks"></a>Comentarios  
 Si la red es compatible con la convención de nomenclatura uniforme (UNC), también puede especificar una ruta de acceso de red, por ejemplo, "\\\\\\\MYSERVER\\\MYSHARE\\\MYDIR\\\MYDB. MDB". (Barras diagonales inversas dobles son necesarias en literales de cadena como "\\" es el carácter de escape de C++.)  
  
 Por ejemplo, podría mostrar este nombre en un encabezado. Si se produce un error mientras se recuperan el nombre, MFC inicia una excepción de tipo [CDaoException](../../mfc/reference/cdaoexception-class.md).  
  
> [!NOTE]
>  Para mejorar el rendimiento cuando se está accediendo bases de datos externas, se recomienda que vincule tablas de base de datos externa a una base de datos de Microsoft Jet (. MDB) en lugar de conectarse directamente al origen de datos.  
  
 El tipo de base de datos se indica mediante el archivo o directorio que la ruta de acceso apunta a, como sigue:  
  
|Puntos de ruta de acceso a...|Tipo de base de datos|  
|--------------------------|-------------------|  
|. Archivo MDB|Base de datos de Microsoft Jet (Microsoft Access)|  
|Directorio que contiene. Archivos DBF|base de datos de dBASE|  
|Directorio que contiene. Archivo XLS|Base de datos de Microsoft Excel|  
|Directorio que contiene. Archivos PDX|Base de datos Paradox|  
|Directorio que contiene archivos de base de datos de texto con el formato apropiado|Base de datos de formato de texto|  
  
 Bases de datos de ODBC como SQL Server y Oracle, cadena de conexión de la base de datos identifica un nombre de origen de datos (DSN) que está registrado por ODBC.  
  
##  <a name="getquerydefcount"></a>CDaoDatabase::GetQueryDefCount  
 Llame a esta función miembro para recuperar el número de consultas definidas en la colección de definiciones de consulta de la base de datos.  
  
```  
short GetQueryDefCount();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de consultas definidas en la base de datos.  
  
### <a name="remarks"></a>Comentarios  
 `GetQueryDefCount`es útil si tiene que recorrer todas las definiciones de consulta en la colección de definiciones de consulta. Para obtener información acerca de una consulta determinada en la colección, consulte [función miembro GetQueryDefInfo](#getquerydefinfo).  
  
##  <a name="getquerydefinfo"></a>CDaoDatabase::GetQueryDefInfo  
 Llame a esta función miembro para obtener información acerca de una consulta definida en la base de datos de diferentes tipos.  
  
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
 `nIndex`  
 El índice de la consulta predefinida en QueryDefs (colección) de la base de datos, para la búsqueda por su índice.  
  
 *querydefinfo*  
 Una referencia a un [CDaoQueryDefInfo](../../mfc/reference/cdaoquerydefinfo-structure.md) objeto que devuelve la información solicitada.  
  
 `dwInfoOptions`  
 Opciones que especifican qué información acerca de los registros que se va a recuperar. Las opciones disponibles son las siguientes junto con lo que hacen que la función devuelva sobre el conjunto de registros:  
  
- `AFX_DAO_PRIMARY_INFO`(Valor predeterminado) Nombre de tipo  
  
- `AFX_DAO_SECONDARY_INFO`Signo más de información principal: fecha de creación, fecha de última actualización, devuelve los registros, actualizables  
  
- `AFX_DAO_ALL_INFO`Más información primaria y secundaria: SQL, conectar, ODBCTimeout  
  
 `lpszName`  
 Una cadena que contiene el nombre de una consulta definida en la base de datos para la búsqueda por nombre.  
  
### <a name="remarks"></a>Comentarios  
 Dos versiones de la función se proporcionan para que pueda seleccionar una consulta por su índice en la colección de definiciones de consulta de la base de datos o por el nombre de la consulta.  
  
 Para obtener una descripción de la información devuelta en *querydefinfo*, consulte el [CDaoQueryDefInfo](../../mfc/reference/cdaoquerydefinfo-structure.md) estructura. Esta estructura no tiene miembros que se corresponden con los elementos de información enumerados anteriormente en la descripción de `dwInfoOptions`. Si se solicita un nivel de información, obtendrá los niveles anteriores de información también.  
  
##  <a name="getquerytimeout"></a>CDaoDatabase::GetQueryTimeout  
 Llame a esta función miembro para recuperar el número de segundos que se permiten antes de que se agotó el tiempo las operaciones subsiguientes en la base de datos conectada actual.  
  
```  
short GetQueryTimeout();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un entero corto que contiene el valor de tiempo de espera en segundos.  
  
### <a name="remarks"></a>Comentarios  
 Una operación podría tiempo de espera debido a problemas de acceso de red, el tiempo de procesamiento de consulta excesivo y así sucesivamente. Mientras que la configuración está en vigor, afecta a todos los abiertos, agregar nuevas, actualizar y eliminar operaciones en los conjuntos de registros asociados con este `CDaoDatabase` objeto. Puede cambiar la configuración de tiempo de espera actual mediante una llamada a [SetQueryTimeout](#setquerytimeout). Cambiar el valor de tiempo de espera de consulta para un conjunto de registros después de la apertura, no cambie el valor para el conjunto de registros. Por ejemplo, posterior [mover](../../mfc/reference/cdaorecordset-class.md#move) operaciones no utilizarán el nuevo valor. El valor predeterminado se establece inicialmente cuando se inicializa el motor de base de datos.  
  
 El valor predeterminado para los tiempos de espera de consulta se realiza desde el registro de Windows. Si no hay ninguna configuración del registro, el valor predeterminado es 60 segundos. No todas las bases de datos admiten la capacidad para establecer un valor de tiempo de espera de consulta. Si establece un valor de tiempo de espera de consulta de 0, se produce sin tiempo de espera; y la comunicación con la base de datos podría dejar de responder. Este comportamiento puede ser útil durante el desarrollo. Si se produce un error en la llamada, MFC inicia una excepción de tipo [CDaoException](../../mfc/reference/cdaoexception-class.md).  
  
 Para obtener información relacionada, vea el tema "Propiedad QueryTimeout" en la Ayuda de DAO.  
  
##  <a name="getrecordsaffected"></a>CDaoDatabase::GetRecordsAffected  
 Llame a esta función miembro para determinar el número de registros afectados por la llamada más reciente de la [Execute](#execute) función miembro.  
  
```  
long GetRecordsAffected();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un entero largo que contiene el número de registros afectados.  
  
### <a name="remarks"></a>Comentarios  
 El valor devuelto incluye el número de registros eliminados, actualizados o insertados por una consulta de acción que se ejecuta con **Execute**. El recuento devuelto no reflejará los cambios en las tablas relacionadas cuando cascade actualiza o elimina entran en vigor.  
  
 Para obtener información relacionada, vea el tema "Propiedad RecordsAffected" en la Ayuda de DAO.  
  
##  <a name="getrelationcount"></a>CDaoDatabase::GetRelationCount  
 Llame a esta función miembro para obtener el número de relaciones definidas entre las tablas de la base de datos.  
  
```  
short GetRelationCount();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de relaciones definidas entre las tablas de la base de datos.  
  
### <a name="remarks"></a>Comentarios  
 **GetRelationCount** es útil si tiene que recorrer todas las relaciones definidas en la colección de relaciones de la base de datos. Para obtener información acerca de una relación determinada de la colección, consulte [GetRelationInfo](#getrelationinfo).  
  
 Para ilustrar el concepto de una relación, considere la posibilidad de una tabla de proveedores y una tabla de productos, que puede que tenga una relación uno a varios. En esta relación, un proveedor puede proporcionar más de un producto. Otras relaciones son uno a uno y varios a varios.  
  
##  <a name="getrelationinfo"></a>CDaoDatabase::GetRelationInfo  
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
 `nIndex`  
 El índice del objeto de relación en la colección de relaciones de la base de datos, para la búsqueda por su índice.  
  
 *relinfo*  
 Una referencia a un [CDaoRelationInfo](../../mfc/reference/cdaorelationinfo-structure.md) objeto que devuelve la información solicitada.  
  
 `dwInfoOptions`  
 Opciones que especifican qué información acerca de la relación para recuperar. Las opciones disponibles son las siguientes junto con lo que hacen que la función devuelva acerca de la relación:  
  
- `AFX_DAO_PRIMARY_INFO`(Valor predeterminado) Tabla externa de nombre, tabla,  
  
- `AFX_DAO_SECONDARY_INFO`Atributos de información de campo  
  
 La información de campo es un [CDaoRelationFieldInfo](../../mfc/reference/cdaorelationfieldinfo-structure.md) objeto que contiene los campos de la tabla principal implicada en la relación.  
  
 `lpszName`  
 Una cadena que contiene el nombre del objeto de relación para la búsqueda por nombre.  
  
### <a name="remarks"></a>Comentarios  
 Dos versiones de esta función proporcionan acceso por índice o por nombre. Para obtener una descripción de la información devuelta en *relinfo*, consulte el [CDaoRelationInfo](../../mfc/reference/cdaorelationinfo-structure.md) estructura. Esta estructura no tiene miembros que se corresponden con los elementos de información enumerados anteriormente en la descripción de `dwInfoOptions`. Si se solicita información en un nivel, también obtendrá información en todos los niveles anteriores.  
  
> [!NOTE]
>  Si establece la relación de atributos del objeto para activar operaciones en cascada ( **dbRelationUpdateCascades** o **dbRelationDeleteCascades**), el motor de base de datos de Microsoft Jet se actualiza automáticamente o Elimina los registros de una o varias tablas cuando se realizan cambios en tablas relacionadas de clave principales. Por ejemplo, supongamos que establece una relación de eliminación en cascada entre una tabla Customers y una tabla Orders. Al eliminar registros de la tabla Customers, también se eliminan registros de la tabla de pedidos relacionados con ese cliente. Además, si establece cascade delete relaciones entre la tabla Orders y otras tablas, registros de esas tablas se eliminan automáticamente cuando se eliminan registros de la tabla Customers.  
  
##  <a name="gettabledefcount"></a>CDaoDatabase:: GetTableDefCount  
 Llame a esta función miembro para recuperar el número de tablas definidas en la base de datos.  
  
```  
short GetTableDefCount();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de definiciones de tabla definidas en la base de datos.  
  
### <a name="remarks"></a>Comentarios  
 `GetTableDefCount`es útil si tiene que recorrer todas las definiciones de tabla en la colección de definiciones de tabla de la base de datos. Para obtener información acerca de una tabla determinada en la colección, consulte [GetTableDefInfo](#gettabledefinfo).  
  
##  <a name="gettabledefinfo"></a>CDaoDatabase:: GetTableDefInfo  
 Llame a esta función miembro para obtener información acerca de una tabla definida en la base de datos de diferentes tipos.  
  
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
 `nIndex`  
 El índice del objeto tabledef en TableDefs (colección) de la base de datos, para la búsqueda por su índice.  
  
 `tabledefinfo`  
 Una referencia a un [CDaoTableDefInfo](../../mfc/reference/cdaotabledefinfo-structure.md) objeto que devuelve la información solicitada.  
  
 `dwInfoOptions`  
 Opciones que especifican qué información acerca de la tabla para recuperar. Las opciones disponibles son las siguientes junto con lo que hacen que la función devuelva acerca de la relación:  
  
- `AFX_DAO_PRIMARY_INFO`(Valor predeterminado) Nombre actualizable, atributos  
  
- `AFX_DAO_SECONDARY_INFO`Signo más de información principal: fecha de creación, fecha de la última actualización, nombre de la tabla de origen, conectar  
  
- `AFX_DAO_ALL_INFO`Más información primaria y secundaria: número de registros de la regla de validación, texto de validación  
  
 `lpszName`  
 El nombre del objeto de definición de tabla para la búsqueda por nombre.  
  
### <a name="remarks"></a>Comentarios  
 Por lo que puede seleccionar una tabla de índice en la colección de definiciones de tabla de la base de datos o el nombre de la tabla, se proporcionan dos versiones de la función.  
  
 Para obtener una descripción de la información devuelta en `tabledefinfo`, consulte el [CDaoTableDefInfo](../../mfc/reference/cdaotabledefinfo-structure.md) estructura. Esta estructura no tiene miembros que se corresponden con los elementos de información enumerados anteriormente en la descripción de `dwInfoOptions`. Si se solicita información en un nivel, obtendrá información para todos los niveles anteriores.  
  
> [!NOTE]
>  El `AFX_DAO_ALL_INFO` opción proporciona información que puede resultar lenta a obtener. En este caso, el recuento de los registros en la tabla podría ser muy lento si hay muchos registros.  
  
##  <a name="getversion"></a>CDaoDatabase::GetVersion  
 Llame a esta función miembro para determinar la versión del archivo de base de datos de Microsoft Jet.  
  
```  
CString GetVersion();
```  
  
### <a name="return-value"></a>Valor devuelto  
 A [CString](../../atl-mfc-shared/reference/cstringt-class.md) que indica la versión del archivo de base de datos asociado al objeto.  
  
### <a name="remarks"></a>Comentarios  
 El valor devuelto representa el número de versión en la forma "principal.secundario"; Por ejemplo, "3.0". El número de versión de producto (por ejemplo, 3.0) está formada por el número de versión (3), un punto y el número de versión (0). Las versiones hasta la fecha son 1.0, 1.1, 2.0 y 3.0.  
  
 Para obtener información relacionada, vea el tema "Propiedad de versión" en la Ayuda de DAO.  
  
##  <a name="isopen"></a>CDaoDatabase::IsOpen  
 Llame a esta función miembro para determinar si la `CDaoDatabase` objeto está actualmente abierto en una base de datos.  
  
```  
BOOL IsOpen() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si la `CDaoDatabase` objeto está actualmente abierto; de lo contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="m_pdaodatabase"></a>CDaoDatabase::m_pDAODatabase  
 Contiene un puntero a la interfaz OLE para el objeto de base de datos DAO subyacente la `CDaoDatabase` objeto.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este puntero si necesita acceso directo a la interfaz DAO.  
  
 Para obtener información acerca de cómo llamar a DAO directamente, vea [Nota técnica 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).  
  
##  <a name="m_pworkspace"></a>CDaoDatabase::m_pWorkspace  
 Contiene un puntero a la [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md) objeto que contiene el objeto de base de datos.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este puntero si necesita acceder directamente el área de trabajo, por ejemplo, para obtener punteros a otros objetos de base de datos de colección de bases de datos del área de trabajo.  
  
##  <a name="open"></a>CDaoDatabase::Open  
 Debe llamar a esta función miembro para inicializar un recién construido `CDaoDatabase` objeto que representa una base de datos existente.  
  
```  
virtual void Open(
    LPCTSTR lpszName,  
    BOOL bExclusive = FALSE,  
    BOOL bReadOnly = FALSE,  
    LPCTSTR lpszConnect = _T(""));
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszName`  
 Una expresión de cadena que es el nombre de una existente de Microsoft Jet (. Archivo de base de datos de Microsoft Access). Si el nombre de archivo tiene una extensión, se requiere. Si la red es compatible con la convención de nomenclatura uniforme (UNC), también puede especificar una ruta de acceso de red, como "\\\\\\\MYSERVER\\\MYSHARE\\\MYDIR\\\MYDB. MDB". (Barras diagonales inversas dobles son necesarias en literales de cadena como "\\" es el carácter de escape de C++.)  
  
 Algunas consideraciones que se aplican al usar `lpszName`. Si lo:  
  
-   Hace referencia a una base de datos que ya está abierto para acceso exclusivo por otro usuario, MFC inicia una excepción de tipo [CDaoException](../../mfc/reference/cdaoexception-class.md). Captura de esa excepción para que el usuario sepa que la base de datos no está disponible.  
  
-   Es una cadena vacía ("") y *lpszConnect* es "ODBC;", se muestra un cuadro de diálogo lista de todos los nombres de origen de datos ODBC para el usuario pueda seleccionar una base de datos. Debe evitar conexiones directas a orígenes de datos ODBC; Utilice en su lugar una tabla asociada.  
  
-   En caso contrario, no hace referencia a una base de datos existente o válido ODBC nombre origen de datos, MFC inicia una excepción de tipo `CDaoException`.  
  
> [!NOTE]
>  Para obtener más información acerca de los códigos de error DAO, vea el DAOERR. H del proyecto. Para obtener información relacionada, vea el tema "Errores interceptables de acceso de datos" en la Ayuda de DAO.  
  
 `bExclusive`  
 Un valor booleano que es **TRUE** si la base de datos es abrir obtener un acceso exclusivo (no compartido) y **FALSE** si la base de datos se pueden abrir para el acceso compartido. Si se omite este argumento, se abre la base de datos para el acceso compartido.  
  
 `bReadOnly`  
 Un valor booleano que es **TRUE** si la base de datos consiste en Abrir para acceso de solo lectura y **FALSE** si la base de datos que se va a estar abierto para acceso de lectura/escritura. Si se omite este argumento, la base de datos se abre para acceso de lectura/escritura. Todos los conjuntos de registros dependientes heredan este atributo.  
  
 `lpszConnect`  
 Una expresión de cadena utilizada para abrir la base de datos. Esta cadena constituye ODBC conectarse argumentos. Debe proporcionar los argumentos mutuamente y de solo lectura para proporcionar una cadena de origen. Si la base de datos es una base de datos de Microsoft Jet (. MDB), esta cadena está vacía (""). La sintaxis para el valor predeterminado: **_T**(""), proporciona portabilidad para Unicode como ANSI para la compilación de la aplicación.  
  
### <a name="remarks"></a>Comentarios  
 **Abra** asocia la base de datos con el objeto DAO subyacente. No se puede usar el objeto de base de datos para construir el conjunto de registros, tabledef o querydef (objetos) hasta que se inicializa. **Abra** anexa el objeto de base de datos a la colección de bases de datos del área de trabajo asociada.  
  
 Use los parámetros de la siguiente manera:  
  
-   Si se está abriendo un Microsoft Jet (. Base de datos de Microsoft Access), utilice la `lpszName` parámetro y pase una cadena vacía para el `lpszConnect` parámetro o pase una cadena de contraseña de la forma "; PWD = contraseña "si la base de datos está protegido por contraseña (. MDB sólo bases de datos).  
  
-   Si se está abriendo un origen de datos ODBC, pase una cadena de conexión ODBC válida en `lpszConnect` y una cadena vacía en `lpszName`.  
  
 Para obtener información relacionada, vea el tema "Método OpenDatabase" en la Ayuda de DAO.  
  
> [!NOTE]
>  Para mejorar el rendimiento al obtener acceso a bases de datos externas, incluidas las bases de datos ISAM y orígenes de datos ODBC, se recomienda que vincule tablas de base de datos externa a una base de datos de motor de Microsoft Jet (. MDB) en lugar de conectarse directamente al origen de datos.  
  
 Es posible que un intento de conexión en tiempo de espera si, por ejemplo, el host DBMS no está disponible. Si se produce un error en el intento de conexión, **abiertos** produce una excepción de tipo [CDaoException](../../mfc/reference/cdaoexception-class.md).  
  
 Las observaciones restantes se aplican únicamente a las bases de datos ODBC:  
  
 Si la base de datos es una base de datos ODBC y los parámetros en su **abiertos** llamada no contienen información suficiente para realizar la conexión, el controlador ODBC abre un cuadro de diálogo para obtener la información necesaria del usuario. Cuando se llama a **abiertos**, la cadena de conexión, `lpszConnect`, se almacena de forma privada y está disponible mediante una llamada a la [GetConnect](#getconnect) función miembro.  
  
 Si lo desea, puede abrir su propio cuadro de diálogo antes de llamar a **abrir** para obtener información del usuario, como una contraseña, a continuación, agregue dicha información a la cadena de conexión se pasa a **abrir**. Es posible que quiera guardar la cadena de conexión se pasa (por ejemplo, en el registro de Windows), por lo que puede volver a usarla la próxima vez su aplicación llama **abiertos** en un `CDaoDatabase` objeto.  
  
 También puede utilizar la cadena de conexión para varios niveles de autorización de inicio de sesión (cada uno de ellos para otro `CDaoDatabase` objeto) o para transmitir otra información específica de la base de datos.  
  
##  <a name="setquerytimeout"></a>CDaoDatabase::SetQueryTimeout  
 Llame a esta función miembro para anular el número predeterminado de segundos que se permiten antes de las operaciones subsiguientes en el tiempo de espera de base de datos conectada.  
  
```  
void SetQueryTimeout(short nSeconds);
```  
  
### <a name="parameters"></a>Parámetros  
 `nSeconds`  
 El número de segundos que se permiten antes de un intento de consulta agote el tiempo de espera.  
  
### <a name="remarks"></a>Comentarios  
 Una operación podría tiempo de espera debido a problemas de acceso de red, el tiempo de procesamiento de consulta excesivo y así sucesivamente. Llame a `SetQueryTimeout` antes de abrir el conjunto de registros o antes de llamar a la función miembro [AddNew](../../mfc/reference/cdaorecordset-class.md#addnew), [actualización](../../mfc/reference/cdaorecordset-class.md#update), o [eliminar](../../mfc/reference/cdaorecordset-class.md#delete) funciones miembro si desea cambiar la consulta valor de tiempo de espera. El valor afecta a todas las posteriores [abiertos](../../mfc/reference/cdaorecordset-class.md#open), `AddNew`, **actualización**, y **eliminar** llamadas a los conjuntos de registros asociados con este `CDaoDatabase` objeto. Cambiar el valor de tiempo de espera de consulta para un conjunto de registros después de la apertura, no cambie el valor para el conjunto de registros. Por ejemplo, posterior [mover](../../mfc/reference/cdaorecordset-class.md#move) operaciones no utilizarán el nuevo valor.  
  
 El valor predeterminado para los tiempos de espera de consulta es 60 segundos. No todas las bases de datos admiten la capacidad para establecer un valor de tiempo de espera de consulta. Si establece un valor de tiempo de espera de consulta de 0, se produce sin tiempo de espera; la comunicación con la base de datos podría dejar de responder. Este comportamiento puede ser útil durante el desarrollo.  
  
 Para obtener información relacionada, vea el tema "Propiedad QueryTimeout" en la Ayuda de DAO.  
  
## <a name="see-also"></a>Vea también  
 [CObject (clase)](../../mfc/reference/cobject-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CDaoWorkspace (clase)](../../mfc/reference/cdaoworkspace-class.md)   
 [CDaoRecordset (clase)](../../mfc/reference/cdaorecordset-class.md)   
 [Clase CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)   
 [CDaoQueryDef (clase)](../../mfc/reference/cdaoquerydef-class.md)   
 [CDatabase (clase)](../../mfc/reference/cdatabase-class.md)   
 [CDaoException (clase)](../../mfc/reference/cdaoexception-class.md)
