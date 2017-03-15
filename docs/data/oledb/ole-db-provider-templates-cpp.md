---
title: "Plantillas de proveedores OLE DB (C++) | Microsoft Docs"
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
  - "bases de datos [C++], plantillas OLE DB"
  - "plantillas de proveedores OLE DB [C++], acerca de las plantillas del proveedor OLE DB"
  - "proveedores OLE DB [C++], acerca de los proveedores"
  - "plantillas [C++], OLE DB"
ms.assetid: fccff85f-2af8-4500-82bd-6312d28a74b8
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Plantillas de proveedores OLE DB (C++)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

OLE DB constituye una parte importante de la estrategia Universal Data Access de Microsoft.  El diseño OLE DB permite un acceso de alto rendimiento a datos de cualquier origen.  Cualquier conjunto de datos organizados en formato de tabla puede verse mediante OLE DB, independientemente de que provenga o no de una base de datos.  Esta flexibilidad ofrece una enorme eficacia.  
  
 Como se explica en [Consumidores y proveedores OLE DB](../../data/oledb/ole-db-consumers-and-providers.md), OLE DB utiliza el concepto de consumidores y proveedores.  El consumidor realiza solicitudes de datos y el proveedor devuelve al consumidor datos organizados en formato de tabla.  Desde una perspectiva de programación, la implicación más importante de este modelo es que el proveedor tiene que implementar cualquier llamada que pueda hacer el consumidor.  
  
## ¿Qué es un proveedor?  
 Un proveedor OLE DB es un conjunto de objetos COM que atiende llamadas de interfaz realizadas por un objeto consumidor, transfiriendo al consumidor datos organizados en formato de tabla desde un origen duradero \(denominado almacén de datos\).  
  
 Los proveedores pueden ser simples o complejos.  Un proveedor puede ofrecer una cantidad mínima de funcionalidad o una alta calidad de producción mediante la implementación de más interfaces.  Un proveedor puede devolver una tabla, permitir al cliente determinar su formato y realizar operaciones con los datos.  
  
 Cada proveedor implementa un conjunto estándar de objetos COM para procesar las solicitudes del cliente; estándar indica que cualquier consumidor OLE DB puede tener acceso a datos de cualquier proveedor, independientemente del lenguaje utilizado \(C\+\+, Basic, etc.\).  
  
 Cada objeto COM contiene varias interfaces, de las cuales parte son obligatorias y parte son opcionales.  Al implementar las interfaces exigidas, un proveedor garantiza un nivel mínimo de funcionalidad \(denominado conformidad\) que cualquier cliente debe poder utilizar.  Un proveedor puede implementar interfaces opcionales para proporcionar funcionalidad adicional.  [En Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md) se describen estas interfaces de forma detallada.  El cliente debe llamar siempre a `QueryInterface` para determinar si un proveedor admite una interfaz determinada.  
  
## Compatibilidad con el nivel de especificación de OLE DB  
 Las plantillas de proveedor OLE DB son compatibles con la especificación de OLE DB versión 2.7.  Mediante las plantillas de proveedor OLE DB, se puede implementar un proveedor compatible con el nivel 0.  La aplicación de ejemplo Provider utiliza las plantillas para implementar un servidor de comandos que no son de SQL \(MS\-DOS\) que ejecuta el comando DIR de DOS para consultar el sistema de archivos.  El ejemplo de proveedor devuelve la información del directorio en un conjunto de filas, que es el mecanismo estándar de OLE DB para devolver datos organizados en tablas.  
  
 El tipo de proveedor más sencillo compatible con las plantillas OLE DB es un proveedor de sólo lectura sin ningún comando.  También se admiten proveedores con comandos, el uso de marcadores y la capacidad de lectura y escritura.  Para implementar un proveedor de lectura y escritura debe agregar código adicional.  La versión actual no admite transacciones y conjuntos de filas dinámicos, pero se puede agregar esta funcionalidad si se desea.  
  
## ¿Cuándo debe crear un proveedor OLE DB?  
 No siempre tendrá que crear su propio proveedor; Microsoft proporciona varios proveedores estándar ya preparados en el cuadro de diálogo **Propiedades de vínculo de datos** de Visual C\+\+.  La razón principal para crear un proveedor OLE DB es aprovechar la estrategia Universal Data Access.  Algunas de las ventajas de hacerlo son:  
  
-   Acceso a datos con lenguajes como C\+\+, Basic y Visual Basic Scripting Edition.  Permite a los distintos programadores de la organización tener acceso a los mismos datos de la misma manera, independientemente del lenguaje que utilicen.  
  
-   Permite exponer los datos propios a otros orígenes de datos como SQL Server, Microsoft Excel y Access.  Esto puede ser muy útil si desea transferir datos entre formatos diferentes.  
  
-   Permite participar en operaciones con orígenes de datos cruzados \(heterogéneas\).  Esto puede ser una forma eficaz de implementar el almacenamiento de datos.  Con los proveedores OLE DB, puede conservar los datos en su formato nativo y tener acceso a los mismos mediante una operación sencilla.  
  
-   Permite agregar otras características a los datos, como el procesamiento de consultas.  
  
-   Permite aumentar el rendimiento del acceso a datos mediante el control de la manipulación de datos.  
  
-   Aumenta la robustez.  Si tiene un formato de datos propietario al que sólo tiene acceso un programador, pueden producirse problemas.  Al utilizar proveedores OLE DB, puede abrir ese formato propietario a todos los programadores.  
  
## Proveedores de sólo lectura y actualizables  
 La complejidad y la funcionalidad de los distintos proveedores varía mucho.  Es útil clasificarlos como proveedores de sólo lectura o proveedores actualizables:  
  
-   Visual C\+\+ 6.0 únicamente admitía proveedores de sólo lectura.  [Crear un proveedor OLE DB](../../data/oledb/creating-an-ole-db-provider.md) describe cómo se crea un proveedor de sólo lectura.  
  
-   Visual C\+\+ .NET admite proveedores actualizables, que pueden actualizar \(escribir en\) el almacén de datos.  Para obtener información sobre proveedores que se pueden utilizar, vea [Crear un proveedor actualizable](../../data/oledb/creating-an-updatable-provider.md); [UpdatePV](http://msdn.microsoft.com/es-es/c8bed873-223c-4a7d-af55-f90138c6f38f) es un ejemplo de proveedor que se puede actualizar.  
  
 Para obtener más información, vea:  
  
-   [Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)  
  
-   [Crear un proveedor OLE DB](../../data/oledb/creating-an-ole-db-provider.md)  
  
-   [Programación de OLE DB](../../data/oledb/ole-db-programming.md)  
  
## Vea también  
 [Acceso a datos en ASP.NET \(Visual Studio\)](../Topic/Data%20Access%20in%20Visual%20C++.md)   
 [Documentación del SDK de OLE DB](https://msdn.microsoft.com/en-us/library/ms722784.aspx)   
 [Referencia del programador de OLE DB](https://msdn.microsoft.com/en-us/library/ms713643.aspx)