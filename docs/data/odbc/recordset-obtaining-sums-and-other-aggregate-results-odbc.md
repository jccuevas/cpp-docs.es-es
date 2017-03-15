---
title: "Conjunto de registros: Obtener c&#225;lculos SUM y otros resultados agregados (ODBC) | Microsoft Docs"
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
  - "conjuntos de registros ODBC, recuperar valores de agregado de SQL"
  - "conjuntos de registros, recuperar valores de agregado de SQL"
  - "recuperar valores de agregado de SQL de conjuntos de registros"
  - "valores de agregado de SQL"
  - "valores de agregado de SQL, recuperar de conjuntos de registros"
  - "proyectos de SQL Server, recuperar valores de agregado de conjuntos de registros"
  - "SQL, recuperar valores de agregado de conjuntos de registros"
ms.assetid: 94500662-22a4-443e-82d7-acbe6eca447b
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Conjunto de registros: Obtener c&#225;lculos SUM y otros resultados agregados (ODBC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Este tema es aplicable a las clases ODBC de MFC.  
  
 Este tema explica cómo obtener resultados agregados mediante las siguientes palabras clave de [SQL](../../data/odbc/sql.md):  
  
-   **SUM** Calcula el total de los valores de una columna con un tipo de datos numérico.  
  
-   **MIN** Extrae el valor más pequeño de una columna con un tipo de datos numérico.  
  
-   **MAX** Extrae el valor más grande de una columna con un tipo de datos numérico.  
  
-   **AVG** Calcula el valor medio de todos los valores de una columna con un tipo de datos numérico.  
  
-   **COUNT** Cuenta el número de registros de una columna de cualquier tipo de datos.  
  
 Estas funciones SQL se utilizan para obtener información estadística sobre los registros de un origen de datos en lugar de extraerlos de éste.  El conjunto de registros creado suele estar compuesto por un solo registro \(si todas las columnas son agregadas\) que contiene un valor. \(Puede haber más de un registro si se utiliza una cláusula **GROUP BY**.\) Este valor es el resultado del cálculo o extracción realizados por la función SQL.  
  
> [!TIP]
>  Para agregar una cláusula SQL **GROUP BY** \(y posiblemente una cláusula **HAVING**\) a la instrucción SQL, anéxela al final de **m\_strFilter**.  Por ejemplo:  
  
```  
m_strFilter = "sales > 10 GROUP BY SALESPERSON_ID";  
```  
  
 Se puede limitar el número de registros utilizados para obtener resultados agregados filtrando y ordenando las columnas.  
  
> [!CAUTION]
>  Algunos operadores de agregación devuelven un tipo de datos diferente del de las columnas que están agregando.  
  
-   **SUM** y **AVG** pueden devolver el siguiente tipo de datos mayor \(por ejemplo, una llamada con un tipo `int` devuelve **LONG** o **double**\).  
  
-   **COUNT** suele devolver **LONG** sin tener en cuenta el tipo de la columna de destino.  
  
-   **MAX** y **MIN** devuelven el mismo tipo de datos que las columnas que calculan.  
  
     Por ejemplo, el asistente **Agregar clase** crea `long``m_lSales` para acomodar una columna Sales \(ventas\), pero debe reemplazarse con un miembro de datos `double m_dblSumSales` para acomodar el resultado agregado.  Vea el ejemplo siguiente.  
  
#### Para obtener un resultado agregado en un conjunto de registros  
  
1.  Cree un conjunto de registros según se describe en [Agregar un consumidor ODBC de MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md) que contenga las columnas de las cuales desea obtener un resultado agregado.  
  
2.  Modifique la función [DoFieldExchange](../Topic/CRecordset::DoFieldExchange.md) del conjunto de registros.  Reemplace la cadena que representa el nombre de columna \(el segundo argumento de las llamadas de función [RFX](../../data/odbc/record-field-exchange-using-rfx.md)\) por una cadena que represente la función de agregación en la columna.  Por ejemplo, reemplace:  
  
    ```  
    RFX_Long(pFX, "Sales", m_lSales);  
    ```  
  
     con:  
  
    ```  
    RFX_Double(pFX, "Sum(Sales)", m_dblSumSales)  
    ```  
  
3.  Abra el conjunto de registros.  El resultado de la operación de agregación aparece en `m_dblSumSales`.  
  
> [!NOTE]
>  El asistente asigna los nombres de miembros de datos sin prefijos de notación húngara.  Por ejemplo, el asistente produciría `m_Sales` para una columna Sales, en lugar del nombre `m_lSales` usado antes en la ilustración.  
  
 Si se está utilizando una clase [CRecordView](../../mfc/reference/crecordview-class.md) para ver los datos, se debe cambiar la llamada de función DDX para mostrar el nuevo valor de miembro de datos; en este caso, cambiarlo de:  
  
```  
DDX_FieldText(pDX, IDC_SUMSALES, m_pSet->m_lSales, m_pSet);  
```  
  
 Para:  
  
```  
DDX_FieldText(pDX, IDC_SUMSALES, m_pSet->m_dblSumSales, m_pSet);  
```  
  
## Vea también  
 [Conjunto de registros \(ODBC\)](../../data/odbc/recordset-odbc.md)   
 [Conjunto de registros: Cómo se seleccionan los registros \(ODBC\)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)