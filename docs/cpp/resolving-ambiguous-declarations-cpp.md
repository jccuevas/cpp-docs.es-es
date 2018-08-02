---
title: Resolver declaraciones ambiguas (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 3d773ee7-bbea-47de-80c2-cb0a9d4ec0b9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3dc5b5a2b7d8add493efc144931160afb7d15020
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/02/2018
ms.locfileid: "39467883"
---
# <a name="resolving-ambiguous-declarations-c"></a>Resolver declaraciones ambiguas (C++)
Para realizar conversiones explícitas de un tipo a otro, debe utilizar las conversiones especificando el nombre de tipo que desee. Algunas conversiones de tipos producen ambigüedad sintáctica. La siguiente conversión de tipo de estilo de función es ambigua:  
  
```cpp 
char *aName( String( s ) );  
```  
  
 No está claro si es una declaración de función o una declaración de objeto con un estilo de función de conversión como inicializador: podría declarar una función que devuelve el tipo `char *` que toma un argumento de tipo `String`, o podría declarar el objeto `aName` e inicialícela con el valor de `s` conversión al tipo `String`.  
  
 Si una declaración puede considerarse una declaración de función válida, se trata como tal. Solo si no puede ser una declaración de función (es decir, si fuera sintácticamente incorrecta) es una instrucción que podría tratarse como una conversión de tipo de estilo de función. Por consiguiente, el compilador interpreta la instrucción como una declaración de una función y omite los paréntesis incluidos alrededor del identificador `s`. Sin embargo, las instrucciones:  
  
```cpp 
char *aName( (String)s );  
```  
  
 y  
  
```cpp 
char *aName = String( s );  
```  
  
 son claramente declaraciones de objetos y conversión de tipo definido por el usuario `String` escriba `char *` se invoca para llevar a cabo la inicialización de `aName`.  