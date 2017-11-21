---
title: 'Conjunto de registros: Declarar una clase para una consulta predefinida (ODBC) | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- ODBC recordsets, queries
- predefined queries and recordsets
- stored procedures, and recordsets
- recordsets, predefined queries
- recordsets, stored procedures
ms.assetid: d27c4df9-dad2-4484-ba72-92ab0c8ff928
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1d5fdb93880ec29343d38acba7d7d42caf155214
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="recordset-declaring-a-class-for-a-predefined-query-odbc"></a>Conjunto de registros: Declarar una clase para una consulta predefinida (ODBC)
Este tema es aplicable a las clases ODBC de MFC.  
  
 En este tema se explica cómo crear una clase de conjunto de registros para una consulta predefinida (a veces denominada un procedimiento almacenado, como en Microsoft SQL Server).  
  
> [!NOTE]
>  Este tema se aplica a objetos derivados de `CRecordset` donde no se haya implementado la obtención masiva de filas. Si se implementa la obtención masiva de filas, el proceso es muy similar. Para entender las diferencias entre los conjuntos de registros que implementan la obtención masiva de filas y los que no lo hacen, vea [conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Algunos sistemas de administración de bases de datos (DBMS) permiten crear una consulta predefinida y llamarlo desde los programas como una función. La consulta tiene un nombre, podría adoptar parámetros y podría devolver registros. El procedimiento descrito en este tema describe cómo llamar a una consulta predefinida que devuelve registros (y, quizás, toma parámetros).  
  
 Las clases de base de datos no son compatibles con la actualización de consultas predefinidas. La diferencia entre una consulta predefinida de instantánea y una consulta predefinida de conjunto de registros dinámicos no es de capacidad de actualización, pero si los cambios realizados por otros usuarios (o conjuntos de registros en el programa) están visibles en el conjunto de registros.  
  
> [!TIP]
>  No es necesario un conjunto de registros para llamar a una consulta predefinida que no devuelve ningún registro. Preparar la instrucción SQL como se describe a continuación, pero ejecutar mediante una llamada a la `CDatabase` función miembro [ExecuteSQL](../../mfc/reference/cdatabase-class.md#executesql).  
  
 Puede crear una clase de conjunto de registros único para administrar las llamadas a una consulta predefinida, pero se debe hacer parte del trabajo personalmente. Los asistentes no admiten la creación de una clase específicamente para este propósito.  
  
#### <a name="to-create-a-class-for-calling-a-predefined-query-stored-procedure"></a>Para crear una clase para llamar a una consulta predefinida (procedimiento almacenado)  
  
1.  Use la [Asistente para consumidores ODBC de MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md) de **Agregar clase** para crear una clase de conjunto de registros de la tabla que contribuye a la mayoría de las columnas devueltas por la consulta. Esto proporciona un punto de partida.  
  
2.  Agregar manualmente miembros de datos de campo para las columnas de las tablas que devuelva la consulta, pero que el asistente no ha creado para usted.  
  
     Por ejemplo, si la consulta devuelve tres columnas de cada una de las dos tablas adicionales, agregue a seis miembros de datos de campo (de los tipos de datos adecuado) a la clase.  
  
3.  Agregar manualmente [RFX](../../data/odbc/record-field-exchange-rfx.md) función llama a el [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) función miembro de la clase, una de ellas correspondiente al tipo de datos de cada agregado correctamente al miembro de datos de campo.  
  
    ```  
    Immediately before these RFX calls, call <MSHelp:link keywords="_mfc_CFieldExchange.3a3a.SetFieldType" TABINDEX="0">SetFieldType</MSHelp:link>, as shown here:   
    pFX->SetFieldType( CFieldExchange::outputColumn );  
    ```  
  
    > [!NOTE]
    >  Debe conocer los tipos de datos y el orden de las columnas devueltas en el resultado de conjunto. El orden de función RFX llama `DoFieldExchange` debe coincidir con el orden de columnas del conjunto de resultados.  
  
4.  Agregar manualmente el código de inicialización para los nuevos miembros de datos de campo en el constructor de clase de conjunto de registros.  
  
     También debe incrementar el valor de inicialización para la [m_nFields](../../mfc/reference/crecordset-class.md#m_nfields) miembro de datos. El asistente escribe la inicialización, pero sólo cubre a los miembros de datos de campo que agrega automáticamente. Por ejemplo:  
  
    ```  
    m_nFields += 6;  
    ```  
  
     Algunos tipos de datos no se deben inicializar aquí, por ejemplo, `CLongBinary` o matrices de bytes.  
  
5.  Si la consulta acepta parámetros, agregar a un miembro de datos de parámetro para cada parámetro, una llamada de función RFX y código de inicialización para cada uno.  
  
6.  Debe incrementar `m_nParams` para cada parámetro, de agregado como lo hizo `m_nFields` para agregar campos en el paso 4 de este procedimiento. Para obtener más información, consulte [conjunto de registros: parametrizar un conjunto de registros (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).  
  
7.  Escribir manualmente una cadena de instrucción SQL con el formato siguiente:  
  
    ```  
    {CALL proc-name [(? [, ?]...)]}  
    ```  
  
     donde **llamar a** es una palabra clave ODBC, **proc name** es el nombre de la consulta como se conoce en el origen de datos y el "?" son marcadores de posición para los valores de parámetro que proporciona para el conjunto de registros en tiempo de ejecución (si existe) . En el ejemplo siguiente se prepara un marcador de posición para un parámetro:  
  
    ```  
    CString mySQL = "{CALL Delinquent_Accts (?)}";  
    ```  
  
8.  En el código que abre el conjunto de registros, establezca los valores del parámetro del conjunto de registros de miembros de datos y, a continuación, llame a la **abiertos** función miembro, pasando la cadena SQL la **lpszSQL** parámetro. O bien, reemplace la cadena devuelta por la `GetDefaultSQL` función miembro en la clase.  
  
 Los ejemplos siguientes muestran el procedimiento para llamar a una consulta predefinida, denominada `Delinquent_Accts`, que toma un parámetro para un número de zona de ventas. Esta consulta devuelve tres columnas: `Acct_No`, `L_Name`, `Phone`. Todas las columnas son de la tabla Customers.  
  
 El siguiente conjunto de registros especifica a miembros de datos de campo para las columnas que devuelve la consulta y un parámetro para las ventas por distrito número solicitado en tiempo de ejecución.  
  
```  
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
  
 Esta declaración de clase es como el asistente escribe, salvo por la `m_lDistParam` miembro agregado manualmente. Otros miembros no se muestran aquí.  
  
 En el ejemplo siguiente se muestra el código de inicialización de los miembros de datos en el `CDelinquents` constructor.  
  
```  
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
  
 Tenga en cuenta las inicializaciones de [m_nFields](../../mfc/reference/crecordset-class.md#m_nfields) y [m_nParams](../../mfc/reference/crecordset-class.md#m_nparams). El asistente inicializa `m_nFields`; inicializar `m_nParams`.  
  
 En el ejemplo siguiente se muestra las funciones de RFX en `CDelinquents::DoFieldExchange`:  
  
```  
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
  
 Además de realizar las llamadas RFX para las tres columnas devueltas, este código administra el enlace del parámetro pasado en tiempo de ejecución. El parámetro como clave para la `Dist_No` columna (número de distrito).  
  
 En el ejemplo siguiente se muestra cómo configurar la cadena de SQL y cómo utilizarla para abrir el conjunto de registros.  
  
```  
// Construct a CDelinquents recordset object  
CDelinquents rsDel( NULL );  
CString strSQL = "{CALL Delinquent_Accts (?)}"  
// Specify a parameter value (obtained earlier from the user)  
rsDel.m_lDistParam = lDistrict;  
// Open the recordset and run the query  
if( rsDel.Open( CRecordset::snapshot, strSQL ) )  
    // Use the recordset ...  
```  
  
 Este código crea una instantánea, le pasa un parámetro obtenido anteriormente en el usuario y llama a la consulta predefinida. Cuando se ejecuta la consulta, devuelve los registros de la zona de ventas especificado. Cada registro contiene columnas para el número de cuenta, el apellido del cliente y el número de teléfono del cliente.  
  
> [!TIP]
>  Puede controlar el valor devuelto (parámetro de salida) de un procedimiento almacenado. Para obtener más información y un ejemplo, vea [CFieldExchange:: SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype).  
  
## <a name="see-also"></a>Vea también  
 [Conjunto de registros (ODBC)](../../data/odbc/recordset-odbc.md)   
 [Conjunto de registros: Volver a consultar un conjunto de registros (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md)   
 [Conjunto de registros: Declarar una clase para una tabla (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)   
 [Conjunto de registros: Realizar una combinación (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md)