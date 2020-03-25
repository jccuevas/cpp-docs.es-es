---
title: 'Conjunto de registros: Parametrizar un conjunto de registros (ODBC)'
ms.date: 05/09/2019
helpviewer_keywords:
- parameterizing recordsets
- ODBC recordsets, parameterizing
- recordsets, parameterizing
- passing parameters, to queries at runtime
ms.assetid: 7d1dfeb6-5ee0-45e2-aacc-63bc52a465cd
ms.openlocfilehash: ec4198c283700daa2e02e2507b9874eaf02858e9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212815"
---
# <a name="recordset-parameterizing-a-recordset-odbc"></a>Conjunto de registros: Parametrizar un conjunto de registros (ODBC)

Este tema es aplicable a las clases ODBC de MFC.

En ocasiones le interesa poder seleccionar registros en tiempo de ejecución mediante el uso de la información que ha calculado o que ha obtenido del usuario final. Los parámetros del conjunto de registros le permiten lograr ese objetivo.

En este tema se explica:

- [El propósito de un conjunto de registros parametrizado](#_core_parameterized_recordsets).

- [Cuándo y por qué puede interesarle parametrizar un conjunto de registros](#_core_when_to_use_parameters).

- [Cómo declarar miembros de datos de parámetros en la clase de conjunto de registros](#_core_parameterizing_your_recordset_class).

- [Cómo pasar información de parámetros a un objeto de conjunto de registros en tiempo de ejecución](#_core_passing_parameter_values_at_run_time).

##  <a name="parameterized-recordsets"></a><a name="_core_parameterized_recordsets"></a> Conjuntos de registros parametrizados

Un conjunto de registros parametrizado permite pasar información de parámetros en tiempo de ejecución. Esto tiene dos efectos de gran valor:

- La velocidad de ejecución podría mejorar.

- Permite crear una consulta en tiempo de ejecución, basada en información que no está disponible para usted en tiempo de diseño (por ejemplo, información obtenida del usuario o calculada en tiempo de ejecución).

Cuando llame a `Open` para ejecutar la consulta, el conjunto de registros usa la información de parámetros para completar la instrucción **SQL SELECT**. Se puede parametrizar cualquier conjunto de registros.

##  <a name="when-to-use-parameters"></a><a name="_core_when_to_use_parameters"></a> Cuándo se deben usar parámetros

Entre los usos más habituales de los parámetros se incluyen los siguientes:

- Pasar argumentos en tiempo de ejecución a una consulta predefinida.

   Para pasar parámetros a un procedimiento almacenado, debe especificar una instrucción completa **CALL** de ODBC personalizada (con marcadores de posición de parámetro) cuando llame a `Open` y reemplazar la instrucción SQL predeterminada del conjunto de registros. Para obtener más información, vea [CRecordset:: Open](../../mfc/reference/crecordset-class.md#open) en la referencia de la *biblioteca de clases* y [SQL: personalizar la instrucción SQL del conjunto de registros (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md) y el [conjunto de registros: declarar una clase para una consulta predefinida (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md).

- Realizar eficazmente un gran número de nuevas consultas con diferente información de parámetros.

   Por ejemplo, cada vez que el usuario final busque información sobre un alumno específico en la base de datos de registro de alumnos, usted puede especificar el nombre o el identificador del alumno como un parámetro obtenido del usuario. Después, cuando llame a la función miembro `Requery` del conjunto de registros, la consulta solo seleccionará el registro de ese alumno.

   La cadena de filtro del conjunto de registros, almacenada en `m_strFilter`, podría tener un aspecto parecido a este:

    ```cpp
    "StudentID = ?"
    ```

   Supongamos que obtiene el identificador del alumno en la variable `strInputID`. Al establecer un parámetro en `strInputID` (por ejemplo, el identificador de alumno 100), el valor de la variable se enlaza al marcador de posición del parámetro representado por el símbolo "?" en la cadena de filtro.

   Asigne el valor del parámetro de la manera siguiente:

    ```cpp
    strInputID = "100";
    ...
    m_strParam = strInputID;
    ```

   No conviene establecer una cadena de filtro de esta manera:

    ```cpp
    m_strFilter = "StudentID = 100";   // 100 is incorrectly quoted
                                       // for some drivers
    ```

   Para obtener una explicación de cómo usar las comillas correctamente para las cadenas de filtro, vea conjunto de registros [: filtrar registros (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md).

   El valor del parámetro es distinto cada vez que vuelve a consultar el conjunto de registros para un nuevo identificador de alumno.

   > [!TIP]
   > Es mucho más eficaz usar un parámetro que simplemente un filtro. Para un conjunto de registros parametrizado, la base de datos debe procesar una instrucción **SELECT** de SQL una sola vez. Para un conjunto de registros filtrado sin parámetros, la instrucción **SELECT** debe procesarse cada vez que vuelva a realizar una consulta con `Requery` con un nuevo valor de filtro.

Para obtener más información sobre los filtros, vea conjunto de registros [: filtrar registros (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md).

##  <a name="parameterizing-your-recordset-class"></a><a name="_core_parameterizing_your_recordset_class"></a> Parametrización de la clase de conjunto de registros

> [!NOTE]
> Esta sección se aplica a objetos derivados de `CRecordset` donde no se haya implementado la obtención masiva de filas. Si usa la obtención masiva de filas, la implementación de parámetros es un proceso similar. Para obtener más información, vea [conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Antes de crear la clase de conjunto de registros, determine qué parámetros necesita, cuáles son sus tipos de datos y cómo los usa el conjunto de registros.

#### <a name="to-parameterize-a-recordset-class"></a>Parametrización de una clase de conjunto de registros

> [!NOTE]
> El Asistente para consumidores ODBC de MFC no está disponible en Visual Studio 2019 ni en versiones posteriores. Aun así, puede crear esta funcionalidad manualmente.

1. Ejecute el [Asistente para consumidores ODBC MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md) desde **Agregar clase** para crear la clase.

1. Especifique los miembros de datos de campo para las columnas del conjunto de registros.

1. Después de que el asistente escriba la clase en un archivo del proyecto, vaya al archivo .h y agregue manualmente uno o más miembros de datos de parámetros a la declaración de clase. La adición podría tener un aspecto parecido al ejemplo siguiente, como parte de una clase de instantánea diseñada para responder a la consulta "¿Qué alumnos están en el último curso?".

    ```cpp
    class CStudentSet : public CRecordset
    {
    // Field/Param Data
        CString m_strFirstName;
        CString m_strLastName;
        CString m_strStudentID;
        CString m_strGradYear;

        CString m_strGradYrParam;
    };
    ```

   Agregue los miembros de datos de parámetros después de los miembros de datos de campo generados por el asistente. La convención es anexar la palabra "Param" al nombre de cada parámetro definido por el usuario.

1. Modifique la definición de la función miembro [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) en el archivo. cpp. Agregue una llamada de función de RFX para cada miembro de datos de parámetros que haya agregado a la clase. Para obtener información sobre cómo escribir las funciones de RFX, consulte [intercambio de campos de registros:](../../data/odbc/record-field-exchange-how-rfx-works.md)funcionamiento de RFX. Preceda las llamadas a RFX para los parámetros de una sola llamada a:

    ```cpp
    pFX->SetFieldType( CFieldExchange::param );
    // RFX calls for parameter data members
    ```

1. En el constructor de la clase de conjunto de registros, aumente el número de parámetros, `m_nParams`.

   Para obtener más información, vea [intercambio de campos de registros: trabajar con el código del asistente](../../data/odbc/record-field-exchange-working-with-the-wizard-code.md).

1. Al escribir el código que crea un objeto de conjunto de registros de esta clase, coloque un símbolo "?" (signo de interrogación) en todos los lugares de las cadenas de la instrucción SQL en los que se deba reemplazar un parámetro.

   En tiempo de ejecución, los valores de parámetro se pase rellenarán en orden los marcadores de posición "?". El primer miembro de datos de parámetros establecido después de la llamada a [SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype) reemplazará el primer símbolo "?"de la cadena SQL, el segundo miembro de datos de parámetros reemplazará el segundo símbolo "?", y así sucesivamente.

> [!NOTE]
> El orden de los parámetros es importante, ya que el orden de las llamadas a RFX para los parámetros de la función `DoFieldExchange` debe coincidir con el orden de los marcadores de posición de parámetros de la cadena SQL.

> [!TIP]
> La cadena con la que probablemente trabajará es aquella que especifique (si lo hace) para el miembro de datos [m_strFilter](../../mfc/reference/crecordset-class.md#m_strfilter) de la clase, pero algunos controladores ODBC podrían admitir parámetros en otras cláusulas SQL.

##  <a name="passing-parameter-values-at-run-time"></a><a name="_core_passing_parameter_values_at_run_time"></a> Cómo pasar valores de parámetro en tiempo de ejecución

Debe especificar los valores de parámetro antes de llamar a `Open` (para un nuevo objeto de conjunto de registros) o `Requery` (para uno ya existente).

#### <a name="to-pass-parameter-values-to-a-recordset-object-at-run-time"></a>Procedimiento para pasar valores de parámetro a un objeto de conjunto de registros en tiempo de ejecución

1. Construya el objeto de conjunto de registros.

1. Prepare una o varias cadenas, como la cadena `m_strFilter`, que contengan la instrucción SQL o partes de ella. Coloque marcadores de posición "?" en los que irá la información de los parámetros.

1. Asigne un valor de parámetro en tiempo de ejecución a cada miembro de datos de parámetros del objeto.

1. Llame a la función miembro `Open` (o `Requery`, para un conjunto de registros existente).

Por ejemplo, suponga que quiere especificar una cadena de filtro para el conjunto de registros mediante el uso de la información obtenida en tiempo de ejecución. Imagine que previamente construyó un conjunto de registros de la clase `CStudentSet`, denominado `rsStudents`, y que ahora quiere volver a consultarlo para encontrar determinada información sobre los alumnos.

```cpp
// Set up a filter string with
// parameter placeholders
rsStudents.m_strFilter = "GradYear <= ?";

// Obtain or calculate parameter values
// to pass--simply assigned here
CString strGradYear = GetCurrentAcademicYear( );

// Assign the values to parameter data members
rsStudents.m_strGradYrParam = strGradYear;

// Run the query
if( !rsStudents.Requery( ) )
    return FALSE;
```

El conjunto de registros contiene registros para aquellos alumnos cuyos registros cumplan las condiciones especificadas por el filtro, que se construyó a partir de parámetros en tiempo de ejecución. En este caso, el conjunto de registros contiene registros para todos los alumnos del último curso.

> [!NOTE]
>  Si es necesario, puede establecer el valor de un miembro de datos de parámetros en null mediante [SetParamNull](../../mfc/reference/crecordset-class.md#setparamnull). Del mismo modo, puede comprobar si un miembro de datos de parámetros es null mediante [IsFieldNull](../../mfc/reference/crecordset-class.md#isfieldnull).

## <a name="see-also"></a>Consulte también

[Conjunto de registros (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Conjunto de registros: Agregar, actualizar y eliminar registros (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)<br/>
[Conjunto de registros: Cómo se seleccionan los registros (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)
