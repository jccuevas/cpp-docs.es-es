---
title: "Operador String::operator+ | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::String::operator+"
dev_langs: 
  - "C++"
ms.assetid: 919b5ba4-3d3b-47a4-9893-9a9ce51fb9c8
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Operador String::operator+
Indica si dos objetos [String](../cppcx/platform-string-class.md) especificados tienen el mismo valor.  
  
## Sintaxis  
  
```cpp  
  
bool String::operator+( String^ str1,  
                         String^ str2)  
  
```  
  
#### Parámetros  
 `str1`  
 El primer objeto `String`.  
  
 `str2`  
 Segundo objeto `String`, cuyo contenido se anexará a `str1`.  
  
## Valor devuelto  
 `true` si `str1` es igual a `str2`; en caso contrario, `false`.  
  
## Comentarios  
 Este operador crea un objeto `String^` que contiene los datos de los operandos. Úsalo por comodidad cuando no sea necesario un rendimiento extreme. Es probable que algunas llamadas a "`+`" en una función no produzcan efectos apreciables, pero si estás manipulando objetos grandes o datos de texto en un bucle ajustado, usa los mecanismos y los tipos estándar de C\+\+.  
  
## Requisitos  
 **Cliente mínimo admitido:** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **Servidor mínimo admitido:** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **Espacio de nombres:** Platform  
  
 **Metadatos:** vccorlib.h  
  
## Vea también  
 [Platform::String \(Clase\)](../cppcx/platform-string-class.md)