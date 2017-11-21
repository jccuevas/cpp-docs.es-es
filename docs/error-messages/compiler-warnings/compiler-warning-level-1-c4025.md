---
title: Compilador advertencia (nivel 1) C4025 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4025
dev_langs: C++
helpviewer_keywords: C4025
ms.assetid: c4f6a651-0641-4446-973e-8290065e49ad
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0e9bca6428358d1ce33e8069c7fcdfef19b23c7a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4025"></a>Advertencia del compilador (nivel 1) C4025
'number': el puntero de tipo basado se pasó a la función con los argumentos de variable: parámetro número  
  
 Si se pasa un puntero de tipo basado a una función con argumentos de variable, el puntero se normaliza, con resultados imprevisibles. No pase punteros de tipo basado a funciones con argumentos de variable.