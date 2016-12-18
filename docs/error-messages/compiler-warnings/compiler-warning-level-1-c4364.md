---
title: "Advertencia del compilador (nivel 1) C4364 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4364"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4364"
ms.assetid: 1477634c-d60f-4570-ad16-1aaeae24ac7f
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 1) C4364
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

\#using para el ensamblado 'archivo' ya aparecía previamente en ubicación\(número\_de\_línea\) sin el atributo as\_friend; as\_friend no se aplica  
  
 Había una directiva `#using` repetida para un archivo de metadatos determinado, pero el calificador `as_friend` no se utilizó en la primera aparición; el compilador omitirá el calificador `as_friend` de la segunda directiva.  
  
 Para obtener más información, vea [Ensamblados de confianza \(C\+\+\)](../../dotnet/friend-assemblies-cpp.md).  
  
## Ejemplo  
 En el siguiente ejemplo se crea un componente.  
  
```  
// C4364.cpp  
// compile with: /clr /LD  
ref class A {};  
```  
  
## Ejemplo  
 El ejemplo siguiente genera el error C4364.  
  
```  
// C4364_b.cpp  
// compile with: /clr /W1 /c  
#using " C4364.dll"  
#using " C4364.dll" as_friend   // C4364  
```