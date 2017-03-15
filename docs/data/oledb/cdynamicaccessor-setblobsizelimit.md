---
title: "CDynamicAccessor::SetBlobSizeLimit | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CDynamicAccessor::SetBlobSizeLimit"
  - "SetBlobSizeLimit"
  - "CDynamicAccessor.SetBlobSizeLimit"
  - "ATL.CDynamicAccessor.SetBlobSizeLimit"
  - "ATL::CDynamicAccessor::SetBlobSizeLimit"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SetBlobSizeLimit (método)"
ms.assetid: fb8cb85d-f841-408e-a344-37895b10993f
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# CDynamicAccessor::SetBlobSizeLimit
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Establece el tamaño máximo del BLOB en bytes.  
  
## Sintaxis  
  
```  
  
      void SetBlobSizeLimit(  
   DBLENGTH nBlobSize   
);  
```  
  
#### Parámetros  
 `nBlobSize`  
 Especifica el tamaño del BLOB.  
  
## Comentarios  
 Establece el tamaño máximo del BLOB en bytes; los datos de columna mayores que este valor se tratan como BLOB.  Algunos proveedores proporcionan los tamaños muy grandes para columnas \(como 2 GB\).  En lugar de intentar asignar memoria para una columna este tamaño, se intentaría normalmente para enlazar estas columnas como objetos binarios.  De esta manera no tiene que asignar toda la memoria, pero sí podrá leer todos los datos sin miedo de truncamiento.  Sin embargo, hay algunos casos en los que puede ser conveniente forzar `CDynamicAccessor` para enlazar columnas grandes en sus tipos de datos nativos.  Para ello, llame `SetBlobSizeLimit` antes de llamar a **Abierta**.  
  
 El método [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md) de constructor establece el tamaño máximo del BLOB en un valor predeterminado de 8.000 bytes.  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [CDynamicAccessor \(Clase\)](../../data/oledb/cdynamicaccessor-class.md)