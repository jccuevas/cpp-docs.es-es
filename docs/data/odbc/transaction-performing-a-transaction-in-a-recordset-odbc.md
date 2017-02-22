---
title: "Transacci&#243;n: Realizar una transacci&#243;n en un conjunto de registros (ODBC) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "transacciones, actualizar conjuntos de registros"
ms.assetid: cf1d6b48-7fb8-4903-84f7-a1822054534d
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Transacci&#243;n: Realizar una transacci&#243;n en un conjunto de registros (ODBC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Este tema explica cómo realizar una transacción en un conjunto de registros.  
  
> [!NOTE]
>  Sólo se admite un nivel de transacciones; no es posible anidar las transacciones.  
  
#### Para realizar una transacción en un conjunto de registros  
  
1.  Llame a la función miembro **BeginTrans** del objeto `CDatabase`.  
  
2.  Si no está implementada la obtención de filas masiva, llame a las funciones miembro **AddNew\/Update**, **Edit\/Update** y **Delete** de uno o más objetos de conjunto de registros correspondientes a la misma base de datos tantas veces como sea necesario.  Para obtener más información, vea [Conjunto de registros: Agregar, actualizar y eliminar registros \(ODBC\)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md) Si está implementada la obtención de filas masiva, debe escribir sus propias funciones para actualizar el origen de datos.  
  
3.  Por último, llame a la función miembro **CommitTrans** del objeto `CDatabase`.  Si ocurre un error en una de las actualizaciones o decide cancelar los cambios, llame a su función miembro **Rollback**.  
  
 El ejemplo siguiente usa dos conjuntos de registros para eliminar la inscripción de un estudiante de una base de datos de registro de estudiantes, quitando al estudiante de todas las clases en que se inscribió.  Deben ejecutarse con éxito las llamadas a **Delete** en ambos conjuntos de registros, por lo que se requiere una transacción.  El ejemplo supone la existencia de `m_dbStudentReg`, una variable miembro del tipo `CDatabase` ya conectada al origen de datos, y de las clases de conjunto de registros `CEnrollmentSet` y `CStudentSet`.  La variable `strStudentID` contiene un valor obtenido del usuario.  
  
```  
BOOL CEnrollDoc::RemoveStudent( CString strStudentID )  
{  
    // remove student from all the classes  
    // the student is enrolled in  
  
    if ( !m_dbStudentReg.BeginTrans( ) )  
        return FALSE;  
  
    CEnrollmentSet rsEnrollmentSet(&m_dbStudentReg);  
    rsEnrollmentSet.m_strFilter = "StudentID = " + strStudentID;  
  
    if ( !rsEnrollmentSet.Open(CRecordset::dynaset) )  
        return FALSE;  
  
    CStudentSet rsStudentSet(&m_dbStudentReg);  
    rsStudentSet.m_strFilter = "StudentID = " + strStudentID;  
  
    if ( !rsStudentSet.Open(CRecordset::dynaset) )  
        return FALSE;  
  
    TRY  
    {  
        while ( !rsEnrollmentSet.IsEOF( ) )  
        {  
            rsEnrollmentSet.Delete( );  
            rsEnrollmentSet.MoveNext( );  
        }  
  
        // delete the student record  
        rsStudentSet.Delete( );  
  
        m_dbStudentReg.CommitTrans( );  
    }  
  
    CATCH_ALL(e)  
    {  
        m_dbStudentReg.Rollback( );  
        return FALSE;  
    }  
    END_CATCH_ALL  
  
    rsEnrollmentSet.Close( );  
    rsStudentSet.Close( );  
  
    return TRUE;  
  
}  
```  
  
> [!NOTE]
>  Si se llama de nuevo a **BeginTrans** sin llamar a **CommitTrans** o **Rollback**, se produce un error.  
  
## Vea también  
 [Transacción \(ODBC\)](../../data/odbc/transaction-odbc.md)   
 [Transacción: Cómo afectan las transacciones a las actualizaciones \(ODBC\)](../../data/odbc/transaction-how-transactions-affect-updates-odbc.md)   
 [CDatabase Class](../../mfc/reference/cdatabase-class.md)   
 [CRecordset Class](../../mfc/reference/crecordset-class.md)