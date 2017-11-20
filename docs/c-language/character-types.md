---
title: Tipos de caracteres | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- character data types [C]
- types [C], character
ms.assetid: d3ca8cda-c0d7-43af-9472-697e8ef015ce
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 275b1798665caaaa70aaa0de20aaec20c9979440
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="character-types"></a>Tipos de caracteres
Una constante de caracteres entera no precedida por la letra **L** tiene el tipo `int`. El valor de una constante de caracteres entera que contiene un carácter individual es el valor numérico del carácter interpretado como un entero. Por ejemplo, el valor numérico del carácter `a` es 97 en decimal y 61 en hexadecimal.  
  
 Sintácticamente, una "constante de caracteres anchos" es una constante de caracteres que tienen como prefijo la letra **L**. Una constante de caracteres anchos es de tipo `wchar_t`, un tipo entero definido en el archivo de encabezado STDDEF.H. Por ejemplo:  
  
```  
char    schar =  'x';   /* A character constant          */  
wchar_t wchar = L'x';   /* A wide-character constant for   
                            the same character           */  
```  
  
 Las constantes de caracteres anchos tienen 16 bits de ancho y especifican miembros del juego de caracteres de ejecución extendidos. Permiten expresar caracteres en los alfabetos demasiado grandes para representarlos mediante el tipo `char`. Vea [Caracteres multibyte y anchos](../c-language/multibyte-and-wide-characters.md) para obtener más información sobre los caracteres anchos.  
  
## <a name="see-also"></a>Vea también  
 [Constantes de caracteres de C](../c-language/c-character-constants.md)