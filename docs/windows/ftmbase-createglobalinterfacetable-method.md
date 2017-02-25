---
title: "FtmBase::CreateGlobalInterfaceTable (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ftm/Microsoft::WRL::FtmBase::CreateGlobalInterfaceTable"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CreateGlobalInterfaceTable (método)"
ms.assetid: bb82a0c5-22b9-4844-9204-7922033d8b07
caps.latest.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# FtmBase::CreateGlobalInterfaceTable (M&#233;todo)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Crea una tabla global \(GIT\) de interfaz.  
  
## Sintaxis  
  
```  
static HRESULT CreateGlobalInterfaceTable(  
   __out IGlobalInterfaceTable **git  
);  
```  
  
#### Parámetros  
 `git`  
 Cuando esta operación finaliza, un puntero a una tabla global de la interfaz.  
  
## Valor devuelto  
 S\_OK si correctamente; si no, un HRESULT que indica el error.  
  
## Comentarios  
 Para obtener más información, vea el tema “IGlobalInterfaceTable” en el subtema “las interfaces COM” del tema de “referencia COM” en MSDN Library.  
  
## Requisitos  
 **Encabezado:** ftm.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## Vea también  
 [FtmBase \(Clase\)](../windows/ftmbase-class.md)