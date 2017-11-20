---
title: "Access incorrecto a una unión | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: b273d984-62a8-4003-9a87-bf0149d3f2dd
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 54eeffebcc20846666c6ebb6a2951f8d55a5b8c5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="improper-access-to-a-union"></a>Access incorrecto a una unión
**ANSI 3.3.2.3** El acceso a un objeto de unión se realiza mediante un miembro de tipo diferente  
  
 Si se declara una unión de dos tipos y se almacena un valor, pero se obtiene acceso a la unión con el otro tipo, los resultados no son confiables.  
  
 Por ejemplo, se declara una unión de **float** e `int`. Se almacena un valor **float**, pero el programa accede posteriormente al valor como `int`. En esta situación, el valor dependería del almacenamiento interno de los valores **float**. El valor entero no sería confiable.  
  
## <a name="see-also"></a>Vea también  
 [Estructuras, uniones, enumeraciones y campos de bits](../c-language/structures-unions-enumerations-and-bit-fields.md)