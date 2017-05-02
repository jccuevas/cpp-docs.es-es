---
title: "Agile::Release (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "agile/Platform::Agile::Release"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::Agile::Release"
ms.assetid: aa825134-943f-425d-857e-449ec104765e
caps.latest.revision: 2
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Agile::Release (M&#233;todo)
Descarta el objeto y el contexto subyacentes del objeto Agile actual.  
  
## Sintaxis  
  
```cpp  
  
void Release() throw();  
  
```  
  
## Comentarios  
 Si existen, el objeto y el contexto subyacentes del objeto Agile actual se descartan y, a continuación, el valor del objeto Agile se establece en null.  
  
## Requisitos  
 **Cliente mínimo admitido:** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **Servidor mínimo admitido:** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **Espacio de nombres:** Platform  
  
 **Encabezado:** vccorlib.h  
  
## Vea también  
 [Platform::Agile \(Clase\)](../cppcx/platform-agile-class.md)