---
title: Modelo de objetos OLE DB | Microsoft Docs
ms.custom: ''
ms.date: 10/22/2018
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- rowsets, OLE DB object model
- OLE DB, object model
ms.assetid: 1a274a25-c310-4430-a1ec-bd2bd8120eff
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 65cb4ef7acad08d3065f8394d61a50441d5e597c
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50056573"
---
# <a name="ole-db-object-model"></a>Modelo de objetos OLE DB

El modelo de objetos de OLE DB está formado por los siguientes objetos o componentes. Los primeros cuatro objetos o componentes (orígenes de datos, sesiones, comandos y conjuntos de filas) permiten conectarse a un origen de datos y verlo. El resto, a partir de los descriptores de acceso, se refieren a trabajar con los datos cuando se muestre.

## <a name="data-sources"></a>Orígenes de datos

Objetos de origen de datos permiten conectarse a un origen de datos como un archivo o DBMS. Un objeto de origen de datos crea y administra la conexión y contiene información de permisos y autenticación (por ejemplo, el nombre de inicio de sesión y contraseña). Un objeto de origen de datos puede crear una o varias sesiones.

## <a name="sessions"></a>Sesiones

Una sesión administra una interacción determinada con el origen de datos para consultar y recuperar datos. Cada sesión es una sola transacción. Una transacción es una unidad de trabajo indivisible definida por la prueba de ácido. Para una definición de ACID, vea [transacciones](#vcconoledbcomponents_transactions).

Las sesiones de realizar tareas importantes, como abrir conjuntos de filas y devolver el objeto de origen de datos que lo creó. Las sesiones también pueden devolver metadatos o información sobre el origen de datos (por ejemplo, información de la tabla).

Una sesión puede crear uno o más comandos.

## <a name="commands"></a>Comandos

Los comandos ejecutan un comando de texto como una instrucción SQL. Si el comando de texto especifica un conjunto de filas, como una instancia de SQL **seleccione** instrucción, el comando crea el conjunto de filas.

Un comando es sencillamente un contenedor para un comando de texto, que es una cadena (por ejemplo, una instrucción SQL) que se pasa de un consumidor a un objeto de origen de datos para su ejecución por el almacén de datos subyacente del proveedor. Normalmente, el comando de texto es una instancia de SQL **seleccione** instrucción (en cuyo caso, porque SQL **seleccione** especifica un conjunto de filas, el comando crea automáticamente un conjunto de filas).

## <a name="rowsets"></a>Conjuntos de filas

Conjuntos de filas de mostrar datos en formato tabular. Un índice es un caso especial de un conjunto de filas. Puede crear conjuntos de filas de la sesión o el comando.

### <a name="schema-rowsets"></a>Conjuntos de filas de esquema

Los esquemas tienen metadatos (información estructural) sobre una base de datos. Conjuntos de filas de esquema son conjuntos de filas que tienen información de esquema. Algunos proveedores de OLE DB para DBMS admiten objetos de conjunto de filas de esquema. Para obtener más información acerca de los conjuntos de filas de esquema, vea [obtener metadatos con conjuntos de filas de esquema](../../data/oledb/obtaining-metadata-with-schema-rowsets.md) y [clases de conjunto de filas de esquema y clases Typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md).

### <a name="view-objects"></a>Objetos de vista

Un objeto de vista define un subconjunto de las filas y columnas de un conjunto de filas. No tiene datos propios. Objetos de vista no pueden combinar datos de varios conjuntos de filas.

## <a name="accessors"></a>Descriptores de acceso

Sólo OLE DB usa el concepto de descriptores de acceso. Un descriptor de acceso describe cómo se almacenan los datos en el consumidor. Tiene un conjunto de enlaces (denominado un mapa de columnas) entre los campos de conjunto de filas (columnas) y los miembros de datos que se declaran en el consumidor.

##  <a name="vcconoledbcomponents_transactions"></a> Transacciones

Los objetos de transacción se utilizan al confirmar o anular transacciones anidadas en que no sea el nivel más bajo. Una transacción es una unidad de trabajo indivisible definida por la prueba de ácido. ACID es el acrónimo:

- Atomicidad, no pueden dividirse en unidades más pequeñas de trabajo

- Simultaneidad, puede haber más de una transacción a la vez

- Aislamiento de una transacción tiene un conocimiento limitado acerca de los cambios realizados por otro

- Durabilidad, la transacción realiza cambios persistentes

## <a name="enumerators"></a>Enumeradores

Los enumeradores buscan orígenes de datos disponibles y otros enumeradores. Los consumidores que no se personaliza para un origen de datos determinado utilizar enumeradores para buscar un origen de datos para utilizarlo.

Un enumerador de raíz, que se incluye en el SDK de Microsoft Data Access, recorre el registro, busque los orígenes de datos y otros enumeradores. Otros enumeradores recorren el registro o la búsqueda de una manera específica del proveedor.

## <a name="errors"></a>Errores

Cualquier interfaz en cualquier objeto de OLE DB puede generar errores. Los errores tienen información adicional sobre el error, incluido un objeto opcional de error personalizado. Esta información se almacena en un valor HRESULT.

## <a name="notifications"></a>Notificaciones

Las notificaciones se utilizan en grupos de consumidores cooperativos comparten un conjunto de filas (donde compartir significa que se supone que los consumidores de estar trabajando dentro de la misma transacción). Las notificaciones de permiten que los consumidores cooperativos comparten un conjunto de filas para mantenerse informado sobre las acciones realizadas por sus homólogos el conjunto de filas.

## <a name="see-also"></a>Vea también

[Programación de OLE DB](../../data/oledb/ole-db-programming.md)<br/>
[Información general sobre la programación de OLE DB](../../data/oledb/ole-db-programming-overview.md)