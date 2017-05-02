---
title: "Type::GetTypeCode (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::Type::GetTypeCode"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Type::GetTypeCode (Método)"
ms.assetid: 20c30432-91a3-400e-b9d6-eba265daaefc
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Type::GetTypeCode (M&#233;todo)
Recupera una categoría de tipo numérico de tipos integrados.  
  
## Sintaxis  
  
```cpp  
Platform::TypeCode GetTypeCode();  
```  
  
## Valor devuelto  
 Uno de los valores enumerados de Platform::TypeCode.  
  
## Comentarios  
 El equivalente del método miembro GetTypeCode\(\) es la propiedad `typeid`.  
  
## Requisitos  
 **Cliente mínimo admitido:** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **Servidor mínimo admitido:** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **Espacio de nombres:** Platform  
  
 **Metadatos:** platform.winmd  
  
## Vea también  
 [Platform::ValueType \(Clase\)](../cppcx/platform-valuetype-class.md)