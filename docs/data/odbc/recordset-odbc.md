---
title: Conjunto de registros (ODBC)
ms.date: 11/04/2016
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
ms.openlocfilehash: b201e152d83d3812253aa4803eebe715d726219d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62397749"
---
# <a name="recordset-odbc"></a>Conjunto de registros (ODBC)

Este tema es aplicable a las clases ODBC de MFC.

Un [CRecordset](../../mfc/reference/crecordset-class.md) objeto representa un conjunto de registros seleccionados de un origen de datos. Los registros pueden ser de:

- Una tabla.

- Una consulta.

- Un procedimiento almacenado que tiene acceso a una o varias tablas.

Un ejemplo de un conjunto de registros basada en una tabla es "todos los clientes", que tiene acceso a una tabla de clientes. Un ejemplo de una consulta es "todas las facturas de Joe Smith." Un ejemplo de un conjunto de registros basado en un procedimiento almacenado (denominado a veces, una consulta predefinida) es "todas las cuentas delictivos," que invoca un procedimiento almacenado en la base de datos back-end. Un conjunto de registros puede combinar dos o más tablas del mismo origen de datos, pero no las tablas de orígenes de datos diferentes.

> [!NOTE]
>  Para obtener información acerca de cómo derivar clases de conjunto de registros con los asistentes, vea [agregar un consumidor ODBC de MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md) y [soporte técnico de la base de datos, Asistente para aplicaciones MFC](../../mfc/reference/database-support-mfc-application-wizard.md).

> [!NOTE]
>  Algunos controladores ODBC admiten vistas de la base de datos. Una vista en este sentido es una consulta creada originalmente con el lenguaje SQL `CREATE VIEW` instrucción. Los asistentes no admiten actualmente las vistas, pero es posible que codificar esta funcionalidad usted mismo.

##  <a name="_core_recordset_capabilities"></a> Capacidades del conjunto de registros

Todos los objetos de conjunto de registros comparten las siguientes funcionalidades:

- Si el origen de datos no es de solo lectura, puede especificar que el conjunto de registros sea [actualizable](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md), [anexable](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md), o de solo lectura. Si el conjunto de registros es actualizable, puede elegir optimista o pesimista [bloqueo](../../data/odbc/recordset-locking-records-odbc.md) métodos, proporciona el controlador proporciona la compatibilidad de bloqueo apropiada. Si el origen de datos es de solo lectura, el conjunto de registros será de solo lectura.

- Se puede llamar a funciones miembro para [desplazamiento](../../data/odbc/recordset-scrolling-odbc.md) a través de los registros seleccionados.

- También puede [filtro](../../data/odbc/recordset-filtering-records-odbc.md) los registros para restringir qué registros se seleccionan en las que están disponibles.

- También puede [ordenación](../../data/odbc/recordset-sorting-records-odbc.md) los registros en orden ascendente o descendente, según una o varias columnas.

- También puede [parametrizar](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md) el conjunto de registros para calificar la selección de conjunto de registros en tiempo de ejecución.

##  <a name="_core_snapshots_and_dynasets"></a> Las instantáneas y conjuntos de registros dinámicos

Hay dos tipos principales de conjuntos de registros: [instantáneas](../../data/odbc/snapshot.md) y [dynasets](../../data/odbc/dynaset.md). Ambas son compatibles con la clase `CRecordset`. Cada uno comparte las características comunes de todos los conjuntos de registros, pero también extiende la funcionalidad común en su propia manera especializado. Las instantáneas proporcionan una vista estática de los datos y son útiles para los informes y otras situaciones en que desea una vista de los datos tal como se encontraban en un momento determinado. Conjuntos de registros dinámicos son útiles cuando desea actualizaciones realizadas por otros usuarios que sean visibles en el conjunto de registros sin tener que volver a consultar o actualizar el conjunto de registros. Las instantáneas y conjuntos de registros dinámicos pueden ser actualizables o de solo lectura. Para reflejar los registros agregados o eliminados por otros usuarios, llamar a [CRecordset:: Requery](../../mfc/reference/crecordset-class.md#requery).

`CRecordset` También permite que otros dos tipos de conjuntos de registros: conjuntos de registros dinámicos y los conjuntos de registros solo hacia delante. Conjuntos de registros dinámicos son similares a los conjuntos de registros dinámicos; Sin embargo, los conjuntos de registros dinámicos reflejan los registros agregados o eliminados sin llamar a `CRecordset::Requery`. Por este motivo, los conjuntos de registros dinámicos suelen ser costosos con respecto al tiempo de procesamiento en el DBMS y no son compatibles con muchos controladores ODBC. En cambio, los conjuntos de registros solo hacia delante proporcionan el método más eficaz de acceso a datos para los conjuntos de registros que no requieren actualizaciones o desplazamiento hacia atrás. Por ejemplo, podría usar un conjunto de registros solo hacia delante para migrar datos desde un origen de datos a otro, donde solo es necesario desplazarse por los datos hacia delante. Para usar un conjunto de registros solo hacia delante, debe hacer lo siguiente:

- Pase la opción `CRecordset::forwardOnly` como el *nOpenType* parámetro de la [abierto](../../mfc/reference/crecordset-class.md#open) función miembro.

- Especificar `CRecordset::readOnly` en el *dwOptions* parámetro de `Open`.

    > [!NOTE]
    >  Para obtener información sobre los requisitos del controlador ODBC para la compatibilidad de tipo dinámico, vea [ODBC](../../data/odbc/odbc-basics.md). Para obtener una lista de controladores ODBC incluidos en esta versión de Visual C++ y para obtener información acerca de cómo obtener controladores adicionales, consulte [lista de controladores ODBC](../../data/odbc/odbc-driver-list.md).

##  <a name="_core_your_recordsets"></a> Los conjuntos de registros

Para cada tabla, vista o procedimiento almacenado que desea tener acceso a, normalmente definen una clase derivada de `CRecordset`. (La excepción es una combinación de la base de datos, en el que un conjunto de registros representa las columnas de dos o más tablas). Al derivar una clase de conjunto de registros, habilita el mecanismo de campos de registros (RFX) de exchange o el mecanismo de intercambio (RFX masivo) campos de registros de forma masiva, que son similares para el mecanismo de intercambio (DDX) de datos de cuadro de diálogo. RFX y RFX masivo simplifican a la transferencia de datos del origen de datos en el conjunto de registros; Además, RFX transfiere datos desde el conjunto de registros para el origen de datos. Para obtener más información, consulte [intercambio de campos de registros (RFX)](../../data/odbc/record-field-exchange-rfx.md) y [conjunto de registros: Obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Un objeto de conjunto de registros proporciona acceso a todos los registros seleccionados. Se desplaza por los diferentes registros seleccionados mediante `CRecordset` funciones miembro, como `MoveNext` y `MovePrev`. Al mismo tiempo, un objeto de conjunto de registros representa solo uno de los registros seleccionados, el registro actual. Puede examinar los campos del registro actual mediante la declaración de variables de miembro de clase que corresponden a columnas de la tabla o de los registros que se derivan de la consulta de base de datos de conjunto de registros. Para obtener información acerca de los miembros de datos del conjunto de registros, vea [conjunto de registros: Arquitectura (ODBC)](../../data/odbc/recordset-architecture-odbc.md).

Los siguientes temas explican los detalles del uso de objetos de conjunto de registros. Los temas se muestran en categorías funcionales y en orden natural de exploración para permitir una lectura secuencial.

### <a name="topics-about-the-mechanics-of-opening-reading-and-closing-recordsets"></a>Temas sobre el mecanismo de abrir, leer y cerrar conjuntos de registros

- [Conjunto de registros: arquitectura (ODBC)](../../data/odbc/recordset-architecture-odbc.md)

- [Conjunto de registros: declarar una clase para una tabla (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)

- [Conjunto de registros: crear y cerrar conjuntos de registros (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md)

- [Conjunto de registros: desplazarse (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)

- [Conjunto de registros: marcadores y posiciones absolutas (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)

- [Conjunto de registros: filtrar registros (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)

- [Conjunto de registros: ordenar registros (ODBC)](../../data/odbc/recordset-sorting-records-odbc.md)

- [Conjunto de registros: parametrizar un conjunto de registros (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)

### <a name="topics-about-the-mechanics-of-modifying-recordsets"></a>Temas sobre el mecanismo de modificación de conjuntos de registros

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

### <a name="topics-about-how-recordsets-work"></a>Temas acerca de cómo funcionan los conjuntos de registros

- [Conjunto de registros: cómo los conjuntos de registros seleccionan los registros (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)

- [Conjunto de registros: cómo los conjuntos de registros actualizan los registros (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)

## <a name="see-also"></a>Vea también

[Conectividad abierta de bases de datos (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)<br/>
[Consumidor ODBC de MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)<br/>
[Transacción (ODBC)](../../data/odbc/transaction-odbc.md)