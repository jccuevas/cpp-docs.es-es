---
title: "Conjunto de registros: Ordenar registros (ODBC) | Microsoft Docs"
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
  - "conjuntos de registros ODBC, ordenar"
  - "conjuntos de registros, ordenar"
  - "ordenar datos, datos del conjunto de registros"
ms.assetid: b40b152e-0a91-452e-be7b-e5bc27f744c7
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Conjunto de registros: Ordenar registros (ODBC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Este tema es aplicable a las clases ODBC de MFC.  
  
 Este tema explica cómo ordenar un conjunto de registros.  Se pueden especificar una o varias columnas en las que basar la ordenación, así como el orden ascendente o descendente \(`ASC` o **DESC**; `ASC` es el predeterminado\) para cada columna especificada.  Por ejemplo, si se especifican dos columnas, los registros se ordenan en primer lugar por la primera columna indicada y después por la segunda.  La ordenación se define mediante una cláusula SQL **ORDER BY**.  Cuando el marco de trabajo anexa esta cláusula a la consulta SQL del conjunto de registros, ésta controla la ordenación de la selección.  
  
 Se debe establecer un criterio de ordenación para el conjunto de registros después de crear el objeto, pero antes de llamar a su función miembro **Open** \(o antes de llamar a la función miembro **Requery** de un objeto de conjunto de registros existente a cuya función miembro **Open** se llamó anteriormente\).  
  
#### Para especificar una criterio de ordenación en un objeto de conjunto de registros  
  
1.  Cree un nuevo objeto de conjunto de registros \(o prepare la llamada a **Requery** para un objeto existente\).  
  
2.  Establezca el valor del miembro de datos [m\_strSort](../Topic/CRecordset::m_strSort.md) del objeto.  
  
     El tipo de orden es una cadena terminada en null.  Contiene el texto de la cláusula SQL **ORDER BY**, pero no la palabra clave **ORDER BY**.  Por ejemplo, utilice:  
  
    ```  
    recordset.m_strSort = "LastName DESC, FirstName DESC";  
    ```  
  
     not  
  
    ```  
    recordset.m_strSort = "ORDER BY LastName DESC, FirstName DESC";  
    ```  
  
3.  Establezca otras opciones que necesite, como el filtro, el modo de bloqueo o los parámetros.  
  
4.  Llame a **Open** para el nuevo objeto \(o a **Requery** para un objeto existente\).  
  
 Los registros seleccionados se ordenan según lo especificado.  Por ejemplo, para ordenar una serie de registros de estudiantes en orden descendente por el apellido y después por el nombre, haga lo siguiente:  
  
```  
// Construct the recordset  
CStudentSet rsStudent( NULL );  
// Set the sort  
rsStudent.m_strSort = "LastName DESC, FirstName DESC";  
// Run the query with the sort in place  
rsStudent.Open( );  
```  
  
 El conjunto de registros contiene todos los registros de estudiantes, ordenados de forma descendente \(de la Z a la A\), primero por apellido y después por nombre.  
  
> [!NOTE]
>  Si elige reemplazar la cadena SQL predeterminada del conjunto de registros pasando su propia cadena SQL a **Open**, no debe establecer un orden si la cadena personalizada contiene una cláusula **ORDER BY**.  
  
## Vea también  
 [Conjunto de registros \(ODBC\)](../../data/odbc/recordset-odbc.md)   
 [Conjunto de registros: Parametrizar un conjunto de registros \(ODBC\)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)   
 [Conjunto de registros: Filtrar registros \(ODBC\)](../../data/odbc/recordset-filtering-records-odbc.md)