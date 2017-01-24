---
title: "CAccessor (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL.CAccessor<T>"
  - "ATL::CAccessor"
  - "CAccessor"
  - "ATL::CAccessor<T>"
  - "ATL.CAccessor"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAccessor (clase)"
ms.assetid: b2ba959f-a686-46f3-8837-176248aef748
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CAccessor (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Representa uno de los descriptores de acceso.  
  
## Sintaxis  
  
```  
  
      template < class   
      T  
       >  
class CAccessor : public CAccessorBase, public T  
```  
  
#### Parámetros  
 `T`  
 La clase de registro de usuario.  
  
## Comentarios  
 Se utiliza cuando un registro se enlaza estáticamente a un origen de datos.  El registro contiene el búfer.  Esta clase admite múltiples descriptores de acceso en un conjunto de filas.  
  
 Utilice este tipo de descriptor cuando sepa la estructura y el tipo de la base de datos.  
  
 Si el descriptor de acceso contiene campos que señalan a memoria \(como `BSTR` o interfaz\) que será liberada, llame a la función [CAccessorRowset::FreeRecordMemory](../../data/oledb/caccessorrowset-freerecordmemory.md) miembro para que se lea el registro siguiente.  
  
## Requisitos  
 **Header:** atldbcli.h  
  
## Vea también  
 [Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)