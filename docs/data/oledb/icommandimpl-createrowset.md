---
title: "ICommandImpl::CreateRowset | Microsoft Docs"
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
  - "ICommandImpl::CreateRowset"
  - "ICommandImpl.CreateRowset"
  - "CreateRowset"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CreateRowset (método)"
ms.assetid: a0890009-205e-4970-879f-01ed9d6a93f1
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ICommandImpl::CreateRowset
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Llamado por [Ejecución](../../data/oledb/icommandimpl-execute.md) para crear un único conjunto de filas.  
  
## Sintaxis  
  
```  
  
      template <class   
      RowsetClass  
      >  
HRESULT CreateRowset(  
   IUnknown* pUnkOuter,  
   REFIID riid,  
   DBPARAMS* pParams,  
   DBROWCOUNT* pcRowsAffected,  
   IUnknown** ppRowset,  
   RowsetClass*& pRowsetObj   
);  
```  
  
#### Parámetros  
 `RowsetClass`  
 Un miembro de la clase de plantilla que representa la clase de conjunto de filas del usuario.  Generado normalmente por el asistente.  
  
 `pUnkOuter`  
 \[in\] Un puntero a la interfaz de **IUnknown** que controla si se está creando el conjunto de filas como parte de un agregado; de lo contrario, es null.  
  
 `riid`  
 \[in\] Corresponde a `riid` en `ICommand::Execute`.  
  
 `pParams`  
 \[in\/out\] Corresponde a `pParams` en `ICommand::Execute`.  
  
 `pcRowsAffected`  
 Corresponde a `pcRowsAffected` en `ICommand::Execute`.  
  
 `ppRowset`  
 \[in\/out\] Corresponde a `ppRowset` en `ICommand::Execute`.  
  
 `pRowsetObj`  
 \[out\] Un puntero a un objeto de conjunto de filas.  Este parámetro no se utiliza normalmente, pero se puede utilizar si debe realizar más trabajo en el conjunto de filas antes de pasarla a un objeto COM.  La duración de `pRowsetObj` está enlazado por `ppRowset`.  
  
## Valor devuelto  
 Un valor estándar de `HRESULT` .  Vea `ICommand::Execute` para una lista de valores típicos.  
  
## Comentarios  
 Para crear a más de un conjunto de filas, o proporcionarlo dispone las condiciones para crear diferentes conjuntos de filas, varias llamadas de lugar a `CreateRowset` dentro de **Ejecución**.  
  
 Vea [ICommand::Execute](https://msdn.microsoft.com/en-us/library/ms718095.aspx) en *la referencia del programador.*  
  
## Requisitos  
 **Header:** atldb.h  
  
## Vea también  
 [ICommandImpl \(Clase\)](../../data/oledb/icommandimpl-class.md)