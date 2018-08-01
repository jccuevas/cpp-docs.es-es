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
ms.openlocfilehash: 981d4c8c0ef30993811e5dbb6fd0a112a6447011
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/01/2018
ms.locfileid: "39406499"
---
# <a name="main-function-restrictions"></a>Restricciones de la función main
Varias restricciones se aplican a la **principal** función que no se aplican a otras funciones de C++. El **principal** función:  
  
-   No se pueden sobrecargar (vea [sobrecarga de funciones](function-overloading.md)).  
  
-   No se puede declarar como **inline**.  
  
-   No se puede declarar como **estático**.  
  
-   No se puede tomar su dirección.  
  
-   No se puede llamar.  
  
## <a name="see-also"></a>Vea también  
 
  [main: Inicio de programa](../cpp/main-program-startup.md)