---
title: 'TN068: Realizar transacciones con el controlador ODBC de Microsoft Access 7 | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.data.odbc
dev_langs:
- C++
helpviewer_keywords:
- TN068 [MFC]
- transactions [MFC], calling BeginTrans
- transactions [MFC], Microsoft Access
ms.assetid: d3f8f5d9-b118-4194-be36-a1aefb630c45
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 63cce7532d93b1bd44b6a44c526310bd894d5e07
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="tn068-performing-transactions-with-the-microsoft-access-7-odbc-driver"></a>TN068: Realizar transacciones con el controlador ODBC de Microsoft Access 7
> [!NOTE]
>  La nota técnica siguiente no se ha actualizado desde que se incluyó por primera vez en la documentación en línea. Como resultado, algunos procedimientos y temas podrían estar obsoletos o ser incorrectos. Para obtener información más reciente, se recomienda buscar el tema de interés en el índice de la documentación en línea.  
  
 Esta nota describe cómo realizar transacciones cuando se usan las clases de base de datos ODBC de MFC y el controlador ODBC de Microsoft Access 7.0 incluidas en la versión de escritorio de Microsoft ODBC Driver Pack 3.0.  
  
## <a name="overview"></a>Información general  
 Si la aplicación de base de datos realiza las transacciones, que debe tener cuidado llamar a `CDatabase::BeginTrans` y `CRecordset::Open` en la secuencia correcta en la aplicación. El controlador de Microsoft Access 7.0 utiliza el motor de base de datos de Microsoft Jet y Jet requiere que la aplicación no iniciar una transacción en cualquier base de datos que tiene un cursor abierto. Para las clases de base de datos ODBC de MFC, un cursor abierto equivale a un formato de archivo `CRecordset` objeto.  
  
 Si abre un conjunto de registros antes de llamar a **BeginTrans**, quizás no pueda ver los mensajes de error. Sin embargo, cualquier conjunto de registros actualiza los facilita la aplicación se convierten en permanentes después de llamar a `CRecordset::Update`, y las actualizaciones no se revertirá mediante una llamada a **reversión**. Para evitar este problema, debe llamar a **BeginTrans** primero y, a continuación, abra el conjunto de registros.  
  
 MFC comprueba la funcionalidad del controlador para el comportamiento del cursor commit y rollback. Clase `CDatabase` proporciona dos funciones de miembro, `GetCursorCommitBehavior` y `GetCursorRollbackBehavior`, para determinar el efecto de cualquier transacción en el abierto `CRecordset` objeto. Para el controlador ODBC de Microsoft Access 7.0, estas funciones miembro devuelven `SQL_CB_CLOSE` porque el controlador de Access no admite la conservación del cursor. Por lo tanto, debe llamar a `CRecordset::Requery` siguiente un **CommitTrans** o **reversión** operación.  
  
 Cuando necesite realizar varias transacciones uno tras otro, no se puede llamar **Requery** después de la primera transacción y, a continuación, inicio siguiente. Debe cerrar el conjunto de registros antes de la siguiente llamada a **BeginTrans** para satisfacer el requisito de Jet. Esta nota técnica describe dos métodos para controlar esta situación:  
  
-   Cierre el conjunto de registros después de cada uno de ellos **CommitTrans** o **reversión** operación.  
  
-   Con la función de la API de ODBC **SQLFreeStmt**.  
  
## <a name="closing-the-recordset-after-each-committrans-or-rollback-operation"></a>Cierre el conjunto de registros después de cada operación de reversión o CommitTrans  
 Antes de iniciar una transacción, asegúrese de que se cierre el objeto de conjunto de registros. Después de llamar a **BeginTrans**, llame a la función miembro **abiertos** función miembro. Cierre el conjunto de registros inmediatamente después de llamar a **CommitTrans** o **reversión**. Tenga en cuenta que repetidamente de apertura y cierre el conjunto de registros pueden ralentizar el rendimiento de la aplicación.  
  
## <a name="using-sqlfreestmt"></a>Usar SQLFreeStmt  
 También puede utilizar la función de API de ODBC **SQLFreeStmt** cerrar explícitamente el cursor después de finalizar una transacción. Para iniciar otra transacción, llame a **BeginTrans** seguido de `CRecordset::Requery`. Al llamar a **SQLFreeStmt**, debe especificar HSTMT del conjunto de registros como primer parámetro y **SQL_CLOSE** como segundo parámetro. Este método es más rápido que el conjunto de registros al principio de cada transacción de apertura y cierre. El código siguiente muestra cómo implementar esta técnica:  
  
```  
CMyDatabase db;  
db.Open("MYDATASOURCE");

CMyRecordset rs(&db);

 
// start transaction 1 and   
// open the recordset  
db.BeginTrans();

rs.Open();

 
// manipulate data  
 
// end transaction 1  
db.CommitTrans();
*// or Rollback()  
 
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
  
 Otra manera de implementar esta técnica consiste en escribir una nueva función, **RequeryWithBeginTrans**, que puede llamar para iniciar la transacción siguiente después de confirmar o revertir la primera de ellas. Para escribir una función de este tipo, realice los pasos siguientes:  
  
1.  Copie el código para **() CRecordset:: Requery** a la nueva función.  
  
2.  Agregue la línea siguiente inmediatamente después de llamar a **SQLFreeStmt**:  
  
 `m_pDatabase->BeginTrans( );`  
  
 Ahora puede llamar a esta función entre cada par de transacciones:  
  
```  
// start transaction 1 and   
// open the recordset  
db.BeginTrans();

rs.Open();

 
// manipulate data  
 
// end transaction 1  
db.CommitTrans();
*// or Rollback()  
 
// close the cursor,
    start new transaction,  
// and get the result set  
rs.RequeryWithBeginTrans();

 
// manipulate data  
 
// end transaction 2  
db.CommitTrans();
*// or Rollback()  
```  
  
> [!NOTE]
>  No use esta técnica si tiene que cambiar las variables de miembro del conjunto de registros **m_strFilter** o `m_strSort` entre las transacciones. En ese caso, debe cerrar el conjunto de registros después de cada uno **CommitTrans** o **reversión** operación.  
  
## <a name="see-also"></a>Vea también  
 [Notas técnicas por número](../mfc/technical-notes-by-number.md)   
 [Notas técnicas por categoría](../mfc/technical-notes-by-category.md)

