---
title: naked (C++) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- naked_cpp
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword [C++], naked
- naked __declspec keyword
ms.assetid: 69723241-05e1-439b-868e-20a83a16ab6d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 84e172c24bbb87f9243a4c0de25a98c90e043acc
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="naked-c"></a>naked (C++)
**Específicos de Microsoft**  
  
 Para las funciones declaradas con el atributo `naked`, el compilador genera código sin código de prólogo y epílogo. Puede utilizar esta característica para escribir sus propias secuencias de código de prólogo/epílogo mediante código del ensamblador alineado. Las funciones naked son especialmente útiles al escribir controladores de dispositivos virtuales.  Tenga en cuenta que el atributo `naked` solo es válido en x86 y ARM, y no está disponible en [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)].  
  
## <a name="syntax"></a>Sintaxis  
  
```  
__declspec(naked) declarator  
```  
  
## <a name="remarks"></a>Comentarios  
 Dado que la `naked` atributo solo es pertinente para la definición de una función y no es un modificador de tipo, funciones naked deben utilizar la sintaxis de atributo extendido y la [__declspec](../cpp/declspec.md) palabra clave.  
  

 El compilador no puede generar una función insertada para una función marcada con el atributo naked, incluso si la función también se marca con la [__forceinline](inline-functions-cpp.md) palabra clave.  

  
 El compilador emite un error si el atributo `naked` se aplica a algo distinto de la definición de un método que no es miembro.  
  
## <a name="examples"></a>Ejemplos  
 En este código se define una función con el atributo `naked`:  
  
```  
__declspec( naked ) int func( formal_parameters ) {}  
```  
  
 O bien, como alternativa:  
  
```  
#define Naked __declspec( naked )  
Naked int func( formal_parameters ) {}  
```  
  
 El atributo `naked` solo afecta a la naturaleza de la generación de código del compilador para las secuencias de prólogo y epílogo de la función. No afecta al código que se genera para llamar a esas funciones. Por tanto, el atributo `naked` no se considera parte del tipo de la función y los punteros a función no pueden tener el atributo `naked`. Además, el atributo `naked` no se puede aplicar a una definición de datos. Por ejemplo, en este ejemplo de código se genera un error:  
  
```  
__declspec( naked ) int i;       // Error--naked attribute not  
                                 // permitted on data declarations.  
```  
  
 El atributo `naked` solo es pertinente para la definición de la función y no se puede especificar en el prototipo de la función. Por ejemplo, esta declaración genera un error del compilador:  
  
```  
__declspec( naked ) int func();  // Error--naked attribute not   
                                 // permitted on function declarations  
```  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [__declspec](../cpp/declspec.md)   
 [Palabras clave](../cpp/keywords-cpp.md)   
 [Llamadas de función naked](../cpp/naked-function-calls.md)