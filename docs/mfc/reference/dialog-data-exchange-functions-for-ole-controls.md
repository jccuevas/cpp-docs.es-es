---
title: "Funciones de intercambio de datos de cuadro de di&#225;logo para controles OLE | Microsoft Docs"
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
  - "vc.mfc.macros.data"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DDX (intercambio de datos de cuadros de diálogo), compatibilidad con OLE"
  - "controles OLE, DDX (funciones)"
ms.assetid: 7ef1f288-ff65-40d4-aad2-5497bc00bb27
caps.latest.revision: 13
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Funciones de intercambio de datos de cuadro de di&#225;logo para controles OLE
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Este tema muestra las funciones de DDX\_OC utilizadas para intercambiar datos entre una propiedad de un control OLE en un cuadro de diálogo, vista de formulario, o un objeto de vista de control y un miembro de datos de cuadro de diálogo, del formulario, o del objeto de vista del control.  
  
### Funciones de DDX\_OC  
  
|||  
|-|-|  
|[DDX\_OCBool](../Topic/DDX_OCBool.md)|Administra la transferencia de datos de **bool** entre una propiedad de un control OLE y un miembro de datos de **bool** .|  
|[DDX\_OCBoolRO](../Topic/DDX_OCBoolRO.md)|Administra la transferencia de datos de **bool** entre una propiedad de solo lectura de un control OLE y un miembro de datos de **bool** .|  
|[DDX\_OCColor](../Topic/DDX_OCColor.md)|Administra la transferencia de datos de **OLE\_COLOR** entre una propiedad de un control OLE y un miembro de datos de **OLE\_COLOR** .|  
|[DDX\_OCColorRO](../Topic/DDX_OCColorRO.md)|Administra la transferencia de datos de **OLE\_COLOR** entre una propiedad de solo lectura de un control OLE y un miembro de datos de **OLE\_COLOR** .|  
|[DDX\_OCFloat](../Topic/DDX_OCFloat.md)|Administra la transferencia de datos de **flotante** \(o **double**\) entre una propiedad de un control OLE y un miembro de datos de **flotante** \(o **double**\).|  
|[DDX\_OCFloatRO](../Topic/DDX_OCFloatRO.md)|Administra la transferencia de datos de **flotante** \(o **double**\) entre una propiedad de solo lectura de un control OLE y un miembro de datos de **flotante** \(o **double**\).|  
|[DDX\_OCInt](../Topic/DDX_OCInt.md)|Administra la transferencia de datos de `int` \(o **long**\) entre una propiedad de un control OLE y un miembro de datos de `int` \(o **long**\).|  
|[DDX\_OCIntRO](../Topic/DDX_OCIntRO.md)|Administra la transferencia de datos de `int` \(o **long**\) entre una propiedad de solo lectura de un control OLE y un miembro de datos de `int` \(o **long**\).|  
|[DDX\_OCShort](../Topic/DDX_OCShort.md)|Administra la transferencia de datos de **corto** entre una propiedad de un control OLE y un miembro de datos de **corto** .|  
|[DDX\_OCShortRO](../Topic/DDX_OCShortRO.md)|Administra la transferencia de datos de **corto** entre una propiedad de solo lectura de un control OLE y un miembro de datos de **corto** .|  
|[DDX\_OCText](../Topic/DDX_OCText.md)|Administra la transferencia de datos de **CString** entre una propiedad de un control OLE y un miembro de datos de **CString** .|  
|[DDX\_OCTextRO](../Topic/DDX_OCTextRO.md)|Administra la transferencia de datos de **CString** entre una propiedad de solo lectura de un control OLE y un miembro de datos de **CString** .|  
  
## Vea también  
 [Macros y variables globales](../../mfc/reference/mfc-macros-and-globals.md)