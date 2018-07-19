---
title: 'Transacción: Realizar una transacción en un conjunto de registros (ODBC) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- transactions, updating recordsets
ms.assetid: cf1d6b48-7fb8-4903-84f7-a1822054534d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 1d7cae3b05c20736a2e271b574569bcac4d5cdc7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33094610"
---
# <a name="transaction-performing-a-transaction-in-a-recordset-odbc"></a>Transacción: Realizar una transacción en un conjunto de registros (ODBC)
Este tema explica cómo realizar una transacción en un conjunto de registros.  
  
> [!NOTE]
>  Se admite solo un nivel de transacciones; no se pueden anidar transacciones.  
  
#### <a name="to-perform-a-transaction-in-a-recordset"></a>Para realizar una transacción en un conjunto de registros  
  
1.  Llame a la `CDatabase` del objeto **BeginTrans** función miembro.  
  
2.  Si no ha implementado la obtención masiva de filas, llame a la **AddNew/Update**, **editar o actualizar**, y **eliminar** las funciones miembro de uno o más objetos de conjunto de registros de la misma base de datos tantas veces como sea necesario. Para obtener más información, consulte [conjunto de registros: agregar, actualizar y eliminar registros (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md). Si ha implementado la obtención masiva de filas, debe escribir sus propias funciones para actualizar el origen de datos.  
  
3.  Por último, llame a la `CDatabase` del objeto **CommitTrans** función miembro. Si se produce un error en una de las actualizaciones o decide cancelar los cambios, llame a su **reversión** función miembro.  
  
 En el ejemplo siguiente se usa dos conjuntos de registros para eliminar la inscripción de un estudiante de una base de datos de registro de escuela, quitando al estudiante de todas las clases en el que está inscrito los estudiantes. Dado que la **eliminar** llamadas en ambos conjuntos de registros deben tener éxito, se requiere una transacción. El ejemplo supone la existencia de `m_dbStudentReg`, una variable miembro de tipo `CDatabase` ya está conectado al origen de datos y las clases de conjunto de registros `CEnrollmentSet` y `CStudentSet`. El `strStudentID` variable contiene un valor obtenido del usuario.  
  
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
>  Al llamar a **BeginTrans** sin necesidad de llamar a **CommitTrans** o **reversión** es un error.  
  
## <a name="see-also"></a>Vea también  
 [Transacción (ODBC)](../../data/odbc/transaction-odbc.md)   
 [Transacción: Cómo afectan las transacciones a las actualizaciones (ODBC)](../../data/odbc/transaction-how-transactions-affect-updates-odbc.md)   
 [CDatabase (clase)](../../mfc/reference/cdatabase-class.md)   
 [CRecordset (clase)](../../mfc/reference/crecordset-class.md)