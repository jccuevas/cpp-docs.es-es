---
title: '&lt;istream&gt; | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- istream/std::<istream>
- <istream>
- std::<istream>
dev_langs: C++
helpviewer_keywords: istream header
ms.assetid: efcf24e4-05d1-4719-ab0b-9e7ebe845d89
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a1e19ee61fd6a4b19e288c44b2d5c83950ee78e4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="ltistreamgt"></a>&lt;istream&gt;
Define el basic_istream de clase de plantilla que remita extracciones para las iostreams, y el basic_iostream de clase de plantilla que remita las inserciones y extracciones. El encabezado define también un manipulador relacionado. Este archivo de encabezado se suele incluir automáticamente mediante otro encabezado de iostreams; rara vez tendrá que incluirlo directamente.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
#include <istream>  
  
```  
  
### <a name="typedefs"></a>Definiciones de tipo  
  
|||  
|-|-|  
|[iostream](../standard-library/istream-typedefs.md#iostream)|Tipo `basic_iostream` especializado en `char`.|  
|[istream](../standard-library/istream-typedefs.md#istream)|Tipo `basic_istream` especializado en `char`.|  
|[wiostream](../standard-library/istream-typedefs.md#wiostream)|Tipo `basic_iostream` especializado en **wchar**.|  
|[wistream](../standard-library/istream-typedefs.md#wistream)|Tipo `basic_istream` especializado en **wchar**.|  
  
### <a name="manipulators"></a>Manipuladores  
  
|||  
|-|-|  
|[ws](../standard-library/istream-functions.md#ws)|Omite los espacios en blanco en el flujo.|  
|[swap](../standard-library/istream-functions.md#istream_swap)|Intercambia dos objetos de flujo.|  
  
### <a name="operators"></a>Operadores  
  
|||  
|-|-|  
|[operator>>](../standard-library/istream-operators.md#op_gt_gt)|Extrae caracteres y cadenas del flujo.|  
  
### <a name="classes"></a>Clases  
  
|||  
|-|-|  
|[basic_iostream](../standard-library/basic-iostream-class.md)|Clase de secuencia que puede realizar tanto operaciones de entrada como de salida.|  
|[basic_istream](../standard-library/basic-istream-class.md)|La clase de plantilla describe un objeto que controla la extracción de elementos y objetos codificados de un búfer de flujo con elementos de tipo **Elem**, también conocido como [char_type](../standard-library/basic-ios-class.md#char_type), cuyos rasgos de caracteres están determinados por la clase **Tr**, también conocida como [traits_type](../standard-library/basic-ios-class.md#traits_type).|  
  
## <a name="see-also"></a>Vea también  
 [Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Programación con iostream](../standard-library/iostream-programming.md)   
 [Convenciones de iostreams](../standard-library/iostreams-conventions.md)



