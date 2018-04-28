---
title: Error irrecuperable A1017 de ML | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A1017
dev_langs:
- C++
helpviewer_keywords:
- A1017
ms.assetid: bef0b312-5431-4e5a-b637-c19919acf01b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c5fcb2d921a40b35c6022b2aca1e22adc2d8c45e
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/28/2018
---
# <a name="ml-fatal-error-a1017"></a>Error irrecuperable A1017 de ML
**nombre de archivo de origen que faltan**  
  
 Aprendizaje automático no encontró un archivo para ensamblar o pasar al vinculador.  
  
 Este error se genera cuando se proporcionan opciones de línea de comandos de ML sin especificar un nombre de archivo para que actúe sobre. Para montar archivos que no tienen una extensión de ASM, use la **/Ta** opción de línea de comandos.  
  
 Este error también puede generarse mediante la invocación de aprendizaje automático sin parámetros si la variable de entorno de aprendizaje automático contiene las opciones de línea de comandos.  
  
## <a name="see-also"></a>Vea también  
 [Mensajes de error de ML](../../assembler/masm/ml-error-messages.md)