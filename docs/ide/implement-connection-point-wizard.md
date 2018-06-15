---
title: Asistente para implementar puntos de conexión | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.codewiz.impl.cp.overview
dev_langs:
- C++
helpviewer_keywords:
- Implement Connection Point Wizard [C++]
ms.assetid: c117f6c6-30f0-4adb-82b4-b1f34e0f0fa8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ef2f7efa92de3714170e403ea50b5f486c8367d6
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "33323763"
---
# <a name="implement-connection-point-wizard"></a>Asistente para implementar puntos de conexión
Este asistente implementa un punto de conexión para un objeto COM. Un objeto conectable (es decir, un origen) puede exponer un punto de conexión para sus propias interfaces o para cualquier interfaz de salida. En Visual C++ y Windows se proporcionan bibliotecas de tipos que tienen interfaces de salida. Cada interfaz de salida se puede implementar mediante un cliente en un objeto (es decir, un receptor).  
  
 Para obtener más información, vea [Puntos de conexión en ATL](../atl/atl-connection-points.md).  
  
 **Bibliotecas de tipos disponibles**  
 Muestra las bibliotecas de tipos disponibles que contienen las definiciones de interfaz para las que se pueden implementar puntos de conexión. Haga clic en el botón de puntos suspensivos para buscar un archivo que contenga la biblioteca de tipos que se va a usar.  
  
 **Ubicación**  
 Muestra la ubicación de la biblioteca de tipos seleccionada actualmente en la lista **Bibliotecas de tipos disponibles**.  
  
 **Interfaces**  
 Muestra las interfaces cuyas definiciones se encuentran en la biblioteca de tipos seleccionada actualmente en el cuadro **Bibliotecas de tipos disponibles**.  
  
|Botón de transferencia|Description|  
|---------------------|-----------------|  
|**>**|Agrega el nombre de interfaz seleccionado actualmente en la lista **Interfaces** a la lista **Implementar puntos de conexión**.|  
|**>>**|Agrega todos los nombres de interfaz disponibles en la lista **Interfaces** a la lista **Implementar puntos de conexión**.|  
|**<**|Quita el nombre de interfaz seleccionado actualmente en la lista **Implementar puntos de conexión**.|  
|**<<**|Quita todos los nombres de interfaz que se muestran actualmente en la lista **Implementar puntos de conexión**.|  
  
 **Implementar puntos de conexión**  
 Muestra los nombres de las interfaces para las que se implementarán los puntos de conexión al hacer clic en **Finalizar**.  
  
## <a name="see-also"></a>Vea también  
 [Implementar un punto de conexión](../ide/implementing-a-connection-point-visual-cpp.md)