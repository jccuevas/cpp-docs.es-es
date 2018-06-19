---
title: Crear mediante programación una tabla en un origen de datos ODBC | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- programmatically creating ODBC tables [C++]
- tables [C++]
- ODBC data sources, creating tables in
- tables [C++], creating programmatically
ms.assetid: 9ca68fb5-c3df-424a-a75c-e3fb01cc1b18
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 5ea8ddc8e683c0e5f0681bdf98cbddca180e4023
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33090515"
---
# <a name="data-source-programmatically-creating-a-table-in-an-odbc-data-source"></a>Origen de datos: Crear una tabla en un origen de datos ODBC mediante programación
En este tema se explica cómo crear una tabla para los datos de origen, con el `ExecuteSQL` función miembro de clase `CDatabase`, pasa a la función una cadena que contiene un **CREATE TABLE** instrucción SQL.  
  
 Para obtener información general acerca de los orígenes de datos ODBC de MFC, vea [origen de datos (ODBC)](../../data/odbc/data-source-odbc.md). El tema [origen de datos: configuración mediante programación de un origen de datos ODBC](../../data/odbc/data-source-programmatically-configuring-an-odbc-data-source.md) describe crear orígenes de datos.  
  
 Una vez establecido el origen de datos, puede crear fácilmente tablas usando la `ExecuteSQL` función miembro y **CREATE TABLE** instrucción SQL. Por ejemplo, si tuviera un `CDatabase` objeto denominado `myDB`, podría utilizar el siguiente código MFC para crear una tabla:  
  
```  
myDB.ExecuteSQL("CREATE TABLE OFFICES (OfficeID TEXT(4)" ",   
                         OfficeName TEXT(10))");  
```  
  
 Este ejemplo de código crea una tabla denominada "OFFICES" en la conexión de origen de datos de Microsoft Access mantenida por `myDB`; la tabla contiene dos campos, "OfficeID" y "OfficeName".  
  
> [!NOTE]
>  Los tipos de campo especificados en la **CREATE TABLE** instrucción SQL puede variar según el controlador ODBC que está utilizando. El programa Microsoft Query (distribuido con Visual C++ 1.5) es una manera de detectar los tipos de campo están disponibles para un origen de datos. En Microsoft Query, haga clic en **archivo**, haga clic en **definición de tabla**, seleccione una tabla en un origen de datos y cuál es el tipo que se muestra en el **tipo** cuadro combinado. También existe sintaxis SQL para crear índices.  
  
## <a name="see-also"></a>Vea también  
 [Origen de datos (ODBC)](../../data/odbc/data-source-odbc.md)