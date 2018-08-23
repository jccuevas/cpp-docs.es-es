---
title: Modificadores específicos de Microsoft | Microsoft Docs
ms.custom: ''
ms.date: 08/16/2018
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
ms.openlocfilehash: a3dfc57e1d6af11628b37823f2452ee2b65f8a7f
ms.sourcegitcommit: 7f3df9ff0310a4716b8136ca20deba699ca86c6c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/21/2018
ms.locfileid: "42572520"
---
# <a name="microsoft-specific-modifiers"></a>Modificadores específicos de Microsoft
En esta sección se describen las extensiones específicas de Microsoft para C++ en las áreas siguientes:  
  
-   [Direccionamiento con base](based-addressing.md), la práctica de usar un puntero como base desde la que se pueden desplazar otros punteros  
  
-   [Convenciones de llamada de función](calling-conventions.md)  
  
-   Atributos extendidos de almacenamiento clase declarados con el [__declspec](declspec.md) palabra clave  
  
-   El [__w64](w64.md) palabra clave  

### <a name="microsoft-specific-keywords"></a>Palabras clave específicas de Microsoft  

Muchas de las palabras clave específicas de Microsoft se pueden utilizar para modificar declaradores y formar tipos derivados. Para obtener más información acerca de los declaradores, vea [declaradores](overview-of-declarators.md).  

|Palabra clave|Significado|¿Se usa para formar tipos derivados?|   
|-------------|-------------|---------------------------------|
|[__based](based-grammar.md)|El nombre que sigue declara un desplazamiento de 32 bits con respecto a la base de 32 bits incluida en la declaración.|Sí|   
|[__cdecl](cdecl.md)|El nombre que sigue usa las convenciones de nomenclatura y llamada de C.|Sí|      
|[__declspec](declspec.md)|El nombre que sigue especifica un atributo de clase de almacenamiento específico de Microsoft.|No|    
|[__fastcall](fastcall.md)|El nombre que sigue declara una función que usa registros, cuando están disponibles, en lugar de la pila para pasar el argumento.|Sí|   
|[__restrict](extension-restrict.md)|Similar a __declspec ([restringir](restrict.md)), pero para usarlo en variables.|No|      
|[__stdcall](stdcall.md)|El nombre que sigue especifica una función conforme a la convención de llamada estándar.|Sí|     
|[__w64](w64.md)|Marca un tipo de datos como mayor en un compilador de 64 bits.|No|    
|[__unaligned](unaligned.md)|Especifica que un puntero a un tipo u otros datos no esté alineado.|No|      
|[__vectorcall](vectorcall.md)|El nombre que sigue declara una función que usa registros, incluidos registros de SSE, si están disponibles, en lugar de la pila para el paso de argumentos.|Sí|      
    
## <a name="see-also"></a>Vea también     
 [Referencia del lenguaje C++](cpp-language-reference.md)