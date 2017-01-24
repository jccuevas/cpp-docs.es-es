---
title: "Conjunto de registros: Filtrar registros (ODBC) | Microsoft Docs"
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
  - "datos [MFC], filtrar"
  - "filtrar conjuntos de registros"
  - "filtros [C++], recordset (objeto)"
  - "conjuntos de registros ODBC [C++], filtrar registros"
  - "conjuntos de registros [C++], filtrar"
ms.assetid: 5c075f37-c837-464d-90c1-d028a9d1c175
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Conjunto de registros: Filtrar registros (ODBC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Este tema es aplicable a las clases ODBC de MFC.  
  
 Este tema explica cómo filtrar un conjunto de registros para que sólo seleccione un subconjunto específico de los registros disponibles.  Por ejemplo, puede desear seleccionar sólo las secciones de clase de un curso determinado, como MATH101 *\(Matemáticas\)*.  Un filtro es una condición de búsqueda definida por el contenido de una cláusula SQL **WHERE**.  Cuando el marco de trabajo la anexa a la instrucción SQL del conjunto de registros, la cláusula **WHERE** restringe la selección.  
  
 Se debe establecer un filtro para el objeto de conjunto de registros después de crear el objeto, pero antes de llamar a su función miembro **Open** \(o antes de llamar a la función miembro **Requery** de un objeto de conjunto de registros existente a cuya función miembro **Open** se llamó anteriormente\).  
  
#### Para especificar un filtro en un objeto de conjunto de registros  
  
1.  Cree un nuevo objeto de conjunto de registros \(o prepare la llamada a **Requery** para un objeto existente\).  
  
2.  Establezca el valor del miembro de datos [m\_strFilter](../Topic/CRecordset::m_strFilter.md) del objeto.  
  
     El filtro es una cadena terminada en null con el contenido de la cláusula SQL **WHERE** pero no la palabra clave **WHERE**.  Por ejemplo, utilice:  
  
    ```  
    m_pSet->m_strFilter = "CourseID = 'MATH101'";  
    ```  
  
     not  
  
    ```  
    m_pSet->m_strFilter = "WHERE CourseID = 'MATH101'";  
    ```  
  
    > [!NOTE]
    >  La cadena literal "MATH101" aparece con comillas simples.  En la especificación SQL de ODBC, las comillas simples se usan para denotar un literal de cadena de caracteres.  Compruebe la documentación de su controlador ODBC en lo relativo al uso de comillas del sistema de administración de bases de datos \(DBMS\) en esta situación.  Esta sintaxis también se trata más adelante, hacia el final del tema.  
  
3.  Establezca otras opciones que necesite, como el criterio de ordenación, el modo de bloqueo o los parámetros.  Especificar un parámetro resulta especialmente útil.  Para obtener más información sobre cómo parametrizar un filtro, vea [Conjunto de registros: Parametrizar un conjunto de registros \(ODBC\)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).  
  
4.  Llame a **Open** para el nuevo objeto \(o a **Requery** para un objeto abierto anteriormente\).  
  
> [!TIP]
>  El uso de parámetros en el filtro es, potencialmente, el método más eficaz para recuperar registros.  
  
> [!TIP]
>  Los filtros de conjuntos de registros son útiles para [combinar](../../data/odbc/recordset-performing-a-join-odbc.md) tablas y usar [parámetros](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md) basados en información obtenida o calculada en tiempo de ejecución.  
  
 El conjunto de registros selecciona sólo aquellos registros que cumplen la condición de búsqueda especificada.  Por ejemplo, para especificar el filtro de curso descrito anteriormente \(suponiendo una variable `strCourseID` establecida en "MATH101"\), haga lo siguiente:  
  
```  
// Using the recordset pointed to by m_pSet  
  
// Set the filter  
m_pSet->m_strFilter = "CourseID = " + strCourseID;   
  
// Run the query with the filter in place  
if ( m_pSet->Open( CRecordset::snapshot, NULL, CRecordset::readOnly ) )  
  
// Use the recordset  
```  
  
 El conjunto de registros contiene registros para todas las secciones de clase de MATH101.  
  
 Observe cómo se estableció la cadena de filtro en el ejemplo anterior mediante una variable de cadena.  Esta es la forma más usual.  Pero suponga que deseaba especificar el valor literal 100 como identificador del curso.  El código siguiente muestra cómo configurar correctamente la cadena de filtro con un valor literal:  
  
```  
m_strFilter = "StudentID = '100'";   // correct  
```  
  
 Observe el uso de las comillas simples; si se establece la cadena de filtro directamente, su valor es **not**:  
  
```  
m_strFilter = "StudentID = 100";   // incorrect for some drivers  
```  
  
 El uso de comillas anterior se ajusta a la especificación ODBC, pero algunos sistemas de administración de bases de datos \(DBMS\) pueden requerir otra norma.  Para obtener más información, vea [SQL: Personalizar la instrucción SQL del conjunto de registros \(ODBC\)](../../data/odbc/sql-customizing-your-recordset’s-sql-statement-odbc.md).  
  
> [!NOTE]
>  Si elige reemplazar la cadena SQL predeterminada del conjunto de registros pasando su propia cadena SQL a **Open**, no debe establecer ningún filtro si la cadena personalizada contiene una cláusula **WHERE**.  Para obtener más información sobre cómo reemplazar el código SQL predeterminado, vea [SQL: Personalizar la instrucción SQL del conjunto de registros \(ODBC\)](../../data/odbc/sql-customizing-your-recordset’s-sql-statement-odbc.md).  
  
## Vea también  
 [Conjunto de registros \(ODBC\)](../../data/odbc/recordset-odbc.md)   
 [Conjunto de registros: Ordenar registros \(ODBC\)](../../data/odbc/recordset-sorting-records-odbc.md)   
 [Conjunto de registros: Cómo se seleccionan los registros \(ODBC\)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)   
 [Conjunto de registros: Actualizar los registros \(ODBC\)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)   
 [Conjunto de registros: Bloquear registros \(ODBC\)](../../data/odbc/recordset-locking-records-odbc.md)