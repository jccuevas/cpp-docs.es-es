---
title: detect_mismatch | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- vc-pragma.detect_mismatch
- detect_mismatch_CPP
dev_langs:
- C++
helpviewer_keywords:
- pragmas, detect_mismatch
- detect_mismatch pragma
ms.assetid: ddb13ac9-0e2f-40ce-be69-7e44c04f5a12
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f165d24dc1a3044fb89474aef58a2992fa6feed9
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/10/2018
ms.locfileid: "42539095"
---
# <a name="detectmismatch"></a>detect_mismatch
Inserta un registro en un objeto. El vinculador comprueba estos registros para detectar potenciales discordancias.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
#pragma detect_mismatch( "name", "value"))  
```  
  
## <a name="remarks"></a>Comentarios  
 
Cuando se vincula el proyecto, el vinculador produce un error `LNK2038` si el proyecto contiene dos objetos que tengan el mismo `name` pero cada uno tiene diferente `value`. Utilice esta directiva pragma para evitar la vinculación de archivos objeto incoherentes.  
  
El nombre y el valor son literales de cadena y siguen las reglas para los literales de cadena con respecto a los caracteres de escape y concatenación. Se distinguen mayúsculas de minúsculas y no puede contener una coma, el signo igual, comillas, o la **null** caracteres.  
  
## <a name="example"></a>Ejemplo  
 
En este ejemplo se crean dos archivos que tienen números de versión diferentes para la misma etiqueta de versión.  
  
```cpp  
// pragma_directive_detect_mismatch_a.cpp  
#pragma detect_mismatch("myLib_version", "9")  
int main ()  
{  
   return 0;  
}  
  
// pragma_directive_detect_mismatch_b.cpp  
#pragma detect_mismatch("myLib_version", "1")  
```  
  
Si compila ambos archivos mediante la línea de comandos `cl pragma_directive_detect_mismatch_a.cpp pragma_directive_detect_mismatch_b.cpp`, recibirá el error `LNK2038`.  
  
## <a name="see-also"></a>Vea también  
 
[Directivas pragma y la palabra clave __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)