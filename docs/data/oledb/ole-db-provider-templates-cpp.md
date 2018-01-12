---
title: Plantillas del proveedor OLE DB (C++) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- OLE DB providers [C++], about providers
- databases [C++], OLE DB templates
- OLE DB provider templates [C++], about OLE DB provider templates
- templates [C++], OLE DB
ms.assetid: fccff85f-2af8-4500-82bd-6312d28a74b8
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f95b32d62d964c83853025ed4e4af9b90e7a630a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="ole-db-provider-templates-c"></a>Plantillas de proveedores OLE DB (C++)
OLE DB es una parte importante de la estrategia de Microsoft Universal Data Access. El diseño de OLE DB permite el acceso a datos de alto rendimiento desde cualquier origen de datos. Los datos tabulares están visibles a través de OLE DB, independientemente de si proviene de una base de datos. Esta flexibilidad ofrece una enorme cantidad de energía.  
  
 Como se explica en [consumidores OLE DB y proveedores](../../data/oledb/ole-db-consumers-and-providers.md), OLE DB utiliza el concepto de consumidores y proveedores. El consumidor realiza las solicitudes de datos; el proveedor devuelve datos en formato tabular al consumidor. Desde una perspectiva de programación, la implicación más importante de este modelo es que el proveedor debe implementar cualquier llamada que se puede hacer que el consumidor.  
  
## <a name="what-is-a-provider"></a>¿Qué es un proveedor?  
 Un proveedor OLE DB es un conjunto de objetos COM que atiende llamadas a las interfaces de un objeto de consumidor, transferencia de datos en formato tabular desde un origen duradero (denominado almacén de datos) para el consumidor.  
  
 Los proveedores pueden ser simples o complejos. El proveedor puede admitir una cantidad mínima de funcionalidad o un proveedor de calidad de producción completamente desarrollado mediante la implementación de más interfaces. Un proveedor puede devolver una tabla, permitir que el cliente determinar el formato de la tabla y realizar operaciones en los datos.  
  
 Cada proveedor implementa un conjunto estándar de objetos COM para procesar las solicitudes del cliente, con un significado estándar que cualquier consumidor de OLE DB puede tener acceso a datos de cualquier proveedor, independientemente del lenguaje (como C++ y básico).  
  
 Cada objeto COM contiene varias interfaces, algunos de los cuales son necesarios y algunos de los cuales son opcionales. Al implementar las interfaces obligatorias, un proveedor garantiza un nivel mínimo de funcionalidad (denominado conformidad) que cualquier cliente debe ser capaz de usar. Un proveedor puede implementar interfaces opcionales para proporcionar funcionalidad adicional. [La arquitectura de plantillas de proveedor de OLE DB](../../data/oledb/ole-db-provider-template-architecture.md) describe estas interfaces en detalle. El cliente siempre debe llamar a `QueryInterface` para determinar si un proveedor admite una interfaz determinada.  
  
## <a name="ole-db-specification-level-support"></a>Compatibilidad con nivel de OLE DB especificación  
 Las plantillas de proveedor OLE DB admiten la especificación de la versión 2.7 de OLE DB. Con las plantillas de proveedor OLE DB, puede implementar un proveedor compatible con el nivel 0. El ejemplo de proveedor, por ejemplo, usa las plantillas para implementar un servidor de aplicación de comandos que se ejecuta el comando DIR de DOS para consultar el sistema de archivos. El ejemplo de proveedor devuelve la información de directorio en un conjunto de filas, que es el mecanismo estándar de OLE DB para devolver datos tabulares.  
  
 El tipo más sencillo de proveedor admitido por las plantillas OLE DB es un proveedor de sólo lectura con ningún comando. También se admiten proveedores con comandos, como son la capacidad de marcar y lectura/escritura. Puede implementar un proveedor de lectura/escritura al escribir código adicional. Las transacciones y conjuntos de filas dinámicos no son compatibles con la versión actual, pero puede agregar si desea.  
  
## <a name="when-do-you-need-to-create-an-ole-db-provider"></a>¿Cuando necesite crear un proveedor OLE DB?  
 No siempre necesitan crear su propio proveedor; Microsoft proporciona varios proveedores estándares ya preparados en el **propiedades de vínculo de datos** cuadro de diálogo de Visual C++. La razón principal para crear un proveedor OLE DB es aprovechar las ventajas de la estrategia de Universal Data Access. Por lo que algunas de las ventajas de hacerlo son:  
  
-   Acceso a datos mediante cualquier lenguaje, como C++, Basic y Visual Basic Scripting Edition. Permite a los programadores diferentes en su organización para tener acceso a los mismos datos de la misma manera, independientemente del lenguaje en que utilice.  
  
-   Permite exponer los datos a otros datos de orígenes como SQL Server, Excel y Access. Esto puede resultar muy útil si desea transferir datos entre los diferentes formatos.  
  
-   Participa en las operaciones de origen de datos entre (heterogéneos). Esto puede ser una forma muy eficaz de almacenamiento de datos. Mediante el uso de proveedores OLE DB, puede mantener los datos en su formato nativo y seguir siendo capaces de acceder a ella mediante una operación sencilla.  
  
-   Agregar capacidades adicionales a los datos, como el procesamiento de consultas.  
  
-   Aumento del rendimiento de acceso a datos mediante el control de la manipulación.  
  
-   Aumentar la solidez. Si tiene un formato de datos confidenciales que sólo un programador puede tener acceso, están en riesgo. Con los proveedores OLE DB, puede abrir ese formato propietario a todos los programadores.  
  
## <a name="read-only-and-updatable-providers"></a>Proveedores de sólo lectura y actualizables  
 Los proveedores pueden variar mucho en complejidad y la funcionalidad. Es útil clasificar los proveedores en solo lectura o proveedores actualizables:  
  
-   Visual C++ 6.0 admite solo proveedores de sólo lectura. [Crear un proveedor OLE DB](../../data/oledb/creating-an-ole-db-provider.md) se explica cómo crear un proveedor de sólo lectura.  
  
-   Visual C++ admite proveedores actualizables, que pueden actualizar (escribir en) el almacén de datos. Para obtener información sobre proveedores actualizables, vea [crear un proveedor actualizable](../../data/oledb/creating-an-updatable-provider.md); el [UpdatePV](http://msdn.microsoft.com/en-us/c8bed873-223c-4a7d-af55-f90138c6f38f) es un ejemplo de un proveedor actualizable.  
  
 Para obtener más información, consulte:  
  
-   [La arquitectura de plantilla de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)  
  
-   [Crear un proveedor OLE DB](../../data/oledb/creating-an-ole-db-provider.md)  
  
-   [Programación de OLE DB](../../data/oledb/ole-db-programming.md)  
  
## <a name="see-also"></a>Vea también  
 [Acceso a datos](../data-access-in-cpp.md)   
 [Documentación del SDK de OLE DB](https://msdn.microsoft.com/en-us/library/ms722784.aspx)   
 [Referencia del programador OLE DB](https://msdn.microsoft.com/en-us/library/ms713643.aspx)