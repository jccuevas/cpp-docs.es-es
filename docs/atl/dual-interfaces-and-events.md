---
title: "Dual Interfaces and Events | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "interfaces duales, eventos"
  - "eventos [C++], interfaces duales"
ms.assetid: bb382f7c-e885-4274-bf07-83f3602615d2
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Dual Interfaces and Events
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Aunque es posible diseñar una interfaz de eventos como dual, hay buenas razones de diseño para no hacerlo.  La razón fundamental es que el origen de eventos se iniciará solo el evento mediante el vtable o mediante `Invoke`, no ambos.  Si el origen de eventos desencadena el evento como una llamada al método vtable directa, los métodos de `IDispatch` nunca se utilizarán y está claro que la interfaz debe haberse una interfaz vtable pura.  Si el origen de eventos desencadena el evento como una llamada a `Invoke`, los métodos vtable nunca se utilizarán y está claro que la interfaz debe haberse dispinterface.  Si define las interfaces de eventos como se dobla, necesitará a clientes implementar la parte de una interfaz que nunca se utiliza.  
  
> [!NOTE]
>  Este argumento no se aplica a las interfaces duales, en general.  Desde una perspectiva de implementación, se dobla es una forma rápida, conviene, y bien\-admitida de implementar las interfaces que son accesibles a una gran variedad de clientes.  
  
 Hay otras razones para evitar interfaces duales de evento; ni compatibilidad con Visual Basic ni de Internet Explorer ellas.  
  
## Vea también  
 [Dual Interfaces and ATL](../atl/dual-interfaces-and-atl.md)