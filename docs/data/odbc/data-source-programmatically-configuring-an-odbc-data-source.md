---
title: 'Origen de datos: Configurar un origen de datos ODBC mediante programación'
ms.date: 11/04/2016
f1_keywords:
- SQLConfigDataSource
helpviewer_keywords:
- ODBC data sources, configuring
- SQLConfigDataSource method example
- ODBC connections, configuring
- configuring ODBC data sources
ms.assetid: b8cabe9b-9e12-4d73-ae36-7cb12dee3213
ms.openlocfilehash: ba0224d166795b34d636ace610265e115209e49c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358857"
---
# <a name="data-source-programmatically-configuring-an-odbc-data-source"></a>Origen de datos: Configurar un origen de datos ODBC mediante programación

En este tema se explica cómo configurar los nombres de origen de datos de Open Database Connectivity (ODBC) mediante programación. Esto le da flexibilidad para tener acceso a los datos sin forzar al usuario a usar explícitamente el Administrador ODBC u otros programas para especificar los nombres de los orígenes de datos.

Normalmente, un usuario ejecuta administrador ODBC para crear un origen de datos si el sistema de administración de bases de datos (DBMS) asociado admite esta operación.

Al crear un origen de datos ODBC de Microsoft Access a través del Administrador ODBC, se le ofrecen dos opciones: puede seleccionar un archivo .mdb existente o puede crear un nuevo archivo .mdb. No hay ninguna forma mediante programación de crear el archivo .mdb desde la aplicación ODBC de MFC. Por lo tanto, si la aplicación requiere que coloque datos en un origen de datos de Microsoft Access (archivo .mdb), lo más probable es que desee tener un archivo .mdb vacío que puede usar o copiar siempre que lo necesite.

Sin embargo, muchos DBMS permiten la creación de orígenes de datos mediante programación. Algunos orígenes de datos mantienen una especificación de directorio para las bases de datos. Es decir, un directorio es el origen de datos y cada tabla dentro del origen de datos se almacena en un archivo independiente (en el caso de dBASE, cada tabla es un archivo .dbf). Los controladores para otras bases de datos ODBC, como Microsoft Access y SQL Server, requieren que se cumplan algunos criterios específicos antes de que se pueda establecer un origen de datos. Por ejemplo, al usar el controlador ODBC de SQL ServerSQL Server , debe haber establecido un equipo de SQL ServerSQL Server .

## <a name="sqlconfigdatasource-example"></a><a name="_core_sqlconfigdatasource_example"></a>Ejemplo de SQLConfigDataSource

En el ejemplo `::SQLConfigDataSource` siguiente se utiliza la función DE API ODBC para crear un nuevo origen de datos de Excel denominado Nuevo origen de datos de Excel:

```
SQLConfigDataSource(NULL,ODBC_ADD_DSN, "Excel Files (*.xls)",
                   "DSN=New Excel Data Source\0"
                   "Description=New Excel Data Source\0"
                   "FileType=Excel\0"
                   "DataDirectory=C:\\EXCELDIR\0"
                   "MaxScanRows=20\0");
```

Tenga en cuenta que el origen de datos es en realidad un directorio (C:-EXCELDIR); este directorio debe existir. El controlador de Excel utiliza directorios como sus orígenes de datos y archivos como tablas individuales (una tabla por archivo .xls).

Para obtener más información acerca de la creación de tablas, vea Origen de [datos: creación de una tabla mediante programación en un origen](../../data/odbc/data-source-programmatically-creating-a-table-in-an-odbc-data-source.md)de datos ODBC .

En la siguiente información se describen los `::SQLConfigDataSource` parámetros que deben pasarse a la función de API ODBC. Para `::SQLConfigDataSource`utilizar , debe incluir el archivo de encabezado Odbcinst.h y utilizar la biblioteca de importación Odbcinst.lib. Además, Odbccp32.dll debe estar en la ruta de acceso en tiempo de ejecución (o Odbcinst.dll para 16 bits).

Puede crear un nombre de origen de datos ODBC mediante el Administrador ODBC o una utilidad similar. Sin embargo, a veces es deseable crear un nombre de origen de datos directamente desde la aplicación para obtener acceso sin necesidad de que el usuario ejecute una utilidad independiente.

Administrador ODBC (normalmente instalado en el Panel de control) crea un nuevo origen de datos colocando entradas en el registro de Windows (o, para 16 bits, en el archivo Odbc.ini). El Administrador de controladores ODBC consulta este archivo para obtener la información necesaria sobre el origen de datos. Es importante saber qué información debe colocarse en el registro porque debe `::SQLConfigDataSource`proporcionarla con la llamada a .

Aunque esta información se puede escribir `::SQLConfigDataSource`directamente en el registro sin usar , cualquier aplicación que lo haga se basa en la técnica actual que el Administrador de controladores utiliza para mantener sus datos. Si una revisión posterior del Administrador de controladores ODBC implementa el mantenimiento de registros sobre orígenes de datos de una manera diferente, se interrumpe cualquier aplicación que use esta técnica. Por lo general, es recomendable utilizar una función de API cuando se proporciona una. Por ejemplo, el código es portátil de 16 bits `::SQLConfigDataSource` a 32 bits si utiliza la función, porque la función escribe correctamente en el archivo Odbc.ini o en el registro.

## <a name="sqlconfigdatasource-parameters"></a><a name="_core_sqlconfigdatasource_parameters"></a>Parámetros SQLConfigDataSource

A continuación se explican `::SQLConfigDataSource` los parámetros de la función. Gran parte de la información se toma de la *referencia del programador* de la API ODBC proporcionada con Visual C++ versión 1.5 y versiones posteriores.

### <a name="function-prototype"></a><a name="_core_function_prototype"></a>Prototipo de función

```
BOOL SQLConfigDataSource(HWND hwndParent,UINT fRequest, LPCSTR lpszDriver, LPCSTR lpszAttributes);
```

### <a name="remarks"></a>Observaciones

#### <a name="parameters-and-usage"></a><a name="_core_parameters_and_usage"></a>Parámetros y uso

*hwndParent*<br/>
La ventana especificada como propietario de los cuadros de diálogo que el Administrador de controladores ODBC o el controlador ODBC específico crea para obtener información adicional del usuario sobre el nuevo origen de datos. Si el parámetro *lpszAttributes* no proporciona suficiente información, aparece un cuadro de diálogo. El *hwndParent* parámetro podría ser NULL.

*lpszDriver*<br/>
La descripción del controlador. Este es el nombre que se presenta a los usuarios en lugar del nombre del controlador físico (el archivo DLL).

*lpszAttributes*<br/>
Lista de atributos con el formato "nombreclave-valor". Estas cadenas están separadas por terminadores nulos con dos terminadores nulos consecutivos al final de la lista. Estos atributos son principalmente entradas específicas del controlador predeterminadas, que van al registro para el nuevo origen de datos. Una clave importante que no se menciona en la referencia de la API ODBC para esta función es "DSN" ("nombre del origen de datos"), que especifica el nombre del nuevo origen de datos. El resto de las entradas son específicas del controlador para el nuevo origen de datos. A menudo no es necesario proporcionar todas las entradas porque el controlador puede solicitar al usuario cuadros de diálogo para los nuevos valores. (Establecer *hwndParent* en NULL para hacer esto.) Es posible que desee proporcionar explícitamente los valores predeterminados para que no se solicite al usuario.

#### <a name="to-determine-the-description-of-a-driver-for-the-lpszdriver-parameter-using-odbc-administrator"></a>Para determinar la descripción de un controlador para el parámetro lpszDriver mediante el Administrador ODBC

1. Ejecute Administrador ODBC.

1. Haga clic en **Agregar**.

Esto le da una lista de los controladores instalados y sus descripciones. Utilice esta descripción como parámetro *lpszDriver.* Tenga en cuenta que utiliza toda la descripción, como "Archivos de Excel (*.xls)", incluida la extensión de nombre de archivo y los paréntesis si existen en la descripción.

Como alternativa, puede examinar el registro (o, para 16 bits, el archivo Odbcinst.ini), que contiene una lista de todas las entradas y descripciones del controlador bajo la clave del Registro "Controladores ODBC" (o la sección [Controladores ODBC] en Odbcinst.ini).

Una forma de encontrar los nombres de clave y los valores para el parámetro *lpszAttributes* es examinar el archivo Odbc.ini para un origen de datos ya configurado (quizás uno que ha sido configurado por el Administrador ODBC).

#### <a name="to-find-keynames-and-values-for-the-lpszattributes-parameter"></a>Para buscar nombres y valores para el parámetro lpszAttributes

1. Ejecute el editor del registro de Windows (o, durante 16 bits, abra el archivo Odbc.ini).

1. Busque la información de orígenes de datos ODBC mediante una de las siguientes opciones:

   - Para 32 bits, busque la clave **HKEY_CURRENT_USER, Software, ODBC y ODBC. Orígenes de datos INI-ODBC** en el panel izquierdo.

      El panel derecho enumera las entradas del formulario: "pub: REG_SZ: * \<* *\<nombre *del origen de datos>", donde el nombre del origen de datos>es un origen de datos que ya se ha configurado con la configuración deseada para el controlador que va a utilizar. Seleccione el origen de datos que desee, por ejemplo, SQL Server. Los elementos que siguen a la cadena "pub:" son, en orden, el nombre de clave y el valor que se va a utilizar en el parámetro *lpszAttributes.*

   - Para 16 bits, busque la sección en el*\< *archivo Odbc.ini marcada por [ nombre de origen de datos>].

      Las líneas que siguen a esta línea tienen la forma "nombreclave-valor". Estas son exactamente las entradas que se van a utilizar en el parámetro *lpszAttributes.*

También es posible que desee examinar la documentación para el controlador específico que va a utilizar. Puede encontrar información útil en la Ayuda en línea para el controlador, a la que puede acceder ejecutando el Administrador ODBC. Estos archivos de Ayuda se colocan normalmente en el directorio WINDOWS-SYSTEM para Windows NT, Windows 3.1 o Windows 95.

#### <a name="to-obtain-online-help-for-your-odbc-driver"></a>Para obtener ayuda en línea para el controlador ODBC

1. Ejecute Administrador ODBC.

1. Haga clic en **Agregar**.

1. Seleccione el nombre del controlador.

1. Haga clic en **OK**.

Cuando el Administrador ODBC muestre la información para crear un nuevo origen de datos para ese controlador en particular, haga clic en **Ayuda**. Esto abre el archivo de ayuda para ese controlador en particular, que generalmente contiene información importante sobre el uso del controlador.

## <a name="see-also"></a>Consulte también

[Origen de datos (ODBC)](../../data/odbc/data-source-odbc.md)
