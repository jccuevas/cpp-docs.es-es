---
title: Resolver ambiguas declaraciones (C++) | Documentos de Microsoft
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
ms.openlocfilehash: 530111ee439a991201debab876d485a36b7f5ac5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="resolving-ambiguous-declarations-c"></a>Resolver ambiguas declaraciones (C++)
Para realizar conversiones explícitas de un tipo a otro, debe utilizar las conversiones especificando el nombre de tipo que desee. Algunas conversiones de tipos producen ambigüedad sintáctica. La siguiente conversión de tipo de estilo de función es ambigua:  
  
```  
char *aName( String( s ) );  
```  
  
 No está claro si es una declaración de función o una declaración de objeto con un estilo de función convierte como inicializador: podría declarar una función que devuelve el tipo de **char \***  que toma un argumento de tipo `String` , o podría declarar el objeto `aName` e inicialícela con el valor de `s` conversión al tipo `String`.  
  
 Si una declaración puede considerarse una declaración de función válida, se trata como tal. Solo si no puede ser una declaración de función (es decir, si fuera sintácticamente incorrecta) es una instrucción que podría tratarse como una conversión de tipo de estilo de función. Por consiguiente, el compilador interpreta la instrucción como una declaración de una función y omite los paréntesis incluidos alrededor del identificador `s`. Sin embargo, las instrucciones:  
  
```  
char *aName( (String)s );  
```  
  
 y  
  
```  
char *aName = String( s );  
```  
  
 son claramente las declaraciones de objetos y una conversión de tipo definido por el usuario `String` al tipo **char \***  se invoca para realizar la inicialización de `aName`.  
  
## <a name="see-also"></a>Vea también  
 