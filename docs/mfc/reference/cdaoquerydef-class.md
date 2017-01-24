---
title: "CDaoQueryDef Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CDaoQueryDef"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDaoQueryDef class"
  - "consultas [Visual Studio], definir"
  - "QueryDef objects"
ms.assetid: 9676a4a3-c712-44d4-8c5d-d1cc78288d3a
caps.latest.revision: 24
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDaoQueryDef Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Representa una definición de consulta, o “tabla,” normalmente guarda una en una base de datos.  
  
## Sintaxis  
  
```  
class CDaoQueryDef : public CObject  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDaoQueryDef::CDaoQueryDef](../Topic/CDaoQueryDef::CDaoQueryDef.md)|construye un objeto de **CDaoQueryDef** .  La siguiente llamada **Abrir** o **Crear**, según las necesidades.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDaoQueryDef::Append](../Topic/CDaoQueryDef::Append.md)|Anexa la tabla a la colección de QueryDefs de base de datos como una consulta guardada.|  
|[CDaoQueryDef::CanUpdate](../Topic/CDaoQueryDef::CanUpdate.md)|Devuelve cero si la consulta puede actualizar la base de datos.|  
|[CDaoQueryDef::Close](../Topic/CDaoQueryDef::Close.md)|Cierre el objeto de tabla.  Destruya el objeto C\+\+ cuando acaba con él.|  
|[CDaoQueryDef::Create](../Topic/CDaoQueryDef::Create.md)|Crea el objeto subyacente de tabla de DAO.  Utilice la tabla como una consulta temporal, o llamada **Anexar** guardarla en la base de datos.|  
|[CDaoQueryDef::Execute](../Topic/CDaoQueryDef::Execute.md)|Ejecuta la consulta definido por el objeto de tabla.|  
|[CDaoQueryDef::GetConnect](../Topic/CDaoQueryDef::GetConnect.md)|Devuelve la cadena de conexión asociado a la tabla.  la cadena de conexión identifica el origen de datos.  \(Para las consultas de paso a través de SQL sólo; si no una cadena vacía\).|  
|[CDaoQueryDef::GetDateCreated](../Topic/CDaoQueryDef::GetDateCreated.md)|Devuelve la fecha que la consulta guardada se creó.|  
|[CDaoQueryDef::GetDateLastUpdated](../Topic/CDaoQueryDef::GetDateLastUpdated.md)|Devuelve la fecha que la consulta guardada se actualizó por última vez.|  
|[CDaoQueryDef::GetFieldCount](../Topic/CDaoQueryDef::GetFieldCount.md)|Devuelve el número de campos definidos por la tabla.|  
|[CDaoQueryDef::GetFieldInfo](../Topic/CDaoQueryDef::GetFieldInfo.md)|Devuelve información sobre un campo específico definido en la consulta.|  
|[CDaoQueryDef::GetName](../Topic/CDaoQueryDef::GetName.md)|Devuelve el nombre de tabla.|  
|[CDaoQueryDef::GetODBCTimeout](../Topic/CDaoQueryDef::GetODBCTimeout.md)|Devuelve el valor de tiempo de espera utilizado por ODBC \(para una consulta de ODBC\) cuando se ejecuta el tabla.  Esto determina cuánto tiempo permitir a la acción de la consulta completa.|  
|[CDaoQueryDef::GetParameterCount](../Topic/CDaoQueryDef::GetParameterCount.md)|devuelve el número de parámetros definido para la consulta.|  
|[CDaoQueryDef::GetParameterInfo](../Topic/CDaoQueryDef::GetParameterInfo.md)|Devuelve información sobre un parámetro especificado a la consulta.|  
|[CDaoQueryDef::GetParamValue](../Topic/CDaoQueryDef::GetParamValue.md)|devuelve el valor de un parámetro especificado a la consulta.|  
|[CDaoQueryDef::GetRecordsAffected](../Topic/CDaoQueryDef::GetRecordsAffected.md)|Devuelve el número de registros afectados por una consulta de acciones.|  
|[CDaoQueryDef::GetReturnsRecords](../Topic/CDaoQueryDef::GetReturnsRecords.md)|Devuelve cero si la consulta definido por la tabla devuelve los registros.|  
|[CDaoQueryDef::GetSQL](../Topic/CDaoQueryDef::GetSQL.md)|Devuelve la cadena SQL que especifica la consulta definido por la tabla.|  
|[CDaoQueryDef::GetType](../Topic/CDaoQueryDef::GetType.md)|Devuelve el tipo: cancelación, actualización, anexa, crear\-tabla, etc.|  
|[CDaoQueryDef::IsOpen](../Topic/CDaoQueryDef::IsOpen.md)|Devuelve cero si la tabla está abierto y puede ejecutarse.|  
|[CDaoQueryDef::Open](../Topic/CDaoQueryDef::Open.md)|Abra una tabla existente almacenado en la colección de QueryDefs de base de datos.|  
|[CDaoQueryDef::SetConnect](../Topic/CDaoQueryDef::SetConnect.md)|establece la cadena de conexión para una consulta de paso a través de SQL en un origen de datos ODBC.|  
|[CDaoQueryDef::SetName](../Topic/CDaoQueryDef::SetName.md)|Establece el nombre de la consulta guardada, reemplace el nombre en uso cuando la tabla se creó.|  
|[CDaoQueryDef::SetODBCTimeout](../Topic/CDaoQueryDef::SetODBCTimeout.md)|Establece el valor de tiempo de espera utilizado por ODBC \(para una consulta de ODBC\) cuando se ejecuta el tabla.|  
|[CDaoQueryDef::SetParamValue](../Topic/CDaoQueryDef::SetParamValue.md)|establece el valor de un parámetro especificado a la consulta.|  
|[CDaoQueryDef::SetReturnsRecords](../Topic/CDaoQueryDef::SetReturnsRecords.md)|Especifica si la tabla devuelve los registros.  Establecer este atributo a **TRUE** sólo es válido para las consultas de paso a través de SQL.|  
|[CDaoQueryDef::SetSQL](../Topic/CDaoQueryDef::SetSQL.md)|Establece la cadena de SQL que especifica la consulta definido por la tabla.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDaoQueryDef::m\_pDAOQueryDef](../Topic/CDaoQueryDef::m_pDAOQueryDef.md)|Un puntero a la interfaz OLE para el objeto subyacente de tabla de DAO.|  
|[CDaoQueryDef::m\_pDatabase](../Topic/CDaoQueryDef::m_pDatabase.md)|Un puntero al objeto de `CDaoDatabase` con el que la tabla es asociado.  La tabla se puede guardar en la base de datos o no.|  
  
## Comentarios  
 Un tabla es un objeto de acceso a datos que contiene la instrucción SQL que describe una consulta, y sus propiedades, como “fecha de creación” y “tiempo de espera de ODBC”. También puede crear objetos temporales de tabla sin guardarlos, pero es conveniente — y mucho más eficaz — guardar consultas normalmente reusadas en una base de datos.  Un objeto de [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) mantiene una colección, denominada la colección de QueryDefs, que contiene los querydefs guardados.  
  
> [!NOTE]
>  Las clases de base de datos de DAO son distintas de las clases de base de datos MFC basadas en ODBC.  Todos los nombres de clase de base de datos de DAO tienen el prefijo “CDao”.  Todavía puede tener acceso a orígenes de datos ODBC con las clases DAO.  las clases MFC basadas en DAO son generalmente más capaces que las clases MFC basadas en ODBC; las clases DAO pueden tener acceso a los datos, incluidos mediante controladores ODBC, a través de su propio motor de base de datos.  Las operaciones admiten DAO de lenguaje de definición de datos de \(DDL\) las clases también, como tablas de suma mediante las clases, sin tener que llamar a DAO directamente.  
  
## Uso  
 Objetos de tabla de uso para trabajar con una consulta guardada existente o crear una nueva consulta guardada o consulta temporal:  
  
1.  En todos los casos, primero cree un objeto de `CDaoQueryDef` , proporcionando un puntero al objeto de [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) al que la consulta pertenece.  
  
2.  Haga lo siguiente, en función de lo que desea:  
  
    -   Para utilizar un existente guardó consulta, llame a la función miembro de [Abrir](../Topic/CDaoQueryDef::Open.md) del objeto de tabla, proporcionando el nombre de la consulta guardada.  
  
    -   Para crear una nueva consulta guardada, llame a la función miembro de [Crear](../Topic/CDaoQueryDef::Create.md) del objeto de tabla, proporcionando el nombre de la consulta.  Llamar a continuación a [Anexar](../Topic/CDaoQueryDef::Append.md) para guardar la consulta y se anexa a la colección de QueryDefs de base de datos.  **Crear** coloca el tabla en un estado abierto, por lo que después de llamar a **Crear** que no llama **Abrir**.  
  
    -   Para crear una tabla temporal, llame a **Crear**.  pase una cadena vacía para el nombre de la consulta.  No llame a **Anexar**.  
  
 Cuando termine de usar un objeto de tabla, llame a su función miembro de [Cerrar](../Topic/CDaoQueryDef::Close.md) ; a continuación destruya el objeto de tabla.  
  
> [!TIP]
>  La manera más fácil de crear consultas guardadas es crearlas y almacenar en la base de datos mediante Microsoft Access.  Puede abrir y utilizarlos en el código de MFC.  
  
## propósitos  
 Puede utilizar un objeto de tabla para realizar cualquiera de propósitos:  
  
-   para crear un objeto de `CDaoRecordset`  
  
-   Para llamar a la función miembro de **Ejecutar** de objeto para ejecutar directamente una consulta de acciones o una consulta de paso a través de SQL  
  
 Puede utilizar un objeto de tabla para cualquier tipo de consulta, incluidos seleccione, acciones, referencia cruzada, eliminar, actualizar, anexarlo, crear\-tabla, definición de datos, paso a través de SQL, join, y consultas masivas.  El contenido de la instrucción SQL determina el tipo de consulta especificados.  Para obtener información sobre los tipos de consulta, vea **Ejecutar** y el miembro de [GetType](../Topic/CDaoQueryDef::GetType.md) funciona.  Los conjuntos de registros se utilizan para las consultas que ha modificado la fila cambian, normalmente las utilizando **SELECT… Palabras clave FROM**.  **Ejecutar** es el más utilizadas para las operaciones masivas.  Para obtener más información, vea [Ejecutar](../Topic/CDaoQueryDef::Execute.md) y [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md).  
  
## Querydefs y conjuntos de registros  
 Para utilizar un objeto de tabla para crear un objeto de `CDaoRecordset` , crea o abre normalmente un tabla anteriormente descrita.  Después crear un objeto de conjunto de registros, pasar un puntero al objeto de tabla cuando se llama a [CDaoRecordset:: Abrir](../Topic/CDaoRecordset::Open.md).  La tabla que pasa debe estar en un estado abierto.  Para obtener más información, vea la clase [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md).  
  
 No puede usar una tabla para crear un conjunto de registros \(el uso más común para un tabla\) a menos que esté en un estado abierto.  Coloque el tabla en un estado abierto llamando a **Abrir** o **Crear**.  
  
## bases de datos externas  
 Los objetos de Tabla son la manera preferida de utilizar el dialecto SQL nativo de un motor de base de datos externo.  Por ejemplo, puede crear una consulta SQL de Transact \(como se utiliza en Microsoft SQL Server\) y almacenarla en un objeto de tabla.  Cuando necesite utilizar una consulta SQL no basada en el motor de base de datos Microsoft Jet, debe proporcionar una cadena de conexión que apunte al origen de datos externo.  Las consultas con las cadenas de conexión válidas omiten el motor de base de datos y pasar la consulta directamente en el servidor de bases de datos externo para procesar.  
  
> [!TIP]
>  La mejor forma de trabajar con tablas de ODBC es adjuntarlas a una base de datos de Microsoft Jet \(.MDB\).  
  
 Para obtener información relacionada, vea los temas “objeto de Tabla”, “colección de QueryDefs”, y “objeto de CdbDatabase” en el SDK de DAO.  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CDaoQueryDef`  
  
## Requisitos  
 **encabezado:** afxdao.h  
  
## Vea también  
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CDaoRecordset Class](../../mfc/reference/cdaorecordset-class.md)   
 [CDaoDatabase Class](../../mfc/reference/cdaodatabase-class.md)   
 [CDaoTableDef Class](../../mfc/reference/cdaotabledef-class.md)   
 [CDaoException Class](../../mfc/reference/cdaoexception-class.md)