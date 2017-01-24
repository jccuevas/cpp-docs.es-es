---
title: "setlocale | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "setlocale_CPP"
  - "vc-pragma.setlocale"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "pragma (directivas), setlocale"
  - "setlocale (pragma)"
ms.assetid: e60b43d9-fbdf-4c4e-ac85-805523a13b86
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# setlocale
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Define la configuración regional \(país o región e idioma\) que se utilizará al traducir constantes de caracteres y literales de cadena anchos.  
  
## Sintaxis  
  
```  
  
#pragma setlocale( "[locale-string]" )  
```  
  
## Comentarios  
 Puesto que el algoritmo para convertir caracteres multibyte en caracteres anchos puede variar en función de la configuración regional o la compilación puede tener lugar en una configuración regional diferente de donde se ejecuta un archivo ejecutable, esta directiva pragma proporciona una manera de especificar la configuración regional de destino en tiempo de compilación.  Esto garantiza que las cadenas de caracteres anchos se almacenen en el formato correcto.  
  
 El valor predeterminado de *locale\-string* es "".  
  
 La configuración regional “C” asigna cada carácter de la cadena a su valor como `wchar_t` \(unsigned short\).  Otros valores que son válidos para `setlocale` son las entradas que se encuentran en la lista de [Cadenas de idioma](../c-runtime-library/language-strings.md).  Por ejemplo, podría emitir:  
  
```  
#pragma setlocale("dutch")  
```  
  
 La capacidad de emitir una cadena de idioma depende de la compatibilidad con la página de códigos y el identificador de idioma en el equipo.  
  
## Vea también  
 [Directives pragma y la palabra clave \_\_pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)