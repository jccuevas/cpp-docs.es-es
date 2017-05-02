---
title: "Object::ToString (M&#233;todo) (C++/CX) | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::Object::ToString"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform, Object::ToString"
ms.assetid: 229dbf1c-cb43-4ed2-a1c5-a1f36b22a7ea
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Object::ToString (M&#233;todo) (C++/CX)
Devuelve una cadena que representa el objeto actual.  
  
## Sintaxis  
  
```cpp  
public:  
virtual String^ ToString()  
```  
  
## Valor devuelto  
 Una cadena que representa el objeto actual. Puedes invalidar este método para proporcionar un mensaje de cadena personalizado en la clase o el struct ref:  
  
```cpp  
public ref class Tree sealed { public: Tree(){} virtual Platform::String^ ToString()override { return "I’m a Tree"; }; };  
```  
  
## Requisitos  
 **Cliente mínimo admitido:** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **Servidor mínimo admitido:** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **Espacio de nombres:** Platform  
  
 **Encabezado:** vccorlib.h  
  
## Vea también  
 [Platform::Object \(Clase\)](../cppcx/platform-object-class.md)