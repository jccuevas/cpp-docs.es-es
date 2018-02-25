---
title: '&lt;ostream&gt; | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- <ostream>
- ostream/std::<ostream>
- std::<ostream>
dev_langs:
- C++
helpviewer_keywords:
- ostream header
ms.assetid: 90c3b6fb-57cd-4ae7-99b8-8512f24a67d2
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9ed7238f2c0716f3eaea01bec25ebf54cc24f340
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="ltostreamgt"></a>&lt;ostream&gt;
Define la clase de plantilla [basic_ostream](../standard-library/basic-ostream-class.md), que remite inserciones para iostreams. El encabezado define también varios manipuladores relacionados. (Este encabezado suele incluirlo automáticamente otro encabezado de iostreams. Rara vez tendrá que incluirlo directamente).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
#include <ostream>  
  
```  
  
### <a name="typedefs"></a>Typedefs  
  
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



