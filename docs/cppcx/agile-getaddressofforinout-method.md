---
title: "Agile::GetAddressOfForInOut (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "agile/Platform::Agile::GetAddressOfForInOut"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::Agile::GetAddressOfForInOut"
ms.assetid: 8bb27b4c-c325-49ee-91db-9adf87c530c4
caps.latest.revision: 2
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Agile::GetAddressOfForInOut (M&#233;todo)
Devuelve la dirección de un identificador al objeto representado por el objeto Agile actual.  
  
## Sintaxis  
  
```cpp  
  
       T^* GetAddressOfForInOut()   
throw();  
  
```  
  
#### Parámetros  
 `T`  
 Un tipo especificado por el parámetro typename de la plantilla.  
  
## Valor devuelto  
 La dirección de un identificador al objeto representado por el objeto Agile actual.  
  
## Comentarios  
 Esta operación adquiere el contexto de subprocesos actual y devuelve después la dirección de un identificador al objeto subyacente.  
  
## Requisitos  
 **Cliente mínimo admitido:** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **Servidor mínimo admitido:** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **Espacio de nombres:** Platform  
  
 **Encabezado:** vccorlib.h  
  
## Vea también  
 [Platform::Agile \(Clase\)](../cppcx/platform-agile-class.md)