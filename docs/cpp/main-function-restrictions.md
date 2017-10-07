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
caps.latest.revision: 8
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 10fe82b0bb7ad700164b05ba466854db7716ba76
ms.contentlocale: es-es
ms.lasthandoff: 09/25/2017

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
