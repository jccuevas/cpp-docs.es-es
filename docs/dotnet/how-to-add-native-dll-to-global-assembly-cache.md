---
title: "C&#243;mo: Agregar un archivo DLL nativo a la memoria cach&#233; global de ensamblados | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DLL [C++], nativas"
  - "GAC (caché global de ensamblados), cargar archivos DLL nativos"
  - "DLL nativas [C++]"
ms.assetid: 25e8d78a-b197-4269-b4e9-237a544ab3c8
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# C&#243;mo: Agregar un archivo DLL nativo a la memoria cach&#233; global de ensamblados
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Puede colocar un archivo DLL nativo \(no COM\) en la caché global de ensamblados.  
  
## Ejemplo  
 **\/ASSEMBLYLINKRESOURCE** le permite incrustar un archivo DLL nativo en un ensamblado.  
  
 Para obtener más información, vea [\/ASSEMBLYLINKRESOURCE \(Vincular a recursos de .NET Framework\)](../build/reference/assemblylinkresource-link-to-dotnet-framework-resource.md).  
  
```  
/ASSEMBLYLINKRESOURCE:MyComponent.dll  
```  
  
## Vea también  
 [Utilizar la interoperabilidad de C\+\+ \(PInvoke implícito\)](../dotnet/using-cpp-interop-implicit-pinvoke.md)