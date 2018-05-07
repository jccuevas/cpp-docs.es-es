---
title: Implementar el Asistente para puntos de conexión | Documentos de Microsoft
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
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="implement-connection-point-wizard"></a>Asistente para implementar puntos de conexión
Este asistente implementa un punto de conexión para un objeto COM. Un objeto conectable (es decir, un origen) puede exponer un punto de conexión para sus propias interfaces o para cualquier interfaz de salida. Visual C++ y Windows proporcionan las bibliotecas de tipos que tienen interfaces de salida. Cada interfaz de salida puede ser implementada por un cliente en un objeto (es decir, un receptor).  
  
 Para obtener más información, consulte [puntos de conexión ATL](../atl/atl-connection-points.md).  
  
 **Bibliotecas de tipos disponibles**  
 Muestra las bibliotecas de tipos disponibles que contienen las definiciones de interfaz para el que puede implementar puntos de conexión. Haga clic en el botón de puntos suspensivos para buscar un archivo que contiene la biblioteca de tipos para usar.  
  
 **Ubicación**  
 Muestra la ubicación de la biblioteca de tipos está seleccionada en el **bibliotecas de tipos disponibles** lista.  
  
 **Interfaces**  
 Muestra las interfaces cuyas definiciones se encuentran en la biblioteca de tipos está seleccionada en el **bibliotecas de tipos disponibles** cuadro.  
  
|Botón de transferencia|Descripción|  
|---------------------|-----------------|  
|**>**|Agrega a la **implementar puntos de conexión** lista el nombre de interfaz seleccionado actualmente en el **Interfaces** lista.|  
|**>>**|Agrega a la **implementar puntos de conexión** lista todos los nombres de interfaz disponibles en la **Interfaces** lista.|  
|**<**|Quita el nombre de interfaz seleccionado actualmente en el **implementar puntos de conexión** lista.|  
|**<<**|Quita todos los nombres que actualmente aparecen en la interfaz del **implementar puntos de conexión** lista.|  
  
 **Implementar puntos de conexión**  
 Muestra los nombres de las interfaces para las cuales se implementarán puntos de conexión al hacer clic en **finalizar**.  
  
## <a name="see-also"></a>Vea también  
 [Implementar un punto de conexión](../ide/implementing-a-connection-point-visual-cpp.md)