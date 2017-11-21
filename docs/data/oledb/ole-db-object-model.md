---
title: Modelo de objetos OLE DB | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- rowsets, OLE DB object model
- OLE DB, object model
ms.assetid: 1a274a25-c310-4430-a1ec-bd2bd8120eff
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b91198d4280a271c775b7be79ecab3da7271fb57
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="ole-db-object-model"></a>Modelo de objetos OLE DB
El modelo de objetos OLE DB consta de los siguientes objetos o componentes. Los primeros cuatro objetos o componentes (orígenes de datos, sesiones, comandos y conjuntos de filas) permiten conectarse a un origen de datos y verlo. El resto, a partir de los descriptores de acceso, se refieren a trabajar con los datos cuando se muestre.  
  
## <a name="data-sources"></a>Orígenes de datos  
 Objetos de origen de datos permiten conectarse a un origen de datos como un archivo o DBMS. Un objeto de origen de datos crea y administra la conexión y contiene información de permisos y las autenticaciones (por ejemplo, nombre de inicio de sesión y contraseña). Un objeto de origen de datos puede crear una o varias sesiones.  
  
## <a name="sessions"></a>Sesiones  
 Una sesión administra una determinado interacción con el origen de datos para consultar y recuperar datos. Cada sesión es una sola transacción. Una transacción es una unidad de trabajo indivisible definida por la prueba ACID. Para una definición de ACID, vea [transacciones](#vcconoledbcomponents_transactions).  
  
 Las sesiones realizan tareas importantes como abrir conjuntos de filas y devolver el objeto de origen de datos que lo creó. Las sesiones también pueden devolver metadatos o información sobre el origen de datos (por ejemplo, información de la tabla).  
  
 Una sesión puede crear uno o varios comandos.  
  
## <a name="commands"></a>Comandos  
 Comandos ejecutan un comando de texto como una instrucción SQL. Si el comando de texto especifica un conjunto de filas, como una instancia de SQL **seleccione** instrucción, el comando crea el conjunto de filas.  
  
 Un comando es simplemente un contenedor para un comando de texto, que es una cadena (por ejemplo, una instrucción SQL) que se pasan de un consumidor a un objeto de origen de datos para la ejecución por el almacén de datos subyacente del proveedor. Normalmente, el comando de texto es una instancia de SQL **seleccione** instrucción (en cuyo caso, porque SQL **seleccione** especifica un conjunto de filas, el comando crea automáticamente un conjunto de filas).  
  
## <a name="rowsets"></a>Conjuntos de filas  
 Conjuntos de filas exponen datos en formato tabular. Un índice es un caso especial de un conjunto de filas. Puede crear conjuntos de filas de la sesión o el comando.  
  
### <a name="schema-rowsets"></a>Conjuntos de filas de esquema  
 Los esquemas contienen metadatos (información estructural) sobre una base de datos. Conjuntos de filas de esquema son conjuntos de filas que contienen información de esquema. Algunos proveedores de OLE DB para DBMS admiten objetos de conjunto de filas de esquema. Para obtener más información sobre conjuntos de filas de esquema, consulte [obtener metadatos con conjuntos de filas de esquema](../../data/oledb/obtaining-metadata-with-schema-rowsets.md) y [clases de conjunto de filas de esquema y clases Typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md).  
  
### <a name="view-objects"></a>Objetos de vista  
 Un objeto de vista define un subconjunto de las filas y columnas de un conjunto de filas. No contiene datos propios. Objetos de vista no pueden combinar datos de varios conjuntos de filas.  
  
## <a name="accessors"></a>Descriptores de acceso  
 Sólo OLE DB usa el concepto de descriptores de acceso. Un descriptor de acceso describe cómo se almacenan los datos en un consumidor. Contiene un conjunto de enlaces (denominado un mapa de columnas) entre campos de conjunto de filas (columnas) y los miembros de datos que se declaran en el consumidor.  
  
##  <a name="vcconoledbcomponents_transactions"></a>Transacciones  
 Objetos de transacción se utilizan al confirmar o anular transacciones anidadas en que no sea el nivel más bajo. Una transacción es una unidad de trabajo indivisible definida por la prueba ACID. El acrónimo ACID:  
  
-   Atomicidad: no se puede dividir en unidades más pequeñas de trabajo.  
  
-   Simultaneidad: puede haber más de una transacción a la vez.  
  
-   Aislamiento: una transacción tiene un conocimiento limitado sobre los cambios realizados por otro.  
  
-   Durabilidad: la transacción realiza cambios que son persistentes.  
  
## <a name="enumerators"></a>Enumeradores  
 Los enumeradores buscan orígenes de datos disponibles y otros enumeradores. Los consumidores que no se personalizan para un origen de datos determinado usar enumeradores para buscar un origen de datos para utilizarlo.  
  
 Un enumerador raíz, incluido en el SDK de Microsoft Data Access, recorre el registro buscando orígenes de datos y otros enumeradores. Resto de enumeradores recorre el registro o la búsqueda de una manera específica del proveedor.  
  
## <a name="errors"></a>Errores  
 Cualquier interfaz a cualquier objeto de OLE DB puede generar errores. Errores contienen información adicional sobre un error, incluido un objeto opcional de error personalizado. Esta información se encuentra en un valor HRESULT.  
  
## <a name="notifications"></a>Notificaciones  
 Las notificaciones se usan en grupos de consumidores cooperativos comparten un conjunto de filas (donde compartir significa que se supone que los consumidores de estar trabajando dentro de la misma transacción). Las notificaciones de permiten que los consumidores cooperativos comparten un conjunto de filas estar informado acerca de las acciones en el conjunto de filas realizadas por sus colegas.  
  
## <a name="see-also"></a>Vea también  
 [Programación de OLE DB](../../data/oledb/ole-db-programming.md)   
 [Información general sobre la programación de OLE DB](../../data/oledb/ole-db-programming-overview.md)