---
title: 'Transacción: Realizar una transacción en un conjunto de registros (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- transactions, updating recordsets
ms.assetid: cf1d6b48-7fb8-4903-84f7-a1822054534d
ms.openlocfilehash: 94177a27a1f99a8c9c37b7fce3f697fd0088b7c6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212594"
---
# <a name="transaction-performing-a-transaction-in-a-recordset-odbc"></a>Transacción: Realizar una transacción en un conjunto de registros (ODBC)

En este tema se explica cómo realizar una transacción en un conjunto de registros.

> [!NOTE]
>  Solo se admite un nivel de transacciones; no se pueden anidar transacciones.

#### <a name="to-perform-a-transaction-in-a-recordset"></a>Para realizar una transacción en un conjunto de registros

1. Llame a la función miembro `BeginTrans` del objeto `CDatabase`.

1. Si no ha implementado la obtención masiva de filas, llame a las funciones miembro `AddNew/Update`, `Edit/Update`y `Delete` de uno o más objetos de conjunto de registros de la misma base de datos tantas veces como sea necesario. Para obtener más información, vea [conjunto de registros: agregar, actualizar y eliminar registros (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md). Si ha implementado la obtención masiva de filas, debe escribir sus propias funciones para actualizar el origen de datos.

1. Por último, llame a la función miembro `CommitTrans` del objeto `CDatabase`. Si se produce un error en una de las actualizaciones o decide cancelar los cambios, llame a su función miembro `Rollback`.

En el ejemplo siguiente se usan dos conjuntos de registros para eliminar la inscripción de un estudiante de una base de datos de registro escolar y quitar el estudiante de todas las clases en las que el estudiante está inscrito. Dado que las llamadas `Delete` en ambos conjuntos de registros deben ejecutarse correctamente, se requiere una transacción. En el ejemplo se supone la existencia de `m_dbStudentReg`, una variable miembro de tipo `CDatabase` ya está conectada al origen de datos y las clases de conjunto de registros `CEnrollmentSet` y `CStudentSet`. La variable `strStudentID` contiene un valor obtenido del usuario.

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
>  Llamar a `BeginTrans` de nuevo sin llamar a `CommitTrans` o `Rollback` es un error.

## <a name="see-also"></a>Consulte también

[Transacción (ODBC)](../../data/odbc/transaction-odbc.md)<br/>
[Transacción: Cómo afectan las transacciones a las actualizaciones (ODBC)](../../data/odbc/transaction-how-transactions-affect-updates-odbc.md)<br/>
[CDatabase (clase)](../../mfc/reference/cdatabase-class.md)<br/>
[CRecordset (clase)](../../mfc/reference/crecordset-class.md)
