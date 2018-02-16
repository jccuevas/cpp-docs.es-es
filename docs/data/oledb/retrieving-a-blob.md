---
title: Recuperar un objeto BLOB | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- retrieving BLOBs
- BLOB (binary large object), retrieving
- OLE DB, BLOBs (binary large objects)
ms.assetid: 2893eb0a-5c05-4016-8914-1e40ccbaf0b3
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 9a0519631d843f875788b394b72d56795c562ae0
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="retrieving-a-blob"></a>Recuperar un objeto BLOB
Puede recuperar un objeto grande binario (BLOB) de varias maneras. Puede usar **DBTYPE_BYTES** para recuperar el BLOB como una secuencia de bytes o usar una interfaz como `ISequentialStream`. Para obtener más información, consulte [objetos BLOB y OLE](https://msdn.microsoft.com/en-us/library/ms711511.aspx) en el *referencia del programador de OLE DB*.  
  
 El código siguiente muestra cómo recuperar un BLOB con `ISequentialStream`. La macro [BLOB_ENTRY](../../data/oledb/blob-entry.md) le permite especificar la interfaz y los indicadores usados para la interfaz. Después de abrir la tabla, el código llama **lectura** repetidamente en `ISequentialStream` para leer los bytes del BLOB. El código llama **versión** para desechar el puntero de interfaz antes de llamar a `MoveNext` para obtener el siguiente registro.  
  
```  
class CCategories  
{  
public:  
   ISequentialStream*   pPicture;  
  
BEGIN_COLUMN_MAP(CCategories)  
   BLOB_ENTRY(4, IID_ISequentialStream, STGM_READ, pPicture)  
END_COLUMN_MAP()  
};  
  
CTable<CAccessor<CCategories>> categories;  
ULONG          cb;  
BYTE            myBuffer[65536];  
  
categories.Open(session, "Categories");  

while (categories.MoveNext() == S_OK)  
{  
   do  
   {  
      categories.pPicture->Read(myBuffer, 65536, &cb);  
      // Do something with the buffer  
   } while (cb > 0);  
   categories.pPicture->Release();  
}  
```  
  
 Para obtener más información acerca de las macros que controlan datos BLOB, vea "Macros de mapa de columnas" en [Macros y funciones globales para las plantillas de consumidor OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md).  
  
## <a name="see-also"></a>Vea también  
 [Utilizar descriptores de acceso](../../data/oledb/using-accessors.md)   
 [Macros y funciones globales para las plantillas de consumidor OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)