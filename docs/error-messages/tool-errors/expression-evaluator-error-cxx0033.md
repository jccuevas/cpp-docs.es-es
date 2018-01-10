---
title: Error del evaluador de expresiones CXX0033 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: CXX0033
dev_langs: C++
helpviewer_keywords:
- CAN0033
- CXX0033
ms.assetid: 0bd62c5b-de89-481f-9b12-88fe84805afe
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 49f2b6221d385587fa5e62af51d37eb7d3b78872
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="expression-evaluator-error-cxx0033"></a>Error del evaluador de expresiones CXX0033
Error en la información de tipo OMF  
  
 El archivo ejecutable no tenía un formato de módulo de objeto válido (OMF) para la depuración.  
  
 Este error es idéntico a CAN0033.  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Posibles causas del error:  
  
1.  El archivo ejecutable no se creó con el vinculador lanzado con esta versión de Visual C++. Volver a vincular el código de objeto con la versión actual de LINK.exe.  
  
2.  Puede que el archivo .exe que esté dañado. Volver a compilar y volver a vincular el programa.