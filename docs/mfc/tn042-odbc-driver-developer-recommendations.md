---
title: "TN042: Recomendaciones para desarrolladores de controladores ODBC | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.odbc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "bases de datos [C++], ODBC"
  - "controladores ODBC [C++], escribir"
  - "TN042"
ms.assetid: ecc6b5d9-f480-4582-9e22-8309fe561dad
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# TN042: Recomendaciones para desarrolladores de controladores ODBC
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  La nota técnica siguiente no se ha actualizado desde que se incluyó por primera vez en la documentación en línea.  Como resultado, algunos procedimientos y temas podrían estar obsoletos o ser incorrectos.  Para obtener información más reciente, se recomienda buscar el tema de interés en el índice de la documentación en línea.  
  
 Esta nota describe las instrucciones para los programadores de controladores ODBC.  Describe requisitos generales y supuestos de la funcionalidad de ODBC que las clases de base de datos MFC crean, y los distintos detalles semánticos esperados.  La funcionalidad necesaria del controlador para admitir los tres modos abierto de `CRecordset` \(**forwardOnly**, **instantánea** y **dynaset**\) se describe.  
  
## La biblioteca de cursores ODBC  
 Las clases de base de datos MFC muestran funcionalidad al usuario que en muchos casos supera la funcionalidad proporcionada por la mayoría de los controladores ODBC de nivel 1.  Afortunadamente, la biblioteca de cursores ODBC se acodará entre las clases de base de datos y el controlador y, proporcionará automáticamente gran parte de esta funcionalidad adicional.  
  
 Por ejemplo, la mayoría 1,0 controladores no admiten el desplazamiento hacia atrás.  La biblioteca de cursores puede detectar esto, y almacene en memoria caché filas de controlador y las mostrará como se solicitan en llamadas de FETCH\_PREV en **SQLExtendedFetch**.  
  
 Otro ejemplo importante de la dependencia de la biblioteca de cursores es actualizaciones con ubicación.  La mayoría 1,0 controladores tampoco tienen actualizaciones con ubicación, pero la biblioteca de cursores generará instrucciones de actualización que identifican una fila de destino en el origen de datos basado en los valores de datos en caché actuales, o una marca de tiempo almacenada en caché.  
  
 La biblioteca de clases nunca utiliza los conjuntos de filas.  Por consiguiente, las pocas instrucciones de **SQLSetPos** siempre se aplican a la fila 1 de conjunto de filas.  
  
## CDatabases  
 Cada `CDatabase` asigna único **HDBC**. \(Si se utiliza la función de `CDatabase``ExecuteSQL` , **HSTMT** se asigna temporalmente.\) Tan si se requiere entity\_CODECDatabase múltiple, s múltiple de **HDBC**por **HENV** debe admitirse.  
  
 Las clases de base de datos requieren la biblioteca de cursores.  Esto se refleja en una llamada **SQL\_ODBC\_CURSORS**, **SQL\_CUR\_USE\_ODBC**de **SQLSetConnections** .  
  
 **SQLDriverConnect**, **SQL\_DRIVER\_COMPLETE** es utilizado por `CDatabase::Open` para establecer la conexión al origen de datos.  
  
 El controlador debe admitir **SQLGetInfo SQL\_ODBC\_API\_CONFORMANCE** \>\= **SQL\_OAC\_LEVEL1**, **SQLGetInfo SQL\_ODBC\_SQL\_CONFORMANCE** \>\= **SQL\_OSC\_MINIMUM**.  
  
 Para que las transacciones admitidas para `CDatabase` y los conjuntos de registros dependientes, **SQLGetInfo SQL\_CURSOR\_COMMIT\_BEHAVIOR** y **SQL\_CURSOR\_ROLLBACK\_BEHAVIOR** deben tener **SQL\_CR\_PRESERVE**.  Si no, los intentos de realizar el control de la transacción se omitirán.  
  
 **SQLGetInfo SQL\_DATA\_SOURCE\_READ\_ONLY** debe admitir.  Si devuelve “y”, no se realizará ninguna operación de actualización en el origen de datos.  
  
 Si `CDatabase` es de sólo lectura abierta, un intento de establecer readonly del origen de datos se creará con **SQLSetConnectOption SQL\_ACCESS\_MODE**, **SQL\_MODE\_READ\_ONLY**.  
  
 Si los identificadores requieren entrecomillado, esta información se debe devolver el controlador con una llamada de **SQLGetInfoSQL\_IDENTIFIER\_QUOTE\_CHAR** .  
  
 A efectos de depuración, **SQLGetInfo SQL\_DBMS\_VER** y **SQL\_DBMS\_NAME** se recuperan del controlador.  
  
 **SQLSetStmtOption SQL\_QUERY\_TIMEOUT** y **SQL\_ASYNC\_ENABLE** se puede llamar `CDatabase`**HDBC**.  
  
 **SQLError** se puede llamar con o todos los argumentos NULL.  
  
 Por supuesto, **SQLAllocEnv**, **SQLAllocConnect**, **SQLDisconnect** y **SQLFreeConnect** deben ser compatibles.  
  
## ExecuteSQL  
 Además de asignar y de liberar **HSTMT**temporal, `ExecuteSQL` llama **SQLExecDirect**, **SQLFetch**, **SQLNumResultCol** y `SQLMoreResults`.  **SQLCancel** se puede llamar en **HSTMT**.  
  
## GetDatabaseName  
 **SQLGetInfo SQL\_DATABASE\_NAME** se denominará.  
  
## BeginTrans, CommitTrans, recuperación  
 **SQLSetConnectOption SQL\_AUTOCOMMIT** y **SQLTransact SQL\_COMMIT**, **SQL\_ROLLBACK** y **SQL\_AUTOCOMMIT** se llamará si se realizan las solicitudes de la transacción.  
  
## CRecordsets  
 **SQLAllocStmt**, **SQLPrepare**, **SQLExecute** \(For **Abierta** y **Requery**\), **SQLExecDirect** \(para las operaciones de actualización\), **SQLFreeStmt** debe admitir.  **SQLNumResultCols** y **SQLDescribeCol** se llama los resultados en distintas ocasiones.  
  
 **SQLSetParam** se usa mayoritariamente en los datos de parámetro y la funcionalidad de enlace de **DATA\_AT\_EXEC** .  
  
 **SQLBindCol** se usa mayoritariamente para registrar ubicaciones de almacenamiento de datos de columna de salida con ODBC.  
  
 Dos llamadas de **SQLGetData** se utilizan para recuperar los datos de **SQL\_LONG\_VARCHAR** y de **SQL\_LONG\_VARBINARY** .  Los intentos de primera llamada buscar la longitud total del valor de la columna llamando a **SQLGetData** con el cbMaxValue de 0, pero con un pcbValue válido.  Si el pcbValue contiene **SQL\_NO\_TOTAL**, se produce una excepción.  Si no, se asigna `HGLOBAL` , y otra llamada a **SQLGetData** se hace para recuperar el resultado completo.  
  
## Updating  
 Si se solicita el bloqueo pesimista, **SQLGetInfo SQL\_LOCK\_TYPES** se consulta.  Si **SQL\_LCK\_EXCLUSIVE** no se admite, se producirá una excepción.  
  
 Los intentos de actualizar `CRecordset` \(**instantánea** o **dynaset**\) producirán un segundo **HSTMT** que se asignará.  Para los controladores que no admiten segundo **HSTMT**, la biblioteca de cursores simulará esta funcionalidad.  Desgraciadamente, esto puede significar a veces forzar la consulta actual en primer **HSTMT** completamente antes de procesar la segunda solicitud de **HSTMT** .  
  
 **SQLFreeStmt SQL\_CLOSE** y **SQL\_RESET\_PARAMS** y **SQLGetCursorName** se llamará durante las operaciones de actualización.  
  
 Si hay **CLongBinarys** en **outputColumns**, la funcionalidad de **DATA\_AT\_EXEC** de ODBC debe ser compatible.  Esto incluye devolver **SQL\_NEED\_DATA** de **SQLExecDirect**, de **SQLParamData** y de **SQLPutData**.  
  
 **SQLRowCount** se denomina después de ejecutar para comprobar que solo 1 registro se actualizó por **SQLExecDirect**.  
  
## Cursores de ForwardOnly  
 Sólo **SQLFetch** se requiere para las operaciones de **Mover** .  Observe que los cursores de **forwardOnly** no admiten actualizaciones.  
  
## Cursores de instantánea  
 La funcionalidad de instantánea requiere compatibilidad con **SQLExtendedFetch** .  Como se indicó anteriormente, la biblioteca de cursores ODBC detectará cuando un controlador no admite **SQLExtendedFetch**, y proporciona la compatibilidad necesaria propio.  
  
 **SQLGetInfo**, **SQL\_SCROLL\_OPTIONS** debe admitir **SQL\_SO\_STATIC**.  
  
## Cursores de Dinámico  
 A continuación se muestra la compatibilidad mínimo necesario para abrir un conjunto:  
  
 **SQLGetInfo**, **SQL\_ODBC\_VER** debe devolver \> “01 ".  
  
 **SQLGetInfo**, **SQL\_SCROLL\_OPTIONS** debe admitir **SQL\_SO\_KEYSET\_DRIVEN**.  
  
 **SQLGetInfo**, **SQL\_ROW\_UPDATES** debe devolver “y”.  
  
 **SQLGetInfo**, **SQL\_POSITIONED\_UPDATES** debe admitir **SQL\_PS\_POSITIONED\_DELETE** y **SQL\_PS\_POSITIONED\_UPDATE**.  
  
 Además, si se solicita el bloqueo pesimista, una llamada a **SQLSetPos** con el irow 1, el fRefresh FALSE y la multitud **SQL\_LCK\_EXCLUSIVE** se lleve.  
  
## Vea también  
 [Notas técnicas por número](../mfc/technical-notes-by-number.md)   
 [Notas técnicas por categoría](../mfc/technical-notes-by-category.md)