---
title: naked (C++) | Microsoft Docs
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
ms.openlocfilehash: 3366995105f6295fd1d4d89ad85896fbb625519d
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/01/2018
ms.locfileid: "39402501"
---
# <a name="naked-c"></a>naked (C++)
**Específicos de Microsoft**  
  
 Para las funciones declaradas con el **naked** atributo, el compilador genera código sin código de prólogo y epílogo. Puede utilizar esta característica para escribir sus propias secuencias de código de prólogo/epílogo mediante código del ensamblador alineado. Las funciones naked son especialmente útiles al escribir controladores de dispositivos virtuales.  Tenga en cuenta que el **naked** atributo solo es válido en x86 y ARM y no está disponible en [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)].  
  
## <a name="syntax"></a>Sintaxis  
  
```  
__declspec(naked) declarator  
```  
  
## <a name="remarks"></a>Comentarios  
 Dado que el **naked** atributo solo es pertinente para la definición de una función y no es un modificador de tipo, funciones naked deben utilizar la sintaxis de atributo extendido y la [__declspec](../cpp/declspec.md) palabra clave.  
  

 El compilador no puede generar una función insertada para una función marcada con el atributo naked, incluso si la función está marcada también con la [__forceinline](inline-functions-cpp.md) palabra clave.  

 El compilador emite un error si el **naked** atributo se aplica a algo distinto de la definición de un método que no es miembro.  
  
## <a name="examples"></a>Ejemplos  
 Este código define una función con el **naked** atributo:  
  
```  
__declspec( naked ) int func( formal_parameters ) {}  
```  
  
 O bien, como alternativa:  
  
```  
#define Naked __declspec( naked )  
Naked int func( formal_parameters ) {}  
```  
  
 El **naked** atributo afecta solo a la naturaleza de generación de código del compilador para las secuencias de prólogo y epílogo de la función. No afecta al código que se genera para llamar a esas funciones. Por lo tanto, el **naked** atributo no se considera parte del tipo de la función y punteros de función no pueden tener la **naked** atributo. Además, el **naked** atributo no se puede aplicar a una definición de datos. Por ejemplo, en este ejemplo de código se genera un error:  
  
```  
__declspec( naked ) int i;  
// Error--naked attribute not permitted on data declarations.  
```  
  
 El **naked** atributo sólo es relevante para la definición de la función y no se puede especificar en el prototipo de la función. Por ejemplo, esta declaración genera un error del compilador:  
  
```  
__declspec( naked ) int func();  // Error--naked attribute not permitted on function declarations  
```  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [__declspec](../cpp/declspec.md)   
 [Palabras clave](../cpp/keywords-cpp.md)   
 [Llamadas de función naked](../cpp/naked-function-calls.md)