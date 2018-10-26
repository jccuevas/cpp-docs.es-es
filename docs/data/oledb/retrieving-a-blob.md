---
title: Recuperar un objeto BLOB | Microsoft Docs
ms.custom: ''
ms.date: 10/24/2018
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- retrieving BLOBs
- BLOB (binary large object), retrieving
- OLE DB, BLOBs (binary large objects)
ms.assetid: 2893eb0a-5c05-4016-8914-1e40ccbaf0b3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 1608bf5db491a090f70da5242173fc96419a6179
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50070171"
---
# <a name="retrieving-a-blob"></a>Recuperar un objeto BLOB

Puede recuperar un objeto grande binario (BLOB) de varias maneras. Puede usar `DBTYPE_BYTES` para recuperar el BLOB como una secuencia de bytes o usar una interfaz como `ISequentialStream`. Para obtener más información, consulte [BLOB y objetos OLE](/previous-versions/windows/desktop/ms711511) en el **referencia del programador de OLE DB**.

El código siguiente muestra cómo recuperar un BLOB mediante `ISequentialStream`. La macro [BLOB_ENTRY](../../data/oledb/blob-entry.md) le permite especificar la interfaz y los marcadores utilizados para la interfaz. Después de abrir la tabla, el código llama a `Read` repetidamente en `ISequentialStream` para leer los bytes del BLOB. El código llama a `Release` para desechar el puntero de interfaz antes de llamar a `MoveNext` para ir al siguiente registro.

```cpp
class CCategories
{
public:
   ISequentialStream* pPicture;

BEGIN_COLUMN_MAP(CCategories)
   BLOB_ENTRY(4, IID_ISequentialStream, STGM_READ, pPicture)
END_COLUMN_MAP()
};
```

A continuación, usa el código siguiente:

```cpp
CTable<CAccessor<CCategories>> categories;
ULONG cb;
BYTE myBuffer[65536];

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

Para obtener más información acerca de las macros que controlan datos BLOB, consulte **Macros de mapa de columna** en [Macros y funciones globales para las plantillas de consumidor OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md).

## <a name="see-also"></a>Vea también

[Usar descriptores de acceso](../../data/oledb/using-accessors.md)<br/>
[Macros y funciones globales para las plantillas de consumidor OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)<br/>
