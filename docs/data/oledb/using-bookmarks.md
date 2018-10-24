---
title: Uso de marcadores | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- rowsets, bookmarks
- OLE DB provider templates, bookmarks
- bookmarks, OLE DB
- OLE DB providers, bookmark support
ms.assetid: 7fa1d1a8-5063-4aa9-93ee-815bb9c98fae
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: d8d23ba81ba83202da1dd6814374a0c4aa1cb98b
ms.sourcegitcommit: c045c3a7e9f2c7e3e0de5b7f9513e41d8b6d19b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2018
ms.locfileid: "49990083"
---
# <a name="using-bookmarks"></a>Utilizar marcadores

Antes de abrir el conjunto de filas, se debe indicar al proveedor que desea utilizar marcadores. Para ello, establezca el `DBPROP_BOOKMARKS` propiedad **true** en conjunto de sus propiedades. El proveedor recupera los marcadores como columna cero, lo que debe usar la macro especial BOOKMARK_ENTRY y `CBookmark` clase si está utilizando un descriptor de acceso estático. `CBookmark` es una clase de plantilla donde el argumento es la longitud en bytes del búfer del marcador. La longitud del búfer necesario para un marcador depende del proveedor. Si usa el proveedor OLE DB de ODBC, como se muestra en el ejemplo siguiente, el búfer debe ser de 4 bytes.  
  
```cpp  
class CProducts  
{  
public:  
   CBookmark<4>   bookmark;  
  
   BEGIN_COLUMN_MAP(CProducts)  
      BOOKMARK_ENTRY(bookmark)  
   END_COLUMN_MAP()  
};  
  
CDBPropSet propset(DBPROPSET_ROWSET);  

propset.AddProperty(DBPROP_BOOKMARKS, true);  
  
CTable<CAccessor<CProducts>> product;  
product.Open(session, "Products", &propset);  
```  
  
Si usa `CDynamicAccessor`, el búfer se asigna dinámicamente en tiempo de ejecución. En este caso, puede usar una versión especializada de `CBookmark` para el que no se especifica una longitud de búfer. Use la función `GetBookmark` para recuperar el marcador del registro actual, como se muestra en este ejemplo de código:  
  
```cpp  
CTable<CDynamicAccessor> product;  
CBookmark<>              bookmark;  
CDBPropSet propset(DBPROPSET_ROWSET);  
  
propset.AddProperty(DBPROP_BOOKMARKS, true);  

product.Open(session, "Products", &propset);  

product.MoveNext();  

product.GetBookmark(&bookmark);  
```  
  
Para obtener información sobre la compatibilidad con marcadores en proveedores, vea [proveedor de compatibilidad con los marcadores](../../data/oledb/provider-support-for-bookmarks.md).  
  
## <a name="see-also"></a>Vea también  

[Usar descriptores de acceso](../../data/oledb/using-accessors.md)