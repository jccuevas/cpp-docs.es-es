---
title: "TN068: Realizar transacciones con el controlador ODBC de Microsoft Access 7 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.data.odbc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "TN068"
  - "transacciones, llamar a BeginTrans"
  - "transacciones, Microsoft Access"
ms.assetid: d3f8f5d9-b118-4194-be36-a1aefb630c45
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# TN068: Realizar transacciones con el controlador ODBC de Microsoft Access 7
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  La nota técnica siguiente no se ha actualizado desde que se incluyó por primera vez en la documentación en línea.  Como resultado, algunos procedimientos y temas podrían estar obsoletos o ser incorrectos.  Para obtener información más reciente, se recomienda buscar el tema de interés en el índice de la documentación en línea.  
  
 Esta nota describe cómo realizar transacciones al utilizar las clases de base de datos ODBC de MFC y el controlador ODBC de Microsoft Access 7,0 incluido en el controlador de escritorio de Microsoft ODBC empaqueta la versión 3.0.  
  
## Información general  
 Si la aplicación de base de datos realiza transacciones, debe tener cuidado de llamar a `CDatabase::BeginTrans` y `CRecordset::Open` en la secuencia correcta en la aplicación.  El controlador de Microsoft Access 7,0 utiliza el motor de base de datos Microsoft Jet, y Jet requiere que el inicio de la aplicación no una transacción en cualquier base de datos que tiene el cursor abierto.  Para las clases de base de datos ODBC de MFC, el cursor abierto con `CRecordset` un objeto abierto.  
  
 Si abre un conjunto de registros antes de llamar a **BeginTrans**, no puede ver los mensajes de error.  Sin embargo, cualquier conjunto de registros actualiza la aplicación crea pasar a permanente después de llamar a `CRecordset::Update`, y las actualizaciones no se revertirá llamando a **Reversión**.  Para evitar este problema, debe llamar a **BeginTrans** primero y abra el conjunto de registros.  
  
 MFC comprueba la funcionalidad del controlador de confirmación del cursor y el comportamiento de recuperación.  La clase `CDatabase` proporciona dos funciones miembro, `GetCursorCommitBehavior` y `GetCursorRollbackBehavior`, para determinar el efecto de cualquier transacción en el objeto abierto de `CRecordset` .  Para el controlador ODBC de Microsoft Access 7,0, estas funciones miembro devuelven `SQL_CB_CLOSE` porque el controlador de Access no admite la conservación del cursor.  Por tanto, debe llamar a `CRecordset::Requery` tras una operación de **CommitTrans** o de **Reversión** .  
  
 Cuando necesite realizar varias transacciones uno tras otro, no puede llamar a **Requery** después de la primera transacción e iniciar el siguiente.  Debe cerrar el conjunto de registros antes de la llamada siguiente a **BeginTrans** para satisfacer el requisito de Jet.  Esta nota técnica describe dos métodos para administrar esta situación:  
  
-   Cerrando el conjunto de registros después de cada operación de **CommitTrans** o de **Reversión** .  
  
-   Mediante la función API **SQLFreeStmt**de ODBC.  
  
## Cerrando el conjunto de registros después de cada CommitTrans u operación de combinar  
 Antes de iniciar una transacción, asegúrese de que se cierre el objeto de conjunto de registros.  Después de llamar a **BeginTrans**, llame a la función miembro de **Abierta** de conjunto de registros.  Cierre el conjunto de registros inmediatamente después de llamar a **CommitTrans** o **Reversión**.  Observe que repetidamente la apertura y de cierre el conjunto de registros pueden reducir el rendimiento de una aplicación.  
  
## Mediante SQLFreeStmt  
 También puede usar la función API **SQLFreeStmt** de ODBC explícitamente para cerrar el cursor después de finalizar una transacción.  Para iniciar otra transacción, llame a **BeginTrans** seguido de `CRecordset::Requery`.  Al llamar a **SQLFreeStmt**, debe especificar el HSTMT de conjunto de registros como primer parámetro y **SQL\_CLOSE** como segundo parámetro.  Este método es más rápido que cerrar y abrir el conjunto de registros al inicio de cada transacción.  El código siguiente muestra cómo implementar esta técnica:  
  
```  
CMyDatabase db;  
db.Open( "MYDATASOURCE" );  
CMyRecordset rs( &db );  
  
// start transaction 1 and   
// open the recordset  
db.BeginTrans( );  
rs.Open( );  
  
// manipulate data  
  
// end transaction 1  
db.CommitTrans( );  // or Rollback( )  
  
// close the cursor  
::SQLFreeStmt( rs.m_hstmt, SQL_CLOSE );  
  
// start transaction 2  
db.BeginTrans( );  
  
// now get the result set  
rs.Requery( );  
  
// manipulate data  
  
// end transaction 2  
db.CommitTrans( );  
  
rs.Close( );  
db.Close( );  
```  
  
 Otra manera de implementar esta técnica es escribir una función nueva, **RequeryWithBeginTrans**, que puede llamar para iniciar la transacción después de confirmar o revertir primero.  Para escribir una función, realice los pasos siguientes:  
  
1.  Copie el código para **CRecordset::Requery\( \)** a la nueva función.  
  
2.  Agregue la siguiente línea inmediatamente después de llamar a **SQLFreeStmt**:  
  
     `m_pDatabase->BeginTrans( );`  
  
 Ahora puede llamar a esta función entre cada par de transacciones:  
  
```  
// start transaction 1 and   
// open the recordset  
db.BeginTrans( );  
rs.Open( );  
  
// manipulate data  
  
// end transaction 1  
db.CommitTrans( );  // or Rollback( )  
  
// close the cursor, start new transaction,  
// and get the result set  
rs.RequeryWithBeginTrans( );  
  
// manipulate data  
  
// end transaction 2  
db.CommitTrans( );  // or Rollback( )  
```  
  
> [!NOTE]
>  No utilice esta técnica si necesita cambiar las variables miembro **m\_strFilter** o `m_strSort` de conjunto de registros entre las transacciones.  En ese caso, debe cerrar el conjunto de registros después de cada operación de **CommitTrans** o de **Reversión** .  
  
## Vea también  
 [Notas técnicas por número](../mfc/technical-notes-by-number.md)   
 [Notas técnicas por categoría](../mfc/technical-notes-by-category.md)