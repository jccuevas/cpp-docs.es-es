---
title: "CCommand::SetParameterInfo | Microsoft Docs"
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
  - "SetParameterInfo"
  - "CCommand.SetParameterInfo"
  - "CCommand::SetParameterInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SetParameterInfo (método)"
ms.assetid: a70e92f4-1e73-41d7-a5b7-c6ebb45a6477
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CCommand::SetParameterInfo
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Especifica el tipo nativo de cada parámetro de comando.  
  
## Sintaxis  
  
```  
  
      HRESULT CCommandBase::SetParameterInfo(  
   DB_UPARAMS ulParams,  
   const DBORDINAL* pOrdinals,  
   const DBPARAMBINDINFO* pParamInfo   
) throw( );  
```  
  
#### Parámetros  
 Vea [ICommandWithParameters::SetParameterInfo](https://msdn.microsoft.com/en-us/library/ms725393.aspx) en *la referencia del*programador.  
  
## Valor devuelto  
 `HRESULT`estándar.  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [CCommand \(Clase\)](../../data/oledb/ccommand-class.md)