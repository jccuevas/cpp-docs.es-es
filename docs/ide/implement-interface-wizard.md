---
title: "Asistente para implementar interfaces | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.codewiz.impl.interface.overview"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Asistente para implementar interfaces [C++]"
ms.assetid: 947c329e-0815-4ca7-835e-c41dfeb75f9e
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Asistente para implementar interfaces
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Este asistente implementa una interfaz para un objeto COM.  Las bibliotecas COM disponibles con Visual Studio y Windows incluyen las implementaciones de numerosas interfaces.  Una implementación de interfaz se asocia a un objeto cuando se crea una instancia del objeto, y suministra los servicios que ofrece el objeto.  
  
 Para obtener una descripción de las interfaces y su implementación, vea [Interfaces e implementación de las interfaces](http://msdn.microsoft.com/library/windows/desktop/ms694356) en [!INCLUDE[winsdkshort](../atl/reference/includes/winsdkshort_md.md)].  
  
 **Implementar interfaz desde**  
 Especifica la ubicación de la biblioteca de tipos desde la que se crea la interfaz.  
  
|Opción|Descripción|  
|------------|-----------------|  
|**Proyecto**|La biblioteca de tipos es parte del proyecto.|  
|**Registro**|La biblioteca de tipos se registra en el sistema.  Las bibliotecas de tipos registradas aparecen en **Controles ActiveX disponibles**.|  
|**Archivo**|La biblioteca de tipos no tiene por qué estar registrada en el sistema, pero sí está contenida en un archivo.  Deberá especificar la ubicación del archivo en **Ubicación**.|  
  
 **Bibliotecas de tipos disponibles**  
 Muestra las bibliotecas de tipos disponibles que contienen las definiciones de interfaz que puede implementar.  Si eligió **Archivo** en **Implementar interfaz desde**, no podrá realizar cambios en este cuadro.  
  
 **Ubicación**  
 Muestra la ubicación de la biblioteca de tipos seleccionada en la lista **Bibliotecas de tipos disponibles**.  Si seleccionó **Archivo** en **Implementar interfaz desde**, haga clic en el botón de puntos suspensivos para buscar el archivo que contiene la biblioteca de tipos que desea utilizar.  
  
 **Interfaces**  
 Muestra las interfaces cuyas definiciones se encuentran en la biblioteca de tipos que está seleccionada en el cuadro **Bibliotecas de tipos disponibles**.  
  
> [!NOTE]
>  Las interfaces que tienen el mismo nombre que las ya implementadas por el objeto seleccionado no se muestran en el cuadro **Interfaces**.  
  
|Botón de transferencia|Descripción|  
|----------------------------|-----------------|  
|**\>**|Agrega a la lista **Implementar interfaces** el nombre de la interfaz seleccionada en la lista **Interfaces**.|  
|**\>\>**|Agrega a la lista **Implementar interfaces** el nombre de todas las interfaces disponibles en la lista **Interfaces**.|  
|**\<**|Quita el nombre de la interfaz seleccionada en la lista **Implementar interfaces**.|  
|**\<\<**|Quita el nombre de todas las interfaces relacionadas en la lista **Implementar interfaces**.|  
  
 **Implementar interfaces**  
 Muestra el nombre de las interfaces que están seleccionadas para implementación en el objeto.  
  
> [!NOTE]
>  Si incluye más de una interfaz que se deriva de `IDispatch`, o si intenta implementar una interfaz que se deriva de otra interfaz ya presente en su clase, debe eliminar la ambigüedad de las entradas de COM\_MAP.  Para obtener más información, vea [COM\_INTERFACE\_ENTRY2](../Topic/COM_INTERFACE_ENTRY2.md).  
  
## Vea también  
 [Implementar una interfaz](../ide/implementing-an-interface-visual-cpp.md)