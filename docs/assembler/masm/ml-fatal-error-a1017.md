---
title: Error irrecuperable A1017 de ML | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- A1017
dev_langs:
- C++
helpviewer_keywords:
- A1017
ms.assetid: bef0b312-5431-4e5a-b637-c19919acf01b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3f77f6d2905d70614735beb6cbcefeeb7e07b491
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="ml-fatal-error-a1017"></a>Error irrecuperable A1017 de ML
**nombre de archivo de origen que faltan**  
  
 Aprendizaje automático no encontró un archivo para ensamblar o pasar al vinculador.  
  
 Este error se genera cuando se proporcionan opciones de línea de comandos de ML sin especificar un nombre de archivo para que actúe sobre. Para montar archivos que no tienen una extensión de ASM, use la **/Ta** opción de línea de comandos.  
  
 Este error también puede generarse mediante la invocación de aprendizaje automático sin parámetros si la variable de entorno de aprendizaje automático contiene las opciones de línea de comandos.  
  
## <a name="see-also"></a>Vea también  
 [Mensajes de error de ML](../../assembler/masm/ml-error-messages.md)