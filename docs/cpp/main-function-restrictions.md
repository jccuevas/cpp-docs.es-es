---
title: Restricciones de la función Main | Microsoft Docs
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
ms.openlocfilehash: 3114f1ef379495f36f4231dbad6fd41ac145bcfe
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/10/2018
ms.locfileid: "37941751"
---
# <a name="main-function-restrictions"></a>Restricciones de la función main
Varias restricciones se aplican a la `main` función que no se aplican a otras funciones de C++. El `main` función:  
  
-   No se pueden sobrecargar (vea [sobrecarga de funciones](function-overloading.md)).  
  
-   No se puede declarar como **inline**.  
  
-   No se puede declarar como **estático**.  
  
-   No se puede tomar su dirección.  
  
-   No se puede llamar.  
  
## <a name="see-also"></a>Vea también  
 [main: Inicio de programa](../cpp/main-program-startup.md)