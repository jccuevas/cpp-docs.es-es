---
title: "Conjunto de registros: Parametrizar un conjunto de registros (ODBC) | Microsoft Docs"
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
  - "conjuntos de registros ODBC, parametrizar"
  - "parametrizar conjuntos de registros"
  - "pasar parámetros, a consultas en tiempo de ejecución"
  - "conjuntos de registros, parametrizar"
ms.assetid: 7d1dfeb6-5ee0-45e2-aacc-63bc52a465cd
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# Conjunto de registros: Parametrizar un conjunto de registros (ODBC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Este tema es aplicable a las clases ODBC de MFC.  
  
 A veces es conveniente poder seleccionar registros en tiempo de ejecución, usando información calculada u obtenida del usuario final.  Los parámetros de conjunto de registros permiten alcanzar este objetivo.  
  
 En este tema se explica:  
  
-   [El propósito de un conjunto de registros parametrizado](#_core_parameterized_recordsets).  
  
-   [Cuándo y por qué es conveniente parametrizar un conjunto de registros](#_core_when_to_use_parameters).  
  
-   [Cómo declarar miembros de datos de parámetro en un conjunto de registros](#_core_parameterizing_your_recordset_class).  
  
-   [Cómo pasar información de parámetros a un objeto de conjunto de registros en tiempo de ejecución](#_core_passing_parameter_values_at_run_time).  
  
##  <a name="_core_parameterized_recordsets"></a> Conjuntos de registros parametrizados  
 Los conjuntos de registros parametrizados permiten pasar información de parámetros en tiempo de ejecución.  De esta forma, se obtienen dos efectos de gran valor:  
  
-   Se puede conseguir una mayor velocidad de ejecución.  
  
-   Permite generar una consulta en tiempo de ejecución, basada en información no disponible en tiempo de diseño, como la información obtenida del usuario o calculada en tiempo de ejecución.  
  
 Al llamar a **Open** para ejecutar la consulta, el conjunto de registros usa la información de parámetros para completar su instrucción **SQL SELECT**.  Se puede parametrizar cualquier conjunto de registros.  
  
##  <a name="_core_when_to_use_parameters"></a> Cuándo utilizar parámetros  
 Los usos más habituales para los parámetros son:  
  
-   Pasar argumentos en tiempo de ejecución a una consulta predefinida.  
  
     Para pasar parámetros a un procedimiento almacenado, se debe especificar una instrucción ODBC **CALL** completa y personalizada \(con marcadores de posición de parámetro\) al llamar a **Open**, reemplazando la instrucción SQL predeterminada del conjunto de registros.  Para obtener más información, vea [CRecordset::Open](../Topic/CRecordset::Open.md) en la *Referencia de la biblioteca de clases* y [SQL: Personalizar la instrucción SQL del conjunto de registros \(ODBC\)](../../data/odbc/sql-customizing-your-recordset’s-sql-statement-odbc.md) y [Conjunto de registros: Declarar una clase para una consulta predefinida \(ODBC\)](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md).  
  
-   Realizar de manera eficiente nuevas consultas con diferentes parámetros.  
  
     Por ejemplo, cada vez que un usuario final busca información acerca de un estudiante concreto en la base de datos de registro de estudiantes, se puede especificar el nombre o identificador del estudiante como parámetro obtenido del usuario.  Así pues, al llamar a la función miembro **Requery** del conjunto de registros, la consulta selecciona sólo el registro de ese estudiante.  
  
     La cadena de filtro del conjunto de registros, almacenada en **m\_strFilter**, podría tener este aspecto:  
  
    ```  
    "StudentID = ?"  
    ```  
  
     Suponga que obtiene el identificador de estudiante en la variable `strInputID`.  Al establecer un parámetro para `strInputID` \(por ejemplo, el identificador de estudiante 100\), el valor de la variable queda enlazado con el marcador de posición del parámetro representado por "?" en la cadena de filtro.  
  
     Asigne el valor de parámetro del siguiente modo:  
  
    ```  
    strInputID = "100";  
    ...  
    m_strParam = strInputID;  
    ```  
  
     No es conveniente que prepare ninguna cadena de filtro de esta manera:  
  
    ```  
    m_strFilter = "StudentID = 100";   // 100 is incorrectly quoted  
                                       // for some drivers  
    ```  
  
     Para consultar el uso correcto de las comillas en las cadenas de filtro, vea [Conjunto de registros: Filtrar registros \(ODBC\)](../../data/odbc/recordset-filtering-records-odbc.md).  
  
     El valor de parámetro es diferente cada vez que se realiza una nueva consulta al conjunto de registros con un nuevo identificador de estudiante.  
  
    > [!TIP]
    >  Usar un parámetro es más eficaz que usar solamente un filtro.  En un conjunto de registros parametrizado, la base de datos debe procesar la instrucción SQL **SELECT** sólo una vez.  En un conjunto de registros filtrado sin parámetros, la instrucción **SELECT** debe procesarse cada vez que se llame a **Requery** utilizando un nuevo valor de filtro.  
  
 Para obtener más información acerca de los filtros, vea [Conjunto de registros: Filtrar registros \(ODBC\)](../../data/odbc/recordset-filtering-records-odbc.md).  
  
##  <a name="_core_parameterizing_your_recordset_class"></a> Parametrizar la clase de conjunto de registros  
  
> [!NOTE]
>  Esta sección se aplica a los objetos derivados de `CRecordset` donde no se haya implementado la obtención masiva de filas.  Si se está usando la obtención masiva de filas, implementar los parámetros es un proceso similar.  Para obtener más información, vea [Conjunto de registros: Obtener registros de forma masiva \(ODBC\)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Antes de crear la clase de conjunto de registros, determine qué parámetros necesita, sus tipos de datos y cómo los utiliza el conjunto de registros.  
  
#### Para parametrizar una clase de conjunto de registros  
  
1.  Ejecute el [Asistente para consumidores ODBC de MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md) utilizando **Agregar clase** para crear la clase.  
  
2.  Especifique los miembros de datos de campo para las columnas del conjunto de registros.  
  
3.  Después de que el asistente escriba la clase en un archivo del proyecto, vaya al archivo .h y agregue manualmente uno o más miembros de datos de parámetro a la declaración de clase.  Esta acción puede tener el siguiente aspecto, como parte de una clase de instantánea diseñada para responder a la consulta "¿Qué estudiantes hay inscritos en el último curso?".  
  
    ```  
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
  
     Agregue los miembros de datos de parámetro después de que el asistente genere los miembros de datos de campo.  La convención es anexar la palabra "Param" a cada nombre de parámetro definido por el usuario.  
  
4.  Modifique la definición de la función miembro [DoFieldExchange](../Topic/CRecordset::DoFieldExchange.md) en el archivo .cpp.  Agregue una llamada de función RFX para cada miembro de datos de parámetro agregado a la clase.  Para obtener información sobre cómo escribir sus propias funciones RFX, vea [Intercambio de campos de registros: Funcionamiento de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).  Anteponga a las llamadas RFX correspondientes a los parámetros una única llamada a:  
  
    ```  
    pFX->SetFieldType( CFieldExchange::param );  
    // RFX calls for parameter data members  
    ```  
  
5.  En el constructor de la clase de conjunto de registros, aumente el número de parámetros, `m_nParams`.  
  
     Para obtener información, vea [Intercambio de campos de registros: trabajar con el código de asistente](../../data/odbc/record-field-exchange-working-with-the-wizard-code.md).  
  
6.  Cuando escriba el código que crea un objeto de conjunto de registros de esta clase, coloque un símbolo "?" \(signo de interrogación\) en cada lugar de las cadenas de instrucciones SQL donde se vaya a reemplazar un parámetro.  
  
     En tiempo de ejecución, los marcadores de posición "?" se rellenan, en orden, por los valores de parámetro que se pasan.  El primer miembro de datos de parámetro establecido después de la llamada a [SetFieldType](../Topic/CFieldExchange::SetFieldType.md) reemplaza al primer símbolo "?" de la cadena SQL, el segundo miembro de datos de parámetro reemplaza al segundo "?" y así sucesivamente.  
  
> [!NOTE]
>  El orden de parámetros es importante: el orden de las llamadas RFX en los parámetros de la función `DoFieldExchange` debe coincidir con el orden de los marcadores de posición de parámetro en la cadena SQL.  
  
> [!TIP]
>  La cadena con la que es probable que trabaje es la especificada \(si la hay\) para el miembro de datos [m\_strFilter](../Topic/CRecordset::m_strFilter.md) de la clase, pero puede que algunos controladores ODBC permitan parámetros en otras cláusulas SQL.  
  
##  <a name="_core_passing_parameter_values_at_run_time"></a> Pasar valores de parámetro en tiempo de ejecución  
 Se deben especificar valores de parámetro antes de llamar a **Open** \(para un nuevo objeto de conjunto de registros\) o a **Requery** \(para uno existente\).  
  
#### Para pasar valores de parámetro a un objeto de conjunto de registros en tiempo de ejecución  
  
1.  Cree el objeto de conjunto de registros.  
  
2.  Prepare una cadena o varias, como la cadena **m\_strFilter**, que contengan la instrucción SQL, o parte de ella.  Coloque marcadores de posición "?" donde vaya a ir la información de parámetros.  
  
3.  Asigne un valor de parámetro en tiempo de ejecución a todos los miembros de datos de parámetro del objeto.  
  
4.  Llame a la función miembro **Open** \(o a **Requery**, para un conjunto de registros existente\).  
  
 Por ejemplo, supongamos que desea especificar una cadena de filtro para el conjunto de registros usando información obtenida en tiempo de ejecución.  Supongamos, igualmente, que se creó anteriormente un conjunto de registros de la clase `CStudentSet`, denominado `rsStudent`, y que ahora desea volver a consultarlo para obtener un tipo determinado de información de estudiantes.  
  
```  
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
  
 El conjunto de registros contiene registros para aquellos estudiantes cuyos registros cumplen las condiciones especificadas por el filtro que se creó a partir de parámetros en tiempo de ejecución.  En este caso, el conjunto de registros contiene registros para todos los estudiantes matriculados en el último año de estudios.  
  
> [!NOTE]
>  Si es necesario, se puede establecer el valor de un miembro de datos de parámetro en Null mediante [SetParamNull](../Topic/CRecordset::SetParamNull.md).  También se puede comprobar si un miembro de datos de parámetro es Null mediante [IsFieldNull](../Topic/CRecordset::IsFieldNull.md).  
  
## Vea también  
 [Conjunto de registros \(ODBC\)](../../data/odbc/recordset-odbc.md)   
 [Conjunto de registros: Agregar, actualizar y eliminar registros \(ODBC\)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)   
 [Conjunto de registros: Cómo se seleccionan los registros \(ODBC\)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)