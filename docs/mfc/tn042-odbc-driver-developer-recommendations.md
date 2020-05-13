---
title: 'TN042: Recomendaciones para desarrolladores de controladores ODBC'
ms.date: 11/04/2016
f1_keywords:
- vc.odbc
helpviewer_keywords:
- ODBC drivers [MFC], writing
- databases [MFC], ODBC
- TN042
ms.assetid: ecc6b5d9-f480-4582-9e22-8309fe561dad
ms.openlocfilehash: 67f7a86a247b60be66dabb0a89f04d39ce76222b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372131"
---
# <a name="tn042-odbc-driver-developer-recommendations"></a>TN042: Recomendaciones para desarrolladores de controladores ODBC

> [!NOTE]
> La nota técnica siguiente no se ha actualizado desde que se incluyó por primera vez en la documentación en línea. Como resultado, algunos procedimientos y temas podrían estar obsoletos o ser incorrectos. Para obtener información más reciente, se recomienda buscar el tema de interés en el índice de la documentación en línea.

En esta nota se describen las directrices para los escritores de controladores ODBC. Describe los requisitos generales y las suposiciones de la funcionalidad ODBC que realizan las clases de base de datos MFC y varios detalles semánticos esperados. Se describe la funcionalidad `CRecordset` de controlador necesaria para admitir los tres modos Open **(forwardOnly**, **snapshot** y **dynaset).**

## <a name="odbcs-cursor-library"></a>Biblioteca de cursores de ODBC

Las clases de base de datos MFC presentan funcionalidad para el usuario que en muchos casos supera la funcionalidad proporcionada por la mayoría de los controladores ODBC de nivel 1. Afortunadamente, la biblioteca de cursores de ODBC se superpondrá a sí misma entre las clases de base de datos y el controlador, y proporcionará automáticamente gran parte de esta funcionalidad adicional.

Por ejemplo, la mayoría de los controladores 1.0 no admiten el desplazamiento hacia atrás. La biblioteca de cursores puede detectar esto y almacenaren en caché `SQLExtendedFetch`las filas del controlador y las presentarán según lo solicitado en FETCH_PREV llamadas en .

Otro ejemplo importante de dependencia de la biblioteca de cursores son las actualizaciones posicionadas. La mayoría de los controladores 1.0 tampoco tienen actualizaciones posicionadas, pero la biblioteca de cursores generará instrucciones de actualización que identifican una fila de destino en el origen de datos en función de sus valores de datos almacenados en caché actuales o un valor de marca de tiempo almacenado en caché.

La biblioteca de clases nunca hace uso de varios conjuntos de filas. Por lo `SQLSetPos` tanto, las pocas instrucciones siempre se aplican a la fila 1 del conjunto de filas.

## <a name="cdatabases"></a>CBases de datos

Cada `CDatabase` uno asigna un único **HDBC**. (Si `CDatabase`se `ExecuteSQL` utiliza la función 's, se asigna temporalmente un **HSTMT.)** Por lo `CDatabase`tanto, si se requieren varios 's, se deben admitir varios **HDBC**s por **HENV.**

Las clases de base de datos requieren la biblioteca de cursores. Esto se refleja `SQLSetConnections` en una llamada **SQL_ODBC_CURSORS**, **SQL_CUR_USE_ODBC**.

`SQLDriverConnect`, **SQL_DRIVER_COMPLETE** se `CDatabase::Open` utiliza para establecer la conexión con el origen de datos.

El controlador `SQLGetInfo SQL_ODBC_API_CONFORMANCE`  >= debe `SQLGetInfo SQL_ODBC_SQL_CONFORMANCE`  >= admitir **SQL_OAC_LEVEL1**, **SQL_OSC_MINIMUM**.

Para que las transacciones se `CDatabase` admitan para `SQLGetInfo SQL_CURSOR_COMMIT_BEHAVIOR` los conjuntos de registros dependientes y sus, y **SQL_CURSOR_ROLLBACK_BEHAVIOR** deben tener **SQL_CR_PRESERVE**. De lo contrario, se omitirán los intentos de realizar el control de transacciones.

`SQLGetInfo SQL_DATA_SOURCE_READ_ONLY`debe ser apoyado. Si devuelve "Y", no se realizará ninguna operación de actualización en el origen de datos.

Si `CDatabase` se abre ReadOnly, se realizará un intento de `SQLSetConnectOption SQL_ACCESS_MODE`establecer el origen de datos de solo lectura con , **SQL_MODE_READ_ONLY**.

Si los identificadores requieren comillas, esta información debe `SQLGetInfo SQL_IDENTIFIER_QUOTE_CHAR` devolverse desde el controlador con una llamada.

Para fines de `SQLGetInfo SQL_DBMS_VER` depuración, y **SQL_DBMS_NAME** se recuperan del controlador.

`SQLSetStmtOption SQL_QUERY_TIMEOUT`y **SQL_ASYNC_ENABLE** se puede `CDatabase`llamar en un **'s HDBC**.

`SQLError`puede llamarse con cualquiera o todos los argumentos NULL.

Por `SQLAllocEnv`supuesto, `SQLAllocConnect` `SQLDisconnect` , `SQLFreeConnect` , y debe ser compatible.

## <a name="executesql"></a>ExecuteSQL

Además de asignar y liberar un **HSTMT** `ExecuteSQL` temporal, llamadas `SQLExecDirect` `SQLFetch`, , `SQLNumResultCol` y `SQLMoreResults`. `SQLCancel`pueden llamarse al **HSTMT**.

## <a name="getdatabasename"></a>GetDatabaseName

`SQLGetInfo SQL_DATABASE_NAME`se llamará.

## <a name="begintrans-committrans-rollback"></a>BeginTrans, CommitTrans, Rollback

`SQLSetConnectOption SQL_AUTOCOMMIT`y `SQLTransact SQL_COMMIT`, se llamará **SQL_ROLLBACK** y **SQL_AUTOCOMMIT** si se realizan solicitudes de transacción.

## <a name="crecordsets"></a>CRecordsets

`SQLAllocStmt`, `SQLPrepare` `SQLExecute` , `Open` (For y `Requery`), `SQLExecDirect` `SQLFreeStmt` (para operaciones de actualización), debe ser compatible. `SQLNumResultCols`y `SQLDescribeCol` se le llamará a los resultados establecidos en varios momentos.

`SQLSetParam`se utiliza ampliamente para enlazar datos de parámetros y **DATA_AT_EXEC** funcionalidad.

`SQLBindCol`se utiliza ampliamente para registrar ubicaciones de almacenamiento de datos de columna de salida con ODBC.

Se `SQLGetData` utilizan dos llamadas para recuperar **datos SQL_LONG_VARCHAR** y **SQL_LONG_VARBINARY.** La primera llamada intenta encontrar la longitud total `SQLGetData` del valor de columna llamando a cbMaxValue de 0, pero con un pcbValue válido. Si pcbValue contiene **SQL_NO_TOTAL**, se produce una excepción. De lo contrario, se asigna `SQLGetData` un **HGLOBAL** y se realiza otra llamada para recuperar el resultado completo.

## <a name="updating"></a>Actualizando

Si se solicita un bloqueo `SQLGetInfo SQL_LOCK_TYPES` pesimista, se consultará. Si no se admite **SQL_LCK_EXCLUSIVE,** se producirá una excepción.

Los intentos `CRecordset` de actualizar un (**snapshot** o **dynaset**) harán que se asigne un segundo **HSTMT.** Para los controladores que no admiten el segundo **HSTMT**, la biblioteca de cursores simulará esta funcionalidad. Desafortunadamente, esto a veces puede significar forzar la consulta actual en el primer **HSTMT** a completarse antes de procesar la segunda solicitud de **HSTMT.**

`SQLFreeStmt SQL_CLOSE`y **SQL_RESET_PARAMS** SQL_RESET_PARAMS `SQLGetCursorName` y se llamará durante las operaciones de actualización.

Si hay **CLongBinarys** en **outputColumns**, se debe admitir la funcionalidad **de DATA_AT_EXEC** de ODBC. Esto incluye **SQL_NEED_DATA** devolver `SQLExecDirect`SQL_NEED_DATA `SQLParamData` `SQLPutData`de , y .

`SQLRowCount`se llama después de ejecutar para comprobar `SQLExecDirect`que solo el archivo .

## <a name="forwardonly-cursors"></a>Cursores ForwardOnly

Solo `SQLFetch` es necesario `Move` para las operaciones. Tenga en cuenta que los cursores **forwardOnly** no admiten actualizaciones.

## <a name="snapshot-cursors"></a>Cursores de instantáneas

La funcionalidad de `SQLExtendedFetch` instantáneas requiere compatibilidad. Como se indicó anteriormente, la biblioteca de `SQLExtendedFetch`cursores ODBC detectará cuando un controlador no admite y proporcionará la compatibilidad necesaria en sí.

`SQLGetInfo`, **SQL_SCROLL_OPTIONS** debe admitir **SQL_SO_STATIC**.

## <a name="dynaset-cursors"></a>Cursores Dynaset

A continuación se muestra el soporte mínimo necesario para abrir un conjunto de registros dinámicos:

`SQLGetInfo`, **SQL_ODBC_VER** debe devolver > "01".

`SQLGetInfo`, **SQL_SCROLL_OPTIONS** debe admitir **SQL_SO_KEYSET_DRIVEN**.

`SQLGetInfo`, **SQL_ROW_UPDATES** debe devolver "Y".

`SQLGetInfo`, **SQL_POSITIONED_UPDATES** debe admitir **SQL_PS_POSITIONED_DELETE** y **SQL_PS_POSITIONED_UPDATE**.

Además, si se solicita un bloqueo `SQLSetPos` pesimista, se realizará una llamada a irow 1, fRefresh FALSE y fLock **SQL_LCK_EXCLUSIVE.**

## <a name="see-also"></a>Consulte también

[Notas técnicas por número](../mfc/technical-notes-by-number.md)<br/>
[Notas técnicas por categoría](../mfc/technical-notes-by-category.md)
