---
title: 'Excepciones: Excepciones de base de datos | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- DAO [MFC], exceptions
- exceptions [MFC], database
- exception handling [MFC], databases
- ODBC exceptions [MFC]
- ODBC [MFC], exceptions
- database exceptions [MFC]
- databases [MFC], exception handling
- error codes [MFC], database exception handling
ms.assetid: 28daf260-f824-4be6-aecc-1f859e6dec26
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2168bc530accfdde6fad4d41cd68e94d3088f153
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33354307"
---
# <a name="exceptions-database-exceptions"></a>Excepciones: Excepciones de base de datos
En este artículo se explica cómo controlar las excepciones de base de datos. La mayoría de los materiales en este artículo se aplica si está trabajando con las clases MFC para Open Database Connectivity (ODBC) o las clases MFC para Data Access Objects (DAO). Material específico a uno de los modelos se marca explícitamente. Entre los temas se incluyen los siguientes:  
  
-   [Enfoques para control de excepciones](#_core_approaches_to_exception_handling)  
  
-   [Un ejemplo de control de excepciones de base de datos](#_core_a_database_exception.2d.handling_example)  
  
##  <a name="_core_approaches_to_exception_handling"></a> Enfoques para control de excepciones  
 El enfoque es el mismo independientemente de si trabaja con DAO u ODBC.  
  
 Siempre debería escribir controladores de excepciones para controlar condiciones excepcionales.  
  
 El enfoque más práctico para detectar excepciones de base de datos es probar la aplicación con escenarios de excepciones. Determine las excepciones posibles que podrían producirse debido a una operación en el código y forzar que se produzca la excepción. A continuación, examine los resultados de seguimiento para ver qué excepción se inicia o examinar la información del error devuelto en el depurador. Esto le permite saber que verá en los escenarios de excepción que utilizas de códigos de retorno.  
  
### <a name="error-codes-used-for-odbc-exceptions"></a>Códigos de error usados para las excepciones de ODBC  
 Además de los códigos de retorno definidos por el marco de trabajo, que tienen nombres de la forma **AFX_SQL_ERROR_XXX**, algunas [excepciones CDBException](../mfc/reference/cdbexception-class.md) se basan en [ODBC](../data/odbc/odbc-basics.md) códigos de retorno. Los códigos de retorno para dichas excepciones tienen nombres de la forma **SQL_ERROR_XXX**.  
  
 Los códigos de retorno, definida por ODBC y definidas por el marco de trabajo, que las clases de base de datos pueden devolver se documentan en el [m_nRetCode](../mfc/reference/cdbexception-class.md#m_nretcode) miembro de datos de la clase `CDBException`. Información adicional acerca de los códigos de retorno definida por ODBC está disponible en el SDK de ODBC *referencia del programador* en MSDN Library.  
  
### <a name="error-codes-used-for-dao-exceptions"></a>Códigos de error usados para las excepciones de DAO  
 Para las excepciones de DAO, hay suele estar disponible más información. Puede tener acceso a información de error a través de tres miembros de datos de un detectada [CDaoException](../mfc/reference/cdaoexception-class.md) objeto:  
  
-   [miembro m_pErrorInfo](../mfc/reference/cdaoexception-class.md#m_perrorinfo) contiene un puntero a un [CDaoErrorInfo](../mfc/reference/cdaoerrorinfo-structure.md) objeto que encapsula la información de error en la colección DAO de objetos de error asociados a la base de datos.  
  
-   [m_nAfxDaoError](../mfc/reference/cdaoexception-class.md#m_nafxdaoerror) contiene un código de error extendida de las clases DAO de MFC. Estos códigos de error, que tienen nombres de la forma **AFX_DAO_ERROR_XXX**, están documentados en el miembro de datos en `CDaoException`.  
  
-   [m_scode](../mfc/reference/cdaoexception-class.md#m_scode) contiene un OLE `SCODE` de DAO, si procede. Rara vez necesitará trabajar con este código de error, sin embargo. Por lo general más información está disponible en los otros dos miembros de datos. Ver el miembro de datos para obtener más información acerca de `SCODE` valores.  
  
 Información adicional sobre los errores DAO, el tipo de objeto DAO Error y la colección de errores de DAO está disponible en la clase [CDaoException](../mfc/reference/cdaoexception-class.md).  
  
##  <a name="_core_a_database_exception.2d.handling_example"></a> Un ejemplo de control de excepciones de base de datos  
 En el ejemplo siguiente se intenta construir una [CRecordset](../mfc/reference/crecordset-class.md)-objeto del montón con derivado la **nueva** operador y, a continuación, abra el conjunto de registros (para un origen de datos ODBC). Para obtener un ejemplo similar para las clases DAO, vea "Ejemplo de excepción DAO" a continuación.  
  
### <a name="odbc-exception-example"></a>Ejemplo de excepción ODBC  
 El [abierto](../mfc/reference/crecordset-class.md#open) función miembro podría producir una excepción (de tipo [CDBException](../mfc/reference/cdbexception-class.md) para las clases ODBC), por lo que esta código corchetes el **abierto** llame con un **intente**  bloque. La subsiguiente **catch** bloque detectará un `CDBException`. Puede examinar el objeto de excepción, denominado `e`, pero en este caso resulta suficiente para saber que ha fallado el intento de crear un conjunto de registros. El **catch** bloque muestra un cuadro de mensaje y limpia eliminando el objeto de conjunto de registros.  
  
 [!code-cpp[NVC_MFCDatabase#36](../mfc/codesnippet/cpp/exceptions-database-exceptions_1.cpp)]  
  
### <a name="dao-exception-example"></a>Ejemplo de excepción DAO  
 El ejemplo DAO es similar al ejemplo de ODBC, pero normalmente puede recuperar más tipos de información. El código siguiente también intenta abrir un conjunto de registros. Si ese intento inicia una excepción, puede examinar a un miembro de datos del objeto de excepción para obtener información de error. Como con el ejemplo anterior de ODBC, es probable que sea suficiente para saber que el intento de crear un conjunto de registros falló.  
  
 [!code-cpp[NVC_MFCDatabase#37](../mfc/codesnippet/cpp/exceptions-database-exceptions_2.cpp)]  
  
 Este código obtiene una cadena de mensaje de error de la [miembro m_pErrorInfo](../mfc/reference/cdaoexception-class.md#m_perrorinfo) miembro del objeto de excepción. MFC ocupa a este miembro cuando produce la excepción.  
  
 Para obtener una descripción de la información de error devuelta por un `CDaoException` de objetos, consulte las clases de [CDaoException](../mfc/reference/cdaoexception-class.md) y [CDaoErrorInfo](../mfc/reference/cdaoerrorinfo-structure.md).  
  
 Cuando se trabaja con bases de datos de Microsoft Jet (.mdb) y en la mayoría de los casos, cuando se trabaja con ODBC, habrá un único objeto de error. En el caso excepcional cuando está utilizando un origen de datos ODBC y hay varios errores, puede repetirse a través de la colección de errores de DAO en función del número de errores devueltos por [CDaoException::GetErrorCount](../mfc/reference/cdaoexception-class.md#geterrorcount). Cada vez que el bucle, llame a [CDaoException:: GetErrorInfo](../mfc/reference/cdaoexception-class.md#geterrorinfo) para rellenar la `m_pErrorInfo` miembro de datos.  
  
## <a name="see-also"></a>Vea también  
 [Control de excepciones](../mfc/exception-handling-in-mfc.md)

