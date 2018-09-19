---
title: Asistente para implementar interfaces | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.codewiz.impl.interface.overview
dev_langs:
- C++
helpviewer_keywords:
- Implement Interface Wizard [C++]
ms.assetid: 947c329e-0815-4ca7-835e-c41dfeb75f9e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3e5d48688d271330c1cbcbac69f2e0b0c60ccbe8
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45713757"
---
# <a name="implement-interface-wizard"></a>Asistente para implementar interfaces
Este asistente implementa una interfaz para un objeto COM. Las implementaciones de muchas interfaces se incluyen en las bibliotecas COM disponibles con Visual Studio y Windows. Una implementación de interfaz está asociada a un objeto cuando se crea una instancia de ese objeto, y proporciona los servicios que ofrece el objeto.  
  
Para obtener una explicación de las interfaces y las implementaciones, vea [Interfaces and Interface Implementations](/windows/desktop/com/interfaces-and-interface-implementations) (Interfaces e implementaciones de interfaz) de Windows SDK.  
  
- **Implementar interfaz desde**

   Especifica la ubicación de la biblioteca de tipos, desde la que se crea la interfaz.  
  
   |Opción|Descripción|  
   |------------|-----------------|  
   |**Proyecto**|La biblioteca de tipos forma parte del proyecto.|  
   |**Registry**|La biblioteca de tipos se registra en el sistema. Las bibliotecas de tipos registradas se enumeran en **Bibliotecas de tipos disponibles**.|  
   |**Archivo**|La biblioteca de tipos no está necesariamente registrada en el sistema pero se incluye en un archivo. Debe proporcionar la ubicación del archivo en **Ubicación**.|  
  
- **Bibliotecas de tipos disponibles**

   Muestra las bibliotecas de tipos disponibles que contienen las definiciones de interfaz que se pueden implementar. Si hace clic en **Archivo** en **Implementar interfaz desde**, este cuadro no está disponible para el cambio.  
  
- **Ubicación**

   Muestra la ubicación de la biblioteca de tipos seleccionada actualmente en la lista **Bibliotecas de tipos disponibles**. Si seleccionó **Archivo** en **Implementar interfaz desde**, haga clic en el botón de puntos suspensivos para buscar un archivo que contenga la biblioteca de tipos que se va a usar.  
  
- **Interfaces**

   Muestra las interfaces cuyas definiciones se encuentran en la biblioteca de tipos seleccionada actualmente en el cuadro **Bibliotecas de tipos disponibles**.  
  
   > [!NOTE]
   > Las interfaces que tienen el mismo nombre que las ya implementadas por el objeto seleccionado no se muestran en el cuadro **Interfaces**.  
  
   |Botón de transferencia|Descripción|  
   |---------------------|-----------------|  
   |**>**|Agrega el nombre de interfaz seleccionado actualmente en la lista **Interfaces** a la lista **Implementar interfaces**.|  
   |**>>**|Agrega todos los nombre de interfaz disponibles en la lista **Interfaces** a la lista **Implementar interfaces**.|  
   |**\<**|Quita el nombre de interfaz seleccionado actualmente en la lista **Implementar interfaces**.|  
   |**\<\<**|Quita todos los nombres de interfaz que se muestran actualmente en la lista **Implementar interfaces**.|  
  
- **Implementar Interfaces**

   Muestra los nombres de las interfaces que ha seleccionado para implementar en el objeto.  
  
   > [!NOTE]
   > Si incluye más de una interfaz que se deriva de `IDispatch`, o bien si se intenta implementar una interfaz que se deriva de otra ya presente en la clase, tendrá que eliminar la ambigüedad de las entradas COM_MAP. Vea [COM_INTERFACE_ENTRY2](../atl/reference/com-interface-entry-macros.md#com_interface_entry2) para obtener más información.  
  
## <a name="see-also"></a>Vea también  
 [Implementar una interfaz](../ide/implementing-an-interface-visual-cpp.md)