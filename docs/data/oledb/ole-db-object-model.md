---
title: Modelo de objetos OLE DB
ms.date: 10/22/2018
helpviewer_keywords:
- rowsets, OLE DB object model
- OLE DB, object model
ms.assetid: 1a274a25-c310-4430-a1ec-bd2bd8120eff
ms.openlocfilehash: b37205eb91317c602010a4b568057845b2345ef0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369794"
---
# <a name="ole-db-object-model"></a>Modelo de objetos OLE DB

El modelo de objetos OLE DB se compone de los siguientes objetos o componentes. Los primeros cuatro objetos o componentes enumerados (orígenes de datos, sesiones, comandos y conjuntos de filas) le permiten conectarse a un origen de datos y verlo. El resto, empezando por los descriptores de acceso, se relacionan con trabajar con los datos cuando se muestran.

## <a name="data-sources"></a>Orígenes de datos

Los objetos de origen de datos le permiten conectarse a un origen de datos como un archivo o DBMS. Un objeto de origen de datos crea y administra la conexión y contiene información de permisos y autenticaciones (como el nombre de inicio de sesión y la contraseña). Un objeto de origen de datos puede crear una o varias sesiones.

## <a name="sessions"></a>Sesiones

Una sesión administra una interacción determinada con el origen de datos para consultar y recuperar datos. Cada sesión es una sola transacción. Una transacción es una unidad de trabajo indivisible definida por la prueba ACID. Para obtener una definición de ACID, vea [Transacciones](#vcconoledbcomponents_transactions).

Las sesiones realizan tareas importantes, como abrir conjuntos de filas y devolver el objeto de origen de datos que lo creó. Las sesiones también pueden devolver metadatos o información sobre el propio origen de datos (por ejemplo, información de tabla).

Una sesión puede crear uno o varios comandos.

## <a name="commands"></a>Comandos:

Los comandos ejecutan un comando de texto como una instrucción SQL. Si el comando text especifica un conjunto de filas, como una instrucción **SELECT** de SQL, el comando crea el conjunto de filas.

Un comando es simplemente un contenedor para un comando de texto, que es una cadena (como una instrucción SQL) que se pasa de un consumidor a un objeto de origen de datos para su ejecución por el almacén de datos subyacente del proveedor. Normalmente, el comando text es una instrucción **SELECT** de SQL (en cuyo caso, dado que **SELECT** de SQL especifica un conjunto de filas, el comando crea automáticamente un conjunto de filas).

## <a name="rowsets"></a>Conjuntos de filas

Los conjuntos de filas muestran los datos en formato tabular. Un índice es un caso especial de un conjunto de filas. Puede crear conjuntos de filas a partir de la sesión o el comando.

### <a name="schema-rowsets"></a>Conjuntos de filas de esquema

Los esquemas tienen metadatos (información estructural) sobre una base de datos. Los conjuntos de filas de esquema son conjuntos de filas que tienen información de esquema. Algunos proveedores OLE DB para DBMS admiten objetos de conjunto de filas de esquema. Para obtener más información acerca de los conjuntos de filas de esquema, vea [Obtención de metadatos con conjuntos](../../data/oledb/obtaining-metadata-with-schema-rowsets.md) de filas de esquema y clases de conjunto de filas de [esquema y clases typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md).

### <a name="view-objects"></a>Ver objetos

Un objeto de vista define un subconjunto de las filas y columnas de un conjunto de filas. No tiene datos propios. Los objetos de vista no pueden combinar datos de varios conjuntos de filas.

## <a name="accessors"></a>Descriptores de acceso

Solo OLE DB utiliza el concepto de descriptores de acceso. Un descriptor de acceso describe cómo se almacenan los datos en un consumidor. Tiene un conjunto de enlaces (denominado mapa de columnas) entre los campos de conjunto de filas (columnas) y los miembros de datos que se declaran en el consumidor.

## <a name="transactions"></a><a name="vcconoledbcomponents_transactions"></a>Transacciones

Los objetos de transacción se utilizan al confirmar o anular transacciones anidadas en un nivel distinto del nivel más bajo. Una transacción es una unidad de trabajo indivisible definida por la prueba ACID. ACID significa:

- Atomicidad, no se puede dividir en unidades de trabajo más pequeñas

- Simultaneidad, más de una transacción puede ocurrir a la vez

- Aislamiento, una transacción tiene un conocimiento limitado sobre los cambios realizados por otro

- Durabilidad, la transacción realiza cambios persistentes

## <a name="enumerators"></a>Enumerators

Los enumeradores buscan orígenes de datos disponibles y otros enumeradores. Los consumidores que no están personalizados para un origen de datos determinado usan enumeradores para buscar un origen de datos que se va a usar.

Un enumerador raíz, incluido en el SDK de Microsoft Data Access, recorre el registro en busca de orígenes de datos y otros enumeradores. Otros enumeradores recorren el registro o la búsqueda de una manera específica del proveedor.

## <a name="errors"></a>Errors

Cualquier interfaz en cualquier objeto OLE DB puede generar errores. Los errores tienen información adicional acerca de un error, incluido un objeto de error personalizado opcional. Esta información se almacena en un HRESULT.

## <a name="notifications"></a>Notificaciones

Las notificaciones las usan los grupos de consumidores cooperantes que comparten un conjunto de filas (cuando el uso compartido significa que se supone que los consumidores trabajan dentro de la misma transacción). Las notificaciones permiten a los consumidores cooperantes que comparten un conjunto de filas informarse sobre las acciones en el conjunto de filas realizadas por sus pares.

## <a name="see-also"></a>Consulte también

[Programación OLE DB](../../data/oledb/ole-db-programming.md)<br/>
[Descripción general de la programación OLE DB](../../data/oledb/ole-db-programming-overview.md)
