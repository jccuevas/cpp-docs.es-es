---
title: "WeakReference::operator= | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vccorlib/WeakReference::operator="
ms.assetid: 20b034d1-8f4f-46ae-81f0-73b76599f86b
caps.latest.revision: 2
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# WeakReference::operator=
Asigna un valor a WeakReference.  
  
## Sintaxis  
  
```cpp  
WeakReference& operator=(decltype(__nullptr));  
  
WeakReference& operator=(const WeakReference& __otherArg);  
  
WeakReference& operator=(WeakReference&& __otherArg);  
  
WeakReference& operator=(const volatile ::Platform::Object^ const __otherArg);  
  
```  
  
## Comentarios  
 La última sobrecarga de la lista permite asignar una clase ref a una variable WeakReference. En este caso, la clase ref se convierte en [Platform::Object](../cppcx/platform-object-class.md)^. Puedes restablecer el tipo original más adelante especificándolo como argumento del parámetro de tipo en la función miembro [WeakReference::Resolve\<T\>](../cppcx/weakreference-resolve-method-platform-namespace.md).  
  
## Requisitos  
 Windows 8.0 o posterior  
  
## Vea también  
 [Platform::WeakReference \(Clase\)](../cppcx/platform-weakreference-class.md)