---
title: Comandos y tablas | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 23d2739807a065b93b10a209a9ea68070b36970b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="commands-and-tables"></a>Comandos y tablas
Comandos y tablas permiten tener acceso a conjuntos de filas; es decir, abrir conjuntos de filas, ejecutar comandos y enlazar las columnas. El [CCommand](../../data/oledb/ccommand-class.md) y [CTable](../../data/oledb/ctable-class.md) clases crean instancias de los objetos de comando y tabla, respectivamente. Estas clases derivan de [CAccessorRowset](../../data/oledb/caccessorrowset-class.md) tal como se muestra en la ilustración siguiente.  
  
 ![CCommand y CTable](../../data/oledb/media/vccommandstables.gif "vccommandstables")  
Comandos y las clases de la tabla  
  
 En la tabla anterior, `TAccessor` puede ser cualquier tipo de descriptor de acceso que se muestran en [tipos de descriptor de acceso](../../data/oledb/accessors-and-rowsets.md). *TRowset* puede ser cualquier tipo de conjunto de filas que se muestran en [tipos de conjunto de filas](../../data/oledb/accessors-and-rowsets.md). *TMultiple* especifica el tipo de resultado (uno o varios conjuntos de resultados).  
  
 El [el Asistente para consumidores OLE DB ATL](../../atl/reference/atl-ole-db-consumer-wizard.md) le permite especificar si desea que un objeto de comando o tabla.  
  
-   Para los orígenes de datos sin comandos, puede usar el `CTable` clase. Normalmente se utiliza para conjuntos de filas simples que no especifican parámetros y no requieren múltiples resultados. Esta clase abre una tabla en un origen de datos mediante un nombre de tabla que especifique.  
  
-   Orígenes de datos que admiten los comandos, puede usar el `CCommand` clase en su lugar. Para ejecutar un comando, llame al [abiertos](../../data/oledb/ccommand-open.md) en esta clase. Como alternativa, puede llamar a `Prepare` para preparar un comando que se desea ejecutar más de una vez.  
  
     **CCommand** tiene tres argumentos de plantilla: un tipo de descriptor de acceso, un tipo de conjunto de filas y un tipo de resultado (`CNoMultipleResults`, de forma predeterminada, o `CMultipleResults`). Si especifica `CMultipleResults`, `CCommand` clase admite la **IMultipleResults** interfaz y administra varios conjuntos de filas. El [DBVIEWER](http://msdn.microsoft.com/en-us/07620f99-c347-4d09-9ebc-2459e8049832) ejemplo muestra cómo controlar múltiples resultados.  
  
## <a name="see-also"></a>Vea también  
 [Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)