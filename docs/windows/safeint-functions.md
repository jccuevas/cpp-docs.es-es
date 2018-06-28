---
title: SafeInt (funciones) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- functions, SafeInt
ms.assetid: fdc208e5-5d8a-41a9-8271-567fd438958d
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 97edd25abca3c9e80a35745165eedc93cc13a9b9
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33889312"
---
# <a name="safeint-functions"></a>SafeInt (Funciones)
La Biblioteca SafeInt proporciona varias funciones que puede utilizar sin crear una instancia de la [SafeInt (clase)](../windows/safeint-class.md). Si desea proteger una sola operación matemática de desbordamiento de enteros, puede usar estas funciones. Si desea proteger varias operaciones matemáticas, debe crear `SafeInt` objetos. Resulta más eficaz para crear `SafeInt` objetos que estas funciones varias veces.  
  
 Estas funciones permiten comparar, o para realizar operaciones matemáticas con dos tipos diferentes de parámetros sin tener que convertirlos a mismo tipo.  
  
 Cada una de estas funciones tiene dos tipos de plantilla: `T` y `U`. Cada uno de estos tipos puede ser un valor booleano, un carácter o un tipo entero. Tipos enteros pueden ser con o sin signo y cualquier tamaño de 8 bits a 64 bits.  
  
## <a name="in-this-section"></a>En esta sección  
  
|Función|Descripción|  
|--------------|-----------------|  
|[SafeAdd](../windows/safeadd.md)|Suma dos números y protege contra los desbordamientos.|  
|[SafeCast](../windows/safecast.md)|Convierte un tipo de parámetro a otro tipo.|  
|[SafeDivide](../windows/safedivide.md)|Divide dos números y protege frente a dividir por cero.|  
|[SafeEquals](../windows/safeequals.md), [SafeGreaterThan](../windows/safegreaterthan.md), [SafeGreaterThanEquals](../windows/safegreaterthanequals.md), [SafeLessThan](../windows/safelessthan.md), [SafeLessThanEquals](../windows/safelessthanequals.md), [ SafeNotEquals](../windows/safenotequals.md)|Compara dos números. Estas funciones le permiten comparar dos tipos diferentes de números sin cambiar sus tipos.|  
|[SafeModulus](../windows/safemodulus.md)|Realiza la operación de módulo en dos números.|  
|[SafeMultiply](../windows/safemultiply.md)|Multiplica a dos números juntos y protege contra los desbordamientos.|  
|[SafeSubtract](../windows/safesubtract.md)|Resta dos números y protege contra los desbordamientos.|  
  
## <a name="related-sections"></a>Secciones relacionadas  
  
|Sección|Descripción|  
|-------------|-----------------|  
|[SafeInt (clase)](../windows/safeint-class.md)|La clase `SafeInt`.|  
|[SafeIntException (clase)](../windows/safeintexception-class.md)|La clase de excepción específica a la Biblioteca SafeInt.|