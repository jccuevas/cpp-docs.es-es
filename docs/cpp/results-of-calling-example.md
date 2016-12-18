---
title: "Resultados del ejemplo de llamada | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ejemplos [C++], resultados de llamada"
  - "resultados, __cdecl (llamada)"
  - "resultados, __fastcall (llamada con palabra clave)"
  - "resultados, __stdcall (llamada)"
  - "resultados, thiscall (llamada)"
ms.assetid: aa70a7cb-ba1d-4aa6-bd0a-ba783da2e642
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Resultados del ejemplo de llamada
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Específicos de Microsoft  
  
## \_\_cdecl  
 El nombre de función representativo C es "\_MyFunc".  
  
 ![Convención de llamada CDECL](../cpp/media/vc37i01.png "vc37I01")  
La convención de llamada \_\_cdecl  
  
## \_\_stdcall y thiscall  
 El nombre representativo C \(`__stdcall`\) es "\_MyFunc@20". El nombre representativo C\+\+ es propietario.  
  
 ![Convenciones de llamada &#95;&#95;stdcall y thiscall](../cpp/media/vc37i02.png "vc37I02")  
Las convenciones de llamada de \_\_stdcall y thiscall  
  
## \_\_fastcall  
 El nombre representativo C \(`__fastcall`\) es "@MyFunc@20". El nombre representativo C\+\+ es propietario.  
  
 ![Convención de llamada de &#95;&#95;fastcall](../cpp/media/vc37i03.png "vc37I03")  
La convención de llamada \_\_fastcall  
  
### FIN de Específicos de Microsoft  
  
## Vea también  
 [Ejemplo de llamada: prototipo y llamada de función](../cpp/calling-example-function-prototype-and-call.md)