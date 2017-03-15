---
title: "Origen de datos: Crear una tabla en un origen de datos ODBC mediante programaci&#243;n | Microsoft Docs"
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
  - "orígenes de datos ODBC, crear tablas"
  - "crear tablas ODBC mediante programación [C++]"
  - "tablas [C++]"
  - "tablas [C++], crear mediante programación"
ms.assetid: 9ca68fb5-c3df-424a-a75c-e3fb01cc1b18
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# Origen de datos: Crear una tabla en un origen de datos ODBC mediante programaci&#243;n
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Este tema explica cómo se crea una tabla para el origen de datos, utilizando la función miembro `ExecuteSQL` de la clase `CDatabase` y pasando a la función una cadena que contiene la instrucción SQL **CREATE TABLE**.  
  
 Para obtener información general sobre orígenes de datos ODBC en MFC, vea [Origen de datos \(ODBC\)](../../data/odbc/data-source-odbc.md).  El tema [Origen de datos: Configurar un origen de datos ODBC mediante programación](../../data/odbc/data-source-programmatically-configuring-an-odbc-data-source.md) describe cómo se crean orígenes de datos.  
  
 Una vez establecido el origen de datos, se pueden crear fácilmente tablas usando la función miembro `ExecuteSQL` y la instrucción SQL **CREATE TABLE**.  Por ejemplo, si se tuviese un objeto `CDatabase` denominado `myDB`, se podría utilizar el siguiente código MFC para crear una tabla:  
  
```  
myDB.ExecuteSQL("CREATE TABLE OFFICES (OfficeID TEXT(4)" ",   
                         OfficeName TEXT(10))");  
```  
  
 Este código de ejemplo crea una tabla denominada "OFFICES" en la conexión al origen de datos de Microsoft Access mantenida por `myDB`; la tabla contiene dos campos, "OfficeID" y "OfficeName".  
  
> [!NOTE]
>  Los tipos de campo especificados en la instrucción SQL **CREATE TABLE** pueden variar dependiendo del controlador ODBC que se esté utilizando.  El programa Microsoft Query \(distribuido con Visual C\+\+ 1.5\) es una forma de detectar los tipos de campo que están disponibles para un origen de datos.  En Microsoft Query, haga clic en **Archivo**, haga clic en **Definición de tabla**, seleccione una tabla de un origen de datos y mire el tipo mostrado en el cuadro combinado **Tipo**.  También existe sintaxis SQL para crear índices.  
  
## Vea también  
 [Origen de datos \(ODBC\)](../../data/odbc/data-source-odbc.md)