---
title: Seleccionar y manipular registros | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- records, selecting
- record selection, MFC ODBC classes
- ODBC recordsets, selecting records
ms.assetid: 7f0b3a4a-9941-4475-a612-9ec8d15b7691
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: dec5e0094405cf9d038e53959da97ba079736505
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="selecting-and-manipulating-records"></a>Seleccionar y manipular registros
Normalmente cuando se seleccionan registros desde un origen de datos mediante una instancia de SQL **seleccione** instrucción, obtendrá un conjunto de resultados, que es un conjunto de registros de una tabla o una consulta. Con las clases de base de datos, se usa un objeto de conjunto de registros para seleccionar y obtener acceso al conjunto de resultados. Se trata de un objeto de una clase específica de la aplicación que se deriva de la clase [CRecordset](../../mfc/reference/crecordset-class.md). Cuando se define una clase de conjunto de registros, especifica para asociarlo con el origen de datos, la tabla que se va a utilizar y las columnas de la tabla. El Asistente para aplicaciones MFC o **Agregar clase** (como se describe en [agregar un consumidor ODBC de MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)) crea una clase con una conexión a un origen de datos específico. Los asistentes para escribir el [GetDefaultSQL](../../mfc/reference/crecordset-class.md#getdefaultsql) función miembro de clase `CRecordset` para devolver el nombre de tabla. Para obtener más información sobre cómo usar los asistentes para crear clases de conjunto de registros, vea [compatibilidad de base de datos, Asistente para aplicaciones MFC](../../mfc/reference/database-support-mfc-application-wizard.md) y [agregar un consumidor ODBC de MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md).  
  
 Con un [CRecordset](../../mfc/reference/crecordset-class.md) objeto en tiempo de ejecución, puede:  
  
-   Examine los campos de datos del registro actual.  
  
-   Filtrar u ordenar el conjunto de registros.  
  
-   Personalizar el código SQL predeterminado **seleccione** instrucción.  
  
-   Desplazarse por los registros seleccionados.  
  
-   Agregar, actualizar o eliminar registros (si el origen de datos y el conjunto de registros son actualizables).  
  
-   Comprobar si el conjunto de registros permite volver a consultar y actualizar el contenido del conjunto de registros.  
  
 Cuando haya terminado de utilizar el objeto de conjunto de registros, cierre y destruirlo. Para obtener más información acerca de los conjuntos de registros, vea [conjunto de registros (ODBC)](../../data/odbc/recordset-odbc.md).  
  
## <a name="see-also"></a>Vea también  
 [ODBC y MFC](../../data/odbc/odbc-and-mfc.md)