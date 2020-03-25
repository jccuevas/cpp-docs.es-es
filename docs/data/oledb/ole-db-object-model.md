---
title: Modelo de objetos OLE DB
ms.date: 10/22/2018
helpviewer_keywords:
- rowsets, OLE DB object model
- OLE DB, object model
ms.assetid: 1a274a25-c310-4430-a1ec-bd2bd8120eff
ms.openlocfilehash: 192195d02b034546e50b1cb860b1f11c47dc2b65
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210124"
---
# <a name="ole-db-object-model"></a>Modelo de objetos OLE DB

El modelo de objetos de OLE DB se compone de los siguientes objetos o componentes. Los primeros cuatro objetos o componentes enumerados (orígenes de datos, sesiones, comandos y conjuntos de filas) le permiten conectarse a un origen de datos y verlo. El resto, a partir de los descriptores de acceso, se relaciona con trabajar con los datos cuando se muestran.

## <a name="data-sources"></a>Orígenes de datos

Los objetos de origen de datos permiten conectarse a un origen de datos, como un archivo o DBMS. Un objeto de origen de datos crea y administra la conexión y contiene permisos e información de autenticación (por ejemplo, el nombre de inicio de sesión y la contraseña). Un objeto de origen de datos puede crear una o varias sesiones.

## <a name="sessions"></a>Sesiones

Una sesión administra una interacción determinada con el origen de datos para consultar y recuperar datos. Cada sesión es una transacción única. Una transacción es una unidad de trabajo indivisible definida por la prueba ACID. Para obtener una definición de ACID, consulte [transacciones](#vcconoledbcomponents_transactions).

Las sesiones realizan tareas importantes como abrir conjuntos de filas y devolver el objeto de origen de datos que lo creó. Las sesiones también pueden devolver metadatos o información sobre el propio origen de datos (como la información de tabla).

Una sesión puede crear uno o más comandos.

## <a name="commands"></a>Comandos:

Los comandos ejecutan un comando de texto como una instrucción SQL. Si el comando de texto especifica un conjunto de filas, como una instrucción **Select** de SQL, el comando crea el conjunto de filas.

Un comando es simplemente un contenedor para un comando de texto, que es una cadena (como una instrucción SQL) pasada desde un consumidor a un objeto de origen de datos para que lo ejecute el almacén de datos subyacente del proveedor. Normalmente, el comando de texto es una instrucción **Select** de SQL (en cuyo caso, dado que SQL **Select** especifica un conjunto de filas, el comando crea automáticamente un conjunto de filas).

## <a name="rowsets"></a>Conjuntos de filas

Los conjuntos de filas muestran los datos en formato tabular. Un índice es un caso especial de un conjunto de filas. Puede crear conjuntos de filas desde la sesión o el comando.

### <a name="schema-rowsets"></a>Conjuntos de filas de esquema

Los esquemas tienen metadatos (información estructural) sobre una base de datos. Los conjuntos de filas de esquema son conjuntos de filas que tienen información de esquema. Algunos proveedores de OLE DB de DBMS admiten objetos de conjunto de filas de esquema. Para obtener más información sobre los conjuntos de filas de esquema, vea [obtener metadatos con conjuntos](../../data/oledb/obtaining-metadata-with-schema-rowsets.md) de filas de esquema y clases [de conjunto de filas de esquema y clases typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md).

### <a name="view-objects"></a>Objetos de vista

Un objeto de vista define un subconjunto de las filas y columnas de un conjunto de filas. No tiene datos propios. Los objetos de vista no pueden combinar datos de varios conjuntos de filas.

## <a name="accessors"></a>Descriptores

Solo OLE DB usa el concepto de descriptores de acceso. Un descriptor de acceso describe cómo se almacenan los datos en un consumidor. Tiene un conjunto de enlaces (denominado mapa de columnas) entre los campos del conjunto de filas (columnas) y los miembros de datos que se declaran en el consumidor.

##  <a name="transactions"></a><a name="vcconoledbcomponents_transactions"></a> Transactions

Los objetos de transacción se utilizan al confirmar o anular las transacciones anidadas que no sean el nivel más bajo. Una transacción es una unidad de trabajo indivisible definida por la prueba ACID. ACID significa:

- Atomicidad, no se puede dividir en unidades de trabajo más pequeñas

- Simultaneidad, puede haber más de una transacción a la vez

- Aislamiento, una transacción tiene un conocimiento limitado sobre los cambios realizados por otro

- Durabilidad, la transacción realiza cambios persistentes

## <a name="enumerators"></a>Enumerators

Los enumeradores buscan los orígenes de datos disponibles y otros enumeradores. Los consumidores que no están personalizados para un origen de datos determinado usan enumeradores para buscar un origen de datos que se va a usar.

Un enumerador raíz, incluido en el SDK de Microsoft Data Access, recorre el registro en busca de orígenes de datos y otros enumeradores. Otros enumeradores atraviesan el registro o buscan en una forma específica del proveedor.

## <a name="errors"></a>Errors

Cualquier interfaz de cualquier objeto OLE DB puede generar errores. Los errores tienen información adicional sobre un error, incluido un objeto de error personalizado opcional. Esta información se almacena en HRESULT.

## <a name="notifications"></a>Notificaciones

Las notificaciones se usan en grupos de consumidores cooperativos que comparten un conjunto de filas (donde el uso compartido significa que se supone que los consumidores trabajan dentro de la misma transacción). Las notificaciones permiten a los consumidores cooperativos que comparten un conjunto de filas ser informados sobre las acciones del conjunto de filas realizadas por sus elementos del mismo nivel.

## <a name="see-also"></a>Consulte también

[Programación de OLE DB](../../data/oledb/ole-db-programming.md)<br/>
[Información general sobre la programación de OLE DB](../../data/oledb/ole-db-programming-overview.md)
