---
title: C2667 de Error del compilador | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2667
dev_langs:
- C++
helpviewer_keywords:
- C2667
ms.assetid: 3c91d9d1-18fa-4e0d-a9ba-984d38980ca3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f5458bc5dc9500ea7850833b073d40d66bfc6e2a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33232361"
---
# <a name="compiler-error-c2667"></a>C2667 de Error del compilador
'función': ninguna de las sobrecargas número tiene una conversión mejor  
  
 Una llamada de función sobrecargada es ambigua y no se puede resolver.  
  
 La conversión requerida para que coincida con los parámetros reales de la llamada de función a una de las funciones sobrecargadas debe ser estrictamente mejor que las conversiones requeridas por todas las demás funciones sobrecargadas.  
  
 Vea el artículo de Knowledge Base Q240869 para obtener más información sobre la ordenación parcial de plantillas de función.