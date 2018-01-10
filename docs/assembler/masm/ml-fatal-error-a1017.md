---
title: Error irrecuperable A1017 de ML | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: A1017
dev_langs: C++
helpviewer_keywords: A1017
ms.assetid: bef0b312-5431-4e5a-b637-c19919acf01b
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0603ccb1de5767294afcfc012c1b9c8b18ac776d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="ml-fatal-error-a1017"></a>Error irrecuperable A1017 de ML
**nombre de archivo de origen que faltan**  
  
 Aprendizaje automático no encontró un archivo para ensamblar o pasar al vinculador.  
  
 Este error se genera cuando se proporcionan opciones de línea de comandos de ML sin especificar un nombre de archivo para que actúe sobre. Para montar archivos que no tienen una extensión de ASM, use la **/Ta** opción de línea de comandos.  
  
 Este error también puede generarse mediante la invocación de aprendizaje automático sin parámetros si la variable de entorno de aprendizaje automático contiene las opciones de línea de comandos.  
  
## <a name="see-also"></a>Vea también  
 [Mensajes de error de ML](../../assembler/masm/ml-error-messages.md)