---
title: '&lt;ccomplex&gt; | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- <ccomplex>
dev_langs:
- C++
ms.assetid: a9fcb5f0-88e3-464b-a5fd-d1afb8cd7e6f
caps.latest.revision: 15
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
ms.sourcegitcommit: 3f69f0c3176d2fbe19e11ce08c071691a72d858d
ms.openlocfilehash: 63374ad7a56060da78621e9543f38dcfe8a06ae7
ms.lasthandoff: 02/24/2017

---
# <a name="ltccomplexgt"></a>&lt;ccomplex&gt;
Incluye el encabezado [\<complex>](../standard-library/complex.md) de la biblioteca estándar de C++ que, de forma efectiva, incluye el encabezado \<complex.h> de la biblioteca estándar de C y agrega los nombres asociados al espacio de nombres `std`.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
#include <ccomplex>  
  
```  
  
## <a name="remarks"></a>Comentarios  
 Incluir este encabezado también garantiza que los nombres declarados mediante vinculación externa en el encabezado de la biblioteca estándar de C se declaran en el espacio de nombres `std`.  
  
 El nombre `clog`, que está declarado en \<complex.h>, no está definido en el espacio de nombres `std` por los conflictos potenciales con el `clog` que está declarado en [\<iostream>](../standard-library/iostream.md).  
  
## <a name="see-also"></a>Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)   
 [Información general sobre la biblioteca estándar de C++](../standard-library/cpp-standard-library-overview.md)




