---
title: Comandos y tablas
ms.date: 11/19/2018
helpviewer_keywords:
- OLE DB consumer templates, table support
- CCommand class, OLE DB consumer templates
- commands [C++], OLE DB Consumer Templates
- CTable class
- CAccessorRowset class, command and table classes
- rowsets, accessing
- tables [C++], OLE DB Consumer Templates
- OLE DB consumer templates, command support
ms.assetid: 4bd3787b-6d26-40a9-be0c-083080537c12
ms.openlocfilehash: 0d5f6bd8d5f813497cba399e5c071f43dc1a7c4d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211528"
---
# <a name="commands-and-tables"></a>Comandos y tablas

Los comandos y las tablas permiten tener acceso a los conjuntos de filas; es decir, abrir conjuntos de filas, ejecutar comandos y enlazar columnas. Las clases [CCommand](../../data/oledb/ccommand-class.md) y [CTable](../../data/oledb/ctable-class.md) crean instancias de los objetos de comando y tabla, respectivamente. Estas clases se derivan de [CAccessorRowset](../../data/oledb/caccessorrowset-class.md) , tal y como se muestra en la ilustración siguiente.

![CCommand y CTable](../../data/oledb/media/vccommandstables.gif "CCommand y CTable")<br/>
Clases de comandos y tablas

En la tabla anterior, `TAccessor` puede ser cualquier tipo de descriptor de acceso incluido en los [tipos de descriptores de acceso](../../data/oledb/accessors-and-rowsets.md). `TRowset` puede ser cualquier tipo de conjunto de filas incluido en los [tipos de conjunto de filas](../../data/oledb/accessors-and-rowsets.md). `TMultiple` especifica el tipo de resultado (un conjunto de resultados único o múltiple).

El [Asistente para consumidores OLE DB ATL](../../atl/reference/atl-ole-db-consumer-wizard.md) le permite especificar si desea un comando o un objeto de tabla.

- En el caso de los orígenes de datos sin comandos, puede usar la clase `CTable`. Normalmente, se usa para conjuntos de filas simples que no especifican ningún parámetro y no requieren varios resultados. Esta clase simple abre una tabla en un origen de datos con el nombre de tabla que especifique.

- En el caso de los orígenes de datos que admiten comandos, puede usar la clase `CCommand` en su lugar. Para ejecutar un comando, llame a [Open](../../data/oledb/ccommand-open.md) en esta clase. Como alternativa, puede llamar a `Prepare` para preparar un comando que desee ejecutar más de una vez.

   `CCommand` tiene tres argumentos de plantilla: un tipo de descriptor de acceso, un tipo de conjunto de filas y un tipo de resultado (`CNoMultipleResults`, de forma predeterminada o `CMultipleResults`). Si especifica `CMultipleResults`, la clase `CCommand` admite la interfaz `IMultipleResults` y controla varios conjuntos de filas. El ejemplo [DBVIEWER](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Consumer) muestra cómo controlar los diversos resultados.

## <a name="see-also"></a>Consulte también

[Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)
