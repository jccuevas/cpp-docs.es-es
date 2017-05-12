---
title: "Platform::Delegate (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::Delegate"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::Delegate (Clase)"
ms.assetid: 82b21271-768f-4193-9ca2-be68ddfd546e
caps.latest.revision: 5
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 5
---
# Platform::Delegate (Clase)
Representa un objeto de función.  
  
## Sintaxis  
  
```cpp  
public delegate void delegate_name();  
```  
  
## Miembros  
 La clase Delegate tiene los métodos Equals\(\), GetHashCode\(\) y ToString\(\) que se derivan de [Platform::Object \(Clase\)](../cppcx/platform-object-class.md).  
  
## Comentarios  
 Use la palabra clave [delegate](~/windows/delegate-cpp-component-extensions.md) para crear delegados; no use Platform::Delegate de manera explícita. Para obtener más información, consulta [Delegados](../cppcx/delegates-c-cx.md). Para un ejemplo de cómo crear y usar un delegado, vea [Crear componentes de Windows en tiempo de ejecución en C\+\+](http://msdn.microsoft.com/library/5b7251e6-4271-4f13-af80-c1cf5b1489bf).  
  
## Requisitos  
 **Cliente mínimo admitido:** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **Servidor mínimo admitido:** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **Espacio de nombres:** Platform  
  
 **Metadatos:** platform.winmd  
  
## Vea también  
 [Espacio de nombres de plataforma](../cppcx/platform-namespace-c-cx.md)