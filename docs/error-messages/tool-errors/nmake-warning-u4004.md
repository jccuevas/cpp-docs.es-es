---
title: Advertencia de NMAKE U4004 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- U4004
dev_langs:
- C++
helpviewer_keywords:
- U4004
ms.assetid: 5086bbcb-42d7-4677-a877-1a02202a86a2
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: fcbda9dd9d7ca5ecb99e46b9916fb95c2c560e49
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="nmake-warning-u4004"></a>Advertencia de NMAKE U4004
demasiadas reglas para el destino 'nombrededestino'  
  
 Se especificó más de un bloque de descripción para el destino dado usando signos de dos puntos (**:**) como separadores. NMAKE ejecuta los comandos en el primer bloque de descripción y omite los bloques posteriores.  
  
 Para especificar el mismo destino en varias dependencias, use dos puntos dobles (`::`) como separador en cada línea de dependencia.