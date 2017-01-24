---
title: "Conjunto de registros: Declarar una clase para una consulta predefinida (ODBC) | Microsoft Docs"
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
  - "conjuntos de registros ODBC, consultas"
  - "consultas y conjuntos de registros predefinidos"
  - "conjuntos de registros, consultas predefinidas"
  - "conjuntos de registros, procedimientos almacenados"
  - "procedimientos almacenados, conjuntos de registros"
ms.assetid: d27c4df9-dad2-4484-ba72-92ab0c8ff928
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Conjunto de registros: Declarar una clase para una consulta predefinida (ODBC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Este tema es aplicable a las clases ODBC de MFC.  
  
 Este tema explica la creación de una clase de conjunto de registros para una consulta predefinida \(a veces denominada "procedimiento almacenado", como en Microsoft SQL Server\).  
  
> [!NOTE]
>  Este tema se aplica a objetos derivados de `CRecordset` donde no se haya implementado la obtención masiva de filas.  Si se implementa la obtención masiva de filas, el proceso es muy similar.  Para comprender las diferencias entre conjuntos de registros que implementan la obtención masiva de filas y los que no, vea [Conjunto de registros: obtener registros de forma masiva \(ODBC\)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Algunos sistemas de administración de bases de datos \(DBMSs\) permiten crear una consulta predefinida y llamarla desde los programas como si fuera una función.  La consulta tiene nombre, podría adoptar parámetros y devolver registros.  El procedimiento de este tema describe cómo llamar a una consulta predefinida que devuelve registros \(y, quizás, toma parámetros\).  
  
 Las clases de base de datos no admiten la actualización de consultas predefinidas.  La diferencia entre una consulta predefinida de instantánea y otra de conjunto de registros dinámico no se encuentra en la capacidad de actualización, sino en el hecho de si los cambios realizados por otros usuarios \(u otros conjuntos de registros de la aplicación\) serán visibles en el conjunto de registros.  
  
> [!TIP]
>  No es necesario ningún conjunto de registros para llamar a una consulta predefinida que no devuelve registros.  Prepare la instrucción SQL como se describe a continuación, pero ejecútela llamando a la función miembro de `CDatabase` [ExecuteSQL](../Topic/CDatabase::ExecuteSQL.md).  
  
 Se puede crear una sola clase de conjunto de registros para administrar las llamadas a una consulta predefinida, pero se debe hacer parte del trabajo personalmente.  Los asistentes no admiten la creación de una clase específicamente para este fin.  
  
#### Cómo crear una clase para llamar a una consulta predefinida \(procedimiento almacenado\)  
  
1.  Utilice el [Asistente para consumidores ODBC de MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md) mediante **Agregar clase para crear una clase de conjunto de registros que aporte la mayoría de las columnas devueltas por la consulta.** Esto sirve de preparación para el proceso.  
  
2.  Agregue manualmente los miembros de datos de campo para cualquier columna de cualquier tabla que devuelva la consulta, pero que no haya sido creada por el asistente.  
  
     Por ejemplo, si la consulta devuelve tres columnas de cada una de las dos tablas adicionales, agregue a la clase seis miembros de datos de campo \(de los tipos de datos apropiados\).  
  
3.  Agregue manualmente llamadas de función [RFX](../../data/odbc/record-field-exchange-rfx.md) a la función miembro [DoFieldExchange](../Topic/CRecordset::DoFieldExchange.md) de la clase, una de ellas correspondiente al tipo de datos de cada miembro de datos de campo agregado.  
  
    ```  
    Immediately before these RFX calls, call <MSHelp:link keywords="_mfc_CFieldExchange.3a3a.SetFieldType" TABINDEX="0">SetFieldType</MSHelp:link>, as shown here:   
    pFX->SetFieldType( CFieldExchange::outputColumn );  
    ```  
  
    > [!NOTE]
    >  Se deben conocer los tipos de datos y el orden de las columnas devueltas en el conjunto de resultados.  El orden de las llamadas de función RFX en `DoFieldExchange` debe coincidir con el orden de las columnas del conjunto de resultados.  
  
4.  Agregue manualmente código de inicialización para los nuevos miembros de datos de campo en el constructor de la clase de conjunto de registros.  
  
     Se debe aumentar el valor de inicialización del miembro de datos [m\_nFields](../Topic/CRecordset::m_nFields.md).  El asistente escribe la inicialización, pero sólo cubre los miembros de datos de campo que agrega.  Por ejemplo:  
  
    ```  
    m_nFields += 6;  
    ```  
  
     Algunos tipos de datos no se deben inicializar aquí; por ejemplo, `CLongBinary` o las matrices de bytes.  
  
5.  Si la consulta toma parámetros, por cada uno de ellos se debe agregar un miembro de datos de parámetro, una llamada de función RFX y código de inicialización.  
  
6.  Se debe aumentar `m_nParams` para cada parámetro agregado, como lo hizo con `m_nFields` para los campos agregados en el paso 4 de este procedimiento.  Para obtener más información, vea [Conjunto de registros: Parametrizar un conjunto de registros \(ODBC\)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).  
  
7.  Escriba manualmente una cadena de instrucción SQL con la siguiente forma:  
  
    ```  
    {CALL proc-name [(? [, ?]...)]}  
    ```  
  
     donde **CALL** es una palabra clave de ODBC, **proc name** es el nombre de la consulta como se conoce en el origen de datos, y los símbolos "?" son marcadores de posición para los valores de parámetro que se pasan al conjunto de registros en tiempo de ejecución \(si los hay\).  El siguiente ejemplo prepara un marcador de posición para un parámetro:  
  
    ```  
    CString mySQL = "{CALL Delinquent_Accts (?)}";  
    ```  
  
8.  En el código que abre el conjunto de registros, establezca los valores de los miembros de datos de parámetro del conjunto de registros y, a continuación, llame a la función miembro **Open**, pasando la cadena SQL que corresponde al parámetro **lpszSQL**.  O bien, reemplace la cadena devuelta por la función miembro `GetDefaultSQL` en la clase.  
  
 Los siguientes ejemplos muestran el procedimiento para llamar a una consulta predefinida, denominada `Delinquent_Accts`, que toma un parámetro para un número de distrito de ventas.  Esta consulta devuelve tres columnas: `Acct_No`, `L_Name`, `Phone`.  Todas las columnas pertenecen a la tabla Customers.  
  
 El siguiente conjunto de registros especifica miembros de datos de campo para las columnas que devuelve la consulta, así como un parámetro para el número de distrito de ventas solicitado en tiempo de ejecución.  
  
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
  
 Esta declaración de clase se ajusta a lo que escribe el asistente, excepto por el miembro `m_lDistParam`, que se agrega manualmente.  Otros miembros no se muestran aquí.  
  
 El siguiente ejemplo muestra el código de inicialización de los miembros de datos del constructor `CDelinquents`.  
  
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
  
 Observe el código de inicialización de [m\_nFields](../Topic/CRecordset::m_nFields.md) y [m\_nParams](../Topic/CRecordset::m_nParams.md).  El asistente inicializa `m_nFields`; el usuario inicializa `m_nParams`.  
  
 El siguiente ejemplo muestra las funciones RFX de `CDelinquents::DoFieldExchange`:  
  
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
  
 Además de realizar las llamadas RFX de las tres columnas devueltas, este código administra el enlace del parámetro pasado en tiempo de ejecución.  Se pasa el parámetro como clave a la columna `Dist_No` \(número de distrito\).  
  
 El siguiente ejemplo enseña cómo configurar la cadena SQL y cómo utilizarla para abrir el conjunto de registros.  
  
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
  
 Este código crea una instantánea, le pasa un parámetro obtenido previamente del usuario y llama a la consulta predefinida.  Al ejecutarse la consulta, devuelve los registros del distrito de ventas especificado.  Cada registro contiene las columnas del número de cuenta, los apellidos y el número de teléfono del cliente.  
  
> [!TIP]
>  Puede ser conveniente controlar el valor devuelto \(parámetro de salida\) por un procedimiento almacenado.  Para obtener más información y un ejemplo, vea [CFieldExchange::SetFieldType](../Topic/CFieldExchange::SetFieldType.md).  
  
## Vea también  
 [Conjunto de registros \(ODBC\)](../../data/odbc/recordset-odbc.md)   
 [Conjunto de registros: Volver a consultar un conjunto de registros \(ODBC\)](../../data/odbc/recordset-requerying-a-recordset-odbc.md)   
 [Conjunto de registros: Declarar una clase para una tabla \(ODBC\)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)   
 [Conjunto de registros: Realizar una combinación \(ODBC\)](../../data/odbc/recordset-performing-a-join-odbc.md)