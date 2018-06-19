---
title: setlocale | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- setlocale_CPP
- vc-pragma.setlocale
dev_langs:
- C++
helpviewer_keywords:
- pragmas, setlocale
- setlocale pragma
ms.assetid: e60b43d9-fbdf-4c4e-ac85-805523a13b86
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0cfabfa3c83fe2ff90a6f7dbe07d5205f7a6f9a9
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33847421"
---
# <a name="setlocale"></a>setlocale
Define la configuración regional (país o región e idioma) que se utilizará al traducir constantes de caracteres y literales de cadena anchos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
#pragma setlocale( "[locale-string]" )  
```  
  
## <a name="remarks"></a>Comentarios  
 Puesto que el algoritmo para convertir caracteres multibyte en caracteres anchos puede variar en función de la configuración regional o la compilación puede tener lugar en una configuración regional diferente de donde se ejecuta un archivo ejecutable, esta directiva pragma proporciona una manera de especificar la configuración regional de destino en tiempo de compilación. Esto garantiza que las cadenas de caracteres anchos se almacenen en el formato correcto.  
  
 El valor predeterminado *cadena de configuración regional* es "".  
  
 La configuración regional “C” asigna cada carácter de la cadena a su valor como `wchar_t` (unsigned short). Otros valores que son válidos para `setlocale` son las entradas que se encuentran en el [cadenas de idioma](../c-runtime-library/language-strings.md) lista. Por ejemplo, podría emitir:  
  
```  
#pragma setlocale("dutch")  
```  
  
 La capacidad de emitir una cadena de idioma depende de la compatibilidad con la página de códigos y el identificador de idioma en el equipo.  
  
## <a name="see-also"></a>Vea también  
 [Directivas pragma y la palabra clave __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)