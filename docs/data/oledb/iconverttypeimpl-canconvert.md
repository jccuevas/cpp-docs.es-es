---
title: "IConvertTypeImpl::CanConvert | Microsoft Docs"
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
  - "IConvertTypeImpl.CanConvert"
  - "CanConvert"
  - "IConvertTypeImpl::CanConvert"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CanConvert (método)"
ms.assetid: bdad6e95-bc0b-4427-9b5e-eea51f09f392
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IConvertTypeImpl::CanConvert
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Proporciona información sobre la disponibilidad de conversiones de tipos en un comando o en un conjunto de filas.  
  
## Sintaxis  
  
```  
  
      STDMETHOD(CanConvert)(   
   DBTYPE wFromType,   
   DBTYPE wToType,   
   DBCONVERTFLAGS dwConvertFlags    
);  
```  
  
#### Parámetros  
 Vea [IConvertType::CanConvert](https://msdn.microsoft.com/en-us/library/ms711224.aspx) en *la referencia del*programador.  
  
## Comentarios  
 Utiliza la conversión de datos OLE DB en `MSADC.DLL`.  
  
## Requisitos  
 **Header:** atldb.h  
  
## Vea también  
 [IConvertTypeImpl \(Clase\)](../../data/oledb/iconverttypeimpl-class.md)