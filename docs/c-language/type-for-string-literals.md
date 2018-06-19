---
title: Tipo para literales de cadena | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- string literals, type
- types [C], string literals
ms.assetid: f50a28af-20c1-4440-bdc6-564c86a309c8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1bfabc412c46a5fa73bf0cd3d000bb3823e5a389
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32386776"
---
# <a name="type-for-string-literals"></a>Tipo para literales de cadena
Los literales de cadena tienen una matriz de tipos de `char` (es decir, **char[ ]**). (Las cadenas de caracteres anchos tienen una matriz de tipos de `wchar_t`, es decir, **wchar_t[ ]**). Esto significa que una cadena es una matriz con elementos de tipo `char`. El número de elementos de la matriz es igual al número de caracteres de la cadena más una por el carácter NULL de terminación.  
  
## <a name="see-also"></a>Vea también  
 [Literales de cadena de C](../c-language/c-string-literals.md)