---
title: 'Conjunto de registros: Declarar una clase para una consulta predefinida (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC recordsets, queries
- predefined queries and recordsets
- stored procedures, and recordsets
- recordsets, predefined queries
- recordsets, stored procedures
ms.assetid: d27c4df9-dad2-4484-ba72-92ab0c8ff928
ms.openlocfilehash: d4ae9f21c4bd53a8050d6f8c3765bb9823d077ba
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62395604"
---
# <a name="recordset-declaring-a-class-for-a-predefined-query-odbc"></a>Conjunto de registros: Declarar una clase para una consulta predefinida (ODBC)

Este tema es aplicable a las clases ODBC de MFC.

En este tema se explica cómo crear una clase de conjunto de registros para una consulta predefinida (también conocida como un procedimiento almacenado, como en Microsoft SQL Server).

> [!NOTE]
>  Este tema se aplica a objetos derivados de `CRecordset` donde no se haya implementado la obtención masiva de filas. Si se implementa la obtención masiva de filas, el proceso es muy similar. Para comprender las diferencias entre los conjuntos de registros que implementan la obtención masiva de filas y los que no lo hacen, consulte [conjunto de registros: Obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Algunos sistemas de administración de bases de datos (DBMS) permiten crear una consulta predefinida y llamarla desde los programas, como una función. La consulta tiene un nombre, es posible que toman parámetros y podría devolver registros. El procedimiento descrito en este tema describe cómo llamar a una consulta predefinida que devuelve registros (y quizás toma parámetros).

Las clases de base de datos no admiten la actualización de consultas predefinidas. No es la diferencia entre una consulta predefinida de instantánea y una consulta predefinida dynaset updateability pero si los cambios realizados por otros usuarios (u otros conjuntos de registros en el programa) están visibles en el conjunto de registros.

> [!TIP]
>  No es necesario un conjunto de registros para llamar a una consulta predefinida que no devuelve ningún registro. Preparar la instrucción SQL como se describe a continuación, pero ejecútela mediante una llamada a la `CDatabase` función miembro [ExecuteSQL](../../mfc/reference/cdatabase-class.md#executesql).

Puede crear una clase de conjunto de registros solo para administrar una llamada a una consulta predefinida, pero se debe hacer parte del trabajo personalmente. Los asistentes no admiten la creación de una clase específicamente para este propósito.

#### <a name="to-create-a-class-for-calling-a-predefined-query-stored-procedure"></a>Para crear una clase para llamar a una consulta predefinida (procedimiento almacenado)

1. Use la [Asistente para consumidores ODBC de MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md) desde **Agregar clase** para crear una clase de conjunto de registros para la tabla que aporte el máximo partido de las columnas devueltas por la consulta. Esto le ofrece un punto de partida.

1. Agregar manualmente miembros de datos de campo para las columnas de todas las tablas que devuelva la consulta, pero que el asistente no ha creado para usted.

   Por ejemplo, si la consulta devuelve tres columnas de cada una de las dos tablas adicionales, agregue a seis miembros de datos de campo (de los tipos de datos adecuado) a la clase.

1. Agregar manualmente [RFX](../../data/odbc/record-field-exchange-rfx.md) llamadas función en el [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) agregado de función miembro de la clase, una de ellas correspondiente al tipo de datos de cada miembro de datos de campo.

    ```cpp
    Immediately before these RFX calls, call <MSHelp:link keywords="_mfc_CFieldExchange.3a3a.SetFieldType" TABINDEX="0">SetFieldType</MSHelp:link>, as shown here:
    pFX->SetFieldType( CFieldExchange::outputColumn );
    ```

    > [!NOTE]
    >  Debe conocer los tipos de datos y el orden de las columnas devueltas en el resultado de conjunto. El orden de función RFX las llamadas `DoFieldExchange` debe coincidir con el orden de columnas del conjunto de resultados.

1. Agregar manualmente las inicializaciones de los nuevos miembros de datos de campo en el constructor de clase de conjunto de registros.

   También debe incrementar el valor de inicialización para la [m_nFields](../../mfc/reference/crecordset-class.md#m_nfields) miembro de datos. El asistente escribe la inicialización, pero sólo cubre a los miembros de datos de campo que agrega automáticamente. Por ejemplo:

    ```cpp
    m_nFields += 6;
    ```

   Algunos tipos de datos no deberían inicializarse en este caso, por ejemplo, `CLongBinary` o matrices de bytes.

1. Si la consulta acepta parámetros, agregar a un miembro de datos de parámetro para cada parámetro, una llamada de función RFX y código de inicialización para cada uno.

1. Se debe incrementar `m_nParams` para cada uno de ellos se ha agregado el parámetro, como lo hizo `m_nFields` para agregar campos en el paso 4 de este procedimiento. Para obtener más información, consulte [conjunto de registros: Parametrizar un conjunto de registros (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).

1. Escribir manualmente una cadena de instrucción SQL con el formato siguiente:

    ```
    {CALL proc-name [(? [, ?]...)]}
    ```

   donde **llamar** es una palabra clave ODBC, **nombre de procedimiento** es el nombre de la consulta como se conoce en el origen de datos y el "?" son marcadores de posición para los valores de parámetro que proporcione al conjunto de registros en tiempo de ejecución (si existe) . El ejemplo siguiente prepara un marcador de posición para un parámetro:

    ```
    CString mySQL = "{CALL Delinquent_Accts (?)}";
    ```

1. En el código que se abre el conjunto de registros, establezca los valores del parámetro del conjunto de registros de miembros de datos y, a continuación, llame a la `Open` función miembro, pasando la cadena SQL la *lpszSQL* parámetro. O bien, reemplace la cadena devuelta por la `GetDefaultSQL` función de miembro en la clase.

Los ejemplos siguientes muestran el procedimiento para llamar a una consulta predefinida, denominada `Delinquent_Accts`, que toma un parámetro para un número de ventas de distrito. Esta consulta devuelve tres columnas: `Acct_No`, `L_Name`, `Phone`. Todas las columnas son de la tabla Customers.

El conjunto de registros siguiente especifica a los miembros de datos de campo para las columnas que devuelve la consulta y un parámetro para las ventas por número de distrito solicitado en tiempo de ejecución.

```cpp
class CDelinquents : public CRecordset
{
// Field/Param Data
    LONG m_lAcct_No;
    CString m_strL_Name;
    CString m_strPhone;
    LONG m_lDistParam;
    // ...
};
```

Esta declaración de clase es como el asistente escribe, salvo el `m_lDistParam` miembro agregado manualmente. Otros miembros no se muestran aquí.

En el ejemplo siguiente se muestra el código de inicialización de los miembros de datos en el `CDelinquents` constructor.

```cpp
CDelinquents::CDelinquents(CDatabase* pdb)
   : CRecordset(pdb)
{
    // Wizard-generated params:
    m_lAcct_No = 0;
    m_strL_Name = "";
    m_strPhone = "";
    m_nFields = 3;
    // User-defined params:
    m_nParams = 1;
    m_lDistParam = 0;
}
```

Tenga en cuenta las inicializaciones de [m_nFields](../../mfc/reference/crecordset-class.md#m_nfields) y [m_nParams](../../mfc/reference/crecordset-class.md#m_nparams). Inicializa el asistente `m_nFields`; inicialice `m_nParams`.

En el ejemplo siguiente se muestra en las funciones de RFX `CDelinquents::DoFieldExchange`:

```cpp
void CDelinquents::DoFieldExchange(CFieldExchange* pFX)
{
    pFX->SetFieldType(CFieldExchange::outputColumn);
    RFX_Long(pFX, "Acct_No", m_lAcct_No);
    RFX_Text(pFX, "L_Name", m_strL_Name);
    RFX_Text(pFX, "Phone", m_strPhone);
    pFX->SetFieldType(CFieldExchange::param);
    RFX_Long(pFX, "Dist_No", m_lDistParam);
}
```

Además de realizar las llamadas RFX para las tres columnas devueltas, este código administra el enlace del parámetro que se pasa en tiempo de ejecución. El parámetro se introduce la `Dist_No` columna (número de distrito).

En el ejemplo siguiente se muestra cómo configurar la cadena de SQL y cómo se usa para abrir el conjunto de registros.

```cpp
// Construct a CDelinquents recordset object
CDelinquents rsDel( NULL );
CString strSQL = "{CALL Delinquent_Accts (?)}"
// Specify a parameter value (obtained earlier from the user)
rsDel.m_lDistParam = lDistrict;
// Open the recordset and run the query
if( rsDel.Open( CRecordset::snapshot, strSQL ) )
    // Use the recordset ...
```

Este código crea una instantánea, pasa un parámetro que obtuvo anteriormente en el usuario y llama a la consulta predefinida. Cuando se ejecuta la consulta, devuelve los registros de la zona de ventas especificado. Cada registro contiene columnas para el número de cuenta, el apellido del cliente y número de teléfono del cliente.

> [!TIP]
>  Es posible que desee controlar el valor devuelto (parámetro de salida) desde un procedimiento almacenado. Para obtener más información y un ejemplo, vea [CFieldExchange:: SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype).

## <a name="see-also"></a>Vea también

[Conjunto de registros (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Conjunto de registros: volver a consultar un conjunto de registros (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md)<br/>
[Conjunto de registros: declarar una clase para una tabla (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)<br/>
[Conjunto de registros: realizar una combinación (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md)