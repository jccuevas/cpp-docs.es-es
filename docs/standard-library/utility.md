---
title: '&lt;utility&gt; | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- <utility>
- utility/std::<utility>
- std.<utility>
- std::<utility>
dev_langs:
- C++
helpviewer_keywords:
- utility header
ms.assetid: c4491103-5da9-47a1-9c2b-ed8bc64b0599
caps.latest.revision: 18
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 66798adc96121837b4ac2dd238b9887d3c5b7eef
ms.openlocfilehash: 1a65dea30745ce3afa680c0851fe33cc9f386404
ms.contentlocale: es-es
ms.lasthandoff: 04/29/2017

---
# <a name="ltutilitygt"></a>&lt;utility&gt;
Define los tipos, funciones y operadores de las biblioteca estándar de C++ que facilitan la creación y administración de pares de objetos, que resultan útiles cuando se deben tratar dos objetos como si fueran uno solo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
#include <utility>  
  
```  
  
## <a name="remarks"></a>Comentarios  
 Los pares se usan ampliamente en la biblioteca estándar de C++. Son necesarios como argumentos y valores de devolución para distintas funciones y como tipos de elemento para contenedores como [la clase map](../standard-library/map-class.md) y la [clase multimap](../standard-library/multimap-class.md). \<map> incluye automáticamente el encabezado \<utility> para ayudar en la administración de los elementos de tipo de par clave/valor.  
  
### <a name="classes"></a>Clases  
  
|||  
|-|-|  
|[tuple_element](../standard-library/tuple-element-class-tuple.md)|Clase que contiene el tipo de un elemento `pair`.|  
|[tuple_size](../standard-library/tuple-size-class-tuple.md)|Clase que contiene el recuento de elementos `pair`.|  
  
### <a name="functions"></a>Funciones  
  
|||  
|-|-|  
|[forward](../standard-library/utility-functions.md#forward)|Impide que el reenvío directo oculte el tipo de referencia (`lvalue` o `rvalue`) del argumento.|  
|[get](../standard-library/utility-functions.md#get)|Función que obtiene un elemento de un objeto `pair`.|  
|[make_pair](../standard-library/utility-functions.md#make_pair)|Función de aplicación auxiliar de plantilla usada para construir objetos de tipo `pair`, donde los tipos de componente se basan en los tipos de datos pasados como parámetros.|  
|[move](../standard-library/utility-functions.md#move)|Devuelve los argumentos pasados como referencia `rvalue`.|  
|[swap](../standard-library/utility-functions.md#swap)|Intercambia los elementos de dos objetos `pair`.|  
  
### <a name="operators"></a>Operadores  
  
|||  
|-|-|  
|[operator!=](../standard-library/utility-operators.md#op_neq)|Comprueba si el objeto de par del lado izquierdo del operador no es igual que el objeto de par del lado derecho.|  
|[operator==](../standard-library/utility-operators.md#op_eq_eq)|Comprueba si el objeto de par del lado izquierdo del operador es igual que el objeto de par del lado derecho.|  
|[operator<](../standard-library/utility-operators.md#op_lt)|Comprueba si el objeto de par del lado izquierdo del operador es menor que el objeto de par del lado derecho.|  
|[operator\<=](../standard-library/utility-operators.md#op_gt_eq)|Comprueba si el objeto de par del lado izquierdo del operador es menor o igual que el objeto de par del lado derecho.|  
|[operator>](../standard-library/utility-operators.md#op_gt)|Comprueba si el objeto de par del lado izquierdo del operador es mayor que el objeto de par del lado derecho.|  
|[operator>=](../standard-library/utility-operators.md#op_gt_eq)|Comprueba si el objeto de par del lado izquierdo del operador es mayor o igual que el objeto de par del lado derecho.|  
  
### <a name="structs"></a>Estructuras  
  
|||  
|-|-|  
|[identity](../standard-library/identity-structure.md)||  
|[pair](../standard-library/pair-structure.md)|Tipo que proporciona la capacidad de tratar dos objetos como uno solo.|  
  
## <a name="see-also"></a>Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)




