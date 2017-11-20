---
title: Tipo para literales de cadena | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- string literals, type
- types [C], string literals
ms.assetid: f50a28af-20c1-4440-bdc6-564c86a309c8
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: cd43cd92dbc0580ab87e45ed77bae1c1798613c5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="type-for-string-literals"></a>Tipo para literales de cadena
Los literales de cadena tienen una matriz de tipos de `char` (es decir, **char[ ]**). (Las cadenas de caracteres anchos tienen una matriz de tipos de `wchar_t`, es decir, **wchar_t[ ]**). Esto significa que una cadena es una matriz con elementos de tipo `char`. El número de elementos de la matriz es igual al número de caracteres de la cadena más una por el carácter NULL de terminación.  
  
## <a name="see-also"></a>Vea también  
 [Literales de cadena de C](../c-language/c-string-literals.md)