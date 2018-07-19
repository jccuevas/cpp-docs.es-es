---
title: __if_not_exists (instrucción) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __if_not_exists_cpp
dev_langs:
- C++
helpviewer_keywords:
- __if_not_exists keyword [C++]
ms.assetid: a2f322d4-e96f-4a32-954e-4323d20c6e32
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bd4e586a211d7c4e2ead1ce3f225e2d92d2bd5a7
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32418821"
---
# <a name="ifnotexists-statement"></a>__if_not_exists (Instrucción)
La instrucción `__if_not_exists` prueba si existe el identificador especificado. Si el identificador no existe, se ejecuta el bloque de instrucción especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
__if_not_exists ( identifier ) {   
statements  
};  
```  
  
#### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`identifier`|El identificador cuya existencia se desea probar.|  
|`statements`|Una o más instrucciones que se ejecutarán si `identifier` no existe.|  
  
## <a name="remarks"></a>Comentarios  
  
> [!CAUTION]
>  Para obtener los resultados más confiables, conviene utilizar la instrucción `__if_not_exists` con las restricciones siguientes.  
  
-   Aplique la instrucción `__if_not_exists` solo a tipos simples y no a plantillas.  
  
-   Aplique la instrucción `__if_not_exists` a identificadores tanto dentro como fuera de una clase. No aplique la instrucción `__if_not_exists` a variables locales.  
  
-   Utilice la instrucción `__if_not_exists` solo en el cuerpo de una función. Fuera del cuerpo de una función, la instrucción `__if_not_exists` solo puede probar tipos totalmente definidos.  
  
-   Cuando se prueban funciones sobrecargadas, no se puede probar una forma específica de la sobrecarga.  
  
 El complemento a la `__if_not_exists` instrucción es la [__if_exists](../cpp/if-exists-statement.md) instrucción.  
  
## <a name="example"></a>Ejemplo  
 Para obtener un ejemplo sobre cómo usar `__if_not_exists`, consulte [__if_exists instrucción](../cpp/if-exists-statement.md).  
  
## <a name="see-also"></a>Vea también  
 [Instrucciones de selección](../cpp/selection-statements-cpp.md)   
 [Palabras clave](../cpp/keywords-cpp.md)   
 [__if_exists (Instrucción)](../cpp/if-exists-statement.md)