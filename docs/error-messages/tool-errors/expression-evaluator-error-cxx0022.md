---
title: Error del evaluador de expresiones CXX0022 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0022
dev_langs:
- C++
helpviewer_keywords:
- CXX0022
- CAN0022
ms.assetid: f6b299ac-a4ee-492c-bd9f-6fff005bc537
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 822e07c9173d9010bb8ab63b6ca4837b9c52e066
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33297659"
---
# <a name="expression-evaluator-error-cxx0022"></a>Error del evaluador de expresiones CXX0022
llamada de función antes de _main  
  
 El evaluador de expresiones de C no puede evaluar una función antes de que el depurador ha entrado en la función **_main**. El programa no se inicializó correctamente hasta que **_main** se ha llamado.  
  
 Este error es idéntico a CAN0022.