---
title: "&#191;Qu&#233; es el modelo de programaci&#243;n de base de datos de MFC? | Microsoft Docs"
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
  - "DAO [C++], MFC"
  - "acceso a datos [C++], tecnologías"
  - "bases de datos [C++], MFC"
  - "MFC [C++], aplicaciones de base de datos"
  - "ODBC [C++], MFC"
  - "clases ODBC [C++], clases de base de datos de MFC"
ms.assetid: f6f15bb8-4115-41f2-ad68-036e74a11bd9
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# &#191;Qu&#233; es el modelo de programaci&#243;n de base de datos de MFC?
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Aunque MFC implementa internamente DAO y ODBC de forma muy diferente, ambas tienen interfaces similares que permiten adaptar fácilmente las aplicaciones de una tecnología a la otra, especialmente de ODBC a DAO.  Para obtener información sobre cómo adaptar de ODBC a DAO, vea la [Nota técnica 55](../mfc/tn055-migrating-mfc-odbc-database-class-applications-to-mfc-dao-classes.md).  Las interfaces de DAO y ODBC que proporciona MFC también son muy similares a las proporcionadas en Visual Basic.  
  
 El modelo de programación MFC proporciona un objeto de base de datos para cada base de datos abierta.  El objeto de base de datos representa la conexión establecida con la base de datos.  Puede realizar consultas y actualizaciones mediante objetos de conjunto de registros.  DAO proporciona objetos adicionales para trabajar con la estructura de la tabla, guardar las consultas para reutilizarlas, etc., como se describe más adelante.  MFC proporciona clases para cada uno de estos objetos: un conjunto de clases para DAO y otro conjunto para ODBC.  
  
 El uso de MFC facilita el acceso a los datos.  Las clases de base de datos de DAO y ODBC proporcionan abstracciones de alto nivel que le liberan de la necesidad de utilizar DAO u ODBC directamente.  Programar con las API es más complejo que utilizar las clases MFC.  Esto es especialmente cierto en el caso de que programe aplicaciones pequeñas y relativamente sencillas.  
  
 Las clases de base de datos agregan los siguientes componentes a la biblioteca de clases de MFC:  
  
-   Clases de base de datos de C\+\+ que proporcionan una API de alto nivel para el acceso a bases de datos a través de DAO u ODBC  
  
-   Extensiones del asistente para aplicaciones y **Agregar clase** para crear clases de base de datos específicas de la aplicación  
  
-   Programas de ejemplo que ilustran el uso de las clases y los asistentes  
  
-   Documentación en pantalla, que incluye introducciones, artículos sobre temas de programación y materiales de referencia de las clases  
  
 Para obtener información sobre estos componentes, vea [ODBC y MFC](../data/odbc/odbc-and-mfc.md).  
  
 Para obtener más información, vea:  
  
-   [Elegir entre DAO y ODBC](../data/should-i-use-dao-or-odbc-q.md).  
  
-   [Disponibilidad del lenguaje de definición de base de datos \(DDL\) y el lenguaje de manipulación de base de datos \(DML\)](../data/are-ddl-and-dml-supported-q.md) en DAO y ODBC.  
  
-   [Configurar compatibilidad con bases de datos MFC](../data/installing-mfc-database-support.md).  
  
-   Las clases [ODBC](../data/odbc/odbc-and-mfc.md) en MFC.  
  
-   [Documentación sobre la programación del acceso a datos de MFC](../data/mfc-database-documentation.md).  
  
-   [Implementación de ODBC en MFC](../data/odbc/odbc-and-mfc.md).  
  
## Vea también  
 [Preguntas más frecuentes sobre Data Access](../data/data-access-frequently-asked-questions-mfc-data-access.md)