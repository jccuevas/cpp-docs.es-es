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
ms.openlocfilehash: 2eb2447d1f984b7734d5e9c45087023e5a6f003f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371840"
---
# <a name="dynaset"></a>Conjunto de registros dinámicos

En este tema se describen los conjuntos de registros dinámicos y se describe su [disponibilidad.](#_core_availability_of_dynasets)

> [!NOTE]
> Este tema se aplica a las clases ODBC de MFC, incluido [CRecordset](../../mfc/reference/crecordset-class.md). Para obtener información acerca de los conjuntos de registros dinámicos en las clases DAO, vea [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md). Con DAO, puede abrir conjuntos de registros de tipo dinámico.

Un conjunto de registros dinámicos es un conjunto de registros con propiedades dinámicas. Durante su duración, un objeto de conjunto de registros en modo dynaset (normalmente denominado conjunto de registros dinámicos) permanece sincronizado con el origen de datos de la siguiente manera. En un entorno multiusuario, otros usuarios pueden editar o eliminar registros que se encuentran en el conjunto de registros dinámicos o agregar registros a la tabla que representa el conjunto de registros dinámicos. Los registros que la aplicación agrega o elimina del conjunto de registros se reflejan en el conjunto de registros dinámicos. Los registros que otros usuarios agregan a la tabla no se reflejarán `Requery` en el conjunto de registros dinámicos hasta que se reconstruya el conjunto de registros dinámicos llamando a su función miembro. Cuando otros usuarios eliminan registros, el código MFC omite las eliminaciones del conjunto de registros. Los cambios de edición de otros usuarios en los registros existentes se reflejan en el conjunto de registros dinámicos tan pronto como se desplaza al registro afectado.

Del mismo modo, las ediciones que realice en los registros de un conjunto de registros dinámicos se reflejan en conjuntos de registros dinámicos que utilizan otros usuarios. Los registros que agregue no se reflejan en los conjuntos de registros dinámicos de otros usuarios hasta que vuelvan a consultar sus conjuntos de registros dinámicos. Los registros que elimine se marcan como "eliminados" en los conjuntos de registros de otros usuarios. Si tiene varias conexiones a `CDatabase` la misma base de datos (varios objetos), los conjuntos de registros asociados a esas conexiones tienen el mismo estado que los conjuntos de registros de otros usuarios.

Los Dynasets son más valiosos cuando los datos deben ser dinámicos, como (por ejemplo) en un sistema de reservas de aerolíneas.

> [!NOTE]
> Para usar conjuntos de registros dinámicos, debe tener un controlador ODBC para el origen de datos que admita conjuntos de registros dinámicos y no se debe cargar la biblioteca de cursores ODBC. Para obtener más información, consulte [Disponibilidad de dynasets](#_core_availability_of_dynasets).

Para especificar que un conjunto de `CRecordset::dynaset` registros es `Open` un conjunto de registros dinámicos, pase como primer parámetro a la función miembro del objeto de conjunto de registros.

> [!NOTE]
> Para conjuntos de registros dinámicos actualizables, el controlador `::SQLSetPos` ODBC debe admitir instrucciones de actualización posicionadas o la función de API ODBC. Si se admiten `::SQLSetPos` ambos, MFC se usa para la eficiencia.

## <a name="availability-of-dynasets"></a><a name="_core_availability_of_dynasets"></a>Disponibilidad de Dynasets

Las clases de base de datos MFC admiten conjuntos de registros dinámicos si se cumplen los siguientes requisitos:

- El archivo DLL de la biblioteca de cursores ODBC no debe estar en uso para este origen de datos.

   Si se utiliza la biblioteca de cursores, enmascara algunas funciones del controlador ODBC subyacente que es necesaria para la compatibilidad con conjuntos de registros dinámicos. Si desea utilizar conjuntos de registros dinámicos (y el controlador ODBC tiene la funcionalidad necesaria para los conjuntos de registros dinámicos, como se describe en el resto de esta sección), puede hacer que MFC no cargue la biblioteca de cursores al crear un `CDatabase` objeto. Para obtener más información, vea [ODBC](../../data/odbc/odbc-basics.md) y la `CDatabase`función miembro [OpenEx](../../mfc/reference/cdatabase-class.md#openex) u [Open](../../mfc/reference/cdatabase-class.md#open) de la clase .

   En la terminología ODBC, los conjuntos de registros dinámicos y las instantáneas se conocen como cursores. Un cursor es un mecanismo utilizado para realizar un seguimiento de su posición en un conjunto de registros.

- El controlador ODBC del origen de datos debe admitir cursores controlados por conjuntos de claves.

   Los cursores controlados por conjuntos de claves administran los datos de una tabla obteniendo y almacenando un conjunto de claves. Las claves se utilizan para obtener los datos actuales de la tabla cuando el usuario se desplaza a un registro determinado. Para determinar si el controlador proporciona `::SQLGetInfo` esta compatibilidad, llame a la función de API ODBC con el parámetro *SQL_SCROLL_OPTIONS.*

   Si intenta abrir un conjunto de registros dinámicos sin compatibilidad con conjuntos de claves, obtendrá un `CDBException` con el valor de código de retorno AFX_SQL_ERROR_DYNASET_NOT_SUPPORTED.

- El controlador ODBC del origen de datos debe admitir la obtención extendida.

   La obtención extendida es la capacidad de desplazarse hacia atrás y hacia delante sobre los registros resultantes de la consulta SQL. Para determinar si el controlador admite `::SQLGetFunctions` esta capacidad, llame a la función de API ODBC con el *parámetro SQL_API_SQLEXTENDEDFETCH.*

Si desea conjuntos de registros dinámicos actualizables (o instantáneas, `::SQLSetPos` para el caso), el controlador ODBC también debe admitir la función de API ODBC o actualizaciones posicionadas. La `::SQLSetPos` función permite a MFC actualizar el origen de datos sin enviar instrucciones SQL. Si esta compatibilidad está disponible, MFC lo usa en lugar de realizar actualizaciones mediante SQL. Para determinar si `::SQLSetPos`el `::SQLGetInfo` controlador admite , llame con el parámetro *SQL_POS_OPERATIONS.*

Las actualizaciones posicionadas utilizan la sintaxis SQL (del formulario **WHERE CURRENT OF** \<cursorname>) para identificar una fila determinada de la tabla del origen de datos. Para determinar si el controlador admite `::SQLGetInfo` actualizaciones posicionadas, llame con el parámetro *SQL_POSITIONED_STATEMENTS.*

Por lo general, los conjuntos de registros dinámicos MFC (pero no los conjuntos de registros de solo avance) requieren un controlador ODBC con conformidad de api de nivel 2. Si el controlador del origen de datos se ajusta al conjunto de API de nivel 1, puede seguir utilizando instantáneas actualizables y de solo lectura y conjuntos de registros de solo avance, pero no conjuntos de registros dinámicos. Sin embargo, un controlador de nivel 1 puede admitir conjuntos de registros dinámicos si admite la obtención extendida y cursores controlados por conjuntos de claves. Para obtener más información acerca de los niveles de conformidad ODBC, vea [ODBC](../../data/odbc/odbc-basics.md).

> [!NOTE]
> Si desea utilizar instantáneas y conjuntos de registros `CDatabase` dinámicos, debe basarlos en dos objetos diferentes (dos conexiones diferentes).

A diferencia de las instantáneas, que utilizan almacenamiento intermedio mantenido por la biblioteca de cursores ODBC, los conjuntos de registros dinámicos recuperan un registro directamente desde el origen de datos tan pronto como se desplaza a él. Esto mantiene los registros seleccionados originalmente por el conjunto de registros dinámicos sincronizados con el origen de datos.

Vea [Lista de controladores ODBC](../../data/odbc/odbc-driver-list.md) para obtener una lista de los controladores ODBC incluidos en esta versión de Visual C++ e información sobre cómo obtener controladores adicionales.

## <a name="see-also"></a>Consulte también

[Conectividad de base de datos abierta (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)
