---
title: Conjunto de registros dinámicos
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC recordsets, dynasets
- ODBC cursor library [ODBC], dynasets
- keyset-driven cursors in dynasets
- cursors [ODBC], keyset-driven cursors in dynasets
- cursor library [ODBC], dynaset availability
- recordsets [C++], dynasets
- dynasets
ms.assetid: 2867e6be-208e-4fe7-8bbe-b8697cb1045c
ms.openlocfilehash: ed7098600126005978c8b017e7db378fca4c1a68
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213244"
---
# <a name="dynaset"></a>Conjunto de registros dinámicos

En este tema se describen los conjuntos de registros dinámicos y se describe su [disponibilidad](#_core_availability_of_dynasets).

> [!NOTE]
>  Este tema se aplica a las clases ODBC de MFC, incluido [CRecordset](../../mfc/reference/crecordset-class.md). Para obtener información sobre los conjuntos de registros dinámicos en las clases DAO, vea [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md). Con DAO, puede abrir conjuntos de registros de tipo Dynaset.

Un Dynaset es un conjunto de registros con propiedades dinámicas. Durante su duración, un objeto de conjunto de registros en modo Dynaset (normalmente denominado Dynaset) permanece sincronizado con el origen de datos de la siguiente manera. En un entorno multiusuario, otros usuarios pueden editar o eliminar registros que se encuentran en el conjunto de registros dinámicos o agregar registros a la tabla que representa el Dynaset. Los registros que se agregan a la aplicación o se eliminan del conjunto de registros se reflejan en el Dynaset. Los registros que otros usuarios agreguen a la tabla no se verán reflejados en el conjunto de registros dinámicos hasta que se vuelva a generar el Dynaset llamando a su función miembro `Requery`. Cuando otros usuarios eliminan registros, el código MFC omite las eliminaciones en el conjunto de registros. Los cambios de edición de otros usuarios en los registros existentes se reflejan en el conjunto de registros dinámicos en cuanto se desplaza al registro afectado.

Del mismo modo, las modificaciones realizadas en los registros de un conjunto de registros dinámico se reflejan en los conjuntos de registros dinámicos que usan otros usuarios. Los registros que agregue no se reflejarán en los conjuntos de registros dinámicos de otros usuarios hasta que reconsulten su dynasets. Los registros que elimine se marcan como "eliminados" en los conjuntos de registros de otros usuarios. Si tiene varias conexiones a la misma base de datos (varios objetos `CDatabase`), los conjuntos de registros asociados a esas conexiones tienen el mismo estado que los conjuntos de registros de otros usuarios.

Los dynasets son más útiles cuando los datos deben ser dinámicos, como (por ejemplo,) en un sistema de reserva de una línea aérea.

> [!NOTE]
> Para usar dynasets, debe tener un controlador ODBC para el origen de datos que admita dynasets y no se debe cargar la biblioteca de cursores ODBC. Para obtener más información, vea [Availability of dynasets](#_core_availability_of_dynasets).

Para especificar que un conjunto de registros es un Dynaset, pase `CRecordset::dynaset` como primer parámetro a la función miembro `Open` del objeto de conjunto de registros.

> [!NOTE]
> En el caso de los conjuntos de registros dinámicos actualizables, el controlador ODBC debe admitir instrucciones Update posicionadas o la función de la API de ODBC `::SQLSetPos`. Si se admiten ambos, MFC utiliza `::SQLSetPos` para mayor eficacia.

##  <a name="availability-of-dynasets"></a><a name="_core_availability_of_dynasets"></a>Disponibilidad de dynasets

Las clases de base de datos MFC admiten dynasets si se cumplen los siguientes requisitos:

- El archivo DLL de la biblioteca de cursores ODBC no debe estar en uso para este origen de datos.

   Si se utiliza la biblioteca de cursores, se enmascara parte de la funcionalidad del controlador ODBC subyacente que es necesaria para la compatibilidad con conjuntos de registros dinámicos. Si desea usar dynasets (y el controlador ODBC tiene la funcionalidad necesaria para los dynasets, tal y como se describe en el resto de esta sección), puede hacer que MFC no cargue la biblioteca de cursores al crear un objeto de `CDatabase`. Para obtener más información, vea [ODBC](../../data/odbc/odbc-basics.md) y la función [OpenEx](../../mfc/reference/cdatabase-class.md#openex) o [Open](../../mfc/reference/cdatabase-class.md#open) miembro de la clase `CDatabase`.

   En la terminología de ODBC, los conjuntos de registros dinámicos y las instantáneas se denominan cursores. Un cursor es un mecanismo que se usa para realizar un seguimiento de su posición en un conjunto de registros.

- El controlador ODBC para el origen de datos debe ser compatible con los cursores controlados por conjunto de claves.

   Los cursores controlados por conjunto de claves administran los datos de una tabla al obtener y almacenar un conjunto de claves. Las claves se utilizan para obtener los datos actuales de la tabla cuando el usuario se desplaza a un registro determinado. Para determinar si el controlador proporciona esta compatibilidad, llame a la función de la API de ODBC `::SQLGetInfo` con el parámetro *SQL_SCROLL_OPTIONS* .

   Si intenta abrir un conjunto de registros dinámico sin compatibilidad con KEYSET, obtendrá un `CDBException` con el valor del código de retorno AFX_SQL_ERROR_DYNASET_NOT_SUPPORTED.

- El controlador ODBC para el origen de datos debe admitir la captura extendida.

   La captura extendida es la capacidad de desplazarse hacia atrás y hacia delante por los registros resultantes de la consulta SQL. Para determinar si el controlador admite esta capacidad, llame a la función de la API de ODBC `::SQLGetFunctions` con el parámetro *SQL_API_SQLEXTENDEDFETCH* .

Si desea que los conjuntos de registros dinámicos (o las instantáneas) se actualicen, el controlador ODBC también debe ser compatible con la `::SQLSetPos` función de la API de ODBC o con las actualizaciones colocadas. La función `::SQLSetPos` permite que MFC actualice el origen de datos sin enviar instrucciones SQL. Si esta compatibilidad está disponible, MFC la usa en su preferencia para hacer actualizaciones mediante SQL. Para determinar si el controlador admite `::SQLSetPos`, llame a `::SQLGetInfo` con el parámetro *SQL_POS_OPERATIONS* .

Las actualizaciones posicionadas usan la sintaxis SQL (del formulario **donde Current of** \<cursorname >) para identificar una fila determinada de la tabla en el origen de datos. Para determinar si el controlador admite las actualizaciones posicionadas, llame a `::SQLGetInfo` con el parámetro *SQL_POSITIONED_STATEMENTS* .

Por lo general, los conjuntos de registros dinámicos MFC (pero no los conjuntos de registros solo hacia delante) requieren un controlador ODBC con la conformidad de la API de nivel 2. Si el controlador del origen de datos se ajusta al conjunto de API de nivel 1, todavía puede usar instantáneas actualizables y de solo lectura y conjuntos de registros solo hacia delante, pero no dynasets. Sin embargo, un controlador de nivel 1 puede admitir dynasets si admite la captura extendida y los cursores controlados por conjunto de claves. Para obtener más información sobre los niveles de cumplimiento ODBC, vea [ODBC](../../data/odbc/odbc-basics.md).

> [!NOTE]
> Si desea utilizar las instantáneas y los conjuntos de registros dinámicos, debe basarlos en dos objetos de `CDatabase` diferentes (dos conexiones diferentes).

A diferencia de las instantáneas, que utilizan el almacenamiento intermedio mantenido por la biblioteca de cursores ODBC, los conjuntos de registros dinámicos capturan un registro directamente desde el origen de datos en cuanto se desplaza a él. Esto mantiene los registros seleccionados originalmente por el Dynaset sincronizado con el origen de datos.

Vea [Lista de controladores ODBC](../../data/odbc/odbc-driver-list.md) para obtener una lista de los controladores ODBC incluidos en esta versión de Visual C++ e información sobre cómo obtener controladores adicionales.

## <a name="see-also"></a>Consulte también

[Conectividad abierta de bases de datos (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)
