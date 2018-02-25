---
title: pointers_to_members | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- pointers_to_members_CPP
- vc-pragma.pointers_to_members
dev_langs:
- C++
helpviewer_keywords:
- class members, pointers to
- pragmas, pointers_to_members
- members, pointers to
- pointers_to_members pragma
ms.assetid: 8325428c-c90a-4aed-9e82-cb1dda23f4ca
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4313aaa38d410b8e6f46594cd9ce11269b523073
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="pointerstomembers"></a>pointers_to_members
**C++ Specific**  
  
 Especifica si un puntero a un miembro de una clase se puede declarar antes que su definición de clase asociada y se utiliza para controlar el tamaño de puntero y el código requerido para interpretar el puntero.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
#pragma pointers_to_members( pointer-declaration, [most-general-representation] )  
```  
  
## <a name="remarks"></a>Comentarios  
 Puede colocar una **pointers_to_members** pragma en el archivo de origen como una alternativa al uso de la [/vmx](../build/reference/vmb-vmg-representation-method.md) opciones del compilador o el [palabras clave de herencia](../cpp/inheritance-keywords.md).  
  
 El *declaración de puntero* argumento especifica si se ha declarado un puntero a un miembro antes o después de la definición de función asociada. El *declaración de puntero* argumento es uno de los dos símbolos siguientes:  
  
|Argumento|Comentarios|  
|--------------|--------------|  
|**full_generality**|Genera código seguro, a veces no optimo. Usa **full_generality** si cualquier puntero a un miembro se declara antes de la definición de clase asociada. Este argumento siempre usa la representación de puntero especificada por el *most-general-representation* argumento. Equivalente a /vmg.|  
|**best_case**|Genera código seguro y óptimo que usa la representación best-case para todos los punteros a miembros. Requiere que se defina la clase antes de declarar un puntero a un miembro de la clase. El valor predeterminado es **best_case**.|  
  
 El *most-general-representation* la representación de puntero más pequeña que el compilador puede utilizar de forma segura para hacer referencia a cualquier puntero a un miembro de una clase en una unidad de traducción que especifica el argumento. El argumento puede ser uno de los siguientes:  
  
|Argumento|Comentarios|  
|--------------|--------------|  
|**single_inheritance**|La representación más general es single-inheritance, puntero a una función miembro. Produce un error si el modelo de herencia de una definición de clase para la que se declara un puntero a un miembro es múltiple o virtual.|  
|**multiple_inheritance**|La representación más general es multiple-inheritance, puntero a una función miembro. Produce un error si el modelo de herencia de una definición de clase para la que se declara un puntero a un miembro es virtual.|  
|**virtual_inheritance**|La representación más general es virtual-inheritance, puntero a una función miembro. Nunca produce un error. Este es el argumento predeterminado cuando **#pragma pointers_to_members (full_generality)** se utiliza.|  
  
> [!CAUTION]
>  Se aconseja colocar la pragma `pointers_to_members` solo en el archivo de código fuente al que desea que afecte, y solo después de directivas `#include`. Esta práctica reduce el riesgo de que la pragma afecte a otros archivos, y de que especifique accidentalmente varias definiciones para la misma variable, función o nombre de clase.  
  
## <a name="example"></a>Ejemplo  
  
```  
//   Specify single-inheritance only  
#pragma pointers_to_members( full_generality, single_inheritance )  
```  
  
## <a name="end-c-specific"></a>Específicos de C++: END  
  
## <a name="see-also"></a>Vea también  
 [Directivas pragma y la palabra clave __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)