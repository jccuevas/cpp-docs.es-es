---
title: "Recuperar un objeto BLOB | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BLOB (objeto binario grande), recuperar"
  - "OLE DB, BLOB (objetos binarios grandes)"
  - "recuperar BLOB"
ms.assetid: 2893eb0a-5c05-4016-8914-1e40ccbaf0b3
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Recuperar un objeto BLOB
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Se puede recuperar un objeto binario grande \(BLOB, *Binary Large Object*\) de varias maneras.  Puede usar **DBTYPE\_BYTES** para recuperarlo como una secuencia de bytes o usar una interfaz como `ISequentialStream`.  Para obtener más información, vea [Objetos BLOB y OLE](https://msdn.microsoft.com/en-us/library/ms711511.aspx) en la *Referencia del programador de OLE DB*.  
  
 En el código siguiente se muestra cómo recuperar un objeto BLOB a través de `ISequentialStream`.  La macro [BLOB\_ENTRY](../../data/oledb/blob-entry.md) permite especificar la interfaz y los marcadores usados para la interfaz.  Después de abrir la tabla, el código llama repetidas veces a **Read** en `ISequentialStream` para leer bytes del objeto BLOB.  El código llama a **Release** para deshacerse del puntero de interfaz antes de llamar a `MoveNext` para obtener el siguiente registro.  
  
```  
class CCategories  
{  
public:  
   ISequentialStream*   pPicture;  
  
BEGIN_COLUMN_MAP(CCategories)  
   BLOB_ENTRY(4, IID_ISequentialStream, STGM_READ, pPicture)  
END_COLUMN_MAP()  
};  
  
CTable<CAccessor<CCategories> > categories;  
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
  
 Para obtener más información acerca de las macros que controlan datos BLOB, vea "Macros del mapa de columnas" en [Macros y funciones globales para las plantillas de consumidor OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md).  
  
## Vea también  
 [Utilizar descriptores de acceso](../../data/oledb/using-accessors.md)   
 [Macros y funciones globales para las plantillas de consumidor OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)