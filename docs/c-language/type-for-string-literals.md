---
title: Tipo para literales de cadena | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- string literals, type
- types [C], string literals
ms.assetid: f50a28af-20c1-4440-bdc6-564c86a309c8
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: Human Translation
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: 8e8d285bf85c711bd6adcbdb45c6384ea2309dc0
ms.contentlocale: es-es
ms.lasthandoff: 05/18/2017

---
# <a name="type-for-string-literals"></a>Tipo para literales de cadena
Los literales de cadena tienen una matriz de tipos de `char` (es decir, **char[ ]**). (Las cadenas de caracteres anchos tienen una matriz de tipos de `wchar_t`, es decir, **wchar_t[ ]**). Esto significa que una cadena es una matriz con elementos de tipo `char`. El número de elementos de la matriz es igual al número de caracteres de la cadena más una por el carácter NULL de terminación.  
  
## <a name="see-also"></a>Vea también  
 [Literales de cadena de C](../c-language/c-string-literals.md)
