---
title: "Conjunto de registros: Obtener cálculos SUM y otros resultados agregados (ODBC) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- SQL, retrieving aggregate values from recordsets
- recordsets, retrieving SQL aggregate values
- retrieving SQL aggregate values from recordsets
- ODBC recordsets, retrieving SQL aggregate values
- SQL aggregate values
- SQL Server projects, retrieving aggregate values from recordsets
- SQL aggregate values, retrieving from recordsets
ms.assetid: 94500662-22a4-443e-82d7-acbe6eca447b
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 4753193789c95b726a8770cef9a153b041fa762c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="recordset-obtaining-sums-and-other-aggregate-results-odbc"></a>Conjunto de registros: Obtener cálculos SUM y otros resultados agregados (ODBC)
Este tema es aplicable a las clases ODBC de MFC.  
  
 Este tema explica cómo obtener resultados agregados mediante las siguientes [SQL](../../data/odbc/sql.md) palabras clave:  
  
-   **SUMA** calcula el total de los valores de una columna con un tipo de datos numéricos.  
  
-   **MIN** extrae el valor más pequeño de una columna con un tipo de datos numéricos.  
  
-   **MAX** extrae el valor más grande en una columna con un tipo de datos numéricos.  
  
-   **AVG** calcula un valor medio de todos los valores en una columna con un tipo de datos numéricos.  
  
-   **RECUENTO de** cuenta el número de registros en una columna de cualquier tipo de datos.  
  
 Use estas funciones SQL para obtener información estadística acerca de los registros en un origen de datos, en lugar de extraer registros del origen de datos. El conjunto de registros que se crea normalmente consta de un solo registro (si todas las columnas son agregados) que contiene un valor. (Puede haber más de un registro si ha usado un **GROUP BY** cláusula.) Este valor es el resultado del cálculo o extracción realizados por la función SQL.  
  
> [!TIP]
>  Para agregar una instancia de SQL **GROUP BY** cláusula (y posiblemente un **HAVING** cláusula) a la instrucción SQL, anexar al final de **m_strFilter**. Por ejemplo:  
  
```  
m_strFilter = "sales > 10 GROUP BY SALESPERSON_ID";  
```  
  
 Puede limitar el número de registros que se utiliza para obtener resultados agregados filtrando y ordenando las columnas.  
  
> [!CAUTION]
>  Algunos operadores de agregación devuelven un tipo de datos diferentes de las columnas que están agregando.  
  
-   **SUMA** y **AVG** podría devolver el siguiente tipo de datos mayor (por ejemplo, al llamar a con `int` devuelve **largo** o **doble**).  
  
-   **RECUENTO de** normalmente devuelve **largo** independientemente del tipo de columna de destino.  
  
-   **MAX** y **MIN** devuelven el mismo tipo de datos como las columnas que calculan.  
  
     Por ejemplo, el **Agregar clase** asistente crea `long` `m_lSales` dar cabida a una columna de ventas, pero también necesite reemplazar esto con un `double m_dblSumSales` miembro de datos para acomodar el resultado agregado. Vea el ejemplo siguiente.  
  
#### <a name="to-obtain-an-aggregate-result-for-a-recordset"></a>Para obtener un resultado agregado para un conjunto de registros  
  
1.  Crear un conjunto de registros como se describe en [agregar un consumidor ODBC de MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md) que contiene las columnas desde el que va a obtener un resultado agregado.  
  
2.  Modificar el [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) función para el conjunto de registros. Reemplace la cadena que representa el nombre de columna (el segundo argumento de la [RFX](../../data/odbc/record-field-exchange-using-rfx.md) llamadas a funciones) con una cadena que representa la función de agregación en la columna. Por ejemplo, reemplace:  
  
    ```  
    RFX_Long(pFX, "Sales", m_lSales);  
    ```  
  
     Con:  
  
    ```  
    RFX_Double(pFX, "Sum(Sales)", m_dblSumSales)  
    ```  
  
3.  Abra el conjunto de registros. El resultado de la operación de agregación se deja en `m_dblSumSales`.  
  
> [!NOTE]
>  El asistente asigna los nombres de miembro de datos sin prefijos de notación húngara. Por ejemplo, el asistente produciría `m_Sales` para una columna Sales, en lugar de la `m_lSales` nombre usado anteriormente en la ilustración.  
  
 Si usas un [CRecordView](../../mfc/reference/crecordview-class.md) clase para ver los datos, tendrá que cambiar la llamada de función DDX para mostrar el nuevo valor de miembro de datos; en este caso, cambiarlo de:  
  
```  
DDX_FieldText(pDX, IDC_SUMSALES, m_pSet->m_lSales, m_pSet);  
```  
  
 A:  
  
```  
DDX_FieldText(pDX, IDC_SUMSALES, m_pSet->m_dblSumSales, m_pSet);  
```  
  
## <a name="see-also"></a>Vea también  
 [Conjunto de registros (ODBC)](../../data/odbc/recordset-odbc.md)   
 [Conjunto de registros: Cómo se seleccionan los registros (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)