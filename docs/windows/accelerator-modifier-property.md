---
title: "Modifier (Propiedad de acelerador) | Microsoft Docs"
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
  - "Modifier (propiedad)"
ms.assetid: f05a9379-e037-4cfb-b6ef-d2c655bcfa7f
caps.latest.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Modifier (Propiedad de acelerador)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las entradas siguientes son valores válidos para la propiedad Modifier de la tabla de aceleradores:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|**None**|El usuario deberá presionar únicamente el valor de tecla \(Key\).  Su uso es más eficaz con los valores ASCII\/ANSI de 001 a 026, que se interpretan como ^A a ^Z \(CTRL\-A a CTRL\-Z\).|  
|**Alt**|El usuario deberá presionar la tecla ALT antes del valor de tecla \(Key\).|  
|**Ctrl**|El usuario deberá presionar la tecla CTRL antes del valor de tecla \(Key\).  No es válido si Type es ASCII.|  
|**Shift**|El usuario deberá presionar la tecla MAYÚS antes del valor de tecla \(Key\).|  
|**Ctrl\+Alt**|El usuario deberá presionar las teclas CTRL y ALT antes del valor de tecla \(Key\).  No es válido si Type es ASCII.|  
|**Ctrl\+Mayús**|El usuario deberá presionar las teclas CTRL y MAYÚS antes del valor de tecla \(Key\).  No es válido si Type es ASCII.|  
|**Alt\+Mayús**|El usuario deberá presionar las teclas ALT y MAYÚS antes del valor de tecla \(Key\).  No es válido si Type es ASCII.|  
|**Ctrl\+Alt\+Mayús**|El usuario deberá presionar las teclas CTRL, ALT y MAYÚS antes del valor de tecla \(Key\).  No es válido si Type es ASCII.|  
  
## Requisitos  
 Win32  
  
## Vea también  
 [Setting Accelerator Properties](../windows/setting-accelerator-properties.md)   
 [Accelerator Editor](../mfc/accelerator-editor.md)