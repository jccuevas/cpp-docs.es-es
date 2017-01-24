---
title: "Transacci&#243;n (ODBC) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "bases de datos [C++], transacciones"
  - "ODBC [C++], transacciones"
  - "conjuntos de registros ODBC [C++], transacciones"
  - "conjuntos de registros ODBC [C++], actualizar"
  - "conjuntos de registros [C++], transacciones"
  - "conjuntos de registros [C++], actualizar"
  - "transacciones [C++], clases ODBC de MFC"
ms.assetid: a2ec0995-2029-45f2-8092-6efd6f2a77f4
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Transacci&#243;n (ODBC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Este tema es aplicable a las clases ODBC de MFC.  
  
 Una transacción es una forma de agrupar una serie de actualizaciones a un [origen de datos](../../data/odbc/data-source-odbc.md) de forma que se confirmen todas a la vez, o no se confirme ninguna si se revierte la transacción.  Si no se utiliza una transacción, se confirman automáticamente los campos en el origen de datos en lugar de confirmarse a petición.  
  
> [!NOTE]
>  No todos los controladores de base de datos ODBC admiten el uso de transacciones.  Llame a la función miembro `CanTransact` del objeto [CDatabase](../../mfc/reference/cdatabase-class.md) o [CRecordset](../../mfc/reference/crecordset-class.md) para determinar si su controlador admite las transacciones para una base de datos en particular.  Observe que `CanTransact` no informa si el origen de datos proporciona total compatibilidad con transacciones.  Se debe llamar también a `CDatabase::GetCursorCommitBehavior` y `CDatabase::GetCursorRollbackBehavior` después de **CommitTrans** y **Rollback** para comprobar el efecto de la transacción en el objeto `CRecordset` abierto.  
  
 Las llamadas a las funciones miembro `AddNew` y **Edit** de un objeto `CRecordset` afectan al origen de datos inmediatamente al llamar a **Update**.  Las llamadas a **Delete** también surten efecto de inmediato.  En contraste, se puede utilizar una transacción compuesta de múltiples llamadas a `AddNew`, **Edit**, **Update** y **Delete**, que se ejecutan pero no se confirman hasta que se llama explícitamente a **CommitTrans**.  Al establecer una transacción, es posible ejecutar una serie de llamadas de este tipo a la vez que se mantiene la posibilidad de revertirlas.  Si un recurso necesario no está disponible o hay alguna otra circunstancia que impida completar toda la transacción, se puede revertir la transacción en lugar de confirmarla.  En ese caso, ninguno de los campos que pertenecen a la transacción afectan al origen de datos.  
  
> [!NOTE]
>  Actualmente, la clase `CRecordset` no permite las actualizaciones en el origen de datos si se ha implementado la obtención masiva de filas.  Esto significa que no es posible realizar llamadas a `AddNew`, **Edit**, **Delete** o **Update**.  Sin embargo, puede escribir sus propias funciones para realizar actualizaciones y después llamar a esas funciones desde una transacción determinada.  Para obtener más información sobre la obtención masiva de filas, vea [Conjunto de registros: Obtener registros de forma masiva \(ODBC\)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
> [!NOTE]
>  Además de afectar al conjunto de registros, las transacciones afectan a las instrucciones SQL ejecutadas directamente en tanto en cuanto se utilice el valor **HDBC** de ODBC asociado al objeto `CDatabase` o un valor de **HSTMT** de ODBC basado en el valor anterior de **HDBC**.  
  
 Las transacciones son especialmente útiles cuando existen múltiples registros que deben actualizarse simultáneamente.  En este caso, es conveniente evitar una transacción parcialmente completada, como puede suceder si se produce una excepción antes de realizar la última actualización.  Agrupar tales actualizaciones en una transacción permite revertir \(rollback\) los cambios y devuelve los registros a su estado anterior a la transacción.  Por ejemplo, si un banco transfiere dinero desde la cuenta A a la cuenta B, la retirada de fondos de A y el depósito en B deben producirse con éxito para procesar los fondos correctamente, de lo contrario la transacción entera debe cancelarse.  
  
 En las clases de base de datos las transacciones se llevan a cabo mediante objetos `CDatabase`.  El objeto `CDatabase` representa una conexión a un origen de datos. Uno o más conjuntos de registros asociados a ese objeto `CDatabase` operan sobre las tablas de la base de datos mediante funciones miembro del conjunto de registros.  
  
> [!NOTE]
>  Sólo se admite un nivel de transacciones.  No se pueden anidar las transacciones y tampoco pueden ocupar varios objetos de base de datos.  
  
 Los temas siguientes proporcionan más información sobre la manera de realizar las transacciones:  
  
-   [Transacción: Realizar una transacción en un conjunto de registros \(ODBC\)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)  
  
-   [Transacción: Cómo afectan las transacciones a las actualizaciones \(ODBC\)](../../data/odbc/transaction-how-transactions-affect-updates-odbc.md)  
  
## Vea también  
 [Conectividad abierta de bases de datos \(ODBC\)](../../data/odbc/open-database-connectivity-odbc.md)