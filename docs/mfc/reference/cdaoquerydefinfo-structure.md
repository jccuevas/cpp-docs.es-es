---
title: CDaoQueryDefInfo (Estructura)
ms.date: 11/04/2016
f1_keywords:
- CDaoQueryDefInfo
helpviewer_keywords:
- DAO (Data Access Objects), QueryDefs collection
- CDaoQueryDefInfo structure [MFC]
ms.assetid: e20837dc-e78d-4171-a195-1b4075fb5d2a
ms.openlocfilehash: e2f0325237a30989637821464c63a4d8b8000b1e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368935"
---
# <a name="cdaoquerydefinfo-structure"></a>CDaoQueryDefInfo (Estructura)

La `CDaoQueryDefInfo` estructura contiene información sobre un objeto querydef definido para objetos de acceso a datos (DAO).

## <a name="syntax"></a>Sintaxis

```
struct CDaoQueryDefInfo
{
    CString m_strName;               // Primary
    short m_nType;   // Primary
    COleDateTime m_dateCreated;      // Secondary
    COleDateTime m_dateLastUpdated;  // Secondary
    BOOL m_bUpdatable;               // Secondary
    BOOL m_bReturnsRecords;          // Secondary
    CString m_strSQL;                // All
    CString m_strConnect;            // All
    short m_nODBCTimeout;            // All
};
```

#### <a name="parameters"></a>Parámetros

*m_strName*<br/>
Asigna un nombre único al objeto querydef. Para obtener más información, vea el tema "Propiedad de nombre" en la Ayuda de DAO. Llame a [CDaoQueryDef::GetName](../../mfc/reference/cdaoquerydef-class.md#getname) para recuperar esta propiedad directamente.

*m_nType*<br/>
Valor que indica el tipo operativo de un objeto querydef. El valor puede ser uno de los siguientes:

- `dbQSelect`Seleccionar: la consulta selecciona registros.

- `dbQAction`Acción: la consulta mueve o cambia los datos, pero no devuelve registros.

- `dbQCrosstab`Ficha cruzada: la consulta devuelve datos en un formato similar a una hoja de cálculo.

- `dbQDelete`Delete: la consulta elimina un conjunto de filas especificadas.

- `dbQUpdate`Actualizar: la consulta cambia un conjunto de registros.

- `dbQAppend`Anexar: la consulta agrega nuevos registros al final de una tabla o consulta.

- `dbQMakeTable`Make-table: la consulta crea una nueva tabla a partir de un conjunto de registros.

- `dbQDDL`Definición de datos: la consulta afecta a la estructura de las tablas o sus partes.

- `dbQSQLPassThrough`Paso a través: la instrucción SQL se pasa directamente al back-end de la base de datos, sin procesamiento intermedio.

- `dbQSetOperation`Unión: la consulta crea un objeto de conjunto de registros de tipo instantánea que contiene datos de todos los registros especificados en dos o más tablas con los registros duplicados eliminados. Para incluir los duplicados, agregue la palabra clave **ALL** en la instrucción SQL de la definición de consulta.

- `dbQSPTBulk`Se `dbQSQLPassThrough` utiliza con para especificar una consulta que no devuelve registros.

> [!NOTE]
> Para crear una consulta de paso a `dbQSQLPassThrough` través de SQL, no se establece la constante. Esto lo establece automáticamente el motor de base de datos Microsoft Jet al crear un objeto querydef y establecer la propiedad Connect.

Para obtener más información, vea el tema "Propiedad de tipo" en la Ayuda de DAO.

*m_dateCreated*<br/>
La fecha y hora en que se creó la definición de consulta. Para recuperar directamente la fecha en que se creó la `CDaoTableDef` definición de consulta, llame a la [GetDateCreated](../../mfc/reference/cdaotabledef-class.md#getdatecreated) función miembro del objeto asociado a la tabla. Consulte Comentarios a continuación para obtener más información. Consulte también el tema "DateCreated, LastUpdated Properties" en la Ayuda de DAO.

*m_dateLastUpdated*<br/>
La fecha y hora del cambio más reciente realizado en la definición de consulta. Para recuperar directamente la fecha en que se actualizó por última vez la tabla, llame a la [GetDateLastUpdated](../../mfc/reference/cdaoquerydef-class.md#getdatelastupdated) función miembro de la definición de consulta. Consulte Comentarios a continuación para obtener más información. Y vea el tema "DateCreated, LastUpdated Properties" en la Ayuda de DAO.

*m_bUpdatable*<br/>
Indica si se pueden realizar cambios en un objeto querydef. Si esta propiedad es TRUE, la definición de consulta es actualizable; de lo contrario, no lo es. Actualizable significa que se puede cambiar la definición de consulta del objeto querydef. La propiedad Updatable de un objeto querydef se establece en TRUE si se puede actualizar la definición de consulta, incluso si el conjunto de registros resultante no es actualizable. Para recuperar esta propiedad directamente, llame a la definición de consulta [CanUpdate](../../mfc/reference/cdaoquerydef-class.md#canupdate) función miembro. Para obtener más información, vea el tema "Propiedad actualizable" en la Ayuda de DAO.

*m_bReturnsRecords*<br/>
Indica si una consulta de paso a través de SQL a una base de datos externa devuelve registros. Si esta propiedad es TRUE, la consulta devuelve registros. Para recuperar directamente esta propiedad, llame a [CDaoQueryDef::GetReturnsRecords](../../mfc/reference/cdaoquerydef-class.md#getreturnsrecords). No todas las consultas de paso a través de SQL a bases de datos externas devuelven registros. Por ejemplo, una instrucción **UPDATE** de SQL actualiza los registros sin devolver registros, mientras que una instrucción **SELECT** de SQL devuelve registros. Para obtener más información, vea el tema "ReturnsRecords Property" en la Ayuda de DAO.

*m_strSQL*<br/>
La instrucción SQL que define la consulta ejecutada por un objeto querydef. La propiedad SQL contiene la instrucción SQL que determina cómo se seleccionan, agrupan y ordenan los registros al ejecutar la consulta. Puede utilizar la consulta para seleccionar registros que se incluirán en un objeto de conjunto de registros de tipo dinámico o de instantánea. También puede definir consultas masivas para modificar datos sin devolver registros. Puede recuperar el valor de esta propiedad directamente llamando a la definición de consulta [GetSQL](../../mfc/reference/cdaoquerydef-class.md#getsql) función miembro.

*m_strConnect*<br/>
Proporciona información sobre el origen de una base de datos utilizada en una consulta de paso a través. Esta información toma la forma de una cadena de conexión. Para obtener más información acerca de las cadenas de conexión y para obtener información acerca de cómo recuperar el valor de esta propiedad directamente, vea el [CDaoDatabase::GetConnect](../../mfc/reference/cdaodatabase-class.md#getconnect) función miembro.

*m_nODBCTimeout*<br/>
El número de segundos que el motor de base de datos de Microsoft Jet espera antes de que se produzca un error de tiempo de espera cuando se ejecuta una consulta en una base de datos ODBC. Cuando se usa una base de datos ODBC, como Microsoft SQL Server, puede haber retrasos debido al tráfico de red o al uso intensivo del servidor ODBC. En lugar de esperar indefinidamente, puede especificar cuánto tiempo espera el motor de Microsoft Jet antes de que produzca un error. El valor de tiempo de espera predeterminado es 60 segundos. Puede recuperar el valor de esta propiedad directamente llamando a la función miembro [GetODBCTimeout](../../mfc/reference/cdaoquerydef-class.md#getodbctimeout) de la definición de consulta. Para obtener más información, vea el tema "Propiedad ODBCTimeout" en la Ayuda de DAO.

## <a name="remarks"></a>Observaciones

Querydef es un objeto de la clase [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md). Las referencias a Primary, Secondary y All anteriorindican cómo devuelve la información la `CDaoDatabase`función miembro [GetQueryDefInfo](../../mfc/reference/cdaodatabase-class.md#getquerydefinfo) en la clase .

Información recuperada por el [CDaoDatabase::GetQueryDefInfo](../../mfc/reference/cdaodatabase-class.md#getquerydefinfo) función miembro se almacena en una `CDaoQueryDefInfo` estructura. Llame `GetQueryDefInfo` al objeto de base de datos en cuya colección QueryDefs se almacena el objeto querydef. `CDaoQueryDefInfo`también define `Dump` una función miembro en compilaciones de depuración. Puede utilizar `Dump` para volcar `CDaoQueryDefInfo` el contenido de un objeto. Class `CDaoDatabase` también proporciona funciones miembro para tener acceso `CDaoQueryDefInfo` directamente a todas las propiedades `GetQueryDefInfo`devueltas en un objeto, por lo que probablemente rara vez tendrá que llamar a .

Al anexar un nuevo campo o objeto de parámetro a la colección Fields o Parameters de un objeto querydef, se produce una excepción si la base de datos subyacente no admite el tipo de datos especificado para el nuevo objeto.

La configuración de fecha y hora se deriva del equipo en el que se creó o actualizó por última vez la definición de consulta. En un entorno multiusuario, los usuarios deben obtener esta configuración directamente desde el servidor de archivos mediante el comando **net time** para evitar discrepancias en la configuración de las propiedades DateCreated y LastUpdated.

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdao.h

## <a name="see-also"></a>Consulte también

[Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[Clase CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)<br/>
[CDaoDatabase (clase)](../../mfc/reference/cdaodatabase-class.md)
