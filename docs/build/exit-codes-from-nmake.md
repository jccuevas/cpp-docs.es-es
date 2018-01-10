---
title: "Códigos de salida de NMAKE | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- NMAKE program, exit codes
- exit codes
ms.assetid: 75f6913c-1da5-4572-a2d3-8a4e058bed15
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 13cbe4806d8b3960cbf80df41c7cce6e7657ba7e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="exit-codes-from-nmake"></a>Códigos de salida de NMAKE
NMAKE devuelve los siguientes códigos de salida:  
  
|Código|Significado|  
|----------|-------------|  
|0|Ningún error (posiblemente una advertencia)|  
|1|Generación incompleta (emitido solo cuando se usa/k)|  
|2|Error en un programa, posiblemente a causa de uno de los siguientes:|  
||-Un error de sintaxis en el archivo MAKE|  
||-Un código de error o de salida de un comando|  
||-Una interrupción por el usuario|  
|4|Error del sistema: memoria insuficiente|  
|255|Destino no está actualizado (emite solo cuando se usa/q)|  
  
## <a name="see-also"></a>Vea también  
 [Ejecución de NMAKE](../build/running-nmake.md)