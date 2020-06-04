---
title: 'Conjunto de registros: Declarar una clase para una consulta predefinida (ODBC)'
ms.date: 05/09/2019
helpviewer_keywords:
- ODBC recordsets, queries
- predefined queries and recordsets
- stored procedures, and recordsets
- recordsets, predefined queries
- recordsets, stored procedures
ms.assetid: d27c4df9-dad2-4484-ba72-92ab0c8ff928
ms.openlocfilehash: f9618f25d738c092ab1818ef7c4ea52928e2ea60
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367037"
---
# <a name="recordset-declaring-a-class-for-a-predefined-query-odbc"></a>Conjunto de registros: Declarar una clase para una consulta predefinida (ODBC)

> [!NOTE]
> El Asistente para consumidores ODBC MFC no está disponible en Visual Studio 2019 ni en versiones posteriores. Aun así, puede crear un consumidor manualmente.

Este tema es aplicable a las clases ODBC de MFC.

En este tema se explica cómo crear una clase de conjunto de registros para una consulta predefinida (también denominada procedimiento almacenado, como en Microsoft SQL Server).

> [!NOTE]
> Este tema se aplica a objetos derivados de `CRecordset` donde no se haya implementado la obtención masiva de filas. Si se implementa la obtención masiva de filas, el proceso es muy similar. Para comprender las diferencias entre los conjuntos de registros que implementan la obtención masiva de filas y los que no, vea [Conjunto de registros: obtención de registros en masa (ODBC).](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)

Algunos sistemas de administración de bases de datos (DBMS) permiten crear una consulta predefinida y llamarla desde programas como una función. La consulta tiene un nombre y es posible que tome parámetros y que devuelva registros. En el procedimiento descrito en este tema se explica cómo llamar a una consulta predefinida que devuelve registros (y que es posible que tome parámetros).

Las clases de base de datos no admiten la actualización de consultas predefinidas. La diferencia entre una consulta predefinida de instantánea y una consulta predefinida de conjunto de registros dinámicos no es la capacidad de actualización, sino si los cambios realizados por otros usuarios (u otros conjuntos de registros del programa) son visibles en el conjunto de registros.

> [!TIP]
> No se necesita un conjunto de registros para llamar a una consulta predefinida que no devuelve ningún registro. Prepare la instrucción SQL como se describe a continuación, pero ejecútela mediante una llamada a la función miembro [ExecuteSQL](../../mfc/reference/cdatabase-class.md#executesql) de `CDatabase`.

Puede crear una única clase de conjunto de registros para administrar la llamada a una consulta predefinida, pero tendrá que hacer parte del trabajo personalmente. Los asistentes no admiten la creación de una clase específicamente para este propósito.

#### <a name="to-create-a-class-for-calling-a-predefined-query-stored-procedure"></a>Para crear una clase para llamar a una consulta predefinida (procedimiento almacenado)

1. Use el [Asistente para consumidores ODBC MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md) desde **Agregar clase** para crear una clase de conjunto de registros para la tabla que aporte el número máximo de columnas devueltas por la consulta. Esto le ofrece una ventaja inicial.

1. Agregue manualmente miembros de datos de campo para las columnas de todas las tablas que devuelva la consulta, pero que el asistente no ha creado de forma automática.

   Por ejemplo, si la consulta devuelve tres columnas de cada una de las dos tablas adicionales, agregue a la clase seis miembros de datos de campo (de los tipos de datos adecuados).

1. Agregue manualmente las llamadas de función [RFX](../../data/odbc/record-field-exchange-rfx.md) en la función miembro [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) de la clase, una para el tipo de datos de cada miembro de datos de campo.

    ```cpp
    Immediately before these RFX calls, call <MSHelp:link keywords="_mfc_CFieldExchange.3a3a.SetFieldType" TABINDEX="0">SetFieldType</MSHelp:link>, as shown here:
    pFX->SetFieldType( CFieldExchange::outputColumn );
    ```

    > [!NOTE]
    >  Debe conocer los tipos de datos y el orden de las columnas devueltas en el conjunto de resultados. El orden de las llamadas de función RFX de `DoFieldExchange` debe coincidir con el orden de las columnas del conjunto de resultados.

1. Agregue manualmente inicializaciones para los nuevos miembros de datos de campo en el constructor de clase del conjunto de registros.

   También debe incrementar el valor de inicialización para el miembro de datos [m_nFields](../../mfc/reference/crecordset-class.md#m_nfields). El asistente escribe la inicialización, pero solo abarca los miembros de datos de campo que agrega de forma automática. Por ejemplo:

    ```cpp
    m_nFields += 6;
    ```

   Algunos tipos de datos no deberían inicializarse aquí, por ejemplo, `CLongBinary` o las matrices de bytes.

1. Si la consulta acepta parámetros, agregue un miembro de datos de parámetro para cada parámetro, una llamada de función RFX y una inicialización para cada uno.

1. Debe incrementar `m_nParams` para cada parámetro que se agregue, como ha hecho con `m_nFields` para los campos agregados en el paso 4 de este procedimiento. Para obtener más información, vea [Conjunto de registros: parametrizar un conjunto de registros (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).

1. Escriba manualmente una cadena de instrucción SQL con el formato siguiente:

    ```
    {CALL proc-name [(? [, ?]...)]}
    ```

   donde **CALL** es una palabra clave de ODBC, **proc-name** es el nombre de la consulta como se conoce en el origen de datos y los elementos "?" son marcadores de posición para los valores de parámetro que se proporcionan al conjunto de registros en tiempo de ejecución (si existe). En el ejemplo siguiente se prepara un marcador de posición para un parámetro:

    ```
    CString mySQL = "{CALL Delinquent_Accts (?)}";
    ```

1. En el código que abre el conjunto de registros, establezca los valores de los miembros de datos de parámetro del conjunto de registros y, después, llame a la función miembro `Open`, pasando la cadena SQL para el parámetro *lpszSQL*. O bien, reemplace la cadena devuelta por la función miembro `GetDefaultSQL` en la clase.

En los ejemplos siguientes se muestra el procedimiento para llamar a una consulta predefinida, denominada `Delinquent_Accts`, que toma un parámetro para un número de región de ventas. Esta consulta devuelve tres columnas: `Acct_No`, `L_Name` y `Phone`. Todas las columnas son de la tabla Customers.

En el conjunto de registros siguiente se especifican miembros de datos de campo para las columnas que devuelve la consulta y un parámetro para el número de región de ventas solicitado en tiempo de ejecución.

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

Esta declaración de clase es como la escribe el asistente, salvo el miembro `m_lDistParam`, que se ha agregado manualmente. Aquí no se muestran los demás miembros.

En el ejemplo siguiente se muestra la inicialización de los miembros de datos en el constructor `CDelinquents`.

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

Observe las inicializaciones de [m_nFields](../../mfc/reference/crecordset-class.md#m_nfields) y [m_nParams](../../mfc/reference/crecordset-class.md#m_nparams). El asistente inicializa `m_nFields`; usted `m_nParams`.

En el ejemplo siguiente se muestran las funciones RFX de `CDelinquents::DoFieldExchange`:

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

Además de realizar las llamadas RFX para las tres columnas devueltas, en este código se administra el enlace del parámetro que se pasa en tiempo de ejecución. El parámetro se escribe en la columna `Dist_No` (el número de región).

En el ejemplo siguiente se muestra cómo configurar la cadena SQL y cómo usarla para abrir el conjunto de registros.

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

Este código crea una instantánea, le pasa un parámetro que ha obtenido antes del usuario y llama a la consulta predefinida. Cuando se ejecuta la consulta, devuelve los registros para la región de ventas especificada. Cada registro contiene columnas para el número de cuenta y el apellido y el número de teléfono del cliente.

> [!TIP]
> Es posible que quiera controlar un valor devuelto (parámetro de salida) desde un procedimiento almacenado. Para obtener más información y un ejemplo, vea [CFieldExchange::SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype).

## <a name="see-also"></a>Consulte también

[Conjunto de registros (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Conjunto de registros: Volver a consultar un conjunto de registros (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md)<br/>
[Conjunto de registros: Declarar una clase para una tabla (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)<br/>
[Conjunto de registros: Realizar una combinación (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md)
