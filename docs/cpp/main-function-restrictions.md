---
title: Restricciones de la función principal | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- Main
dev_langs:
- C++
helpviewer_keywords:
- main function, restrictions on using
ms.assetid: 7b3df731-344b-44a8-850c-11cbcbfbfa83
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ed5be2df6e152b26bcade1970b35ad33655e8e02
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
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