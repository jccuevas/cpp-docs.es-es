---
title: '&lt;ccomplex&gt; | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: <ccomplex>
dev_langs: C++
ms.assetid: a9fcb5f0-88e3-464b-a5fd-d1afb8cd7e6f
caps.latest.revision: "15"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c381a68e913be77a1d62dc0f90fecdca9ee8d226
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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



