---
title: '&lt;ostream&gt; | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- std.<ostream>
- <ostream>
- ostream/std::<ostream>
- std::<ostream>
dev_langs:
- C++
helpviewer_keywords:
- ostream header
ms.assetid: 90c3b6fb-57cd-4ae7-99b8-8512f24a67d2
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 66798adc96121837b4ac2dd238b9887d3c5b7eef
ms.openlocfilehash: 4b8e9c4f86ac9bab261824c10a8e6d8c3506bc1a
ms.contentlocale: es-es
ms.lasthandoff: 04/29/2017

---
# <a name="ltostreamgt"></a>&lt;ostream&gt;
Define la clase de plantilla [basic_ostream](../standard-library/basic-ostream-class.md), que remite inserciones para iostreams. El encabezado define también varios manipuladores relacionados. (Este encabezado suele incluirlo automáticamente otro encabezado de iostreams. Rara vez tendrá que incluirlo directamente).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
#include <ostream>  
  
```  
  
### <a name="typedefs"></a>Definiciones de tipo  
  
|||  
|-|-|  
|[ostream](../standard-library/ostream-typedefs.md#ostream)|Crea un tipo de `basic_ostream` que está especializado en `char` y `char_traits` especializado en `char`.|  
|[wostream](../standard-library/ostream-typedefs.md#wostream)|Crea un tipo de `basic_ostream` que está especializado en `wchar_t` y `char_traits` especializado en `wchar_t`.|  
  
### <a name="manipulators"></a>Manipuladores  
  
|||  
|-|-|  
|[endl](../standard-library/ostream-functions.md#endl)|Termina una línea y vacía el búfer.|  
|[ends](../standard-library/ostream-functions.md#ends)|Termina una cadena|  
|[flush](../standard-library/ostream-functions.md#flush)|Vacía el búfer.|  
|[swap](../standard-library/ostream-functions.md#swap)|Intercambia los valores del parámetro de objeto `basic_ostream` de la izquierda con los del parámetro del objeto `basic_ostream` de la derecha.|  
  
### <a name="operators"></a>Operadores  
  
|||  
|-|-|  
|[operator<<](../standard-library/ostream-operators.md#op_lt_lt)|Escribe varios tipos en la secuencia.|  
  
### <a name="classes"></a>Clases  
  
|||  
|-|-|  
|[basic_ostream](../standard-library/basic-ostream-class.md)|La clase de plantilla describe un objeto que controla la inserción de objetos codificados y elementos en un búfer de secuencia.|  
  
## <a name="see-also"></a>Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Programación con iostream](../standard-library/iostream-programming.md)   
 [Convenciones de iostreams](../standard-library/iostreams-conventions.md)




