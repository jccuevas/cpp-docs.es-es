---
title: "ICommandImpl::Execute | Microsoft Docs"
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
  - "ICommandImpl::Execute"
  - "ICommandImpl.Execute"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Execute (método)"
ms.assetid: 033e0d4e-256b-4eed-9215-70e0bebb768c
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ICommandImpl::Execute
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Ejecuta el comando.  
  
## Sintaxis  
  
```  
  
      HRESULT Execute(  
   IUnknown* pUnkOuter,  
   REFIID riid,  
   DBPARAMS* pParams,  
   DBROWCOUNT* pcRowsAffected,  
   IUnknown** ppRowset   
);  
```  
  
#### Parámetros  
 Vea [ICommand::Execute](https://msdn.microsoft.com/en-us/library/ms718095.aspx) en *la referencia del*programador.  
  
## Comentarios  
 La interfaz de salida solicitada será una interfaz adquirida del objeto de conjunto de filas que esta función crea.  
  
 llamadas [CreateRowset](../../data/oledb/icommandimpl-createrowset.md)de**Ejecución** .  Reemplace la implementación predeterminada para crear a más de un conjunto o para proporcionarlo dispone las condiciones para crear diferentes conjuntos de filas.  
  
## Requisitos  
 **Header:** atldb.h  
  
## Vea también  
 [ICommandImpl \(Clase\)](../../data/oledb/icommandimpl-class.md)   
 [ICommandImpl::CancelExecution](../../data/oledb/icommandimpl-cancelexecution.md)