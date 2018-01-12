---
title: 'Origen de datos: Determinar el esquema del origen de datos (ODBC) | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- ODBC data sources [C++], schema
- schemas [C++], data sources
- data sources [C++], determining schema
ms.assetid: 17284acb-eb10-4f27-9944-ad1d973c0b05
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: fc425cf767db6939223288ebe74dcbc7fd4cf5b9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="data-source-determining-the-schema-of-the-data-source-odbc"></a>Origen de datos: Determinar el esquema del origen de datos (ODBC)
Este tema es aplicable a las clases ODBC de MFC.  
  
 Para configurar los miembros de datos en su `CRecordset` objetos, necesita conocer el esquema del origen de datos al que se está conectando. Determinar el esquema de un origen de datos implica obtener una lista de las tablas del origen de datos, una lista de las columnas de cada tabla, el tipo de datos de cada columna y la existencia de los índices.  
  
## <a name="see-also"></a>Vea también  
 [Origen de datos (ODBC)](../../data/odbc/data-source-odbc.md)   
 [Origen de datos: Administrar conexiones (ODBC)](../../data/odbc/data-source-managing-connections-odbc.md)