---
title: "IErrorRecordsImpl::GetErrorHelpFile | Microsoft Docs"
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
  - "IErrorRecordsImpl::GetErrorHelpFile"
  - "GetErrorHelpFile"
  - "IErrorRecordsImpl.GetErrorHelpFile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetErrorHelpFile (método)"
ms.assetid: ad198f76-5bdf-4b8d-9f1a-3d38f72f31ad
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IErrorRecordsImpl::GetErrorHelpFile
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Obtiene el nombre de ruta de acceso del archivo de ayuda de un registro de errores.  
  
## Sintaxis  
  
```  
  
      LPOLESTR GetErrorHelpFile(  
   ERRORINFO& rCurError   
);  
```  
  
#### Parámetros  
 `rCurError`  
 Un registro de `ERRORINFO` en una interfaz de **IErrorInfo** .  
  
## Valor devuelto  
 Puntero a una cadena que contiene el nombre de ruta de acceso del archivo de ayuda del error.  
  
## Requisitos  
 **Header:** atldb.h  
  
## Vea también  
 [IErrorRecordsImpl \(Clase\)](../../data/oledb/ierrorrecordsimpl-class.md)