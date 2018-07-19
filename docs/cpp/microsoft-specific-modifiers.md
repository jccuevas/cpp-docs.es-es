---
title: Modificadores específicos de Microsoft | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 22c7178c-f854-47fa-9de6-07d23fda58e1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8490a50f30d366a53a9e3288417a8d83032c556d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32420228"
---
# <a name="microsoft-specific-modifiers"></a>Modificadores específicos de Microsoft
En esta sección se describen las extensiones específicas de Microsoft para C++ en las áreas siguientes:  
  
-   [Direccionamiento con base](../cpp/based-addressing.md), la práctica de usar un puntero como base desde la que se pueden desplazar otros punteros  
  
-   [Convenciones de llamada de función](../cpp/calling-conventions.md)  
  
-   Atributos extendidos de almacenamiento clase declaradas con el [__declspec](../cpp/declspec.md) (palabra clave)  
  
-   El [__w64](../cpp/w64.md) (palabra clave)  
  
 Muchas de las palabras clave específicas de Microsoft se pueden utilizar para modificar declaradores y formar tipos derivados. Para obtener más información acerca de los declaradores, vea [declaradores](http://msdn.microsoft.com/en-us/8a7b9b51-92bd-4ac0-b3fe-0c4abe771838).  
  
### <a name="microsoft-specific-keywords"></a>Palabras clave específicas de Microsoft  
  
|Palabra clave|Significado|¿Se usa para formar tipos derivados?|  
|-------------|-------------|---------------------------------|  
|[__based](../cpp/based-grammar.md)|El nombre que sigue declara un desplazamiento de 32 bits con respecto a la base de 32 bits incluida en la declaración.|Sí|  
|[__cdecl](../cpp/cdecl.md)|El nombre que sigue usa las convenciones de nomenclatura y llamada de C.|Sí|  
|[__declspec](../cpp/declspec.md)|El nombre que sigue especifica un atributo de clase de almacenamiento específico de Microsoft.|No|  
|[__fastcall](../cpp/fastcall.md)|El nombre que sigue declara una función que usa registros, cuando están disponibles, en lugar de la pila para pasar el argumento.|Sí|  
|[__restrict](../cpp/extension-restrict.md)|Similar a __declspec ([restringir](../cpp/restrict.md)), pero para el uso de las variables.|No|  
|[__stdcall](../cpp/stdcall.md)|El nombre que sigue especifica una función conforme a la convención de llamada estándar.|Sí|  
|[__w64](../cpp/w64.md)|Marca un tipo de datos como mayor en un compilador de 64 bits.|No|  
|[__unaligned](../cpp/unaligned.md)|Especifica que un puntero a un tipo u otros datos no esté alineado.|No|  
|[__vectorcall](../cpp/vectorcall.md)|El nombre que sigue declara una función que usa registros, incluidos registros de SSE, si están disponibles, en lugar de la pila para el paso de argumentos.|Sí|  
  
## <a name="see-also"></a>Vea también  
 [Referencia del lenguaje C++](../cpp/cpp-language-reference.md)