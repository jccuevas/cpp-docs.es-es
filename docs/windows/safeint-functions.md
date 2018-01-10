---
title: SafeInt (funciones) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords: functions, SafeInt
ms.assetid: fdc208e5-5d8a-41a9-8271-567fd438958d
caps.latest.revision: "13"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6ae482b7f58d64a46b82b32c6c6d62d7f69f0dce
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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
|[SafeEquals](../windows/safeequals.md), [SafeGreaterThan](../windows/safegreaterthan.md), [SafeGreaterThanEquals](../windows/safegreaterthanequals.md), [SafeLessThan](../windows/safelessthan.md), [SafeLessThanEquals](../windows/safelessthanequals.md), [SafeNotEquals](../windows/safenotequals.md)|Compara dos números. Estas funciones le permiten comparar dos tipos diferentes de números sin cambiar sus tipos.|  
|[SafeModulus](../windows/safemodulus.md)|Realiza la operación de módulo en dos números.|  
|[SafeMultiply](../windows/safemultiply.md)|Multiplica a dos números juntos y protege contra los desbordamientos.|  
|[SafeSubtract](../windows/safesubtract.md)|Resta dos números y protege contra los desbordamientos.|  
  
## <a name="related-sections"></a>Secciones relacionadas  
  
|Sección|Descripción|  
|-------------|-----------------|  
|[SafeInt (clase)](../windows/safeint-class.md)|La clase `SafeInt`.|  
|[SafeIntException (clase)](../windows/safeintexception-class.md)|La clase de excepción específica a la Biblioteca SafeInt.|