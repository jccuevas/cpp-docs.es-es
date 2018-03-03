---
title: Error de BSCMAKE BK1517 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- BK1517
dev_langs:
- C++
helpviewer_keywords:
- BK1517
ms.assetid: 24391f42-0a3e-40a9-9991-c8b9a6a7b1c7
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5978ceab4a5a5e768ddda635398466bb941c42cd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="bscmake-error-bk1517"></a>Error de BSCMAKE BK1517
archivo de código fuente para archivo .sbr compilado con /Yc e /Yu  
  
 El archivo .sbr hace referencia a sí misma. Probablemente se recompilan con /Yu después de compilar con/Yc. Restablecer la opción de compilador para el archivo de origen/Yc, a continuación, seleccione **volver a generar** para generar nuevos archivos .sbr. No volver a compilar el archivo de código fuente con/Yu.