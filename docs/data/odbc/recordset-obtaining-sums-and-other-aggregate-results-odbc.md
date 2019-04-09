---
title: 'Conjunto de registros: Obtener cálculos SUM y otros resultados agregados (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- SQL, retrieving aggregate values from recordsets
- recordsets, retrieving SQL aggregate values
- retrieving SQL aggregate values from recordsets
- ODBC recordsets, retrieving SQL aggregate values
- SQL aggregate values
- SQL Server projects, retrieving aggregate values from recordsets
- SQL aggregate values, retrieving from recordsets
ms.assetid: 94500662-22a4-443e-82d7-acbe6eca447b
ms.openlocfilehash: e10f2e1574dae234d98d210784d4a8ddef3bb57e
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59025327"
---
# <a name="recordset-obtaining-sums-and-other-aggregate-results-odbc"></a>Conjunto de registros: Obtener cálculos SUM y otros resultados agregados (ODBC)

Este tema es aplicable a las clases ODBC de MFC.

En este tema se explica cómo obtener resultados agregados mediante el siguiente [SQL](../../data/odbc/sql.md) palabras clave:

- **SUMA** calcula el total de los valores de una columna con un tipo de datos numéricos.

- **MIN** extrae el valor más pequeño en una columna con un tipo de datos numérico.

- **MAX** extrae el valor más grande en una columna con un tipo de datos numérico.

- **AVG** calcula un valor medio de todos los valores en una columna con un tipo de datos numéricos.

- **RECUENTO** cuenta el número de registros en una columna de cualquier tipo de datos.

Utilice estas funciones SQL para obtener información estadística acerca de los registros en un origen de datos, en lugar de extraer los registros del origen de datos. El conjunto de registros que se crea normalmente consta de un solo registro (si todas las columnas son agregados) que contiene un valor. (Puede haber más de un registro si ha usado un **GROUP BY** cláusula.) Este valor es el resultado del cálculo o extracción realizados por la función de SQL.

> [!TIP]
>  Para agregar una instancia de SQL **GROUP BY** cláusula (y posiblemente un **HAVING** cláusula) a la instrucción SQL, debe anexarlo al final de `m_strFilter`. Por ejemplo:

```
m_strFilter = "sales > 10 GROUP BY SALESPERSON_ID";
```

Puede limitar el número de registros que se utiliza para obtener resultados agregados mediante el filtrado y ordenación de las columnas.

> [!CAUTION]
>  Algunos operadores de agregación devuelven un tipo de datos diferentes de las columnas que están agregando.

- **SUMA** y **AVG** podría devolver el siguiente tipo de datos mayor (por ejemplo, una llamada con `int` devuelve **largo** o **doble**).

- **RECUENTO de** normalmente devuelve **largo** independientemente del tipo de columna de destino.

- **MAX** y **MIN** devuelven el mismo tipo de datos como las columnas que calculan.

     Por ejemplo, el **Agregar clase** asistente crea `long` `m_lSales` dar cabida a una columna de ventas, pero se debe reemplazar esto con un `double m_dblSumSales` miembro de datos para acomodar el resultado agregado. Vea el ejemplo siguiente.

#### <a name="to-obtain-an-aggregate-result-for-a-recordset"></a>Para obtener un resultado agregado para un conjunto de registros

1. Crear un conjunto de registros como se describe en [agregar un consumidor ODBC de MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md) que contiene las columnas que desea obtener resultados agregados.

1. Modificar el [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) función para el conjunto de registros. Reemplace la cadena que representa el nombre de columna (el segundo argumento de la [RFX](../../data/odbc/record-field-exchange-using-rfx.md) llamadas a funciones) con una cadena que representa la función de agregación en la columna. Por ejemplo, reemplace:

    ```
    RFX_Long(pFX, "Sales", m_lSales);
    ```

     Por:

    ```
    RFX_Double(pFX, "Sum(Sales)", m_dblSumSales)
    ```

1. Abra el conjunto de registros. El resultado de la operación de agregación se deja en `m_dblSumSales`.

> [!NOTE]
>  El asistente asigna los nombres de miembro de datos sin prefijos de notación húngara. Por ejemplo, el asistente produciría `m_Sales` para una columna de ventas, en lugar de `m_lSales` nombre usado anteriormente en la ilustración.

Si usas un [CRecordView](../../mfc/reference/crecordview-class.md) clase para ver los datos, tendrá que cambiar la llamada de función DDX para mostrar el nuevo valor de miembro de datos; en este caso, cambiarlo de:

```
DDX_FieldText(pDX, IDC_SUMSALES, m_pSet->m_lSales, m_pSet);
```

A:

```
DDX_FieldText(pDX, IDC_SUMSALES, m_pSet->m_dblSumSales, m_pSet);
```

## <a name="see-also"></a>Vea también

[Conjunto de registros (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Conjunto de registros: ¿Cómo se seleccionan los registros (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)