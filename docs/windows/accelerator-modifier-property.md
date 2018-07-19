---
title: Modifier (propiedad) Acelerador | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Modifier property
ms.assetid: f05a9379-e037-4cfb-b6ef-d2c655bcfa7f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d99d4656f2835f9adb60f310e429c4ccb97ac7b6
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33854059"
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