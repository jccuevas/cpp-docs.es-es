---
title: "Evitar excepciones al apagar CLR cuando se utilizan objetos COM compilados con /clr | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/clr (opción del compilador) [C++], excepciones de apagado de CLR"
  - "/clr (opción del compilador) [C++], objetos COM"
  - "excepciones de apagado de CLR [C++]"
  - "interoperabilidad [C++], excepciones de apagado de CLR"
  - "interoperabilidad [C++], excepciones de apagado de CLR"
  - "ensamblados mixtos [C++], excepciones de apagado de CLR"
ms.assetid: 41249d83-4b51-4e46-866f-27f475f2498c
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Evitar excepciones al apagar CLR cuando se utilizan objetos COM compilados con /clr
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Cuando Common Language Runtime \(CLR\) pasa al modo de apagado, las funciones nativas tienen acceso limitado a los servicios de CLR.  Al intentar llamar a Release en un objeto COM compilado con **\/clr**, CLR pasa a código nativo y luego de nuevo a código administrado para dar servicio a la llamada IUnknown::Release \(que está definida en código administrado\).  CLR evita la devolución de llamada a código administrado ya que está en modo de apagado.  
  
 Para resolver esto, asegúrese de que los destructores llamados desde los métodos Release incluyen sólo código nativo.  
  
## Vea también  
 [Ensamblados mixtos \(nativos y administrados\)](../dotnet/mixed-native-and-managed-assemblies.md)