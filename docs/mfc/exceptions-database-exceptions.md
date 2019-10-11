---
title: 'Excepciones: Excepciones de base de datos'
ms.date: 09/17/2019
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
ms.openlocfilehash: c279c5b788cc7bd8a68fe36128c116d8df91c2eb
ms.sourcegitcommit: 2f96e2fda591d7b1b28842b2ea24e6297bcc3622
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2019
ms.locfileid: "71095820"
---
# <a name="exceptions-database-exceptions"></a>Excepciones: Excepciones de base de datos

En este artículo se explica cómo controlar las excepciones de la base de datos. La mayor parte del material de este artículo se aplica tanto si trabaja con las clases MFC para la conectividad abierta de bases de datos (ODBC) como para las clases MFC para objetos de acceso a datos (DAO). El material específico de uno u otro modelo se marca explícitamente. Entre los temas se incluyen los siguientes:

- [Enfoques para el control de excepciones](#_core_approaches_to_exception_handling)

- [Ejemplo de control de excepciones de base de datos](#_core_a_database_exception.2d.handling_example)

##  <a name="_core_approaches_to_exception_handling"></a>Enfoques para el control de excepciones

El enfoque es el mismo si está trabajando con DAO (obsoleto) u ODBC.

Siempre debe escribir controladores de excepciones para controlar condiciones excepcionales.

El enfoque más pragmático para detectar excepciones de base de datos es probar la aplicación con escenarios de excepción. Determinar las posibles excepciones que se pueden producir para una operación en el código y forzar que se produzca la excepción. A continuación, examine la salida del seguimiento para ver qué excepción se produce o examine la información de error devuelta en el depurador. Esto le permite saber qué códigos de retorno verá para los escenarios de excepción que está usando.

### <a name="error-codes-used-for-odbc-exceptions"></a>Códigos de error usados para las excepciones de ODBC

Además de los códigos de retorno definidos por el marco de trabajo, que tienen nombres con el formato **AFX_SQL_ERROR_XXX**, algunos [CDBExceptions](../mfc/reference/cdbexception-class.md) se basan en códigos de retorno de [ODBC](../data/odbc/odbc-basics.md) . Los códigos de retorno para tales excepciones tienen nombres con el formato **SQL_ERROR_XXX**.

Los códigos de retorno (definidos por el marco y definidos por ODBC) que las clases de base de datos pueden devolver están documentados en el miembro de datos [m_nRetCode](../mfc/reference/cdbexception-class.md#m_nretcode) de la clase `CDBException`. La información adicional sobre los códigos de retorno definidos por ODBC está disponible en la *Referencia del programador* del SDK de ODBC en MSDN Library.

### <a name="error-codes-used-for-dao-exceptions"></a>Códigos de error usados para excepciones DAO

En el caso de las excepciones DAO, hay más información disponible normalmente. Puede tener acceso a la información de error a través de tres miembros de datos de un objeto [CDaoException](../mfc/reference/cdaoexception-class.md) detectado:

- [m_pErrorInfo](../mfc/reference/cdaoexception-class.md#m_perrorinfo) contiene un puntero a un objeto [cdaoerrorinfo (](../mfc/reference/cdaoerrorinfo-structure.md) que encapsula la información de error en la colección de objetos de error de DAO asociada a la base de datos.

- [m_nAfxDaoError](../mfc/reference/cdaoexception-class.md#m_nafxdaoerror) contiene un código de error extendido de las clases DAO de MFC. Estos códigos de error, que tienen nombres con el formato **AFX_DAO_ERROR_XXX**, se documentan en el miembro `CDaoException`de datos en.

- [m_scode](../mfc/reference/cdaoexception-class.md#m_scode) contiene un OLE **SCODE** de DAO, si procede. No obstante, rara vez necesitará trabajar con este código de error. Normalmente, hay más información disponible en los otros dos miembros de datos. Vea el miembro de datos para obtener más información sobre los valores **SCODE** .

En la clase [CDaoException](../mfc/reference/cdaoexception-class.md)se ofrece información adicional acerca de los errores Dao, el tipo de objeto de error Dao y la colección de errores DAO.

##  <a name="_core_a_database_exception.2d.handling_example"></a>Ejemplo de control de excepciones de base de datos

En el ejemplo siguiente se intenta construir un objeto derivado de [CRecordset](../mfc/reference/crecordset-class.md)en el montón con el operador **New** y, a continuación, se abre el conjunto de registros (para un origen de datos ODBC). Para obtener un ejemplo similar de las clases DAO, vea "ejemplo de excepción DAO" a continuación.

### <a name="odbc-exception-example"></a>Ejemplo de excepción ODBC

La función miembro [Open](../mfc/reference/crecordset-class.md#open) podría producir una excepción (de tipo [CDBException](../mfc/reference/cdbexception-class.md) para las clases ODBC), por lo que este código corchete la `Open` llamada con un bloque **try** . El bloque **catch** subsiguiente detectará un `CDBException`. Podría examinar el propio objeto de excepción, llamado `e`, pero en este caso basta con saber que se ha producido un error en el intento de crear un conjunto de registros. El bloque **catch** muestra un cuadro de mensaje y limpia mediante la eliminación del objeto de conjunto de registros.

[!code-cpp[NVC_MFCDatabase#36](../mfc/codesnippet/cpp/exceptions-database-exceptions_1.cpp)]

### <a name="dao-exception-example"></a>Ejemplo de excepción DAO

El ejemplo de DAO es similar al ejemplo de ODBC, pero normalmente puede recuperar más tipos de información. El código siguiente también intenta abrir un conjunto de registros. Si ese intento produce una excepción, puede examinar un miembro de datos del objeto de excepción para obtener información sobre el error. Al igual que en el ejemplo de ODBC anterior, es bastante probable que sepa que se produjo un error al intentar crear un conjunto de registros.

[!code-cpp[NVC_MFCDatabase#37](../mfc/codesnippet/cpp/exceptions-database-exceptions_2.cpp)]

Este código obtiene una cadena de mensaje de error del miembro [m_pErrorInfo](../mfc/reference/cdaoexception-class.md#m_perrorinfo) del objeto de excepción. MFC rellena este miembro cuando produce la excepción.

Para obtener una descripción de la información de error devuelta por un `CDaoException` objeto, vea las clases [CDaoException](../mfc/reference/cdaoexception-class.md) y [cdaoerrorinfo (](../mfc/reference/cdaoerrorinfo-structure.md).

Cuando se trabaja con bases de datos de Microsoft Jet (. mdb) y, en la mayoría de los casos, cuando se trabaja con ODBC, solo habrá un objeto de error. En el caso excepcional de que utilice un origen de datos ODBC y haya varios errores, puede recorrer en bucle la colección de errores de DAO en función del número de errores devueltos por [CDaoException:: GetErrorCount](../mfc/reference/cdaoexception-class.md#geterrorcount). Cada vez a través del bucle, llame a [CDaoException:: GetErrorInfo](../mfc/reference/cdaoexception-class.md#geterrorinfo) para rellenar el `m_pErrorInfo` miembro de datos.

## <a name="see-also"></a>Vea también

[Control de excepciones](../mfc/exception-handling-in-mfc.md)
