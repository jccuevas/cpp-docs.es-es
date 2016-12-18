---
title: "Documentaci&#243;n de la base de datos MFC | Microsoft Docs"
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
  - "bases de datos [C++], MFC"
  - "MFC [C++], aplicaciones de base de datos"
  - "ODBC [C++], MFC"
ms.assetid: bb120282-cd0d-4bf4-a27c-93b3501fb3a0
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Documentaci&#243;n de la base de datos MFC
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La documentación MFC de las clases DAO y ODBC comprende los componentes enumerados en la siguiente tabla.  
  
### Documentación de la base de datos MFC  
  
|Para documentación sobre|Vea|  
|------------------------------|---------|  
|Las clases DAO y ODBC|El nombre de cada clase en la *Referencia de MFC*|  
|Las funciones y macros globales de DAO y ODBC|El nombre de función o macro en la *Referencia de MFC*|  
|La programación con las clases ODBC de MFC|[ODBC y MFC](../data/odbc/odbc-and-mfc.md)|  
|Las notas técnicas de DAO y ODBC|[Notas técnicas de MFC](../mfc/technical-notes-by-category.md)|  
  
##  <a name="_core_mfc_documentation_and_dao_documentation"></a> Documentación de MFC y documentación de DAO  
 A lo largo de la documentación de MFC correspondiente a las clases DAO de MFC encontrará referencias a los temas del SDK de DAO, incluido en la documentación en línea.  Debido a que MFC encapsula \(o envuelve\) a DAO, la documentación de MFC:  
  
-   Se centra en MFC y sus diferencias con la implementación subyacente de DAO.  
  
-   Señala a los temas de ayuda del SDK de DAO en lo referente a los detalles de funcionamiento.  Estas referencias cruzadas se denominan siempre "tema *X* de la ayuda de DAO".  
  
-   Señala las diferencias entre la forma de actuar de MFC y DAO.  MFC no encapsula todas las funciones de DAO.  Por ejemplo, MFC no proporciona objetos de seguridad DAO.  
  
> [!NOTE]
>  La Ayuda del SDK de DAO es un archivo de Ayuda independiente.  No hay vínculos de hipertexto entre esta documentación y la ayuda de DAO en esta versión de Visual C\+\+.  
  
> [!NOTE]
>  Puede resultar necesario realizar algún tipo de conversión del lenguaje al examinar los temas de Ayuda del SDK de DAO.  Los ejemplos de la documentación principal del SDK de DAO están escritos en el lenguaje Basic, no en C\+\+. Sin embargo, el SDK de DAO incluye un conjunto de ejemplos en C\+\+ que no utilizan MFC.  
  
##  <a name="_core_mfc_documentation_and_odbc_documentation"></a> Documentación de MFC y documentación de ODBC  
 La documentación de MFC de las clases ODBC de MFC está organizada de manera diferente.  Las clases ODBC de MFC proporcionan un alto nivel de abstracción basado en ODBC, más que un contenedor de la API ODBC.  Por ello, los dos conjuntos de documentación están menos conectados entre sí que la documentación de MFC y DAO.  La documentación de ODBC usa el lenguaje C, que está mucho más próximo a C\+\+ que Basic.  
  
## Vea también  
 [Clases de base de datos MFC \(ODBC y DAO\)](../data/mfc-database-classes-odbc-and-dao.md)   
 [Conceptos básicos de ODBC](../data/odbc/odbc-basics.md)