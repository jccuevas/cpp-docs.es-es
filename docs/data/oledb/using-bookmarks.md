---
title: Utilizar marcadores
ms.date: 10/24/2018
helpviewer_keywords:
- rowsets, bookmarks
- OLE DB provider templates, bookmarks
- bookmarks, OLE DB
- OLE DB providers, bookmark support
ms.assetid: 7fa1d1a8-5063-4aa9-93ee-815bb9c98fae
ms.openlocfilehash: 5a4a2d65ba7367b5568603b5f08a07c6d85cc4a5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209319"
---
# <a name="using-bookmarks"></a>Utilizar marcadores

Antes de abrir el conjunto de filas, debe indicar al proveedor que desea utilizar marcadores. Para ello, establezca la propiedad `DBPROP_BOOKMARKS` en **true** en el conjunto de propiedades. El proveedor recupera los marcadores como columna cero, por lo que debe usar la macro especial BOOKMARK_ENTRY y la clase `CBookmark` si usa un descriptor de acceso estático. `CBookmark` es una clase de plantilla en la que el argumento es la longitud en bytes del búfer del marcador. La longitud del búfer necesario para un marcador depende del proveedor. Si utiliza el proveedor de OLE DB ODBC, como se muestra en el ejemplo siguiente, el búfer debe ser de 4 bytes.

```cpp
class CProducts
{
public:
   CBookmark<4> bookmark;

   BEGIN_COLUMN_MAP(CProducts)
      BOOKMARK_ENTRY(bookmark)
   END_COLUMN_MAP()
};
```

A continuación, utilizado por el código siguiente:

```cpp
CDBPropSet propset(DBPROPSET_ROWSET);
propset.AddProperty(DBPROP_BOOKMARKS, true);

CTable<CAccessor<CProducts>> product;
CSession session;
product.Open(session, "Products", &propset);
```

Si utiliza `CDynamicAccessor`, el búfer se establece dinámicamente en tiempo de ejecución. En este caso, puede usar una versión especializada de `CBookmark` para la que no especifique una longitud de búfer. Utilice la función `GetBookmark` para recuperar el marcador del registro actual, como se muestra en este ejemplo de código:

```cpp
CTable<CDynamicAccessor> product;
CBookmark<> bookmark;
CDBPropSet propset(DBPROPSET_ROWSET);
CSession session;

propset.AddProperty(DBPROP_BOOKMARKS, true);
product.Open(session, "Products", &propset);
product.MoveNext();
product.GetBookmark(&bookmark);
```

Para obtener información acerca de la compatibilidad de marcadores en proveedores, vea [compatibilidad de](../../data/oledb/provider-support-for-bookmarks.md)proveedores con marcadores.

## <a name="see-also"></a>Consulte también

[Usar descriptores de acceso](../../data/oledb/using-accessors.md)
