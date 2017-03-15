---
title: "Excepciones: Excepciones de base de datos | Microsoft Docs"
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
  - "DAO [C++], excepciones"
  - "excepciones de la base de datos [C++]"
  - "bases de datos [C++], control de excepciones"
  - "códigos de error [C++], control de excepciones de la base de datos"
  - "control de excepciones [C++], bases de datos"
  - "excepciones [C++], base de datos"
  - "ODBC [C++], excepciones"
  - "excepciones ODBC [C++]"
ms.assetid: 28daf260-f824-4be6-aecc-1f859e6dec26
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Excepciones: Excepciones de base de datos
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este artículo se explica cómo controlar excepciones de base de datos.  La mayor parte del material en este artículo se aplica si trabaja con las clases MFC para ODBC o clases MFC para Objetos de acceso a datos \(DAO\).  El concreto material a un u otro modelo se marca explícitamente.  Entre los temas se incluyen los siguientes:  
  
-   [Enfoques al control de excepciones](#_core_approaches_to_exception_handling)  
  
-   [Un ejemplo de control de excepciones de base de datos](#_core_a_database_exception.2d.handling_example)  
  
##  <a name="_core_approaches_to_exception_handling"></a> Enfoques al control de excepciones  
 El enfoque es el mismo si trabaja con DAO u ODBC.  
  
 Debe escribir siempre los controladores de excepciones a las condiciones excepcionales ID.  
  
 El enfoque más a pragmatic detectar excepciones de base de datos es probar la aplicación con escenarios de la excepción.  Determine las excepciones probable que podrían aparecer para una operación en el código, y fuerza la excepción aparezca.  A continuación examine el resultado de traza para ver se produce la excepción, o para examinar la información de error devuelta en el depurador.  Esto le permite saber que los códigos devueltos se consideren para escenarios de excepción que está utilizando.  
  
### Códigos de error utilizados para ODBC Excepciones  
 Además de los códigos devueltos definidos por el marco, que tienen nombres de formulario **AFX\_SQL\_ERROR\_XXX**, algún [CDBExceptions](../mfc/reference/cdbexception-class.md) se basa en los códigos de retorno de [ODBC](../data/odbc/odbc-basics.md) .  Los códigos de retorno para esas excepciones tienen nombres de formulario **SQL\_ERROR\_XXX**.  
  
 Los códigos de retorno — marco\- definido y ODBC\- definido — que las clases de base de datos pueden devolver se documentan en miembro de datos de [m\_nRetCode](../Topic/CDBException::m_nRetCode.md) de la clase `CDBException`.  Información adicional sobre los códigos devueltos definidos por ODBC está disponible en *la referencia* de ODBC en el CD de MSDN Library.  
  
### Códigos de error utilizados para DAO Excepciones  
 Para las excepciones de DAO, más información es normalmente disponibles.  Puede tener acceso a la información de error a través de tres miembros de datos de un objeto detectado de [CDaoException](../mfc/reference/cdaoexception-class.md) :  
  
-   [m\_pErrorInfo](../Topic/CDaoException::m_pErrorInfo.md) contiene un puntero a un objeto de [CDaoErrorInfo](../mfc/reference/cdaoerrorinfo-structure.md) que encapsula información de error en la colección de DAO de objetos error asociados a la base de datos.  
  
-   [m\_nAfxDaoError](../Topic/CDaoException::m_nAfxDaoError.md) contiene un código de error extendido de las clases DAO de MFC.  Estos códigos de error, que tienen nombres de formulario **AFX\_DAO\_ERROR\_XXX**, se documentan en miembro de datos en `CDaoException`.  
  
-   [m\_scode](../Topic/CDaoException::m_scode.md) contiene `SCODE` OLE de DAO, si es necesario.  Necesitará raramente ejecutar este código de error, sin embargo.  Más información suele ser disponibles en los otros dos miembros de datos.  Vea el miembro de datos para más información sobre los valores de `SCODE` .  
  
 Información adicional sobre los errores de DAO, el tipo de objeto del error de DAO, y la colección de errores de DAO está disponible bajo la clase [CDaoException](../mfc/reference/cdaoexception-class.md).  
  
##  <a name="_core_a_database_exception.2d.handling_example"></a> Un ejemplo de control de excepciones de base de datos  
 El ejemplo siguiente se intenta construir [CRecordset](../mfc/reference/crecordset-class.md)\- objeto derivado en la pila con el operador de **new** , y abrir el conjunto de registros \(para un origen de datos ODBC\).  Para obtener un ejemplo similar para las clases DAO, vea el “ejemplo de DAO Exception”.  
  
### Ejemplo de excepción de ODBC  
 La función miembro de [Abierta](../Topic/CRecordset::Open.md) podría producir una excepción \(de [CDBException](../mfc/reference/cdbexception-class.md) con tipo para las clases ODBC\), por lo que los corchetes de este código la llamada de **Abierta** con un bloque de **try** .  El bloque posterior de **catch** detectará `CDBException`.  Puede examinar el objeto de excepción propio, denominado `e`, pero en este caso es bastante saber que se ha producido un error en el intento de crear un conjunto de registros.  El bloque de **catch** muestra un cuadro de mensaje y limpia eliminando el objeto de conjunto de registros.  
  
 [!code-cpp[NVC_MFCDatabase#36](../mfc/codesnippet/CPP/exceptions-database-exceptions_1.cpp)]  
  
### Ejemplo de excepción de DAO  
 El ejemplo de DAO es similar al ejemplo de ODBC, pero puede recuperar normalmente a varios tipos de información.  El código siguiente también intenta abrir un conjunto de registros.  Si ese intento produce una excepción, puede ir a un miembro de datos del objeto de excepción para la información de error.  Como en el ejemplo anterior de ODBC, es suficiente saber que se produjo un error en el intento de crear un conjunto de registros.  
  
 [!code-cpp[NVC_MFCDatabase#37](../mfc/codesnippet/CPP/exceptions-database-exceptions_2.cpp)]  
  
 Este código obtiene una cadena de mensaje de error de miembro de [m\_pErrorInfo](../Topic/CDaoException::m_pErrorInfo.md) del objeto de excepción.  MFC rellena este miembro cuando produce la excepción.  
  
 Para obtener una descripción de la información de error devuelta por un objeto de `CDaoException` , vea las clases [CDaoException](../mfc/reference/cdaoexception-class.md) y [CDaoErrorInfo](../mfc/reference/cdaoerrorinfo-structure.md).  
  
 Cuando trabaja con bases de datos de Microsoft Jet \(.mdb\) y, en la mayoría de los casos cuando se trabaja con ODBC, habrá sólo un objeto error.  En el caso poco frecuente cuando se utiliza un origen de datos ODBC y hay varios errores, puede recorrer en iteración la colección de errores de DAO basándose en el número de errores devueltos por [CDaoException::GetErrorCount](../Topic/CDaoException::GetErrorCount.md).  Cada vez que a través del bucle, llamada [CDaoException::GetErrorInfo](../Topic/CDaoException::GetErrorInfo.md) para rellenar el miembro de datos de `m_pErrorInfo` .  
  
## Vea también  
 [Control de excepciones](../mfc/exception-handling-in-mfc.md)