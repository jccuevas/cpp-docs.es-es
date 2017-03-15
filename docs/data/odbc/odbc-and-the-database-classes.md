---
title: "ODBC y las clases de base de datos | Microsoft Docs"
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
  - "clases de base de datos [C++], ODBC"
  - "MFC [C++], ODBC y"
  - "funciones de la API de ODBC [C++]"
  - "clases ODBC [C++], clases de base de datos de MFC"
ms.assetid: b166f82d-6f85-4556-aac8-fb851235d22c
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# ODBC y las clases de base de datos
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Las clases de base de datos ODBC de MFC encapsulan las llamadas a funciones de la API de ODBC que normalmente haría el usuario en las funciones miembro de las clases [CDatabase](../../mfc/reference/cdatabase-class.md) y [CRecordset](../../mfc/reference/crecordset-class.md).  Por ejemplo, las secuencias de llamadas ODBC complejas, el enlace de los registros devueltos con ubicaciones de almacenamiento, el control de las condiciones de error y otras operaciones son administradas por las clases de base de datos en lugar del usuario.  El resultado es que éste utiliza una interfaz de clase bastante más sencilla para manipular registros mediante un objeto de conjunto de registros.  
  
> [!NOTE]
>  Mediante las clases ODBC de MFC, como se describe en este TEMA, o las clases DAO de MFC se puede tener acceso a los orígenes de datos ODBC.  
  
 Aunque las clases de base de datos encapsulan la funcionalidad de ODBC, no proporcionan asignaciones individualizadas de las funciones de la API de ODBC.  Las clases de base de datos proporcionan un mayor nivel de abstracción y están diseñadas a partir de los objetos de acceso a datos existentes en Microsoft Access y Microsoft Visual Basic.  Para obtener más información, vea [¿Qué es el modelo de programación de base de datos de MFC?](../../data/what-is-the-mfc-database-programming-model-q.md).  
  
## Vea también  
 [Conceptos básicos de ODBC](../../data/odbc/odbc-basics.md)