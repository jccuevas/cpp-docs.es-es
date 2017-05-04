---
title: "WeakReference::WeakReference (Constructor de C++/CX) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vccorlib/WeakReference::WeakReference"
ms.assetid: b2f712e0-3ee0-4a05-b861-973b4a212609
caps.latest.revision: 2
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# WeakReference::WeakReference (Constructor de C++/CX)
Proporciona distintas formas de crear un objeto WeakReference.  
  
## Sintaxis  
  
```scr  
WeakReference();  
WeakReference(decltype(__nullptr));  
WeakReference(const WeakReference& __otherArg);  
WeakReference(WeakReference&& __otherArg);  
explicit WeakReference(const volatile ::Platform::Object^ const __otherArg);  
```  
  
## Ejemplo  
  
```scr  
  
MyClass^ mc = ref new MyClass(); WeakReference wr(mc); MyClass^ copy2 = wr.Resolve<MyClass>();  
  
```  
  
## Comentarios  
  
## Requisitos  
  
## Vea también  
 [Espacio de nombres de plataforma](../cppcx/platform-namespace-c-cx.md)   
 [Platform::WeakReference \(Clase\)](../cppcx/platform-weakreference-class.md)