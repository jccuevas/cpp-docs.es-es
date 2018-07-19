---
title: __if_not_exists (instrucción) | Microsoft Docs
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
ms.openlocfilehash: 37148a3849e859d7ca77595416616cfa0b952ecf
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/10/2018
ms.locfileid: "37939954"
---
# <a name="ifnotexists-statement"></a>__if_not_exists (Instrucción)
El **__if_not_exists** instrucción comprueba si existe el identificador especificado. Si el identificador no existe, se ejecuta el bloque de instrucción especificado.  
  
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
|`statements`|Una o varias instrucciones que se ejecutarán si `identifier` no existe.|  
  
## <a name="remarks"></a>Comentarios  
  
> [!CAUTION]
>  Para lograr los resultados más confiables, use el **__if_not_exists** instrucción con las restricciones siguientes.  
  
-   Aplicar el **__if_not_exists** instrucción solo a tipos simples, no a plantillas.  
  
-   Aplicar el **__if_not_exists** instrucción a identificadores tanto dentro como fuera de una clase. No se aplican los **__if_not_exists** instrucción a variables locales.  
  
-   Use la **__if_not_exists** instrucción sólo en el cuerpo de una función. Fuera del cuerpo de una función, el **__if_not_exists** instrucción puede probar solo tipos totalmente definidos.  
  
-   Cuando se prueban funciones sobrecargadas, no se puede probar una forma específica de la sobrecarga.  
  
 El complemento para el **__if_not_exists** instrucción es la [__if_exists](../cpp/if-exists-statement.md) instrucción.  
  
## <a name="example"></a>Ejemplo  
 Para obtener un ejemplo sobre cómo usar **__if_not_exists**, consulte [__if_exists instrucción](../cpp/if-exists-statement.md).  
  
## <a name="see-also"></a>Vea también  
 [Instrucciones de selección](../cpp/selection-statements-cpp.md)   
 [Palabras clave](../cpp/keywords-cpp.md)   
 [__if_exists (Instrucción)](../cpp/if-exists-statement.md)