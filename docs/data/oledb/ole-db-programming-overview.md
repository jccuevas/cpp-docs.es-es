---
title: "Informaci&#243;n general sobre la programaci&#243;n de OLE DB | Microsoft Docs"
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
  - "OLE DB, acerca de OLE DB"
  - "Universal Data Access"
ms.assetid: a5a69730-2793-4277-a67d-6f3c8edab6df
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Informaci&#243;n general sobre la programaci&#243;n de OLE DB
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

¿En qué consiste OLE DB y qué es lo que lo hace distinto de otras tecnologías de base de datos?  OLE DB es una tecnología de base de datos de alto rendimiento basada en COM y creada por Microsoft.  Lo que diferencia a OLE DB de otras tecnologías de base de datos de Microsoft es la forma en que proporciona acceso universal a los datos.  
  
## Acceso universal a los datos \(Universal Data Access\)  
 La estrategia de Microsoft de acceso universal a los datos, conocida como *Universal Data Access*, proporciona una forma común de obtener acceso a los datos sin importar la forma en que se almacenan.  En una situación típica de negocios, una gran cantidad de información se almacena fuera de las bases de datos corporativas.  Esta información se halla en sistemas de archivos \(FAT o NTFS, por ejemplo\), archivos secuenciales indizados, bases de datos personales \(como Access\), hojas de cálculo \(como Excel\), aplicaciones de planeación de proyectos \(como Project\) y correo electrónico \(como Outlook\).  
  
 El acceso a estos datos con las diferentes aplicaciones asociadas constituye un importante cuello de botella en el flujo de trabajo o, cuando menos, una serie de molestias.  La mayoría de las compañías se encuentran en esta situación y se enfrentan al problema consolidando la información en un sistema de administración de bases de datos \(DBMS\).  Sin embargo, tal proceso es costoso, consume mucho tiempo y en muchas ocasiones no es práctico.  
  
 La alternativa consiste en programar una solución Universal Data Access.  OLE DB y ADO son compatibles con el estándar Universal Data Access.  De ellos dos, OLE DB da mejor rendimiento y se recomienda para el uso con aplicaciones de Visual C\+\+.  
  
 Universal Data Access implica dos características: la primera es una consulta distribuida o acceso uniforme a varios orígenes de datos \(distribuidos\) y la segunda es la posibilidad de poner los orígenes de datos no DBMS a disposición de las aplicaciones de base de datos.  
  
-   Consulta distribuida  
  
     La capacidad de obtener acceso a los datos de manera uniforme en múltiples orígenes de datos \(distribuidos\).  Los orígenes de datos pueden ser del mismo tipo \(como dos bases de datos de Access\) o de diferente tipo \(como una base de datos de SQL Server y una base de datos de Access\).  El acceso uniforme significa que se pueda ejecutar la misma consulta en todos los orígenes de datos con iguales resultados.  
  
-   Acceso no DBMS  
  
     La capacidad de hacer accesibles los orígenes de datos no DBMS a las aplicaciones de base de datos.  Los ejemplos de orígenes de datos DBMS incluyen IMS, DB2, Oracle, SQL Server, Access y Paradox.  Algunos ejemplos de orígenes de datos no DBMS son: información en sistemas de archivos, correo electrónico, hojas de cálculo y herramientas de administración de proyectos.  
  
 Piense en un escenario en el que un departamento de ventas necesita buscar todos los mensajes de correo electrónico recibidos durante un período de tiempo de una semana de los clientes de un área concreta.  Esta consulta puede requerir una búsqueda en un archivo del buzón de la aplicación de correo electrónico y otra en una tabla de clientes de Access para especificar los nombres de los clientes.  Si bien Access es una aplicación DBMS, Outlook no lo es.  
  
 OLE DB permite desarrollar aplicaciones que obtienen acceso a diversos orígenes de datos, tanto si son DBMS como si no lo son.  OLE DB hace posible el acceso universal a datos mediante interfaces COM compatibles con la funcionalidad DBMS de un origen de datos determinado.  COM reduce la duplicación innecesaria de servicios y proporciona interoperabilidad máxima, no sólo entre orígenes de datos, sino también entre otras aplicaciones.  
  
## Ventajas de COM  
 Aquí es donde entra en juego COM.  OLE DB es un conjunto de interfaces COM.  Al obtener acceso a los datos a través de un conjunto uniforme de interfaces, se puede organizar una base de datos en una matriz de componentes cooperativos.  
  
 Basado en la especificación COM, OLE DB define una colección ampliable y mantenible de interfaces que extienden y encapsulan partes coherentes y reutilizables de la funcionalidad DBMS.  Estas interfaces definen los límites de componentes DBMS como contenedores de filas, procesadores de consultas y coordinadores de transacciones, que permiten el acceso transaccional uniforme a diversos orígenes de información.  
  
 Habitualmente, las aplicaciones OLE DB se programan como DLLs, pero su implementación COM compensa las desventajas de las DLL \(como los problemas de nombres y versiones\) al usar código dividido en componentes.  En OLE DB se llama a las interfaces o se obtiene acceso a otros componentes por medio de sus identificadores únicos globales \(GUID\).  
  
 Por último, COM efectúa un seguimiento del uso de los componentes por medio del recuento de referencias.  Al llamar a un método en una interfaz, se incrementa el recuento de referencias; cuando el método devuelve un valor, se decrementa.  Cuando el número de referencias es igual a cero, se libera el componente al que pertenece el método.  
  
## Vea también  
 [Programación de OLE DB](../../data/oledb/ole-db-programming.md)   
 [Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [plantillas OLE DB](../../data/oledb/ole-db-templates.md)