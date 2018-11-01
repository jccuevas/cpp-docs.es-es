---
title: CDaoQueryDefInfo (Estructura)
ms.date: 11/04/2016
f1_keywords:
- CDaoQueryDefInfo
helpviewer_keywords:
- DAO (Data Access Objects), QueryDefs collection
- CDaoQueryDefInfo structure [MFC]
ms.assetid: e20837dc-e78d-4171-a195-1b4075fb5d2a
ms.openlocfilehash: f3c8b464a84bd33d15a19f24010b942bdea59620
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50603000"
---
# <a name="cdaoquerydefinfo-structure"></a>CDaoQueryDefInfo (Estructura)

El `CDaoQueryDefInfo` estructura contiene información sobre un objeto de definición de consulta definido para los objetos de acceso a datos (DAO).

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
Identifica inequívocamente el objeto de definición de consulta. Para obtener más información, vea el tema "Nombre de la propiedad" en la Ayuda de DAO. Llame a [CDaoQueryDef::GetName](../../mfc/reference/cdaoquerydef-class.md#getname) para recuperar esta propiedad directamente.

*m_nType*<br/>
Un valor que indica el tipo de un objeto querydef operativo. El valor puede ser uno de los siguientes:

- `dbQSelect` Seleccione — la consulta selecciona los registros.

- `dbQAction` Acción: la consulta se mueve o cambia los datos pero no devuelve ningún registro.

- `dbQCrosstab` Tabla de referencias cruzadas, la consulta devuelve los datos en un formato de hojas de cálculo.

- `dbQDelete` Eliminar: la consulta elimina un conjunto de filas especificados.

- `dbQUpdate` Actualización: la consulta cambia un conjunto de registros.

- `dbQAppend` Anexar, la consulta agrega nuevos registros hasta el final de una tabla o consulta.

- `dbQMakeTable` Creación de tabla: la consulta crea una nueva tabla de conjunto de registros.

- `dbQDDL` Definición de datos, la consulta afecta a la estructura de tablas o de sus partes.

- `dbQSQLPassThrough` Paso a través, la instrucción SQL se pasa directamente a la base de datos de back-end, sin procesamiento intermedio.

- `dbQSetOperation` La consulta de unión, crea un objeto de conjunto de registros de tipo de instantánea que contiene datos de todos los registros especificados en dos o más tablas con todos los registros duplicados se quitan. Para incluir los duplicados, agregue la palabra clave **todas** en la instrucción SQL de la definición de la consulta.

- `dbQSPTBulk` Puede usar con `dbQSQLPassThrough` para especificar una consulta que no devuelve ningún registro.

> [!NOTE]
>  Para crear una consulta de paso a través de SQL, no establezca la `dbQSQLPassThrough` constante. Esto se establece automáticamente el motor de base de datos Microsoft Jet cuando se crea un objeto de definición de consulta y establecer la propiedad Connect.

Para obtener más información, vea el tema "Propiedad de tipo" en la Ayuda de DAO.

*m_dateCreated*<br/>
La fecha y hora de que creación de la definición de consulta. Para recuperar directamente la fecha en que se creó la definición de consulta, llame el [GetDateCreated](../../mfc/reference/cdaotabledef-class.md#getdatecreated) función miembro de la `CDaoTableDef` objeto asociado a la tabla. Para obtener más información, vea los comentarios a continuación. También vea el tema "DateCreated y LastUpdated propiedades" en la Ayuda de DAO.

*m_dateLastUpdated*<br/>
La fecha y hora de los cambios más recientes realizados en la definición de consulta. Para recuperar directamente la fecha en que se actualizó por última vez la tabla, llame el [GetDateLastUpdated](../../mfc/reference/cdaoquerydef-class.md#getdatelastupdated) función miembro de la definición de consulta. Para obtener más información, vea los comentarios a continuación. Y vea el tema "DateCreated y LastUpdated propiedades" en la Ayuda de DAO.

*m_bUpdatable*<br/>
Indica si se pueden realizar cambios a un objeto de definición de consulta. Si esta propiedad es TRUE, la definición de consulta es actualizable; en caso contrario, no lo es. Actualizable significa que se puede cambiar la definición de la consulta del objeto de definición de consulta. La propiedad actualizable de un objeto de definición de consulta se establece en TRUE si se puede actualizar la definición de consulta, incluso si el conjunto de registros resultante no es actualizable. Para recuperar esta propiedad directamente, llame a la definición de consulta [CanUpdate](../../mfc/reference/cdaoquerydef-class.md#canupdate) función miembro. Para obtener más información, vea el tema "Propiedad actualizable" en la Ayuda de DAO.

*m_bReturnsRecords*<br/>
Indica si una consulta de paso a través de SQL para una base de datos externa devuelve registros. Si esta propiedad es TRUE, la consulta devuelve los registros. Para recuperar directamente esta propiedad, llame al [CDaoQueryDef::GetReturnsRecords](../../mfc/reference/cdaoquerydef-class.md#getreturnsrecords). No todas las consultas de paso a través de SQL para bases de datos externas devuelven registros. Por ejemplo, una instancia de SQL **actualización** instrucción actualiza los registros sin devolver registros, mientras una instancia de SQL **seleccione** instrucción devolver registros. Para obtener más información, vea el tema "Propiedad ReturnsRecords" en la Ayuda de DAO.

*m_strSQL*<br/>
La instrucción SQL que define la consulta ejecutada por un objeto de definición de consulta. La propiedad SQL contiene la instrucción SQL que determina cómo se seleccionan, agrupan y ordenan los registros cuando ejecute la consulta. Puede usar la consulta para seleccionar los registros que desee incluir en un objeto de conjunto de registros de tipo dinámico o instantánea. También puede definir consultas de gran volumen para modificar los datos sin devolver los registros. Puede recuperar el valor de esta propiedad directamente mediante una llamada a la definición de consulta [GetSQL](../../mfc/reference/cdaoquerydef-class.md#getsql) función miembro.

*m_strConnect*<br/>
Proporciona información sobre el origen de una base de datos de una consulta de paso a través. Esta información adopta la forma de una cadena de conexión. Para obtener más información acerca de connect cadenas y para obtener información acerca de cómo recuperar el valor de esta propiedad directamente, vea el [CDaoDatabase::GetConnect](../../mfc/reference/cdaodatabase-class.md#getconnect) función miembro.

*m_nODBCTimeout*<br/>
El número de segundos que espera el motor de base de datos Microsoft Jet antes de un error de tiempo de espera se produce cuando se ejecuta una consulta en una base de datos ODBC. Cuando se usa una base de datos ODBC, como Microsoft SQL Server, puede haber retrasos debido a uso de tráfico o con mucha actividad de red del servidor ODBC. En lugar de esperar indefinidamente, puede especificar cuánto tiempo espera el motor Microsoft Jet antes de que se produce un error. El valor de tiempo de espera predeterminado es 60 segundos. Puede recuperar el valor de esta propiedad directamente mediante una llamada a la definición de consulta [GetODBCTimeout](../../mfc/reference/cdaoquerydef-class.md#getodbctimeout) función miembro. Para obtener más información, vea el tema "Propiedad ODBCTimeout" en la Ayuda de DAO.

## <a name="remarks"></a>Comentarios

La definición de consulta es un objeto de clase [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md). Las referencias a principal, secundaria y todo lo anterior indican cómo devuelve la información de la [función miembro GetQueryDefInfo](../../mfc/reference/cdaodatabase-class.md#getquerydefinfo) función miembro de clase `CDaoDatabase`.

Información recuperada por el [CDaoDatabase::GetQueryDefInfo](../../mfc/reference/cdaodatabase-class.md#getquerydefinfo) función miembro se almacena en un `CDaoQueryDefInfo` estructura. Llame a `GetQueryDefInfo` para el objeto de base de datos en cuya colección de definiciones de consulta se almacena el objeto de definición de consulta. `CDaoQueryDefInfo` También define un `Dump` se basa en función de miembro en modo de depuración. Puede usar `Dump` para volcar el contenido de un `CDaoQueryDefInfo` objeto. Clase `CDaoDatabase` también proporciona funciones de miembro para el acceso directo a todas las propiedades que se devuelven en un `CDaoQueryDefInfo` objeto, por lo que probablemente rara vez necesitará llamar a `GetQueryDefInfo`.

Al anexar un nuevo campo u objeto de parámetro a la colección de campos o parámetros de un objeto de definición de consulta, se produce una excepción si la base de datos subyacente no admite el tipo de datos especificado para el nuevo objeto.

La configuración de fecha y hora se deriva del equipo en el que se creó o actualizó por última vez la definición de consulta. En un entorno multiusuario, los usuarios deben obtener estos valores directamente desde el servidor de archivos mediante el **net tiempo** comando para evitar las discrepancias en los valores de propiedades DateCreated y LastUpdated.

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdao.h

## <a name="see-also"></a>Vea también

[Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoQueryDef (clase)](../../mfc/reference/cdaoquerydef-class.md)<br/>
[CDaoDatabase (clase)](../../mfc/reference/cdaodatabase-class.md)
