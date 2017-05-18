---
title: Sobrecargar el operador &gt;&gt; para las clases propias | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- operator>>
- operator>>, overloading for your own classes
- operator >>, overloading for your own classes
ms.assetid: 40dab4e0-3f97-4745-9cc8-b86e740fa246
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 4ac48927cc0b68dc958a09ee541c41895f11f86b
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="overloading-the-gtgt-operator-for-your-own-classes"></a>Sobrecargar el operador &gt;&gt; para las clases propias
Los flujos de entrada usan el operador de extracción (`>>`) para los tipos estándar. Puede escribir operadores de extracción similares para sus propios tipos; el éxito depende de usar los espacios en blanco de manera precisa.  
  
 Aquí se muestra un ejemplo de un operador de extracción para la clase `Date` que se ha presentado anteriormente:  
  
```  
istream& operator>> (istream& is, Date& dt)  
{  
    is>> dt.mo>> dt.da>> dt.yr;  
    return is;  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [Flujos de entrada](../standard-library/input-streams.md)


