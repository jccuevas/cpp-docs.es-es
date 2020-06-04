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
ms.openlocfilehash: 894960338a7e8c293054ade00e0cdf3295648bb7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366623"
---
# <a name="exceptions-database-exceptions"></a>Excepciones: Excepciones de base de datos

En este artículo se explica cómo controlar las excepciones de base de datos. La mayor parte del material de este artículo se aplica si está trabajando con las clases MFC para Open Database Connectivity (ODBC) o las clases MFC para objetos de acceso a datos (DAO). El material específico de uno u otro modelo se marca explícitamente. Contenido de los temas:

- [Enfoques para el control de excepciones](#_core_approaches_to_exception_handling)

- [Un ejemplo de control de excepciones de base de datos](#_core_a_database_exception.2d.handling_example)

## <a name="approaches-to-exception-handling"></a><a name="_core_approaches_to_exception_handling"></a>Enfoques para el manejo de excepciones

El enfoque es el mismo si está trabajando con DAO (obsoleto) u ODBC.

Siempre debe escribir controladores de excepciones para controlar condiciones excepcionales.

El enfoque más pragmático para detectar excepciones de base de datos es probar la aplicación con escenarios de excepción. Determine las excepciones probables que pueden producirse para una operación en el código y fuerce la excepción. A continuación, examine la salida de seguimiento para ver qué excepción se produce o examine la información de error devuelta en el depurador. Esto le permite saber qué códigos de retorno verá para los escenarios de excepción que está utilizando.

### <a name="error-codes-used-for-odbc-exceptions"></a>Códigos de error utilizados para excepciones ODBC

Además de los códigos de retorno definidos por el marco de trabajo, que tienen nombres del formulario **AFX_SQL_ERROR_XXX**, [algunas CDBExceptions](../mfc/reference/cdbexception-class.md) se basan en códigos de retorno [ODBC.](../data/odbc/odbc-basics.md) Los códigos de retorno para estas excepciones tienen nombres del formulario **SQL_ERROR_XXX**.

Los códigos de retorno (definidos por el marco y definidos por ODBC) que las clases de base de datos pueden devolver están documentados en el miembro de datos [m_nRetCode](../mfc/reference/cdbexception-class.md#m_nretcode) de la clase `CDBException`. Información adicional acerca de los códigos de retorno definidos por ODBC está disponible en la *referencia del programador del* SDK de ODBC en MSDN Library.

### <a name="error-codes-used-for-dao-exceptions"></a>Códigos de error utilizados para excepciones DAO

Para las excepciones DAO, normalmente hay más información disponible. Puede tener acceso a la información de error a través de tres miembros de datos de un [objeto CDaoException](../mfc/reference/cdaoexception-class.md) capturado:

- [m_pErrorInfo](../mfc/reference/cdaoexception-class.md#m_perrorinfo) contiene un puntero a un [CDaoErrorInfo](../mfc/reference/cdaoerrorinfo-structure.md) objeto que encapsula la información de error en la colección de DAO de objetos de error asociados a la base de datos.

- [m_nAfxDaoError](../mfc/reference/cdaoexception-class.md#m_nafxdaoerror) contiene un código de error extendido de las clases DAO de MFC. Estos códigos de error, **AFX_DAO_ERROR_XXX**que tienen nombres del formulario `CDaoException`AFX_DAO_ERROR_XXX , se documentan en el miembro de datos en .

- [m_scode](../mfc/reference/cdaoexception-class.md#m_scode) contiene un **OLE SCODE** de DAO, si procede. Sin embargo, rara vez tendrá que trabajar con este código de error. Por lo general, hay más información disponible en los otros dos miembros de datos. Consulte el miembro de datos para obtener más información sobre los valores **SCODE.**

La información adicional sobre los errores DAO, el tipo de objeto Error de DAO y la colección Errores de DAO está disponible en la clase [CDaoException](../mfc/reference/cdaoexception-class.md).

## <a name="a-database-exception-handling-example"></a><a name="_core_a_database_exception.2d.handling_example"></a>Un ejemplo de control de excepciones de base de datos

En el ejemplo siguiente se intenta construir un [CRecordset](../mfc/reference/crecordset-class.md)-objeto derivado en el montón con el **operador new** y, a continuación, abrir el conjunto de registros (para un origen de datos ODBC). Para obtener un ejemplo similar para las clases DAO, vea "Ejemplo de excepción DAO" a continuación.

### <a name="odbc-exception-example"></a>Ejemplo de excepción ODBC

El [Open](../mfc/reference/crecordset-class.md#open) función miembro podría producir una excepción (de tipo [CDBException](../mfc/reference/cdbexception-class.md) para las clases ODBC), por lo que este código entre corchetes la `Open` llamada con un bloque **try.** El bloque **catch** posterior `CDBException`capturará un archivo . Puede examinar el propio objeto `e`de excepción, llamado , pero en este caso es suficiente saber que el intento de crear un conjunto de registros ha fallado. El bloque **catch** muestra un cuadro de mensaje y se limpia eliminando el objeto de conjunto de registros.

[!code-cpp[NVC_MFCDatabase#36](../mfc/codesnippet/cpp/exceptions-database-exceptions_1.cpp)]

### <a name="dao-exception-example"></a>Ejemplo de excepción DAO

El ejemplo dao es similar al ejemplo de ODBC, pero normalmente puede recuperar más tipos de información. El código siguiente también intenta abrir un conjunto de registros. Si ese intento produce una excepción, puede examinar un miembro de datos del objeto de excepción para obtener información de error. Al igual que con el ejemplo ODBC anterior, probablemente sea suficiente saber que se produjo un error en el intento de crear un conjunto de registros.

[!code-cpp[NVC_MFCDatabase#37](../mfc/codesnippet/cpp/exceptions-database-exceptions_2.cpp)]

Este código obtiene una cadena de mensaje de error del [m_pErrorInfo](../mfc/reference/cdaoexception-class.md#m_perrorinfo) miembro del objeto de excepción. MFC rellena este miembro cuando produce la excepción.

Para obtener una explicación de `CDaoException` la información de error devuelta por un objeto, vea las clases [CDaoException](../mfc/reference/cdaoexception-class.md) y [CDaoErrorInfo](../mfc/reference/cdaoerrorinfo-structure.md).

Cuando se trabaja con bases de datos de Microsoft Jet (.mdb) y, en la mayoría de los casos, cuando se trabaja con ODBC, solo habrá un objeto de error. En raras ocasiones, cuando se utiliza un origen de datos ODBC y hay varios errores, puede recorrer en bucle la colección Errors de DAO en función del número de errores devueltos por [CDaoException::GetErrorCount](../mfc/reference/cdaoexception-class.md#geterrorcount). Cada vez a través del bucle, llame a [CDaoException::GetErrorInfo](../mfc/reference/cdaoexception-class.md#geterrorinfo) para rellenar el `m_pErrorInfo` miembro de datos.

## <a name="see-also"></a>Consulte también

[Control de excepciones](../mfc/exception-handling-in-mfc.md)
