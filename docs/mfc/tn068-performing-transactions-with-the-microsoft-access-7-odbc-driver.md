---
title: 'TN068: Realizar transacciones con el controlador ODBC de Microsoft Access 7'
ms.date: 06/28/2018
f1_keywords:
- vc.data.odbc
helpviewer_keywords:
- TN068 [MFC]
- transactions [MFC], calling BeginTrans
- transactions [MFC], Microsoft Access
ms.assetid: d3f8f5d9-b118-4194-be36-a1aefb630c45
ms.openlocfilehash: 3121587f85c4ea19cc92e39569008b597d24ea58
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62363796"
---
# <a name="tn068-performing-transactions-with-the-microsoft-access-7-odbc-driver"></a>TN068: Realizar transacciones con el controlador ODBC de Microsoft Access 7

> [!NOTE]
> La nota técnica siguiente no se ha actualizado desde que se incluyó por primera vez en la documentación en línea. Como resultado, algunos procedimientos y temas podrían estar obsoletos o ser incorrectos. Para obtener información más reciente, se recomienda buscar el tema de interés en el índice de la documentación en línea.

Esta nota describe cómo realizar las transacciones cuando se usan las clases de base de datos ODBC de MFC y el controlador ODBC de Microsoft Access 7.0 incluidas en la versión de escritorio de Microsoft ODBC Driver Pack 3.0.

## <a name="overview"></a>Información general

Si la aplicación de base de datos realiza las transacciones, debe llamar a `CDatabase::BeginTrans` y `CRecordset::Open` en la secuencia correcta en la aplicación. El controlador de Microsoft Access 7.0 utiliza el motor de base de datos Microsoft Jet y Jet requiere que la aplicación no iniciar una transacción en cualquier base de datos con un cursor abierto. Para las clases de base de datos ODBC de MFC, un cursor abierto equivale a una apertura `CRecordset` objeto.

Si abre un conjunto de registros antes de llamar a `BeginTrans`, no puede ver los mensajes de error. Sin embargo, cualquier conjunto de registros actualiza su aplicación tiene que convertirse en permanente después de llamar a `CRecordset::Update`, y las actualizaciones no se revertirán mediante una llamada a `Rollback`. Para evitar este problema, debe llamar a `BeginTrans` primero y, a continuación, abra el conjunto de registros.

MFC comprueba la funcionalidad del controlador para el comportamiento del cursor commit y rollback. Clase `CDatabase` proporciona dos funciones miembro, `GetCursorCommitBehavior` y `GetCursorRollbackBehavior`, para determinar el efecto de cualquier transacción en el abierto `CRecordset` objeto. Para el controlador ODBC de Microsoft Access 7.0, estas funciones miembro devuelven `SQL_CB_CLOSE` porque el controlador de Access no admite la conservación del cursor. Por lo tanto, debe llamar a `CRecordset::Requery` siguiente un `CommitTrans` o `Rollback` operación.

Cuando deba realizar varias transacciones uno tras otro, no puede llamar a `Requery` después de la primera transacción y después iniciar siguiente. Debe cerrar el conjunto de registros antes de la siguiente llamada a `BeginTrans` con el fin de satisfacer el requisito de Jet. Esta nota técnica describe dos métodos para controlar esta situación:

- Cierre el conjunto de registros después de cada `CommitTrans` o `Rollback` operación.

- Mediante la función de la API de ODBC `SQLFreeStmt`.

## <a name="closing-the-recordset-after-each-committrans-or-rollback-operation"></a>Cierre el conjunto de registros después de cada operación de reversión o CommitTrans

Antes de iniciar una transacción, asegúrese de que el objeto de conjunto de registros está cerrado. Después de llamar a `BeginTrans`, llame a la función miembro `Open` función miembro. Cierre el conjunto de registros inmediatamente después de llamar a `CommitTrans` o `Rollback`. Tenga en cuenta que varias veces de apertura y cierre el conjunto de registros pueden ralentizar el rendimiento de la aplicación.

## <a name="using-sqlfreestmt"></a>Using SQLFreeStmt

También puede usar la función de la API de ODBC `SQLFreeStmt` cerrar explícitamente el cursor después de finalizar una transacción. Para iniciar otra transacción, llame a `BeginTrans` seguido `CRecordset::Requery`. Al llamar a `SQLFreeStmt`, debe especificar HSTMT del conjunto de registros como primer parámetro y *SQL_CLOSE* como segundo parámetro. Este método es más rápido que el conjunto de registros al principio de cada transacción de apertura y cierre. El código siguiente muestra cómo implementar esta técnica:

```cpp
CMyDatabase db;
db.Open("MYDATASOURCE");
CMyRecordset rs(&db);

// start transaction 1 and
// open the recordset
db.BeginTrans();
rs.Open();

// manipulate data

// end transaction 1
db.CommitTrans(); // or Rollback()

// close the cursor
::SQLFreeStmt(rs.m_hstmt, SQL_CLOSE);

// start transaction 2
db.BeginTrans();
// now get the result set
rs.Requery();

// manipulate data

// end transaction 2
db.CommitTrans();

rs.Close();
db.Close();
```

Otra manera de implementar esta técnica es escribir una nueva función, `RequeryWithBeginTrans`, que puede llamar para iniciar la siguiente transacción después de confirmar o revertir la primera de ellas. Para escribir una función de ese tipo, realice los pasos siguientes:

1. Copie el código para `CRecordset::Requery( )` a la nueva función.

2. Agregue la siguiente línea inmediatamente después de llamar a `SQLFreeStmt`:

   `m_pDatabase->BeginTrans( );`

Ahora puede llamar a esta función entre cada par de transacciones:

```cpp
// start transaction 1 and
// open the recordset
db.BeginTrans();

rs.Open();

// manipulate data

// end transaction 1
db.CommitTrans();   // or Rollback()

// close the cursor, start new transaction,
// and get the result set
rs.RequeryWithBeginTrans();

// manipulate data

// end transaction 2
db.CommitTrans();   // or Rollback()
```

> [!NOTE]
> No use esta técnica si tiene que cambiar las variables de miembro del conjunto de registros *m_strFilter* o *m_strSort* entre las transacciones. En ese caso, debe cerrar el conjunto de registros después de cada `CommitTrans` o `Rollback` operación.

## <a name="see-also"></a>Vea también

[Notas técnicas por número](../mfc/technical-notes-by-number.md)<br/>
[Notas técnicas por categoría](../mfc/technical-notes-by-category.md)
