---
title: "Utilizar marcadores | Microsoft Docs"
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
  - "marcadores, OLE DB"
  - "plantillas del proveedor OLE DB, marcadores"
  - "proveedores OLE DB, compatibilidad con marcadores"
  - "conjuntos de filas, marcadores"
ms.assetid: 7fa1d1a8-5063-4aa9-93ee-815bb9c98fae
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Utilizar marcadores
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Antes de abrir el conjunto de filas debe indicarse al proveedor que se desean utilizar marcadores.  Para ello, establezca la propiedad **DBPROP\_BOOKMARKS** en **true** en el conjunto de propiedades.  El proveedor recupera los marcadores como columna cero, por lo que debe usar la macro especial `BOOKMARK_ENTRY` y la clase `CBookmark` si usa un descriptor de acceso estático.  `CBookmark` es una clase de plantilla donde el argumento tiene la longitud en bytes del búfer del marcador.  La longitud del búfer requerida para un marcador depende del proveedor.  Si utiliza el proveedor OLE DB de ODBC, como se muestra en el siguiente ejemplo, el búfer tendrá que ser de 4 bytes.  
  
```  
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
  
CTable<CAccessor<CProducts> > product;  
product.Open(session, "Products", &propset);  
```  
  
 Si utiliza `CDynamicAccessor`, el búfer se asigna dinámicamente en tiempo de ejecución.  En ese caso, se puede usar una versión especializada de `CBookmark` para la que no se especifica la longitud de búfer.  Utilice la función `GetBookmark` para recuperar el marcador del registro actual, como se muestra en este ejemplo de código:  
  
```  
CTable<CDynamicAccessor> product;  
CBookmark<>              bookmark;  
CDBPropSet propset(DBPROPSET_ROWSET);  
  
propset.AddProperty(DBPROP_BOOKMARKS, true);  
product.Open(session, "Products", &propset);  
product.MoveNext();  
product.GetBookmark(&bookmark);  
```  
  
 Para obtener información acerca de la compatibilidad con marcadores en proveedores, vea [Compatibilidad del proveedor con los marcadores](../../data/oledb/provider-support-for-bookmarks.md).  
  
## Vea también  
 [Utilizar descriptores de acceso](../../data/oledb/using-accessors.md)