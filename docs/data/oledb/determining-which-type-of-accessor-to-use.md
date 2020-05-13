---
title: Determinar qué tipo de descriptor de acceso se debe utilizar
ms.date: 05/09/2019
helpviewer_keywords:
- rowsets [C++], data types
- accessors [C++], types
ms.assetid: 22483dd2-f4e0-4dcb-8e4d-cd43a9c1a3db
ms.openlocfilehash: 31efa36bcd61caa154cd3e4c147ad5ed8728b04c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210995"
---
# <a name="determining-which-type-of-accessor-to-use"></a>Determinar qué tipo de descriptor de acceso se debe utilizar

Puede determinar los tipos de datos de un conjunto de filas en tiempo de compilación o de ejecución.

Si necesita determinar los tipos de datos en tiempo de compilación, utilice un descriptor de acceso estático (como `CAccessor`).

Si necesita determinar los tipos de datos en tiempo de ejecución, utilice un dinámico (`CDynamicAccessor` o sus elementos secundarios) o un descriptor de acceso manual (`CManualAccessor`). En estos casos, puede llamar a `GetColumnInfo` en el conjunto de filas para devolver la información de enlace de columna desde la que se pueden determinar los tipos.

En la tabla siguiente se enumeran los tipos de descriptores de acceso proporcionadas en las plantillas de consumidor. Cada descriptor de acceso tiene ventajas y desventajas. Dependiendo de su situación, un tipo de descriptor de acceso debe adaptarse a sus necesidades.

|Clase de descriptor de acceso|Enlace|Parámetro|Comentario|
|--------------------|-------------|---------------|-------------|
|`CAccessor`|Cree un registro de usuario con macros COLUMN_ENTRY. Las macros de enlazan a un miembro de datos de ese registro al descriptor de acceso. Cuando se crea el conjunto de filas, las columnas no se pueden enlazar.|Sí, mediante el uso de una entrada de macro PARAM_MAP. Una vez enlazados, los parámetros no se pueden enlazar.|Descriptor de acceso más rápido debido a una cantidad pequeña de código.|
|`CDynamicAccessor`|Automático.|No.|Resulta útil si desconoce el tipo de datos en un conjunto de filas.|
|`CDynamicParameterAccessor`|Automático, pero se puede [invalidar](../../data/oledb/overriding-a-dynamic-accessor.md).|Sí, si el proveedor admite `ICommandWithParameters`. Los parámetros se enlazan automáticamente.|Más lento que `CDynamicAccessor`, pero útil para llamar a procedimientos almacenados genéricos.|
|`CDynamicStringAccessor[A,W]`|Automático.|No.|Recupera los datos a los que se accede desde el almacén de datos como datos de cadena.|
|`CManualAccessor`|Manual mediante `AddBindEntry`.|Manualmente mediante `AddParameterEntry`.|Rápido; los parámetros y las columnas se enlazan solo una vez. Determina el tipo de datos que se va a usar. (Vea el ejemplo [DBVIEWER](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Consumer) para obtener un ejemplo). Requiere más código que `CDynamicAccessor` o `CAccessor`. Es más parecido a llamar directamente a OLE DB.|
|`CXMLAccessor`|Automático.|No.|Recupera los datos a los que se accede desde el almacén de datos como datos de cadena y se les aplica formato de etiquetas XML.|

## <a name="see-also"></a>Consulte también

[Usar descriptores de acceso](../../data/oledb/using-accessors.md)
