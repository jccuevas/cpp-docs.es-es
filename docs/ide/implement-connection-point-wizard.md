---
title: "Asistente para implementar puntos de conexi&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.codewiz.impl.cp.overview"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Asistente para implementar puntos de conexión [C++]"
ms.assetid: c117f6c6-30f0-4adb-82b4-b1f34e0f0fa8
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Asistente para implementar puntos de conexi&#243;n
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Este asistente implementa un punto de conexión para un objeto COM.  Un objeto conectable \(es decir, un origen\) puede exponer un punto de conexión para sus propias interfaces o para una interfaz de salida.  Tanto Visual C\+\+ como Windows disponen de bibliotecas de tipos que cuentan con interfaces de salida.  Cada interfaz de salida puede ser implementada por un cliente sobre un objeto \(es decir, un receptor\).  
  
 Para obtener más información, vea [Puntos de conexión en ATL](../atl/atl-connection-points.md).  
  
 **Bibliotecas de tipos disponibles**  
 Muestra las bibliotecas de tipos disponibles que contienen aquellas definiciones de interfaz para las que puede implementar puntos de conexión.  Haga clic en el botón de puntos suspensivos para buscar un archivo que contenga la biblioteca de tipos que desea utilizar.  
  
 **Ubicación**  
 Muestra la ubicación de la biblioteca de tipos seleccionada en la lista **Bibliotecas de tipos disponibles**.  
  
 **Interfaces**  
 Muestra las interfaces cuyas definiciones se encuentran en la biblioteca de tipos que está seleccionada en el cuadro **Bibliotecas de tipos disponibles**.  
  
|Botón de transferencia|Descripción|  
|----------------------------|-----------------|  
|**\>**|Agrega a la lista **Implementar puntos de conexión** el nombre de la interfaz seleccionada en la lista **Interfaces**.|  
|**\>\>**|Agrega a la lista **Implementar puntos de conexión** el nombre de todas las interfaces disponibles en la lista **Interfaces**.|  
|**\<**|Quita el nombre de la interfaz seleccionada en la lista **Implementar puntos de conexión**.|  
|**\<\<**|Quita el nombre de todas las interfaces relacionadas en la lista **Implementar puntos de conexión**.|  
  
 **Implementar puntos de conexión**  
 Muestra el nombre de aquellas interfaces para las cuales se implementarán puntos de conexión cuando haga clic en **Finalizar**.  
  
## Vea también  
 [Implementar un punto de conexión](../ide/implementing-a-connection-point-visual-cpp.md)