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
ms.openlocfilehash: 462f8229d995add79f48f34b7f81257710b4a8b8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62305416"
---
# <a name="tn042-odbc-driver-developer-recommendations"></a>TN042: Recomendaciones para desarrolladores de controladores ODBC

> [!NOTE]
>  La nota técnica siguiente no se ha actualizado desde que se incluyó por primera vez en la documentación en línea. Como resultado, algunos procedimientos y temas podrían estar obsoletos o ser incorrectos. Para obtener información más reciente, se recomienda buscar el tema de interés en el índice de la documentación en línea.

Esta nota describe las instrucciones para los escritores de controladores ODBC. Describe los requisitos generales y las suposiciones de funcionalidad ODBC que hacen que las clases de base de datos de MFC y diversos detalles semánticos esperados. Requiere la funcionalidad del controlador para admitir los tres `CRecordset` abrir modos (**forwardOnly**, **instantánea** y **dynaset**) se describen.

## <a name="odbcs-cursor-library"></a>Biblioteca de cursores de ODBC

Las clases de base de datos de MFC presentan funcionalidad al usuario que, en muchos casos, supera la funcionalidad proporcionada por la mayoría de los controladores de ODBC de nivel 1. Afortunadamente, la biblioteca de cursores de ODBC se usa entre las clases de base de datos y el controlador y proporcionará automáticamente gran parte de esta funcionalidad adicional.

Por ejemplo, la mayoría de los controladores 1.0 no admiten el desplazamiento hacia atrás. La biblioteca de cursores puede detectar esto y se almacene en caché filas desde el controlador y presentarlos como se solicitó en llamadas FETCH_PREV en `SQLExtendedFetch`.

Otro ejemplo importante de dependencia de biblioteca de cursores es actualizaciones posicionadas. Mayoría de los controladores 1.0 no tiene también actualizaciones por posición, pero la biblioteca de cursores generará las instrucciones update que identifican una fila de destino en el origen de datos en función de sus valores actuales de los datos almacenados en caché o un valor de marca de tiempo en caché.

La biblioteca de clases nunca hace uso de varios conjuntos de filas. Por lo tanto, solo algunos `SQLSetPos` siempre se aplican las instrucciones para la fila 1 del conjunto de filas.

## <a name="cdatabases"></a>CDatabases

Cada `CDatabase` asigna una sola **HDBC**. (Si `CDatabase`del `ExecuteSQL` se utiliza la función, un **HSTMT** se asigna temporalmente.) Por tanto, si varios `CDatabase`del son necesarios, varios **HDBC**s por **HENV** deben ser compatibles.

Las clases de base de datos requieren la biblioteca de cursores. Esto se refleja en una `SQLSetConnections` llamar **SQL_ODBC_CURSORS**, **SQL_CUR_USE_ODBC**.

`SQLDriverConnect`, **SQL_DRIVER_COMPLETE** usa `CDatabase::Open` para establecer la conexión al origen de datos.

El controlador debe admitir `SQLGetInfo SQL_ODBC_API_CONFORMANCE`  >=  **SQL_OAC_LEVEL1**, `SQLGetInfo SQL_ODBC_SQL_CONFORMANCE`  >=  **SQL_OSC_MINIMUM**.

En el orden de las transacciones que se admite para la `CDatabase` y sus conjuntos de registros dependientes, `SQLGetInfo SQL_CURSOR_COMMIT_BEHAVIOR` y **SQL_CURSOR_ROLLBACK_BEHAVIOR** debe tener **SQL_CR_PRESERVE**. En caso contrario, se omitirán los intentos de realizar el control de transacciones.

`SQLGetInfo SQL_DATA_SOURCE_READ_ONLY` debe ser compatible. Si devuelve "S", no se realizará ninguna operación de actualización en el origen de datos.

Si el `CDatabase` se abre de solo lectura, un intento para establecer el origen de datos de lectura solo se realizará con `SQLSetConnectOption SQL_ACCESS_MODE`, **SQL_MODE_READ_ONLY**.

Si los identificadores requieren comillas, esta información debe devolverse desde el controlador con un `SQLGetInfo SQL_IDENTIFIER_QUOTE_CHAR` llamar.

Para la depuración, `SQLGetInfo SQL_DBMS_VER` y **SQL_DBMS_NAME** se recuperan desde el controlador.

`SQLSetStmtOption SQL_QUERY_TIMEOUT` y **SQL_ASYNC_ENABLE** puede llamarse en un `CDatabase`del **HDBC**.

`SQLError` se puede llamar con cualquier o todos los argumentos es NULL.

Por supuesto, `SQLAllocEnv`, `SQLAllocConnect`, `SQLDisconnect` y `SQLFreeConnect` deben ser compatibles.

## <a name="executesql"></a>ExecuteSQL

Además de asignar y liberar un archivo temporal **HSTMT**, `ExecuteSQL` llamadas `SQLExecDirect`, `SQLFetch`, `SQLNumResultCol` y `SQLMoreResults`. `SQLCancel` se pueden llamar en el **HSTMT**.

## <a name="getdatabasename"></a>GetDatabaseName

`SQLGetInfo SQL_DATABASE_NAME` se llamará.

## <a name="begintrans-committrans-rollback"></a>BeginTrans, CommitTrans y Rollback

`SQLSetConnectOption SQL_AUTOCOMMIT` y `SQLTransact SQL_COMMIT`, **SQL_ROLLBACK** y **SQL_AUTOCOMMIT** llamará si se realizan solicitudes de transacción.

## <a name="crecordsets"></a>CRecordsets

`SQLAllocStmt`, `SQLPrepare`, `SQLExecute` (Para `Open` y `Requery`), `SQLExecDirect` (para las operaciones de actualización), `SQLFreeStmt` deben ser compatibles. `SQLNumResultCols` y `SQLDescribeCol` se llamará en los resultados que se establezca en momentos diferentes.

`SQLSetParam` se usa habitualmente para el enlace de datos de parámetro y **DATA_AT_EXEC** funcionalidad.

`SQLBindCol` se usa ampliamente para registrar la salida de las ubicaciones de almacenamiento de datos de columna con ODBC.

Dos `SQLGetData` llamadas se usan para recuperar **SQL_LONG_VARCHAR** y **SQL_LONG_VARBINARY** datos. La primera llamada intenta buscar la longitud total del valor de columna mediante una llamada a `SQLGetData` cbMaxValue 0, pero con un pcbValue válido. Si mantiene pcbValue **SQL_NO_TOTAL**, se produce una excepción. En caso contrario, un **HGLOBAL** está asignado y otro `SQLGetData` llamada realizada al recuperar todo el resultado.

## <a name="updating"></a>Updating

Si se solicita el bloqueo pesimista, `SQLGetInfo SQL_LOCK_TYPES` se va a consultar. Si **SQL_LCK_EXCLUSIVE** no es compatible, se producirá una excepción.

Al intentar actualizar un `CRecordset` (**instantánea** o **dynaset**) hará que un segundo **HSTMT** asignarse. Para los controladores que no admiten la segunda **HSTMT**, la biblioteca de cursores para simular esta funcionalidad. Lamentablemente, esto a veces, quizá forzar el uso de la consulta actual en la primera **HSTMT** hasta su finalización antes de procesar el segundo **HSTMT**lo solicita.

`SQLFreeStmt SQL_CLOSE` y **SQL_RESET_PARAMS** y `SQLGetCursorName` lo llamará durante las operaciones de actualización.

Si no hay **CLongBinarys** en el **outputColumns**, de ODBC **DATA_AT_EXEC** funcionalidad debe ser compatibles. Esto incluye devolver **SQL_NEED_DATA** desde `SQLExecDirect`, `SQLParamData` y `SQLPutData`.

`SQLRowCount` se llama después de ejecutar para comprobar que solo 1 registro se actualizó con la `SQLExecDirect`.

## <a name="forwardonly-cursors"></a>Cursores ForwardOnly

Solo `SQLFetch` es necesaria para la `Move` operaciones. Tenga en cuenta que **forwardOnly** cursores no admiten las actualizaciones.

## <a name="snapshot-cursors"></a>Cursores de instantánea

La funcionalidad de instantánea requiere `SQLExtendedFetch` admite. Como se mencionó anteriormente, la biblioteca de cursores ODBC lo detectará cuando un controlador no es compatible con `SQLExtendedFetch`y proporcionan la compatibilidad necesaria propio.

`SQLGetInfo`, **SQL_SCROLL_OPTIONS** debe admitir **SQL_SO_STATIC**.

## <a name="dynaset-cursors"></a>Cursores de conjunto de registros dinámicos

Esta es la compatibilidad mínima necesaria para abrir un conjunto de registros dinámicos:

`SQLGetInfo`, **SQL_ODBC_VER** debe devolver > "01".

`SQLGetInfo`, **SQL_SCROLL_OPTIONS** debe admitir **SQL_SO_KEYSET_DRIVEN**.

`SQLGetInfo`, **SQL_ROW_UPDATES** debe devolver "S".

`SQLGetInfo`, **SQL_POSITIONED_UPDATES** debe admitir **SQL_PS_POSITIONED_DELETE** y **SQL_PS_POSITIONED_UPDATE**.

Además, si se solicita el bloqueo pesimista, una llamada a `SQLSetPos` con irow 1, fRefresh FALSE y manada **SQL_LCK_EXCLUSIVE** se realizarán.

## <a name="see-also"></a>Vea también

[Notas técnicas por número](../mfc/technical-notes-by-number.md)<br/>
[Notas técnicas por categoría](../mfc/technical-notes-by-category.md)
