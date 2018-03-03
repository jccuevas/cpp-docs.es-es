---
title: CDaoQueryDefInfo (estructura) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDaoQueryDefInfo
dev_langs:
- C++
helpviewer_keywords:
- DAO (Data Access Objects), QueryDefs collection
- CDaoQueryDefInfo structure [MFC]
ms.assetid: e20837dc-e78d-4171-a195-1b4075fb5d2a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e476fd8e95b48b59bbb3bae41d9ad84829ca8fa9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="cdaoquerydefinfo-structure"></a>CDaoQueryDefInfo (Estructura)
El `CDaoQueryDefInfo` estructura contiene información sobre un objeto de definición de consulta definido para objetos de acceso a datos (DAO).  
  
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
 `m_strName`  
 Identifica inequívocamente el objeto de definición de consulta. Para obtener más información, vea el tema "Nombre de propiedad" en la Ayuda de DAO. Llame a [CDaoQueryDef::GetName](../../mfc/reference/cdaoquerydef-class.md#getname) para recuperar esta propiedad directamente.  
  
 `m_nType`  
 Un valor que indica el tipo de un objeto querydef operativo. El valor puede ser uno de los siguientes:  
  
- **dbQSelect** seleccione, la consulta selecciona los registros.  
  
- **dbQAction** acción, la consulta se mueve o cambia los datos pero no devuelve ningún registro.  
  
- **dbQCrosstab** tabla de referencias cruzadas, la consulta devuelve los datos en un formato de hoja de cálculo.  
  
- **dbQDelete** eliminar, la consulta elimina un conjunto de filas especificados.  
  
- **dbQUpdate** actualización: la consulta cambia un conjunto de registros.  
  
- **dbQAppend** anexado, la consulta agrega nuevos registros al final de una tabla o consulta.  
  
- **dbQMakeTable** creación de tabla, la consulta crea una nueva tabla de un conjunto de registros.  
  
- **dbQDDL** definición de datos, la consulta afecta a la estructura de tablas o sus partes.  
  
- **dbQSQLPassThrough** acceso directo: la instrucción SQL se pasa directamente a la base de datos de back-end, sin procesamiento intermedio.  
  
- **dbQSetOperation** unión, la consulta crea un objeto de conjunto de registros de tipo de instantánea que contiene datos de todos los registros especificados en dos o más tablas con registros duplicados se quitan. Para incluir los duplicados, agregue la palabra clave **todos los** en la instrucción SQL de la definición de la consulta.  
  
- **dbQSPTBulk** utilizar con **dbQSQLPassThrough** para especificar una consulta que no devuelve ningún registro.  
  
> [!NOTE]
>  Para crear una consulta de paso a través de SQL, no establezca la **dbQSQLPassThrough** constante. Esto se establece automáticamente el motor de base de datos de Microsoft Jet cuando se crea un objeto de definición de consulta y establecer la propiedad Connect.  
  
 Para obtener más información, vea el tema "Tipo de propiedad" en la Ayuda de DAO.  
  
 `m_dateCreated`  
 La fecha y hora en que se creó la definición de consulta. Para recuperar directamente la fecha de creación de la definición de consulta, llame a la [GetDateCreated](../../mfc/reference/cdaotabledef-class.md#getdatecreated) función miembro de la `CDaoTableDef` objeto asociado a la tabla. Para obtener más información, vea comentarios a continuación. Consulte también el tema "DateCreated y LastUpdated propiedades" en la Ayuda de DAO.  
  
 `m_dateLastUpdated`  
 La fecha y hora del cambio más reciente realizado en la definición de consulta. Para recuperar directamente la fecha en que se actualizó por última vez la tabla, llame a la [GetDateLastUpdated](../../mfc/reference/cdaoquerydef-class.md#getdatelastupdated) función miembro de la definición de consulta. Para obtener más información, vea comentarios a continuación. Y vea el tema "DateCreated y LastUpdated propiedades" en la Ayuda de DAO.  
  
 `m_bUpdatable`  
 Indica si se pueden realizar cambios a un objeto de definición de consulta. Si esta propiedad es **TRUE**, la definición de consulta es actualizable; de lo contrario, no lo es. Actualizable significa que se puede cambiar la definición de la consulta del objeto de definición de consulta. Se establece la propiedad de un objeto querydef actualizable en **TRUE** si puede actualizarse la definición de consulta, incluso si el conjunto de registros resultante no es actualizable. Para recuperar esta propiedad directamente, llame a la definición de consulta [CanUpdate](../../mfc/reference/cdaoquerydef-class.md#canupdate) función miembro. Para obtener más información, vea el tema "Propiedad actualizable" en la Ayuda de DAO.  
  
 *m_bReturnsRecords*  
 Indica si una consulta de paso a través de SQL para una base de datos externa devuelve registros. Si esta propiedad es **TRUE**, la consulta devuelve registros. Para recuperar directamente esta propiedad, llame a [CDaoQueryDef::GetReturnsRecords](../../mfc/reference/cdaoquerydef-class.md#getreturnsrecords). No todas las consultas de paso a través de SQL para bases de datos externas devuelven registros. Por ejemplo, una instancia de SQL **actualización** instrucción actualiza registros sin devolver registros, mientras una instancia de SQL **seleccione** instrucción devuelva registros. Para obtener más información, vea el tema "Propiedad ReturnsRecords" en la Ayuda de DAO.  
  
 *m_strSQL*  
 La instrucción SQL que define la consulta ejecutada por un objeto de definición de consulta. La propiedad SQL contiene la instrucción SQL que determina cómo se seleccionan, agrupan y ordenan los registros cuando se ejecuta la consulta. Puede usar la consulta para seleccionar los registros que se incluirán en un objeto de conjunto de registros de tipo dynaset o snapshot. También puede definir consultas de forma masiva para modificar datos sin devolver los registros. Puede recuperar el valor de esta propiedad directamente mediante una llamada a la definición de consulta [GetSQL](../../mfc/reference/cdaoquerydef-class.md#getsql) función miembro.  
  
 `m_strConnect`  
 Proporciona información sobre el origen de una base de datos utilizada en una consulta de paso. Esta información toma la forma de una cadena de conexión. Para obtener más información acerca las cadenas de conexión y para obtener información acerca de cómo recuperar el valor de esta propiedad directamente, vea la [CDaoDatabase::GetConnect](../../mfc/reference/cdaodatabase-class.md#getconnect) función miembro.  
  
 *m_nODBCTimeout*  
 El número de segundos que espera a que el motor de base de datos de Microsoft Jet antes de un error de tiempo de espera se produce cuando se ejecuta una consulta en una base de datos ODBC. Cuando se usa una base de datos ODBC, como Microsoft SQL Server, puede haber retrasos debido a la utilice de tráfico o a la sobrecarga de red del servidor ODBC. En lugar de esperar indefinidamente, puede especificar cuánto tiempo espera el motor Microsoft Jet antes de que se producirá un error. El valor de tiempo de espera predeterminado es 60 segundos. Puede recuperar el valor de esta propiedad directamente mediante una llamada a la definición de consulta [GetODBCTimeout](../../mfc/reference/cdaoquerydef-class.md#getodbctimeout) función miembro. Para obtener más información, vea el tema "Propiedad ODBCTimeout" en la Ayuda de DAO.  
  
## <a name="remarks"></a>Comentarios  
 La definición de consulta es un objeto de clase [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md). Las referencias a principal, secundaria y todo lo anterior indican cómo se devuelve la información de la [función miembro GetQueryDefInfo](../../mfc/reference/cdaodatabase-class.md#getquerydefinfo) función de miembro de clase `CDaoDatabase`.  
  
 La información recuperada por la [CDaoDatabase::GetQueryDefInfo](../../mfc/reference/cdaodatabase-class.md#getquerydefinfo) función miembro se almacena en un `CDaoQueryDefInfo` estructura. Llame a `GetQueryDefInfo` para el objeto de base de datos en cuya colección de definiciones de consulta se almacena el objeto de definición de consulta. `CDaoQueryDefInfo`También define un `Dump` compila la función miembro en versiones de depuración. Puede usar `Dump` para volcar el contenido de un `CDaoQueryDefInfo` objeto. Clase `CDaoDatabase` también proporciona funciones miembro para obtener acceso directamente a todas las propiedades que se devuelven en un `CDaoQueryDefInfo` objeto, por lo que probablemente rara vez deberá llamar a `GetQueryDefInfo`.  
  
 Al anexar un nuevo campo u objeto de parámetro a la colección de campos o parámetros de un objeto de definición de consulta, se produce una excepción si la base de datos subyacente no admite el tipo de datos especificado para el nuevo objeto.  
  
 La configuración de fecha y hora se deriva del equipo en el que se creó o actualizó por última vez la definición de consulta. En un entorno multiusuario, los usuarios deben obtener estos valores directamente desde el servidor de archivos con la **net tiempo** comando para evitar las discrepancias en los valores de propiedad DateCreated y LastUpdated.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdao.h  
  
## <a name="see-also"></a>Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDaoQueryDef (clase)](../../mfc/reference/cdaoquerydef-class.md)   
 [CDaoDatabase (clase)](../../mfc/reference/cdaodatabase-class.md)
