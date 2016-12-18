---
title: "CDaoQueryDefInfo (Estructura) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CDaoQueryDefInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDaoQueryDefInfo (estructura)"
  - "DAO (objetos de acceso a datos), QueryDefs (colección)"
ms.assetid: e20837dc-e78d-4171-a195-1b4075fb5d2a
caps.latest.revision: 13
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDaoQueryDefInfo (Estructura)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La estructura de `CDaoQueryDefInfo` contiene información sobre un objeto de tabla definido para los objetos \(DAO\) de acceso a datos.  
  
## Sintaxis  
  
```  
  
      struct CDaoQueryDefInfo  
{  
   CString m_strName;               // Primary  
   short m_nType;                   // Primary  
   COleDateTime m_dateCreated;      // Secondary  
   COleDateTime m_dateLastUpdated;  // Secondary  
   BOOL m_bUpdatable;               // Secondary  
   BOOL m_bReturnsRecords;          // Secondary  
   CString m_strSQL;                // All  
   CString m_strConnect;            // All  
   short m_nODBCTimeout;            // All  
};  
```  
  
#### Parámetros  
 `m_strName`  
 Nombres de forma única el objeto de tabla.  Para obtener más información, vea el tema “propiedad Name” en la Ayuda de DAO.  Llamada [CDaoQueryDef::GetName](../Topic/CDaoQueryDef::GetName.md) para recuperar esta propiedad directamente.  
  
 `m_nType`  
 Un valor que indica el tipo operativo de un objeto de tabla.  El valor puede ser:  
  
-   **dbQSelect** seleccione \(la consulta selecciona los registros.  
  
-   acción de**dbQAction**\(la consulta se desplaza o los datos de los cambios pero no devuelve los registros.  
  
-   referencia cruzada de**dbQCrosstab**\(la consulta devuelve datos en una hoja de cálculo\- como formato.  
  
-   Suprimir de**dbQDelete**\(la consulta elimina un conjunto de filas especificadas.  
  
-   **dbQUpdate** actualiza — cambia la consulta un conjunto de registros.  
  
-   **dbQAppend** anexa \(la consulta agrega nuevos registros al final de una tabla o consulta.  
  
-   Crear\- tabla de**dbQMakeTable**\(la consulta crea una nueva tabla de un conjunto de registros.  
  
-   definición de datos de**dbQDDL**\(la consulta afecta a la estructura de tablas o de sus elementos.  
  
-   paso a través de**dbQSQLPassThrough**— la instrucción SQL se pasa directamente al servidor de bases de datos, sin el procesamiento intermedio.  
  
-   unión de**dbQSetOperation**\(la consulta crea un objeto de conjunto de registros de instantánea\- tipo que contiene datos de todos los registros especificados en dos o más tablas con los registros duplicados colocados.  Para incluir los duplicados, agregue la palabra clave **TODAS** en la instrucción SQL de la tabla.  
  
-   **dbQSPTBulk** utilizado con **dbQSQLPassThrough** para especificar una consulta que no devuelve los registros.  
  
> [!NOTE]
>  Para crear una consulta de paso a través de SQL, no establece la constante de **dbQSQLPassThrough** .  Esto se establece automáticamente el motor de base de datos Microsoft Jet cuando se crea un objeto de tabla y establezca la propiedad conectarse.  
  
 Para obtener más información, vea el tema “propiedad de tipo” en la Ayuda de DAO.  
  
 `m_dateCreated`  
 Fecha y hora que la tabla se creó.  Para recuperar directamente la fecha que la tabla se creó, llamar a la función miembro de [GetDateCreated](../Topic/CDaoTableDef::GetDateCreated.md) del objeto de `CDaoTableDef` asociado a la tabla.  Vea los comentarios más adelante para obtener más información.  También vea el tema “DateCreated, propiedades de LastUpdated” en la Ayuda de DAO.  
  
 `m_dateLastUpdated`  
 Fecha y hora del cambio realizado más reciente a tabla.  Para recuperar directamente la fecha que la tabla se actualizó, que llama a por última vez la función miembro de [GetDateLastUpdated](../Topic/CDaoQueryDef::GetDateLastUpdated.md) de tabla.  Vea los comentarios más adelante para obtener más información.  Y consulte el tema “DateCreated, propiedades de LastUpdated” en la Ayuda de DAO.  
  
 `m_bUpdatable`  
 Indica si se pueden realizar en un objeto de tabla.  Si esta propiedad es **VERDADERO**, el tabla es actualizable; si no, no.  Actualizable significa que la definición de la consulta del objeto de tabla se puede cambiar.  La propiedad de Actualizable de un objeto de tabla se establece en **VERDADERO** si la definición de la consulta puede actualizarse, aunque el conjunto de registros resultante no es actualizable.  Para recuperar esta propiedad directamente, llame a la función miembro de [CanUpdate](../Topic/CDaoQueryDef::CanUpdate.md) de la tabla.  Para obtener más información, vea el tema “propiedades de Actualizable” en la Ayuda de DAO.  
  
 *m\_bReturnsRecords*  
 Indica si una consulta de paso a través de SQL a una base de datos externa devuelve los registros.  Si esta propiedad es **VERDADERO**, la consulta devuelve los registros.  Para recuperar directamente esta propiedad, llame a [CDaoQueryDef::GetReturnsRecords](../Topic/CDaoQueryDef::GetReturnsRecords.md).  No todas las consultas de paso a través de SQL a los registros externos de retorno de las bases de datos.  Por ejemplo, una instrucción SQL **ACTUALIZACIÓN** actualiza registros sin devolver los registros, como una instrucción SQL **activada** devuelve los registros.  Para obtener más información, vea el tema “propiedades de ReturnsRecords” en la Ayuda de DAO.  
  
 *m\_strSQL*  
 La instrucción SQL que define la consulta ejecutada por un objeto de tabla.  La propiedad SQL contiene la instrucción SQL que determina cómo se selecciona, se agrupan, y se ordenan los registros al ejecutar la consulta.  Puede utilizar la consulta para seleccionar registros para incluir en un objeto de conjunto de registros de dynaset\- o de instantánea\- tipo.  También puede definir consultas masivas para modificar datos sin devolver registros.  Puede recuperar el valor de esta propiedad directamente llamando a la función miembro de [GetSQL](../Topic/CDaoQueryDef::GetSQL.md) de la tabla.  
  
 `m_strConnect`  
 Proporciona información sobre el origen de una base de datos utilizada en una consulta de paso a través.  Esta información toma la forma de una cadena de conexión.  Para obtener más información sobre cadenas se conectan, y para obtener información sobre cómo recuperar el valor de esta propiedad directamente, vea la función miembro de [CDaoDatabase::GetConnect](../Topic/CDaoDatabase::GetConnect.md) trabajar.  
  
 *m\_nODBCTimeout*  
 El número de segundos que el motor de base de datos Microsoft Jet espera antes de que un error de tiempo de espera aparece cuando una consulta se ejecuta en una base de datos ODBC.  Si utiliza una base de datos ODBC, como Microsoft SQL Server, puede haber retrasos debido al tráfico de red o un uso intensivo del servidor de ODBC.  En lugar de espera indefinidamente, puede especificar cuánto tiempo el motor de Microsoft Jet espera antes de que se produzca un error.  El valor de tiempo de espera predeterminado es de 60 segundos.  Puede recuperar el valor de esta propiedad directamente llamando a la función miembro de [GetODBCTimeout](../Topic/CDaoQueryDef::GetODBCTimeout.md) de la tabla.  Para obtener más información, vea el tema “propiedades de ODBCTimeout” en la Ayuda de DAO.  
  
## Comentarios  
 La tabla es un objeto de la clase [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md).  Las referencias a principal, a Secondary, y a Todo anterior indican cómo la información es devuelta por la función miembro de [GetQueryDefInfo](../Topic/CDaoDatabase::GetQueryDefInfo.md) en la clase `CDaoDatabase`.  
  
 La información recuperada por la función miembro de [CDaoDatabase::GetQueryDefInfo](../Topic/CDaoDatabase::GetQueryDefInfo.md) se almacena en una estructura de `CDaoQueryDefInfo` .  Llame a `GetQueryDefInfo` para el objeto de base de datos en cuya colección de QueryDefs se almacena el objeto de tabla.  `CDaoQueryDefInfo` también define una función miembro de `Dump` en versiones de depuración.  Puede utilizar `Dump` para volcar el contenido de un objeto de `CDaoQueryDefInfo` .  El miembro de `CDaoDatabase` de la clase también funciona directamente para tener acceso a todas las propiedades devueltas en un objeto de `CDaoQueryDefInfo` , por lo que deberá probablemente raramente llamar `GetQueryDefInfo`.  
  
 Cuando se agrega un nuevo campo u objeto parameter a la colección de campos o de los parámetros de un objeto de tabla, se produce una excepción si la base de datos subyacente no admite el tipo de datos especificado para el nuevo objeto.  
  
 Los valores de fecha y hora se derivan del equipo en el que la tabla se ha creado o actualizado pasado.  En un entorno multiusuario, los usuarios deben obtener estos valores directamente en el servidor de archivos utilizando el comando de **NET TIME** de evitar discrepancias en los valores de propiedades de DateCreated y de LastUpdated.  
  
## Requisitos  
 **Header:** afxdao.h  
  
## Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDaoQueryDef Class](../../mfc/reference/cdaoquerydef-class.md)   
 [CDaoDatabase Class](../../mfc/reference/cdaodatabase-class.md)