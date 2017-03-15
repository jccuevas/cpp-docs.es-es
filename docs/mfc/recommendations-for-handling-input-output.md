---
title: "Recomendaciones para el control de entrada/salida | Microsoft Docs"
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
  - "opciones de E/S basadas en archivo"
  - "E/S [C++]"
  - "E/S [C++], opciones basadas en archivo"
  - "E/S [C++], opciones"
  - "E/S [MFC], acerca de E/S"
ms.assetid: d664b175-3b4a-40c3-b14b-39de6b12e419
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Recomendaciones para el control de entrada/salida
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Si utiliza E\/S basada en archivos o no depende de cómo se responde a las preguntas del árbol de decisión siguiente:  
  
 **¿Los datos primario en la aplicación reside en un archivo de disco?**  
  
-   Sí, los datos primarios reside en un archivo de disco:  
  
     **¿La aplicación lee el archivo completo en memoria en Abrir archivos y escribe el archivo de conjunto de nuevo en el disco en el archivo Guardar?**  
  
    -   Sí: Éste es el caso predeterminado del documento de MFC.  Serialización de **CDocument** de uso.  
  
    -   No: Normalmente es el caso de actualizar transacción\- basado en archivo.  Actualiza el archivo según la por\- transacción y no necesita la serialización de **CDocument** .  
  
-   No, los datos primarios no reside en un archivo de disco:  
  
     **¿Los datos residen en un origen de datos ODBC?**  
  
    -   Sí, los datos reside en un origen de datos ODBC:  
  
         Compatibilidad con bases de datos MFC de uso.  La implementación estándar de MFC para este caso incluye un objeto de **CDocument** que almacena un objeto de `CDatabase` , como se describe en el artículo [¿Qué es el modelo de programación de base de datos de MFC?](../data/what-is-the-mfc-database-programming-model-q.md).  La aplicación también puede leer y escribir un archivo auxiliar — la finalidad del asistente para aplicaciones “una vista de base de datos y opción de compatibilidad de archivo”.  En este caso, se debería utilizar la serialización para el archivo auxiliar.  
  
    -   No, los datos no reside en un origen de datos ODBC.  
  
         Ejemplos de este caso: los datos residen en que ODBC DBMS; los datos se lee mediante algún otro mecanismo, como OLE o DDE.  
  
         En casos como éste, no utilizará la serialización, y la aplicación no tendrá elementos de menú para Abrir y guardar.  Es posible que se desee utilizar **CDocument** como base de orígen, como una aplicación ODBC de MFC utiliza el documento para almacenar objetos de `CRecordset` .  Pero no utilizará la serialización de documentos para Abrir o guardar archivos predeterminado del marco.  
  
 Para admitir el Abrir, Guardar, y Guardar como comandos en el menú archivo, el marco de trabajo proporciona la serialización de documentos.  Datos de lecturas y escrituras de serialización, incluidos los objetos derivados de la clase `CObject`, el almacenamiento permanente, normalmente un archivo de disco.  La serialización es fácil de usar y proporciona muchos de necesarias, pero puede ser inadecuado en muchas aplicaciones de acceso a datos.  Las aplicaciones de acceso a datos actualizan los datos en función de la por\- transacción.  Actualizan los registros afectados por la transacción en lugar de leer y escribir un archivo de datos entero inmediatamente.  
  
 Para obtener información sobre serialización, vea [Serialización](../mfc/serialization-in-mfc.md).  
  
## Vea también  
 [Serialización: Serialización frente a entrada\/salida de bases de datos](../mfc/serialization-serialization-vs-database-input-output.md)