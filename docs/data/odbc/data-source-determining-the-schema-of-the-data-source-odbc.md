---
title: 'Origen de datos: Determinar el esquema del origen de datos (ODBC) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ODBC data sources [C++], schema
- schemas [C++], data sources
- data sources [C++], determining schema
ms.assetid: 17284acb-eb10-4f27-9944-ad1d973c0b05
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 6da4067766eddab40bac75ee73d825dc5886dd0f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="data-source-determining-the-schema-of-the-data-source-odbc"></a>Origen de datos: Determinar el esquema del origen de datos (ODBC)
Este tema es aplicable a las clases ODBC de MFC.  
  
 Para configurar los miembros de datos en su `CRecordset` objetos, necesita conocer el esquema del origen de datos al que se está conectando. Determinar el esquema de un origen de datos implica obtener una lista de las tablas del origen de datos, una lista de las columnas de cada tabla, el tipo de datos de cada columna y la existencia de los índices.  
  
## <a name="see-also"></a>Vea también  
 [Origen de datos (ODBC)](../../data/odbc/data-source-odbc.md)   
 [Origen de datos: Administrar conexiones (ODBC)](../../data/odbc/data-source-managing-connections-odbc.md)