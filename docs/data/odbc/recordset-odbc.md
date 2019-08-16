---
title: Conjunto de registros (ODBC)
ms.date: 05/09/2019
helpviewer_keywords:
- recordsets, snapshots
- recordsets, creating
- dynamic recordsets
- forward-only recordsets
- recordsets, dynasets
- ODBC recordsets, CRecordset objects
- ODBC recordsets
- recordsets, about recordsets
- snapshots, ODBC recordsets
- dynasets
ms.assetid: 333337c5-575e-4d26-b5f6-47166ad7874d
ms.openlocfilehash: b043b08e13611b87bbffbe9dfb3255d5520e3359
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65707838"
---
# <a name="recordset-odbc"></a>Conjunto de registros (ODBC)

Este tema es aplicable a las clases ODBC de MFC.

Un objeto [CRecordset](../../mfc/reference/crecordset-class.md) representa un conjunto de registros seleccionados de un origen de datos. Los registros pueden proceder de:

- Una tabla.

- Una consulta.

- Un procedimiento almacenado que accede a una o varias tablas.

Un ejemplo de un conjunto de registros basado en una tabla es "todos los clientes", que accede a una tabla de clientes. Un ejemplo de consulta es "todas las facturas de Joe Smith". Un ejemplo de un conjunto de registros basado en un procedimiento almacenado (a veces denominado "consulta predefinida") es "todas las cuentas morosas", que invoca un procedimiento almacenado en la base de datos back-end. Un conjunto de registros puede combinar dos o más tablas del mismo origen de datos, pero no tablas de orígenes de datos diferentes.

> [!NOTE]
>  Algunos controladores ODBC admiten vistas de la base de datos. En este sentido, una vista es una consulta creada originalmente con una instrucción `CREATE VIEW` de SQL.

##  <a name="_core_recordset_capabilities"></a> Funcionalidades del conjunto de registros

Todos los objetos de conjunto de registros comparten las funcionalidades siguientes:

- Si el origen de datos no es de solo lectura, puede especificar que el conjunto de registros sea [actualizable](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md), [agregable](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md) o de solo lectura. Si el conjunto de registros es actualizable, puede elegir métodos de [bloqueo](../../data/odbc/recordset-locking-records-odbc.md) optimistas o pesimistas, siempre y cuando el controlador proporcione la compatibilidad de bloqueo apropiada. Si el origen de datos es de solo lectura, el conjunto de registros será de solo lectura.

- Puede llamar a funciones miembro para [desplazarse](../../data/odbc/recordset-scrolling-odbc.md) por los registros seleccionados.

- Puede [filtrar](../../data/odbc/recordset-filtering-records-odbc.md) los registros para restringir cuáles se seleccionan entre los disponibles.

- Puede [ordenar](../../data/odbc/recordset-sorting-records-odbc.md) los registros de manera ascendente o descendente, en función de una o varias columnas.

- Puede [parametrizar](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md) el conjunto de registros para aprobar la selección del conjunto de registros en tiempo de ejecución.

##  <a name="_core_snapshots_and_dynasets"></a> Instantáneas y dynasets

Hay dos tipos principales de conjuntos de registros: [instantáneas](../../data/odbc/snapshot.md) y [dynasets](../../data/odbc/dynaset.md). Ambos son compatibles con la clase `CRecordset`. Cada uno de ellos comparte las características comunes de todos los conjuntos de registros, pero también extiende las funcionalidades comunes según su especialización. Las instantáneas proporcionan una vista estática de los datos y son útiles para los informes y otras situaciones en las que se quiere obtener una vista de los datos tal como se encontraban en un momento determinado. Los dynasets son útiles cuando se quiere que las actualizaciones realizadas por otros usuarios sean visibles en el conjunto de registros sin necesidad de volver a consultar o actualizar el conjunto de registros. Las instantáneas y los dynasets pueden ser actualizables o de solo lectura. Para reflejar los registros agregados o eliminados por otros usuarios, llame a [CRecordset::Requery](../../mfc/reference/crecordset-class.md#requery).

`CRecordset` también admite otros dos tipos de conjuntos de registros: dinámicos y de solo avance. Los conjuntos de registros dinámicos son similares a los dynasets, pero los primeros reflejan todos los registros que se han agregado o eliminado sin llamar a `CRecordset::Requery`. Por este motivo, los conjuntos de registros dinámicos suelen ser costosos en lo que respecta al tiempo de procesamiento en el sistema de administración de bases de datos y muchos controladores ODBC no los admiten. En cambio, los conjuntos de registros de solo avance proporcionan el método más eficaz de acceso a datos para los conjuntos de registros que no requieren actualizaciones ni desplazamiento hacia atrás. Por ejemplo, podría usar un conjunto de registros de solo avance para migrar datos de un origen de datos a otro si solo necesita desplazarse por los datos hacia delante. Para usar un conjunto de registros de solo avance, debe hacer lo siguiente:

- Pasar la opción `CRecordset::forwardOnly` como parámetro *nOpenType* de la función miembro [Open](../../mfc/reference/crecordset-class.md#open).

- Especificar `CRecordset::readOnly` en el parámetro *dwOptions* de `Open`.

    > [!NOTE]
    >  Para obtener información sobre los requisitos del controlador ODBC para la compatibilidad con dynasets, vea [ODBC](../../data/odbc/odbc-basics.md). Vea [Lista de controladores ODBC](../../data/odbc/odbc-driver-list.md) para obtener una lista de los controladores ODBC incluidos en esta versión de Visual C++ e información sobre cómo obtener controladores adicionales.

##  <a name="_core_your_recordsets"></a> Conjuntos de registros

Para cada tabla, vista o procedimiento almacenado al que quiere acceder, por lo general define una clase derivada de `CRecordset`. (La excepción es la combinación de bases de datos, en la que un conjunto de registros representa las columnas de dos o más tablas). Al derivar una clase de conjunto de registros, habilita el mecanismo RFX (intercambio de campos de registros) o RFX masivo (intercambio masivo de campos de registros), que son similares al mecanismo DDX (intercambio de datos de cuadro de diálogo). RFX y RFX masivo simplifican la transferencia de datos del origen de datos al conjunto de registros. Además, RFX transfiere datos del conjunto de registros al origen de datos. Para obtener más información, vea [Intercambio de campos de registros (RFX)](../../data/odbc/record-field-exchange-rfx.md) y [Conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Un objeto de conjunto de registros proporciona acceso a todos los registros seleccionados. Puede desplazarse por los diferentes registros seleccionados mediante funciones miembro `CRecordset`, como `MoveNext` y `MovePrev`. Al mismo tiempo, un objeto de conjunto de registros representa uno solo de los registros seleccionados: el registro actual. Para examinar los campos del registro actual, declare las variables de miembro de la clase de conjunto de registros que se correspondan con las columnas de la tabla o de los registros que se derivan de la consulta de la base de datos. Para obtener información sobre los miembros de datos del conjunto de registros, vea [Conjunto de registros: arquitectura (ODBC)](../../data/odbc/recordset-architecture-odbc.md).

En los siguientes temas se explica con más detalle el uso de los objetos de conjunto de registros. Los temas se muestran en categorías funcionales y en el orden natural de exploración para permitir una lectura secuencial.

### <a name="topics-about-the-mechanics-of-opening-reading-and-closing-recordsets"></a>Temas sobre los mecanismos para abrir, leer y cerrar conjuntos de registros

- [Conjunto de registros: arquitectura (ODBC)](../../data/odbc/recordset-architecture-odbc.md)

- [Conjunto de registros: declarar una clase para una tabla (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)

- [Conjunto de registros: crear y cerrar conjuntos de registros (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md)

- [Conjunto de registros: desplazarse (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)

- [Conjunto de registros: marcadores y posiciones absolutas (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)

- [Conjunto de registros: filtrar registros (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)

- [Conjunto de registros: ordenar registros (ODBC)](../../data/odbc/recordset-sorting-records-odbc.md)

- [Conjunto de registros: parametrizar un conjunto de registros (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)

### <a name="topics-about-the-mechanics-of-modifying-recordsets"></a>Temas sobre los mecanismos para modificar conjuntos de registros

- [Conjunto de registros: agregar, actualizar y eliminar registros (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)

- [Conjunto de registros: bloquear registros (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)

- [Conjunto de registros: volver a consultar un conjunto de registros (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md)

### <a name="topics-about-somewhat-more-advanced-techniques"></a>Temas sobre técnicas más avanzadas

- [Conjunto de registros: realizar una combinación (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md)

- [Conjunto de registros: declarar una clase para una consulta predefinida (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md)

- [Conjunto de registros: enlazar dinámicamente columnas de datos (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)

- [Conjunto de registros: capturar registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)

- [Conjunto de registros: trabajar con grandes elementos de datos (ODBC)](../../data/odbc/recordset-working-with-large-data-items-odbc.md)

- [Conjunto de registros: obtener cálculos SUM y otros resultados agregados (ODBC)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md)

### <a name="topics-about-how-recordsets-work"></a>Temas sobre el funcionamiento de los conjuntos de registros

- [Conjunto de registros: cómo los conjuntos de registros seleccionan los registros (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)

- [Conjunto de registros: cómo los conjuntos de registros actualizan los registros (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)

## <a name="see-also"></a>Vea también

[Conectividad abierta de bases de datos (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)<br/>
[Consumidor ODBC MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)<br/>
[Transacción (ODBC)](../../data/odbc/transaction-odbc.md)