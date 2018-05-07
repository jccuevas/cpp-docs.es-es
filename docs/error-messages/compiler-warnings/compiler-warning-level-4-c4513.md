---
title: Compilador advertencia (nivel 4) C4513 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4513
dev_langs:
- C++
helpviewer_keywords:
- C4513
ms.assetid: 6877334a-f30a-4184-9483-dac3348737a4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 92c3e89204ec30f9c96a5ea03ede5093dd013d0c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-4-c4513"></a>Advertencia del compilador (nivel 4) C4513
'clase': no se pudo generar un destructor  
  
 El compilador no puede generar un destructor predeterminado para la clase dada; no se creó ningún destructor. Es el destructor de una clase base que no es accesible para la clase derivada. Si la clase base tiene un destructor privado, debe hacerse público o protegido.