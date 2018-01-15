---
title: Modifier (propiedad) Acelerador | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: Modifier property
ms.assetid: f05a9379-e037-4cfb-b6ef-d2c655bcfa7f
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 63d6a4b526fc1f2aeb2a942e682a8c7cc6f9b58c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="accelerator-modifier-property"></a>Modifier (Propiedad de acelerador)
Las entradas siguientes son válidas para la propiedad modificador en la tabla de aceleradores.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|**Ninguno**|Usuario presiona solo el valor de clave. Uso es más eficaz con los valores ASCII/ANSI 001 a 026, que se interpreta como ^ A ^ Z (CTRL-A CTRL-Z).|  
|**ALT**|El usuario debe presionar la tecla ALT antes del valor de clave.|  
|**CTRL**|El usuario debe presionar la tecla CTRL antes del valor de clave. No es válido con el tipo de ASCII.|  
|**Tecla MAYÚS**|El usuario debe presionar la tecla MAYÚS antes del valor de clave.|  
|**Ctrl + Alt**|El usuario debe presionar la tecla CTRL y la tecla ALT antes del valor de clave. No es válido con el tipo de ASCII.|  
|**CTRL + MAYÚS**|El usuario debe presionar la tecla CTRL y MAYÚS antes del valor de clave. No es válido con el tipo de ASCII.|  
|**ALT + MAYÚS**|El usuario debe presionar la tecla ALT y la tecla MAYÚS antes del valor de clave. No es válido con el tipo de ASCII.|  
|**Ctrl + Alt + Mayús**|Usuario debe presionar CTRL, ALT y MAYÚS antes del valor de clave. No es válido con el tipo de ASCII.|  
  
## <a name="requirements"></a>Requisitos  
 Win32  
  
## <a name="see-also"></a>Vea también  
 [Establecer las propiedades de Acelerador](../windows/setting-accelerator-properties.md)   
 [Editor de aceleradores](../windows/accelerator-editor.md)