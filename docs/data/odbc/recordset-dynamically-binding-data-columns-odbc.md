---
title: 'Conjunto de registros: Enlazar dinámicamente columnas de datos (ODBC)'
ms.date: 05/09/2019
helpviewer_keywords:
- ODBC recordsets [C++], binding columns dynamically
- data binding [C++], recordset columns
- recordsets [C++], binding data
- data binding [C++], columns in recordsets
- columns [C++], binding to recordsets
ms.assetid: bff67254-d953-4ae4-9716-91c348cb840b
ms.openlocfilehash: 456d999a056abc4c15f2dcf3b8774dfc86182272
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212932"
---
# <a name="recordset-dynamically-binding-data-columns-odbc"></a>Conjunto de registros: Enlazar dinámicamente columnas de datos (ODBC)

Este tema es aplicable a las clases ODBC de MFC.

Los conjuntos de registros administran el enlace de las columnas de tabla que se especifican en tiempo de diseño, pero hay casos en los que es posible que quiera enlazar columnas que desconoce en tiempo de diseño. En este tema se explica:

- [Cuándo es posible que quiera enlazar columnas de forma dinámica a un conjunto de registros](#_core_when_you_might_bind_columns_dynamically).

- [Cómo enlazar columnas de forma dinámica en tiempo de ejecución](#_core_how_to_bind_columns_dynamically).

> [!NOTE]
>  Este tema se aplica a objetos derivados de `CRecordset` donde no se haya implementado la obtención masiva de filas. Por lo general, si usa la obtención masiva de filas, las técnicas descritas no son recomendables. Para obtener más información sobre la obtención masiva de filas, vea [conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

##  <a name="when-you-might-bind-columns-dynamically"></a><a name="_core_when_you_might_bind_columns_dynamically"></a> Cuándo podría enlazar columnas de forma dinámica

> [!NOTE]
> El Asistente para consumidores ODBC de MFC no está disponible en Visual Studio 2019 ni en versiones posteriores. Aun así, puede crear un consumidor de forma manual.

En tiempo de diseño, el Asistente para aplicaciones MFC o el [Asistente para consumidores ODBC de MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md) (desde **Agregar clase**) crea clases de conjunto de registros en función de las tablas y columnas conocidas del origen de datos. Las bases de datos pueden cambiar entre el momento de diseñarlas y cuando la aplicación usa esas tablas y columnas en tiempo de ejecución. Usted u otro usuario puede agregar o quitar una tabla o una columna de una tabla de la que depende el conjunto de registros de la aplicación. Puede que esto no sea un problema para todas las aplicaciones de acceso a datos, pero si se trata de la suya, ¿cómo puede afrontar los cambios en el esquema de base de datos sin tener que rediseñar y volver a compilar? El propósito de este tema es responder esa pregunta.

En este tema se describe el caso más común en el que podría enlazar las columnas de forma dinámica: cuando se ha empezado con un conjunto de registros basado en un esquema de base de datos conocido y se quiere trabajar con columnas adicionales en tiempo de ejecución. Además, en el tema se da por supuesto que las columnas adicionales se asignan a miembros de datos de campo `CString`, el caso más común, aunque se proporcionan sugerencias para ayudarle a administrar otros tipos de datos.

Con una pequeña cantidad de código adicional, puede hacer lo siguiente:

- [Determinar qué columnas están disponibles en tiempo de ejecución](#_core_how_to_bind_columns_dynamically).

- [Enlazar columnas adicionales de forma dinámica al conjunto de registros, en tiempo de ejecución](#_core_adding_the_columns).

El conjunto de registros todavía contiene miembros de datos para las columnas que ya conocía en tiempo de diseño. También contiene una pequeña cantidad de código adicional que determina de forma dinámica si se han agregado columnas nuevas a la tabla de destino y, si es así, enlaza estas columnas nuevas a almacenamiento asignado de forma dinámica (en lugar de miembros de datos del conjunto de registros).

En este tema no se describen otros casos de enlace dinámico, como las tablas o columnas eliminadas. Para esos casos, tendrá que usar llamadas de API de ODBC más directamente. Para obtener información, vea la *referencia del programador* del SDK de ODBC en el CD de MSDN Library.

##  <a name="how-to-bind-columns-dynamically"></a><a name="_core_how_to_bind_columns_dynamically"></a> Cómo enlazar columnas de forma dinámica

Para enlazar columnas de forma dinámica, debe conocer (o poder determinar) los nombres de las columnas adicionales. También tendrá que asignar almacenamiento para los miembros de datos de campo adicionales, especificar sus nombres y sus tipos, y el número de columnas que se van a agregar.

En la descripción siguiente se mencionan dos conjuntos de registros diferentes. El primero es el conjunto de registros principal que selecciona los registros de la tabla de destino. El segundo es un conjunto de registros de columna especial que se usa para obtener información sobre las columnas de la tabla de destino.

###  <a name="general-process"></a><a name="_core_the_general_process"></a> Proceso general

En el nivel más general, siga estos pasos:

1. Cree el objeto de conjunto de registros principal.

   Opcionalmente, pase un puntero a un objeto `CDatabase` abierto o tenga la capacidad de proporcionar información de conexión al conjunto de registros de columna de alguna otra manera.

1. Siga los pasos para agregar columnas de forma dinámica.

   Vea el proceso que se describe en Adición de las columnas a continuación.

1. Abra el conjunto de registros principal.

   El conjunto de registros selecciona los registros y usa el intercambio de campos de registros (RFX) para enlazar las columnas estáticas (las que se asignan a miembros de datos de campo del conjunto de registros) y las columnas dinámicas (las que se asignan al almacenamiento adicional que se asigna).

###  <a name="adding-the-columns"></a><a name="_core_adding_the_columns"></a> Adición de las columnas

El enlace dinámico de las columnas agregadas en tiempo de ejecución requiere los pasos siguientes:

1. Determine en tiempo de ejecución qué columnas se encuentran en la tabla de destino. De esta información, se extrae una lista de las columnas que se han agregado a la tabla desde que se ha diseñado la clase del conjunto de registros.

   Un enfoque correcto consiste en usar una clase de conjunto de registros de columna diseñada para consultar el origen de datos para obtener información de columna para la tabla de destino (por ejemplo, el tipo de datos y el nombre de las columnas).

1. Proporcione almacenamiento para los nuevos miembros de datos de campo. Como la clase del conjunto de registros principal no tiene miembros de datos de campo para las columnas desconocidas, debe proporcionar un lugar para almacenar los nombres, los valores de resultado y, posiblemente, información de tipo de datos (si las columnas son de tipos de datos diferentes).

   Un enfoque consiste en crear una o varias listas dinámicas: una para los nombres de las columnas nuevas, otra para los valores de resultado y una tercera para sus tipos de datos (si es necesario). Estas listas, en concreto la de valores, proporcionan la información y el almacenamiento necesarios para el enlace. En la figura siguiente se ilustra la creación de las listas.

   ![Generar listas de columnas para enlazar dinámicamente](../../data/odbc/media/vc37w61.gif "Compilar listas de columnas para enlazarlas dinámicamente")<br/>
   Compilar listas de columnas para enlazarlas dinámicamente

1. Agregue una llamada de función RFX a la función `DoFieldExchange` del conjunto de registros principal para cada columna agregada. Estas llamadas RFX se encargan de capturar un registro, incluir las columnas adicionales y enlazar las columnas a miembros de datos del conjunto de registros o al almacenamiento que se les haya asignado de forma dinámica.

   Un enfoque consiste en agregar un bucle a la función `DoFieldExchange` del conjunto de registros principal que recorra la lista de las columnas nuevas y llame a la función RFX correspondiente para cada columna de la lista. En cada llamada RFX, pase un nombre de columna de la lista de nombres de columna y una ubicación de almacenamiento en el miembro correspondiente de la lista de valores de resultado.

###  <a name="lists-of-columns"></a><a name="_core_lists_of_columns"></a> Listas de columnas

Las cuatro listas con las que tiene que trabajar se muestran en la tabla siguiente.

|||
|-|-|
|**Columnas de la tabla actual**| (Lista 1 en la ilustración) Una lista de las columnas que están actualmente en la tabla del origen de datos. Es posible que esta lista coincida con la de columnas enlazadas actualmente en el conjunto de registros.|
|**Columnas enlazadas del conjunto de registros**| (Lista 2 en la ilustración) Una lista de las columnas enlazadas en el conjunto de registros. Estas columnas ya contienen instrucciones RFX en la función `DoFieldExchange`.|
|**Columnas para enlazar de forma dinámica**| (Lista 3 en la ilustración) Una lista de las columnas que están en la tabla pero no en el conjunto de registros. Son las columnas que quiere enlazar de forma dinámica.|
|**Valores de las columnas dinámicas**| (Lista 4 en la ilustración) Una lista que contiene almacenamiento para los valores recuperados de las columnas que se enlazan de forma dinámica. Los elementos de esta lista se corresponden, uno a uno, con los de Columnas para enlazar de forma dinámica.|

###  <a name="building-your-lists"></a><a name="_core_building_your_lists"></a> Creación de las listas

Con una estrategia general en mente, puede pasar a los detalles. En los procedimientos descritos en el resto de este tema se muestra cómo generar las listas mostradas en [Listas de columnas](#_core_lists_of_columns). Los procedimientos sirven de guía para que pueda:

- [Determinar los nombres de las columnas que no están en el conjunto de registros](#_core_determining_which_table_columns_are_not_in_your_recordset).

- [Proporcionar almacenamiento dinámico para las columnas recién agregadas a la tabla](#_core_providing_storage_for_the_new_columns).

- [Agregar de forma dinámica llamadas RFX para las nuevas columnas](#_core_adding_rfx_calls_to_bind_the_columns).

###  <a name="determining-which-table-columns-are-not-in-your-recordset"></a><a name="_core_determining_which_table_columns_are_not_in_your_recordset"></a> Determinación de las columnas de tabla que no están en el conjunto de registros

Cree una lista (Columnas enlazadas del conjunto de registros, como en la Lista 2 de la ilustración) que contenga una lista de las columnas ya enlazadas en el conjunto de registros principal. Después, cree una lista (Columnas para enlazar de forma dinámica, derivada de Columnas de la tabla actual y Columnas enlazadas del conjunto de registros) que contenga los nombres de columna que están en la tabla del origen de datos, pero no en el conjunto de registros principal.

##### <a name="to-determine-the-names-of-columns-not-in-the-recordset-columns-to-bind-dynamically"></a>Para determinar los nombres de las columnas que no están en el conjunto de registros (Columnas para enlazar de forma dinámica)

1. Cree una lista (Columnas enlazadas del conjunto de registros) de las columnas ya enlazadas en el conjunto de registros principal.

   Un enfoque consiste en crear Columnas enlazadas del conjunto de registros en tiempo de diseño. Para obtener estos nombres, puede examinar de forma visual las llamadas de función RFX en la función `DoFieldExchange` del conjunto de registros. Después, establezca la lista como una matriz inicializada con los nombres.

   Por ejemplo, en la ilustración se muestra Columnas enlazadas del conjunto de registros (Lista 2) con tres elementos. En Columnas enlazadas del conjunto de registros falta la columna Phone que se muestra en Columnas de la tabla actual (Lista 1).

1. Compare Columnas de la tabla actual y Columnas enlazadas del conjunto de registros para crear una lista (Columnas para enlazar de forma dinámica) de las columnas que todavía no están enlazadas en el conjunto de registros principal.

   Un enfoque consiste en recorrer en bucle la lista de columnas de la tabla en tiempo de ejecución (Columnas de la tabla actual) y la de columnas ya enlazadas en el conjunto de registros (Columnas enlazadas del conjunto de registros) en paralelo. En Columnas para enlazar de forma dinámica, incluya todos los nombres de Columnas de la tabla actual que no aparezcan en Columnas enlazadas del conjunto de registros.

   Por ejemplo, en la ilustración se muestra Columnas para enlazar de forma dinámica (Lista 3) con un elemento: la columna Phone encontrada en Columnas de la tabla actual (Lista 1) pero no en Columnas enlazadas del conjunto de registros (Lista 2).

1. Cree una lista Valores de las columnas dinámicas (como en la Lista 4 de la ilustración) para almacenar los valores de datos correspondientes a cada nombre de columna almacenado en la lista de columnas que se van a enlazar de forma dinámica (Columnas para enlazar de forma dinámica).

   Los elementos de esta lista desempeñan el rol de miembros de datos de campo nuevos del conjunto de registros. Son las ubicaciones de almacenamiento a las que se enlazan las columnas dinámicas. Para obtener descripciones de las listas, vea [Listas de columnas](#_core_lists_of_columns).

###  <a name="providing-storage-for-the-new-columns"></a><a name="_core_providing_storage_for_the_new_columns"></a> Proporcionar almacenamiento para las nuevas columnas

A continuación, defina ubicaciones de almacenamiento para las columnas que se van a enlazar de forma dinámica. La idea es proporcionar un elemento de lista en el que almacenar el valor de cada columna. Estas ubicaciones de almacenamiento son similares a las variables miembro del conjunto de registros, que almacenan las columnas enlazadas con normalidad.

#### <a name="to-provide-dynamic-storage-for-new-columns-dynamic-column-values"></a>Para proporcionar almacenamiento dinámico para las columnas nuevas (Valores de las columnas dinámicas)

1. Cree Valores de las columnas dinámicas, en paralelo a Columnas para enlazar de forma dinámica, para contener el valor de los datos de cada columna.

   Por ejemplo, en la ilustración se muestran los valores de columna dinámica (lista 4) con un elemento: un `CString` objeto que contiene el número de teléfono real para el registro actual: "555-1212".

   En el caso más común, Valores de las columnas dinámicas tiene elementos de tipo `CString`. Si trabaja con columnas de diferentes tipos de datos, necesita una lista que pueda contener elementos de varios tipos.

El resultado de los procedimientos anteriores es dos listas principales: columnas a enlazar dinámicamente que contienen los nombres de las columnas y los valores de columnas dinámicas que contienen los valores de las columnas del registro actual.

> [!TIP]
> Si las columnas nuevas no son todas del mismo tipo de datos, es posible que quiera una lista paralela adicional que contenga elementos que definan de algún modo el tipo de cada elemento correspondiente en la lista de columnas. (Si quiere, para esto puede usar los valores AFX_RFX_BOOL, AFX_RFX_BYTE y así sucesivamente. Estas constantes se definen en AFXDB. H.) elija un tipo de lista en función de cómo represente los tipos de datos de las columnas.

###  <a name="adding-rfx-calls-to-bind-the-columns"></a><a name="_core_adding_rfx_calls_to_bind_the_columns"></a> Adición de llamadas RFX para enlazar las columnas

Por último, para preparar el enlace dinámico, coloque llamadas RFX para las nuevas columnas en la función `DoFieldExchange`.

##### <a name="to-dynamically-add-rfx-calls-for-new-columns"></a>Para agregar llamadas RFX de forma dinámica para las columnas nuevas

1. En la función miembro `DoFieldExchange` del conjunto de registros principal, agregue código que recorra en bucle la lista de columnas nuevas (Columnas para enlazar de forma dinámica). En cada bucle, extraiga un nombre de columna desde Columnas para enlazar de forma dinámica y un valor de resultado para la columna desde Valores de las columnas dinámicas. Pase estos elementos a una llamada de función RFX adecuada para el tipo de datos de la columna. Para obtener descripciones de las listas, vea [Listas de columnas](#_core_lists_of_columns).

En el caso habitual, en las llamadas de función `RFX_Text` se extraen objetos `CString` de las listas, como se muestra en las líneas de código siguientes, donde Columnas para enlazar de forma dinámica es un elemento `CStringList` denominado `m_listName` y Valores de las columnas dinámicas es un elemento `CStringList` denominado `m_listValue`:

```cpp
RFX_Text( pFX,
            m_listName.GetNext( posName ),
            m_listValue.GetNext( posValue ));
```

Para más información sobre las funciones RFX, vea [Macros y variables globales](../../mfc/reference/mfc-macros-and-globals.md) en la *Referencia de la biblioteca de clases*.

> [!TIP]
> Si las columnas nuevas son de tipos de datos distintos, use una instrucción switch en el bucle para llamar a la función RFX adecuada para cada tipo.

Cuando el marco de trabajo llama a `DoFieldExchange` durante el proceso `Open` para enlazar las columnas al conjunto de registros, las llamadas RFX para las columnas estáticas enlazan esas columnas. Después, el bucle llama repetidamente a las funciones RFX para las columnas dinámicas.

## <a name="see-also"></a>Consulte también

[Conjunto de registros (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Conjunto de registros: Trabajar con grandes elementos de datos (ODBC)](../../data/odbc/recordset-working-with-large-data-items-odbc.md)
