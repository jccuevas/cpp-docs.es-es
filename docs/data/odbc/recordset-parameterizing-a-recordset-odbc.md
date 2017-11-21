---
title: 'Conjunto de registros: Parametrizar un conjunto de registros (ODBC) | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- parameterizing recordsets
- ODBC recordsets, parameterizing
- recordsets, parameterizing
- passing parameters, to queries at runtime
ms.assetid: 7d1dfeb6-5ee0-45e2-aacc-63bc52a465cd
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e282bf795435d21264ff4ab62575b9315781a0e0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="recordset-parameterizing-a-recordset-odbc"></a>Conjunto de registros: Parametrizar un conjunto de registros (ODBC)
Este tema es aplicable a las clases ODBC de MFC.  
  
 A veces debe poder seleccionar registros en tiempo de ejecución, usando información calculada u obtenida del usuario final. Parámetros de conjunto de registros permiten realizar ese objetivo.  
  
 En este tema se explica:  
  
-   [El propósito de un conjunto de registros parametrizado](#_core_parameterized_recordsets).  
  
-   [Cuándo y por qué desea parametrizar un conjunto de registros](#_core_when_to_use_parameters).  
  
-   [Cómo declarar miembros de datos en la clase de conjunto de registros de parámetro](#_core_parameterizing_your_recordset_class).  
  
-   [Cómo pasar información de parámetros a un objeto de conjunto de registros en tiempo de ejecución](#_core_passing_parameter_values_at_run_time).  
  
##  <a name="_core_parameterized_recordsets"></a>Conjuntos de registros con parámetros  
 Un conjunto de registros con parámetros permite pasar información de parámetros en tiempo de ejecución. Esto tiene dos efectos de gran valor:  
  
-   Podría dar como resultado una mayor velocidad de ejecución.  
  
-   Le permite generar una consulta en tiempo de ejecución basada en información no disponible en tiempo de diseño, como la información obtenida del usuario o calculada en tiempo de ejecución.  
  
 Cuando se llama a **abiertos** para ejecutar la consulta, el conjunto de registros usa la información de parámetros para completar su **SQL SELECT** instrucción. Se puede parametrizar cualquier conjunto de registros.  
  
##  <a name="_core_when_to_use_parameters"></a>Cuándo utilizar parámetros  
 Entre los usos típicos de los parámetros se incluyen:  
  
-   Pasar argumentos de tiempo de ejecución para una consulta predefinida.  
  
     Para pasar parámetros a un procedimiento almacenado, debe especificar un ODBC personalizado completo **llamar a** instrucción, con marcadores de posición de parámetro: cuando se llama a **abiertos**, reemplazar la instrucción de SQL predeterminada del conjunto de registros. Para obtener más información, consulte [CRecordset:: Open](../../mfc/reference/crecordset-class.md#open) en el *Class Library Reference* y [SQL: SQL instrucción (ODBC de personalizar un conjunto de registros)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md) y [ Conjunto de registros: Declarar una clase para una consulta predefinida (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md).  

  
-   Realizar eficazmente nuevas consultas con información de parámetros diferentes.  
  
     Por ejemplo, cada vez que el usuario final busca información acerca de un estudiante concreto en la base de datos de registro de estudiantes, se puede especificar nombre o identificador del estudiante como un parámetro obtenido del usuario. A continuación, cuando se llama a su conjunto de registros **Requery** función de miembro, la consulta selecciona sólo el registro de ese estudiante.  
  
     Cadena de filtro del conjunto de registros, almacenada en **m_strFilter**, podría tener este aspecto:  
  
    ```  
    "StudentID = ?"  
    ```  
  
     Suponga que obtiene el identificador de estudiante en la variable `strInputID`. Al establecer un parámetro `strInputID` (por ejemplo, el identificador de estudiante 100), el valor de la variable se enlaza al marcador de posición del parámetro representado por el "?" en la cadena de filtro.  
  
     Asignar el valor del parámetro como sigue:  
  
    ```  
    strInputID = "100";  
    ...  
    m_strParam = strInputID;  
    ```  
  
     No se debería configurar una cadena de filtro de esta manera:  
  
    ```  
    m_strFilter = "StudentID = 100";   // 100 is incorrectly quoted  
                                       // for some drivers  
    ```  
  
     Para obtener una explicación de cómo usar comillas correctamente las cadenas de filtro, vea [conjunto de registros: filtrar registros (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md).  
  
     El valor del parámetro es distinto cada vez que consultar el conjunto de registros para un nuevo identificador de estudiante.  
  
    > [!TIP]
    >  Usar un parámetro es más eficaz que simplemente un filtro. Para un conjunto de registros con parámetros, la base de datos debe procesar una instancia de SQL **seleccione** instrucción una sola vez. Para un conjunto de registros filtrado sin parámetros, el **seleccione** instrucción debe procesarse cada vez que se **Requery** con un nuevo valor de filtro.  
  
 Para obtener más información acerca de los filtros, vea [conjunto de registros: filtrar registros (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md).  
  
##  <a name="_core_parameterizing_your_recordset_class"></a>Parametrizar la clase de conjunto de registros  
  
> [!NOTE]
>  En esta sección se aplica a objetos derivados de `CRecordset` qué masiva de filas no se ha implementado la obtención. Si utilizas una fila de forma masiva de filas, implementar los parámetros es un proceso similar. Para obtener más información, consulte [conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Antes de crear la clase de conjunto de registros, determine qué parámetros necesita, ¿cuáles son sus tipos de datos y cómo los utiliza el conjunto de registros.  
  
#### <a name="to-parameterize-a-recordset-class"></a>Para parametrizar una clase de conjunto de registros  
  
1.  Ejecute el [Asistente para consumidores ODBC de MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md) de **Agregar clase** para crear la clase.  
  
2.  Especifique a los miembros de datos de campo para las columnas del conjunto de registros.  
  
3.  Después de que el asistente escribe la clase en un archivo en el proyecto, vaya al archivo .h y agregue manualmente uno o más miembros de datos de parámetro a la declaración de clase. La adición podría ser similar al ejemplo siguiente, la parte de una clase de instantánea diseñada para responder a la consulta "¿Qué estudiantes hay en la clase senior?"  
  
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
  
     Agregue a los miembros de datos de parámetro después de los miembros de datos de campo generados por el asistente. La convención es anexar la palabra "Param" a cada nombre de parámetro definido por el usuario.  
  
4.  Modificar el [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) definición de función miembro en el archivo .cpp. Agregue una llamada de función RFX para cada miembro de datos de parámetro agregado a la clase. Para obtener información sobre cómo escribir sus propias funciones RFX, consulte [intercambio de campos de registros: funcionamiento de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md). Preceden a las llamadas a RFX para los parámetros con una sola llamada a:  
  
    ```  
    pFX->SetFieldType( CFieldExchange::param );  
    // RFX calls for parameter data members  
    ```  
  
5.  En el constructor de la clase de conjunto de registros, aumente el número de parámetros, `m_nParams`.  
  
     Para obtener información, consulte [intercambio de campos de registros: trabajar con el código de asistente](../../data/odbc/record-field-exchange-working-with-the-wizard-code.md).  
  
6.  Cuando se escribe el código que crea un objeto de conjunto de registros de esta clase, coloque un "?" símbolo (signo de interrogación) en cada lugar de las cadenas de instrucción SQL donde es un parámetro que se debe reemplazar.  
  
     En tiempo de ejecución "?" se rellenan los marcadores de posición, en orden, por los valores de parámetro se pasa. El primer miembro de datos de parámetro establecido después de la [SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype) llamada reemplaza el primer símbolo "?"en la cadena SQL, el segundo miembro de datos de parámetro reemplaza al segundo"?", y así sucesivamente.  
  
> [!NOTE]
>  Orden de los parámetros es importante: el orden de RFX llama para los parámetros en su `DoFieldExchange` función debe coincidir con el orden de los marcadores de posición de parámetro en la cadena SQL.  
  
> [!TIP]

>  La cadena más probable para trabajar con es la cadena que especifica (si existe) para la clase [m_strFilter](../../mfc/reference/crecordset-class.md#m_strfilter) miembro de datos, pero algunos controladores ODBC podrían permitir parámetros en otras cláusulas SQL.  
  
##  <a name="_core_passing_parameter_values_at_run_time"></a>Pasar valores de parámetro en tiempo de ejecución  
 Debe especificar valores de parámetro antes de llamar a **abiertos** (para un nuevo objeto de conjunto de registros) o **Requery** (por otra ya existente).  
  
#### <a name="to-pass-parameter-values-to-a-recordset-object-at-run-time"></a>Para pasar valores de parámetro a un objeto de conjunto de registros en tiempo de ejecución  
  
1.  Construya el objeto de conjunto de registros.  
  
2.  Prepare una cadena o cadenas, como el **m_strFilter** cadena, que contiene la instrucción SQL, o partes de él. Colocar "?" donde es la información de parámetros para pasar los marcadores de posición.  
  
3.  Asignar un valor de parámetro de tiempo de ejecución a cada miembro de datos de parámetro del objeto.  
  
4.  Llame a la **abiertos** función miembro (o **Requery**, para un conjunto de registros existente).  
  
 Por ejemplo, imagine que desea especificar una cadena de filtro para el conjunto de registros usando información obtenida en tiempo de ejecución. Supongamos, un conjunto de registros de clase `CStudentSet` anteriormente: denominado `rsStudents` y ahora desea una nueva consulta para un determinado tipo de información de estudiantes.  
  
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
  
 El conjunto de registros contiene registros para aquellos estudiantes cuyos registros cumplen las condiciones especificadas por el filtro, que se construyó a partir de los parámetros de tiempo de ejecución. En este caso, el conjunto de registros contiene registros para todos los estudiantes senior.  
  
> [!NOTE]
>  Si es necesario, puede establecer el valor de un miembro de datos de parámetro en Null, con [SetParamNull](../../mfc/reference/crecordset-class.md#setparamnull). Del mismo modo, puede comprobar si un miembro de datos de parámetro es Null, con [IsFieldNull](../../mfc/reference/crecordset-class.md#isfieldnull).  
  
## <a name="see-also"></a>Vea también  
 [Conjunto de registros (ODBC)](../../data/odbc/recordset-odbc.md)   
 [Conjunto de registros: Agregar, actualizar y eliminar registros (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)   
 [Conjunto de registros: Cómo se seleccionan los registros (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)