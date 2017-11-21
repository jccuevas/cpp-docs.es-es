---
title: Asistente para implementar interfaces | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.codewiz.impl.interface.overview
dev_langs: C++
helpviewer_keywords: Implement Interface Wizard [C++]
ms.assetid: 947c329e-0815-4ca7-835e-c41dfeb75f9e
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 2c2179d3745f42164ef8cf70162ed560b331d783
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="implement-interface-wizard"></a>Asistente para implementar interfaces
Este asistente implementa una interfaz para un objeto COM. Las implementaciones de las interfaces se incluyen en las bibliotecas COM disponibles con Visual Studio y Windows. Una implementación de interfaz está asociada a un objeto cuando se crea una instancia de ese objeto, así como los servicios que ofrece el objeto.  
  
 Para obtener una explicación de las interfaces y las implementaciones, vea [Interfaces y las implementaciones de interfaz](http://msdn.microsoft.com/library/windows/desktop/ms694356) del SDK de Windows.  
  
 **Implementar interfaz desde**  
 Especifica la ubicación de la biblioteca de tipos, desde el que se crea la interfaz.  
  
|Opción|Descripción|  
|------------|-----------------|  
|**Proyecto**|La biblioteca de tipos es parte del proyecto.|  
|**Registro**|La biblioteca de tipos está registrada en el sistema. Bibliotecas de tipos registradas aparecen en **bibliotecas de tipos disponibles**.|  
|**Archivo**|La biblioteca de tipos no está necesariamente registrada en el sistema pero está contenida en un archivo. Debe proporcionar la ubicación del archivo en **ubicación**.|  
  
 **Bibliotecas de tipos disponibles**  
 Muestra las bibliotecas de tipos disponibles que contienen las definiciones de interfaz que puede implementar. Si hace clic en **archivo** en **Implementar interfaz desde**, este cuadro no está disponible para el cambio.  
  
 **Ubicación**  
 Muestra la ubicación de la biblioteca de tipos está seleccionada en el **bibliotecas de tipos disponibles** lista. Si seleccionó **archivo** en **Implementar interfaz desde**, haga clic en el botón de puntos suspensivos para buscar un archivo que contiene la biblioteca de tipos para usar.  
  
 **Interfaces**  
 Muestra las interfaces cuyas definiciones se encuentran en la biblioteca de tipos está seleccionada en el **bibliotecas de tipos disponibles** cuadro.  
  
> [!NOTE]
>  Interfaces que tienen el mismo nombre que las ya implementadas por el objeto seleccionado no se muestran en la **Interfaces** cuadro.  
  
|Botón de transferencia|Descripción|  
|---------------------|-----------------|  
|**>**|Agrega a la **implementar interfaces** lista el nombre de interfaz seleccionado actualmente en el **Interfaces** lista.|  
|**>>**|Agrega a la **implementar interfaces** lista todos los nombres de interfaz disponibles en la **Interfaces** lista.|  
|**<**|Quita el nombre de interfaz seleccionado actualmente en el **implementar interfaces** lista.|  
|**<\<**|Quita todos los nombres que actualmente aparecen en la interfaz del **implementar interfaces** lista.|  
  
 **Implementar Interfaces**  
 Muestra los nombres de las interfaces que ha seleccionado para implementar en el objeto.  
  
> [!NOTE]
>  Si incluye más de una interfaz que se deriva de `IDispatch`, o si se intenta implementar una interfaz que se deriva de otra interfaz ya presente en su clase, debe eliminar la ambigüedad de las entradas COM_MAP. Vea [COM_INTERFACE_ENTRY2](../atl/reference/com-interface-entry-macros.md#com_interface_entry2) para obtener más información.  
  
## <a name="see-also"></a>Vea también  
 [Implementar una interfaz](../ide/implementing-an-interface-visual-cpp.md)