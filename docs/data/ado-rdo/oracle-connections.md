---
title: "Conexiones Oracle | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "conexiones [C++], bases de datos"
  - "conexiones de bases de datos [C++], Oracle"
  - "bases de datos [C++], conectar"
  - "Oracle [C++], crear conexiones"
  - "bases de datos de Oracle [C++]"
  - "bases de datos de Oracle [C++], conexiones"
ms.assetid: d317e763-44aa-47c9-abe8-261d513d894f
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Conexiones Oracle
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Al configurar un DSN ODBC para Oracle o una conexión OLE DB, debe tener instalados los componentes de cliente SQL\*Net de Oracle.  SQL\*Net es la capa de transporte de red de Oracle.  La mayoría de los controladores ODBC para Oracle, incluidos el controlador de Microsoft y el mapa de proveedores de Microsoft OLE DB para Oracle, llaman directamente a esta capa de SQL\*Net.  
  
 Una vez configurado SQL\*Net, observe la cadena de conexión de SQL\*Net.  Normalmente, consta de un especificador para el nombre del servidor de bases de datos de Oracle y el tipo de protocolo de red \(como TCP\/IP y canalizaciones con nombre\).  La cadena de conexión de SQL\*Net se suele asignar a un alias.  En este caso, solo tendrá que anotar el alias.  Para obtener información sobre cómo configurar SQL\*Net, póngase en contacto con el administrador de la base de datos Oracle, consulte la documentación de SQL\*Net o consulte el archivo de Ayuda del controlador ODBC para Oracle, a fin de ver un ejemplo de una cadena de conexión.  
  
## Vea también  
 [Crear conexiones de bases de datos](../../data/ado-rdo/creating-database-connections.md)