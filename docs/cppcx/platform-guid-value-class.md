---
title: "Platform::Guid (Clase de valor) | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::Guid"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::Guid (struct)"
ms.assetid: 25c0bfb2-7f93-44d8-bdf4-ef4fbac3424a
caps.latest.revision: 6
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 6
---
# Platform::Guid (Clase de valor)
Representa un tipo [GUID](http://msdn.microsoft.com/library/windows/desktop/aa373931\(v=vs.85\).aspx) en el sistema de tipos de Windows en tiempo de ejecución.  
  
## Sintaxis  
  
```cpp  
public value struct Guid  
```  
  
## Miembros  
 Guid tiene los métodos Equals\(\), GetHashCode\(\) y ToString\(\) que se derivan de [Platform::Object \(Clase\)](../cppcx/platform-object-class.md), y el método GetTypeCode\(\) que se deriva de [Platform::Type \(Clase\)](../cppcx/platform-type-class.md). Guid también tiene los siguientes miembros.  
  
|Miembro|Descripción|  
|-------------|-----------------|  
|Guid|Inicializa una nueva instancia del struct Guid.|  
|operator\=\=|Operador Equals \(de igualdad\).|  
|operator\!\=|Operador Not Equals \(de desigualdad\).|  
|operator\(\)|Convierte un Guid en un GUID.|  
  
## Comentarios  
 Para obtener un ejemplo sobre cómo generar un nuevo elemento Platform::Guid mediante el uso de la función de Windows [CoCreateGuid](http://msdn.microsoft.com/library/windows/desktop/ms688568\(v=vs.85\).aspx), consulte [WinRT component: How to generate a GUID?](http://blogs.msdn.com/b/eternalcoding/archive/2013/03/25/winrt-component-how-to-generate-a-guid.aspx) \(Componente de WinRT: ¿Cómo generar un GUID?\).  
  
## Requisitos  
 **Cliente mínimo admitido:** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **Servidor mínimo admitido:** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **Espacio de nombres:** Platform  
  
 **Metadatos:** platform.winmd  
  
## Vea también  
 [Espacio de nombres de plataforma](../cppcx/platform-namespace-c-cx.md)