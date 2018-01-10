---
title: Literales de cadena en expresiones primarias | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: string literals, in primary expressions
ms.assetid: 3ec31278-527b-40d2-8c83-6b09e2d81ca6
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0920280f672b1c45d317ade4c592a6b93356fb8f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="string-literals-in-primary-expressions"></a>Literales de cadena en expresiones primarias
Un “literal de cadena” es un carácter, un carácter ancho o una secuencia de caracteres consecutivos incluidos entre comillas dobles. Puesto que no son variables, los literales de cadena ni ninguno de sus elementos pueden ser el operando izquierdo de una operación de asignación. El tipo de un literal de cadena es una matriz de `char` (o una matriz de `wchar_t` para literales de cadena anchos). Las matrices incluidas en expresiones se convierten en punteros. Para más información sobre las cadenas, vea [Literales de cadena](../c-language/c-string-literals.md).  
  
## <a name="see-also"></a>Vea también  
 [Expresiones primarias de C](../c-language/c-primary-expressions.md)