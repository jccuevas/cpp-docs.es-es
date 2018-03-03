---
title: "Restricciones de la función principal | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Main
dev_langs:
- C++
helpviewer_keywords:
- main function, restrictions on using
ms.assetid: 7b3df731-344b-44a8-850c-11cbcbfbfa83
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8a94844a0d5636c58a764114ed6f413923d69950
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="main-function-restrictions"></a>Restricciones de la función main
Varias restricciones se aplican a la **principal** función que no se aplican a otras funciones de C++. El **principal** función:  
  
-   No se pueden sobrecargar (vea [sobrecarga de funciones](function-overloading.md)).  
  
-   No se pueden declarar como **en línea**.  
  
-   No se pueden declarar como **estático**.  
  
-   No se puede tomar su dirección.  
  
-   No se puede llamar.  
  
## <a name="see-also"></a>Vea también  
 [main: Inicio de programa](../cpp/main-program-startup.md)