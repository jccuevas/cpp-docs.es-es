---
title: 'Transacción: Realizar una transacción en un conjunto de registros (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- transactions, updating recordsets
ms.assetid: cf1d6b48-7fb8-4903-84f7-a1822054534d
ms.openlocfilehash: 45ae414c318376b2c4d787498e9a288a0037af83
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358092"
---
# <a name="transaction-performing-a-transaction-in-a-recordset-odbc"></a>Transacción: Realizar una transacción en un conjunto de registros (ODBC)

En este tema se explica cómo realizar una transacción en un conjunto de registros.

> [!NOTE]
> Solo se admite un nivel de transacciones; no se pueden anidar transacciones.

#### <a name="to-perform-a-transaction-in-a-recordset"></a>Para realizar una transacción en un conjunto de registros

1. Llame `CDatabase` a la `BeginTrans` función miembro del objeto.

1. Si no ha implementado la obtención `AddNew/Update`masiva `Edit/Update`de `Delete` filas, llame a las funciones , , y miembro de uno o varios objetos de conjunto de registros de la misma base de datos tantas veces como sea necesario. Para obtener más información, vea [Conjunto de registros: agregar, actualizar y eliminar registros (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md). Si ha implementado la obtención masiva de filas, debe escribir sus propias funciones para actualizar el origen de datos.

1. Por último, `CDatabase` llame `CommitTrans` a la función miembro del objeto. Si se produce un error en una de las actualizaciones o decide cancelar los cambios, llame a su `Rollback` función miembro.

En el ejemplo siguiente se usan dos conjuntos de registros para eliminar la inscripción de un alumno de una base de datos de registro de la escuela, quitando el alumno de todas las clases en las que está inscrito el alumno. Dado `Delete` que las llamadas de ambos conjuntos de registros deben realizarse correctamente, se requiere una transacción. En el ejemplo se `m_dbStudentReg`supone la existencia `CDatabase` de , una variable miembro `CEnrollmentSet` de `CStudentSet`tipo ya conectada al origen de datos y las clases de conjunto de registros y . La `strStudentID` variable contiene un valor obtenido del usuario.

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
> Llamar `BeginTrans` de `CommitTrans` nuevo `Rollback` sin llamar o es un error.

## <a name="see-also"></a>Consulte también

[Transacción (ODBC)](../../data/odbc/transaction-odbc.md)<br/>
[Transacción: Cómo afectan las transacciones a las actualizaciones (ODBC)](../../data/odbc/transaction-how-transactions-affect-updates-odbc.md)<br/>
[Clase CDatabase](../../mfc/reference/cdatabase-class.md)<br/>
[Clase CRecordset](../../mfc/reference/crecordset-class.md)
