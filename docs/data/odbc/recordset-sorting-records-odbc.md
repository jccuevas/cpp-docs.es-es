---
title: 'Conjunto de registros: Ordenar registros (ODBC) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- sorting data, recordset data
- ODBC recordsets, sorting
- recordsets, sorting
ms.assetid: b40b152e-0a91-452e-be7b-e5bc27f744c7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ddb92016b7b911fc86f2feab27a698ce7fa55c45
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="recordset-sorting-records-odbc"></a>Conjunto de registros: Ordenar registros (ODBC)
Este tema es aplicable a las clases ODBC de MFC.  
  
 Este tema explica cómo ordenar el conjunto de registros. Puede especificar una o varias columnas en el que se va a basar la ordenación, y puede especificar el orden ascendente o descendente (`ASC` o **DESC**; `ASC` es el valor predeterminado) para cada columna especificada. Por ejemplo, si se especifican dos columnas, los registros se ordenan en primer lugar en la primera columna con el nombre y, a continuación, en la segunda columna denominada. Una instancia de SQL **ORDER BY** cláusula define un criterio de ordenación. Cuando el marco de trabajo anexa la **ORDER BY** cláusula para SQL del conjunto de registros de consulta, los controles de la cláusula de orden de la selección.  
  
 Debe establecer el criterio de ordenación del conjunto de registros después de crear el objeto, pero antes de llamar a su **abiertos** función miembro (o antes de llamar a la **Requery** función de miembro para un objeto de conjunto de registros existente cuyo **abiertos** función miembro se ha llamado anteriormente).  
  
#### <a name="to-specify-a-sort-order-for-a-recordset-object"></a>Para especificar un criterio de ordenación para un objeto de conjunto de registros  
  
1.  Construye un nuevo objeto de conjunto de registros (o prepare la llamada a **Requery** por otra ya existente).  
  
2.  Establezca el valor del objeto [m_strSort](../../mfc/reference/crecordset-class.md#m_strsort) miembro de datos.  
  
     La ordenación es una cadena terminada en null. Contiene el contenido de la **ORDER BY** cláusula pero no la palabra clave **ORDER BY**. Por ejemplo, use:  
  
    ```  
    recordset.m_strSort = "LastName DESC, FirstName DESC";  
    ```  
  
     not  
  
    ```  
    recordset.m_strSort = "ORDER BY LastName DESC, FirstName DESC";  
    ```  
  
3.  Establezca las demás opciones que necesite, como un filtro, el modo de bloqueo o parámetros.  
  
4.  Llame a **abiertos** para el nuevo objeto (o **Requery** para un objeto existente).  
  
 Los registros seleccionados se ordenan según se haya especificado. Por ejemplo, para ordenar un conjunto de registros de estudiantes en orden descendente por apellido y luego por nombres, haga lo siguiente:  
  
```  
// Construct the recordset  
CStudentSet rsStudent( NULL );  
// Set the sort  
rsStudent.m_strSort = "LastName DESC, FirstName DESC";  
// Run the query with the sort in place  
rsStudent.Open( );  
```  
  
 El conjunto de registros contiene todos los registros de estudiantes, ordenados de forma descendente (Z a) por apellido, a continuación, por nombre.  
  
> [!NOTE]
>  Si elige reemplazar la cadena SQL predeterminada del conjunto de registros pasando su propia cadena SQL a **abiertos**, no se debe establecer un orden si la cadena personalizada contiene una **ORDER BY** cláusula.  
  
## <a name="see-also"></a>Vea también  
 [Conjunto de registros (ODBC)](../../data/odbc/recordset-odbc.md)   
 [Conjunto de registros: Parametrizar un conjunto de registros (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)   
 [Conjunto de registros: Filtrar registros (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)