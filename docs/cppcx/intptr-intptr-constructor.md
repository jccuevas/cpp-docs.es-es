---
title: "IntPtr::IntPtr (Constructor) | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::IntPtr::IntPtr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IntPtr::IntPtr (Constructor)"
ms.assetid: 828b4c18-790d-4fb4-90fe-47769ff381c0
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# IntPtr::IntPtr (Constructor)
Inicializa una nueva instancia de un objeto IntPtr con el valor especificado.  
  
## Sintaxis  
  
```cpp  
IntPtr( __int64 handle-or-pointer );   IntPtr( void* value );   IntPtr( int 32-bit_value );  
```  
  
#### Parámetros  
 value  
 Un identificador o un puntero de 64 bits, o un puntero a un valor de 64 bits, o un valor de 32 bits que se puede convertir en un valor de 64 bits.  
  
## Requisitos  
 **Cliente mínimo admitido:** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **Servidor mínimo admitido:** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **Espacio de nombres:** Platform  
  
 **Metadatos:** platform.winmd  
  
## Vea también  
 [Platform::IntPtr \(Clase de valor\)](../cppcx/platform-intptr-value-class.md)