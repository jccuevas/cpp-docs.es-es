---
title: "CMFCAcceleratorKey Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCAcceleratorKey"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCAcceleratorKey class"
ms.assetid: d140fbf7-23db-45ea-a63e-414a5ec7b3d5
caps.latest.revision: 36
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 38
---
# CMFCAcceleratorKey Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

una clase auxiliar que implementa la asignación de clave y el formato virtuales.  
  
## Sintaxis  
  
```  
class CMFCAcceleratorKey : public CObject  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCAcceleratorKey::CMFCAcceleratorKey](../Topic/CMFCAcceleratorKey::CMFCAcceleratorKey.md)|Crea un objeto `CMFCAcceleratorKey`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCAcceleratorKey::Format](../Topic/CMFCAcceleratorKey::Format.md)|Convierte la estructura de ACCEL en su representación visual.|  
|[CMFCAcceleratorKey::SetAccelerator](../Topic/CMFCAcceleratorKey::SetAccelerator.md)|establece la tecla de método abreviado para el objeto de `CMFCAcceleratorKey` .|  
  
## Comentarios  
 las teclas de aceleración también se conocen como teclas de método abreviado.  Si desea mostrar los métodos abreviados de teclado que introduce un usuario en, [CMFCAcceleratorKeyAssignCtrl Class](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md) asigna métodos abreviados de teclado, como Alt\+Shift\+S, en un formato de texto personalizado, como “ALT \+ cambio \+ s”.  Cada objeto de `CMFCAcceleratorKey` asigna una única tecla de método abreviado a un formato de texto.  
  
 Para obtener más información sobre cómo usar las teclas de método abreviado y la tabla de aceleradores, vea[CKeyboardManager Class](../../mfc/reference/ckeyboardmanager-class.md).  
  
## Ejemplo  
 El ejemplo siguiente muestra cómo construir un objeto de `CMFCAcceleratorKey` y cómo usar el método de `Format` .  
  
 [!code-cpp[NVC_MFC_RibbonApp#30](../../mfc/reference/codesnippet/CPP/cmfcacceleratorkey-class_1.cpp)]  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCAcceleratorKey](../../mfc/reference/cmfcacceleratorkey-class.md)  
  
## Requisitos  
 **encabezado:** afxacceleratorkey.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CKeyboardManager Class](../../mfc/reference/ckeyboardmanager-class.md)