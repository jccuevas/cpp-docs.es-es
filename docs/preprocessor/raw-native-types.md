---
title: raw_native_types | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- raw_native_types
dev_langs:
- C++
helpviewer_keywords:
- raw_native_types attribute
ms.assetid: 9f38daa8-8dc0-46a5-aff9-f1ff9c1e6f48
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5baa3204b14da53f6a6a3232874e0ac7de0fd91b
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33849800"
---
# <a name="rawnativetypes"></a>raw_native_types
**Específicos de C++**  
  
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