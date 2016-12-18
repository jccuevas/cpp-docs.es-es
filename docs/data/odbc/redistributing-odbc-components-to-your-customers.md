---
title: "Redistribuir componentes ODBC a los clientes | Microsoft Docs"
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
  - "componentes [C++]"
  - "componentes [C++], distribuir"
  - "componentes [C++], redistribuir"
  - "Administrador de ODBC"
  - "componentes de ODBC, redistribuir"
  - "ODBC, distribuir componentes"
ms.assetid: 17b065b4-a307-4b89-99ac-d05831cfab87
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Redistribuir componentes ODBC a los clientes
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Si se incorpora la funcionalidad de los programas del Administrador de ODBC en la aplicación, deben distribuirse también a los usuarios los archivos que ejecutan estos programas.  Estos archivos ODBC residen en el directorio \\OS\\System del CD\-ROM de Visual C\+\+.  En el mismo directorio se encuentran el archivo Redistrb.wri y el contrato de licencia, que contienen una lista de los archivos ODBC que se pueden redistribuir.  
  
 Si desea incluir controladores ODBC, consulte la documentación correspondiente.  Es necesario determinar las DLL y los archivos que se deseen incluir.  
  
 También debería leer [Instalar compatibilidad con bases de datos](../../data/installing-database-support-mfc-atl.md) para obtener información sobre los componentes y controladores ODBC y [Redistribuir controles](../../data/ado-rdo/redistributing-controls.md), que explica cómo redistribuir controles ActiveX.  
  
 Asimismo, en la mayoría de los casos es necesario incluir otro archivo más.  El archivo Odbccr32.dll es la biblioteca de cursores ODBC.  Esta biblioteca proporciona a los controladores de nivel 1 la capacidad de desplazarse hacia delante y hacia atrás.  También proporciona la capacidad de admitir instantáneas.  Para obtener más información sobre la biblioteca de cursores ODBC, vea [ODBC: Biblioteca de cursores ODBC](../../data/odbc/odbc-the-odbc-cursor-library.md).  
  
 Los siguientes temas proporcionan más información sobre cómo se utiliza ODBC con las clases de base de datos:  
  
-   [ODBC: Biblioteca de cursores ODBC](../../data/odbc/odbc-the-odbc-cursor-library.md)  
  
-   [ODBC: Configurar un origen de datos ODBC](../../data/odbc/odbc-configuring-an-odbc-data-source.md)  
  
-   [ODBC: Llamar directamente a funciones de la API de ODBC](../../data/odbc/odbc-calling-odbc-api-functions-directly.md)  
  
## Vea también  
 [Conceptos básicos de ODBC](../../data/odbc/odbc-basics.md)   
 [Administrador de ODBC](../../data/odbc/odbc-administrator.md)