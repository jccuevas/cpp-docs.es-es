---
title: Error de BSCMAKE BK1517 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- BK1517
dev_langs:
- C++
helpviewer_keywords:
- BK1517
ms.assetid: 24391f42-0a3e-40a9-9991-c8b9a6a7b1c7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c6f5619a7c2a6ccf671845b27bbedf93d8eb2d69
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="bscmake-error-bk1517"></a>Error de BSCMAKE BK1517
archivo de código fuente para archivo .sbr compilado con /Yc e /Yu  
  
 El archivo .sbr hace referencia a sí misma. Probablemente se recompilan con /Yu después de compilar con/Yc. Restablecer la opción de compilador para el archivo de origen/Yc, a continuación, seleccione **volver a generar** para generar nuevos archivos .sbr. No volver a compilar el archivo de código fuente con/Yu.