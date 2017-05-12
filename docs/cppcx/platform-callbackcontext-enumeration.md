---
title: "Platform::CallbackContext (Enumeraci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::CallbackContext"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::CallbackContext (Enumeración)"
ms.assetid: 60e0c7cb-5d8f-482a-bdca-ca9335ae4899
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 3
---
# Platform::CallbackContext (Enumeraci&#243;n)
Especifica el contexto del subproceso en el que se ejecuta una función de devolución de llamada \(controlador de eventos\).  
  
## Sintaxis  
  
```cpp  
enum class CallbackContext {};  
```  
  
## Miembros  
  
|Código de tipo|Descripción|  
|--------------------|-----------------|  
|Cualquiera|La función de devolución de llamada se puede ejecutar en cualquier contexto de subproceso.|  
|Igual|La función de devolución de llamada solo se puede ejecutar en el contexto de subproceso que inició la operación asincrónica.|  
  
## Requisitos  
 **Cliente mínimo admitido:** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **Servidor mínimo admitido:** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **Espacio de nombres:** Platform  
  
 **Metadatos:** platform.winmd