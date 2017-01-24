---
title: "Conjunto de registros (ODBC) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "conjuntos de registros dinámicos"
  - "conjuntos de registros dinámicos"
  - "conjuntos de registros sólo hacia delante"
  - "conjuntos de registros ODBC"
  - "conjuntos de registros ODBC, CRecordset (objetos)"
  - "conjuntos de registros, acerca de los conjuntos de registros"
  - "conjuntos de registros, crear"
  - "conjuntos de registros, conjuntos de registros dinámicos"
  - "conjuntos de registros, instantáneas"
  - "instantáneas, conjuntos de registros ODBC"
ms.assetid: 333337c5-575e-4d26-b5f6-47166ad7874d
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Conjunto de registros (ODBC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Este tema es aplicable a las clases ODBC de MFC.  
  
 Un objeto [CRecordset](../../mfc/reference/crecordset-class.md) representa un conjunto de registros seleccionados de un origen de datos.  Los registros pueden proceder de:  
  
-   Una tabla.  
  
-   Una consulta.  
  
-   Un procedimiento almacenado que tiene acceso a una o varias tablas.  
  
 Un ejemplo de conjunto de registros basado en una tabla es "todos los clientes", que tiene acceso a una tabla Clientes.  Un ejemplo de consulta es "todas las facturas de Juan García". Un ejemplo de conjunto de registros basado en un procedimiento almacenado \(a veces denominado consulta predefinida\) es "todas las cuentas pendientes de pago", que llamaría a un procedimiento almacenado en la base de datos del back end .  Un conjunto de registros puede combinar dos o varias tablas del mismo origen de datos, pero no de diferentes orígenes de datos.  
  
> [!NOTE]
>  Para obtener información sobre cómo derivar clases de conjunto de registros mediante asistentes, vea [Agregar un consumidor ODBC de MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md) y [Compatibilidad con bases de datos, Asistente para aplicaciones MFC](../../mfc/reference/database-support-mfc-application-wizard.md).  
  
> [!NOTE]
>  Algunos controladores ODBC admiten vistas de la base de datos.  Una vista en ese sentido es una consulta creada originalmente mediante la instrucción SQL `CREATE VIEW`.  Actualmente, los asistentes no permiten el uso de vistas, pero es posible escribir código para esta compatibilidad manualmente.  
  
##  <a name="_core_recordset_capabilities"></a> Características del conjunto de registros  
 Todos los objetos de conjunto de registros comparten las siguientes características:  
  
-   Si el origen de datos no es de sólo lectura, se puede especificar que el conjunto de registros sea [actualizable](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md), [anexable](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md) o de sólo lectura.  Si el conjunto de registros es actualizable, se puede elegir entre métodos de [bloqueo](../../data/odbc/recordset-locking-records-odbc.md) pesimistas u optimistas, siempre que el controlador proporcione la compatibilidad adecuada para el bloqueo.  Si el origen de datos es de sólo lectura, el conjunto de registros también lo es.  
  
-   Se puede llamar a las funciones miembro para [desplazarse](../../data/odbc/recordset-scrolling-odbc.md) a través de los registros seleccionados.  
  
-   Se pueden [filtrar](../../data/odbc/recordset-filtering-records-odbc.md) los registros para restringir qué registros se seleccionan en los que están disponibles.  
  
-   Se pueden [ordenar](../../data/odbc/recordset-sorting-records-odbc.md) los registros de forma ascendente o descendente, basándose en una o más columnas.  
  
-   Se puede [parametrizar](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md) el conjunto de registros para calificar la selección de conjuntos de registros en tiempo de ejecución.  
  
##  <a name="_core_snapshots_and_dynasets"></a> Instantáneas y conjuntos de registros dinámicos  
 Hay dos tipos principales de conjuntos de registros: [instantáneas](../../data/odbc/snapshot.md) y [conjuntos de registros dinámicos](../../data/odbc/dynaset.md).  Los dos son compatibles con la clase `CRecordset`.  Cada uno de ellos comparte las características comunes de todos los conjuntos de registros, pero también extiende la funcionalidad común de forma diferente.  Las instantáneas proporcionan una vista estática de los datos y son útiles para informes y otras situaciones en las que se desea una vista de los datos tal como existen en un momento determinado.  Los conjuntos de registros dinámicos son útiles cuando se desea que las actualizaciones realizadas por otros usuarios sean visibles en el conjunto de registros sin necesidad de realizar una nueva consulta o actualizar el conjunto de registros.  Tanto las instantáneas como los conjuntos de registros dinámicos pueden ser actualizables o de sólo lectura.  Para reflejar los registros agregados o eliminados por otros usuarios, se debe llamar a [CRecordset::Requery](../Topic/CRecordset::Requery.md).  
  
 `CRecordset` también permite otros dos tipos de conjuntos de registros: Dinámicos y sólo hacia delante.  Los conjuntos dinámicos son similares a los conjuntos de registros dinámicos; sin embargo, los primeros reflejan los registros agregados o eliminados mediante una llamada a `CRecordset::Requery`.  Por este motivo, los conjuntos de registros dinámicos suelen ser costosos en términos de tiempo de procesamiento en el sistema de administración de bases de datos \(DBMS\) y no son compatibles con muchos controladores ODBC.  En cambio, los conjuntos de registros sólo hacia delante proporcionan el método más eficaz de acceso a datos en conjuntos de registros que no requieren actualizaciones ni desplazamiento hacia atrás.  Por ejemplo, se puede usar un conjunto de registros *sólo hacia delante* para migrar datos de un origen de datos a otro donde sólo es necesario desplazarse por los datos hacia delante.  Para utilizar un conjunto de registros *sólo hacia delante* se deben realizar estos dos pasos:  
  
-   Pase la opción **CRecordset::forwardOnly** como parámetro `nOpenType` de la función miembro [Open](../Topic/CRecordset::Open.md).  
  
-   Especificar **CRecordset::readOnly** en el parámetro `dwOptions` de **Open**.  
  
    > [!NOTE]
    >  Para obtener información sobre los requisitos de los controladores ODBC para compatibilidad con conjuntos de registros dinámicos, vea [ODBC](../../data/odbc/odbc-basics.md).  Vea [Lista de controladores ODBC](../../data/odbc/odbc-driver-list.md) para obtener una lista de los controladores ODBC incluidos en esta versión de Visual C\+\+ e información sobre cómo obtener controladores adicionales.  
  
##  <a name="_core_your_recordsets"></a> El conjunto de registros del programador  
 Por cada tabla, vista o procedimiento almacenado a los que se desee tener acceso, normalmente se define una clase derivada de `CRecordset`. \(La excepción es una combinación de bases de datos en la que un conjunto de registros representa columnas de dos o más tablas.\) Al derivar una clase de conjunto de registros, se habilita el mecanismo de Intercambio de campos de registro \(RFX\) o el mecanismo de Intercambio masivo de campos de registros \(RFX masivo\), similares al intercambio de datos de cuadros de diálogo \(DDX\).  RFX y RFX masivo simplifican la transferencia del origen de datos al conjunto de registros; RFX, además, transfiere los datos del conjunto de registros al origen de datos.  Para obtener más información, vea [Intercambio de campos de registros \(RFX\)](../../data/odbc/record-field-exchange-rfx.md) y [Conjunto de registros: Obtener registros de forma masiva \(ODBC\)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Un objeto de conjunto de registros da acceso a todos los registros seleccionados.  Es posible desplazarse por los diferentes registros seleccionados mediante las funciones miembro de `CRecordset`, como `MoveNext` y `MovePrev`.  A la vez, un objeto de conjunto de registros sólo representa uno de los registros seleccionados, el actual.  Se pueden examinar los campos del registro actual declarando variables miembro de la clase de conjunto de registros que correspondan a las columnas de la tabla o de los registros resultantes de la consulta de base de datos.  Para obtener información acerca de los miembros de datos de un conjunto de registros, vea [Conjunto de registros: Arquitectura \(ODBC\)](../../data/odbc/recordset-architecture-odbc.md).  
  
 En los siguientes temas se explican los detalles acerca del uso de objetos de conjunto de registros.  Los temas aparecen clasificados en categorías funcionales y en orden lógico de exploración para permitir una lectura secuencial.  
  
### Temas referentes a la apertura, lectura y cierre de conjuntos de registros  
  
-   [Conjunto de registros: Arquitectura \(ODBC\)](../../data/odbc/recordset-architecture-odbc.md)  
  
-   [Conjunto de registros: Declarar una clase para una tabla \(ODBC\)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)  
  
-   [Conjunto de registros: Crear y cerrar conjuntos de registros \(ODBC\)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md)  
  
-   [Conjunto de registros: Desplazamiento \(ODBC\)](../../data/odbc/recordset-scrolling-odbc.md)  
  
-   [Conjunto de registros: Marcadores y posiciones absolutas \(ODBC\)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)  
  
-   [Conjunto de registros: Filtrar registros \(ODBC\)](../../data/odbc/recordset-filtering-records-odbc.md)  
  
-   [Conjunto de registros: Ordenar registros \(ODBC\)](../../data/odbc/recordset-sorting-records-odbc.md)  
  
-   [Conjunto de registros: Parametrizar un conjunto de registros \(ODBC\)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)  
  
### Temas sobre el mecanismo de modificación de conjuntos de registros  
  
-   [Conjunto de registros: Agregar, actualizar y eliminar registros \(ODBC\)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)  
  
-   [Conjunto de registros: Bloquear registros \(ODBC\)](../../data/odbc/recordset-locking-records-odbc.md)  
  
-   [Conjunto de registros: Volver a consultar un conjunto de registros \(ODBC\)](../../data/odbc/recordset-requerying-a-recordset-odbc.md)  
  
### Temas sobre técnicas más avanzadas  
  
-   [Conjunto de registros: Realizar una combinación \(ODBC\)](../../data/odbc/recordset-performing-a-join-odbc.md)  
  
-   [Conjunto de registros: Declarar una clase para una consulta predefinida \(ODBC\)](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md)  
  
-   [Conjunto de registros: Enlazar dinámicamente columnas de datos \(ODBC\)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)  
  
-   [Conjunto de registros: Obtener registros de forma masiva \(ODBC\)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)  
  
-   [Conjunto de registros: Trabajar con grandes elementos de datos \(ODBC\)](../../data/odbc/recordset-working-with-large-data-items-odbc.md)  
  
-   [Conjunto de registros: Obtener cálculos SUM y otros resultados agregados \(ODBC\)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md)  
  
### Temas sobre el funcionamiento de los conjuntos de registros  
  
-   [Conjunto de registros: Cómo se seleccionan los registros \(ODBC\)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)  
  
-   [Conjunto de registros: Actualizar los registros \(ODBC\)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)  
  
## Vea también  
 [Conectividad abierta de bases de datos \(ODBC\)](../../data/odbc/open-database-connectivity-odbc.md)   
 [Consumidor ODBC de MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)   
 [Transacción \(ODBC\)](../../data/odbc/transaction-odbc.md)