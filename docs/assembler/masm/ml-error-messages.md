---
title: Mensajes de Error de ML | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- vc.errors.ml
dev_langs:
- C++
helpviewer_keywords:
- MASM (Microsoft Macro Assembler), ML error messages
ms.assetid: e7e164b3-6d65-4b5b-8925-bfbebc043523
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 09478bd3cff63e890014c6c14b11335feb8dfb3f
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="ml-error-messages"></a>Mensajes de error de ML
Los mensajes de error generados por componentes MASM se dividen en tres categorías:  
  
-   **Errores irrecuperables.** Éstas indican un problema grave que impide que la utilidad de completar el proceso normal.  
  
-   **Errores recuperables.** La utilidad puede completar su proceso. Si es así, su resultado no es probable que se van a la que desee.  
  
-   **Advertencias.** Estos mensajes indican las condiciones que pueden impedir que se obtengan los resultados que desee.  
  
 Todos los mensajes de error adoptan la forma siguiente:  
  
```  
  
Utility: Filename (Line) : [Error_type} (Code): Message_text  
```  
  
 donde:  
  
 `Utility`  
 El programa que envía el mensaje de error.  
  
 *Nombre de archivo*  
 El archivo que contiene la condición de generación de errores.  
  
 *Line*  
 La línea aproximada donde existe la condición de error.  
  
 *Error_type*  
 Fatal Error, Error o advertencia.  
  
 *Código*  
 El código de error 5 o 6 dígitos único.  
  
 `Message_text`  
 Una descripción breve y general de la condición de error.  
  
## <a name="see-also"></a>Vea también  
 [Referencia de Microsoft Macro Assembler](../../assembler/masm/microsoft-macro-assembler-reference.md)