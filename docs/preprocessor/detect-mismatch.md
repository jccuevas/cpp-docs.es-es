---
title: detect_mismatch | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 875b6980a3c55c07b5765d6d0fc12be1796ee3a3
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="detectmismatch"></a>detect_mismatch
Inserta un registro en un objeto. El vinculador comprueba estos registros para detectar potenciales discordancias.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
#pragma detect_mismatch( "name", "value"))  
```  
  
## <a name="remarks"></a>Comentarios  
 Cuando se vincula el proyecto, el vinculador produce un error `LNK2038` si el proyecto contiene dos objetos que tengan el mismo `name` pero cada uno tiene diferente `value`. Utilice esta directiva pragma para evitar la vinculación de archivos objeto incoherentes.  
  
 El nombre y el valor son literales de cadena y siguen las reglas para los literales de cadena con respecto a los caracteres de escape y concatenación. Distinguen entre mayúsculas y minúsculas y no pueden contener comas, el signo igual, comillas dobles o el carácter `null`.  
  
## <a name="example"></a>Ejemplo  
 En este ejemplo se crean dos archivos que tienen números de versión diferentes para la misma etiqueta de versión.  
  
```  
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