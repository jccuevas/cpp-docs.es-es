---
title: raw_native_types | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- raw_native_types
dev_langs:
- C++
helpviewer_keywords:
- raw_native_types attribute
ms.assetid: 9f38daa8-8dc0-46a5-aff9-f1ff9c1e6f48
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4908f1f06ef0479121d3ec5ac8fa56a797ed05ca
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="rawnativetypes"></a>raw_native_types
**C++ Specific**  
  
 Deshabilita el uso de las clases de soporte de COM en las funciones de contenedor de alto nivel y, en su lugar, fuerza el uso de tipos de datos de bajo nivel.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
raw_native_types  
```  
  
## <a name="remarks"></a>Comentarios  
 De forma predeterminada, los métodos de control de errores de alto nivel usan las clases de soporte COM [_bstr_t](../cpp/bstr-t-class.md) y [_variant_t](../cpp/variant-t-class.md) en lugar de la `BSTR` y **VARIANT** tipos de datos y punteros de interfaz COM sin formato. Estas clases encapsulan los detalles de asignación y desasignación del almacenamiento de memoria para estos tipos de datos, y simplifican considerablemente la conversión de tipos y las operaciones de conversión.  
  
 **FIN de específicos de C++**  
  
## <a name="see-also"></a>Vea también  
 [atributos #import](../preprocessor/hash-import-attributes-cpp.md)   
 [#import (directiva)](../preprocessor/hash-import-directive-cpp.md)