---
title: '&lt;set&gt; | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- std.<set>
- std::<set>
- <set>
dev_langs:
- C++
helpviewer_keywords:
- set header
ms.assetid: 43cb1ab2-6383-48cf-8bdc-2b96d7203596
caps.latest.revision: 20
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 2d05749ba2837a3879c91886b9266de47dd2ece6
ms.openlocfilehash: 1295a8c71464b7cc9d204c807c3492000b73ffa1
ms.lasthandoff: 02/24/2017

---
# <a name="ltsetgt"></a>&lt;set&gt;
Define las clases de plantilla de contenedor set y multiset, así como sus plantillas auxiliares.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
#include <set>  
  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="operators"></a>Operadores  
  
|Versión set |Versión multiset|Descripción|  
|-----------------|----------------------|-----------------|  
|[operator!= (set)](../standard-library/set-operators.md#operator_neq)|[operator!= (multiset)](../standard-library/set-operators.md#operator_neq)|Comprueba si el objeto set o multiset a la izquierda del operador no es igual que el objeto set o multiset situado a la derecha del operador.|  
|[operator< (set)](../standard-library/set-operators.md#operator_lt_)|[operator< (multiset)](../standard-library/set-operators.md#operator_lt_)|Comprueba si el objeto set o multiset a la izquierda del operador es menor que el objeto set o multiset situado a la derecha del operador.|  
|[operator<= (set)](../standard-library/set-operators.md#operator_lt__eq)|[operator\<= (multiset)](../standard-library/set-operators.md#operator_lt__eq)|Comprueba si el objeto set o multiset a la izquierda del operador es menor o igual que el objeto set o multiset situado a la derecha del operador.|  
|[operator== (set)](../standard-library/set-operators.md#operator_eq_eq)|[operator== (multiset)](../standard-library/set-operators.md#operator_eq_eq)|Comprueba si el objeto set o multiset a la izquierda del operador es igual que el objeto set o multiset situado a la derecha del operador.|  
|[operator> (set)](../standard-library/set-operators.md#operator_gt_)|[operator> (multiset)](../standard-library/set-operators.md#operator_gt_)|Comprueba si el objeto set o multiset a la izquierda del operador es mayor que el objeto set o multiset situado a la derecha del operador.|  
|[operator>= (set)](../standard-library/set-operators.md#operator_gt__eq)|[operator>= (multiset)](../standard-library/set-operators.md#operator_gt__eq)|Comprueba si el objeto set o multiset a la izquierda del operador es mayor o igual que el objeto set o multiset situado a la derecha del operador.|  
  
### <a name="specialized-template-functions"></a>Funciones de plantilla especializadas  
  
|Versión set |Versión multiset|Descripción|  
|-----------------|----------------------|-----------------|  
|[swap](../standard-library/set-functions.md#swap)|[swap](../standard-library/set-functions.md#swap)|Intercambia los elementos de dos sets o multisets.|  
  
### <a name="classes"></a>Clases  
  
|||  
|-|-|  
|[set (Clase)](../standard-library/set-class.md)|Se usa para el almacenamiento y la recuperación de datos de una colección en la que los valores de los elementos contenidos son únicos y sirven como valores de clave según los cuales se ordenan automáticamente los datos.|  
|[multiset (Clase)](../standard-library/multiset-class.md)|Se usa para el almacenamiento y la recuperación de datos de una colección en la que los valores de los elementos contenidos no tienen que ser únicos y en la que sirven como valores de clave según los cuales se ordenan automáticamente los datos.|  
  
## <a name="see-also"></a>Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Referencia de biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)




