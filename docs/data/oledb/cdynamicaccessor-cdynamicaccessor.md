---
title: "CDynamicAccessor::CDynamicAccessor | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CDynamicAccessor::CDynamicAccessor"
  - "ATL::CDynamicAccessor::CDynamicAccessor"
  - "ATL.CDynamicAccessor.CDynamicAccessor"
  - "CDynamicAccessor.CDynamicAccessor"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDynamicAccessor (clase), constructor"
ms.assetid: bf40fe81-2c85-473e-9075-51ad9b060b39
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# CDynamicAccessor::CDynamicAccessor
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Crea instancias e inicializa el objeto de `CDynamicAccessor` .  
  
## Sintaxis  
  
```  
  
      CDynamicAccessor(   
   DBBLOBHANDLINGENUM eBlobHandling = DBBLOBHANDLING_DEFAULT,   
   DBLENGTH nBlobSize = 8000   
);  
```  
  
#### Parámetros  
 `eBlobHandling`  
 Especifica cómo los datos de \(BLOB\) de objeto binario grande debe ser administrado.  El valor predeterminado es **DBBLOBHANDLING\_DEFAULT**.  Vea [SetBlobHandling](../../data/oledb/cdynamicaccessor-setblobhandling.md) para obtener una descripción de los valores de **DBBLOBHANDLINGENUM** .  
  
 `nBlobSize`  
 El tamaño máximo del BLOB en bytes; los datos de columna sobre este valor se tratan como BLOB.  El valor predeterminado es 8,000.  Vea [SetBlobSizeLimit](../../data/oledb/cdynamicaccessor-setblobsizelimit.md) para obtener detalles.  
  
## Comentarios  
 Si utiliza el constructor para inicializar el objeto de `CDynamicAccessor` , puede especificar cómo enlazar objetos binarios.  Objetos binarios pueden contener datos binarios como gráficos, audio, o código compilado.  El comportamiento predeterminado consiste en tratar columnas de más de 8.000 bytes como objetos binarios e intentar enlazarlos a un objeto de `ISequentialStream` .  Sin embargo, puede especificar un valor diferente para ser el tamaño del BLOB.  
  
 También puede especificar cómo `CDynamicAccessor` controla los datos de columna que se califican como datos de BLOB: pueden controlar datos BLOB de la manera predeterminada; puede omitir \(no haga enlace\) datos BLOB; o puede enlazar datos BLOB en memoria proveedor\- asignada.  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [CDynamicAccessor \(Clase\)](../../data/oledb/cdynamicaccessor-class.md)