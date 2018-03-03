---
title: C2667 de Error del compilador | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2667
dev_langs:
- C++
helpviewer_keywords:
- C2667
ms.assetid: 3c91d9d1-18fa-4e0d-a9ba-984d38980ca3
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c00e469b2c89c0fa7c3966ec31410324bf6c2ff1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2667"></a>C2667 de Error del compilador
'función': ninguna de las sobrecargas número tiene una conversión mejor  
  
 Una llamada de función sobrecargada es ambigua y no se puede resolver.  
  
 La conversión requerida para que coincida con los parámetros reales de la llamada de función a una de las funciones sobrecargadas debe ser estrictamente mejor que las conversiones requeridas por todas las demás funciones sobrecargadas.  
  
 Vea el artículo de Knowledge Base Q240869 para obtener más información sobre la ordenación parcial de plantillas de función.