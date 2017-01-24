---
title: "CAccessorBase::ReleaseAccessors | Microsoft Docs"
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
  - "CAccessorBase::ReleaseAccessors"
  - "CAccessorBase.ReleaseAccessors"
  - "ReleaseAccessors"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ReleaseAccessors (método)"
ms.assetid: f08bc88e-0552-4a9c-9c65-b4061094649a
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CAccessorBase::ReleaseAccessors
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Libera los descriptores de acceso creados por la clase.  
  
## Sintaxis  
  
```  
  
      HRESULT ReleaseAccessors(  
   IUnknown* pUnk   
);  
```  
  
#### Parámetros  
 *punky*  
 \[in\] Un puntero a una interfaz de **IUnknown** para el objeto COM que se han creado los descriptores de acceso.  
  
## Valor devuelto  
 `HRESULT`estándar.  
  
## Comentarios  
 Nombre de [CAccessorRowset::Close](../../data/oledb/caccessorrowset-close.md).  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [CAccessorBase \(Clase\)](../../data/oledb/caccessorbase-class.md)