---
title: Esquema (acceso a datos MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- structures [C++], database
- databases [C++], schema
- database schema [C++], about database schemas
- database schema [C++]
- schemas [C++], database
- structures [C++]
ms.assetid: 7d17e35f-1ccf-4853-b915-5b8c7a45b9ee
ms.openlocfilehash: cc333ee987ed0c6cba6cb11730d8f940e49d525d
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59039038"
---
# <a name="schema--mfc-data-access"></a>Esquema (acceso a datos MFC)

Un esquema de base de datos describe la estructura actual de las tablas y vistas de base de datos en la base de datos. En general, el código generado por el asistente supone que el esquema de la tabla o tablas a que accede un conjunto de registros no va a cambiar, pero las clases de base de datos pueden tratar algunos cambios de esquema, como agregar, reordenar o eliminar columnas sin enlazar. Si una tabla cambia, debe actualizar manualmente el conjunto de registros de la tabla y, a continuación, volver a compilar la aplicación.

También puede complementar el código generado por el asistente para que actúe en caso de que una base de datos tenga un esquema que no se conoce por completo en el momento de la compilación. Para obtener más información, consulte [conjunto de registros: Enlazar dinámicamente columnas de datos (ODBC)](../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).

## <a name="see-also"></a>Vea también

[Acceso a los datos de programación (MFC/ATL)](../data/data-access-programming-mfc-atl.md)<br/>
[SQL](../data/odbc/sql.md)<br/>
[Conjunto de registros (ODBC)](../data/odbc/recordset-odbc.md)