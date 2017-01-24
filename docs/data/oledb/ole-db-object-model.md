---
title: "Modelo de objetos OLE DB | Microsoft Docs"
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
  - "OLE DB, modelo de objetos"
  - "conjuntos de filas, modelo de objetos OLE DB"
ms.assetid: 1a274a25-c310-4430-a1ec-bd2bd8120eff
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Modelo de objetos OLE DB
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

El modelo de objetos de OLE DB comprende los siguientes objetos o componentes:  Los primeros cuatro objetos o componentes \(orígenes de datos, sesiones, comandos y conjuntos de filas\) permiten conectarse a otro origen de datos y verlo.  El resto, a partir de los descriptores de acceso, está relacionado con el trabajo con los datos cuando se muestran.  
  
## Orígenes de datos  
 Los objetos de origen de datos permiten conectarse a un origen de datos, como un archivo o DBMS.  Un objeto de origen de datos crea y administra la conexión y contiene información de permisos y autenticación \(como el nombre de usuario y contraseña\).  Un objeto de origen de datos puede crear una o varias sesiones.  
  
## Sesiones  
 Una sesión es la encargada de controlar la interacción que tiene lugar con el origen de datos para consultar y recuperar datos.  Cada sesión es una transacción.  Una transacción es una unidad de trabajo indivisible según lo definido por los criterios ACID.  Para consultar una definición de ACID, vea [Transacciones](#vcconoledbcomponents_transactions).  
  
 Las sesiones realizan tareas importantes como la apertura de conjuntos de filas y la devolución del objeto de origen de datos que las creó.  Las sesiones también pueden devolver metadatos o información acerca del propio origen de datos \(como información sobre sus tablas\).  
  
 Una sesión puede crear uno o varios comandos.  
  
## Comandos  
 Los comandos ejecutan un comando de texto, como por ejemplo una instrucción SQL.  Si el comando de texto especifica un conjunto de filas, como una instrucción **SELECT** de SQL, el comando crea el conjunto de filas.  
  
 Un comando es sencillamente un contenedor para un comando de texto, que a su vez es una cadena \(como una instrucción SQL\) pasada por un consumidor a un objeto de origen de datos para su ejecución por el almacén de datos subyacente del proveedor.  Normalmente, el comando de texto es una instrucción **SELECT** de SQL \(en ese caso, como **SELECT** de SQL especifica un conjunto de filas, el comando crea automáticamente un conjunto de filas\).  
  
## Conjuntos de filas  
 Los conjuntos de filas exponen datos en formato tabular.  Un índice es un caso especial de conjunto de filas.  Se pueden crear conjuntos de filas desde la sesión o desde un comando.  
  
### Conjuntos de filas de esquema  
 Los esquemas contienen metadatos \(información estructural\) sobre una base de datos.  Los conjuntos de filas de esquema son conjuntos de filas que contienen información de esquema.  Algunos proveedores OLE DB para DBMS admiten objetos de conjunto de filas de esquema.  Para obtener más información sobre los conjuntos de filas de esquema, vea [Obtener metadatos con conjuntos de filas de esquema](../../data/oledb/obtaining-metadata-with-schema-rowsets.md) y [Clases de conjunto de filas de esquema y clases typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md).  
  
### Objetos de vista  
 Un objeto de vista define un subconjunto de las filas y columnas de un conjunto de filas.  No contiene datos por sí solo.  Los objetos de vista combinan los datos de múltiples conjuntos de filas.  
  
## Descriptores de acceso  
 Sólo OLE DB usa el concepto de descriptor de acceso.  Un descriptor de acceso describe cómo están almacenados los datos en un consumidor.  Contiene un conjunto de enlaces \(denominado mapa de columnas\) entre campos de conjunto de filas \(columnas\) y los miembros de datos que se declaran en el consumidor.  
  
##  <a name="vcconoledbcomponents_transactions"></a> Transacciones  
 Los objetos de transacción se utilizan al confirmar o anular transacciones anidadas en un nivel que no es el nivel inferior.  Una transacción es una unidad de trabajo indivisible según lo definido por los criterios ACID.  ACID corresponde en inglés a:  
  
-   Atomicidad \(*Atomicity*\): no se puede dividir en unidades de trabajo más pequeñas.  
  
-   Simultaneidad \(*Concurrency*\): puede haber más de una transacción a la vez.  
  
-   Aislamiento \(*Isolation*\): una transacción tiene un conocimiento limitado de los cambios efectuados por otra transacción.  
  
-   Durabilidad \(*Durability*\): la transacción realiza cambios que son persistentes.  
  
## Enumeradores  
 Los enumeradores buscan orígenes de datos disponibles y otros enumeradores.  Los consumidores que no están personalizados para un origen de datos particular utilizan enumeradores para buscar el origen de datos con el que trabajarán.  
  
 Un enumerador raíz, incluido en el SDK de Microsoft Data Access Components \(MDAC\), recorre el Registro buscando orígenes de datos y otros enumeradores.  El resto de enumeradores recorre el Registro o busca de la manera especificada por el proveedor.  
  
## Errores  
 Cualquier interfaz de cualquier objeto OLE DB puede generar errores.  Los errores contienen información adicional sobre un error, incluido un objeto opcional de error personalizado.  Esta información se encuentra en un valor HRESULT.  
  
## Notificaciones  
 Las notificaciones se usan en grupos de consumidores cooperantes que comparten un conjunto de filas \(donde compartir significa que se supone que los consumidores trabajan dentro de la misma transacción\).  Las notificaciones permiten también a los consumidores cooperantes que comparten un conjunto de filas recibir información de las acciones realizadas por otros consumidores en el conjunto de filas.  
  
## Vea también  
 [Programación de OLE DB](../../data/oledb/ole-db-programming.md)   
 [Información general sobre la programación de OLE DB](../../data/oledb/ole-db-programming-overview.md)