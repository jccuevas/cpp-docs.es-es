---
title: "AsyncBase::FireCompletion (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "async/Microsoft::WRL::AsyncBase::FireCompletion"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "FireCompletion (método)"
ms.assetid: b5e29d6d-52e7-4148-a7f3-a313b1359819
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# AsyncBase::FireCompletion (M&#233;todo)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Invoca el controlador de eventos de finalización, o restaure el delegado interno de progreso.  
  
## Sintaxis  
  
```  
void FireCompletion(  
   void  
) override;  
  
virtual void FireCompletion();  
```  
  
## Comentarios  
 La primera versión de FireCompletion\(\) restaura la variable interna de delegado de progreso.  La segunda versión invoca el controlador de eventos de finalización si se completa la operación asincrónica.  
  
## Requisitos  
 **Encabezado:** async.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## Vea también  
 [AsyncBase \(Clase\)](../windows/asyncbase-class.md)