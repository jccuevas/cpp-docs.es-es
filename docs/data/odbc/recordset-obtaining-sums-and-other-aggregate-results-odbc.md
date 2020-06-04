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
ms.openlocfilehash: 9ebbe78191d0c4140baf3557637ba2103886577d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368653"
---
# <a name="recordset-obtaining-sums-and-other-aggregate-results-odbc"></a>Conjunto de registros: Obtener cálculos SUM y otros resultados agregados (ODBC)

> [!NOTE]
> El Asistente para consumidores ODBC MFC no está disponible en Visual Studio 2019 ni en versiones posteriores. Aun así, puede crear un consumidor manualmente.

Este tema es aplicable a las clases ODBC de MFC.

En este tema se explica cómo obtener resultados agregados mediante las siguientes palabras clave de [SQL](../../data/odbc/sql.md):

- **SUMA** calcula el total de los valores de una columna con un tipo de datos numérico.

- **MIN** extrae el valor menor de una columna con un tipo de datos numérico.

- **MAX** extrae el valor mayor de una columna con un tipo de datos numérico.

- **AVG** calcula la media de todos los valores de una columna con un tipo de datos numérico.

- **COUNT** cuenta el número de registros de una columna de cualquier tipo de datos.

Puede usar estas funciones SQL para obtener información estadística sobre los registros de un origen de datos, en lugar de extraer los registros de este. El conjunto de registros que se crea suele constar de un solo registro (si todas las columnas son agregados) que contiene un valor. (Puede haber más de un registro si usó una cláusula **GROUP BY.)** Este valor es el resultado del cálculo o extracción realizado por la función SQL.

> [!TIP]
> Para agregar una cláusula **GROUP BY** de SQL (y posiblemente una cláusula **HAVING**) a la instrucción SQL, debe anexarla al final de `m_strFilter`. Por ejemplo:

```
m_strFilter = "sales > 10 GROUP BY SALESPERSON_ID";
```

Puede limitar el número de registros que usa para obtener resultados agregados mediante el filtrado y la ordenación de las columnas.

> [!CAUTION]
> Algunos operadores de agregación devuelven un tipo de datos diferente de las columnas que están agregando.

- **SUM** y **AVG** podrían devolver el siguiente tipo de datos mayor (por ejemplo, una llamada con `int` devuelve **LONG** o **double**).

- **COUNT** suele devolver **LONG**, independientemente del tipo de columna de destino.

- **MAX** y **MIN** devuelven el mismo tipo de datos que el de las columnas que calculan.

     Por ejemplo, el Asistente para **agregar clase** crea `long` `m_lSales` para alojar una columna Sales, pero esto se debe reemplazar por un miembro de datos `double m_dblSumSales` para alojar el resultado agregado. Consulte el ejemplo siguiente.

#### <a name="to-obtain-an-aggregate-result-for-a-recordset"></a>Para obtener un resultado agregado para un conjunto de registros

1. Cree un conjunto de registros, como se describe en [Agregar un consumidor ODBC de MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md), que contenga las columnas de las que quiere obtener resultados agregados.

1. Modifique la función [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) para el conjunto de registros. Reemplace la cadena que representa el nombre de columna (el segundo argumento de las llamadas de función [RFX](../../data/odbc/record-field-exchange-using-rfx.md)) por una cadena que represente la función de agregación en la columna. Por ejemplo, reemplace:

    ```
    RFX_Long(pFX, "Sales", m_lSales);
    ```

     por:

    ```
    RFX_Double(pFX, "Sum(Sales)", m_dblSumSales)
    ```

1. Abra el conjunto de registros. El resultado de la operación de agregación se deja en `m_dblSumSales`.

> [!NOTE]
> El asistente asigna los nombres de los miembros de datos sin prefijos de notación húngara. Por ejemplo, el asistente produciría `m_Sales` para una columna Sales, en lugar del nombre `m_lSales` usado anteriormente como ejemplo.

Si usa una clase [CRecordView](../../mfc/reference/crecordview-class.md) para ver los datos, tendrá que cambiar la llamada de función DDX para mostrar el nuevo valor del miembro de datos. En este caso, cámbielo de:

```
DDX_FieldText(pDX, IDC_SUMSALES, m_pSet->m_lSales, m_pSet);
```

Por:

```
DDX_FieldText(pDX, IDC_SUMSALES, m_pSet->m_dblSumSales, m_pSet);
```

## <a name="see-also"></a>Consulte también

[Conjunto de registros (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Conjunto de registros: Cómo se seleccionan los registros (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)
