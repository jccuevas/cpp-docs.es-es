---
title: Esquema (acceso a datos MFC) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- structures [C++], database
- databases [C++], schema
- database schema [C++], about database schemas
- database schema [C++]
- schemas [C++], database
- structures [C++]
ms.assetid: 7d17e35f-1ccf-4853-b915-5b8c7a45b9ee
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 76a38525f7fdf451d40f555d76d3557cbc155936
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="schema--mfc-data-access"></a>Esquema (acceso a datos MFC)
Un esquema de base de datos describe la estructura actual de las tablas y vistas de base de datos en la base de datos. En general, el código generado por el asistente supone que el esquema de la tabla o tablas a que accede un conjunto de registros no va a cambiar, pero las clases de base de datos pueden tratar algunos cambios de esquema, como agregar, reordenar o eliminar columnas sin enlazar. Si una tabla cambia, debe actualizar manualmente el conjunto de registros de la tabla y, a continuación, volver a compilar la aplicación.  
  
 También puede complementar el código generado por el asistente para que actúe en caso de que una base de datos tenga un esquema que no se conoce por completo en el momento de la compilación. Para obtener más información, consulte [conjunto de registros: enlazar dinámicamente columnas de datos (ODBC)](../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).  
  
## <a name="see-also"></a>Vea también  
 [Acceso a los datos de programación (MFC/ATL)](../data/data-access-programming-mfc-atl.md)   
 [SQL](../data/odbc/sql.md)   
 [Conjunto de registros (ODBC)](../data/odbc/recordset-odbc.md)