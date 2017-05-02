---
title: "Platform::IntPtr (Clase de valor) | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::IntPtr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::IntPtr (struct)"
ms.assetid: 6c0326e8-edfd-4e53-a963-240b845dcde8
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 4
---
# Platform::IntPtr (Clase de valor)
Representa un puntero o un identificador con signo cuyo tamaño es específico de la plataforma \(32 bits o 64 bits\).  
  
## Sintaxis  
  
```cpp  
public value struct IntPtr  
```  
  
## Miembros  
 IntPtr tiene los siguientes miembros:  
  
|Miembro|Descripción|  
|-------------|-----------------|  
|[IntPtr::IntPtr \(Constructor\)](../cppcx/intptr-intptr-constructor.md)|Inicializa una nueva instancia de IntPtr.|  
|[IntPtr::op\_explicit \(Operador\)](../cppcx/intptr-op-explicit-operator.md)|Convierte el parámetro especificado un IntPtr o un puntero a un valor de IntPtr.|  
|[IntPtr::ToInt32 \(Método\)](../cppcx/intptr-toint32-method.md)|Convierte el IntPtr actual en un entero de 32 bits.|  
  
## Requisitos  
 **Cliente mínimo admitido:** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **Servidor mínimo admitido:** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **Espacio de nombres:** Platform  
  
 **Metadatos:** platform.winmd  
  
## Vea también  
 [Espacio de nombres de plataforma](../cppcx/platform-namespace-c-cx.md)