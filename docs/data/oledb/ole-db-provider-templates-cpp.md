---
title: Plantillas de proveedores OLE DB (C++)
ms.date: 10/24/2018
helpviewer_keywords:
- OLE DB providers [C++], about providers
- databases [C++], OLE DB templates
- OLE DB provider templates [C++], about OLE DB provider templates
- templates [C++], OLE DB
ms.assetid: fccff85f-2af8-4500-82bd-6312d28a74b8
ms.openlocfilehash: 793aa08630ec92f99c33c2a4f3688e78630a6c58
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59027492"
---
# <a name="ole-db-provider-templates-c"></a>Plantillas de proveedores OLE DB (C++)

OLE DB es una parte importante de la estrategia de Microsoft Universal Data Access. El diseño de OLE DB permite el acceso a datos de alto rendimiento desde cualquier origen de datos. Datos tabulares están visibles a través de OLE DB, independientemente de si lo procede de una base de datos. Esta flexibilidad le ofrece una gran cantidad de energía.

Como se explica en [consumidores OLE DB y proveedores](../../data/oledb/ole-db-consumers-and-providers.md), OLE DB usa el concepto de consumidores y proveedores. El consumidor realiza las solicitudes de datos; el proveedor devuelve datos en formato tabular al consumidor. Desde una perspectiva de programación, la implicación más importante de este modelo es que el proveedor debe implementar cualquier llamada que se puede hacer que el consumidor.

## <a name="what-is-a-provider"></a>¿Qué es un proveedor?

Un proveedor OLE DB es un conjunto de objetos COM que atender las llamadas a la interfaz de un objeto de consumidor, transferencia de datos en formato tabular desde un origen duradero (denominado almacén de datos) para el consumidor.

Los proveedores pueden ser simple o complejo. El proveedor puede admitir una cantidad mínima de funcionalidad o un proveedor de calidad de producción completa al implementar más interfaces. Un proveedor puede devolver una tabla, permitir que el cliente determinar el formato de la tabla y realizar operaciones con los datos.

Cada proveedor implementa un conjunto estándar de objetos COM para controlar las solicitudes del cliente, con un significado estándar que cualquier consumidor de OLE DB puede tener acceso a datos desde cualquier proveedor, independientemente del lenguaje (por ejemplo, C++ y básico).

Cada objeto COM contiene varias interfaces, algunos de los cuales son necesarios y algunos de los cuales son opcionales. Implementando las interfaces obligatorias, un proveedor garantiza un nivel mínimo de funcionalidad (denominado conformidad) que cualquier cliente debe ser capaz de usar. Un proveedor puede implementar interfaces opcionales para proporcionar funcionalidad adicional. El [arquitectura de plantillas de proveedor OLE DB](../../data/oledb/ole-db-provider-template-architecture.md) describe estas interfaces en detalle. El cliente siempre debe llamar a `QueryInterface` para determinar si un proveedor admite una interfaz determinada.

## <a name="ole-db-specification-level-support"></a>Compatibilidad con nivel de OLE DB especificación

Las plantillas de proveedor OLE DB admiten la especificación de OLE DB versión 2.7. Mediante las plantillas de proveedor OLE DB, puede implementar un proveedor compatible con el nivel 0. El `Provider` ejemplo, por ejemplo, utiliza las plantillas para implementar un servidor de comando de aplicación que se ejecuta el comando DIR de DOS para consultar el sistema de archivos. El `Provider` ejemplo devuelve la información del directorio en un conjunto de filas, que es el mecanismo estándar de OLE DB para devolver datos tabulares.

El tipo más sencillo de proveedor compatible con las plantillas OLE DB es un proveedor de sólo lectura con ningún comando. También se admiten proveedores con comandos, como son las características de marcadores y lectura/escritura. Puede implementar un proveedor de lectura/escritura al escribir código adicional. Las transacciones y los conjuntos de filas dinámicas no son compatibles con la versión actual, pero puede agregar si desea.

## <a name="when-do-you-need-to-create-an-ole-db-provider"></a>¿Cuando necesite crear un proveedor OLE DB?

No siempre es necesario crear su propio proveedor; Microsoft proporciona varios proveedores estándares ya preparados en el **propiedades de vínculo de datos** cuadro de diálogo de Visual C++. Es la razón principal para crear un proveedor OLE DB aprovechar las ventajas de la estrategia de Universal Data Access. Por lo que algunas de las ventajas de hacerlo son:

- Acceso a datos a través de cualquier lenguaje como C++, Basic y Visual Basic Scripting Edition. Permite que distintos programadores de su organización para tener acceso a los mismos datos de la misma manera, independientemente del lenguaje utilizan.

- Abra los datos a otros orígenes de datos como SQL Server, Excel y Access. Esto puede ser útil si desea transferir datos entre diferentes formatos.

- Tomar parte en operaciones de origen de datos entre (heterogéneos). Esto puede ser una forma eficaz de almacenamiento de datos. Mediante el uso de proveedores OLE DB, puede mantener los datos en su formato nativo y seguir siendo capaces de obtener acceso a él en una operación sencilla.

- Agregar características adicionales a los datos, como el procesamiento de consultas.

- Aumento del rendimiento de acceso a datos mediante el control de la manipulación.

- Aumentar la solidez. Si tiene un formato de datos privados a los que sólo un programador puede tener acceso a, está en riesgo. Con los proveedores OLE DB, puede abrir ese formato propietario a todos los programadores.

## <a name="read-only-and-updatable-providers"></a>Proveedores de sólo lectura y actualizables

Los proveedores pueden variar en gran medida en complejidad y la funcionalidad. Es útil clasificar los proveedores en solo lectura o proveedores actualizables:

- Visual C++ 6.0 admite solamente los proveedores de solo lectura. [Crear un proveedor OLE DB](../../data/oledb/creating-an-ole-db-provider.md) se describe cómo crear un proveedor de sólo lectura.
- Visual C++ admite proveedores actualizables, que pueden actualizar (escribir en) el almacén de datos. Para obtener información acerca de los proveedores actualizables, vea [crear un proveedor actualizable](../../data/oledb/creating-an-updatable-provider.md); el [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV) es un ejemplo de un proveedor actualizable.

Para obtener más información, consulte:

- [La arquitectura de plantilla de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)

- [Crear un proveedor OLE DB](../../data/oledb/creating-an-ole-db-provider.md)

- [Programación de OLE DB](../../data/oledb/ole-db-programming.md)

## <a name="see-also"></a>Vea también

[Acceso a datos en ASP.NET (Visual Studio)](../data-access-in-cpp.md)<br/>
[Documentación del SDK de OLE DB](/previous-versions/windows/desktop/ms722784(v=vs.85))<br/>
[Referencia del programador de OLE DB](/sql/connect/oledb/ole-db/oledb-driver-for-sql-server-programming)<br/>
