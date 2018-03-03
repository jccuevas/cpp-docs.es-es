---
title: Error del evaluador de expresiones CXX0022 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- CXX0022
dev_langs:
- C++
helpviewer_keywords:
- CXX0022
- CAN0022
ms.assetid: f6b299ac-a4ee-492c-bd9f-6fff005bc537
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3ba715176ef5e1d7cece8c53adbf4c3d2daad628
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="expression-evaluator-error-cxx0022"></a>Error del evaluador de expresiones CXX0022
llamada de función antes de _main  
  
 El evaluador de expresiones de C no puede evaluar una función antes de que el depurador ha entrado en la función **_main**. El programa no se inicializó correctamente hasta que **_main** se ha llamado.  
  
 Este error es idéntico a CAN0022.