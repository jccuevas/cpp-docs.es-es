---
title: SafeInt (funciones) | Microsoft Docs
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
ms.openlocfilehash: b8a0475b5d3ba9053cd5d2df5ffd99ce9292ba8e
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2018
ms.locfileid: "39603460"
---
# <a name="safeint-functions"></a>SafeInt (Funciones)
La Biblioteca SafeInt proporciona varias funciones que puede utilizar sin necesidad de crear una instancia de la [clase SafeInt](../windows/safeint-class.md). Si desea proteger una sola operación matemática de desbordamiento de enteros, puede usar estas funciones. Si desea proteger varias operaciones matemáticas, debe crear **SafeInt** objetos. Resulta más eficaz crear **SafeInt** objetos para usar estas funciones varias veces.  
  
 Estas funciones permiten comparar o realizar operaciones matemáticas con dos tipos diferentes de parámetros sin tener que convertir en primer lugar en el mismo tipo.  
  
 Cada una de estas funciones tiene dos tipos de plantilla: `T` y `U`. Cada uno de estos tipos puede ser un valor booleano, un carácter o un tipo entero. Tipos enteros pueden ser con o sin signo y de cualquier tamaño de 8 bits a 64 bits.  
  
## <a name="in-this-section"></a>En esta sección  
  
|Función|Descripción|  
|--------------|-----------------|  
|[SafeAdd](../windows/safeadd.md)|Suma dos números y protege contra el desbordamiento.|  
|[SafeCast](../windows/safecast.md)|Convierte un tipo de parámetro a otro tipo.|  
|[SafeDivide](../windows/safedivide.md)|Divide dos números y protege frente al dividir por cero.|  
|[SafeEquals](../windows/safeequals.md), [SafeGreaterThan](../windows/safegreaterthan.md), [SafeGreaterThanEquals](../windows/safegreaterthanequals.md), [SafeLessThan](../windows/safelessthan.md), [SafeLessThanEquals](../windows/safelessthanequals.md), [ SafeNotEquals](../windows/safenotequals.md)|Compara dos números. Estas funciones le permiten comparar dos tipos diferentes de números sin cambiar sus tipos.|  
|[SafeModulus](../windows/safemodulus.md)|Realiza la operación de módulo en dos números.|  
|[SafeMultiply](../windows/safemultiply.md)|Multiplica a dos números juntos y protege contra el desbordamiento.|  
|[SafeSubtract](../windows/safesubtract.md)|Resta dos números y protege contra el desbordamiento.|  
  
## <a name="related-sections"></a>Secciones relacionadas  
  
|Sección|Descripción|  
|-------------|-----------------|  
|[SafeInt (clase)](../windows/safeint-class.md)|El **SafeInt** clase.|  
|[SafeIntException (clase)](../windows/safeintexception-class.md)|La clase de excepción específica de la Biblioteca SafeInt.|