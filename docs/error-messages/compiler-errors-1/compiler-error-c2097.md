---
title: C2097 de Error del compilador | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2097
dev_langs: C++
helpviewer_keywords: C2097
ms.assetid: 7e5b2fd4-f61c-4b8a-b265-93e987a04bd3
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e50154d88a5019cdc181c4921c09cbd222d8b530
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2097"></a>C2097 de Error del compilador
inicialización no válida  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Posibles causas del error:  
  
1.  Inicialización de una variable con un valor no constante.  
  
2.  Inicialización de una dirección corta con una dirección larga.  
  
3.  Inicialización de un local estructura, unión o matriz con una expresión no constante cuando se compila con **/Za**.  
  
4.  Inicialización con una expresión que contiene un operador de coma.  
  
5.  Inicialización con una expresión que no sea constante ni simbólica.